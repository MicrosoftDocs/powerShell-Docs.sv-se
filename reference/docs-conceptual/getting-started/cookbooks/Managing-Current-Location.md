---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Hantera aktuell plats
ms.assetid: a9f9e7a7-3ea8-47d3-bbb4-6e437f6d4a4a
ms.openlocfilehash: 8d529bf4a85553b95a9cab2739016859662486f2
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="managing-current-location"></a><span data-ttu-id="eb879-103">Hantera aktuell plats</span><span class="sxs-lookup"><span data-stu-id="eb879-103">Managing Current Location</span></span>

<span data-ttu-id="eb879-104">När du navigerar i mappen System i Utforskaren, har vanligtvis en specifik plats i fungerande - nämligen den aktuella öppna mappen.</span><span class="sxs-lookup"><span data-stu-id="eb879-104">When navigating folder systems in File Explorer, you usually have a specific working location - namely, the current open folder.</span></span> <span data-ttu-id="eb879-105">Objekt i den aktuella mappen kan ändras genom att klicka på dem enkelt.</span><span class="sxs-lookup"><span data-stu-id="eb879-105">Items in the current folder can be manipulated easily by clicking them.</span></span> <span data-ttu-id="eb879-106">För kommandoradsverktyget gränssnitt, till exempel Cmd.exe, när du är i samma mapp som en viss fil, kan du öppna den genom att ange ett relativt kort namn i stället för att behöva ange hela sökvägen till filen.</span><span class="sxs-lookup"><span data-stu-id="eb879-106">For command-line interfaces such as Cmd.exe, when you are in the same folder as a particular file, you can access it by specifying a relatively short name, rather than needing to specify the entire path to the file.</span></span> <span data-ttu-id="eb879-107">Den aktuella katalogen kallas arbetskatalogen.</span><span class="sxs-lookup"><span data-stu-id="eb879-107">The current directory is called the working directory.</span></span>

<span data-ttu-id="eb879-108">Windows PowerShell använder substantivet **plats** att referera till arbetskatalogen, och implementerar en familj av cmdletar för att granska och ändra din plats.</span><span class="sxs-lookup"><span data-stu-id="eb879-108">Windows PowerShell uses the noun **Location** to refer to the working directory, and implements a family of cmdlets to examine and manipulate your location.</span></span>

### <a name="getting-your-current-location-get-location"></a><span data-ttu-id="eb879-109">Hämta din aktuella plats (Get-plats)</span><span class="sxs-lookup"><span data-stu-id="eb879-109">Getting Your Current Location (Get-Location)</span></span>

<span data-ttu-id="eb879-110">För att fastställa sökvägen för din aktuella katalogplats, ange den **Get-plats** kommando:</span><span class="sxs-lookup"><span data-stu-id="eb879-110">To determine the path of your current directory location, enter the **Get-Location** command:</span></span>

```
PS> Get-Location
Path
----
C:\Documents and Settings\PowerUser
```

> [!NOTE]
> <span data-ttu-id="eb879-111">Get-plats-cmdlet liknar den **pwd** i BASH-gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="eb879-111">The Get-Location cmdlet is similar to the **pwd** command in the BASH shell.</span></span> <span data-ttu-id="eb879-112">Cmdlet Set-Location liknar den **cd** i Cmd.exe.</span><span class="sxs-lookup"><span data-stu-id="eb879-112">The Set-Location cmdlet is similar to the **cd** command in Cmd.exe.</span></span>

### <a name="setting-your-current-location-set-location"></a><span data-ttu-id="eb879-113">Ange din aktuella plats (Set-plats)</span><span class="sxs-lookup"><span data-stu-id="eb879-113">Setting Your Current Location (Set-Location)</span></span>

<span data-ttu-id="eb879-114">Den **Get-plats** kommandot används med den **Set-Location** kommando.</span><span class="sxs-lookup"><span data-stu-id="eb879-114">The **Get-Location** command is used with the **Set-Location** command.</span></span> <span data-ttu-id="eb879-115">Den **Set-Location** kommandot kan du ange den aktuella directory-platsen.</span><span class="sxs-lookup"><span data-stu-id="eb879-115">The **Set-Location** command allows you to specify your current directory location.</span></span>

