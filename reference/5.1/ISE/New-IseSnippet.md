---
external help file: ISE-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: ISE
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/ise/new-isesnippet?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-IseSnippet
ms.openlocfilehash: 0ed1c2913fc7531574bfbdd435a002d60931d24a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263876"
---
# <span data-ttu-id="6bc31-103">New-IseSnippet</span><span class="sxs-lookup"><span data-stu-id="6bc31-103">New-IseSnippet</span></span>

## <span data-ttu-id="6bc31-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="6bc31-104">SYNOPSIS</span></span>
<span data-ttu-id="6bc31-105">Skapar ett Windows PowerShell ISE kodfragment.</span><span class="sxs-lookup"><span data-stu-id="6bc31-105">Creates a Windows PowerShell ISE code snippet.</span></span>

## <span data-ttu-id="6bc31-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6bc31-106">SYNTAX</span></span>

```
New-IseSnippet [-Title] <String> [-Description] <String> [-Text] <String> [-Author <String>]
 [-CaretOffset <Int32>] [-Force] [<CommonParameters>]
```

## <span data-ttu-id="6bc31-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="6bc31-107">DESCRIPTION</span></span>

<span data-ttu-id="6bc31-108">`New-ISESnippet`Cmdleten skapar en återanvändbar text "kodfragment" för Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="6bc31-108">The `New-ISESnippet` cmdlet creates a reusable text "snippet" for Windows PowerShell ISE.</span></span> <span data-ttu-id="6bc31-109">Du kan använda kodfragment för att lägga till text i skript fönstret eller kommando fönstret i Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="6bc31-109">You can use snippets to add text to the Script pane or Command pane in Windows PowerShell ISE.</span></span> <span data-ttu-id="6bc31-110">Den här cmdleten är endast tillgänglig i Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="6bc31-110">This cmdlet is available only in Windows PowerShell ISE.</span></span>

<span data-ttu-id="6bc31-111">Från och med Windows PowerShell 3,0 innehåller Windows PowerShell ISE en samling inbyggda kodfragment.</span><span class="sxs-lookup"><span data-stu-id="6bc31-111">Beginning in Windows PowerShell 3.0, Windows PowerShell ISE includes a collection of built-in snippets.</span></span> <span data-ttu-id="6bc31-112">Med `New-ISESnippet` cmdleten kan du skapa egna kod avsnitt som ska läggas till i den inbyggda samlingen.</span><span class="sxs-lookup"><span data-stu-id="6bc31-112">The `New-ISESnippet` cmdlet lets you create your own snippets to add to the built-in collection.</span></span> <span data-ttu-id="6bc31-113">Du kan visa, ändra, lägga till, ta bort och dela fragment-filer och inkludera dem i Windows PowerShell-moduler.</span><span class="sxs-lookup"><span data-stu-id="6bc31-113">You can view, change, add, delete, and share snippet files and include them in Windows PowerShell modules.</span></span> <span data-ttu-id="6bc31-114">Om du vill se kodfragment i Windows PowerShell ISE väljer du **Starta kodfragment** på **Redigera** -menyn eller trycker på <kbd>CTRL</kbd> + <kbd>J</kbd>.</span><span class="sxs-lookup"><span data-stu-id="6bc31-114">To see snippets in Windows PowerShell ISE, from the **Edit** menu, select **Start Snippets** or press <kbd>CTRL</kbd>+<kbd>J</kbd>.</span></span>

<span data-ttu-id="6bc31-115">`New-ISESnippet`Cmdleten skapar en `<Title>.Snippets.ps1xml` fil i `$home\Documents\WindowsPowerShell\Snippets` katalogen med den rubrik som du anger.</span><span class="sxs-lookup"><span data-stu-id="6bc31-115">The `New-ISESnippet` cmdlet creates a `<Title>.Snippets.ps1xml` file in the `$home\Documents\WindowsPowerShell\Snippets` directory with the title that you specify.</span></span> <span data-ttu-id="6bc31-116">Om du vill inkludera en kodfragments fil i en modul som du redigerar lägger du till kodfragment filen i en under katalog i en kod avsnitt i din modul katalog.</span><span class="sxs-lookup"><span data-stu-id="6bc31-116">To include a snippet file in a module that you are authoring, add the snippet file to a Snippets subdirectory of your module directory.</span></span>

<span data-ttu-id="6bc31-117">Du kan inte använda användardefinierade kodfragment i en session där körnings principen är **begränsad** eller **AllSigned**.</span><span class="sxs-lookup"><span data-stu-id="6bc31-117">You cannot use user-created snippets in a session in which the execution policy is **Restricted** or **AllSigned**.</span></span>

