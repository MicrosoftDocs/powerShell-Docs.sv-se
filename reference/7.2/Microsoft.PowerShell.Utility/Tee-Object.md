---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/tee-object?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Tee-Object
ms.openlocfilehash: 5fd1ff9760cbddeb0c5c29052caf0f36d6d760d0
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709420"
---
# <span data-ttu-id="55249-102">Tee-Object</span><span class="sxs-lookup"><span data-stu-id="55249-102">Tee-Object</span></span>

## <span data-ttu-id="55249-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="55249-103">SYNOPSIS</span></span>
<span data-ttu-id="55249-104">Sparar kommandoutdata i en fil eller variabel och skickar det sedan till pipelinen.</span><span class="sxs-lookup"><span data-stu-id="55249-104">Saves command output in a file or variable and also sends it down the pipeline.</span></span>

## <span data-ttu-id="55249-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="55249-105">SYNTAX</span></span>

### <span data-ttu-id="55249-106">Fil (standard)</span><span class="sxs-lookup"><span data-stu-id="55249-106">File (Default)</span></span>

```
Tee-Object [-InputObject <PSObject>] [-FilePath] <String> [-Append] [<CommonParameters>]
```

### <span data-ttu-id="55249-107">LiteralFile</span><span class="sxs-lookup"><span data-stu-id="55249-107">LiteralFile</span></span>

```
Tee-Object [-InputObject <PSObject>] -LiteralPath <String> [<CommonParameters>]
```

### <span data-ttu-id="55249-108">Variabel</span><span class="sxs-lookup"><span data-stu-id="55249-108">Variable</span></span>

```
Tee-Object [-InputObject <PSObject>] -Variable <String> [<CommonParameters>]
```

## <span data-ttu-id="55249-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="55249-109">DESCRIPTION</span></span>

<span data-ttu-id="55249-110">`Tee-Object`Cmdleten omdirigerar utdata, det vill säga skickar utdata från ett kommando i två riktningar (t. ex. bokstaven T).</span><span class="sxs-lookup"><span data-stu-id="55249-110">The `Tee-Object` cmdlet redirects output, that is, it sends the output of a command in two directions (like the letter T).</span></span> <span data-ttu-id="55249-111">Den lagrar utdata i en fil eller variabel och skickar den sedan nedåt i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="55249-111">It stores the output in a file or variable and also sends it down the pipeline.</span></span> <span data-ttu-id="55249-112">Om `Tee-Object` är det sista kommandot i pipelinen visas kommandots utdata i prompten.</span><span class="sxs-lookup"><span data-stu-id="55249-112">If `Tee-Object` is the last command in the pipeline, the command output is displayed at the prompt.</span></span>

## <span data-ttu-id="55249-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="55249-113">EXAMPLES</span></span>

### <span data-ttu-id="55249-114">Exempel 1: utmatnings processer till en fil och till konsolen</span><span class="sxs-lookup"><span data-stu-id="55249-114">Example 1: Output processes to a file and to the console</span></span>

<span data-ttu-id="55249-115">Det här exemplet hämtar en lista över processerna som körs på datorn och skickar resultatet till en fil.</span><span class="sxs-lookup"><span data-stu-id="55249-115">This example gets a list of the processes running on the computer and sends the result to a file.</span></span>
<span data-ttu-id="55249-116">Eftersom en andra sökväg inte anges visas även processerna i-konsolen.</span><span class="sxs-lookup"><span data-stu-id="55249-116">Because a second path is not specified, the processes are also displayed in the console.</span></span>

```powershell
Get-Process | Tee-Object -FilePath "C:\Test1\testfile2.txt"
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)    Id ProcessName
-------  ------    -----      ----- -----   ------    -- -----------
83       4     2300       4520    39     0.30    4032 00THotkey
272      6     1400       3944    34     0.06    3088 alg
81       3      804       3284    21     2.45     148 ApntEx
81       4     2008       5808    38     0.75    3684 Apoint
...
```

### <span data-ttu-id="55249-117">Exempel 2: utmatnings processer till en variabel och `Select-Object`</span><span class="sxs-lookup"><span data-stu-id="55249-117">Example 2: Output processes to a variable and `Select-Object`</span></span>

<span data-ttu-id="55249-118">Det här exemplet hämtar en lista över processer som körs på datorn, sparar dem i `$proc` variabeln och rör dem `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="55249-118">This example gets a list of the processes running on the computer, saves them to the `$proc` variable, and pipes them to `Select-Object`.</span></span>

```powershell
Get-Process notepad | Tee-Object -Variable proc | Select-Object processname,handles
```

```Output
ProcessName                              Handles
-----------                              -------
notepad                                  43
notepad                                  37
notepad                                  38
notepad                                  38
```

<span data-ttu-id="55249-119">`Select-Object`Cmdleten väljer **processname** och **hanterar** egenskaperna.</span><span class="sxs-lookup"><span data-stu-id="55249-119">The `Select-Object` cmdlet selects the **ProcessName** and **Handles** properties.</span></span> <span data-ttu-id="55249-120">Observera att `$proc` variabeln innehåller den standard information som returneras av `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="55249-120">Note that the `$proc` variable includes the default information returned by `Get-Process`.</span></span>

