---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 08/07/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/out-host?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-Host
ms.openlocfilehash: 98a9d7d5775bd6d92f60035efedc9d97ae7e8618
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266853"
---
# <span data-ttu-id="33f8d-103">Out-Host</span><span class="sxs-lookup"><span data-stu-id="33f8d-103">Out-Host</span></span>

## <span data-ttu-id="33f8d-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="33f8d-104">SYNOPSIS</span></span>
<span data-ttu-id="33f8d-105">Skickar utdata till kommando raden.</span><span class="sxs-lookup"><span data-stu-id="33f8d-105">Sends output to the command line.</span></span>

## <span data-ttu-id="33f8d-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="33f8d-106">SYNTAX</span></span>

### <span data-ttu-id="33f8d-107">Alla</span><span class="sxs-lookup"><span data-stu-id="33f8d-107">All</span></span>

```
Out-Host [-Paging] [-InputObject <PSObject>] [<CommonParameters>]
```

## <span data-ttu-id="33f8d-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="33f8d-108">DESCRIPTION</span></span>

<span data-ttu-id="33f8d-109">`Out-Host`Cmdleten skickar utdata till PowerShell-värden för visning.</span><span class="sxs-lookup"><span data-stu-id="33f8d-109">The `Out-Host` cmdlet sends output to the PowerShell host for display.</span></span> <span data-ttu-id="33f8d-110">Värden visar utdata på kommando raden.</span><span class="sxs-lookup"><span data-stu-id="33f8d-110">The host displays the output at the command line.</span></span> <span data-ttu-id="33f8d-111">Eftersom `Out-Host` är standard behöver du inte ange den om du inte vill använda dess parametrar.</span><span class="sxs-lookup"><span data-stu-id="33f8d-111">Because `Out-Host` is the default, you don't have to specify it unless you want to use its parameters.</span></span>

<span data-ttu-id="33f8d-112">`Out-Host` läggs automatiskt till varje kommando som körs.</span><span class="sxs-lookup"><span data-stu-id="33f8d-112">`Out-Host` is automatically appended to every command that is executed.</span></span> <span data-ttu-id="33f8d-113">Den skickar ut pipelinen till värden som kör kommandot.</span><span class="sxs-lookup"><span data-stu-id="33f8d-113">It passes the output of the pipeline to the host executing the command.</span></span> <span data-ttu-id="33f8d-114">`Out-Host` ignorerar ANSI escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="33f8d-114">`Out-Host` ignores ANSI escape sequences.</span></span> <span data-ttu-id="33f8d-115">Escape-sekvenser hanteras av värden.</span><span class="sxs-lookup"><span data-stu-id="33f8d-115">The escape sequences are handled by the host.</span></span> <span data-ttu-id="33f8d-116">`Out-Host` skickar ANSI escape-sekvenser till värden utan att försöka tolka eller ändra dem.</span><span class="sxs-lookup"><span data-stu-id="33f8d-116">`Out-Host` passes ANSI escape sequences to the host without trying to interpret or change them.</span></span>

## <span data-ttu-id="33f8d-117">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="33f8d-117">EXAMPLES</span></span>

### <span data-ttu-id="33f8d-118">Exempel 1: Visa utdata en sida i taget</span><span class="sxs-lookup"><span data-stu-id="33f8d-118">Example 1: Display output one page at a time</span></span>

<span data-ttu-id="33f8d-119">I det här exemplet visas en sida i taget i systemet.</span><span class="sxs-lookup"><span data-stu-id="33f8d-119">This example displays the system processes one page at a time.</span></span>

```powershell
Get-Process | Out-Host -Paging
```

```Output
NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     30    24.12      36.95      15.86   21004  14 ApplicationFrameHost
     55    24.33      60.48      10.80   12904  14 BCompare
<SPACE> next page; <CR> next line; Q quit
      9     4.71       8.94       0.00   16864  14 explorer
<SPACE> next page; <CR> next line; Q quit
```

<span data-ttu-id="33f8d-120">`Get-Process` hämtar system processerna och skickar objekten nedåt i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="33f8d-120">`Get-Process` gets the system processes and sends the objects down the pipeline.</span></span> <span data-ttu-id="33f8d-121">`Out-Host` använder **växlings** parametern för att visa en sida med data i taget.</span><span class="sxs-lookup"><span data-stu-id="33f8d-121">`Out-Host` uses the **Paging** parameter to display one page of data at a time.</span></span>

### <span data-ttu-id="33f8d-122">Exempel 2: Använd en variabel som inmatad</span><span class="sxs-lookup"><span data-stu-id="33f8d-122">Example 2: Use a variable as input</span></span>

