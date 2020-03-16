---
ms.date: 12/12/2018
keywords: DSC, PowerShell, konfiguration, installation
title: Använda Import-DSCResource
ms.openlocfilehash: a041169ad557becf7ca87641d9ce5222ee8f6beb
ms.sourcegitcommit: c97dcf1e00ef540e7464c36c88f841474060044c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/15/2020
ms.locfileid: "79406911"
---
# <a name="using-import-dscresource"></a>Använda Import-DSCResource

`Import-DScResource` är ett dynamiskt nyckelord som bara kan användas i ett konfigurations skript block. Nyckelordet `Import-DSCResource` för att importera de resurser som behövs i konfigurationen. Resurser under `$pshome` importeras automatiskt, men det anses fortfarande vara bästa praxis att importera alla resurser som används i [konfigurationen](Configurations.md).

Syntaxen för `Import-DSCResource` visas nedan.  När du anger moduler efter namn är det ett krav för att lista var och en på en ny rad.

```syntax
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName>] [-ModuleVersion <ModuleVersion>]
```

|Parameter  |Beskrivning  |
|---------|---------|
|`-Name`|DSC-resursens namn som du måste importera. Om modulnamnet anges söker kommandot efter dessa DSC-resurser i den här modulen. Annars söker kommandot igenom DSC-resurserna i alla DSC-resurs Sök vägar. Jokertecken stöds.|
|`-ModuleName`|Modulens namn eller modulens specifikation.  Om du anger vilka resurser som ska importeras från en modul försöker kommandot endast importera resurserna. Om du bara anger modulen importeras alla DSC-resurser i modulen.|
|`-ModuleVersion`|Från och med PowerShell 5,0 kan du ange vilken version av en modul som en konfiguration ska använda. Mer information finns i [Importera en angiven version av en installerad resurs](sxsresource.md).|

```powershell
Import-DscResource -ModuleName xActiveDirectory
```

## <a name="example-use-import-dscresource-within-a-configuration"></a>Exempel: Använd import-Dscresource Keyword Supports i en konfiguration

```powershell
Configuration MSDSCConfiguration
{
    # Search for and imports Service, File, and Registry from the module PSDesiredStateConfiguration.
    Import-DSCResource -ModuleName PSDesiredStateConfiguration -Name Service, File, Registry

    # Search for and import Resource1 from the module that defines it.
    # If only –Name parameter is used then resources can belong to different PowerShell modules as well.
    # TimeZone resource is from the ComputerManagementDSC module which is not installed by default.
    # As a best practice, list each requirement on a different line if possible.  This makes reviewing
    # multiple changes in source control a bit easier.
    Import-DSCResource -Name File
    Import-DSCResource -Name TimeZone

    # Search for and import all DSC resources inside the module PSDesiredStateConfiguration.
    # When specifying the modulename parameter, it is a requirement to list each on a new line.
    Import-DSCResource -ModuleName PSDesiredStateConfiguration
    # In PowerShell 5.0 and later, you can specify a ModuleVersion parameter
    Import-DSCResource -ModuleName ComputerManagementDsc -ModuleVersion 6.0.0.0
...
```

> [!NOTE]
> Det finns inte stöd för att ange flera värden för resurs namn och moduler i samma kommando. Det kan ha icke-deterministiskt beteende för vilken resurs som ska läsas in från vilken modul i samma resurs som finns i flera moduler. Kommandot nedan leder till ett fel under kompileringen.
>
> ```powershell
> Import-DscResource -Name UserConfigProvider*,TestLogger1 -ModuleName UserConfigProv,PsModuleForTestLogger
> ```

Saker att tänka på när du bara använder parametern name:

- Det är en resurs intensiv åtgärd beroende på hur många moduler som är installerade på datorn.
- Den första resursen som påträffas med det aktuella namnet läses in. Om det finns fler än en resurs med samma namn installerat kan fel resurs läsas in.

Den rekommenderade användningen är att ange `–ModuleName` med parametern `-Name`, enligt beskrivningen nedan.

Den här användningen har följande fördelar:

- Det minskar prestanda påverkan genom att begränsa Sök omfånget för den angivna resursen.
- Det definierar uttryckligen den modul som definierar resursen, vilket säkerställer att rätt resurs läses in.

> [!NOTE]
> I PowerShell 5,0 kan DSC-resurser ha flera versioner och versioner kan installeras på en dator sida vid sida. Detta implementeras genom att ha flera versioner av en resurs-modul som finns i samma modul-mapp.
> Mer information finns i [använda resurser med flera versioner](sxsresource.md).

