---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-verbose?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Verbose
ms.openlocfilehash: 177e32106f37c59593bbecac13843f6603327cc9
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710333"
---
# <span data-ttu-id="345dc-102">Write-Verbose</span><span class="sxs-lookup"><span data-stu-id="345dc-102">Write-Verbose</span></span>

## <span data-ttu-id="345dc-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="345dc-103">SYNOPSIS</span></span>
<span data-ttu-id="345dc-104">Skriver text till data strömmen för utförliga meddelanden.</span><span class="sxs-lookup"><span data-stu-id="345dc-104">Writes text to the verbose message stream.</span></span>

## <span data-ttu-id="345dc-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="345dc-105">SYNTAX</span></span>

```
Write-Verbose [-Message] <String> [<CommonParameters>]
```

## <span data-ttu-id="345dc-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="345dc-106">DESCRIPTION</span></span>

<span data-ttu-id="345dc-107">`Write-Verbose`Cmdleten skriver text till data strömmen för utförliga meddelanden i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="345dc-107">The `Write-Verbose` cmdlet writes text to the verbose message stream in PowerShell.</span></span> <span data-ttu-id="345dc-108">Den utförliga meddelande strömmen används vanligt vis för att leverera mer ingående information om kommando bearbetning.</span><span class="sxs-lookup"><span data-stu-id="345dc-108">Typically, the verbose message stream is used to deliver more in depth information about command processing.</span></span>

<span data-ttu-id="345dc-109">Den utförliga meddelande strömmen visas som standard inte, men du kan visa den genom att ändra värdet för `$VerbosePreference` variabeln eller använda den **utförliga** gemensamma parametern i alla kommandon.</span><span class="sxs-lookup"><span data-stu-id="345dc-109">By default, the verbose message stream is not displayed, but you can display it by changing the value of the `$VerbosePreference` variable or using the **Verbose** common parameter in any command.</span></span>

## <span data-ttu-id="345dc-110">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="345dc-110">EXAMPLES</span></span>

### <span data-ttu-id="345dc-111">Exempel 1: Skriv ett status meddelande</span><span class="sxs-lookup"><span data-stu-id="345dc-111">Example 1: Write a status message</span></span>

```powershell
Write-Verbose -Message "Searching the Application Event Log."
Write-Verbose -Message "Searching the Application Event Log." -Verbose
```

<span data-ttu-id="345dc-112">Dessa kommandon använder `Write-Verbose` cmdleten för att visa ett status meddelande.</span><span class="sxs-lookup"><span data-stu-id="345dc-112">These commands use the `Write-Verbose` cmdlet to display a status message.</span></span> <span data-ttu-id="345dc-113">Som standard visas inte meddelandet.</span><span class="sxs-lookup"><span data-stu-id="345dc-113">By default, the message is not displayed.</span></span>

<span data-ttu-id="345dc-114">Det andra kommandot använder den **utförliga** gemensamma parametern, som visar alla utförliga meddelanden, oavsett värdet för `$VerbosePreference` variabeln.</span><span class="sxs-lookup"><span data-stu-id="345dc-114">The second command uses the **Verbose** common parameter, which displays any verbose messages, regardless of the value of the `$VerbosePreference` variable.</span></span>

### <span data-ttu-id="345dc-115">Exempel 2: Ange $VerbosePreference och skriv ett status meddelande</span><span class="sxs-lookup"><span data-stu-id="345dc-115">Example 2: Set $VerbosePreference and write a status message</span></span>

```powershell
$VerbosePreference = "Continue"
Write-Verbose "Copying file $filename"
```

<span data-ttu-id="345dc-116">Dessa kommandon använder `Write-Verbose` cmdleten för att visa ett status meddelande.</span><span class="sxs-lookup"><span data-stu-id="345dc-116">These commands use the `Write-Verbose` cmdlet to display a status message.</span></span> <span data-ttu-id="345dc-117">Som standard visas inte meddelandet.</span><span class="sxs-lookup"><span data-stu-id="345dc-117">By default, the message is not displayed.</span></span>

<span data-ttu-id="345dc-118">Det första kommandot tilldelar värdet Fortsätt till `$VerbosePreference` Preference-variabeln.</span><span class="sxs-lookup"><span data-stu-id="345dc-118">The first command assigns a value of Continue to the `$VerbosePreference` preference variable.</span></span> <span data-ttu-id="345dc-119">Standardvärdet, `SilentlyContinue` , förhindrar utförliga meddelanden.</span><span class="sxs-lookup"><span data-stu-id="345dc-119">The default value, `SilentlyContinue`, suppresses verbose messages.</span></span> <span data-ttu-id="345dc-120">Det andra kommandot skriver ett utförligt meddelande.</span><span class="sxs-lookup"><span data-stu-id="345dc-120">The second command writes a verbose message.</span></span>