<span data-ttu-id="33f8d-123">I det här exemplet används objekt som är lagrade i en variabel som inloggade `Out-Host` .</span><span class="sxs-lookup"><span data-stu-id="33f8d-123">This example uses objects stored in a variable as the input for `Out-Host`.</span></span>

```powershell
$io = Get-History
Out-Host -InputObject $io
```

<span data-ttu-id="33f8d-124">`Get-History` hämtar PowerShell-sessionens historik och lagrar objekten i `$io` variabeln.</span><span class="sxs-lookup"><span data-stu-id="33f8d-124">`Get-History` gets the PowerShell session's history, and stores the objects in the `$io` variable.</span></span>
<span data-ttu-id="33f8d-125">`Out-Host` använder parametern **InputObject** för att ange `$io` variabeln och visar historiken.</span><span class="sxs-lookup"><span data-stu-id="33f8d-125">`Out-Host` uses the **InputObject** parameter to specify the `$io` variable and displays the history.</span></span>

## <span data-ttu-id="33f8d-126">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="33f8d-126">PARAMETERS</span></span>

### <span data-ttu-id="33f8d-127">– InputObject</span><span class="sxs-lookup"><span data-stu-id="33f8d-127">-InputObject</span></span>

<span data-ttu-id="33f8d-128">Anger de objekt som skrivs till-konsolen.</span><span class="sxs-lookup"><span data-stu-id="33f8d-128">Specifies the objects that are written to the console.</span></span> <span data-ttu-id="33f8d-129">Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten.</span><span class="sxs-lookup"><span data-stu-id="33f8d-129">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="33f8d-130">-Sid indelning</span><span class="sxs-lookup"><span data-stu-id="33f8d-130">-Paging</span></span>

<span data-ttu-id="33f8d-131">Anger att `Out-Host` visar en sida med utdata i taget och väntar på användarindata innan de återstående sidorna visas.</span><span class="sxs-lookup"><span data-stu-id="33f8d-131">Indicates that `Out-Host` displays one page of output at a time, and waits for user input before the remaining pages are displayed.</span></span> <span data-ttu-id="33f8d-132">Som standard visas alla utdata på en enda sida.</span><span class="sxs-lookup"><span data-stu-id="33f8d-132">By default, all the output is displayed on a single page.</span></span> <span data-ttu-id="33f8d-133">Sid storleken bestäms av egenskaperna för värden.</span><span class="sxs-lookup"><span data-stu-id="33f8d-133">The page size is determined by the characteristics of the host.</span></span>

<span data-ttu-id="33f8d-134">Tryck på <kbd>blank steg</kbd> för att visa nästa sida med utdata eller <kbd>RETUR</kbd> tangenten för att visa nästa rad utdata.</span><span class="sxs-lookup"><span data-stu-id="33f8d-134">Press the <kbd>Space</kbd> bar to display the next page of output or the <kbd>Enter</kbd> key to view the next line of output.</span></span> <span data-ttu-id="33f8d-135">Tryck på <kbd>Q</kbd> för att avsluta.</span><span class="sxs-lookup"><span data-stu-id="33f8d-135">Press <kbd>Q</kbd> to quit.</span></span>

<span data-ttu-id="33f8d-136">**Sid indelning** liknar kommandot **more** .</span><span class="sxs-lookup"><span data-stu-id="33f8d-136">**Paging** is similar to the **more** command.</span></span>

> [!NOTE]
> <span data-ttu-id="33f8d-137">**Växlings** parametern stöds inte av PowerShell ISE-värden.</span><span class="sxs-lookup"><span data-stu-id="33f8d-137">The **Paging** parameter isn't supported by the PowerShell ISE host.</span></span>

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

### <span data-ttu-id="33f8d-138">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="33f8d-138">CommonParameters</span></span>

<span data-ttu-id="33f8d-139">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="33f8d-139">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="33f8d-140">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="33f8d-140">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="33f8d-141">INDATA</span><span class="sxs-lookup"><span data-stu-id="33f8d-141">INPUTS</span></span>

### <span data-ttu-id="33f8d-142">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="33f8d-142">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="33f8d-143">Du kan skicka objekt nedåt i pipelinen till `Out-Host` .</span><span class="sxs-lookup"><span data-stu-id="33f8d-143">You can send objects down the pipeline to `Out-Host`.</span></span>

## <span data-ttu-id="33f8d-144">UTDATA</span><span class="sxs-lookup"><span data-stu-id="33f8d-144">OUTPUTS</span></span>

### <span data-ttu-id="33f8d-145">Inget</span><span class="sxs-lookup"><span data-stu-id="33f8d-145">None</span></span>

