---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-unique?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Unique
ms.openlocfilehash: de827d956e6e813e84d87bb1578ee7d596fe2f15
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710098"
---
# <span data-ttu-id="77234-102">Get-Unique</span><span class="sxs-lookup"><span data-stu-id="77234-102">Get-Unique</span></span>

## <span data-ttu-id="77234-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="77234-103">SYNOPSIS</span></span>
<span data-ttu-id="77234-104">Returnerar unika objekt från en sorterad lista.</span><span class="sxs-lookup"><span data-stu-id="77234-104">Returns unique items from a sorted list.</span></span>

## <span data-ttu-id="77234-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="77234-105">SYNTAX</span></span>

### <span data-ttu-id="77234-106">Uppsträng (standard)</span><span class="sxs-lookup"><span data-stu-id="77234-106">AsString (Default)</span></span>

```
Get-Unique [-InputObject <PSObject>] [-AsString] [<CommonParameters>]
```

### <span data-ttu-id="77234-107">UniqueByType</span><span class="sxs-lookup"><span data-stu-id="77234-107">UniqueByType</span></span>

```
Get-Unique [-InputObject <PSObject>] [-OnType] [<CommonParameters>]
```

## <span data-ttu-id="77234-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="77234-108">DESCRIPTION</span></span>

<span data-ttu-id="77234-109">`Get-Unique`Cmdleten jämför varje objekt i en sorterad lista med nästa objekt, eliminerar dubbletter och returnerar bara en instans av varje objekt.</span><span class="sxs-lookup"><span data-stu-id="77234-109">The `Get-Unique` cmdlet compares each item in a sorted list to the next item, eliminates duplicates, and returns only one instance of each item.</span></span> <span data-ttu-id="77234-110">Listan måste vara sorterad för att cmdleten ska fungera korrekt.</span><span class="sxs-lookup"><span data-stu-id="77234-110">The list must be sorted for the cmdlet to work properly.</span></span>

<span data-ttu-id="77234-111">`Get-Unique` är Skift läges känsligt.</span><span class="sxs-lookup"><span data-stu-id="77234-111">`Get-Unique` is case-sensitive.</span></span> <span data-ttu-id="77234-112">Det innebär att strängar som bara skiljer sig i gemener och versaler anses vara unika.</span><span class="sxs-lookup"><span data-stu-id="77234-112">As a result, strings that differ only in character casing are considered to be unique.</span></span>

## <span data-ttu-id="77234-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="77234-113">EXAMPLES</span></span>

### <span data-ttu-id="77234-114">Exempel 1: Hämta unika ord i en textfil</span><span class="sxs-lookup"><span data-stu-id="77234-114">Example 1: Get unique words in a text file</span></span>

<span data-ttu-id="77234-115">De här kommandona hittar antalet unika ord i en textfil.</span><span class="sxs-lookup"><span data-stu-id="77234-115">These commands find the number of unique words in a text file.</span></span>

```powershell
$A = $( foreach ($line in Get-Content C:\Test1\File1.txt) {
    $line.tolower().split(" ")
  }) | Sort-Object | Get-Unique
$A.count
```

<span data-ttu-id="77234-116">Det första kommandot hämtar innehållet i File.txts filen.</span><span class="sxs-lookup"><span data-stu-id="77234-116">The first command gets the content of the File.txt file.</span></span> <span data-ttu-id="77234-117">Alla text rader konverteras till gemener och sedan delas varje ord på en separat rad i utrymmet ("").</span><span class="sxs-lookup"><span data-stu-id="77234-117">It converts each line of text to lowercase letters and then splits each word onto a separate line at the space (" ").</span></span> <span data-ttu-id="77234-118">Sedan sorteras den resulterande listan i alfabetisk ordning (standard) och använder `Get-Unique` cmdleten för att ta bort duplicerade ord.</span><span class="sxs-lookup"><span data-stu-id="77234-118">Then, it sorts the resulting list alphabetically (the default) and uses the `Get-Unique` cmdlet to eliminate any duplicate words.</span></span> <span data-ttu-id="77234-119">Resultaten lagras i `$A` variabeln.</span><span class="sxs-lookup"><span data-stu-id="77234-119">The results are stored in the `$A` variable.</span></span>

<span data-ttu-id="77234-120">Det andra kommandot använder egenskapen **Count** för samlingen med strängar i `$A` för att fastställa hur många objekt som finns `$A` .</span><span class="sxs-lookup"><span data-stu-id="77234-120">The second command uses the **Count** property of the collection of strings in `$A` to determine how many items are in `$A`.</span></span>

### <span data-ttu-id="77234-121">Exempel 2: Hämta unika heltal i en matris</span><span class="sxs-lookup"><span data-stu-id="77234-121">Example 2: Get unique integers in an array</span></span>

<span data-ttu-id="77234-122">Det här kommandot hittar unika medlemmar i uppsättningen med heltal.</span><span class="sxs-lookup"><span data-stu-id="77234-122">This command finds the unique members of the set of integers.</span></span>

```powershell
1,1,1,1,12,23,4,5,4643,5,3,3,3,3,3,3,3 | Sort-Object | Get-Unique
```

