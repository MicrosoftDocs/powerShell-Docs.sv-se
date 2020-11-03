---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/split-path?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Split-Path
ms.openlocfilehash: b0366e9d84826d84dcdc341a9e83e4ed7dc45059
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93262574"
---
# <span data-ttu-id="9c3c6-103">Split-Path</span><span class="sxs-lookup"><span data-stu-id="9c3c6-103">Split-Path</span></span>

## <span data-ttu-id="9c3c6-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="9c3c6-104">SYNOPSIS</span></span>
<span data-ttu-id="9c3c6-105">Returnerar den angivna delen av en sökväg.</span><span class="sxs-lookup"><span data-stu-id="9c3c6-105">Returns the specified part of a path.</span></span>

## <span data-ttu-id="9c3c6-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9c3c6-106">SYNTAX</span></span>

### <span data-ttu-id="9c3c6-107">ParentSet (standard)</span><span class="sxs-lookup"><span data-stu-id="9c3c6-107">ParentSet (Default)</span></span>

```
Split-Path [-Path] <String[]> [-Parent] [-Resolve] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### <span data-ttu-id="9c3c6-108">LeafSet</span><span class="sxs-lookup"><span data-stu-id="9c3c6-108">LeafSet</span></span>

```
Split-Path [-Path] <String[]> [-Leaf] [-Resolve] [-Credential <PSCredential>] [<CommonParameters>]
```

### <span data-ttu-id="9c3c6-109">LeafBaseSet</span><span class="sxs-lookup"><span data-stu-id="9c3c6-109">LeafBaseSet</span></span>

```
Split-Path [-Path] <String[]> [-LeafBase] [-Resolve] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### <span data-ttu-id="9c3c6-110">ExtensionSet</span><span class="sxs-lookup"><span data-stu-id="9c3c6-110">ExtensionSet</span></span>

```
Split-Path [-Path] <String[]> [-Extension] [-Resolve] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### <span data-ttu-id="9c3c6-111">QualifierSet</span><span class="sxs-lookup"><span data-stu-id="9c3c6-111">QualifierSet</span></span>

```
Split-Path [-Path] <String[]> [[-Qualifier]] [-Resolve] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### <span data-ttu-id="9c3c6-112">NoQualifierSet</span><span class="sxs-lookup"><span data-stu-id="9c3c6-112">NoQualifierSet</span></span>

```
Split-Path [-Path] <String[]> [-NoQualifier] [-Resolve] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### <span data-ttu-id="9c3c6-113">IsAbsoluteSet</span><span class="sxs-lookup"><span data-stu-id="9c3c6-113">IsAbsoluteSet</span></span>

```
Split-Path [-Path] <String[]> [-Resolve] [-IsAbsolute] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### <span data-ttu-id="9c3c6-114">LiteralPathSet</span><span class="sxs-lookup"><span data-stu-id="9c3c6-114">LiteralPathSet</span></span>

```
Split-Path -LiteralPath <String[]> [-Resolve] [-Credential <PSCredential>] [<CommonParameters>]
```

## <span data-ttu-id="9c3c6-115">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="9c3c6-115">DESCRIPTION</span></span>

<span data-ttu-id="9c3c6-116">Cmdleten **Split-Path** returnerar bara den angivna delen av en sökväg, till exempel den överordnade mappen, en undermapp eller ett fil namn.</span><span class="sxs-lookup"><span data-stu-id="9c3c6-116">The **Split-Path** cmdlet returns only the specified part of a path, such as the parent folder, a subfolder, or a file name.</span></span>
<span data-ttu-id="9c3c6-117">Det kan också hämta objekt som refereras av den delade sökvägen och se om sökvägen är relativ eller absolut.</span><span class="sxs-lookup"><span data-stu-id="9c3c6-117">It can also get items that are referenced by the split path and tell whether the path is relative or absolute.</span></span>

