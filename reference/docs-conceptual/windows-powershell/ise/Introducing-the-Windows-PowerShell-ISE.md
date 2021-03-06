---
ms.date: 08/14/2018
title: Introducerar Windows PowerShell ISE
description: PowerShell ISE är ett värd program för Windows PowerShell som gör att du kan köra kommandon och skriva, testa och felsöka skript i ett enda Windows-baserat grafiskt användar gränssnitt.
ms.openlocfilehash: ab2b11e5d81933b166d404c0b24c96aa73253895
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92663605"
---
# <a name="the-windows-powershell-ise"></a>Windows PowerShell ISE

Windows PowerShell ISE (Integrated Scripting Environment) är ett värd program för Windows PowerShell. I ISE kan du köra kommandon och skriva, testa och felsöka skript i ett enda Windows-baserat grafiskt användar gränssnitt. ISE ger redigering av flera rader, TABB-och syntax-färgning, selektiv körning, Sammanhangs beroende hjälp och stöd för höger-till-vänster-språk. Meny objekt och kortkommandon mappas till många av de uppgifter som du skulle göra i Windows PowerShell-konsolen. När du till exempel felsöker ett skript i ISE kan du högerklicka på en kodrad i fönstret Redigera för att ange en Bryt punkt.

## <a name="support"></a>Support

ISE introducerades först med Windows PowerShell V2 och har återskapats med PowerShell v3. ISE stöds i alla Windows PowerShell-versioner som stöds upp till och inklusive Windows PowerShell V 5.1.

> [!NOTE]
> PowerShell ISE är inte längre vid utveckling av aktiva funktioner. Som en leverans komponent i Windows fortsätter den att vara officiellt tillgänglig för säkerhets-och högprioriterade service-korrigeringar.
> Vi har för närvarande inga planer på att ta bort ISE från Windows.
>
> Det finns inget stöd för ISE i PowerShell V6 och senare. Användare som söker efter ersättning för ISE bör använda [Visual Studio Code](https://code.visualstudio.com/) med [PowerShell-tillägget](https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell).

## <a name="key-features"></a>Viktiga funktioner

Viktiga funktioner i Windows PowerShell ISE inkluderar:

- Redigering i flera rader: om du vill infoga en tom rad under den aktuella raden i kommando fönstret trycker du på <kbd>SKIFT</kbd> + <kbd>RETUR</kbd>.
- Selektiv körning: om du vill köra en del av ett skript väljer du den text som du vill köra och klickar sedan på knappen **Kör skript** . Eller tryck på <kbd>F5</kbd>.
- Sammanhangs beroende hjälp: Skriv `Invoke-Item` och tryck sedan på <kbd>F1</kbd>. Hjälp filen öppnas i artikeln för `Invoke-Item` cmdleten.

Med Windows PowerShell ISE kan du anpassa vissa delar av utseendet. Det har också ett eget skript för Windows PowerShell-profiler.

## <a name="to-start-the-windows-powershell-ise"></a>Starta Windows PowerShell ISE

Klicka på **Start** , Välj **Windows PowerShell** och klicka sedan på **Windows PowerShell ISE** .
Alternativt kan du skriva `powershell_ise.exe` in ett kommando gränssnitt eller i rutan Kör.

## <a name="to-get-help-in-the-windows-powershell-ise"></a>För att få hjälp i Windows PowerShell ISE

På **Hjälp** -menyn klickar du på **Windows PowerShell-hjälpen** . Eller tryck på <kbd>F1</kbd>. Filen som öppnas beskriver Windows PowerShell ISE och Windows PowerShell, inklusive all hjälp som är tillgänglig från `Get-Help` cmdleten.