<span data-ttu-id="6bc31-118">Den här cmdleten introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="6bc31-118">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="6bc31-119">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="6bc31-119">EXAMPLES</span></span>

### <span data-ttu-id="6bc31-120">Exempel 1: skapa ett fragment för Comment-Based hjälp</span><span class="sxs-lookup"><span data-stu-id="6bc31-120">Example 1: Create a Comment-Based help snippet</span></span>

```
New-IseSnippet -Title Comment-BasedHelp -Description "A template for comment-based help." -Text "<#
    .SYNOPSIS

    .DESCRIPTION
    .PARAMETER  <Parameter-Name>
    .INPUTS
    .OUTPUTS
    .EXAMPLE
    .LINK
#>"
```

<span data-ttu-id="6bc31-121">Det här kommandot skapar ett Comment-BasedHelp-kodfragment för Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="6bc31-121">This command creates a Comment-BasedHelp snippet for Windows PowerShell ISE.</span></span> <span data-ttu-id="6bc31-122">Den skapar en fil med namnet `Comment-BasedHelp.snippets.ps1xml` i användarens kod avsnitts katalog `$home\Documents\WindowsPowerShell\Snippets` .</span><span class="sxs-lookup"><span data-stu-id="6bc31-122">It creates a file named `Comment-BasedHelp.snippets.ps1xml` in the user's Snippets directory `$home\Documents\WindowsPowerShell\Snippets`.</span></span>

### <span data-ttu-id="6bc31-123">Exempel 2: skapa ett obligatoriskt kod avsnitt</span><span class="sxs-lookup"><span data-stu-id="6bc31-123">Example 2: Create a mandatory snippet</span></span>

```
$M = @'
Param
(
  [parameter(Mandatory=$true)]
  [String[]]
  $<ParameterName>
)
'@

New-ISESnippet -Text $M -Title Mandatory -Description "Adds a mandatory function parameter." -Author "Patti Fuller, Fabrikam Corp." -Force
```

<span data-ttu-id="6bc31-124">I det här exemplet skapas ett kodfragment med namnet **obligatorisk** för Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="6bc31-124">This example creates a snippet named **Mandatory** for Windows PowerShell ISE.</span></span> <span data-ttu-id="6bc31-125">Det första kommandot sparar kodfragments texten i `$M` variabeln.</span><span class="sxs-lookup"><span data-stu-id="6bc31-125">The first command saves the snippet text in the `$M` variable.</span></span> <span data-ttu-id="6bc31-126">Det andra kommandot använder `New-ISESnippet` cmdleten för att skapa kodfragmentet.</span><span class="sxs-lookup"><span data-stu-id="6bc31-126">The second command uses the `New-ISESnippet` cmdlet to create the snippet.</span></span> <span data-ttu-id="6bc31-127">Kommandot använder **Force** -parametern för att skriva över ett tidigare kodfragment med samma namn.</span><span class="sxs-lookup"><span data-stu-id="6bc31-127">The command uses the **Force** parameter to overwrite a previous snippet with the same name.</span></span>

### <span data-ttu-id="6bc31-128">Exempel 3: kopiera ett obligatoriskt kodfragment från en mapp till en målmapp</span><span class="sxs-lookup"><span data-stu-id="6bc31-128">Example 3: Copy a mandatory snippet from a folder to a destination folder</span></span>

```
Copy-Item "$Home\Documents\WindowsPowerShell\Snippets\Mandatory.Snippets.ps1xml" -Destination "\\Server\Share"
```

<span data-ttu-id="6bc31-129">Det här kommandot använder `Copy-Item` cmdleten för att kopiera det **obligatoriska** kodfragmentet från mappen där `New-ISESnippet` placerar det till fil resursen Server\Share.</span><span class="sxs-lookup"><span data-stu-id="6bc31-129">This command uses the `Copy-Item` cmdlet to copy the **Mandatory** snippet from the folder where `New-ISESnippet` places it to the Server\Share file share.</span></span>

## <span data-ttu-id="6bc31-130">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="6bc31-130">PARAMETERS</span></span>

### <span data-ttu-id="6bc31-131">– Författare</span><span class="sxs-lookup"><span data-stu-id="6bc31-131">-Author</span></span>

<span data-ttu-id="6bc31-132">Anger författaren till kodfragmentet.</span><span class="sxs-lookup"><span data-stu-id="6bc31-132">Specifies the author of the snippet.</span></span> <span data-ttu-id="6bc31-133">Fältet författare visas i kodfragments filen, men det visas inte när du klickar på kodfragmentet i Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="6bc31-133">The author field appears in the snippet file, but it does not appear when you click the snippet name in Windows PowerShell ISE.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6bc31-134">-CaretOffset</span><span class="sxs-lookup"><span data-stu-id="6bc31-134">-CaretOffset</span></span>

