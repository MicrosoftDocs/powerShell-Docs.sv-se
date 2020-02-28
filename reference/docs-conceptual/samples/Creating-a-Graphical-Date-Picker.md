---
ms.date: 06/05/2017
keywords: PowerShell, cmdlet
title: Skapa en grafisk datumväljare
ms.openlocfilehash: b748e301b24ed643488079b547e2da1a5a7a6551
ms.sourcegitcommit: 0a3f9945d52e963e9cba2538ffb33e42156e1395
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/27/2020
ms.locfileid: "77706145"
---
# <a name="creating-a-graphical-date-picker"></a>Skapa en grafisk datumväljare

Använd Windows PowerShell 3,0 och senare versioner för att skapa ett formulär med en grafisk, kalender typ kontroll som låter användarna välja en dag i månaden.

## <a name="create-a-graphical-date-picker-control"></a>Skapa en grafisk kontroll för datum väljare

Kopiera och klistra in följande i Windows PowerShell ISE och spara det sedan som ett Windows PowerShell-skript (. ps1).

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object Windows.Forms.Form -Property @{
    StartPosition = [Windows.Forms.FormStartPosition]::CenterScreen
    Size          = New-Object Drawing.Size 243, 230
    Text          = 'Select a Date'
    Topmost       = $true
}

$calendar = New-Object Windows.Forms.MonthCalendar -Property @{
    ShowTodayCircle   = $false
    MaxSelectionCount = 1
}
$form.Controls.Add($calendar)

$okButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 38, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'OK'
    DialogResult = [Windows.Forms.DialogResult]::OK
}
$form.AcceptButton = $okButton
$form.Controls.Add($okButton)

$cancelButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 113, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'Cancel'
    DialogResult = [Windows.Forms.DialogResult]::Cancel
}
$form.CancelButton = $cancelButton
$form.Controls.Add($cancelButton)

$result = $form.ShowDialog()

if ($result -eq [Windows.Forms.DialogResult]::OK) {
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

Skriptet börjar genom att läsa in två .NET Framework klasser: **system. Drawing** och **system. Windows. Forms**. Sedan startar du en ny instans av klassen **Windows. Forms. Forms**i .NET Framework. Det innehåller ett tomt formulär eller fönster som du kan börja lägga till kontroller i.

```powershell
$form = New-Object Windows.Forms.Form -Property @{
    StartPosition = [Windows.Forms.FormStartPosition]::CenterScreen
    Size          = New-Object Drawing.Size 243, 230
    Text          = 'Select a Date'
    Topmost       = $true
}
```

I det här exemplet tilldelas värden till fyra egenskaper för den här klassen med **egenskapen Property** och hash.

1. **Start position**: om du inte lägger till den här egenskapen väljer Windows en plats när formuläret öppnas. Genom att ange den här egenskapen som **CenterScreen**visas formuläret automatiskt i mitten av skärmen varje gången det läses in.

2. **Storlek**: det här är storleken på formuläret, i bild punkter.
   Föregående skript skapar ett formulär som är 243 bild punkter brett med 230 pixlar högt.

3. **Text**: detta blir rubriken för fönstret.

4. **Översta**: genom att ange den här egenskapen till `$true`, kan du tvinga fönstret att öppna ovanpå andra öppna fönster och dialog rutor.

Skapa sedan och Lägg till en kalender kontroll i formuläret.
I det här exemplet är den aktuella dagen inte markerad eller inringad.
Användarna kan bara välja en dag i kalendern i taget.

```powershell
$calendar = New-Object Windows.Forms.MonthCalendar -Property @{
    ShowTodayCircle   = $false
    MaxSelectionCount = 1
}
$form.Controls.Add($calendar)
```

Skapa sedan en **OK** -knapp för formuläret. Ange storlek och beteende för **OK** -knappen. I det här exemplet är knapp positionen 165 bild punkter från formulärets övre kant och 38 pixlar från den vänstra kanten. Knapp höjden är 23 bild punkter, medan knapp längden är 75 bild punkter. Skriptet använder fördefinierade Windows Forms typer för att fastställa knapp beteenden.

```powershell
$okButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 38, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'OK'
    DialogResult = [Windows.Forms.DialogResult]::OK
}
$form.AcceptButton = $okButton
$form.Controls.Add($okButton)
```

På samma sätt skapar du en **Avbryt** -knapp.
Knappen **Avbryt** är 165 bild punkter ovanifrån, men 113 pixlar från den vänstra kanten av fönstret.

```powershell
$cancelButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 113, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'Cancel'
    DialogResult = [Windows.Forms.DialogResult]::Cancel
}
$form.CancelButton = $cancelButton
$form.Controls.Add($cancelButton)
```

Lägg till följande kodrad för att visa formuläret i Windows.

```powershell
$result = $form.ShowDialog()
```

Slutligen instruerar koden inuti `if`-blocket Windows vad som ska göras med formuläret när användarna har valt en dag i kalendern. Klicka sedan på **OK** eller tryck på **RETUR** -tangenten. Windows PowerShell visar det valda datumet för användarna.

```powershell
if ($result -eq [Windows.Forms.DialogResult]::OK) {
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

## <a name="see-also"></a>Se även

- [GitHub: Dave Wyatt s WinFormsExampleUpdates](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [Veckans Windows PowerShell-tips: skapa en grafisk datum väljare](/previous-versions/windows/it-pro/windows-powershell-1.0/ff730942(v=technet.10))
