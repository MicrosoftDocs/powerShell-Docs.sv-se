---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-error?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Error
ms.openlocfilehash: d0ee66e1002e4f1d58f63e198bcb7f03b1c8d3a8
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709373"
---
# <span data-ttu-id="27c5d-102">Write-Error</span><span class="sxs-lookup"><span data-stu-id="27c5d-102">Write-Error</span></span>

## <span data-ttu-id="27c5d-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="27c5d-103">SYNOPSIS</span></span>
<span data-ttu-id="27c5d-104">Skriver ett objekt till fel strömmen.</span><span class="sxs-lookup"><span data-stu-id="27c5d-104">Writes an object to the error stream.</span></span>

## <span data-ttu-id="27c5d-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="27c5d-105">SYNTAX</span></span>

### <span data-ttu-id="27c5d-106">Noexception (standard)</span><span class="sxs-lookup"><span data-stu-id="27c5d-106">NoException (Default)</span></span>

```
Write-Error [-Message] <String> [-Category <ErrorCategory>] [-ErrorId <String>] [-TargetObject <Object>]
 [-RecommendedAction <String>] [-CategoryActivity <String>] [-CategoryReason <String>]
 [-CategoryTargetName <String>] [-CategoryTargetType <String>] [<CommonParameters>]
```

### <span data-ttu-id="27c5d-107">WithException</span><span class="sxs-lookup"><span data-stu-id="27c5d-107">WithException</span></span>

```
Write-Error -Exception <Exception> [[-Message] <String>] [-Category <ErrorCategory>] [-ErrorId <String>]
 [-TargetObject <Object>] [-RecommendedAction <String>] [-CategoryActivity <String>] [-CategoryReason <String>]
 [-CategoryTargetName <String>] [-CategoryTargetType <String>] [<CommonParameters>]
```

### <span data-ttu-id="27c5d-108">ErrorRecord</span><span class="sxs-lookup"><span data-stu-id="27c5d-108">ErrorRecord</span></span>

```
Write-Error -ErrorRecord <ErrorRecord> [-RecommendedAction <String>] [-CategoryActivity <String>]
 [-CategoryReason <String>] [-CategoryTargetName <String>] [-CategoryTargetType <String>] [<CommonParameters>]
```

## <span data-ttu-id="27c5d-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="27c5d-109">DESCRIPTION</span></span>

<span data-ttu-id="27c5d-110">`Write-Error`Cmdleten deklarerar ett icke-avslutande fel.</span><span class="sxs-lookup"><span data-stu-id="27c5d-110">The `Write-Error` cmdlet declares a non-terminating error.</span></span> <span data-ttu-id="27c5d-111">Som standard skickas fel i fel strömmen till värd programmet som ska visas, tillsammans med utdata.</span><span class="sxs-lookup"><span data-stu-id="27c5d-111">By default, errors are sent in the error stream to the host program to be displayed, along with output.</span></span>

<span data-ttu-id="27c5d-112">Om du vill skriva ett icke-avslutande fel, ange en fel meddelande sträng, ett **ErrorRecord** -objekt eller ett **undantags** objekt.</span><span class="sxs-lookup"><span data-stu-id="27c5d-112">To write a non-terminating error, enter an error message string, an **ErrorRecord** object, or an **Exception** object.</span></span> <span data-ttu-id="27c5d-113">Använd de andra parametrarna för `Write-Error` för att fylla i fel posten.</span><span class="sxs-lookup"><span data-stu-id="27c5d-113">Use the other parameters of `Write-Error` to populate the error record.</span></span>

<span data-ttu-id="27c5d-114">Icke-avslutande fel skriver ett fel till fel strömmen, men de stoppar inte kommando bearbetningen.</span><span class="sxs-lookup"><span data-stu-id="27c5d-114">Non-terminating errors write an error to the error stream, but they do not stop command processing.</span></span>
<span data-ttu-id="27c5d-115">Om ett icke-avslutande fel har deklarerats för ett objekt i en samling ingångs objekt fortsätter kommandot att bearbeta de andra objekten i samlingen.</span><span class="sxs-lookup"><span data-stu-id="27c5d-115">If a non-terminating error is declared on one item in a collection of input items, the command continues to process the other items in the collection.</span></span>

