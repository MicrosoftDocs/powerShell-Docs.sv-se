---
description: Miljö
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_environment_provider?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Miljö leverantör
ms.openlocfilehash: f50558ba23d21b5ca145a06086c1c6d9b1fcd3bf
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710627"
---
# <a name="environment-provider"></a>Miljö leverantör

## <a name="provider-name"></a>Providernamn
Miljö

## <a name="drives"></a>Enheter

`Env:`

## <a name="capabilities"></a>Funktioner

**ShouldProcess**

## <a name="short-description"></a>Kort beskrivning

Ger åtkomst till Windows-miljövariabler.

## <a name="detailed-description"></a>Detaljerad beskrivning

Med PowerShell **-operatören** kan du hämta, lägga till, ändra, radera och ta bort miljövariabler och värden i PowerShell.

**Miljövariabler är** dynamiskt namngivna variabler som beskriver i vilken miljö dina program körs. Windows och PowerShell använder miljövariabler för att lagra beständig information som påverkar system-och process körning. Till skillnad från PowerShell-variabler omfattas miljövariabler inte av omfattnings begränsningar.

**Miljö** enheten är ett plant namn område som innehåller miljövariablerna som är speciella för den aktuella användarens session. Miljövariablerna har inga underordnade objekt.

- **Miljö** leverantören stöder följande cmdletar, som beskrivs i den här artikeln.

- [Get-location](xref:Microsoft.PowerShell.Management.Get-Location)
- [Ange plats](xref:Microsoft.PowerShell.Management.Set-Location)
- [Hämta objekt](xref:Microsoft.PowerShell.Management.Get-Item)
- [Nytt objekt](xref:Microsoft.PowerShell.Management.New-Item)
- [Ta bort objekt](xref:Microsoft.PowerShell.Management.Remove-Item)
- [Rensa objekt](xref:Microsoft.PowerShell.Management.Clear-Item)

## <a name="types-exposed-by-this-provider"></a>Typer som exponeras av denna provider

Varje miljö variabel är en instans av klassen [system. Collections. typen DictionaryEntry](/dotnet/api/system.collections.dictionaryentry) . Namnet på variabeln är ord listans nyckel. Värdet för miljö variabeln är värdet för ord listan.

## <a name="navigating-the-environment-drive"></a>Navigera i miljö enheten

- **Miljö** leverantören exponerar data lagret i `Env:` enheten. Ändra platsen till `Env:` enheten ( `Set-Location Env:` ) eller arbeta från en annan PowerShell-enhet om du vill arbeta med miljövariabler. Om du vill referera till en miljö variabel från en annan plats använder du `Env:` enhets namnet i sökvägen.

```powershell
Set-Location Env:
```

Om du vill återgå till en fil systemen het skriver du enhetens namn. Skriv till exempel:

```powershell
Set-Location C:
```

Du kan också arbeta med- **miljö** leverantören från andra PowerShell-enheter. Om du vill referera till en miljö variabel från en annan plats använder du enhets namnet `Env:` i sökvägen.

- **Miljö** leverantören exponerar också miljövariabler med hjälp av ett variabel prefix `$env:` .  Följande kommando visar innehållet i miljövariabeln **ProgramFiles** . Det `$env:` variabla prefixet kan användas från valfri PowerShell-enhet.

```
PS C:\> $env:ProgramFiles
C:\Program Files
```

Du kan också ändra värdet för en miljö variabel med hjälp av `$env:` variabeln prefix.  Alla ändringar som gjorts gäller bara för den aktuella PowerShell-sessionen så länge den är aktiv.

> [!NOTE]
> PowerShell använder alias för att ge dig ett välbekant sätt att arbeta med providerns sökvägar. Kommandon som `dir` och `ls` är nu alias för [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` är ett alias för [set-location](xref:Microsoft.PowerShell.Management.Set-Location). och `pwd` är ett alias för [Get-location](xref:Microsoft.PowerShell.Management.Get-Location).

## <a name="getting-environment-variables"></a>Hämtar miljövariabler

Det här kommandot visar alla miljövariabler i den aktuella sessionen.

```powershell
Get-Item -Path Env:
```

Du kan använda det här kommandot från valfri PowerShell-enhet.

Det finns inga behållare i miljö leverantören, så kommandot ovan har samma påverkan när den används med `Get-ChildItem` .

```powershell
Get-ChildItem -Path Env:
```

### <a name="get-a-selected-environment-variable"></a>Hämta en vald miljö variabel

Det här kommandot hämtar `WINDIR` miljövariabeln.

```powershell
Get-ChildItem -Path Env:windir
```

Du kan också använda formatet variabel prefix.

```powershell
$env:windir
```

## <a name="create-an-environment-variable"></a>Skapa en miljö variabel

Det här kommandot skapar `USERMODE` miljövariabeln med värdet "icke-admin". `-Path`Parametervärdet skapar det nya objektet i `Env:` enheten. Den nya miljö variabeln kan bara användas i den aktuella PowerShell-sessionen så länge den är aktiv.

```powershell
PS C:\> New-Item -Path Env: -Name USERMODE -Value Non-Admin
```

## <a name="changing-an-environment-variable"></a>Ändra en miljö variabel

### <a name="rename-an-environment-variable"></a>Byta namn på en miljö variabel

Detta kommando använder `Rename-Item` cmdleten för att ändra namnet på den `USERMODE` miljö variabel som du skapade till `USERROLE` . Ändra inte namnet på en miljö variabel som används i systemet. Även om dessa ändringar endast påverkar den aktuella sessionen kan det leda till att systemet eller ett program fungerar felaktigt.

```powershell
Rename-Item -Path Env:USERMODE -NewName USERROLE
```

### <a name="change-an-environment-variable"></a>Ändra en miljö variabel

Det här kommandot använder `Set-Item` cmdleten för att ändra värdet för `USERROLE` miljövariabeln till "administratör".

```powershell
Set-Item -Path Env:USERROLE -Value Administrator
```

## <a name="copy-an-environment-variable"></a>Kopiera en miljö variabel

Det här kommandot kopierar värdet för `USERROLE` miljö variabeln till `USERROLE2` miljövariabeln.

```powershell
Copy-Item -Path Env:USERROLE -Destination Env:USERROLE2
```

## <a name="remove-an-environment-variable"></a>Ta bort en miljö variabel

Det här kommandot tar bort `USERROLE2` miljövariabeln från den aktuella sessionen.

```powershell
Remove-Item -Path Env:USERROLE2
```

## <a name="remove-an-environment-variable-with-clear-item"></a>Ta bort en miljö variabel med Clear-Item

Det här kommandot tar bort `USERROLE` miljövariabeln genom att rensa dess värde.

```powershell
Clear-Item -Path Env:USERROLE
```

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
Get-Help Get-ChildItem -Path env:
```

## <a name="see-also"></a>Se även

[about_Providers](../About/about_Providers.md)