<span data-ttu-id="9c3c6-118">Du kan använda den här cmdleten för att hämta eller skicka endast en markerad del av en sökväg.</span><span class="sxs-lookup"><span data-stu-id="9c3c6-118">You can use this cmdlet to get or submit only a selected part of a path.</span></span>

## <span data-ttu-id="9c3c6-119">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="9c3c6-119">EXAMPLES</span></span>

### <span data-ttu-id="9c3c6-120">Exempel 1: Hämta en sökvägs kvalificerare</span><span class="sxs-lookup"><span data-stu-id="9c3c6-120">Example 1: Get the qualifier of a path</span></span>

```
PS C:\> Split-Path -Path "HKCU:\Software\Microsoft" -Qualifier
HKCU:
```

<span data-ttu-id="9c3c6-121">Det här kommandot returnerar bara kvalificeraren för sökvägen.</span><span class="sxs-lookup"><span data-stu-id="9c3c6-121">This command returns only the qualifier of the path.</span></span>
<span data-ttu-id="9c3c6-122">Kvalificeraren är enheten.</span><span class="sxs-lookup"><span data-stu-id="9c3c6-122">The qualifier is the drive.</span></span>

### <span data-ttu-id="9c3c6-123">Exempel 2: Visa fil namn</span><span class="sxs-lookup"><span data-stu-id="9c3c6-123">Example 2: Display file names</span></span>

```
PS C:\> Split-Path -Path "C:\Test\Logs\*.log" -Leaf -Resolve
Pass1.log
Pass2.log
...
```

<span data-ttu-id="9c3c6-124">Det här kommandot visar de filer som refereras av den delade sökvägen.</span><span class="sxs-lookup"><span data-stu-id="9c3c6-124">This command displays the files that are referenced by the split path.</span></span>
<span data-ttu-id="9c3c6-125">Eftersom den här sökvägen är delad till det sista objektet, även kallat lövnod, visar kommandot bara fil namnen.</span><span class="sxs-lookup"><span data-stu-id="9c3c6-125">Because this path is split to the last item, also known as the leaf, the command displays only the file names.</span></span>

<span data-ttu-id="9c3c6-126">Parametern *resolve* anger **delad-sökväg** för att visa de objekt som den delade sökvägen refererar till, i stället för att Visa delnings Sök vägen.</span><span class="sxs-lookup"><span data-stu-id="9c3c6-126">The *Resolve* parameter tells **Split-Path** to display the items that the split path references, instead of displaying the split path.</span></span>

<span data-ttu-id="9c3c6-127">Precis som alla kommandon för **delad sökväg** returnerar det här kommandot strängar.</span><span class="sxs-lookup"><span data-stu-id="9c3c6-127">Like all **Split-Path** commands, this command returns strings.</span></span>
<span data-ttu-id="9c3c6-128">Den returnerar inte **fileinfo** -objekt som representerar filerna.</span><span class="sxs-lookup"><span data-stu-id="9c3c6-128">It does not return **FileInfo** objects that represent the files.</span></span>

### <span data-ttu-id="9c3c6-129">Exempel 3: hämta den överordnade behållaren</span><span class="sxs-lookup"><span data-stu-id="9c3c6-129">Example 3: Get the parent container</span></span>

```
PS C:\> Split-Path -Path "C:\WINDOWS\system32\WindowsPowerShell\V1.0\about_*.txt"
C:\WINDOWS\system32\WindowsPowerShell\V1.0
```

<span data-ttu-id="9c3c6-130">Det här kommandot returnerar bara de överordnade behållarna för sökvägen.</span><span class="sxs-lookup"><span data-stu-id="9c3c6-130">This command returns only the parent containers of the path.</span></span>
<span data-ttu-id="9c3c6-131">Eftersom den inte innehåller några parametrar för att ange delning, använder **delad sökväg** den delade platsens standard, som är *överordnad*.</span><span class="sxs-lookup"><span data-stu-id="9c3c6-131">Because it does not include any parameters to specify the split, **Split-Path** uses the split location default, which is *Parent*.</span></span>

