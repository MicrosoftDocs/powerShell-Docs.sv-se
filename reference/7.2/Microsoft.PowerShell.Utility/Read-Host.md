---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Read-Host
ms.openlocfilehash: 2efe75730ef7d35618dc0d1fbf7a8d6f8a5db5ae
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709750"
---
# <span data-ttu-id="b284d-102">Read-Host</span><span class="sxs-lookup"><span data-stu-id="b284d-102">Read-Host</span></span>

## <span data-ttu-id="b284d-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="b284d-103">SYNOPSIS</span></span>
<span data-ttu-id="b284d-104">Läser en rad med ininformation från-konsolen.</span><span class="sxs-lookup"><span data-stu-id="b284d-104">Reads a line of input from the console.</span></span>

## <span data-ttu-id="b284d-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b284d-105">SYNTAX</span></span>

### <span data-ttu-id="b284d-106">Uppsträng (standard)</span><span class="sxs-lookup"><span data-stu-id="b284d-106">AsString (Default)</span></span>

```
Read-Host [[-Prompt] <Object>] [-MaskInput] [<CommonParameters>]
```

### <span data-ttu-id="b284d-107">AsSecureString</span><span class="sxs-lookup"><span data-stu-id="b284d-107">AsSecureString</span></span>

```
Read-Host [[-Prompt] <Object>] [-AsSecureString] [<CommonParameters>]
```

## <span data-ttu-id="b284d-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="b284d-108">DESCRIPTION</span></span>

<span data-ttu-id="b284d-109">`Read-Host`Cmdlet: en läser en rad med ininformation från-konsolen.</span><span class="sxs-lookup"><span data-stu-id="b284d-109">The `Read-Host` cmdlet reads a line of input from the console.</span></span> <span data-ttu-id="b284d-110">Du kan använda den för att uppmana användaren att ange indata.</span><span class="sxs-lookup"><span data-stu-id="b284d-110">You can use it to prompt a user for input.</span></span> <span data-ttu-id="b284d-111">Eftersom du kan spara indata som en säker sträng kan du använda denna cmdlet för att uppmana användarna att ange säkra data, till exempel lösen ord, samt delade data.</span><span class="sxs-lookup"><span data-stu-id="b284d-111">Because you can save the input as a secure string, you can use this cmdlet to prompt users for secure data, such as passwords, as well as shared data.</span></span>

## <span data-ttu-id="b284d-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="b284d-112">EXAMPLES</span></span>

### <span data-ttu-id="b284d-113">Exempel 1: Spara konsol indata till en variabel</span><span class="sxs-lookup"><span data-stu-id="b284d-113">Example 1: Save console input to a variable</span></span>

<span data-ttu-id="b284d-114">Det här exemplet visar strängen "Ange din ålder:" som en prompt.</span><span class="sxs-lookup"><span data-stu-id="b284d-114">This example displays the string "Please enter your age:" as a prompt.</span></span> <span data-ttu-id="b284d-115">När ett värde anges och tangenten Enter trycks ned, lagras värdet i `$Age` variabeln.</span><span class="sxs-lookup"><span data-stu-id="b284d-115">When a value is entered and the Enter key is pressed, the value is stored in the `$Age` variable.</span></span>

```powershell
$Age = Read-Host "Please enter your age"
```

### <span data-ttu-id="b284d-116">Exempel 2: Spara konsol indata som en säker sträng</span><span class="sxs-lookup"><span data-stu-id="b284d-116">Example 2: Save console input as a secure string</span></span>

<span data-ttu-id="b284d-117">I det här exemplet visas strängen "Ange ett lösen ord:" som en prompt.</span><span class="sxs-lookup"><span data-stu-id="b284d-117">This example displays the string "Enter a Password:" as a prompt.</span></span> <span data-ttu-id="b284d-118">När ett värde anges visas asterisker () i- `*` konsolen i stället för indatamängden.</span><span class="sxs-lookup"><span data-stu-id="b284d-118">As a value is being entered, asterisks (`*`) appear on the console in place of the input.</span></span> <span data-ttu-id="b284d-119">När ENTER-tangenten trycks ned, lagras värdet som ett **SecureString** -objekt i `$pwd_secure_string` variabeln.</span><span class="sxs-lookup"><span data-stu-id="b284d-119">When the Enter key is pressed, the value is stored as a **SecureString** object in the `$pwd_secure_string` variable.</span></span>

```powershell
$pwd_secure_string = Read-Host "Enter a Password" -AsSecureString
```

### <span data-ttu-id="b284d-120">Exempel 3: maskera inmatade och som en oformaterad text sträng</span><span class="sxs-lookup"><span data-stu-id="b284d-120">Example 3: Mask input and as a plaintext string</span></span>

<span data-ttu-id="b284d-121">I det här exemplet visas strängen "Ange ett lösen ord:" som en prompt.</span><span class="sxs-lookup"><span data-stu-id="b284d-121">This example displays the string "Enter a Password:" as a prompt.</span></span> <span data-ttu-id="b284d-122">När ett värde anges visas asterisker () i- `*` konsolen i stället för indatamängden.</span><span class="sxs-lookup"><span data-stu-id="b284d-122">As a value is being entered, asterisks (`*`) appear on the console in place of the input.</span></span> <span data-ttu-id="b284d-123">När ENTER-tangenten trycks ned, lagras värdet som **ett text objekt** i klartext i `$pwd_string` variabeln.</span><span class="sxs-lookup"><span data-stu-id="b284d-123">When the Enter key is pressed, the value is stored as a plaintext **String** object in the `$pwd_string` variable.</span></span>

