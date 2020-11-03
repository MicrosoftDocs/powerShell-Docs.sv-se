---
description: Funktion
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_function_provider?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Funktions leverantör
ms.openlocfilehash: 8789ceadbefed2dca47c10c26204f3e9ae82d36e
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270201"
---
# <a name="function-provider"></a>Funktions leverantör

## <a name="provider-name"></a>Providernamn
Funktion

## <a name="drives"></a>Enheter

`Function:`

## <a name="capabilities"></a>Funktioner

**ShouldProcess**

## <a name="short-description"></a>Kort beskrivning

Ger åtkomst till de funktioner som definierats i PowerShell.

## <a name="detailed-description"></a>Detaljerad beskrivning

Med PowerShell **Function** -providern kan du hämta, lägga till, ändra, radera och ta bort funktioner och filter i PowerShell.

En funktion är ett namngivet kodblock som utför en åtgärd. När du skriver in funktions namnet körs koden i funktionen. Ett filter är ett namngivet kodblock som upprättar villkor för en åtgärd. Du kan ange namnet på filtret i stället för villkoret, t. ex. i ett `Where-Object` kommando.

**Funktions** enheten är en planad namnrymd som bara innehåller funktionen och filtrerar objekt. Varken Functions eller filter har underordnade objekt.

**Funktions** leverantören stöder följande cmdletar, som beskrivs i den här artikeln.

- [Get-location](xref:Microsoft.PowerShell.Management.Get-Location)
- [Ange plats](xref:Microsoft.PowerShell.Management.Set-Location)
- [Hämta objekt](xref:Microsoft.PowerShell.Management.Get-Item)
- [Nytt objekt](xref:Microsoft.PowerShell.Management.New-Item)
- [Ta bort objekt](xref:Microsoft.PowerShell.Management.Remove-Item)
- [Rensa objekt](xref:Microsoft.PowerShell.Management.Clear-Item)

## <a name="types-exposed-by-this-provider"></a>Typer som exponeras av denna provider

Varje funktion är en instans av klassen [system. Management. Automation. FunctionInfo](/dotnet/api/system.management.automation.functioninfo) . Varje filter är en instans av klassen [system. Management. Automation. FilterInfo](/dotnet/api/system.management.automation.filterinfo) .

## <a name="navigating-the-function-drive"></a>Navigera i funktions enheten

**Funktions** leverantören visar dess data lager på `Function:` enheten. Om du vill arbeta med funktioner kan du ändra platsen till `Function:` enheten ( `Set-Location Function:` ). Eller så kan du arbeta från en annan PowerShell-enhet. Om du vill referera till en funktion från en annan plats använder du enhets namnet ( `Function:` ) i sökvägen.

```powershell
Set-Location Function:
```

Om du vill återgå till en fil systemen het skriver du enhetens namn. Skriv till exempel:

```powershell
Set-Location C:
```

Du kan också arbeta med **funktions** leverantören från någon annan PowerShell-enhet. Om du vill referera till en funktion från en annan plats använder du enhets namnet `Function:` i sökvägen.