## <span data-ttu-id="345dc-121">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="345dc-121">PARAMETERS</span></span>

### <span data-ttu-id="345dc-122">– Meddelande</span><span class="sxs-lookup"><span data-stu-id="345dc-122">-Message</span></span>

<span data-ttu-id="345dc-123">Anger meddelandet som ska visas.</span><span class="sxs-lookup"><span data-stu-id="345dc-123">Specifies the message to display.</span></span> <span data-ttu-id="345dc-124">Den här parametern är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="345dc-124">This parameter is required.</span></span> <span data-ttu-id="345dc-125">Du kan också skicka en meddelande sträng till `Write-Verbose` .</span><span class="sxs-lookup"><span data-stu-id="345dc-125">You can also pipe a message string to `Write-Verbose`.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Msg

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="345dc-126">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="345dc-126">CommonParameters</span></span>

<span data-ttu-id="345dc-127">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="345dc-127">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="345dc-128">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="345dc-128">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="345dc-129">INDATA</span><span class="sxs-lookup"><span data-stu-id="345dc-129">INPUTS</span></span>

### <span data-ttu-id="345dc-130">System. String</span><span class="sxs-lookup"><span data-stu-id="345dc-130">System.String</span></span>

<span data-ttu-id="345dc-131">Du kan skicka vidare en sträng som innehåller meddelandet till `Write-Verbose` .</span><span class="sxs-lookup"><span data-stu-id="345dc-131">You can pipe a string that contains the message to `Write-Verbose`.</span></span>

## <span data-ttu-id="345dc-132">UTDATA</span><span class="sxs-lookup"><span data-stu-id="345dc-132">OUTPUTS</span></span>

### <span data-ttu-id="345dc-133">Inga</span><span class="sxs-lookup"><span data-stu-id="345dc-133">None</span></span>

<span data-ttu-id="345dc-134">`Write-Verbose` skriver enbart till den utförliga meddelande strömmen.</span><span class="sxs-lookup"><span data-stu-id="345dc-134">`Write-Verbose` writes only to the verbose message stream.</span></span>

## <span data-ttu-id="345dc-135">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="345dc-135">NOTES</span></span>

- <span data-ttu-id="345dc-136">Utförliga meddelanden returneras bara när kommandot använder den **utförliga** gemensamma parametern.</span><span class="sxs-lookup"><span data-stu-id="345dc-136">Verbose messages are returned only when the command uses the **Verbose** common parameter.</span></span> <span data-ttu-id="345dc-137">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="345dc-137">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>
- <span data-ttu-id="345dc-138">I Windows PowerShell bakgrunds jobb och fjärrkommandon `$VerbosePreference` avgör variabeln i jobbschemaläggaren och fjärrsession om utförligt meddelande visas som standard.</span><span class="sxs-lookup"><span data-stu-id="345dc-138">In Windows PowerShell background jobs and remote commands, the `$VerbosePreference` variable in the job session and remote session determine whether the verbose message is displayed by default.</span></span>
  <span data-ttu-id="345dc-139">Mer information om `$VerbosePreference` variabeln finns i [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="345dc-139">For more information about the `$VerbosePreference` variable, see [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span></span>

## <span data-ttu-id="345dc-140">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="345dc-140">RELATED LINKS</span></span>

[<span data-ttu-id="345dc-141">about_Output_Streams</span><span class="sxs-lookup"><span data-stu-id="345dc-141">about_Output_Streams</span></span>](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[<span data-ttu-id="345dc-142">about_Redirection</span><span class="sxs-lookup"><span data-stu-id="345dc-142">about_Redirection</span></span>](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[<span data-ttu-id="345dc-143">Skriv-debug</span><span class="sxs-lookup"><span data-stu-id="345dc-143">Write-Debug</span></span>](Write-Debug.md)

[<span data-ttu-id="345dc-144">Skriv-fel</span><span class="sxs-lookup"><span data-stu-id="345dc-144">Write-Error</span></span>](Write-Error.md)

[<span data-ttu-id="345dc-145">Skriv värd</span><span class="sxs-lookup"><span data-stu-id="345dc-145">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="345dc-146">Skriv information</span><span class="sxs-lookup"><span data-stu-id="345dc-146">Write-Information</span></span>](Write-Information.md)

[<span data-ttu-id="345dc-147">Skriva-utdata</span><span class="sxs-lookup"><span data-stu-id="345dc-147">Write-Output</span></span>](Write-Output.md)

[<span data-ttu-id="345dc-148">Skriv förlopp</span><span class="sxs-lookup"><span data-stu-id="345dc-148">Write-Progress</span></span>](Write-Progress.md)

[<span data-ttu-id="345dc-149">Skriv varning</span><span class="sxs-lookup"><span data-stu-id="345dc-149">Write-Warning</span></span>](Write-Warning.md)
