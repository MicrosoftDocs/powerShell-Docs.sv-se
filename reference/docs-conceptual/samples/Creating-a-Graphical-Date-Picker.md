---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Skapa en grafisk datumväljare
ms.assetid: c1cb722c-41e9-4baa-be83-59b4653222e9
ms.openlocfilehash: 6dd43a3b1f4c67633ad1755de3db88eb8c6772c8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686504"
---
# <a name="creating-a-graphical-date-picker"></a>Skapa en grafisk datumväljare

Använda Windows PowerShell 3.0 och senare versioner för att skapa ett formulär med en grafisk, kalender-style-kontroll som användaren kan välja en dag i månaden.

## <a name="create-a-graphical-date-picker-control"></a>Skapa en grafisk datumväljare-kontroll

Kopiera och klistra in följande i Windows PowerShell ISE och spara det som ett Windows PowerShell-skript (.ps1).

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

Skriptet börjar genom att läsa in två .NET Framework-klasser: **System.Drawing** och **System.Windows.Forms**. Du startar sedan en ny instans av klassen .NET Framework **Windows.Forms.Form**; som innehåller ett tomt formulär eller fönster som du kan börja lägga till kontroller.

```powershell
$form = New-Object Windows.Forms.Form
```

När du har skapat en instans av klassen Form tilldela värden till tre egenskaper i den här klassen.

- **Text.** Detta blir titeln på fönstret.

- **Storlek.** Det här är storleken på formuläret i bildpunkter. Det här skriptet skapar ett formulär som är 243 bildpunkter på bredden 230 pixlar hög.

- **StartingPosition.** Den här valfria egenskapen anges till **CenterScreen** i föregående skript. Om du inte lägger till den här egenskapen, väljer en plats i Windows när formuläret öppnas. Genom att ange den **StartingPosition** till **CenterScreen**, du automatiskt visar formuläret mitt på skärmen varje gång den läses in.

```powershell
$form.Text = 'Select a Date'
$form.Size = New-Object Drawing.Size @(243,230)
$form.StartPosition = 'CenterScreen'
```

Sedan skapar och sedan lägga till en kalenderkontroll i formuläret. I det här exemplet är den aktuella dagen inte markerat eller inringade. Användarna kan välja endast en dag i kalendern i taget.

```powershell
$calendar = New-Object System.Windows.Forms.MonthCalendar
$calendar.ShowTodayCircle = $false
$calendar.MaxSelectionCount = 1
$form.Controls.Add($calendar)
```

Skapa sedan en **OK** knappen för formuläret. Ange storlek och beteendet för den **OK** knappen. I det här exemplet är knappen positionen 165 pixlar från formulärets övre kant och 38 pixlar från den vänstra kanten. Knappen höjden är 23 bildpunkter, medan den knapp längden är 75 bildpunkter. Skriptet använder fördefinierade Windows Forms-typer för att fastställa knappen beteenden.

```powershell
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(38,165)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

På samma sätt kan du skapa en **Avbryt** knappen. Den **Avbryt** knappen är 165 bildpunkter uppifrån, men 113 bildpunkter från den vänstra kanten av fönstret.

```powershell
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(113,165)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

Ange den **Topmost** egenskap **$true** att tvinga den tidsperioden för att öppna ovanpå andra fönster och dialogrutor.

```powershell
$form.Topmost = $true
```

Lägg till följande rad med kod för att visa formuläret i Windows.

```powershell
$result = $form.ShowDialog()
```

Koden i den **om** block instruerar Windows vad som ska göras med formuläret när användare väljer en dag i kalendern och klicka sedan på den **OK** knapp eller genom att trycka på den **RETUR** nyckeln. Windows PowerShell visas det valda datumet för användarna.

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

## <a name="see-also"></a>Se även

- [Hej skriptdoktorn:  Varför fungerar inte dessa PowerShell-GUI-exempel?](https://go.microsoft.com/fwlink/?LinkId=506644)
- [GitHub: Dave Wyatt WinFormsExampleUpdates](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [Windows PowerShell-tips i veckan:  Skapa en grafisk datumväljare](https://technet.microsoft.com/library/ff730942.aspx)