---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Grunderna i Windows PowerShell
ms.assetid: 6b3cbbc8-060c-4877-b00b-7300dbbe4e28
ms.openlocfilehash: b21c6cd84ea29d5e8085ccf8df2a5a9199e1d859
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="windows-powershell-basics"></a>Grunderna i Windows PowerShell
Grafiska användargränssnitt använda några grundläggande begrepp som är kända för de flesta användare. Användare är beroende av välbekanta av dessa gränssnitt för att utföra aktiviteter. Operativsystem ge användarna en grafisk representation av objekt som kan visas, vanligtvis med nedrullningsbara menyer för specifika funktioner och kontext menyer för att komma åt sammanhangsberoende funktioner.

Kommandoradsgränssnittet (CLI), till exempel Windows PowerShell måste använda en annan metod för att avslöja information, eftersom den inte har menyer eller grafiska system kan hjälpa användaren. Du bör känna till kommandonamn innan du kan använda dem. Men du kan skriva komplexa kommandon som motsvarar funktionerna i en GUI-miljö, måste du bekanta dig med vanliga kommandon och parametrar.

De flesta CLIs har inte mönster som kan hjälpa användaren att lära dig gränssnittet. Eftersom CLIs var de första gränssnitt för operativsystemet, har många kommandonamn och parameternamn valts godtyckligt. Terse kommandonamn har vanligtvis valt över avmarkera de. Även om hjälpsystemet och kommandot designstandarder är integrerade i de flesta CLIs, de är vanligtvis avsedda för kompatibilitet med kommandona tidigaste så kommandot är fortfarande formats av beslut som gjorts sedan åren.

Windows PowerShell har utformats för att dra nytta av en användares historiska kunskap om CLIs. I det här kapitlet kommer vi om vissa grundläggande verktyg och koncept som du kan använda för att snabbt lära sig Windows PowerShell. Dessa är:

- Med hjälp av [Get-Command](/powershell/module/Microsoft.PowerShell.Core/get-command)

- Med hjälp av [Cmd.exe](/windows-server/administration/windows-commands/cmd) och [UNIX-kommandon](/windows/wsl/reference)

- [Med fliken slutförande](../../core-powershell/console/using-tab-expansion.md)

- [Med hjälp av Get-Help](./getting-detailed-help-information.md)