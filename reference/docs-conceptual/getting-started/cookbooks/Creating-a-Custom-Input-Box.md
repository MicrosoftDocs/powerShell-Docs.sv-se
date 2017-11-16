---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Skapa en anpassad textrutan
ms.assetid: 0b12e56c-299f-40ee-afbf-d30d23ed2565
ms.openlocfilehash: 94172102fb81a9b31b7e84188f3e60a372e9cba2
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/08/2017
---
# <a name="creating-a-custom-input-box"></a><span data-ttu-id="c5c28-103">Skapa en anpassad textrutan</span><span class="sxs-lookup"><span data-stu-id="c5c28-103">Creating a Custom Input Box</span></span>
<span data-ttu-id="c5c28-104">Skript som en grafisk anpassade textrutan med hjälp av Microsoft .NET Framework formuläret skapa funktioner i Windows PowerShell 3.0 och senare versioner.</span><span class="sxs-lookup"><span data-stu-id="c5c28-104">Script a graphical custom input box by using Microsoft .NET Framework form-building features in Windows PowerShell 3.0 and later releases.</span></span>

## <a name="create-a-custom-graphical-input-box"></a><span data-ttu-id="c5c28-105">Skapa en anpassad, grafisk textrutan</span><span class="sxs-lookup"><span data-stu-id="c5c28-105">Create a custom, graphical input box</span></span>
<span data-ttu-id="c5c28-106">Kopiera och klistra in följande i Windows PowerShell ISE och spara den som en Windows PowerShell-skript (.ps1).</span><span class="sxs-lookup"><span data-stu-id="c5c28-106">Copy and then paste the following into Windows PowerShell ISE, and then save it as a Windows PowerShell script (.ps1).</span></span>

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
$label.Text = "Please enter the information in the space below:"
$form.Controls.Add($label) 

$textBox = New-Object System.Windows.Forms.TextBox 
$textBox.Location = New-Object System.Drawing.Point(10,40) 
$textBox.Size = New-Object System.Drawing.Size(260,20) 
$form.Controls.Add($textBox) 

$form.Topmost = $True

$form.Add_Shown({$textBox.Select()})
$result = $form.ShowDialog()

