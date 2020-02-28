---
ms.date: 06/05/2017
keywords: PowerShell, cmdlet
title: Skapa en grafisk datumväljare
ms.openlocfilehash: b748e301b24ed643488079b547e2da1a5a7a6551
ms.sourcegitcommit: 0a3f9945d52e963e9cba2538ffb33e42156e1395
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/27/2020
ms.locfileid: "77706145"
---
# <a name="creating-a-graphical-date-picker"></a><span data-ttu-id="27f9e-103">Skapa en grafisk datumväljare</span><span class="sxs-lookup"><span data-stu-id="27f9e-103">Creating a Graphical Date Picker</span></span>

<span data-ttu-id="27f9e-104">Använd Windows PowerShell 3,0 och senare versioner för att skapa ett formulär med en grafisk, kalender typ kontroll som låter användarna välja en dag i månaden.</span><span class="sxs-lookup"><span data-stu-id="27f9e-104">Use Windows PowerShell 3.0 and later releases to create a form with a graphical, calendar-style control that lets users select a day of the month.</span></span>

## <a name="create-a-graphical-date-picker-control"></a><span data-ttu-id="27f9e-105">Skapa en grafisk kontroll för datum väljare</span><span class="sxs-lookup"><span data-stu-id="27f9e-105">Create a graphical date-picker control</span></span>

<span data-ttu-id="27f9e-106">Kopiera och klistra in följande i Windows PowerShell ISE och spara det sedan som ett Windows PowerShell-skript (. ps1).</span><span class="sxs-lookup"><span data-stu-id="27f9e-106">Copy and then paste the following into Windows PowerShell ISE, and then save it as a Windows PowerShell script (.ps1).</span></span>

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

$okButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 38, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'OK'
    DialogResult = [Windows.Forms.DialogResult]::OK
}
$form.AcceptButton = $okButton
$form.Controls.Add($okButton)

$cancelButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 113, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'Cancel'
    DialogResult = [Windows.Forms.DialogResult]::Cancel
}
$form.CancelButton = $cancelButton
$form.Controls.Add($cancelButton)

$result = $form.ShowDialog()