<span data-ttu-id="6bc31-135">Anger tecken på kodfragments texten som denna cmdlet placerar markören på.</span><span class="sxs-lookup"><span data-stu-id="6bc31-135">Specifies the character of the snippet text that this cmdlet places the cursor on.</span></span> <span data-ttu-id="6bc31-136">Ange ett heltal som representerar markörens position med "1" som representerar det första text tecknen.</span><span class="sxs-lookup"><span data-stu-id="6bc31-136">Enter an integer that represents the cursor position, with "1" representing the first character of text.</span></span> <span data-ttu-id="6bc31-137">Standardvärdet, 0 (noll), placerar markören direkt före det första text tecken.</span><span class="sxs-lookup"><span data-stu-id="6bc31-137">The default value, 0 (zero), places the cursor immediately before the first character of text.</span></span> <span data-ttu-id="6bc31-138">Den här parametern drar inte in text i kodfragmentet.</span><span class="sxs-lookup"><span data-stu-id="6bc31-138">This parameter does not indent the snippet text.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 0
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6bc31-139">-Beskrivning</span><span class="sxs-lookup"><span data-stu-id="6bc31-139">-Description</span></span>

<span data-ttu-id="6bc31-140">Anger en beskrivning av kodfragmentet.</span><span class="sxs-lookup"><span data-stu-id="6bc31-140">Specifies a description of the snippet.</span></span> <span data-ttu-id="6bc31-141">Beskrivning svärdet visas när du klickar på namn kods tycket i Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="6bc31-141">The description value appears when you click the snippet name in Windows PowerShell ISE.</span></span> <span data-ttu-id="6bc31-142">Den här parametern är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="6bc31-142">This parameter is required.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6bc31-143">-Force</span><span class="sxs-lookup"><span data-stu-id="6bc31-143">-Force</span></span>

<span data-ttu-id="6bc31-144">Anger att denna cmdlet skriver över kodfragment-filer med samma namn på samma plats.</span><span class="sxs-lookup"><span data-stu-id="6bc31-144">Indicates that this cmdlet overwrites snippet files with the same name in the same location.</span></span> <span data-ttu-id="6bc31-145">Som standard `New-ISESnippet` skrivs inte filer över.</span><span class="sxs-lookup"><span data-stu-id="6bc31-145">By default, `New-ISESnippet` does not overwrite files.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6bc31-146">– Text</span><span class="sxs-lookup"><span data-stu-id="6bc31-146">-Text</span></span>

<span data-ttu-id="6bc31-147">Anger det text värde som läggs till när du väljer kodfragmentet.</span><span class="sxs-lookup"><span data-stu-id="6bc31-147">Specifies the text value that is added when you select the snippet.</span></span> <span data-ttu-id="6bc31-148">Kodfragmentet visas när du klickar på namn kods tycket i Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="6bc31-148">The snippet text appears when you click the snippet name in Windows PowerShell ISE.</span></span> <span data-ttu-id="6bc31-149">Den här parametern är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="6bc31-149">This parameter is required.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6bc31-150">– Rubrik</span><span class="sxs-lookup"><span data-stu-id="6bc31-150">-Title</span></span>

<span data-ttu-id="6bc31-151">Anger en titel eller ett namn för kodfragmentet.</span><span class="sxs-lookup"><span data-stu-id="6bc31-151">Specifies a title or name for the snippet.</span></span> <span data-ttu-id="6bc31-152">Rubriken namnger också kod filen.</span><span class="sxs-lookup"><span data-stu-id="6bc31-152">The title also names the snippet file.</span></span> <span data-ttu-id="6bc31-153">Den här parametern är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="6bc31-153">This parameter is required.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6bc31-154">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6bc31-154">CommonParameters</span></span>

<span data-ttu-id="6bc31-155">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="6bc31-155">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6bc31-156">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="6bc31-156">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6bc31-157">INDATA</span><span class="sxs-lookup"><span data-stu-id="6bc31-157">INPUTS</span></span>

### <span data-ttu-id="6bc31-158">Inget</span><span class="sxs-lookup"><span data-stu-id="6bc31-158">None</span></span>

<span data-ttu-id="6bc31-159">Den här cmdleten tar inte emot några ininformation från pipelinen.</span><span class="sxs-lookup"><span data-stu-id="6bc31-159">This cmdlet does not take input from the pipeline.</span></span>

## <span data-ttu-id="6bc31-160">UTDATA</span><span class="sxs-lookup"><span data-stu-id="6bc31-160">OUTPUTS</span></span>

