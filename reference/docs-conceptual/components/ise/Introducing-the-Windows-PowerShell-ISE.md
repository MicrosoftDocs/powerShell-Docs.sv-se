---
ms.date: 08/14/2018
keywords: PowerShell cmdlet
title: Introducerar Windows PowerShell ISE
ms.openlocfilehash: 729c8535dbcfcd2c51070b8beac5d328375f36ae
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057433"
---
# <a name="the-windows-powershell-ise"></a>Windows PowerShell ISE

I Windows PowerShell Integrated Scripting Environment (ISE) är ett program för Windows PowerShell. Du kan köra kommandon och skriva, testa och felsöka skript i ett enda Windows-baserade grafiska användargränssnitt i ISE. ISE ger flerradsredigering, tabbifyllning, syntaxfärgning, selektiv körning, sammanhangsberoende hjälp och support för höger-till-vänster-språk. Menyalternativ och kortkommandon mappas till många av de uppgifter som du gör i Windows PowerShell-konsolen. Till exempel när du felsöker ett skript i ISE kan du högerklicka på en rad med kod i redigeringsfönstret för att konfigurera en brytpunkt.

## <a name="support"></a>Support

ISE introducerades med Windows PowerShell V2 och utformades igen med PowerShell V3. ISE stöds i alla versioner av Windows PowerShell upp till och inklusive Windows PowerShell V5.1 stöds. ISE, men är i underhållsläge och inga nya funktioner förmodligen kommer att läggas till.
Dessutom finns inget stöd för ISE med PowerShell v6 och mycket mer. Användare som vill ha ett grafiskt verktyg som kan hantera PowerShell-skript, osv, bör [Visual Studio Code](https://code.visualstudio.com/).

## <a name="key-features"></a>Viktiga funktioner

Viktiga funktioner i Windows PowerShell ISE:

- Flerradsredigering: Infoga en tom rad under den aktuella raden i fönstret kommandot, trycka på SKIFT + RETUR.
- Selektiv körning: Om du vill köra en del av ett skript, markerar du texten som du vill köra och klicka sedan på den **kör skript** knappen. Eller tryck på F5.
- Sammanhangsberoende hjälp: Typ **Invoke-Item**, och tryck på F1. Hjälpfilen öppnas i artikeln för den **Invoke-Item** cmdlet.

Windows PowerShell ISE kan du anpassa vissa aspekter av utseendet. Det har också sin egen Windows PowerShell-skript för profilen.

## <a name="to-start-the-windows-powershell-ise"></a>Starta Windows PowerShell ISE

Klicka på **starta**väljer **Windows PowerShell**, och klicka sedan på **Windows PowerShell ISE**.
Alternativt kan du ange `powershell_ise.exe` i valfritt kommandogränssnitt eller i rutan Kör.

## <a name="to-get-help-in-the-windows-powershell-ise"></a>Att få hjälp i Windows PowerShell ISE

På den **hjälpa** -menyn klickar du på **Windows PowerShell-hjälp**. Eller tryck på F1. Filen som öppnas beskriver Windows PowerShell ISE och Windows PowerShell, inklusive alla hjälpen som finns i cmdleten Get-Help.