### <span data-ttu-id="9c3c6-132">Exempel 4: avgör om en sökväg är absolut</span><span class="sxs-lookup"><span data-stu-id="9c3c6-132">Example 4: Determines whether a path is absolute</span></span>

```
PS C:\> Split-Path -Path ".\My Pictures\*.jpg" -IsAbsolute
False
```

<span data-ttu-id="9c3c6-133">Det här kommandot avgör om sökvägen är relativ eller absolut.</span><span class="sxs-lookup"><span data-stu-id="9c3c6-133">This command determines whether the path is relative or absolute.</span></span>
<span data-ttu-id="9c3c6-134">I det här fallet, eftersom sökvägen är relativ till den aktuella mappen, som representeras av en punkt (.), returneras $False.</span><span class="sxs-lookup"><span data-stu-id="9c3c6-134">In this case, because the path is relative to the current folder, which is represented by a dot (.), it returns $False.</span></span>

### <span data-ttu-id="9c3c6-135">Exempel 5: ändra plats till en angiven sökväg</span><span class="sxs-lookup"><span data-stu-id="9c3c6-135">Example 5: Change location to a specified path</span></span>

```
PS C:\> Set-Location (Split-Path -Path $profile)
PS C:\Documents and Settings\User01\My Documents\WindowsPowerShell>
```

<span data-ttu-id="9c3c6-136">Det här kommandot ändrar platsen till den mapp som innehåller PowerShell-profilen.</span><span class="sxs-lookup"><span data-stu-id="9c3c6-136">This command changes your location to the folder that contains the PowerShell profile.</span></span>

<span data-ttu-id="9c3c6-137">Kommandot inom parentes använder **delad sökväg** för att endast returnera den överordnade sökvägen till den lagrade sökvägen i den inbyggda $Profile variabeln.</span><span class="sxs-lookup"><span data-stu-id="9c3c6-137">The command in parentheses uses **Split-Path** to return only the parent of the path stored in the built-in $Profile variable.</span></span>
<span data-ttu-id="9c3c6-138">Den *överordnade* parametern är standard parametern för delad plats.</span><span class="sxs-lookup"><span data-stu-id="9c3c6-138">The *Parent* parameter is the default split location parameter.</span></span>
<span data-ttu-id="9c3c6-139">Därför kan du utelämna det från kommandot.</span><span class="sxs-lookup"><span data-stu-id="9c3c6-139">Therefore, you can omit it from the command.</span></span>
<span data-ttu-id="9c3c6-140">Parenteserna Direct PowerShell för att köra kommandot först.</span><span class="sxs-lookup"><span data-stu-id="9c3c6-140">The parentheses direct PowerShell to run the command first.</span></span>
<span data-ttu-id="9c3c6-141">Detta är ett bra sätt att flytta till en mapp som har ett långt Sök vägs namn.</span><span class="sxs-lookup"><span data-stu-id="9c3c6-141">This is a useful way to move to a folder that has a long path name.</span></span>

### <span data-ttu-id="9c3c6-142">Exempel 6: dela en bana med hjälp av pipelinen</span><span class="sxs-lookup"><span data-stu-id="9c3c6-142">Example 6: Split a path by using the pipeline</span></span>

```
PS C:\> 'C:\Documents and Settings\User01\My Documents\My Pictures' | Split-Path
C:\Documents and Settings\User01\My Documents
```

<span data-ttu-id="9c3c6-143">Det här kommandot använder en pipeline-operator (|) för att skicka en sökväg till en **delad sökväg**.</span><span class="sxs-lookup"><span data-stu-id="9c3c6-143">This command uses a pipeline operator (|) to send a path to **Split-Path**.</span></span>
<span data-ttu-id="9c3c6-144">Sökvägen omges av citat tecken för att ange att den är en enskild token.</span><span class="sxs-lookup"><span data-stu-id="9c3c6-144">The path is enclosed in quotation marks to indicate that it is a single token.</span></span>

