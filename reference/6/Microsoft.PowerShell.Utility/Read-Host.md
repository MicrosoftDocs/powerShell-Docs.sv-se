---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/read-host?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Read-Host
ms.openlocfilehash: 8e0c1057a4117eb60cdc8ec494470dacaca78699
ms.sourcegitcommit: 57df49488015e7ac17ff1df402a94441aa6d6064
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/08/2020
ms.locfileid: "93267986"
---
# <span data-ttu-id="0b12f-103">Read-Host</span><span class="sxs-lookup"><span data-stu-id="0b12f-103">Read-Host</span></span>

## <span data-ttu-id="0b12f-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="0b12f-104">SYNOPSIS</span></span>
<span data-ttu-id="0b12f-105">Läser en rad med ininformation från-konsolen.</span><span class="sxs-lookup"><span data-stu-id="0b12f-105">Reads a line of input from the console.</span></span>

## <span data-ttu-id="0b12f-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="0b12f-106">SYNTAX</span></span>

```
Read-Host [[-Prompt] <Object>] [-AsSecureString] [<CommonParameters>]
```

## <span data-ttu-id="0b12f-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="0b12f-107">DESCRIPTION</span></span>

<span data-ttu-id="0b12f-108">`Read-Host`Cmdlet: en läser en rad med ininformation från-konsolen.</span><span class="sxs-lookup"><span data-stu-id="0b12f-108">The `Read-Host` cmdlet reads a line of input from the console.</span></span> <span data-ttu-id="0b12f-109">Du kan använda den för att uppmana användaren att ange indata.</span><span class="sxs-lookup"><span data-stu-id="0b12f-109">You can use it to prompt a user for input.</span></span> <span data-ttu-id="0b12f-110">Eftersom du kan spara indata som en säker sträng kan du använda denna cmdlet för att uppmana användarna att ange säkra data, till exempel lösen ord, samt delade data.</span><span class="sxs-lookup"><span data-stu-id="0b12f-110">Because you can save the input as a secure string, you can use this cmdlet to prompt users for secure data, such as passwords, as well as shared data.</span></span>

## <span data-ttu-id="0b12f-111">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="0b12f-111">EXAMPLES</span></span>

### <span data-ttu-id="0b12f-112">Exempel 1: Spara konsol indata till en variabel</span><span class="sxs-lookup"><span data-stu-id="0b12f-112">Example 1: Save console input to a variable</span></span>

<span data-ttu-id="0b12f-113">Det här exemplet visar strängen "Ange din ålder:" som en prompt.</span><span class="sxs-lookup"><span data-stu-id="0b12f-113">This example displays the string "Please enter your age:" as a prompt.</span></span> <span data-ttu-id="0b12f-114">När ett värde anges och tangenten Enter trycks ned, lagras värdet i `$Age` variabeln.</span><span class="sxs-lookup"><span data-stu-id="0b12f-114">When a value is entered and the Enter key is pressed, the value is stored in the `$Age` variable.</span></span>

```powershell
$Age = Read-Host "Please enter your age"
```

### <span data-ttu-id="0b12f-115">Exempel 2: Spara konsol indata som en säker sträng</span><span class="sxs-lookup"><span data-stu-id="0b12f-115">Example 2: Save console input as a secure string</span></span>

<span data-ttu-id="0b12f-116">I det här exemplet visas strängen "Ange ett lösen ord:" som en prompt.</span><span class="sxs-lookup"><span data-stu-id="0b12f-116">This example displays the string "Enter a Password:" as a prompt.</span></span> <span data-ttu-id="0b12f-117">När ett värde anges visas asterisker () i- `*` konsolen i stället för indatamängden.</span><span class="sxs-lookup"><span data-stu-id="0b12f-117">As a value is being entered, asterisks (`*`) appear on the console in place of the input.</span></span> <span data-ttu-id="0b12f-118">När ENTER-tangenten trycks ned, lagras värdet som ett **SecureString** -objekt i `$pwd_secure_string` variabeln.</span><span class="sxs-lookup"><span data-stu-id="0b12f-118">When the Enter key is pressed, the value is stored as a **SecureString** object in the `$pwd_secure_string` variable.</span></span>

```powershell
$pwd_secure_string = Read-Host "Enter a Password" -AsSecureString
```

## <span data-ttu-id="0b12f-119">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="0b12f-119">PARAMETERS</span></span>

