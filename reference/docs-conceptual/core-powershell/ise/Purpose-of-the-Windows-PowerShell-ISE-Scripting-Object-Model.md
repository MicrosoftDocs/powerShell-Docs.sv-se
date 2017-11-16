---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Syftet med Windows PowerShell ISE Scripting Object Model
ms.assetid: d176a131-ab0c-43ee-80c1-f824ab8e4a05
ms.openlocfilehash: 3256d8bff3885d266f0db6f52932e40c4beaf8b1
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/08/2017
---
# <a name="purpose-of-the-windows-powershell-ise-scripting-object-model"></a>Syftet med Windows PowerShell ISE Scripting Object Model
  Objekt är kopplade till form och funktion i Windows PowerShell Integrated Scripting Environment (ISE). Objektreferensen modellen innehåller information om medlemmen egenskaper och metoder som visar dessa objekt. Exempel som visar hur du kan använda skript för direkt åtkomst till dessa metoder och egenskaper. Scripting object model gör det enklare att följande intervall av uppgifter.

## <a name="customizing-the-appearance-of-windows-powershell-ise"></a>Anpassa utseendet på Windows PowerShell ISE
 Du kan använda objektmodellen för att ändra programinställningarna och alternativ. T.ex, kan du ändra dem på följande sätt:

- Du kan ändra färgen för fel, varningar, utförlig utdata och debug matar ut.

- Du kan hämta eller ange bakgrundsfärger för kommando-rutan, utdatarutan och skriptfönstret.

- Du kan ange förgrundsfärgen för utdatarutan.

- Du kan ange teckensnitt och teckenstorlek för Windows PowerShell ISE.

- Du kan konfigurera varningar. Den här inställningen inkluderar varningar som utfärdas när en fil öppnas i flera PowerShell flikar eller köra ett skript i filen innan filen har sparats.

- Du kan växla mellan att visa där skriptfönstret och utdatarutan är sida vid sida och en vy där skriptfönstret är ovanpå utdatarutan. Du kan docka fönstret kommandot ned eller upp i utdatarutan.

## <a name="enhancing-the-functionality-of-windows-powershell-ise"></a>Utöka funktionerna i Windows PowerShell ISE
 Du kan använda objektmodellen för att förbättra funktionerna i Windows PowerShell ISE. Du kan till exempel:

- Lägg till och ändra instansen av Windows PowerShell ISE sig själv. Om du vill ändra menyerna kan du exempelvis lägga till nya menyalternativ och mappa nya menyalternativ skript.

- Skapa skript som utför vissa av de uppgifter som du kan utföra med hjälp av knapparna och kommandon i Windows PowerShell ISE. Du kan exempelvis lägga till, ta bort eller välja en PowerShell-flik.

- Komplement aktiviteter som kan utföras med hjälp av menykommandon och knappar. Exempelvis kan du byta namn på en PowerShell-flik.

- Ändra texten buffertar för kommando-rutan, utdatarutan och rutan skript som är kopplade till en fil. Du kan till exempel:

    -   Hämta eller ange alla text.

    -   Hämta eller ange en textmarkering.

    -   Kör ett skript eller kör en del av ett skript.

    -   Rulla en rad i vyn.

    -   Infoga texten vid en hatt position.

    -   Välj ett block med text.

    -   Hämta senaste numret.

- Utföra filåtgärder. Du kan till exempel:

    -   Öppna en fil, spara en fil eller spara en fil med ett annat namn.

    -   Avgör om en fil har ändrats efter den senast sparades.

    -   Hämta namnet på filen.

    -   Välj en fil.

## <a name="automating-tasks"></a>Automatisera uppgifter
 Du kan använda scripting object model kortkommandon för ofta förekommande åtgärder.

## <a name="see-also"></a>Se även
- [Modellen objekthierarkin ISE](The-ISE-Object-Model-Hierarchy.md) 
- [Windows PowerShell ISE objektreferens modellen](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [Windows PowerShell ISE Scripting Object Model](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)

  
