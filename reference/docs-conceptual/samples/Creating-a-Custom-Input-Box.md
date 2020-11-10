---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Skapa en anpassad indataruta
description: Den här artikeln visar hur du skapar en anpassad Indatatyp med hjälp av .NET Framework Forms Building-funktioner i Windows PowerShell.
ms.openlocfilehash: b7786706d2461c329da429c1bd4971d7dc874d6d
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94390090"
---
# <a name="creating-a-custom-input-box"></a><span data-ttu-id="6238d-104">Skapa en anpassad indataruta</span><span class="sxs-lookup"><span data-stu-id="6238d-104">Creating a Custom Input Box</span></span>

<span data-ttu-id="6238d-105">Skripta en grafisk anpassad Indatatyp med hjälp av Microsoft .NET ramverk Forms Bygg funktioner i Windows PowerShell 3,0 och senare versioner.</span><span class="sxs-lookup"><span data-stu-id="6238d-105">Script a graphical custom input box by using Microsoft .NET Framework form-building features in Windows PowerShell 3.0 and later releases.</span></span>

## <a name="create-a-custom-graphical-input-box"></a><span data-ttu-id="6238d-106">Skapa en anpassad, grafisk inmatad ruta</span><span class="sxs-lookup"><span data-stu-id="6238d-106">Create a custom, graphical input box</span></span>

<span data-ttu-id="6238d-107">Kopiera och klistra in följande i Windows PowerShell ISE och spara det sedan som ett Windows PowerShell-skript (. ps1).</span><span class="sxs-lookup"><span data-stu-id="6238d-107">Copy and then paste the following into Windows PowerShell ISE, and then save it as a Windows PowerShell script (.ps1).</span></span>

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

<span data-ttu-id="6238d-108">Skriptet börjar genom att läsa in två .NET Framework klasser: **system. Drawing** och **system. Windows. Forms**.</span><span class="sxs-lookup"><span data-stu-id="6238d-108">The script begins by loading two .NET Framework classes: **System.Drawing** and **System.Windows.Forms**.</span></span> <span data-ttu-id="6238d-109">Sedan startar du en ny instans av klassen .NET Framework klass **system. Windows. Forms. form** ; Det innehåller ett tomt formulär eller fönster som du kan börja lägga till kontroller i.</span><span class="sxs-lookup"><span data-stu-id="6238d-109">You then start a new instance of the .NET Framework class **System.Windows.Forms.Form** ; that provides a blank form or window to which you can start adding controls.</span></span>

```powershell
$form = New-Object System.Windows.Forms.Form
```

<span data-ttu-id="6238d-110">När du har skapat en instans av formulär klassen tilldelar du värden till tre egenskaper för den här klassen.</span><span class="sxs-lookup"><span data-stu-id="6238d-110">After you create an instance of the Form class, assign values to three properties of this class.</span></span>

- <span data-ttu-id="6238d-111">**Information.**</span><span class="sxs-lookup"><span data-stu-id="6238d-111">**Text.**</span></span> <span data-ttu-id="6238d-112">Detta blir rubriken för fönstret.</span><span class="sxs-lookup"><span data-stu-id="6238d-112">This becomes the title of the window.</span></span>

- <span data-ttu-id="6238d-113">**Ändra.**</span><span class="sxs-lookup"><span data-stu-id="6238d-113">**Size.**</span></span> <span data-ttu-id="6238d-114">Detta är storleken på formuläret, i bild punkter.</span><span class="sxs-lookup"><span data-stu-id="6238d-114">This is the size of the form, in pixels.</span></span> <span data-ttu-id="6238d-115">Föregående skript skapar ett formulär som är 300 bild punkter brett med 200 pixlar högt.</span><span class="sxs-lookup"><span data-stu-id="6238d-115">The preceding script creates a form that's 300 pixels wide by 200 pixels tall.</span></span>

- <span data-ttu-id="6238d-116">**Star ting position.**</span><span class="sxs-lookup"><span data-stu-id="6238d-116">**StartingPosition.**</span></span> <span data-ttu-id="6238d-117">Den här valfria egenskapen anges till **CenterScreen** i föregående skript.</span><span class="sxs-lookup"><span data-stu-id="6238d-117">This optional property is set to **CenterScreen** in the preceding script.</span></span>
  <span data-ttu-id="6238d-118">Om du inte lägger till den här egenskapen väljer Windows en plats när formuläret öppnas.</span><span class="sxs-lookup"><span data-stu-id="6238d-118">If you don't add this property, Windows selects a location when the form is opened.</span></span> <span data-ttu-id="6238d-119">Genom att ange **Star ting position** till **CenterScreen** visas formuläret automatiskt i mitten av skärmen varje gången det läses in.</span><span class="sxs-lookup"><span data-stu-id="6238d-119">By setting the **StartingPosition** to **CenterScreen** , you're automatically displaying the form in the middle of the screen each time it loads.</span></span>

```powershell
$form.Text = 'Data Entry Form'
$form.Size = New-Object System.Drawing.Size(300,200)
$form.StartPosition = 'CenterScreen'
```

<span data-ttu-id="6238d-120">Skapa sedan en **OK** -knapp för formuläret.</span><span class="sxs-lookup"><span data-stu-id="6238d-120">Next, create an **OK** button for your form.</span></span> <span data-ttu-id="6238d-121">Ange storlek och beteende för **OK** -knappen.</span><span class="sxs-lookup"><span data-stu-id="6238d-121">Specify the size and behavior of the **OK** button.</span></span> <span data-ttu-id="6238d-122">I det här exemplet är knapp positionen 120 bild punkter från formulärets övre kant och 75 pixlar från den vänstra kanten.</span><span class="sxs-lookup"><span data-stu-id="6238d-122">In this example, the button position is 120 pixels from the form's top edge, and 75 pixels from the left edge.</span></span> <span data-ttu-id="6238d-123">Knapp höjden är 23 bild punkter, medan knapp längden är 75 bild punkter.</span><span class="sxs-lookup"><span data-stu-id="6238d-123">The button height is 23 pixels, while the button length is 75 pixels.</span></span> <span data-ttu-id="6238d-124">Skriptet använder fördefinierade Windows Forms typer för att fastställa knapp beteenden.</span><span class="sxs-lookup"><span data-stu-id="6238d-124">The script uses predefined Windows Forms types to determine the button behaviors.</span></span>

