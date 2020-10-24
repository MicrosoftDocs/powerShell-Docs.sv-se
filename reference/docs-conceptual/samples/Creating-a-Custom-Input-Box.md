---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Skapa en anpassad indataruta
description: Den här artikeln visar hur du skapar en anpassad Indatatyp med hjälp av .NET Framework Forms Building-funktioner i Windows PowerShell.
ms.openlocfilehash: 18fba743b169010936d2ea83dca4e95203664fe9
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500563"
---
# <a name="creating-a-custom-input-box"></a>Skapa en anpassad indataruta

Skripta en grafisk anpassad Indatatyp med hjälp av Microsoft .NET ramverk Forms Bygg funktioner i Windows PowerShell 3,0 och senare versioner.

## <a name="create-a-custom-graphical-input-box"></a>Skapa en anpassad, grafisk inmatad ruta

Kopiera och klistra in följande i Windows PowerShell ISE och spara det sedan som ett Windows PowerShell-skript (. ps1).

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object System.Windows.Forms.Form
$form.Text = 'Data Entry Form'
$form.Size = New-Object System.Drawing.Size(300,200)
$form.StartPosition = 'CenterScreen'

$okButton = New-Object System.Windows.Forms.Button
$okButton.Location = New-Object System.Drawing.Point(75,120)
$okButton.Size = New-Object System.Drawing.Size(75,23)
$okButton.Text = 'OK'
$okButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $okButton
$form.Controls.Add($okButton)

$cancelButton = New-Object System.Windows.Forms.Button
$cancelButton.Location = New-Object System.Drawing.Point(150,120)
$cancelButton.Size = New-Object System.Drawing.Size(75,23)
$cancelButton.Text = 'Cancel'
$cancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $cancelButton
$form.Controls.Add($cancelButton)

$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20)
$label.Size = New-Object System.Drawing.Size(280,20)
$label.Text = 'Please enter the information in the space below:'
$form.Controls.Add($label)

$textBox = New-Object System.Windows.Forms.TextBox
$textBox.Location = New-Object System.Drawing.Point(10,40)
$textBox.Size = New-Object System.Drawing.Size(260,20)
$form.Controls.Add($textBox)

$form.Topmost = $true

$form.Add_Shown({$textBox.Select()})
$result = $form.ShowDialog()

if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $textBox.Text
    $x
}
```

Skriptet börjar genom att läsa in två .NET Framework klasser: **system. Drawing** och **system. Windows. Forms**. Sedan startar du en ny instans av klassen .NET Framework klass **system. Windows. Forms. form**; Det innehåller ett tomt formulär eller fönster som du kan börja lägga till kontroller i.

```powershell
$form = New-Object System.Windows.Forms.Form
```

När du har skapat en instans av formulär klassen tilldelar du värden till tre egenskaper för den här klassen.

- **Information.** Detta blir rubriken för fönstret.

- **Ändra.** Detta är storleken på formuläret, i bild punkter. Föregående skript skapar ett formulär som är 300 bild punkter brett med 200 pixlar högt.

- **Star ting position.** Den här valfria egenskapen anges till **CenterScreen** i föregående skript.
  Om du inte lägger till den här egenskapen väljer Windows en plats när formuläret öppnas. Genom att ange **Star ting position** till **CenterScreen**visas formuläret automatiskt i mitten av skärmen varje gången det läses in.

```powershell
$form.Text = 'Data Entry Form'
$form.Size = New-Object System.Drawing.Size(300,200)
$form.StartPosition = 'CenterScreen'
```

Skapa sedan en **OK** -knapp för formuläret. Ange storlek och beteende för **OK** -knappen. I det här exemplet är knapp positionen 120 bild punkter från formulärets övre kant och 75 pixlar från den vänstra kanten. Knapp höjden är 23 bild punkter, medan knapp längden är 75 bild punkter. Skriptet använder fördefinierade Windows Forms typer för att fastställa knapp beteenden.

```powershell
$okButton = New-Object System.Windows.Forms.Button
$okButton.Location = New-Object System.Drawing.Point(75,120)
$okButton.Size = New-Object System.Drawing.Size(75,23)
$okButton.Text = 'OK'
$okButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

På samma sätt skapar du en **Avbryt** -knapp. Knappen **Avbryt** är 120 bild punkter ovanifrån, men 150 pixlar från den vänstra kanten av fönstret.

```powershell
$cancelButton = New-Object System.Windows.Forms.Button
$cancelButton.Location = New-Object System.Drawing.Point(150,120)
$cancelButton.Size = New-Object System.Drawing.Size(75,23)
$cancelButton.Text = 'Cancel'
$cancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $cancelButton
$form.Controls.Add($cancelButton)
```

Ange sedan etikettext i fönstret som beskriver den information som du vill att användarna ska kunna tillhandahålla.

```powershell
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20)
$label.Size = New-Object System.Drawing.Size(280,20)
$label.Text = 'Please enter the information in the space below:'
$form.Controls.Add($label)
```

Lägg till kontrollen (i det här fallet en text ruta) som gör det möjligt för användarna att ange den information som du har beskrivet i din etikett text. Det finns många andra kontroller som du kan använda förutom text rutor. Mer kontroller finns i [namn området system. Windows. Forms](/dotnet/api/system.windows.forms) på MSDN.

```powershell
$textBox = New-Object System.Windows.Forms.TextBox
$textBox.Location = New-Object System.Drawing.Point(10,40)
$textBox.Size = New-Object System.Drawing.Size(260,20)
$form.Controls.Add($textBox)
```

Ställ in den **översta** egenskapen på **$True** för att tvinga fönstret att öppna ovanpå andra öppna fönster och dialog rutor.

```powershell
$form.Topmost = $true
```

Lägg sedan till den här kodraden för att aktivera formuläret och ange fokus till text rutan som du skapade.

```powershell
$form.Add_Shown({$textBox.Select()})
```

Lägg till följande kodrad för att visa formuläret i Windows.

```powershell
$result = $form.ShowDialog()
```

Slutligen instruerar koden inuti **IF** -block Windows vad som ska göras med formuläret när användarna har angett text i text rutan. Klicka sedan på **OK** eller tryck på **RETUR** -tangenten.

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $textBox.Text
    $x
}
```

## <a name="see-also"></a>Se även

- [GitHub: Dave Wyatt s WinFormsExampleUpdates](/previous-versions/windows/it-pro/windows-powershell-1.0/ff730941(v=technet.10))
- [Veckans Windows PowerShell-tips: skapa en anpassad indatamängds ruta](https://technet.microsoft.com/library/ff730941.aspx)
