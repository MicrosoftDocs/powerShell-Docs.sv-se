---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: Alternativ för autentiseringsuppgifter i konfigurationsdata
ms.openlocfilehash: 2a326e45bbbad7bd2362b66b88bf61b98df7b02e
ms.sourcegitcommit: 6ae5b50a4b3ffcd649de1525c3ce6f15d3669082
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/18/2019
ms.locfileid: "55686378"
---
# <a name="credentials-options-in-configuration-data"></a>Alternativ för autentiseringsuppgifter i konfigurationsdata

>Gäller för: Windows PowerShell 5.0

## <a name="plain-text-passwords-and-domain-users"></a>Lösenord i klartext och domänanvändare

DSC-konfigurationer som innehåller en autentiseringsuppgift utan kryptering genererar ett felmeddelande om lösenord i klartext.
Dessutom genererar DSC en varning när du använder autentiseringsuppgifter för domänen.
Använd nyckelorden DSC-konfiguration data för att ignorera dessa fel och varningar:

- **PsDscAllowPlainTextPassword**
- **PsDscAllowDomainUser**

> [!NOTE]
> Lagra/överföring av okrypterade lösenord i klartext är inte säker. Du rekommenderas att säkra autentiseringsuppgifter genom att använda de tekniker som beskrivs senare i det här avsnittet.
> Tjänsten Azure Automation DSC kan du centralt hantera autentiseringsuppgifter som ska kompileras i konfigurationer och lagras på ett säkert sätt.
> För information, se: [Kompilering av DSC-konfigurationer / Credential tillgångar](/azure/automation/automation-dsc-compile#credential-assets)

## <a name="handling-credentials-in-dsc"></a>Hantering av autentiseringsuppgifter i DSC

Kör som-resurser för DSC-konfigurationen `Local System` som standard.
Men vissa resurser behöver autentiseringsuppgifter, till exempel när den `Package` resurs ska installera programvara under ett visst användarkonto.

Tidigare resurser används en hårdkodad `Credential` egenskapsnamn för att hantera detta.
WMF 5.0 lagt till en automatisk `PsDscRunAsCredential` egenskap för alla resurser.
Information om hur du använder `PsDscRunAsCredential`, se [kör DSC med autentiseringsuppgifterna för användaren](runAsUser.md).
Nyare resurser och anpassade resurser kan använda automatiska egenskapen i stället för att skapa egna egenskapen för autentiseringsuppgifter.

> [!NOTE]
> Designen för vissa resurser som använder olika autentiseringsuppgifter för en specifik orsak och de har sina egna autentiseringsuppgifter egenskaper.

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

Det här exemplet används en [grupp](../resources/resources.md) resurs från den `PSDesiredStateConfiguration` inbyggda DSC-Resursmodul.
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

1. Ett fel som förklarar att lösenord i klartext inte rekommenderas
2. En varning om att du inte använder en domän-autentiseringsuppgift

Flaggorna **PSDSCAllowPlainTextPassword** och **PSDSCAllowDomainUser** ignorera felet och varning som informerar användaren om risken.

## <a name="psdscallowplaintextpassword"></a>PSDSCAllowPlainTextPassword

Det första felmeddelandet har en URL till dokumentation.
Den här länken förklarar hur du krypterar lösenord med en [ConfigurationData](./configData.md) struktur och ett certifikat.
Mer information om certifikat och DSC [läsa inlägget](http://aka.ms/certs4dsc).

Om du vill framtvinga ett lösenord i oformaterad text resursen kräver den `PsDscAllowPlainTextPassword` nyckelord i konfigurationsdata avsnittet på följande sätt:

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

Den **PSDSCAllowPlainTextPassword** flaggan kräver att användaren bekräftar risken för att lagra lösenord i klartext i en MOF-fil. I den genererade MOF-filen, även om en **PSCredential** objekt som innehåller en **SecureString** användes, lösenorden fortfarande visas som oformaterad text. Detta är den enda autentiseringsuppgifter exponeras. Få åtkomst till den här MOF-fil ger någon åtkomst till administratörskontot.

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

- Den **PSDscAllowPlainTextPassword** -flagga gör sammanställning av MOF-filer som innehåller lösenord i klartext.
  Vidta åtgärder när du lagrar MOF-filer som innehåller rena textlösenord.
- När MOF-filen som levereras till en nod i **Push** läge, WinRM krypterar kommunikation för att skydda lösenordet i klartext såvida du inte åsidosätter standard med den **AllowUnencrypted** parameter.
  - Kryptera MOF med ett certifikat skyddar MOF-filen i viloläge innan den har kopplats till en nod.
- I **Pull** läge, som du kan konfigurera Windows pull-server att använda HTTPS för att kryptera trafik med hjälp av protokoll som anges i Internet Information Server. Mer information finns i artiklarna [installera en klient för DSC-pull](../pull-server/pullclient.md) och [skydda MOF-filer med certifikat](../pull-server/secureMOF.md).
  - I den [Azure Automation-tillståndskonfigurationen](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview) service, Pull trafiken krypteras alltid.
- På noden, krypteras MOF-filer vilande från och med PowerShell 5.0.
  - Filer är okrypterad i vila i PowerShell 4.0 MOF om de är krypterade med ett certifikat när de flyttas eller hämtas till noden.

**Microsoft avråder för att undvika lösenord på grund av en stor säkerhetsrisk.**

## <a name="domain-credentials"></a>Domain Credentials

Kör exempel konfigurationsskript igen (med eller utan kryptering) fortfarande genererar den varning som använder en domän-konto för en autentiseringsuppgift inte rekommenderas.
Med ett lokalt konto eliminerar eventuell exponering av autentiseringsuppgifter för domänen som kan användas på andra servrar.

**När du använder autentiseringsuppgifter med DSC-resurser, föredrar du ett lokalt konto under ett domänkonto när det är möjligt.**

Om det finns en ”\\'eller'\@' i den `Username` egenskapen för autentiseringsuppgifter och sedan DSC ska behandla det som ett domänkonto.
Det finns ett undantag för ”localhost”, ”127.0.0.1” och ”:: 1” i den som domändel av användarnamnet.

## <a name="psdscallowdomainuser"></a>PSDscAllowDomainUser

I DSC `Group` resurs-exemplet ovan, frågar Active Directory-domänen *kräver* ett domänkonto.
I det här fallet lägger du till den `PSDscAllowDomainUser` egenskapen till den `ConfigurationData` blockera på följande sätt:

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

Nu skapar skriptet configuration MOF-filen med några fel eller varningar.