## <span data-ttu-id="9c3c6-145">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="9c3c6-145">PARAMETERS</span></span>

### <span data-ttu-id="9c3c6-146">-Credential</span><span class="sxs-lookup"><span data-stu-id="9c3c6-146">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="9c3c6-147">Den här parametern stöds inte av några providrar som installeras med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9c3c6-147">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="9c3c6-148">Om du vill personifiera en annan användare eller öka dina autentiseringsuppgifter när du kör denna cmdlet, använder du [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="9c3c6-148">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="9c3c6-149">-Tillägg</span><span class="sxs-lookup"><span data-stu-id="9c3c6-149">-Extension</span></span>

<span data-ttu-id="9c3c6-150">Anger att denna cmdlet bara returnerar tillägg för bladet.</span><span class="sxs-lookup"><span data-stu-id="9c3c6-150">Indicates that this cmdlet returns only the extension of the leaf.</span></span>
<span data-ttu-id="9c3c6-151">I sökvägen returneras till exempel `C:\Test\Logs\Pass1.log` bara `.log` .</span><span class="sxs-lookup"><span data-stu-id="9c3c6-151">For example, in the path `C:\Test\Logs\Pass1.log`, it returns only `.log`.</span></span>

<span data-ttu-id="9c3c6-152">Den här parametern introducerades i PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="9c3c6-152">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ExtensionSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9c3c6-153">-IsAbsolute</span><span class="sxs-lookup"><span data-stu-id="9c3c6-153">-IsAbsolute</span></span>

<span data-ttu-id="9c3c6-154">Anger att denna cmdlet returnerar $True om sökvägen är absolut och $False om den är relativ.</span><span class="sxs-lookup"><span data-stu-id="9c3c6-154">Indicates that this cmdlet returns $True if the path is absolute and $False if it is relative.</span></span>
<span data-ttu-id="9c3c6-155">En absolut sökväg har en längd som är större än noll och använder inte en punkt (.) för att ange den aktuella sökvägen.</span><span class="sxs-lookup"><span data-stu-id="9c3c6-155">An absolute path has a length greater than zero and does not use a dot (.) to indicate the current path.</span></span>

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

### <span data-ttu-id="9c3c6-156">-Löv</span><span class="sxs-lookup"><span data-stu-id="9c3c6-156">-Leaf</span></span>

<span data-ttu-id="9c3c6-157">Anger att denna cmdlet endast returnerar det sista objektet eller behållaren i sökvägen.</span><span class="sxs-lookup"><span data-stu-id="9c3c6-157">Indicates that this cmdlet returns only the last item or container in the path.</span></span>
<span data-ttu-id="9c3c6-158">I sökvägen returnerar till exempel `C:\Test\Logs\Pass1.log` bara Pass1. log.</span><span class="sxs-lookup"><span data-stu-id="9c3c6-158">For example, in the path `C:\Test\Logs\Pass1.log`, it returns only Pass1.log.</span></span>

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

### <span data-ttu-id="9c3c6-159">-LeafBase</span><span class="sxs-lookup"><span data-stu-id="9c3c6-159">-LeafBase</span></span>

<span data-ttu-id="9c3c6-160">Anger att denna cmdlet returnerar endast bas namnet för löv.</span><span class="sxs-lookup"><span data-stu-id="9c3c6-160">Indicates that this cmdlet returns only base name of the leaf.</span></span>
<span data-ttu-id="9c3c6-161">I sökvägen returneras till exempel `C:\Test\Logs\Pass1.log` bara `Pass1` .</span><span class="sxs-lookup"><span data-stu-id="9c3c6-161">For example, in the path `C:\Test\Logs\Pass1.log`, it returns only `Pass1`.</span></span>

