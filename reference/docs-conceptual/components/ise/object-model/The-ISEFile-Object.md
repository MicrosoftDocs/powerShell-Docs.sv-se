---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: ISEFile-objektet
ms.assetid: 1c6d91f3-c556-42a2-a017-79b6b7b4b7db
ms.openlocfilehash: 24549720b8bc35435882533b0eb138de432ede65
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685139"
---
# <a name="the-isefile-object"></a><span data-ttu-id="9576f-103">ISEFile-objektet</span><span class="sxs-lookup"><span data-stu-id="9576f-103">The ISEFile Object</span></span>

<span data-ttu-id="9576f-104">En **ISEFile** -objektet representerar en fil i Windows PowerShell® Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="9576f-104">An **ISEFile** object represents a file in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="9576f-105">Det är en instans av klassen Microsoft.PowerShell.Host.ISE.ISEFile.</span><span class="sxs-lookup"><span data-stu-id="9576f-105">It is an instance of the Microsoft.PowerShell.Host.ISE.ISEFile class.</span></span> <span data-ttu-id="9576f-106">Det här avsnittet visas dess medlem metoder och egenskaper.</span><span class="sxs-lookup"><span data-stu-id="9576f-106">This topic lists its member methods and member properties.</span></span> <span data-ttu-id="9576f-107">Den **$psISE.CurrentFile** filerna i samlingen filer i en PowerShell-flik är alla instanser av klassen Microsoft.PowerShell.Host.ISE.ISEFile.</span><span class="sxs-lookup"><span data-stu-id="9576f-107">The **$psISE.CurrentFile** and the files in the Files collection in a PowerShell tab are all instances of the Microsoft.PowerShell.Host.ISE.ISEFile class.</span></span>

## <a name="methods"></a><span data-ttu-id="9576f-108">Metoder</span><span class="sxs-lookup"><span data-stu-id="9576f-108">Methods</span></span>

### <a name="save-saveencoding-"></a><span data-ttu-id="9576f-109">Spara\( \[saveEncoding\] \)</span><span class="sxs-lookup"><span data-stu-id="9576f-109">Save\( \[saveEncoding\] \)</span></span>

<span data-ttu-id="9576f-110">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="9576f-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="9576f-111">Sparar filen till disk.</span><span class="sxs-lookup"><span data-stu-id="9576f-111">Saves the file to disk.</span></span>

