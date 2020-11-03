---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-alias?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-Alias
ms.openlocfilehash: 67bcb45ec9e23ba9d4f4ae38d378d2c48180666b
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93263181"
---
# <span data-ttu-id="950ae-103">Import-Alias</span><span class="sxs-lookup"><span data-stu-id="950ae-103">Import-Alias</span></span>

## <span data-ttu-id="950ae-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="950ae-104">SYNOPSIS</span></span>
<span data-ttu-id="950ae-105">Importerar en aliasresurspost från en fil.</span><span class="sxs-lookup"><span data-stu-id="950ae-105">Imports an alias list from a file.</span></span>

## <span data-ttu-id="950ae-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="950ae-106">SYNTAX</span></span>

### <span data-ttu-id="950ae-107">ByPath (standard)</span><span class="sxs-lookup"><span data-stu-id="950ae-107">ByPath (Default)</span></span>

```
Import-Alias [-Path] <String> [-Scope <String>] [-PassThru] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="950ae-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="950ae-108">ByLiteralPath</span></span>

```
Import-Alias -LiteralPath <String> [-Scope <String>] [-PassThru] [-Force] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="950ae-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="950ae-109">DESCRIPTION</span></span>

<span data-ttu-id="950ae-110">`Import-Alias`Cmdleten importerar en lista med alias från en fil.</span><span class="sxs-lookup"><span data-stu-id="950ae-110">The `Import-Alias` cmdlet imports an alias list from a file.</span></span>

<span data-ttu-id="950ae-111">Från och med Windows PowerShell 3,0, som en säkerhetsfunktion, `Import-Alias` skriver inte befintliga alias över som standard.</span><span class="sxs-lookup"><span data-stu-id="950ae-111">Beginning in Windows PowerShell 3.0, as a security feature, `Import-Alias` does not overwrite existing aliases by default.</span></span>
<span data-ttu-id="950ae-112">Om du vill skriva över ett befintligt alias, när du har bevarat att innehållet i Ali Aset är säkert, använder du parametern **Force** .</span><span class="sxs-lookup"><span data-stu-id="950ae-112">To overwrite an existing alias, after assuring that the contents of the alias file is safe, use the **Force** parameter.</span></span>

## <span data-ttu-id="950ae-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="950ae-113">EXAMPLES</span></span>

### <span data-ttu-id="950ae-114">Exempel 1: importera alias från en fil</span><span class="sxs-lookup"><span data-stu-id="950ae-114">Example 1: Import aliases from a file</span></span>

```powershell
Import-Alias test.txt
```

<span data-ttu-id="950ae-115">Det här kommandot importerar Ali Aset information från en fil med namnet test.txt.</span><span class="sxs-lookup"><span data-stu-id="950ae-115">This command imports alias information from a file named test.txt.</span></span>

## <span data-ttu-id="950ae-116">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="950ae-116">PARAMETERS</span></span>

### <span data-ttu-id="950ae-117">-Force</span><span class="sxs-lookup"><span data-stu-id="950ae-117">-Force</span></span>

<span data-ttu-id="950ae-118">Tillåter att cmdleten importerar ett alias som redan har definierats eller är skrivskyddat.</span><span class="sxs-lookup"><span data-stu-id="950ae-118">Allows the cmdlet to import an alias that is already defined or is read only.</span></span>
<span data-ttu-id="950ae-119">Du kan använda följande kommando för att visa information om de för närvarande definierade aliasen:</span><span class="sxs-lookup"><span data-stu-id="950ae-119">You can use the following command to display information about the currently-defined aliases:</span></span>

`Get-Alias | Select-Object Name, Options`

<span data-ttu-id="950ae-120">Om motsvarande alias är skrivskyddat visas det i värdet för egenskapen **Options** .</span><span class="sxs-lookup"><span data-stu-id="950ae-120">If the corresponding alias is read-only, it will be displayed in the value of the **Options** property.</span></span>

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

### <span data-ttu-id="950ae-121">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="950ae-121">-LiteralPath</span></span>

<span data-ttu-id="950ae-122">Anger sökvägen till en fil som innehåller information om exporterat alias.</span><span class="sxs-lookup"><span data-stu-id="950ae-122">Specifies the path to a file that includes exported alias information.</span></span>
<span data-ttu-id="950ae-123">Till skillnad från parametern **Path** används värdet för parametern **LiteralPath** exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="950ae-123">Unlike the **Path** parameter, the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span>
<span data-ttu-id="950ae-124">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="950ae-124">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="950ae-125">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="950ae-125">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="950ae-126">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="950ae-126">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="950ae-127">– PassThru</span><span class="sxs-lookup"><span data-stu-id="950ae-127">-PassThru</span></span>

<span data-ttu-id="950ae-128">Returnerar ett objekt som representerar det objekt som du arbetar med.</span><span class="sxs-lookup"><span data-stu-id="950ae-128">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="950ae-129">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="950ae-129">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="950ae-130">-Path</span><span class="sxs-lookup"><span data-stu-id="950ae-130">-Path</span></span>

