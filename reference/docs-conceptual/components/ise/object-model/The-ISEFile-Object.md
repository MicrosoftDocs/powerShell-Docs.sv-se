---
ms.date: 12/31/2019
keywords: PowerShell, cmdlet
title: ISEFile-objektet
ms.openlocfilehash: 1069e46aa586b8df2050129194a909b90f77b745
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/08/2020
ms.locfileid: "75737006"
---
# <a name="the-isefile-object"></a><span data-ttu-id="2310c-103">ISEFile-objektet</span><span class="sxs-lookup"><span data-stu-id="2310c-103">The ISEFile Object</span></span>

<span data-ttu-id="2310c-104">Ett **ISEFile** -objekt representerar en fil i Windows POWERSHELL® Ise (Integrated Scripting Environment).</span><span class="sxs-lookup"><span data-stu-id="2310c-104">An **ISEFile** object represents a file in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="2310c-105">Det är en instans av klassen **Microsoft. PowerShell. Host. ISE. ISEFile** .</span><span class="sxs-lookup"><span data-stu-id="2310c-105">It is an instance of the **Microsoft.PowerShell.Host.ISE.ISEFile** class.</span></span> <span data-ttu-id="2310c-106">I det här avsnittet visas dess medlems metoder och medlems egenskaper.</span><span class="sxs-lookup"><span data-stu-id="2310c-106">This topic lists its member methods and member properties.</span></span> <span data-ttu-id="2310c-107">`$psISE.CurrentFile` och filerna i samlingen filer på en PowerShell-flik är alla instanser av klassen \* \* \* \* Microsoft. PowerShell. Host. ISE. ISEFile \* \*.</span><span class="sxs-lookup"><span data-stu-id="2310c-107">The `$psISE.CurrentFile` and the files in the Files collection in a PowerShell tab are all instances of the \*\*\*\*Microsoft.PowerShell.Host.ISE.ISEFile\*\* class.</span></span>

## <a name="methods"></a><span data-ttu-id="2310c-108">Metoder</span><span class="sxs-lookup"><span data-stu-id="2310c-108">Methods</span></span>

### <a name="save-saveencoding-"></a><span data-ttu-id="2310c-109">Spara\( \[saveEncoding\] \)</span><span class="sxs-lookup"><span data-stu-id="2310c-109">Save\( \[saveEncoding\] \)</span></span>

<span data-ttu-id="2310c-110">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="2310c-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="2310c-111">Sparar filen på disk.</span><span class="sxs-lookup"><span data-stu-id="2310c-111">Saves the file to disk.</span></span>