```powershell
$okButton = New-Object System.Windows.Forms.Button
$okButton.Location = New-Object System.Drawing.Point(75,120)
$okButton.Size = New-Object System.Drawing.Size(75,23)
$okButton.Text = 'OK'
$okButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

<span data-ttu-id="6238d-125">På samma sätt skapar du en **Avbryt** -knapp.</span><span class="sxs-lookup"><span data-stu-id="6238d-125">Similarly, you create a **Cancel** button.</span></span> <span data-ttu-id="6238d-126">Knappen **Avbryt** är 120 bild punkter ovanifrån, men 150 pixlar från den vänstra kanten av fönstret.</span><span class="sxs-lookup"><span data-stu-id="6238d-126">The **Cancel** button is 120 pixels from the top, but 150 pixels from the left edge of the window.</span></span>

```powershell
$cancelButton = New-Object System.Windows.Forms.Button
$cancelButton.Location = New-Object System.Drawing.Point(150,120)
$cancelButton.Size = New-Object System.Drawing.Size(75,23)
$cancelButton.Text = 'Cancel'
$cancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $cancelButton
$form.Controls.Add($cancelButton)
```

<span data-ttu-id="6238d-127">Ange sedan etikettext i fönstret som beskriver den information som du vill att användarna ska kunna tillhandahålla.</span><span class="sxs-lookup"><span data-stu-id="6238d-127">Next, provide label text on your window that describes the information you want users to provide.</span></span>

```powershell
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20)
$label.Size = New-Object System.Drawing.Size(280,20)
$label.Text = 'Please enter the information in the space below:'
$form.Controls.Add($label)
```

<span data-ttu-id="6238d-128">Lägg till kontrollen (i det här fallet en text ruta) som gör det möjligt för användarna att ange den information som du har beskrivet i din etikett text.</span><span class="sxs-lookup"><span data-stu-id="6238d-128">Add the control (in this case, a text box) that lets users provide the information you've described in your label text.</span></span> <span data-ttu-id="6238d-129">Det finns många andra kontroller som du kan använda förutom text rutor. Mer kontroller finns i [namn området system. Windows. Forms](/dotnet/api/system.windows.forms).</span><span class="sxs-lookup"><span data-stu-id="6238d-129">There are many other controls you can apply besides text boxes; for more controls, see [System.Windows.Forms Namespace](/dotnet/api/system.windows.forms).</span></span>

```powershell
$textBox = New-Object System.Windows.Forms.TextBox
$textBox.Location = New-Object System.Drawing.Point(10,40)
$textBox.Size = New-Object System.Drawing.Size(260,20)
$form.Controls.Add($textBox)
```

<span data-ttu-id="6238d-130">Ställ in den **översta** egenskapen på **$True** för att tvinga fönstret att öppna ovanpå andra öppna fönster och dialog rutor.</span><span class="sxs-lookup"><span data-stu-id="6238d-130">Set the **Topmost** property to **$true** to force the window to open atop other open windows and dialog boxes.</span></span>

```powershell
$form.Topmost = $true
```

<span data-ttu-id="6238d-131">Lägg sedan till den här kodraden för att aktivera formuläret och ange fokus till text rutan som du skapade.</span><span class="sxs-lookup"><span data-stu-id="6238d-131">Next, add this line of code to activate the form, and set the focus to the text box that you created.</span></span>

```powershell
$form.Add_Shown({$textBox.Select()})
```

<span data-ttu-id="6238d-132">Lägg till följande kodrad för att visa formuläret i Windows.</span><span class="sxs-lookup"><span data-stu-id="6238d-132">Add the following line of code to display the form in Windows.</span></span>

```powershell
$result = $form.ShowDialog()
```

<span data-ttu-id="6238d-133">Slutligen instruerar koden inuti **IF** -block Windows vad som ska göras med formuläret när användarna har angett text i text rutan. Klicka sedan på **OK** eller tryck på **RETUR** -tangenten.</span><span class="sxs-lookup"><span data-stu-id="6238d-133">Finally, the code inside the **If** block instructs Windows what to do with the form after users provide text in the text box, and then click the **OK** button or press the **Enter** key.</span></span>

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $textBox.Text
    $x
}
```

## <a name="see-also"></a><span data-ttu-id="6238d-134">Se även</span><span class="sxs-lookup"><span data-stu-id="6238d-134">See Also</span></span>

- <span data-ttu-id="6238d-135">[GitHub: Dave Wyatt s WinFormsExampleUpdates](/previous-versions/windows/it-pro/windows-powershell-1.0/ff730941(v=technet.10))</span><span class="sxs-lookup"><span data-stu-id="6238d-135">[GitHub: Dave Wyatt's WinFormsExampleUpdates](/previous-versions/windows/it-pro/windows-powershell-1.0/ff730941(v=technet.10))</span></span>
- [<span data-ttu-id="6238d-136">Veckans Windows PowerShell-tips: skapa en anpassad indatamängds ruta</span><span class="sxs-lookup"><span data-stu-id="6238d-136">Windows PowerShell Tip of the Week:  Creating a Custom Input Box</span></span>](https://technet.microsoft.com/library/ff730941.aspx)