### <span data-ttu-id="55249-121">Exempel 3: Spara systemfiler till två loggfiler</span><span class="sxs-lookup"><span data-stu-id="55249-121">Example 3: Output system files to two log files</span></span>

<span data-ttu-id="55249-122">I det här exemplet sparas en lista över systemfiler i två loggfiler, en ackumulerad fil och en aktuell fil.</span><span class="sxs-lookup"><span data-stu-id="55249-122">This example saves a list of system files in a two log files, a cumulative file and a current file.</span></span>

```powershell
Get-ChildItem -Path D: -File -System -Recurse |
  Tee-Object -FilePath "c:\test\AllSystemFiles.txt" -Append |
    Out-File c:\test\NewSystemFiles.txt
```

<span data-ttu-id="55249-123">Kommandot använder `Get-ChildItem` cmdleten för att göra en rekursiv sökning efter systemfiler på enheten D:.</span><span class="sxs-lookup"><span data-stu-id="55249-123">The command uses the `Get-ChildItem` cmdlet to do a recursive search for system files on the D: drive.</span></span> <span data-ttu-id="55249-124">En pipeline-operator (|) skickar listan till `Tee-Object` , som lägger till listan i AllSystemFiles.txt-filen och skickar listan nedåt till `Out-File` cmdleten, som sparar listan i NewSystemFiles.txts filen.</span><span class="sxs-lookup"><span data-stu-id="55249-124">A pipeline operator (|) sends the list to `Tee-Object`, which appends the list to the AllSystemFiles.txt file and passes the list down the pipeline to the `Out-File` cmdlet, which saves the list in the NewSystemFiles.txt file.</span></span>

## <span data-ttu-id="55249-125">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="55249-125">PARAMETERS</span></span>

### <span data-ttu-id="55249-126">-Lägg till</span><span class="sxs-lookup"><span data-stu-id="55249-126">-Append</span></span>

<span data-ttu-id="55249-127">Anger att cmdleten lägger till utdata i den angivna filen.</span><span class="sxs-lookup"><span data-stu-id="55249-127">Indicates that the cmdlet appends the output to the specified file.</span></span> <span data-ttu-id="55249-128">Utan den här parametern ersätter det nya innehållet det befintliga innehållet i filen utan varning.</span><span class="sxs-lookup"><span data-stu-id="55249-128">Without this parameter, the new content replaces any existing content in the file without warning.</span></span>

<span data-ttu-id="55249-129">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="55249-129">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: File
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="55249-130">-Sökväg</span><span class="sxs-lookup"><span data-stu-id="55249-130">-FilePath</span></span>

<span data-ttu-id="55249-131">Anger en fil som denna cmdlet sparar objektet i jokertecken tillåts, men måste matcha en enskild fil.</span><span class="sxs-lookup"><span data-stu-id="55249-131">Specifies a file that this cmdlet saves the object to Wildcard characters are permitted, but must resolve to a single file.</span></span>

```yaml
Type: System.String
Parameter Sets: File
Aliases: Path

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="55249-132">– InputObject</span><span class="sxs-lookup"><span data-stu-id="55249-132">-InputObject</span></span>

<span data-ttu-id="55249-133">Anger det objekt som ska sparas och visas.</span><span class="sxs-lookup"><span data-stu-id="55249-133">Specifies the object to be saved and displayed.</span></span> <span data-ttu-id="55249-134">Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten.</span><span class="sxs-lookup"><span data-stu-id="55249-134">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span> <span data-ttu-id="55249-135">Du kan också skicka ett objekt till `Tee-Object` .</span><span class="sxs-lookup"><span data-stu-id="55249-135">You can also pipe an object to `Tee-Object`.</span></span>

<span data-ttu-id="55249-136">När du använder parametern **InputObject** i `Tee-Object` , i stället för att skicka kommando resultat till `Tee-Object` , behandlas **InputObject** -värdet som ett enskilt objekt, även om värdet är en samling.</span><span class="sxs-lookup"><span data-stu-id="55249-136">When you use the **InputObject** parameter with `Tee-Object`, instead of piping command results to `Tee-Object`, the **InputObject** value is treated as a single object even if the value is a collection.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="55249-137">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="55249-137">-LiteralPath</span></span>

<span data-ttu-id="55249-138">Anger en fil som denna cmdlet sparar objektet i.</span><span class="sxs-lookup"><span data-stu-id="55249-138">Specifies a file that this cmdlet saves the object to.</span></span> <span data-ttu-id="55249-139">Till skillnad från **sökväg**, används värdet för parametern **LiteralPath** exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="55249-139">Unlike **FilePath**, the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="55249-140">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="55249-140">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="55249-141">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="55249-141">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="55249-142">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="55249-142">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: LiteralFile
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="55249-143">– Variabel</span><span class="sxs-lookup"><span data-stu-id="55249-143">-Variable</span></span>

<span data-ttu-id="55249-144">Anger en variabel som cmdleten sparar objektet i.</span><span class="sxs-lookup"><span data-stu-id="55249-144">Specifies a variable that the cmdlet saves the object to.</span></span> <span data-ttu-id="55249-145">Ange ett variabel namn utan föregående dollar tecken ( `$` ).</span><span class="sxs-lookup"><span data-stu-id="55249-145">Enter a variable name without the preceding dollar sign (`$`).</span></span>

```yaml
Type: System.String
Parameter Sets: Variable
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="55249-146">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="55249-146">CommonParameters</span></span>

