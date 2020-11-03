---
external help file: ISE-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: ISE
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/ise/import-isesnippet?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-IseSnippet
ms.openlocfilehash: 810be675fc593f665ccc6f3d5b86ac2f6b633863
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263877"
---
# <span data-ttu-id="1ed91-103">Import-IseSnippet</span><span class="sxs-lookup"><span data-stu-id="1ed91-103">Import-IseSnippet</span></span>

## <span data-ttu-id="1ed91-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="1ed91-104">SYNOPSIS</span></span>
<span data-ttu-id="1ed91-105">Importerar ISE-kodfragment till den aktuella sessionen</span><span class="sxs-lookup"><span data-stu-id="1ed91-105">Imports ISE snippets into the current session</span></span>

## <span data-ttu-id="1ed91-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="1ed91-106">SYNTAX</span></span>

### <span data-ttu-id="1ed91-107">FromFolder (standard)</span><span class="sxs-lookup"><span data-stu-id="1ed91-107">FromFolder (Default)</span></span>

```
Import-IseSnippet [-Path] <String> [-Recurse] [<CommonParameters>]
```

### <span data-ttu-id="1ed91-108">FromModule</span><span class="sxs-lookup"><span data-stu-id="1ed91-108">FromModule</span></span>

```
Import-IseSnippet [-Recurse] -Module <String> [-ListAvailable] [<CommonParameters>]
```

## <span data-ttu-id="1ed91-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="1ed91-109">DESCRIPTION</span></span>

<span data-ttu-id="1ed91-110">`Import-IseSnippet`Cmdleten importerar åter användning av text "fragment" från en modul eller en katalog till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="1ed91-110">The `Import-IseSnippet` cmdlet imports reusable text "snippets" from a module or a directory into the current session.</span></span> <span data-ttu-id="1ed91-111">Kodfragmenten är omedelbart tillgängliga för användning i Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="1ed91-111">The snippets are immediately available for use in Windows PowerShell ISE.</span></span> <span data-ttu-id="1ed91-112">Denna cmdlet fungerar bara i Windows PowerShell ISE (Integrated Scripting Environment).</span><span class="sxs-lookup"><span data-stu-id="1ed91-112">This cmdlet works only in Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

<span data-ttu-id="1ed91-113">Om du vill visa och använda de importerade kodfragmenten klickar du på **Starta kodfragment** på Windows PowerShell ISE **Redigera** -menyn eller trycker på <kbd>CTRL</kbd> + <kbd>J</kbd>.</span><span class="sxs-lookup"><span data-stu-id="1ed91-113">To view and use the imported snippets, from the Windows PowerShell ISE **Edit** menu, click **Start Snippets** or press <kbd>Ctrl</kbd>+<kbd>J</kbd>.</span></span>

<span data-ttu-id="1ed91-114">Importerade kodfragment är bara tillgängliga i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="1ed91-114">Imported snippets are available only in the current session.</span></span> <span data-ttu-id="1ed91-115">Om du vill importera kodfragmenten till alla Windows PowerShell ISE-sessioner, lägger du till ett `Import-IseSnippet` kommando i din Windows PowerShell-profil eller kopierar kodfragmentet till din lokala kodfragments katalog `$home\Documents\WindowsPowershell\Snippets` .</span><span class="sxs-lookup"><span data-stu-id="1ed91-115">To import the snippets into all Windows PowerShell ISE sessions, add an `Import-IseSnippet` command to your Windows PowerShell profile or copy the snippet files to your local snippets directory `$home\Documents\WindowsPowershell\Snippets`.</span></span>

