---
ms.date: 12/12/2018
keywords: DSC, powershell, konfiguration, installation
title: Använda Import-DSCResource
ms.openlocfilehash: f22c741969b1429074e7307a00a5c014cf563089
ms.sourcegitcommit: 6ae5b50a4b3ffcd649de1525c3ce6f15d3669082
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/14/2019
ms.locfileid: "56265509"
---
# <a name="using-import-dscresource"></a>Använda Import-DSCResource

`Import-DScResource` är ett dynamiskt nyckelord som kan bara användas i ett skriptblock konfiguration. Den `Import-DSCResource` nyckelord för att importera alla resurser som behövs i konfigurationen. Resurser under `$phsome` importeras automatiskt, men den betraktas ändå bäst att explicit importera alla resurser som används i din [Configuration](Configurations.md).

Syntaxen för `Import-DSCResource` visas nedan.  När du anger moduler efter namn, är det ett krav att visa på en ny rad.

```syntax
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName>]
```

|Parameter  |Beskrivning  |
|---------|---------|
|`-Name`|Namn för DSC-resurs som du måste importera. Om modulnamnet anges söker kommandot efter dessa DSC-resurser i den här modulen. kommandot söker annars DSC-resurser i alla sökvägar för DSC-resurs. Jokertecken stöds.|
|`-ModuleName`|Modulnamn eller module-specifikationen.  Om du anger resurser som ska importeras från en modul görs kommandot försök att importera endast de resurserna. Om du anger modulen endast importerar kommandot alla DSC-resurser i modulen.|

```powershell
Import-DscResource -ModuleName xActiveDirectory;
```

## <a name="example-use-import-dscresource-within-a-configuration"></a>Exempel: Använda importera DSCResource i en konfiguration

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
> Att ange flera värden för namn på resursen och moduler i samma kommando stöds inte. Den kan ha icke-deterministiska beteende om vilken resurs som ska läsas in från vilken modul samma resurs finns i flera moduler. Under kommandot resulterar i fel under kompilering.
>
> ```powershell
> Import-DscResource -Name UserConfigProvider*,TestLogger1 -ModuleName UserConfigProv,PsModuleForTestLogger
> ```

Saker att tänka på när du använder bara parametern Name:

- Det är en resursintensiv åtgärd beroende på antalet moduler som installerats på datorn.
- Den kommer att läsa in den första resursen med det namnet hittades. I fall där det finns fler än en resurs med samma namn som har installerats, det gick att läsa in fel resurs.

Den rekommenderade användningen är att ange `–ModuleName` med den `-Name` parametern, som beskrivs nedan.

Denna användning har följande fördelar:

- Det minskar påverkan på prestandan genom att begränsa omfattningen av sökningen för den angivna resursen.
- Den definierar uttryckligen modulen definiera resursen, se till att rätt resurs har lästs in.

> [!NOTE]
> I PowerShell 5.0 DSC-resurser kan ha flera versioner och versioner kan installeras på en dator sida-vid-sida. Det har implementerats genom att låta flera versioner av en Resursmodul som ingår i samma modul mapp.
> Mer information finns i [av resurser med flera versioner](sxsresource.md).

## <a name="intellisense-with-import-dscresource"></a>IntelliSense med Import DSCResource

När du redigerar DSC-konfigurationen i ISE innehåller PowerShell IntelliSence för resurser och resursegenskaper. Resursdefinitionerna under den `$pshome` sökvägen modulen laddas automatiskt. När du importerar resurser med hjälp av den `Import-DSCResource` nyckelordet angivna resursdefinitionerna läggs och Intellisense utökas för att inkludera resursen importerade schemat.

![Resursen Intellisense](/media/resource-intellisense.png)

> [!NOTE]
> Från och med PowerShell 5.0, har flikavslutande lagts till ISE för DSC-resurser och deras egenskaper. Mer information finns i [resurser](../resources/resources.md).

Vid kompilering av konfigurationen, använder PowerShell importerade resursdefinitionerna för att verifiera alla resurs block i konfigurationen.
Varje resurs block verifieras med hjälp av resursens schemadefinition för följande regler.

- Endast egenskaper som definierats i schemat används.
- Datatyper av för varje egenskap är korrekta.
- Nycklar egenskaper har angetts.
- Ingen skrivskyddad egenskap används.
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

Kompilerar den här konfigurationen leder till att ett fel.

```output
PSDesiredStateConfiguration\WindowsFeature: At least one of the values ‘Invalid’ is not supported or valid for property ‘Ensure’ on class ‘WindowsFeature’. Please specify only supported values: Present, Absent.
```

Verifiering av IntelliSense och schemat kan du fånga upp mer fel under parse och sammanställning tid att undvika problem vid körning.

> [!NOTE]
> Varje DSC-resurs kan ha ett namn och en **FriendlyName** definieras av resursens schema. Nedan visas de två första raderna i ”MSFT_ServiceResource.shema.mof”.
> ```syntax
> [ClassVersion("1.0.0"),FriendlyName("Service")]
> class MSFT_ServiceResource : OMI_BaseResource
> ```
> När du använder den här resursen i en konfiguration, kan du ange **MSFT_ServiceResource** eller **tjänsten**.

## <a name="powershell-v4-and-v5-differences"></a>PowerShell v4 och v5 skillnader

Det finns flera skillnader som du kan se när redigering konfigurationer i jämfört med PowerShell 4.0. PowerShell 5.0 och senare. Det här avsnittet kommer Markera skillnaderna som visas är relevanta för den här artikeln.

### <a name="multiple-resource-versions"></a>Flera resurs-versioner

Installera och använda flera versioner av resurser sida vid sida stöds inte i PowerShell 4.0. Se till att du bara har en version av resursen installeras om du upptäcker problem importerar resurser till din konfiguration.

I bilden nedan, två versioner av den **xPSDesiredStateConfiguration** modulen är installerad.

![Flera resurs versioner fast](/media/multiple-resource-versions-broken.md)

Kopiera innehållet i din önskade Modulversion till den översta nivån i modul-katalog.

![Flera resurs versioner fast](/media/multiple-resource-versions-fixed.md)

### <a name="resource-location"></a>Resursplats

När redigering och sammanställa konfigurationer, dina resurser kan lagras i katalogen som anges av din [PSModulePath](/powershell/developer/module/modifying-the-psmodulepath-installation-path). PowerShell 4.0 i MGM kräver att alla DSC resurs moduler lagras under ”programmet Files\WindowsPowerShell\Modules” eller `$pshome\Modules`. Från och med PowerShell 5.0 kan det här kravet togs bort och resursen moduler kan lagras i katalogen som anges av `PSModulePath`.

## <a name="see-also"></a>Se även

- [Resurser](../resources/resources.md)
