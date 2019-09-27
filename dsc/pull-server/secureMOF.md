---
ms.date: 10/31/2017
keywords: DSC, PowerShell, konfiguration, installation
title: Skydda MOF-filen
ms.openlocfilehash: 4ca540303cb740ac602bce181e0e446efcd16b6e
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71324887"
---
# <a name="securing-the-mof-file"></a>Skydda MOF-filen

> Gäller för: Windows PowerShell 4,0, Windows PowerShell 5,0

DSC hanterar konfigurationen av serverklusternoder genom att använda information som lagras i en MOF-fil, där den lokala Configuration Manager (LCM) implementerar det önskade slut läget.
Eftersom den här filen innehåller information om konfigurationen är det viktigt att skydda den.
I det här avsnittet beskrivs hur du ser till att målnoden har krypterat filen.

Från och med PowerShell version 5,0 krypteras hela MOF-filen som standard när den tillämpas på noden med hjälp `Start-DSCConfiguration` av cmdleten.
Processen som beskrivs i den här artikeln krävs bara när du implementerar en lösning med hjälp av protokollet för pull-protokollet om certifikat inte hanteras, för att se till att konfigurationer som hämtas av målnoden kan dekrypteras och läsas av systemet innan de tillämpas (till exempel den pull-tjänst som är tillgänglig i Windows Server).
Noder som är registrerade för [Azure Automation DSC](https://docs.microsoft.com/azure/automation/automation-dsc-overview) har automatiskt certifikat som installeras och hanteras av tjänsten utan att det krävs någon administrativ omkostnader.

> [!NOTE]
> I det här avsnittet beskrivs certifikat som används för kryptering.
> För kryptering räcker ett självsignerat certifikat, eftersom den privata nyckeln alltid hålls hemlig och kryptering innebär inte att dokumentet är tillförlitligt.
> Självsignerade certifikat bör *inte* användas för autentisering.
> Du bör använda ett certifikat från en betrodd certifikat utfärdare (CA) i alla autentiserings syfte.

## <a name="prerequisites"></a>Förutsättningar

Kontrol lera att du har följande för att kunna kryptera de autentiseringsuppgifter som används för att skydda en DSC-konfiguration:

- **Några sätt att utfärda och distribuera certifikat**. I det här avsnittet och dess exempel förutsätter vi att du använder Active Directory certifikat utfärdare. Mer bakgrunds information om Active Directory Certificate Services finns i [Översikt över Active Directory Certificate Services](https://technet.microsoft.com/library/hh831740.aspx) och [Active Directory Certificate Services i Windows Server 2008](https://technet.microsoft.com/windowsserver/dd448615.aspx).
- **Administrativ åtkomst till målnoden eller noder**.
- **Varje målnod har ett krypterat certifikat som har sparats i det personliga arkivet**. I Windows PowerShell är sökvägen till arkivet certifikat: \ LocalMachine\My. I exemplen i det här avsnittet används mallen "arbetsstations autentisering", som du hittar (tillsammans med andra certifikatmallar) på [standardmallarna för certifikat](https://technet.microsoft.com/library/cc740061(v=WS.10).aspx).
- Om du kommer att köra den här konfigurationen på en annan dator än målnoden, **Exportera den offentliga nyckeln för certifikatet**och sedan importera den till datorn som du ska köra konfigurationen från. Se till att du endast exporterar den **offentliga** nyckeln. skydda den privata nyckeln.

## <a name="overall-process"></a>Övergripande process

 1. Konfigurera certifikat, nycklar och tumavtrycken och se till att varje målnod har kopior av certifikatet och att konfigurations datorn har den offentliga nyckeln och tumavtryck.
 2. Skapa ett konfigurations data block som innehåller sökvägen och tumavtrycket för den offentliga nyckeln.
 3. Skapa ett konfigurations skript som definierar den önskade konfigurationen för målnoden och ställer in dekryptering på målnoden genom att använda den lokala Konfigurations hanteraren för att dekryptera konfigurations data med hjälp av certifikatet och dess tumavtryck.
 4. Kör konfigurationen, som anger de lokala Configuration Manager inställningarna och startar DSC-konfigurationen.

![Diagram1](../images/CredentialEncryptionDiagram1.png)

## <a name="certificate-requirements"></a>Certifikat krav

För att anta kryptering av autentiseringsuppgifter måste ett offentligt nyckel certifikat vara tillgängligt på den _målnod_ som är **betrodd** av den dator som används för att redigera DSC-konfigurationen.
Det här certifikatet för den offentliga nyckeln har särskilda krav för att det ska kunna användas för kryptering av DSC-autentiseringsuppgifter:

1. **Nyckel användning**:
   - Måste innehålla: ' KeyEncipherment ' och ' DataEncipherment '.
   - Får _inte_ innehålla: Digital signatur.
2. **Förbättrad nyckel användning**:
   - Måste innehålla: Dokument kryptering (1.3.6.1.4.1.311.80.1).
   - Får _inte_ innehålla: Klientautentisering (1.3.6.1.5.5.7.3.2) och serverautentisering (1.3.6.1.5.5.7.3.1).
3. Den privata nyckeln för certifikatet finns på * Target-Node_.
4. **Providern** för certifikatet måste vara "Microsoft RSA SChannel Cryptographic Provider".

> [!IMPORTANT]
> Även om du kan använda ett certifikat med en nyckel användning av "Digital Signature" eller en av EKU för autentisering, så gör detta att krypterings nyckeln blir enklare att använda och sårbar för angrepp. Vi rekommenderar att du använder ett certifikat som har skapats specifikt för att skydda DSC-autentiseringsuppgifter som utesluter denna nyckel användning och EKU.

Alla befintliga certifikat på _målnoden_ som uppfyller dessa villkor kan användas för att skydda DSC-autentiseringsuppgifter.

## <a name="certificate-creation"></a>Skapa certifikat

Det finns två sätt som du kan vidta för att skapa och använda det krypterings certifikat som krävs (offentligt-privat nyckel par).

1. Skapa den på **målnoden** och exportera bara den offentliga nyckeln till **redigerings noden**
2. Skapa den på **noden redigering** och exportera hela nyckel paret till **målnoden**

Metod 1 rekommenderas eftersom den privata nyckel som används för att dekryptera autentiseringsuppgifter i MOF kvar på målnoden.

### <a name="creating-the-certificate-on-the-target-node"></a>Skapar certifikatet på målnoden

Den privata nyckeln måste hållas hemlig, eftersom används för att dekryptera MOF på **målnoden det enklaste** sättet att göra det är att skapa certifikatet för den privata nyckeln på **målnoden**och kopiera det **offentliga nyckel certifikatet** till den dator som används för att redigera DSC-konfigurationen i en MOF-fil.
Följande exempel:

1. skapar ett certifikat på **målnoden**
2. exporterar certifikatet för den offentliga nyckeln på **målnoden**.
3. importerar certifikatet för den offentliga nyckeln till **mitt** certifikat Arkiv på **noden redigering**.

#### <a name="on-the-target-node-create-and-export-the-certificate"></a>På målnoden: skapa och exportera certifikatet

> Målnod: Windows Server 2016 och Windows 10

```powershell
# note: These steps need to be performed in an Administrator PowerShell session
$cert = New-SelfSignedCertificate -Type DocumentEncryptionCertLegacyCsp -DnsName 'DscEncryptionCert' -HashAlgorithm SHA256
# export the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
```

När du har exporterat måste du kopiera den `DscPublicKey.cer` till redigerings- **noden**.

> Målnod: Windows Server 2012 R2/Windows 8,1 och tidigare
> [!WARNING]
> Eftersom cmdleten på Windows-operativsystem före Windows 10 och Windows Server 2016 inte stöder typ parametern, krävs en alternativ metod för att skapa det här certifikatet på dessa operativ system. `New-SelfSignedCertificate`
>
> I det här fallet kan du `makecert.exe` använda `certutil.exe` eller för att skapa certifikatet.
>
>En alternativ metod är att [Hämta skriptet New-SelfSignedCertificateEx. ps1 från Microsoft Script Center](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) och använda det för att skapa certifikatet i stället:

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

När du har exporterat måste du kopiera den ```DscPublicKey.cer``` till redigerings- **noden**.

#### <a name="on-the-authoring-node-import-the-certs-public-key"></a>På noden redigering: importera certifikatets offentliga nyckel

```powershell
# Import to the my store
Import-Certificate -FilePath "$env:temp\DscPublicKey.cer" -CertStoreLocation Cert:\LocalMachine\My
```

### <a name="creating-the-certificate-on-the-authoring-node"></a>Skapa certifikatet på noden redigering

Alternativt kan du skapa krypterings certifikatet på **noden redigering**, som exporteras med den **privata nyckeln** som en PFX-fil och sedan importeras på **målnoden**.
Det här är den aktuella metoden för att implementera kryptering av DSC-autentiseringsuppgifter på _Nano Server_.
Även om PFX är skyddat med ett lösen ord bör det hållas säkert under överföringen.
Följande exempel:

1. skapar ett certifikat på **noden redigering**.
2. exporterar certifikatet inklusive den privata nyckeln på **noden redigering**.
3. tar bort den privata nyckeln från **redigerings noden**, men behåller certifikatet för den offentliga nyckeln i **My** Store.
4. importerar det privata nyckel certifikatet till certifikat arkivet My (personal) på **målnoden**.
   - den måste läggas till i rot arkivet så att den är betrodd av **målnoden**.

#### <a name="on-the-authoring-node-create-and-export-the-certificate"></a>På noden redigering: skapa och exportera certifikatet

> Målnod: Windows Server 2016 och Windows 10

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

När du har exporterat måste du kopiera den `DscPrivateKey.pfx` till **målnoden**.

> Målnod: Windows Server 2012 R2/Windows 8,1 och tidigare
> [!WARNING]
> Eftersom cmdleten på Windows-operativsystem före Windows 10 och Windows Server 2016 inte stöder typ parametern, krävs en alternativ metod för att skapa det här certifikatet på dessa operativ system. `New-SelfSignedCertificate`
>
> I det här fallet kan du `makecert.exe` använda `certutil.exe` eller för att skapa certifikatet.
>
> En alternativ metod är att [Hämta skriptet New-SelfSignedCertificateEx. ps1 från Microsoft Script Center](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) och använda det för att skapa certifikatet i stället:

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

#### <a name="on-the-target-node-import-the-certs-private-key-as-a-trusted-root"></a>På målnoden: importera certifikatets privata nyckel som en betrodd rot

```powershell
# Import to the root store so that it is trusted
$mypwd = ConvertTo-SecureString -String "YOUR_PFX_PASSWD" -Force -AsPlainText
Import-PfxCertificate -FilePath "$env:temp\DscPrivateKey.pfx" -CertStoreLocation Cert:\LocalMachine\My -Password $mypwd > $null
```

## <a name="configuration-data"></a>Konfigurationsdata

Konfigurations data blocket definierar vilka mål noder som ska användas, om du vill kryptera autentiseringsuppgifterna, krypterings metoder och annan information. Mer information om konfigurations data blocket finns i [avgränsa konfigurations-och miljö data](../configurations/configData.md).

De element som kan konfigureras för varje nod som är relaterade till kryptering av autentiseringsuppgifter är:

- **Nodnamn** -namnet på den målnod som kryptering av autentiseringsuppgifter konfigureras för.
- **PsDscAllowPlainTextPassword** – anger om okrypterade autentiseringsuppgifter ska kunna skickas till den här noden. Detta **rekommenderas inte**.
- **Tumavtryck** -tumavtrycket för det certifikat som ska användas för att dekryptera AUTENTISERINGSUPPGIFTERNA i DSC-konfigurationen på _målnoden_. **Det här certifikatet måste finnas i den lokala datorns certifikat Arkiv på målnoden.**
- **CertificateFile** – certifikat filen (som endast innehåller den offentliga nyckeln) som ska användas för att kryptera autentiseringsuppgifterna för _målnoden_. Måste vara antingen en DER-kodad binär X. 509-eller Base-64-kodad X. 509-format certifikat fil.

Det här exemplet visar ett konfigurations data block som anger en målnod som agerar på namngivna targetNode, sökvägen till certifikat filen för offentlig nyckel (med namnet targetNode. cer) och tumavtrycket för den offentliga nyckeln.

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

## <a name="configuration-script"></a>Konfigurations skript

I själva konfigurations skriptet använder du `PsCredential` parametern för att se till att autentiseringsuppgifterna lagras på kortast möjliga tid. När du kör det angivna exemplet uppmanas du att ange autentiseringsuppgifter för DSC och sedan kryptera MOF-filen med hjälp av den CertificateFile som är kopplad till målnoden i konfigurations data blocket. I det här kod exemplet kopieras en fil från en resurs som är skyddad till en användare.

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

Innan [`Start-DscConfiguration`](https://technet.microsoft.com/library/dn521623.aspx) kan fungera måste du ange den lokala Configuration Manager på varje målnod som certifikatet ska använda för att dekryptera autentiseringsuppgifterna, med hjälp av CertificateID-resursen för att verifiera certifikatets tumavtryck. Den här exempel funktionen hittar lämpligt lokalt certifikat (du kanske måste anpassa det så att det hittar det exakta certifikat som du vill använda):

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

Med certifikatet som identifieras av sitt tumavtryck kan konfigurations skriptet uppdateras för att använda värdet:

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

## <a name="running-the-configuration"></a>Köra konfigurationen

I det här läget kan du köra konfigurationen, som kommer att skriva ut två filer:

- En *. meta. MOF-fil som konfigurerar den lokala Configuration Manager för att dekryptera autentiseringsuppgifterna med hjälp av det certifikat som lagras i den lokala datorns Arkiv och identifieras av dess tumavtryck. [`Set-DscLocalConfigurationManager`](https://technet.microsoft.com/library/dn521621.aspx)använder *. meta. MOF-filen.
- En MOF-fil som faktiskt tillämpar konfigurationen. Start-DscConfiguration tillämpar konfigurationen.

Dessa kommandon utför dessa steg:

```powershell
Write-Host "Generate DSC Configuration..."
CredentialEncryptionExample -ConfigurationData $ConfigData -OutputPath .\CredentialEncryptionExample

Write-Host "Setting up LCM to decrypt credentials..."
Set-DscLocalConfigurationManager .\CredentialEncryptionExample -Verbose

Write-Host "Starting Configuration..."
Start-DscConfiguration .\CredentialEncryptionExample -wait -Verbose
```

I det här exemplet pushar DSC-konfigurationen till målnoden.
DSC-konfigurationen kan också användas med en DSC-pull-server om en sådan finns tillgänglig.

Mer information om hur du använder DSC-konfigurationer med en DSC-pull-server finns i [Konfigurera en DSC-pull-klient](pullClient.md) .

## <a name="credential-encryption-module-example"></a>Modul för kryptering av autentiseringsuppgifter

Här är ett fullständigt exempel som införlivar alla dessa steg, plus en hjälp-cmdlet som exporterar och kopierar offentliga nycklar:

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