if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $textBox.Text
    $x
}
```

<span data-ttu-id="c5c28-107">Skriptet börjar genom att läsa in två klasser i .NET Framework: **System.Drawing** och **System.Windows.Forms**.</span><span class="sxs-lookup"><span data-stu-id="c5c28-107">The script begins by loading two .NET Framework classes: **System.Drawing** and **System.Windows.Forms**.</span></span> <span data-ttu-id="c5c28-108">Du startar sedan en ny instans av klassen .NET Framework **System.Windows.Forms.Form**; som innehåller ett tomt formulär eller fönster som du kan börja lägga till kontroller.</span><span class="sxs-lookup"><span data-stu-id="c5c28-108">You then start a new instance of the .NET Framework class **System.Windows.Forms.Form**; that provides a blank form or window to which you can start adding controls.</span></span>

```
$form = New-Object System.Windows.Forms.Form
```

<span data-ttu-id="c5c28-109">När du har skapat en instans av klassen formuläret tilldela värden till tre egenskaper i den här klassen.</span><span class="sxs-lookup"><span data-stu-id="c5c28-109">After you create an instance of the Form class, assign values to three properties of this class.</span></span>

- <span data-ttu-id="c5c28-110">**Text.**</span><span class="sxs-lookup"><span data-stu-id="c5c28-110">**Text.**</span></span> <span data-ttu-id="c5c28-111">Detta är titeln på fönstret.</span><span class="sxs-lookup"><span data-stu-id="c5c28-111">This becomes the title of the window.</span></span>

- <span data-ttu-id="c5c28-112">**Storlek.**</span><span class="sxs-lookup"><span data-stu-id="c5c28-112">**Size.**</span></span> <span data-ttu-id="c5c28-113">Detta är storleken på formuläret i bildpunkter.</span><span class="sxs-lookup"><span data-stu-id="c5c28-113">This is the size of the form, in pixels.</span></span> <span data-ttu-id="c5c28-114">Det här skriptet skapar ett formulär som är 300 bildpunkter av 200 bildpunkter.</span><span class="sxs-lookup"><span data-stu-id="c5c28-114">The preceding script creates a form that’s 300 pixels wide by 200 pixels tall.</span></span>

- <span data-ttu-id="c5c28-115">**StartingPosition.**</span><span class="sxs-lookup"><span data-stu-id="c5c28-115">**StartingPosition.**</span></span> <span data-ttu-id="c5c28-116">Den här valfria egenskapen **CenterScreen** i det här skriptet.</span><span class="sxs-lookup"><span data-stu-id="c5c28-116">This optional property is set to **CenterScreen** in the preceding script.</span></span> <span data-ttu-id="c5c28-117">Om du inte lägger till den här egenskapen, väljer en plats i Windows när formuläret öppnas.</span><span class="sxs-lookup"><span data-stu-id="c5c28-117">If you don’t add this property, Windows selects a location when the form is opened.</span></span> <span data-ttu-id="c5c28-118">Genom att ange den **StartingPosition** till **CenterScreen**, du automatiskt visar formuläret på skärmen för varje gång den läses in.</span><span class="sxs-lookup"><span data-stu-id="c5c28-118">By setting the **StartingPosition** to **CenterScreen**, you’re automatically displaying the form in the middle of the screen each time it loads.</span></span>

```
$form.Text = "Data Entry Form"
$form.Size = New-Object System.Drawing.Size(300,200) 
$form.StartPosition = "CenterScreen"
```

<span data-ttu-id="c5c28-119">Skapa sedan en **OK** knappen för formuläret.</span><span class="sxs-lookup"><span data-stu-id="c5c28-119">Next, create an **OK** button for your form.</span></span> <span data-ttu-id="c5c28-120">Ange storlek och hur den **OK** knappen.</span><span class="sxs-lookup"><span data-stu-id="c5c28-120">Specify the size and behavior of the **OK** button.</span></span> <span data-ttu-id="c5c28-121">I det här exemplet är knappen positionen 120 bildpunkter från formulärets övre kant och 75 bildpunkter från den vänstra kanten.</span><span class="sxs-lookup"><span data-stu-id="c5c28-121">In this example, the button position is 120 pixels from the form’s top edge, and 75 pixels from the left edge.</span></span> <span data-ttu-id="c5c28-122">Knappen höjden är 23 bildpunkter när knappen är 75 bildpunkter.</span><span class="sxs-lookup"><span data-stu-id="c5c28-122">The button height is 23 pixels, while the button length is 75 pixels.</span></span> <span data-ttu-id="c5c28-123">Skriptet använder fördefinierade Windows Forms-typer för att fastställa knappen beteenden.</span><span class="sxs-lookup"><span data-stu-id="c5c28-123">The script uses predefined Windows Forms types to determine the button behaviors.</span></span>

```
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = "OK"
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

<span data-ttu-id="c5c28-124">På liknande sätt kan du skapa en **Avbryt** knappen.</span><span class="sxs-lookup"><span data-stu-id="c5c28-124">Similarly, you create a **Cancel** button.</span></span> <span data-ttu-id="c5c28-125">Den **Avbryt** knappen är 120 bildpunkter uppifrån, men 150 bildpunkter från vänster i fönstret.</span><span class="sxs-lookup"><span data-stu-id="c5c28-125">The **Cancel** button is 120 pixels from the top, but 150 pixels from the left edge of the window.</span></span>

