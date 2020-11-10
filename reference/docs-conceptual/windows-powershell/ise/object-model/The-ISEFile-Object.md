---
ms.date: 12/31/2019
title: ISEFile-objektet
description: Ett ISEFile-objekt representerar en fil i Windows PowerShell ISE.
ms.openlocfilehash: b5ea70219787f254fe85d728518cbc4746c00250
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94391501"
---
# <a name="the-isefile-object"></a><span data-ttu-id="440c3-103">ISEFile-objektet</span><span class="sxs-lookup"><span data-stu-id="440c3-103">The ISEFile Object</span></span>

<span data-ttu-id="440c3-104">Ett **ISEFile** -objekt representerar en fil i Windows PowerShell ISE (Integrated Scripting Environment).</span><span class="sxs-lookup"><span data-stu-id="440c3-104">An **ISEFile** object represents a file in Windows PowerShell Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="440c3-105">Det är en instans av klassen **Microsoft. PowerShell. Host. ISE. ISEFile** .</span><span class="sxs-lookup"><span data-stu-id="440c3-105">It is an instance of the **Microsoft.PowerShell.Host.ISE.ISEFile** class.</span></span> <span data-ttu-id="440c3-106">I det här avsnittet visas dess medlems metoder och medlems egenskaper.</span><span class="sxs-lookup"><span data-stu-id="440c3-106">This topic lists its member methods and member properties.</span></span> <span data-ttu-id="440c3-107">`$psISE.CurrentFile`Filerna och filerna i samlingen filer på en PowerShell-flik är alla instanser av klassen \* \* \* \* Microsoft. PowerShell. Host. ISE. ISEFile \* \*.</span><span class="sxs-lookup"><span data-stu-id="440c3-107">The `$psISE.CurrentFile` and the files in the Files collection in a PowerShell tab are all instances of the \*\*\*\*Microsoft.PowerShell.Host.ISE.ISEFile\*\* class.</span></span>

## <a name="methods"></a><span data-ttu-id="440c3-108">Metoder</span><span class="sxs-lookup"><span data-stu-id="440c3-108">Methods</span></span>

### <a name="save-saveencoding-"></a><span data-ttu-id="440c3-109">Spara \( \[ saveEncoding \]\)</span><span class="sxs-lookup"><span data-stu-id="440c3-109">Save\( \[saveEncoding\] \)</span></span>

<span data-ttu-id="440c3-110">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="440c3-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="440c3-111">Sparar filen på disk.</span><span class="sxs-lookup"><span data-stu-id="440c3-111">Saves the file to disk.</span></span>

<span data-ttu-id="440c3-112">`[saveEncoding]` – valfri [system. text. Encoding](/dotnet/api/system.text.encoding) en valfri tecken kodnings parameter som ska användas för den sparade filen.</span><span class="sxs-lookup"><span data-stu-id="440c3-112">`[saveEncoding]` - optional [System.Text.Encoding](/dotnet/api/system.text.encoding) An optional character encoding parameter to be used for the saved file.</span></span> <span data-ttu-id="440c3-113">Standardvärdet är **utf8**.</span><span class="sxs-lookup"><span data-stu-id="440c3-113">The default value is **UTF8**.</span></span>

### <a name="exceptions"></a><span data-ttu-id="440c3-114">Undantag</span><span class="sxs-lookup"><span data-stu-id="440c3-114">Exceptions</span></span>

- <span data-ttu-id="440c3-115">**System. io. IOException** : det gick inte att spara filen.</span><span class="sxs-lookup"><span data-stu-id="440c3-115">**System.IO.IOException** : The file could not be saved.</span></span>

```powershell
# Save the file using the default encoding (UTF8)
$psISE.CurrentFile.Save()

# Save the file as ASCII.
$psISE.CurrentFile.Save([System.Text.Encoding]::ASCII)

# Gets the current encoding.
$myfile = $psISE.CurrentFile
$myfile.Encoding
```