```powershell
Set-Location -Path C:\Windows
```

<span data-ttu-id="eb879-116">När du har angett kommandot ser du att du inte har fått någon direkt feedback om effekten av kommandot.</span><span class="sxs-lookup"><span data-stu-id="eb879-116">After you enter the command, you will notice that you do not receive any direct feedback about the effect of the command.</span></span> <span data-ttu-id="eb879-117">De flesta Windows PowerShell-kommandon som utför en åtgärd resultat lite eller ingen eftersom utdata inte är alltid praktiskt.</span><span class="sxs-lookup"><span data-stu-id="eb879-117">Most Windows PowerShell commands that perform an action produce little or no output because the output is not always useful.</span></span> <span data-ttu-id="eb879-118">Att verifiera att en lyckad katalogändring uppstod när du anger den **Set-Location** kommandot, innehåller den **- PassThru** parameter när du anger den **Set-Location**kommando:</span><span class="sxs-lookup"><span data-stu-id="eb879-118">To verify that a successful directory change has occurred when you enter the **Set-Location** command, include the **-PassThru** parameter when you enter the **Set-Location** command:</span></span>

```
PS> Set-Location -Path C:\Windows -PassThru

Path
----
C:\WINDOWS
```

<span data-ttu-id="eb879-119">Den **- PassThru** parameter som kan användas med många uppsättning kommandon i Windows PowerShell för att returnera information om resultatet i fall där det finns inga standardutdata.</span><span class="sxs-lookup"><span data-stu-id="eb879-119">The **-PassThru** parameter can be used with many Set commands in Windows PowerShell to return information about the result in cases in which there is no default output.</span></span>

<span data-ttu-id="eb879-120">Du kan ange sökvägar i förhållande till din aktuella plats på samma sätt som du skulle i de flesta UNIX- och Windows kommandot gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="eb879-120">You can specify paths relative to your current location in the same way as you would in most UNIX and Windows command shells.</span></span> <span data-ttu-id="eb879-121">I standard notation för relativa sökvägar, en period (**.**) representerar den aktuella mappen och en dubbelt period (**...** ) representerar den överordnade katalogen i din aktuella plats.</span><span class="sxs-lookup"><span data-stu-id="eb879-121">In standard notation for relative paths, a period (**.**)represents your current folder, and a doubled period (**..**) represents the parent directory of your current location.</span></span>

<span data-ttu-id="eb879-122">Om du befinner dig i till exempel den **C:\\Windows** mapp, en period (**.**) representerar **C:\\Windows** och punkter (**...** ) representerar **C:**.</span><span class="sxs-lookup"><span data-stu-id="eb879-122">For example, if you are in the **C:\\Windows** folder, a period (**.**)represents **C:\\Windows** and double periods (**..**) represent **C:**.</span></span> <span data-ttu-id="eb879-123">Du kan ändra från den aktuella platsen till roten på enhet C: genom att skriva:</span><span class="sxs-lookup"><span data-stu-id="eb879-123">You can change from your current location to the root of the C: drive by typing:</span></span>

```
PS> Set-Location -Path .. -PassThru

Path
----
C:\
```

<span data-ttu-id="eb879-124">Samma teknik som fungerar på Windows PowerShell-enheter som inte enheter, exempelvis **HKLM:**.</span><span class="sxs-lookup"><span data-stu-id="eb879-124">The same technique works on Windows PowerShell drives that are not file system drives, such as **HKLM:**.</span></span> <span data-ttu-id="eb879-125">Du kan ange plats och HKLM\\programvarunyckel i registret genom att skriva:</span><span class="sxs-lookup"><span data-stu-id="eb879-125">You can set your location to the HKLM\\Software key in the registry by typing:</span></span>

```
PS> Set-Location -Path HKLM:\SOFTWARE -PassThru

Path
----
HKLM:\SOFTWARE
```

<span data-ttu-id="eb879-126">Du kan sedan ändra katalogen till den överordnade katalogen som är roten till Windows PowerShell HKLM:-enheten med hjälp av en relativ sökväg:</span><span class="sxs-lookup"><span data-stu-id="eb879-126">You can then change the directory location to the parent directory, which is the root of the Windows PowerShell HKLM: drive, by using a relative path:</span></span>