```
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = "Cancel"
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

<span data-ttu-id="c5c28-126">Ange sedan etikettexten på fönstret som beskriver den information som du vill att användarna ska ange.</span><span class="sxs-lookup"><span data-stu-id="c5c28-126">Next, provide label text on your window that describes the information you want users to provide.</span></span>

```
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20) 
$label.Size = New-Object System.Drawing.Size(280,20) 
$label.Text = "Please enter the information in the space below:"
$form.Controls.Add($label)
```

<span data-ttu-id="c5c28-127">Lägg till kontrollen (i det här fallet en textruta) som gör att användarna anger du den information som du har beskrivs i din etikettext.</span><span class="sxs-lookup"><span data-stu-id="c5c28-127">Add the control (in this case, a text box) that lets users provide the information you’ve described in your label text.</span></span> <span data-ttu-id="c5c28-128">Det finns många andra kontroller som du kan använda förutom textrutor; fler kontroller finns [System.Windows.Forms Namespace](http://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) på MSDN.</span><span class="sxs-lookup"><span data-stu-id="c5c28-128">There are many other controls you can apply besides text boxes; for more controls, see [System.Windows.Forms Namespace](http://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) on MSDN.</span></span>

```
$textBox = New-Object System.Windows.Forms.TextBox 
$textBox.Location = New-Object System.Drawing.Point(10,40) 
$textBox.Size = New-Object System.Drawing.Size(260,20) 
$form.Controls.Add($textBox)
```

<span data-ttu-id="c5c28-129">Ange den **Topmost** egenskapen **$True** att tvinga fönstret för att öppna ovanpå andra fönster och dialogrutor.</span><span class="sxs-lookup"><span data-stu-id="c5c28-129">Set the **Topmost** property to **$True** to force the window to open atop other open windows and dialog boxes.</span></span>

```
$form.Topmost = $True
```

<span data-ttu-id="c5c28-130">Sedan lägger du till kod för att aktivera formuläret och ange fokus i textrutan som du skapade.</span><span class="sxs-lookup"><span data-stu-id="c5c28-130">Next, add this line of code to activate the form, and set the focus to the text box that you created.</span></span>

```
$form.Add_Shown({$textBox.Select()})
```

<span data-ttu-id="c5c28-131">Lägg till följande kod för att visa formulär i Windows.</span><span class="sxs-lookup"><span data-stu-id="c5c28-131">Add the following line of code to display the form in Windows.</span></span>

```
$result = $form.ShowDialog()
```

<span data-ttu-id="c5c28-132">Slutligen kod inuti den **om** block instruerar Windows vad ska göras med formuläret när användare ange text i textrutan och klicka sedan på den **OK** knappen eller tryck på den **RETUR** nyckel.</span><span class="sxs-lookup"><span data-stu-id="c5c28-132">Finally, the code inside the **If** block instructs Windows what to do with the form after users provide text in the text box, and then click the **OK** button or press the **Enter** key.</span></span>

```
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $textBox.Text
    $x
}
```

## <a name="see-also"></a><span data-ttu-id="c5c28-133">Se även</span><span class="sxs-lookup"><span data-stu-id="c5c28-133">See Also</span></span>
- [<span data-ttu-id="c5c28-134">Hey Scripting Guy: Varför exemplen PowerShell-Gränssnittet fungerar inte?</span><span class="sxs-lookup"><span data-stu-id="c5c28-134">Hey Scripting Guy:  Why don’t these PowerShell GUI examples work?</span></span>](http://go.microsoft.com/fwlink/?LinkId=506644)
- [<span data-ttu-id="c5c28-135">GitHub: Dave Wyatt WinFormsExampleUpdates</span><span class="sxs-lookup"><span data-stu-id="c5c28-135">GitHub: Dave Wyatt's WinFormsExampleUpdates</span></span>](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [<span data-ttu-id="c5c28-136">Windows PowerShell-tips i veckan: skapa en anpassad Inmatningsruta</span><span class="sxs-lookup"><span data-stu-id="c5c28-136">Windows PowerShell Tip of the Week:  Creating a Custom Input Box</span></span>](http://technet.microsoft.com/library/ff730941.aspx)

