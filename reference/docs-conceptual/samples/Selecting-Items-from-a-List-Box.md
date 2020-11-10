---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Välj objekt från en listruta
description: Den här artikeln visar hur du skapar en List Rute kontroll med hjälp av .NET Framework Forms Building-funktioner i Windows PowerShell.
ms.openlocfilehash: d6f881f0b92f294da105ae7df5e25e8c20ce5094
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94391246"
---
# <a name="selecting-items-from-a-list-box"></a><span data-ttu-id="05cad-104">Välj objekt från en listruta</span><span class="sxs-lookup"><span data-stu-id="05cad-104">Selecting Items from a List Box</span></span>

<span data-ttu-id="05cad-105">Använd Windows PowerShell 3,0 och senare versioner för att skapa en dialog ruta där användarna kan välja objekt från en List Rute kontroll.</span><span class="sxs-lookup"><span data-stu-id="05cad-105">Use Windows PowerShell 3.0 and later releases to create a dialog box that lets users select items from a list box control.</span></span>

## <a name="create-a-list-box-control-and-select-items-from-it"></a><span data-ttu-id="05cad-106">Skapa en List Rute kontroll och välj objekt från den</span><span class="sxs-lookup"><span data-stu-id="05cad-106">Create a list box control, and select items from it</span></span>

<span data-ttu-id="05cad-107">Kopiera och klistra in följande i Windows PowerShell ISE och spara det sedan som ett Windows PowerShell-skript (. ps1).</span><span class="sxs-lookup"><span data-stu-id="05cad-107">Copy and then paste the following into Windows PowerShell ISE, and then save it as a Windows PowerShell script (.ps1).</span></span>

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