<span data-ttu-id="1ed91-116">För att importera kodfragment måste de vara korrekt formaterade i XML-kodfragmentet för Windows PowerShell ISE kodfragment och sparas i Snippet.ps1XML-filer.</span><span class="sxs-lookup"><span data-stu-id="1ed91-116">To import snippets, they must be properly formatted in the snippet XML for Windows PowerShell ISE snippets and saved in Snippet.ps1xml files.</span></span> <span data-ttu-id="1ed91-117">Använd cmdleten för att skapa kvalificerade kodfragment `New-IseSnippet` .</span><span class="sxs-lookup"><span data-stu-id="1ed91-117">To create eligible snippets, use the `New-IseSnippet` cmdlet.</span></span> <span data-ttu-id="1ed91-118">`New-IseSnippet` skapar en `<SnippetTitle>.Snippets.ps1xml` fil i `$home\Documents\WindowsPowerShell\Snippets` katalogen.</span><span class="sxs-lookup"><span data-stu-id="1ed91-118">`New-IseSnippet` creates a `<SnippetTitle>.Snippets.ps1xml` file in the `$home\Documents\WindowsPowerShell\Snippets` directory.</span></span> <span data-ttu-id="1ed91-119">Du kan flytta eller kopiera kodfragmenten till katalogen kodfragment i en Windows PowerShell-modul, eller till en annan katalog.</span><span class="sxs-lookup"><span data-stu-id="1ed91-119">You can move or copy the snippets to the Snippets directory of a Windows PowerShell module, or to any other directory.</span></span>

<span data-ttu-id="1ed91-120">`Get-IseSnippet`Cmdleten, som hämtar användarbaserade kodfragment i den lokala kodfragment katalogen, hämtar inte importerade kodfragment.</span><span class="sxs-lookup"><span data-stu-id="1ed91-120">The `Get-IseSnippet` cmdlet, which gets user-created snippets in the local snippets directory, does not get imported snippets.</span></span>

<span data-ttu-id="1ed91-121">Den här cmdleten introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="1ed91-121">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="1ed91-122">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="1ed91-122">EXAMPLES</span></span>

### <span data-ttu-id="1ed91-123">Exempel 1: importera kodfragment från en katalog</span><span class="sxs-lookup"><span data-stu-id="1ed91-123">Example 1: Import snippets from a directory</span></span>

<span data-ttu-id="1ed91-124">I det här exemplet importeras kodfragmenten från `\\Server01\Public\Snippets` katalogen till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="1ed91-124">This example imports the snippets from the `\\Server01\Public\Snippets` directory into the current session.</span></span> <span data-ttu-id="1ed91-125">Den använder parametern **rekursivt** för att hämta kodfragment från alla under kataloger i avsnittet kod avsnitt.</span><span class="sxs-lookup"><span data-stu-id="1ed91-125">It uses the **Recurse** parameter to get snippets from all subdirectories of the Snippets directory.</span></span>

```powershell
Import-IseSnippet -Path \\Server01\Public\Snippets -Recurse
```

### <span data-ttu-id="1ed91-126">Exempel 2: importera kodfragment från en modul</span><span class="sxs-lookup"><span data-stu-id="1ed91-126">Example 2: Import snippets from a module</span></span>

<span data-ttu-id="1ed91-127">I det här exemplet importeras kodfragmenten från **SnippetModule** -modulen.</span><span class="sxs-lookup"><span data-stu-id="1ed91-127">This example imports the snippets from the **SnippetModule** module.</span></span> <span data-ttu-id="1ed91-128">Kommandot använder parametern **ListAvailable** för att importera kodfragmenten även om **SnippetModule** -modulen inte importeras till användarens session när kommandot körs.</span><span class="sxs-lookup"><span data-stu-id="1ed91-128">The command uses the **ListAvailable** parameter to import the snippets even if the **SnippetModule** module is not imported into the user's session when the command runs.</span></span>

```powershell
Import-IseSnippet -Module SnippetModule -ListAvailable
```

### <span data-ttu-id="1ed91-129">Exempel 3: hitta kodfragment i moduler</span><span class="sxs-lookup"><span data-stu-id="1ed91-129">Example 3: Find snippets in modules</span></span>

