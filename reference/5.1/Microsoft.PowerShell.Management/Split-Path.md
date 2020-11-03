---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/split-path?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Split-Path
ms.openlocfilehash: 5d92acbe080b0d232047f1184c9a369b8837845c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265365"
---
# <span data-ttu-id="fb182-103">Split-Path</span><span class="sxs-lookup"><span data-stu-id="fb182-103">Split-Path</span></span>

## <span data-ttu-id="fb182-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="fb182-104">SYNOPSIS</span></span>
<span data-ttu-id="fb182-105">Returnerar den angivna delen av en sökväg.</span><span class="sxs-lookup"><span data-stu-id="fb182-105">Returns the specified part of a path.</span></span>

## <span data-ttu-id="fb182-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="fb182-106">SYNTAX</span></span>

### <span data-ttu-id="fb182-107">ParentSet (standard)</span><span class="sxs-lookup"><span data-stu-id="fb182-107">ParentSet (Default)</span></span>

```
Split-Path [-Path] <String[]> [-Parent] [-Resolve] [-Credential <PSCredential>] [-UseTransaction]
 [<CommonParameters>]
```

### <span data-ttu-id="fb182-108">NoQualifierSet</span><span class="sxs-lookup"><span data-stu-id="fb182-108">NoQualifierSet</span></span>

```
Split-Path [-Path] <String[]> [-NoQualifier] [-Resolve] [-Credential <PSCredential>] [-UseTransaction]
 [<CommonParameters>]
```

### <span data-ttu-id="fb182-109">LeafSet</span><span class="sxs-lookup"><span data-stu-id="fb182-109">LeafSet</span></span>

```
Split-Path [-Path] <String[]> [-Leaf] [-Resolve] [-Credential <PSCredential>] [-UseTransaction]
 [<CommonParameters>]
```

### <span data-ttu-id="fb182-110">QualifierSet</span><span class="sxs-lookup"><span data-stu-id="fb182-110">QualifierSet</span></span>

```
Split-Path [-Path] <String[]> [-Qualifier] [-Resolve] [-Credential <PSCredential>] [-UseTransaction]
 [<CommonParameters>]
```

### <span data-ttu-id="fb182-111">IsAbsoluteSet</span><span class="sxs-lookup"><span data-stu-id="fb182-111">IsAbsoluteSet</span></span>

```
Split-Path [-Path] <String[]> [-Resolve] [-IsAbsolute] [-Credential <PSCredential>] [-UseTransaction]
 [<CommonParameters>]
```

### <span data-ttu-id="fb182-112">LiteralPathSet</span><span class="sxs-lookup"><span data-stu-id="fb182-112">LiteralPathSet</span></span>

```
Split-Path -LiteralPath <String[]> [-Resolve] [-Credential <PSCredential>] [-UseTransaction]
 [<CommonParameters>]
```

## <span data-ttu-id="fb182-113">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="fb182-113">DESCRIPTION</span></span>

<span data-ttu-id="fb182-114">Cmdleten **Split-Path** returnerar bara den angivna delen av en sökväg, till exempel den överordnade mappen, en undermapp eller ett fil namn.</span><span class="sxs-lookup"><span data-stu-id="fb182-114">The **Split-Path** cmdlet returns only the specified part of a path, such as the parent folder, a subfolder, or a file name.</span></span>
<span data-ttu-id="fb182-115">Det kan också hämta objekt som refereras av den delade sökvägen och se om sökvägen är relativ eller absolut.</span><span class="sxs-lookup"><span data-stu-id="fb182-115">It can also get items that are referenced by the split path and tell whether the path is relative or absolute.</span></span>

<span data-ttu-id="fb182-116">Du kan använda den här cmdleten för att hämta eller skicka endast en markerad del av en sökväg.</span><span class="sxs-lookup"><span data-stu-id="fb182-116">You can use this cmdlet to get or submit only a selected part of a path.</span></span>

## <span data-ttu-id="fb182-117">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="fb182-117">EXAMPLES</span></span>

### <span data-ttu-id="fb182-118">Exempel 1: Hämta en sökvägs kvalificerare</span><span class="sxs-lookup"><span data-stu-id="fb182-118">Example 1: Get the qualifier of a path</span></span>

