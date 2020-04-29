---
ms.date: 12/23/2019
keywords: PowerShell, cmdlet
title: Arbeta med registernycklar
ms.openlocfilehash: 3feaf6d26db51a507434a6cec1f1095c9013efc8
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "75736853"
---
# <a name="working-with-registry-keys"></a><span data-ttu-id="57068-103">Arbeta med registernycklar</span><span class="sxs-lookup"><span data-stu-id="57068-103">Working with Registry Keys</span></span>

<span data-ttu-id="57068-104">Eftersom register nycklar är objekt på PowerShell-enheter, är det mycket likt att arbeta med filer och mappar.</span><span class="sxs-lookup"><span data-stu-id="57068-104">Because registry keys are items on PowerShell drives, working with them is very similar to working with files and folders.</span></span> <span data-ttu-id="57068-105">En kritisk skillnad är att varje objekt på en register-baserad PowerShell-enhet är en behållare, precis som en mapp på en fil system enhet.</span><span class="sxs-lookup"><span data-stu-id="57068-105">One critical difference is that every item on a registry-based PowerShell drive is a container, just like a folder on a file system drive.</span></span> <span data-ttu-id="57068-106">Register poster och deras associerade värden är dock egenskaper för objekten, inte distinkta objekt.</span><span class="sxs-lookup"><span data-stu-id="57068-106">However, registry entries and their associated values are properties of the items, not distinct items.</span></span>

## <a name="listing-all-subkeys-of-a-registry-key"></a><span data-ttu-id="57068-107">Lista alla under nycklar för en register nyckel</span><span class="sxs-lookup"><span data-stu-id="57068-107">Listing All Subkeys of a Registry Key</span></span>

<span data-ttu-id="57068-108">Du kan visa alla objekt direkt i en register nyckel med hjälp `Get-ChildItem`av.</span><span class="sxs-lookup"><span data-stu-id="57068-108">You can show all items directly within a registry key by using `Get-ChildItem`.</span></span> <span data-ttu-id="57068-109">Lägg till den valfria **Force** -parametern om du vill visa dolda eller system objekt.</span><span class="sxs-lookup"><span data-stu-id="57068-109">Add the optional **Force** parameter to display hidden or system items.</span></span> <span data-ttu-id="57068-110">Detta kommando visar till exempel objekten direkt i PowerShell-enheten `HKCU:`, som motsvarar `HKEY_CURRENT_USER` registrerings data filen:</span><span class="sxs-lookup"><span data-stu-id="57068-110">For example, this command displays the items directly within PowerShell drive `HKCU:`, which corresponds to the `HKEY_CURRENT_USER` registry hive:</span></span>

```powershell
Get-ChildItem -Path HKCU:\ | Select-Object Name
```

```Output
   Hive: Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER

Name
----
HKEY_CURRENT_USER\AppEvents
HKEY_CURRENT_USER\Console
HKEY_CURRENT_USER\Control Panel
HKEY_CURRENT_USER\DirectShow
HKEY_CURRENT_USER\dummy
HKEY_CURRENT_USER\Environment
HKEY_CURRENT_USER\EUDC
HKEY_CURRENT_USER\Keyboard Layout
HKEY_CURRENT_USER\MediaFoundation
HKEY_CURRENT_USER\Microsoft
HKEY_CURRENT_USER\Network
HKEY_CURRENT_USER\Printers
HKEY_CURRENT_USER\Software
HKEY_CURRENT_USER\System
HKEY_CURRENT_USER\Uninstall
HKEY_CURRENT_USER\WXP
HKEY_CURRENT_USER\Volatile Environment
```

<span data-ttu-id="57068-111">Det här är nycklarna på den översta nivån som `HKEY_CURRENT_USER` visas under i Registereditorn (regedit. exe).</span><span class="sxs-lookup"><span data-stu-id="57068-111">These are the top-level keys visible under `HKEY_CURRENT_USER` in the Registry Editor (Regedit.exe).</span></span>

<span data-ttu-id="57068-112">Du kan också ange den här register Sök vägen genom att ange namnet på registrerings leverantören följt `::`av.</span><span class="sxs-lookup"><span data-stu-id="57068-112">You can also specify this registry path by specifying the registry provider's name, followed by `::`.</span></span> <span data-ttu-id="57068-113">Register leverantörens fullständiga namn är `Microsoft.PowerShell.Core\Registry`, men detta kan kortas ned till bara. `Registry`</span><span class="sxs-lookup"><span data-stu-id="57068-113">The registry provider's full name is `Microsoft.PowerShell.Core\Registry`, but this can be shortened to just `Registry`.</span></span> <span data-ttu-id="57068-114">Något av följande kommandon visar innehållet direkt under `HKCU:`.</span><span class="sxs-lookup"><span data-stu-id="57068-114">Any of the following commands will list the contents directly under `HKCU:`.</span></span>

