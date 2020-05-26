---
ms.date: 01/02/2020
keywords: powershell,cmdlet
title: Felsök skript i Windows PowerShell ISE
ms.openlocfilehash: 6fbe340cbff832b5d0e2a5515ef432cec574a3c1
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/23/2020
ms.locfileid: "83810675"
---
# <a name="how-to-debug-scripts-in-windows-powershell-ise"></a>Felsök skript i Windows PowerShell ISE

Den här artikeln beskriver hur du felsöker skript på en lokal dator med hjälp av fel söknings funktionerna i Windows PowerShell ISE (Integrated Scripting Environment).

## <a name="how-to-manage-breakpoints"></a>Hantera Bryt punkter

En Bryt punkt är en utsedd punkt i ett skript där du vill att åtgärden ska pausas så att du kan undersöka det aktuella läget för variablerna och miljön där skriptet körs.
När skriptet har pausats med en Bryt punkt kan du köra kommandon i konsol fönstret för att kontrol lera status för skriptet. Du kan mata ut variabler eller köra andra kommandon. Du kan till och med ändra värdet för alla variabler som är synliga för kontexten för det skript som körs för tillfället. När du har undersökt vad du vill se kan du återuppta körningen av skriptet.

Du kan ange tre typer av Bryt punkter i fel söknings miljön i Windows PowerShell:

1. **Rad Bryt punkt**. Skriptet pausar när den angivna raden har nåtts vid körning av skriptet

1. **Variabel Bryt punkt.** Skriptet pausas när den angivna variabelns värde ändras.

1. **Kommando Bryt punkt.** Skriptet pausas när det angivna kommandot ska köras när skriptet körs. Den kan innehålla parametrar för att ytterligare filtrera Bryt punkten till den åtgärd som du vill använda. Kommandot kan också vara en funktion som du har skapat.

Av dessa, i Windows PowerShell ISE fel söknings miljö, kan endast rad Bryt punkter anges med hjälp av menyn eller kortkommandona. De andra två typerna av Bryt punkter kan anges, men de ställs in från konsol fönstret med hjälp av cmdleten [set-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Set-PSBreakpoint) . I det här avsnittet beskrivs hur du kan utföra fel sökning av uppgifter i Windows PowerShell ISE genom att använda menyerna där de är tillgängliga och utföra ett bredare antal kommandon från konsol fönstret med hjälp av skript.

### <a name="to-set-a-breakpoint"></a>Ange en Bryt punkt

En Bryt punkt kan bara anges i ett skript när den har sparats. Högerklicka på linjen där du vill ange en rad Bryt punkt och klicka sedan på **Växla Bryt punkt**. Alternativt klickar du på linjen där du vill ange en rad Bryt punkt och trycker på <kbd>F9</kbd> eller klickar på **Växla Bryt punkt**på **fel söknings** menyn.

Följande skript är ett exempel på hur du kan ange en variabel Bryt punkt från konsol fönstret med hjälp av cmdleten [set-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Set-PSBreakpoint) .

```powershell
# This command sets a breakpoint on the Server variable in the Sample.ps1 script.
Set-PSBreakpoint -Script sample.ps1 -Variable Server
```

### <a name="list-all-breakpoints"></a>Lista alla Bryt punkter

Visar alla Bryt punkter i den aktuella Windows PowerShell-sessionen.

På **fel söknings** menyn klickar du på **list Bryt punkter**. Följande skript är ett exempel på hur du kan visa alla Bryt punkter från konsol fönstret med hjälp av cmdleten [Get-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Get-PSBreakpoint) .

```powershell
# This command lists all breakpoints in the current session.
Get-PSBreakpoint
```

### <a name="remove-a-breakpoint"></a>Ta bort en Bryt punkt

Borttagning av en Bryt punkt tar bort den.

