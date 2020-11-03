---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-output?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Output
ms.openlocfilehash: ccc72ac961adbcba542a7b8be55ad49df68a5ef6
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/16/2020
ms.locfileid: "93272745"
---
# <span data-ttu-id="2ffd8-103">Write-Output</span><span class="sxs-lookup"><span data-stu-id="2ffd8-103">Write-Output</span></span>

## <span data-ttu-id="2ffd8-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="2ffd8-104">SYNOPSIS</span></span>
<span data-ttu-id="2ffd8-105">Skickar de angivna objekten till nästa-kommando i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="2ffd8-105">Sends the specified objects to the next command in the pipeline.</span></span> <span data-ttu-id="2ffd8-106">Om kommandot är det sista kommandot i pipelinen visas objekten i-konsolen.</span><span class="sxs-lookup"><span data-stu-id="2ffd8-106">If the command is the last command in the pipeline, the objects are displayed in the console.</span></span>

## <span data-ttu-id="2ffd8-107">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2ffd8-107">SYNTAX</span></span>

```
Write-Output [-InputObject] <PSObject[]> [-NoEnumerate] [<CommonParameters>]
```

## <span data-ttu-id="2ffd8-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="2ffd8-108">DESCRIPTION</span></span>

<span data-ttu-id="2ffd8-109">`Write-Output`Cmdleten skickar det angivna objektet nedåt i pipeline till nästa kommando.</span><span class="sxs-lookup"><span data-stu-id="2ffd8-109">The `Write-Output` cmdlet sends the specified object down the pipeline to the next command.</span></span>
<span data-ttu-id="2ffd8-110">Om kommandot är det sista kommandot i pipelinen visas objektet i-konsolen.</span><span class="sxs-lookup"><span data-stu-id="2ffd8-110">If the command is the last command in the pipeline, the object is displayed in the console.</span></span>

<span data-ttu-id="2ffd8-111">`Write-Output` skickar objekt nedåt i den primära pipelinen, även kallat "utdataström" eller "lyckad pipeline".</span><span class="sxs-lookup"><span data-stu-id="2ffd8-111">`Write-Output` sends objects down the primary pipeline, also known as the "output stream" or the "success pipeline."</span></span> <span data-ttu-id="2ffd8-112">Om du vill skicka fel-objekt går du till fel pipeline, använder Write-Error.</span><span class="sxs-lookup"><span data-stu-id="2ffd8-112">To send error objects down the error pipeline, use Write-Error.</span></span>

<span data-ttu-id="2ffd8-113">Denna cmdlet används vanligt vis i skript för att Visa strängar och andra objekt i-konsolen.</span><span class="sxs-lookup"><span data-stu-id="2ffd8-113">This cmdlet is typically used in scripts to display strings and other objects on the console.</span></span> <span data-ttu-id="2ffd8-114">Ett av de inbyggda aliasen för `Write-Output` är `echo` och liknar andra gränssnitt som använder `echo` , vilket är standard beteendet för att visa utdata i slutet av en pipeline.</span><span class="sxs-lookup"><span data-stu-id="2ffd8-114">One of the built-in aliases for `Write-Output` is `echo` and similar to other shells that use `echo`, the default behavior is to display the output at the end of a pipeline.</span></span> <span data-ttu-id="2ffd8-115">I PowerShell är det vanligt vis inte nödvändigt att använda cmdleten i instanser där utdata visas som standard.</span><span class="sxs-lookup"><span data-stu-id="2ffd8-115">In PowerShell, it is generally not necessary to use the cmdlet in instances where the output is displayed by default.</span></span> <span data-ttu-id="2ffd8-116">`Get-Process | Write-Output` motsvarar till exempel `Get-Process`.</span><span class="sxs-lookup"><span data-stu-id="2ffd8-116">For example, `Get-Process | Write-Output` is equivalent to `Get-Process`.</span></span> <span data-ttu-id="2ffd8-117">Eller, `echo "Home directory: $HOME"` kan skrivas, `"Home directory: $HOME"` .</span><span class="sxs-lookup"><span data-stu-id="2ffd8-117">Or, `echo "Home directory: $HOME"` can be written, `"Home directory: $HOME"`.</span></span>

