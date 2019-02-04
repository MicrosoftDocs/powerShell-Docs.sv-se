---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Arbeta med registernycklar
ms.assetid: 91bfaecd-8684-48b4-ad86-065dfe6dc90a
ms.openlocfilehash: a9d08f2f6b5803980dec45a4e266ad66879c8c8d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55686952"
---
# <a name="working-with-registry-keys"></a><span data-ttu-id="21945-103">Arbeta med registernycklar</span><span class="sxs-lookup"><span data-stu-id="21945-103">Working with Registry Keys</span></span>

<span data-ttu-id="21945-104">Eftersom registernycklar finns på Windows PowerShell-enheter, påminner arbeta med dem mycket om att arbeta med filer och mappar.</span><span class="sxs-lookup"><span data-stu-id="21945-104">Because registry keys are items on Windows PowerShell drives, working with them is very similar to working with files and folders.</span></span> <span data-ttu-id="21945-105">En viktig skillnad är att varje objekt i en registerbaserade Windows PowerShell-enhet är en behållare, precis som en mapp på en filsystemets enhet.</span><span class="sxs-lookup"><span data-stu-id="21945-105">One critical difference is that every item on a registry-based Windows PowerShell drive is a container, just like a folder on a file system drive.</span></span> <span data-ttu-id="21945-106">Registerposter och deras associerade värden är dock egenskaperna hos objekten inte olika objekt.</span><span class="sxs-lookup"><span data-stu-id="21945-106">However, registry entries and their associated values are properties of the items, not distinct items.</span></span>

### <a name="listing-all-subkeys-of-a-registry-key"></a><span data-ttu-id="21945-107">Visa en lista över alla undernycklar till en registernyckel</span><span class="sxs-lookup"><span data-stu-id="21945-107">Listing All Subkeys of a Registry Key</span></span>

<span data-ttu-id="21945-108">Du kan visa alla objekt direkt i en registernyckel med hjälp av **Get-ChildItem**.</span><span class="sxs-lookup"><span data-stu-id="21945-108">You can show all items directly within a registry key by using **Get-ChildItem**.</span></span> <span data-ttu-id="21945-109">Lägg till det valfria **kraft** parameter för att visa dolda eller poster.</span><span class="sxs-lookup"><span data-stu-id="21945-109">Add the optional **Force** parameter to display hidden or system items.</span></span> <span data-ttu-id="21945-110">Till exempel det här kommandot visar objekt direkt i Windows PowerShell-enhet HKCU:, som motsvarar registreringsdatafilen HKEY_CURRENT_USER:</span><span class="sxs-lookup"><span data-stu-id="21945-110">For example, this command displays the items directly within Windows PowerShell drive HKCU:, which corresponds to the HKEY_CURRENT_USER registry hive:</span></span>

```
PS> Get-ChildItem -Path hkcu:\

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER

SKC  VC Name                           Property
---  -- ----                           --------
  2   0 AppEvents                      {}
  7  33 Console                        {ColorTable00, ColorTable01, ColorTab...
 25   1 Control Panel                  {Opened}
  0   5 Environment                    {APR_ICONV_PATH, INCLUDE, LIB, TEMP...}
  1   7 Identities                     {Last Username, Last User ...
  4   0 Keyboard Layout                {}
...
```

<span data-ttu-id="21945-111">Det här är de översta nycklarna som visas under HKEY_CURRENT_USER i Registereditorn (Regedit.exe).</span><span class="sxs-lookup"><span data-stu-id="21945-111">These are the top-level keys visible under HKEY_CURRENT_USER in the Registry Editor (Regedit.exe).</span></span>

<span data-ttu-id="21945-112">Du kan också ange den här sökvägen i registret genom att ange registret leverantörens namn följt av ”**::**”.</span><span class="sxs-lookup"><span data-stu-id="21945-112">You can also specify this registry path by specifying the registry provider's name, followed by "**::**".</span></span> <span data-ttu-id="21945-113">Det fullständiga namnet för register-provider är **Microsoft.PowerShell.Core\\registret**, men detta kan vara kortats ned för att bara **registret**.</span><span class="sxs-lookup"><span data-stu-id="21945-113">The registry provider's full name is **Microsoft.PowerShell.Core\\Registry**, but this can be shortened to just **Registry**.</span></span> <span data-ttu-id="21945-114">Något av följande kommandon visar en lista över innehållet direkt under HKCU:</span><span class="sxs-lookup"><span data-stu-id="21945-114">Any of the following commands will list the contents directly under HKCU:</span></span>

