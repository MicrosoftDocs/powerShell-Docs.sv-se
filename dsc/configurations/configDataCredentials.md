---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: Alternativ för autentiseringsuppgifter i konfigurationsdata
ms.openlocfilehash: c4057457bf6beb2c5fc9dffef9122cd488ccdcd7
ms.sourcegitcommit: 9df29dfc637191b62ca591893c251c1e02d4eb4c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/04/2019
ms.locfileid: "54012440"
---
# <a name="credentials-options-in-configuration-data"></a>Alternativ för autentiseringsuppgifter i konfigurationsdata
>Gäller för: Windows PowerShell 5.0

## <a name="plain-text-passwords-and-domain-users"></a>Oformaterad textlösenord och domänanvändare

DSC-konfigurationer som innehåller en autentiseringsuppgift utan kryptering genererar ett felmeddelande om lösenord i klartext.
Dessutom genererar DSC en varning när du använder autentiseringsuppgifter för domänen.
Använda DSC-konfiguration data nyckelord för att ignorera dessa fel och varningar:
* **PsDscAllowPlainTextPassword**
* **PsDscAllowDomainUser**

> [!NOTE]
> Lagra/överföring av okrypterade lösenord i klartext är inte säker. Du rekommenderas att skydda autentiseringsuppgifter med hjälp av de metoder som beskrivs senare i det här avsnittet.
> Tjänsten Azure Automation DSC kan du centralt hantera autentiseringsuppgifter för att kompileras i konfigurationer och lagras på ett säkert sätt.
> Läs om: [Kompilera DSC-konfigurationer / Autentiseringstillgångar](/azure/automation/automation-dsc-compile#credential-assets)

Följande är ett exempel på Skicka autentiseringsuppgifter med oformaterad text:

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
        $password = $Node.LocalPassword | ConvertTo-SecureString -asPlainText -Force
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
            Credential = $promptedCreds
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

Det här är ett utdrag från filen ”.mof” som skapats av konfigurationen för ”TestMachine1”. Den `System.Security.SecureString` används i konfigurationen har konverterats till oformaterad text och lagras i filen ”.mof” som en `MSF_Credential`. En `SecureString` krypteras med den aktuella användarens profilen. Detta fungerar bra med alla former av PowerShell fjärrhantering. En ”.mof”-fil är avsett att vara en fristående enbart tjänstkonfigurationens mekanism. Från och med PowerShell 5.0, krypteras MOF-filerna på en nod i vila, men inte under överföringen till noden. Det innebär att lösenord i en ”.mof”-fil visas i klartext när du tillämpar dem på en nod. För att kryptera autentiseringsuppgifter kan du behöva använda en **Hämtningsserver**. Mer information finns i [skydda MOF-filer med certifikat](./pull-server/secureMOF.md).

```syntax
instance of MSFT_Credential as $MSFT_Credential1ref
{
Password = "ThisIsYetAnotherPlaintextPassword";
 UserName = "User2";

};

instance of MSFT_UserResource as $MSFT_UserResource1ref
{
ResourceID = "[User]User2";
 Description = "local account";
 UserName = "User2";
 Ensure = "Present";
 Password = $MSFT_Credential1ref;
 Disabled = False;
 SourceInfo = "::66::9::User";
 PasswordNeverExpires = True;
 ModuleName = "PsDesiredStateConfiguration";
 PasswordChangeRequired = False;

ModuleVersion = "1.0";

 ConfigurationName = "unencryptedPasswordDemo";

};
```

## <a name="handling-credentials-in-dsc"></a>Hantering av autentiseringsuppgifter i DSC

DSC-konfiguration resurser kör som- `Local System` som standard.
Men vissa resurser måste autentiseringsuppgifter, till exempel när den `Package` resurs ska installera programvara under ett visst användarkonto.

Resurser som tidigare använde ett hårdkodat `Credential` egenskapsnamn ska hantera detta.
WMF 5.0 har lagts till en automatisk `PsDscRunAsCredential` egenskap för alla resurser.
Information om hur du använder `PsDscRunAsCredential`, se [kör DSC med autentiseringsuppgifterna för användaren](runAsUser.md).
Nyare resurser och anpassade resurser kan använda den här automatiska egenskapen istället för att skapa sina egna egenskapen för autentiseringsuppgifter.

> [!NOTE]
> Design av vissa resurser är använder olika autentiseringsuppgifter för en särskild anledning och de har sina egna autentiseringsegenskaper.

För att hitta tillgängliga autentiseringsuppgifterna egenskaperna för en resurs använder antingen `Get-DscResource -Name ResourceName -Syntax` eller Intellisense i ISE (`CTRL+SPACE`).

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

Det här exemplet används en [grupp](../resources/resources.md) resurs från den `PSDesiredStateConfiguration` inbyggda modulen för DSC-resurs.
Det kan skapa lokala grupper och lägga till eller ta bort medlemmar.
Den accepterar både den `Credential` egenskap och automatiskt `PsDscRunAsCredential` egenskapen.
Resursen endast använder dock den `Credential` egenskapen.

Mer information om den `PsDscRunAsCredential` egenskap, finns i [kör DSC med autentiseringsuppgifterna för användaren](runAsUser.md).

## <a name="example-the-group-resource-credential-property"></a>Exempel: Gruppresurs Credential-egenskapen

DSC körs under `Local System`, så att den redan har behörighet att ändra lokala användare och grupper.
Om medlemmen har lagts till är ett lokalt konto, krävs inga autentiseringsuppgifter.
Om den `Group` resurs lägger till ett nytt konto i den lokala gruppen och sedan en autentiseringsuppgift är nödvändigt.

Anonyma frågor till Active Directory är inte tillåtna.
Den `Credential` egenskapen för den `Group` resurs är det domänkonto som används för att fråga Active Directory.
För de flesta ändamål detta kan bero på ett generiskt användarkonto att som standard kan användare *läsa* de flesta objekt i Active Directory.

## <a name="example-configuration"></a>Exempel på konfiguration

Följande exempelkod använder DSC för att fylla i en lokal grupp med en domänanvändare:

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

Den här koden genererar ett fel och ett varningsmeddelande:

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
1. Felmeddelandet förklarar att lösenord i klartext inte rekommenderas
2. En varning om att du inte använder en domänautentiseringsuppgift

## <a name="psdscallowplaintextpassword"></a>PsDscAllowPlainTextPassword

Det första felmeddelandet har en URL med dokumentation.
Den här länken förklarar hur du krypterar lösenord med hjälp av en [ConfigurationData](./configData.md) struktur och ett certifikat.
Mer information om certifikat och DSC [Läs det här inlägget](http://aka.ms/certs4dsc).

Om du vill framtvinga ett lösenord i oformaterad text, resursen kräver den `PsDscAllowPlainTextPassword` nyckelord i konfigurationsdata avsnittet på följande sätt:

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

> [!NOTE]
> `NodeName` Det går inte att vara lika med asterisk, en viss nod-namn är obligatoriskt.

**Microsoft avråder för att undvika lösenord på grund av en stor säkerhetsrisk.**

## <a name="domain-credentials"></a>Autentiseringsuppgifter för domänen

Som exempel konfigurationsskript igen (med eller utan kryptering), fortfarande att genererar varning som använder en domän-konto för en autentiseringsuppgift inte rekommenderas.
Med ett lokalt konto eliminerar potentiell exponering av autentiseringsuppgifter för domänen som kan användas på andra servrar.

**När du använder autentiseringsuppgifter med DSC-resurser, föredrar du ett lokalt konto under ett domänkonto när det är möjligt.**

Om det finns en ”\' eller ' @' i den `Username` egenskapen för autentiseringsuppgifter och sedan DSC behandlar det som ett domänkonto.
Det finns ett undantag för ”localhost”, ”127.0.0.1” och ”:: 1” i domändelen i användarnamnet.

## <a name="psdscallowdomainuser"></a>PSDscAllowDomainUser

I DSC `Group` resursexempel ovan, frågar ett Active Directory-domän *kräver* ett domänkonto.
I det här fallet lägger du till den `PSDscAllowDomainUser` egenskap enligt den `ConfigurationData` blockera på följande sätt:

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

Nu genererar konfigurationsskriptet MOF-filen med några fel eller varningar.
