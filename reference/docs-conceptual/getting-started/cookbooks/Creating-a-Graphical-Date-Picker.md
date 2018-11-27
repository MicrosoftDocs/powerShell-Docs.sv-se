---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Skapa en grafisk datumväljare
ms.assetid: c1cb722c-41e9-4baa-be83-59b4653222e9
ms.openlocfilehash: 6dd43a3b1f4c67633ad1755de3db88eb8c6772c8
ms.sourcegitcommit: 221b7daab7f597f8b2e4864cf9b5d9dda9b9879b
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/27/2018
ms.locfileid: "52320337"
---
# <a name="creating-a-graphical-date-picker"></a><span data-ttu-id="6d0b0-103">Skapa en grafisk datumväljare</span><span class="sxs-lookup"><span data-stu-id="6d0b0-103">Creating a Graphical Date Picker</span></span>

<span data-ttu-id="6d0b0-104">Använda Windows PowerShell 3.0 och senare versioner för att skapa ett formulär med en grafisk, kalender-style-kontroll som användaren kan välja en dag i månaden.</span><span class="sxs-lookup"><span data-stu-id="6d0b0-104">Use Windows PowerShell 3.0 and later releases to create a form with a graphical, calendar-style control that lets users select a day of the month.</span></span>

## <a name="create-a-graphical-date-picker-control"></a><span data-ttu-id="6d0b0-105">Skapa en grafisk datumväljare-kontroll</span><span class="sxs-lookup"><span data-stu-id="6d0b0-105">Create a graphical date-picker control</span></span>

<span data-ttu-id="6d0b0-106">Kopiera och klistra in följande i Windows PowerShell ISE och spara det som ett Windows PowerShell-skript (.ps1).</span><span class="sxs-lookup"><span data-stu-id="6d0b0-106">Copy and then paste the following into Windows PowerShell ISE, and then save it as a Windows PowerShell script (.ps1).</span></span>

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

<span data-ttu-id="6d0b0-107">Skriptet börjar genom att läsa in två .NET Framework-klasser: **System.Drawing** och **System.Windows.Forms**.</span><span class="sxs-lookup"><span data-stu-id="6d0b0-107">The script begins by loading two .NET Framework classes: **System.Drawing** and **System.Windows.Forms**.</span></span> <span data-ttu-id="6d0b0-108">Du startar sedan en ny instans av klassen .NET Framework **Windows.Forms.Form**; som innehåller ett tomt formulär eller fönster som du kan börja lägga till kontroller.</span><span class="sxs-lookup"><span data-stu-id="6d0b0-108">You then start a new instance of the .NET Framework class **Windows.Forms.Form**; that provides a blank form or window to which you can start adding controls.</span></span>

```powershell
$form = New-Object Windows.Forms.Form
```

<span data-ttu-id="6d0b0-109">När du har skapat en instans av klassen Form tilldela värden till tre egenskaper i den här klassen.</span><span class="sxs-lookup"><span data-stu-id="6d0b0-109">After you create an instance of the Form class, assign values to three properties of this class.</span></span>

- <span data-ttu-id="6d0b0-110">**Text.**</span><span class="sxs-lookup"><span data-stu-id="6d0b0-110">**Text.**</span></span> <span data-ttu-id="6d0b0-111">Detta blir titeln på fönstret.</span><span class="sxs-lookup"><span data-stu-id="6d0b0-111">This becomes the title of the window.</span></span>

- <span data-ttu-id="6d0b0-112">**Storlek.**</span><span class="sxs-lookup"><span data-stu-id="6d0b0-112">**Size.**</span></span> <span data-ttu-id="6d0b0-113">Det här är storleken på formuläret i bildpunkter.</span><span class="sxs-lookup"><span data-stu-id="6d0b0-113">This is the size of the form, in pixels.</span></span> <span data-ttu-id="6d0b0-114">Det här skriptet skapar ett formulär som är 243 bildpunkter på bredden 230 pixlar hög.</span><span class="sxs-lookup"><span data-stu-id="6d0b0-114">The preceding script creates a form that’s 243 pixels wide by 230 pixels tall.</span></span>

- <span data-ttu-id="6d0b0-115">**StartingPosition.**</span><span class="sxs-lookup"><span data-stu-id="6d0b0-115">**StartingPosition.**</span></span> <span data-ttu-id="6d0b0-116">Den här valfria egenskapen anges till **CenterScreen** i föregående skript.</span><span class="sxs-lookup"><span data-stu-id="6d0b0-116">This optional property is set to **CenterScreen** in the preceding script.</span></span> <span data-ttu-id="6d0b0-117">Om du inte lägger till den här egenskapen, väljer en plats i Windows när formuläret öppnas.</span><span class="sxs-lookup"><span data-stu-id="6d0b0-117">If you don’t add this property, Windows selects a location when the form is opened.</span></span> <span data-ttu-id="6d0b0-118">Genom att ange den **StartingPosition** till **CenterScreen**, du automatiskt visar formuläret mitt på skärmen varje gång den läses in.</span><span class="sxs-lookup"><span data-stu-id="6d0b0-118">By setting the **StartingPosition** to **CenterScreen**, you’re automatically displaying the form in the middle of the screen each time it loads.</span></span>

```powershell
$form.Text = 'Select a Date'
$form.Size = New-Object Drawing.Size @(243,230)
$form.StartPosition = 'CenterScreen'
```

