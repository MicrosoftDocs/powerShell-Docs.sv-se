---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 05/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/clear-history?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-History
ms.openlocfilehash: 1b465779f56c6bd71d7adfa7ffb5b391f5402656
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710909"
---
# <span data-ttu-id="00374-102">Clear-History</span><span class="sxs-lookup"><span data-stu-id="00374-102">Clear-History</span></span>

## <span data-ttu-id="00374-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="00374-103">SYNOPSIS</span></span>
<span data-ttu-id="00374-104">Tar bort poster från PowerShell-sessionens kommando historik.</span><span class="sxs-lookup"><span data-stu-id="00374-104">Deletes entries from the PowerShell session command history.</span></span>

## <span data-ttu-id="00374-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="00374-105">SYNTAX</span></span>

### <span data-ttu-id="00374-106">IDParameter (standard)</span><span class="sxs-lookup"><span data-stu-id="00374-106">IDParameter (Default)</span></span>

```
Clear-History [[-Id] <int[]>] [[-Count] <int>] [-Newest] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="00374-107">CommandLineParameter</span><span class="sxs-lookup"><span data-stu-id="00374-107">CommandLineParameter</span></span>

```
Clear-History [[-Count] <int>] [-CommandLine <string[]>] [-Newest] [-WhatIf] [-Confirm]
[<CommonParameters>]
```

## <span data-ttu-id="00374-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="00374-108">DESCRIPTION</span></span>

<span data-ttu-id="00374-109">`Clear-History` tar bort kommando historiken från en PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="00374-109">`Clear-History` deletes the command history from a PowerShell session.</span></span> <span data-ttu-id="00374-110">Varje PowerShell-session har en egen kommando historik.</span><span class="sxs-lookup"><span data-stu-id="00374-110">Each PowerShell session has its own command history.</span></span> <span data-ttu-id="00374-111">Om du vill visa kommando historiken använder du `Get-History` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="00374-111">To display the command history, use the `Get-History` cmdlet.</span></span>

<span data-ttu-id="00374-112">Som standard `Clear-History` tar bort hela kommando historiken från en PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="00374-112">By default, `Clear-History` deletes the entire command history from a PowerShell session.</span></span> <span data-ttu-id="00374-113">Du kan använda parametrar med `Clear-History` för att ta bort valda kommandon.</span><span class="sxs-lookup"><span data-stu-id="00374-113">You can use parameters with `Clear-History` to delete selected commands.</span></span>

<span data-ttu-id="00374-114">`Clear-History` tar inte bort `PSReadLine` kommando historik filen.</span><span class="sxs-lookup"><span data-stu-id="00374-114">`Clear-History` does not clear the `PSReadLine` command history file.</span></span> <span data-ttu-id="00374-115">`PSReadLine`Modulen lagrar en historik fil som innehåller alla PowerShell-kommandon från varje PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="00374-115">The `PSReadLine` module stores a history file that contains every PowerShell command from every PowerShell session.</span></span> <span data-ttu-id="00374-116">Från en PowerShell-kommandotolk använder du upp-och nedpilarna på tangent bordet för att bläddra genom kommando historiken.</span><span class="sxs-lookup"><span data-stu-id="00374-116">From a PowerShell prompt, use the up and down arrows on your keyboard to scroll through the command history.</span></span> <span data-ttu-id="00374-117">Om du vill visa `PSReadLine` konfigurationen för kommando historik använder du `Get-PSReadLineOption` .</span><span class="sxs-lookup"><span data-stu-id="00374-117">To display the `PSReadLine` configuration for command history, use `Get-PSReadLineOption`.</span></span>
<span data-ttu-id="00374-118">`PSReadLine` levereras med PowerShell 5,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="00374-118">`PSReadLine` shipped with PowerShell 5.0 and above.</span></span> <span data-ttu-id="00374-119">Mer information finns i [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md).</span><span class="sxs-lookup"><span data-stu-id="00374-119">For more information, see [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md).</span></span>

## <span data-ttu-id="00374-120">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="00374-120">EXAMPLES</span></span>

### <span data-ttu-id="00374-121">Exempel 1: ta bort kommando historiken från en PowerShell-session</span><span class="sxs-lookup"><span data-stu-id="00374-121">Example 1: Delete the command history from a PowerShell session</span></span>

<span data-ttu-id="00374-122">Det här kommandot tar bort alla kommandon från en PowerShell-sessions historik.</span><span class="sxs-lookup"><span data-stu-id="00374-122">This command deletes all of the commands from a PowerShell session's history.</span></span>

```powershell
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location .\Test
   2 Update-Help
   3 Set-Location C:\Test\Logs
   4 Get-Location
