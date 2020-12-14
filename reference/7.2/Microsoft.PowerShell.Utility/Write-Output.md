---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-output?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Output
ms.openlocfilehash: 7e0c958201dbd1b42d1f4c4ee286b8aca1f8595a
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709066"
---
# <span data-ttu-id="7e97e-102">Write-Output</span><span class="sxs-lookup"><span data-stu-id="7e97e-102">Write-Output</span></span>

## <span data-ttu-id="7e97e-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="7e97e-103">SYNOPSIS</span></span>
<span data-ttu-id="7e97e-104">Skickar de angivna objekten till nästa-kommando i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="7e97e-104">Sends the specified objects to the next command in the pipeline.</span></span> <span data-ttu-id="7e97e-105">Om kommandot är det sista kommandot i pipelinen visas objekten i-konsolen.</span><span class="sxs-lookup"><span data-stu-id="7e97e-105">If the command is the last command in the pipeline, the objects are displayed in the console.</span></span>

## <span data-ttu-id="7e97e-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="7e97e-106">SYNTAX</span></span>

```
Write-Output [-InputObject] <PSObject[]> [-NoEnumerate] [<CommonParameters>]
```

## <span data-ttu-id="7e97e-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="7e97e-107">DESCRIPTION</span></span>

<span data-ttu-id="7e97e-108">`Write-Output`Cmdleten skickar det angivna objektet nedåt i pipeline till nästa kommando.</span><span class="sxs-lookup"><span data-stu-id="7e97e-108">The `Write-Output` cmdlet sends the specified object down the pipeline to the next command.</span></span>
<span data-ttu-id="7e97e-109">Om kommandot är det sista kommandot i pipelinen visas objektet i-konsolen.</span><span class="sxs-lookup"><span data-stu-id="7e97e-109">If the command is the last command in the pipeline, the object is displayed in the console.</span></span>

<span data-ttu-id="7e97e-110">`Write-Output` skickar objekt nedåt i den primära pipelinen, även kallat "utdataström" eller "lyckad pipeline".</span><span class="sxs-lookup"><span data-stu-id="7e97e-110">`Write-Output` sends objects down the primary pipeline, also known as the "output stream" or the "success pipeline."</span></span> <span data-ttu-id="7e97e-111">Om du vill skicka fel-objekt går du till fel pipeline, använder Write-Error.</span><span class="sxs-lookup"><span data-stu-id="7e97e-111">To send error objects down the error pipeline, use Write-Error.</span></span>

<span data-ttu-id="7e97e-112">Denna cmdlet används vanligt vis i skript för att Visa strängar och andra objekt i-konsolen.</span><span class="sxs-lookup"><span data-stu-id="7e97e-112">This cmdlet is typically used in scripts to display strings and other objects on the console.</span></span> <span data-ttu-id="7e97e-113">Ett av de inbyggda aliasen för `Write-Output` är `echo` och liknar andra gränssnitt som använder `echo` , vilket är standard beteendet för att visa utdata i slutet av en pipeline.</span><span class="sxs-lookup"><span data-stu-id="7e97e-113">One of the built-in aliases for `Write-Output` is `echo` and similar to other shells that use `echo`, the default behavior is to display the output at the end of a pipeline.</span></span> <span data-ttu-id="7e97e-114">I PowerShell är det vanligt vis inte nödvändigt att använda cmdleten i instanser där utdata visas som standard.</span><span class="sxs-lookup"><span data-stu-id="7e97e-114">In PowerShell, it is generally not necessary to use the cmdlet in instances where the output is displayed by default.</span></span> <span data-ttu-id="7e97e-115">`Get-Process | Write-Output` motsvarar till exempel `Get-Process`.</span><span class="sxs-lookup"><span data-stu-id="7e97e-115">For example, `Get-Process | Write-Output` is equivalent to `Get-Process`.</span></span> <span data-ttu-id="7e97e-116">Eller, `echo "Home directory: $HOME"` kan skrivas, `"Home directory: $HOME"` .</span><span class="sxs-lookup"><span data-stu-id="7e97e-116">Or, `echo "Home directory: $HOME"` can be written, `"Home directory: $HOME"`.</span></span>