```powershell
Get-ChildItem -Path Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Registry::HKCU
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKCU
Get-ChildItem HKCU:
```

<span data-ttu-id="57068-115">Kommandona visar bara de objekt som finns direkt, ungefär som `DIR` att använda i **cmd. exe** eller `ls` i ett UNIX-gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="57068-115">These commands list only the directly contained items, much like using `DIR` in **Cmd.exe** or `ls` in a UNIX shell.</span></span> <span data-ttu-id="57068-116">Om du vill visa tillgängliga objekt måste du ange parametern **rekursivt** .</span><span class="sxs-lookup"><span data-stu-id="57068-116">To show contained items, you need to specify the **Recurse** parameter.</span></span> <span data-ttu-id="57068-117">Om du vill visa alla register `HKCU:`nycklar i använder du följande kommando.</span><span class="sxs-lookup"><span data-stu-id="57068-117">To list all registry keys in `HKCU:`, use the following command.</span></span>

```powershell
Get-ChildItem -Path HKCU:\ -Recurse
```

<span data-ttu-id="57068-118">`Get-ChildItem`kan utföra komplexa filtrerings funktioner med hjälp av **sökvägen**, **filtrera**, **Inkludera**och **exkludera** parametrar, men dessa parametrar baseras vanligt vis endast på namn.</span><span class="sxs-lookup"><span data-stu-id="57068-118">`Get-ChildItem` can perform complex filtering capabilities through its **Path**, **Filter**, **Include**, and **Exclude** parameters, but those parameters are typically based only on name.</span></span> <span data-ttu-id="57068-119">Du kan utföra komplex filtrering baserat på andra egenskaper för objekt med hjälp av `Where-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="57068-119">You can perform complex filtering based on other properties of items by using the `Where-Object` cmdlet.</span></span> <span data-ttu-id="57068-120">Följande kommando hittar alla nycklar i `HKCU:\Software` som inte har fler än en under nyckel och har även exakt fyra värden:</span><span class="sxs-lookup"><span data-stu-id="57068-120">The following command finds all keys within `HKCU:\Software` that have no more than one subkey and also have exactly four values:</span></span>

```powershell
Get-ChildItem -Path HKCU:\Software -Recurse |
  Where-Object {($_.SubKeyCount -le 1) -and ($_.ValueCount -eq 4) }
```

## <a name="copying-keys"></a><span data-ttu-id="57068-121">Kopierar nycklar</span><span class="sxs-lookup"><span data-stu-id="57068-121">Copying Keys</span></span>

<span data-ttu-id="57068-122">Kopieringen görs med `Copy-Item`.</span><span class="sxs-lookup"><span data-stu-id="57068-122">Copying is done with `Copy-Item`.</span></span> <span data-ttu-id="57068-123">I följande exempel kopieras `CurrentVersion` under nyckeln för `HKLM:\SOFTWARE\Microsoft\Windows\` och alla dess egenskaper till. `HKCU:\`</span><span class="sxs-lookup"><span data-stu-id="57068-123">The following example copies the `CurrentVersion` subkey of `HKLM:\SOFTWARE\Microsoft\Windows\` and all of its properties to `HKCU:\`.</span></span>

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination HKCU:
```