<span data-ttu-id="33f8d-146">`Out-Host` genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="33f8d-146">`Out-Host` doesn't generate any output.</span></span> <span data-ttu-id="33f8d-147">Den skickar objekt till värden för visning.</span><span class="sxs-lookup"><span data-stu-id="33f8d-147">It sends objects to the host for display.</span></span>

## <span data-ttu-id="33f8d-148">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="33f8d-148">NOTES</span></span>

<span data-ttu-id="33f8d-149">**Växlings** parametern stöds inte av alla PowerShell-värdar.</span><span class="sxs-lookup"><span data-stu-id="33f8d-149">The **Paging** parameter isn't supported by all PowerShell hosts.</span></span> <span data-ttu-id="33f8d-150">Om du till exempel använder **växlings** parametern i PowerShell ISE visas följande fel: `out-lineoutput : The method or operation is not implemented.`</span><span class="sxs-lookup"><span data-stu-id="33f8d-150">For example, if you use the **Paging** parameter in the PowerShell ISE, the following error is displayed: `out-lineoutput : The method or operation is not implemented.`</span></span>

<span data-ttu-id="33f8d-151">De cmdletar som **innehåller verbet** , `Out-` formaterar inte objekt.</span><span class="sxs-lookup"><span data-stu-id="33f8d-151">The cmdlets that contain the **Out** verb, `Out-`, don't format objects.</span></span> <span data-ttu-id="33f8d-152">De återger objekt och skickar dem till det angivna visnings målet.</span><span class="sxs-lookup"><span data-stu-id="33f8d-152">They render objects and send them to the specified display destination.</span></span> <span data-ttu-id="33f8d-153">Om du skickar ett oformaterat objekt till en `Out-` cmdlet skickar cmdleten den till en formaterings-cmdlet innan du återger den.</span><span class="sxs-lookup"><span data-stu-id="33f8d-153">If you send an unformatted object to an `Out-` cmdlet, the cmdlet sends it to a formatting cmdlet before rendering it.</span></span>

<span data-ttu-id="33f8d-154">`Out-`Cmdletarna har inte parametrar för namn eller fil Sök vägar.</span><span class="sxs-lookup"><span data-stu-id="33f8d-154">The `Out-` cmdlets don't have parameters for names or file paths.</span></span> <span data-ttu-id="33f8d-155">Om du vill skicka data till en `Out-` cmdlet använder du pipelinen för att skicka ett PowerShell-kommandos utdata till cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="33f8d-155">To send data to an `Out-` cmdlet, use the pipeline to send a PowerShell command's output to the cmdlet.</span></span> <span data-ttu-id="33f8d-156">Du kan också lagra data i en variabel och använda parametern **InputObject** för att skicka data till cmdleten.</span><span class="sxs-lookup"><span data-stu-id="33f8d-156">Or, you can store data in a variable and use the **InputObject** parameter to pass the data to the cmdlet.</span></span>

<span data-ttu-id="33f8d-157">`Out-Host` skickar data, men genererar inga utdata-objekt.</span><span class="sxs-lookup"><span data-stu-id="33f8d-157">`Out-Host` sends data, but it doesn't produce any output objects.</span></span> <span data-ttu-id="33f8d-158">Om du pipelinerar utdata från `Out-Host` till `Get-Member` cmdlet: en `Get-Member` rapporteras inga objekt.</span><span class="sxs-lookup"><span data-stu-id="33f8d-158">If you pipeline the output of `Out-Host` to the `Get-Member` cmdlet, `Get-Member` reports that no objects have been specified.</span></span>

## <span data-ttu-id="33f8d-159">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="33f8d-159">RELATED LINKS</span></span>

[<span data-ttu-id="33f8d-160">Rensa värd</span><span class="sxs-lookup"><span data-stu-id="33f8d-160">Clear-Host</span></span>](Clear-Host.md)

[<span data-ttu-id="33f8d-161">Ut-standard</span><span class="sxs-lookup"><span data-stu-id="33f8d-161">Out-Default</span></span>](Out-Default.md)

[<span data-ttu-id="33f8d-162">Ut-fil</span><span class="sxs-lookup"><span data-stu-id="33f8d-162">Out-File</span></span>](../Microsoft.PowerShell.Utility/Out-File.md)

[<span data-ttu-id="33f8d-163">Ut-null</span><span class="sxs-lookup"><span data-stu-id="33f8d-163">Out-Null</span></span>](Out-Null.md)

[<span data-ttu-id="33f8d-164">Out-sträng</span><span class="sxs-lookup"><span data-stu-id="33f8d-164">Out-String</span></span>](../Microsoft.PowerShell.Utility/Out-String.md)

[<span data-ttu-id="33f8d-165">Skriv värd</span><span class="sxs-lookup"><span data-stu-id="33f8d-165">Write-Host</span></span>](../Microsoft.PowerShell.Utility/Write-Host.md)
