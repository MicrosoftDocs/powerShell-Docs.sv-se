---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: "Felsöka skript i Windows PowerShell ISE"
ms.openlocfilehash: 0ec520dfcba5e4562258256570f140e618e77cdb
ms.sourcegitcommit: 3720ce4efb6735694cfb53a1b793d949af5d1bc5
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/29/2017
---
# <a name="how-to-debug-scripts-in-windows-powershell-ise"></a>Felsöka skript i Windows PowerShell ISE

Det här avsnittet beskriver hur du felsöker skript på en lokal dator med hjälp av Windows PowerShell Integrated Scripting Environment (ISE) visual felsökning funktioner.

## <a name="how-to-manage-breakpoints"></a>Så här hanterar du brytpunkter
En brytpunkt är avsedda platsen i ett skript som var du vill att pausa så att du kan kontrollera det aktuella tillståndet för variablerna och miljön där skriptet körs. När skriptet har pausats av en brytpunkt, kan du köra kommandon i konsolfönstret för att kontrollera tillståndet för skriptet.  Du kan skapa variabler eller köra andra kommandon. Du kan även ändra värdet för alla variabler som är synliga i kontexten av skriptet körs för tillfället. När du har undersökt vad du vill se, kan du återuppta användningen av skript.

Du kan ange tre typer av brytpunkter i felsökningsmiljö för Windows PowerShell:

1. **Rad brytpunkt**. Skriptet pausar när den angivna raden nås under drift av skriptet

2. **Variabeln brytpunkt.** Skriptet pausar när avsedda variabelns värde ändras.

3. **Kommandot brytpunkt.** Skriptet pausar när kommandot avsedda håller på att köras under drift av skriptet. Det kan innefatta parametrar för att filtrera ytterligare brytpunkt för den åtgärd som du vill. Kommandot kan också vara en funktion som du skapade.