<span data-ttu-id="950ae-131">Anger sökvägen till en fil som innehåller information om exporterat alias.</span><span class="sxs-lookup"><span data-stu-id="950ae-131">Specifies the path to a file that includes exported alias information.</span></span>
<span data-ttu-id="950ae-132">Jokertecken tillåts, men de måste matcha ett enda namn.</span><span class="sxs-lookup"><span data-stu-id="950ae-132">Wildcards are allowed but they must resolve to a single name.</span></span>

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="950ae-133">– Omfattning</span><span class="sxs-lookup"><span data-stu-id="950ae-133">-Scope</span></span>

<span data-ttu-id="950ae-134">Anger omfattningen som aliasen importeras till.</span><span class="sxs-lookup"><span data-stu-id="950ae-134">Specifies the scope into which the aliases are imported.</span></span>
<span data-ttu-id="950ae-135">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="950ae-135">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="950ae-136">Global</span><span class="sxs-lookup"><span data-stu-id="950ae-136">Global</span></span>
- <span data-ttu-id="950ae-137">Lokal</span><span class="sxs-lookup"><span data-stu-id="950ae-137">Local</span></span>
- <span data-ttu-id="950ae-138">Skript</span><span class="sxs-lookup"><span data-stu-id="950ae-138">Script</span></span>
- <span data-ttu-id="950ae-139">Ett tal i förhållande till det aktuella omfånget (0 till antalet omfattningar, där 0 är det aktuella omfånget och 1 är överordnat)</span><span class="sxs-lookup"><span data-stu-id="950ae-139">A number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent)</span></span>

<span data-ttu-id="950ae-140">Standardvärdet är Local.</span><span class="sxs-lookup"><span data-stu-id="950ae-140">The default is Local.</span></span>
<span data-ttu-id="950ae-141">Mer information finns i about_Scopes.</span><span class="sxs-lookup"><span data-stu-id="950ae-141">For more information, see about_Scopes.</span></span>

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

### <span data-ttu-id="950ae-142">-Confirm</span><span class="sxs-lookup"><span data-stu-id="950ae-142">-Confirm</span></span>

<span data-ttu-id="950ae-143">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="950ae-143">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="950ae-144">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="950ae-144">-WhatIf</span></span>

<span data-ttu-id="950ae-145">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="950ae-145">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="950ae-146">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="950ae-146">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="950ae-147">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="950ae-147">CommonParameters</span></span>

<span data-ttu-id="950ae-148">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="950ae-148">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="950ae-149">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="950ae-149">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="950ae-150">INDATA</span><span class="sxs-lookup"><span data-stu-id="950ae-150">INPUTS</span></span>

### <span data-ttu-id="950ae-151">System. String</span><span class="sxs-lookup"><span data-stu-id="950ae-151">System.String</span></span>

<span data-ttu-id="950ae-152">Du kan skicka vidare en sträng som innehåller en sökväg till `Import-Alias` .</span><span class="sxs-lookup"><span data-stu-id="950ae-152">You can pipe a string that contains a path to `Import-Alias`.</span></span>

## <span data-ttu-id="950ae-153">UTDATA</span><span class="sxs-lookup"><span data-stu-id="950ae-153">OUTPUTS</span></span>

### <span data-ttu-id="950ae-154">Ingen eller system. Management. Automation. AliasInfo</span><span class="sxs-lookup"><span data-stu-id="950ae-154">None or System.Management.Automation.AliasInfo</span></span>

<span data-ttu-id="950ae-155">När du använder parametern **Passthru** `Import-Alias` returneras ett objekt av **system. Management. Automation. AliasInfo** som representerar aliaset.</span><span class="sxs-lookup"><span data-stu-id="950ae-155">When you use the **Passthru** parameter, `Import-Alias` returns a **System.Management.Automation.AliasInfo** object that represents the alias.</span></span>
<span data-ttu-id="950ae-156">Annars genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="950ae-156">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="950ae-157">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="950ae-157">NOTES</span></span>

## <span data-ttu-id="950ae-158">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="950ae-158">RELATED LINKS</span></span>

[<span data-ttu-id="950ae-159">Exportera-alias</span><span class="sxs-lookup"><span data-stu-id="950ae-159">Export-Alias</span></span>](Export-Alias.md)

[<span data-ttu-id="950ae-160">Get-alias</span><span class="sxs-lookup"><span data-stu-id="950ae-160">Get-Alias</span></span>](Get-Alias.md)

[<span data-ttu-id="950ae-161">Nytt-alias</span><span class="sxs-lookup"><span data-stu-id="950ae-161">New-Alias</span></span>](New-Alias.md)

[<span data-ttu-id="950ae-162">Set-alias</span><span class="sxs-lookup"><span data-stu-id="950ae-162">Set-Alias</span></span>](Set-Alias.md)