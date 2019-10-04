---
ms.date: 12/12/2018
keywords: DSC, PowerShell, resurs, Galleri, installation
title: Installera ytterligare DSC-resurser
ms.openlocfilehash: ecaf176230ccd934b57b1c27d72ff83e6ba906e9
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71942323"
---
# <a name="install-additional-dsc-resources"></a>Installera ytterligare DSC-resurser

PowerShell innehåller flera färdiga resurser för önskad tillstånds konfiguration (DSC). **PSDesiredStateConfiguration** -modulen innehåller alla OOB DSC-resurser som är tillgängliga på din speciella instans av PowerShell.

Det här är en lista över OOB-resurser som ingår i PowerShell 4,0 och en beskrivning av resursens funktioner.

> [!NOTE]
> Det här är en ofullständig lista eftersom antalet OOB-resurser har växt med varje version av PowerShell.

|Resource  |Beskrivning  |
|---------|---------|
|**Fil**|Styr tillstånd för filer och kataloger. Kopierar filer från en **källa** till ett **mål** och uppdaterar dem när **källan** ändras genom att jämföra datum, kontroll summor och hash-värden.|
|**Arkiv**|Packar upp arkiv och en angiven plats. Validerar arkiven med en angiven **kontroll Summa**.|
|**Miljö**|Hanterar miljövariabler.|
|**Grupp**|Hanterar medlemskap i lokala grupper och kontroll grupper.|
|**log**|Skriver meddelanden till händelse loggen `Microsoft-Windows-Desired State Configuration/Analytic`.|
|**Paketfilerna**|Installerar eller avinstallerar paket med **argument**, **LogPath**, **ReturnCode**, andra inställningar.|
|**Registernyckeln**|Hanterar register nycklar och värden.|
|**Över**|Gör att du kan skapa egna skript block för [Get-test-uppsättning](../resources/get-test-set.md) .|
|**Tjänst**|Konfigurerar Windows-tjänster.|
|**Användarvänlig** |Hanterar lokala användare och attribut.|
|**WindowsFeature**|Hanterar roller och funktioner.|
|**WindowsProcess**|Konfigurerar Windows-processer.|

OOB-resurserna gör det möjligt att använda en lämplig start punkt för vanliga åtgärder. Om OOB-resurserna inte uppfyller dina behov kan du skriva en egen [anpassad resurs](../resources/authoringResource.md). Innan du skriver en anpassad resurs för att lösa problemet bör du titta igenom det stora antalet DSC-resurser som redan har skapats av både Microsoft och PowerShell-communityn.

