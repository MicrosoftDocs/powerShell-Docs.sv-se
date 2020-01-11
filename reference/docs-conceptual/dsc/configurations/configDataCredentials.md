---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: Alternativ för autentiseringsuppgifter i konfigurations data
ms.openlocfilehash: aac27f1ff4b4287b53745fa3b946fb3de84771c2
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870565"
---
# <a name="credentials-options-in-configuration-data"></a>Alternativ för autentiseringsuppgifter i konfigurations data

> Gäller för: Windows PowerShell 5,0

## <a name="plain-text-passwords-and-domain-users"></a>Lösen ord för oformaterad text och domän användare

DSC-konfigurationer som innehåller en autentiseringsuppgift utan kryptering genererar ett fel meddelande om lösen ord med oformaterad text. DSC kommer också att generera en varning när du använder domänautentiseringsuppgifter. För att ignorera dessa fel och varnings meddelanden använder du nyckelorden DSC-konfigurations data:

- **PsDscAllowPlainTextPassword**
- **PsDscAllowDomainUser**

> [!NOTE]
> Det är vanligt vis inte säkert att lagra/överföra okrypterade lösen ord okrypterade. Att skydda autentiseringsuppgifter genom att använda de metoder som beskrivs senare i det här avsnittet rekommenderas. Med tjänsten Azure Automation DSC kan du centralt hantera autentiseringsuppgifter som ska kompileras i konfigurationer och lagras på ett säkert sätt. Mer information finns i: [kompilera DSC-konfigurationer/Credential-tillgångar](/azure/automation/automation-dsc-compile#credential-assets)

## <a name="handling-credentials-in-dsc"></a>Hantera autentiseringsuppgifter i DSC

DSC-konfigurations resurser körs som `Local System` som standard. Vissa resurser behöver dock en autentiseringsuppgift, till exempel när den `Package` resursen måste installera program vara under ett visst användar konto.

Tidigare resurser använde ett hårdkodat `Credential` egenskaps namn för att hantera detta. WMF 5,0 har lagt till en automatisk `PsDscRunAsCredential`-egenskap för alla resurser. Information om hur du använder `PsDscRunAsCredential`finns i [köra DSC med användarautentiseringsuppgifter](runAsUser.md). Nya resurser och anpassade resurser kan använda denna automatiska egenskap i stället för att skapa egna egenskaper för autentiseringsuppgifter.

> [!NOTE]
> Designen av vissa resurser är att använda flera autentiseringsuppgifter av en viss anledning och de har sina egna egenskaper för autentiseringsuppgifter.

Om du vill hitta tillgängliga egenskaper för autentiseringsuppgifter på en resurs använder du antingen `Get-DscResource -Name ResourceName -Syntax` eller IntelliSense i ISE (`CTRL+SPACE`).

```powershell
Get-DscResource -Name Group -Syntax
```

```Output
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

I det här exemplet används en [grupp](../resources/resources.md) resurs från den `PSDesiredStateConfiguration` inbyggda DSC-modulen. Den kan skapa lokala grupper och lägga till eller ta bort medlemmar. Den accepterar både egenskapen `Credential` och den automatiska `PsDscRunAsCredential`-egenskapen. Resursen använder dock endast egenskapen `Credential`.

Mer information om `PsDscRunAsCredential`-egenskapen finns i [köra DSC med användarautentiseringsuppgifter](runAsUser.md).

## <a name="example-the-group-resource-credential-property"></a>Exempel: egenskapen autentiseringsuppgifter för grupp resurs

DSC körs under `Local System`, så den har redan behörighet att ändra lokala användare och grupper. Om medlemmen som har lagts till är ett lokalt konto krävs ingen autentiseringsuppgift. Om `Group`-resursen lägger till ett domän konto i den lokala gruppen, krävs en autentiseringsuppgift.

Anonyma frågor till Active Directory är inte tillåtna. Egenskapen `Credential` för `Group` resursen är det domän konto som används för att fråga Active Directory. Detta kan vara ett allmänt användar konto, eftersom användare som standard kan *läsa* de flesta objekt i Active Directory.

## <a name="example-configuration"></a>Exempel på konfiguration

I följande exempel kod används DSC för att fylla i en lokal grupp med en domän användare:

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

Den här koden genererar både ett fel och ett varnings meddelande:

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

1. Ett fel förklarar att lösen ord för oformaterad text inte rekommenderas
2. En varning om att använda en domän behörighet

Flaggorna **PSDSCAllowPlainTextPassword** och **PSDSCAllowDomainUser** undertrycker felet och varningen som informerar användaren om risken.

## <a name="psdscallowplaintextpassword"></a>PSDSCAllowPlainTextPassword

Det första fel meddelandet har en URL med dokumentation. Den här länken förklarar hur du krypterar lösen ord med hjälp av en [ConfigurationData](./configData.md) -struktur och ett certifikat. Mer information om certifikat och DSC [finns i det här inlägget](https://aka.ms/certs4dsc).

För att framtvinga ett lösen ord för oformaterad text kräver resursen `PsDscAllowPlainTextPassword` nyckelordet i konfigurations data avsnittet enligt följande:

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

### <a name="localhostmof"></a>localhost. MOF

**PSDSCAllowPlainTextPassword** -flaggan kräver att användaren bekräftar risken för att lösen ord för oformaterad text ska lagras i en MOF-fil. I den genererade MOF-filen, även om ett **PSCredential** -objekt som innehåller en **SecureString** användes, visas lösen orden fortfarande som oformaterad text. Detta är den enda tidpunkt då autentiseringsuppgifterna exponeras. Om du får åtkomst till den här MOF-filen får vem som helst åtkomst till administratörs kontot.

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

- Flaggan **PSDscAllowPlainTextPassword** tillåter KOMPILERING av MOF-filer som innehåller lösen ord i klartext. Vidta försiktighets åtgärder när du lagrar MOF-filer som innehåller lösen ord för klartext.
- När MOF-filen levereras till en nod i **push** -läge krypterar WinRM kommunikationen för att skydda lösen ordet för klartext om du inte åsidosätter standardvärdet med parametern **AllowUnencrypted** .
  - Kryptering av MOF med ett certifikat skyddar MOF-filen i vila innan den tillämpas på en nod.
- I **pull** -läge kan du konfigurera Windows pull server för att använda HTTPS för att kryptera trafik med protokollet som anges i Internet Information Server. Mer information finns i artikeln om att konfigurera [en DSC-pull-klient](../pull-server/pullclient.md) och [skydda MOF-filer med certifikat](../pull-server/secureMOF.md).
  - Pull-trafik är alltid krypterad i [Azure Automation tillstånds konfigurations](/azure/automation/automation-dsc-overview) tjänsten.
- På noden krypteras MOF-filer i vila från och med PowerShell 5,0.
  - I PowerShell 4,0 MOF-filer okrypterade i rest om de inte krypteras med ett certifikat när de skickas eller hämtas till noden.

**Microsoft rekommenderar att lösen ord för oformaterad text undviks på grund av en betydande säkerhets risk.**

## <a name="domain-credentials"></a>Domänautentiseringsuppgifter

Om du kör exempel konfigurations skriptet igen (med eller utan kryptering), genererar fortfarande varningen att ett domän konto för en autentiseringsuppgift inte rekommenderas. Genom att använda ett lokalt konto elimineras potentiell exponering för domänautentiseringsuppgifter som kan användas på andra servrar.

**När du använder autentiseringsuppgifter med DSC-resurser föredrar du ett lokalt konto över ett domän konto när det är möjligt.**

Om det finns en "\\" eller "\@" i behörighetens `Username`-egenskap, kommer DSC att behandla det som ett domän konto. Det finns ett undantag för "localhost", "127.0.0.1" och ":: 1" i domän delen av användar namnet.

## <a name="psdscallowdomainuser"></a>PSDscAllowDomainUser

I exempel exemplet för DSC-`Group` ovan, *kräver* en fråga till en Active Directory domän ett domän konto. I det här fallet lägger du till egenskapen `PSDscAllowDomainUser` i `ConfigurationData`-blocket på följande sätt:

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

Nu kommer konfigurations skriptet att generera MOF-filen utan fel eller varningar.