```
PS C:\> Split-Path -Path "HKCU:\Software\Microsoft" -Qualifier
HKCU:
```

<span data-ttu-id="fb182-119">Det här kommandot returnerar bara kvalificeraren för sökvägen.</span><span class="sxs-lookup"><span data-stu-id="fb182-119">This command returns only the qualifier of the path.</span></span>
<span data-ttu-id="fb182-120">Kvalificeraren är enheten.</span><span class="sxs-lookup"><span data-stu-id="fb182-120">The qualifier is the drive.</span></span>

### <span data-ttu-id="fb182-121">Exempel 2: Visa fil namn</span><span class="sxs-lookup"><span data-stu-id="fb182-121">Example 2: Display file names</span></span>

```
PS C:\> Split-Path -Path "C:\Test\Logs\*.log" -Leaf -Resolve
Pass1.log
Pass2.log
...
```

<span data-ttu-id="fb182-122">Det här kommandot visar de filer som refereras av den delade sökvägen.</span><span class="sxs-lookup"><span data-stu-id="fb182-122">This command displays the files that are referenced by the split path.</span></span>
<span data-ttu-id="fb182-123">Eftersom den här sökvägen är delad till det sista objektet, även kallat lövnod, visar kommandot bara fil namnen.</span><span class="sxs-lookup"><span data-stu-id="fb182-123">Because this path is split to the last item, also known as the leaf, the command displays only the file names.</span></span>

<span data-ttu-id="fb182-124">Parametern *resolve* anger **delad-sökväg** för att visa de objekt som den delade sökvägen refererar till, i stället för att Visa delnings Sök vägen.</span><span class="sxs-lookup"><span data-stu-id="fb182-124">The *Resolve* parameter tells **Split-Path** to display the items that the split path references, instead of displaying the split path.</span></span>

<span data-ttu-id="fb182-125">Precis som alla kommandon för **delad sökväg** returnerar det här kommandot strängar.</span><span class="sxs-lookup"><span data-stu-id="fb182-125">Like all **Split-Path** commands, this command returns strings.</span></span>
<span data-ttu-id="fb182-126">Den returnerar inte **fileinfo** -objekt som representerar filerna.</span><span class="sxs-lookup"><span data-stu-id="fb182-126">It does not return **FileInfo** objects that represent the files.</span></span>

### <span data-ttu-id="fb182-127">Exempel 3: hämta den överordnade behållaren</span><span class="sxs-lookup"><span data-stu-id="fb182-127">Example 3: Get the parent container</span></span>

```
PS C:\> Split-Path -Path "C:\WINDOWS\system32\WindowsPowerShell\V1.0\about_*.txt"
C:\WINDOWS\system32\WindowsPowerShell\V1.0
```

<span data-ttu-id="fb182-128">Det här kommandot returnerar bara de överordnade behållarna för sökvägen.</span><span class="sxs-lookup"><span data-stu-id="fb182-128">This command returns only the parent containers of the path.</span></span>
<span data-ttu-id="fb182-129">Eftersom den inte innehåller några parametrar för att ange delning, använder **delad sökväg** den delade platsens standard, som är *överordnad*.</span><span class="sxs-lookup"><span data-stu-id="fb182-129">Because it does not include any parameters to specify the split, **Split-Path** uses the split location default, which is *Parent*.</span></span>

### <span data-ttu-id="fb182-130">Exempel 4: avgör om en sökväg är absolut</span><span class="sxs-lookup"><span data-stu-id="fb182-130">Example 4: Determines whether a path is absolute</span></span>

```
PS C:\> Split-Path -Path ".\My Pictures\*.jpg" -IsAbsolute
False
```

<span data-ttu-id="fb182-131">Det här kommandot avgör om sökvägen är relativ eller absolut.</span><span class="sxs-lookup"><span data-stu-id="fb182-131">This command determines whether the path is relative or absolute.</span></span>
<span data-ttu-id="fb182-132">I det här fallet, eftersom sökvägen är relativ till den aktuella mappen, som representeras av en punkt (.), returneras $False.</span><span class="sxs-lookup"><span data-stu-id="fb182-132">In this case, because the path is relative to the current folder, which is represented by a dot (.), it returns $False.</span></span>

