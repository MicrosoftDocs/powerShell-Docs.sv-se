---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Hantera aktuell plats
description: PowerShell använder platsen Substantiv för att referera till arbets katalogen och implementerar en serie cmdlets för att granska och ändra din plats.
ms.openlocfilehash: 0ce9ed1269921233b0d6b07da832c12e159a84dc
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500478"
---
# <a name="managing-current-location"></a><span data-ttu-id="63ede-104">Hantera aktuell plats</span><span class="sxs-lookup"><span data-stu-id="63ede-104">Managing Current Location</span></span>

<span data-ttu-id="63ede-105">När du navigerar i mappfönster i Utforskaren har du vanligt vis en speciell arbets plats, nämligen den aktuella öppna mappen.</span><span class="sxs-lookup"><span data-stu-id="63ede-105">When navigating folder systems in File Explorer, you usually have a specific working location - namely, the current open folder.</span></span> <span data-ttu-id="63ede-106">Objekt i den aktuella mappen kan ändras enkelt genom att du klickar på dem.</span><span class="sxs-lookup"><span data-stu-id="63ede-106">Items in the current folder can be manipulated easily by clicking them.</span></span> <span data-ttu-id="63ede-107">För kommando rads gränssnitt som Cmd.exe, när du befinner dig i samma mapp som en viss fil, kan du komma åt den genom att ange ett relativt kort namn, i stället för att behöva ange hela sökvägen till filen.</span><span class="sxs-lookup"><span data-stu-id="63ede-107">For command-line interfaces such as Cmd.exe, when you are in the same folder as a particular file, you can access it by specifying a relatively short name, rather than needing to specify the entire path to the file.</span></span> <span data-ttu-id="63ede-108">Den aktuella katalogen kallas arbets katalog.</span><span class="sxs-lookup"><span data-stu-id="63ede-108">The current directory is called the working directory.</span></span>

<span data-ttu-id="63ede-109">Windows PowerShell använder **platsen** Substantiv för att referera till arbets katalogen och implementerar en serie cmdlets för att granska och ändra din plats.</span><span class="sxs-lookup"><span data-stu-id="63ede-109">Windows PowerShell uses the noun **Location** to refer to the working directory, and implements a family of cmdlets to examine and manipulate your location.</span></span>

## <a name="getting-your-current-location-get-location"></a><span data-ttu-id="63ede-110">Hämta din aktuella plats (Get-location)</span><span class="sxs-lookup"><span data-stu-id="63ede-110">Getting Your Current Location (Get-Location)</span></span>

<span data-ttu-id="63ede-111">För att fastställa sökvägen till din nuvarande katalog plats, ange kommandot **Get-location** :</span><span class="sxs-lookup"><span data-stu-id="63ede-111">To determine the path of your current directory location, enter the **Get-Location** command:</span></span>

```
PS> Get-Location
Path
----
C:\Documents and Settings\PowerUser
```

> [!NOTE]
> <span data-ttu-id="63ede-112">Get-Location cmdlet liknar **PWD** -kommandot i bash-gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="63ede-112">The Get-Location cmdlet is similar to the **pwd** command in the BASH shell.</span></span> <span data-ttu-id="63ede-113">Set-Location cmdlet liknar kommandot **CD** i Cmd.exe.</span><span class="sxs-lookup"><span data-stu-id="63ede-113">The Set-Location cmdlet is similar to the **cd** command in Cmd.exe.</span></span>

## <a name="setting-your-current-location-set-location"></a><span data-ttu-id="63ede-114">Ange din aktuella plats (Ange plats)</span><span class="sxs-lookup"><span data-stu-id="63ede-114">Setting Your Current Location (Set-Location)</span></span>

<span data-ttu-id="63ede-115">Kommandot **Get-location** används med kommandot **set-location** .</span><span class="sxs-lookup"><span data-stu-id="63ede-115">The **Get-Location** command is used with the **Set-Location** command.</span></span> <span data-ttu-id="63ede-116">Med kommandot **set-location** kan du ange din nuvarande katalog plats.</span><span class="sxs-lookup"><span data-stu-id="63ede-116">The **Set-Location** command allows you to specify your current directory location.</span></span>

```powershell
Set-Location -Path C:\Windows
```

