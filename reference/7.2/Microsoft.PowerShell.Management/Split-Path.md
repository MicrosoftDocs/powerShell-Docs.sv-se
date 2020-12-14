---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/split-path?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Split-Path
ms.openlocfilehash: e2498c02d42123e207b49e622654d3cb881fc0fc
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710386"
---
# <span data-ttu-id="0720e-102">Split-Path</span><span class="sxs-lookup"><span data-stu-id="0720e-102">Split-Path</span></span>

## <span data-ttu-id="0720e-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="0720e-103">SYNOPSIS</span></span>
<span data-ttu-id="0720e-104">Returnerar den angivna delen av en sökväg.</span><span class="sxs-lookup"><span data-stu-id="0720e-104">Returns the specified part of a path.</span></span>

## <span data-ttu-id="0720e-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="0720e-105">SYNTAX</span></span>

### <span data-ttu-id="0720e-106">ParentSet (standard)</span><span class="sxs-lookup"><span data-stu-id="0720e-106">ParentSet (Default)</span></span>

```
Split-Path [-Path] <String[]> [-Parent] [-Resolve] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### <span data-ttu-id="0720e-107">LeafSet</span><span class="sxs-lookup"><span data-stu-id="0720e-107">LeafSet</span></span>

```
Split-Path [-Path] <String[]> -Leaf [-Resolve] [-Credential <PSCredential>] [<CommonParameters>]
```

### <span data-ttu-id="0720e-108">LeafBaseSet</span><span class="sxs-lookup"><span data-stu-id="0720e-108">LeafBaseSet</span></span>

```
Split-Path [-Path] <String[]> -LeafBase [-Resolve] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### <span data-ttu-id="0720e-109">ExtensionSet</span><span class="sxs-lookup"><span data-stu-id="0720e-109">ExtensionSet</span></span>

```
Split-Path [-Path] <String[]> -Extension [-Resolve] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### <span data-ttu-id="0720e-110">QualifierSet</span><span class="sxs-lookup"><span data-stu-id="0720e-110">QualifierSet</span></span>

```
Split-Path [-Path] <String[]> -Qualifier [-Resolve] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### <span data-ttu-id="0720e-111">NoQualifierSet</span><span class="sxs-lookup"><span data-stu-id="0720e-111">NoQualifierSet</span></span>

```
Split-Path [-Path] <String[]> -NoQualifier [-Resolve] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### <span data-ttu-id="0720e-112">IsAbsoluteSet</span><span class="sxs-lookup"><span data-stu-id="0720e-112">IsAbsoluteSet</span></span>

```
Split-Path [-Path] <String[]> [-Resolve] -IsAbsolute [-Credential <PSCredential>]
 [<CommonParameters>]
