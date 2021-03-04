---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/02/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Read-Host
ms.openlocfilehash: 1c799a5b0f9041d285ce0e83a98582d6888c607e
ms.sourcegitcommit: 1dfd5554b70c7e8f4e3df19e29c384a9c0a4b227
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/03/2021
ms.locfileid: "101685309"
---
# <span data-ttu-id="0770a-103">Read-Host</span><span class="sxs-lookup"><span data-stu-id="0770a-103">Read-Host</span></span>

## <span data-ttu-id="0770a-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="0770a-104">SYNOPSIS</span></span>
<span data-ttu-id="0770a-105">Läser en rad med ininformation från-konsolen.</span><span class="sxs-lookup"><span data-stu-id="0770a-105">Reads a line of input from the console.</span></span>

## <span data-ttu-id="0770a-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="0770a-106">SYNTAX</span></span>

### <span data-ttu-id="0770a-107">Uppsträng (standard)</span><span class="sxs-lookup"><span data-stu-id="0770a-107">AsString (Default)</span></span>

```
Read-Host [[-Prompt] <Object>] [-MaskInput] [<CommonParameters>]
```

### <span data-ttu-id="0770a-108">AsSecureString</span><span class="sxs-lookup"><span data-stu-id="0770a-108">AsSecureString</span></span>

```
Read-Host [[-Prompt] <Object>] [-AsSecureString] [<CommonParameters>]
```

## <span data-ttu-id="0770a-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="0770a-109">DESCRIPTION</span></span>

<span data-ttu-id="0770a-110">`Read-Host`Cmdlet: en läser en rad med ininformation från-konsolen.</span><span class="sxs-lookup"><span data-stu-id="0770a-110">The `Read-Host` cmdlet reads a line of input from the console.</span></span> <span data-ttu-id="0770a-111">Du kan använda den för att uppmana användaren att ange indata.</span><span class="sxs-lookup"><span data-stu-id="0770a-111">You can use it to prompt a user for input.</span></span> <span data-ttu-id="0770a-112">Eftersom du kan spara indata som en säker sträng kan du använda denna cmdlet för att uppmana användarna att ange säkra data, till exempel lösen ord, samt delade data.</span><span class="sxs-lookup"><span data-stu-id="0770a-112">Because you can save the input as a secure string, you can use this cmdlet to prompt users for secure data, such as passwords, as well as shared data.</span></span>

> [!NOTE]
> <span data-ttu-id="0770a-113">`Read-Host` har en gräns på 1022 tecken som kan accepteras som indata från en användare.</span><span class="sxs-lookup"><span data-stu-id="0770a-113">`Read-Host` has a limit of 1022 characters it can accept as input from a user.</span></span>

## <span data-ttu-id="0770a-114">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="0770a-114">EXAMPLES</span></span>

### <span data-ttu-id="0770a-115">Exempel 1: Spara konsol indata till en variabel</span><span class="sxs-lookup"><span data-stu-id="0770a-115">Example 1: Save console input to a variable</span></span>

<span data-ttu-id="0770a-116">Det här exemplet visar strängen "Ange din ålder:" som en prompt.</span><span class="sxs-lookup"><span data-stu-id="0770a-116">This example displays the string "Please enter your age:" as a prompt.</span></span> <span data-ttu-id="0770a-117">När ett värde anges och tangenten Enter trycks ned, lagras värdet i `$Age` variabeln.</span><span class="sxs-lookup"><span data-stu-id="0770a-117">When a value is entered and the Enter key is pressed, the value is stored in the `$Age` variable.</span></span>

```powershell
$Age = Read-Host "Please enter your age"
```

### <span data-ttu-id="0770a-118">Exempel 2: Spara konsol indata som en säker sträng</span><span class="sxs-lookup"><span data-stu-id="0770a-118">Example 2: Save console input as a secure string</span></span>

<span data-ttu-id="0770a-119">I det här exemplet visas strängen "Ange ett lösen ord:" som en prompt.</span><span class="sxs-lookup"><span data-stu-id="0770a-119">This example displays the string "Enter a Password:" as a prompt.</span></span> <span data-ttu-id="0770a-120">När ett värde anges visas asterisker () i- `*` konsolen i stället för indatamängden.</span><span class="sxs-lookup"><span data-stu-id="0770a-120">As a value is being entered, asterisks (`*`) appear on the console in place of the input.</span></span> <span data-ttu-id="0770a-121">När ENTER-tangenten trycks ned, lagras värdet som ett **SecureString** -objekt i `$pwd_secure_string` variabeln.</span><span class="sxs-lookup"><span data-stu-id="0770a-121">When the Enter key is pressed, the value is stored as a **SecureString** object in the `$pwd_secure_string` variable.</span></span>

```powershell
$pwd_secure_string = Read-Host "Enter a Password" -AsSecureString
```

### <span data-ttu-id="0770a-122">Exempel 3: maskera inmatade och som en oformaterad text sträng</span><span class="sxs-lookup"><span data-stu-id="0770a-122">Example 3: Mask input and as a plaintext string</span></span>

<span data-ttu-id="0770a-123">I det här exemplet visas strängen "Ange ett lösen ord:" som en prompt.</span><span class="sxs-lookup"><span data-stu-id="0770a-123">This example displays the string "Enter a Password:" as a prompt.</span></span> <span data-ttu-id="0770a-124">När ett värde anges visas asterisker () i- `*` konsolen i stället för indatamängden.</span><span class="sxs-lookup"><span data-stu-id="0770a-124">As a value is being entered, asterisks (`*`) appear on the console in place of the input.</span></span> <span data-ttu-id="0770a-125">När ENTER-tangenten trycks ned, lagras värdet som **ett text objekt** i klartext i `$pwd_string` variabeln.</span><span class="sxs-lookup"><span data-stu-id="0770a-125">When the Enter key is pressed, the value is stored as a plaintext **String** object in the `$pwd_string` variable.</span></span>

