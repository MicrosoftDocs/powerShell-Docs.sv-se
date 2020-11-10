---
description: Beskriver funktioner och system krav för Windows PowerShell ISE (Integrated Scripting Environment).
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_windows_powershell_ise?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Windows_PowerShell_ISE
ms.openlocfilehash: ff543024d7c62c70217eeaf3ded192a5a24c4757
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388849"
---
# <a name="about-windows-powershell-ise"></a>Om Windows PowerShell ISE

## <a name="short-description"></a>KORT BESKRIVNING

Beskriver funktioner och system krav för Windows PowerShell ISE (Integrated Scripting Environment).

## <a name="long-description"></a>LÅNG BESKRIVNING

Windows PowerShell ISE är ett grafiskt värd program för Windows PowerShell.
I Windows PowerShell ISE kan du köra kommandon och skriva, testa och felsöka skript i ett enda Windows-baserat grafiskt användar gränssnitt. I dess funktioner ingår IntelliSense, flerradig redigering, TABB-komplettering, Autospara, syntax, selektiv körning, Sammanhangs beroende hjälp, Visa kommando (skapa kommandon i ett fönster) och stöd för teckenuppsättningar med dubbla byte och språk som skrivs från höger till vänster.

Windows PowerShell ISE är ett utmärkt verktyg för nybörjare. Fliken Visa Fönstret Kommando och ny fjärran sluten PowerShell vägleder dig genom aktiviteter så att du kan lyckas med det första försöket. Kodfragment och fel indikatorer hjälper dig att lära dig om Windows PowerShell-språket när du arbetar.

Avancerade användare kan dra nytta av avancerade fel söknings funktioner, tillägg och Windows PowerShell ISE objekt modell.

Vad är nytt i Windows PowerShell ISE i Windows PowerShell 4,0

Windows PowerShell ISE introducerar två nya funktioner i Windows PowerShell 4,0.

- Windows PowerShell ISE stöder nu både Windows PowerShell-arbetsflöde och fel sökning av fjärrskript. Mer information finns i about_Debuggers.

- IntelliSense-stöd har lagts till för Windows PowerShell Desired State Configuration providers och konfigurationer.

## <a name="starting-windows-powershell-ise"></a>Startar Windows PowerShell ISE

Windows PowerShell ISE är installerat, aktiverat och redo att användas i alla Windows-versioner som stöds.

- I Windows 8,1, Windows 8, Windows Server 2012 R2 och Windows Server 2012 skriver du PowerShell_ISE på Start skärmen och klickar sedan på PowerShell_ISE eller Windows PowerShell ISE.

- Klicka på Windows PowerShell ISE i Serverhanteraren på Verktyg-menyn i Windows Server 2012 R2 och Windows Server 2012.

- I tidigare versioner av Windows klickar du på Start, alla program, tillbehör, Windows PowerShell och klickar sedan på Windows PowerShell ISE.

- I en Windows PowerShell-konsol, Cmd.exe eller i rutan Kör eller i Windows skriver du "PowerShell_ise.exe". Du kan också använda kommando rads parametrarna, inklusive växeln noprofile. Mer information finns i [ hjälpen förPowerShell_ISE.exe-konsolen](about_powershell_ise_exe.md).

## <a name="running-interactive-commands"></a>Köra interaktiva kommandon

Du kan köra ett Windows PowerShell-uttryck eller-kommando i Windows PowerShell ISE. Du kan använda cmdlets, providers, snapin-moduler och moduler som du använder dem i Windows PowerShell-konsolen.

Du kan skriva eller klistra in interaktiva kommandon i konsol fönstret. Om du vill köra kommandona kan du använda knappar, meny alternativ och kortkommandon.

Du kan använda funktionen för redigering av flera rader för att skriva eller klistra in flera kodrader i konsol fönstret samtidigt. När du trycker på UPPIL-tangenten för att återkalla föregående kommando, återkallas alla rader i kommandot. När du skriver kommandon trycker du på SKIFT + RETUR så att en ny tom rad visas under den aktuella raden.