<span data-ttu-id="57068-124">Om du undersöker den nya nyckeln i Registereditorn eller använder `Get-ChildItem`kan du se att du inte har kopior av de inneslutna under nycklarna på den nya platsen.</span><span class="sxs-lookup"><span data-stu-id="57068-124">If you examine this new key in the registry editor or by using `Get-ChildItem`, you notice that you do not have copies of the contained subkeys in the new location.</span></span> <span data-ttu-id="57068-125">För att kunna kopiera allt innehåll i en behållare måste du ange parametern **rekursivt** .</span><span class="sxs-lookup"><span data-stu-id="57068-125">In order to copy all of the contents of a container, you need to specify the **Recurse** parameter.</span></span> <span data-ttu-id="57068-126">Om du vill göra föregående kopierings kommando rekursivt använder du följande kommando:</span><span class="sxs-lookup"><span data-stu-id="57068-126">To make the preceding copy command recursive, you would use this command:</span></span>

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination HKCU: -Recurse
```

<span data-ttu-id="57068-127">Du kan fortfarande använda andra verktyg som du redan har tillgängligt för att utföra fil Systems kopior.</span><span class="sxs-lookup"><span data-stu-id="57068-127">You can still use other tools you already have available to perform filesystem copies.</span></span> <span data-ttu-id="57068-128">Alla redigerings verktyg för registret, inklusive **reg. exe**, **regini. exe**, **regedit. exe**och com-objekt som stöder redigering av registret, till exempel **wscript. Shell** och WMI: s **StdRegProv** -klass kan användas i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="57068-128">Any registry editing tools—including **reg.exe**, **regini.exe**, **regedit.exe**, and COM objects that support registry editing, such as **WScript.Shell** and WMI's **StdRegProv** class can be used from within Windows PowerShell.</span></span>

## <a name="creating-keys"></a><span data-ttu-id="57068-129">Skapar nycklar</span><span class="sxs-lookup"><span data-stu-id="57068-129">Creating Keys</span></span>

<span data-ttu-id="57068-130">Det är enklare att skapa nya nycklar i registret än att skapa ett nytt objekt i ett fil system.</span><span class="sxs-lookup"><span data-stu-id="57068-130">Creating new keys in the registry is simpler than creating a new item in a file system.</span></span> <span data-ttu-id="57068-131">Eftersom alla register nycklar är behållare behöver du inte ange typ av objekt. du anger bara en explicit sökväg, till exempel:</span><span class="sxs-lookup"><span data-stu-id="57068-131">Because all registry keys are containers, you do not need to specify the item type; you simply supply an explicit path, such as:</span></span>

```powershell
New-Item -Path HKCU:\Software_DeleteMe
```

<span data-ttu-id="57068-132">Du kan också använda en provider-baserad sökväg för att ange en nyckel:</span><span class="sxs-lookup"><span data-stu-id="57068-132">You can also use a provider-based path to specify a key:</span></span>

```powershell
New-Item -Path Registry::HKCU\Software_DeleteMe
```

## <a name="deleting-keys"></a><span data-ttu-id="57068-133">Tar bort nycklar</span><span class="sxs-lookup"><span data-stu-id="57068-133">Deleting Keys</span></span>

<span data-ttu-id="57068-134">Att ta bort objekt är i princip samma för alla leverantörer.</span><span class="sxs-lookup"><span data-stu-id="57068-134">Deleting items is essentially the same for all providers.</span></span> <span data-ttu-id="57068-135">Följande kommandon tar bort objekt tyst:</span><span class="sxs-lookup"><span data-stu-id="57068-135">The following commands will silently remove items:</span></span>

```powershell
Remove-Item -Path HKCU:\Software_DeleteMe
Remove-Item -Path 'HKCU:\key with spaces in the name'
```

## <a name="removing-all-keys-under-a-specific-key"></a><span data-ttu-id="57068-136">Ta bort alla nycklar under en angiven nyckel</span><span class="sxs-lookup"><span data-stu-id="57068-136">Removing All Keys Under a Specific Key</span></span>

<span data-ttu-id="57068-137">Du kan ta bort de objekt som `Remove-Item`finns med, men du uppmanas att bekräfta borttagningen om objektet innehåller något annat.</span><span class="sxs-lookup"><span data-stu-id="57068-137">You can remove contained items by using `Remove-Item`, but you will be prompted to confirm the removal if the item contains anything else.</span></span> <span data-ttu-id="57068-138">Om vi till exempel försöker ta bort `HKCU:\CurrentVersion` under nyckeln som vi skapade, ser vi följande:</span><span class="sxs-lookup"><span data-stu-id="57068-138">For example, if we attempt to delete the `HKCU:\CurrentVersion` subkey we created, we see this:</span></span>

```powershell
Remove-Item -Path HKCU:\CurrentVersion
```

```Output
Confirm
The item at HKCU:\CurrentVersion\AdminDebug has children and the -recurse
parameter was not specified. If you continue, all children will be removed with
the item. Are you sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="57068-139">Om du vill ta bort de objekt som finns utan att du behöver göra det anger du parametern **rekursivt** :</span><span class="sxs-lookup"><span data-stu-id="57068-139">To delete contained items without prompting, specify the **Recurse** parameter:</span></span>

```powershell
Remove-Item -Path HKCU:\CurrentVersion -Recurse
```

<span data-ttu-id="57068-140">Om du vill ta bort alla objekt inom `HKCU:\CurrentVersion` men inte `HKCU:\CurrentVersion` själv, kan du istället använda:</span><span class="sxs-lookup"><span data-stu-id="57068-140">If you wanted to remove all items within `HKCU:\CurrentVersion` but not `HKCU:\CurrentVersion` itself, you could instead use:</span></span>

```powershell
Remove-Item -Path HKCU:\CurrentVersion\* -Recurse
```