```
PS> Set-Location -Path .. -PassThru

Path
----
HKLM:\
```

<span data-ttu-id="eb879-127">Du kan skriva Set-Location eller använda någon av de inbyggda Windows PowerShell-alias för Set-Location (cd, chdir, sl).</span><span class="sxs-lookup"><span data-stu-id="eb879-127">You can type Set-Location or use any of the built-in Windows PowerShell aliases for Set-Location (cd, chdir, sl).</span></span> <span data-ttu-id="eb879-128">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="eb879-128">For example:</span></span>

```powershell
cd -Path C:\Windows
```

```powershell
chdir -Path .. -PassThru
```

```powershell
sl -Path HKLM:\SOFTWARE -PassThru
```

### <a name="saving-and-recalling-recent-locations-push-location-and-pop-location"></a><span data-ttu-id="eb879-129">Spara och återkalla senaste platser (Push- och Pop-plats)</span><span class="sxs-lookup"><span data-stu-id="eb879-129">Saving and Recalling Recent Locations (Push-Location and Pop-Location)</span></span>

<span data-ttu-id="eb879-130">När du ändrar platser, är det bra att hålla reda på var du har varit och för att kunna återgå till föregående plats.</span><span class="sxs-lookup"><span data-stu-id="eb879-130">When changing locations, it is helpful to keep track of where you have been and to be able to return to your previous location.</span></span> <span data-ttu-id="eb879-131">Den **Push-plats** cmdlet i Windows PowerShell skapar en ordnad historik (en ”stack”) för katalogsökvägar där du har, och du kan gå tillbaka historiken för directory-sökvägar med hjälp av den kompletterande  **POP-plats** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="eb879-131">The **Push-Location** cmdlet in Windows PowerShell creates a ordered history (a "stack") of directory paths where you have been, and you can step back through the history of directory paths by using the complementary **Pop-Location** cmdlet.</span></span>

<span data-ttu-id="eb879-132">Till exempel startas Windows PowerShell normalt i användarens hemkatalog.</span><span class="sxs-lookup"><span data-stu-id="eb879-132">For example, Windows PowerShell typically starts in the user's home directory.</span></span>

```
PS> Get-Location

Path
----
C:\Documents and Settings\PowerUser
```

> [!NOTE]
> <span data-ttu-id="eb879-133">Ordet *stack* har en särskild innebörd i många programmeringsspråk inställningar, inklusive .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="eb879-133">The word *stack* has a special meaning in many programming settings, including .NET Framework.</span></span> <span data-ttu-id="eb879-134">Det sista objektet som du lägger till stacken är det första objektet som du kan inaktivera stacken som en fysisk stack objekt.</span><span class="sxs-lookup"><span data-stu-id="eb879-134">Like a physical stack of items, the last item you put onto the stack is the first item that you can pull off the stack.</span></span> <span data-ttu-id="eb879-135">Lägga till ett objekt i en stack kallas colloquially ”push-installation” objektet till stacken.</span><span class="sxs-lookup"><span data-stu-id="eb879-135">Adding an item to a stack is colloquially known as "pushing" the item onto the stack.</span></span> <span data-ttu-id="eb879-136">Dra ett objekt från bufferten kallas colloquially ”poppar” objektet från stacken.</span><span class="sxs-lookup"><span data-stu-id="eb879-136">Pulling an item off the stack is colloquially known as "popping" the item off the stack.</span></span>

<span data-ttu-id="eb879-137">För att push-den aktuella platsen till stacken och gå sedan till mappen lokala inställningar, skriver du:</span><span class="sxs-lookup"><span data-stu-id="eb879-137">To push the current location onto the stack, and then move to the Local Settings folder, type:</span></span>

```powershell
Push-Location -Path "Local Settings"
```

<span data-ttu-id="eb879-138">Du kan sedan push lokala inställningar plats i bufferten och och gå till Temp-mappen genom att skriva:</span><span class="sxs-lookup"><span data-stu-id="eb879-138">You can then push the Local Settings location onto the stack and and move to the Temp folder by typing:</span></span>

```powershell
Push-Location -Path Temp
```

