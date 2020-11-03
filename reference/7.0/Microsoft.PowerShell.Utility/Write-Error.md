---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-error?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Error
ms.openlocfilehash: 883990ace87c947ad9f0e10100d4d1dc7f1b8cbe
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/16/2020
ms.locfileid: "93272805"
---
# <span data-ttu-id="e5283-103">Write-Error</span><span class="sxs-lookup"><span data-stu-id="e5283-103">Write-Error</span></span>

## <span data-ttu-id="e5283-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="e5283-104">SYNOPSIS</span></span>
<span data-ttu-id="e5283-105">Skriver ett objekt till fel strömmen.</span><span class="sxs-lookup"><span data-stu-id="e5283-105">Writes an object to the error stream.</span></span>

## <span data-ttu-id="e5283-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e5283-106">SYNTAX</span></span>

### <span data-ttu-id="e5283-107">Noexception (standard)</span><span class="sxs-lookup"><span data-stu-id="e5283-107">NoException (Default)</span></span>

```
Write-Error [-Message] <String> [-Category <ErrorCategory>] [-ErrorId <String>] [-TargetObject <Object>]
 [-RecommendedAction <String>] [-CategoryActivity <String>] [-CategoryReason <String>]
 [-CategoryTargetName <String>] [-CategoryTargetType <String>] [<CommonParameters>]
```

### <span data-ttu-id="e5283-108">WithException</span><span class="sxs-lookup"><span data-stu-id="e5283-108">WithException</span></span>

```
Write-Error -Exception <Exception> [-Message <String>] [-Category <ErrorCategory>] [-ErrorId <String>]
 [-TargetObject <Object>] [-RecommendedAction <String>] [-CategoryActivity <String>] [-CategoryReason <String>]
 [-CategoryTargetName <String>] [-CategoryTargetType <String>] [<CommonParameters>]
```

### <span data-ttu-id="e5283-109">ErrorRecord</span><span class="sxs-lookup"><span data-stu-id="e5283-109">ErrorRecord</span></span>

```
Write-Error -ErrorRecord <ErrorRecord> [-RecommendedAction <String>] [-CategoryActivity <String>]
 [-CategoryReason <String>] [-CategoryTargetName <String>] [-CategoryTargetType <String>] [<CommonParameters>]
```

## <span data-ttu-id="e5283-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="e5283-110">DESCRIPTION</span></span>

<span data-ttu-id="e5283-111">`Write-Error`Cmdleten deklarerar ett icke-avslutande fel.</span><span class="sxs-lookup"><span data-stu-id="e5283-111">The `Write-Error` cmdlet declares a non-terminating error.</span></span> <span data-ttu-id="e5283-112">Som standard skickas fel i fel strömmen till värd programmet som ska visas, tillsammans med utdata.</span><span class="sxs-lookup"><span data-stu-id="e5283-112">By default, errors are sent in the error stream to the host program to be displayed, along with output.</span></span>

<span data-ttu-id="e5283-113">Om du vill skriva ett icke-avslutande fel, ange en fel meddelande sträng, ett **ErrorRecord** -objekt eller ett **undantags** objekt.</span><span class="sxs-lookup"><span data-stu-id="e5283-113">To write a non-terminating error, enter an error message string, an **ErrorRecord** object, or an **Exception** object.</span></span> <span data-ttu-id="e5283-114">Använd de andra parametrarna för `Write-Error` för att fylla i fel posten.</span><span class="sxs-lookup"><span data-stu-id="e5283-114">Use the other parameters of `Write-Error` to populate the error record.</span></span>

<span data-ttu-id="e5283-115">Icke-avslutande fel skriver ett fel till fel strömmen, men de stoppar inte kommando bearbetningen.</span><span class="sxs-lookup"><span data-stu-id="e5283-115">Non-terminating errors write an error to the error stream, but they do not stop command processing.</span></span>
<span data-ttu-id="e5283-116">Om ett icke-avslutande fel har deklarerats för ett objekt i en samling ingångs objekt fortsätter kommandot att bearbeta de andra objekten i samlingen.</span><span class="sxs-lookup"><span data-stu-id="e5283-116">If a non-terminating error is declared on one item in a collection of input items, the command continues to process the other items in the collection.</span></span>

