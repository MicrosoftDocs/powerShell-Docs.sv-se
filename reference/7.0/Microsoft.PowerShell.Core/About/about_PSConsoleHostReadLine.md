---
description: Förklarar hur du skapar en anpassning av hur PowerShell läser in inläsningar i konsol tolken.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/04/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_psconsolehostreadline?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PSConsoleHostReadLine
ms.openlocfilehash: 49c3ce4099109fc721a13b61f390f564b8893a25
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93272259"
---
# <a name="about_psconsolehostreadline"></a>about_PSConsoleHostReadLine

## <a name="short-description"></a>KORT BESKRIVNING
Förklarar hur du skapar en anpassning av hur PowerShell läser in inläsningar i konsol tolken.

## <a name="long-description"></a>LÅNG BESKRIVNING

Från och med Windows PowerShell 3,0 kan du skriva en funktion med namnet PSConsoleHostReadLine som åsidosätter standard sättet som konsol indatatypen bearbetas.

### <a name="examples"></a>EXEMPEL

I följande exempel startas anteckningar och indata hämtas från en textfil som användaren skapar:

```powershell
function PSConsoleHostReadLine
{
  $inputFile = Join-Path $env:TEMP PSConsoleHostReadLine
  Set-Content $inputFile "PS > "

  # Notepad opens. Enter your command in it, save the file, and then exit.
  notepad $inputFile | Out-Null
  $userInput = Get-Content $inputFile
  $resultingCommand = $userInput.Replace("PS >", "")
  $resultingCommand
}
```

### <a name="remarks"></a>REMARKS

Som standard läser PowerShell inmatad från-konsolen i vad som kallas "tillagat läge" – där del systemet i Windows-konsolen hanterar alla tangenttryckningar, F7-menyer och andra ingångar. När du trycker på RETUR eller Tab hämtar PowerShell den text som du har skrivit upp till den punkten. Det finns inget sätt för IT att veta att du tryckte på CTRL-R, CTRL-A, CTRL-E eller någon annan tangent innan du trycker på RETUR eller TABB. I Windows PowerShell 3,0 löser PSConsoleHostReadLine-funktionen det här problemet. När du definierar en funktion med namnet PSConsoleHostReadline i PowerShell-konsolens värd, anropar PowerShell funktionen i stället för Indataporten "" tillagat läge ".

### <a name="see-also"></a>SE ÄVEN

[about_Prompts](about_Prompts.md)