<span data-ttu-id="27c5d-116">Om du vill deklarera ett avslutande fel använder du `Throw` nyckelordet.</span><span class="sxs-lookup"><span data-stu-id="27c5d-116">To declare a terminating error, use the `Throw` keyword.</span></span>
<span data-ttu-id="27c5d-117">Mer information finns i [about_Throw](../Microsoft.PowerShell.Core/About/about_Throw.md).</span><span class="sxs-lookup"><span data-stu-id="27c5d-117">For more information, see [about_Throw](../Microsoft.PowerShell.Core/About/about_Throw.md).</span></span>

## <span data-ttu-id="27c5d-118">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="27c5d-118">EXAMPLES</span></span>

### <span data-ttu-id="27c5d-119">Exempel 1: Skriv ett fel för RegistryKey-objektet</span><span class="sxs-lookup"><span data-stu-id="27c5d-119">Example 1: Write an error for RegistryKey object</span></span>

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

<span data-ttu-id="27c5d-120">Det här kommandot deklarerar ett icke-avslutande fel när `Get-ChildItem` cmdleten returnerar ett `Microsoft.Win32.RegistryKey` objekt, t. ex. objekten i- `HKLM:` eller- `HKCU:` enheterna i PowerShell-huvudprovidern.</span><span class="sxs-lookup"><span data-stu-id="27c5d-120">This command declares a non-terminating error when the `Get-ChildItem` cmdlet returns a `Microsoft.Win32.RegistryKey` object, such as the objects in the `HKLM:` or `HKCU:` drives of the PowerShell Registry provider.</span></span>

### <span data-ttu-id="27c5d-121">Exempel 2: Skriv ett fel meddelande till konsolen</span><span class="sxs-lookup"><span data-stu-id="27c5d-121">Example 2: Write an error message to the console</span></span>

```powershell
Write-Error "Access denied."
```

<span data-ttu-id="27c5d-122">Det här kommandot deklarerar ett icke-avslutande fel och skriver "åtkomst nekad"-fel.</span><span class="sxs-lookup"><span data-stu-id="27c5d-122">This command declares a non-terminating error and writes an "Access denied" error.</span></span> <span data-ttu-id="27c5d-123">Kommandot använder **meddelande** parametern för att ange meddelandet, men utelämnar det valfria namnet för **meddelande** parametern.</span><span class="sxs-lookup"><span data-stu-id="27c5d-123">The command uses the **Message** parameter to specify the message, but omits the optional **Message** parameter name.</span></span>

### <span data-ttu-id="27c5d-124">Exempel 3: Skriv ett fel till konsolen och ange kategorin</span><span class="sxs-lookup"><span data-stu-id="27c5d-124">Example 3: Write an error to the console and specify the category</span></span>

```powershell
Write-Error -Message "Error: Too many input values." -Category InvalidArgument
```

<span data-ttu-id="27c5d-125">Det här kommandot deklarerar ett icke-avslutande fel och anger en fel kategori.</span><span class="sxs-lookup"><span data-stu-id="27c5d-125">This command declares a non-terminating error and specifies an error category.</span></span>

### <span data-ttu-id="27c5d-126">Exempel 4: Skriv ett fel med ett undantags objekt</span><span class="sxs-lookup"><span data-stu-id="27c5d-126">Example 4: Write an error using an Exception object</span></span>

```powershell
$E = [System.Exception]@{Source="Get-ParameterNames.ps1";HelpLink="https://go.microsoft.com/fwlink/?LinkID=113425"}
Write-Error -Exception $E -Message "Files not found. The $Files location does not contain any XML files."
```

<span data-ttu-id="27c5d-127">Det här kommandot använder ett **undantags** objekt för att deklarera ett icke-avslutande fel.</span><span class="sxs-lookup"><span data-stu-id="27c5d-127">This command uses an **Exception** object to declare a non-terminating error.</span></span>

<span data-ttu-id="27c5d-128">Det första kommandot använder en hash-tabell för att skapa objektet **system. Exception** .</span><span class="sxs-lookup"><span data-stu-id="27c5d-128">The first command uses a hash table to create the **System.Exception** object.</span></span> <span data-ttu-id="27c5d-129">Det sparar undantags objekt i `$E` variabeln.</span><span class="sxs-lookup"><span data-stu-id="27c5d-129">It saves the exception object in the `$E` variable.</span></span> <span data-ttu-id="27c5d-130">Du kan använda en hash-tabell för att skapa ett objekt av en typ som har en null-konstruktor.</span><span class="sxs-lookup"><span data-stu-id="27c5d-130">You can use a hash table to create any object of a type that has a null constructor.</span></span>