### <span data-ttu-id="fb182-133">Exempel 5: ändra plats till en angiven sökväg</span><span class="sxs-lookup"><span data-stu-id="fb182-133">Example 5: Change location to a specified path</span></span>

```
PS C:\> Set-Location (Split-Path -Path $profile)
PS C:\Documents and Settings\User01\My Documents\WindowsPowerShell>
```

<span data-ttu-id="fb182-134">Det här kommandot ändrar platsen till den mapp som innehåller PowerShell-profilen.</span><span class="sxs-lookup"><span data-stu-id="fb182-134">This command changes your location to the folder that contains the PowerShell profile.</span></span>

<span data-ttu-id="fb182-135">Kommandot inom parentes använder **delad sökväg** för att endast returnera den överordnade sökvägen till den lagrade sökvägen i den inbyggda $Profile variabeln.</span><span class="sxs-lookup"><span data-stu-id="fb182-135">The command in parentheses uses **Split-Path** to return only the parent of the path stored in the built-in $Profile variable.</span></span>
<span data-ttu-id="fb182-136">Den *överordnade* parametern är standard parametern för delad plats.</span><span class="sxs-lookup"><span data-stu-id="fb182-136">The *Parent* parameter is the default split location parameter.</span></span>
<span data-ttu-id="fb182-137">Därför kan du utelämna det från kommandot.</span><span class="sxs-lookup"><span data-stu-id="fb182-137">Therefore, you can omit it from the command.</span></span>
<span data-ttu-id="fb182-138">Parenteserna Direct PowerShell för att köra kommandot först.</span><span class="sxs-lookup"><span data-stu-id="fb182-138">The parentheses direct PowerShell to run the command first.</span></span>
<span data-ttu-id="fb182-139">Detta är ett bra sätt att flytta till en mapp som har ett långt Sök vägs namn.</span><span class="sxs-lookup"><span data-stu-id="fb182-139">This is a useful way to move to a folder that has a long path name.</span></span>

### <span data-ttu-id="fb182-140">Exempel 6: dela en bana med hjälp av pipelinen</span><span class="sxs-lookup"><span data-stu-id="fb182-140">Example 6: Split a path by using the pipeline</span></span>

```
PS C:\> 'C:\Documents and Settings\User01\My Documents\My Pictures' | Split-Path
C:\Documents and Settings\User01\My Documents
```

<span data-ttu-id="fb182-141">Det här kommandot använder en pipeline-operator (|) för att skicka en sökväg till en **delad sökväg**.</span><span class="sxs-lookup"><span data-stu-id="fb182-141">This command uses a pipeline operator (|) to send a path to **Split-Path**.</span></span>
<span data-ttu-id="fb182-142">Sökvägen omges av citat tecken för att ange att den är en enskild token.</span><span class="sxs-lookup"><span data-stu-id="fb182-142">The path is enclosed in quotation marks to indicate that it is a single token.</span></span>

## <span data-ttu-id="fb182-143">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="fb182-143">PARAMETERS</span></span>

### <span data-ttu-id="fb182-144">-Credential</span><span class="sxs-lookup"><span data-stu-id="fb182-144">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="fb182-145">Den här parametern stöds inte av några providrar som installeras med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fb182-145">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="fb182-146">Om du vill personifiera en annan användare eller öka dina autentiseringsuppgifter när du kör denna cmdlet, använder du [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="fb182-146">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="fb182-147">-IsAbsolute</span><span class="sxs-lookup"><span data-stu-id="fb182-147">-IsAbsolute</span></span>

<span data-ttu-id="fb182-148">Anger att denna cmdlet returnerar $True om sökvägen är absolut och $False om den är relativ.</span><span class="sxs-lookup"><span data-stu-id="fb182-148">Indicates that this cmdlet returns $True if the path is absolute and $False if it is relative.</span></span>
<span data-ttu-id="fb182-149">En absolut sökväg har en längd som är större än noll och använder inte en punkt (.) för att ange den aktuella sökvägen.</span><span class="sxs-lookup"><span data-stu-id="fb182-149">An absolute path has a length greater than zero and does not use a dot (.) to indicate the current path.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: IsAbsoluteSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fb182-150">-Löv</span><span class="sxs-lookup"><span data-stu-id="fb182-150">-Leaf</span></span>

