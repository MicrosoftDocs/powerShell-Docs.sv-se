---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Flerval listrutor
ms.assetid: f74cd5d9-da57-4802-b614-0b194a7bc8f8
ms.openlocfilehash: 122014888bc5cf93c1c709b9d534d572037f5ffe
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/08/2017
---
# <a name="multiple-selection-list-boxes"></a>Flera val listrutor
Använda Windows PowerShell 3.0 och senare versioner för att skapa en listruta med flera val i ett anpassat formulär för Windows.

## <a name="create-list-box-controls-that-allow-multiple-selections"></a>Skapa lista kontroller som gör att flera markeringar
Kopiera och klistra in följande i Windows PowerShell ISE och spara den som en Windows PowerShell-skript (.ps1).

```
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object System.Windows.Forms.Form 
$form.Text = "Data Entry Form"
$form.Size = New-Object System.Drawing.Size(300,200) 
$form.StartPosition = "CenterScreen"

$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = "OK"
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)

$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = "Cancel"
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)

$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20) 
$label.Size = New-Object System.Drawing.Size(280,20) 
$label.Text = "Please make a selection from the list below:"
$form.Controls.Add($label) 

$listBox = New-Object System.Windows.Forms.Listbox 
$listBox.Location = New-Object System.Drawing.Point(10,40) 
$listBox.Size = New-Object System.Drawing.Size(260,20) 

$listBox.SelectionMode = "MultiExtended"

[void] $listBox.Items.Add("Item 1")
[void] $listBox.Items.Add("Item 2")
[void] $listBox.Items.Add("Item 3")
[void] $listBox.Items.Add("Item 4")
[void] $listBox.Items.Add("Item 5")

$listBox.Height = 70
$form.Controls.Add($listBox) 
$form.Topmost = $True

$result = $form.ShowDialog()

if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItems
    $x
}
```

Skriptet börjar genom att läsa in två klasser i .NET Framework: **System.Drawing** och **System.Windows.Forms**. Du startar sedan en ny instans av klassen .NET Framework **System.Windows.Forms.Form**; som innehåller ett tomt formulär eller fönster som du kan börja lägga till kontroller.

```
$form = New-Object System.Windows.Forms.Form
```

När du har skapat en instans av klassen formuläret tilldela värden till tre egenskaper i den här klassen.

- **Text.** Detta är titeln på fönstret.

- **Storlek.** Detta är storleken på formuläret i bildpunkter. Det här skriptet skapar ett formulär som är 300 bildpunkter av 200 bildpunkter.

- **StartingPosition.** Den här valfria egenskapen **CenterScreen** i det här skriptet. Om du inte lägger till den här egenskapen, väljer en plats i Windows när formuläret öppnas. Genom att ange den **StartingPosition** till **CenterScreen**, du automatiskt visar formuläret på skärmen för varje gång den läses in.

```
$form.Text = "Data Entry Form"
$form.Size = New-Object System.Drawing.Size(300,200) 
$form.StartPosition = "CenterScreen"
```

Skapa sedan en **OK** knappen för formuläret. Ange storlek och hur den **OK** knappen. I det här exemplet är knappen positionen 120 bildpunkter från formulärets övre kant och 75 bildpunkter från den vänstra kanten. Knappen höjden är 23 bildpunkter när knappen är 75 bildpunkter. Skriptet använder fördefinierade Windows Forms-typer för att fastställa knappen beteenden.

```
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Size(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = "OK"
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

På liknande sätt kan du skapa en **Avbryt** knappen. Den **Avbryt** knappen är 120 bildpunkter uppifrån, men 150 bildpunkter från vänster i fönstret.

```
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = "Cancel"
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

Ange sedan etikettexten på fönstret som beskriver den information som du vill att användarna ska ange.

```
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20) 
$label.Size = New-Object System.Drawing.Size(280,20) 
$label.Text = "Please make a selection from the list below:"
$form.Controls.Add($label)
```

Lägg till kontrollen (i det här fallet en listruta) som gör att användarna anger du den information som du har beskrivs i din etikettext. Det finns många andra kontroller som du kan använda förutom textrutor; fler kontroller finns [System.Windows.Forms Namespace](http://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) på MSDN.

```
$listBox = New-Object System.Windows.Forms.Listbox 
$listBox.Location = New-Object System.Drawing.Point(10,40) 
$listBox.Size = New-Object System.Drawing.Size(260,20)
```


Här är hur du anger att du vill tillåta användare att välja flera värden i listan.

```
$listBox.SelectionMode = "MultiExtended"
```

I nästa avsnitt anger du de värden du vill ska visas för användarna.

```
[void] $listBox.Items.Add("Item 1")
[void] $listBox.Items.Add("Item 2")
[void] $listBox.Items.Add("Item 3")
[void] $listBox.Items.Add("Item 4")
[void] $listBox.Items.Add("Item 5")
```

Ange maximala höjd på listruta.

```
$listBox.Height = 70
```

Lägga till listruta i formuläret och instruerar Windows för att öppna formuläret på andra fönster och dialogrutor när den öppnas.

```
$form.Controls.Add($listBox) 
$form.Topmost = $True
```

Lägg till följande kod för att visa formulär i Windows.

```
$result = $form.ShowDialog()
```

Slutligen kod inuti den **om** block instruerar Windows vad ska göras med formuläret när användare väljer ett eller flera alternativ i listrutan och klicka sedan på den **OK** knappen eller tryck på den **RETUR**  nyckel.

```
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItems
    $x
}
```

## <a name="see-also"></a>Se även
- [Hey Scripting Guy: Varför exemplen PowerShell-Gränssnittet fungerar inte?](http://go.microsoft.com/fwlink/?LinkId=506644)
- [GitHub: Dave Wyatt WinFormsExampleUpdates](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [Windows PowerShell-tips i veckan: flera Select-listan rutor- och mycket mer!](http://technet.microsoft.com/library/ff730950.aspx)