```Output
1
3
4
5
12
23
4643
```

<span data-ttu-id="77234-123">Det första kommandot tar en matris med heltal som skrivs på kommando raden, kopplar dem till cmdlet: en `Sort-Object` som ska sorteras och kopplar dem sedan till `Get-Unique` , vilket eliminerar dubbletter av poster.</span><span class="sxs-lookup"><span data-stu-id="77234-123">The first command takes an array of integers typed at the command line, pipes them to the `Sort-Object` cmdlet to be sorted, and then pipes them to `Get-Unique`, which eliminates duplicate entries.</span></span>

### <span data-ttu-id="77234-124">Exempel 3: Hämta unika objekt typer i en katalog</span><span class="sxs-lookup"><span data-stu-id="77234-124">Example 3: Get unique object types in a directory</span></span>

<span data-ttu-id="77234-125">Det här kommandot använder `Get-ChildItem` cmdleten för att hämta innehållet i den lokala katalogen, inklusive filer och kataloger.</span><span class="sxs-lookup"><span data-stu-id="77234-125">This command uses the `Get-ChildItem` cmdlet to retrieve the contents of the local directory, which includes files and directories.</span></span>

```powershell
Get-ChildItem | Sort-Object {$_.GetType()} | Get-Unique -OnType
```

<span data-ttu-id="77234-126">Pipeline-operatorn (|) skickar resultaten till `Sort-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="77234-126">The pipeline operator (|) sends the results to the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="77234-127">`$_.GetType()`Instruktionen använder **gettype** -metoden för varje fil eller katalog.</span><span class="sxs-lookup"><span data-stu-id="77234-127">The `$_.GetType()` statement applies the **GetType** method to each file or directory.</span></span> <span data-ttu-id="77234-128">`Sort-Object`Sorterar sedan objekt efter typ.</span><span class="sxs-lookup"><span data-stu-id="77234-128">Then, `Sort-Object` sorts the items by type.</span></span> <span data-ttu-id="77234-129">En annan pipeline-operator skickar resultatet till `Get-Unique` .</span><span class="sxs-lookup"><span data-stu-id="77234-129">Another pipeline operator sends the results to `Get-Unique`.</span></span> <span data-ttu-id="77234-130">Parametern **OnType** styrs `Get-Unique` för att returnera endast ett objekt av varje typ.</span><span class="sxs-lookup"><span data-stu-id="77234-130">The **OnType** parameter directs `Get-Unique` to return only one object of each type.</span></span>

### <span data-ttu-id="77234-131">Exempel 4: Hämta unika processer</span><span class="sxs-lookup"><span data-stu-id="77234-131">Example 4: Get unique processes</span></span>

<span data-ttu-id="77234-132">Det här kommandot hämtar namnen på de processer som körs på datorn med borttagna dubbletter.</span><span class="sxs-lookup"><span data-stu-id="77234-132">This command gets the names of processes running on the computer with duplicates eliminated.</span></span>

```powershell
Get-Process | Sort-Object | Select-Object processname | Get-Unique -AsString
```

<span data-ttu-id="77234-133">`Get-Process`Kommandot hämtar alla processer på datorn.</span><span class="sxs-lookup"><span data-stu-id="77234-133">The `Get-Process` command gets all of the processes on the computer.</span></span> <span data-ttu-id="77234-134">Pipeline-operatorn (|) skickar resultatet till `Sort-Object` , som som standard sorterar processerna i alfabetisk ordning efter processname.</span><span class="sxs-lookup"><span data-stu-id="77234-134">The pipeline operator (|) passes the result to `Sort-Object`, which, by default, sorts the processes alphabetically by ProcessName.</span></span> <span data-ttu-id="77234-135">Resultaten är skickas till `Select-Object` cmdleten, som endast väljer värden för egenskapen processname för varje objekt.</span><span class="sxs-lookup"><span data-stu-id="77234-135">The results are piped to the `Select-Object` cmdlet, which selects only the values of the ProcessName property of each object.</span></span> <span data-ttu-id="77234-136">Resultatet blir sedan skickas för `Get-Unique` att eliminera dubbletter.</span><span class="sxs-lookup"><span data-stu-id="77234-136">The results are then piped to `Get-Unique` to eliminate duplicates.</span></span>

<span data-ttu-id="77234-137">Parametern **enstring** instruerar `Get-Unique` att behandla **processname** -värden som strängar.</span><span class="sxs-lookup"><span data-stu-id="77234-137">The **AsString** parameter tells `Get-Unique` to treat the **ProcessName** values as strings.</span></span>
<span data-ttu-id="77234-138">Utan den här parametern `Get-Unique` behandlar **processname** -värden som objekt och returnerar bara en instans av objektet, det vill säga det första process namnet i listan.</span><span class="sxs-lookup"><span data-stu-id="77234-138">Without this parameter, `Get-Unique` treats the **ProcessName** values as objects and returns only one instance of the object, that is, the first process name in the list.</span></span>

## <span data-ttu-id="77234-139">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="77234-139">PARAMETERS</span></span>

### <span data-ttu-id="77234-140">-Uppsträng</span><span class="sxs-lookup"><span data-stu-id="77234-140">-AsString</span></span>

<span data-ttu-id="77234-141">Anger att denna cmdlet använder data som en sträng.</span><span class="sxs-lookup"><span data-stu-id="77234-141">Indicates that this cmdlet uses the data as a string.</span></span> <span data-ttu-id="77234-142">Utan den här parametern behandlas data som ett objekt, så när du skickar en samling objekt av samma typ till `Get-Unique` , till exempel en samling filer, returnerar den bara en (första).</span><span class="sxs-lookup"><span data-stu-id="77234-142">Without this parameter, data is treated as an object, so when you submit a collection of objects of the same type to `Get-Unique`, such as a collection of files, it returns just one (the first).</span></span> <span data-ttu-id="77234-143">Du kan använda den här parametern för att hitta unika värden för objekt egenskaper, t. ex. fil namnen.</span><span class="sxs-lookup"><span data-stu-id="77234-143">You can use this parameter to find the unique values of object properties, such as the file names.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AsString
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="77234-144">– InputObject</span><span class="sxs-lookup"><span data-stu-id="77234-144">-InputObject</span></span>

<span data-ttu-id="77234-145">Anger ininformation för `Get-Unique` .</span><span class="sxs-lookup"><span data-stu-id="77234-145">Specifies input for `Get-Unique`.</span></span> <span data-ttu-id="77234-146">Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten.</span><span class="sxs-lookup"><span data-stu-id="77234-146">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span>

<span data-ttu-id="77234-147">Den här cmdleten behandlar inskickade inskickade med **InputObject** som en samling.</span><span class="sxs-lookup"><span data-stu-id="77234-147">This cmdlet treats the input submitted by using **InputObject** as a collection.</span></span> <span data-ttu-id="77234-148">den räknar inte upp enskilda objekt i samlingen.</span><span class="sxs-lookup"><span data-stu-id="77234-148">it does not enumerate individual items in the collection.</span></span> <span data-ttu-id="77234-149">Eftersom samlingen är ett enda objekt returneras alltid insamlade inskickade med **InputObject** .</span><span class="sxs-lookup"><span data-stu-id="77234-149">Because the collection is a single item, input submitted by using **InputObject** is always returned unchanged.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="77234-150">-OnType</span><span class="sxs-lookup"><span data-stu-id="77234-150">-OnType</span></span>

<span data-ttu-id="77234-151">Anger att denna cmdlet bara returnerar ett objekt av varje typ.</span><span class="sxs-lookup"><span data-stu-id="77234-151">Indicates that this cmdlet returns only one object of each type.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: UniqueByType
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="77234-152">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="77234-152">CommonParameters</span></span>

<span data-ttu-id="77234-153">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="77234-153">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="77234-154">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="77234-154">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="77234-155">INDATA</span><span class="sxs-lookup"><span data-stu-id="77234-155">INPUTS</span></span>

### <span data-ttu-id="77234-156">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="77234-156">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="77234-157">Du kan skicka vidare alla typer av objekt till `Get-Unique` .</span><span class="sxs-lookup"><span data-stu-id="77234-157">You can pipe any type of object to `Get-Unique`.</span></span>

## <span data-ttu-id="77234-158">UTDATA</span><span class="sxs-lookup"><span data-stu-id="77234-158">OUTPUTS</span></span>

### <span data-ttu-id="77234-159">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="77234-159">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="77234-160">Den typ av objekt som `Get-Unique` returneras bestäms av indatamängden.</span><span class="sxs-lookup"><span data-stu-id="77234-160">The type of object that `Get-Unique` returns is determined by the input.</span></span>

## <span data-ttu-id="77234-161">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="77234-161">NOTES</span></span>

<span data-ttu-id="77234-162">Du kan också referera till `Get-Unique` med dess inbyggda alias `gu` .</span><span class="sxs-lookup"><span data-stu-id="77234-162">You can also refer to `Get-Unique` by its built-in alias, `gu`.</span></span> <span data-ttu-id="77234-163">Mer information finns i [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span><span class="sxs-lookup"><span data-stu-id="77234-163">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>

<span data-ttu-id="77234-164">Om du vill sortera en lista använder du sorterings objekt.</span><span class="sxs-lookup"><span data-stu-id="77234-164">To sort a list, use Sort-Object.</span></span> <span data-ttu-id="77234-165">Du kan också använda den **unika** parametern för `Sort-Object` för att hitta unika objekt i en lista.</span><span class="sxs-lookup"><span data-stu-id="77234-165">You can also use the **Unique** parameter of `Sort-Object` to find the unique items in a list.</span></span>

## <span data-ttu-id="77234-166">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="77234-166">RELATED LINKS</span></span>

[<span data-ttu-id="77234-167">Select-Object</span><span class="sxs-lookup"><span data-stu-id="77234-167">Select-Object</span></span>](Select-Object.md)

[<span data-ttu-id="77234-168">Sortera objekt</span><span class="sxs-lookup"><span data-stu-id="77234-168">Sort-Object</span></span>](Sort-Object.md)