<span data-ttu-id="2ffd8-118">Som standard `Write-Output` räknar upp genom samlingar som tillhandahålls till cmdleten.</span><span class="sxs-lookup"><span data-stu-id="2ffd8-118">By default, `Write-Output` enumerates through collections provided to the cmdlet.</span></span> <span data-ttu-id="2ffd8-119">`Write-Output`Du kan dock även använda för att skicka samlingar nedåt i pipeline som ett enda objekt med parametern **noenumeration** .</span><span class="sxs-lookup"><span data-stu-id="2ffd8-119">However, `Write-Output` can also be used to pass collections down the pipeline as a single object with the **NoEnumerate** parameter.</span></span>

## <span data-ttu-id="2ffd8-120">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="2ffd8-120">EXAMPLES</span></span>

### <span data-ttu-id="2ffd8-121">Exempel 1: Hämta objekt och skriv dem till konsolen</span><span class="sxs-lookup"><span data-stu-id="2ffd8-121">Example 1: Get objects and write them to the console</span></span>

```powershell
$P = Get-Process
Write-Output $P
```

<span data-ttu-id="2ffd8-122">Det första kommandot hämtar processer som körs på datorn och lagrar dem i `$P` variabeln.</span><span class="sxs-lookup"><span data-stu-id="2ffd8-122">The first command gets processes running on the computer and stores them in the `$P` variable.</span></span>

<span data-ttu-id="2ffd8-123">Det andra och tredje kommandot visar process objekt i `$P` på-konsolen.</span><span class="sxs-lookup"><span data-stu-id="2ffd8-123">The second and third commands display the process objects in `$P` on the console.</span></span>

### <span data-ttu-id="2ffd8-124">Exempel 2: skicka utdata till en annan cmdlet</span><span class="sxs-lookup"><span data-stu-id="2ffd8-124">Example 2: Pass output to another cmdlet</span></span>

```powershell
Write-Output "test output" | Get-Member
```

<span data-ttu-id="2ffd8-125">Det här kommandot rör strängen "test output" till `Get-Member` cmdleten, som visar medlemmarna i klassen **system. String** , som demonstrerar att strängen skickades ut i pipeline.</span><span class="sxs-lookup"><span data-stu-id="2ffd8-125">This command pipes the "test output" string to the `Get-Member` cmdlet, which displays the members of the **System.String** class, demonstrating that the string was passed along the pipeline.</span></span>

### <span data-ttu-id="2ffd8-126">Exempel 3: utelämna uppräkning i utdata</span><span class="sxs-lookup"><span data-stu-id="2ffd8-126">Example 3: Suppress enumeration in output</span></span>

```powershell
Write-Output 1,2,3 | Measure-Object
```

```Output
Count    : 3
...
```

```powershell
Write-Output 1,2,3 -NoEnumerate | Measure-Object
```

```Output
Count    : 1
...
```

<span data-ttu-id="2ffd8-127">Det här kommandot lägger till parametern **noenumeration** för att behandla en samling eller matris som ett enskilt objekt via pipelinen.</span><span class="sxs-lookup"><span data-stu-id="2ffd8-127">This command adds the **NoEnumerate** parameter to treat a collection or array as a single object through the pipeline.</span></span>

## <span data-ttu-id="2ffd8-128">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="2ffd8-128">PARAMETERS</span></span>

### <span data-ttu-id="2ffd8-129">– InputObject</span><span class="sxs-lookup"><span data-stu-id="2ffd8-129">-InputObject</span></span>

<span data-ttu-id="2ffd8-130">Anger de objekt som ska skickas ned pipelinen.</span><span class="sxs-lookup"><span data-stu-id="2ffd8-130">Specifies the objects to send down the pipeline.</span></span> <span data-ttu-id="2ffd8-131">Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten.</span><span class="sxs-lookup"><span data-stu-id="2ffd8-131">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="2ffd8-132">-Noenumeration</span><span class="sxs-lookup"><span data-stu-id="2ffd8-132">-NoEnumerate</span></span>

