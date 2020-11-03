---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-verbose?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Verbose
ms.openlocfilehash: fab0d14d8f22227b37d0dabd2287a5cdff13cce7
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/16/2020
ms.locfileid: "93272895"
---
# <span data-ttu-id="90816-103">Write-Verbose</span><span class="sxs-lookup"><span data-stu-id="90816-103">Write-Verbose</span></span>

## <span data-ttu-id="90816-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="90816-104">SYNOPSIS</span></span>
<span data-ttu-id="90816-105">Skriver text till data strömmen för utförliga meddelanden.</span><span class="sxs-lookup"><span data-stu-id="90816-105">Writes text to the verbose message stream.</span></span>

## <span data-ttu-id="90816-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="90816-106">SYNTAX</span></span>

```
Write-Verbose [-Message] <String> [<CommonParameters>]
```

## <span data-ttu-id="90816-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="90816-107">DESCRIPTION</span></span>

<span data-ttu-id="90816-108">`Write-Verbose`Cmdleten skriver text till data strömmen för utförliga meddelanden i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="90816-108">The `Write-Verbose` cmdlet writes text to the verbose message stream in PowerShell.</span></span> <span data-ttu-id="90816-109">Den utförliga meddelande strömmen används vanligt vis för att leverera mer ingående information om kommando bearbetning.</span><span class="sxs-lookup"><span data-stu-id="90816-109">Typically, the verbose message stream is used to deliver more in depth information about command processing.</span></span>

<span data-ttu-id="90816-110">Den utförliga meddelande strömmen visas som standard inte, men du kan visa den genom att ändra värdet för `$VerbosePreference` variabeln eller använda den **utförliga** gemensamma parametern i alla kommandon.</span><span class="sxs-lookup"><span data-stu-id="90816-110">By default, the verbose message stream is not displayed, but you can display it by changing the value of the `$VerbosePreference` variable or using the **Verbose** common parameter in any command.</span></span>

## <span data-ttu-id="90816-111">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="90816-111">EXAMPLES</span></span>

### <span data-ttu-id="90816-112">Exempel 1: Skriv ett status meddelande</span><span class="sxs-lookup"><span data-stu-id="90816-112">Example 1: Write a status message</span></span>

```powershell
Write-Verbose -Message "Searching the Application Event Log."
Write-Verbose -Message "Searching the Application Event Log." -Verbose
```

<span data-ttu-id="90816-113">Dessa kommandon använder `Write-Verbose` cmdleten för att visa ett status meddelande.</span><span class="sxs-lookup"><span data-stu-id="90816-113">These commands use the `Write-Verbose` cmdlet to display a status message.</span></span> <span data-ttu-id="90816-114">Som standard visas inte meddelandet.</span><span class="sxs-lookup"><span data-stu-id="90816-114">By default, the message is not displayed.</span></span>

<span data-ttu-id="90816-115">Det andra kommandot använder den **utförliga** gemensamma parametern, som visar alla utförliga meddelanden, oavsett värdet för `$VerbosePreference` variabeln.</span><span class="sxs-lookup"><span data-stu-id="90816-115">The second command uses the **Verbose** common parameter, which displays any verbose messages, regardless of the value of the `$VerbosePreference` variable.</span></span>

### <span data-ttu-id="90816-116">Exempel 2: Ange $VerbosePreference och skriv ett status meddelande</span><span class="sxs-lookup"><span data-stu-id="90816-116">Example 2: Set $VerbosePreference and write a status message</span></span>

```powershell
$VerbosePreference = "Continue"
Write-Verbose "Copying file $filename"
```

<span data-ttu-id="90816-117">Dessa kommandon använder `Write-Verbose` cmdleten för att visa ett status meddelande.</span><span class="sxs-lookup"><span data-stu-id="90816-117">These commands use the `Write-Verbose` cmdlet to display a status message.</span></span> <span data-ttu-id="90816-118">Som standard visas inte meddelandet.</span><span class="sxs-lookup"><span data-stu-id="90816-118">By default, the message is not displayed.</span></span>

<span data-ttu-id="90816-119">Det första kommandot tilldelar värdet Fortsätt till `$VerbosePreference` Preference-variabeln.</span><span class="sxs-lookup"><span data-stu-id="90816-119">The first command assigns a value of Continue to the `$VerbosePreference` preference variable.</span></span> <span data-ttu-id="90816-120">Standardvärdet, `SilentlyContinue` , förhindrar utförliga meddelanden.</span><span class="sxs-lookup"><span data-stu-id="90816-120">The default value, `SilentlyContinue`, suppresses verbose messages.</span></span> <span data-ttu-id="90816-121">Det andra kommandot skriver ett utförligt meddelande.</span><span class="sxs-lookup"><span data-stu-id="90816-121">The second command writes a verbose message.</span></span>