<span data-ttu-id="9c3c6-162">Den här parametern introducerades i PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="9c3c6-162">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LeafBaseSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9c3c6-163">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="9c3c6-163">-LiteralPath</span></span>

<span data-ttu-id="9c3c6-164">Anger vilka sökvägar som ska delas.</span><span class="sxs-lookup"><span data-stu-id="9c3c6-164">Specifies the paths to be split.</span></span>
<span data-ttu-id="9c3c6-165">Till skillnad från *sökväg* används värdet för *LiteralPath* exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="9c3c6-165">Unlike *Path* , the value of *LiteralPath* is used exactly as it is typed.</span></span>
<span data-ttu-id="9c3c6-166">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="9c3c6-166">No characters are interpreted as wildcard characters.</span></span>
<span data-ttu-id="9c3c6-167">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="9c3c6-167">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="9c3c6-168">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="9c3c6-168">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPathSet
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9c3c6-169">-Nokvalificerare</span><span class="sxs-lookup"><span data-stu-id="9c3c6-169">-NoQualifier</span></span>

<span data-ttu-id="9c3c6-170">Anger att denna cmdlet returnerar sökvägen utan kvalificeraren.</span><span class="sxs-lookup"><span data-stu-id="9c3c6-170">Indicates that this cmdlet returns the path without the qualifier.</span></span>
<span data-ttu-id="9c3c6-171">För fil systemet eller register leverantörer är kvalificeraren enhet för providerns sökväg, till exempel C: eller HKCU:.</span><span class="sxs-lookup"><span data-stu-id="9c3c6-171">For the FileSystem or registry providers, the qualifier is the drive of the provider path, such as C: or HKCU:.</span></span>
<span data-ttu-id="9c3c6-172">I sökvägen returnerar till exempel `C:\Test\Logs\Pass1.log` bara \Test\Logs\Pass1.log.</span><span class="sxs-lookup"><span data-stu-id="9c3c6-172">For example, in the path `C:\Test\Logs\Pass1.log`, it returns only \Test\Logs\Pass1.log.</span></span>

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

### <span data-ttu-id="9c3c6-173">– Överordnad</span><span class="sxs-lookup"><span data-stu-id="9c3c6-173">-Parent</span></span>

<span data-ttu-id="9c3c6-174">Anger att denna cmdlet endast returnerar överordnade behållare för objektet eller den behållare som anges av sökvägen.</span><span class="sxs-lookup"><span data-stu-id="9c3c6-174">Indicates that this cmdlet returns only the parent containers of the item or of the container specified by the path.</span></span>
<span data-ttu-id="9c3c6-175">I sökvägen returnerar till exempel `C:\Test\Logs\Pass1.log` C:\Test\Logs.</span><span class="sxs-lookup"><span data-stu-id="9c3c6-175">For example, in the path `C:\Test\Logs\Pass1.log`, it returns C:\Test\Logs.</span></span>
<span data-ttu-id="9c3c6-176">Den *överordnade* parametern är standard parametern för delad plats.</span><span class="sxs-lookup"><span data-stu-id="9c3c6-176">The *Parent* parameter is the default split location parameter.</span></span>

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

### <span data-ttu-id="9c3c6-177">-Path</span><span class="sxs-lookup"><span data-stu-id="9c3c6-177">-Path</span></span>

<span data-ttu-id="9c3c6-178">Anger vilka sökvägar som ska delas.</span><span class="sxs-lookup"><span data-stu-id="9c3c6-178">Specifies the paths to be split.</span></span>
<span data-ttu-id="9c3c6-179">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="9c3c6-179">Wildcard characters are permitted.</span></span>
<span data-ttu-id="9c3c6-180">Om sökvägen innehåller blank steg, omger du den med citat tecken.</span><span class="sxs-lookup"><span data-stu-id="9c3c6-180">If the path includes spaces, enclose it in quotation marks.</span></span>
<span data-ttu-id="9c3c6-181">Du kan också skicka en sökväg till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9c3c6-181">You can also pipe a path to this cmdlet.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ParentSet, LeafSet, LeafBaseSet, ExtensionSet, QualifierSet, NoQualifierSet, IsAbsoluteSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="9c3c6-182">-Kvalificerare</span><span class="sxs-lookup"><span data-stu-id="9c3c6-182">-Qualifier</span></span>

