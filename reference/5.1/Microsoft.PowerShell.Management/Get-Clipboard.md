---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 09/21/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-clipboard?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Clipboard
ms.openlocfilehash: 2885b2624f8334e8699e0baea5fc41b3f025fe2a
ms.sourcegitcommit: d757d64ea8c8af4d92596e8fbe15f2f40d48d3ac
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/22/2020
ms.locfileid: "93269559"
---
# <span data-ttu-id="4ee74-103">Get-Clipboard</span><span class="sxs-lookup"><span data-stu-id="4ee74-103">Get-Clipboard</span></span>

## <span data-ttu-id="4ee74-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="4ee74-104">SYNOPSIS</span></span>
<span data-ttu-id="4ee74-105">Hämtar det aktuella urklipps posten i Windows.</span><span class="sxs-lookup"><span data-stu-id="4ee74-105">Gets the current Windows clipboard entry.</span></span>

## <span data-ttu-id="4ee74-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4ee74-106">SYNTAX</span></span>

```
Get-Clipboard [-Format <ClipboardFormat>] [-TextFormatType <TextDataFormat>] [-Raw] [<CommonParameters>]
```

## <span data-ttu-id="4ee74-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="4ee74-107">DESCRIPTION</span></span>

<span data-ttu-id="4ee74-108">`Get-Clipboard`Cmdleten hämtar det aktuella urklipps posten i Windows.</span><span class="sxs-lookup"><span data-stu-id="4ee74-108">The `Get-Clipboard` cmdlet gets the current Windows clipboard entry.</span></span> <span data-ttu-id="4ee74-109">Flera rader med text returneras som en sträng mat ris som liknar `Get-Content` .</span><span class="sxs-lookup"><span data-stu-id="4ee74-109">Multiple lines of text are returned as an array of strings similar to `Get-Content`.</span></span>

## <span data-ttu-id="4ee74-110">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="4ee74-110">EXAMPLES</span></span>

### <span data-ttu-id="4ee74-111">Exempel 1: hämta innehållet i Urklipp och visa det på kommando raden</span><span class="sxs-lookup"><span data-stu-id="4ee74-111">Example 1: Get the content of the clipboard and display it to the command-line</span></span>

<span data-ttu-id="4ee74-112">I det här exemplet har vi klickat på en bild i en webbläsare och valde **kopierings** åtgärden.</span><span class="sxs-lookup"><span data-stu-id="4ee74-112">In this example we have right-clicked on an image in a browser and chose the **Copy** action.</span></span> <span data-ttu-id="4ee74-113">Följande kommando visar länken, som en URL, för den bild som lagras i Urklipp.</span><span class="sxs-lookup"><span data-stu-id="4ee74-113">The following command displays the link, as a URL, of the image that is stored in the clipboard.</span></span>

```powershell
Get-Clipboard
```

```Output
https://en.wikipedia.org/wiki/PowerShell
```

### <span data-ttu-id="4ee74-114">Exempel 2: hämta innehållet i Urklipp i ett särskilt format</span><span class="sxs-lookup"><span data-stu-id="4ee74-114">Example 2: Get the content of the clipboard in a specific format</span></span>

<span data-ttu-id="4ee74-115">I det här exemplet kopierade filer till Urklipp i Windows Explorerby och trycker på <kbd>CTRL-C</kbd>.</span><span class="sxs-lookup"><span data-stu-id="4ee74-115">In this example we copied files to the clipboard in Windows Explorerby selecting them and pressing <kbd>Ctrl-C</kbd>.</span></span> <span data-ttu-id="4ee74-116">Med hjälp av följande kommando kan du komma åt innehållet i Urklipp som en lista över filer:</span><span class="sxs-lookup"><span data-stu-id="4ee74-116">Using the following command, you can access the contents of the clipboard as a list of files:</span></span>

```powershell
Get-Clipboard -Format FileDropList
```

```Output
    Directory: C:\Git\PS-Docs\PowerShell-Docs\wmf

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----         5/7/2019   1:11 PM          10010 TOC.yml
-a----       11/18/2016  10:10 AM             53 md.style
-a----         5/6/2019   9:32 AM           4177 overview.md
-a----        6/28/2018   2:28 PM            345 README.md
```

## <span data-ttu-id="4ee74-117">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="4ee74-117">PARAMETERS</span></span>