## <span data-ttu-id="90816-122">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="90816-122">PARAMETERS</span></span>

### <span data-ttu-id="90816-123">– Meddelande</span><span class="sxs-lookup"><span data-stu-id="90816-123">-Message</span></span>

<span data-ttu-id="90816-124">Anger meddelandet som ska visas.</span><span class="sxs-lookup"><span data-stu-id="90816-124">Specifies the message to display.</span></span> <span data-ttu-id="90816-125">Den här parametern är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="90816-125">This parameter is required.</span></span> <span data-ttu-id="90816-126">Du kan också skicka en meddelande sträng till `Write-Verbose` .</span><span class="sxs-lookup"><span data-stu-id="90816-126">You can also pipe a message string to `Write-Verbose`.</span></span>

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

### <span data-ttu-id="90816-127">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="90816-127">CommonParameters</span></span>

<span data-ttu-id="90816-128">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="90816-128">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="90816-129">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="90816-129">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="90816-130">INDATA</span><span class="sxs-lookup"><span data-stu-id="90816-130">INPUTS</span></span>

### <span data-ttu-id="90816-131">System. String</span><span class="sxs-lookup"><span data-stu-id="90816-131">System.String</span></span>

<span data-ttu-id="90816-132">Du kan skicka vidare en sträng som innehåller meddelandet till `Write-Verbose` .</span><span class="sxs-lookup"><span data-stu-id="90816-132">You can pipe a string that contains the message to `Write-Verbose`.</span></span>

## <span data-ttu-id="90816-133">UTDATA</span><span class="sxs-lookup"><span data-stu-id="90816-133">OUTPUTS</span></span>

### <span data-ttu-id="90816-134">Inget</span><span class="sxs-lookup"><span data-stu-id="90816-134">None</span></span>

<span data-ttu-id="90816-135">`Write-Verbose` skriver enbart till den utförliga meddelande strömmen.</span><span class="sxs-lookup"><span data-stu-id="90816-135">`Write-Verbose` writes only to the verbose message stream.</span></span>

## <span data-ttu-id="90816-136">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="90816-136">NOTES</span></span>

- <span data-ttu-id="90816-137">Utförliga meddelanden returneras bara när kommandot använder den **utförliga** gemensamma parametern.</span><span class="sxs-lookup"><span data-stu-id="90816-137">Verbose messages are returned only when the command uses the **Verbose** common parameter.</span></span> <span data-ttu-id="90816-138">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="90816-138">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>
- <span data-ttu-id="90816-139">I Windows PowerShell bakgrunds jobb och fjärrkommandon `$VerbosePreference` avgör variabeln i jobbschemaläggaren och fjärrsession om utförligt meddelande visas som standard.</span><span class="sxs-lookup"><span data-stu-id="90816-139">In Windows PowerShell background jobs and remote commands, the `$VerbosePreference` variable in the job session and remote session determine whether the verbose message is displayed by default.</span></span>
  <span data-ttu-id="90816-140">Mer information om `$VerbosePreference` variabeln finns i [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="90816-140">For more information about the `$VerbosePreference` variable, see [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span></span>

## <span data-ttu-id="90816-141">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="90816-141">RELATED LINKS</span></span>

[<span data-ttu-id="90816-142">about_Output_Streams</span><span class="sxs-lookup"><span data-stu-id="90816-142">about_Output_Streams</span></span>](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[<span data-ttu-id="90816-143">about_Redirection</span><span class="sxs-lookup"><span data-stu-id="90816-143">about_Redirection</span></span>](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[<span data-ttu-id="90816-144">Skriv-debug</span><span class="sxs-lookup"><span data-stu-id="90816-144">Write-Debug</span></span>](Write-Debug.md)

[<span data-ttu-id="90816-145">Skriv-fel</span><span class="sxs-lookup"><span data-stu-id="90816-145">Write-Error</span></span>](Write-Error.md)

[<span data-ttu-id="90816-146">Skriv värd</span><span class="sxs-lookup"><span data-stu-id="90816-146">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="90816-147">Skriv information</span><span class="sxs-lookup"><span data-stu-id="90816-147">Write-Information</span></span>](Write-Information.md)

[<span data-ttu-id="90816-148">Skriva-utdata</span><span class="sxs-lookup"><span data-stu-id="90816-148">Write-Output</span></span>](Write-Output.md)

[<span data-ttu-id="90816-149">Skriv förlopp</span><span class="sxs-lookup"><span data-stu-id="90816-149">Write-Progress</span></span>](Write-Progress.md)

[<span data-ttu-id="90816-150">Skriv varning</span><span class="sxs-lookup"><span data-stu-id="90816-150">Write-Warning</span></span>](Write-Warning.md)
