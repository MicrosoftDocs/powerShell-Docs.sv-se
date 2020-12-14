---
description: Alias
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_alias_provider?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Aliasresurspost
ms.openlocfilehash: d6bfbaf878a6d971b1e01d963faec8c8ece5d1fc
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710723"
---
# <a name="alias-provider"></a>Aliasresurspost

## <a name="provider-name"></a>Providernamn
Alias

## <a name="drives"></a>Enheter

`Alias:`

## <a name="capabilities"></a>Funktioner

**ShouldProcess**

## <a name="short-description"></a>Kort beskrivning

Ger åtkomst till PowerShell-alias och de värden som de representerar.

## <a name="detailed-description"></a>Detaljerad beskrivning

Med PowerShell- **Ali** -leverantören kan du hämta, lägga till, ändra, radera och ta bort alias i PowerShell.

Ett alias är ett alternativt namn för en cmdlet, Function, körbar fil, inklusive skript. PowerShell innehåller en uppsättning inbyggda alias. Du kan lägga till egna alias till den aktuella sessionen och till din PowerShell-profil.

**Ali Aset** är ett platt namn område som bara innehåller Ali-objekten.
Aliasen har inga underordnade objekt.

**Alias** -providern stöder följande cmdlets, som beskrivs i den här artikeln.

- [Get-location](xref:Microsoft.PowerShell.Management.Get-Location)
- [Ange plats](xref:Microsoft.PowerShell.Management.Set-Location)
- [Hämta objekt](xref:Microsoft.PowerShell.Management.Get-Item)
- [Nytt objekt](xref:Microsoft.PowerShell.Management.New-Item)
- [Ta bort objekt](xref:Microsoft.PowerShell.Management.Remove-Item)
- [Rensa objekt](xref:Microsoft.PowerShell.Management.Clear-Item)

PowerShell innehåller en uppsättning cmdletar som är utformade för att visa och ändra alias. När du använder **alias** -cmdletar behöver du inte ange `Alias:` enheten i namnet. Den här artikeln beskriver inte hur du arbetar med **alias** -cmdletar.

- [Exportera-alias](xref:Microsoft.PowerShell.Utility.Export-Alias)
- [Get-alias](xref:Microsoft.PowerShell.Utility.Get-Alias)
- [Importera-alias](xref:Microsoft.PowerShell.Utility.Import-Alias)
- [Nytt-alias](xref:Microsoft.PowerShell.Utility.New-Alias)
- [Set-alias](xref:Microsoft.PowerShell.Utility.Set-Alias)

## <a name="types-exposed-by-this-provider"></a>Typer som exponeras av denna provider

Varje alias är en instans av klassen [system. Management. Automation. AliasInfo](/dotnet/api/system.management.automation.aliasinfo) .

## <a name="navigating-the-alias-drive"></a>Navigera mellan Ali medie enheten

**Ali Aset** visar data lagret i `Alias:` enheten. Om du vill arbeta med alias kan du ändra din plats till `Alias:` enheten med hjälp av följande kommando:

```powershell
Set-Location Alias:
```

Om du vill återgå till en fil systemen het skriver du enhetens namn. Skriv till exempel:

```powershell
Set-Location C:
```

Du kan också arbeta med Ali Aset provider från andra PowerShell-enheter. Om du vill referera till ett alias från en annan plats använder du `Alias:` enhets namnet i sökvägen.