### <span data-ttu-id="0b12f-120">– AsSecureString</span><span class="sxs-lookup"><span data-stu-id="0b12f-120">-AsSecureString</span></span>

<span data-ttu-id="0b12f-121">Anger att cmdleten visar asterisker ( `*` ) i stället för de tecken som användaren skriver som indata.</span><span class="sxs-lookup"><span data-stu-id="0b12f-121">Indicates that the cmdlet displays asterisks (`*`) in place of the characters that the user types as input.</span></span> <span data-ttu-id="0b12f-122">När du använder den här parametern är utdata från `Read-Host` cmdleten ett **SecureString** -objekt ( **system. Security. SecureString** ).</span><span class="sxs-lookup"><span data-stu-id="0b12f-122">When you use this parameter, the output of the `Read-Host` cmdlet is a **SecureString** object ( **System.Security.SecureString** ).</span></span>

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

### <span data-ttu-id="0b12f-123">-Prompt</span><span class="sxs-lookup"><span data-stu-id="0b12f-123">-Prompt</span></span>

<span data-ttu-id="0b12f-124">Anger texten i prompten.</span><span class="sxs-lookup"><span data-stu-id="0b12f-124">Specifies the text of the prompt.</span></span>
<span data-ttu-id="0b12f-125">Skriv en sträng.</span><span class="sxs-lookup"><span data-stu-id="0b12f-125">Type a string.</span></span>
<span data-ttu-id="0b12f-126">Om strängen innehåller blank steg omger du den med citat tecken.</span><span class="sxs-lookup"><span data-stu-id="0b12f-126">If the string includes spaces, enclose it in quotation marks.</span></span>
<span data-ttu-id="0b12f-127">PowerShell lägger till ett kolon ( `:` ) för den text som du anger.</span><span class="sxs-lookup"><span data-stu-id="0b12f-127">PowerShell appends a colon (`:`) to the text that you enter.</span></span>

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

### <span data-ttu-id="0b12f-128">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0b12f-128">CommonParameters</span></span>

<span data-ttu-id="0b12f-129">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="0b12f-129">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0b12f-130">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="0b12f-130">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="0b12f-131">INDATA</span><span class="sxs-lookup"><span data-stu-id="0b12f-131">INPUTS</span></span>

### <span data-ttu-id="0b12f-132">Inget</span><span class="sxs-lookup"><span data-stu-id="0b12f-132">None</span></span>

<span data-ttu-id="0b12f-133">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0b12f-133">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="0b12f-134">UTDATA</span><span class="sxs-lookup"><span data-stu-id="0b12f-134">OUTPUTS</span></span>

### <span data-ttu-id="0b12f-135">System. String eller system. Security. SecureString</span><span class="sxs-lookup"><span data-stu-id="0b12f-135">System.String or System.Security.SecureString</span></span>

<span data-ttu-id="0b12f-136">Om parametern **AsSecureString** används `Read-Host` returnerar en **SecureString**.</span><span class="sxs-lookup"><span data-stu-id="0b12f-136">If the **AsSecureString** parameter is used, `Read-Host` returns a **SecureString**.</span></span> <span data-ttu-id="0b12f-137">Annars returnerar den en sträng.</span><span class="sxs-lookup"><span data-stu-id="0b12f-137">Otherwise, it returns a string.</span></span>

## <span data-ttu-id="0b12f-138">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="0b12f-138">NOTES</span></span>

## <span data-ttu-id="0b12f-139">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="0b12f-139">RELATED LINKS</span></span>

[<span data-ttu-id="0b12f-140">Rensa värd</span><span class="sxs-lookup"><span data-stu-id="0b12f-140">Clear-Host</span></span>](../microsoft.powershell.core/clear-host.md)

[<span data-ttu-id="0b12f-141">Hämta värd</span><span class="sxs-lookup"><span data-stu-id="0b12f-141">Get-Host</span></span>](Get-Host.md)

[<span data-ttu-id="0b12f-142">Skriv värd</span><span class="sxs-lookup"><span data-stu-id="0b12f-142">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="0b12f-143">ConvertFrom – SecureString</span><span class="sxs-lookup"><span data-stu-id="0b12f-143">ConvertFrom-SecureString</span></span>](../Microsoft.PowerShell.Security/ConvertFrom-SecureString.md)