<span data-ttu-id="1ed91-130">Det här exemplet hämtar kodfragment i alla installerade moduler i PSModulePath-miljövariabeln.</span><span class="sxs-lookup"><span data-stu-id="1ed91-130">This example gets snippets in all installed modules in the PSModulePath environment variable.</span></span>

```powershell
($env:PSModulePath).split(";") |
  ForEach-Object {dir $_\*\Snippets\*.Snippets.ps1xml -ErrorAction SilentlyContinue} |
    ForEach-Object {$_.fullname}
```

### <span data-ttu-id="1ed91-131">Exempel 4: importera alla modul-kodfragment</span><span class="sxs-lookup"><span data-stu-id="1ed91-131">Example 4: Import all module snippets</span></span>

<span data-ttu-id="1ed91-132">I det här exemplet importeras alla kodfragment från alla installerade moduler till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="1ed91-132">This example imports all snippets from all installed modules into the current session.</span></span> <span data-ttu-id="1ed91-133">Normalt behöver du inte köra ett kommando som detta eftersom moduler som har kodfragment använder `Import-IseSnippet` cmdleten för att importera dem åt dig när modulen importeras.</span><span class="sxs-lookup"><span data-stu-id="1ed91-133">Typically, you don't need to run a command like this because modules that have snippets will use the `Import-IseSnippet` cmdlet to import them for you when the module is imported.</span></span>

```powershell
($env:PSModulePath).split(";") |
  ForEach-Object {dir $_\*\Snippets\*.Snippets.ps1xml -ErrorAction SilentlyContinue} |
    ForEach-Object {$psise.CurrentPowerShellTab.Snippets.Load($_)}
```

### <span data-ttu-id="1ed91-134">Exempel 5: kopiera alla kodfragment</span><span class="sxs-lookup"><span data-stu-id="1ed91-134">Example 5: Copy all module snippets</span></span>

<span data-ttu-id="1ed91-135">I det här exemplet kopieras kodfragment-filerna från alla installerade moduler till avsnittet kodfragment för den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="1ed91-135">This example copies the snippet files from all installed modules into the Snippets directory of the current user.</span></span> <span data-ttu-id="1ed91-136">Till skillnad från importerade kodfragment, som endast påverkar den aktuella sessionen, är de kopierade kodfragmenten tillgängliga i alla Windows PowerShell ISE-sessioner.</span><span class="sxs-lookup"><span data-stu-id="1ed91-136">Unlike imported snippets, which affect only the current session, copied snippets are available in every Windows PowerShell ISE session.</span></span>

```powershell
($env:PSModulePath).split(";") |
  ForEach-Object {dir $_\*\Snippets\*.Snippets.ps1xml -ErrorAction SilentlyContinue} |
    Copy-Item -Destination $home\Documents\WindowsPowerShell\Snippets
```

## <span data-ttu-id="1ed91-137">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="1ed91-137">PARAMETERS</span></span>

### <span data-ttu-id="1ed91-138">– ListAvailable</span><span class="sxs-lookup"><span data-stu-id="1ed91-138">-ListAvailable</span></span>

<span data-ttu-id="1ed91-139">Anger att denna cmdlet hämtar kodfragment från moduler som är installerade på datorn, även om modulerna inte importeras till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="1ed91-139">Indicates that this cmdlet gets snippets from modules that are installed on the computer, even if the modules are not imported into the current session.</span></span> <span data-ttu-id="1ed91-140">Om den här parametern utelämnas och modulen som anges av parametern **modul** inte importeras till den aktuella sessionen, Miss lyckas försöket att hämta kodfragmenten från modulen.</span><span class="sxs-lookup"><span data-stu-id="1ed91-140">If this parameter is omitted, and the module that is specified by the **Module** parameter is not imported into the current session, the attempt to get the snippets from the module fails.</span></span>

<span data-ttu-id="1ed91-141">Den här parametern är endast giltig när parametern **module** används i kommandot.</span><span class="sxs-lookup"><span data-stu-id="1ed91-141">This parameter is valid only when the **Module** parameter is used in the command.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: FromModule
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1ed91-142">– Modul</span><span class="sxs-lookup"><span data-stu-id="1ed91-142">-Module</span></span>