<span data-ttu-id="2ffd8-133">Som standard `Write-Output` räknar cmdleten alltid upp utdata.</span><span class="sxs-lookup"><span data-stu-id="2ffd8-133">By default, the `Write-Output` cmdlet always enumerates its output.</span></span> <span data-ttu-id="2ffd8-134">Parametern **Noenumeration** förhindrar standard beteendet och förhindrar att `Write-Output` utdata räknas upp.</span><span class="sxs-lookup"><span data-stu-id="2ffd8-134">The **NoEnumerate** parameter suppresses the default behavior, and prevents `Write-Output` from enumerating output.</span></span> <span data-ttu-id="2ffd8-135">Parametern **noenumeration** har ingen verkan om kommandot omsluts av parenteser, eftersom parenteser tvingar fram uppräkningen.</span><span class="sxs-lookup"><span data-stu-id="2ffd8-135">The **NoEnumerate** parameter has no effect if the command is wrapped in parentheses, because the parentheses force enumeration.</span></span> <span data-ttu-id="2ffd8-136">Räknar till exempel `(Write-Output 1,2,3)` fortfarande matrisen.</span><span class="sxs-lookup"><span data-stu-id="2ffd8-136">For example, `(Write-Output 1,2,3)` still enumerates the array.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2ffd8-137">Det finns ett problem med den här växeln i Windows PowerShell som åtgärdas i PowerShell 6,2 och senare.</span><span class="sxs-lookup"><span data-stu-id="2ffd8-137">There is an issue with this switch in Windows PowerShell that is fixed in PowerShell 6.2 and above.</span></span> <span data-ttu-id="2ffd8-138">När du använder **noenumeration** och uttryckligen använder parametern **InputObject** , räknas kommandot fortfarande upp.</span><span class="sxs-lookup"><span data-stu-id="2ffd8-138">When using **NoEnumerate** and explicitly using the **InputObject** parameter, the command still enumerates.</span></span> <span data-ttu-id="2ffd8-139">Undvik detta genom att skicka **InputObject** -argumenten position (er).</span><span class="sxs-lookup"><span data-stu-id="2ffd8-139">To work around this, pass the **InputObject** argument(s) positionally.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2ffd8-140">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2ffd8-140">CommonParameters</span></span>

<span data-ttu-id="2ffd8-141">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="2ffd8-141">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2ffd8-142">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="2ffd8-142">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2ffd8-143">INDATA</span><span class="sxs-lookup"><span data-stu-id="2ffd8-143">INPUTS</span></span>

### <span data-ttu-id="2ffd8-144">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="2ffd8-144">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="2ffd8-145">Du kan skicka pipe-objekt till `Write-Output` .</span><span class="sxs-lookup"><span data-stu-id="2ffd8-145">You can pipe objects to `Write-Output`.</span></span>

## <span data-ttu-id="2ffd8-146">UTDATA</span><span class="sxs-lookup"><span data-stu-id="2ffd8-146">OUTPUTS</span></span>

### <span data-ttu-id="2ffd8-147">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="2ffd8-147">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="2ffd8-148">`Write-Output` Returnerar de objekt som skickas som inaktuella inmatade objekt.</span><span class="sxs-lookup"><span data-stu-id="2ffd8-148">`Write-Output` returns the objects that are submitted as input.</span></span>

## <span data-ttu-id="2ffd8-149">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="2ffd8-149">NOTES</span></span>

## <span data-ttu-id="2ffd8-150">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="2ffd8-150">RELATED LINKS</span></span>

[<span data-ttu-id="2ffd8-151">about_Output_Streams</span><span class="sxs-lookup"><span data-stu-id="2ffd8-151">about_Output_Streams</span></span>](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[<span data-ttu-id="2ffd8-152">about_Redirection</span><span class="sxs-lookup"><span data-stu-id="2ffd8-152">about_Redirection</span></span>](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[<span data-ttu-id="2ffd8-153">Tee – objekt</span><span class="sxs-lookup"><span data-stu-id="2ffd8-153">Tee-Object</span></span>](Tee-Object.md)

[<span data-ttu-id="2ffd8-154">Skriv-debug</span><span class="sxs-lookup"><span data-stu-id="2ffd8-154">Write-Debug</span></span>](Write-Debug.md)

[<span data-ttu-id="2ffd8-155">Skriv-fel</span><span class="sxs-lookup"><span data-stu-id="2ffd8-155">Write-Error</span></span>](Write-Error.md)

[<span data-ttu-id="2ffd8-156">Skriv värd</span><span class="sxs-lookup"><span data-stu-id="2ffd8-156">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="2ffd8-157">Skriv information</span><span class="sxs-lookup"><span data-stu-id="2ffd8-157">Write-Information</span></span>](Write-Information.md)

[<span data-ttu-id="2ffd8-158">Skriv förlopp</span><span class="sxs-lookup"><span data-stu-id="2ffd8-158">Write-Progress</span></span>](Write-Progress.md)

[<span data-ttu-id="2ffd8-159">Skriv-verbose</span><span class="sxs-lookup"><span data-stu-id="2ffd8-159">Write-Verbose</span></span>](Write-Verbose.md)

[<span data-ttu-id="2ffd8-160">Skriv varning</span><span class="sxs-lookup"><span data-stu-id="2ffd8-160">Write-Warning</span></span>](Write-Warning.md)
