---
ms.date: 2017-10-31
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: Skydda MOF-filen
ms.openlocfilehash: fdb8fa17e9b5e92b56e0a62bf850529c241eee41
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/17/2018
---
# <a name="securing-the-mof-file"></a>Skydda MOF-filen

>Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0

DSC hanterar konfigurationen av servernoder genom att använda informationen i en MOF-fil där den lokala Configuration Manager (MGM) implementerar tillståndet önskade resultatet.
Eftersom den här filen innehåller information om konfigurationen, är det viktigt att skydda den.
Det här avsnittet beskriver hur du målnoden har krypterade filen.

Från och med PowerShell version 5.0, hela MOF-filen är krypterad som standard när den används på en nod med hjälp av den **Start DSCConfiguration** cmdlet.
Processen som beskrivs i den här artikeln krävs bara när du implementerar en lösning med pull-tjänsten-protokollet om certifikat inte som hanteras så konfigurationer som hämtas av målnoden kan dekryptera och läsa av systemet innan de tillämpas (till exempel pull tjänsten finns i Windows Server).
Noder registrerad [Azure Automation DSC](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview) automatiskt har certifikat installerat och hanteras av tjänsten med inga administrativa kostnader krävs.

>**Obs:** det här avsnittet beskrivs certifikat som används för kryptering.
>Ett självsignerat certifikat är tillräcklig för kryptering, eftersom den privata nyckeln sparas alltid hemlighet och kryptering innebär inte förtroende för dokumentet.
>Självsignerade certifikat bör *inte* ska användas för autentisering.
>Du bör använda ett certifikat från en betrodd certifikatutfärdare (CA) för andra syften för autentisering.

## <a name="prerequisites"></a>Förutsättningar

För att kryptera har de autentiseringsuppgifter som används för att skydda en DSC-konfiguration, kontrollera att du har följande:

* **Vissa sätt för att utfärda och distribuera certifikat**. Det här avsnittet och dess exempel förutsätter att du använder Active Directory-certifikatutfärdare. Mer bakgrundsinformation om Active Directory Certificate Services finns i avsnittet [Active Directory Certificate Services översikt](https://technet.microsoft.com/library/hh831740.aspx) och [Active Directory-certifikattjänster i Windows Server 2008](https://technet.microsoft.com/windowsserver/dd448615.aspx).
* **Administrativ åtkomst till målnoden eller noder**.
* **Varje målnoden har kryptering-kompatibla certifikat sparade personliga arkivet**. Sökvägen till arkivet är i Windows PowerShell-Cert: \LocalMachine\My. Exemplen i det här avsnittet använder mallen ”autentisering av arbetsstation”, som du kan hitta (tillsammans med andra certifikatmallar) på [Standardcertifikatmallar](https://technet.microsoft.com/library/cc740061(v=WS.10).aspx).
* Om du ska köra den här konfigurationen på en annan dator än målnoden **exportera den offentliga nyckeln för certifikatet**, och sedan importera den till den dator som du vill köra konfigurationen från. Kontrollera att du exporterar endast den **offentliga** nyckeln; skydda den privata nyckeln.

## <a name="overall-process"></a>Övergripande processen

 1. Konfigurera certifikat, nycklar och tumavtryck, se till att varje målnoden har kopior av certifikat och konfiguration av datorn har den offentliga nyckeln och tumavtrycket.
 2. Skapa ett configuration datablock som innehåller sökvägen och tumavtrycket för den offentliga nyckeln.
 3. Skapa ett konfigurationsskript som definierar konfigurationen för målnoden och ställer in dekryptering på målnoder av drar till sig den lokala Configuration manager för att dekryptera konfigurationsdata med hjälp av certifikatet och dess tumavtryck.
 4. Kör sedan konfigurationen, vilket anger Local Configuration Manager-inställningar och starta DSC-konfigurationen.

![Diagram1](images/CredentialEncryptionDiagram1.png)

## <a name="certificate-requirements"></a>Certifikatkrav

Certifikatets offentliga nyckel för att du tillämpar kryptering av autentiseringsuppgifter måste vara tillgängligt på den _målnoden_ som **betrodda** för datorn som används för att skapa DSC-konfigurationen.
Den här offentliga nyckelcertifikat har särskilda krav för att användas för kryptering av DSC-autentiseringsuppgifter:
 1. **Nyckelanvändning**:
   - Måste innehålla: 'KeyEncipherment' och 'DataEncipherment'.
   - Ska _inte_ innehålla: ”Digital signatur”.
 2. **Utökad nyckelanvändning**:
   - Måste innehålla: dokumentkryptering (1.3.6.1.4.1.311.80.1).
   - Ska _inte_ innehålla: klientautentisering (1.3.6.1.5.5.7.3.2) och serverautentisering (1.3.6.1.5.5.7.3.1).
 3. Den privata nyckeln för certifikatet är tillgängligt på den * mål Node_.
 4. Den **Provider** för certifikatet måste vara ”Microsoft RSA SChannel kryptografiprovider”.
 
>**Rekommenderad praxis:** men du kan använda ett certifikat med som innehåller en nyckelanvändning i ”Digital signatur” eller något av Nyckelanvändning för klientautentisering, detta aktiverar krypteringsnyckeln ska vara enklare felanvända och sårbar för angrepp. Det är därför bäst att använda ett certifikat som skapats specifikt för att skydda DSC-autentiseringsuppgifter som utesluter dessa nyckelanvändning och EKU.
  
Alla befintliga certifikat på den _målnoden_ som uppfyller dessa villkor kan användas för att säkra DSC-referenser.

## <a name="certificate-creation"></a>Skapande av certifikat

Det finns två metoder som du kan använda för att skapa och använda nödvändiga krypteringscertifikat (privat-offentligt nyckelpar).

1. Skapa den på den **målnoden** och exportera den offentliga nyckeln till den **redigering nod**
2. Skapa den på den **redigering nod** och exportera hela nyckelparet till den **målnod**

Metod 1 rekommenderas eftersom den privata nyckeln används för att dekryptera autentiseringsuppgifterna i MOF finns kvar på målnoden vid alla tidpunkter.


### <a name="creating-the-certificate-on-the-target-node"></a>Skapa certifikatet på målnoden

Den privata nyckeln måste hållas hemliga eftersom används för att dekryptera MOF på den **målnoden** det enklaste sättet att göra det är att skapa certifikat för privata nyckel på den **målnoden**, och kopierar den  **Certifikatets offentliga nyckel** på datorn som används för att skapa DSC-konfigurationen till en MOF-fil.
I följande exempel:
 1. skapar ett certifikat på den **målnod**
 2. exporterar det offentliga nyckelcertifikatet på den **målnoden**.
 3. importerar det offentliga nyckelcertifikatet till den **min** certifikatarkivet på den **redigering nod**.

#### <a name="on-the-target-node-create-and-export-the-certificate"></a>På målnoden: skapa och exportera certifikatet
>Målnoden: Windows Server 2016 och Windows 10

```powershell
# note: These steps need to be performed in an Administrator PowerShell session
$cert = New-SelfSignedCertificate -Type DocumentEncryptionCertLegacyCsp -DnsName 'DscEncryptionCert' -HashAlgorithm SHA256
# export the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
```
En gång exporterade den ```DscPublicKey.cer``` måste kopieras till den **redigering nod**.

>Målnoden: Windows Server 2012 R2/Windows 8.1 och tidigare

Eftersom cmdlet New-SelfSignedCertificate på Windows-operativsystem före Windows 10 och Windows Server 2016 inte stöder den **typen** parameter, en alternativ metod för att skapa det här certifikatet måste finnas på dessa operativsystem.
I det här fallet kan du använda ```makecert.exe``` eller ```certutil.exe``` att skapa certifikatet.

En alternativ metod är att [hämta ny SelfSignedCertificateEx.ps1 skriptet från Microsoft Script Center](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) och använda den för att skapa certifikatet i stället:
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
$Cert = Get-ChildItem -Path cert:\LocalMachine\My `
    | Where-Object {
        ($_.FriendlyName -eq 'DSC Credential Encryption certificate') `
        -and ($_.Subject -eq "CN=${ENV:ComputerName}")
    } | Select-Object -First 1
# export the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
```
En gång exporterade den ```DscPublicKey.cer``` måste kopieras till den **redigering nod**.

#### <a name="on-the-authoring-node-import-the-certs-public-key"></a>På noden redigering: importera på certifikatets offentliga nyckel
```powershell
# Import to the my store
Import-Certificate -FilePath "$env:temp\DscPublicKey.cer" -CertStoreLocation Cert:\LocalMachine\My
```

### <a name="creating-the-certificate-on-the-authoring-node"></a>Skapa certifikatet på noden redigering
Alternativt kan krypteringscertifikat kan skapas på den **redigering nod**, exporterade med den **privat nyckel** som en PFX-fil och sedan importeras på den **målnoden**.
Detta är den aktuella metoden för att implementera kryptering av DSC-autentiseringsuppgifter på _Nano Server_.
Även om den PFX-filen är skyddad med ett lösenord bör den hållas säkra under överföringen.
I följande exempel:
 1. skapar ett certifikat på den **redigering nod**.
 2. exporterar certifikatet inklusive den privata nyckeln på den **redigering nod**.
 3. tar bort den privata nyckeln från den **redigering nod**, men behåller det offentliga nyckelcertifikatet i den **min** lagras.
 4. importerar privata nyckel certifikatet till rotarkivet certifikat på den **målnoden**.
   - den måste läggas till rotarkivet så att det ska vara betrott av den **målnoden**.

#### <a name="on-the-authoring-node-create-and-export-the-certificate"></a>På noden redigering: skapa och exportera certifikatet
>Målnoden: Windows Server 2016 och Windows 10

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
En gång exporterade den ```DscPrivateKey.pfx``` måste kopieras till den **målnoden**.

>Målnoden: Windows Server 2012 R2/Windows 8.1 och tidigare

Eftersom cmdlet New-SelfSignedCertificate på Windows-operativsystem före Windows 10 och Windows Server 2016 inte stöder den **typen** parameter, en alternativ metod för att skapa det här certifikatet måste finnas på dessa operativsystem.
I det här fallet kan du använda ```makecert.exe``` eller ```certutil.exe``` att skapa certifikatet.

En alternativ metod är att [hämta ny SelfSignedCertificateEx.ps1 skriptet från Microsoft Script Center](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) och använda den för att skapa certifikatet i stället:
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
$Cert = Get-ChildItem -Path cert:\LocalMachine\My `
    | Where-Object {
        ($_.FriendlyName -eq 'DSC Credential Encryption certificate') `
        -and ($_.Subject -eq "CN=${ENV:ComputerName}")
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

Datablock konfigurationen definierar vilka målnoder ska fungera på om eller inte för att kryptera autentiseringsuppgifterna för kryptering och annan information. Mer information om konfiguration datablock finns [avgränsa konfiguration och miljödata](configData.md).

Element som kan konfigureras för varje nod som är relaterade till autentiseringsuppgifter kryptering är:
* **Nodnamn** -namnet på målnoden kryptering av autentiseringsuppgifter konfigureras för.
* **PsDscAllowPlainTextPassword** – oavsett om okrypterad autentiseringsuppgifter kan skickas till den här noden. Detta är **bör inte**.
* **Tumavtryck för** -tumavtrycket för certifikatet som används för att dekryptera autentiseringsuppgifterna i DSC-konfigurationen på den _målnoden_. **Det här certifikatet måste finnas i lokala datorns certifikatarkiv på målnoden.**
* **CertificateFile** - certifikatfilen (som innehåller den offentliga nyckeln) som ska användas för att kryptera autentiseringsuppgifterna för den _målnoden_. Det här måste vara antingen en DER-kodad binärfil X.509 eller Base64-kodat X.509-format-certifikatfil.

Det här exemplet illustrerar en konfiguration datablock som anger en målnoden för att fungera på namngiven targetNode, sökvägen till filen certifikat med offentlig nyckel (som kallas targetNode.cer) och tumavtrycket för den offentliga nyckeln.

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

I konfigurationsskript själva använder den `PsCredential` parametern för att se till att autentiseringsuppgifterna lagras för på kortast möjliga tid. När du kör det angivna exemplet DSC efterfrågar autentiseringsuppgifter och kryptera MOF-filen med hjälp av CertificateFile som är kopplad till målnoden i datablock konfiguration. Det här kodexemplet kopierar en fil från en resurs som skyddas till en användare.

```
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

Innan du [ `Start-DscConfiguration` ](https://technet.microsoft.com/en-us/library/dn521623.aspx) kan fungera, måste du ange Local Configuration Manager på varje målnoden vilket certifikat som ska använda för att dekryptera autentiseringsuppgifterna resursnamnet CertificateID för att verifiera certifikatets tumavtryck. Den här funktionen exempel hittar lokala intyg (du kan behöva anpassa den så att den ska hitta exakt certifikatet som du vill använda):

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

Skriptet konfiguration kan uppdateras för att använda värdet med det certifikat som identifieras av dess tumavtryck:

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

Du kan nu köra konfiguration, som kommer att skapa två filer:

 * A *. meta.mof-fil som konfigurerar den lokala Configuration Manager för att dekryptera autentiseringsuppgifterna med det certifikat som lagras på lokala datorns Arkiv och identifieras av dess tumavtryck. [`Set-DscLocalConfigurationManager`](https://technet.microsoft.com/en-us/library/dn521621.aspx)gäller de *. meta.mof fil.
 * En MOF-fil som faktiskt gäller konfigurationen av. Start-DscConfiguration gäller konfigurationen av.

Dessa kommandon kan utföra dessa steg:

```powershell
Write-Host "Generate DSC Configuration..."
CredentialEncryptionExample -ConfigurationData $ConfigData -OutputPath .\CredentialEncryptionExample

Write-Host "Setting up LCM to decrypt credentials..."
Set-DscLocalConfigurationManager .\CredentialEncryptionExample -Verbose 
 
Write-Host "Starting Configuration..."
Start-DscConfiguration .\CredentialEncryptionExample -wait -Verbose
```

Det här exemplet skulle skicka DSC-konfigurationen till målnoden.
DSC-konfigurationen kan också användas med en DSC Pull-Server om det inte finns.

Se [installera en klient för DSC-pull](pullClient.md) för mer information om hur du använder DSC-konfigurationer som använder en DSC Pull-Server.

## <a name="credential-encryption-module-example"></a>Autentiseringsuppgifter kryptering modulen exempel

Här är ett fullständigt exempel som omfattar alla de här stegen plus en helper-cmdlet som exporterar och kopierar de offentliga nycklarna:

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