<span data-ttu-id="fb182-151">Anger att denna cmdlet endast returnerar det sista objektet eller behållaren i sökvägen.</span><span class="sxs-lookup"><span data-stu-id="fb182-151">Indicates that this cmdlet returns only the last item or container in the path.</span></span>
<span data-ttu-id="fb182-152">I sökvägen returnerar till exempel `C:\Test\Logs\Pass1.log` bara Pass1. log.</span><span class="sxs-lookup"><span data-stu-id="fb182-152">For example, in the path `C:\Test\Logs\Pass1.log`, it returns only Pass1.log.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LeafSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="fb182-153">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="fb182-153">-LiteralPath</span></span>

<span data-ttu-id="fb182-154">Anger vilka sökvägar som ska delas.</span><span class="sxs-lookup"><span data-stu-id="fb182-154">Specifies the paths to be split.</span></span>
<span data-ttu-id="fb182-155">Till skillnad från *sökväg* används värdet för *LiteralPath* exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="fb182-155">Unlike *Path* , the value of *LiteralPath* is used exactly as it is typed.</span></span>
<span data-ttu-id="fb182-156">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="fb182-156">No characters are interpreted as wildcard characters.</span></span>
<span data-ttu-id="fb182-157">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="fb182-157">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="fb182-158">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="fb182-158">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPathSet
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="fb182-159">-Nokvalificerare</span><span class="sxs-lookup"><span data-stu-id="fb182-159">-NoQualifier</span></span>

<span data-ttu-id="fb182-160">Anger att denna cmdlet returnerar sökvägen utan kvalificeraren.</span><span class="sxs-lookup"><span data-stu-id="fb182-160">Indicates that this cmdlet returns the path without the qualifier.</span></span>
<span data-ttu-id="fb182-161">För fil systemet eller register leverantörer är kvalificeraren enhet för providerns sökväg, till exempel C: eller HKCU:.</span><span class="sxs-lookup"><span data-stu-id="fb182-161">For the FileSystem or registry providers, the qualifier is the drive of the provider path, such as C: or HKCU:.</span></span>
<span data-ttu-id="fb182-162">I sökvägen returnerar till exempel `C:\Test\Logs\Pass1.log` bara \Test\Logs\Pass1.log.</span><span class="sxs-lookup"><span data-stu-id="fb182-162">For example, in the path `C:\Test\Logs\Pass1.log`, it returns only \Test\Logs\Pass1.log.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NoQualifierSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="fb182-163">– Överordnad</span><span class="sxs-lookup"><span data-stu-id="fb182-163">-Parent</span></span>

<span data-ttu-id="fb182-164">Anger att denna cmdlet endast returnerar överordnade behållare för objektet eller den behållare som anges av sökvägen.</span><span class="sxs-lookup"><span data-stu-id="fb182-164">Indicates that this cmdlet returns only the parent containers of the item or of the container specified by the path.</span></span>
<span data-ttu-id="fb182-165">I sökvägen returnerar till exempel `C:\Test\Logs\Pass1.log` C:\Test\Logs.</span><span class="sxs-lookup"><span data-stu-id="fb182-165">For example, in the path `C:\Test\Logs\Pass1.log`, it returns C:\Test\Logs.</span></span>
<span data-ttu-id="fb182-166">Den *överordnade* parametern är standard parametern för delad plats.</span><span class="sxs-lookup"><span data-stu-id="fb182-166">The *Parent* parameter is the default split location parameter.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ParentSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="fb182-167">-Path</span><span class="sxs-lookup"><span data-stu-id="fb182-167">-Path</span></span>

