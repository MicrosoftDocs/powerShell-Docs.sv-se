---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: ISEFile-objektet
ms.assetid: 1c6d91f3-c556-42a2-a017-79b6b7b4b7db
ms.openlocfilehash: 276e8f04a827e18999b5b3ecb08f47de4f4b23b1
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="the-isefile-object"></a><span data-ttu-id="fa880-103">ISEFile-objektet</span><span class="sxs-lookup"><span data-stu-id="fa880-103">The ISEFile Object</span></span>

<span data-ttu-id="fa880-104">En **ISEFile** -objektet representerar en fil i Windows PowerShell® Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="fa880-104">An **ISEFile** object represents a file in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="fa880-105">Det är en instans av klassen Microsoft.PowerShell.Host.ISE.ISEFile.</span><span class="sxs-lookup"><span data-stu-id="fa880-105">It is an instance of the Microsoft.PowerShell.Host.ISE.ISEFile class.</span></span> <span data-ttu-id="fa880-106">Det här avsnittet visar dess medlem metoder och egenskaper.</span><span class="sxs-lookup"><span data-stu-id="fa880-106">This topic lists its member methods and member properties.</span></span> <span data-ttu-id="fa880-107">Den **$psISE.CurrentFile** och filerna i samlingen filer i en PowerShell-flik är alla instanser av klassen Microsoft.PowerShell.Host.ISE.ISEFile.</span><span class="sxs-lookup"><span data-stu-id="fa880-107">The **$psISE.CurrentFile** and the files in the Files collection in a PowerShell tab are all instances of the Microsoft.PowerShell.Host.ISE.ISEFile class.</span></span>

## <a name="methods"></a><span data-ttu-id="fa880-108">Metoder</span><span class="sxs-lookup"><span data-stu-id="fa880-108">Methods</span></span>

### <a name="save-saveencoding-"></a><span data-ttu-id="fa880-109">Save\( \[saveEncoding\] \)</span><span class="sxs-lookup"><span data-stu-id="fa880-109">Save\( \[saveEncoding\] \)</span></span>

<span data-ttu-id="fa880-110">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="fa880-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="fa880-111">Filen sparas till disk.</span><span class="sxs-lookup"><span data-stu-id="fa880-111">Saves the file to disk.</span></span>

<span data-ttu-id="fa880-112">**\[saveEncoding\]**  – valfritt [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) ett valfritt tecken kodning parameter som ska användas för den sparade filen.</span><span class="sxs-lookup"><span data-stu-id="fa880-112">**\[saveEncoding\]** - optional [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) An optional character encoding parameter to be used for the saved file.</span></span> <span data-ttu-id="fa880-113">Standardvärdet är **UTF8**.</span><span class="sxs-lookup"><span data-stu-id="fa880-113">The default value is **UTF8**.</span></span>

### <a name="exceptions"></a><span data-ttu-id="fa880-114">Undantag</span><span class="sxs-lookup"><span data-stu-id="fa880-114">Exceptions</span></span>

- <span data-ttu-id="fa880-115">**System.IO.IOException**: Det gick inte att spara filen.</span><span class="sxs-lookup"><span data-stu-id="fa880-115">**System.IO.IOException**: The file could not be saved.</span></span>

```powershell
# Save the file using the default encoding (UTF8)
$psISE.CurrentFile.Save()

# Save the file as ASCII.
$psISE.CurrentFile.Save([System.Text.Encoding]::ASCII)

# Gets the current encoding.
$myfile = $psISE.CurrentFile
$myfile.Encoding
```

### <a name="saveasfilename-saveencoding"></a><span data-ttu-id="fa880-116">SaveAs\(filename, \[saveEncoding\]\)</span><span class="sxs-lookup"><span data-stu-id="fa880-116">SaveAs\(filename, \[saveEncoding\]\)</span></span>

<span data-ttu-id="fa880-117">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="fa880-117">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="fa880-118">Kodning och sparar filen med det angivna filnamnet.</span><span class="sxs-lookup"><span data-stu-id="fa880-118">Saves the file with the specified file name and encoding.</span></span>

<span data-ttu-id="fa880-119">**filnamn** -String-namn som används för att spara filen.</span><span class="sxs-lookup"><span data-stu-id="fa880-119">**filename** - String The name to be used to save the file.</span></span>

<span data-ttu-id="fa880-120">**\[saveEncoding\]**  – valfritt [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) ett valfritt tecken kodning parameter som ska användas för den sparade filen.</span><span class="sxs-lookup"><span data-stu-id="fa880-120">**\[saveEncoding\]** - optional [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) An optional character encoding parameter to be used for the saved file.</span></span> <span data-ttu-id="fa880-121">Standardvärdet är **UTF8**.</span><span class="sxs-lookup"><span data-stu-id="fa880-121">The default value is **UTF8**.</span></span>

### <a name="exceptions"></a><span data-ttu-id="fa880-122">Undantag</span><span class="sxs-lookup"><span data-stu-id="fa880-122">Exceptions</span></span>

- <span data-ttu-id="fa880-123">**System.ArgumentNullException**: den **filename** -parametern är null.</span><span class="sxs-lookup"><span data-stu-id="fa880-123">**System.ArgumentNullException**: The **filename** parameter is null.</span></span>
- <span data-ttu-id="fa880-124">**System.ArgumentException**: den **filename** parameter är tom.</span><span class="sxs-lookup"><span data-stu-id="fa880-124">**System.ArgumentException**: The **filename** parameter is empty.</span></span>
- <span data-ttu-id="fa880-125">**System.IO.IOException**: Det gick inte att spara filen.</span><span class="sxs-lookup"><span data-stu-id="fa880-125">**System.IO.IOException**: The file could not be saved.</span></span>

