---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Listrutor med flera val
ms.openlocfilehash: 7bf71fb76a11f88c4ad4790bf3a2b383d0babb81
ms.sourcegitcommit: 3e343f005fe76960c998ef1869a1a093d37ef349
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/23/2020
ms.locfileid: "85216081"
---
# <a name="multiple-selection-list-boxes"></a><span data-ttu-id="c7d93-103">List rutor med flera val</span><span class="sxs-lookup"><span data-stu-id="c7d93-103">Multiple-selection List Boxes</span></span>

<span data-ttu-id="c7d93-104">Använd Windows PowerShell 3,0 och senare versioner för att skapa en List Rute kontroll med flera val i ett anpassat Windows-formulär.</span><span class="sxs-lookup"><span data-stu-id="c7d93-104">Use Windows PowerShell 3.0 and later releases to create a multiple-selection list box control in a custom Windows Form.</span></span>

## <a name="create-list-box-controls-that-allow-multiple-selections"></a><span data-ttu-id="c7d93-105">Skapa List Rute kontroller som tillåter flera val</span><span class="sxs-lookup"><span data-stu-id="c7d93-105">Create list box controls that allow multiple selections</span></span>

<span data-ttu-id="c7d93-106">Kopiera och klistra in följande i Windows PowerShell ISE och spara det sedan som ett Windows PowerShell-skript (. ps1).</span><span class="sxs-lookup"><span data-stu-id="c7d93-106">Copy and then paste the following into Windows PowerShell ISE, and then save it as a Windows PowerShell script (.ps1).</span></span>

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
$label.Text = 'Please make a selection from the list below:'
$form.Controls.Add($label)

$listBox = New-Object System.Windows.Forms.Listbox
$listBox.Location = New-Object System.Drawing.Point(10,40)
$listBox.Size = New-Object System.Drawing.Size(260,20)

$listBox.SelectionMode = 'MultiExtended'

[void] $listBox.Items.Add('Item 1')
[void] $listBox.Items.Add('Item 2')
[void] $listBox.Items.Add('Item 3')
[void] $listBox.Items.Add('Item 4')
[void] $listBox.Items.Add('Item 5')

$listBox.Height = 70
$form.Controls.Add($listBox)
$form.Topmost = $true

$result = $form.ShowDialog()

