---
ms.date: 06/05/2017
keywords: PowerShell, cmdlet
title: Användningsområden för Windows PowerShell ISE-skriptobjektmodellen
ms.openlocfilehash: e59593ef06911c709e92fa7a1eabd96d2636ca30
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030906"
---
# <a name="purpose-of-the-windows-powershell-ise-scripting-object-model"></a>Användningsområden för Windows PowerShell ISE-skriptobjektmodellen

Objekt är kopplade till form och funktion i Windows PowerShell ISE (Integrated Scripting Environment). Objekt modell referensen innehåller information om medlems egenskaper och metoder som dessa objekt exponerar. Exempel finns för att visa hur du kan använda skript för att komma åt dessa metoder och egenskaper direkt. Skript objekt modellen gör följande olika uppgifter enklare.

## <a name="customizing-the-appearance-of-windows-powershell-ise"></a>Anpassa utseendet på Windows PowerShell ISE

Du kan använda objekt modellen för att ändra program inställningar och-alternativ. Du kan till exempel ändra dem på följande sätt:

- Du kan ändra färg på fel, varningar, utförliga utdata och fel söknings utdata.
- Du kan hämta eller ange bakgrunds färger för kommando fönstret, fönstret utdata och skript fönstret.
- Du kan ställa in förgrunds färgen för fönstret utdata.
- Du kan ange teckensnitts namn och tecken storlek för Windows PowerShell ISE.
- Du kan konfigurera varningar. Den här inställningen innehåller varningar som utfärdas när en fil öppnas i flera PowerShell-flikar eller när ett skript i filen körs innan filen har sparats.
- Du kan växla mellan en vy där skript fönstret och utdatafönstret visas sida vid sida och en vy där skript fönstret visas överst i fönstret utdata. Du kan docka kommando fönstret längst ned eller överst i fönstret utdata.

## <a name="enhancing-the-functionality-of-windows-powershell-ise"></a>Förbättra funktionerna i Windows PowerShell ISE

Du kan använda objekt modellen för att förbättra funktionerna i Windows PowerShell ISE. Du kan till exempel:

- Lägg till och ändra instansen för Windows PowerShell ISE. Om du till exempel vill ändra menyerna kan du lägga till nya meny alternativ och mappa de nya meny alternativen till skript.
- Skapa skript som utför några av de uppgifter som du kan utföra med hjälp av meny kommandona och knapparna i Windows PowerShell ISE. Du kan till exempel lägga till, ta bort eller välja en PowerShell-flik.
- Komplettera uppgifter som kan utföras med hjälp av Meny kommandon och knappar. Du kan till exempel byta namn på en PowerShell-flik.
- Ändra textbuffertar för kommando fönstret, fönstret utdata och skript fönstret som är associerade med en fil. Du kan till exempel:
  - Hämta eller ange all text.
  - Hämta eller ange ett text val.
  - Kör ett skript eller kör en vald del av ett skript.
  - Rulla en rad till vyn.
  - Infoga text i cirkumflex.
  - Välj ett textblock.
  - Hämta det sista rad numret.
- Utför fil åtgärder. Du kan till exempel:
  - Öppna en fil, spara en fil eller spara en fil med hjälp av ett annat namn.
  - Avgör om en fil har ändrats efter att den senast sparades.
  - Hämta fil namnet.
  - Välj en fil.

## <a name="automating-tasks"></a>Automatisera uppgifter

Du kan använda skript objekt modellen för att skapa kortkommandon för frekventa åtgärder.

## <a name="see-also"></a>Se även

- [Hierarki för ISE-objektmodellen](The-ISE-Object-Model-Hierarchy.md)
