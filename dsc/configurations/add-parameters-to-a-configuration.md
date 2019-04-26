---
ms.date: 12/12/2018
keywords: DSC, powershell, resurs, galleriet, inställning
title: Lägga till parametrar i en konfiguration
ms.openlocfilehash: 15213404f0cdd6416baf1f83af91b8f5279cc97f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080268"
---
# <a name="add-parameters-to-a-configuration"></a>Lägga till parametrar i en konfiguration

Ha funktioner, [konfigurationer](configurations.md) kan parameteriseras för att tillåta mer dynamiska konfigurationer baserat på indata från användaren. Stegen är samma som beskrivs i [funktioner med parametrar](/powershell/module/microsoft.powershell.core/about/about_functions).

Det här exemplet börjar med en grundläggande konfiguration som konfigurerar ”Utskriftshanteraren” till ”körs”.

```powershell
Configuration TestConfig
{
    # It is best practice to implicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node localhost
    {
        Service 'Spooler'
        {
            Name = 'Spooler'
            State = 'Running'
        }
    }
}
```

## <a name="built-in-configuration-parameters"></a>Inbyggda konfigurationsparametrar

Till skillnad från en funktion dock den [CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute) attributet lägger till inga funktioner. Förutom [gemensamma parametrar](/powershell/module/microsoft.powershell.core/about/about_commonparameters), konfigurationer kan också använda följande inbyggda parametrar, utan att du behöver definiera dem.

|Parameter  |Beskrivning  |
|---------|---------|
|`-InstanceName`|Används för att definiera [sammansatta konfigurationer](compositeconfigs.md)|
|`-DependsOn`|Används för att definiera [sammansatta konfigurationer](compositeconfigs.md)|
|`-PSDSCRunAsCredential`|Används för att definiera [sammansatta konfigurationer](compositeconfigs.md)|
|`-ConfigurationData`|Används för att skicka i strukturerade [konfigurationsdata](configData.md) för användning i konfigurationen.|
|`-OutputPath`|Används för att ange var din ”\<computername\>.mof” filen kompileras|

## <a name="adding-your-own-parameters-to-configurations"></a>Att lägga till dina egna parametrar konfigurationer

Förutom de inbyggda parametrarna, kan du också lägga till dina egna parametrar dina konfigurationer. Parameterblocket går direkt i deklarationen konfiguration, precis som en funktion. En konfiguration Parameterblocket bör finnas utanför någon **nod** deklarationer, och senare någon *importera* instruktioner. Genom att lägga till parametrar, kan du göra dina konfigurationer mer stabilt och dynamisk.

```powershell
Configuration TestConfig
{
    param
    (

    )
```

### <a name="add-a-computername-parameter"></a>Lägg till en ComputerName-parameter

Den första parametern som du kan lägga till är en `-Computername` parametern så att du kan dynamiskt sammanställa en ”.mof”-fil för alla `-Computername` du skickar till din konfiguration. Som Functions, kan du också definiera ett standardvärde om användaren inte skickar ett värde för `-ComputerName`

```powershell
param
(
    [String]
    $ComputerName="localhost"
)
```

I din konfiguration kan du sedan ange din `-ComputerName` parameter när du definierar din nod-block.

```powershell
Node $ComputerName
{

}
```

### <a name="calling-your-configuration-with-parameters"></a>Anropar din konfiguration med parametrar

När du har lagt till parametrar i din konfiguration, kan du använda dem precis som med en cmdlet.

```powershell
TestConfig -ComputerName "server01"
```

### <a name="compiling-multiple-mof-files"></a>Kompilera flera MOF-filer

Noden blocket kan också acceptera en kommaavgränsad lista med datornamn och genererar MOF-filerna för var och en. Du kan köra i följande exempel för att generera MOF-filerna för alla datorer som skickas till den `-ComputerName` parametern.

