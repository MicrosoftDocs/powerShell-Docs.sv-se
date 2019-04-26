---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Skapa en anpassad indataruta
ms.assetid: 0b12e56c-299f-40ee-afbf-d30d23ed2565
ms.openlocfilehash: 2d04ad6df65cdb4ff13d136dea47bbba6a01f3a2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086297"
---
# <a name="creating-a-custom-input-box"></a><span data-ttu-id="331a8-103">Skapa en anpassad indataruta</span><span class="sxs-lookup"><span data-stu-id="331a8-103">Creating a Custom Input Box</span></span>

<span data-ttu-id="331a8-104">Skript en grafisk anpassad indataruta med hjälp av Microsoft .NET Framework formuläret för att skapa funktioner i Windows PowerShell 3.0 och senare versioner.</span><span class="sxs-lookup"><span data-stu-id="331a8-104">Script a graphical custom input box by using Microsoft .NET Framework form-building features in Windows PowerShell 3.0 and later releases.</span></span>

## <a name="create-a-custom-graphical-input-box"></a><span data-ttu-id="331a8-105">Skapa en anpassad, grafisk indataruta</span><span class="sxs-lookup"><span data-stu-id="331a8-105">Create a custom, graphical input box</span></span>

<span data-ttu-id="331a8-106">Kopiera och klistra in följande i Windows PowerShell ISE och spara det som ett Windows PowerShell-skript (.ps1).</span><span class="sxs-lookup"><span data-stu-id="331a8-106">Copy and then paste the following into Windows PowerShell ISE, and then save it as a Windows PowerShell script (.ps1).</span></span>

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

<span data-ttu-id="331a8-107">Skriptet börjar genom att läsa in två .NET Framework-klasser: **System.Drawing** och **System.Windows.Forms**.</span><span class="sxs-lookup"><span data-stu-id="331a8-107">The script begins by loading two .NET Framework classes: **System.Drawing** and **System.Windows.Forms**.</span></span> <span data-ttu-id="331a8-108">Du startar sedan en ny instans av klassen .NET Framework **System.Windows.Forms.Form**; som innehåller ett tomt formulär eller fönster som du kan börja lägga till kontroller.</span><span class="sxs-lookup"><span data-stu-id="331a8-108">You then start a new instance of the .NET Framework class **System.Windows.Forms.Form**; that provides a blank form or window to which you can start adding controls.</span></span>

```powershell
$form = New-Object System.Windows.Forms.Form
```

<span data-ttu-id="331a8-109">När du har skapat en instans av klassen Form tilldela värden till tre egenskaper i den här klassen.</span><span class="sxs-lookup"><span data-stu-id="331a8-109">After you create an instance of the Form class, assign values to three properties of this class.</span></span>

- <span data-ttu-id="331a8-110">**Text.**</span><span class="sxs-lookup"><span data-stu-id="331a8-110">**Text.**</span></span> <span data-ttu-id="331a8-111">Detta blir titeln på fönstret.</span><span class="sxs-lookup"><span data-stu-id="331a8-111">This becomes the title of the window.</span></span>

- <span data-ttu-id="331a8-112">**Storlek.**</span><span class="sxs-lookup"><span data-stu-id="331a8-112">**Size.**</span></span> <span data-ttu-id="331a8-113">Det här är storleken på formuläret i bildpunkter.</span><span class="sxs-lookup"><span data-stu-id="331a8-113">This is the size of the form, in pixels.</span></span> <span data-ttu-id="331a8-114">Det här skriptet skapar ett formulär som är 300 bildpunkter på bredden 200 bildpunkter.</span><span class="sxs-lookup"><span data-stu-id="331a8-114">The preceding script creates a form that’s 300 pixels wide by 200 pixels tall.</span></span>

- <span data-ttu-id="331a8-115">**StartingPosition.**</span><span class="sxs-lookup"><span data-stu-id="331a8-115">**StartingPosition.**</span></span> <span data-ttu-id="331a8-116">Den här valfria egenskapen anges till **CenterScreen** i föregående skript.</span><span class="sxs-lookup"><span data-stu-id="331a8-116">This optional property is set to **CenterScreen** in the preceding script.</span></span> <span data-ttu-id="331a8-117">Om du inte lägger till den här egenskapen, väljer en plats i Windows när formuläret öppnas.</span><span class="sxs-lookup"><span data-stu-id="331a8-117">If you don’t add this property, Windows selects a location when the form is opened.</span></span> <span data-ttu-id="331a8-118">Genom att ange den **StartingPosition** till **CenterScreen**, du automatiskt visar formuläret mitt på skärmen varje gång den läses in.</span><span class="sxs-lookup"><span data-stu-id="331a8-118">By setting the **StartingPosition** to **CenterScreen**, you’re automatically displaying the form in the middle of the screen each time it loads.</span></span>

```powershell
$form.Text = 'Data Entry Form'
$form.Size = New-Object System.Drawing.Size(300,200)
$form.StartPosition = 'CenterScreen'
```