> [!NOTE]
> PowerShell använder alias för att ge dig ett välbekant sätt att arbeta med providerns sökvägar. Kommandon som `dir` och `ls` är nu alias för [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` är ett alias för [set-location](xref:Microsoft.PowerShell.Management.Set-Location). och `pwd` är ett alias för [Get-location](xref:Microsoft.PowerShell.Management.Get-Location).

## <a name="getting-functions"></a>Hämta funktioner

Det här kommandot hämtar listan över alla funktioner i den aktuella sessionen. Du kan använda det här kommandot från valfri PowerShell-enhet.

```powershell
Get-ChildItem -Path Function:
```

Funktions leverantören har inga behållare, så kommandot ovan har samma påverkan när den används med `Get-ChildItem` .

```powershell
Get-ChildItem -Path Function:
```

Du kan hämta en funktions definition genom att komma åt **definitions** egenskapen, som du ser nedan.

```powershell
(Get-Item -Path function:more).Definition
```

Du kan också hämta en funktions definition med hjälp av dess Provider-sökväg som föregås av dollar tecknet ( `$` ).

```powershell
$function:more
```

### <a name="getting-selected-functions"></a>Hämtar markerade funktioner

Detta kommando hämtar `man` funktionen från `Function:` enheten. Den använder `Get-Item` cmdleten för att hämta funktionen. Pipeline-operatorn ( `|` ) skickar resultatet till `Format-Table` . `-Wrap`Parametern dirigerar text som inte får plats på raden till nästa rad. `-Autosize`Parametern ändrar storlek på tabell kolumnerna för att rymma texten.

```powershell
Get-Item -Path man | Format-Table -Wrap -Autosize
```

### <a name="working-with-function-provider-paths"></a>Arbeta med sökvägar för funktions leverantörer

De här kommandona hämtar funktionen med namnet `c:` . Det första kommandot kan användas i vilken enhet som helst. Det andra kommandot används i `Function:` enheten. Eftersom namnet slutar i ett kolon, vilket är syntaxen för en enhet, måste du kvalificera sökvägen med enhets namnet. I `Function:` enheten kan du använda något av formaten. I det andra kommandot representerar punkten ( `.` ) den aktuella platsen.

```
PS C:\> Get-Item -Path Function:c:
PS Function:\> Get-Item -Path .\c:
```

## <a name="creating-a-function"></a>Skapa en funktion

Detta kommando använder `New-Item` cmdleten för att skapa en funktion som kallas `Win32:` .
Uttrycket i klamrar är det skript block som representeras av funktions namnet.

```powershell
New-Item -Path Function:Win32: -Value {Set-Location C:\Windows\System32}
```

Du kan också skapa en funktion genom att skriva den på PowerShell-kommandoraden. Till exempel TPE `Function:Win32: {Set-Location C:\Windows\System32}` . Om du är i `Function:` enheten kan du utelämna enhets namnet.

## <a name="deleting-a-function"></a>Ta bort en funktion

Det här kommandot tar bort `more:` funktionen från den aktuella sessionen.

```powershell
Remove-Item Function:more:
```

## <a name="changing-a-function"></a>Ändra en funktion

Detta kommando använder `Set-Item` cmdleten för att ändra `prompt` funktionen så att den visar tiden före sökvägen.

```powershell
Set-Item -Path Function:prompt -Value {
  'PS '+ (Get-Date -Format t) + " " + (Get-Location) + '> '
  }
```

### <a name="rename-a-function"></a>Byta namn på en funktion

Detta kommando använder `Rename-Item` cmdleten för att ändra namnet på `help` funktionen till `gh` .

```powershell
Rename-Item -Path Function:help -NewName gh
```

## <a name="copying-a-function"></a>Kopiera en funktion

Detta kommando kopierar `prompt` funktionen till `oldPrompt` , och skapar ett nytt namn för skript blocket som är associerat med prompt-funktionen.
Du kan använda detta för att spara den ursprungliga prompt-funktionen om du planerar att ändra den.
Egenskapen **Options** för den nya funktionen har värdet `None` . Om du vill ändra värdet för egenskapen **alternativ** använder du `Set-Item` .

```powershell
Copy-Item -Path Function:prompt -Destination Function:oldPrompt
```

## <a name="dynamic-parameters"></a>Dynamiska parametrar

Dynamiska parametrar är cmdlet-parametrar som läggs till av en PowerShell-Provider och är bara tillgängliga när cmdleten används i den provider-aktiverade enheten.

### <a name="options-systemmanagementautomationscopeditemoptions"></a>Alternativ < [system. Management. Automation. ScopedItemOptions] >

Anger värdet för egenskapen **Options** för en funktion.

- `None`: Inga alternativ. `None` används som standard.
- `Constant`: Det går inte att ta bort funktionen och dess egenskaper kan inte ändras. `Constant` är bara tillgängligt när du skapar en funktion.
  Du kan inte ändra alternativet för en befintlig funktion till `Constant` .
- `Private`: Funktionen är endast synlig i det aktuella omfånget
- (inte i underordnade omfång).
- `ReadOnly`: Det går inte att ändra egenskaperna för funktionen, förutom med `-Force` parametern. Du kan använda `Remove-Item` för att ta bort funktionen.
- `AllScope`: Funktionen kopieras till alla nya omfattningar som skapas.

### <a name="cmdlets-supported"></a>Cmdlets som stöds

- [Nytt objekt](xref:Microsoft.PowerShell.Management.New-Item)

- [Ange objekt](xref:Microsoft.PowerShell.Management.Set-Item)

## <a name="using-the-pipeline"></a>Använda pipelinen

Provider-cmdletar accepterar pipeline-ininformation. Du kan använda pipelinen för att förenkla uppgiften genom att skicka leverantörs data från en cmdlet till en annan provider-cmdlet.
Mer information om hur du använder pipelinen med Provider-cmdletar finns i cmdlet-referenser som finns i den här artikeln.

## <a name="getting-help"></a>Få hjälp

Från och med Windows PowerShell 3,0 kan du hämta anpassade hjälp avsnitt för provider-cmdletar som förklarar hur dessa cmdletar fungerar i en fil systemen het.

Om du vill få hjälp avsnitten som är anpassade för fil system enheten kör du ett [Get-Help-](xref:Microsoft.PowerShell.Core.Get-Help) kommando i en fil system enhet eller använder `-Path` parametern för [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) för att ange en fil systemen het.

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path function:
```

## <a name="see-also"></a>Se även

[about_Functions](../About/about_Functions.md)

[about_Providers](../About/about_Providers.md)