Du hittar DSC-resurser i både [PowerShell-galleriet](https://www.powershellgallery.com/) -och [GitHub](https://github.com/). Du kan också installera DSC-resurser direkt från PowerShell-konsolen med hjälp av [PowerShellGet](/powershell/module/powershellget/).

## <a name="installing-powershellget"></a>Installera PowerShellGet

Om du vill kontrol lera om du redan har **PowerShell** , eller om du vill ha hjälp med att installera den, kan du läsa följande guide: [Installerar PowerShellGet](/powershell/gallery/installing-psget).

## <a name="finding-dsc-resources-using-powershellget"></a>Hitta DSC-resurser med PowerShellGet

När **PowerShellGet** har installerats på systemet kan du söka efter och installera DSC-resurser som finns i [PowerShell-galleriet](https://www.powershellgallery.com/).

Använd först cmdleten [find-dscresource Keyword Supports](/powershell/module/powershellget/find-dscresource) för att hitta DSC-resurser. När du kör `Find-DSCResource` för första gången, visas följande uppmanad att installera "NuGet Provider".

```
PS> Find-DSCResource

NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The
NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies' or
'C:\Users\xAdministrator\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider
 by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to
install and import the NuGet provider now?
[Y] Yes  [N] No  [?] Help (default is "Y"):
```

När du har tryckt på "y" installeras "NuGet"-providern. du ser en lista över DSC-resurser som du kan installera från PowerShell-galleriet.

> [!NOTE]
> Listan visas inte eftersom den är mycket stor.

Du kan också ange parametern `-Name` med jokertecken eller `-Filter`-parameter utan jokertecken för att begränsa sökningen. Det här exemplet försöker hitta en "TimeZone" DSC-resurs med hjälp av jokertecken.

> [!IMPORTANT]
> För närvarande finns det ett fel i cmdleten `Find-DSCResource` som förhindrar användning av jokertecken i både parametrarna `-Name` och @no__t 2. I det andra exemplet nedan visas en lösning med `Where-Object`.

```
PS> Find-DSCResource -Name *Time*

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
Carbon_EnvironmentVariable          2.6.0      Carbon                              PSGallery
Carbon_FirewallRule                 2.6.0      Carbon                              PSGallery
Carbon_Group                        2.6.0      Carbon                              PSGallery
Carbon_IniFile                      2.6.0      Carbon                              PSGallery
Carbon_Permission                   2.6.0      Carbon                              PSGallery
Carbon_Privilege                    2.6.0      Carbon                              PSGallery
Carbon_ScheduledTask                2.6.0      Carbon                              PSGallery
Carbon_Service                      2.6.0      Carbon                              PSGallery
TimeZone                            6.0.0.0    ComputerManagementDsc               PSGallery
xTimeZone                           1.8.0.0    xTimeZone                           PSGallery
xSqlServerDefaultDir                1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerMoveDatabaseFiles         1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerSQLDataRoot               1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerStartupParam              1.0.0      mlSqlServerDSC                      PSGallery
```

Du kan också använda `Where-Object` för att hitta DSC-resurser med mer detaljerad filtrering. Den här metoden går långsammare än att använda inbyggda filtrerings parametrar.

```
PS> Find-DSCResource | Where-Object {$_.Name -like "Time*"}

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
TimeZone                            6.0.0.0    ComputerManagementDsc               PSGallery
```

Mer information om filtrering finns i [Where-Object](/powershell/module/microsoft.powershell.core/where-object).

## <a name="installing-dsc-resources-using-powershellget"></a>Installera DSC-resurser med PowerShellGet

Om du vill installera en DSC-resurs använder du cmdleten [install-module](/powershell/module/PowershellGet/Install-Module) och anger namnet på modulen som visas under **Modulnamn** i Sök resultatet.

"TimeZone"-resursen finns i modulen "ComputerManagementDSC", så att är den modul som det här exemplet installerar.

> [!NOTE]
> Om du inte har betrott PowerShell-galleriet ser du varningen nedan och ber om bekräftelse och instruerar dig att undvika efterföljande frågor om installationer.

```
PS> Install-Module -Name ComputerManagementDSC

Untrusted repository
You are installing the modules from an untrusted repository. If you trust this repository, change its
InstallationPolicy value by running the Set-PSRepository cmdlet. Are you sure you want to install the modules from
'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

Tryck på "y" för att fortsätta installera modulen. Efter installationen kan du kontrol lera att den nya resursen är installerad med hjälp av [Get-dscresource Keyword Supports](/powershell/module/PSDesiredStateConfiguration/Get-DscResource).

```
PS> Get-DSCResource -Name TimeZone -Syntax

TimeZone [String] #ResourceName
{
    IsSingleInstance = [string]{ Yes }
    TimeZone = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
}
```

Du kan också visa andra resurser i den nyligen installerade modulen genom att ange parametern `-ModuleName`.

```
PS> Get-DSCResource -Module ComputerManagementDSC

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      Computer                  ComputerManagementDsc          6.0.0.0    {Name, Credential, DependsOn, ...
PowerShell      OfflineDomainJoin         ComputerManagementDsc          6.0.0.0    {IsSingleInstance, RequestFile...
PowerShell      PowerPlan                 ComputerManagementDsc          6.0.0.0    {IsSingleInstance, Name, Depen...
PowerShell      PowerShellExecutionPolicy ComputerManagementDsc          6.0.0.0    {ExecutionPolicy, ExecutionPol...
PowerShell      ScheduledTask             ComputerManagementDsc          6.0.0.0    {TaskName, ActionArguments, Ac...
PowerShell      TimeZone                  ComputerManagementDsc          6.0.0.0    {IsSingleInstance, TimeZone, D...
PowerShell      VirtualMemory             ComputerManagementDsc          6.0.0.0    {Drive, Type, DependsOn, Initi...
```

## <a name="see-also"></a>Se även

- [Vad är resurser?](../resources/resources.md)