> [!NOTE]
> PowerShell använder alias för att ge dig ett välbekant sätt att arbeta med providerns sökvägar. Kommandon som `dir` och `ls` är nu alias för [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` är ett alias för [set-location](xref:Microsoft.PowerShell.Management.Set-Location). och `pwd` är ett alias för [Get-location](xref:Microsoft.PowerShell.Management.Get-Location).

### <a name="displaying-the-contents-of-the-alias-drive"></a>Visar innehållet i aliaset: enhet

Det här kommandot hämtar listan över alla alias när den aktuella platsen är `Alias:` enheten. Ett jokertecken används `*` för att ange allt innehåll på den aktuella platsen.

```powershell
PS Alias:\> Get-Item -Path *
```

I `Alias:` enheten, en punkt `.` som representerar den aktuella platsen och ett jokertecken `*` , som representerar alla objekt på den aktuella platsen, har samma resultat. Till exempel `Get-Item -Path .` eller `Get-Item \*` skapa samma resultat.

Ali Aset-providern har inga behållare, så kommandot ovan har samma påverkan när den används med `Get-ChildItem` .

```powershell
Get-ChildItem -Path Alias:
```

### <a name="get-a-selected-alias"></a>Hämta ett markerat alias

Det här kommandot hämtar `ls` aliaset.
Eftersom det innehåller sökvägen kan du använda den på valfri PowerShell-enhet.

```powershell
Get-Item -Path Alias:ls
```

Om du är i `Alias:` enheten kan du utelämna enhets namnet från sökvägen.

Du kan också hämta definitionen för ett alias genom att förlösa providerns sökväg med dollar tecknet ( `$` ).

```powershell
$Alias:ls
```

### <a name="get-all-aliases-for-a-specific-cmdlet"></a>Hämta alla alias för en angiven cmdlet

Det här kommandot hämtar en lista över de alias som är associerade med `Get-ChildItem` cmdleten. Den använder **definitions** egenskapen som lagrar cmdlet-namnet.

```powershell
Get-Item -Path Alias:* | Where-Object {$_.Definition -eq "Get-ChildItem"}
```

## <a name="creating-aliases"></a>Skapa alias

### <a name="create-an-alias-from-the-alias-drive"></a>Skapa ett alias från aliaset: enhet

Det här kommandot skapar `serv` aliaset för `Get-Service` cmdleten. Eftersom den aktuella platsen finns i `Alias:` enheten `-Path` behövs ingen parameter.

Det här kommandot använder också den `-Options` dynamiska parametern för att ange alternativet **AllScope** i aliaset. `-Options`Parametern är bara tillgänglig i `New-Item` cmdleten när du befinner dig i `Alias:` enheten. Punkten ( `.` ) visar den aktuella katalogen, som är Ali Aset.

```
PS Alias:\> New-Item -Path . -Name serv -Value Get-Service -Options "AllScope"
```

### <a name="create-an-alias-with-an-absolute-path"></a>Skapa ett alias med en absolut sökväg

Du kan skapa ett alias för alla objekt som anropar ett kommando.
Det här kommandot skapar `np` alias för `Notepad.exe` .

```powershell
New-Item -Path Alias:np -Value c:\windows\notepad.exe
```

### <a name="create-an-alias-to-a-new-function"></a>Skapa ett alias för en ny funktion

Du kan skapa ett alias för vilken funktion som helst. Du kan använda den här funktionen för att skapa ett alias som innehåller både en cmdlet och dess parametrar.

Det första kommandot skapar `CD32` funktionen, som ändrar den aktuella katalogen till `System32` katalogen. Det andra kommandot skapar `go` aliaset för `CD32` funktionen.

När kommandot har slutförts kan du använda antingen `CD32` eller `go` för att anropa funktionen.

```powershell
function CD32 {Set-Location -Path c:\windows\system32}
Set-Item -Path Alias:go -Value CD32
```

## <a name="changing-aliases"></a>Ändra alias

### <a name="change-the-options-of-an-alias"></a>Ändra alternativen för ett alias

Du kan använda `Set-Item` cmdleten med den `-Options` dynamiska parametern för att ändra värdet för `-Options` egenskapen för ett alias.

Det här kommandot anger **AllScope** och **ReadOnly** -alternativen för `dir` aliaset. Kommandot använder `-Options` `Set-Item` cmdletens dynamiska parameter. `-Options`Parametern är tillgänglig i `Set-Item` när du använder den med **alias** -eller **funktions** leverantören.

```powershell
Set-Item -Path Alias:dir -Options "AllScope,ReadOnly"
```

### <a name="change-an-aliases-referenced-command"></a>Ändra ett alias som refereras till kommandot

Detta kommando använder `Set-Item` cmdleten för att ändra `gp` alias så att det representerar `Get-Process` cmdleten i stället för `Get-ItemProperty` cmdleten.
`-Force`Parametern är obligatorisk eftersom värdet på egenskapen **alternativ** för `gp` aliaset är inställt på `ReadOnly` . Eftersom kommandot skickas inifrån `Alias:` enheten, anges inte enheten i sökvägen.

```powershell
Set-Item -Path gp -Value Get-Process -Force
```

Ändringen påverkar de fyra egenskaperna som definierar associationen mellan aliaset och kommandot. Skriv följande kommando om du vill visa ändrings resultatet:

```powershell
Get-Item -Path gp | Format-List -Property *
```

### <a name="rename-an-alias"></a>Byta namn på ett alias

Det här kommandot använder `Rename-Item` cmdleten för att ändra `popd` aliaset till `pop` .

```powershell
Rename-Item -Path Alias:popd -NewName pop
```

## <a name="copying-an-alias"></a>Kopierar ett alias

Det här kommandot kopierar `pushd` aliaset så att ett nytt `push` alias skapas för `Push-Location` cmdleten.

När det nya aliaset skapas har egenskapen **Description** värdet null.
Och dess **alternativ** egenskap har värdet `None` . Om kommandot utfärdas inifrån `Alias:` enheten kan du utelämna enhets namnet från `-Path` parameterns värde.

```powershell
Copy-Item -Path Alias:pushd -Destination Alias:push
```

## <a name="deleting-an-alias"></a>Tar bort ett alias

Det här kommandot tar bort `serv` aliaset från den aktuella sessionen.
Du kan använda det här kommandot i valfri PowerShell-enhet.

```powershell
Remove-Item -Path Alias:serv
```

Det här kommandot tar bort alias som börjar med "s".
Det tar inte bort skrivskyddade alias.

```powershell
Clear-Item -Path Alias:s*
```

### <a name="delete-read-only-aliases"></a>Ta bort skrivskyddade alias

Det här kommandot tar bort alla alias från den aktuella sessionen, förutom de med värdet `Constant` för egenskapen **Options** . `-Force`Parametern tillåter kommandot att ta bort alias vars **alternativ** egenskap har värdet `ReadOnly` .

```powershell
Remove-Item Alias:* -Force
```

## <a name="dynamic-parameters"></a>Dynamiska parametrar

Dynamiska parametrar är cmdlet-parametrar som läggs till av en PowerShell-Provider och är bara tillgängliga när cmdleten används i den provider-aktiverade enheten.

### <a name="options-systemmanagementautomationscopeditemoptions"></a>Alternativ [system. Management. Automation. ScopedItemOptions]

Anger värdet för egenskapen **Options** för ett alias.

- **Ingen**: inga alternativ. Detta värde är standard.
- **Konstant**: det går inte att ta bort aliaset och dess egenskaper kan inte ändras.
  **Konstant** är endast tillgängligt när du skapar ett alias. Det går inte att ändra alternativet för ett befintligt alias till **konstant**.
- **Privat**: aliaset är endast synligt i det aktuella omfånget, inte i de underordnade omfången.
- **ReadOnly**: egenskaperna för aliaset kan inte ändras förutom genom att använda `-Force` parametern. Du kan använda `Remove-Item` för att ta bort aliaset.
- **AllScope**: aliaset kopieras till alla nya omfattningar som skapas.

#### <a name="cmdlets-supported"></a>Cmdlets som stöds

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
Get-Help Get-ChildItem -Path alias:
```

## <a name="see-also"></a>Se även

[about_Aliases](../About/about_Aliases.md)

[about_Providers](../About/about_Providers.md)