<span data-ttu-id="eb879-139">Du kan kontrollera att du har ändrat kataloger genom att ange den **Get-plats** kommando:</span><span class="sxs-lookup"><span data-stu-id="eb879-139">You can verify that you changed directories by entering the **Get-Location** command:</span></span>

```
PS> Get-Location

Path
----
C:\Documents and Settings\PowerUser\Local Settings\Temp
```

<span data-ttu-id="eb879-140">Du kan sedan öppna tillbaka till den senast besökta katalogen genom att ange den **Pop plats** och kontrollera ändringen genom att ange den **Get-plats** kommando:</span><span class="sxs-lookup"><span data-stu-id="eb879-140">You can then pop back into the most recently visited directory by entering the **Pop-Location** command, and verify the change by entering the **Get-Location** command:</span></span>

```
PS> Pop-Location
PS> Get-Location

Path
----
C:\Documents and Settings\me\Local Settings
```

<span data-ttu-id="eb879-141">Precis som med den **Set-Location** cmdlet, som du kan inkludera den **- PassThru** parameter när du anger den **Pop plats** för att visa den katalog som du angav:</span><span class="sxs-lookup"><span data-stu-id="eb879-141">Just as with the **Set-Location** cmdlet, you can include the **-PassThru** parameter when you enter the **Pop-Location** cmdlet to display the directory that you entered:</span></span>

```
PS> Pop-Location -PassThru

Path
----
C:\Documents and Settings\PowerUser
```

<span data-ttu-id="eb879-142">Du kan också använda cmdlet: ar för plats med nätverkssökvägar.</span><span class="sxs-lookup"><span data-stu-id="eb879-142">You can also use the Location cmdlets with network paths.</span></span> <span data-ttu-id="eb879-143">Om du har en server med namnet FS01 med en resurs med namnet Public, kan du ändra din plats genom att skriva</span><span class="sxs-lookup"><span data-stu-id="eb879-143">If you have a server named FS01 with an share named Public, you can change your location by typing</span></span>

```powershell
Set-Location \\FS01\Public
```

<span data-ttu-id="eb879-144">eller</span><span class="sxs-lookup"><span data-stu-id="eb879-144">or</span></span>

```powershell
Push-Location \\FS01\Public
```

<span data-ttu-id="eb879-145">Du kan använda den **Push-plats** och **Set-Location** kommandon för att ändra platsen till en tillgänglig enhet.</span><span class="sxs-lookup"><span data-stu-id="eb879-145">You can use the **Push-Location** and **Set-Location** commands to change the location to any available drive.</span></span> <span data-ttu-id="eb879-146">Till exempel om du har en lokal CD-ROM-enhet med enhetsbeteckningen D som innehåller en CD, du kan ändra platsen från CD-enheten genom att ange den **Set-Location D:** kommando.</span><span class="sxs-lookup"><span data-stu-id="eb879-146">For example, if you have a local CD-ROM drive with drive letter D that contains a data CD, you can change the location to the CD drive by entering the **Set-Location D:** command.</span></span>

<span data-ttu-id="eb879-147">Om enheten är tom, får du följande felmeddelande:</span><span class="sxs-lookup"><span data-stu-id="eb879-147">If the drive is empty, you will get the following error message:</span></span>

```
PS> Set-Location D:
Set-Location : Cannot find path 'D:\' because it does not exist.
```

<span data-ttu-id="eb879-148">När du använder ett kommandoradsgränssnitt, är det inte praktiskt att använda Utforskaren för att undersöka tillgängliga fysiska enheter.</span><span class="sxs-lookup"><span data-stu-id="eb879-148">When you are using a command-line interface, it is not convenient to use File Explorer to examine the available physical drives.</span></span> <span data-ttu-id="eb879-149">Dessutom innehåller Utforskaren inte alla enheter som Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="eb879-149">Also, File Explorer would not show you the all of the Windows PowerShell drives.</span></span> <span data-ttu-id="eb879-150">Windows PowerShell innehåller en uppsättning kommandon för att hantera enheter med Windows PowerShell och vi pratar om dessa nästa.</span><span class="sxs-lookup"><span data-stu-id="eb879-150">Windows PowerShell provides a set of commands for manipulating Windows PowerShell drives, and we will talk about these next.</span></span>