### <a name="saveasfilename-saveencoding"></a><span data-ttu-id="440c3-116">Spara som \( fil namn, \[ saveEncoding\]\)</span><span class="sxs-lookup"><span data-stu-id="440c3-116">SaveAs\(filename, \[saveEncoding\]\)</span></span>

<span data-ttu-id="440c3-117">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="440c3-117">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="440c3-118">Sparar filen med det angivna fil namnet och kodningen.</span><span class="sxs-lookup"><span data-stu-id="440c3-118">Saves the file with the specified file name and encoding.</span></span>

<span data-ttu-id="440c3-119">**filename** – sträng namnet som ska användas för att spara filen.</span><span class="sxs-lookup"><span data-stu-id="440c3-119">**filename** - String The name to be used to save the file.</span></span>

<span data-ttu-id="440c3-120">`[saveEncoding]` – valfri [system. text. Encoding](/dotnet/api/system.text.encoding) en valfri tecken kodnings parameter som ska användas för den sparade filen.</span><span class="sxs-lookup"><span data-stu-id="440c3-120">`[saveEncoding]` - optional [System.Text.Encoding](/dotnet/api/system.text.encoding) An optional character encoding parameter to be used for the saved file.</span></span> <span data-ttu-id="440c3-121">Standardvärdet är **utf8**.</span><span class="sxs-lookup"><span data-stu-id="440c3-121">The default value is **UTF8**.</span></span>

### <a name="exceptions"></a><span data-ttu-id="440c3-122">Undantag</span><span class="sxs-lookup"><span data-stu-id="440c3-122">Exceptions</span></span>

- <span data-ttu-id="440c3-123">**System. ArgumentNullException** : **fil namns** parametern är null.</span><span class="sxs-lookup"><span data-stu-id="440c3-123">**System.ArgumentNullException** : The **filename** parameter is null.</span></span>
- <span data-ttu-id="440c3-124">**System. ArgumentException** : **fil namns** parametern är tom.</span><span class="sxs-lookup"><span data-stu-id="440c3-124">**System.ArgumentException** : The **filename** parameter is empty.</span></span>
- <span data-ttu-id="440c3-125">**System. io. IOException** : det gick inte att spara filen.</span><span class="sxs-lookup"><span data-stu-id="440c3-125">**System.IO.IOException** : The file could not be saved.</span></span>

```powershell
# Save the file with a full path and name.
$fullpath = "c:\temp\newname.txt"
$psISE.CurrentFile.SaveAs($fullPath)
# Save the file with a full path and name and explicitly as UTF8.
$psISE.CurrentFile.SaveAs($fullPath, [System.Text.Encoding]::UTF8)
```

## <a name="properties"></a><span data-ttu-id="440c3-126">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="440c3-126">Properties</span></span>

### <a name="displayname"></a><span data-ttu-id="440c3-127">DisplayName</span><span class="sxs-lookup"><span data-stu-id="440c3-127">DisplayName</span></span>

<span data-ttu-id="440c3-128">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="440c3-128">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="440c3-129">Den skrivskyddade egenskapen som hämtar den sträng som innehåller visnings namnet för den här filen.</span><span class="sxs-lookup"><span data-stu-id="440c3-129">The read-only property that gets the string that contains the display name of this file.</span></span> <span data-ttu-id="440c3-130">Namnet visas på fliken **fil** överst i redigeraren.</span><span class="sxs-lookup"><span data-stu-id="440c3-130">The name is shown on the **File** tab at the top of the editor.</span></span> <span data-ttu-id="440c3-131">Förekomsten av en asterisk `(*)` i slutet av namnet anger att filen har ändringar som inte har sparats.</span><span class="sxs-lookup"><span data-stu-id="440c3-131">The presence of an asterisk `(*)` at the end of the name indicates that the file has changes that have not been saved.</span></span>

```powershell
# Shows the display name of the file.
$psISE.CurrentFile.DisplayName
```

### <a name="editor"></a><span data-ttu-id="440c3-132">Redigerare</span><span class="sxs-lookup"><span data-stu-id="440c3-132">Editor</span></span>

