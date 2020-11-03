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
# <a name="about_psconsolehostreadline"></a><span data-ttu-id="e6726-104">about_PSConsoleHostReadLine</span><span class="sxs-lookup"><span data-stu-id="e6726-104">about_PSConsoleHostReadLine</span></span>

## <a name="short-description"></a><span data-ttu-id="e6726-105">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="e6726-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="e6726-106">Förklarar hur du skapar en anpassning av hur PowerShell läser in inläsningar i konsol tolken.</span><span class="sxs-lookup"><span data-stu-id="e6726-106">Explains how to create a customize how PowerShell reads input at the console prompt.</span></span>

## <a name="long-description"></a><span data-ttu-id="e6726-107">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="e6726-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="e6726-108">Från och med Windows PowerShell 3,0 kan du skriva en funktion med namnet PSConsoleHostReadLine som åsidosätter standard sättet som konsol indatatypen bearbetas.</span><span class="sxs-lookup"><span data-stu-id="e6726-108">Starting in Windows PowerShell 3.0, you can write a function named PSConsoleHostReadLine that overrides the default way that console input is processed.</span></span>

### <a name="examples"></a><span data-ttu-id="e6726-109">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="e6726-109">EXAMPLES</span></span>

<span data-ttu-id="e6726-110">I följande exempel startas anteckningar och indata hämtas från en textfil som användaren skapar:</span><span class="sxs-lookup"><span data-stu-id="e6726-110">The following example launches Notepad and gets input from a text File that the user creates:</span></span>

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

### <a name="remarks"></a><span data-ttu-id="e6726-111">REMARKS</span><span class="sxs-lookup"><span data-stu-id="e6726-111">REMARKS</span></span>

<span data-ttu-id="e6726-112">Som standard läser PowerShell inmatad från-konsolen i vad som kallas "tillagat läge" – där del systemet i Windows-konsolen hanterar alla tangenttryckningar, F7-menyer och andra ingångar.</span><span class="sxs-lookup"><span data-stu-id="e6726-112">By default, PowerShell reads input from the console in what is known as "Cooked Mode" -- in which the Windows console subsystem handles all the keypresses, F7 menus, and other input.</span></span> <span data-ttu-id="e6726-113">När du trycker på RETUR eller Tab hämtar PowerShell den text som du har skrivit upp till den punkten.</span><span class="sxs-lookup"><span data-stu-id="e6726-113">When you press Enter or Tab, PowerShell gets the text that you have typed up to that point.</span></span> <span data-ttu-id="e6726-114">Det finns inget sätt för IT att veta att du tryckte på CTRL-R, CTRL-A, CTRL-E eller någon annan tangent innan du trycker på RETUR eller TABB. I Windows PowerShell 3,0 löser PSConsoleHostReadLine-funktionen det här problemet.</span><span class="sxs-lookup"><span data-stu-id="e6726-114">There is no way for it to know that you pressed Ctrl-R, Ctrl-A, Ctrl-E, or any other keys before pressing Enter or Tab. In Windows PowerShell 3.0, the PSConsoleHostReadLine function solves this issue.</span></span> <span data-ttu-id="e6726-115">När du definierar en funktion med namnet PSConsoleHostReadline i PowerShell-konsolens värd, anropar PowerShell funktionen i stället för Indataporten "" tillagat läge ".</span><span class="sxs-lookup"><span data-stu-id="e6726-115">When you define a function named PSConsoleHostReadline in the PowerShell console host, PowerShell calls that function instead of the "Cooked Mode" input mechanism.</span></span>

### <a name="see-also"></a><span data-ttu-id="e6726-116">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="e6726-116">SEE ALSO</span></span>

[<span data-ttu-id="e6726-117">about_Prompts</span><span class="sxs-lookup"><span data-stu-id="e6726-117">about_Prompts</span></span>](about_Prompts.md)
