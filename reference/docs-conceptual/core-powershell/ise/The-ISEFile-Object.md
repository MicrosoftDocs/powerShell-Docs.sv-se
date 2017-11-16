---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Objektet ISEFile
ms.assetid: 1c6d91f3-c556-42a2-a017-79b6b7b4b7db
ms.openlocfilehash: a1fbd48e872684cc578adb03f52430eabdc54c2c
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/08/2017
---
# <a name="the-isefile-object"></a><span data-ttu-id="f417a-103">Objektet ISEFile</span><span class="sxs-lookup"><span data-stu-id="f417a-103">The ISEFile Object</span></span>
  <span data-ttu-id="f417a-104">En **ISEFile** -objektet representerar en fil i Windows PowerShell® Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="f417a-104">An **ISEFile** object represents a file in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="f417a-105">Det är en instans av klassen Microsoft.PowerShell.Host.ISE.ISEFile.</span><span class="sxs-lookup"><span data-stu-id="f417a-105">It is an instance of the Microsoft.PowerShell.Host.ISE.ISEFile class.</span></span> <span data-ttu-id="f417a-106">Det här avsnittet visar dess medlem metoder och egenskaper.</span><span class="sxs-lookup"><span data-stu-id="f417a-106">This topic lists its member methods and member properties.</span></span> <span data-ttu-id="f417a-107">Den **$psISE.CurrentFile** och filerna i samlingen filer i en PowerShell-flik är alla instanser av klassen Microsoft.PowerShell.Host.ISE.ISEFile.</span><span class="sxs-lookup"><span data-stu-id="f417a-107">The **$psISE.CurrentFile** and the files in the Files collection in a PowerShell tab are all instances of the Microsoft.PowerShell.Host.ISE.ISEFile class.</span></span>

## <a name="methods"></a><span data-ttu-id="f417a-108">Metoder</span><span class="sxs-lookup"><span data-stu-id="f417a-108">Methods</span></span>

### <a name="save-saveencoding-"></a><span data-ttu-id="f417a-109">Spara\( \[saveEncoding\]\)</span><span class="sxs-lookup"><span data-stu-id="f417a-109">Save\( \[saveEncoding\] \)</span></span>
  <span data-ttu-id="f417a-110">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="f417a-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="f417a-111">Filen sparas till disk.</span><span class="sxs-lookup"><span data-stu-id="f417a-111">Saves the file to disk.</span></span>

 <span data-ttu-id="f417a-112">**\[saveEncoding\]**  – valfritt [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) ett valfritt tecken kodning parameter som ska användas för den sparade filen.</span><span class="sxs-lookup"><span data-stu-id="f417a-112">**\[saveEncoding\]** - optional [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) An optional character encoding parameter to be used for the saved file.</span></span> <span data-ttu-id="f417a-113">Standardvärdet är **UTF8**.</span><span class="sxs-lookup"><span data-stu-id="f417a-113">The default value is **UTF8**.</span></span>

 <span data-ttu-id="f417a-114">**Undantag**</span><span class="sxs-lookup"><span data-stu-id="f417a-114">**Exceptions**</span></span>
 -   <span data-ttu-id="f417a-115">**System.IO.IOException**: Det gick inte att spara filen.</span><span class="sxs-lookup"><span data-stu-id="f417a-115">**System.IO.IOException**: The file could not be saved.</span></span>

```
# Save the file using the default encoding (UTF8)
$psIse.CurrentFile.Save()

# Save the file as ASCII.
$psIse.CurrentFile.Save( [System.Text.Encoding]::ASCII )

# Gets the current encoding.
$myfile=$psIse.CurrentFile
$myfile.Encoding

```