<span data-ttu-id="440c3-133">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="440c3-133">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="440c3-134">Den skrivskyddade egenskapen som hämtar det [Editor-objekt](The-ISEEditor-Object.md) som används för den angivna filen.</span><span class="sxs-lookup"><span data-stu-id="440c3-134">The read-only property that gets the [editor object](The-ISEEditor-Object.md) that is used for the specified file.</span></span>

```powershell
# Gets the editor and the text.
$psISE.CurrentFile.Editor.Text
```

### <a name="encoding"></a><span data-ttu-id="440c3-135">Kodning</span><span class="sxs-lookup"><span data-stu-id="440c3-135">Encoding</span></span>

<span data-ttu-id="440c3-136">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="440c3-136">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="440c3-137">Den skrivskyddade egenskapen som hämtar den ursprungliga fil kodningen.</span><span class="sxs-lookup"><span data-stu-id="440c3-137">The read-only property that gets the original file encoding.</span></span> <span data-ttu-id="440c3-138">Detta är ett **system. text. Encoding** -objekt.</span><span class="sxs-lookup"><span data-stu-id="440c3-138">This is a **System.Text.Encoding** object.</span></span>

```powershell
# Shows the encoding for the file.
$psISE.CurrentFile.Encoding
```

### <a name="fullpath"></a><span data-ttu-id="440c3-139">FullPath</span><span class="sxs-lookup"><span data-stu-id="440c3-139">FullPath</span></span>

<span data-ttu-id="440c3-140">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="440c3-140">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="440c3-141">Den skrivskyddade egenskapen som hämtar strängen som anger den fullständiga sökvägen till den öppna filen.</span><span class="sxs-lookup"><span data-stu-id="440c3-141">The read-only property that gets the string that specifies the full path of the opened file.</span></span>

```powershell
# Shows the full path for the file.
$psISE.CurrentFile.FullPath
```

### <a name="issaved"></a><span data-ttu-id="440c3-142">IsSaved</span><span class="sxs-lookup"><span data-stu-id="440c3-142">IsSaved</span></span>

<span data-ttu-id="440c3-143">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="440c3-143">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="440c3-144">Den skrivskyddade booleska egenskapen som returnerar `$true` om filen har sparats efter att den senast ändrades.</span><span class="sxs-lookup"><span data-stu-id="440c3-144">The read-only Boolean property that returns `$true` if the file has been saved after it was last modified.</span></span>

```powershell
# Determines whether the file has been saved since it was last modified.
$myfile = $psISE.CurrentFile
$myfile.IsSaved
```

### <a name="isuntitled"></a><span data-ttu-id="440c3-145">IsUntitled</span><span class="sxs-lookup"><span data-stu-id="440c3-145">IsUntitled</span></span>

<span data-ttu-id="440c3-146">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="440c3-146">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="440c3-147">Den skrivskyddade egenskapen som returnerar `$true` om filen aldrig har fått en rubrik.</span><span class="sxs-lookup"><span data-stu-id="440c3-147">The read-only property that returns `$true` if the file has never been given a title.</span></span>

```powershell
# Determines whether the file has never been given a title.
$psISE.CurrentFile.IsUntitled
$psISE.CurrentFile.SaveAs("temp.txt")
$psISE.CurrentFile.IsUntitled
```

## <a name="see-also"></a><span data-ttu-id="440c3-148">Se även</span><span class="sxs-lookup"><span data-stu-id="440c3-148">See Also</span></span>

- [<span data-ttu-id="440c3-149">ISEFileCollectionObject</span><span class="sxs-lookup"><span data-stu-id="440c3-149">The ISEFileCollectionObject</span></span>](The-ISEFileCollection-Object.md)
- [<span data-ttu-id="440c3-150">Användningsområden för Windows PowerShell ISE-skriptobjektmodellen</span><span class="sxs-lookup"><span data-stu-id="440c3-150">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="440c3-151">Objekt modells-hierarkin för ISE</span><span class="sxs-lookup"><span data-stu-id="440c3-151">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
