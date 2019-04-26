---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Välj objekt från en listruta
ms.assetid: 327c7cc5-21d0-4ace-b151-aa1491d1d3c2
ms.openlocfilehash: e3d52839409a2fd58fbdc924a2b92d96fbecee53
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086076"
---
# <a name="selecting-items-from-a-list-box"></a><span data-ttu-id="e872f-103">Välj objekt från en listruta</span><span class="sxs-lookup"><span data-stu-id="e872f-103">Selecting Items from a List Box</span></span>

<span data-ttu-id="e872f-104">Använda Windows PowerShell 3.0 och senare versioner för att skapa en dialogruta som användarna kan välja objekt från en listruta.</span><span class="sxs-lookup"><span data-stu-id="e872f-104">Use Windows PowerShell 3.0 and later releases to create a dialog box that lets users select items from a list box control.</span></span>

## <a name="create-a-list-box-control-and-select-items-from-it"></a><span data-ttu-id="e872f-105">Skapa en listruta och välj objekt från den</span><span class="sxs-lookup"><span data-stu-id="e872f-105">Create a list box control, and select items from it</span></span>

<span data-ttu-id="e872f-106">Kopiera och klistra in följande i Windows PowerShell ISE och spara det som ett Windows PowerShell-skript (.ps1).</span><span class="sxs-lookup"><span data-stu-id="e872f-106">Copy and then paste the following into Windows PowerShell ISE, and then save it as a Windows PowerShell script (.ps1).</span></span>

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

<span data-ttu-id="e872f-107">Skriptet börjar genom att läsa in två .NET Framework-klasser: **System.Drawing** och **System.Windows.Forms**.</span><span class="sxs-lookup"><span data-stu-id="e872f-107">The script begins by loading two .NET Framework classes: **System.Drawing** and **System.Windows.Forms**.</span></span> <span data-ttu-id="e872f-108">Du startar sedan en ny instans av klassen .NET Framework **System.Windows.Forms.Form**; som innehåller ett tomt formulär eller fönster som du kan börja lägga till kontroller.</span><span class="sxs-lookup"><span data-stu-id="e872f-108">You then start a new instance of the .NET Framework class **System.Windows.Forms.Form**; that provides a blank form or window to which you can start adding controls.</span></span>

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing
```

<span data-ttu-id="e872f-109">När du har skapat en instans av klassen Form tilldela värden till tre egenskaper i den här klassen.</span><span class="sxs-lookup"><span data-stu-id="e872f-109">After you create an instance of the Form class, assign values to three properties of this class.</span></span>

- <span data-ttu-id="e872f-110">**Text.**</span><span class="sxs-lookup"><span data-stu-id="e872f-110">**Text.**</span></span> <span data-ttu-id="e872f-111">Detta blir titeln på fönstret.</span><span class="sxs-lookup"><span data-stu-id="e872f-111">This becomes the title of the window.</span></span>

- <span data-ttu-id="e872f-112">**Storlek.**</span><span class="sxs-lookup"><span data-stu-id="e872f-112">**Size.**</span></span> <span data-ttu-id="e872f-113">Det här är storleken på formuläret i bildpunkter.</span><span class="sxs-lookup"><span data-stu-id="e872f-113">This is the size of the form, in pixels.</span></span> <span data-ttu-id="e872f-114">Det här skriptet skapar ett formulär som är 300 bildpunkter på bredden 200 bildpunkter.</span><span class="sxs-lookup"><span data-stu-id="e872f-114">The preceding script creates a form that’s 300 pixels wide by 200 pixels tall.</span></span>

- <span data-ttu-id="e872f-115">**StartingPosition.**</span><span class="sxs-lookup"><span data-stu-id="e872f-115">**StartingPosition.**</span></span> <span data-ttu-id="e872f-116">Den här valfria egenskapen anges till **CenterScreen** i föregående skript.</span><span class="sxs-lookup"><span data-stu-id="e872f-116">This optional property is set to **CenterScreen** in the preceding script.</span></span> <span data-ttu-id="e872f-117">Om du inte lägger till den här egenskapen, väljer en plats i Windows när formuläret öppnas.</span><span class="sxs-lookup"><span data-stu-id="e872f-117">If you don’t add this property, Windows selects a location when the form is opened.</span></span> <span data-ttu-id="e872f-118">Genom att ange den **StartingPosition** till **CenterScreen**, du automatiskt visar formuläret mitt på skärmen varje gång den läses in.</span><span class="sxs-lookup"><span data-stu-id="e872f-118">By setting the **StartingPosition** to **CenterScreen**, you’re automatically displaying the form in the middle of the screen each time it loads.</span></span>

```powershell
$form.Text = 'Select a Computer'
$form.Size = New-Object System.Drawing.Size(300,200)
$form.StartPosition = 'CenterScreen'
```

<span data-ttu-id="e872f-119">Skapa sedan en **OK** knappen för formuläret.</span><span class="sxs-lookup"><span data-stu-id="e872f-119">Next, create an **OK** button for your form.</span></span> <span data-ttu-id="e872f-120">Ange storlek och beteendet för den **OK** knappen.</span><span class="sxs-lookup"><span data-stu-id="e872f-120">Specify the size and behavior of the **OK** button.</span></span> <span data-ttu-id="e872f-121">I det här exemplet är knappen positionen 120 bildpunkter från formulärets övre kant och 75 bildpunkter från den vänstra kanten.</span><span class="sxs-lookup"><span data-stu-id="e872f-121">In this example, the button position is 120 pixels from the form’s top edge, and 75 pixels from the left edge.</span></span> <span data-ttu-id="e872f-122">Knappen höjden är 23 bildpunkter, medan den knapp längden är 75 bildpunkter.</span><span class="sxs-lookup"><span data-stu-id="e872f-122">The button height is 23 pixels, while the button length is 75 pixels.</span></span> <span data-ttu-id="e872f-123">Skriptet använder fördefinierade Windows Forms-typer för att fastställa knappen beteenden.</span><span class="sxs-lookup"><span data-stu-id="e872f-123">The script uses predefined Windows Forms types to determine the button behaviors.</span></span>

```powershell
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