```powershell
# Save the file with a full path and name.
$fullpath = "c:\temp\newname.txt"
$psISE.CurrentFile.SaveAs($fullPath)
# Save the file with a full path and name and explicitly as UTF8.
$psISE.CurrentFile.SaveAs($fullPath, [System.Text.Encoding]::UTF8)
```

## <a name="properties"></a><span data-ttu-id="fa880-126">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="fa880-126">Properties</span></span>

### <a name="displayname"></a><span data-ttu-id="fa880-127">Visningsnamn</span><span class="sxs-lookup"><span data-stu-id="fa880-127">DisplayName</span></span>

<span data-ttu-id="fa880-128">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="fa880-128">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="fa880-129">Den skrivskyddade egenskapen som hämtar den sträng som innehåller namnet på den här filen.</span><span class="sxs-lookup"><span data-stu-id="fa880-129">The read-only property that gets the string that contains the display name of this file.</span></span> <span data-ttu-id="fa880-130">Namnet visas på den **filen** fliken överst i redigeraren.</span><span class="sxs-lookup"><span data-stu-id="fa880-130">The name is shown on the **File** tab at the top of the editor.</span></span> <span data-ttu-id="fa880-131">Förekomsten av en asterisk \( \* \) anger att filen har ändringar som inte har sparats i slutet av namnet.</span><span class="sxs-lookup"><span data-stu-id="fa880-131">The presence of an asterisk \(\*\) at the end of the name indicates that the file has changes that have not been saved.</span></span>

```powershell
# Shows the display name of the file.
$psISE.CurrentFile.DisplayName
```

### <a name="editor"></a><span data-ttu-id="fa880-132">Redigeraren</span><span class="sxs-lookup"><span data-stu-id="fa880-132">Editor</span></span>

<span data-ttu-id="fa880-133">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="fa880-133">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="fa880-134">Skrivskyddad egenskap som hämtar den [editor-objekt](The-ISEEditor-Object.md) som används för den angivna filen.</span><span class="sxs-lookup"><span data-stu-id="fa880-134">The read-only property that gets the [editor object](The-ISEEditor-Object.md) that is used for the specified file.</span></span>

```powershell
# Gets the editor and the text.
$psISE.CurrentFile.Editor.Text
```

### <a name="encoding"></a><span data-ttu-id="fa880-135">Kodning</span><span class="sxs-lookup"><span data-stu-id="fa880-135">Encoding</span></span>

<span data-ttu-id="fa880-136">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="fa880-136">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="fa880-137">Den skrivskyddade egenskapen som hämtar ursprungliga Filkodning.</span><span class="sxs-lookup"><span data-stu-id="fa880-137">The read-only property that gets the original file encoding.</span></span> <span data-ttu-id="fa880-138">Det här är en **System.Text.Encoding** objekt.</span><span class="sxs-lookup"><span data-stu-id="fa880-138">This is a **System.Text.Encoding** object.</span></span>

```powershell
# Shows the encoding for the file.
$psISE.CurrentFile.Encoding
```

### <a name="fullpath"></a><span data-ttu-id="fa880-139">FullPath</span><span class="sxs-lookup"><span data-stu-id="fa880-139">FullPath</span></span>

<span data-ttu-id="fa880-140">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="fa880-140">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="fa880-141">Den skrivskyddade egenskapen som hämtar den sträng som anger den fullständiga sökvägen till den öppna filen.</span><span class="sxs-lookup"><span data-stu-id="fa880-141">The read-only property that gets the string that specifies the full path of the opened file.</span></span>

```powershell
# Shows the full path for the file.
$psISE.CurrentFile.FullPath
```

### <a name="issaved"></a><span data-ttu-id="fa880-142">IsSaved</span><span class="sxs-lookup"><span data-stu-id="fa880-142">IsSaved</span></span>

<span data-ttu-id="fa880-143">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="fa880-143">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="fa880-144">Den skrivskyddade boolesk egenskap returnerar **$true** om filen har sparats när den senast ändrades.</span><span class="sxs-lookup"><span data-stu-id="fa880-144">The read-only Boolean property that returns **$true** if the file has been saved after it was last modified.</span></span>

```powershell
# Determines whether the file has been saved since it was last modified.
$myfile = $psISE.CurrentFile
$myfile.IsSaved
```

### <a name="isuntitled"></a><span data-ttu-id="fa880-145">IsUntitled</span><span class="sxs-lookup"><span data-stu-id="fa880-145">IsUntitled</span></span>

<span data-ttu-id="fa880-146">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="fa880-146">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="fa880-147">Skrivskyddad egenskap som returnerar **$true** om filen har aldrig tilldelats en rubrik.</span><span class="sxs-lookup"><span data-stu-id="fa880-147">The read-only property that returns **$true** if the file has never been given a title.</span></span>

```powershell
# Determines whether the file has never been given a title.
$psISE.CurrentFile.IsUntitled
$psISE.CurrentFile.SaveAs("temp.txt")
$psISE.CurrentFile.IsUntitled
```

## <a name="see-also"></a><span data-ttu-id="fa880-148">Se även</span><span class="sxs-lookup"><span data-stu-id="fa880-148">See Also</span></span>

- [<span data-ttu-id="fa880-149">ISEFileCollectionObject</span><span class="sxs-lookup"><span data-stu-id="fa880-149">The ISEFileCollectionObject</span></span>](The-ISEFileCollection-Object.md)
- [<span data-ttu-id="fa880-150">Syftet med Windows PowerShell ISE Scripting Object Model</span><span class="sxs-lookup"><span data-stu-id="fa880-150">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="fa880-151">Hierarki för ISE-objektmodellen</span><span class="sxs-lookup"><span data-stu-id="fa880-151">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)