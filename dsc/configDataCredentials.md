---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: "Alternativ för autentiseringsuppgifter i konfigurationsdata"
ms.openlocfilehash: 94ff541fc517254ef2876c424307513eaf1d362a
ms.sourcegitcommit: 28e71b0ae868014523631fec3f5417de751944f3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/25/2017
---
# <a name="credentials-options-in-configuration-data"></a>Alternativ för autentiseringsuppgifter i konfigurationsdata
>Gäller för: Windows PowerShell 5.0

## <a name="plain-text-passwords-and-domain-users"></a>Lösenord i klartext och domänanvändare

DSC-konfigurationer som innehåller en autentiseringsuppgift utan kryptering genererar ett felmeddelande om lösenord i klartext.
Dessutom genererar DSC en varning när du använder autentiseringsuppgifter för domänen.
Använd nyckelorden DSC-konfiguration data för att ignorera dessa fel och varningar:
* **PsDscAllowPlainTextPassword**
* **PsDscAllowDomainUser**

>**Kommentarer:** <p>Lagra/överföring av okrypterade lösenord i klartext är inte säker. Du rekommenderas att säkra autentiseringsuppgifter genom att använda de tekniker som beskrivs senare i det här avsnittet.</p> <p>Tjänsten Azure Automation DSC kan du centralt hantera autentiseringsuppgifter som ska kompileras i konfigurationer och lagras på ett säkert sätt.  Mer information finns i: [kompilering av DSC-konfigurationer / Inloggningstillgångar](https://docs.microsoft.com/en-in/azure/automation/automation-dsc-compile#credential-assets)</p>

Följande är ett exempel på att skicka autentiseringsuppgifter med oformaterad text:

```powershell
#Prompt user for their credentials
#credentials will be unencrypted in the MOF
$promptedCreds = get-credential -Message "Please enter your credentials to generate a DSC MOF:"

# Store passwords in plaintext, in the document itself
# will also be stored in plaintext in the mof
$password = "ThisIsAPlaintextPassword" | ConvertTo-SecureString -asPlainText -Force
$username = "User1"
[PSCredential] $credential = New-Object System.Management.Automation.PSCredential($username,$password)

# DSC requires explicit confirmation before storing passwords insecurely
$ConfigurationData = @{
    AllNodes = @(
        @{
            # The "*" means "all nodes named in ConfigData" so we don't have to repeat ourselves
            NodeName="*"
            PSDscAllowPlainTextPassword = $true
        },
        #however, each node still needs to be explicitly defined for "*" to have meaning
        @{
            NodeName = "TestMachine1"
        },
        #we can also use a property to define node-specific passwords, although this is no more secure
        @{
            NodeName = "TestMachine2";
            UserName = "User2"
            LocalPassword = "ThisIsYetAnotherPlaintextPassword"
        }
        )
}
configuration unencryptedPasswordDemo
{
    Node "TestMachine1"
    {
        # We use the plaintext password to generate a new account
        User User1
        {
            UserName = $username
            Password = $credential
            Description = "local account"
            Ensure = "Present"
            Disabled = $false
            PasswordNeverExpires = $true
            PasswordChangeRequired = $false
        }
        # We use the prompted password to add this account to the local admins group
        Group addToAdmin
        {
            # Ensure the user exists before we add the user to a group
            DependsOn = "[User]User1"
            Credential = $promptedCreds
            GroupName = "Administrators"
            Ensure = "Present"
            MembersToInclude = "User1"
        }
    }

    Node "TestMachine2"
    {
        # Now we'll use a node-specific password to this machine
        $password = $Node.LocalPass | ConvertTo-SecureString -asPlainText -Force
        $username = $node.UserName
        [PSCredential] $nodeCred = New-Object System.Management.Automation.PSCredential($username,$password)

        User User2
        {
            UserName = $username
            Password = $nodeCred
            Description = "local account"
            Ensure = "Present"
            Disabled = $false
            PasswordNeverExpires = $true
            PasswordChangeRequired = $false
        }

        Group addToAdmin
        {
            Credential = $domain
            GroupName = "Administrators"
            DependsOn = "[User]User2"
            Ensure = "Present"
            MembersToInclude = "User2"
        }
    }

}
# We declared the ConfigurationData in a local variable, but we need to pass it in to our configuration function
# We need to invoke the configuration function we created to generate a MOF
unencryptedPasswordDemo -ConfigurationData $ConfigurationData
# We need to pass the MOF to the machines we named.
#-wait: doesn't use jobs so we get blocked at the prompt until the configuration is done
#-verbose: so we can see what's going on and catch any errors
#-force: for testing purposes, I run start-dscconfiguration frequently + want to make sure i'm
#        not blocked by previous configurations that are still running
Start-DscConfiguration ./unencryptedPasswordDemo -verbose -wait -force
```

## <a name="handling-credentials-in-dsc"></a>Hantering av autentiseringsuppgifter i DSC

Kör som-resurser för DSC-konfigurationen `Local System` som standard.
Men vissa resurser behöver autentiseringsuppgifter, till exempel när den `Package` resurs ska installera programvara under ett visst användarkonto.

Tidigare resurser används en hårdkodad `Credential` egenskapsnamn för att hantera detta.
WMF 5.0 lagt till en automatisk `PsDscRunAsCredential` egenskap för alla resurser.
Information om hur du använder `PsDscRunAsCredential`, se [kör DSC med autentiseringsuppgifterna för användaren](runAsUser.md).
Nyare resurser och anpassade resurser kan använda automatiska egenskapen i stället för att skapa egna egenskapen för autentiseringsuppgifter.

>**Obs:** designen för vissa resurser som använder olika autentiseringsuppgifter för en specifik orsak och de har sina egna autentiseringsuppgifter egenskaper.

För att hitta tillgängliga autentiseringsuppgifter egenskaperna för en resurs använder antingen `Get-DscResource -Name ResourceName -Syntax` eller Intellisense i ISE (`CTRL+SPACE`).

```powershell
PS C:\> Get-DscResource -Name Group -Syntax
Group [String] #ResourceName
{
    GroupName = [string]
    [Credential = [PSCredential]]
    [DependsOn = [string[]]]
    [Description = [string]]
    [Ensure = [string]{ Absent | Present }]
    [Members = [string[]]]
    [MembersToExclude = [string[]]]
    [MembersToInclude = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
}
```

Det här exemplet används en [grupp](https://msdn.microsoft.com/en-us/powershell/dsc/groupresource) resurs från den `PSDesiredStateConfiguration` inbyggda DSC-Resursmodul.
Det kan skapa lokala grupper och lägga till eller ta bort medlemmar.
Accepteras både den `Credential` egenskap och automatiskt `PsDscRunAsCredential` egenskapen.
Resursen som endast använder dock den `Credential` egenskapen.

Mer information om den `PsDscRunAsCredential` egenskap, se [kör DSC med autentiseringsuppgifterna för användaren](runAsUser.md).

## <a name="example-the-group-resource-credential-property"></a>Exempel: Gruppresurser Credential-egenskapen

DSC körs under `Local System`, så den redan har behörighet att ändra lokala användare och grupper.
Om den medlem som lagts till är ett lokalt konto, krävs inga autentiseringsuppgifter.
Om den `Group` resurs lägger till ett domänkonto till den lokala gruppen och sedan autentiseringsuppgifter krävs.

Anonyma frågor till Active Directory är inte tillåtna.
Den `Credential` -egenskapen för den `Group` resursen är domänkontot som används för att fråga Active Directory.
För de flesta ändamål det kan bero ett allmänt användarkonto som standard användarna kan *läsa* de flesta objekt i Active Directory.

## <a name="example-configuration"></a>Exempel på konfiguration

Följande exempelkod använder DSC för att fylla i en lokal grupp med domän:

```powershell
Configuration DomainCredentialExample
{
    param
    (
        [PSCredential] $DomainCredential
    )
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    node localhost
    {
        Group DomainUserToLocalGroup
        {
            GroupName        = 'ApplicationAdmins'
            MembersToInclude = 'contoso\alice'
            Credential       = $DomainCredential
        }
    }
}

$cred = Get-Credential -UserName contoso\genericuser -Message "Password please"
DomainCredentialExample -DomainCredential $cred
```

Den här koden genereras ett fel och ett varningsmeddelande:

```
ConvertTo-MOFInstance : System.InvalidOperationException error processing
property 'Credential' OF TYPE 'Group': Converting and storing encrypted
passwords as plain text is not recommended. For more information on securing
credentials in MOF file, please refer to MSDN blog:
http://go.microsoft.com/fwlink/?LinkId=393729

At line:11 char:9
+   Group
At line:297 char:16
+     $aliasId = ConvertTo-MOFInstance $keywordName $canonicalizedValue
+                ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Write-Error], InvalidOperationException
    + FullyQualifiedErrorId : FailToProcessProperty,ConvertTo-MOFInstance

WARNING: It is not recommended to use domain credential for node 'localhost'.
In order to suppress the warning, you can add a property named
'PSDscAllowDomainUser' with a value of $true to your DSC configuration data
for node 'localhost'.
```

Det här exemplet har två problem:
1.  Ett fel som förklarar att lösenord i klartext inte rekommenderas
2.  En varning om att du inte använder en domän-autentiseringsuppgift

## <a name="psdscallowplaintextpassword"></a>PsDscAllowPlainTextPassword

Det första felmeddelandet har en URL till dokumentation.
Den här länken förklarar hur du krypterar lösenord med en [ConfigurationData](https://msdn.microsoft.com/en-us/powershell/dsc/configdata) struktur och ett certifikat.
Mer information om certifikat och DSC [läsa inlägget](http://aka.ms/certs4dsc).

Om du vill framtvinga ett lösenord i oformaterad text resursen kräver den `PsDscAllowPlainTextPassword` nyckelord i konfigurationsdata avsnittet på följande sätt:

```powershell
Configuration DomainCredentialExample
{
    param
    (
        [PSCredential] $DomainCredential
    )
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    node localhost
    {
        Group DomainUserToLocalGroup
        {
            GroupName        = 'ApplicationAdmins'
            MembersToInclude = 'contoso\alice'
            Credential       = $DomainCredential
        }
    }
}

$cd = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            PSDscAllowPlainTextPassword = $true
        }
    )
}

$cred = Get-Credential -UserName contoso\genericuser -Message "Password please"
DomainCredentialExample -DomainCredential $cred -ConfigurationData $cd
```

>**Obs:** `NodeName` får inte vara lika asterisk, en specifik nod-namn är obligatoriskt.

**Microsoft avråder för att undvika lösenord på grund av en stor säkerhetsrisk.**
Ett undantag är när du använder tjänsten Azure Automation DSC, eftersom data lagras alltid krypterad (under överföring i vila i tjänsten och i vila på noden).

## <a name="domain-credentials"></a>Autentiseringsuppgifter för domänen

Kör exempel konfigurationsskript igen (med eller utan kryptering) fortfarande genererar den varning som använder en domän-konto för en autentiseringsuppgift inte rekommenderas.
Med ett lokalt konto eliminerar eventuell exponering av autentiseringsuppgifter för domänen som kan användas på andra servrar.

**När du använder autentiseringsuppgifter med DSC-resurser, föredrar du ett lokalt konto under ett domänkonto när det är möjligt.**

Om det finns en '\' eller ”@” i den `Username` egenskapen för autentiseringsuppgifter och sedan DSC ska behandla det som ett domänkonto.
Det finns ett undantag för ”localhost”, ”127.0.0.1” och ”:: 1” i den som domändel av användarnamnet.

## <a name="psdscallowdomainuser"></a>PSDscAllowDomainUser

I DSC `Group` resurs-exemplet ovan, frågar Active Directory-domänen *kräver* ett domänkonto.
I det här fallet lägger du till den `PSDscAllowDomainUser` egenskapen till den `ConfigurationData` blockera på följande sätt:

```powershell
$cd = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            PSDscAllowDomainUser = $true
            # PSDscAllowPlainTextPassword = $true
            CertificateFile = "C:\PublicKeys\server1.cer"
        }
    )
}
```

Nu skapar skriptet configuration MOF-filen med några fel eller varningar.