## <a name="viewing-output"></a>Visa utdata

Resultatet av kommandon och skript visas i konsol fönstret. Du kan flytta eller kopiera resultaten från konsol fönstret med kortkommandon eller knappen Kopiera i verktygsfältet, och du kan klistra in resultaten i skript fönstret eller konsol fönster eller andra program. Om du vill rensa konsol fönstret klickar du på knappen "Rensa utdata" eller skriver något av följande kommandon:

```
Clear-Host
cls
```

## <a name="writing-scripts-and-functions"></a>Skriva skript och funktioner

I fönstret skript kan du öppna, skapa, redigera och köra skript. Med skript fönstret kan du Redigera skript med hjälp av knappar och kortkommandon. Du kan också kopiera, klippa ut och klistra in text mellan skript fönstret och konsol fönstret.

Du kan använda funktionen selektiv körning för att köra hela eller delar av ett skript. Om du vill köra en del av ett skript väljer du den text som du vill köra och klickar sedan på knappen Kör markering eller trycker på F8. Som standard kör F8 den aktuella raden.

Avancerade redigerings funktioner innehåller klammerparenteser-matchning, expandera-komprimera, rad nummer, fel symboler, blockera redigering och indrag, omfattande kopiering och Skift läges konvertering.

## <a name="getting-help"></a>Få hjälp

Windows PowerShell ISE innehåller hjälp avsnitt som beskriver hur det används. Dessutom är alla installerade hjälpfiler tillgängliga från skript-och kommando Fönstren.

Windows PowerShell ISE också stöd för Sammanhangs beroende hjälp. Om du vill ha hjälp med en viss cmdlet, provider eller nyckelord placerar du markören i namnet på objektet och trycker på F1. Om du vill söka i hjälp avsnitten trycker du på F1 och anger Sök termen.

Om du vill uppdatera hjälp avsnitten på datorn använder du hjälp alternativet Uppdatera Windows PowerShell på Hjälp-menyn. Det här objektet uppdaterar hjälpen för modulerna i den aktuella sessionen i den aktuella kulturen för användar gränssnittet. Det motsvarar att köra cmdleten Update-Help utan parametrar. Om du vill uppdatera hjälpen för de cmdlets som medföljer Windows PowerShell startar du Windows PowerShell ISE med alternativet "kör som administratör".

Du kan också använda cmdletarna Get-Help, Save-Help och Update-Help i Windows PowerShell ISE, precis som du använder dem i Windows PowerShell-konsolen. Men i Windows PowerShell ISE visar Help-funktionen hela hjälp avsnittet, inte en sida i taget.

## <a name="debugging-scripts"></a>Felsöka skript

Du kan använda Windows PowerShell ISE fel sökning för att felsöka ett Windows PowerShell-skript eller-funktion. När du felsöker ett skript kan du använda meny alternativ och kortkommandon för att utföra många av de uppgifter som du skulle utföra i Windows PowerShell-konsolen. Om du till exempel vill ange en rad Bryt punkt i ett skript, högerklicka på kodraden och klicka sedan på Växla Bryt punkt.

När du går igenom ett skript under fel sökningen visar fel sökaren för fel sökning exakt vilken del av kommandot som körs och öppnar automatiskt filer som innehåller anropade funktioner och skript.

Som standard anger meny alternativet Växla Bryt punkt en Bryt punkt på en hel rad i ett skript, men du kan ange en Bryt punkt för en variabel eller ett kommando namn.
Du kan också ange en Bryt punkt för ett kommando med rad-och kolumn nummer, vilket gör det enklare att felsöka kommandon för lång pipelines.

Du kan ofta felsöka syntaxfel i ett skript genom att öppna skript filen i Windows PowerShell ISE. Fel indikatorerna identifierar syntaxfel och dispositions funktionerna gör att du kan dölja delar av skriptet för att fokusera på problem fläckar.