```powershell
Get-ChildItem -Path Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Registry::HKCU
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKCU
Get-ChildItem HKCU:
```

<span data-ttu-id="21945-115">De här kommandona visar endast direkt ingående objekt, ungefär som med Cmd.exe's **DIR** kommando eller **ls** i ett UNIX-gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="21945-115">These commands list only the directly contained items, much like using Cmd.exe's **DIR** command or **ls** in a UNIX shell.</span></span> <span data-ttu-id="21945-116">För att visa ingående objekt, måste du ange den **Recurse** parametern.</span><span class="sxs-lookup"><span data-stu-id="21945-116">To show contained items, you need to specify the **Recurse** parameter.</span></span> <span data-ttu-id="21945-117">Om du vill visa alla registernycklar i HKCU, använder du följande kommando (den här åtgärden kan ta en mycket lång tid.):</span><span class="sxs-lookup"><span data-stu-id="21945-117">To list all registry keys in HKCU, use the following command (This operation can take an extremely long time.):</span></span>

```powershell
Get-ChildItem -Path hkcu:\ -Recurse
```

<span data-ttu-id="21945-118">**Get-ChildItem** kan utföra avancerade filtreringsfunktioner via dess **sökväg**, **Filter**, **inkludera**, och **undanta**parametrar, men de här parametrarna vanligtvis endast baseras på namnet.</span><span class="sxs-lookup"><span data-stu-id="21945-118">**Get-ChildItem** can perform complex filtering capabilities through its **Path**, **Filter**, **Include**, and **Exclude** parameters, but those parameters are typically based only on name.</span></span> <span data-ttu-id="21945-119">Du kan utföra komplex filtrering baserat på andra egenskaper för objekt med hjälp av den **Where-Object** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="21945-119">You can perform complex filtering based on other properties of items by using the **Where-Object** cmdlet.</span></span> <span data-ttu-id="21945-120">Kommandot söker efter alla nycklar i HKCU:\\programvara som har mer än en undernyckel och samtidigt ha exakt fyra värden:</span><span class="sxs-lookup"><span data-stu-id="21945-120">The following command finds all keys within HKCU:\\Software that have no more than one subkey and also have exactly four values:</span></span>

```powershell
Get-ChildItem -Path HKCU:\Software -Recurse | Where-Object -FilterScript {($_.SubKeyCount -le 1) -and ($_.ValueCount -eq 4) }
```

### <a name="copying-keys"></a><span data-ttu-id="21945-121">Kopiera nycklar</span><span class="sxs-lookup"><span data-stu-id="21945-121">Copying Keys</span></span>

<span data-ttu-id="21945-122">Kopieringen är klar med **Copy-Item**.</span><span class="sxs-lookup"><span data-stu-id="21945-122">Copying is done with **Copy-Item**.</span></span> <span data-ttu-id="21945-123">I följande kopieras HKLM:\\programvara\\Microsoft\\Windows\\CurrentVersion och alla dess egenskaper så att HKCU:\\, skapa en ny nyckel med namnet ”CurrentVersion”:</span><span class="sxs-lookup"><span data-stu-id="21945-123">The following command copies HKLM:\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion and all of its properties to HKCU:\\, creating a new key named "CurrentVersion":</span></span>

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination hkcu:
```

<span data-ttu-id="21945-124">Om du granskar den här nya nyckeln i Registereditorn eller genom att använda **Get-ChildItem**, ser du att du inte har kopior av inneslutna undernycklar i den nya platsen.</span><span class="sxs-lookup"><span data-stu-id="21945-124">If you examine this new key in the registry editor or by using **Get-ChildItem**, you will notice that you do not have copies of the contained subkeys in the new location.</span></span> <span data-ttu-id="21945-125">För att kopiera alla innehållet i en behållare, måste du ange den **Recurse** parametern.</span><span class="sxs-lookup"><span data-stu-id="21945-125">In order to copy all of the contents of a container, you need to specify the **Recurse** parameter.</span></span> <span data-ttu-id="21945-126">Om du vill göra det föregående kopiera kommandot rekursivt, använder du det här kommandot:</span><span class="sxs-lookup"><span data-stu-id="21945-126">To make the preceding copy command recursive, you would use this command:</span></span>

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination hkcu: -Recurse
```