<span data-ttu-id="6d0b0-119">Sedan skapar och sedan lägga till en kalenderkontroll i formuläret.</span><span class="sxs-lookup"><span data-stu-id="6d0b0-119">Next, create and then add a calendar control in your form.</span></span> <span data-ttu-id="6d0b0-120">I det här exemplet är den aktuella dagen inte markerat eller inringade.</span><span class="sxs-lookup"><span data-stu-id="6d0b0-120">In this example, the current day is not highlighted or circled.</span></span> <span data-ttu-id="6d0b0-121">Användarna kan välja endast en dag i kalendern i taget.</span><span class="sxs-lookup"><span data-stu-id="6d0b0-121">Users can select only one day on the calendar at one time.</span></span>

```powershell
$calendar = New-Object System.Windows.Forms.MonthCalendar
$calendar.ShowTodayCircle = $false
$calendar.MaxSelectionCount = 1
$form.Controls.Add($calendar)
```

<span data-ttu-id="6d0b0-122">Skapa sedan en **OK** knappen för formuläret.</span><span class="sxs-lookup"><span data-stu-id="6d0b0-122">Next, create an **OK** button for your form.</span></span> <span data-ttu-id="6d0b0-123">Ange storlek och beteendet för den **OK** knappen.</span><span class="sxs-lookup"><span data-stu-id="6d0b0-123">Specify the size and behavior of the **OK** button.</span></span> <span data-ttu-id="6d0b0-124">I det här exemplet är knappen positionen 165 pixlar från formulärets övre kant och 38 pixlar från den vänstra kanten.</span><span class="sxs-lookup"><span data-stu-id="6d0b0-124">In this example, the button position is 165 pixels from the form’s top edge, and 38 pixels from the left edge.</span></span> <span data-ttu-id="6d0b0-125">Knappen höjden är 23 bildpunkter, medan den knapp längden är 75 bildpunkter.</span><span class="sxs-lookup"><span data-stu-id="6d0b0-125">The button height is 23 pixels, while the button length is 75 pixels.</span></span> <span data-ttu-id="6d0b0-126">Skriptet använder fördefinierade Windows Forms-typer för att fastställa knappen beteenden.</span><span class="sxs-lookup"><span data-stu-id="6d0b0-126">The script uses predefined Windows Forms types to determine the button behaviors.</span></span>

```powershell
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(38,165)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

<span data-ttu-id="6d0b0-127">På samma sätt kan du skapa en **Avbryt** knappen.</span><span class="sxs-lookup"><span data-stu-id="6d0b0-127">Similarly, you create a **Cancel** button.</span></span> <span data-ttu-id="6d0b0-128">Den **Avbryt** knappen är 165 bildpunkter uppifrån, men 113 bildpunkter från den vänstra kanten av fönstret.</span><span class="sxs-lookup"><span data-stu-id="6d0b0-128">The **Cancel** button is 165 pixels from the top, but 113 pixels from the left edge of the window.</span></span>

```powershell
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(113,165)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

<span data-ttu-id="6d0b0-129">Ange den **Topmost** egenskap **$true** att tvinga den tidsperioden för att öppna ovanpå andra fönster och dialogrutor.</span><span class="sxs-lookup"><span data-stu-id="6d0b0-129">Set the **Topmost** property to **$true** to force the window to open atop other open windows and dialog boxes.</span></span>

```powershell
$form.Topmost = $true
```

<span data-ttu-id="6d0b0-130">Lägg till följande rad med kod för att visa formuläret i Windows.</span><span class="sxs-lookup"><span data-stu-id="6d0b0-130">Add the following line of code to display the form in Windows.</span></span>

```powershell
$result = $form.ShowDialog()
```

<span data-ttu-id="6d0b0-131">Koden i den **om** block instruerar Windows vad som ska göras med formuläret när användare väljer en dag i kalendern och klicka sedan på den **OK** knapp eller genom att trycka på den **RETUR** nyckeln.</span><span class="sxs-lookup"><span data-stu-id="6d0b0-131">Finally, the code inside the **If** block instructs Windows what to do with the form after users select a day on the calendar, and then click the **OK** button or press the **Enter** key.</span></span> <span data-ttu-id="6d0b0-132">Windows PowerShell visas det valda datumet för användarna.</span><span class="sxs-lookup"><span data-stu-id="6d0b0-132">Windows PowerShell displays the selected date to users.</span></span>

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

## <a name="see-also"></a><span data-ttu-id="6d0b0-133">Se även</span><span class="sxs-lookup"><span data-stu-id="6d0b0-133">See Also</span></span>

- [<span data-ttu-id="6d0b0-134">Hey Scripting Guy: Varför exemplen PowerShell-Gränssnittet fungerar inte?</span><span class="sxs-lookup"><span data-stu-id="6d0b0-134">Hey Scripting Guy:  Why don’t these PowerShell GUI examples work?</span></span>](https://go.microsoft.com/fwlink/?LinkId=506644)
- [<span data-ttu-id="6d0b0-135">GitHub: Dave Wyatt WinFormsExampleUpdates</span><span class="sxs-lookup"><span data-stu-id="6d0b0-135">GitHub: Dave Wyatt's WinFormsExampleUpdates</span></span>](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [<span data-ttu-id="6d0b0-136">Windows PowerShell veckans tips: skapa en grafisk datumväljare</span><span class="sxs-lookup"><span data-stu-id="6d0b0-136">Windows PowerShell Tip of the Week:  Creating a Graphical Date Picker</span></span>](https://technet.microsoft.com/library/ff730942.aspx)