<span data-ttu-id="331a8-119">Skapa sedan en **OK** knappen för formuläret.</span><span class="sxs-lookup"><span data-stu-id="331a8-119">Next, create an **OK** button for your form.</span></span> <span data-ttu-id="331a8-120">Ange storlek och beteendet för den **OK** knappen.</span><span class="sxs-lookup"><span data-stu-id="331a8-120">Specify the size and behavior of the **OK** button.</span></span> <span data-ttu-id="331a8-121">I det här exemplet är knappen positionen 120 bildpunkter från formulärets övre kant och 75 bildpunkter från den vänstra kanten.</span><span class="sxs-lookup"><span data-stu-id="331a8-121">In this example, the button position is 120 pixels from the form’s top edge, and 75 pixels from the left edge.</span></span> <span data-ttu-id="331a8-122">Knappen höjden är 23 bildpunkter, medan den knapp längden är 75 bildpunkter.</span><span class="sxs-lookup"><span data-stu-id="331a8-122">The button height is 23 pixels, while the button length is 75 pixels.</span></span> <span data-ttu-id="331a8-123">Skriptet använder fördefinierade Windows Forms-typer för att fastställa knappen beteenden.</span><span class="sxs-lookup"><span data-stu-id="331a8-123">The script uses predefined Windows Forms types to determine the button behaviors.</span></span>

```powershell
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

<span data-ttu-id="331a8-124">På samma sätt kan du skapa en **Avbryt** knappen.</span><span class="sxs-lookup"><span data-stu-id="331a8-124">Similarly, you create a **Cancel** button.</span></span> <span data-ttu-id="331a8-125">Den **Avbryt** knappen är 120 bildpunkter uppifrån, men 150 pixlar från den vänstra kanten av fönstret.</span><span class="sxs-lookup"><span data-stu-id="331a8-125">The **Cancel** button is 120 pixels from the top, but 150 pixels from the left edge of the window.</span></span>

```powershell
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

<span data-ttu-id="331a8-126">Ange därefter etikettext på din fönster som beskriver den information du vill att användarna måste ange.</span><span class="sxs-lookup"><span data-stu-id="331a8-126">Next, provide label text on your window that describes the information you want users to provide.</span></span>

```powershell
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20)
$label.Size = New-Object System.Drawing.Size(280,20)
$label.Text = 'Please enter the information in the space below:'
$form.Controls.Add($label)
```

<span data-ttu-id="331a8-127">Lägg till kontrollen (i det här fallet en textruta) som användarna kan ange den information som du har som beskrivs i din etikettext.</span><span class="sxs-lookup"><span data-stu-id="331a8-127">Add the control (in this case, a text box) that lets users provide the information you’ve described in your label text.</span></span> <span data-ttu-id="331a8-128">Det finns många andra kontroller som du kan använda förutom textrutor; Läs fler kontroller [System.Windows.Forms Namespace](https://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) på MSDN.</span><span class="sxs-lookup"><span data-stu-id="331a8-128">There are many other controls you can apply besides text boxes; for more controls, see [System.Windows.Forms Namespace](https://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) on MSDN.</span></span>

```powershell
$textBox = New-Object System.Windows.Forms.TextBox
$textBox.Location = New-Object System.Drawing.Point(10,40)
$textBox.Size = New-Object System.Drawing.Size(260,20)
$form.Controls.Add($textBox)
```

<span data-ttu-id="331a8-129">Ange den **Topmost** egenskap **$true** att tvinga den tidsperioden för att öppna ovanpå andra fönster och dialogrutor.</span><span class="sxs-lookup"><span data-stu-id="331a8-129">Set the **Topmost** property to **$true** to force the window to open atop other open windows and dialog boxes.</span></span>

```powershell
$form.Topmost = $true
```

<span data-ttu-id="331a8-130">Sedan lägger du till den här raden med kod för att aktivera formuläret och ange att fokusera på textrutan som du skapade.</span><span class="sxs-lookup"><span data-stu-id="331a8-130">Next, add this line of code to activate the form, and set the focus to the text box that you created.</span></span>

```powershell
$form.Add_Shown({$textBox.Select()})
```

<span data-ttu-id="331a8-131">Lägg till följande rad med kod för att visa formuläret i Windows.</span><span class="sxs-lookup"><span data-stu-id="331a8-131">Add the following line of code to display the form in Windows.</span></span>

```powershell
$result = $form.ShowDialog()
```

<span data-ttu-id="331a8-132">Koden i den **om** block instruerar Windows vad som ska göras med formuläret när användare ange text i textrutan och klicka sedan på den **OK** knapp eller genom att trycka på den **RETUR** nyckeln.</span><span class="sxs-lookup"><span data-stu-id="331a8-132">Finally, the code inside the **If** block instructs Windows what to do with the form after users provide text in the text box, and then click the **OK** button or press the **Enter** key.</span></span>

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $textBox.Text
    $x
}
```

## <a name="see-also"></a><span data-ttu-id="331a8-133">Se även</span><span class="sxs-lookup"><span data-stu-id="331a8-133">See Also</span></span>

- [<span data-ttu-id="331a8-134">Hej skriptdoktorn:  Varför fungerar inte dessa PowerShell-GUI-exempel?</span><span class="sxs-lookup"><span data-stu-id="331a8-134">Hey Scripting Guy:  Why don’t these PowerShell GUI examples work?</span></span>](https://go.microsoft.com/fwlink/?LinkId=506644)
- [<span data-ttu-id="331a8-135">GitHub: Dave Wyatt WinFormsExampleUpdates</span><span class="sxs-lookup"><span data-stu-id="331a8-135">GitHub: Dave Wyatt's WinFormsExampleUpdates</span></span>](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [<span data-ttu-id="331a8-136">Windows PowerShell-tips i veckan:  Skapa en anpassad indataruta</span><span class="sxs-lookup"><span data-stu-id="331a8-136">Windows PowerShell Tip of the Week:  Creating a Custom Input Box</span></span>](https://technet.microsoft.com/library/ff730941.aspx)