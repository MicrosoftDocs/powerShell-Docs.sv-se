---
description: Definierar vad ett skript block är och förklarar hur du använder skript block i PowerShell-programmeringsspråket.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_script_blocks?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Script_Blocks
ms.openlocfilehash: f842701d83c525e4695debf99c4725580661b1de
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93271431"
---
# <a name="about-script-blocks"></a>Om skript block

## <a name="short-description"></a>Kort beskrivning

Definierar vad ett skript block är och förklarar hur du använder skript block i PowerShell-programmeringsspråket.

## <a name="long-description"></a>Lång beskrivning

I PowerShell-programmeringsspråket är ett skript block en samling med instruktioner eller uttryck som kan användas som en enda enhet.
Ett skript block kan acceptera argument och returnerade värden.

Ett skript block är syntaktiskt som en instruktions lista inom klammerparentes, som du ser i följande syntax:

```
{<statement list>}
```

Ett skript block returnerar utdata från alla kommandon i skript blocket, antingen som ett enskilt objekt eller som en matris.

Du kan också ange ett retur värde med hjälp av `return` nyckelordet. `return`Nyckelordet påverkar eller utelämnar inte andra utdata som returneras från skript blocket. `return`Nyckelordet avslutar dock skript blocket på raden. Mer information finns i [about_Return](about_Return.md).

Precis som funktioner kan ett skript block innehålla parametrar. Använd nyckelordet param för att tilldela namngivna parametrar, som du ser i följande syntax:

```
{
Param([type]$Parameter1 [,[type]$Parameter2])
<statement list>
}
```

> [!NOTE]
> I ett-skript block kan du till skillnad från en funktion inte ange parametrar utanför klamrarna.

Precis som funktioner kan skript block innehålla `DynamicParam` `Begin` `Process` nyckelorden,, och `End` . Mer information finns i [about_Functions](about_Functions.md) och [about_Functions_Advanced](about_Functions_Advanced.md).

## <a name="using-script-blocks"></a>Använda skript block

Ett skript block är en instans av en Microsoft .NET Framework-typ `System.Management.Automation.ScriptBlock` . Kommandon kan innehålla parameter värden för skript block. Till exempel `Invoke-Command` har cmdleten en `ScriptBlock` parameter som tar ett skript block värde, som du ser i det här exemplet:

```powershell
Invoke-Command -ScriptBlock { Get-Process }
```

```Output
Handles  NPM(K)    PM(K)     WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----     ----- -----   ------     -- -----------
999          28    39100     45020   262    15.88   1844 communicator
721          28    32696     36536   222    20.84   4028 explorer
...
```

`Invoke-Command` kan också köra skript block som har parameter block.
Parametrar tilldelas enligt position med parametern **argument List** .

```powershell
Invoke-Command -ScriptBlock { param($p1, $p2)
"p1: $p1"
"p2: $p2"
} -ArgumentList "First", "Second"
```

```Output
p1: First
p2: Second
```

Skript blocket i föregående exempel använder `param` nyckelordet för att skapa en parameter `$p1` och `$p2` . Strängen "First" är kopplad till den första parametern ( `$p1` ) och "sekund" är kopplad till ( `$p2` ).

Mer information om beteendet för **argument List** finns [about_Splatting](about_Splatting.md#splatting-with-arrays).

Du kan använda variabler för att lagra och köra skript block. Exemplet nedan lagrar ett skript block i en variabel och skickar det till `Invoke-Command` .

```powershell
$a = { Get-Service BITS }
Invoke-Command -ScriptBlock $a
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  BITS               Background Intelligent Transfer Ser...
```

Anrops operatorn är ett annat sätt att köra skript block som lagras i en variabel.
Till exempel `Invoke-Command` Kör anrops operatorn skript blocket i ett underordnat omfång. Anrops operatorn kan göra det enklare för dig att använda parametrar med skript block.

```powershell
$a ={ param($p1, $p2)
"p1: $p1"
"p2: $p2"
}
&$a -p2 "First" -p1 "Second"
```

```Output
p1: Second
p2: First
```

Du kan lagra utdata från skript block i en variabel som använder tilldelning.

```
PS>  $a = { 1 + 1}
PS>  $b = &$a
PS>  $b
2
```

```
PS>  $a = { 1 + 1}
PS>  $b = Invoke-Command $a
PS>  $b
2
```

Mer information om samtals operatören finns [about_Operators](about_Operators.md).

## <a name="using-delay-bind-script-blocks-with-parameters"></a>Använder skript block med fördröjnings bindning med parametrar

En typ parameter som godkänner pipeline-inmatare ( `by Value` ) eller ( `by PropertyName` ) aktiverar användning av skript blocken **Delay-bind** i parametern.
I skript blocket **Delay-bind** kan du referera till skickas i-objekt med hjälp av pipeline-variabeln `$_` .

```powershell
# Renames config.log to old_config.log
dir config.log | Rename-Item -NewName {"old_" + $_.Name}
```

I mer komplexa cmdletar kan fördröjning – binda skript block tillåta åter användning av en skickas i objekt för att fylla i andra parametrar.

Anmärkningar om **Delay-bind** skript block som parametrar:

- Du måste uttryckligen ange eventuella parameter namn som du använder med **Delay-bind-** skript block.
- Parametern får inte vara avskriven och parameterns typ får inte vara `[scriptblock]` eller `[object]` .
- Du får ett fel meddelande om du använder ett **Delay-bind-** skript block utan att tillhandahålla pipeline-inflöden.

  ```powershell
  Rename-Item -NewName {$_.Name + ".old"}
  ```

  ```Output
  Rename-Item : Cannot evaluate parameter 'NewName' because its argument is
  specified as a script block and there is no input. A script block cannot
  be evaluated without input.
  At line:1 char:23
  +  Rename-Item -NewName {$_.Name + ".old"}
  +                       ~~~~~~~~~~~~~~~~~~
      + CategoryInfo          : MetadataError: (:) [Rename-Item],
        ParameterBindingException
      + FullyQualifiedErrorId : ScriptBlockArgumentNoInput,
        Microsoft.PowerShell.Commands.RenameItemCommand
  ```

## <a name="see-also"></a>Se även

[about_Functions](about_Functions.md)

[about_Functions_Advanced](about_Functions_Advanced.md)

[about_Operators](about_Operators.md)