<span data-ttu-id="55249-147">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="55249-147">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="55249-148">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="55249-148">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="55249-149">INDATA</span><span class="sxs-lookup"><span data-stu-id="55249-149">INPUTS</span></span>

### <span data-ttu-id="55249-150">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="55249-150">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="55249-151">Du kan skicka pipe-objekt till `Tee-Object` .</span><span class="sxs-lookup"><span data-stu-id="55249-151">You can pipe objects to `Tee-Object`.</span></span>

## <span data-ttu-id="55249-152">UTDATA</span><span class="sxs-lookup"><span data-stu-id="55249-152">OUTPUTS</span></span>

### <span data-ttu-id="55249-153">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="55249-153">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="55249-154">`Tee-Object` Returnerar det objekt som omdirigeras.</span><span class="sxs-lookup"><span data-stu-id="55249-154">`Tee-Object` returns the object that it redirects.</span></span>

## <span data-ttu-id="55249-155">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="55249-155">NOTES</span></span>

<span data-ttu-id="55249-156">Du kan också använda `Out-File` cmdleten eller omdirigerings operatorn, som båda sparar utdata i en fil, men som inte skickar den till pipelinen.</span><span class="sxs-lookup"><span data-stu-id="55249-156">You can also use the `Out-File` cmdlet or the redirection operator, both of which save the output in a file but do not send it down the pipeline.</span></span>

<span data-ttu-id="55249-157">Från och med PowerShell 6 `Tee-Object` använder BOM-mindre UTF-8-kodning när den skriver till filer.</span><span class="sxs-lookup"><span data-stu-id="55249-157">Beginning in PowerShell 6, `Tee-Object` uses BOM-less UTF-8 encoding when it writes to files.</span></span> <span data-ttu-id="55249-158">Om du behöver en annan kodning använder du `Out-File` cmdleten med parametern **encoding** .</span><span class="sxs-lookup"><span data-stu-id="55249-158">If you need a different encoding, use the `Out-File` cmdlet with the **Encoding** parameter.</span></span>

## <span data-ttu-id="55249-159">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="55249-159">RELATED LINKS</span></span>

[<span data-ttu-id="55249-160">Jämför objekt</span><span class="sxs-lookup"><span data-stu-id="55249-160">Compare-Object</span></span>](Compare-Object.md)

[<span data-ttu-id="55249-161">-Objekt</span><span class="sxs-lookup"><span data-stu-id="55249-161">ForEach-Object</span></span>](../Microsoft.PowerShell.Core/ForEach-Object.md)

[<span data-ttu-id="55249-162">Gruppera objekt</span><span class="sxs-lookup"><span data-stu-id="55249-162">Group-Object</span></span>](Group-Object.md)

[<span data-ttu-id="55249-163">Mått – objekt</span><span class="sxs-lookup"><span data-stu-id="55249-163">Measure-Object</span></span>](Measure-Object.md)

[<span data-ttu-id="55249-164">Nytt – objekt</span><span class="sxs-lookup"><span data-stu-id="55249-164">New-Object</span></span>](New-Object.md)

[<span data-ttu-id="55249-165">Select-Object</span><span class="sxs-lookup"><span data-stu-id="55249-165">Select-Object</span></span>](Select-Object.md)

[<span data-ttu-id="55249-166">Sortera objekt</span><span class="sxs-lookup"><span data-stu-id="55249-166">Sort-Object</span></span>](Sort-Object.md)

[<span data-ttu-id="55249-167">Where-objekt</span><span class="sxs-lookup"><span data-stu-id="55249-167">Where-Object</span></span>](../Microsoft.PowerShell.Core/Where-Object.md)

[<span data-ttu-id="55249-168">about_Redirection</span><span class="sxs-lookup"><span data-stu-id="55249-168">about_Redirection</span></span>](../Microsoft.PowerShell.Core/About/about_Redirection.md)