```

### <span data-ttu-id="0720e-113">LiteralPathSet</span><span class="sxs-lookup"><span data-stu-id="0720e-113">LiteralPathSet</span></span>

```
Split-Path -LiteralPath <String[]> [-Resolve] [-Credential <PSCredential>] [<CommonParameters>]
```

## <span data-ttu-id="0720e-114">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="0720e-114">DESCRIPTION</span></span>

<span data-ttu-id="0720e-115">`Split-Path`Cmdleten returnerar bara den angivna delen av en sökväg, till exempel den överordnade mappen, en undermapp eller ett fil namn.</span><span class="sxs-lookup"><span data-stu-id="0720e-115">The `Split-Path` cmdlet returns only the specified part of a path, such as the parent folder, a subfolder, or a file name.</span></span> <span data-ttu-id="0720e-116">Det kan också hämta objekt som refereras av den delade sökvägen och se om sökvägen är relativ eller absolut.</span><span class="sxs-lookup"><span data-stu-id="0720e-116">It can also get items that are referenced by the split path and tell whether the path is relative or absolute.</span></span>

<span data-ttu-id="0720e-117">Du kan använda den här cmdleten för att hämta eller skicka endast en markerad del av en sökväg.</span><span class="sxs-lookup"><span data-stu-id="0720e-117">You can use this cmdlet to get or submit only a selected part of a path.</span></span>

## <span data-ttu-id="0720e-118">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="0720e-118">EXAMPLES</span></span>

### <span data-ttu-id="0720e-119">Exempel 1: Hämta en sökvägs kvalificerare</span><span class="sxs-lookup"><span data-stu-id="0720e-119">Example 1: Get the qualifier of a path</span></span>

```powershell
Split-Path -Path "HKCU:\Software\Microsoft" -Qualifier
```

```Output
HKCU:
```

<span data-ttu-id="0720e-120">Det här kommandot returnerar bara kvalificeraren för sökvägen.</span><span class="sxs-lookup"><span data-stu-id="0720e-120">This command returns only the qualifier of the path.</span></span> <span data-ttu-id="0720e-121">Kvalificeraren är enheten.</span><span class="sxs-lookup"><span data-stu-id="0720e-121">The qualifier is the drive.</span></span>

### <span data-ttu-id="0720e-122">Exempel 2: Visa fil namn</span><span class="sxs-lookup"><span data-stu-id="0720e-122">Example 2: Display file names</span></span>

```powershell
Split-Path -Path "C:\Test\Logs\*.log" -Leaf -Resolve
```

```Output
Pass1.log
Pass2.log
...
```

<span data-ttu-id="0720e-123">Det här kommandot visar de filer som refereras av den delade sökvägen.</span><span class="sxs-lookup"><span data-stu-id="0720e-123">This command displays the files that are referenced by the split path.</span></span> <span data-ttu-id="0720e-124">Eftersom den här sökvägen är delad till det sista objektet, även kallat lövnod, visar kommandot bara fil namnen.</span><span class="sxs-lookup"><span data-stu-id="0720e-124">Because this path is split to the last item, also known as the leaf, the command displays only the file names.</span></span>

<span data-ttu-id="0720e-125">Parametern **matcha** visar `Split-Path` de objekt som den delade sökvägen refererar till, i stället för att Visa delnings Sök vägen.</span><span class="sxs-lookup"><span data-stu-id="0720e-125">The **Resolve** parameter tells `Split-Path` to display the items that the split path references, instead of displaying the split path.</span></span>

<span data-ttu-id="0720e-126">Precis som alla `Split-Path` kommandon returnerar det här kommandot strängar.</span><span class="sxs-lookup"><span data-stu-id="0720e-126">Like all `Split-Path` commands, this command returns strings.</span></span> <span data-ttu-id="0720e-127">Den returnerar inte **fileinfo** -objekt som representerar filerna.</span><span class="sxs-lookup"><span data-stu-id="0720e-127">It does not return **FileInfo** objects that represent the files.</span></span>

### <span data-ttu-id="0720e-128">Exempel 3: hämta den överordnade behållaren</span><span class="sxs-lookup"><span data-stu-id="0720e-128">Example 3: Get the parent container</span></span>

```powershell
Split-Path -Path "C:\WINDOWS\system32\WindowsPowerShell\V1.0\about_*.txt"
```

```Output
C:\WINDOWS\system32\WindowsPowerShell\V1.0
```

<span data-ttu-id="0720e-129">Det här kommandot returnerar bara de överordnade behållarna för sökvägen.</span><span class="sxs-lookup"><span data-stu-id="0720e-129">This command returns only the parent containers of the path.</span></span> <span data-ttu-id="0720e-130">Eftersom den inte innehåller några parametrar för att ange delning, `Split-Path` använder standard delnings platsen, som är **överordnad**.</span><span class="sxs-lookup"><span data-stu-id="0720e-130">Because it does not include any parameters to specify the split, `Split-Path` uses the split location default, which is **Parent**.</span></span>

### <span data-ttu-id="0720e-131">Exempel 4: avgör om en sökväg är absolut</span><span class="sxs-lookup"><span data-stu-id="0720e-131">Example 4: Determines whether a path is absolute</span></span>

```powershell
Split-Path -Path ".\My Pictures\*.jpg" -IsAbsolute
```

```Output
False
```

<span data-ttu-id="0720e-132">Det här kommandot avgör om sökvägen är relativ eller absolut.</span><span class="sxs-lookup"><span data-stu-id="0720e-132">This command determines whether the path is relative or absolute.</span></span> <span data-ttu-id="0720e-133">I det här fallet, eftersom sökvägen är relativ till den aktuella mappen, som representeras av en punkt ( `.` ), returneras `$False` .</span><span class="sxs-lookup"><span data-stu-id="0720e-133">In this case, because the path is relative to the current folder, which is represented by a dot (`.`), it returns `$False`.</span></span>

### <span data-ttu-id="0720e-134">Exempel 5: ändra plats till en angiven sökväg</span><span class="sxs-lookup"><span data-stu-id="0720e-134">Example 5: Change location to a specified path</span></span>

```powershell
PS C:\> Set-Location (Split-Path -Path $profile)
PS C:\Documents and Settings\User01\My Documents\WindowsPowerShell>
```

<span data-ttu-id="0720e-135">Det här kommandot ändrar platsen till den mapp som innehåller PowerShell-profilen.</span><span class="sxs-lookup"><span data-stu-id="0720e-135">This command changes your location to the folder that contains the PowerShell profile.</span></span>

<span data-ttu-id="0720e-136">Kommandot inom parenteser använder `Split-Path` för att bara returnera den överordnade sökvägen till sökvägen som lagras i den inbyggda `$Profile` variabeln.</span><span class="sxs-lookup"><span data-stu-id="0720e-136">The command in parentheses uses `Split-Path` to return only the parent of the path stored in the built-in `$Profile` variable.</span></span> <span data-ttu-id="0720e-137">Den **överordnade** parametern är standard parametern för delad plats.</span><span class="sxs-lookup"><span data-stu-id="0720e-137">The **Parent** parameter is the default split location parameter.</span></span>
<span data-ttu-id="0720e-138">Därför kan du utelämna det från kommandot.</span><span class="sxs-lookup"><span data-stu-id="0720e-138">Therefore, you can omit it from the command.</span></span> <span data-ttu-id="0720e-139">Parenteserna Direct PowerShell för att köra kommandot först.</span><span class="sxs-lookup"><span data-stu-id="0720e-139">The parentheses direct PowerShell to run the command first.</span></span> <span data-ttu-id="0720e-140">Detta är ett bra sätt att flytta till en mapp som har ett långt Sök vägs namn.</span><span class="sxs-lookup"><span data-stu-id="0720e-140">This is a useful way to move to a folder that has a long path name.</span></span>

### <span data-ttu-id="0720e-141">Exempel 6: dela en bana med hjälp av pipelinen</span><span class="sxs-lookup"><span data-stu-id="0720e-141">Example 6: Split a path by using the pipeline</span></span>

```powershell
'C:\Documents and Settings\User01\My Documents\My Pictures' | Split-Path
```

```Output
C:\Documents and Settings\User01\My Documents
```

<span data-ttu-id="0720e-142">Det här kommandot använder en pipeline-operator ( `|` ) för att skicka en sökväg till `Split-Path` .</span><span class="sxs-lookup"><span data-stu-id="0720e-142">This command uses a pipeline operator (`|`) to send a path to `Split-Path`.</span></span> <span data-ttu-id="0720e-143">Sökvägen omges av citat tecken för att ange att den är en enskild token.</span><span class="sxs-lookup"><span data-stu-id="0720e-143">The path is enclosed in quotation marks to indicate that it is a single token.</span></span>

## <span data-ttu-id="0720e-144">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="0720e-144">PARAMETERS</span></span>

### <span data-ttu-id="0720e-145">-Credential</span><span class="sxs-lookup"><span data-stu-id="0720e-145">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="0720e-146">Den här parametern stöds inte av några providrar som installeras med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0720e-146">This parameter is not supported by any providers installed with PowerShell.</span></span> <span data-ttu-id="0720e-147">Om du vill personifiera en annan användare eller öka dina autentiseringsuppgifter när du kör denna cmdlet, använder du [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="0720e-147">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="0720e-148">-Tillägg</span><span class="sxs-lookup"><span data-stu-id="0720e-148">-Extension</span></span>

<span data-ttu-id="0720e-149">Anger att denna cmdlet bara returnerar tillägg för bladet.</span><span class="sxs-lookup"><span data-stu-id="0720e-149">Indicates that this cmdlet returns only the extension of the leaf.</span></span> <span data-ttu-id="0720e-150">I sökvägen returneras till exempel `C:\Test\Logs\Pass1.log` bara `.log` .</span><span class="sxs-lookup"><span data-stu-id="0720e-150">For example, in the path `C:\Test\Logs\Pass1.log`, it returns only `.log`.</span></span>

<span data-ttu-id="0720e-151">Den här parametern introducerades i PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="0720e-151">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ExtensionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="0720e-152">-IsAbsolute</span><span class="sxs-lookup"><span data-stu-id="0720e-152">-IsAbsolute</span></span>

<span data-ttu-id="0720e-153">Anger att denna cmdlet returnerar $True om sökvägen är absolut och $False om den är relativ.</span><span class="sxs-lookup"><span data-stu-id="0720e-153">Indicates that this cmdlet returns $True if the path is absolute and $False if it is relative.</span></span> <span data-ttu-id="0720e-154">En absolut sökväg har en längd som är större än noll och använder inte en punkt ( `.` ) för att ange den aktuella sökvägen.</span><span class="sxs-lookup"><span data-stu-id="0720e-154">An absolute path has a length greater than zero and does not use a dot (`.`) to indicate the current path.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: IsAbsoluteSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0720e-155">-Löv</span><span class="sxs-lookup"><span data-stu-id="0720e-155">-Leaf</span></span>

<span data-ttu-id="0720e-156">Anger att denna cmdlet endast returnerar det sista objektet eller behållaren i sökvägen.</span><span class="sxs-lookup"><span data-stu-id="0720e-156">Indicates that this cmdlet returns only the last item or container in the path.</span></span> <span data-ttu-id="0720e-157">I sökvägen returnerar till exempel `C:\Test\Logs\Pass1.log` bara Pass1. log.</span><span class="sxs-lookup"><span data-stu-id="0720e-157">For example, in the path `C:\Test\Logs\Pass1.log`, it returns only Pass1.log.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LeafSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="0720e-158">-LeafBase</span><span class="sxs-lookup"><span data-stu-id="0720e-158">-LeafBase</span></span>

<span data-ttu-id="0720e-159">Anger att denna cmdlet returnerar endast bas namnet för löv.</span><span class="sxs-lookup"><span data-stu-id="0720e-159">Indicates that this cmdlet returns only base name of the leaf.</span></span> <span data-ttu-id="0720e-160">I sökvägen returneras till exempel `C:\Test\Logs\Pass1.log` bara `Pass1` .</span><span class="sxs-lookup"><span data-stu-id="0720e-160">For example, in the path `C:\Test\Logs\Pass1.log`, it returns only `Pass1`.</span></span>

<span data-ttu-id="0720e-161">Den här parametern introducerades i PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="0720e-161">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LeafBaseSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="0720e-162">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="0720e-162">-LiteralPath</span></span>

<span data-ttu-id="0720e-163">Anger vilka sökvägar som ska delas.</span><span class="sxs-lookup"><span data-stu-id="0720e-163">Specifies the paths to be split.</span></span> <span data-ttu-id="0720e-164">Till skillnad från **sökväg** används värdet för **LiteralPath** exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="0720e-164">Unlike **Path**, the value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="0720e-165">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="0720e-165">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="0720e-166">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="0720e-166">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="0720e-167">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="0720e-167">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="0720e-168">-Nokvalificerare</span><span class="sxs-lookup"><span data-stu-id="0720e-168">-NoQualifier</span></span>

<span data-ttu-id="0720e-169">Anger att denna cmdlet returnerar sökvägen utan kvalificeraren.</span><span class="sxs-lookup"><span data-stu-id="0720e-169">Indicates that this cmdlet returns the path without the qualifier.</span></span> <span data-ttu-id="0720e-170">För fil systemet eller register leverantörer är kvalificeraren enhet för providerns sökväg, till exempel `C:` eller `HKCU:` .</span><span class="sxs-lookup"><span data-stu-id="0720e-170">For the FileSystem or registry providers, the qualifier is the drive of the provider path, such as `C:` or `HKCU:`.</span></span> <span data-ttu-id="0720e-171">I sökvägen returneras till exempel `C:\Test\Logs\Pass1.log` bara `\Test\Logs\Pass1.log` .</span><span class="sxs-lookup"><span data-stu-id="0720e-171">For example, in the path `C:\Test\Logs\Pass1.log`, it returns only `\Test\Logs\Pass1.log`.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NoQualifierSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="0720e-172">– Överordnad</span><span class="sxs-lookup"><span data-stu-id="0720e-172">-Parent</span></span>

<span data-ttu-id="0720e-173">Anger att denna cmdlet endast returnerar överordnade behållare för objektet eller den behållare som anges av sökvägen.</span><span class="sxs-lookup"><span data-stu-id="0720e-173">Indicates that this cmdlet returns only the parent containers of the item or of the container specified by the path.</span></span> <span data-ttu-id="0720e-174">I sökvägen returneras till exempel `C:\Test\Logs\Pass1.log` `C:\Test\Logs` .</span><span class="sxs-lookup"><span data-stu-id="0720e-174">For example, in the path `C:\Test\Logs\Pass1.log`, it returns `C:\Test\Logs`.</span></span>
<span data-ttu-id="0720e-175">Den **överordnade** parametern är standard parametern för delad plats.</span><span class="sxs-lookup"><span data-stu-id="0720e-175">The **Parent** parameter is the default split location parameter.</span></span>

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

### <span data-ttu-id="0720e-176">-Path</span><span class="sxs-lookup"><span data-stu-id="0720e-176">-Path</span></span>

<span data-ttu-id="0720e-177">Anger vilka sökvägar som ska delas.</span><span class="sxs-lookup"><span data-stu-id="0720e-177">Specifies the paths to be split.</span></span> <span data-ttu-id="0720e-178">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="0720e-178">Wildcard characters are permitted.</span></span> <span data-ttu-id="0720e-179">Om sökvägen innehåller blank steg, omger du den med citat tecken.</span><span class="sxs-lookup"><span data-stu-id="0720e-179">If the path includes spaces, enclose it in quotation marks.</span></span> <span data-ttu-id="0720e-180">Du kan också skicka en sökväg till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0720e-180">You can also pipe a path to this cmdlet.</span></span>

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

### <span data-ttu-id="0720e-181">-Kvalificerare</span><span class="sxs-lookup"><span data-stu-id="0720e-181">-Qualifier</span></span>

<span data-ttu-id="0720e-182">Anger att denna cmdlet bara returnerar kvalificeraren för den angivna sökvägen.</span><span class="sxs-lookup"><span data-stu-id="0720e-182">Indicates that this cmdlet returns only the qualifier of the specified path.</span></span> <span data-ttu-id="0720e-183">För fil systemet eller register leverantörer är kvalificeraren enhet för providerns sökväg, till exempel `C:` eller `HKCU:` .</span><span class="sxs-lookup"><span data-stu-id="0720e-183">For the FileSystem or registry providers, the qualifier is the drive of the provider path, such as `C:` or `HKCU:`.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: QualifierSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="0720e-184">-Lös</span><span class="sxs-lookup"><span data-stu-id="0720e-184">-Resolve</span></span>

<span data-ttu-id="0720e-185">Anger att den här cmdleten visar objekt som refereras till av den resulterande delade sökvägen i stället för att Visa Sök vägs elementen.</span><span class="sxs-lookup"><span data-stu-id="0720e-185">Indicates that this cmdlet displays the items that are referenced by the resulting split path instead of displaying the path elements.</span></span>

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

### <span data-ttu-id="0720e-186">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0720e-186">CommonParameters</span></span>

<span data-ttu-id="0720e-187">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="0720e-187">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0720e-188">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="0720e-188">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="0720e-189">INDATA</span><span class="sxs-lookup"><span data-stu-id="0720e-189">INPUTS</span></span>

### <span data-ttu-id="0720e-190">System. String</span><span class="sxs-lookup"><span data-stu-id="0720e-190">System.String</span></span>

<span data-ttu-id="0720e-191">Du kan skicka vidare en sträng som innehåller en sökväg till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0720e-191">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="0720e-192">UTDATA</span><span class="sxs-lookup"><span data-stu-id="0720e-192">OUTPUTS</span></span>

### <span data-ttu-id="0720e-193">System. String, system. Boolean</span><span class="sxs-lookup"><span data-stu-id="0720e-193">System.String, System.Boolean</span></span>

<span data-ttu-id="0720e-194">`Split-Path` returnerar text strängar.</span><span class="sxs-lookup"><span data-stu-id="0720e-194">`Split-Path` returns text strings.</span></span> <span data-ttu-id="0720e-195">När du anger parametern **matcha** `Split-Path` returneras en sträng som beskriver objektets placering. det returnerar inte objekt som representerar objekten, till exempel ett **fileinfo** -eller **RegistryKey** -objekt.</span><span class="sxs-lookup"><span data-stu-id="0720e-195">When you specify the **Resolve** parameter, `Split-Path` returns a string that describes the location of the items; it does not return objects that represent the items, such as a **FileInfo** or **RegistryKey** object.</span></span>

<span data-ttu-id="0720e-196"> `Split-Path` Returnerar ett **booleskt** värde när du anger parametern IsAbsolute.</span><span class="sxs-lookup"><span data-stu-id="0720e-196">When you specify the **IsAbsolute** parameter, `Split-Path` returns a **Boolean** value.</span></span>

## <span data-ttu-id="0720e-197">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="0720e-197">NOTES</span></span>

- <span data-ttu-id="0720e-198">Parametrarna för delad plats (**kvalificerare**, **överordnad**, **tillägg**, **löv**, **LeafBase** och **noqualifier**) är exklusiva.</span><span class="sxs-lookup"><span data-stu-id="0720e-198">The split location parameters (**Qualifier**, **Parent**, **Extension**, **Leaf**, **LeafBase**, and **NoQualifier**) are exclusive.</span></span> <span data-ttu-id="0720e-199">Du kan bara använda ett i varje kommando.</span><span class="sxs-lookup"><span data-stu-id="0720e-199">You can use only one in each command.</span></span>

- <span data-ttu-id="0720e-200">Cmdlet: arna som innehåller **sökvägen** Substantiv ( **Sök vägs** -cmdletarna) fungerar med Sök vägs namn och returnerar namnen i ett koncist format som alla PowerShell-leverantörer kan tolka.</span><span class="sxs-lookup"><span data-stu-id="0720e-200">The cmdlets that contain the **Path** noun (the **Path** cmdlets) work with path names and return the names in a concise format that all PowerShell providers can interpret.</span></span> <span data-ttu-id="0720e-201">De är utformade för användning i program och skript där du vill visa hela eller delar av ett Sök vägs namn i ett visst format.</span><span class="sxs-lookup"><span data-stu-id="0720e-201">They are designed for use in programs and scripts where you want to display all or part of a path name in a particular format.</span></span> <span data-ttu-id="0720e-202">Använd dem på det sätt som du använder **logsdirectory**, **Normpath**, **realpath**, **Join** eller andra Sök vägs manipulerare.</span><span class="sxs-lookup"><span data-stu-id="0720e-202">Use them in the way that you would use **Dirname**, **Normpath**, **Realpath**, **Join**, or other path manipulators.</span></span>

- <span data-ttu-id="0720e-203">Du kan använda **Sök vägs** -cmdletarna tillsammans med flera providers.</span><span class="sxs-lookup"><span data-stu-id="0720e-203">You can use the **Path** cmdlets together with several providers.</span></span> <span data-ttu-id="0720e-204">Dessa omfattar fil systemet system, register och certifikat.</span><span class="sxs-lookup"><span data-stu-id="0720e-204">These include the FileSystem, Registry, and Certificate providers.</span></span>

- <span data-ttu-id="0720e-205">`Split-Path` är utformad för att fungera med data som exponeras av vilken provider som helst.</span><span class="sxs-lookup"><span data-stu-id="0720e-205">`Split-Path` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="0720e-206">Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="0720e-206">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="0720e-207">Mer information finns i about_Providers.</span><span class="sxs-lookup"><span data-stu-id="0720e-207">For more information, see about_Providers.</span></span>

## <span data-ttu-id="0720e-208">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="0720e-208">RELATED LINKS</span></span>

[<span data-ttu-id="0720e-209">Konvertera-sökväg</span><span class="sxs-lookup"><span data-stu-id="0720e-209">Convert-Path</span></span>](Convert-Path.md)

[<span data-ttu-id="0720e-210">Anslut till sökväg</span><span class="sxs-lookup"><span data-stu-id="0720e-210">Join-Path</span></span>](Join-Path.md)

[<span data-ttu-id="0720e-211">Lös-sökväg</span><span class="sxs-lookup"><span data-stu-id="0720e-211">Resolve-Path</span></span>](Resolve-Path.md)

[<span data-ttu-id="0720e-212">Test-sökväg</span><span class="sxs-lookup"><span data-stu-id="0720e-212">Test-Path</span></span>](Test-Path.md)
