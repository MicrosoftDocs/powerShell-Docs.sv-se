---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Välj objekt från en listruta
ms.assetid: 327c7cc5-21d0-4ace-b151-aa1491d1d3c2
ms.openlocfilehash: e3d52839409a2fd58fbdc924a2b92d96fbecee53
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688499"
---
# <a name="selecting-items-from-a-list-box"></a>Välj objekt från en listruta

Använda Windows PowerShell 3.0 och senare versioner för att skapa en dialogruta som användarna kan välja objekt från en listruta.

## <a name="create-a-list-box-control-and-select-items-from-it"></a>Skapa en listruta och välj objekt från den

Kopiera och klistra in följande i Windows PowerShell ISE och spara det som ett Windows PowerShell-skript (.ps1).

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object System.Windows.Forms.Form
$form.Text = 'Select a Computer'
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
$label.Text = 'Please select a computer:'
$form.Controls.Add($label)

$listBox = New-Object System.Windows.Forms.ListBox
$listBox.Location = New-Object System.Drawing.Point(10,40)
$listBox.Size = New-Object System.Drawing.Size(260,20)
$listBox.Height = 80

[void] $listBox.Items.Add('atl-dc-001')
[void] $listBox.Items.Add('atl-dc-002')
[void] $listBox.Items.Add('atl-dc-003')
[void] $listBox.Items.Add('atl-dc-004')
[void] $listBox.Items.Add('atl-dc-005')
[void] $listBox.Items.Add('atl-dc-006')
[void] $listBox.Items.Add('atl-dc-007')

$form.Controls.Add($listBox)

$form.Topmost = $true

$result = $form.ShowDialog()

if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItem
    $x
}
```

Skriptet börjar genom att läsa in två .NET Framework-klasser: **System.Drawing** och **System.Windows.Forms**. Du startar sedan en ny instans av klassen .NET Framework **System.Windows.Forms.Form**; som innehåller ett tomt formulär eller fönster som du kan börja lägga till kontroller.

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing
```

När du har skapat en instans av klassen Form tilldela värden till tre egenskaper i den här klassen.

- **Text.** Detta blir titeln på fönstret.

- **Storlek.** Det här är storleken på formuläret i bildpunkter. Det här skriptet skapar ett formulär som är 300 bildpunkter på bredden 200 bildpunkter.

- **StartingPosition.** Den här valfria egenskapen anges till **CenterScreen** i föregående skript. Om du inte lägger till den här egenskapen, väljer en plats i Windows när formuläret öppnas. Genom att ange den **StartingPosition** till **CenterScreen**, du automatiskt visar formuläret mitt på skärmen varje gång den läses in.

```powershell
$form.Text = 'Select a Computer'
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

Ange därefter etikettext på din fönster som beskriver den information du vill att användarna måste ange. I detta fall använder du användarna att välja en dator.

```powershell
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20)
$label.Size = New-Object System.Drawing.Size(280,20)
$label.Text = 'Please select a computer:'
$form.Controls.Add($label)
```

Lägg till kontrollen (i det här fallet en listruta) som användarna kan ange den information som du har som beskrivs i din etikettext. Det finns många andra kontroller som du kan använda förutom listrutor; Läs fler kontroller [System.Windows.Forms Namespace](https://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) på MSDN.

```powershell
$listBox = New-Object System.Windows.Forms.ListBox
$listBox.Location = New-Object System.Drawing.Point(10,40)
$listBox.Size = New-Object System.Drawing.Size(260,20)
$listBox.Height = 80
```

I nästa avsnitt anger du de värden som du vill ska visas för användarna.

> [!NOTE]
> I listrutan som skapats av det här skriptet kan endast en markering. Om du vill skapa en listruta som gör att flera val, ange ett värde för den **SelectionMode** egenskapen på samma sätt som följande: `$listBox.SelectionMode = 'MultiExtended'`. Mer information finns i [erval listrutor](Multiple-selection-List-Boxes.md).

```powershell
[void] $listBox.Items.Add('atl-dc-001')
[void] $listBox.Items.Add('atl-dc-002')
[void] $listBox.Items.Add('atl-dc-003')
[void] $listBox.Items.Add('atl-dc-004')
[void] $listBox.Items.Add('atl-dc-005')
[void] $listBox.Items.Add('atl-dc-006')
[void] $listBox.Items.Add('atl-dc-007')
```

Lägga till listruta i formuläret och ber Windows att öppna formuläret ovanpå andra fönster och dialogrutor när den öppnas.

```powershell
$form.Controls.Add($listBox)
$form.Topmost = $true
```

Lägg till följande rad med kod för att visa formuläret i Windows.

```powershell
$result = $form.ShowDialog()
```

Koden i den **om** block instruerar Windows vad som ska göras med formuläret när användarna välja ett alternativ i listrutan och klicka sedan på den **OK** knapp eller genom att trycka på den **RETUR**nyckel.

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItem
    $x
}
```

## <a name="see-also"></a>Se även

- [Hej skriptdoktorn:  Varför fungerar inte dessa PowerShell-GUI-exempel?](https://go.microsoft.com/fwlink/?LinkId=506644)
- [GitHub: Dave Wyatt WinFormsExampleUpdates](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [Windows PowerShell-tips i veckan:  Välj objekt från en listruta](https://technet.microsoft.com/library/ff730949.aspx)