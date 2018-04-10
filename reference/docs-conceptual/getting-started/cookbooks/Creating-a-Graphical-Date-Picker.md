---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Skapa en grafisk datumväljare
ms.assetid: c1cb722c-41e9-4baa-be83-59b4653222e9
ms.openlocfilehash: 3727c90c314a6fc1b3a338ec60e44259f153d954
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="creating-a-graphical-date-picker"></a><span data-ttu-id="46a02-103">Skapa en grafisk datumväljare</span><span class="sxs-lookup"><span data-stu-id="46a02-103">Creating a Graphical Date Picker</span></span>

<span data-ttu-id="46a02-104">Använda Windows PowerShell 3.0 och senare versioner för att skapa ett formulär med en grafisk, kalender-format-kontroll som användarna kan välja en dag i månaden.</span><span class="sxs-lookup"><span data-stu-id="46a02-104">Use Windows PowerShell 3.0 and later releases to create a form with a graphical, calendar-style control that lets users select a day of the month.</span></span>

## <a name="create-a-graphical-date-picker-control"></a><span data-ttu-id="46a02-105">Skapa en grafisk datum-väljarkontrollen</span><span class="sxs-lookup"><span data-stu-id="46a02-105">Create a graphical date-picker control</span></span>

<span data-ttu-id="46a02-106">Kopiera och klistra in följande i Windows PowerShell ISE och spara den som en Windows PowerShell-skript (.ps1).</span><span class="sxs-lookup"><span data-stu-id="46a02-106">Copy and then paste the following into Windows PowerShell ISE, and then save it as a Windows PowerShell script (.ps1).</span></span>

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object Windows.Forms.Form

$form.Text = 'Select a Date'
$form.Size = New-Object Drawing.Size @(243,230)
$form.StartPosition = 'CenterScreen'

$calendar = New-Object System.Windows.Forms.MonthCalendar
$calendar.ShowTodayCircle = $false
$calendar.MaxSelectionCount = 1
$form.Controls.Add($calendar)

$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(38,165)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)

$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(113,165)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)

$form.Topmost = $true

$result = $form.ShowDialog()

if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

<span data-ttu-id="46a02-107">Skriptet börjar genom att läsa in två klasser i .NET Framework: **System.Drawing** och **System.Windows.Forms**.</span><span class="sxs-lookup"><span data-stu-id="46a02-107">The script begins by loading two .NET Framework classes: **System.Drawing** and **System.Windows.Forms**.</span></span> <span data-ttu-id="46a02-108">Du startar sedan en ny instans av klassen .NET Framework **Windows.Forms.Form**; som innehåller ett tomt formulär eller fönster som du kan börja lägga till kontroller.</span><span class="sxs-lookup"><span data-stu-id="46a02-108">You then start a new instance of the .NET Framework class **Windows.Forms.Form**; that provides a blank form or window to which you can start adding controls.</span></span>

```powershell
$form = New-Object Windows.Forms.Form
```

<span data-ttu-id="46a02-109">När du har skapat en instans av klassen formuläret tilldela värden till tre egenskaper i den här klassen.</span><span class="sxs-lookup"><span data-stu-id="46a02-109">After you create an instance of the Form class, assign values to three properties of this class.</span></span>

- <span data-ttu-id="46a02-110">**Text.**</span><span class="sxs-lookup"><span data-stu-id="46a02-110">**Text.**</span></span> <span data-ttu-id="46a02-111">Detta är titeln på fönstret.</span><span class="sxs-lookup"><span data-stu-id="46a02-111">This becomes the title of the window.</span></span>

- <span data-ttu-id="46a02-112">**Storlek.**</span><span class="sxs-lookup"><span data-stu-id="46a02-112">**Size.**</span></span> <span data-ttu-id="46a02-113">Detta är storleken på formuläret i bildpunkter.</span><span class="sxs-lookup"><span data-stu-id="46a02-113">This is the size of the form, in pixels.</span></span> <span data-ttu-id="46a02-114">Det här skriptet skapar ett formulär som är 243 pixlar brett och 230 bildpunkter.</span><span class="sxs-lookup"><span data-stu-id="46a02-114">The preceding script creates a form that’s 243 pixels wide by 230 pixels tall.</span></span>

- <span data-ttu-id="46a02-115">**StartingPosition.**</span><span class="sxs-lookup"><span data-stu-id="46a02-115">**StartingPosition.**</span></span> <span data-ttu-id="46a02-116">Den här valfria egenskapen **CenterScreen** i det här skriptet.</span><span class="sxs-lookup"><span data-stu-id="46a02-116">This optional property is set to **CenterScreen** in the preceding script.</span></span> <span data-ttu-id="46a02-117">Om du inte lägger till den här egenskapen, väljer en plats i Windows när formuläret öppnas.</span><span class="sxs-lookup"><span data-stu-id="46a02-117">If you don’t add this property, Windows selects a location when the form is opened.</span></span> <span data-ttu-id="46a02-118">Genom att ange den **StartingPosition** till **CenterScreen**, du automatiskt visar formuläret på skärmen för varje gång den läses in.</span><span class="sxs-lookup"><span data-stu-id="46a02-118">By setting the **StartingPosition** to **CenterScreen**, you’re automatically displaying the form in the middle of the screen each time it loads.</span></span>

```powershell
$form.Text = 'Select a Date'
$form.Size = New-Object Drawing.Size @(243,230)
$form.StartPosition = 'CenterScreen'
```