```powershell
Configuration TestConfig
{
    param
    (
        [String]
        $ComputerName="localhost"
    )

    # It is best practice to implicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node $ComputerName
    {
        Service 'Spooler'
        {
            Name = 'Spooler'
            State = 'Running'
        }
    }
}

TestConfig -ComputerName "server01", "server02", "server03"
```

## <a name="advanced-parameters-in-configurations"></a>Avancerade parametrar i konfigurationer

Förutom en `-ComputerName` parameter, kan vi lägga till parametrar för tjänstens namn och status. I följande exempel läggs en Parameterblocket med en `-ServiceName` parametern och används för att definiera dynamiskt den **Service** resource block. Läggs även en `-State` parametern för att definiera dynamiskt den **tillstånd** i den **Service** resource block.

```powershell
Configuration TestConfig
{
    param
    (
        [String]
        $ServiceName,

        [String]
        $State,

        [String]
        $ComputerName="localhost"
    )

    # It is best practice to implicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node $ComputerName
    {
        Service $ServiceName
        {
            Name = $ServiceName
            State = $State
        }
    }
}
```

> [!NOTE]
> I fler advacned scenarier kan det vara bättre att flytta dynamiska data till en strukturerade [konfigurationsdata](configData.md).

Exempel konfiguration nu tar en dynamisk `$ServiceName`, men om inget annat anges, kompilera uppstår ett fel. Du kan lägga till ett standardvärde som i följande exempel.

```powershell
[String]
$ServiceName="Spooler"
```

I den här instansen dock är det mer praktiskt att bara tvinga användaren att ange ett värde för den `$ServiceName` parametern. Den `parameter` attribut kan du lägga till ytterligare verifiering och pipeline stöd till parametrar för din konfiguration.

Ovanför alla parameterdeklaration lägger du till den `parameter` attributet block som i exemplet nedan.

```powershell
[parameter()]
[String]
$ServiceName
```

Du kan ange argument för varje `parameter` attribut för att kontrollen aspekter av definierad parameter. I följande exempel gör den `$ServiceName` en **obligatorisk** parametern.

```powershell
[parameter(Mandatory)]
[String]
$ServiceName
```

För den `$State` parametern, som vi vill hindra användaren från att ange värden utanför en fördefinierad uppsättning (som körs, stoppad) den `ValidationSet*`attributet skulle hindra användaren från att ange värden utanför en fördefinierad uppsättning (till exempel drift, Stoppats). I följande exempel läggs den `ValidationSet` attributet den `$State` parametern. Eftersom vi inte vill göra den `$State` parametern **obligatorisk**, vi måste lägga till ett standardvärde för den.

```powershell
[ValidateSet("Running", "Stopped")]
[String]
$State="Running"
```

> [!NOTE]
> Du behöver inte ange en `parameter` attribut när du använder en `validation` attribut.

Du kan läsa mer om den `parameter` och verifiering attribut i [about_Functions_Advanced_Parameters](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters.md).

## <a name="fully-parameterized-configuration"></a>Fullständigt parametriserade konfiguration

Nu har vi en parametriserade konfiguration som tvingar användaren att ange en `-InstanceName`, `-ServiceName`, och för att kontrollera den `-State` parametern.

```powershell
Configuration TestConfig
{
    param
    (
        [parameter(Mandatory)]
        [String]
        $ServiceName,

        [ValidateSet("Running","Stopped")]
        [String]
        $State="Running",

        [String]
        $ComputerName="localhost",
    )

    # It is best practice to implicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node localhost
    {
        Service $ServiceName
        {
            Name = $ServiceName
            State = $State
        }
    }
}
```

## <a name="see-also"></a>Se även

- [Skriva hjälp för DSC-konfigurationer](configHelp.md)
- [Dynamiska konfigurationer](flow-control-in-configurations.md)
- [Använd konfigurationsdata i dina konfigurationer](configData.md)
- [Separata konfigurations- och miljödata](separatingEnvData.md)