<span data-ttu-id="63ede-117">När du har angett kommandot ser du att du inte får någon direkt feedback om kommandots effekter.</span><span class="sxs-lookup"><span data-stu-id="63ede-117">After you enter the command, you will notice that you do not receive any direct feedback about the effect of the command.</span></span> <span data-ttu-id="63ede-118">De flesta Windows PowerShell-kommandon som utför en åtgärd ger lite eller inga utdata eftersom utdata inte alltid är användbara.</span><span class="sxs-lookup"><span data-stu-id="63ede-118">Most Windows PowerShell commands that perform an action produce little or no output because the output is not always useful.</span></span> <span data-ttu-id="63ede-119">För att kontrol lera att en lyckad katalog ändring har inträffat när du anger kommandot **set-location** , inkluderar du parametern **-Passthru** när du anger kommandot **set-location** :</span><span class="sxs-lookup"><span data-stu-id="63ede-119">To verify that a successful directory change has occurred when you enter the **Set-Location** command, include the **-PassThru** parameter when you enter the **Set-Location** command:</span></span>

```
PS> Set-Location -Path C:\Windows -PassThru

Path
----
C:\WINDOWS
```

<span data-ttu-id="63ede-120">Parametern **-Passthru** kan användas med många Set-kommandon i Windows PowerShell för att returnera information om resultatet i fall där det inte finns några standardutdata.</span><span class="sxs-lookup"><span data-stu-id="63ede-120">The **-PassThru** parameter can be used with many Set commands in Windows PowerShell to return information about the result in cases in which there is no default output.</span></span>

<span data-ttu-id="63ede-121">Du kan ange sökvägar i förhållande till din aktuella plats på samma sätt som i de flesta UNIX-och Windows-kommandofiler.</span><span class="sxs-lookup"><span data-stu-id="63ede-121">You can specify paths relative to your current location in the same way as you would in most UNIX and Windows command shells.</span></span> <span data-ttu-id="63ede-122">I standard notation för relativa sökvägar, en punkt (**.**) representerar den aktuella mappen och en dubbel period (**..**) representerar den överordnade katalogen för din aktuella plats.</span><span class="sxs-lookup"><span data-stu-id="63ede-122">In standard notation for relative paths, a period (**.**)represents your current folder, and a doubled period (**..**) represents the parent directory of your current location.</span></span>

<span data-ttu-id="63ede-123">Om du till exempel är i mappen **C: \\ Windows** , en punkt (**.**) representerar **c: \\ Windows** -och dubbla punkter (**..**) representerar **c:**.</span><span class="sxs-lookup"><span data-stu-id="63ede-123">For example, if you are in the **C:\\Windows** folder, a period (**.**)represents **C:\\Windows** and double periods (**..**) represent **C:**.</span></span> <span data-ttu-id="63ede-124">Du kan ändra från din aktuella plats till roten på enhet C: genom att skriva:</span><span class="sxs-lookup"><span data-stu-id="63ede-124">You can change from your current location to the root of the C: drive by typing:</span></span>

```
PS> Set-Location -Path .. -PassThru

Path
----
C:\
```

<span data-ttu-id="63ede-125">Samma teknik fungerar på Windows PowerShell-enheter som inte är fil system enheter, till exempel **HKLM:**.</span><span class="sxs-lookup"><span data-stu-id="63ede-125">The same technique works on Windows PowerShell drives that are not file system drives, such as **HKLM:**.</span></span> <span data-ttu-id="63ede-126">Du kan ange din plats till HKLM- \\ program nyckeln i registret genom att skriva:</span><span class="sxs-lookup"><span data-stu-id="63ede-126">You can set your location to the HKLM\\Software key in the registry by typing:</span></span>

```
PS> Set-Location -Path HKLM:\SOFTWARE -PassThru

Path
----
HKLM:\SOFTWARE
```

<span data-ttu-id="63ede-127">Du kan sedan ändra katalog platsen till den överordnade katalogen, som är roten för Windows PowerShell HKLM: Drive, genom att använda en relativ sökväg:</span><span class="sxs-lookup"><span data-stu-id="63ede-127">You can then change the directory location to the parent directory, which is the root of the Windows PowerShell HKLM: drive, by using a relative path:</span></span>

```
PS> Set-Location -Path .. -PassThru

Path
----
HKLM:\
```