<span data-ttu-id="9576f-112">**\[saveEncoding\]**  – valfritt [System.Text.Encoding](https://msdn.microsoft.com/library/system.text.encoding.aspx) ett valfritt tecken kodning parametern som ska användas för den sparade filen.</span><span class="sxs-lookup"><span data-stu-id="9576f-112">**\[saveEncoding\]** - optional [System.Text.Encoding](https://msdn.microsoft.com/library/system.text.encoding.aspx) An optional character encoding parameter to be used for the saved file.</span></span> <span data-ttu-id="9576f-113">Standardvärdet är **UTF8**.</span><span class="sxs-lookup"><span data-stu-id="9576f-113">The default value is **UTF8**.</span></span>

### <a name="exceptions"></a><span data-ttu-id="9576f-114">Undantag</span><span class="sxs-lookup"><span data-stu-id="9576f-114">Exceptions</span></span>

- <span data-ttu-id="9576f-115">**System.IO.IOException**: Det gick inte att spara filen.</span><span class="sxs-lookup"><span data-stu-id="9576f-115">**System.IO.IOException**: The file could not be saved.</span></span>

```powershell
# Save the file using the default encoding (UTF8)
$psISE.CurrentFile.Save()

# Save the file as ASCII.
$psISE.CurrentFile.Save([System.Text.Encoding]::ASCII)

# Gets the current encoding.
$myfile = $psISE.CurrentFile
$myfile.Encoding
```

### <a name="saveasfilename-saveencoding"></a><span data-ttu-id="9576f-116">Spara\(filnamnet \[saveEncoding\]\)</span><span class="sxs-lookup"><span data-stu-id="9576f-116">SaveAs\(filename, \[saveEncoding\]\)</span></span>

<span data-ttu-id="9576f-117">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="9576f-117">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="9576f-118">Sparar filen med det angivna filnamnet och kodning.</span><span class="sxs-lookup"><span data-stu-id="9576f-118">Saves the file with the specified file name and encoding.</span></span>

<span data-ttu-id="9576f-119">**filename** -String-namn som används för att spara filen.</span><span class="sxs-lookup"><span data-stu-id="9576f-119">**filename** - String The name to be used to save the file.</span></span>

<span data-ttu-id="9576f-120">**\[saveEncoding\]**  – valfritt [System.Text.Encoding](https://msdn.microsoft.com/library/system.text.encoding.aspx) ett valfritt tecken kodning parametern som ska användas för den sparade filen.</span><span class="sxs-lookup"><span data-stu-id="9576f-120">**\[saveEncoding\]** - optional [System.Text.Encoding](https://msdn.microsoft.com/library/system.text.encoding.aspx) An optional character encoding parameter to be used for the saved file.</span></span> <span data-ttu-id="9576f-121">Standardvärdet är **UTF8**.</span><span class="sxs-lookup"><span data-stu-id="9576f-121">The default value is **UTF8**.</span></span>

### <a name="exceptions"></a><span data-ttu-id="9576f-122">Undantag</span><span class="sxs-lookup"><span data-stu-id="9576f-122">Exceptions</span></span>

- <span data-ttu-id="9576f-123">**System.ArgumentNullException**: Den **filename** parametern är null.</span><span class="sxs-lookup"><span data-stu-id="9576f-123">**System.ArgumentNullException**: The **filename** parameter is null.</span></span>
- <span data-ttu-id="9576f-124">**System.ArgumentException**: Den **filename** parametern är tom.</span><span class="sxs-lookup"><span data-stu-id="9576f-124">**System.ArgumentException**: The **filename** parameter is empty.</span></span>
- <span data-ttu-id="9576f-125">**System.IO.IOException**: Det gick inte att spara filen.</span><span class="sxs-lookup"><span data-stu-id="9576f-125">**System.IO.IOException**: The file could not be saved.</span></span>

```powershell
# Save the file with a full path and name.
$fullpath = "c:\temp\newname.txt"
$psISE.CurrentFile.SaveAs($fullPath)
# Save the file with a full path and name and explicitly as UTF8.
$psISE.CurrentFile.SaveAs($fullPath, [System.Text.Encoding]::UTF8)
```

## <a name="properties"></a><span data-ttu-id="9576f-126">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="9576f-126">Properties</span></span>

### <a name="displayname"></a><span data-ttu-id="9576f-127">Visningsnamn</span><span class="sxs-lookup"><span data-stu-id="9576f-127">DisplayName</span></span>

<span data-ttu-id="9576f-128">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="9576f-128">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="9576f-129">Den skrivskyddade egenskapen som hämtar den sträng som innehåller visningsnamnet för den här filen.</span><span class="sxs-lookup"><span data-stu-id="9576f-129">The read-only property that gets the string that contains the display name of this file.</span></span> <span data-ttu-id="9576f-130">Namnet visas på den **filen** fliken högst upp i redigeraren.</span><span class="sxs-lookup"><span data-stu-id="9576f-130">The name is shown on the **File** tab at the top of the editor.</span></span> <span data-ttu-id="9576f-131">Förekomsten av en asterisk \( \* \) anger att filen har ändringar som inte har sparats i slutet av namnet.</span><span class="sxs-lookup"><span data-stu-id="9576f-131">The presence of an asterisk \(\*\) at the end of the name indicates that the file has changes that have not been saved.</span></span>

```powershell
# Shows the display name of the file.
$psISE.CurrentFile.DisplayName
```

### <a name="editor"></a><span data-ttu-id="9576f-132">Redigeraren</span><span class="sxs-lookup"><span data-stu-id="9576f-132">Editor</span></span>

<span data-ttu-id="9576f-133">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="9576f-133">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="9576f-134">Skrivskyddad egenskap som hämtar den [editor-objekt](The-ISEEditor-Object.md) som används för den angivna filen.</span><span class="sxs-lookup"><span data-stu-id="9576f-134">The read-only property that gets the [editor object](The-ISEEditor-Object.md) that is used for the specified file.</span></span>

```powershell
# Gets the editor and the text.
$psISE.CurrentFile.Editor.Text
```

### <a name="encoding"></a><span data-ttu-id="9576f-135">Encoding</span><span class="sxs-lookup"><span data-stu-id="9576f-135">Encoding</span></span>

<span data-ttu-id="9576f-136">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="9576f-136">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="9576f-137">Den skrivskyddade egenskapen som hämtar den ursprungliga Filkodning.</span><span class="sxs-lookup"><span data-stu-id="9576f-137">The read-only property that gets the original file encoding.</span></span> <span data-ttu-id="9576f-138">Det här är en **System.Text.Encoding** objekt.</span><span class="sxs-lookup"><span data-stu-id="9576f-138">This is a **System.Text.Encoding** object.</span></span>

```powershell
# Shows the encoding for the file.
$psISE.CurrentFile.Encoding
```

### <a name="fullpath"></a><span data-ttu-id="9576f-139">FullPath</span><span class="sxs-lookup"><span data-stu-id="9576f-139">FullPath</span></span>

<span data-ttu-id="9576f-140">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="9576f-140">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="9576f-141">Den skrivskyddade egenskapen som hämtar den sträng som anger den fullständiga sökvägen till den öppna filen.</span><span class="sxs-lookup"><span data-stu-id="9576f-141">The read-only property that gets the string that specifies the full path of the opened file.</span></span>

```powershell
# Shows the full path for the file.
$psISE.CurrentFile.FullPath
```

### <a name="issaved"></a><span data-ttu-id="9576f-142">IsSaved</span><span class="sxs-lookup"><span data-stu-id="9576f-142">IsSaved</span></span>

<span data-ttu-id="9576f-143">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="9576f-143">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="9576f-144">Den skrivskyddade boolesk egenskap som returnerar **$true** om filen har sparats sedan den senast ändrades.</span><span class="sxs-lookup"><span data-stu-id="9576f-144">The read-only Boolean property that returns **$true** if the file has been saved after it was last modified.</span></span>

```powershell
# Determines whether the file has been saved since it was last modified.
$myfile = $psISE.CurrentFile
$myfile.IsSaved
```

### <a name="isuntitled"></a><span data-ttu-id="9576f-145">IsUntitled</span><span class="sxs-lookup"><span data-stu-id="9576f-145">IsUntitled</span></span>

<span data-ttu-id="9576f-146">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="9576f-146">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="9576f-147">Skrivskyddad egenskap som returnerar **$true** om filen har aldrig fått en rubrik.</span><span class="sxs-lookup"><span data-stu-id="9576f-147">The read-only property that returns **$true** if the file has never been given a title.</span></span>

```powershell
# Determines whether the file has never been given a title.
$psISE.CurrentFile.IsUntitled
$psISE.CurrentFile.SaveAs("temp.txt")
$psISE.CurrentFile.IsUntitled
```

## <a name="see-also"></a><span data-ttu-id="9576f-148">Se även</span><span class="sxs-lookup"><span data-stu-id="9576f-148">See Also</span></span>

- [<span data-ttu-id="9576f-149">The ISEFileCollectionObject</span><span class="sxs-lookup"><span data-stu-id="9576f-149">The ISEFileCollectionObject</span></span>](The-ISEFileCollection-Object.md)
- [<span data-ttu-id="9576f-150">Syftet med den Windows PowerShell ISE-Skriptobjektmodellen</span><span class="sxs-lookup"><span data-stu-id="9576f-150">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="9576f-151">Hierarki för ISE-objektmodellen</span><span class="sxs-lookup"><span data-stu-id="9576f-151">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)