<span data-ttu-id="1ed91-143">Importerar kodfragment från den angivna modulen till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="1ed91-143">Imports snippets from the specified module into the current session.</span></span> <span data-ttu-id="1ed91-144">Jokertecken stöds inte.</span><span class="sxs-lookup"><span data-stu-id="1ed91-144">Wildcard characters are not supported.</span></span>

<span data-ttu-id="1ed91-145">Den här parametern importerar kodfragment från Snippet.ps1XML-filer i under katalogen kodfragment i-modulens sökväg, till exempel `$home\Documents\WindowsPowerShell\Modules\<ModuleName>\Snippets` .</span><span class="sxs-lookup"><span data-stu-id="1ed91-145">This parameter imports snippets from Snippet.ps1xml files in the Snippets subdirectory in the module path, such as `$home\Documents\WindowsPowerShell\Modules\<ModuleName>\Snippets`.</span></span>

<span data-ttu-id="1ed91-146">Den här parametern är utformad för att användas av modulens författare i ett start skript, till exempel ett skript som anges i nyckeln **ScriptsToProcess** för ett modul manifest.</span><span class="sxs-lookup"><span data-stu-id="1ed91-146">This parameter is designed to be used by module authors in a startup script, such as a script specified in the **ScriptsToProcess** key of a module manifest.</span></span> <span data-ttu-id="1ed91-147">Kodfragment i en modul importeras inte automatiskt med modulen, men du kan använda ett `Import-IseSnippet` kommando för att importera dem.</span><span class="sxs-lookup"><span data-stu-id="1ed91-147">Snippets in a module are not automatically imported with the module, but you can use an `Import-IseSnippet` command to import them.</span></span>

```yaml
Type: System.String
Parameter Sets: FromModule
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1ed91-148">-Path</span><span class="sxs-lookup"><span data-stu-id="1ed91-148">-Path</span></span>

<span data-ttu-id="1ed91-149">Anger sökvägen till den katalog kod avsnitt där denna cmdlet importerar kodfragment.</span><span class="sxs-lookup"><span data-stu-id="1ed91-149">Specifies the path to the snippets directory in which this cmdlet imports snippets.</span></span>

```yaml
Type: System.String
Parameter Sets: FromFolder
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="1ed91-150">– Rekursivt</span><span class="sxs-lookup"><span data-stu-id="1ed91-150">-Recurse</span></span>

<span data-ttu-id="1ed91-151">Anger att denna cmdlet importerar kodfragment från alla under kataloger till värdet för parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="1ed91-151">Indicates that this cmdlet imports snippets from all subdirectories of the value of the **Path** parameter.</span></span>

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

### <span data-ttu-id="1ed91-152">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1ed91-152">CommonParameters</span></span>

<span data-ttu-id="1ed91-153">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1ed91-153">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1ed91-154">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="1ed91-154">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1ed91-155">INDATA</span><span class="sxs-lookup"><span data-stu-id="1ed91-155">INPUTS</span></span>

### <span data-ttu-id="1ed91-156">Inget</span><span class="sxs-lookup"><span data-stu-id="1ed91-156">None</span></span>

<span data-ttu-id="1ed91-157">Den här cmdleten tar inte emot några ininformation från pipelinen.</span><span class="sxs-lookup"><span data-stu-id="1ed91-157">This cmdlet does not take input from the pipeline.</span></span>

## <span data-ttu-id="1ed91-158">UTDATA</span><span class="sxs-lookup"><span data-stu-id="1ed91-158">OUTPUTS</span></span>

### <span data-ttu-id="1ed91-159">Inget</span><span class="sxs-lookup"><span data-stu-id="1ed91-159">None</span></span>

<span data-ttu-id="1ed91-160">Denna cmdlet genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="1ed91-160">This cmdlet does not generate output.</span></span>