<span data-ttu-id="21945-127">Du kan fortfarande använda andra verktyg som du redan har tillgängliga för att utföra filsystem kopior.</span><span class="sxs-lookup"><span data-stu-id="21945-127">You can still use other tools you already have available to perform filesystem copies.</span></span> <span data-ttu-id="21945-128">Alla registerredigeringsverktygen – inklusive reg.exe och regini.exe regedit.exe—and COM-objekt som har stöd för redigering av registret (till exempel WScript.Shell och WMI StdRegProv-klassen) kan användas i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="21945-128">Any registry editing tools—including reg.exe, regini.exe, and regedit.exe—and COM objects that support registry editing (such as WScript.Shell and WMI's StdRegProv class) can be used from within Windows PowerShell.</span></span>

### <a name="creating-keys"></a><span data-ttu-id="21945-129">Hur du skapar nycklar</span><span class="sxs-lookup"><span data-stu-id="21945-129">Creating Keys</span></span>

<span data-ttu-id="21945-130">Skapa nya nycklar i registret är enklare än att skapa ett nytt objekt i ett filsystem.</span><span class="sxs-lookup"><span data-stu-id="21945-130">Creating new keys in the registry is simpler than creating a new item in a file system.</span></span> <span data-ttu-id="21945-131">Eftersom alla registernycklar är behållare, behöver du inte ange objekttypen; du bara ange en explicit sökväg, till exempel:</span><span class="sxs-lookup"><span data-stu-id="21945-131">Because all registry keys are containers, you do not need to specify the item type; you simply supply an explicit path, such as:</span></span>

```powershell
New-Item -Path hkcu:\software_DeleteMe
```

<span data-ttu-id="21945-132">Du kan också använda en provider-baserad sökväg för att ange en nyckel:</span><span class="sxs-lookup"><span data-stu-id="21945-132">You can also use a provider-based path to specify a key:</span></span>

```powershell
New-Item -Path Registry::HKCU_DeleteMe
```

### <a name="deleting-keys"></a><span data-ttu-id="21945-133">Ta bort nycklar</span><span class="sxs-lookup"><span data-stu-id="21945-133">Deleting Keys</span></span>

<span data-ttu-id="21945-134">Ta bort objekt är i stort sett desamma för alla leverantörer.</span><span class="sxs-lookup"><span data-stu-id="21945-134">Deleting items is essentially the same for all providers.</span></span> <span data-ttu-id="21945-135">Följande kommandon raderas tyst objekt:</span><span class="sxs-lookup"><span data-stu-id="21945-135">The following commands will silently remove items:</span></span>

```powershell
Remove-Item -Path hkcu:\Software_DeleteMe
Remove-Item -Path 'hkcu:\key with spaces in the name'
```

### <a name="removing-all-keys-under-a-specific-key"></a><span data-ttu-id="21945-136">Ta bort alla nycklar Under en viss nyckel</span><span class="sxs-lookup"><span data-stu-id="21945-136">Removing All Keys Under a Specific Key</span></span>

<span data-ttu-id="21945-137">Du kan ta bort ingående objekt med hjälp av **Remove-Item**, men du kommer att uppmanas att bekräfta borttagningen om objektet innehåller något annat.</span><span class="sxs-lookup"><span data-stu-id="21945-137">You can remove contained items by using **Remove-Item**, but you will be prompted to confirm the removal if the item contains anything else.</span></span> <span data-ttu-id="21945-138">Exempel: om vi försöker ta bort HKCU:\\CurrentVersion-undernyckeln infogades, ser vi detta:</span><span class="sxs-lookup"><span data-stu-id="21945-138">For example, if we attempt to delete the HKCU:\\CurrentVersion subkey we created, we see this:</span></span>

```
Remove-Item -Path hkcu:\CurrentVersion

Confirm
The item at HKCU:\CurrentVersion\AdminDebug has children and the -recurse
parameter was not specified. If you continue, all children will be removed with
 the item. Are you sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

<span data-ttu-id="21945-139">Om du vill ta bort ingående objekt utan att fråga, ange den **-Recurse** parameter:</span><span class="sxs-lookup"><span data-stu-id="21945-139">To delete contained items without prompting, specify the **-Recurse** parameter:</span></span>

```powershell
Remove-Item -Path HKCU:\CurrentVersion -Recurse
```

<span data-ttu-id="21945-140">Om du vill ta bort alla objekt i HKCU:\\CurrentVersion men inte HKCU:\\CurrentVersion själva, du kan i stället använda:</span><span class="sxs-lookup"><span data-stu-id="21945-140">If you wanted to remove all items within HKCU:\\CurrentVersion but not HKCU:\\CurrentVersion itself, you could instead use:</span></span>

```powershell
Remove-Item -Path HKCU:\CurrentVersion\* -Recurse
```