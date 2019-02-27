---
ms.date: 12/12/2018
keywords: DSC, powershell, konfiguration, installation
title: Använda Import-DSCResource
ms.openlocfilehash: ee0b2f0469c6507c8f0148138198597a9e57cdd7
ms.sourcegitcommit: c581c4c8036edf55147e7bce4b00c860da6c5a8b
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/25/2019
ms.locfileid: "56803420"
---
# <a name="using-import-dscresource"></a>Använda Import-DSCResource

`Import-DScResource` är ett dynamiskt nyckelord som endast kan användas inuti en konfiguration-skriptblock. Den `Import-DSCResource` nyckelord att importera alla resurser som behövs i konfigurationen. Resurser under `$pshome` importeras automatiskt, men det betraktas fortfarande bästa praxis att uttryckligen importera alla resurser som används i din [Configuration](Configurations.md).

Syntaxen för `Import-DSCResource` visas nedan.  När du anger moduler efter namn, är det ett krav att lista på en ny rad.

```syntax
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName>]
```

|Parameter  |Beskrivning  |
|---------|---------|
|`-Name`|Namnen för DSC-resurs som du måste importera. Om modulnamnet på har angetts, söker kommandot efter dessa DSC-resurser i den här modulen. kommandot söker annars DSC-resurser i alla sökvägar för DSC-resurs. Jokertecken stöds.|
|`-ModuleName`|Modulnamn eller modulen-specifikationen.  Om du anger resurser som ska importeras från en modul, försöker kommandot Importera endast dessa resurser. Om du anger modulen endast importerar kommandot alla DSC-resurser i modulen.|

```powershell
Import-DscResource -ModuleName xActiveDirectory;
```

## <a name="example-use-import-dscresource-within-a-configuration"></a>Exempel: Använda Import-DSCResource i en konfiguration

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
    Import-DSCResource -ModuleName ComputerManagementDsc
...
```

> [!NOTE]
> Att ange flera värden för namn på resursen och moduler i samma kommando stöds inte. Den kan ha icke-deterministisk beteende om vilken resurs som ska läsas in från vilken modul samma resurs finns i flera moduler. Kommandot nedan leder till fel under kompilering.
>
> ```powershell
> Import-DscResource -Name UserConfigProvider*,TestLogger1 -ModuleName UserConfigProv,PsModuleForTestLogger
> ```

Saker att tänka på när du använder endast parametern Name:

- Det är en resurskrävande åtgärd beroende på antalet moduler som installerats på datorn.
- Den läser in den första resursen hittades med det angivna namnet. I fall där det finns fler än en resurs med samma namn som är installerad, det kan läsa in fel-resursen.

Den rekommenderade användningen är att ange `–ModuleName` med den `-Name` parameter, enligt beskrivningen nedan.

Den här användningen har följande fördelar:

- Det minskar påverkan på prestanda genom att begränsa sökomfånget för den angivna resursen.
- Den definierar uttryckligen modulen definiera resursen, att se till att rätt resurs har lästs in.

> [!NOTE]
> DSC-resurser kan ha flera versioner i PowerShell 5.0 och versioner kan installeras på en dator sida-vid-sida. Detta är implementerat genom att låta flera versioner av en Resursmodul som finns i samma mapp i modulen.
> Mer information finns i [av resurser med flera versioner](sxsresource.md).

## <a name="intellisense-with-import-dscresource"></a>IntelliSense med Import-DSCResource

När du redigerar DSC-konfigurationen i ISE, innehåller PowerShell IntelliSence för resurser och resursegenskaper. Resursdefinitionerna under den `$pshome` modulsökväg läses in automatiskt. När du importerar resurser med hjälp av den `Import-DSCResource` nyckelord, angivna resursdefinitionerna läggs och Intellisense utökas för att inkludera den importerade resursen schemat.

![Resursen Intellisense](/media/resource-intellisense.png)

> [!NOTE]
> Från och med PowerShell 5.0, har tabbifyllning lagts till ISE för DSC-resurser och deras egenskaper. Mer information finns i [resurser](../resources/resources.md).

Vid kompilering konfigurationen använder PowerShell importerade resursdefinitionerna för att verifiera alla resurs block i konfigurationen.
Varje resurs block har verifierats med hjälp av resursens schemadefinitionen, för följande regler.

- Endast de egenskaper som anges i schemat används.
- Datatyperna för varje egenskap är korrekta.
- Egenskaper för nycklar har angetts.
- Inga skrivskyddad egenskap används.
- Validering av värdet mappar typer.

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
            Name = “Telnet-Client”
            Ensure = “Invalid”
        }
    }
}
```

Kompilera den här konfigurationen uppstår ett fel.

```output
PSDesiredStateConfiguration\WindowsFeature: At least one of the values ‘Invalid’ is not supported or valid for property ‘Ensure’ on class ‘WindowsFeature’. Please specify only supported values: Present, Absent.
```

Verifiering av IntelliSense och schemat kan du fånga upp flera fel under parsning och kompilering tiden kan undvika komplikationer vid körning.

> [!NOTE]
> Varje DSC-resurs kan ha ett namn och en **FriendlyName** definieras av schemat för den resursen. Nedan visas de två första raderna för ”MSFT_ServiceResource.shema.mof”.
> ```syntax
> [ClassVersion("1.0.0"),FriendlyName("Service")]
> class MSFT_ServiceResource : OMI_BaseResource
> ```
> När du använder den här resursen i en konfiguration, kan du ange **MSFT_ServiceResource** eller **Service**.

## <a name="powershell-v4-and-v5-differences"></a>V4 och v5 skillnader i PowerShell

Det finns flera skillnader som du ser när du redigerar konfigurationer i PowerShell 4.0 vs. PowerShell 5.0 och senare. Det här avsnittet kommer markerar skillnaderna att du kan se relevanta för den här artikeln.

### <a name="multiple-resource-versions"></a>Flera versioner av resurs

Installera och använda flera versioner av resurser sida vid sida stöds inte i PowerShell 4.0. Om du upptäcker problem när du importerar resurser i din konfiguration, se till att du bara har en version av den resurs som är installerad.

I bilden nedan, två versioner av den **xPSDesiredStateConfiguration** modulen är installerad.

![Flera resurs-versioner som har åtgärdats](/media/multiple-resource-versions-broken.md)

Kopiera innehållet i önskad modul-version till den översta nivån i modulkatalogen.

![Flera resurs-versioner som har åtgärdats](/media/multiple-resource-versions-fixed.md)

### <a name="resource-location"></a>Resursplats

När redigering och kompilera konfigurationer, dina resurser kan lagras i en katalog som anges av din [PSModulePath](/powershell/developer/module/modifying-the-psmodulepath-installation-path). I PowerShell 4.0 LCM kräver alla moduler som DSC-resurs som ska lagras under ”programmet Files\WindowsPowerShell\Modules” eller `$pshome\Modules`. Från och med PowerShell 5.0 kan det här kravet togs bort och resurs-moduler kan lagras i en katalog som anges av `PSModulePath`.

## <a name="see-also"></a>Se även

- [Resurser](../resources/resources.md)