<span data-ttu-id="2310c-112">**\[saveEncoding\]** -valfri [system. text. Encoding](https://msdn.microsoft.com/library/system.text.encoding.aspx) en valfri tecken kodnings parameter som ska användas för den sparade filen.</span><span class="sxs-lookup"><span data-stu-id="2310c-112">**\[saveEncoding\]** - optional [System.Text.Encoding](https://msdn.microsoft.com/library/system.text.encoding.aspx) An optional character encoding parameter to be used for the saved file.</span></span> <span data-ttu-id="2310c-113">Standardvärdet är **utf8**.</span><span class="sxs-lookup"><span data-stu-id="2310c-113">The default value is **UTF8**.</span></span>

### <a name="exceptions"></a><span data-ttu-id="2310c-114">Undantag</span><span class="sxs-lookup"><span data-stu-id="2310c-114">Exceptions</span></span>

- <span data-ttu-id="2310c-115">**System. io. IOException**: det gick inte att spara filen.</span><span class="sxs-lookup"><span data-stu-id="2310c-115">**System.IO.IOException**: The file could not be saved.</span></span>

```powershell
# Save the file using the default encoding (UTF8)
$psISE.CurrentFile.Save()

# Save the file as ASCII.
$psISE.CurrentFile.Save([System.Text.Encoding]::ASCII)

# Gets the current encoding.
$myfile = $psISE.CurrentFile
$myfile.Encoding
```

### <a name="saveasfilename-saveencoding"></a><span data-ttu-id="2310c-116">Spara som\(fil namn, \[saveEncoding\]\)</span><span class="sxs-lookup"><span data-stu-id="2310c-116">SaveAs\(filename, \[saveEncoding\]\)</span></span>

<span data-ttu-id="2310c-117">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="2310c-117">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="2310c-118">Sparar filen med det angivna fil namnet och kodningen.</span><span class="sxs-lookup"><span data-stu-id="2310c-118">Saves the file with the specified file name and encoding.</span></span>

<span data-ttu-id="2310c-119">**filename** – sträng namnet som ska användas för att spara filen.</span><span class="sxs-lookup"><span data-stu-id="2310c-119">**filename** - String The name to be used to save the file.</span></span>

<span data-ttu-id="2310c-120">**\[saveEncoding\]** -valfri [system. text. Encoding](https://msdn.microsoft.com/library/system.text.encoding.aspx) en valfri tecken kodnings parameter som ska användas för den sparade filen.</span><span class="sxs-lookup"><span data-stu-id="2310c-120">**\[saveEncoding\]** - optional [System.Text.Encoding](https://msdn.microsoft.com/library/system.text.encoding.aspx) An optional character encoding parameter to be used for the saved file.</span></span> <span data-ttu-id="2310c-121">Standardvärdet är **utf8**.</span><span class="sxs-lookup"><span data-stu-id="2310c-121">The default value is **UTF8**.</span></span>

### <a name="exceptions"></a><span data-ttu-id="2310c-122">Undantag</span><span class="sxs-lookup"><span data-stu-id="2310c-122">Exceptions</span></span>

- <span data-ttu-id="2310c-123">**System. ArgumentNullException**: **fil namns** parametern är null.</span><span class="sxs-lookup"><span data-stu-id="2310c-123">**System.ArgumentNullException**: The **filename** parameter is null.</span></span>
- <span data-ttu-id="2310c-124">**System. ArgumentException**: **fil namns** parametern är tom.</span><span class="sxs-lookup"><span data-stu-id="2310c-124">**System.ArgumentException**: The **filename** parameter is empty.</span></span>
- <span data-ttu-id="2310c-125">**System. io. IOException**: det gick inte att spara filen.</span><span class="sxs-lookup"><span data-stu-id="2310c-125">**System.IO.IOException**: The file could not be saved.</span></span>

```powershell
# Save the file with a full path and name.
$fullpath = "c:\temp\newname.txt"
$psISE.CurrentFile.SaveAs($fullPath)
# Save the file with a full path and name and explicitly as UTF8.
$psISE.CurrentFile.SaveAs($fullPath, [System.Text.Encoding]::UTF8)
```

## <a name="properties"></a><span data-ttu-id="2310c-126">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="2310c-126">Properties</span></span>

### <a name="displayname"></a><span data-ttu-id="2310c-127">Visningsnamn</span><span class="sxs-lookup"><span data-stu-id="2310c-127">DisplayName</span></span>

<span data-ttu-id="2310c-128">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="2310c-128">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="2310c-129">Den skrivskyddade egenskapen som hämtar den sträng som innehåller visnings namnet för den här filen.</span><span class="sxs-lookup"><span data-stu-id="2310c-129">The read-only property that gets the string that contains the display name of this file.</span></span> <span data-ttu-id="2310c-130">Namnet visas på fliken **fil** överst i redigeraren.</span><span class="sxs-lookup"><span data-stu-id="2310c-130">The name is shown on the **File** tab at the top of the editor.</span></span> <span data-ttu-id="2310c-131">Förekomsten av en asterisk `(*)` i slutet av namnet anger att filen har ändringar som inte har sparats.</span><span class="sxs-lookup"><span data-stu-id="2310c-131">The presence of an asterisk `(*)` at the end of the name indicates that the file has changes that have not been saved.</span></span>

```powershell
# Shows the display name of the file.
$psISE.CurrentFile.DisplayName
```

### <a name="editor"></a><span data-ttu-id="2310c-132">Redigeringsprogram</span><span class="sxs-lookup"><span data-stu-id="2310c-132">Editor</span></span>

<span data-ttu-id="2310c-133">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="2310c-133">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="2310c-134">Den skrivskyddade egenskapen som hämtar det [Editor-objekt](The-ISEEditor-Object.md) som används för den angivna filen.</span><span class="sxs-lookup"><span data-stu-id="2310c-134">The read-only property that gets the [editor object](The-ISEEditor-Object.md) that is used for the specified file.</span></span>

```powershell
# Gets the editor and the text.
$psISE.CurrentFile.Editor.Text
```

### <a name="encoding"></a><span data-ttu-id="2310c-135">Encoding</span><span class="sxs-lookup"><span data-stu-id="2310c-135">Encoding</span></span>

<span data-ttu-id="2310c-136">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="2310c-136">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="2310c-137">Den skrivskyddade egenskapen som hämtar den ursprungliga fil kodningen.</span><span class="sxs-lookup"><span data-stu-id="2310c-137">The read-only property that gets the original file encoding.</span></span> <span data-ttu-id="2310c-138">Detta är ett **system. text. Encoding** -objekt.</span><span class="sxs-lookup"><span data-stu-id="2310c-138">This is a **System.Text.Encoding** object.</span></span>

```powershell
# Shows the encoding for the file.
$psISE.CurrentFile.Encoding
```

### <a name="fullpath"></a><span data-ttu-id="2310c-139">FullPath</span><span class="sxs-lookup"><span data-stu-id="2310c-139">FullPath</span></span>

<span data-ttu-id="2310c-140">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="2310c-140">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="2310c-141">Den skrivskyddade egenskapen som hämtar strängen som anger den fullständiga sökvägen till den öppna filen.</span><span class="sxs-lookup"><span data-stu-id="2310c-141">The read-only property that gets the string that specifies the full path of the opened file.</span></span>

```powershell
# Shows the full path for the file.
$psISE.CurrentFile.FullPath
```

### <a name="issaved"></a><span data-ttu-id="2310c-142">IsSaved</span><span class="sxs-lookup"><span data-stu-id="2310c-142">IsSaved</span></span>

<span data-ttu-id="2310c-143">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="2310c-143">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="2310c-144">Den skrivskyddade booleska egenskapen som returnerar `$true` om filen har sparats efter att den senast ändrades.</span><span class="sxs-lookup"><span data-stu-id="2310c-144">The read-only Boolean property that returns `$true` if the file has been saved after it was last modified.</span></span>

```powershell
# Determines whether the file has been saved since it was last modified.
$myfile = $psISE.CurrentFile
$myfile.IsSaved
```

### <a name="isuntitled"></a><span data-ttu-id="2310c-145">IsUntitled</span><span class="sxs-lookup"><span data-stu-id="2310c-145">IsUntitled</span></span>

<span data-ttu-id="2310c-146">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="2310c-146">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="2310c-147">Den skrivskyddade egenskapen som returnerar `$true` om filen aldrig har fått en rubrik.</span><span class="sxs-lookup"><span data-stu-id="2310c-147">The read-only property that returns `$true` if the file has never been given a title.</span></span>

```powershell
# Determines whether the file has never been given a title.
$psISE.CurrentFile.IsUntitled
$psISE.CurrentFile.SaveAs("temp.txt")
$psISE.CurrentFile.IsUntitled
```

## <a name="see-also"></a><span data-ttu-id="2310c-148">Se även</span><span class="sxs-lookup"><span data-stu-id="2310c-148">See Also</span></span>

- [<span data-ttu-id="2310c-149">ISEFileCollectionObject</span><span class="sxs-lookup"><span data-stu-id="2310c-149">The ISEFileCollectionObject</span></span>](The-ISEFileCollection-Object.md)
- [<span data-ttu-id="2310c-150">Syftet med Windows PowerShell ISE-skriptets objekt modell</span><span class="sxs-lookup"><span data-stu-id="2310c-150">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="2310c-151">Hierarki för ISE-objektmodellen</span><span class="sxs-lookup"><span data-stu-id="2310c-151">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
