---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Felsök skript i Windows PowerShell ISE
ms.openlocfilehash: b7af2de83a3f796a2057514e36ad8b74367e8ce2
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405985"
---
# <a name="how-to-debug-scripts-in-windows-powershell-ise"></a>Felsök skript i Windows PowerShell ISE

Den här artikeln beskriver hur du felsöker skript på en lokal dator med Windows PowerShell Integrated Scripting Environment (ISE) visual felsökningsfunktioner.

## <a name="how-to-manage-breakpoints"></a>Så här hanterar du brytpunkter

En brytpunkt är en avsedda platsen där du vill att pausa så att du kan kontrollera det aktuella tillståndet för variablerna och miljön där skriptet körs i ett skript. När skriptet har pausats av en brytpunkt, kan du köra kommandon i konsolfönstret för att undersöka tillståndet för ditt skript.  Du kan mata ut variabler eller köra andra kommandon. Du kan även ändra värdet för alla variabler som är synliga för kontexten för skriptet som körs för tillfället. När du har undersökt vad du vill se, kan du återuppta användningen av skript.

Du kan ange tre typer av brytpunkter i Windows PowerShell-felsökningsmiljö:

1. **Rad brytpunkt**. Skriptet pausar när den angivna raden har nåtts under drift av skriptet

2. **Variabeln brytpunkt.** Skriptet pausar när avsedda variabelns värde ändras.

3. **Kommandot brytpunkt.** Skriptet pausar när det angivna kommandot är håller på att köras under drift av skriptet. Den kan innehålla parametrar för att filtrera ytterligare brytpunkt för den åtgärd som du vill. Kommandot kan också vara en funktion som du skapade.