<span data-ttu-id="7e97e-117">Som standard `Write-Output` räknar upp genom samlingar som tillhandahålls till cmdleten.</span><span class="sxs-lookup"><span data-stu-id="7e97e-117">By default, `Write-Output` enumerates through collections provided to the cmdlet.</span></span> <span data-ttu-id="7e97e-118">`Write-Output`Du kan dock även använda för att skicka samlingar nedåt i pipeline som ett enda objekt med parametern **noenumeration** .</span><span class="sxs-lookup"><span data-stu-id="7e97e-118">However, `Write-Output` can also be used to pass collections down the pipeline as a single object with the **NoEnumerate** parameter.</span></span>

## <span data-ttu-id="7e97e-119">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="7e97e-119">EXAMPLES</span></span>

### <span data-ttu-id="7e97e-120">Exempel 1: Hämta objekt och skriv dem till konsolen</span><span class="sxs-lookup"><span data-stu-id="7e97e-120">Example 1: Get objects and write them to the console</span></span>

```powershell
$P = Get-Process
Write-Output $P
```

<span data-ttu-id="7e97e-121">Det första kommandot hämtar processer som körs på datorn och lagrar dem i `$P` variabeln.</span><span class="sxs-lookup"><span data-stu-id="7e97e-121">The first command gets processes running on the computer and stores them in the `$P` variable.</span></span>

<span data-ttu-id="7e97e-122">Det andra och tredje kommandot visar process objekt i `$P` på-konsolen.</span><span class="sxs-lookup"><span data-stu-id="7e97e-122">The second and third commands display the process objects in `$P` on the console.</span></span>

### <span data-ttu-id="7e97e-123">Exempel 2: skicka utdata till en annan cmdlet</span><span class="sxs-lookup"><span data-stu-id="7e97e-123">Example 2: Pass output to another cmdlet</span></span>

```powershell
Write-Output "test output" | Get-Member
```

<span data-ttu-id="7e97e-124">Det här kommandot rör strängen "test output" till `Get-Member` cmdleten, som visar medlemmarna i klassen **system. String** , som demonstrerar att strängen skickades ut i pipeline.</span><span class="sxs-lookup"><span data-stu-id="7e97e-124">This command pipes the "test output" string to the `Get-Member` cmdlet, which displays the members of the **System.String** class, demonstrating that the string was passed along the pipeline.</span></span>

### <span data-ttu-id="7e97e-125">Exempel 3: utelämna uppräkning i utdata</span><span class="sxs-lookup"><span data-stu-id="7e97e-125">Example 3: Suppress enumeration in output</span></span>

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

<span data-ttu-id="7e97e-126">Det här kommandot lägger till parametern **noenumeration** för att behandla en samling eller matris som ett enskilt objekt via pipelinen.</span><span class="sxs-lookup"><span data-stu-id="7e97e-126">This command adds the **NoEnumerate** parameter to treat a collection or array as a single object through the pipeline.</span></span>

## <span data-ttu-id="7e97e-127">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="7e97e-127">PARAMETERS</span></span>

### <span data-ttu-id="7e97e-128">– InputObject</span><span class="sxs-lookup"><span data-stu-id="7e97e-128">-InputObject</span></span>

<span data-ttu-id="7e97e-129">Anger de objekt som ska skickas ned pipelinen.</span><span class="sxs-lookup"><span data-stu-id="7e97e-129">Specifies the objects to send down the pipeline.</span></span> <span data-ttu-id="7e97e-130">Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten.</span><span class="sxs-lookup"><span data-stu-id="7e97e-130">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="7e97e-131">-Noenumeration</span><span class="sxs-lookup"><span data-stu-id="7e97e-131">-NoEnumerate</span></span>

<span data-ttu-id="7e97e-132">Som standard `Write-Output` räknar cmdleten alltid upp utdata.</span><span class="sxs-lookup"><span data-stu-id="7e97e-132">By default, the `Write-Output` cmdlet always enumerates its output.</span></span> <span data-ttu-id="7e97e-133">Parametern **Noenumeration** förhindrar standard beteendet och förhindrar att `Write-Output` utdata räknas upp.</span><span class="sxs-lookup"><span data-stu-id="7e97e-133">The **NoEnumerate** parameter suppresses the default behavior, and prevents `Write-Output` from enumerating output.</span></span> <span data-ttu-id="7e97e-134">Parametern **noenumeration** har ingen verkan om kommandot omsluts av parenteser, eftersom parenteser tvingar fram uppräkningen.</span><span class="sxs-lookup"><span data-stu-id="7e97e-134">The **NoEnumerate** parameter has no effect if the command is wrapped in parentheses, because the parentheses force enumeration.</span></span> <span data-ttu-id="7e97e-135">Räknar till exempel `(Write-Output 1,2,3)` fortfarande matrisen.</span><span class="sxs-lookup"><span data-stu-id="7e97e-135">For example, `(Write-Output 1,2,3)` still enumerates the array.</span></span>

