---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/02/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Read-Host
ms.openlocfilehash: 5563413400abd28ce376265970631ad1206ca518
ms.sourcegitcommit: 1dfd5554b70c7e8f4e3df19e29c384a9c0a4b227
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/03/2021
ms.locfileid: "101685266"
---
# <span data-ttu-id="c2037-102">Read-Host</span><span class="sxs-lookup"><span data-stu-id="c2037-102">Read-Host</span></span>

## <span data-ttu-id="c2037-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="c2037-103">SYNOPSIS</span></span>
<span data-ttu-id="c2037-104">Läser en rad med ininformation från-konsolen.</span><span class="sxs-lookup"><span data-stu-id="c2037-104">Reads a line of input from the console.</span></span>

## <span data-ttu-id="c2037-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c2037-105">SYNTAX</span></span>

### <span data-ttu-id="c2037-106">Uppsträng (standard)</span><span class="sxs-lookup"><span data-stu-id="c2037-106">AsString (Default)</span></span>

```
Read-Host [[-Prompt] <Object>] [-MaskInput] [<CommonParameters>]
```

### <span data-ttu-id="c2037-107">AsSecureString</span><span class="sxs-lookup"><span data-stu-id="c2037-107">AsSecureString</span></span>

```
Read-Host [[-Prompt] <Object>] [-AsSecureString] [<CommonParameters>]
```

## <span data-ttu-id="c2037-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="c2037-108">DESCRIPTION</span></span>

<span data-ttu-id="c2037-109">`Read-Host`Cmdlet: en läser en rad med ininformation från-konsolen.</span><span class="sxs-lookup"><span data-stu-id="c2037-109">The `Read-Host` cmdlet reads a line of input from the console.</span></span> <span data-ttu-id="c2037-110">Du kan använda den för att uppmana användaren att ange indata.</span><span class="sxs-lookup"><span data-stu-id="c2037-110">You can use it to prompt a user for input.</span></span> <span data-ttu-id="c2037-111">Eftersom du kan spara indata som en säker sträng kan du använda denna cmdlet för att uppmana användarna att ange säkra data, till exempel lösen ord, samt delade data.</span><span class="sxs-lookup"><span data-stu-id="c2037-111">Because you can save the input as a secure string, you can use this cmdlet to prompt users for secure data, such as passwords, as well as shared data.</span></span>

> [!NOTE]
> <span data-ttu-id="c2037-112">`Read-Host` har en gräns på 1022 tecken som kan accepteras som indata från en användare.</span><span class="sxs-lookup"><span data-stu-id="c2037-112">`Read-Host` has a limit of 1022 characters it can accept as input from a user.</span></span>

## <span data-ttu-id="c2037-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="c2037-113">EXAMPLES</span></span>

### <span data-ttu-id="c2037-114">Exempel 1: Spara konsol indata till en variabel</span><span class="sxs-lookup"><span data-stu-id="c2037-114">Example 1: Save console input to a variable</span></span>

<span data-ttu-id="c2037-115">Det här exemplet visar strängen "Ange din ålder:" som en prompt.</span><span class="sxs-lookup"><span data-stu-id="c2037-115">This example displays the string "Please enter your age:" as a prompt.</span></span> <span data-ttu-id="c2037-116">När ett värde anges och tangenten Enter trycks ned, lagras värdet i `$Age` variabeln.</span><span class="sxs-lookup"><span data-stu-id="c2037-116">When a value is entered and the Enter key is pressed, the value is stored in the `$Age` variable.</span></span>

```powershell
$Age = Read-Host "Please enter your age"
```

### <span data-ttu-id="c2037-117">Exempel 2: Spara konsol indata som en säker sträng</span><span class="sxs-lookup"><span data-stu-id="c2037-117">Example 2: Save console input as a secure string</span></span>

<span data-ttu-id="c2037-118">I det här exemplet visas strängen "Ange ett lösen ord:" som en prompt.</span><span class="sxs-lookup"><span data-stu-id="c2037-118">This example displays the string "Enter a Password:" as a prompt.</span></span> <span data-ttu-id="c2037-119">När ett värde anges visas asterisker () i- `*` konsolen i stället för indatamängden.</span><span class="sxs-lookup"><span data-stu-id="c2037-119">As a value is being entered, asterisks (`*`) appear on the console in place of the input.</span></span> <span data-ttu-id="c2037-120">När ENTER-tangenten trycks ned, lagras värdet som ett **SecureString** -objekt i `$pwd_secure_string` variabeln.</span><span class="sxs-lookup"><span data-stu-id="c2037-120">When the Enter key is pressed, the value is stored as a **SecureString** object in the `$pwd_secure_string` variable.</span></span>

```powershell
$pwd_secure_string = Read-Host "Enter a Password" -AsSecureString
```

### <span data-ttu-id="c2037-121">Exempel 3: maskera inmatade och som en oformaterad text sträng</span><span class="sxs-lookup"><span data-stu-id="c2037-121">Example 3: Mask input and as a plaintext string</span></span>

<span data-ttu-id="c2037-122">I det här exemplet visas strängen "Ange ett lösen ord:" som en prompt.</span><span class="sxs-lookup"><span data-stu-id="c2037-122">This example displays the string "Enter a Password:" as a prompt.</span></span> <span data-ttu-id="c2037-123">När ett värde anges visas asterisker () i- `*` konsolen i stället för indatamängden.</span><span class="sxs-lookup"><span data-stu-id="c2037-123">As a value is being entered, asterisks (`*`) appear on the console in place of the input.</span></span> <span data-ttu-id="c2037-124">När ENTER-tangenten trycks ned, lagras värdet som **ett text objekt** i klartext i `$pwd_string` variabeln.</span><span class="sxs-lookup"><span data-stu-id="c2037-124">When the Enter key is pressed, the value is stored as a plaintext **String** object in the `$pwd_string` variable.</span></span>

