---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Skapa en anpassad indataruta
ms.assetid: 0b12e56c-299f-40ee-afbf-d30d23ed2565
ms.openlocfilehash: 2d04ad6df65cdb4ff13d136dea47bbba6a01f3a2
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404703"
---
# <a name="creating-a-custom-input-box"></a>Skapa en anpassad indataruta

Skript en grafisk anpassad indataruta med hjälp av Microsoft .NET Framework formuläret för att skapa funktioner i Windows PowerShell 3.0 och senare versioner.

## <a name="create-a-custom-graphical-input-box"></a>Skapa en anpassad, grafisk indataruta

Kopiera och klistra in följande i Windows PowerShell ISE och spara det som ett Windows PowerShell-skript (.ps1).

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object System.Windows.Forms.Form
$form.Text = 'Data Entry Form'
$form.Size = New-Object System.Drawing.Size(300,200)
$form.StartPosition = 'CenterScreen'

$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)

$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)

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

Skriptet börjar genom att läsa in två .NET Framework-klasser: **System.Drawing** och **System.Windows.Forms**. Du startar sedan en ny instans av klassen .NET Framework **System.Windows.Forms.Form**; som innehåller ett tomt formulär eller fönster som du kan börja lägga till kontroller.

```powershell
$form = New-Object System.Windows.Forms.Form
```

När du har skapat en instans av klassen Form tilldela värden till tre egenskaper i den här klassen.

- **Text.** Detta blir titeln på fönstret.

- **Storlek.** Det här är storleken på formuläret i bildpunkter. Det här skriptet skapar ett formulär som är 300 bildpunkter på bredden 200 bildpunkter.

- **StartingPosition.** Den här valfria egenskapen anges till **CenterScreen** i föregående skript. Om du inte lägger till den här egenskapen, väljer en plats i Windows när formuläret öppnas. Genom att ange den **StartingPosition** till **CenterScreen**, du automatiskt visar formuläret mitt på skärmen varje gång den läses in.

```powershell
$form.Text = 'Data Entry Form'
$form.Size = New-Object System.Drawing.Size(300,200)
$form.StartPosition = 'CenterScreen'
```

Skapa sedan en **OK** knappen för formuläret. Ange storlek och beteendet för den **OK** knappen. I det här exemplet är knappen positionen 120 bildpunkter från formulärets övre kant och 75 bildpunkter från den vänstra kanten. Knappen höjden är 23 bildpunkter, medan den knapp längden är 75 bildpunkter. Skriptet använder fördefinierade Windows Forms-typer för att fastställa knappen beteenden.

```powershell
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

På samma sätt kan du skapa en **Avbryt** knappen. Den **Avbryt** knappen är 120 bildpunkter uppifrån, men 150 pixlar från den vänstra kanten av fönstret.

```powershell
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

Ange därefter etikettext på din fönster som beskriver den information du vill att användarna måste ange.

```powershell
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20)
$label.Size = New-Object System.Drawing.Size(280,20)
$label.Text = 'Please enter the information in the space below:'
$form.Controls.Add($label)
```

Lägg till kontrollen (i det här fallet en textruta) som användarna kan ange den information som du har som beskrivs i din etikettext. Det finns många andra kontroller som du kan använda förutom textrutor; Läs fler kontroller [System.Windows.Forms Namespace](https://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) på MSDN.

```powershell
$textBox = New-Object System.Windows.Forms.TextBox
$textBox.Location = New-Object System.Drawing.Point(10,40)
$textBox.Size = New-Object System.Drawing.Size(260,20)
$form.Controls.Add($textBox)
```

Ange den **Topmost** egenskap **$true** att tvinga den tidsperioden för att öppna ovanpå andra fönster och dialogrutor.

```powershell
$form.Topmost = $true
```

Sedan lägger du till den här raden med kod för att aktivera formuläret och ange att fokusera på textrutan som du skapade.

```powershell
$form.Add_Shown({$textBox.Select()})
```

Lägg till följande rad med kod för att visa formuläret i Windows.

```powershell
$result = $form.ShowDialog()
```

Koden i den **om** block instruerar Windows vad som ska göras med formuläret när användare ange text i textrutan och klicka sedan på den **OK** knapp eller genom att trycka på den **RETUR** nyckeln.

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $textBox.Text
    $x
}
```

## <a name="see-also"></a>Se även

- [Hej skriptdoktorn:  Varför fungerar inte dessa PowerShell-GUI-exempel?](https://go.microsoft.com/fwlink/?LinkId=506644)
- [GitHub: Dave Wyatt WinFormsExampleUpdates](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [Windows PowerShell-tips i veckan:  Skapa en anpassad indataruta](https://technet.microsoft.com/library/ff730941.aspx)