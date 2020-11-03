---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-warning?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Warning
ms.openlocfilehash: 7e74e53bd056a452917d2f2380b817fc6925f0fe
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/16/2020
ms.locfileid: "93272793"
---
# <span data-ttu-id="c4acb-103">Write-Warning</span><span class="sxs-lookup"><span data-stu-id="c4acb-103">Write-Warning</span></span>

## <span data-ttu-id="c4acb-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="c4acb-104">SYNOPSIS</span></span>
<span data-ttu-id="c4acb-105">Skriver ett varnings meddelande.</span><span class="sxs-lookup"><span data-stu-id="c4acb-105">Writes a warning message.</span></span>

## <span data-ttu-id="c4acb-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c4acb-106">SYNTAX</span></span>

```
Write-Warning [-Message] <String> [<CommonParameters>]
```

## <span data-ttu-id="c4acb-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="c4acb-107">DESCRIPTION</span></span>

<span data-ttu-id="c4acb-108">`Write-Warning`Cmdleten skriver ett varnings meddelande till PowerShell-värden.</span><span class="sxs-lookup"><span data-stu-id="c4acb-108">The `Write-Warning` cmdlet writes a warning message to the PowerShell host.</span></span> <span data-ttu-id="c4acb-109">Svaret på varningen beror på värdet på användarens `$WarningPreference` variabel och användningen av den gemensamma **WarningAction** -parametern.</span><span class="sxs-lookup"><span data-stu-id="c4acb-109">The response to the warning depends on the value of the user's `$WarningPreference` variable and the use of the **WarningAction** common parameter.</span></span>

## <span data-ttu-id="c4acb-110">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="c4acb-110">EXAMPLES</span></span>

### <span data-ttu-id="c4acb-111">Exempel 1: Skriv ett varnings meddelande</span><span class="sxs-lookup"><span data-stu-id="c4acb-111">Example 1: Write a warning message</span></span>

<span data-ttu-id="c4acb-112">Det här kommandot visar meddelandet "Varning: Detta är bara en test varning".</span><span class="sxs-lookup"><span data-stu-id="c4acb-112">This command displays the message "WARNING: This is only a test warning."</span></span>

```powershell
Write-Warning "This is only a test warning."
```

### <span data-ttu-id="c4acb-113">Exempel 2: skicka en sträng till Write-Warning</span><span class="sxs-lookup"><span data-stu-id="c4acb-113">Example 2: Pass a string to Write-Warning</span></span>

<span data-ttu-id="c4acb-114">Det här kommandot visar att du kan använda en pipeline-operator ( `|` ) för att skicka en sträng till `Write-Warning` .</span><span class="sxs-lookup"><span data-stu-id="c4acb-114">This command shows that you can use a pipeline operator (`|`) to send a string to `Write-Warning`.</span></span>
<span data-ttu-id="c4acb-115">Du kan spara strängen i en variabel, som du ser i det här kommandot eller skicka vidare strängen direkt till `Write-Warning` .</span><span class="sxs-lookup"><span data-stu-id="c4acb-115">You can save the string in a variable, as shown in this command, or pipe the string directly to `Write-Warning`.</span></span>

```powershell
$w = "This is only a test warning."
$w | Write-Warning
```

### <span data-ttu-id="c4acb-116">Exempel 3: Ange variabeln $WarningPreference och skriv en varning</span><span class="sxs-lookup"><span data-stu-id="c4acb-116">Example 3: Set the $WarningPreference variable and write a warning</span></span>

<span data-ttu-id="c4acb-117">I det här exemplet visas resultatet av `$WarningPreference` variabeln i ett `Write-Warning` kommando.</span><span class="sxs-lookup"><span data-stu-id="c4acb-117">This example shows the effect of the value of the `$WarningPreference` variable on a `Write-Warning` command.</span></span>

```powershell
PS> $WarningPreference
Continue
PS> Write-Warning "This is only a test warning."
This is only a test warning.
PS> $WarningPreference = "SilentlyContinue"
PS> Write-Warning "This is only a test warning."
PS> $WarningPreference = "Stop"
PS> Write-Warning "This is only a test warning."
WARNING: This is only a test message.
Write-Warning : Command execution stopped because the shell variable "WarningPreference" is set to Stop.
At line:1 char:14
     + Write-Warning <<<<  "This is only a test message."
```

