---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: Alternativ för autentiseringsuppgifter i konfigurationsdata
ms.openlocfilehash: 2a326e45bbbad7bd2362b66b88bf61b98df7b02e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080160"
---
# <a name="credentials-options-in-configuration-data"></a>Alternativ för autentiseringsuppgifter i konfigurationsdata

>Gäller för: Windows PowerShell 5.0

## <a name="plain-text-passwords-and-domain-users"></a>Oformaterad textlösenord och domänanvändare

DSC-konfigurationer som innehåller en autentiseringsuppgift utan kryptering genererar ett felmeddelande om lösenord i klartext.
Dessutom genererar DSC en varning när du använder autentiseringsuppgifter för domänen.
Använda DSC-konfiguration data nyckelord för att ignorera dessa fel och varningar:

- **PsDscAllowPlainTextPassword**
- **PsDscAllowDomainUser**

> [!NOTE]
> Lagra/överföring av okrypterade lösenord i klartext är inte säker. Du rekommenderas att skydda autentiseringsuppgifter med hjälp av de metoder som beskrivs senare i det här avsnittet.
> Tjänsten Azure Automation DSC kan du centralt hantera autentiseringsuppgifter för att kompileras i konfigurationer och lagras på ett säkert sätt.
> Läs om: [Kompilera DSC-konfigurationer / Autentiseringstillgångar](/azure/automation/automation-dsc-compile#credential-assets)

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
ConvertTo-MOFInstance : System.InvalidOperationException error processing property 'Credential' OF
TYPE 'Group': Converting and storing encrypted passwords as plain text is not recommended.
For more information on securing credentials in MOF file, please refer to MSDN blog:
https://go.microsoft.com/fwlink/?LinkId=393729

At line:11 char:9
+   Group
At line:341 char:16
+     $aliasId = ConvertTo-MOFInstance $keywordName $canonicalizedValue
+                ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Write-Error], InvalidOperationException
    + FullyQualifiedErrorId : FailToProcessProperty,ConvertTo-MOFInstance
WARNING: It is not recommended to use domain credential for node 'localhost'. In order to suppress
the warning, you can add a property named 'PSDscAllowDomainUser' with a value of $true to your DSC
configuration data for node 'localhost'.

Compilation errors occurred while processing configuration
'DomainCredentialExample'. Please review the errors reported in error stream and modify your
configuration code appropriately.
At C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\PSDesiredStateConfiguration.psm1:3917 char:5
+     throw $ErrorRecord
+     ~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (DomainCredentialExample:String) [], InvalidOperationException
    + FullyQualifiedErrorId : FailToProcessConfiguration
```

Det här exemplet har två problem:

1. Felmeddelandet förklarar att lösenord i klartext inte rekommenderas
2. En varning om att du inte använder en domänautentiseringsuppgift

Flaggorna **PSDSCAllowPlainTextPassword** och **PSDSCAllowDomainUser** Ignorera fel- och varningsstatusmeddelanden som informerar användaren om risken i fråga.

## <a name="psdscallowplaintextpassword"></a>PSDSCAllowPlainTextPassword

Det första felmeddelandet har en URL med dokumentation.
Den här länken förklarar hur du krypterar lösenord med hjälp av en [ConfigurationData](./configData.md) struktur och ett certifikat.
Mer information om certifikat och DSC [Läs det här inlägget](http://aka.ms/certs4dsc).

Om du vill framtvinga ett lösenord i oformaterad text, resursen kräver den `PsDscAllowPlainTextPassword` nyckelord i konfigurationsdata avsnittet på följande sätt:

```powershell
$password = "ThisIsAPlaintextPassword" | ConvertTo-SecureString -asPlainText -Force
$username = "contoso\Administrator"
[PSCredential] $credential = New-Object System.Management.Automation.PSCredential($username,$password)