```powershell
$pwd_string = Read-Host "Enter a Password" -MaskInput
```

## <span data-ttu-id="c2037-125">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="c2037-125">PARAMETERS</span></span>

### <span data-ttu-id="c2037-126">– AsSecureString</span><span class="sxs-lookup"><span data-stu-id="c2037-126">-AsSecureString</span></span>

<span data-ttu-id="c2037-127">Anger att cmdleten visar asterisker ( `*` ) i stället för de tecken som användaren skriver som indata.</span><span class="sxs-lookup"><span data-stu-id="c2037-127">Indicates that the cmdlet displays asterisks (`*`) in place of the characters that the user types as input.</span></span> <span data-ttu-id="c2037-128">När du använder den här parametern är utdata från `Read-Host` cmdleten ett **SecureString** -objekt (**system. Security. SecureString**).</span><span class="sxs-lookup"><span data-stu-id="c2037-128">When you use this parameter, the output of the `Read-Host` cmdlet is a **SecureString** object (**System.Security.SecureString**).</span></span>

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

### <span data-ttu-id="c2037-129">-MaskInput</span><span class="sxs-lookup"><span data-stu-id="c2037-129">-MaskInput</span></span>

<span data-ttu-id="c2037-130">Anger att cmdleten visar asterisker ( `*` ) i stället för de tecken som användaren skriver som indata.</span><span class="sxs-lookup"><span data-stu-id="c2037-130">Indicates that the cmdlet displays asterisks (`*`) in place of the characters that the user types as input.</span></span> <span data-ttu-id="c2037-131">När du använder den här parametern är utdata från `Read-Host` cmdleten ett **String** -objekt.</span><span class="sxs-lookup"><span data-stu-id="c2037-131">When you use this parameter, the output of the `Read-Host` cmdlet is a **String** object.</span></span>
<span data-ttu-id="c2037-132">På så sätt kan du säkert uppmanas att ange ett lösen ord som returneras som klartext i stället för **SecureString**.</span><span class="sxs-lookup"><span data-stu-id="c2037-132">This allows you to safely prompt for a password that is returned as plaintext instead of **SecureString**.</span></span>

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

### <span data-ttu-id="c2037-133">-Prompt</span><span class="sxs-lookup"><span data-stu-id="c2037-133">-Prompt</span></span>

<span data-ttu-id="c2037-134">Anger texten i prompten.</span><span class="sxs-lookup"><span data-stu-id="c2037-134">Specifies the text of the prompt.</span></span> <span data-ttu-id="c2037-135">Skriv en sträng.</span><span class="sxs-lookup"><span data-stu-id="c2037-135">Type a string.</span></span> <span data-ttu-id="c2037-136">Om strängen innehåller blank steg omger du den med citat tecken.</span><span class="sxs-lookup"><span data-stu-id="c2037-136">If the string includes spaces, enclose it in quotation marks.</span></span> <span data-ttu-id="c2037-137">PowerShell lägger till ett kolon ( `:` ) för den text som du anger.</span><span class="sxs-lookup"><span data-stu-id="c2037-137">PowerShell appends a colon (`:`) to the text that you enter.</span></span>

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

### <span data-ttu-id="c2037-138">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c2037-138">CommonParameters</span></span>

<span data-ttu-id="c2037-139">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c2037-139">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c2037-140">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="c2037-140">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c2037-141">INDATA</span><span class="sxs-lookup"><span data-stu-id="c2037-141">INPUTS</span></span>

### <span data-ttu-id="c2037-142">Inget</span><span class="sxs-lookup"><span data-stu-id="c2037-142">None</span></span>

<span data-ttu-id="c2037-143">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c2037-143">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="c2037-144">UTDATA</span><span class="sxs-lookup"><span data-stu-id="c2037-144">OUTPUTS</span></span>

### <span data-ttu-id="c2037-145">System. String eller system. Security. SecureString</span><span class="sxs-lookup"><span data-stu-id="c2037-145">System.String or System.Security.SecureString</span></span>

<span data-ttu-id="c2037-146">Om parametern **AsSecureString** används `Read-Host` returnerar en **SecureString**.</span><span class="sxs-lookup"><span data-stu-id="c2037-146">If the **AsSecureString** parameter is used, `Read-Host` returns a **SecureString**.</span></span> <span data-ttu-id="c2037-147">Annars returnerar den en sträng.</span><span class="sxs-lookup"><span data-stu-id="c2037-147">Otherwise, it returns a string.</span></span>

## <span data-ttu-id="c2037-148">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="c2037-148">NOTES</span></span>

## <span data-ttu-id="c2037-149">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="c2037-149">RELATED LINKS</span></span>

[<span data-ttu-id="c2037-150">Rensa värd</span><span class="sxs-lookup"><span data-stu-id="c2037-150">Clear-Host</span></span>](../microsoft.powershell.core/clear-host.md)

[<span data-ttu-id="c2037-151">Hämta värd</span><span class="sxs-lookup"><span data-stu-id="c2037-151">Get-Host</span></span>](Get-Host.md)

[<span data-ttu-id="c2037-152">Skriv värd</span><span class="sxs-lookup"><span data-stu-id="c2037-152">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="c2037-153">ConvertFrom – SecureString</span><span class="sxs-lookup"><span data-stu-id="c2037-153">ConvertFrom-SecureString</span></span>](../Microsoft.PowerShell.Security/ConvertFrom-SecureString.md)