### <span data-ttu-id="6bc31-161">Inget</span><span class="sxs-lookup"><span data-stu-id="6bc31-161">None</span></span>

<span data-ttu-id="6bc31-162">Denna cmdlet genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="6bc31-162">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="6bc31-163">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="6bc31-163">NOTES</span></span>

<span data-ttu-id="6bc31-164">`New-IseSnippet` lagrar nya användare-skapade kodfragment i osignerade. ps1xml-filer.</span><span class="sxs-lookup"><span data-stu-id="6bc31-164">`New-IseSnippet` stores new user-created snippets in unsigned .ps1xml files.</span></span> <span data-ttu-id="6bc31-165">Det innebär att Windows PowerShell inte kan lägga till dem i en session där körnings principen är **AllSigned** eller **begränsad**.</span><span class="sxs-lookup"><span data-stu-id="6bc31-165">As such, Windows PowerShell cannot add them to a session in which the execution policy is **AllSigned** or **Restricted**.</span></span> <span data-ttu-id="6bc31-166">I en **begränsad** eller **AllSigned** session kan du skapa, hämta och importera osignerade kodfragment, men du kan inte använda dem i sessionen.</span><span class="sxs-lookup"><span data-stu-id="6bc31-166">In a **Restricted** or **AllSigned** session, you can create, get, and import unsigned user-created snippets, but you cannot use them in the session.</span></span>

<span data-ttu-id="6bc31-167">Om du använder `New-IseSnippet` cmdleten i en **begränsad** eller **AllSigned** -session, skapas kodfragmentet, men ett fel meddelande visas när Windows PowerShell försöker lägga till det nyligen skapade kodfragmentet i sessionen.</span><span class="sxs-lookup"><span data-stu-id="6bc31-167">If you use the `New-IseSnippet` cmdlet in a **Restricted** or **AllSigned** session, the snippet is created, but an error message appears when Windows PowerShell tries to add the newly created snippet to the session.</span></span> <span data-ttu-id="6bc31-168">Om du vill använda det nya kodfragmentet (och andra osignerade användar kods tycken) ändrar du körnings principen och startar sedan om Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="6bc31-168">To use the new snippet (and other unsigned user-created snippets), change the execution policy, and then restart Windows PowerShell ISE.</span></span>

<span data-ttu-id="6bc31-169">Mer information om körnings principer för Windows PowerShell finns i about_Execution_Policies.</span><span class="sxs-lookup"><span data-stu-id="6bc31-169">For more information about Windows PowerShell execution policies, see about_Execution_Policies.</span></span>

- <span data-ttu-id="6bc31-170">Ändra kodfragmentet genom att redigera kodfragments filen.</span><span class="sxs-lookup"><span data-stu-id="6bc31-170">To change a snippet, edit the snippet file.</span></span> <span data-ttu-id="6bc31-171">Du kan redigera kodfragment-filer i skript fönstret i Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="6bc31-171">You can edit snippet files in the Script pane of Windows PowerShell ISE.</span></span>
- <span data-ttu-id="6bc31-172">Ta bort ett kodfragment som du har lagt till genom att ta bort kodfragments filen.</span><span class="sxs-lookup"><span data-stu-id="6bc31-172">To delete a snippet that you added, delete the snippet file.</span></span>
- <span data-ttu-id="6bc31-173">Det går inte att ta bort ett inbyggt kodfragment, men du kan dölja alla inbyggda kodfragment med hjälp av $psise. Options. ShowDefaultSnippets = $false "kommandot.</span><span class="sxs-lookup"><span data-stu-id="6bc31-173">You cannot delete a built-in snippet, but you can hide all built-in snippets by using the "$psise.Options.ShowDefaultSnippets=$false" command.</span></span>
- <span data-ttu-id="6bc31-174">Du kan skapa ett kodfragment som har samma namn som ett inbyggt kodfragment.</span><span class="sxs-lookup"><span data-stu-id="6bc31-174">You can create a snippet that has the same name as a built-in snippet.</span></span> <span data-ttu-id="6bc31-175">Båda kodfragmenten visas i menyn kodfragment i Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="6bc31-175">Both snippets appear in the snippet menu in Windows PowerShell ISE.</span></span>

## <span data-ttu-id="6bc31-176">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="6bc31-176">RELATED LINKS</span></span>

[<span data-ttu-id="6bc31-177">Get-IseSnippet</span><span class="sxs-lookup"><span data-stu-id="6bc31-177">Get-IseSnippet</span></span>](Get-IseSnippet.md)

[<span data-ttu-id="6bc31-178">Importera – IseSnippet</span><span class="sxs-lookup"><span data-stu-id="6bc31-178">Import-IseSnippet</span></span>](Import-IseSnippet.md)