<span data-ttu-id="fb182-168">Anger vilka sökvägar som ska delas.</span><span class="sxs-lookup"><span data-stu-id="fb182-168">Specifies the paths to be split.</span></span>
<span data-ttu-id="fb182-169">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="fb182-169">Wildcard characters are permitted.</span></span>
<span data-ttu-id="fb182-170">Om sökvägen innehåller blank steg, omger du den med citat tecken.</span><span class="sxs-lookup"><span data-stu-id="fb182-170">If the path includes spaces, enclose it in quotation marks.</span></span>
<span data-ttu-id="fb182-171">Du kan också skicka en sökväg till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fb182-171">You can also pipe a path to this cmdlet.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ParentSet, NoQualifierSet, LeafSet, QualifierSet, IsAbsoluteSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="fb182-172">-Kvalificerare</span><span class="sxs-lookup"><span data-stu-id="fb182-172">-Qualifier</span></span>

<span data-ttu-id="fb182-173">Anger att denna cmdlet bara returnerar kvalificeraren för den angivna sökvägen.</span><span class="sxs-lookup"><span data-stu-id="fb182-173">Indicates that this cmdlet returns only the qualifier of the specified path.</span></span>
<span data-ttu-id="fb182-174">För fil systemet eller register leverantörer är kvalificeraren enhet för providerns sökväg, till exempel C: eller HKCU:.</span><span class="sxs-lookup"><span data-stu-id="fb182-174">For the FileSystem or registry providers, the qualifier is the drive of the provider path, such as C: or HKCU:.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: QualifierSet
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="fb182-175">-Lös</span><span class="sxs-lookup"><span data-stu-id="fb182-175">-Resolve</span></span>

<span data-ttu-id="fb182-176">Anger att den här cmdleten visar objekt som refereras till av den resulterande delade sökvägen i stället för att Visa Sök vägs elementen.</span><span class="sxs-lookup"><span data-stu-id="fb182-176">Indicates that this cmdlet displays the items that are referenced by the resulting split path instead of displaying the path elements.</span></span>

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

### <span data-ttu-id="fb182-177">– UseTransaction</span><span class="sxs-lookup"><span data-stu-id="fb182-177">-UseTransaction</span></span>

<span data-ttu-id="fb182-178">Inkluderar kommandot i den aktiva transaktionen.</span><span class="sxs-lookup"><span data-stu-id="fb182-178">Includes the command in the active transaction.</span></span>
<span data-ttu-id="fb182-179">Den här parametern är bara giltig medan en transaktion pågår.</span><span class="sxs-lookup"><span data-stu-id="fb182-179">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="fb182-180">Mer information finns i about_Transactions.</span><span class="sxs-lookup"><span data-stu-id="fb182-180">For more information, see about_Transactions.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: usetx

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="fb182-181">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="fb182-181">CommonParameters</span></span>

<span data-ttu-id="fb182-182">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="fb182-182">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="fb182-183">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="fb182-183">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="fb182-184">INDATA</span><span class="sxs-lookup"><span data-stu-id="fb182-184">INPUTS</span></span>

### <span data-ttu-id="fb182-185">System. String</span><span class="sxs-lookup"><span data-stu-id="fb182-185">System.String</span></span>

<span data-ttu-id="fb182-186">Du kan skicka vidare en sträng som innehåller en sökväg till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fb182-186">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="fb182-187">UTDATA</span><span class="sxs-lookup"><span data-stu-id="fb182-187">OUTPUTS</span></span>

### <span data-ttu-id="fb182-188">System. String, system. Boolean</span><span class="sxs-lookup"><span data-stu-id="fb182-188">System.String, System.Boolean</span></span>

<span data-ttu-id="fb182-189">**Split-Path** returnerar text strängar.</span><span class="sxs-lookup"><span data-stu-id="fb182-189">**Split-Path** returns text strings.</span></span>
<span data-ttu-id="fb182-190">När du anger parametern *matcha* , returnerar **delad sökväg** en sträng som beskriver objektets placering. det returnerar inte objekt som representerar objekten, till exempel ett **fileinfo** -eller **RegistryKey** -objekt.</span><span class="sxs-lookup"><span data-stu-id="fb182-190">When you specify the *Resolve* parameter, **Split-Path** returns a string that describes the location of the items; it does not return objects that represent the items, such as a **FileInfo** or **RegistryKey** object.</span></span>