### <span data-ttu-id="4ee74-118">– Format</span><span class="sxs-lookup"><span data-stu-id="4ee74-118">-Format</span></span>

<span data-ttu-id="4ee74-119">Anger urklippets typ eller format.</span><span class="sxs-lookup"><span data-stu-id="4ee74-119">Specifies the type, or format, of the clipboard.</span></span> <span data-ttu-id="4ee74-120">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="4ee74-120">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="4ee74-121">Text</span><span class="sxs-lookup"><span data-stu-id="4ee74-121">Text</span></span>
- <span data-ttu-id="4ee74-122">FileDropList</span><span class="sxs-lookup"><span data-stu-id="4ee74-122">FileDropList</span></span>
- <span data-ttu-id="4ee74-123">Bild</span><span class="sxs-lookup"><span data-stu-id="4ee74-123">Image</span></span>
- <span data-ttu-id="4ee74-124">Ljud</span><span class="sxs-lookup"><span data-stu-id="4ee74-124">Audio</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ClipboardFormat
Parameter Sets: (All)
Aliases:
Accepted values: Text, FileDropList, Image, Audio

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4ee74-125">– RAW</span><span class="sxs-lookup"><span data-stu-id="4ee74-125">-Raw</span></span>

<span data-ttu-id="4ee74-126">Hämtar hela innehållet i Urklipp.</span><span class="sxs-lookup"><span data-stu-id="4ee74-126">Gets the entire contents of the clipboard.</span></span> <span data-ttu-id="4ee74-127">Flerradig text returneras som en enskild Multiline-sträng i stället för en sträng mat ris.</span><span class="sxs-lookup"><span data-stu-id="4ee74-127">Multiline text is returned as a single multiline string rather than an array of strings.</span></span>

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

### <span data-ttu-id="4ee74-128">-TextFormatType</span><span class="sxs-lookup"><span data-stu-id="4ee74-128">-TextFormatType</span></span>

<span data-ttu-id="4ee74-129">Anger typ av text data format för Urklipp.</span><span class="sxs-lookup"><span data-stu-id="4ee74-129">Specifies the text data format type of the clipboard.</span></span> <span data-ttu-id="4ee74-130">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="4ee74-130">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="4ee74-131">Text</span><span class="sxs-lookup"><span data-stu-id="4ee74-131">Text</span></span>
- <span data-ttu-id="4ee74-132">UnicodeText</span><span class="sxs-lookup"><span data-stu-id="4ee74-132">UnicodeText</span></span>
- <span data-ttu-id="4ee74-133">RTF</span><span class="sxs-lookup"><span data-stu-id="4ee74-133">Rtf</span></span>
- <span data-ttu-id="4ee74-134">Html</span><span class="sxs-lookup"><span data-stu-id="4ee74-134">Html</span></span>
- <span data-ttu-id="4ee74-135">CommaSeparatedValue</span><span class="sxs-lookup"><span data-stu-id="4ee74-135">CommaSeparatedValue</span></span>

```yaml
Type: System.Windows.Forms.TextDataFormat
Parameter Sets: (All)
Aliases:
Accepted values: Text, UnicodeText, Rtf, Html, CommaSeparatedValue

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4ee74-136">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4ee74-136">CommonParameters</span></span>

<span data-ttu-id="4ee74-137">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4ee74-137">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4ee74-138">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="4ee74-138">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4ee74-139">INDATA</span><span class="sxs-lookup"><span data-stu-id="4ee74-139">INPUTS</span></span>

## <span data-ttu-id="4ee74-140">UTDATA</span><span class="sxs-lookup"><span data-stu-id="4ee74-140">OUTPUTS</span></span>

### <span data-ttu-id="4ee74-141">System. String, system. IO. FileInfo, system. IO. Stream, system. Drawing. image</span><span class="sxs-lookup"><span data-stu-id="4ee74-141">System.String, System.IO.FileInfo, System.IO.Stream, System.Drawing.Image</span></span>

## <span data-ttu-id="4ee74-142">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="4ee74-142">NOTES</span></span>

## <span data-ttu-id="4ee74-143">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="4ee74-143">RELATED LINKS</span></span>

[<span data-ttu-id="4ee74-144">Ange Urklipp</span><span class="sxs-lookup"><span data-stu-id="4ee74-144">Set-Clipboard</span></span>](Set-Clipboard.md)
