---
ms.date: 10/31/2017
keywords: DSC, powershell, konfiguration, installation
title: Skydda MOF-filen
ms.openlocfilehash: 6c2aadb75ac617d9b845ef387f292b8156bb8889
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079345"
---
# <a name="securing-the-mof-file"></a>Skydda MOF-filen

> Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0

DSC hanterar konfigurationen av servernoder genom att använda information som lagras i en MOF-fil där den lokala Configuration Manager (LCM) implementerar den önskade sluttillstånd.
Eftersom den här filen innehåller information om konfigurationen, är det viktigt att skydda den.
Det här avsnittet beskriver hur du kontrollerar målnoden har krypterade filen.

Från och med PowerShell-version 5.0, hela MOF-filen är krypterad som standard när det används i noden med hjälp av den `Start-DSCConfiguration` cmdlet.
Processen som beskrivs i den här artikeln krävs bara när du implementerar en lösning med hjälp av protokollet pull-tjänsten om certifikat inte som hanteras så konfigurationer som hämtas av målnoden kan dekryptera och läsas av systemet innan de tillämpas (till exempel vara hämtningstjänsten som är tillgängliga i Windows Server).
Noder som registrerats för [Azure Automation DSC](https://docs.microsoft.com/azure/automation/automation-dsc-overview) automatiskt har certifikat installerat och hanteras av tjänsten utan administrativa merkostnader krävs.

> [!NOTE]
> Det här avsnittet beskrivs certifikat som används för kryptering.
> För kryptering, ett självsignerat certifikat räcker, eftersom den privata nyckeln sparas alltid hemlighet och kryptering innebär inte litar på dokumentet.
> Självsignerade certifikat bör *inte* kan användas för autentisering.
> Du bör använda ett certifikat från en betrodd certifikatutfärdare (CA) för autentiseringssyfte.

## <a name="prerequisites"></a>Förutsättningar

För att kryptera har de autentiseringsuppgifter som används för att skydda en DSC-konfiguration kan du kontrollera att du har följande:

- **Några sätt att utfärda och distribuering av certifikat**. Det här avsnittet och dess exempel förutsätter att du använder Active Directory-certifikatutfärdare. Mer bakgrundsinformation om Active Directory Certificate Services finns i [Active Directory Certificate Services översikt](https://technet.microsoft.com/library/hh831740.aspx) och [Active Directory-certifikattjänster i Windows Server 2008](https://technet.microsoft.com/windowsserver/dd448615.aspx).
- **Administrativ åtkomst till målnoden eller noder**.
- **Varje målnoden har en kryptering-kompatibelt certifikat som har sparats sin personliga Store**. I Windows PowerShell är sökvägen till arkivet för certifikat: \LocalMachine\My. Exemplen i det här avsnittet använder mallen ”autentisering av arbetsstation”, som du kan hitta (tillsammans med andra certifikatmallar) på [Standardcertifikatmallar](https://technet.microsoft.com/library/cc740061(v=WS.10).aspx).
- Om du ska köra den här konfigurationen på en annan dator än målnoden **exportera den offentliga nyckeln för certifikatet**, och sedan importera den till den dator som du vill köra konfigurationen från. Se till att du exporterar endast den **offentliga** nyckeln; skydda den privata nyckeln.

## <a name="overall-process"></a>Övergripande processen

 1. Ställa in certifikat, nycklar och tumavtryck, se till att varje målnoden har kopior av certifikat och datorns konfiguration har den offentliga nyckeln och tumavtrycket.
 2. Skapa ett configuration datablock som innehåller sökvägen och tumavtrycket för den offentliga nyckeln.
 3. Skapa ett konfigurationsskript som definierar önskad konfiguration för målnoden och ställer in dekryptering på målnoder av kommandogivning lokala Configuration manager för att dekryptera konfigurationsdata med hjälp av certifikatet och dess tumavtryck.
 4. Kör sedan konfigurationen som Local Configuration Manager-inställningar och starta DSC-konfigurationen.

![Diagram1](../images/CredentialEncryptionDiagram1.png)

## <a name="certificate-requirements"></a>Certifikatkrav

För att du tillämpar kryptering av autentiseringsuppgifter, certifikatets offentliga nyckel måste vara tillgängliga på den _målnoden_ dvs **betrodda** av datorn som används för att skapa DSC-konfigurationen.
Den här offentliga nyckelcertifikat har särskilda krav för att kunna användas för kryptering av DSC-autentiseringsuppgifter:

1. **Nyckelanvändning**:
   - Måste innehålla: 'KeyEncipherment' och 'DataEncipherment'.
   - Bör _inte_ innehåller: Digital signatur.
2. **Utökad nyckelanvändning**:
   - Måste innehålla: Dokumentkryptering (1.3.6.1.4.1.311.80.1).
   - Bör _inte_ innehåller: Klientautentisering (1.3.6.1.5.5.7.3.2) och serverautentisering (1.3.6.1.5.5.7.3.1).
3. Den privata nyckeln för certifikatet är tillgänglig på den * Target Node_.
4. Den **Provider** för certifikatet måste vara ”Microsoft RSA SChannel kryptografiprovider”.

> [!IMPORTANT]
> Men du kan använda ett certifikat med som innehåller en nyckelanvändning i ”Digital signatur” eller något av Serverautentiserings-EKU, gör det att krypteringsnyckeln ska vara enklare felanvända och sårbar för angrepp. Så är det bäst att använda ett certifikat som skapats specifikt i syfte att skydda autentiseringsuppgifter för DSC som utan dessa nyckelanvändning och EKU.

Alla befintliga certifikat på den _målnoden_ som uppfyller dessa villkor kan användas till att säkra DSC-autentiseringsuppgifter.

## <a name="certificate-creation"></a>Skapandet av certifikat

Det finns två metoder som du kan använda för att skapa och använda nödvändiga krypteringscertifikatet (offentligt / privat nyckelpar).

1. Skapa den på den **målnoden** och exportera den offentliga nyckeln till den **redigering nod**
2. Skapa den på den **redigering noden** och exportera hela nyckelpar för den **målnoden**

Metod 1 rekommenderas eftersom den privata nyckeln som används för att dekryptera autentiseringsuppgifterna i MOF förblir på målnoden hela tiden.

### <a name="creating-the-certificate-on-the-target-node"></a>Skapa certifikatet på målnoden

Den privata nyckeln måste hållas hemliga eftersom används för att dekryptera MOF på den **målnoden** det enklaste sättet att göra det är att skapa certifikatet för privata nyckeln på den **målnoden**, och kopiera den  **offentliga nyckelcertifikat** på datorn som används för att skapa en MOF-fil att DSC-konfigurationen.
I följande exempel:

1. skapar ett certifikat på den **målnoden**
2. exporterar certifikatet för offentliga nyckeln på den **målnoden**.
3. importerar certifikatet för offentliga nyckeln till den **min** certifikatarkivet på den **redigering noden**.

#### <a name="on-the-target-node-create-and-export-the-certificate"></a>På målnoden: skapa och exportera certifikatet

> Målnoden: Windows Server 2016 och Windows 10

```powershell
# note: These steps need to be performed in an Administrator PowerShell session
$cert = New-SelfSignedCertificate -Type DocumentEncryptionCertLegacyCsp -DnsName 'DscEncryptionCert' -HashAlgorithm SHA256
# export the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
```

En gång exporterade den `DscPublicKey.cer` måste kopieras till den **redigering noden**.

> Målnoden: Windows Server 2012 R2/Windows 8.1 och tidigare
> [!WARNING]
> Eftersom den `New-SelfSignedCertificate` cmdlet på Windows operativsystem före Windows 10 och Windows Server 2016 stöder inte den **typ** parameter, en alternativ metod för att skapa det här certifikatet måste finnas på de här operativsystemen.
>
> I det här fallet kan du använda `makecert.exe` eller `certutil.exe` att skapa certifikatet.
>
>En alternativ metod är att [ladda ned skriptet New-SelfSignedCertificateEx.ps1 från Microsoft Script Center](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) och använda den för att skapa certifikatet i stället:

```powershell
# note: These steps need to be performed in an Administrator PowerShell session
# and in the folder that contains New-SelfSignedCertificateEx.ps1
. .\New-SelfSignedCertificateEx.ps1
New-SelfsignedCertificateEx `
    -Subject "CN=${ENV:ComputerName}" `
    -EKU 'Document Encryption' `
    -KeyUsage 'KeyEncipherment, DataEncipherment' `
    -SAN ${ENV:ComputerName} `
    -FriendlyName 'DSC Credential Encryption certificate' `
    -Exportable `
    -StoreLocation 'LocalMachine' `
    -KeyLength 2048 `
    -ProviderName 'Microsoft Enhanced Cryptographic Provider v1.0' `
    -AlgorithmName 'RSA' `
    -SignatureAlgorithm 'SHA256'
# Locate the newly created certificate
$Cert = Get-ChildItem -Path cert:\LocalMachine\My | Where-Object {
        ($_.FriendlyName -eq 'DSC Credential Encryption certificate') -and ($_.Subject -eq "CN=${ENV:ComputerName}")
    } | Select-Object -First 1
# export the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
```

En gång exporterade den ```DscPublicKey.cer``` måste kopieras till den **redigering noden**.

#### <a name="on-the-authoring-node-import-the-certs-public-key"></a>På noden redigering: importera på certifikatets offentliga nyckel

```powershell
# Import to the my store
Import-Certificate -FilePath "$env:temp\DscPublicKey.cer" -CertStoreLocation Cert:\LocalMachine\My
```

### <a name="creating-the-certificate-on-the-authoring-node"></a>Skapa certifikatet på noden för redigering

Alternativt kan krypteringscertifikatet kan skapas på den **redigering noden**, exporterade med den **privata nyckeln** som en PFX-filen och sedan importeras på den **målnoden**.
Det här är den aktuella metoden för kryptering av autentiseringsuppgifter för DSC om _Nano Server_.
Även om den PFX-filen är skyddad med ett lösenord bör den hållas säkra under överföringen.
I följande exempel:

1. skapar ett certifikat på den **redigering noden**.
2. exporterar certifikatet, inklusive den privata nyckeln på den **redigering noden**.
3. tar bort den privata nyckeln från den **redigering noden**, men de är fortfarande certifikatet för offentliga nyckeln den **min** lagra.
4. importerar certifikatet för privata nyckeln till My(Personal) certifikatarkivet på den **målnoden**.
   - Det måste läggas till rotarkivet så att det ska vara betrott av den **målnoden**.

#### <a name="on-the-authoring-node-create-and-export-the-certificate"></a>På noden redigering: skapa och exportera certifikatet

> Målnoden: Windows Server 2016 och Windows 10

```powershell
# note: These steps need to be performed in an Administrator PowerShell session
$cert = New-SelfSignedCertificate -Type DocumentEncryptionCertLegacyCsp -DnsName 'DscEncryptionCert' -HashAlgorithm SHA256
# export the private key certificate
$mypwd = ConvertTo-SecureString -String "YOUR_PFX_PASSWD" -Force -AsPlainText
$cert | Export-PfxCertificate -FilePath "$env:temp\DscPrivateKey.pfx" -Password $mypwd -Force
# remove the private key certificate from the node but keep the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
$cert | Remove-Item -Force
Import-Certificate -FilePath "$env:temp\DscPublicKey.cer" -CertStoreLocation Cert:\LocalMachine\My
```

En gång exporterade den `DscPrivateKey.pfx` måste kopieras till den **målnoden**.

> Målnoden: Windows Server 2012 R2/Windows 8.1 och tidigare
> [!WARNING]
> Eftersom den `New-SelfSignedCertificate` cmdlet på Windows operativsystem före Windows 10 och Windows Server 2016 stöder inte den **typ** parameter, en alternativ metod för att skapa det här certifikatet måste finnas på de här operativsystemen.
>
> I det här fallet kan du använda `makecert.exe` eller `certutil.exe` att skapa certifikatet.
>
> En alternativ metod är att [ladda ned skriptet New-SelfSignedCertificateEx.ps1 från Microsoft Script Center](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) och använda den för att skapa certifikatet i stället:

```powershell
# note: These steps need to be performed in an Administrator PowerShell session
# and in the folder that contains New-SelfSignedCertificateEx.ps1
. .\New-SelfSignedCertificateEx.ps1
New-SelfsignedCertificateEx `
    -Subject "CN=${ENV:ComputerName}" `
    -EKU 'Document Encryption' `
    -KeyUsage 'KeyEncipherment, DataEncipherment' `
    -SAN ${ENV:ComputerName} `
    -FriendlyName 'DSC Credential Encryption certificate' `
    -Exportable `
    -StoreLocation 'LocalMachine' `
    -KeyLength 2048 `
    -ProviderName 'Microsoft Enhanced Cryptographic Provider v1.0' `
    -AlgorithmName 'RSA' `
    -SignatureAlgorithm 'SHA256'
# Locate the newly created certificate
$Cert = Get-ChildItem -Path cert:\LocalMachine\My | Where-Object {
        ($_.FriendlyName -eq 'DSC Credential Encryption certificate') -and ($_.Subject -eq "CN=${ENV:ComputerName}")
    } | Select-Object -First 1
# export the public key certificate
$mypwd = ConvertTo-SecureString -String "YOUR_PFX_PASSWD" -Force -AsPlainText
$cert | Export-PfxCertificate -FilePath "$env:temp\DscPrivateKey.pfx" -Password $mypwd -Force
# remove the private key certificate from the node but keep the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
$cert | Remove-Item -Force
Import-Certificate -FilePath "$env:temp\DscPublicKey.cer" -CertStoreLocation Cert:\LocalMachine\My
```

#### <a name="on-the-target-node-import-the-certs-private-key-as-a-trusted-root"></a>På målnoden: importera den certifikatets privata nyckel som en betrodd rot

```powershell
# Import to the root store so that it is trusted
$mypwd = ConvertTo-SecureString -String "YOUR_PFX_PASSWD" -Force -AsPlainText
Import-PfxCertificate -FilePath "$env:temp\DscPrivateKey.pfx" -CertStoreLocation Cert:\LocalMachine\My -Password $mypwd > $null
```

## <a name="configuration-data"></a>Konfigurationsdata

Datablocket konfigurationen definierar vilka målnoder att driva på om eller inte för att kryptera autentiseringsuppgifterna, insamling av kryptering och annan information. Mer information om datablocket konfiguration finns i [att avgränsa konfigurations- och miljödata](../configurations/configData.md).

De element som kan konfigureras för varje nod som är relaterade till kryptering av autentiseringsuppgifter är:

- **Nodnamn** -namnet på målnoden som kryptering av autentiseringsuppgifter konfigureras för.
- **PsDscAllowPlainTextPassword** – oavsett om okrypterade autentiseringsuppgifter kommer att kunna skickas till den här noden. Det här är **rekommenderas inte**.
- **Tumavtrycket** -tumavtrycket för certifikatet som används för att dekryptera autentiseringsuppgifterna i DSC-konfigurationen på den _målnoden_. **Det här certifikatet måste finnas i lokala datorns certifikatarkiv på målnoden.**
- **CertificateFile** - certifikatfilen (som innehåller den offentliga nyckeln) som ska användas för att kryptera autentiseringsuppgifterna för den _målnoden_. Detta måste vara antingen en DER-kodad binärfil X.509 eller Base64-kodad X.509-format-certifikatfil.

Det här exemplet visar ett datablock för konfigurationen som anger en målnoden att agera på namngivna målnod, sökvägen till den certifikatfil (med namnet targetNode.cer) och tumavtrycket för den offentliga nyckeln.

```powershell
$ConfigData= @{
    AllNodes = @(
            @{
                # The name of the node we are describing
                NodeName = "targetNode"

                # The path to the .cer file containing the
                # public key of the Encryption Certificate
                # used to encrypt credentials for this node
                CertificateFile = "C:\publicKeys\targetNode.cer"


                # The thumbprint of the Encryption Certificate
                # used to decrypt the credentials on target node
                Thumbprint = "AC23EA3A9E291A75757A556D0B71CBBF8C4F6FD8"
            };
        );
    }
```

## <a name="configuration-script"></a>Konfigurationsskript

I konfigurationsskript själva använder den `PsCredential` parametern för att se till att autentiseringsuppgifterna lagras för på kortast möjliga tid. När du kör det angivna exemplet DSC efterfrågar autentiseringsuppgifter och kryptera MOF-filen med hjälp av CertificateFile som är associerad med målnoden i datablocket konfiguration. Det här kodexemplet kopierar en fil från en resurs som skyddas till en användare.

```powershell
configuration CredentialEncryptionExample
{
    param(
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [PsCredential] $credential
        )


    Node $AllNodes.NodeName
    {
        File exampleFile
        {
            SourcePath = "\\Server\share\path\file.ext"
            DestinationPath = "C:\destinationPath"
            Credential = $credential
        }
    }
}
```

## <a name="setting-up-decryption"></a>Konfigurera dekryptering

Innan du [ `Start-DscConfiguration` ](https://technet.microsoft.com/library/dn521623.aspx) kan fungera, måste du ange den lokala Konfigurationshanteraren på varje målnoden vilket certifikat som ska använda för att dekryptera autentiseringsuppgifterna, med CertificateID resursen för att verifiera certifikatets tumavtryck. Den här funktionen för exemplet hittar lämpliga lokala certifikatet (du kan behöva anpassa den så hittar du det exakta certifikatet som du vill använda):

```powershell
# Get the certificate that works for encryption
function Get-LocalEncryptionCertificateThumbprint
{
    (dir Cert:\LocalMachine\my) | %{
        # Verify the certificate is for Encryption and valid
        if ($_.PrivateKey.KeyExchangeAlgorithm -and $_.Verify())
        {
            return $_.Thumbprint
        }
    }
}
```

Skript för konfiguration kan uppdateras för att använda värdet med det certifikat som identifieras av dess tumavtryck:

```powershell
configuration CredentialEncryptionExample
{
    param(
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [PsCredential] $credential
        )


    Node $AllNodes.NodeName
    {
        File exampleFile
        {
            SourcePath = "\\Server\share\path\file.ext"
            DestinationPath = "C:\destinationPath"
            Credential = $credential
        }

        LocalConfigurationManager
        {
             CertificateId = $node.Thumbprint
        }
    }
}
```

## <a name="running-the-configuration"></a>Kör konfigurationen

Du kan nu köra konfiguration, som ska skapa två filer:

- A *. meta.mof-fil som konfigurerar den lokala Konfigurationshanteraren för att dekryptera autentiseringsuppgifterna med det certifikat som lagras på lokala datorns Arkiv och identifieras av dess tumavtryck. [`Set-DscLocalConfigurationManager`](https://technet.microsoft.com/library/dn521621.aspx) gäller den *. meta.mof fil.
- En MOF-fil som faktiskt gäller konfigurationen av. Start-DscConfiguration gäller konfigurationen av.

Dessa kommandon kan utföra de här stegen:

```powershell
Write-Host "Generate DSC Configuration..."
CredentialEncryptionExample -ConfigurationData $ConfigData -OutputPath .\CredentialEncryptionExample

Write-Host "Setting up LCM to decrypt credentials..."
Set-DscLocalConfigurationManager .\CredentialEncryptionExample -Verbose

Write-Host "Starting Configuration..."
Start-DscConfiguration .\CredentialEncryptionExample -wait -Verbose
```

Det här exemplet skickar DSC-konfigurationen till målnoden.
DSC-konfiguration kan också användas med hjälp av en DSC-Hämtningsserver om någon är tillgänglig.

Se [konfigurera en DSC-pullklient](pullClient.md) för mer information om hur du använder DSC-konfigurationer med en DSC-Hämtningsservern.

## <a name="credential-encryption-module-example"></a>Autentiseringsuppgifter kryptering modulen exempel

Här är ett fullständigt exempel som omfattar alla de här stegen, plus en helper-cmdlet som exporterar och kopierar de offentliga nycklarna:

```powershell
# A simple example of using credentials
configuration CredentialEncryptionExample
{
    param(
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [PsCredential] $credential
        )


    Node $AllNodes.NodeName
    {
        File exampleFile
        {
            SourcePath = "\\server\share\file.txt"
            DestinationPath = "C:\Users\user"
            Credential = $credential
        }

        LocalConfigurationManager
        {
            CertificateId = $node.Thumbprint
        }
    }
}

# A Helper to invoke the configuration, with the correct public key
# To encrypt the configuration credentials
function Start-CredentialEncryptionExample
{
    [CmdletBinding()]
    param ($computerName)


    [string] $thumbprint = Get-EncryptionCertificate -computerName $computerName -Verbose
    Write-Verbose "using cert: $thumbprint"

    $certificatePath = join-path -Path "$env:SystemDrive\$script:publicKeyFolder" -childPath "$computername.EncryptionCertificate.cer"

    $ConfigData=    @{
        AllNodes = @(
                        @{
                            # The name of the node we are describing
                            NodeName = "$computerName"

                            # The path to the .cer file containing the
                            # public key of the Encryption Certificate
                            CertificateFile = "$certificatePath"

                            # The thumbprint of the Encryption Certificate
                            # used to decrypt the credentials
                            Thumbprint = $thumbprint
                        };
                    );
    }

    Write-Verbose "Generate DSC Configuration..."
    CredentialEncryptionExample -ConfigurationData $ConfigData -OutputPath .\CredentialEncryptionExample `
        -credential (Get-Credential -UserName "$env:USERDOMAIN\$env:USERNAME" -Message "Enter credentials for configuration")

    Write-Verbose "Setting up LCM to decrypt credentials..."
    Set-DscLocalConfigurationManager .\CredentialEncryptionExample -Verbose

    Write-Verbose "Starting Configuration..."
    Start-DscConfiguration .\CredentialEncryptionExample -wait -Verbose

}


#region HelperFunctions

# The folder name for the exported public keys
$script:publicKeyFolder = "publicKeys"

# Get the certificate that works for encryptions
function Get-EncryptionCertificate
{
    [CmdletBinding()]
    param ($computerName)
    $returnValue= Invoke-Command -ComputerName $computerName -ScriptBlock {
            $certificates = dir Cert:\LocalMachine\my

            $certificates | %{
                    # Verify the certificate is for Encryption and valid
                    if ($_.PrivateKey.KeyExchangeAlgorithm -and $_.Verify())
                    {
                        # Create the folder to hold the exported public key
                        $folder= Join-Path -Path $env:SystemDrive\ -ChildPath $using:publicKeyFolder
                        if (! (Test-Path $folder))
                        {
                            md $folder | Out-Null
                        }

                        # Export the public key to a well known location
                        $certPath = Export-Certificate -Cert $_ -FilePath (Join-Path -path $folder -childPath "EncryptionCertificate.cer")

                        # Return the thumbprint, and exported certificate path
                        return @($_.Thumbprint,$certPath);
                    }
                  }
        }
    Write-Verbose "Identified and exported cert..."
    # Copy the exported certificate locally
    $destinationPath = join-path -Path "$env:SystemDrive\$script:publicKeyFolder" -childPath "$computername.EncryptionCertificate.cer"
    Copy-Item -Path (join-path -path \\$computername -childPath $returnValue[1].FullName.Replace(":","$"))  $destinationPath | Out-Null

    # Return the thumbprint
    return $returnValue[0]
}

Start-CredentialEncryptionExample
```
