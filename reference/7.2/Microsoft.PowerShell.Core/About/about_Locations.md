---
description: Beskriver hur du kommer åt objekt från arbets platsen i PowerShell.
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_locations?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Locations
ms.openlocfilehash: 4876abe3c651ad2279b85355f2e5e029203b6d4e
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708486"
---
# <a name="about_locations"></a><span data-ttu-id="bd91b-103">about_Locations</span><span class="sxs-lookup"><span data-stu-id="bd91b-103">about_Locations</span></span>

## <a name="short-description"></a><span data-ttu-id="bd91b-104">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="bd91b-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="bd91b-105">Beskriver hur du kommer åt objekt från arbets platsen i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bd91b-105">Describes how to access items from the working location in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="bd91b-106">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="bd91b-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="bd91b-107">Den aktuella arbets platsen är standard platsen som kommando punkten används för.</span><span class="sxs-lookup"><span data-stu-id="bd91b-107">The current working location is the default location to which commands point.</span></span>
<span data-ttu-id="bd91b-108">Detta är alltså den plats som PowerShell använder om du inte anger en explicit sökväg till objektet eller platsen som påverkas av kommandot.</span><span class="sxs-lookup"><span data-stu-id="bd91b-108">In other words, this is the location that PowerShell uses if you do not supply an explicit path to the item or location that is affected by the command.</span></span> <span data-ttu-id="bd91b-109">I de flesta fall är den aktuella arbets platsen en enhet som nås via PowerShell-filsystem-providern och, i vissa fall, en katalog på den enheten.</span><span class="sxs-lookup"><span data-stu-id="bd91b-109">In most cases, the current working location is a drive accessed through the PowerShell FileSystem provider and, in some cases, a directory on that drive.</span></span>
<span data-ttu-id="bd91b-110">Du kan till exempel ange den aktuella arbets platsen till följande plats:</span><span class="sxs-lookup"><span data-stu-id="bd91b-110">For example, you might set your current working location to the following location:</span></span>

```powershell
C:\Program Files\Windows PowerShell
```

<span data-ttu-id="bd91b-111">Därför bearbetas alla kommandon från den här platsen om inte en annan sökväg uttryckligen anges.</span><span class="sxs-lookup"><span data-stu-id="bd91b-111">As a result, all commands are processed from this location unless another path is explicitly provided.</span></span>

<span data-ttu-id="bd91b-112">PowerShell behåller den aktuella arbets platsen för varje enhet även om enheten inte är den aktuella enheten.</span><span class="sxs-lookup"><span data-stu-id="bd91b-112">PowerShell maintains the current working location for each drive even when the drive is not the current drive.</span></span> <span data-ttu-id="bd91b-113">På så sätt kan du komma åt objekt från den aktuella arbets platsen genom att bara referera till enheten på en annan plats.</span><span class="sxs-lookup"><span data-stu-id="bd91b-113">This allows you to access items from the current working location by referring only to the drive of another location.</span></span>
<span data-ttu-id="bd91b-114">Anta till exempel att din aktuella arbets plats är C: \\ Windows.</span><span class="sxs-lookup"><span data-stu-id="bd91b-114">For example, suppose that your current working location is C:\\Windows.</span></span> <span data-ttu-id="bd91b-115">Anta nu att du använder följande kommando för att ändra den aktuella arbets platsen till HKLM: Drive:</span><span class="sxs-lookup"><span data-stu-id="bd91b-115">Now, suppose you use the following command to change your current working location to the HKLM: drive:</span></span>

```powershell
Set-Location HKLM:
```

<span data-ttu-id="bd91b-116">Även om din aktuella plats nu är register enheten, kan du fortfarande komma åt objekt i C: \\ Windows-katalogen genom att använda enheten c:, som visas i följande exempel:</span><span class="sxs-lookup"><span data-stu-id="bd91b-116">Although your current location is now the registry drive, you can still access items in the C:\\Windows directory simply by using the C: drive, as shown in the following example:</span></span>

```powershell
Get-ChildItem C:
```

<span data-ttu-id="bd91b-117">PowerShell kommer att bli medlem i den aktuella arbets platsen för den enheten, så att den hämtar objekt från den katalogen.</span><span class="sxs-lookup"><span data-stu-id="bd91b-117">PowerShell remembers that your current working location for that drive is the Windows directory, so it retrieves items from that directory.</span></span> <span data-ttu-id="bd91b-118">Resultatet blir detsamma om du körde följande kommando:</span><span class="sxs-lookup"><span data-stu-id="bd91b-118">The results would be the same if you ran the following command:</span></span>

```powershell
Get-ChildItem C:\Windows
```

<span data-ttu-id="bd91b-119">I PowerShell kan du använda kommandot Get-Location för att fastställa den aktuella arbets platsen och du kan använda kommandot Set-Location för att ange den aktuella arbets platsen.</span><span class="sxs-lookup"><span data-stu-id="bd91b-119">In PowerShell, you can use the Get-Location command to determine the current working location, and you can use the Set-Location command to set the current working location.</span></span> <span data-ttu-id="bd91b-120">Följande kommando anger till exempel den aktuella arbets platsen till Windows-katalogen för enhet C:</span><span class="sxs-lookup"><span data-stu-id="bd91b-120">For example, the following command sets the current working location to the Windows directory of the C: drive:</span></span>

```powershell
Set-Location c:\windows
```

<span data-ttu-id="bd91b-121">När du har angett den aktuella arbets platsen kan du fortfarande komma åt objekt från andra enheter genom att inkludera enhets namnet (följt av ett kolon) i kommandot, som du ser i följande exempel:</span><span class="sxs-lookup"><span data-stu-id="bd91b-121">After you set the current working location, you can still access items from other drives simply by including the drive name (followed by a colon) in the command, as shown in the following example:</span></span>