<span data-ttu-id="c4acb-118">Det första kommandot visar standardvärdet för `$WarningPreference` variabeln, som är `Continue` .</span><span class="sxs-lookup"><span data-stu-id="c4acb-118">The first command displays the default value of the `$WarningPreference` variable, which is `Continue`.</span></span> <span data-ttu-id="c4acb-119">Det innebär att när du skriver en varning visas varnings meddelandet och körningen fortsätter.</span><span class="sxs-lookup"><span data-stu-id="c4acb-119">As a result, when you write a warning, the warning message is displayed and execution continues.</span></span>

<span data-ttu-id="c4acb-120">När du ändrar värdet för `$WarningPreference` variabeln ändras effekterna av `Write-Warning` kommandot igen.</span><span class="sxs-lookup"><span data-stu-id="c4acb-120">When you change the value of the `$WarningPreference` variable, the effect of the `Write-Warning` command changes again.</span></span> <span data-ttu-id="c4acb-121">Värdet `SilentlyContinue` förhindrar varningen.</span><span class="sxs-lookup"><span data-stu-id="c4acb-121">A value of `SilentlyContinue` suppresses the warning.</span></span> <span data-ttu-id="c4acb-122">Värdet `Stop` visar varningen och sedan stoppas körningen av kommandot.</span><span class="sxs-lookup"><span data-stu-id="c4acb-122">A value of `Stop` displays the warning and then stops execution of the command.</span></span>