## <a name="intellisense-with-import-dscresource"></a>IntelliSense med import-Dscresource Keyword Supports

När du redigerar DSC-konfigurationen i ISE tillhandahåller PowerShell IntelliSence för resurser och resurs egenskaper. Resurs definitioner under `$pshome` module-sökvägen läses in automatiskt. När du importerar resurser med hjälp av nyckelordet `Import-DSCResource` läggs de angivna resurs definitionerna till och IntelliSense expanderas för att inkludera den importerade resursens schema.

![Resurs-IntelliSense](media/import-dscresource/resource-intellisense.png)

> [!NOTE]
> Från och med PowerShell 5,0 har TABB-slutförande lagts till i ISE för DSC-resurser och deras egenskaper. Mer information finns i [resurser](../resources/resources.md).

När du kompilerar konfigurationen använder PowerShell de importerade resurs definitionerna för att verifiera alla resurs block i konfigurationen.
Varje resurs block verifieras med hjälp av resursens schema definition, för följande regler.

- Endast egenskaper som definieras i schemat används.
- Data typerna för varje egenskap är korrekta.
- Nycklar egenskaper har angetts.
- Ingen skrivskyddad egenskap används.
- Validering av värde mappnings typer.

Överväg följande konfiguration:

```powershell
Configuration SchemaValidationInCorrectEnumValue
{
    # It is best practice to explicitly import all resources used in your Configuration.
    # This includes resources that are imported automatically, like WindowsFeature.
    Import-DSCResource -Name WindowsFeature
    Node localhost
    {
        WindowsFeature ROLE1
        {
            Name = "Telnet-Client"
            Ensure = "Invalid"
        }
    }
}
```

Att kompilera den här konfigurationen resulterar i ett fel.

```output
PSDesiredStateConfiguration\WindowsFeature: At least one of the values 'Invalid' is not supported or valid for property 'Ensure' on class 'WindowsFeature'. Please specify only supported values: Present, Absent.
```

Med IntelliSense och schema validering kan du fånga fler fel under parsning och kompilering, vilket undviker komplikationer vid körnings tillfället.

> [!NOTE]
> Varje DSC-resurs kan ha ett namn och ett **FriendlyName** som definieras av resursens schema. Nedan visas de två första raderna i "MSFT_ServiceResource. Shema. MOF".
> ```syntax
> [ClassVersion("1.0.0"),FriendlyName("Service")]
> class MSFT_ServiceResource : OMI_BaseResource
> ```
> När du använder den här resursen i en konfiguration kan du ange **MSFT_ServiceResource** eller **tjänst**.

## <a name="powershell-v4-and-v5-differences"></a>Skillnader mellan PowerShell v4 och v5

Det finns flera skillnader som du ser när du redigerar konfigurationer i PowerShell 4,0 jämfört med PowerShell 5,0 och senare. Det här avsnittet visar skillnaderna som du ser relevanta för den här artikeln.

### <a name="multiple-resource-versions"></a>Flera resurs versioner

Det finns inte stöd för att installera och använda flera versioner av resurser sida vid sida i PowerShell 4,0. Om du upptäcker problem med att importera resurser till din konfiguration måste du kontrol lera att du bara har en version av resursen installerad.

I bilden nedan installeras två versioner av **xPSDesiredStateConfiguration** -modulen.

![Flera resurs versioner har åtgärd ATS](media/import-dscresource/multiple-resource-versions-broken.png)

Kopiera innehållet i den önskade modulens version till den översta nivån i modulens katalog.

![Flera resurs versioner har åtgärd ATS](media/import-dscresource/multiple-resource-versions-fixed.png)

### <a name="resource-location"></a>Resurs plats

När du redigerar och kompilerar konfigurationer kan dina resurser lagras i valfri katalog som anges av din [PSModulePath](/powershell/scripting/developer/module/modifying-the-psmodulepath-installation-path). I PowerShell 4,0 kräver LCM att alla DSC-resurspooler lagras under "program Files\WindowsPowerShell\Modules" eller `$pshome\Modules`. Från och med PowerShell 5,0 togs detta krav bort och resurspooler kan lagras i valfri katalog som anges av `PSModulePath`.

### <a name="moduleversion-added"></a>ModuleVersion tillagt

Från och med PowerShell 5,0 kan du med parametern `-ModuleVersion` ange vilken version av en modul som ska användas i konfigurationen.

## <a name="see-also"></a>Se även

- [Resurser](../resources/resources.md)
