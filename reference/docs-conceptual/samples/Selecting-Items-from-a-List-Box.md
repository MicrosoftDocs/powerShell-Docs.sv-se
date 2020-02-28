---
ms.date: 06/05/2017
keywords: PowerShell, cmdlet
title: Välj objekt från en listruta
ms.openlocfilehash: 048bccd403e01e2290a8930a0faba30d4c7caa73
ms.sourcegitcommit: 0a3f9945d52e963e9cba2538ffb33e42156e1395
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/27/2020
ms.locfileid: "77706180"
---
# <a name="selecting-items-from-a-list-box"></a>Välj objekt från en listruta

Använd Windows PowerShell 3,0 och senare versioner för att skapa en dialog ruta där användarna kan välja objekt från en List Rute kontroll.

## <a name="create-a-list-box-control-and-select-items-from-it"></a>Skapa en List Rute kontroll och välj objekt från den

Kopiera och klistra in följande i Windows PowerShell ISE och spara det sedan som ett Windows PowerShell-skript (. ps1).

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object System.Windows.Forms.Form
$form.Text = 'Select a Computer'
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

Skriptet börjar genom att läsa in två .NET Framework klasser: **system. Drawing** och **system. Windows. Forms**. Sedan startar du en ny instans av klassen .NET Framework klass **system. Windows. Forms. form**; Det innehåller ett tomt formulär eller fönster som du kan börja lägga till kontroller i.

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing
```

När du har skapat en instans av formulär klassen tilldelar du värden till tre egenskaper för den här klassen.

- **Information.** Detta blir rubriken för fönstret.

- **Ändra.** Detta är storleken på formuläret, i bild punkter. Föregående skript skapar ett formulär som är 300 bild punkter brett med 200 pixlar högt.

- **Star ting position.** Den här valfria egenskapen anges till **CenterScreen** i föregående skript.
  Om du inte lägger till den här egenskapen väljer Windows en plats när formuläret öppnas. Genom att ange **Star ting position** till **CenterScreen**visas formuläret automatiskt i mitten av skärmen varje gången det läses in.

```powershell
$form.Text = 'Select a Computer'
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
$form.AcceptButton = $okButton
$form.Controls.Add($okButton)
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

Ange sedan etikettext i fönstret som beskriver den information som du vill att användarna ska kunna tillhandahålla. I det här fallet vill du att användarna ska välja en dator.

```powershell
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20)
$label.Size = New-Object System.Drawing.Size(280,20)
$label.Text = 'Please select a computer:'
$form.Controls.Add($label)
```

Lägg till kontrollen (i det här fallet en listruta) som gör det möjligt för användarna att ange den information som du har beskrivet i din etikett text. Det finns många andra kontroller som du kan använda förutom List rutor. Mer kontroller finns i [namn området system. Windows. Forms](/dotnet/api/system.windows.forms) på MSDN.

```powershell
$listBox = New-Object System.Windows.Forms.ListBox
$listBox.Location = New-Object System.Drawing.Point(10,40)
$listBox.Size = New-Object System.Drawing.Size(260,20)
$listBox.Height = 80
```

I nästa avsnitt anger du de värden som du vill att List rutan ska visa för användarna.

> [!NOTE]
> List rutan som skapats av det här skriptet tillåter endast ett val. Om du vill skapa en List Rute kontroll som tillåter flera val anger du ett värde för egenskapen **SelectionMode** , på samma sätt som följande: `$listBox.SelectionMode = 'MultiExtended'`. Mer information finns i [list rutor med flera val](Multiple-selection-List-Boxes.md).

```powershell
[void] $listBox.Items.Add('atl-dc-001')
[void] $listBox.Items.Add('atl-dc-002')
[void] $listBox.Items.Add('atl-dc-003')
[void] $listBox.Items.Add('atl-dc-004')
[void] $listBox.Items.Add('atl-dc-005')
[void] $listBox.Items.Add('atl-dc-006')
[void] $listBox.Items.Add('atl-dc-007')
```

Lägg till List Rute kontrollen i formuläret och instruera Windows att öppna formuläret ovanpå andra fönster och dialog rutor när den öppnas.

```powershell
$form.Controls.Add($listBox)
$form.Topmost = $true
```

Lägg till följande kodrad för att visa formuläret i Windows.

```powershell
$result = $form.ShowDialog()
```

Slutligen instruerar koden inuti **IF** -block Windows vad som ska göras med formuläret när användarna har valt ett alternativ i list rutan. Klicka sedan på **OK** eller tryck på **RETUR** -tangenten.

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItem
    $x
}
```

## <a name="see-also"></a>Se även

- [GitHub: Dave Wyatt s WinFormsExampleUpdates](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [Veckans Windows PowerShell-tips: välja objekt i en listruta](/previous-versions/windows/it-pro/windows-powershell-1.0/ff730949(v=technet.10))