<span data-ttu-id="c4acb-123">Mer information om `$WarningPreference` variabeln finns i [about_Preference_Variables](../Microsoft.Powershell.Core/About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="c4acb-123">For more information about the `$WarningPreference` variable, see [about_Preference_Variables](../Microsoft.Powershell.Core/About/about_Preference_Variables.md).</span></span>

### <span data-ttu-id="c4acb-124">Exempel 4: ange parametern WarningAction och skriv en varning</span><span class="sxs-lookup"><span data-stu-id="c4acb-124">Example 4: Set the WarningAction parameter and write a warning</span></span>

<span data-ttu-id="c4acb-125">Det här exemplet visar effekterna av den gemensamma parametern **WarningAction** i ett `Write-Warning` kommando.</span><span class="sxs-lookup"><span data-stu-id="c4acb-125">This example shows the effect of the **WarningAction** common parameter on a `Write-Warning` command.</span></span> <span data-ttu-id="c4acb-126">Du kan använda den gemensamma parametern **WarningAction** med valfri cmdlet för att avgöra hur PowerShell svarar på varningar som orsakas av kommandot.</span><span class="sxs-lookup"><span data-stu-id="c4acb-126">You can use the **WarningAction** common parameter with any cmdlet to determine how PowerShell responds to warnings resulting from that command.</span></span> <span data-ttu-id="c4acb-127">Parametern **WarningAction** common åsidosätter bara värdet för det `$WarningPreference` specifika kommandot.</span><span class="sxs-lookup"><span data-stu-id="c4acb-127">The **WarningAction** common parameter overrides the value of the `$WarningPreference` only for that particular command.</span></span>

```powershell
PS> Write-Warning "This is only a test warning." -WarningAction Inquire
WARNING: This is only a test warning.
Confirm
Continue with this operation?
 [Y] Yes  [A] Yes to All  [H] Halt Command  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="c4acb-128">Detta kommando använder `Write-Warning` cmdleten för att visa en varning.</span><span class="sxs-lookup"><span data-stu-id="c4acb-128">This command uses the `Write-Warning` cmdlet to display a warning.</span></span> <span data-ttu-id="c4acb-129">Den gemensamma parametern **WarningAction** med värdet fråga instruerar systemet att fråga användaren när kommandot visar en varning.</span><span class="sxs-lookup"><span data-stu-id="c4acb-129">The **WarningAction** common parameter with a value of Inquire directs the system to prompt the user when the command displays a warning.</span></span>

<span data-ttu-id="c4acb-130">Mer information om den gemensamma parametern **WarningAction** finns [about_CommonParameters](../Microsoft.Powershell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="c4acb-130">For more information about the **WarningAction** common parameter, see [about_CommonParameters](../Microsoft.Powershell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="c4acb-131">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="c4acb-131">PARAMETERS</span></span>

### <span data-ttu-id="c4acb-132">– Meddelande</span><span class="sxs-lookup"><span data-stu-id="c4acb-132">-Message</span></span>
<span data-ttu-id="c4acb-133">Anger varnings meddelandet.</span><span class="sxs-lookup"><span data-stu-id="c4acb-133">Specifies the warning message.</span></span>

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

### <span data-ttu-id="c4acb-134">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c4acb-134">CommonParameters</span></span>

<span data-ttu-id="c4acb-135">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c4acb-135">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c4acb-136">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="c4acb-136">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c4acb-137">INDATA</span><span class="sxs-lookup"><span data-stu-id="c4acb-137">INPUTS</span></span>

### <span data-ttu-id="c4acb-138">System. String</span><span class="sxs-lookup"><span data-stu-id="c4acb-138">System.String</span></span>

<span data-ttu-id="c4acb-139">Du kan skicka vidare en sträng som innehåller varningen till `Write-Warning` .</span><span class="sxs-lookup"><span data-stu-id="c4acb-139">You can pipe a string that contains the warning to `Write-Warning`.</span></span>

## <span data-ttu-id="c4acb-140">UTDATA</span><span class="sxs-lookup"><span data-stu-id="c4acb-140">OUTPUTS</span></span>

### <span data-ttu-id="c4acb-141">Inget</span><span class="sxs-lookup"><span data-stu-id="c4acb-141">None</span></span>

<span data-ttu-id="c4acb-142">`Write-Warning` skriver endast till varnings strömmen.</span><span class="sxs-lookup"><span data-stu-id="c4acb-142">`Write-Warning` writes only to the warning stream.</span></span> <span data-ttu-id="c4acb-143">Inga andra utdata genereras.</span><span class="sxs-lookup"><span data-stu-id="c4acb-143">It does not generate any other output.</span></span>

## <span data-ttu-id="c4acb-144">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="c4acb-144">NOTES</span></span>

<span data-ttu-id="c4acb-145">Standardvärdet för `$WarningPreference` variabeln är `Continue` , som visar varningen och fortsätter att köra kommandot.</span><span class="sxs-lookup"><span data-stu-id="c4acb-145">The default value for the `$WarningPreference` variable is `Continue`, which displays the warning and then continues executing the command.</span></span> <span data-ttu-id="c4acb-146">Om du vill fastställa giltiga värden för en inställnings variabel, till exempel `$WarningPreference` , anger du den till en sträng med slumpmässiga tecken, till exempel "ABC".</span><span class="sxs-lookup"><span data-stu-id="c4acb-146">To determine valid values for a preference variable such as `$WarningPreference`, set it to a string of random characters, such as "abc".</span></span> <span data-ttu-id="c4acb-147">I det resulterande fel meddelandet visas giltiga värden.</span><span class="sxs-lookup"><span data-stu-id="c4acb-147">The resulting error message lists the valid values.</span></span>

## <span data-ttu-id="c4acb-148">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="c4acb-148">RELATED LINKS</span></span>

[<span data-ttu-id="c4acb-149">about_Output_Streams</span><span class="sxs-lookup"><span data-stu-id="c4acb-149">about_Output_Streams</span></span>](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[<span data-ttu-id="c4acb-150">about_Redirection</span><span class="sxs-lookup"><span data-stu-id="c4acb-150">about_Redirection</span></span>](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[<span data-ttu-id="c4acb-151">Skriv-debug</span><span class="sxs-lookup"><span data-stu-id="c4acb-151">Write-Debug</span></span>](Write-Debug.md)

[<span data-ttu-id="c4acb-152">Skriv-fel</span><span class="sxs-lookup"><span data-stu-id="c4acb-152">Write-Error</span></span>](Write-Error.md)

[<span data-ttu-id="c4acb-153">Skriv värd</span><span class="sxs-lookup"><span data-stu-id="c4acb-153">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="c4acb-154">Skriv information</span><span class="sxs-lookup"><span data-stu-id="c4acb-154">Write-Information</span></span>](Write-Information.md)

[<span data-ttu-id="c4acb-155">Skriva-utdata</span><span class="sxs-lookup"><span data-stu-id="c4acb-155">Write-Output</span></span>](Write-Output.md)

[<span data-ttu-id="c4acb-156">Skriv förlopp</span><span class="sxs-lookup"><span data-stu-id="c4acb-156">Write-Progress</span></span>](Write-Progress.md)

[<span data-ttu-id="c4acb-157">Skriv-verbose</span><span class="sxs-lookup"><span data-stu-id="c4acb-157">Write-Verbose</span></span>](Write-Verbose.md)