Dessa i Windows PowerShell ISE felsökningsmiljö, kan endast rad brytpunkter anges med hjälp av menyn eller kortkommandon. De andra två typerna av brytpunkter kan ställas in, men de har angetts från konsolfönstret genom att använda den [Set-PSBreakpoint](https://technet.microsoft.com/library/88d2d9ad-17dc-44ae-99aa-f841125b9dc8) cmdlet. Det här avsnittet beskrivs hur du kan utföra fjärrfelsökning uppgifter i Windows PowerShell ISE genom att använda menyerna där det är tillgängligt och utföra fler kommandon från konsolfönstret med hjälp av skript.

### <a name="to-set-a-breakpoint"></a>Ange en brytpunkt

Ställas kan in en brytpunkt i ett skript efter det att den har sparats. Högerklicka på den rad där du vill konfigurera en brytpunkt på rad och klicka sedan på **/Radera brytpunkt**. Alternativt klickar du på den rad där du vill ange en brytpunkt på rad, och tryck på **F9** eller på den **felsöka** -menyn klickar du på **/Radera brytpunkt**.

Följande skript är ett exempel på hur du kan ange en variabel brytpunkt från konsolfönstret genom att använda den [Set-PSBreakpoint](https://technet.microsoft.com/library/6afd5d2c-a285-4796-8607-3cbf49471420) cmdlet.

```powershell
# This command sets a breakpoint on the Server variable in the Sample.ps1 script.
Set-PSBreakpoint -Script sample.ps1 -Variable Server
```

### <a name="list-all-breakpoints"></a>Lista över alla brytpunkter

Visar alla brytpunkter i den aktuella Windows PowerShell-sessionen.

På den **felsöka** -menyn klickar du på **lista brytpunkter**. Följande skript är ett exempel på hur du kan lista alla brytpunkter från konsolfönstret genom att använda den [Get-PSBreakpoint](https://technet.microsoft.com/library/0bf48936-00ab-411c-b5e0-9b10a812a3c6) cmdlet.

```powershell
# This command lists all breakpoints in the current session.
Get-PSBreakpoint
```

### <a name="remove-a-breakpoint"></a>Ta bort en brytpunkt

Ta bort en brytpunkt tas den bort.

Om du tror att du kanske vill använda det igen senare bör du överväga att [inaktivera en brytpunkt](#disable-a-breakpoint) den i stället.
Högerklicka på den rad där du vill ta bort en brytpunkt och klicka sedan på **/Radera brytpunkt**.
Alternativt klickar du på den rad där du vill ta bort en brytpunkt på den **felsöka** -menyn klickar du på **/Radera brytpunkt**.
Följande skript är ett exempel på hur du tar bort en brytpunkt med ett specifikt ID från konsolfönstret genom att använda den [Remove-PSBreakpoint](https://technet.microsoft.com/library/4c877a80-0ea0-4790-9281-88c08ef0ddd6) cmdlet.

```powershell
# This command deletes the breakpoint with breakpoint ID 2.
Remove-PSBreakpoint -Id 2
```

### <a name="remove-all-breakpoints"></a>Ta bort alla brytpunkter

Ta bort alla brytpunkter som definierats i den aktuella sessionen på den **felsöka** -menyn klickar du på **ta bort alla brytpunkter**.

Följande skript är ett exempel på hur du tar bort alla brytpunkter från konsolfönstret genom att använda den [Remove-PSBreakpoint](https://technet.microsoft.com/library/4c877a80-0ea0-4790-9281-88c08ef0ddd6) cmdlet.

```powershell
# This command deletes all of the breakpoints in the current session.
Get-PSBreakpoint | Remove-PSBreakpoint
```

### <a name="disable-a-breakpoint"></a>Inaktivera en brytpunkt

Inaktivera en brytpunkt tar inte bort. Det inaktiverar den förrän den har aktiverats.  Om du vill inaktivera en specifik rad brytpunkt, högerklickar du på den rad där du vill inaktivera en brytpunkt och klicka sedan på **inaktivera brytpunkt**. Alternativt klickar du på den rad där du vill inaktivera en brytpunkt, och tryck på **F9** eller på den **felsöka** -menyn klickar du på **inaktivera brytpunkt**. Följande skript är ett exempel på hur du tar bort en brytpunkt med ett specifikt ID från konsolfönstret genom att använda den [inaktivera PSBreakpoint](https://technet.microsoft.com/library/d4974e9b-0aaa-4e20-b87f-f599a413e4e8) cmdlet.

```powershell
# This command disables the breakpoint with breakpoint ID 0.
Disable-PSBreakpoint -Id 0
```

### <a name="disable-all-breakpoints"></a>Inaktivera alla brytpunkter

Inaktivera en brytpunkt tar inte bort. Det inaktiverar den förrän den har aktiverats.  Att inaktivera alla brytpunkter i den aktuella sessionen på den **felsöka** -menyn klickar du på **inaktivera alla brytpunkter**. Följande skript är ett exempel på hur du kan inaktivera alla brytpunkter från konsolfönstret genom att använda den [inaktivera PSBreakpoint](https://technet.microsoft.com/library/d4974e9b-0aaa-4e20-b87f-f599a413e4e8) cmdlet.

```powershell
# This command disables all breakpoints in the current session.
# You can abbreviate this command as: "gbp | dbp".
Get-PSBreakpoint | Disable-PSBreakpoint
```

### <a name="enable-a-breakpoint"></a>Aktivera en brytpunkt

Om du vill aktivera en specifik brytpunkt, högerklickar du på den rad där du vill aktivera en brytpunkt och klicka sedan på **aktivera brytpunkt**. Alternativt klickar du på den rad där du vill aktivera en brytpunkt och tryck sedan på **F9** eller på den **felsöka** -menyn klickar du på **aktivera brytpunkt**. Följande skript är ett exempel på hur du kan aktivera specifika brytpunkter från konsolfönstret genom att använda den [aktivera PSBreakpoint](https://technet.microsoft.com/library/739e1091-3b3f-405f-a428-bec7543e5df0) cmdlet.

```powershell
# This command enables breakpoints with breakpoint IDs 0, 1, and 5.
Enable-PSBreakpoint -Id 0, 1, 5
```

### <a name="enable-all-breakpoints"></a>Aktivera alla brytpunkter

Aktivera alla brytpunkter som definierats i den aktuella sessionen på den **felsöka** -menyn klickar du på **aktivera alla brytpunkter**. Följande skript är ett exempel på hur du kan aktivera alla brytpunkter från konsolfönstret genom att använda den [aktivera PSBreakpoint](https://technet.microsoft.com/library/739e1091-3b3f-405f-a428-bec7543e5df0) cmdlet.

```powershell
# This command enables all breakpoints in the current session.
# You can abbreviate the command by using their aliases: "gbp | ebp".
Get-PSBreakpoint | Enable-PSBreakpoint
```

## <a name="how-to-manage-a-debugging-session"></a>Så här hanterar du en felsökningssession

Innan du startar felsökning, måste du ange en eller flera brytpunkter. Du kan inte ange en brytpunkt, såvida inte det skript som du vill felsöka sparas. Läs anvisningarna för hur du ställer in en brytpunkt [hantera brytpunkter](#how-to-manage-breakpoints) eller [Set-PSBreakpoint](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-psbreakpoint). När du startar felsökning, kan du inte redigera ett skript tills du stoppa felsökningen. Ett skript som har en eller flera brytpunkter som ställs in sparas automatiskt innan den körs.

### <a name="to-start-debugging"></a>Att starta felsökning

Tryck på **F5** i verktygsfältet klickar du på den **kör skript** ikonen eller på den **felsöka** menyn klickar du på **kör/Fortsätt**. Skriptet körs tills den första brytpunkten påträffas. Den pausar igen där och visar den raden där det pausades.

### <a name="to-continue-debugging"></a>Att fortsätta felsökningen

Tryck på **F5** i verktygsfältet klickar du på den **kör skript** ikonen eller på den **felsöka** -menyn klickar du på **kör/Fortsätt** skriva i konsolfönstret **C** och tryck sedan på **RETUR**. Detta leder till att skriptet ska fortsätta att köra till nästa brytpunkt eller i slutet av skriptet om inga ytterligare brytpunkter uppstår.

### <a name="to-view-the-call-stack"></a>Visa anropsstacken

Anropsstacken visar den aktuella körningsplats i skriptet. Om skriptet körs i en funktion som anropades av en annan funktion, sedan som representeras i visningen av ytterligare rader i utdata. Den nedersta raden visar det ursprungliga skriptet och raden i det som en funktion anropades. Nästa rad anger funktionen och raden i det som en annan funktion kanske har anropats.  Den översta raden visar aktuell kontext för den aktuella raden brytpunkten har angetts.

När pausad, om du vill se aktuella anropsstacken, trycker du på **CTRL + SKIFT + D** eller på den **felsöka** -menyn klickar du på **visa anropsstack** skriva i konsolfönstret **K**  och tryck sedan på **RETUR**.

### <a name="to-stop-debugging"></a>Att stoppa felsökningen

Tryck på **SKIFT F5** eller på den **felsöka** -menyn klickar du på **stoppa felsökare**, skriva i konsolfönstret **Q** och tryck sedan på  **Ange**.

## <a name="how-to-step-over-step-into-and-step-out-while-debugging"></a>Stega över, Stega in och steg när du felsöker

Stega dig är processen att köra en instruktion i taget. Du kan stoppa på en rad med kod och granska värdena för variabler och tillståndet för systemet. I följande tabell beskrivs vanliga felsökning uppgifter, till exempel Stega dig över, gå till och gå.

| Felsökning av uppgiften | Beskrivning | Hur du utför i PowerShell ISE |
| --- | --- | --- |
| **Stega in** | Kör den aktuella instruktionen och sedan stoppas vid nästa instruktionen. Om den aktuella instruktionen är en funktion eller skriptanrop sedan felsökare stegen i den funktion eller ett skript, annars avbryts vid nästa fel. | Tryck på **F11** eller på den **felsöka** -menyn klickar du på **Stega**, eller i konsolfönstret skriver **S** och tryck på **RETUR**. |
| **Hoppa över** | Kör den aktuella instruktionen och sedan stoppas vid nästa instruktionen. Om den aktuella instruktionen är en funktion eller skriptanrop sedan felsökningsprogrammet körs hela funktionen eller skript och stoppas vid nästa fel efter funktionsanropet. | Tryck på **F10** eller på den **felsöka** -menyn klickar du på **Stega**, eller i konsolfönstret skriver **V** och tryck på **RETUR**. |
| **Stega ut** | Steg utanför den aktuella funktionen och upp en nivå om funktionen är kapslade. Om i brödtext, körs skriptet i slutet eller till nästa brytpunkt. Överhoppade instruktionerna körs, men inte stegvis via. | Tryck på **SKIFT + F11**, eller på den **felsöka** -menyn klickar du på **Stega ut**, eller i konsolfönstret skriver **O** och tryck på **RETUR**. |
| **Fortsätta** | Fortsätter körningen till slutet eller till nästa brytpunkt. Överhoppade funktions- och anrop är körs, men inte stegvis via. | Tryck på **F5** eller på den **felsöka** -menyn klickar du på **kör/Fortsätt**, eller i konsolfönstret skriver **C** och tryck på **RETUR**. |

## <a name="how-to-display-the-values-of-variables-while-debugging"></a>Så här visar du värdena för variabler vid felsökning

Du kan visa de aktuella värdena för variabler i skriptet som du går igenom koden.

### <a name="to-display-the-values-of-standard-variables"></a>Visa värdena för variabler som standard

Använd någon av följande metoder:

- Hovra över variabeln för att visa dess värde som en knappbeskrivning i fönstret skript.

- I konsolfönstret skriver variabelnamn och tryck på **RETUR**.

Alla fönster i ISE är alltid i samma definitionsområde. När du felsöker ett skript, kör därför de kommandon som du skriver i konsolfönstret i skriptet omfång. På så sätt kan du använda konsolfönstret för att hitta värdena för variabler och anropa funktioner som definieras endast i skriptet.

### <a name="to-display-the-values-of-automatic-variables"></a>Visa värden över automatiska variabler

Du kan använda föregående metod för att visa värdet för nästan alla variabler när du felsöker ett skript. Dessa metoder fungerar dock inte för följande automatiska variabler.

- $_

- $Input

- $MyInvocation

- $PSBoundParameters

- $Args

Om du försöker visa värdet för någon av dessa variabler, får du värdet för variabeln för en intern pipeline felsökningsprogrammet, inte värdet används av variabeln i skriptet. Du kan komma runt detta för några variabler ($_, $Input, $MyInvocation, $PSBoundParameters och $Args) med hjälp av följande metod:

1. Tilldela värdet för den automatiska variabeln till en ny variabel i skriptet.

2. Visa värdet för variabeln, antingen genom att hovra över den nya variabeln i skriptfönstret eller genom att skriva ny variabel i konsolfönstret.

Till exempel om du vill visa värdet för variabeln $MyInvocation i skriptet, tilldela värdet till en ny variabel, till exempel $scriptname, och sedan hovra över eller Skriv $scriptname variabeln för att visa dess värde.

```powershell
# In C:\ps-test\MyScript.ps1
$scriptname = $MyInvocation.MyCommand.Path
```

```output
# In the Console Pane:
PS> .\MyScript.ps1
PS> $scriptname
C:\ps-test\MyScript.ps1
```

## <a name="see-also"></a>Se även

- [Utforska Windows PowerShell ISE](../../getting-started/fundamental/exploring-the-windows-powershell-ise.md)