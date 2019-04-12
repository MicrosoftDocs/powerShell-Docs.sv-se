---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Skapa en grafisk datumväljare
ms.assetid: c1cb722c-41e9-4baa-be83-59b4653222e9
ms.openlocfilehash: d3b24af935e781a8a36fc346a6108baaed37b6db
ms.sourcegitcommit: 3f6002e7109373eda31cc65fc84d2600447cb7e9
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/11/2019
ms.locfileid: "59506809"
---
# <a name="creating-a-graphical-date-picker"></a><span data-ttu-id="d32fa-103">Skapa en grafisk datumväljare</span><span class="sxs-lookup"><span data-stu-id="d32fa-103">Creating a Graphical Date Picker</span></span>

<span data-ttu-id="d32fa-104">Använda Windows PowerShell 3.0 och senare versioner för att skapa ett formulär med en grafisk, kalender-style-kontroll som användaren kan välja en dag i månaden.</span><span class="sxs-lookup"><span data-stu-id="d32fa-104">Use Windows PowerShell 3.0 and later releases to create a form with a graphical, calendar-style control that lets users select a day of the month.</span></span>

## <a name="create-a-graphical-date-picker-control"></a><span data-ttu-id="d32fa-105">Skapa en grafisk datumväljare-kontroll</span><span class="sxs-lookup"><span data-stu-id="d32fa-105">Create a graphical date-picker control</span></span>

<span data-ttu-id="d32fa-106">Kopiera och klistra in följande i Windows PowerShell ISE och spara det som ett Windows PowerShell-skript (.ps1).</span><span class="sxs-lookup"><span data-stu-id="d32fa-106">Copy and then paste the following into Windows PowerShell ISE, and then save it as a Windows PowerShell script (.ps1).</span></span>

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object Windows.Forms.Form -Property @{
    StartPosition = [Windows.Forms.FormStartPosition]::CenterScreen
    Size          = New-Object Drawing.Size 243, 230
    Text          = 'Select a Date'
    Topmost       = $true
}

$calendar = New-Object Windows.Forms.MonthCalendar -Property @{
    ShowTodayCircle   = $false
    MaxSelectionCount = 1
}
$form.Controls.Add($calendar)

$OKButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 38, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'OK'
    DialogResult = [Windows.Forms.DialogResult]::OK
}
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)

$CancelButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 113, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'Cancel'
    DialogResult = [Windows.Forms.DialogResult]::Cancel
}
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)

$result = $form.ShowDialog()