<span data-ttu-id="e5283-117">Om du vill deklarera ett avslutande fel använder du `Throw` nyckelordet.</span><span class="sxs-lookup"><span data-stu-id="e5283-117">To declare a terminating error, use the `Throw` keyword.</span></span>
<span data-ttu-id="e5283-118">Mer information finns i [about_Throw](../Microsoft.PowerShell.Core/About/about_Throw.md).</span><span class="sxs-lookup"><span data-stu-id="e5283-118">For more information, see [about_Throw](../Microsoft.PowerShell.Core/About/about_Throw.md).</span></span>

## <span data-ttu-id="e5283-119">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="e5283-119">EXAMPLES</span></span>

### <span data-ttu-id="e5283-120">Exempel 1: Skriv ett fel för RegistryKey-objektet</span><span class="sxs-lookup"><span data-stu-id="e5283-120">Example 1: Write an error for RegistryKey object</span></span>

```powershell
Get-ChildItem | ForEach-Object {
    if ($_.GetType().ToString() -eq "Microsoft.Win32.RegistryKey")
    {
        Write-Error "Invalid object" -ErrorId B1 -TargetObject $_
    }
    else
    {
        $_
    }
}
```

<span data-ttu-id="e5283-121">Det här kommandot deklarerar ett icke-avslutande fel när `Get-ChildItem` cmdleten returnerar ett `Microsoft.Win32.RegistryKey` objekt, t. ex. objekten i- `HKLM:` eller- `HKCU:` enheterna i PowerShell-huvudprovidern.</span><span class="sxs-lookup"><span data-stu-id="e5283-121">This command declares a non-terminating error when the `Get-ChildItem` cmdlet returns a `Microsoft.Win32.RegistryKey` object, such as the objects in the `HKLM:` or `HKCU:` drives of the PowerShell Registry provider.</span></span>

### <span data-ttu-id="e5283-122">Exempel 2: Skriv ett fel meddelande till konsolen</span><span class="sxs-lookup"><span data-stu-id="e5283-122">Example 2: Write an error message to the console</span></span>

```powershell
Write-Error "Access denied."
```

<span data-ttu-id="e5283-123">Det här kommandot deklarerar ett icke-avslutande fel och skriver "åtkomst nekad"-fel.</span><span class="sxs-lookup"><span data-stu-id="e5283-123">This command declares a non-terminating error and writes an "Access denied" error.</span></span> <span data-ttu-id="e5283-124">Kommandot använder **meddelande** parametern för att ange meddelandet, men utelämnar det valfria namnet för **meddelande** parametern.</span><span class="sxs-lookup"><span data-stu-id="e5283-124">The command uses the **Message** parameter to specify the message, but omits the optional **Message** parameter name.</span></span>

### <span data-ttu-id="e5283-125">Exempel 3: Skriv ett fel till konsolen och ange kategorin</span><span class="sxs-lookup"><span data-stu-id="e5283-125">Example 3: Write an error to the console and specify the category</span></span>

```powershell
Write-Error -Message "Error: Too many input values." -Category InvalidArgument
```

<span data-ttu-id="e5283-126">Det här kommandot deklarerar ett icke-avslutande fel och anger en fel kategori.</span><span class="sxs-lookup"><span data-stu-id="e5283-126">This command declares a non-terminating error and specifies an error category.</span></span>

### <span data-ttu-id="e5283-127">Exempel 4: Skriv ett fel med ett undantags objekt</span><span class="sxs-lookup"><span data-stu-id="e5283-127">Example 4: Write an error using an Exception object</span></span>

```powershell
$E = [System.Exception]@{Source="Get-ParameterNames.ps1";HelpLink="https://go.microsoft.com/fwlink/?LinkID=113425"}
Write-Error -Exception $E -Message "Files not found. The $Files location does not contain any XML files."
```

<span data-ttu-id="e5283-128">Det här kommandot använder ett **undantags** objekt för att deklarera ett icke-avslutande fel.</span><span class="sxs-lookup"><span data-stu-id="e5283-128">This command uses an **Exception** object to declare a non-terminating error.</span></span>

<span data-ttu-id="e5283-129">Det första kommandot använder en hash-tabell för att skapa objektet **system. Exception** .</span><span class="sxs-lookup"><span data-stu-id="e5283-129">The first command uses a hash table to create the **System.Exception** object.</span></span> <span data-ttu-id="e5283-130">Det sparar undantags objekt i `$E` variabeln.</span><span class="sxs-lookup"><span data-stu-id="e5283-130">It saves the exception object in the `$E` variable.</span></span> <span data-ttu-id="e5283-131">Du kan använda en hash-tabell för att skapa ett objekt av en typ som har en null-konstruktor.</span><span class="sxs-lookup"><span data-stu-id="e5283-131">You can use a hash table to create any object of a type that has a null constructor.</span></span>