<span data-ttu-id="e872f-124">På samma sätt kan du skapa en **Avbryt** knappen.</span><span class="sxs-lookup"><span data-stu-id="e872f-124">Similarly, you create a **Cancel** button.</span></span> <span data-ttu-id="e872f-125">Den **Avbryt** knappen är 120 bildpunkter uppifrån, men 150 pixlar från den vänstra kanten av fönstret.</span><span class="sxs-lookup"><span data-stu-id="e872f-125">The **Cancel** button is 120 pixels from the top, but 150 pixels from the left edge of the window.</span></span>

```powershell
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

<span data-ttu-id="e872f-126">Ange därefter etikettext på din fönster som beskriver den information du vill att användarna måste ange.</span><span class="sxs-lookup"><span data-stu-id="e872f-126">Next, provide label text on your window that describes the information you want users to provide.</span></span> <span data-ttu-id="e872f-127">I detta fall använder du användarna att välja en dator.</span><span class="sxs-lookup"><span data-stu-id="e872f-127">In this case, you want users to select a computer.</span></span>

```powershell
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20)
$label.Size = New-Object System.Drawing.Size(280,20)
$label.Text = 'Please select a computer:'
$form.Controls.Add($label)
```

<span data-ttu-id="e872f-128">Lägg till kontrollen (i det här fallet en listruta) som användarna kan ange den information som du har som beskrivs i din etikettext.</span><span class="sxs-lookup"><span data-stu-id="e872f-128">Add the control (in this case, a list box) that lets users provide the information you’ve described in your label text.</span></span> <span data-ttu-id="e872f-129">Det finns många andra kontroller som du kan använda förutom listrutor; Läs fler kontroller [System.Windows.Forms Namespace](https://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) på MSDN.</span><span class="sxs-lookup"><span data-stu-id="e872f-129">There are many other controls you can apply besides list boxes; for more controls, see [System.Windows.Forms Namespace](https://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) on MSDN.</span></span>

```powershell
$listBox = New-Object System.Windows.Forms.ListBox
$listBox.Location = New-Object System.Drawing.Point(10,40)
$listBox.Size = New-Object System.Drawing.Size(260,20)
$listBox.Height = 80
```

<span data-ttu-id="e872f-130">I nästa avsnitt anger du de värden som du vill ska visas för användarna.</span><span class="sxs-lookup"><span data-stu-id="e872f-130">In the next section, you specify the values you want the list box to display to users.</span></span>

> [!NOTE]
> <span data-ttu-id="e872f-131">I listrutan som skapats av det här skriptet kan endast en markering.</span><span class="sxs-lookup"><span data-stu-id="e872f-131">The list box created by this script allows only one selection.</span></span> <span data-ttu-id="e872f-132">Om du vill skapa en listruta som gör att flera val, ange ett värde för den **SelectionMode** egenskapen på samma sätt som följande: `$listBox.SelectionMode = 'MultiExtended'`.</span><span class="sxs-lookup"><span data-stu-id="e872f-132">To create a list box control that allows multiple selections, specify a value for the **SelectionMode** property, similarly to the following:  `$listBox.SelectionMode = 'MultiExtended'`.</span></span> <span data-ttu-id="e872f-133">Mer information finns i [erval listrutor](Multiple-selection-List-Boxes.md).</span><span class="sxs-lookup"><span data-stu-id="e872f-133">For more information, see [Multiple-selection List Boxes](Multiple-selection-List-Boxes.md).</span></span>

```powershell
[void] $listBox.Items.Add('atl-dc-001')
[void] $listBox.Items.Add('atl-dc-002')
[void] $listBox.Items.Add('atl-dc-003')
[void] $listBox.Items.Add('atl-dc-004')
[void] $listBox.Items.Add('atl-dc-005')
[void] $listBox.Items.Add('atl-dc-006')
[void] $listBox.Items.Add('atl-dc-007')
```

<span data-ttu-id="e872f-134">Lägga till listruta i formuläret och ber Windows att öppna formuläret ovanpå andra fönster och dialogrutor när den öppnas.</span><span class="sxs-lookup"><span data-stu-id="e872f-134">Add the list box control to your form, and instruct Windows to open the form atop other windows and dialog boxes when it’s opened.</span></span>

```powershell
$form.Controls.Add($listBox)
$form.Topmost = $true
```

<span data-ttu-id="e872f-135">Lägg till följande rad med kod för att visa formuläret i Windows.</span><span class="sxs-lookup"><span data-stu-id="e872f-135">Add the following line of code to display the form in Windows.</span></span>

```powershell
$result = $form.ShowDialog()
```

<span data-ttu-id="e872f-136">Koden i den **om** block instruerar Windows vad som ska göras med formuläret när användarna välja ett alternativ i listrutan och klicka sedan på den **OK** knapp eller genom att trycka på den **RETUR**nyckel.</span><span class="sxs-lookup"><span data-stu-id="e872f-136">Finally, the code inside the **If** block instructs Windows what to do with the form after users select an option from the list box, and then click the **OK** button or press the **Enter** key.</span></span>

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItem
    $x
}
```

## <a name="see-also"></a><span data-ttu-id="e872f-137">Se även</span><span class="sxs-lookup"><span data-stu-id="e872f-137">See Also</span></span>

- [<span data-ttu-id="e872f-138">Hej skriptdoktorn:  Varför fungerar inte dessa PowerShell-GUI-exempel?</span><span class="sxs-lookup"><span data-stu-id="e872f-138">Hey Scripting Guy:  Why don’t these PowerShell GUI examples work?</span></span>](https://go.microsoft.com/fwlink/?LinkId=506644)
- [<span data-ttu-id="e872f-139">GitHub: Dave Wyatt WinFormsExampleUpdates</span><span class="sxs-lookup"><span data-stu-id="e872f-139">GitHub: Dave Wyatt's WinFormsExampleUpdates</span></span>](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [<span data-ttu-id="e872f-140">Windows PowerShell-tips i veckan:  Välj objekt från en listruta</span><span class="sxs-lookup"><span data-stu-id="e872f-140">Windows PowerShell Tip of the Week:  Selecting Items from a List Box</span></span>](https://technet.microsoft.com/library/ff730949.aspx)