### <a name="saveasfilename-saveencoding"></a><span data-ttu-id="f417a-116">SaveAs\(filnamn, \[saveEncoding\]\)</span><span class="sxs-lookup"><span data-stu-id="f417a-116">SaveAs\(filename, \[saveEncoding\]\)</span></span>
  <span data-ttu-id="f417a-117">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="f417a-117">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="f417a-118">Kodning och sparar filen med det angivna filnamnet.</span><span class="sxs-lookup"><span data-stu-id="f417a-118">Saves the file with the specified file name and encoding.</span></span>

 <span data-ttu-id="f417a-119">**filnamn** -String-namn som används för att spara filen.</span><span class="sxs-lookup"><span data-stu-id="f417a-119">**filename** - String The name to be used to save the file.</span></span>

 <span data-ttu-id="f417a-120">**\[saveEncoding\]**  – valfritt [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) ett valfritt tecken kodning parameter som ska användas för den sparade filen.</span><span class="sxs-lookup"><span data-stu-id="f417a-120">**\[saveEncoding\]** - optional [System.Text.Encoding](http://msdn.microsoft.com/library/system.text.encoding.aspx) An optional character encoding parameter to be used for the saved file.</span></span> <span data-ttu-id="f417a-121">Standardvärdet är **UTF8**.</span><span class="sxs-lookup"><span data-stu-id="f417a-121">The default value is **UTF8**.</span></span>

 <span data-ttu-id="f417a-122">**Undantag**</span><span class="sxs-lookup"><span data-stu-id="f417a-122">**Exceptions**</span></span>
 -   <span data-ttu-id="f417a-123">**System.ArgumentNullException**: den **filename** -parametern är null.</span><span class="sxs-lookup"><span data-stu-id="f417a-123">**System.ArgumentNullException**: The **filename** parameter is null.</span></span>

- <span data-ttu-id="f417a-124">**System.ArgumentException**: den **filename** parameter är tom.</span><span class="sxs-lookup"><span data-stu-id="f417a-124">**System.ArgumentException**: The **filename** parameter is empty.</span></span>

- <span data-ttu-id="f417a-125">**System.IO.IOException**: Det gick inte att spara filen.</span><span class="sxs-lookup"><span data-stu-id="f417a-125">**System.IO.IOException**: The file could not be saved.</span></span>

```
# Save the file with a full path and name. 
$fullpath = "c:\temp\newname.txt"
$psIse.CurrentFile.SaveAs($fullPath) 
# Save the file with a full path and name and explicitly as UTF8. 
$psIse.CurrentFile.SaveAs( $fullPath, [System.Text.Encoding]::UTF8 )

```

## <a name="properties"></a><span data-ttu-id="f417a-126">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="f417a-126">Properties</span></span>

### <a name="displayname"></a><span data-ttu-id="f417a-127">Visningsnamn</span><span class="sxs-lookup"><span data-stu-id="f417a-127">DisplayName</span></span>
  <span data-ttu-id="f417a-128">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="f417a-128">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

 <span data-ttu-id="f417a-129">Den skrivskyddade egenskapen som hämtar den sträng som innehåller namnet på den här filen.</span><span class="sxs-lookup"><span data-stu-id="f417a-129">The read-only property that gets the string that contains the display name of this file.</span></span> <span data-ttu-id="f417a-130">Namnet visas på den **filen** fliken överst i redigeraren.</span><span class="sxs-lookup"><span data-stu-id="f417a-130">The name is shown on the **File** tab at the top of the editor.</span></span> <span data-ttu-id="f417a-131">Förekomsten av en asterisk \( \* \) anger att filen har ändringar som inte har sparats i slutet av namnet.</span><span class="sxs-lookup"><span data-stu-id="f417a-131">The presence of an asterisk \(\*\) at the end of the name indicates that the file has changes that have not been saved.</span></span>

```
# Shows the display name of the file.
$psIse.CurrentFile.DisplayName

```

### <a name="editor"></a><span data-ttu-id="f417a-132">Redigeraren</span><span class="sxs-lookup"><span data-stu-id="f417a-132">Editor</span></span>
  <span data-ttu-id="f417a-133">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="f417a-133">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="f417a-134">Skrivskyddad egenskap som hämtar den [editor-objekt](The-ISEEditor-Object.md) som används för den angivna filen.</span><span class="sxs-lookup"><span data-stu-id="f417a-134">The read-only property that gets the [editor object](The-ISEEditor-Object.md) that is used for the specified file.</span></span>

```
# Gets the editor and the text.
$psIse.CurrentFile.Editor.Text

```

### <a name="encoding"></a><span data-ttu-id="f417a-135">Kodning</span><span class="sxs-lookup"><span data-stu-id="f417a-135">Encoding</span></span>
  <span data-ttu-id="f417a-136">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="f417a-136">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="f417a-137">Den skrivskyddade egenskapen som hämtar ursprungliga Filkodning.</span><span class="sxs-lookup"><span data-stu-id="f417a-137">The read-only property that gets the original file encoding.</span></span> <span data-ttu-id="f417a-138">Det här är en **System.Text.Encoding** objekt.</span><span class="sxs-lookup"><span data-stu-id="f417a-138">This is a **System.Text.Encoding** object.</span></span>

```
# Shows the encoding for the file. 
$psIse.CurrentFile.Encoding

```

### <a name="fullpath"></a><span data-ttu-id="f417a-139">FullPath</span><span class="sxs-lookup"><span data-stu-id="f417a-139">FullPath</span></span>
  <span data-ttu-id="f417a-140">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="f417a-140">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="f417a-141">Den skrivskyddade egenskapen som hämtar den sträng som anger den fullständiga sökvägen till den öppna filen.</span><span class="sxs-lookup"><span data-stu-id="f417a-141">The read-only property that gets the string that specifies the full path of the opened file.</span></span>

```
# Shows the full path for the file. 
$psIse.CurrentFile.FullPath

```

### <a name="issaved"></a><span data-ttu-id="f417a-142">IsSaved</span><span class="sxs-lookup"><span data-stu-id="f417a-142">IsSaved</span></span>
  <span data-ttu-id="f417a-143">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="f417a-143">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="f417a-144">Den skrivskyddade boolesk egenskap returnerar **$true** om filen har sparats när den senast ändrades.</span><span class="sxs-lookup"><span data-stu-id="f417a-144">The read-only Boolean property that returns **$true** if the file has been saved after it was last modified.</span></span>

```
# Determines whether the file has been saved since it was last modified.
$myfile=$psIse.CurrentFile
$myfile.IsSaved

```

### <a name="isuntitled"></a><span data-ttu-id="f417a-145">IsUntitled</span><span class="sxs-lookup"><span data-stu-id="f417a-145">IsUntitled</span></span>
  <span data-ttu-id="f417a-146">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="f417a-146">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="f417a-147">Skrivskyddad egenskap som returnerar **$true** om filen har aldrig tilldelats en rubrik.</span><span class="sxs-lookup"><span data-stu-id="f417a-147">The read-only property that returns **$true** if the file has never been given a title.</span></span>

```
# Determines whether the file has never been given a title.
$psISE.CurrentFile.IsUntitled
$psISE.CurrentFile.SaveAs("temp.txt")
$psISE.CurrentFile.IsUntitled

```

## <a name="see-also"></a><span data-ttu-id="f417a-148">Se även</span><span class="sxs-lookup"><span data-stu-id="f417a-148">See Also</span></span>
- [<span data-ttu-id="f417a-149">ISEFileCollectionObject</span><span class="sxs-lookup"><span data-stu-id="f417a-149">The ISEFileCollectionObject</span></span>](The-ISEFileCollection-Object.md) 
- [<span data-ttu-id="f417a-150">Windows PowerShell ISE Scripting Object Model</span><span class="sxs-lookup"><span data-stu-id="f417a-150">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="f417a-151">Windows PowerShell ISE objektreferens modellen</span><span class="sxs-lookup"><span data-stu-id="f417a-151">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md)
- [<span data-ttu-id="f417a-152">Modellen objekthierarkin ISE</span><span class="sxs-lookup"><span data-stu-id="f417a-152">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