<span data-ttu-id="27c5d-131">Det andra kommandot använder `Write-Error` cmdleten för att deklarera ett icke-avslutande fel.</span><span class="sxs-lookup"><span data-stu-id="27c5d-131">The second command uses the `Write-Error` cmdlet to declare a non-terminating error.</span></span> <span data-ttu-id="27c5d-132">Värdet för parametern **Exception** är **undantags** objekt i `$E` variabeln.</span><span class="sxs-lookup"><span data-stu-id="27c5d-132">The value of the **Exception** parameter is the **Exception** object in the `$E` variable.</span></span>

## <span data-ttu-id="27c5d-133">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="27c5d-133">PARAMETERS</span></span>

### <span data-ttu-id="27c5d-134">– Kategori</span><span class="sxs-lookup"><span data-stu-id="27c5d-134">-Category</span></span>

<span data-ttu-id="27c5d-135">Anger fel kategori.</span><span class="sxs-lookup"><span data-stu-id="27c5d-135">Specifies the category of the error.</span></span> <span data-ttu-id="27c5d-136">Standardvärdet är **NotSpecified**.</span><span class="sxs-lookup"><span data-stu-id="27c5d-136">The default value is **NotSpecified**.</span></span> <span data-ttu-id="27c5d-137">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="27c5d-137">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="27c5d-138">NotSpecified</span><span class="sxs-lookup"><span data-stu-id="27c5d-138">NotSpecified</span></span>
- <span data-ttu-id="27c5d-139">OpenError</span><span class="sxs-lookup"><span data-stu-id="27c5d-139">OpenError</span></span>
- <span data-ttu-id="27c5d-140">CloseError</span><span class="sxs-lookup"><span data-stu-id="27c5d-140">CloseError</span></span>
- <span data-ttu-id="27c5d-141">DeviceError</span><span class="sxs-lookup"><span data-stu-id="27c5d-141">DeviceError</span></span>
- <span data-ttu-id="27c5d-142">DeadlockDetected</span><span class="sxs-lookup"><span data-stu-id="27c5d-142">DeadlockDetected</span></span>
- <span data-ttu-id="27c5d-143">InvalidArgument</span><span class="sxs-lookup"><span data-stu-id="27c5d-143">InvalidArgument</span></span>
- <span data-ttu-id="27c5d-144">InvalidData</span><span class="sxs-lookup"><span data-stu-id="27c5d-144">InvalidData</span></span>
- <span data-ttu-id="27c5d-145">InvalidOperation</span><span class="sxs-lookup"><span data-stu-id="27c5d-145">InvalidOperation</span></span>
- <span data-ttu-id="27c5d-146">InvalidResult</span><span class="sxs-lookup"><span data-stu-id="27c5d-146">InvalidResult</span></span>
- <span data-ttu-id="27c5d-147">InvalidType</span><span class="sxs-lookup"><span data-stu-id="27c5d-147">InvalidType</span></span>
- <span data-ttu-id="27c5d-148">MetadataError</span><span class="sxs-lookup"><span data-stu-id="27c5d-148">MetadataError</span></span>
- <span data-ttu-id="27c5d-149">NotImplemented</span><span class="sxs-lookup"><span data-stu-id="27c5d-149">NotImplemented</span></span>
- <span data-ttu-id="27c5d-150">NotInstalled</span><span class="sxs-lookup"><span data-stu-id="27c5d-150">NotInstalled</span></span>
- <span data-ttu-id="27c5d-151">ObjectNotFound</span><span class="sxs-lookup"><span data-stu-id="27c5d-151">ObjectNotFound</span></span>
- <span data-ttu-id="27c5d-152">OperationStopped</span><span class="sxs-lookup"><span data-stu-id="27c5d-152">OperationStopped</span></span>
- <span data-ttu-id="27c5d-153">OperationTimeout</span><span class="sxs-lookup"><span data-stu-id="27c5d-153">OperationTimeout</span></span>
- <span data-ttu-id="27c5d-154">SyntaxError</span><span class="sxs-lookup"><span data-stu-id="27c5d-154">SyntaxError</span></span>
- <span data-ttu-id="27c5d-155">ParserError</span><span class="sxs-lookup"><span data-stu-id="27c5d-155">ParserError</span></span>
- <span data-ttu-id="27c5d-156">PermissionDenied</span><span class="sxs-lookup"><span data-stu-id="27c5d-156">PermissionDenied</span></span>
- <span data-ttu-id="27c5d-157">ResourceBusy</span><span class="sxs-lookup"><span data-stu-id="27c5d-157">ResourceBusy</span></span>
- <span data-ttu-id="27c5d-158">ResourceExists</span><span class="sxs-lookup"><span data-stu-id="27c5d-158">ResourceExists</span></span>
- <span data-ttu-id="27c5d-159">ResourceUnavailable</span><span class="sxs-lookup"><span data-stu-id="27c5d-159">ResourceUnavailable</span></span>
- <span data-ttu-id="27c5d-160">ReadError</span><span class="sxs-lookup"><span data-stu-id="27c5d-160">ReadError</span></span>
- <span data-ttu-id="27c5d-161">WriteError</span><span class="sxs-lookup"><span data-stu-id="27c5d-161">WriteError</span></span>
- <span data-ttu-id="27c5d-162">FromStdErr</span><span class="sxs-lookup"><span data-stu-id="27c5d-162">FromStdErr</span></span>
- <span data-ttu-id="27c5d-163">SecurityError</span><span class="sxs-lookup"><span data-stu-id="27c5d-163">SecurityError</span></span>
- <span data-ttu-id="27c5d-164">ProtocolError</span><span class="sxs-lookup"><span data-stu-id="27c5d-164">ProtocolError</span></span>
- <span data-ttu-id="27c5d-165">ConnectionError</span><span class="sxs-lookup"><span data-stu-id="27c5d-165">ConnectionError</span></span>
- <span data-ttu-id="27c5d-166">AuthenticationError</span><span class="sxs-lookup"><span data-stu-id="27c5d-166">AuthenticationError</span></span>
- <span data-ttu-id="27c5d-167">LimitsExceeded</span><span class="sxs-lookup"><span data-stu-id="27c5d-167">LimitsExceeded</span></span>
- <span data-ttu-id="27c5d-168">QuotaExceeded</span><span class="sxs-lookup"><span data-stu-id="27c5d-168">QuotaExceeded</span></span>
- <span data-ttu-id="27c5d-169">NotEnabled</span><span class="sxs-lookup"><span data-stu-id="27c5d-169">NotEnabled</span></span>

