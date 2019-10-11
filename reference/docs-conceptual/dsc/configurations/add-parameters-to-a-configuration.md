---
ms.date: 12/12/2018
keywords: DSC, PowerShell, resurs, Galleri, installation
title: Lägga till parametrar i en konfiguration
ms.openlocfilehash: 72e6c15593d11ed39d7fe8ea79f794089f410cf8
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71942120"
---
# <a name="add-parameters-to-a-configuration"></a>Lägga till parametrar i en konfiguration

Precis som-funktioner kan [konfigurationer](configurations.md) vara parameterstyrda för att tillåta fler dynamiska konfigurationer utifrån användarindata. Stegen liknar de som beskrivs i [Functions med parametrar](/powershell/module/microsoft.powershell.core/about/about_functions).

Det här exemplet börjar med en grundläggande konfiguration som konfigurerar "Spooler"-tjänsten att köras.

```powershell
Configuration TestConfig
{
    # It is best practice to explicitly import any required resources or modules.
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

## <a name="built-in-configuration-parameters"></a>Inbyggda konfigurations parametrar

Till skillnad från en Function-CmdletBinding, lägger attributet [](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute) till inga funktioner. Förutom [vanliga parametrar](/powershell/module/microsoft.powershell.core/about/about_commonparameters)kan konfigurationer också använda följande inbyggda parametrar, utan att du behöver definiera dem.

|Parameter  |Beskrivning  |
|---------|---------|
|`-InstanceName`|Används i definiera [sammansatta konfigurationer](compositeconfigs.md)|
|`-DependsOn`|Används i definiera [sammansatta konfigurationer](compositeconfigs.md)|
|`-PSDSCRunAsCredential`|Används i definiera [sammansatta konfigurationer](compositeconfigs.md)|
|`-ConfigurationData`|Används för att skicka strukturerade [konfigurations data](configData.md) för användning i konfigurationen.|
|`-OutputPath`|Används för att ange var din "@no__t -0computername\>.mof"-fil ska kompileras|

## <a name="adding-your-own-parameters-to-configurations"></a>Lägga till egna parametrar i konfigurationer

Förutom de inbyggda parametrarna kan du också lägga till egna parametrar i dina konfigurationer. Parameter blocket hamnar direkt inuti konfigurations deklarationen, precis som en funktion. Ett konfigurations parameter block ska vara utanför alla **Node** -deklarationer och över alla *import* -instruktioner. Genom att lägga till parametrar kan du göra dina konfigurationer mer robusta och dynamiska.

```powershell
Configuration TestConfig
{
    param
    (

    )
```

### <a name="add-a-computername-parameter"></a>Lägg till en ComputerName-parameter

Den första parametern som du kan lägga till är en `-Computername`-parameter så att du dynamiskt kan kompilera en ". MOF"-fil för alla `-Computername` som du skickar till din konfiguration. Precis som-funktioner kan du också definiera ett standardvärde, om användaren inte skickar något värde för `-ComputerName`

```powershell
param
(
    [String]
    $ComputerName="localhost"
)
```

I konfigurationen kan du ange din `-ComputerName`-parameter när du definierar ett Node-block.

```powershell
Node $ComputerName
{

}
```

### <a name="calling-your-configuration-with-parameters"></a>Anropa konfigurationen med parametrar

När du har lagt till parametrar i konfigurationen kan du använda dem precis som med en-cmdlet.

```powershell
TestConfig -ComputerName "server01"
```

### <a name="compiling-multiple-mof-files"></a>Kompilera flera MOF-filer

Node-blocket kan också acceptera en kommaavgränsad lista med dator namn och genererar "MOF"-filer för var och en. Du kan köra följande exempel för att generera ". MOF"-filer för alla datorer som skickas till parametern `-ComputerName`.

```powershell
Configuration TestConfig
{
    param
    (
        [String]
        $ComputerName="localhost"
    )

    # It is best practice to explicitly import any required resources or modules.
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

Förutom en `-ComputerName`-parameter kan vi lägga till parametrar för tjänstens namn och tillstånd. Följande exempel lägger till ett parameter block med en `-ServiceName`-parameter och använder den för att dynamiskt definiera **tjänst** resurs blocket. Den lägger också till en `-State`-parameter för att dynamiskt definiera **status** i **tjänst** resurs blocket.

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

    # It is best practice to explicitly import any required resources or modules.
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
> I fler advacned-scenarier kan det vara mer meningsfullt att flytta dina dynamiska data till en strukturerad [konfigurations data](configData.md).

Exempel konfigurationen tar nu en dynamisk `$ServiceName`, men om ingen anges kompileras resultatet i ett fel. Du kan lägga till ett standardvärde som det här exemplet.

```powershell
[String]
$ServiceName="Spooler"
```

I den här instansen är det mer meningsfullt att bara tvinga användaren att ange ett värde för parametern `$ServiceName`. Med attributet `parameter` kan du lägga till ytterligare verifiering och stöd för pipelinering i konfigurationens parametrar.

Utöver parameter deklarationen lägger du till attributet `parameter` som i exemplet nedan.

```powershell
[parameter()]
[String]
$ServiceName
```

Du kan ange argument för varje `parameter`-attribut för att kontrol lera aspekter av den definierade parametern. I följande exempel görs en **obligatorisk** parameter `$ServiceName`.

```powershell
[parameter(Mandatory)]
[String]
$ServiceName
```

För parametern `$State` vill vi hindra användaren från att ange värden utanför en fördefinierad uppsättning (som att köra, stoppa) `ValidationSet*`attribute skulle hindra användaren från att ange värden utanför en fördefinierad uppsättning (t. ex. igång, stoppad). I följande exempel läggs attributet `ValidationSet` till i parametern `$State`. Eftersom vi inte vill att parametern `$State` ska vara **obligatorisk**måste vi lägga till ett standardvärde för den.

```powershell
[ValidateSet("Running", "Stopped")]
[String]
$State="Running"
```

> [!NOTE]
> Du behöver inte ange ett `parameter`-attribut när du använder ett `validation`-attribut.

Du kan läsa mer om attributet `parameter` och verifiering i [about_Functions_Advanced_Parameters](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters).

## <a name="fully-parameterized-configuration"></a>Helt parametriserad konfiguration

Nu har vi en parametriserad konfiguration som tvingar användaren att ange en `-InstanceName`, `-ServiceName` och verifierar `-State`-parametern.

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

    # It is best practice to explicitly import any required resources or modules.
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

- [Skriv hjälp för DSC-konfigurationer](configHelp.md)
- [Dynamiska konfigurationer](flow-control-in-configurations.md)
- [Använd konfigurations data i dina konfigurationer](configData.md)
- [Separata konfigurations-och miljö data](separatingEnvData.md)