<span data-ttu-id="63ede-128">Du kan skriva Set-Location eller använda något av de inbyggda Windows PowerShell-aliasen för Set-Location (CD, chdir, SL).</span><span class="sxs-lookup"><span data-stu-id="63ede-128">You can type Set-Location or use any of the built-in Windows PowerShell aliases for Set-Location (cd, chdir, sl).</span></span> <span data-ttu-id="63ede-129">Exempel:</span><span class="sxs-lookup"><span data-stu-id="63ede-129">For example:</span></span>

```powershell
cd -Path C:\Windows
```

```powershell
chdir -Path .. -PassThru
```

```powershell
sl -Path HKLM:\SOFTWARE -PassThru
```

## <a name="saving-and-recalling-recent-locations-push-location-and-pop-location"></a><span data-ttu-id="63ede-130">Spara och återkalla de senaste platserna (push-location och pop-location)</span><span class="sxs-lookup"><span data-stu-id="63ede-130">Saving and Recalling Recent Locations (Push-Location and Pop-Location)</span></span>

<span data-ttu-id="63ede-131">När du ändrar platser är det bra att hålla reda på var du har varit och att du kan återgå till din tidigare plats.</span><span class="sxs-lookup"><span data-stu-id="63ede-131">When changing locations, it is helpful to keep track of where you have been and to be able to return to your previous location.</span></span> <span data-ttu-id="63ede-132">Cmdleten **push-location** i Windows PowerShell skapar en ordnad historik (en "stack") för katalog Sök vägar där du har varit, och du kan gå tillbaka genom historiken för katalog Sök vägar med hjälp av den kompletterande cmdleten för **popup-platsen** .</span><span class="sxs-lookup"><span data-stu-id="63ede-132">The **Push-Location** cmdlet in Windows PowerShell creates a ordered history (a "stack") of directory paths where you have been, and you can step back through the history of directory paths by using the complementary **Pop-Location** cmdlet.</span></span>

<span data-ttu-id="63ede-133">Windows PowerShell startar till exempel normalt i användarens Hem Katalog.</span><span class="sxs-lookup"><span data-stu-id="63ede-133">For example, Windows PowerShell typically starts in the user's home directory.</span></span>

```
PS> Get-Location

Path
----
C:\Documents and Settings\PowerUser
```

> [!NOTE]
> <span data-ttu-id="63ede-134">Word- *stacken* har en särskild betydelse i många programmerings inställningar, inklusive .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="63ede-134">The word *stack* has a special meaning in many programming settings, including .NET Framework.</span></span> <span data-ttu-id="63ede-135">Precis som en fysisk stack med objekt, är det sista objektet som du har placerat i stacken det första objektet som du kan dra av stacken.</span><span class="sxs-lookup"><span data-stu-id="63ede-135">Like a physical stack of items, the last item you put onto the stack is the first item that you can pull off the stack.</span></span> <span data-ttu-id="63ede-136">Att lägga till ett objekt i en stack är colloquially kallat "pusha" objektet till stacken.</span><span class="sxs-lookup"><span data-stu-id="63ede-136">Adding an item to a stack is colloquially known as "pushing" the item onto the stack.</span></span> <span data-ttu-id="63ede-137">Att hämta ett objekt från stacken är colloquially känt som "underordnad" objektet från stacken.</span><span class="sxs-lookup"><span data-stu-id="63ede-137">Pulling an item off the stack is colloquially known as "popping" the item off the stack.</span></span>

<span data-ttu-id="63ede-138">Om du vill skicka den aktuella platsen till stacken och sedan gå till mappen Lokala inställningar skriver du:</span><span class="sxs-lookup"><span data-stu-id="63ede-138">To push the current location onto the stack, and then move to the Local Settings folder, type:</span></span>

```powershell
Push-Location -Path "Local Settings"
```

<span data-ttu-id="63ede-139">Du kan sedan skicka den lokala inställnings platsen till stacken och flytta den till Temp-mappen genom att skriva:</span><span class="sxs-lookup"><span data-stu-id="63ede-139">You can then push the Local Settings location onto the stack and move to the Temp folder by typing:</span></span>

```powershell
Push-Location -Path Temp
```