<span data-ttu-id="27c5d-170">Information om fel kategorierna finns i ErrorCategory- [uppräkning](https://go.microsoft.com/fwlink/?LinkId=143600).</span><span class="sxs-lookup"><span data-stu-id="27c5d-170">For information about the error categories, see [ErrorCategory Enumeration](https://go.microsoft.com/fwlink/?LinkId=143600).</span></span>

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

### <span data-ttu-id="27c5d-171">-CategoryActivity</span><span class="sxs-lookup"><span data-stu-id="27c5d-171">-CategoryActivity</span></span>

<span data-ttu-id="27c5d-172">Anger den åtgärd som orsakade felet.</span><span class="sxs-lookup"><span data-stu-id="27c5d-172">Specifies the action that caused the error.</span></span>

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

### <span data-ttu-id="27c5d-173">-CategoryReason</span><span class="sxs-lookup"><span data-stu-id="27c5d-173">-CategoryReason</span></span>

<span data-ttu-id="27c5d-174">Anger hur eller varför aktiviteten orsakade felet.</span><span class="sxs-lookup"><span data-stu-id="27c5d-174">Specifies how or why the activity caused the error.</span></span>

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

### <span data-ttu-id="27c5d-175">-CategoryTargetName</span><span class="sxs-lookup"><span data-stu-id="27c5d-175">-CategoryTargetName</span></span>

<span data-ttu-id="27c5d-176">Anger namnet på det objekt som bearbetades när felet uppstod.</span><span class="sxs-lookup"><span data-stu-id="27c5d-176">Specifies the name of the object that was being processed when the error occurred.</span></span>

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

### <span data-ttu-id="27c5d-177">-CategoryTargetType</span><span class="sxs-lookup"><span data-stu-id="27c5d-177">-CategoryTargetType</span></span>

<span data-ttu-id="27c5d-178">Anger vilken typ av objekt som bearbetades när felet inträffade.</span><span class="sxs-lookup"><span data-stu-id="27c5d-178">Specifies the type of the object that was being processed when the error occurred.</span></span>

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

### <span data-ttu-id="27c5d-179">-ErrorId</span><span class="sxs-lookup"><span data-stu-id="27c5d-179">-ErrorId</span></span>

<span data-ttu-id="27c5d-180">Anger en ID-sträng för att identifiera felet.</span><span class="sxs-lookup"><span data-stu-id="27c5d-180">Specifies an ID string to identify the error.</span></span> <span data-ttu-id="27c5d-181">Strängen ska vara unik för felet.</span><span class="sxs-lookup"><span data-stu-id="27c5d-181">The string should be unique to the error.</span></span>

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

### <span data-ttu-id="27c5d-182">-ErrorRecord</span><span class="sxs-lookup"><span data-stu-id="27c5d-182">-ErrorRecord</span></span>

<span data-ttu-id="27c5d-183">Anger ett fel post objekt som representerar felet.</span><span class="sxs-lookup"><span data-stu-id="27c5d-183">Specifies an error record object that represents the error.</span></span> <span data-ttu-id="27c5d-184">Använd egenskaperna för objektet för att beskriva felet.</span><span class="sxs-lookup"><span data-stu-id="27c5d-184">Use the properties of the object to describe the error.</span></span>

<span data-ttu-id="27c5d-185">Om du vill skapa ett fel post objekt använder du `New-Object` cmdleten eller hämtar ett fel post objekt från matrisen i den `$Error` automatiska variabeln.</span><span class="sxs-lookup"><span data-stu-id="27c5d-185">To create an error record object, use the `New-Object` cmdlet or get an error record object from the array in the `$Error` automatic variable.</span></span>

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

### <span data-ttu-id="27c5d-186">– Undantag</span><span class="sxs-lookup"><span data-stu-id="27c5d-186">-Exception</span></span>

<span data-ttu-id="27c5d-187">Anger ett undantags objekt som representerar felet.</span><span class="sxs-lookup"><span data-stu-id="27c5d-187">Specifies an exception object that represents the error.</span></span> <span data-ttu-id="27c5d-188">Använd egenskaperna för objektet för att beskriva felet.</span><span class="sxs-lookup"><span data-stu-id="27c5d-188">Use the properties of the object to describe the error.</span></span>

<span data-ttu-id="27c5d-189">Om du vill skapa ett undantags objekt använder du en hash-tabell eller använder `New-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="27c5d-189">To create an exception object, use a hash table or use the `New-Object` cmdlet.</span></span>

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

### <span data-ttu-id="27c5d-190">– Meddelande</span><span class="sxs-lookup"><span data-stu-id="27c5d-190">-Message</span></span>

<span data-ttu-id="27c5d-191">Anger meddelande texten för felet.</span><span class="sxs-lookup"><span data-stu-id="27c5d-191">Specifies the message text of the error.</span></span> <span data-ttu-id="27c5d-192">Om texten innehåller blank steg eller specialtecken, omger du den med citat tecken.</span><span class="sxs-lookup"><span data-stu-id="27c5d-192">If the text includes spaces or special characters, enclose it in quotation marks.</span></span> <span data-ttu-id="27c5d-193">Du kan också skicka en meddelande sträng till `Write-Error` .</span><span class="sxs-lookup"><span data-stu-id="27c5d-193">You can also pipe a message string to `Write-Error`.</span></span>

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

### <span data-ttu-id="27c5d-194">-RecommendedAction</span><span class="sxs-lookup"><span data-stu-id="27c5d-194">-RecommendedAction</span></span>

<span data-ttu-id="27c5d-195">Anger den åtgärd som användaren bör vidta för att lösa eller förhindra felet.</span><span class="sxs-lookup"><span data-stu-id="27c5d-195">Specifies the action that the user should take to resolve or prevent the error.</span></span>

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

### <span data-ttu-id="27c5d-196">– TargetObject</span><span class="sxs-lookup"><span data-stu-id="27c5d-196">-TargetObject</span></span>

<span data-ttu-id="27c5d-197">Anger det objekt som bearbetades när felet inträffade.</span><span class="sxs-lookup"><span data-stu-id="27c5d-197">Specifies the object that was being processed when the error occurred.</span></span> <span data-ttu-id="27c5d-198">Ange objektet, en variabel som innehåller objektet eller ett kommando som hämtar objektet.</span><span class="sxs-lookup"><span data-stu-id="27c5d-198">Enter the object, a variable that contains the object, or a command that gets the object.</span></span>

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

### <span data-ttu-id="27c5d-199">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="27c5d-199">CommonParameters</span></span>

<span data-ttu-id="27c5d-200">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="27c5d-200">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="27c5d-201">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="27c5d-201">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="27c5d-202">INDATA</span><span class="sxs-lookup"><span data-stu-id="27c5d-202">INPUTS</span></span>

### <span data-ttu-id="27c5d-203">System. String</span><span class="sxs-lookup"><span data-stu-id="27c5d-203">System.String</span></span>

<span data-ttu-id="27c5d-204">Du kan skicka vidare en sträng som innehåller ett fel meddelande till `Write-Error` .</span><span class="sxs-lookup"><span data-stu-id="27c5d-204">You can pipe a string that contains an error message to `Write-Error`.</span></span>

## <span data-ttu-id="27c5d-205">UTDATA</span><span class="sxs-lookup"><span data-stu-id="27c5d-205">OUTPUTS</span></span>

### <span data-ttu-id="27c5d-206">Fel objekt</span><span class="sxs-lookup"><span data-stu-id="27c5d-206">Error object</span></span>

<span data-ttu-id="27c5d-207">`Write-Error` skriver endast till fel strömmen.</span><span class="sxs-lookup"><span data-stu-id="27c5d-207">`Write-Error` writes only to the error stream.</span></span> <span data-ttu-id="27c5d-208">Det returnerar inga objekt.</span><span class="sxs-lookup"><span data-stu-id="27c5d-208">It does not return any objects.</span></span>

## <span data-ttu-id="27c5d-209">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="27c5d-209">NOTES</span></span>

<span data-ttu-id="27c5d-210">`Write-Error` ändrar inte värdet för den `$?` automatiska variabeln, och därför signalerar det inte ett avslutande fel villkor.</span><span class="sxs-lookup"><span data-stu-id="27c5d-210">`Write-Error` does not change the value of the `$?` automatic variable, therefore it does not signal a terminating error condition.</span></span> <span data-ttu-id="27c5d-211">Om du vill signalera ett avslutande fel använder du metoden [$PSCmdlet. WriteError ()](/dotnet/api/system.management.automation.cmdlet.writeerror) .</span><span class="sxs-lookup"><span data-stu-id="27c5d-211">To signal a terminating error, use the [$PSCmdlet.WriteError()](/dotnet/api/system.management.automation.cmdlet.writeerror) method.</span></span>

## <span data-ttu-id="27c5d-212">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="27c5d-212">RELATED LINKS</span></span>

[<span data-ttu-id="27c5d-213">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="27c5d-213">about_Automatic_Variables</span></span>](../microsoft.powershell.core/about/about_automatic_variables.md)

[<span data-ttu-id="27c5d-214">about_Output_Streams</span><span class="sxs-lookup"><span data-stu-id="27c5d-214">about_Output_Streams</span></span>](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[<span data-ttu-id="27c5d-215">about_Redirection</span><span class="sxs-lookup"><span data-stu-id="27c5d-215">about_Redirection</span></span>](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[<span data-ttu-id="27c5d-216">Skriv-debug</span><span class="sxs-lookup"><span data-stu-id="27c5d-216">Write-Debug</span></span>](Write-Debug.md)

[<span data-ttu-id="27c5d-217">Skriv värd</span><span class="sxs-lookup"><span data-stu-id="27c5d-217">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="27c5d-218">Skriva-utdata</span><span class="sxs-lookup"><span data-stu-id="27c5d-218">Write-Output</span></span>](Write-Output.md)

[<span data-ttu-id="27c5d-219">Skriv förlopp</span><span class="sxs-lookup"><span data-stu-id="27c5d-219">Write-Progress</span></span>](Write-Progress.md)

[<span data-ttu-id="27c5d-220">Skriv-verbose</span><span class="sxs-lookup"><span data-stu-id="27c5d-220">Write-Verbose</span></span>](Write-Verbose.md)

[<span data-ttu-id="27c5d-221">Skriv varning</span><span class="sxs-lookup"><span data-stu-id="27c5d-221">Write-Warning</span></span>](Write-Warning.md)
