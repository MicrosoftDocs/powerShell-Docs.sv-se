---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 05/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/clear-history?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-History
ms.openlocfilehash: 332cab9d8a635bd4b7deb3c4792e528c8a25e887
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263679"
---
# <span data-ttu-id="d3f42-103">Clear-History</span><span class="sxs-lookup"><span data-stu-id="d3f42-103">Clear-History</span></span>

## <span data-ttu-id="d3f42-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="d3f42-104">SYNOPSIS</span></span>
<span data-ttu-id="d3f42-105">Tar bort poster från PowerShell-sessionens kommando historik.</span><span class="sxs-lookup"><span data-stu-id="d3f42-105">Deletes entries from the PowerShell session command history.</span></span>

## <span data-ttu-id="d3f42-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d3f42-106">SYNTAX</span></span>

### <span data-ttu-id="d3f42-107">IDParameter (standard)</span><span class="sxs-lookup"><span data-stu-id="d3f42-107">IDParameter (Default)</span></span>

```
Clear-History [[-Id] <int[]>] [[-Count] <int>] [-Newest] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="d3f42-108">CommandLineParameter</span><span class="sxs-lookup"><span data-stu-id="d3f42-108">CommandLineParameter</span></span>

```
Clear-History [[-Count] <int>] [-CommandLine <string[]>] [-Newest] [-WhatIf] [-Confirm]
[<CommonParameters>]
```

## <span data-ttu-id="d3f42-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="d3f42-109">DESCRIPTION</span></span>

<span data-ttu-id="d3f42-110">`Clear-History` tar bort kommando historiken från en PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="d3f42-110">`Clear-History` deletes the command history from a PowerShell session.</span></span> <span data-ttu-id="d3f42-111">Varje PowerShell-session har en egen kommando historik.</span><span class="sxs-lookup"><span data-stu-id="d3f42-111">Each PowerShell session has its own command history.</span></span> <span data-ttu-id="d3f42-112">Om du vill visa kommando historiken använder du `Get-History` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="d3f42-112">To display the command history, use the `Get-History` cmdlet.</span></span>

<span data-ttu-id="d3f42-113">Som standard `Clear-History` tar bort hela kommando historiken från en PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="d3f42-113">By default, `Clear-History` deletes the entire command history from a PowerShell session.</span></span> <span data-ttu-id="d3f42-114">Du kan använda parametrar med `Clear-History` för att ta bort valda kommandon.</span><span class="sxs-lookup"><span data-stu-id="d3f42-114">You can use parameters with `Clear-History` to delete selected commands.</span></span>

<span data-ttu-id="d3f42-115">`Clear-History` tar inte bort `PSReadLine` kommando historik filen.</span><span class="sxs-lookup"><span data-stu-id="d3f42-115">`Clear-History` does not clear the `PSReadLine` command history file.</span></span> <span data-ttu-id="d3f42-116">`PSReadLine`Modulen lagrar en historik fil som innehåller alla PowerShell-kommandon från varje PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="d3f42-116">The `PSReadLine` module stores a history file that contains every PowerShell command from every PowerShell session.</span></span> <span data-ttu-id="d3f42-117">Från en PowerShell-kommandotolk använder du upp-och nedpilarna på tangent bordet för att bläddra genom kommando historiken.</span><span class="sxs-lookup"><span data-stu-id="d3f42-117">From a PowerShell prompt, use the up and down arrows on your keyboard to scroll through the command history.</span></span> <span data-ttu-id="d3f42-118">Om du vill visa `PSReadLine` konfigurationen för kommando historik använder du `Get-PSReadLineOption` .</span><span class="sxs-lookup"><span data-stu-id="d3f42-118">To display the `PSReadLine` configuration for command history, use `Get-PSReadLineOption`.</span></span>
<span data-ttu-id="d3f42-119">`PSReadLine` levereras med PowerShell 5,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="d3f42-119">`PSReadLine` shipped with PowerShell 5.0 and above.</span></span> <span data-ttu-id="d3f42-120">Mer information finns i [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md).</span><span class="sxs-lookup"><span data-stu-id="d3f42-120">For more information, see [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md).</span></span>

## <span data-ttu-id="d3f42-121">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="d3f42-121">EXAMPLES</span></span>

### <span data-ttu-id="d3f42-122">Exempel 1: ta bort kommando historiken från en PowerShell-session</span><span class="sxs-lookup"><span data-stu-id="d3f42-122">Example 1: Delete the command history from a PowerShell session</span></span>

<span data-ttu-id="d3f42-123">Det här kommandot tar bort alla kommandon från en PowerShell-sessions historik.</span><span class="sxs-lookup"><span data-stu-id="d3f42-123">This command deletes all of the commands from a PowerShell session's history.</span></span>

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

<span data-ttu-id="d3f42-124">`Get-History`Cmdleten visar PowerShell-sessionens historik.</span><span class="sxs-lookup"><span data-stu-id="d3f42-124">The `Get-History` cmdlet displays the PowerShell session's history.</span></span> <span data-ttu-id="d3f42-125">`Clear-History` tar bort hela kommando historiken.</span><span class="sxs-lookup"><span data-stu-id="d3f42-125">`Clear-History` deletes the entire command history.</span></span> <span data-ttu-id="d3f42-126">`Get-History` visar den uppdaterade kommando historiken och bekräftar att den tidigare historiken har tagits bort.</span><span class="sxs-lookup"><span data-stu-id="d3f42-126">`Get-History` displays the updated command history and confirms the prior history was deleted.</span></span>

### <span data-ttu-id="d3f42-127">Exempel 2: ta bort de nyaste kommandona</span><span class="sxs-lookup"><span data-stu-id="d3f42-127">Example 2: Delete the newest commands</span></span>

<span data-ttu-id="d3f42-128">Det här kommandot använder **antalet** och de **senaste** parametrarna för att ta bort de senaste kommandona från en PowerShell-sessions historik.</span><span class="sxs-lookup"><span data-stu-id="d3f42-128">This command uses the **Count** and **Newest** parameters to delete the newest commands from a PowerShell session's history.</span></span>

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

<span data-ttu-id="d3f42-129">`Get-History`Cmdleten visar PowerShell-sessionens historik.</span><span class="sxs-lookup"><span data-stu-id="d3f42-129">The `Get-History` cmdlet displays the PowerShell session's history.</span></span> <span data-ttu-id="d3f42-130">`Clear-History` används för att ta bort kommando historiken.</span><span class="sxs-lookup"><span data-stu-id="d3f42-130">`Clear-History` is used to delete the command history.</span></span> <span data-ttu-id="d3f42-131">Parametern **Count** anger antalet kommandon som ska tas bort, inklusive det angivna ID: **t**. Den **senaste** parametern anger att de nyaste kommandona tas bort från historiken.</span><span class="sxs-lookup"><span data-stu-id="d3f42-131">The **Count** parameter specifies the number of commands to delete, inclusive of the specified **Id**. The **Newest** parameter specifies that the newest commands are cleared from the history.</span></span> <span data-ttu-id="d3f42-132">`Get-History`visar den uppdaterade kommando historiken och bekräftar att de fem senaste kommandona har tagits bort, **ID 6**  -  **ID 10**.</span><span class="sxs-lookup"><span data-stu-id="d3f42-132">`Get-History` displays the updated command history and confirms that the five newest commands were deleted, **Id 6** - **Id 10**.</span></span>

### <span data-ttu-id="d3f42-133">Exempel 3: ta bort kommandon som matchar vissa villkor</span><span class="sxs-lookup"><span data-stu-id="d3f42-133">Example 3: Delete commands that match specific criteria</span></span>

<span data-ttu-id="d3f42-134">Det här kommandot tar bort kommandon som matchar de kriterier som har definierats av **kommando rads** parametern.</span><span class="sxs-lookup"><span data-stu-id="d3f42-134">This command deletes commands that match specific criteria defined by the **CommandLine** parameter.</span></span>

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

<span data-ttu-id="d3f42-135">`Get-History`Cmdleten visar PowerShell-sessionens historik.</span><span class="sxs-lookup"><span data-stu-id="d3f42-135">The `Get-History` cmdlet displays the PowerShell session's history.</span></span> <span data-ttu-id="d3f42-136">`Clear-History` tar bort kommando historiken.</span><span class="sxs-lookup"><span data-stu-id="d3f42-136">`Clear-History` deletes the command history.</span></span> <span data-ttu-id="d3f42-137">Parametern **CommandLine** anger kommandon som innehåller **Hjälp** eller slutar med **syntax**.</span><span class="sxs-lookup"><span data-stu-id="d3f42-137">The **CommandLine** parameter specifies commands that contain **Help** or end with **Syntax**.</span></span> <span data-ttu-id="d3f42-138">`Get-History` visar den uppdaterade kommando historiken och bekräftar att kommando **-ID 3** , **ID 5** , **ID 6** och **ID 7** har tagits bort.</span><span class="sxs-lookup"><span data-stu-id="d3f42-138">`Get-History` displays the updated command history and confirms that commands **Id 3** , **Id 5** , **Id 6** , and **Id 7** were deleted.</span></span>

### <span data-ttu-id="d3f42-139">Exempel 4: ta bort kommandon efter ID-nummer</span><span class="sxs-lookup"><span data-stu-id="d3f42-139">Example 4: Delete commands by Id number</span></span>

<span data-ttu-id="d3f42-140">Detta kommando tar bort vissa historik objekt med hjälp av **ID**. Om du vill ta bort flera kommandon skickar du en kommaavgränsad lista med **ID-** nummer.</span><span class="sxs-lookup"><span data-stu-id="d3f42-140">This command deletes specific history items using the **Id**. To delete multiple commands, submit a comma-separated list of **Id** numbers.</span></span>

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

<span data-ttu-id="d3f42-141">`Get-History`Cmdleten visar PowerShell-sessionens historik.</span><span class="sxs-lookup"><span data-stu-id="d3f42-141">The `Get-History` cmdlet displays the PowerShell session's history.</span></span> <span data-ttu-id="d3f42-142">`Clear-History` tar bort kommando historiken.</span><span class="sxs-lookup"><span data-stu-id="d3f42-142">`Clear-History` deletes the command history.</span></span> <span data-ttu-id="d3f42-143">Parametern **ID** anger vilka kommandon som ska tas bort.</span><span class="sxs-lookup"><span data-stu-id="d3f42-143">The **Id** parameter specifies which commands to delete.</span></span> <span data-ttu-id="d3f42-144">`Get-History` visar den uppdaterade kommando historiken och bekräftar att **ID 3** och **ID 5** har tagits bort.</span><span class="sxs-lookup"><span data-stu-id="d3f42-144">`Get-History` displays the updated command history and confirms that **Id 3** and **Id 5** were deleted.</span></span>

### <span data-ttu-id="d3f42-145">Exempel 5: ta bort kommandon efter ID-nummer och antal</span><span class="sxs-lookup"><span data-stu-id="d3f42-145">Example 5: Delete commands by Id number and count</span></span>

<span data-ttu-id="d3f42-146">Det här kommandot använder parametrarna **ID** och **Count** för att ta bort kommando historiken.</span><span class="sxs-lookup"><span data-stu-id="d3f42-146">This command uses the **Id** and **Count** parameters to delete command history.</span></span> <span data-ttu-id="d3f42-147">Kommandon tas bort från det angivna **ID: t** i omvänd ordning, nyaste till äldsta.</span><span class="sxs-lookup"><span data-stu-id="d3f42-147">Commands are deleted from the specified **Id** in reverse order, newest to oldest.</span></span>

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

<span data-ttu-id="d3f42-148">`Get-History`Cmdleten visar PowerShell-sessionens historik.</span><span class="sxs-lookup"><span data-stu-id="d3f42-148">The `Get-History` cmdlet displays the PowerShell session's history.</span></span> <span data-ttu-id="d3f42-149">`Clear-History` tar bort kommando historiken.</span><span class="sxs-lookup"><span data-stu-id="d3f42-149">`Clear-History` deletes the command history.</span></span> <span data-ttu-id="d3f42-150">**ID-** parametern anger att börjar med **ID 7**.</span><span class="sxs-lookup"><span data-stu-id="d3f42-150">The **Id** parameter specifies to begin with **Id 7**.</span></span> <span data-ttu-id="d3f42-151">Parametern **Count** anger att fem kommandon ska tas bort, inklusive det angivna **ID: t**. `Get-History`visar den uppdaterade kommando historiken och bekräftar att fem kommandon har tagits bort, **ID 3**  -  **ID 7**.</span><span class="sxs-lookup"><span data-stu-id="d3f42-151">The **Count** parameter specifies to delete five commands, inclusive of the specified **Id**. `Get-History` displays the updated command history and confirms that five commands were deleted, **Id 3** - **Id 7**.</span></span>

## <span data-ttu-id="d3f42-152">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="d3f42-152">PARAMETERS</span></span>

### <span data-ttu-id="d3f42-153">-Kommandorad</span><span class="sxs-lookup"><span data-stu-id="d3f42-153">-CommandLine</span></span>

<span data-ttu-id="d3f42-154">Tar bort kommando historik från en PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="d3f42-154">Deletes command history from a PowerShell session.</span></span> <span data-ttu-id="d3f42-155">Strängen måste vara en exakt matchning eller använda jokertecken för att matcha kommandon i PowerShell-sessionens historik som visas av `Get-History` .</span><span class="sxs-lookup"><span data-stu-id="d3f42-155">The string must be an exact match or use wildcards to match commands in the PowerShell session history displayed by `Get-History`.</span></span> <span data-ttu-id="d3f42-156">Om du anger mer än en sträng `Clear-History` tar bort kommandon som matchar någon av strängarna.</span><span class="sxs-lookup"><span data-stu-id="d3f42-156">If you enter more than one string, `Clear-History` deletes commands that match any of the strings.</span></span> <span data-ttu-id="d3f42-157">**Kommando rads** parametern kan användas med **Count**.</span><span class="sxs-lookup"><span data-stu-id="d3f42-157">The **CommandLine** parameter can be used with **Count**.</span></span>

<span data-ttu-id="d3f42-158">Använd enkla offerter för strängar med ett blank steg.</span><span class="sxs-lookup"><span data-stu-id="d3f42-158">For strings with a space, use single quotations.</span></span> <span data-ttu-id="d3f42-159">Mer information finns i [about_Quoting_Rules](About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="d3f42-159">For more information, see [about_Quoting_Rules](About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="d3f42-160">-Antal</span><span class="sxs-lookup"><span data-stu-id="d3f42-160">-Count</span></span>

<span data-ttu-id="d3f42-161">Anger antalet historik poster som `Clear-History` tas bort.</span><span class="sxs-lookup"><span data-stu-id="d3f42-161">Specifies the number of history entries that `Clear-History` deletes.</span></span> <span data-ttu-id="d3f42-162">Kommandona tas bort i ordning, från och med den äldsta posten i historiken.</span><span class="sxs-lookup"><span data-stu-id="d3f42-162">Commands are deleted in order, beginning with the oldest entry in the history.</span></span>

<span data-ttu-id="d3f42-163">Parametrarna **Count** och **ID** kan användas tillsammans.</span><span class="sxs-lookup"><span data-stu-id="d3f42-163">The **Count** and **Id** parameters can be used together.</span></span> <span data-ttu-id="d3f42-164">Parametern **Count** anger antalet kommandon som ska tas bort, inklusive det angivna ID: **t**. Från och med det angivna **ID: t** raderas kommandon i omvänd ordning.</span><span class="sxs-lookup"><span data-stu-id="d3f42-164">The **Count** parameter specifies the number of commands to delete, inclusive of the specified **Id**. Beginning at the specified **Id** , commands are deleted in reverse sequential order.</span></span> <span data-ttu-id="d3f42-165">Om **ID:** t till exempel är 30 och **antalet** är 10, `Clear-History` tar bort objekt 21 till 30.</span><span class="sxs-lookup"><span data-stu-id="d3f42-165">For example, if the **Id** is 30 and the **Count** is 10, `Clear-History` deletes items 21 through 30.</span></span>

<span data-ttu-id="d3f42-166">Parametrarna **Count** och **CommandLine** kan användas tillsammans.</span><span class="sxs-lookup"><span data-stu-id="d3f42-166">The **Count** and **CommandLine** parameters can be used together.</span></span> <span data-ttu-id="d3f42-167">**Count** anger antalet kommandon som ska tas bort och som matchar parameter värde för **kommando raden** .</span><span class="sxs-lookup"><span data-stu-id="d3f42-167">**Count** specifies the number of commands to delete that match **CommandLine** parameter value.</span></span> <span data-ttu-id="d3f42-168">Kommandona tas bort i sekventiell ordning.</span><span class="sxs-lookup"><span data-stu-id="d3f42-168">The commands are deleted in sequential order.</span></span>

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

### <span data-ttu-id="d3f42-169">-ID</span><span class="sxs-lookup"><span data-stu-id="d3f42-169">-Id</span></span>

<span data-ttu-id="d3f42-170">Anger det **ID** för kommando historik som `Clear-History` tar bort.</span><span class="sxs-lookup"><span data-stu-id="d3f42-170">Specifies the command history **Id** that `Clear-History` deletes.</span></span> <span data-ttu-id="d3f42-171">Använd cmdleten om du vill visa **ID-** nummer `Get-History` .</span><span class="sxs-lookup"><span data-stu-id="d3f42-171">To display **Id** numbers, use the `Get-History` cmdlet.</span></span> <span data-ttu-id="d3f42-172">**ID-** numren är sekventiella och kommandon behåller sina **ID-** nummer i en PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="d3f42-172">The **Id** numbers are sequential and commands keep their **Id** number throughout a PowerShell session.</span></span> <span data-ttu-id="d3f42-173">**ID-** parametern kan användas med **Count** och **nyast**.</span><span class="sxs-lookup"><span data-stu-id="d3f42-173">The **Id** parameter can be used with **Count** and **Newest**.</span></span>

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

### <span data-ttu-id="d3f42-174">– Nyaste</span><span class="sxs-lookup"><span data-stu-id="d3f42-174">-Newest</span></span>

<span data-ttu-id="d3f42-175">När den **senaste** parametern används `Clear-History` raderas de senaste posterna i historiken.</span><span class="sxs-lookup"><span data-stu-id="d3f42-175">When the **Newest** parameter is used, `Clear-History` deletes the newest entries in the history.</span></span> <span data-ttu-id="d3f42-176">Som standard `Clear-History` raderas de äldsta posterna i historiken.</span><span class="sxs-lookup"><span data-stu-id="d3f42-176">By default, `Clear-History` deletes the oldest entries in the history.</span></span>

<span data-ttu-id="d3f42-177">Den **senaste** parametern kan användas med **ID** och **Count**.</span><span class="sxs-lookup"><span data-stu-id="d3f42-177">The **Newest** parameter can be used with **Id** and **Count**.</span></span> <span data-ttu-id="d3f42-178">Parametern **Count** anger antalet kommandon som ska tas bort, inklusive det angivna ID: **t**. Från och med det angivna **ID: t** raderas kommandon i sekventiell ordning.</span><span class="sxs-lookup"><span data-stu-id="d3f42-178">The **Count** parameter specifies the number of commands to delete, inclusive of the specified **Id**. Beginning at the specified **Id** , commands are deleted in sequential order.</span></span> <span data-ttu-id="d3f42-179">Om **ID:** t till exempel är 30 och **antalet** är 10, `Clear-History` tar bort objekt 30 till 39.</span><span class="sxs-lookup"><span data-stu-id="d3f42-179">For example, if the **Id** is 30 and the **Count** is 10, `Clear-History` deletes items 30 through 39.</span></span>

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

### <span data-ttu-id="d3f42-180">-Confirm</span><span class="sxs-lookup"><span data-stu-id="d3f42-180">-Confirm</span></span>

<span data-ttu-id="d3f42-181">Du uppmanas att bekräfta innan du kör `Clear-History` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="d3f42-181">Prompts you for confirmation before running the `Clear-History` cmdlet.</span></span>

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

### <span data-ttu-id="d3f42-182">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="d3f42-182">-WhatIf</span></span>

<span data-ttu-id="d3f42-183">Visar vad som händer om `Clear-History` cmdleten körs.</span><span class="sxs-lookup"><span data-stu-id="d3f42-183">Shows what would happen if the `Clear-History` cmdlet runs.</span></span> <span data-ttu-id="d3f42-184">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="d3f42-184">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="d3f42-185">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d3f42-185">CommonParameters</span></span>

<span data-ttu-id="d3f42-186">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d3f42-186">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d3f42-187">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="d3f42-187">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="d3f42-188">INDATA</span><span class="sxs-lookup"><span data-stu-id="d3f42-188">INPUTS</span></span>

### <span data-ttu-id="d3f42-189">Inget</span><span class="sxs-lookup"><span data-stu-id="d3f42-189">None</span></span>

<span data-ttu-id="d3f42-190">Det går inte att skicka pipe-objekt till `Clear-History` .</span><span class="sxs-lookup"><span data-stu-id="d3f42-190">You cannot pipe objects to `Clear-History`.</span></span>

## <span data-ttu-id="d3f42-191">UTDATA</span><span class="sxs-lookup"><span data-stu-id="d3f42-191">OUTPUTS</span></span>

### <span data-ttu-id="d3f42-192">Inget</span><span class="sxs-lookup"><span data-stu-id="d3f42-192">None</span></span>

<span data-ttu-id="d3f42-193">`Clear-History` genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="d3f42-193">`Clear-History` does not generate any output.</span></span>

## <span data-ttu-id="d3f42-194">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="d3f42-194">NOTES</span></span>

<span data-ttu-id="d3f42-195">PowerShell-sessionens historik är en lista över kommandon som angavs under en PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="d3f42-195">The PowerShell session history is a list of the commands entered during a PowerShell session.</span></span> <span data-ttu-id="d3f42-196">Du kan visa historik, Lägg till och ta bort kommandon och köra kommandon från historiken.</span><span class="sxs-lookup"><span data-stu-id="d3f42-196">You can view the history, add and delete commands, and run commands from the history.</span></span> <span data-ttu-id="d3f42-197">Mer information finns i [about_History](About/about_History.md).</span><span class="sxs-lookup"><span data-stu-id="d3f42-197">For more information, see [about_History](About/about_History.md).</span></span>

<span data-ttu-id="d3f42-198">Historiken för sessionen hanteras separat från historiken som underhålls av **PSReadLine** -modulen.</span><span class="sxs-lookup"><span data-stu-id="d3f42-198">The session history is managed separately from the history maintained by the **PSReadLine** module.</span></span>
<span data-ttu-id="d3f42-199">Båda historiken är tillgängliga i sessioner där **PSReadLine** har lästs in.</span><span class="sxs-lookup"><span data-stu-id="d3f42-199">Both histories are available in sessions where **PSReadLine** is loaded.</span></span> <span data-ttu-id="d3f42-200">Den här cmdleten fungerar bara med tidigare session.</span><span class="sxs-lookup"><span data-stu-id="d3f42-200">This cmdlet only works with the session history.</span></span> <span data-ttu-id="d3f42-201">Mer information finns i [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md).</span><span class="sxs-lookup"><span data-stu-id="d3f42-201">For more information see, [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md).</span></span>

## <span data-ttu-id="d3f42-202">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="d3f42-202">RELATED LINKS</span></span>

[<span data-ttu-id="d3f42-203">about_History</span><span class="sxs-lookup"><span data-stu-id="d3f42-203">about_History</span></span>](About/about_History.md)

[<span data-ttu-id="d3f42-204">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="d3f42-204">about_PSReadLine</span></span>](../PSReadLine/About/about_PSReadLine.md)

[<span data-ttu-id="d3f42-205">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="d3f42-205">about_Quoting_Rules</span></span>](About/about_Quoting_Rules.md)

[<span data-ttu-id="d3f42-206">Lägg till-historik</span><span class="sxs-lookup"><span data-stu-id="d3f42-206">Add-History</span></span>](Add-History.md)

[<span data-ttu-id="d3f42-207">Hämta historik</span><span class="sxs-lookup"><span data-stu-id="d3f42-207">Get-History</span></span>](Get-History.md)

[<span data-ttu-id="d3f42-208">Anropa-historik</span><span class="sxs-lookup"><span data-stu-id="d3f42-208">Invoke-History</span></span>](Invoke-History.md)

[<span data-ttu-id="d3f42-209">Get-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="d3f42-209">Get-PSReadLineOption</span></span>](/powershell/module/psreadline/get-psreadlineoption)

[<span data-ttu-id="d3f42-210">Set-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="d3f42-210">Set-PSReadLineOption</span></span>](/powershell/module/psreadline/set-psreadlineoption)