```

```powershell
Clear-History
Get-History
```

```Output
  Id CommandLine
  -- -----------
   5 Clear-History
```

<span data-ttu-id="00374-123">`Get-History`Cmdleten visar PowerShell-sessionens historik.</span><span class="sxs-lookup"><span data-stu-id="00374-123">The `Get-History` cmdlet displays the PowerShell session's history.</span></span> <span data-ttu-id="00374-124">`Clear-History` tar bort hela kommando historiken.</span><span class="sxs-lookup"><span data-stu-id="00374-124">`Clear-History` deletes the entire command history.</span></span> <span data-ttu-id="00374-125">`Get-History` visar den uppdaterade kommando historiken och bekräftar att den tidigare historiken har tagits bort.</span><span class="sxs-lookup"><span data-stu-id="00374-125">`Get-History` displays the updated command history and confirms the prior history was deleted.</span></span>

### <span data-ttu-id="00374-126">Exempel 2: ta bort de nyaste kommandona</span><span class="sxs-lookup"><span data-stu-id="00374-126">Example 2: Delete the newest commands</span></span>

<span data-ttu-id="00374-127">Det här kommandot använder **antalet** och de **senaste** parametrarna för att ta bort de senaste kommandona från en PowerShell-sessions historik.</span><span class="sxs-lookup"><span data-stu-id="00374-127">This command uses the **Count** and **Newest** parameters to delete the newest commands from a PowerShell session's history.</span></span>

```powershell
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-Command Clear-History
   3 Get-Command Clear-History -Syntax
   4 Get-Command Clear-History -ShowCommandInfo
   5 Get-Help Get-Alias
   6 Get-Command Get-ChildItem -Syntax
   7 Get-Help Clear-History
   8 Set-Location C:\Test\Logs
   9 Get-Help Get-Variable
  10 Get-Help Get-ChildItem
```

```powershell
Clear-History -Count 5 -Newest
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-Command Clear-History
   3 Get-Command Clear-History -Syntax
   4 Get-Command Clear-History -ShowCommandInfo
   5 Get-Help Get-Alias
  11 Clear-History -Count 5 -Newest
```

<span data-ttu-id="00374-128">`Get-History`Cmdleten visar PowerShell-sessionens historik.</span><span class="sxs-lookup"><span data-stu-id="00374-128">The `Get-History` cmdlet displays the PowerShell session's history.</span></span> <span data-ttu-id="00374-129">`Clear-History` används för att ta bort kommando historiken.</span><span class="sxs-lookup"><span data-stu-id="00374-129">`Clear-History` is used to delete the command history.</span></span> <span data-ttu-id="00374-130">Parametern **Count** anger antalet kommandon som ska tas bort, inklusive det angivna ID: **t**. Den **senaste** parametern anger att de nyaste kommandona tas bort från historiken.</span><span class="sxs-lookup"><span data-stu-id="00374-130">The **Count** parameter specifies the number of commands to delete, inclusive of the specified **Id**. The **Newest** parameter specifies that the newest commands are cleared from the history.</span></span> <span data-ttu-id="00374-131">`Get-History`visar den uppdaterade kommando historiken och bekräftar att de fem senaste kommandona har tagits bort, **ID 6**  -  **ID 10**.</span><span class="sxs-lookup"><span data-stu-id="00374-131">`Get-History` displays the updated command history and confirms that the five newest commands were deleted, **Id 6** - **Id 10**.</span></span>

### <span data-ttu-id="00374-132">Exempel 3: ta bort kommandon som matchar vissa villkor</span><span class="sxs-lookup"><span data-stu-id="00374-132">Example 3: Delete commands that match specific criteria</span></span>

<span data-ttu-id="00374-133">Det här kommandot tar bort kommandon som matchar de kriterier som har definierats av **kommando rads** parametern.</span><span class="sxs-lookup"><span data-stu-id="00374-133">This command deletes commands that match specific criteria defined by the **CommandLine** parameter.</span></span>

```powershell
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-Command Clear-History
   3 Get-Command Clear-History -Syntax
   4 Get-Command Clear-History -ShowCommandInfo
   5 Get-Help Get-Alias
   6 Get-Command Get-ChildItem -Syntax
   7 Get-Help Clear-History