```powershell
$pwd_string = Read-Host "Enter a Password" -MaskInput
```

## <span data-ttu-id="0770a-126">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="0770a-126">PARAMETERS</span></span>

### <span data-ttu-id="0770a-127">– AsSecureString</span><span class="sxs-lookup"><span data-stu-id="0770a-127">-AsSecureString</span></span>

<span data-ttu-id="0770a-128">Anger att cmdleten visar asterisker ( `*` ) i stället för de tecken som användaren skriver som indata.</span><span class="sxs-lookup"><span data-stu-id="0770a-128">Indicates that the cmdlet displays asterisks (`*`) in place of the characters that the user types as input.</span></span> <span data-ttu-id="0770a-129">När du använder den här parametern är utdata från `Read-Host` cmdleten ett **SecureString** -objekt (**system. Security. SecureString**).</span><span class="sxs-lookup"><span data-stu-id="0770a-129">When you use this parameter, the output of the `Read-Host` cmdlet is a **SecureString** object (**System.Security.SecureString**).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AsSecureString
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0770a-130">-MaskInput</span><span class="sxs-lookup"><span data-stu-id="0770a-130">-MaskInput</span></span>

<span data-ttu-id="0770a-131">Anger att cmdleten visar asterisker ( `*` ) i stället för de tecken som användaren skriver som indata.</span><span class="sxs-lookup"><span data-stu-id="0770a-131">Indicates that the cmdlet displays asterisks (`*`) in place of the characters that the user types as input.</span></span> <span data-ttu-id="0770a-132">När du använder den här parametern är utdata från `Read-Host` cmdleten ett **String** -objekt.</span><span class="sxs-lookup"><span data-stu-id="0770a-132">When you use this parameter, the output of the `Read-Host` cmdlet is a **String** object.</span></span>
<span data-ttu-id="0770a-133">På så sätt kan du säkert uppmanas att ange ett lösen ord som returneras som klartext i stället för **SecureString**.</span><span class="sxs-lookup"><span data-stu-id="0770a-133">This allows you to safely prompt for a password that is returned as plaintext instead of **SecureString**.</span></span>

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

### <span data-ttu-id="0770a-134">-Prompt</span><span class="sxs-lookup"><span data-stu-id="0770a-134">-Prompt</span></span>

<span data-ttu-id="0770a-135">Anger texten i prompten.</span><span class="sxs-lookup"><span data-stu-id="0770a-135">Specifies the text of the prompt.</span></span> <span data-ttu-id="0770a-136">Skriv en sträng.</span><span class="sxs-lookup"><span data-stu-id="0770a-136">Type a string.</span></span> <span data-ttu-id="0770a-137">Om strängen innehåller blank steg omger du den med citat tecken.</span><span class="sxs-lookup"><span data-stu-id="0770a-137">If the string includes spaces, enclose it in quotation marks.</span></span> <span data-ttu-id="0770a-138">PowerShell lägger till ett kolon ( `:` ) för den text som du anger.</span><span class="sxs-lookup"><span data-stu-id="0770a-138">PowerShell appends a colon (`:`) to the text that you enter.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0770a-139">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0770a-139">CommonParameters</span></span>

<span data-ttu-id="0770a-140">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="0770a-140">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0770a-141">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="0770a-141">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="0770a-142">INDATA</span><span class="sxs-lookup"><span data-stu-id="0770a-142">INPUTS</span></span>

### <span data-ttu-id="0770a-143">Inget</span><span class="sxs-lookup"><span data-stu-id="0770a-143">None</span></span>

<span data-ttu-id="0770a-144">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0770a-144">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="0770a-145">UTDATA</span><span class="sxs-lookup"><span data-stu-id="0770a-145">OUTPUTS</span></span>

### <span data-ttu-id="0770a-146">System. String eller system. Security. SecureString</span><span class="sxs-lookup"><span data-stu-id="0770a-146">System.String or System.Security.SecureString</span></span>

<span data-ttu-id="0770a-147">Om parametern **AsSecureString** används `Read-Host` returnerar en **SecureString**.</span><span class="sxs-lookup"><span data-stu-id="0770a-147">If the **AsSecureString** parameter is used, `Read-Host` returns a **SecureString**.</span></span> <span data-ttu-id="0770a-148">Annars returnerar den en sträng.</span><span class="sxs-lookup"><span data-stu-id="0770a-148">Otherwise, it returns a string.</span></span>

## <span data-ttu-id="0770a-149">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="0770a-149">NOTES</span></span>

## <span data-ttu-id="0770a-150">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="0770a-150">RELATED LINKS</span></span>

[<span data-ttu-id="0770a-151">Rensa värd</span><span class="sxs-lookup"><span data-stu-id="0770a-151">Clear-Host</span></span>](../microsoft.powershell.core/clear-host.md)

[<span data-ttu-id="0770a-152">Hämta värd</span><span class="sxs-lookup"><span data-stu-id="0770a-152">Get-Host</span></span>](Get-Host.md)

[<span data-ttu-id="0770a-153">Skriv värd</span><span class="sxs-lookup"><span data-stu-id="0770a-153">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="0770a-154">ConvertFrom – SecureString</span><span class="sxs-lookup"><span data-stu-id="0770a-154">ConvertFrom-SecureString</span></span>](../Microsoft.PowerShell.Security/ConvertFrom-SecureString.md)