Om du tror att du kanske vill använda den igen senare bör du [inaktivera en Bryt punkt](#disable-a-breakpoint) i stället. Högerklicka på linjen där du vill ta bort en Bryt punkt och klicka sedan på **ToggleBreakpoint**.
Du kan också klicka på den rad där du vill ta bort en Bryt punkt och på **fel söknings** menyn klickar du på **Växla Bryt punkt**. Följande skript är ett exempel på hur du tar bort en Bryt punkt med ett angivet ID från konsol fönstret med hjälp av cmdleten [Remove-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Remove-PSBreakpoint) .

```powershell
# This command deletes the breakpoint with breakpoint ID 2.
Remove-PSBreakpoint -Id 2
```

### <a name="remove-all-breakpoints"></a>Ta bort alla Bryt punkter

Om du vill ta bort alla Bryt punkter som definierats i den aktuella sessionen klickar du på **ta bort alla Bryt punkter**på **Felsök** -menyn.

Följande skript är ett exempel på hur du tar bort alla Bryt punkter från konsol fönstret med hjälp av cmdleten [Remove-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Remove-PSBreakpoint) .

```powershell
# This command deletes all of the breakpoints in the current session.
Get-PSBreakpoint | Remove-PSBreakpoint
```

### <a name="disable-a-breakpoint"></a>Inaktivera en Bryt punkt

Om du inaktiverar en Bryt punkt tas den inte bort. den stänger av den tills den är aktive rad. Om du vill inaktivera en speciell rad Bryt punkt högerklickar du på linjen där du vill inaktivera en Bryt punkt och klickar sedan på **inaktivera Bryt punkt**. Eller klicka på den rad där du vill inaktivera en Bryt punkt och tryck på <kbd>F9</kbd> eller på **fel söknings** menyn, klicka på **inaktivera Bryt punkt**. Följande skript är ett exempel på hur du kan ta bort en Bryt punkt med ett angivet ID från konsol fönstret med hjälp av cmdleten [disable-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Disable-PSBreakpoint) .

```powershell
# This command disables the breakpoint with breakpoint ID 0.
Disable-PSBreakpoint -Id 0
```

### <a name="disable-all-breakpoints"></a>Inaktivera alla Bryt punkter

Om du inaktiverar en Bryt punkt tas den inte bort. den stänger av den tills den är aktive rad. Om du vill inaktivera alla Bryt punkter i den aktuella sessionen går du till **Felsök** -menyn och klickar på **inaktivera alla Bryt punkter**. Följande skript är ett exempel på hur du kan inaktivera alla Bryt punkter från konsol fönstret med hjälp av cmdleten [disable-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Disable-PSBreakpoint) .

```powershell
# This command disables all breakpoints in the current session.
# You can abbreviate this command as: "gbp | dbp".
Get-PSBreakpoint | Disable-PSBreakpoint
```

### <a name="enable-a-breakpoint"></a>Aktivera en Bryt punkt

Om du vill aktivera en speciell Bryt punkt högerklickar du på linjen där du vill aktivera en Bryt punkt och klickar sedan på **Aktivera Bryt punkt**. Du kan också klicka på den rad där du vill aktivera en Bryt punkt och sedan trycka på <kbd>F9</kbd> eller klicka på **Aktivera Bryt punkt**på **fel söknings** menyn. Följande skript är ett exempel på hur du kan aktivera vissa Bryt punkter från konsol fönstret med hjälp av cmdleten [Enable-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Enable-PSBreakpoint) .

```powershell
# This command enables breakpoints with breakpoint IDs 0, 1, and 5.
Enable-PSBreakpoint -Id 0, 1, 5
```

### <a name="enable-all-breakpoints"></a>Aktivera alla Bryt punkter

Om du vill aktivera alla Bryt punkter som definierats i den aktuella sessionen går du till **Felsök** -menyn och klickar på **Aktivera alla Bryt punkter**. Följande skript är ett exempel på hur du kan aktivera alla Bryt punkter från konsol fönstret med hjälp av cmdleten [Enable-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Enable-PSBreakpoint) .

```powershell
# This command enables all breakpoints in the current session.
# You can abbreviate the command by using their aliases: "gbp | ebp".
Get-PSBreakpoint | Enable-PSBreakpoint
```

## <a name="how-to-manage-a-debugging-session"></a>Så här hanterar du en felsökningssession

Innan du börjar felsöka måste du ange en eller flera Bryt punkter. Du kan inte ange en Bryt punkt om inte skriptet som du vill felsöka har sparats. Instruktioner för hur du ställer in en Bryt punkt finns i [Hantera Bryt punkter](#how-to-manage-breakpoints) eller [set-PSBreakpoint](/powershell/module/Microsoft.PowerShell.Utility/Set-PSBreakpoint).
När du har startat fel sökningen kan du inte redigera ett skript förrän du har stoppat fel sökningen. Ett skript som har en eller flera Bryt punkter sparas automatiskt innan det körs.

### <a name="to-start-debugging"></a>Starta fel sökning

Tryck på <kbd>F5</kbd> eller klicka på **Kör skript** ikonen i verktygsfältet eller på **fel söknings** menyn klickar du på **Kör/Fortsätt**. Skriptet körs tills det påträffar den första Bryt punkten. Åtgärden pausar där och markerar den rad där den pausades.

### <a name="to-continue-debugging"></a>För att fortsätta fel sökningen

Tryck på <kbd>F5</kbd> eller klicka på ikonen **Kör skript** i verktygsfältet, eller på **fel söknings** menyn, klicka på **Kör/Fortsätt** eller i konsol fönstret skriver du `C` och trycker sedan på <kbd>RETUR</kbd>. Detta gör att skriptet fortsätter att köras till nästa Bryt punkt eller till slutet av skriptet om inga ytterligare Bryt punkter påträffas.

### <a name="to-view-the-call-stack"></a>Visa anrops stacken

Anrops stacken visar den aktuella körnings platsen i skriptet. Om skriptet körs i en funktion som anropades av en annan funktion visas detta i visningen av ytterligare rader i utdata. Den nedersta raden visar det ursprungliga skriptet och den rad i vilken en funktion anropades. Nästa rad i visar funktionen och den rad i vilken en annan funktion kan ha anropats. Den översta raden visar den aktuella kontexten för den aktuella raden som Bryt punkten har angetts på.

När du är pausad kan du se den aktuella anrops stacken genom att trycka på <kbd>CTRL</kbd> + <kbd>Shift</kbd> + <kbd>D</kbd> eller, på **fel söknings** menyn, klicka på **Visa anrops stack** eller, i rutan konsol, skriva `K` och sedan trycka på <kbd>RETUR</kbd>.

### <a name="to-stop-debugging"></a>Stoppa fel sökningen

Tryck på <kbd>SKIFT</kbd> + <kbd>F5</kbd> eller på **fel** söknings menyn, klicka på **stoppa fel sökning**eller Skriv `Q` och tryck sedan på <kbd>RETUR</kbd>i konsol fönstret.

## <a name="how-to-step-over-step-into-and-step-out-while-debugging"></a>Stega över, stega och stega under fel sökning

Steging är en process för att köra en instruktion i taget. Du kan stoppa en kodrad och undersöka värdena för variabler och systemets tillstånd. I följande tabell beskrivs vanliga fel söknings uppgifter, t. ex. att gå över, integrera och Stega ut.

| Fel söknings uppgift |                                                                                                                   Beskrivning                                                                                                                    |                                                      Så här åstadkommer du det i PowerShell ISE                                                       |
| -------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Stega in**  | Kör den aktuella instruktionen och stoppar sedan nästa instruktion. Om den aktuella instruktionen är en funktion eller ett skript anrop, kommer fel söknings stegen till den funktionen eller skriptet, annars stoppas vid nästa instruktion.                      | Tryck på <kbd>F11</kbd> eller på **fel söknings** menyn, klicka på **stega i**eller Skriv `S` och tryck på <kbd>RETUR</kbd>i konsol fönstret.                 |
| **Steg över**  | Kör den aktuella instruktionen och stoppar sedan nästa instruktion. Om den aktuella instruktionen är en funktion eller ett skript anrop, kör fel söknings programmet hela funktionen eller skriptet och stannar vid nästa instruktion efter funktions anropet. | Tryck på <kbd>F10</kbd> eller på **fel söknings** menyn, klicka på **steg över**eller i konsol fönstret, Skriv `V` och tryck på <kbd>RETUR</kbd>.                 |
| **Gå ut**   | Steg ut ur den aktuella funktionen och upp en nivå om funktionen är kapslad. Om i huvud texten körs skriptet till slutet eller till nästa Bryt punkt. De överhoppade instruktionerna körs, men är inte stegvisa.                   | Tryck på <kbd>Shift</kbd> + eller på **fel söknings** menyn<kbd>,</kbd>Klicka på **Stega ut**eller Skriv `O` och tryck på <kbd>RETUR</kbd>i konsol fönstret. |
| **Fortsätt**   | Fortsätter körningen till slutet eller till nästa Bryt punkt. De överhoppade funktionerna och anropen utförs, men inte stegvisa.                                                                                                          | Tryck på <kbd>F5</kbd> eller på **fel söknings** menyn, klicka på **Kör/Fortsätt**eller i konsol fönstret, Skriv `C` och tryck på <kbd>RETUR</kbd>.               |

## <a name="how-to-display-the-values-of-variables-while-debugging"></a>Så här visar du värden för variabler under fel sökning

Du kan visa de aktuella värdena för variabler i skriptet när du går igenom koden.

### <a name="to-display-the-values-of-standard-variables"></a>Visa värden för standardvariabler

Använd någon av följande metoder:

- Hovra över variabeln i rutan skript och visa dess värde som en verktygs beskrivning.

- I konsol fönstret skriver du variabelns namn och trycker på <kbd>RETUR</kbd>.

Alla fönster i ISE är alltid i samma omfång. När du felsöker ett skript kan du därför köra de kommandon som du skriver i konsol fönstret i skript omfång. På så sätt kan du använda konsol fönstret för att hitta värden för variabler och anropa funktioner som bara definieras i skriptet.

### <a name="to-display-the-values-of-automatic-variables"></a>Visa värden för automatiska variabler

Du kan använda föregående metod för att visa värdet för nästan alla variabler medan du felsöker ett skript. Dessa metoder fungerar dock inte för följande automatiska variabler.

- `$_`

- `$Input`

- `$MyInvocation`

- `$PSBoundParameters`

- `$Args`

Om du försöker visa värdet för någon av dessa variabler får du värdet för den variabeln för i en intern pipeline som fel sökaren använder, inte värdet för variabeln i skriptet. Du kan undvika detta för några variabler (,, `$_` , `$Input` `$MyInvocation` `$PSBoundParameters` och `$Args` ) med hjälp av följande metod:

1. I skriptet tilldelar du värdet för den automatiska variabeln till en ny variabel.

1. Visa värdet för den nya variabeln, antingen genom att hovra över den nya variabeln i skript fönstret eller genom att skriva den nya variabeln i konsol fönstret.

Om du till exempel vill visa värdet för `$MyInvocation` variabeln, i skriptet, tilldelar du värdet till en ny variabel, till exempel `$scriptName` , och hovrar sedan över eller anger `$scriptName` variabeln för att visa dess värde.

```powershell
# In C:\ps-test\MyScript.ps1
$scriptName = $MyInvocation.MyCommand.Path
```

```PowerShell
# In the Console Pane:
.\MyScript.ps1
$scriptName
```

```Output
C:\ps-test\MyScript.ps1
```

## <a name="see-also"></a>Se även

[Utforska Windows PowerShell ISE](exploring-the-windows-powershell-ise.md)