<span data-ttu-id="9c3c6-183">Anger att denna cmdlet bara returnerar kvalificeraren för den angivna sökvägen.</span><span class="sxs-lookup"><span data-stu-id="9c3c6-183">Indicates that this cmdlet returns only the qualifier of the specified path.</span></span>
<span data-ttu-id="9c3c6-184">För fil systemet eller register leverantörer är kvalificeraren enhet för providerns sökväg, till exempel C: eller HKCU:.</span><span class="sxs-lookup"><span data-stu-id="9c3c6-184">For the FileSystem or registry providers, the qualifier is the drive of the provider path, such as C: or HKCU:.</span></span>

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

### <span data-ttu-id="9c3c6-185">-Lös</span><span class="sxs-lookup"><span data-stu-id="9c3c6-185">-Resolve</span></span>

<span data-ttu-id="9c3c6-186">Anger att den här cmdleten visar objekt som refereras till av den resulterande delade sökvägen i stället för att Visa Sök vägs elementen.</span><span class="sxs-lookup"><span data-stu-id="9c3c6-186">Indicates that this cmdlet displays the items that are referenced by the resulting split path instead of displaying the path elements.</span></span>

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

### <span data-ttu-id="9c3c6-187">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9c3c6-187">CommonParameters</span></span>

<span data-ttu-id="9c3c6-188">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9c3c6-188">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9c3c6-189">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="9c3c6-189">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9c3c6-190">INDATA</span><span class="sxs-lookup"><span data-stu-id="9c3c6-190">INPUTS</span></span>

### <span data-ttu-id="9c3c6-191">System. String</span><span class="sxs-lookup"><span data-stu-id="9c3c6-191">System.String</span></span>

<span data-ttu-id="9c3c6-192">Du kan skicka vidare en sträng som innehåller en sökväg till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9c3c6-192">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="9c3c6-193">UTDATA</span><span class="sxs-lookup"><span data-stu-id="9c3c6-193">OUTPUTS</span></span>

### <span data-ttu-id="9c3c6-194">System. String, system. Boolean</span><span class="sxs-lookup"><span data-stu-id="9c3c6-194">System.String, System.Boolean</span></span>

<span data-ttu-id="9c3c6-195">**Split-Path** returnerar text strängar.</span><span class="sxs-lookup"><span data-stu-id="9c3c6-195">**Split-Path** returns text strings.</span></span>
<span data-ttu-id="9c3c6-196">När du anger parametern *matcha* , returnerar **delad sökväg** en sträng som beskriver objektets placering. det returnerar inte objekt som representerar objekten, till exempel ett **fileinfo** -eller **RegistryKey** -objekt.</span><span class="sxs-lookup"><span data-stu-id="9c3c6-196">When you specify the *Resolve* parameter, **Split-Path** returns a string that describes the location of the items; it does not return objects that represent the items, such as a **FileInfo** or **RegistryKey** object.</span></span>

<span data-ttu-id="9c3c6-197">När du anger parametern *IsAbsolute* , returnerar **delad sökväg** ett **booleskt** värde.</span><span class="sxs-lookup"><span data-stu-id="9c3c6-197">When you specify the *IsAbsolute* parameter, **Split-Path** returns a **Boolean** value.</span></span>

## <span data-ttu-id="9c3c6-198">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="9c3c6-198">NOTES</span></span>