if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItems
    $x
}
```

<span data-ttu-id="c7d93-107">Skriptet börjar genom att läsa in två .NET Framework klasser: **system. Drawing** och **system. Windows. Forms**.</span><span class="sxs-lookup"><span data-stu-id="c7d93-107">The script begins by loading two .NET Framework classes: **System.Drawing** and **System.Windows.Forms**.</span></span> <span data-ttu-id="c7d93-108">Sedan startar du en ny instans av klassen .NET Framework klass **system. Windows. Forms. form**; Det innehåller ett tomt formulär eller fönster som du kan börja lägga till kontroller i.</span><span class="sxs-lookup"><span data-stu-id="c7d93-108">You then start a new instance of the .NET Framework class **System.Windows.Forms.Form**; that provides a blank form or window to which you can start adding controls.</span></span>

```powershell
$form = New-Object System.Windows.Forms.Form
```

<span data-ttu-id="c7d93-109">När du har skapat en instans av formulär klassen tilldelar du värden till tre egenskaper för den här klassen.</span><span class="sxs-lookup"><span data-stu-id="c7d93-109">After you create an instance of the Form class, assign values to three properties of this class.</span></span>

- <span data-ttu-id="c7d93-110">**Information.**</span><span class="sxs-lookup"><span data-stu-id="c7d93-110">**Text.**</span></span> <span data-ttu-id="c7d93-111">Detta blir rubriken för fönstret.</span><span class="sxs-lookup"><span data-stu-id="c7d93-111">This becomes the title of the window.</span></span>

- <span data-ttu-id="c7d93-112">**Ändra.**</span><span class="sxs-lookup"><span data-stu-id="c7d93-112">**Size.**</span></span> <span data-ttu-id="c7d93-113">Detta är storleken på formuläret, i bild punkter.</span><span class="sxs-lookup"><span data-stu-id="c7d93-113">This is the size of the form, in pixels.</span></span> <span data-ttu-id="c7d93-114">Föregående skript skapar ett formulär som är 300 bild punkter brett med 200 pixlar högt.</span><span class="sxs-lookup"><span data-stu-id="c7d93-114">The preceding script creates a form that’s 300 pixels wide by 200 pixels tall.</span></span>

- <span data-ttu-id="c7d93-115">**Star ting position.**</span><span class="sxs-lookup"><span data-stu-id="c7d93-115">**StartingPosition.**</span></span> <span data-ttu-id="c7d93-116">Den här valfria egenskapen anges till **CenterScreen** i föregående skript.</span><span class="sxs-lookup"><span data-stu-id="c7d93-116">This optional property is set to **CenterScreen** in the preceding script.</span></span> <span data-ttu-id="c7d93-117">Om du inte lägger till den här egenskapen väljer Windows en plats när formuläret öppnas.</span><span class="sxs-lookup"><span data-stu-id="c7d93-117">If you don’t add this property, Windows selects a location when the form is opened.</span></span> <span data-ttu-id="c7d93-118">Genom att ange **Star ting position** till **CenterScreen**visas formuläret automatiskt i mitten av skärmen varje gången det läses in.</span><span class="sxs-lookup"><span data-stu-id="c7d93-118">By setting the **StartingPosition** to **CenterScreen**, you’re automatically displaying the form in the middle of the screen each time it loads.</span></span>

```powershell
$form.Text = 'Data Entry Form'
$form.Size = New-Object System.Drawing.Size(300,200)
$form.StartPosition = 'CenterScreen'
```

<span data-ttu-id="c7d93-119">Skapa sedan en **OK** -knapp för formuläret.</span><span class="sxs-lookup"><span data-stu-id="c7d93-119">Next, create an **OK** button for your form.</span></span> <span data-ttu-id="c7d93-120">Ange storlek och beteende för **OK** -knappen.</span><span class="sxs-lookup"><span data-stu-id="c7d93-120">Specify the size and behavior of the **OK** button.</span></span> <span data-ttu-id="c7d93-121">I det här exemplet är knapp positionen 120 bild punkter från formulärets övre kant och 75 pixlar från den vänstra kanten.</span><span class="sxs-lookup"><span data-stu-id="c7d93-121">In this example, the button position is 120 pixels from the form’s top edge, and 75 pixels from the left edge.</span></span> <span data-ttu-id="c7d93-122">Knapp höjden är 23 bild punkter, medan knapp längden är 75 bild punkter.</span><span class="sxs-lookup"><span data-stu-id="c7d93-122">The button height is 23 pixels, while the button length is 75 pixels.</span></span> <span data-ttu-id="c7d93-123">Skriptet använder fördefinierade Windows Forms typer för att fastställa knapp beteenden.</span><span class="sxs-lookup"><span data-stu-id="c7d93-123">The script uses predefined Windows Forms types to determine the button behaviors.</span></span>

```powershell
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Size(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

<span data-ttu-id="c7d93-124">På samma sätt skapar du en **Avbryt** -knapp.</span><span class="sxs-lookup"><span data-stu-id="c7d93-124">Similarly, you create a **Cancel** button.</span></span> <span data-ttu-id="c7d93-125">Knappen **Avbryt** är 120 bild punkter ovanifrån, men 150 pixlar från den vänstra kanten av fönstret.</span><span class="sxs-lookup"><span data-stu-id="c7d93-125">The **Cancel** button is 120 pixels from the top, but 150 pixels from the left edge of the window.</span></span>

```powershell
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

<span data-ttu-id="c7d93-126">Ange sedan etikettext i fönstret som beskriver den information som du vill att användarna ska kunna tillhandahålla.</span><span class="sxs-lookup"><span data-stu-id="c7d93-126">Next, provide label text on your window that describes the information you want users to provide.</span></span>

```powershell
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20)
$label.Size = New-Object System.Drawing.Size(280,20)
$label.Text = 'Please make a selection from the list below:'
$form.Controls.Add($label)
```

<span data-ttu-id="c7d93-127">Lägg till kontrollen (i det här fallet en listruta) som gör det möjligt för användarna att ange den information som du har beskrivet i din etikett text.</span><span class="sxs-lookup"><span data-stu-id="c7d93-127">Add the control (in this case, a list box) that lets users provide the information you’ve described in your label text.</span></span> <span data-ttu-id="c7d93-128">Det finns många andra kontroller som du kan använda förutom text rutor. Mer kontroller finns i [namn området system. Windows. Forms](https://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) på MSDN.</span><span class="sxs-lookup"><span data-stu-id="c7d93-128">There are many other controls you can apply besides text boxes; for more controls, see [System.Windows.Forms Namespace](https://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) on MSDN.</span></span>

```powershell
$listBox = New-Object System.Windows.Forms.Listbox
$listBox.Location = New-Object System.Drawing.Point(10,40)
$listBox.Size = New-Object System.Drawing.Size(260,20)
```

<span data-ttu-id="c7d93-129">Så här kan du ange att användarna ska kunna välja flera värden i listan.</span><span class="sxs-lookup"><span data-stu-id="c7d93-129">Here’s how you specify that you want to allow users to select multiple values from the list.</span></span>

```powershell
$listBox.SelectionMode = 'MultiExtended'
```

<span data-ttu-id="c7d93-130">I nästa avsnitt anger du de värden som du vill att List rutan ska visa för användarna.</span><span class="sxs-lookup"><span data-stu-id="c7d93-130">In the next section, you specify the values you want the list box to display to users.</span></span>

```powershell
[void] $listBox.Items.Add('Item 1')
[void] $listBox.Items.Add('Item 2')
[void] $listBox.Items.Add('Item 3')
[void] $listBox.Items.Add('Item 4')
[void] $listBox.Items.Add('Item 5')
```

<span data-ttu-id="c7d93-131">Ange den maximala höjden för List Rute kontrollen.</span><span class="sxs-lookup"><span data-stu-id="c7d93-131">Specify the maximum height of the list box control.</span></span>

```powershell
$listBox.Height = 70
```

<span data-ttu-id="c7d93-132">Lägg till List Rute kontrollen i formuläret och instruera Windows att öppna formuläret ovanpå andra fönster och dialog rutor när den öppnas.</span><span class="sxs-lookup"><span data-stu-id="c7d93-132">Add the list box control to your form, and instruct Windows to open the form atop other windows and dialog boxes when it’s opened.</span></span>

```powershell
$form.Controls.Add($listBox)
$form.Topmost = $true
```

<span data-ttu-id="c7d93-133">Lägg till följande kodrad för att visa formuläret i Windows.</span><span class="sxs-lookup"><span data-stu-id="c7d93-133">Add the following line of code to display the form in Windows.</span></span>

```powershell
$result = $form.ShowDialog()
```

<span data-ttu-id="c7d93-134">Slutligen instruerar koden inuti **IF** -block Windows vad som ska göras med formuläret när användarna har valt ett eller flera alternativ i list rutan. Klicka sedan på **OK** eller tryck på **RETUR** .</span><span class="sxs-lookup"><span data-stu-id="c7d93-134">Finally, the code inside the **If** block instructs Windows what to do with the form after users select one or more options from the list box, and then click the **OK** button or press the **Enter** key.</span></span>

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItems
    $x
}
```

## <a name="see-also"></a><span data-ttu-id="c7d93-135">Se även</span><span class="sxs-lookup"><span data-stu-id="c7d93-135">See Also</span></span>

- [<span data-ttu-id="c7d93-136">Helg skript: åtgärda exempel på PowerShell-gränssnittet</span><span class="sxs-lookup"><span data-stu-id="c7d93-136">Weekend Scripter:  Fixing PowerShell GUI Examples</span></span>](https://go.microsoft.com/fwlink/?LinkId=506644)
- [<span data-ttu-id="c7d93-137">GitHub: Dave Wyatt s WinFormsExampleUpdates</span><span class="sxs-lookup"><span data-stu-id="c7d93-137">GitHub: Dave Wyatt's WinFormsExampleUpdates</span></span>](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [<span data-ttu-id="c7d93-138">Veckans Windows PowerShell-tips: fler List rutor med flera val och mer!</span><span class="sxs-lookup"><span data-stu-id="c7d93-138">Windows PowerShell Tip of the Week:  Multi-Select List Boxes - And More!</span></span>](https://technet.microsoft.com/library/ff730950.aspx)