## <span data-ttu-id="1ed91-161">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="1ed91-161">NOTES</span></span>

- <span data-ttu-id="1ed91-162">Du kan inte använda `Get-IseSnippet` cmdleten för att hämta importerade kodfragment.</span><span class="sxs-lookup"><span data-stu-id="1ed91-162">You cannot use the `Get-IseSnippet` cmdlet to get imported snippets.</span></span> <span data-ttu-id="1ed91-163">`Get-IseSnippet` hämtar endast kodfragment i `$home\Documents\WindowsPowerShell\Snippets` katalogen.</span><span class="sxs-lookup"><span data-stu-id="1ed91-163">`Get-IseSnippet` gets only snippets in the `$home\Documents\WindowsPowerShell\Snippets` directory.</span></span>
- <span data-ttu-id="1ed91-164">`Import-IseSnippet` använder den statiska metoden **load** static för **Microsoft. PowerShell. Host. ISE. ISESnippetCollection** -objekt.</span><span class="sxs-lookup"><span data-stu-id="1ed91-164">`Import-IseSnippet` uses the **Load** static method of **Microsoft.PowerShell.Host.ISE.ISESnippetCollection** objects.</span></span> <span data-ttu-id="1ed91-165">Du kan också använda **load** -metoden för kodfragment i Windows PowerShell ISE objekt modellen: `$psISE.CurrentPowerShellTab.Snippets.Load()`</span><span class="sxs-lookup"><span data-stu-id="1ed91-165">You can also use the **Load** method of snippets in the Windows PowerShell ISE object model: `$psISE.CurrentPowerShellTab.Snippets.Load()`</span></span>
- <span data-ttu-id="1ed91-166">`New-IseSnippet`Cmdlet: en lagrar nya användare-skapade kodfragment i osignerade. ps1xml-filer.</span><span class="sxs-lookup"><span data-stu-id="1ed91-166">The `New-IseSnippet` cmdlet stores new user-created snippets in unsigned .ps1xml files.</span></span> <span data-ttu-id="1ed91-167">Det innebär att Windows PowerShell inte kan läsa in dem i en session där körnings principen är **AllSigned** eller **begränsad**.</span><span class="sxs-lookup"><span data-stu-id="1ed91-167">As such, Windows PowerShell cannot load them into a session in which the execution policy is **AllSigned** or **Restricted**.</span></span> <span data-ttu-id="1ed91-168">I en **begränsad** eller **AllSigned** session kan du skapa, hämta och importera osignerade kodfragment, men du kan inte använda dem i sessionen.</span><span class="sxs-lookup"><span data-stu-id="1ed91-168">In a **Restricted** or **AllSigned** session, you can create, get, and import unsigned user-created snippets, but you cannot use them in the session.</span></span>

  <span data-ttu-id="1ed91-169">Om du vill använda osignerade användar kods tycken som `Import-IseSnippet` cmdleten returnerar ändrar du körnings principen och startar sedan om Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="1ed91-169">To use unsigned user-created snippets that the `Import-IseSnippet` cmdlet returns, change the execution policy, and then restart Windows PowerShell ISE.</span></span>

  <span data-ttu-id="1ed91-170">Mer information om körnings principer för Windows PowerShell finns i [about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md).</span><span class="sxs-lookup"><span data-stu-id="1ed91-170">For more information about Windows PowerShell execution policies, see [about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md).</span></span>

## <span data-ttu-id="1ed91-171">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="1ed91-171">RELATED LINKS</span></span>

[<span data-ttu-id="1ed91-172">Get-IseSnippet</span><span class="sxs-lookup"><span data-stu-id="1ed91-172">Get-IseSnippet</span></span>](Get-IseSnippet.md)

[<span data-ttu-id="1ed91-173">New-IseSnippet</span><span class="sxs-lookup"><span data-stu-id="1ed91-173">New-IseSnippet</span></span>](New-IseSnippet.md)