<span data-ttu-id="63ede-140">Du kan kontrol lera att du har ändrat kataloger genom att ange kommandot **Get-location** :</span><span class="sxs-lookup"><span data-stu-id="63ede-140">You can verify that you changed directories by entering the **Get-Location** command:</span></span>

```
PS> Get-Location

Path
----
C:\Documents and Settings\PowerUser\Local Settings\Temp
```

<span data-ttu-id="63ede-141">Du kan sedan gå tillbaka till den senast besökta katalogen genom att ange kommandot **pop-location** och kontrol lera ändringen genom att ange kommandot **Get-location** :</span><span class="sxs-lookup"><span data-stu-id="63ede-141">You can then pop back into the most recently visited directory by entering the **Pop-Location** command, and verify the change by entering the **Get-Location** command:</span></span>

```
PS> Pop-Location
PS> Get-Location

Path
----
C:\Documents and Settings\me\Local Settings
```

<span data-ttu-id="63ede-142">Precis som med cmdleten **set-location** kan du inkludera parametern **-Passthru** när du anger cmdleten för **popup-platsen** för att visa den katalog som du har angett:</span><span class="sxs-lookup"><span data-stu-id="63ede-142">Just as with the **Set-Location** cmdlet, you can include the **-PassThru** parameter when you enter the **Pop-Location** cmdlet to display the directory that you entered:</span></span>

```
PS> Pop-Location -PassThru

Path
----
C:\Documents and Settings\PowerUser
```

<span data-ttu-id="63ede-143">Du kan också använda plats-cmdlet: ar med nätverks Sök vägar.</span><span class="sxs-lookup"><span data-stu-id="63ede-143">You can also use the Location cmdlets with network paths.</span></span> <span data-ttu-id="63ede-144">Om du har en server med namnet FS01 med en resurs som heter offentlig kan du ändra din plats genom att skriva</span><span class="sxs-lookup"><span data-stu-id="63ede-144">If you have a server named FS01 with an share named Public, you can change your location by typing</span></span>

```powershell
Set-Location \\FS01\Public
```

<span data-ttu-id="63ede-145">eller</span><span class="sxs-lookup"><span data-stu-id="63ede-145">or</span></span>

```powershell
Push-Location \\FS01\Public
```

<span data-ttu-id="63ede-146">Du kan använda kommandona **push-location** och **set-location** för att ändra platsen till en tillgänglig enhet.</span><span class="sxs-lookup"><span data-stu-id="63ede-146">You can use the **Push-Location** and **Set-Location** commands to change the location to any available drive.</span></span> <span data-ttu-id="63ede-147">Om du till exempel har en lokal CD-ROM-enhet med enhets beteckningen D som innehåller en data-CD kan du ändra platsen till CD-enheten genom att ange kommandot **set-location D:** .</span><span class="sxs-lookup"><span data-stu-id="63ede-147">For example, if you have a local CD-ROM drive with drive letter D that contains a data CD, you can change the location to the CD drive by entering the **Set-Location D:** command.</span></span>

<span data-ttu-id="63ede-148">Om enheten är tom visas följande fel meddelande:</span><span class="sxs-lookup"><span data-stu-id="63ede-148">If the drive is empty, you will get the following error message:</span></span>

```
PS> Set-Location D:
Set-Location : Cannot find path 'D:\' because it does not exist.
```

<span data-ttu-id="63ede-149">När du använder ett kommando rads gränssnitt är det inte lämpligt att använda Utforskaren för att undersöka tillgängliga fysiska enheter.</span><span class="sxs-lookup"><span data-stu-id="63ede-149">When you are using a command-line interface, it is not convenient to use File Explorer to examine the available physical drives.</span></span> <span data-ttu-id="63ede-150">Dessutom visar Utforskaren inte alla Windows PowerShell-enheter.</span><span class="sxs-lookup"><span data-stu-id="63ede-150">Also, File Explorer would not show you the all of the Windows PowerShell drives.</span></span> <span data-ttu-id="63ede-151">Windows PowerShell innehåller en uppsättning kommandon för att ändra Windows PowerShell-enheter och vi pratar om dessa härnäst.</span><span class="sxs-lookup"><span data-stu-id="63ede-151">Windows PowerShell provides a set of commands for manipulating Windows PowerShell drives, and we will talk about these next.</span></span>