```

```powershell
Clear-History -CommandLine *Help*, *Syntax
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-Command Clear-History
   4 Get-Command Clear-History -ShowCommandInfo
   8 Clear-History -CommandLine *Help*, *Syntax
```

<span data-ttu-id="00374-134">`Get-History`Cmdleten visar PowerShell-sessionens historik.</span><span class="sxs-lookup"><span data-stu-id="00374-134">The `Get-History` cmdlet displays the PowerShell session's history.</span></span> <span data-ttu-id="00374-135">`Clear-History` tar bort kommando historiken.</span><span class="sxs-lookup"><span data-stu-id="00374-135">`Clear-History` deletes the command history.</span></span> <span data-ttu-id="00374-136">Parametern **CommandLine** anger kommandon som innehåller **Hjälp** eller slutar med **syntax**.</span><span class="sxs-lookup"><span data-stu-id="00374-136">The **CommandLine** parameter specifies commands that contain **Help** or end with **Syntax**.</span></span> <span data-ttu-id="00374-137">`Get-History` visar den uppdaterade kommando historiken och bekräftar att kommando **-ID 3**, **ID 5**, **ID 6** och **ID 7** har tagits bort.</span><span class="sxs-lookup"><span data-stu-id="00374-137">`Get-History` displays the updated command history and confirms that commands **Id 3**, **Id 5**, **Id 6**, and **Id 7** were deleted.</span></span>

### <span data-ttu-id="00374-138">Exempel 4: ta bort kommandon efter ID-nummer</span><span class="sxs-lookup"><span data-stu-id="00374-138">Example 4: Delete commands by Id number</span></span>

<span data-ttu-id="00374-139">Detta kommando tar bort vissa historik objekt med hjälp av **ID**. Om du vill ta bort flera kommandon skickar du en kommaavgränsad lista med **ID-** nummer.</span><span class="sxs-lookup"><span data-stu-id="00374-139">This command deletes specific history items using the **Id**. To delete multiple commands, submit a comma-separated list of **Id** numbers.</span></span>

```powershell
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-History
   3 Get-Help Get-Alias
   4 Get-Command Clear-History
   5 Get-Command Clear-History -Syntax
   6 Get-Command Clear-History -ShowCommandInfo
```

```powershell
Clear-History -Id 3, 5
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-History
   4 Get-Command Clear-History
   6 Get-Command Clear-History -ShowCommandInfo
   7 Get-History
   8 Clear-History -Id 3, 5
```

<span data-ttu-id="00374-140">`Get-History`Cmdleten visar PowerShell-sessionens historik.</span><span class="sxs-lookup"><span data-stu-id="00374-140">The `Get-History` cmdlet displays the PowerShell session's history.</span></span> <span data-ttu-id="00374-141">`Clear-History` tar bort kommando historiken.</span><span class="sxs-lookup"><span data-stu-id="00374-141">`Clear-History` deletes the command history.</span></span> <span data-ttu-id="00374-142">Parametern **ID** anger vilka kommandon som ska tas bort.</span><span class="sxs-lookup"><span data-stu-id="00374-142">The **Id** parameter specifies which commands to delete.</span></span> <span data-ttu-id="00374-143">`Get-History` visar den uppdaterade kommando historiken och bekräftar att **ID 3** och **ID 5** har tagits bort.</span><span class="sxs-lookup"><span data-stu-id="00374-143">`Get-History` displays the updated command history and confirms that **Id 3** and **Id 5** were deleted.</span></span>

### <span data-ttu-id="00374-144">Exempel 5: ta bort kommandon efter ID-nummer och antal</span><span class="sxs-lookup"><span data-stu-id="00374-144">Example 5: Delete commands by Id number and count</span></span>

<span data-ttu-id="00374-145">Det här kommandot använder parametrarna **ID** och **Count** för att ta bort kommando historiken.</span><span class="sxs-lookup"><span data-stu-id="00374-145">This command uses the **Id** and **Count** parameters to delete command history.</span></span> <span data-ttu-id="00374-146">Kommandon tas bort från det angivna **ID: t** i omvänd ordning, nyaste till äldsta.</span><span class="sxs-lookup"><span data-stu-id="00374-146">Commands are deleted from the specified **Id** in reverse order, newest to oldest.</span></span>

```powershell
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-Command Clear-History
   3 Get-Command Clear-History -Syntax
   4 Get-Command Clear-History -ShowCommandInfo
   5 Get-Help Get-Alias
   6 Get-Command Get-ChildItem -Syntax
   7 Get-Help Clear-History
   8 Set-Location C:\Test\Logs
   9 Get-Help Get-Variable
  10 Get-Help Get-ChildItem