Configuration DomainCredentialExample
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    node localhost
    {
        Group DomainUserToLocalGroup
        {
            GroupName        = 'ApplicationAdmins'
            MembersToInclude = 'contoso\alice'
            Credential       = $credential
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

DomainCredentialExample -ConfigurationData $cd
```

### <a name="localhostmof"></a>localhost.mof

Den **PSDSCAllowPlainTextPassword** flaggan kräver att användaren bekräftar risken för att lagra lösenord i oformaterad text i en MOF-fil. I den genererade MOF-filen, även om en **PSCredential** objekt som innehåller en **SecureString** har använts, lösenorden visas fortfarande som oformaterad text. Det här är den enda gången som autentiseringsuppgifterna är tillgängliga. Få åtkomst till MOF-filen på så sätt får alla komma åt administratörskontot.

```
/*
@TargetNode='localhost'
@GeneratedBy=Administrator
@GenerationDate=01/31/2019 06:43:13
@GenerationHost=Server01
*/

instance of MSFT_Credential as $MSFT_Credential1ref
{
Password = "ThisIsAPlaintextPassword";
 UserName = "Administrator";

};

instance of MSFT_GroupResource as $MSFT_GroupResource1ref
{
ResourceID = "[Group]DomainUserToLocalGroup";
 MembersToInclude = {
    "contoso\\alice"
};
 Credential = $MSFT_Credential1ref;
 SourceInfo = "::11::9::Group";
 GroupName = "ApplicationAdmins";
 ModuleName = "PSDesiredStateConfiguration";

ModuleVersion = "1.0";

 ConfigurationName = "DomainCredentialExample";

};
```

### <a name="credentials-in-transit-and-at-rest"></a>Autentiseringsuppgifter vid överföring och i vila

- Den **PSDscAllowPlainTextPassword** -flagga gör kompileringen av MOF-filer som innehåller lösenord i klartext.
  Vidta åtgärder vid lagring MOF-filer som innehåller lösenord i klartext.
- När MOF-filen levereras till en nod i **Push** läge, WinRM krypterar kommunikation för att skydda lösenord i klartext, såvida inte du åsidosätta standardinställningen med den **AllowUnencrypted** parametern.
  - Kryptera MOF med ett certifikat skyddar MOF-filen i viloläge innan den har kopplats till en nod.
- I **Pull** läge, som du kan konfigurera Windows-hämtningsservern för att använda HTTPS för att kryptera trafik med hjälp av det protokoll som anges i Internet Information Server. Mer information finns i artiklarna [konfigurera en DSC-hämtningsklient](../pull-server/pullclient.md) och [skydda MOF-filer med certifikat](../pull-server/secureMOF.md).
  - I den [Azure Automation-Tillståndskonfiguration](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview) service, Pull-trafik krypteras alltid.
- På noden och MOF-filer krypteras på plats från och med PowerShell 5.0.
  - Filer är krypterade i vila i PowerShell 4.0 MOF om de är krypterade med ett certifikat när de skickas eller hämtas till noden.

**Microsoft avråder för att undvika lösenord på grund av en stor säkerhetsrisk.**

## <a name="domain-credentials"></a>Domain Credentials

Som exempel konfigurationsskript igen (med eller utan kryptering), fortfarande att genererar varning som använder en domän-konto för en autentiseringsuppgift inte rekommenderas.
Med ett lokalt konto eliminerar potentiell exponering av autentiseringsuppgifter för domänen som kan användas på andra servrar.

**När du använder autentiseringsuppgifter med DSC-resurser, föredrar du ett lokalt konto under ett domänkonto när det är möjligt.**

Om det finns en ”\\” eller ”\@” i den `Username` egenskapen för autentiseringsuppgifter och sedan DSC behandlar det som ett domänkonto.
Det finns ett undantag för ”localhost”, ”127.0.0.1” och ”:: 1” i domändelen i användarnamnet.

## <a name="psdscallowdomainuser"></a>PSDscAllowDomainUser

I DSC `Group` resursexempel ovan, frågar ett Active Directory-domän *kräver* ett domänkonto.
I det här fallet lägger du till den `PSDscAllowDomainUser` egenskap enligt den `ConfigurationData` blockera på följande sätt:

```powershell
$password = "ThisIsAPlaintextPassword" | ConvertTo-SecureString -asPlainText -Force
$username = "contoso\Administrator"
[PSCredential] $credential = New-Object System.Management.Automation.PSCredential($username,$password)

Configuration DomainCredentialExample
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    node localhost
    {
        Group DomainUserToLocalGroup
        {
            GroupName        = 'ApplicationAdmins'
            MembersToInclude = 'contoso\alice'
            Credential       = $credential
        }
    }
}

$cd = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            PSDscAllowDomainUser = $true
            PSDscAllowPlainTextPassword = $true
        }
    )
}

DomainCredentialExample -ConfigurationData $cd
```

Nu genererar konfigurationsskriptet MOF-filen med några fel eller varningar.