```powershell
Get-ChildItem HKLM:\software
```

<span data-ttu-id="bd91b-122">Exempel kommandot hämtar en lista över objekt i program varu behållaren för den lokala datahive-datorns Hive i registret.</span><span class="sxs-lookup"><span data-stu-id="bd91b-122">The example command retrieves a list of items in the Software container of the HKEY Local Machine hive in the registry.</span></span>

<span data-ttu-id="bd91b-123">Med PowerShell kan du också använda specialtecken för att representera den aktuella arbets platsen och dess överordnade plats.</span><span class="sxs-lookup"><span data-stu-id="bd91b-123">PowerShell also allows you to use special characters to represent the current working location and its parent location.</span></span> <span data-ttu-id="bd91b-124">Använd en enda period för att representera den aktuella arbets platsen.</span><span class="sxs-lookup"><span data-stu-id="bd91b-124">To represent the current working location, use a single period.</span></span> <span data-ttu-id="bd91b-125">Om du vill visa den överordnade platsen för den aktuella arbets platsen, använder du två punkter.</span><span class="sxs-lookup"><span data-stu-id="bd91b-125">To represent the parent of the current working location, use two periods.</span></span> <span data-ttu-id="bd91b-126">Följande anger till exempel system-underkatalogen på den aktuella arbets platsen:</span><span class="sxs-lookup"><span data-stu-id="bd91b-126">For example, the following specifies the System subdirectory in the current working location:</span></span>

```powershell
Get-ChildItem .\system
```

<span data-ttu-id="bd91b-127">Om den aktuella arbets platsen är C: \\ Windows returnerar det här kommandot en lista över alla objekt i C: \\ Windows- \\ systemet.</span><span class="sxs-lookup"><span data-stu-id="bd91b-127">If the current working location is C:\\Windows, this command returns a list of all the items in C:\\Windows\\System.</span></span> <span data-ttu-id="bd91b-128">Men om du använder två perioder används den överordnade katalogen i den aktuella arbets katalogen, som visas i följande exempel:</span><span class="sxs-lookup"><span data-stu-id="bd91b-128">However, if you use two periods, the parent directory of the current working directory is used, as shown in the following example:</span></span>

```powershell
Get-ChildItem ..\"program files"
```

<span data-ttu-id="bd91b-129">I det här fallet behandlar PowerShell de två perioderna som C: Drive, så kommandot hämtar alla objekt i katalogen C: \\ Program Files.</span><span class="sxs-lookup"><span data-stu-id="bd91b-129">In this case, PowerShell treats the two periods as the C: drive, so the command retrieves all the items in the C:\\Program Files directory.</span></span>

<span data-ttu-id="bd91b-130">En sökväg som börjar med ett snedstreck identifierar en sökväg från roten på den aktuella enheten.</span><span class="sxs-lookup"><span data-stu-id="bd91b-130">A path beginning with a slash identifies a path from the root of the current drive.</span></span> <span data-ttu-id="bd91b-131">Om din aktuella arbets plats till exempel är C: \\ program \\ PowerShell, är roten på enheten C. Därför visar följande kommando alla objekt i C: \\ Windows-katalogen:</span><span class="sxs-lookup"><span data-stu-id="bd91b-131">For example, if your current working location is C:\\Program Files\\PowerShell, the root of your drive is C. Therefore, the following command lists all items in the C:\\Windows directory:</span></span>

```powershell
Get-ChildItem \windows
```

<span data-ttu-id="bd91b-132">Om du inte anger en sökväg som börjar med ett enhets namn, ett snedstreck eller en punkt när du anger namnet på en behållare eller ett objekt, förutsätts behållaren eller objektet vara placerat på den aktuella arbets platsen.</span><span class="sxs-lookup"><span data-stu-id="bd91b-132">If you do not specify a path beginning with a drive name, slash, or period when supplying the name of a container or item, the container or item is assumed to be located in the current working location.</span></span> <span data-ttu-id="bd91b-133">Om din aktuella arbets plats exempelvis är C: \\ Windows, returnerar följande kommando alla objekt i katalogen C: \\ Windows \\ system:</span><span class="sxs-lookup"><span data-stu-id="bd91b-133">For example, if your current working location is C:\\Windows, the following command returns all the items in the C:\\Windows\\System directory:</span></span>

```powershell
Get-ChildItem system
```

<span data-ttu-id="bd91b-134">Om du anger ett fil namn i stället för ett katalog namn returnerar PowerShell information om filen (förutsatt att filen finns på den aktuella arbets platsen).</span><span class="sxs-lookup"><span data-stu-id="bd91b-134">If you specify a file name rather than a directory name, PowerShell returns details about that file (assuming that file is located in the current working location).</span></span>

## <a name="see-also"></a><span data-ttu-id="bd91b-135">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="bd91b-135">SEE ALSO</span></span>

[<span data-ttu-id="bd91b-136">Ange plats</span><span class="sxs-lookup"><span data-stu-id="bd91b-136">Set-Location</span></span>](xref:Microsoft.PowerShell.Management.Set-Location)

[<span data-ttu-id="bd91b-137">about_Providers</span><span class="sxs-lookup"><span data-stu-id="bd91b-137">about_Providers</span></span>](about_Providers.md)

[<span data-ttu-id="bd91b-138">about_Path_Syntax</span><span class="sxs-lookup"><span data-stu-id="bd91b-138">about_Path_Syntax</span></span>](about_Path_Syntax.md)
