---
ms.date: 12/19/2019
keywords: PowerShell, cmdlet
title: Hjälpmedelsfunktioner i Windows PowerShell ISE
ms.openlocfilehash: e618daca98d76f767a8b60a3425760bfc0bd0f64
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736291"
---
# <a name="accessibility-in-windows-powershell-ise"></a>Hjälpmedelsfunktioner i Windows PowerShell ISE

I det här avsnittet beskrivs hjälpmedels funktionerna i Windows PowerShell ISE (Integrated Scripting Environment) som du kan ha nytta av.

- [Ändra storlek och plats för konsolen och skript Fönstren](#how-to-change-the-size-and-location-of-the-console-and-script-panes)
- [Kortkommandon för att redigera text](#keyboard-shortcuts-for-editing-text)
- [Kortkommandon för skript som körs](#keyboard-shortcuts-for-running-scripts)
- [Kortkommandon för att anpassa vyn](#keyboard-shortcuts-for-customizing-the-view)
- [Kortkommandon för fel sökning av skript](#keyboard-shortcuts-for-debugging-scripts)
- [Kortkommandon för Windows PowerShell-flikar](#keyboard-shortcuts-for-windows-powershell-tabs)
- [Kortkommandon för att starta och avsluta](#keyboard-shortcuts-for-starting-and-exiting)
- [Bryt punkts hantering med cmdletar](#breakpoint-management)

Microsoft arbetar ständigt med att göra sina produkter och tjänster lättare att använda för alla. Följande avsnitt innehåller information om de funktioner, produkter och tjänster som gör Windows PowerShell ISE mer tillgängligt för personer med funktions nedsättning.

Utöver hjälpmedels funktionerna i Microsoft Windows gör följande funktioner Windows PowerShell ISE mer tillgängliga för personer med funktions hinder:

- Kortkommandon

- Syntax färgning-tabellen och möjligheten att ändra flera andra färg inställningar med hjälp av skript kommandot [$psISE. alternativ](object-model/The-ISEOptions-Object.md) .

- Ändra text storlek

## <a name="how-to-change-the-size-and-location-of-the-console-and-script-panes"></a>Ändra storlek och plats för konsolen och skript Fönstren

Du kan använda följande steg för att ändra storlek och plats för konsol fönstret och skript fönstret. När du öppnar Windows PowerShell ISE igen bevaras storleks-och plats ändringar som du har gjort.

### <a name="to-resize-the-script-pane-and-console-pane"></a>Ändra storlek på skript fönstret och konsol fönstret

1. Pausa pekaren på delnings linjen mellan skript fönstret och konsol fönstret.

2. När mus pekaren ändras till en dubbelriktad pil, drar du kant linjen för att ändra fönstrets storlek.

### <a name="to-move-the-script-pane-and-console-pane"></a>Flytta skript fönstret och konsol fönstret

Gör något av följande:

- Om du vill flytta skript fönstret ovanför konsol fönstret trycker du på <kbd>CTRL</kbd>+<kbd>1</kbd> eller, i verktygsfältet, klicka på ikonen **Visa skript fönstret överst** eller klicka på Visa **skript fönstret överst**i menyn **Visa** .

- Om du vill flytta skript fönstret till höger om konsol fönstret trycker du på <kbd>CTRL</kbd>+<kbd>2</kbd> eller, i verktygsfältet, klicka på höger ikon i fönstret **Visa skript** , eller klicka på **Visa skript fönster**till höger i menyn **Visa** .

- Maximera skript fönstret genom att trycka på <kbd>CTRL</kbd>+<kbd>3</kbd> eller, i verktygsfältet, klicka på ikonen **Visa skript fönstret maximerat** eller på **Visa** -menyn och klicka på **Visa skript fönstret maximerat**.

- Om du vill maximera konsol fönstret och dölja skript fönstret klickar du på ikonen **Dölj skript** fönster på menyn **Visa** på den högra kanten av raden med flikar. Klicka sedan på meny alternativet **Visa skript fönster** .

- Om du vill visa skript fönstret när konsol fönstret är maximerat, klickar du på ikonen **Visa** skript fönstret längst till höger på raden med flikar, eller på menyn **Visa** klickar du på meny alternativet **Visa skript fönster** .

## <a name="keyboard-shortcuts-for-editing-text"></a>Kortkommandon för att redigera text

Du kan använda följande kortkommandon när du redigerar text.

|           Åtgärd            |       Kortkommandon       |          Använd i           |
| --------------------------- | ------------------------------ | ------------------------- |
| **Copy**                    | <kbd>CTRL</kbd>+<kbd>C</kbd>   | Skript fönster, konsol fönster |
| **Styckning**                     | <kbd>CTRL</kbd>+<kbd>X</kbd>   | Skript fönster, konsol fönster |
| **Sök i skript**          | <kbd>CTRL</kbd>+<kbd>F</kbd>   | Skript fönster               |
| **Sök nästa i skriptet**     | <kbd>F3</kbd>                  | Skript fönster               |
| **Hitta föregående i skript** | <kbd>SHIFT</kbd>+<kbd>F3</kbd> | Skript fönster               |
| **Inklistringsfel**                   | <kbd>CTRL</kbd>+<kbd>V</kbd>   | Skript fönster, konsol fönster |
| **Tidigare**                    | <kbd>CTRL</kbd>+<kbd>Y</kbd>   | Skript fönster, konsol fönster |
| **Ersätt i skript**       | <kbd>CTRL</kbd>+<kbd>H</kbd>   | Skript fönster               |
| **Spara**                    | <kbd>CTRL</kbd>+<kbd>S</kbd>   | Skript fönster               |
| **Markera alla**              | <kbd>CTRL</kbd>+<kbd>en</kbd>   | Skript fönster, konsol fönster |
| **Göra**                    | <kbd>CTRL</kbd>+<kbd>Z</kbd>   | Skript fönster, konsol fönster |

## <a name="keyboard-shortcuts-for-running-scripts"></a>Kortkommandon för skript som körs

Du kan använda följande kortkommandon när du kör skript i skript fönstret.

|            Åtgärd            |                                                                                                     Kortkommando                                                                                                      |
| ---------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Ny**                      | <kbd>CTRL</kbd>+<kbd>N</kbd>                                                                                                                                                                                               |
| **Öppna**                     | <kbd>CTRL</kbd>+<kbd>O</kbd>                                                                                                                                                                                               |
| **Kör**                      | <kbd>F5</kbd>                                                                                                                                                                                                              |
| **Kör val**            | <kbd>F8</kbd>                                                                                                                                                                                                              |
| **Stoppa körning**           | <kbd>CTRL</kbd>+<kbd>Bryt</kbd>. Du kan använda <kbd>CTRL</kbd>+<kbd>C</kbd> när kontexten är oklar (när det inte finns någon text markerad).                                                                               |
| **TABB** (till nästa skript)     | <kbd>CTRL</kbd>+<kbd>Tab</kbd> **Obs!** Tab till nästa skript fungerar bara om du har en enda PowerShell-flik öppen eller om du har fler än en PowerShell-flik öppen, men fokus är i skript fönstret.                |
| **TABB** (till föregående skript) | <kbd>CTRL</kbd>+<kbd>Shift</kbd>+<kbd>TABB</kbd> - **anteckning:** TABB till föregående skript fungerar när du bara har en PowerShell-flik öppen, eller om du har fler än en PowerShell-flik öppen och fokus är i skript fönstret. |

## <a name="keyboard-shortcuts-for-customizing-the-view"></a>Kortkommandon för att anpassa vyn

Du kan använda följande kortkommandon för att anpassa vyn i Windows PowerShell ISE. De är tillgängliga från alla rutor i programmet.

|           Åtgärd           |         Kortkommando        |
| -------------------------- | -------------------------------- |
| **Gå till konsol fönstret**     | <kbd>CTRL</kbd>+<kbd>D</kbd>     |
| **Gå till skript fönstret**      | <kbd>CTRL</kbd>+<kbd></kbd>     |
| **Visa skript fönstret**       | <kbd>CTRL</kbd>+<kbd>R</kbd>     |
| **Dölj skript fönstret**       | <kbd>CTRL</kbd>+<kbd>R</kbd>     |
| **Flytta skript fönstret uppåt**    | <kbd>CTRL</kbd>+<kbd>1</kbd>     |
| **Flytta skript fönstret åt höger** | <kbd>CTRL</kbd>+<kbd>2</kbd>     |
| **Maximera skript fönstret**   | <kbd>CTRL</kbd>+<kbd>3</kbd>     |
| **Zooma in**                | <kbd>CTRL</kbd>+<kbd>plus</kbd>  |
| **Zooma ut**               | <kbd>CTRL</kbd>+<kbd>minus</kbd> |

## <a name="keyboard-shortcuts-for-debugging-scripts"></a>Kortkommandon för fel sökning av skript

Du kan använda följande kortkommandon vid fel sökning av skript.

|           Åtgärd           |               Kortkommando                |                Använd i                |
| -------------------------- | ---------------------------------------------- | ------------------------------------ |
| **Kör/Fortsätt**           | <kbd>F5</kbd>                                  | Skript fönstret, vid fel sökning av ett skript |
| **Stega in**              | <kbd>F11</kbd>                                 | Skript fönstret, vid fel sökning av ett skript |
| **Steg över**              | <kbd>F10</kbd>                                 | Skript fönstret, vid fel sökning av ett skript |
| **Gå ut**               | <kbd>SHIFT</kbd>+<kbd>F11</kbd>                | Skript fönstret, vid fel sökning av ett skript |
| **Visa anrops stack**     | <kbd>CTRL</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>  | Skript fönstret, vid fel sökning av ett skript |
| **List Bryt punkter**       | <kbd>CTRL</kbd>+<kbd>Shift</kbd>+<kbd>L</kbd>  | Skript fönstret, vid fel sökning av ett skript |
| **Växla Bryt punkt**      | <kbd>Höj</kbd>                                  | Skript fönstret, vid fel sökning av ett skript |
| **Ta bort alla Bryt punkter** | <kbd>CTRL</kbd>+<kbd>Shift</kbd>+<kbd>F9</kbd> | Skript fönstret, vid fel sökning av ett skript |
| **Stoppa fel sökning**          | <kbd>SHIFT</kbd>+<kbd>F5</kbd>                 | Skript fönstret, vid fel sökning av ett skript |

> [!NOTE]
> Du kan också använda kortkommandon som är utformade för Windows PowerShell-konsolen när du felsöker skript i Windows PowerShell ISE. Om du vill använda dessa genvägar måste du skriva genvägen i konsol fönstret och trycka på RETUR.

|                 Åtgärd                  |      Kortkommando       |                Använd i                 |
| --------------------------------------- | ---------------------------- | ------------------------------------- |
| **Bestå**                            | <kbd>C</kbd>                 | Konsol fönster, vid fel sökning av ett skript |
| **Stega in**                           | <kbd>S</kbd>                 | Konsol fönster, vid fel sökning av ett skript |
| **Steg över**                           | <kbd>V</kbd>                 | Konsol fönster, vid fel sökning av ett skript |
| **Gå ut**                            | <kbd>O</kbd>                 | Konsol fönster, vid fel sökning av ett skript |
| **Upprepa det senaste kommandot**(Stega in/över) | <kbd>GÅR</kbd>             | Konsol fönster, vid fel sökning av ett skript |
| **Visa anrops stack**                  | <kbd>K</kbd>                 | Konsol fönster, vid fel sökning av ett skript |
| **Stoppa fel sökning**                      | <kbd>Q</kbd>                 | Konsol fönster, vid fel sökning av ett skript |
| **Lista skriptet**                     | <kbd>L</kbd>                 | Konsol fönster, vid fel sökning av ett skript |
| **Visa kommandon för konsol fel sökning**  | <kbd>H</kbd> eller <kbd>?</kbd> | Konsol fönster, vid fel sökning av ett skript |

## <a name="keyboard-shortcuts-for-windows-powershell-tabs"></a>Kortkommandon för Windows PowerShell-flikar

Du kan använda följande kortkommandon när du använder Windows PowerShell-flikar.

|             Åtgärd              |                                 Kortkommando                                  |
| ------------------------------- | ---------------------------------------------------------------------------------- |
| **Stäng PowerShell-fliken**        | <kbd>CTRL</kbd>+<kbd>W</kbd>                                                       |
| **Ny PowerShell-flik**          | <kbd>CTRL</kbd>+<kbd>t</kbd>                                                       |
| **Föregående PowerShell-flik**     | <kbd>CTRL</kbd>+<kbd>Shift</kbd>+<kbd>fliken</kbd> (endast när inga filer är öppna på någon PowerShell-flik)                 |
| **Nästa Windows PowerShell-flik** | <kbd>Fliken</kbd> <kbd>CTRL</kbd>+(endast när inga filer är öppna på någon PowerShell-flik) |

## <a name="keyboard-shortcuts-for-starting-and-exiting"></a>Kortkommandon för att starta och avsluta

Du kan använda följande kortkommandon för att starta Windows PowerShell-konsolen (**PowerShell. exe**) eller avsluta Windows PowerShell ISE.

|                        Åtgärd                         |               Kortkommando               |
| ----------------------------------------------------- | --------------------------------------------- |
| **Avsluta**                                              | <kbd>ALT</kbd>+<kbd>F4</kbd>                  |
| **Starta PowerShell. exe** (Windows PowerShell-konsol) | <kbd>CTRL</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> |

## <a name="breakpoint-management"></a>Bryt punkts hantering

För synskadade är Bryt punkts information tillgänglig via cmdletarna för att hantera Bryt punkter, till exempel [Get-PSBreakpoint](/reference/6/Microsoft.PowerShell.Utility/Get-PSBreakpoint.md) och [set-PSBreakpoint](/reference/6/Microsoft.PowerShell.Utility/Set-PSBreakpoint.md).
Mer information finns i "så här hanterar du Bryt punkter" i [fel sökning av skript i Windows PowerShell ISE](How-to-Debug-Scripts-in-Windows-PowerShell-ISE.md).

## <a name="see-also"></a>Se även

[Vi presenterar Windows PowerShell ISE](Introducing-the-Windows-PowerShell-ISE.md)