if ($result -eq [Windows.Forms.DialogResult]::OK) {
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

<span data-ttu-id="27f9e-107">Skriptet börjar genom att läsa in två .NET Framework klasser: **system. Drawing** och **system. Windows. Forms**.</span><span class="sxs-lookup"><span data-stu-id="27f9e-107">The script begins by loading two .NET Framework classes: **System.Drawing** and **System.Windows.Forms**.</span></span> <span data-ttu-id="27f9e-108">Sedan startar du en ny instans av klassen **Windows. Forms. Forms**i .NET Framework. Det innehåller ett tomt formulär eller fönster som du kan börja lägga till kontroller i.</span><span class="sxs-lookup"><span data-stu-id="27f9e-108">You then start a new instance of the .NET Framework class **Windows.Forms.Form**; that provides a blank form or window to which you can start adding controls.</span></span>

```powershell
$form = New-Object Windows.Forms.Form -Property @{
    StartPosition = [Windows.Forms.FormStartPosition]::CenterScreen
    Size          = New-Object Drawing.Size 243, 230
    Text          = 'Select a Date'
    Topmost       = $true
}
```

<span data-ttu-id="27f9e-109">I det här exemplet tilldelas värden till fyra egenskaper för den här klassen med **egenskapen Property** och hash.</span><span class="sxs-lookup"><span data-stu-id="27f9e-109">This example assigns values to four properties of this class by using the **Property** property and hashtable.</span></span>

1. <span data-ttu-id="27f9e-110">**Start position**: om du inte lägger till den här egenskapen väljer Windows en plats när formuläret öppnas.</span><span class="sxs-lookup"><span data-stu-id="27f9e-110">**StartPosition**: If you don’t add this property, Windows selects a location when the form is opened.</span></span> <span data-ttu-id="27f9e-111">Genom att ange den här egenskapen som **CenterScreen**visas formuläret automatiskt i mitten av skärmen varje gången det läses in.</span><span class="sxs-lookup"><span data-stu-id="27f9e-111">By setting this property to **CenterScreen**, you’re automatically displaying the form in the middle of the screen each time it loads.</span></span>

2. <span data-ttu-id="27f9e-112">**Storlek**: det här är storleken på formuläret, i bild punkter.</span><span class="sxs-lookup"><span data-stu-id="27f9e-112">**Size**: This is the size of the form, in pixels.</span></span>
   <span data-ttu-id="27f9e-113">Föregående skript skapar ett formulär som är 243 bild punkter brett med 230 pixlar högt.</span><span class="sxs-lookup"><span data-stu-id="27f9e-113">The preceding script creates a form that’s 243 pixels wide by 230 pixels tall.</span></span>

3. <span data-ttu-id="27f9e-114">**Text**: detta blir rubriken för fönstret.</span><span class="sxs-lookup"><span data-stu-id="27f9e-114">**Text**: This becomes the title of the window.</span></span>

4. <span data-ttu-id="27f9e-115">**Översta**: genom att ange den här egenskapen till `$true`, kan du tvinga fönstret att öppna ovanpå andra öppna fönster och dialog rutor.</span><span class="sxs-lookup"><span data-stu-id="27f9e-115">**Topmost**: By setting this property to `$true`, you can force the window to open atop other open windows and dialog boxes.</span></span>

<span data-ttu-id="27f9e-116">Skapa sedan och Lägg till en kalender kontroll i formuläret.</span><span class="sxs-lookup"><span data-stu-id="27f9e-116">Next, create and then add a calendar control in your form.</span></span>
<span data-ttu-id="27f9e-117">I det här exemplet är den aktuella dagen inte markerad eller inringad.</span><span class="sxs-lookup"><span data-stu-id="27f9e-117">In this example, the current day is not highlighted or circled.</span></span>
<span data-ttu-id="27f9e-118">Användarna kan bara välja en dag i kalendern i taget.</span><span class="sxs-lookup"><span data-stu-id="27f9e-118">Users can select only one day on the calendar at one time.</span></span>

```powershell
$calendar = New-Object Windows.Forms.MonthCalendar -Property @{
    ShowTodayCircle   = $false
    MaxSelectionCount = 1
}
$form.Controls.Add($calendar)
```

<span data-ttu-id="27f9e-119">Skapa sedan en **OK** -knapp för formuläret.</span><span class="sxs-lookup"><span data-stu-id="27f9e-119">Next, create an **OK** button for your form.</span></span> <span data-ttu-id="27f9e-120">Ange storlek och beteende för **OK** -knappen.</span><span class="sxs-lookup"><span data-stu-id="27f9e-120">Specify the size and behavior of the **OK** button.</span></span> <span data-ttu-id="27f9e-121">I det här exemplet är knapp positionen 165 bild punkter från formulärets övre kant och 38 pixlar från den vänstra kanten.</span><span class="sxs-lookup"><span data-stu-id="27f9e-121">In this example, the button position is 165 pixels from the form’s top edge, and 38 pixels from the left edge.</span></span> <span data-ttu-id="27f9e-122">Knapp höjden är 23 bild punkter, medan knapp längden är 75 bild punkter.</span><span class="sxs-lookup"><span data-stu-id="27f9e-122">The button height is 23 pixels, while the button length is 75 pixels.</span></span> <span data-ttu-id="27f9e-123">Skriptet använder fördefinierade Windows Forms typer för att fastställa knapp beteenden.</span><span class="sxs-lookup"><span data-stu-id="27f9e-123">The script uses predefined Windows Forms types to determine the button behaviors.</span></span>

```powershell
$okButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 38, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'OK'
    DialogResult = [Windows.Forms.DialogResult]::OK
}
$form.AcceptButton = $okButton
$form.Controls.Add($okButton)
```

<span data-ttu-id="27f9e-124">På samma sätt skapar du en **Avbryt** -knapp.</span><span class="sxs-lookup"><span data-stu-id="27f9e-124">Similarly, you create a **Cancel** button.</span></span>
<span data-ttu-id="27f9e-125">Knappen **Avbryt** är 165 bild punkter ovanifrån, men 113 pixlar från den vänstra kanten av fönstret.</span><span class="sxs-lookup"><span data-stu-id="27f9e-125">The **Cancel** button is 165 pixels from the top, but 113 pixels from the left edge of the window.</span></span>

```powershell
$cancelButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 113, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'Cancel'
    DialogResult = [Windows.Forms.DialogResult]::Cancel
}
$form.CancelButton = $cancelButton
$form.Controls.Add($cancelButton)
```

<span data-ttu-id="27f9e-126">Lägg till följande kodrad för att visa formuläret i Windows.</span><span class="sxs-lookup"><span data-stu-id="27f9e-126">Add the following line of code to display the form in Windows.</span></span>

```powershell
$result = $form.ShowDialog()
```

<span data-ttu-id="27f9e-127">Slutligen instruerar koden inuti `if`-blocket Windows vad som ska göras med formuläret när användarna har valt en dag i kalendern. Klicka sedan på **OK** eller tryck på **RETUR** -tangenten.</span><span class="sxs-lookup"><span data-stu-id="27f9e-127">Finally, the code inside the `if` block instructs Windows what to do with the form after users select a day on the calendar, and then click the **OK** button or press the **Enter** key.</span></span> <span data-ttu-id="27f9e-128">Windows PowerShell visar det valda datumet för användarna.</span><span class="sxs-lookup"><span data-stu-id="27f9e-128">Windows PowerShell displays the selected date to users.</span></span>

```powershell
if ($result -eq [Windows.Forms.DialogResult]::OK) {
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

## <a name="see-also"></a><span data-ttu-id="27f9e-129">Se även</span><span class="sxs-lookup"><span data-stu-id="27f9e-129">See Also</span></span>

- [<span data-ttu-id="27f9e-130">GitHub: Dave Wyatt s WinFormsExampleUpdates</span><span class="sxs-lookup"><span data-stu-id="27f9e-130">GitHub: Dave Wyatt's WinFormsExampleUpdates</span></span>](https://github.com/dlwyatt/WinFormsExampleUpdates)
- <span data-ttu-id="27f9e-131">[Veckans Windows PowerShell-tips: skapa en grafisk datum väljare](/previous-versions/windows/it-pro/windows-powershell-1.0/ff730942(v=technet.10))</span><span class="sxs-lookup"><span data-stu-id="27f9e-131">[Windows PowerShell Tip of the Week:  Creating a Graphical Date Picker](/previous-versions/windows/it-pro/windows-powershell-1.0/ff730942(v=technet.10))</span></span>