> [!NOTE]
> <span data-ttu-id="7e97e-136">Den här växeln fungerar bara korrekt med PowerShell Core 6,2 och senare.</span><span class="sxs-lookup"><span data-stu-id="7e97e-136">This switch only works correctly with PowerShell Core 6.2 and newer.</span></span> <span data-ttu-id="7e97e-137">I äldre versioner av PowerShell Core räknas samlingen fortfarande upp även om den här växeln används.</span><span class="sxs-lookup"><span data-stu-id="7e97e-137">On older versions of PowerShell Core, the collection is still enumerated even with use of this switch.</span></span>

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

### <span data-ttu-id="7e97e-138">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7e97e-138">CommonParameters</span></span>

<span data-ttu-id="7e97e-139">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7e97e-139">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7e97e-140">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="7e97e-140">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7e97e-141">INDATA</span><span class="sxs-lookup"><span data-stu-id="7e97e-141">INPUTS</span></span>

### <span data-ttu-id="7e97e-142">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="7e97e-142">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="7e97e-143">Du kan skicka pipe-objekt till `Write-Output` .</span><span class="sxs-lookup"><span data-stu-id="7e97e-143">You can pipe objects to `Write-Output`.</span></span>

## <span data-ttu-id="7e97e-144">UTDATA</span><span class="sxs-lookup"><span data-stu-id="7e97e-144">OUTPUTS</span></span>

### <span data-ttu-id="7e97e-145">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="7e97e-145">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="7e97e-146">`Write-Output` Returnerar de objekt som skickas som inaktuella inmatade objekt.</span><span class="sxs-lookup"><span data-stu-id="7e97e-146">`Write-Output` returns the objects that are submitted as input.</span></span>

## <span data-ttu-id="7e97e-147">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="7e97e-147">NOTES</span></span>

## <span data-ttu-id="7e97e-148">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="7e97e-148">RELATED LINKS</span></span>

[<span data-ttu-id="7e97e-149">about_Output_Streams</span><span class="sxs-lookup"><span data-stu-id="7e97e-149">about_Output_Streams</span></span>](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[<span data-ttu-id="7e97e-150">about_Redirection</span><span class="sxs-lookup"><span data-stu-id="7e97e-150">about_Redirection</span></span>](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[<span data-ttu-id="7e97e-151">Tee – objekt</span><span class="sxs-lookup"><span data-stu-id="7e97e-151">Tee-Object</span></span>](Tee-Object.md)

[<span data-ttu-id="7e97e-152">Skriv-debug</span><span class="sxs-lookup"><span data-stu-id="7e97e-152">Write-Debug</span></span>](Write-Debug.md)

[<span data-ttu-id="7e97e-153">Skriv-fel</span><span class="sxs-lookup"><span data-stu-id="7e97e-153">Write-Error</span></span>](Write-Error.md)

[<span data-ttu-id="7e97e-154">Skriv värd</span><span class="sxs-lookup"><span data-stu-id="7e97e-154">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="7e97e-155">Skriv information</span><span class="sxs-lookup"><span data-stu-id="7e97e-155">Write-Information</span></span>](Write-Information.md)

[<span data-ttu-id="7e97e-156">Skriv förlopp</span><span class="sxs-lookup"><span data-stu-id="7e97e-156">Write-Progress</span></span>](Write-Progress.md)

[<span data-ttu-id="7e97e-157">Skriv-verbose</span><span class="sxs-lookup"><span data-stu-id="7e97e-157">Write-Verbose</span></span>](Write-Verbose.md)

[<span data-ttu-id="7e97e-158">Skriv varning</span><span class="sxs-lookup"><span data-stu-id="7e97e-158">Write-Warning</span></span>](Write-Warning.md)
