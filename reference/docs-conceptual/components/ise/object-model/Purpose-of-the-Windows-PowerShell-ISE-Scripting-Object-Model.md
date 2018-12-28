---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Användningsområden för Windows PowerShell ISE-skriptobjektmodellen
ms.assetid: d176a131-ab0c-43ee-80c1-f824ab8e4a05
ms.openlocfilehash: fd5ac2c34b173d4eba7636bb5760b1ac9abb4277
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53406002"
---
# <a name="purpose-of-the-windows-powershell-ise-scripting-object-model"></a>Användningsområden för Windows PowerShell ISE-skriptobjektmodellen

Objekt som är associerade med form och funktion i Windows PowerShell Integrated Scripting Environment (ISE). Referens för objektmodell innehåller information om medlemmen egenskaper och metoder som exponerar dessa objekt. Exempel som visar hur du kan använda skript för direkt åtkomst till dessa metoder och egenskaper. Scripting object model gör det enklare att följande intervall av uppgifter.

## <a name="customizing-the-appearance-of-windows-powershell-ise"></a>Anpassa utseendet på Windows PowerShell ISE

Du kan använda object model för att ändra inställningar för program och alternativ. Exempelvis kan ändra du dem på följande sätt:

- Du kan ändra färg på fel, varningar, utförlig utdata och utdata för felsökning.
- Du kan hämta eller ange bakgrundsfärgerna för kommando-fönstret och utdatarutan skriptfönstret.
- Du kan ange förgrundsfärgen för utdatarutan.
- Du kan ange namn och storlek för Windows PowerShell ISE.
- Du kan konfigurera varningar. Den här inställningen innehåller varningar som utfärdas när en fil öppnas i flera PowerShell-flikar, eller när du kör ett skript i filen innan filen har sparats.
- Du kan växla mellan en vy där skriptfönstret och utdatarutan är sida-vid-sida och en vy där skriptfönstret är ovanpå utdatarutan. Du kan docka fönstret kommando till längst ned eller upp i utdatarutan.

## <a name="enhancing-the-functionality-of-windows-powershell-ise"></a>Utöka funktionerna i Windows PowerShell ISE

Du kan använda object model för att förbättra funktionerna i Windows PowerShell ISE. Du kan till exempel:

- Lägga till och ändra instansen av Windows PowerShell ISE själva. Om du vill ändra menyerna, kan du exempelvis lägga till nya menyalternativ och mappa nya menyalternativ till skript.
- Skapa skript som kan utför vissa uppgifter som du kan utföra med hjälp av menykommandon och knappar i Windows PowerShell ISE. Du kan till exempel lägga till, ta bort eller välja en PowerShell-flik.
- Komplettera aktiviteter som kan utföras med hjälp av menykommandon och knappar. Exempelvis kan du byta namn på en PowerShell-flik.
- Ändra text buffertar för fönstret kommando, utdatarutan och skriptfönstret som är associerade med en fil. Du kan till exempel:
  - Hämta eller ange all text.
  - Hämta eller ange en textmarkering.
  - Köra ett skript eller köra en del av ett skript.
  - Rulla en rad i vyn.
  - Infoga text vid en hatt position.
  - Välj ett block med text.
  - Hämta den senaste radnummer.
- Utföra åtgärder för sammansättningsfiler. Du kan till exempel:
  - Öppna en fil, sparar en fil eller spara en fil med hjälp av ett annat namn.
  - Avgör om en fil har ändrats efter det senast sparades.
  - Hämta namnet på filen.
  - Välj en fil.

## <a name="automating-tasks"></a>Automatisera uppgifter

Du kan använda skript: objektmodell för att skapa kortkommandon för återkommande åtgärder.

## <a name="see-also"></a>Se även

- [Hierarki för ISE-objektmodellen](The-ISE-Object-Model-Hierarchy.md)