```powershell
$pwd_string = Read-Host "Enter a Password" -MaskInput
```

## <span data-ttu-id="b284d-124">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="b284d-124">PARAMETERS</span></span>

### <span data-ttu-id="b284d-125">– AsSecureString</span><span class="sxs-lookup"><span data-stu-id="b284d-125">-AsSecureString</span></span>

<span data-ttu-id="b284d-126">Anger att cmdleten visar asterisker ( `*` ) i stället för de tecken som användaren skriver som indata.</span><span class="sxs-lookup"><span data-stu-id="b284d-126">Indicates that the cmdlet displays asterisks (`*`) in place of the characters that the user types as input.</span></span> <span data-ttu-id="b284d-127">När du använder den här parametern är utdata från `Read-Host` cmdleten ett **SecureString** -objekt (**system. Security. SecureString**).</span><span class="sxs-lookup"><span data-stu-id="b284d-127">When you use this parameter, the output of the `Read-Host` cmdlet is a **SecureString** object (**System.Security.SecureString**).</span></span>

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

### <span data-ttu-id="b284d-128">-MaskInput</span><span class="sxs-lookup"><span data-stu-id="b284d-128">-MaskInput</span></span>

<span data-ttu-id="b284d-129">Anger att cmdleten visar asterisker ( `*` ) i stället för de tecken som användaren skriver som indata.</span><span class="sxs-lookup"><span data-stu-id="b284d-129">Indicates that the cmdlet displays asterisks (`*`) in place of the characters that the user types as input.</span></span> <span data-ttu-id="b284d-130">När du använder den här parametern är utdata från `Read-Host` cmdleten ett **String** -objekt.</span><span class="sxs-lookup"><span data-stu-id="b284d-130">When you use this parameter, the output of the `Read-Host` cmdlet is a **String** object.</span></span>
<span data-ttu-id="b284d-131">På så sätt kan du säkert uppmanas att ange ett lösen ord som returneras som klartext i stället för **SecureString**.</span><span class="sxs-lookup"><span data-stu-id="b284d-131">This allows you to safely prompt for a password that is returned as plaintext instead of **SecureString**.</span></span>

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

### <span data-ttu-id="b284d-132">-Prompt</span><span class="sxs-lookup"><span data-stu-id="b284d-132">-Prompt</span></span>

<span data-ttu-id="b284d-133">Anger texten i prompten.</span><span class="sxs-lookup"><span data-stu-id="b284d-133">Specifies the text of the prompt.</span></span>
<span data-ttu-id="b284d-134">Skriv en sträng.</span><span class="sxs-lookup"><span data-stu-id="b284d-134">Type a string.</span></span>
<span data-ttu-id="b284d-135">Om strängen innehåller blank steg omger du den med citat tecken.</span><span class="sxs-lookup"><span data-stu-id="b284d-135">If the string includes spaces, enclose it in quotation marks.</span></span>
<span data-ttu-id="b284d-136">PowerShell lägger till ett kolon ( `:` ) för den text som du anger.</span><span class="sxs-lookup"><span data-stu-id="b284d-136">PowerShell appends a colon (`:`) to the text that you enter.</span></span>

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

### <span data-ttu-id="b284d-137">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b284d-137">CommonParameters</span></span>

<span data-ttu-id="b284d-138">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b284d-138">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b284d-139">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="b284d-139">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b284d-140">INDATA</span><span class="sxs-lookup"><span data-stu-id="b284d-140">INPUTS</span></span>

### <span data-ttu-id="b284d-141">Inga</span><span class="sxs-lookup"><span data-stu-id="b284d-141">None</span></span>

<span data-ttu-id="b284d-142">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b284d-142">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="b284d-143">UTDATA</span><span class="sxs-lookup"><span data-stu-id="b284d-143">OUTPUTS</span></span>

### <span data-ttu-id="b284d-144">System. String eller system. Security. SecureString</span><span class="sxs-lookup"><span data-stu-id="b284d-144">System.String or System.Security.SecureString</span></span>

<span data-ttu-id="b284d-145">Om parametern **AsSecureString** används `Read-Host` returnerar en **SecureString**.</span><span class="sxs-lookup"><span data-stu-id="b284d-145">If the **AsSecureString** parameter is used, `Read-Host` returns a **SecureString**.</span></span> <span data-ttu-id="b284d-146">Annars returnerar den en sträng.</span><span class="sxs-lookup"><span data-stu-id="b284d-146">Otherwise, it returns a string.</span></span>

## <span data-ttu-id="b284d-147">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="b284d-147">NOTES</span></span>

## <span data-ttu-id="b284d-148">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="b284d-148">RELATED LINKS</span></span>

[<span data-ttu-id="b284d-149">Rensa värd</span><span class="sxs-lookup"><span data-stu-id="b284d-149">Clear-Host</span></span>](../microsoft.powershell.core/clear-host.md)

[<span data-ttu-id="b284d-150">Hämta värd</span><span class="sxs-lookup"><span data-stu-id="b284d-150">Get-Host</span></span>](Get-Host.md)

[<span data-ttu-id="b284d-151">Skriv värd</span><span class="sxs-lookup"><span data-stu-id="b284d-151">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="b284d-152">ConvertFrom – SecureString</span><span class="sxs-lookup"><span data-stu-id="b284d-152">ConvertFrom-SecureString</span></span>](../Microsoft.PowerShell.Security/ConvertFrom-SecureString.md)