<span data-ttu-id="46a02-119">Sedan skapa och Lägg sedan till en kalenderkontroll i formuläret.</span><span class="sxs-lookup"><span data-stu-id="46a02-119">Next, create and then add a calendar control in your form.</span></span> <span data-ttu-id="46a02-120">I det här exemplet är den aktuella dagen inte markerad eller inringad.</span><span class="sxs-lookup"><span data-stu-id="46a02-120">In this example, the current day is not highlighted or circled.</span></span> <span data-ttu-id="46a02-121">Användare kan välja endast en dag i kalendern i taget.</span><span class="sxs-lookup"><span data-stu-id="46a02-121">Users can select only one day on the calendar at one time.</span></span>

```powershell
$calendar = New-Object System.Windows.Forms.MonthCalendar
$calendar.ShowTodayCircle = $false
$calendar.MaxSelectionCount = 1
$form.Controls.Add($calendar)
```

<span data-ttu-id="46a02-122">Skapa sedan en **OK** knappen för formuläret.</span><span class="sxs-lookup"><span data-stu-id="46a02-122">Next, create an **OK** button for your form.</span></span> <span data-ttu-id="46a02-123">Ange storlek och hur den **OK** knappen.</span><span class="sxs-lookup"><span data-stu-id="46a02-123">Specify the size and behavior of the **OK** button.</span></span> <span data-ttu-id="46a02-124">I det här exemplet är knappen positionen 165 pixlar från formulärets övre kant och 38 pixlar från den vänstra kanten.</span><span class="sxs-lookup"><span data-stu-id="46a02-124">In this example, the button position is 165 pixels from the form’s top edge, and 38 pixels from the left edge.</span></span> <span data-ttu-id="46a02-125">Knappen höjden är 23 bildpunkter när knappen är 75 bildpunkter.</span><span class="sxs-lookup"><span data-stu-id="46a02-125">The button height is 23 pixels, while the button length is 75 pixels.</span></span> <span data-ttu-id="46a02-126">Skriptet använder fördefinierade Windows Forms-typer för att fastställa knappen beteenden.</span><span class="sxs-lookup"><span data-stu-id="46a02-126">The script uses predefined Windows Forms types to determine the button behaviors.</span></span>

```powershell
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(38,165)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

<span data-ttu-id="46a02-127">På liknande sätt kan du skapa en **Avbryt** knappen.</span><span class="sxs-lookup"><span data-stu-id="46a02-127">Similarly, you create a **Cancel** button.</span></span> <span data-ttu-id="46a02-128">Den **Avbryt** knappen är 165 bildpunkter uppifrån, men 113 bildpunkter från vänster i fönstret.</span><span class="sxs-lookup"><span data-stu-id="46a02-128">The **Cancel** button is 165 pixels from the top, but 113 pixels from the left edge of the window.</span></span>

```powershell
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(113,165)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

<span data-ttu-id="46a02-129">Ange den **Topmost** egenskapen **$true** att tvinga fönstret för att öppna ovanpå andra fönster och dialogrutor.</span><span class="sxs-lookup"><span data-stu-id="46a02-129">Set the **Topmost** property to **$true** to force the window to open atop other open windows and dialog boxes.</span></span>

```powershell
$form.Topmost = $true
```

<span data-ttu-id="46a02-130">Lägg till följande kod för att visa formulär i Windows.</span><span class="sxs-lookup"><span data-stu-id="46a02-130">Add the following line of code to display the form in Windows.</span></span>

```powershell
$result = $form.ShowDialog()
```

<span data-ttu-id="46a02-131">Slutligen kod inuti den **om** block instruerar Windows vad ska göras med formuläret när användare väljer en dag i kalendern och klicka sedan på den **OK** knappen eller tryck på den **RETUR** nyckel.</span><span class="sxs-lookup"><span data-stu-id="46a02-131">Finally, the code inside the **If** block instructs Windows what to do with the form after users select a day on the calendar, and then click the **OK** button or press the **Enter** key.</span></span> <span data-ttu-id="46a02-132">Windows PowerShell visar det valda datumet för användarna.</span><span class="sxs-lookup"><span data-stu-id="46a02-132">Windows PowerShell displays the selected date to users.</span></span>

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

## <a name="see-also"></a><span data-ttu-id="46a02-133">Se även</span><span class="sxs-lookup"><span data-stu-id="46a02-133">See Also</span></span>

- [<span data-ttu-id="46a02-134">Hey Scripting Guy: Varför exemplen PowerShell-Gränssnittet fungerar inte?</span><span class="sxs-lookup"><span data-stu-id="46a02-134">Hey Scripting Guy:  Why don’t these PowerShell GUI examples work?</span></span>](http://go.microsoft.com/fwlink/?LinkId=506644)
- [<span data-ttu-id="46a02-135">GitHub: Dave Wyatt WinFormsExampleUpdates</span><span class="sxs-lookup"><span data-stu-id="46a02-135">GitHub: Dave Wyatt's WinFormsExampleUpdates</span></span>](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [<span data-ttu-id="46a02-136">Windows PowerShell-tips i veckan: skapar ett grafiskt datum objektväljare</span><span class="sxs-lookup"><span data-stu-id="46a02-136">Windows PowerShell Tip of the Week:  Creating a Graphical Date Picker</span></span>](http://technet.microsoft.com/library/ff730942.aspx)