<span data-ttu-id="fb182-191">När du anger parametern *IsAbsolute* , returnerar **delad sökväg** ett **booleskt** värde.</span><span class="sxs-lookup"><span data-stu-id="fb182-191">When you specify the *IsAbsolute* parameter, **Split-Path** returns a **Boolean** value.</span></span>

## <span data-ttu-id="fb182-192">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="fb182-192">NOTES</span></span>

* <span data-ttu-id="fb182-193">Parametrarna för delad plats ( *kvalificerare* , *överordnad* , *löv* och *nokvalificerare* ) är exklusiva.</span><span class="sxs-lookup"><span data-stu-id="fb182-193">The split location parameters ( *Qualifier* , *Parent* , *Leaf* , and *NoQualifier* ) are exclusive.</span></span> <span data-ttu-id="fb182-194">Du kan bara använda ett i varje kommando.</span><span class="sxs-lookup"><span data-stu-id="fb182-194">You can use only one in each command.</span></span>

  <span data-ttu-id="fb182-195">Cmdlet: arna som innehåller **sökvägen** Substantiv ( **Sök vägs** -cmdletarna) fungerar med Sök vägs namn och returnerar namnen i ett koncist format som alla PowerShell-leverantörer kan tolka.</span><span class="sxs-lookup"><span data-stu-id="fb182-195">The cmdlets that contain the **Path** noun (the **Path** cmdlets) work with path names and return the names in a concise format that all PowerShell providers can interpret.</span></span>
<span data-ttu-id="fb182-196">De är utformade för användning i program och skript där du vill visa hela eller delar av ett Sök vägs namn i ett visst format.</span><span class="sxs-lookup"><span data-stu-id="fb182-196">They are designed for use in programs and scripts where you want to display all or part of a path name in a particular format.</span></span>
<span data-ttu-id="fb182-197">Använd dem på det sätt som du använder **logsdirectory** , **Normpath** , **realpath** , **Join** eller andra Sök vägs manipulerare.</span><span class="sxs-lookup"><span data-stu-id="fb182-197">Use them in the way that you would use **Dirname** , **Normpath** , **Realpath** , **Join** , or other path manipulators.</span></span>

  <span data-ttu-id="fb182-198">Du kan använda **Sök vägs** -cmdletarna tillsammans med flera providers.</span><span class="sxs-lookup"><span data-stu-id="fb182-198">You can use the **Path** cmdlets together with several providers.</span></span>
<span data-ttu-id="fb182-199">Dessa omfattar fil systemet system, register och certifikat.</span><span class="sxs-lookup"><span data-stu-id="fb182-199">These include the FileSystem, Registry, and Certificate providers.</span></span>

  <span data-ttu-id="fb182-200">**Split-Path** är utformad för att fungera med data som exponeras av vilken provider som helst.</span><span class="sxs-lookup"><span data-stu-id="fb182-200">**Split-Path** is designed to work with the data exposed by any provider.</span></span>
<span data-ttu-id="fb182-201">Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="fb182-201">To list the providers available in your session, type `Get-PSProvider`.</span></span>
<span data-ttu-id="fb182-202">Mer information finns i about_Providers.</span><span class="sxs-lookup"><span data-stu-id="fb182-202">For more information, see about_Providers.</span></span>

## <span data-ttu-id="fb182-203">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="fb182-203">RELATED LINKS</span></span>

[<span data-ttu-id="fb182-204">Konvertera-sökväg</span><span class="sxs-lookup"><span data-stu-id="fb182-204">Convert-Path</span></span>](Convert-Path.md)

[<span data-ttu-id="fb182-205">Anslut till sökväg</span><span class="sxs-lookup"><span data-stu-id="fb182-205">Join-Path</span></span>](Join-Path.md)

[<span data-ttu-id="fb182-206">Lös-sökväg</span><span class="sxs-lookup"><span data-stu-id="fb182-206">Resolve-Path</span></span>](Resolve-Path.md)

[<span data-ttu-id="fb182-207">Test-sökväg</span><span class="sxs-lookup"><span data-stu-id="fb182-207">Test-Path</span></span>](Test-Path.md)
