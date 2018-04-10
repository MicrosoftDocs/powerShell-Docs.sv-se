---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Skapa en grafisk datumväljare
ms.assetid: c1cb722c-41e9-4baa-be83-59b4653222e9
ms.openlocfilehash: 3727c90c314a6fc1b3a338ec60e44259f153d954
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="creating-a-graphical-date-picker"></a>Skapa en grafisk datumväljare

Använda Windows PowerShell 3.0 och senare versioner för att skapa ett formulär med en grafisk, kalender-format-kontroll som användarna kan välja en dag i månaden.

## <a name="create-a-graphical-date-picker-control"></a>Skapa en grafisk datum-väljarkontrollen

Kopiera och klistra in följande i Windows PowerShell ISE och spara den som en Windows PowerShell-skript (.ps1).

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object Windows.Forms.Form

$form.Text = 'Select a Date'
$form.Size = New-Object Drawing.Size @(243,230)
$form.StartPosition = 'CenterScreen'

$calendar = New-Object System.Windows.Forms.MonthCalendar
$calendar.ShowTodayCircle = $false
$calendar.MaxSelectionCount = 1
$form.Controls.Add($calendar)

$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(38,165)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)

$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(113,165)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)

$form.Topmost = $true

$result = $form.ShowDialog()

if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

Skriptet börjar genom att läsa in två klasser i .NET Framework: **System.Drawing** och **System.Windows.Forms**. Du startar sedan en ny instans av klassen .NET Framework **Windows.Forms.Form**; som innehåller ett tomt formulär eller fönster som du kan börja lägga till kontroller.

```powershell
$form = New-Object Windows.Forms.Form
```

När du har skapat en instans av klassen formuläret tilldela värden till tre egenskaper i den här klassen.

- **Text.** Detta är titeln på fönstret.

- **Storlek.** Detta är storleken på formuläret i bildpunkter. Det här skriptet skapar ett formulär som är 243 pixlar brett och 230 bildpunkter.

- **StartingPosition.** Den här valfria egenskapen **CenterScreen** i det här skriptet. Om du inte lägger till den här egenskapen, väljer en plats i Windows när formuläret öppnas. Genom att ange den **StartingPosition** till **CenterScreen**, du automatiskt visar formuläret på skärmen för varje gång den läses in.

```powershell
$form.Text = 'Select a Date'
$form.Size = New-Object Drawing.Size @(243,230)
$form.StartPosition = 'CenterScreen'
```

Sedan skapa och Lägg sedan till en kalenderkontroll i formuläret. I det här exemplet är den aktuella dagen inte markerad eller inringad. Användare kan välja endast en dag i kalendern i taget.

```powershell
$calendar = New-Object System.Windows.Forms.MonthCalendar
$calendar.ShowTodayCircle = $false
$calendar.MaxSelectionCount = 1
$form.Controls.Add($calendar)
```

Skapa sedan en **OK** knappen för formuläret. Ange storlek och hur den **OK** knappen. I det här exemplet är knappen positionen 165 pixlar från formulärets övre kant och 38 pixlar från den vänstra kanten. Knappen höjden är 23 bildpunkter när knappen är 75 bildpunkter. Skriptet använder fördefinierade Windows Forms-typer för att fastställa knappen beteenden.

```powershell
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(38,165)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

På liknande sätt kan du skapa en **Avbryt** knappen. Den **Avbryt** knappen är 165 bildpunkter uppifrån, men 113 bildpunkter från vänster i fönstret.

```powershell
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(113,165)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

Ange den **Topmost** egenskapen **$true** att tvinga fönstret för att öppna ovanpå andra fönster och dialogrutor.

```powershell
$form.Topmost = $true
```

Lägg till följande kod för att visa formulär i Windows.

```powershell
$result = $form.ShowDialog()
```

Slutligen kod inuti den **om** block instruerar Windows vad ska göras med formuläret när användare väljer en dag i kalendern och klicka sedan på den **OK** knappen eller tryck på den **RETUR** nyckel. Windows PowerShell visar det valda datumet för användarna.

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

## <a name="see-also"></a>Se även

- [Hey Scripting Guy: Varför exemplen PowerShell-Gränssnittet fungerar inte?](http://go.microsoft.com/fwlink/?LinkId=506644)
- [GitHub: Dave Wyatt WinFormsExampleUpdates](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [Windows PowerShell-tips i veckan: skapar ett grafiskt datum objektväljare](http://technet.microsoft.com/library/ff730942.aspx)