* <span data-ttu-id="9c3c6-199">Parametrarna för delad plats ( *kvalificerare* , *överordnad* , *tillägg* , *löv* , *LeafBase* och *noqualifier* ) är exklusiva.</span><span class="sxs-lookup"><span data-stu-id="9c3c6-199">The split location parameters ( *Qualifier* , *Parent* , *Extension* , *Leaf* , *LeafBase* , and *NoQualifier* ) are exclusive.</span></span> <span data-ttu-id="9c3c6-200">Du kan bara använda ett i varje kommando.</span><span class="sxs-lookup"><span data-stu-id="9c3c6-200">You can use only one in each command.</span></span>

  <span data-ttu-id="9c3c6-201">Cmdlet: arna som innehåller **sökvägen** Substantiv ( **Sök vägs** -cmdletarna) fungerar med Sök vägs namn och returnerar namnen i ett koncist format som alla PowerShell-leverantörer kan tolka.</span><span class="sxs-lookup"><span data-stu-id="9c3c6-201">The cmdlets that contain the **Path** noun (the **Path** cmdlets) work with path names and return the names in a concise format that all PowerShell providers can interpret.</span></span>
<span data-ttu-id="9c3c6-202">De är utformade för användning i program och skript där du vill visa hela eller delar av ett Sök vägs namn i ett visst format.</span><span class="sxs-lookup"><span data-stu-id="9c3c6-202">They are designed for use in programs and scripts where you want to display all or part of a path name in a particular format.</span></span>
<span data-ttu-id="9c3c6-203">Använd dem på det sätt som du använder **logsdirectory** , **Normpath** , **realpath** , **Join** eller andra Sök vägs manipulerare.</span><span class="sxs-lookup"><span data-stu-id="9c3c6-203">Use them in the way that you would use **Dirname** , **Normpath** , **Realpath** , **Join** , or other path manipulators.</span></span>

  <span data-ttu-id="9c3c6-204">Du kan använda **Sök vägs** -cmdletarna tillsammans med flera providers.</span><span class="sxs-lookup"><span data-stu-id="9c3c6-204">You can use the **Path** cmdlets together with several providers.</span></span>
<span data-ttu-id="9c3c6-205">Dessa omfattar fil systemet system, register och certifikat.</span><span class="sxs-lookup"><span data-stu-id="9c3c6-205">These include the FileSystem, Registry, and Certificate providers.</span></span>

  <span data-ttu-id="9c3c6-206">**Split-Path** är utformad för att fungera med data som exponeras av vilken provider som helst.</span><span class="sxs-lookup"><span data-stu-id="9c3c6-206">**Split-Path** is designed to work with the data exposed by any provider.</span></span>
<span data-ttu-id="9c3c6-207">Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="9c3c6-207">To list the providers available in your session, type `Get-PSProvider`.</span></span>
<span data-ttu-id="9c3c6-208">Mer information finns i about_Providers.</span><span class="sxs-lookup"><span data-stu-id="9c3c6-208">For more information, see about_Providers.</span></span>

## <span data-ttu-id="9c3c6-209">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="9c3c6-209">RELATED LINKS</span></span>

[<span data-ttu-id="9c3c6-210">Konvertera-sökväg</span><span class="sxs-lookup"><span data-stu-id="9c3c6-210">Convert-Path</span></span>](Convert-Path.md)

[<span data-ttu-id="9c3c6-211">Anslut till sökväg</span><span class="sxs-lookup"><span data-stu-id="9c3c6-211">Join-Path</span></span>](Join-Path.md)

[<span data-ttu-id="9c3c6-212">Lös-sökväg</span><span class="sxs-lookup"><span data-stu-id="9c3c6-212">Resolve-Path</span></span>](Resolve-Path.md)

[<span data-ttu-id="9c3c6-213">Test-sökväg</span><span class="sxs-lookup"><span data-stu-id="9c3c6-213">Test-Path</span></span>](Test-Path.md)