Dessa i Windows PowerShell ISE felsökningsmiljö, kan endast rad brytpunkter anges med hjälp av menyn eller kortkommandon. De andra två typerna av brytpunkter kan anges, men de har angetts från konsolfönstret med hjälp av den [Set PSBreakpoint](https://technet.microsoft.com/library/88d2d9ad-17dc-44ae-99aa-f841125b9dc8) cmdlet. Det här avsnittet beskrivs hur du kan utföra felsökning aktiviteter i Windows PowerShell ISE via menyer där det är tillgängligt och utföra fler kommandon från konsolfönstret med hjälp av skript.

### <a name="to-set-a-breakpoint"></a>Ange en brytpunkt
En brytpunkt kan anges i ett skript efter att den har sparats. Högerklicka på den rad där du vill ange en brytpunkt i rad och klicka sedan på **brytpunkt**. Eller klicka på den rad där du vill ange en brytpunkt rad, och tryck på **F9** eller på den **felsöka** -menyn klickar du på **brytpunkt**.

Följande skript är ett exempel på hur du kan ange en variabel brytpunkt från konsolfönstret med hjälp av den [Set PSBreakpoint](https://technet.microsoft.com/library/6afd5d2c-a285-4796-8607-3cbf49471420) cmdlet.

``` PowerShell
# This command sets a breakpoint on the Server variable in the Sample.ps1 script.
Set-PSBreakpoint -Script sample.ps1 -Variable Server
```

### <a name="list-all-breakpoints"></a>Visa en lista med alla brytpunkter

Visar alla brytpunkter i den aktuella Windows PowerShell-sessionen.

På den **felsöka** -menyn klickar du på **lista brytpunkter**. Följande skript är ett exempel på hur du kan visa en lista med alla brytpunkter från konsolfönstret med hjälp av den [Get-PSBreakpoint](https://technet.microsoft.com/library/0bf48936-00ab-411c-b5e0-9b10a812a3c6) cmdlet.

``` PowerShell
# This command lists all breakpoints in the current session. 
Get-PSBreakpoint
```

### <a name="remove-a-breakpoint"></a>Ta bort en brytpunkt

Ta bort en brytpunkt tas den bort.

Om du tror att du kanske vill använda igen bör du överväga att [inaktiverar en brytpunkt](#disable-a-breakpoint) den i stället.
Högerklicka på den rad där du vill ta bort en brytpunkt och klicka sedan på **brytpunkt**.
Eller klicka på den rad där du vill ta bort en brytpunkt i den **felsöka** -menyn klickar du på **brytpunkt**.
Följande skript är ett exempel på hur du tar bort en brytpunkt med angivet ID från konsolfönstret med hjälp av den [ta bort PSBreakpoint](https://technet.microsoft.com/library/4c877a80-0ea0-4790-9281-88c08ef0ddd6) cmdlet.

``` PowerShell
# This command deletes the breakpoint with breakpoint ID 2.
Remove-PSBreakpoint -Id 2
```

### <a name="remove-all-breakpoints"></a>Ta bort alla brytpunkter
Ta bort alla brytpunkter som definierats i den aktuella sessionen på den **felsöka** -menyn klickar du på **ta bort alla brytpunkter**.

Följande skript är ett exempel på hur du tar bort alla brytpunkter från konsolfönstret med hjälp av den [ta bort PSBreakpoint](https://technet.microsoft.com/library/4c877a80-0ea0-4790-9281-88c08ef0ddd6) cmdlet.

``` PowerShell
# This command deletes all of the breakpoints in the current session.
Get-PSBreakpoint | Remove-PSBreakpoint
```

### <a name="disable-a-breakpoint"></a>Inaktivera en brytpunkt
Om du inaktiverar en brytpunkt tas inte bort. Det inaktiverar den förrän den har aktiverats.  Högerklicka på den rad där du vill inaktivera en brytpunkt och klicka sedan på om du vill inaktivera en specifik rad brytpunkt **inaktivera brytpunkt**. Eller klicka på den rad där du vill inaktivera en brytpunkt, och tryck på **F9** eller på den **felsöka** -menyn klickar du på **inaktivera brytpunkt**. Följande skript är ett exempel på hur du tar bort en brytpunkt med angivet ID i konsolfönstret med hjälp av den [inaktivera PSBreakpoint](https://technet.microsoft.com/library/d4974e9b-0aaa-4e20-b87f-f599a413e4e8) cmdlet.

``` PowerShell
# This command disables the breakpoint with breakpoint ID 0.
Disable-PSBreakpoint -Id 0
```

### <a name="disable-all-breakpoints"></a>Inaktivera alla brytpunkter
Om du inaktiverar en brytpunkt tas inte bort. Det inaktiverar den förrän den har aktiverats.  För att inaktivera alla brytpunkter i den aktuella sessionen på den **felsöka** -menyn klickar du på **inaktivera alla brytpunkter**. Följande skript är ett exempel på hur du kan inaktivera alla brytpunkter från konsolfönstret med hjälp av den [inaktivera PSBreakpoint](https://technet.microsoft.com/library/d4974e9b-0aaa-4e20-b87f-f599a413e4e8) cmdlet.

``` PowerShell
# This command disables all breakpoints in the current session. 
# You can abbreviate this command as: "gbp | dbp".
Get-PSBreakpoint | Disable-PSBreakpoint
```

### <a name="enable-a-breakpoint"></a>Aktivera en brytpunkt
Högerklicka på raden där du vill aktivera en brytpunkt och klicka sedan på om du vill aktivera en specifik brytpunkt **aktivera brytpunkt**. Eller klicka på den rad där du vill aktivera en brytpunkt och tryck sedan på **F9** eller på den **felsöka** -menyn klickar du på **aktivera brytpunkt**. Följande skript är ett exempel på hur du kan aktivera specifika brytpunkter från konsolfönstret med hjälp av den [aktivera PSBreakpoint](https://technet.microsoft.com/library/739e1091-3b3f-405f-a428-bec7543e5df0) cmdlet.

``` PowerShell
# This command enables breakpoints with breakpoint IDs 0, 1, and 5.
Enable-PSBreakpoint -Id 0, 1, 5
```

### <a name="enable-all-breakpoints"></a>Aktivera alla brytpunkter
Aktivera alla brytpunkter som definierats i den aktuella sessionen på den **felsöka** -menyn klickar du på **aktivera alla brytpunkter**. Följande skript är ett exempel på hur du kan aktivera alla brytpunkter från konsolfönstret med hjälp av den [aktivera PSBreakpoint](https://technet.microsoft.com/library/739e1091-3b3f-405f-a428-bec7543e5df0) cmdlet.

``` PowerShell
# This command enables all breakpoints in the current session. 
# You can abbreviate the command by using their aliases: "gbp | ebp".
Get-PSBreakpoint | Enable-PSBreakpoint
```

## <a name="how-to-manage-a-debugging-session"></a>Så här hanterar du en felsökning
Innan du startar felsökning, måste du ange en eller flera brytpunkter. Du kan inte ange en brytpunkt såvida inte det skript som du vill felsöka sparas. Mer information om hur du ställer in en brytpunkt finns [hantera brytpunkter](#how-to-manage-breakpoints) eller [Set PSBreakpoint](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/set-psbreakpoint). När du startar felsökning kan du inte redigera ett skript tills du avbryter felsökning. Ett skript som har en eller flera brytpunkter ange sparas automatiskt innan den körs.

### <a name="to-start-debugging"></a>Starta felsökning
Tryck på **F5** i verktygsfältet klickar du på den **kör skriptet** ikonen, eller på den **felsöka** och klicka **kör/Fortsätt**. Skriptet körs tills den första brytpunkten påträffas. Den pausar det igen och markerar den rad där det pausades.

### <a name="to-continue-debugging"></a>Att fortsätta felsökningen
Tryck på **F5** i verktygsfältet klickar du på den **kör skriptet** ikonen, eller på den **felsöka** -menyn klickar du på **kör/Fortsätt** skriva i konsolfönstret **C** och tryck sedan på **RETUR**. Detta gör skriptet du vill fortsätta till nästa brytpunkt eller till slutet av skriptet om inga ytterligare brytpunkter påträffas.

### <a name="to-view-the-call-stack"></a>Visa anropsstacken
Anropsstacken visar den aktuella platsen köra skriptet. Om skriptet körs i en funktion som anropades av en annan funktion, sedan som representeras i visningen av nya rader i utdata. Den nedersta raden visar det ursprungliga skriptet och raden i det som en funktion anropades. Nästa rad anger att funktionen och raden i det som en annan funktion kanske har anropats.  Den översta raden visar aktuell kontext för den aktuella raden brytpunkten har angetts.

När pausad, om du vill visa aktuella anropsstacken trycker du på **CTRL + SKIFT + D** eller på den **felsöka** -menyn klickar du på **visa anropsstack** skriva i konsolfönstret **K**  och tryck sedan på **RETUR**.

### <a name="to-stop-debugging"></a>Stoppa felsökning
Tryck på **SKIFT F5** eller på den **felsöka** -menyn klickar du på **stoppa felsökare**, skriva i konsolfönstret **Q** och tryck sedan på  **Ange**.

## <a name="how-to-step-over-step-into-and-step-out-while-debugging"></a>Hur du hoppa över steg i och stega ut vid felsökning
Stega igenom är processen med att köra en instruktion i taget. Du kan stoppa på en rad med kod och undersöka värden för variabler och systemets tillstånd. I följande tabell beskrivs vanliga felsökning uppgifter, till exempel gå över, gå till och gå.

| Felsökning av aktivitet | Beskrivning | Hur du utför i PowerShell ISE |
| --- | --- | --- |
| **Gå till** | Kör den aktuella instruktionen och sedan stoppas vid nästa instruktion. Om den aktuella instruktionen är en funktion eller skript anropet sedan felsökare stegen i den funktion eller ett skript, annars avbryts vid nästa fel. | Tryck på **F11** eller på den **felsöka** -menyn klickar du på **Stega**, eller Skriv i konsolfönstret **S** och tryck på **RETUR**. |
| **Hoppa över** | Kör den aktuella instruktionen och sedan stoppas vid nästa instruktion. Om den aktuella instruktionen är en funktion eller ett skript anrop sedan felsökningsprogrammet körs hela funktion eller skript och slutar vid nästa fel efter funktionsanropet. | Tryck på **F10** eller på den **felsöka** -menyn klickar du på **Stega**, eller Skriv i konsolfönstret **V** och tryck på **RETUR**. |
| **Gå ut** | Steg utanför den aktuella funktionen och en nivå om funktionen är kapslad. Om i brödtexten, körs skriptet till slutet eller till nästa brytpunkt. Överhoppade instruktionerna körs, men inte instruktionerna. | Tryck på **SKIFT + F11**, eller på den **felsöka** -menyn klickar du på **Stega ut**, eller Skriv i konsolfönstret **O** och tryck på **RETUR**. |
| **Fortsätt** | Fortsätter körningen till slutet eller till nästa brytpunkt. Hoppades över funktioner och anrop är köras, men inte instruktionerna. | Tryck på **F5** eller på den **felsöka** -menyn klickar du på **kör/Fortsätt**, eller Skriv i konsolfönstret **C** och tryck på **RETUR**. |

## <a name="how-to-display-the-values-of-variables-while-debugging"></a>Så här visar du värdena för variabler vid felsökning
Du kan visa de aktuella värdena för variabler i skriptet som du stega igenom koden.

### <a name="to-display-the-values-of-standard-variables"></a>Visa värdena för variabler som standard
Använd någon av följande metoder:

- I fönstret skript hovra över variabeln för att visa dess värde som en knappbeskrivning.

- Ange namn och tryck på i konsolfönstret **RETUR**.

Alla fönster i ISE är alltid i samma definitionsområde. När du felsöker ett skript, därför körs kommandon som du skriver i konsolfönstret i skriptet omfång. På så sätt kan du använda konsolfönstret att hitta värdena för variabler och anropa funktioner som är definierade i skriptet.

### <a name="to-display-the-values-of-automatic-variables"></a>Visa värden över automatiska variabler
Du kan använda föregående metod för att visa värdet för nästan alla variabler när du felsöker ett skript. Dessa metoder fungerar dock inte för följande automatiska variabler.

- $_

- $Input

- $MyInvocation

- $PSBoundParameters

- $Args

Om du försöker visa värdet för någon av dessa variabler hämta värdet för variabeln för en intern pipeline felsökningsprogrammet, inte värdet används av variabeln i skriptet. Du kan undvika detta för några variabler ($_, $Input, $MyInvocation, $PSBoundParameters och $Args) med hjälp av följande metod:

1. Tilldela värdet för den automatiska variabeln till en ny variabel i skriptet.

2. Visa värdet för den nya variabeln hovrar över den nya variabeln i skriptfönstret eller genom att skriva den nya variabeln i konsolfönstret.

Till exempel om du vill visa värdet för variabeln $MyInvocation i skriptet tilldela värdet till en ny variabel, exempelvis $scriptname, och sedan hovra över eller ange $scriptname variabel om du vill visa dess värde.

``` PowerShell
#In MyScript.ps1
$scriptname = $MyInvocation.MyCommand.Path

#In the Console Pane:
C:\ps-test> $scriptname
C:\ps-test\MyScript.ps1
```

## <a name="see-also"></a>Se även
- [Med hjälp av Windows PowerShell ISE](Using-the-Windows-PowerShell-ISE.md)

