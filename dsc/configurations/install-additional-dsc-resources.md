---
ms.date: 12/12/2018
keywords: DSC, powershell, resurs, galleriet, inställning
title: Installera ytterligare DSC-resurser
ms.openlocfilehash: ecaf176230ccd934b57b1c27d72ff83e6ba906e9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080092"
---
# <a name="install-additional-dsc-resources"></a>Installera ytterligare DSC-resurser

PowerShell innehåller flera Out-of the box-resurser för Desired State Configuration (DSC). Den **PSDesiredStateConfiguration** modulen innehåller alla OOB DSC-resurser tillgängliga på dina specifika instansen av PowerShell.

Det här är en lista över OOB-resurser som ingår i PowerShell 4.0 och en beskrivning av resursens funktioner.

> [!NOTE]
> Detta är en ofullständig lista eftersom antalet OOB-resurser har vuxit med respektive version av PowerShell.

|Resurs  |Beskrivning  |
|---------|---------|
|**Fil**|Kontrollerar tillståndet för filer och kataloger. Kopierar filer från en **källa** till en **mål** och uppdaterar dem när de **källa** ändringar genom att jämföra datum, kontrollsummor och hashvärden.|
|**Arkiv**|Har packats upp Arkiv och en angiven plats. Verifierar Arkiv med en angiven **kontrollsumma**.|
|**Miljö**|Hanterar miljövariabler.|
|**Grupp**|Hanterar lokala grupper och styr medlemskap.|
|**log**|Skriver meddelanden till den `Microsoft-Windows-Desired State Configuration/Analytic` händelseloggen.|
|**Paketet**|Installerar eller avinstallerar paket med hjälp av **argument**, **LogPath**, **ReturnCode**, andra inställningar.|
|**Registret**|Hanterar registernycklar och värden.|
|**skriptet**|Låter dig utforma din egen [get testmängd](../resources/get-test-set.md) skript block.|
|**Tjänst**|Konfigurerar Windows-tjänster.|
|**Användaren** |Hanterar lokala användare och attribut.|
|**WindowsFeature**|Hanterar roller och funktioner.|
|**WindowsProcess**|Konfigurerar Windows-processer.|

OOB-resurser kan en bra utgångspunkt för vanliga åtgärder. Om OOB-resurser inte uppfyller dina behov kan du skriva din egen [anpassade resursen](../resources/authoringResource.md). Innan du skriver en anpassad resurs för att lösa problemet, bör du titta igenom stora antalet DSC-resurser som redan har skapats av både Microsoft och PowerShell-communityn.

Du kan hitta DSC-resurser i både den [PowerShell-galleriet](https://www.powershellgallery.com/) och [GitHub](https://github.com/). Du kan också installera DSC-resurser direkt från PowerShell-konsolen med [PowerShellGet](/powershell/module/powershellget/).

## <a name="installing-powershellget"></a>Installera PowerShellGet

Att fastställa om du redan har **PowerShell** hämta, eller om du vill ha hjälp med att installera den finns i guiden följande: [Installera PowerShellGet](/powershell/gallery/installing-psget).

## <a name="finding-dsc-resources-using-powershellget"></a>Hitta DSC-resurser med PowerShellGet

En gång **PowerShellGet** är installerad på datorn, kan du hitta och installera DSC-resurser som finns i den [PowerShell-galleriet](https://www.powershellgallery.com/).

Använd först den [Find-DSCResource](/powershell/module/powershellget/find-dscresource) cmdlet för att hitta DSC-resurser. När du kör `Find-DSCResource` för första gången, visas följande meddelande att installera ”NuGet-providern”.

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

När du trycker på ”y”, ”NuGet”-providern har installerats ser du en lista över DSC-resurser som du kan installera från PowerShell-galleriet.

> [!NOTE]
> Lista visas inte eftersom det är mycket stort.

Du kan också ange den `-Name` med jokertecken, parametern eller `-Filter` parametern utan jokertecken för att begränsa sökningen. Det här exemplet försöker hitta en ”tidszon” DSC-resurs med jokertecken.

> [!IMPORTANT]
> Det finns för närvarande en bugg i den `Find-DSCResource` cmdlet som förhindrar med jokertecken i både den `-Name` och `-Filter` parametrar. Det andra exemplet nedan visar en lösning med hjälp av `Where-Object`.

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

Du kan också använda `Where-Object` att hitta DSC-resurser med mer detaljerade filtrering. Den här metoden blir långsammare än att använda inbyggda filtrering parametrar.

```
PS> Find-DSCResource | Where-Object {$_.Name -like "Time*"}

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
TimeZone                            6.0.0.0    ComputerManagementDsc               PSGallery
```

Mer information om filtrering finns [Where-Object](/powershell/module/microsoft.powershell.core/where-object).

## <a name="installing-dsc-resources-using-powershellget"></a>Installera DSC-resurser med PowerShellGet

Om du vill installera en DSC-resurs i [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet, anger namnet på modulen visas under **modulen** i sökresultaten.

”Tidszon” resursen finns i modulen ”ComputerManagementDSC” så att det inte modulen i detta exempel installeras.

> [!NOTE]
> Om du inte har betrott PowerShell-galleriet, visas varningen nedan behöver bekräfta och anvisningar om hur du hur du undviker efterföljande anvisningarna på installerar.

```
PS> Install-Module -Name ComputerManagementDSC

Untrusted repository
You are installing the modules from an untrusted repository. If you trust this repository, change its
InstallationPolicy value by running the Set-PSRepository cmdlet. Are you sure you want to install the modules from
'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

Tryck på y om du vill fortsätta att installera modulen. Efter installationen, kan du kontrollera att din nya resurs är installerad med hjälp av [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource).

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

Du kan också visa andra resurser i din nyligen installerade modulen genom att ange den `-ModuleName` parametern.

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