<span data-ttu-id="05cad-108">Skriptet börjar genom att läsa in två .NET Framework klasser: **system. Drawing** och **system. Windows. Forms**.</span><span class="sxs-lookup"><span data-stu-id="05cad-108">The script begins by loading two .NET Framework classes: **System.Drawing** and **System.Windows.Forms**.</span></span> <span data-ttu-id="05cad-109">Sedan startar du en ny instans av klassen .NET Framework klass **system. Windows. Forms. form** ; Det innehåller ett tomt formulär eller fönster som du kan börja lägga till kontroller i.</span><span class="sxs-lookup"><span data-stu-id="05cad-109">You then start a new instance of the .NET Framework class **System.Windows.Forms.Form** ; that provides a blank form or window to which you can start adding controls.</span></span>

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing
```

<span data-ttu-id="05cad-110">När du har skapat en instans av formulär klassen tilldelar du värden till tre egenskaper för den här klassen.</span><span class="sxs-lookup"><span data-stu-id="05cad-110">After you create an instance of the Form class, assign values to three properties of this class.</span></span>

- <span data-ttu-id="05cad-111">**Information.**</span><span class="sxs-lookup"><span data-stu-id="05cad-111">**Text.**</span></span> <span data-ttu-id="05cad-112">Detta blir rubriken för fönstret.</span><span class="sxs-lookup"><span data-stu-id="05cad-112">This becomes the title of the window.</span></span>

- <span data-ttu-id="05cad-113">**Ändra.**</span><span class="sxs-lookup"><span data-stu-id="05cad-113">**Size.**</span></span> <span data-ttu-id="05cad-114">Detta är storleken på formuläret, i bild punkter.</span><span class="sxs-lookup"><span data-stu-id="05cad-114">This is the size of the form, in pixels.</span></span> <span data-ttu-id="05cad-115">Föregående skript skapar ett formulär som är 300 bild punkter brett med 200 pixlar högt.</span><span class="sxs-lookup"><span data-stu-id="05cad-115">The preceding script creates a form that's 300 pixels wide by 200 pixels tall.</span></span>

- <span data-ttu-id="05cad-116">**Star ting position.**</span><span class="sxs-lookup"><span data-stu-id="05cad-116">**StartingPosition.**</span></span> <span data-ttu-id="05cad-117">Den här valfria egenskapen anges till **CenterScreen** i föregående skript.</span><span class="sxs-lookup"><span data-stu-id="05cad-117">This optional property is set to **CenterScreen** in the preceding script.</span></span>
  <span data-ttu-id="05cad-118">Om du inte lägger till den här egenskapen väljer Windows en plats när formuläret öppnas.</span><span class="sxs-lookup"><span data-stu-id="05cad-118">If you don't add this property, Windows selects a location when the form is opened.</span></span> <span data-ttu-id="05cad-119">Genom att ange **Star ting position** till **CenterScreen** visas formuläret automatiskt i mitten av skärmen varje gången det läses in.</span><span class="sxs-lookup"><span data-stu-id="05cad-119">By setting the **StartingPosition** to **CenterScreen** , you're automatically displaying the form in the middle of the screen each time it loads.</span></span>

```powershell
$form.Text = 'Select a Computer'
$form.Size = New-Object System.Drawing.Size(300,200)
$form.StartPosition = 'CenterScreen'
```

<span data-ttu-id="05cad-120">Skapa sedan en **OK** -knapp för formuläret.</span><span class="sxs-lookup"><span data-stu-id="05cad-120">Next, create an **OK** button for your form.</span></span> <span data-ttu-id="05cad-121">Ange storlek och beteende för **OK** -knappen.</span><span class="sxs-lookup"><span data-stu-id="05cad-121">Specify the size and behavior of the **OK** button.</span></span> <span data-ttu-id="05cad-122">I det här exemplet är knapp positionen 120 bild punkter från formulärets övre kant och 75 pixlar från den vänstra kanten.</span><span class="sxs-lookup"><span data-stu-id="05cad-122">In this example, the button position is 120 pixels from the form's top edge, and 75 pixels from the left edge.</span></span> <span data-ttu-id="05cad-123">Knapp höjden är 23 bild punkter, medan knapp längden är 75 bild punkter.</span><span class="sxs-lookup"><span data-stu-id="05cad-123">The button height is 23 pixels, while the button length is 75 pixels.</span></span> <span data-ttu-id="05cad-124">Skriptet använder fördefinierade Windows Forms typer för att fastställa knapp beteenden.</span><span class="sxs-lookup"><span data-stu-id="05cad-124">The script uses predefined Windows Forms types to determine the button behaviors.</span></span>

```powershell
$okButton = New-Object System.Windows.Forms.Button
$okButton.Location = New-Object System.Drawing.Point(75,120)
$okButton.Size = New-Object System.Drawing.Size(75,23)
$okButton.Text = 'OK'
$okButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $okButton
$form.Controls.Add($okButton)
```

<span data-ttu-id="05cad-125">På samma sätt skapar du en **Avbryt** -knapp.</span><span class="sxs-lookup"><span data-stu-id="05cad-125">Similarly, you create a **Cancel** button.</span></span> <span data-ttu-id="05cad-126">Knappen **Avbryt** är 120 bild punkter ovanifrån, men 150 pixlar från den vänstra kanten av fönstret.</span><span class="sxs-lookup"><span data-stu-id="05cad-126">The **Cancel** button is 120 pixels from the top, but 150 pixels from the left edge of the window.</span></span>

```powershell
$cancelButton = New-Object System.Windows.Forms.Button
$cancelButton.Location = New-Object System.Drawing.Point(150,120)
$cancelButton.Size = New-Object System.Drawing.Size(75,23)
$cancelButton.Text = 'Cancel'
$cancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $cancelButton
$form.Controls.Add($cancelButton)
```

<span data-ttu-id="05cad-127">Ange sedan etikettext i fönstret som beskriver den information som du vill att användarna ska kunna tillhandahålla.</span><span class="sxs-lookup"><span data-stu-id="05cad-127">Next, provide label text on your window that describes the information you want users to provide.</span></span> <span data-ttu-id="05cad-128">I det här fallet vill du att användarna ska välja en dator.</span><span class="sxs-lookup"><span data-stu-id="05cad-128">In this case, you want users to select a computer.</span></span>

```powershell
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20)
$label.Size = New-Object System.Drawing.Size(280,20)
$label.Text = 'Please select a computer:'
$form.Controls.Add($label)
```

<span data-ttu-id="05cad-129">Lägg till kontrollen (i det här fallet en listruta) som gör det möjligt för användarna att ange den information som du har beskrivet i din etikett text.</span><span class="sxs-lookup"><span data-stu-id="05cad-129">Add the control (in this case, a list box) that lets users provide the information you've described in your label text.</span></span> <span data-ttu-id="05cad-130">Det finns många andra kontroller som du kan använda förutom List rutor. Mer kontroller finns i [namn området system. Windows. Forms](/dotnet/api/system.windows.forms).</span><span class="sxs-lookup"><span data-stu-id="05cad-130">There are many other controls you can apply besides list boxes; for more controls, see [System.Windows.Forms Namespace](/dotnet/api/system.windows.forms).</span></span>

```powershell
$listBox = New-Object System.Windows.Forms.ListBox
$listBox.Location = New-Object System.Drawing.Point(10,40)
$listBox.Size = New-Object System.Drawing.Size(260,20)
$listBox.Height = 80
```

<span data-ttu-id="05cad-131">I nästa avsnitt anger du de värden som du vill att List rutan ska visa för användarna.</span><span class="sxs-lookup"><span data-stu-id="05cad-131">In the next section, you specify the values you want the list box to display to users.</span></span>

> [!NOTE]
> <span data-ttu-id="05cad-132">List rutan som skapats av det här skriptet tillåter endast ett val.</span><span class="sxs-lookup"><span data-stu-id="05cad-132">The list box created by this script allows only one selection.</span></span> <span data-ttu-id="05cad-133">Om du vill skapa en List Rute kontroll som tillåter flera val anger du ett värde för egenskapen **SelectionMode** , på samma sätt som följande: `$listBox.SelectionMode = 'MultiExtended'` .</span><span class="sxs-lookup"><span data-stu-id="05cad-133">To create a list box control that allows multiple selections, specify a value for the **SelectionMode** property, similarly to the following: `$listBox.SelectionMode = 'MultiExtended'`.</span></span> <span data-ttu-id="05cad-134">Mer information finns i [list rutor med flera val](Multiple-selection-List-Boxes.md).</span><span class="sxs-lookup"><span data-stu-id="05cad-134">For more information, see [Multiple-selection List Boxes](Multiple-selection-List-Boxes.md).</span></span>

```powershell
[void] $listBox.Items.Add('atl-dc-001')
[void] $listBox.Items.Add('atl-dc-002')
[void] $listBox.Items.Add('atl-dc-003')
[void] $listBox.Items.Add('atl-dc-004')
[void] $listBox.Items.Add('atl-dc-005')
[void] $listBox.Items.Add('atl-dc-006')
[void] $listBox.Items.Add('atl-dc-007')
```

<span data-ttu-id="05cad-135">Lägg till List Rute kontrollen i formuläret och instruera Windows att öppna formuläret ovanpå andra fönster och dialog rutor när den öppnas.</span><span class="sxs-lookup"><span data-stu-id="05cad-135">Add the list box control to your form, and instruct Windows to open the form atop other windows and dialog boxes when it's opened.</span></span>

```powershell
$form.Controls.Add($listBox)
$form.Topmost = $true
```

<span data-ttu-id="05cad-136">Lägg till följande kodrad för att visa formuläret i Windows.</span><span class="sxs-lookup"><span data-stu-id="05cad-136">Add the following line of code to display the form in Windows.</span></span>

```powershell
$result = $form.ShowDialog()
```

<span data-ttu-id="05cad-137">Slutligen instruerar koden inuti **IF** -block Windows vad som ska göras med formuläret när användarna har valt ett alternativ i list rutan. Klicka sedan på **OK** eller tryck på **RETUR** -tangenten.</span><span class="sxs-lookup"><span data-stu-id="05cad-137">Finally, the code inside the **If** block instructs Windows what to do with the form after users select an option from the list box, and then click the **OK** button or press the **Enter** key.</span></span>

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItem
    $x
}
```

## <a name="see-also"></a><span data-ttu-id="05cad-138">Se även</span><span class="sxs-lookup"><span data-stu-id="05cad-138">See Also</span></span>

- [<span data-ttu-id="05cad-139">GitHub: Dave Wyatt s WinFormsExampleUpdates</span><span class="sxs-lookup"><span data-stu-id="05cad-139">GitHub: Dave Wyatt's WinFormsExampleUpdates</span></span>](https://github.com/dlwyatt/WinFormsExampleUpdates)
- <span data-ttu-id="05cad-140">[Veckans Windows PowerShell-tips: välja objekt i en listruta](/previous-versions/windows/it-pro/windows-powershell-1.0/ff730949(v=technet.10))</span><span class="sxs-lookup"><span data-stu-id="05cad-140">[Windows PowerShell Tip of the Week: Selecting Items from a List Box](/previous-versions/windows/it-pro/windows-powershell-1.0/ff730949(v=technet.10))</span></span>