if ($result -eq [Windows.Forms.DialogResult]::OK) {
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

<span data-ttu-id="d32fa-107">Skriptet börjar genom att läsa in två .NET Framework-klasser: **System.Drawing** och **System.Windows.Forms**.</span><span class="sxs-lookup"><span data-stu-id="d32fa-107">The script begins by loading two .NET Framework classes: **System.Drawing** and **System.Windows.Forms**.</span></span>
<span data-ttu-id="d32fa-108">Du startar sedan en ny instans av klassen .NET Framework **Windows.Forms.Form**; som innehåller ett tomt formulär eller fönster som du kan börja lägga till kontroller.</span><span class="sxs-lookup"><span data-stu-id="d32fa-108">You then start a new instance of the .NET Framework class **Windows.Forms.Form**; that provides a blank form or window to which you can start adding controls.</span></span>

```powershell
$form = New-Object Windows.Forms.Form -Property @{
    StartPosition = [Windows.Forms.FormStartPosition]::CenterScreen
    Size          = New-Object Drawing.Size 243, 230
    Text          = 'Select a Date'
    Topmost       = $true
}
```

<span data-ttu-id="d32fa-109">Det här exemplet tilldelar värden till fyra egenskaperna för den här klassen med hjälp av den **egenskapen** egenskap och hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="d32fa-109">This example assigns values to four properties of this class by using the **Property** property and hashtable.</span></span>

1. <span data-ttu-id="d32fa-110">**StartPosition**: Om du inte lägger till den här egenskapen, väljer en plats i Windows när formuläret öppnas.</span><span class="sxs-lookup"><span data-stu-id="d32fa-110">**StartPosition**: If you don’t add this property, Windows selects a location when the form is opened.</span></span>
   <span data-ttu-id="d32fa-111">Genom att ställa in den här egenskapen **CenterScreen**, du automatiskt visar formuläret mitt på skärmen varje gång den läses in.</span><span class="sxs-lookup"><span data-stu-id="d32fa-111">By setting this property to **CenterScreen**, you’re automatically displaying the form in the middle of the screen each time it loads.</span></span>

2. <span data-ttu-id="d32fa-112">**Storlek**: Det här är storleken på formuläret i bildpunkter.</span><span class="sxs-lookup"><span data-stu-id="d32fa-112">**Size**: This is the size of the form, in pixels.</span></span>
   <span data-ttu-id="d32fa-113">Det här skriptet skapar ett formulär som är 243 bildpunkter på bredden 230 pixlar hög.</span><span class="sxs-lookup"><span data-stu-id="d32fa-113">The preceding script creates a form that’s 243 pixels wide by 230 pixels tall.</span></span>

3. <span data-ttu-id="d32fa-114">**Text**: Detta blir titeln på fönstret.</span><span class="sxs-lookup"><span data-stu-id="d32fa-114">**Text**: This becomes the title of the window.</span></span>

4. <span data-ttu-id="d32fa-115">**Översta**: Genom att ställa in den här egenskapen `$true`, du kan tvinga fönstret för att öppna ovanpå andra fönster och dialogrutor.</span><span class="sxs-lookup"><span data-stu-id="d32fa-115">**Topmost**: By setting this property to `$true`, you can force the window to open atop other open windows and dialog boxes.</span></span>

<span data-ttu-id="d32fa-116">Sedan skapar och sedan lägga till en kalenderkontroll i formuläret.</span><span class="sxs-lookup"><span data-stu-id="d32fa-116">Next, create and then add a calendar control in your form.</span></span>
<span data-ttu-id="d32fa-117">I det här exemplet är den aktuella dagen inte markerat eller inringade.</span><span class="sxs-lookup"><span data-stu-id="d32fa-117">In this example, the current day is not highlighted or circled.</span></span>
<span data-ttu-id="d32fa-118">Användarna kan välja endast en dag i kalendern i taget.</span><span class="sxs-lookup"><span data-stu-id="d32fa-118">Users can select only one day on the calendar at one time.</span></span>

```powershell
$calendar = New-Object Windows.Forms.MonthCalendar -Property @{
    ShowTodayCircle   = $false
    MaxSelectionCount = 1
}
$form.Controls.Add($calendar)
```

<span data-ttu-id="d32fa-119">Skapa sedan en **OK** knappen för formuläret.</span><span class="sxs-lookup"><span data-stu-id="d32fa-119">Next, create an **OK** button for your form.</span></span>
<span data-ttu-id="d32fa-120">Ange storlek och beteendet för den **OK** knappen.</span><span class="sxs-lookup"><span data-stu-id="d32fa-120">Specify the size and behavior of the **OK** button.</span></span>
<span data-ttu-id="d32fa-121">I det här exemplet är knappen positionen 165 pixlar från formulärets övre kant och 38 pixlar från den vänstra kanten.</span><span class="sxs-lookup"><span data-stu-id="d32fa-121">In this example, the button position is 165 pixels from the form’s top edge, and 38 pixels from the left edge.</span></span>
<span data-ttu-id="d32fa-122">Knappen höjden är 23 bildpunkter, medan den knapp längden är 75 bildpunkter.</span><span class="sxs-lookup"><span data-stu-id="d32fa-122">The button height is 23 pixels, while the button length is 75 pixels.</span></span>
<span data-ttu-id="d32fa-123">Skriptet använder fördefinierade Windows Forms-typer för att fastställa knappen beteenden.</span><span class="sxs-lookup"><span data-stu-id="d32fa-123">The script uses predefined Windows Forms types to determine the button behaviors.</span></span>

```powershell
$OKButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 38, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'OK'
    DialogResult = [Windows.Forms.DialogResult]::OK
}
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

<span data-ttu-id="d32fa-124">På samma sätt kan du skapa en **Avbryt** knappen.</span><span class="sxs-lookup"><span data-stu-id="d32fa-124">Similarly, you create a **Cancel** button.</span></span>
<span data-ttu-id="d32fa-125">Den **Avbryt** knappen är 165 bildpunkter uppifrån, men 113 bildpunkter från den vänstra kanten av fönstret.</span><span class="sxs-lookup"><span data-stu-id="d32fa-125">The **Cancel** button is 165 pixels from the top, but 113 pixels from the left edge of the window.</span></span>

```powershell
$CancelButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 113, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'Cancel'
    DialogResult = [Windows.Forms.DialogResult]::Cancel
}
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

<span data-ttu-id="d32fa-126">Lägg till följande rad med kod för att visa formuläret i Windows.</span><span class="sxs-lookup"><span data-stu-id="d32fa-126">Add the following line of code to display the form in Windows.</span></span>

```powershell
$result = $form.ShowDialog()
```

<span data-ttu-id="d32fa-127">Koden i den `if` block instruerar Windows vad som ska göras med formuläret när användare väljer en dag i kalendern och klicka sedan på den **OK** knapp eller genom att trycka på den **RETUR** nyckel.</span><span class="sxs-lookup"><span data-stu-id="d32fa-127">Finally, the code inside the `if` block instructs Windows what to do with the form after users select a day on the calendar, and then click the **OK** button or press the **Enter** key.</span></span>
<span data-ttu-id="d32fa-128">Windows PowerShell visas det valda datumet för användarna.</span><span class="sxs-lookup"><span data-stu-id="d32fa-128">Windows PowerShell displays the selected date to users.</span></span>

```powershell
if ($result -eq [Windows.Forms.DialogResult]::OK) {
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

## <a name="see-also"></a><span data-ttu-id="d32fa-129">Se även</span><span class="sxs-lookup"><span data-stu-id="d32fa-129">See Also</span></span>

- [<span data-ttu-id="d32fa-130">Hej skriptdoktorn:  Varför fungerar inte dessa PowerShell-GUI-exempel?</span><span class="sxs-lookup"><span data-stu-id="d32fa-130">Hey Scripting Guy:  Why don’t these PowerShell GUI examples work?</span></span>](https://go.microsoft.com/fwlink/?LinkId=506644)
- [<span data-ttu-id="d32fa-131">GitHub: Dave Wyatt WinFormsExampleUpdates</span><span class="sxs-lookup"><span data-stu-id="d32fa-131">GitHub: Dave Wyatt's WinFormsExampleUpdates</span></span>](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [<span data-ttu-id="d32fa-132">Windows PowerShell-tips i veckan:  Skapa en grafisk datumväljare</span><span class="sxs-lookup"><span data-stu-id="d32fa-132">Windows PowerShell Tip of the Week:  Creating a Graphical Date Picker</span></span>](https://technet.microsoft.com/library/ff730942.aspx)