```

```powershell
Clear-History -Id 7 -Count 5
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-Command Clear-History
   8 Set-Location C:\Test\Logs
   9 Get-Help Get-Variable
  10 Get-Help Get-ChildItem
  11 Clear-History -Id 7 -Count 5
```

<span data-ttu-id="00374-147">`Get-History`Cmdleten visar PowerShell-sessionens historik.</span><span class="sxs-lookup"><span data-stu-id="00374-147">The `Get-History` cmdlet displays the PowerShell session's history.</span></span> <span data-ttu-id="00374-148">`Clear-History` tar bort kommando historiken.</span><span class="sxs-lookup"><span data-stu-id="00374-148">`Clear-History` deletes the command history.</span></span> <span data-ttu-id="00374-149">**ID-** parametern anger att börjar med **ID 7**.</span><span class="sxs-lookup"><span data-stu-id="00374-149">The **Id** parameter specifies to begin with **Id 7**.</span></span> <span data-ttu-id="00374-150">Parametern **Count** anger att fem kommandon ska tas bort, inklusive det angivna **ID: t**. `Get-History`visar den uppdaterade kommando historiken och bekräftar att fem kommandon har tagits bort, **ID 3**  -  **ID 7**.</span><span class="sxs-lookup"><span data-stu-id="00374-150">The **Count** parameter specifies to delete five commands, inclusive of the specified **Id**. `Get-History` displays the updated command history and confirms that five commands were deleted, **Id 3** - **Id 7**.</span></span>

## <span data-ttu-id="00374-151">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="00374-151">PARAMETERS</span></span>

### <span data-ttu-id="00374-152">-Kommandorad</span><span class="sxs-lookup"><span data-stu-id="00374-152">-CommandLine</span></span>

<span data-ttu-id="00374-153">Tar bort kommando historik från en PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="00374-153">Deletes command history from a PowerShell session.</span></span> <span data-ttu-id="00374-154">Strängen måste vara en exakt matchning eller använda jokertecken för att matcha kommandon i PowerShell-sessionens historik som visas av `Get-History` .</span><span class="sxs-lookup"><span data-stu-id="00374-154">The string must be an exact match or use wildcards to match commands in the PowerShell session history displayed by `Get-History`.</span></span> <span data-ttu-id="00374-155">Om du anger mer än en sträng `Clear-History` tar bort kommandon som matchar någon av strängarna.</span><span class="sxs-lookup"><span data-stu-id="00374-155">If you enter more than one string, `Clear-History` deletes commands that match any of the strings.</span></span> <span data-ttu-id="00374-156">**Kommando rads** parametern kan användas med **Count**.</span><span class="sxs-lookup"><span data-stu-id="00374-156">The **CommandLine** parameter can be used with **Count**.</span></span>

<span data-ttu-id="00374-157">Använd enkla offerter för strängar med ett blank steg.</span><span class="sxs-lookup"><span data-stu-id="00374-157">For strings with a space, use single quotations.</span></span> <span data-ttu-id="00374-158">Mer information finns i [about_Quoting_Rules](About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="00374-158">For more information, see [about_Quoting_Rules](About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: CommandLineParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="00374-159">-Antal</span><span class="sxs-lookup"><span data-stu-id="00374-159">-Count</span></span>

<span data-ttu-id="00374-160">Anger antalet historik poster som `Clear-History` tas bort.</span><span class="sxs-lookup"><span data-stu-id="00374-160">Specifies the number of history entries that `Clear-History` deletes.</span></span> <span data-ttu-id="00374-161">Kommandona tas bort i ordning, från och med den äldsta posten i historiken.</span><span class="sxs-lookup"><span data-stu-id="00374-161">Commands are deleted in order, beginning with the oldest entry in the history.</span></span>

<span data-ttu-id="00374-162">Parametrarna **Count** och **ID** kan användas tillsammans.</span><span class="sxs-lookup"><span data-stu-id="00374-162">The **Count** and **Id** parameters can be used together.</span></span> <span data-ttu-id="00374-163">Parametern **Count** anger antalet kommandon som ska tas bort, inklusive det angivna ID: **t**. Från och med det angivna **ID: t** raderas kommandon i omvänd ordning.</span><span class="sxs-lookup"><span data-stu-id="00374-163">The **Count** parameter specifies the number of commands to delete, inclusive of the specified **Id**. Beginning at the specified **Id**, commands are deleted in reverse sequential order.</span></span> <span data-ttu-id="00374-164">Om **ID:** t till exempel är 30 och **antalet** är 10, `Clear-History` tar bort objekt 21 till 30.</span><span class="sxs-lookup"><span data-stu-id="00374-164">For example, if the **Id** is 30 and the **Count** is 10, `Clear-History` deletes items 21 through 30.</span></span>

<span data-ttu-id="00374-165">Parametrarna **Count** och **CommandLine** kan användas tillsammans.</span><span class="sxs-lookup"><span data-stu-id="00374-165">The **Count** and **CommandLine** parameters can be used together.</span></span> <span data-ttu-id="00374-166">**Count** anger antalet kommandon som ska tas bort och som matchar parameter värde för **kommando raden** .</span><span class="sxs-lookup"><span data-stu-id="00374-166">**Count** specifies the number of commands to delete that match **CommandLine** parameter value.</span></span> <span data-ttu-id="00374-167">Kommandona tas bort i sekventiell ordning.</span><span class="sxs-lookup"><span data-stu-id="00374-167">The commands are deleted in sequential order.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="00374-168">-ID</span><span class="sxs-lookup"><span data-stu-id="00374-168">-Id</span></span>

<span data-ttu-id="00374-169">Anger det **ID** för kommando historik som `Clear-History` tar bort.</span><span class="sxs-lookup"><span data-stu-id="00374-169">Specifies the command history **Id** that `Clear-History` deletes.</span></span> <span data-ttu-id="00374-170">Använd cmdleten om du vill visa **ID-** nummer `Get-History` .</span><span class="sxs-lookup"><span data-stu-id="00374-170">To display **Id** numbers, use the `Get-History` cmdlet.</span></span> <span data-ttu-id="00374-171">**ID-** numren är sekventiella och kommandon behåller sina **ID-** nummer i en PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="00374-171">The **Id** numbers are sequential and commands keep their **Id** number throughout a PowerShell session.</span></span> <span data-ttu-id="00374-172">**ID-** parametern kan användas med **Count** och **nyast**.</span><span class="sxs-lookup"><span data-stu-id="00374-172">The **Id** parameter can be used with **Count** and **Newest**.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: IDParameter
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="00374-173">– Nyaste</span><span class="sxs-lookup"><span data-stu-id="00374-173">-Newest</span></span>

<span data-ttu-id="00374-174">När den **senaste** parametern används `Clear-History` raderas de senaste posterna i historiken.</span><span class="sxs-lookup"><span data-stu-id="00374-174">When the **Newest** parameter is used, `Clear-History` deletes the newest entries in the history.</span></span> <span data-ttu-id="00374-175">Som standard `Clear-History` raderas de äldsta posterna i historiken.</span><span class="sxs-lookup"><span data-stu-id="00374-175">By default, `Clear-History` deletes the oldest entries in the history.</span></span>

<span data-ttu-id="00374-176">Den **senaste** parametern kan användas med **ID** och **Count**.</span><span class="sxs-lookup"><span data-stu-id="00374-176">The **Newest** parameter can be used with **Id** and **Count**.</span></span> <span data-ttu-id="00374-177">Parametern **Count** anger antalet kommandon som ska tas bort, inklusive det angivna ID: **t**. Från och med det angivna **ID: t** raderas kommandon i sekventiell ordning.</span><span class="sxs-lookup"><span data-stu-id="00374-177">The **Count** parameter specifies the number of commands to delete, inclusive of the specified **Id**. Beginning at the specified **Id**, commands are deleted in sequential order.</span></span> <span data-ttu-id="00374-178">Om **ID:** t till exempel är 30 och **antalet** är 10, `Clear-History` tar bort objekt 30 till 39.</span><span class="sxs-lookup"><span data-stu-id="00374-178">For example, if the **Id** is 30 and the **Count** is 10, `Clear-History` deletes items 30 through 39.</span></span>

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

### <span data-ttu-id="00374-179">-Confirm</span><span class="sxs-lookup"><span data-stu-id="00374-179">-Confirm</span></span>

<span data-ttu-id="00374-180">Du uppmanas att bekräfta innan du kör `Clear-History` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="00374-180">Prompts you for confirmation before running the `Clear-History` cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="00374-181">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="00374-181">-WhatIf</span></span>

<span data-ttu-id="00374-182">Visar vad som händer om `Clear-History` cmdleten körs.</span><span class="sxs-lookup"><span data-stu-id="00374-182">Shows what would happen if the `Clear-History` cmdlet runs.</span></span> <span data-ttu-id="00374-183">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="00374-183">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="00374-184">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="00374-184">CommonParameters</span></span>

<span data-ttu-id="00374-185">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="00374-185">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="00374-186">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="00374-186">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="00374-187">INDATA</span><span class="sxs-lookup"><span data-stu-id="00374-187">INPUTS</span></span>

### <span data-ttu-id="00374-188">Inga</span><span class="sxs-lookup"><span data-stu-id="00374-188">None</span></span>

<span data-ttu-id="00374-189">Det går inte att skicka pipe-objekt till `Clear-History` .</span><span class="sxs-lookup"><span data-stu-id="00374-189">You cannot pipe objects to `Clear-History`.</span></span>

## <span data-ttu-id="00374-190">UTDATA</span><span class="sxs-lookup"><span data-stu-id="00374-190">OUTPUTS</span></span>

### <span data-ttu-id="00374-191">Inga</span><span class="sxs-lookup"><span data-stu-id="00374-191">None</span></span>

<span data-ttu-id="00374-192">`Clear-History` genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="00374-192">`Clear-History` does not generate any output.</span></span>

## <span data-ttu-id="00374-193">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="00374-193">NOTES</span></span>

<span data-ttu-id="00374-194">PowerShell-sessionens historik är en lista över kommandon som angavs under en PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="00374-194">The PowerShell session history is a list of the commands entered during a PowerShell session.</span></span> <span data-ttu-id="00374-195">Du kan visa historik, Lägg till och ta bort kommandon och köra kommandon från historiken.</span><span class="sxs-lookup"><span data-stu-id="00374-195">You can view the history, add and delete commands, and run commands from the history.</span></span> <span data-ttu-id="00374-196">Mer information finns i [about_History](About/about_History.md).</span><span class="sxs-lookup"><span data-stu-id="00374-196">For more information, see [about_History](About/about_History.md).</span></span>

<span data-ttu-id="00374-197">Historiken för sessionen hanteras separat från historiken som underhålls av **PSReadLine** -modulen.</span><span class="sxs-lookup"><span data-stu-id="00374-197">The session history is managed separately from the history maintained by the **PSReadLine** module.</span></span>
<span data-ttu-id="00374-198">Båda historiken är tillgängliga i sessioner där **PSReadLine** har lästs in.</span><span class="sxs-lookup"><span data-stu-id="00374-198">Both histories are available in sessions where **PSReadLine** is loaded.</span></span> <span data-ttu-id="00374-199">Den här cmdleten fungerar bara med tidigare session.</span><span class="sxs-lookup"><span data-stu-id="00374-199">This cmdlet only works with the session history.</span></span> <span data-ttu-id="00374-200">Mer information finns i [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md).</span><span class="sxs-lookup"><span data-stu-id="00374-200">For more information see, [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md).</span></span>

## <span data-ttu-id="00374-201">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="00374-201">RELATED LINKS</span></span>

[<span data-ttu-id="00374-202">about_History</span><span class="sxs-lookup"><span data-stu-id="00374-202">about_History</span></span>](About/about_History.md)

[<span data-ttu-id="00374-203">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="00374-203">about_PSReadLine</span></span>](../PSReadLine/About/about_PSReadLine.md)

[<span data-ttu-id="00374-204">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="00374-204">about_Quoting_Rules</span></span>](About/about_Quoting_Rules.md)

[<span data-ttu-id="00374-205">Lägg till-historik</span><span class="sxs-lookup"><span data-stu-id="00374-205">Add-History</span></span>](Add-History.md)

[<span data-ttu-id="00374-206">Hämta historik</span><span class="sxs-lookup"><span data-stu-id="00374-206">Get-History</span></span>](Get-History.md)

[<span data-ttu-id="00374-207">Anropa-historik</span><span class="sxs-lookup"><span data-stu-id="00374-207">Invoke-History</span></span>](Invoke-History.md)

[<span data-ttu-id="00374-208">Get-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="00374-208">Get-PSReadLineOption</span></span>](/powershell/module/psreadline/get-psreadlineoption)

[<span data-ttu-id="00374-209">Set-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="00374-209">Set-PSReadLineOption</span></span>](/powershell/module/psreadline/set-psreadlineoption)