Du kan också använda Windows PowerShell-cmdletar för fel sökning i kommando fönstret på samma sätt som du använder dem i-konsolen.

## <a name="running-remote-commands"></a>Kör fjärrkommandon

Med funktionen ny fjärran sluten PowerShell-flik är det enkelt att upprätta en permanent användar hanterad Windows PowerShell-session ("PSSession") till den lokala datorn eller en fjärran sluten dator. Kommandot öppnar ett popup-fönster där du uppmanas att ange ett dator namn och för det användar konto som har behörighet att köra kommandon på fjärrdatorn.

## <a name="customizing-the-view"></a>Anpassa vyn

Du kan använda Windows PowerShell ISE funktioner för att flytta och ändra storlek på konsol fönstret och skript fönstret. Du kan visa och dölja båda Fönstren och du kan ändra text storleken i alla rutor.

Du kan också använda fönstret alternativ för att anpassa utseendet och åtgärden för Windows PowerShell ISE. Windows PowerShell ISE har dessutom en anpassad värd variabel, $psISE, som du kan använda för att anpassa Windows PowerShell ISE, inklusive lägga till menyer och meny objekt.

## <a name="windows-powershell-ise-profile"></a>Windows PowerShell ISE profil

Windows PowerShell ISE har en egen Windows PowerShell-profil Microsoft.PowerShellISE_profile.ps1. I den här profilen kan du lagra funktioner, alias, variabler och kommandon som du använder i Windows PowerShell ISE.

Objekt i Windows PowerShell AllHosts-profiler (CurrentUser \\ AllHosts och allusers \\ AllHosts) är också tillgängliga i Windows PowerShell ISE, precis som de finns i Windows PowerShell-värdprogram. Objekten i Windows PowerShell-konsolens profiler är dock inte tillgängliga i Windows PowerShell ISE.

Instruktioner för att flytta och konfigurera om dina profiler finns i Windows PowerShell ISE hjälp och i about_Profiles.

## <a name="notes"></a>ANTECKNINGAR

Windows PowerShell ISE är en valfri Windows-funktion som är aktive rad som standard på klient-och Server versioner av Windows. Om du vill aktivera och inaktivera Windows PowerShell ISE i klient versioner av Windows använder du aktivera eller inaktivera Windows-funktioner på kontroll panelen. Om du vill aktivera och inaktivera Windows PowerShell ISE i Server versioner av Windows använder du guiden Lägg till roller och funktioner i Serverhanteraren.

Eftersom Windows PowerShell ISE kräver ett användar gränssnitt fungerar det inte på Server Core-installationer av Windows Server. Men om du lägger till funktionen Windows PowerShell ISE konverteras installationen automatiskt till servern med ett grafiskt användar gränssnitt.

Windows PowerShell ISE bygger på Windows Presentation Foundation (WPF).
Om de grafiska elementen i Windows PowerShell ISE inte återges på rätt sätt i systemet kan du lösa problemet genom att lägga till eller justera inställningarna "inaktivera WPF Hardware acceleration" i systemet. Mer information finns i [register inställningar för bild åter givning](/dotnet/framework/wpf/graphics-multimedia/graphics-rendering-registry-settings).

## <a name="see-also"></a>SE ÄVEN

[about_Debuggers](about_Debuggers.md)

[about_Profiles](about_Profiles.md)

[about_Updatable_Help](about_Updatable_Help.md)

[Get – hjälp](xref:Microsoft.PowerShell.Core.Get-Help)

[Get-IseSnippet](xref:ISE.Get-IseSnippet)

[Importera – IseSnippet](xref:ISE.Import-IseSnippet)

[New-IseSnippet](xref:ISE.New-IseSnippet)

[Spara – hjälp](xref:Microsoft.PowerShell.Core.Save-Help)

[Visa-kommando](xref:Microsoft.PowerShell.Utility.Show-Command)

[Uppdatera – hjälp](xref:Microsoft.PowerShell.Core.Update-Help)