<span data-ttu-id="e5283-132">Det andra kommandot använder `Write-Error` cmdleten för att deklarera ett icke-avslutande fel.</span><span class="sxs-lookup"><span data-stu-id="e5283-132">The second command uses the `Write-Error` cmdlet to declare a non-terminating error.</span></span> <span data-ttu-id="e5283-133">Värdet för parametern **Exception** är **undantags** objekt i `$E` variabeln.</span><span class="sxs-lookup"><span data-stu-id="e5283-133">The value of the **Exception** parameter is the **Exception** object in the `$E` variable.</span></span>

## <span data-ttu-id="e5283-134">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="e5283-134">PARAMETERS</span></span>

### <span data-ttu-id="e5283-135">– Kategori</span><span class="sxs-lookup"><span data-stu-id="e5283-135">-Category</span></span>

<span data-ttu-id="e5283-136">Anger fel kategori.</span><span class="sxs-lookup"><span data-stu-id="e5283-136">Specifies the category of the error.</span></span> <span data-ttu-id="e5283-137">Standardvärdet är **NotSpecified**.</span><span class="sxs-lookup"><span data-stu-id="e5283-137">The default value is **NotSpecified**.</span></span> <span data-ttu-id="e5283-138">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="e5283-138">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="e5283-139">NotSpecified</span><span class="sxs-lookup"><span data-stu-id="e5283-139">NotSpecified</span></span>
- <span data-ttu-id="e5283-140">OpenError</span><span class="sxs-lookup"><span data-stu-id="e5283-140">OpenError</span></span>
- <span data-ttu-id="e5283-141">CloseError</span><span class="sxs-lookup"><span data-stu-id="e5283-141">CloseError</span></span>
- <span data-ttu-id="e5283-142">DeviceError</span><span class="sxs-lookup"><span data-stu-id="e5283-142">DeviceError</span></span>
- <span data-ttu-id="e5283-143">DeadlockDetected</span><span class="sxs-lookup"><span data-stu-id="e5283-143">DeadlockDetected</span></span>
- <span data-ttu-id="e5283-144">InvalidArgument</span><span class="sxs-lookup"><span data-stu-id="e5283-144">InvalidArgument</span></span>
- <span data-ttu-id="e5283-145">InvalidData</span><span class="sxs-lookup"><span data-stu-id="e5283-145">InvalidData</span></span>
- <span data-ttu-id="e5283-146">InvalidOperation</span><span class="sxs-lookup"><span data-stu-id="e5283-146">InvalidOperation</span></span>
- <span data-ttu-id="e5283-147">InvalidResult</span><span class="sxs-lookup"><span data-stu-id="e5283-147">InvalidResult</span></span>
- <span data-ttu-id="e5283-148">InvalidType</span><span class="sxs-lookup"><span data-stu-id="e5283-148">InvalidType</span></span>
- <span data-ttu-id="e5283-149">MetadataError</span><span class="sxs-lookup"><span data-stu-id="e5283-149">MetadataError</span></span>
- <span data-ttu-id="e5283-150">NotImplemented</span><span class="sxs-lookup"><span data-stu-id="e5283-150">NotImplemented</span></span>
- <span data-ttu-id="e5283-151">NotInstalled</span><span class="sxs-lookup"><span data-stu-id="e5283-151">NotInstalled</span></span>
- <span data-ttu-id="e5283-152">ObjectNotFound</span><span class="sxs-lookup"><span data-stu-id="e5283-152">ObjectNotFound</span></span>
- <span data-ttu-id="e5283-153">OperationStopped</span><span class="sxs-lookup"><span data-stu-id="e5283-153">OperationStopped</span></span>
- <span data-ttu-id="e5283-154">OperationTimeout</span><span class="sxs-lookup"><span data-stu-id="e5283-154">OperationTimeout</span></span>
- <span data-ttu-id="e5283-155">SyntaxError</span><span class="sxs-lookup"><span data-stu-id="e5283-155">SyntaxError</span></span>
- <span data-ttu-id="e5283-156">ParserError</span><span class="sxs-lookup"><span data-stu-id="e5283-156">ParserError</span></span>
- <span data-ttu-id="e5283-157">PermissionDenied</span><span class="sxs-lookup"><span data-stu-id="e5283-157">PermissionDenied</span></span>
- <span data-ttu-id="e5283-158">ResourceBusy</span><span class="sxs-lookup"><span data-stu-id="e5283-158">ResourceBusy</span></span>
- <span data-ttu-id="e5283-159">ResourceExists</span><span class="sxs-lookup"><span data-stu-id="e5283-159">ResourceExists</span></span>
- <span data-ttu-id="e5283-160">ResourceUnavailable</span><span class="sxs-lookup"><span data-stu-id="e5283-160">ResourceUnavailable</span></span>
- <span data-ttu-id="e5283-161">ReadError</span><span class="sxs-lookup"><span data-stu-id="e5283-161">ReadError</span></span>
- <span data-ttu-id="e5283-162">WriteError</span><span class="sxs-lookup"><span data-stu-id="e5283-162">WriteError</span></span>
- <span data-ttu-id="e5283-163">FromStdErr</span><span class="sxs-lookup"><span data-stu-id="e5283-163">FromStdErr</span></span>
- <span data-ttu-id="e5283-164">SecurityError</span><span class="sxs-lookup"><span data-stu-id="e5283-164">SecurityError</span></span>
- <span data-ttu-id="e5283-165">ProtocolError</span><span class="sxs-lookup"><span data-stu-id="e5283-165">ProtocolError</span></span>
- <span data-ttu-id="e5283-166">ConnectionError</span><span class="sxs-lookup"><span data-stu-id="e5283-166">ConnectionError</span></span>
- <span data-ttu-id="e5283-167">AuthenticationError</span><span class="sxs-lookup"><span data-stu-id="e5283-167">AuthenticationError</span></span>
- <span data-ttu-id="e5283-168">LimitsExceeded</span><span class="sxs-lookup"><span data-stu-id="e5283-168">LimitsExceeded</span></span>
- <span data-ttu-id="e5283-169">QuotaExceeded</span><span class="sxs-lookup"><span data-stu-id="e5283-169">QuotaExceeded</span></span>
- <span data-ttu-id="e5283-170">NotEnabled</span><span class="sxs-lookup"><span data-stu-id="e5283-170">NotEnabled</span></span>

<span data-ttu-id="e5283-171">Information om fel kategorierna finns i ErrorCategory- [uppräkning](https://go.microsoft.com/fwlink/?LinkId=143600).</span><span class="sxs-lookup"><span data-stu-id="e5283-171">For information about the error categories, see [ErrorCategory Enumeration](https://go.microsoft.com/fwlink/?LinkId=143600).</span></span>

```yaml
Type: System.Management.Automation.ErrorCategory
Parameter Sets: NoException, WithException
Aliases:
Accepted values: NotSpecified, OpenError, CloseError, DeviceError, DeadlockDetected, InvalidArgument, InvalidData, InvalidOperation, InvalidResult, InvalidType, MetadataError, NotImplemented, NotInstalled, ObjectNotFound, OperationStopped, OperationTimeout, SyntaxError, ParserError, PermissionDenied, ResourceBusy, ResourceExists, ResourceUnavailable, ReadError, WriteError, FromStdErr, SecurityError, ProtocolError, ConnectionError, AuthenticationError, LimitsExceeded, QuotaExceeded, NotEnabled

Required: False
Position: Named
Default value: NotSpecified
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e5283-172">-CategoryActivity</span><span class="sxs-lookup"><span data-stu-id="e5283-172">-CategoryActivity</span></span>

<span data-ttu-id="e5283-173">Anger den åtgärd som orsakade felet.</span><span class="sxs-lookup"><span data-stu-id="e5283-173">Specifies the action that caused the error.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Activity

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e5283-174">-CategoryReason</span><span class="sxs-lookup"><span data-stu-id="e5283-174">-CategoryReason</span></span>

<span data-ttu-id="e5283-175">Anger hur eller varför aktiviteten orsakade felet.</span><span class="sxs-lookup"><span data-stu-id="e5283-175">Specifies how or why the activity caused the error.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Reason

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e5283-176">-CategoryTargetName</span><span class="sxs-lookup"><span data-stu-id="e5283-176">-CategoryTargetName</span></span>

<span data-ttu-id="e5283-177">Anger namnet på det objekt som bearbetades när felet uppstod.</span><span class="sxs-lookup"><span data-stu-id="e5283-177">Specifies the name of the object that was being processed when the error occurred.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: TargetName

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e5283-178">-CategoryTargetType</span><span class="sxs-lookup"><span data-stu-id="e5283-178">-CategoryTargetType</span></span>

<span data-ttu-id="e5283-179">Anger vilken typ av objekt som bearbetades när felet inträffade.</span><span class="sxs-lookup"><span data-stu-id="e5283-179">Specifies the type of the object that was being processed when the error occurred.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: TargetType

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e5283-180">-ErrorId</span><span class="sxs-lookup"><span data-stu-id="e5283-180">-ErrorId</span></span>

<span data-ttu-id="e5283-181">Anger en ID-sträng för att identifiera felet.</span><span class="sxs-lookup"><span data-stu-id="e5283-181">Specifies an ID string to identify the error.</span></span> <span data-ttu-id="e5283-182">Strängen ska vara unik för felet.</span><span class="sxs-lookup"><span data-stu-id="e5283-182">The string should be unique to the error.</span></span>

```yaml
Type: System.String
Parameter Sets: NoException, WithException
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e5283-183">-ErrorRecord</span><span class="sxs-lookup"><span data-stu-id="e5283-183">-ErrorRecord</span></span>

<span data-ttu-id="e5283-184">Anger ett fel post objekt som representerar felet.</span><span class="sxs-lookup"><span data-stu-id="e5283-184">Specifies an error record object that represents the error.</span></span> <span data-ttu-id="e5283-185">Använd egenskaperna för objektet för att beskriva felet.</span><span class="sxs-lookup"><span data-stu-id="e5283-185">Use the properties of the object to describe the error.</span></span>

<span data-ttu-id="e5283-186">Om du vill skapa ett fel post objekt använder du `New-Object` cmdleten eller hämtar ett fel post objekt från matrisen i den `$Error` automatiska variabeln.</span><span class="sxs-lookup"><span data-stu-id="e5283-186">To create an error record object, use the `New-Object` cmdlet or get an error record object from the array in the `$Error` automatic variable.</span></span>

```yaml
Type: System.Management.Automation.ErrorRecord
Parameter Sets: ErrorRecord
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e5283-187">– Undantag</span><span class="sxs-lookup"><span data-stu-id="e5283-187">-Exception</span></span>

<span data-ttu-id="e5283-188">Anger ett undantags objekt som representerar felet.</span><span class="sxs-lookup"><span data-stu-id="e5283-188">Specifies an exception object that represents the error.</span></span> <span data-ttu-id="e5283-189">Använd egenskaperna för objektet för att beskriva felet.</span><span class="sxs-lookup"><span data-stu-id="e5283-189">Use the properties of the object to describe the error.</span></span>

<span data-ttu-id="e5283-190">Om du vill skapa ett undantags objekt använder du en hash-tabell eller använder `New-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="e5283-190">To create an exception object, use a hash table or use the `New-Object` cmdlet.</span></span>

```yaml
Type: System.Exception
Parameter Sets: WithException
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e5283-191">– Meddelande</span><span class="sxs-lookup"><span data-stu-id="e5283-191">-Message</span></span>

<span data-ttu-id="e5283-192">Anger meddelande texten för felet.</span><span class="sxs-lookup"><span data-stu-id="e5283-192">Specifies the message text of the error.</span></span> <span data-ttu-id="e5283-193">Om texten innehåller blank steg eller specialtecken, omger du den med citat tecken.</span><span class="sxs-lookup"><span data-stu-id="e5283-193">If the text includes spaces or special characters, enclose it in quotation marks.</span></span> <span data-ttu-id="e5283-194">Du kan också skicka en meddelande sträng till `Write-Error` .</span><span class="sxs-lookup"><span data-stu-id="e5283-194">You can also pipe a message string to `Write-Error`.</span></span>

```yaml
Type: System.String
Parameter Sets: NoException, WithException
Aliases: Msg

Required: True (NoException), False (WithException)
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="e5283-195">-RecommendedAction</span><span class="sxs-lookup"><span data-stu-id="e5283-195">-RecommendedAction</span></span>

<span data-ttu-id="e5283-196">Anger den åtgärd som användaren bör vidta för att lösa eller förhindra felet.</span><span class="sxs-lookup"><span data-stu-id="e5283-196">Specifies the action that the user should take to resolve or prevent the error.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e5283-197">– TargetObject</span><span class="sxs-lookup"><span data-stu-id="e5283-197">-TargetObject</span></span>

<span data-ttu-id="e5283-198">Anger det objekt som bearbetades när felet inträffade.</span><span class="sxs-lookup"><span data-stu-id="e5283-198">Specifies the object that was being processed when the error occurred.</span></span> <span data-ttu-id="e5283-199">Ange objektet, en variabel som innehåller objektet eller ett kommando som hämtar objektet.</span><span class="sxs-lookup"><span data-stu-id="e5283-199">Enter the object, a variable that contains the object, or a command that gets the object.</span></span>

```yaml
Type: System.Object
Parameter Sets: NoException, WithException
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e5283-200">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e5283-200">CommonParameters</span></span>

<span data-ttu-id="e5283-201">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e5283-201">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e5283-202">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="e5283-202">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e5283-203">INDATA</span><span class="sxs-lookup"><span data-stu-id="e5283-203">INPUTS</span></span>

### <span data-ttu-id="e5283-204">System. String</span><span class="sxs-lookup"><span data-stu-id="e5283-204">System.String</span></span>

<span data-ttu-id="e5283-205">Du kan skicka vidare en sträng som innehåller ett fel meddelande till `Write-Error` .</span><span class="sxs-lookup"><span data-stu-id="e5283-205">You can pipe a string that contains an error message to `Write-Error`.</span></span>

## <span data-ttu-id="e5283-206">UTDATA</span><span class="sxs-lookup"><span data-stu-id="e5283-206">OUTPUTS</span></span>

### <span data-ttu-id="e5283-207">Fel objekt</span><span class="sxs-lookup"><span data-stu-id="e5283-207">Error object</span></span>

<span data-ttu-id="e5283-208">`Write-Error` skriver endast till fel strömmen.</span><span class="sxs-lookup"><span data-stu-id="e5283-208">`Write-Error` writes only to the error stream.</span></span> <span data-ttu-id="e5283-209">Det returnerar inga objekt.</span><span class="sxs-lookup"><span data-stu-id="e5283-209">It does not return any objects.</span></span>

## <span data-ttu-id="e5283-210">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="e5283-210">NOTES</span></span>

<span data-ttu-id="e5283-211">`Write-Error` ändrar inte värdet för den `$?` automatiska variabeln, och därför signalerar det inte ett avslutande fel villkor.</span><span class="sxs-lookup"><span data-stu-id="e5283-211">`Write-Error` does not change the value of the `$?` automatic variable, therefore it does not signal a terminating error condition.</span></span> <span data-ttu-id="e5283-212">Om du vill signalera ett avslutande fel använder du metoden [$PSCmdlet. WriteError ()](/dotnet/api/system.management.automation.cmdlet.writeerror) .</span><span class="sxs-lookup"><span data-stu-id="e5283-212">To signal a terminating error, use the [$PSCmdlet.WriteError()](/dotnet/api/system.management.automation.cmdlet.writeerror) method.</span></span>

## <span data-ttu-id="e5283-213">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="e5283-213">RELATED LINKS</span></span>

[<span data-ttu-id="e5283-214">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="e5283-214">about_Automatic_Variables</span></span>](../microsoft.powershell.core/about/about_automatic_variables.md)

[<span data-ttu-id="e5283-215">about_Output_Streams</span><span class="sxs-lookup"><span data-stu-id="e5283-215">about_Output_Streams</span></span>](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[<span data-ttu-id="e5283-216">about_Redirection</span><span class="sxs-lookup"><span data-stu-id="e5283-216">about_Redirection</span></span>](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[<span data-ttu-id="e5283-217">Skriv-debug</span><span class="sxs-lookup"><span data-stu-id="e5283-217">Write-Debug</span></span>](Write-Debug.md)

[<span data-ttu-id="e5283-218">Skriv värd</span><span class="sxs-lookup"><span data-stu-id="e5283-218">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="e5283-219">Skriva-utdata</span><span class="sxs-lookup"><span data-stu-id="e5283-219">Write-Output</span></span>](Write-Output.md)

[<span data-ttu-id="e5283-220">Skriv förlopp</span><span class="sxs-lookup"><span data-stu-id="e5283-220">Write-Progress</span></span>](Write-Progress.md)

[<span data-ttu-id="e5283-221">Skriv-verbose</span><span class="sxs-lookup"><span data-stu-id="e5283-221">Write-Verbose</span></span>](Write-Verbose.md)

[<span data-ttu-id="e5283-222">Skriv varning</span><span class="sxs-lookup"><span data-stu-id="e5283-222">Write-Warning</span></span>](Write-Warning.md)
