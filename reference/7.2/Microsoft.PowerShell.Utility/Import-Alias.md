---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-alias?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-Alias
ms.openlocfilehash: 20bc5d141b68cab19374afbe44b3472c72bf69bc
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708627"
---
# <span data-ttu-id="e1090-102">Import-Alias</span><span class="sxs-lookup"><span data-stu-id="e1090-102">Import-Alias</span></span>

## <span data-ttu-id="e1090-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="e1090-103">SYNOPSIS</span></span>
<span data-ttu-id="e1090-104">Importerar en aliasresurspost från en fil.</span><span class="sxs-lookup"><span data-stu-id="e1090-104">Imports an alias list from a file.</span></span>

## <span data-ttu-id="e1090-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e1090-105">SYNTAX</span></span>

### <span data-ttu-id="e1090-106">ByPath (standard)</span><span class="sxs-lookup"><span data-stu-id="e1090-106">ByPath (Default)</span></span>

```
Import-Alias [-Path] <String> [-Scope <String>] [-PassThru] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="e1090-107">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="e1090-107">ByLiteralPath</span></span>

```
Import-Alias -LiteralPath <String> [-Scope <String>] [-PassThru] [-Force] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="e1090-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="e1090-108">DESCRIPTION</span></span>

<span data-ttu-id="e1090-109">`Import-Alias`Cmdleten importerar en lista med alias från en fil.</span><span class="sxs-lookup"><span data-stu-id="e1090-109">The `Import-Alias` cmdlet imports an alias list from a file.</span></span>

<span data-ttu-id="e1090-110">Från och med Windows PowerShell 3,0, som en säkerhetsfunktion, `Import-Alias` skriver inte befintliga alias över som standard.</span><span class="sxs-lookup"><span data-stu-id="e1090-110">Beginning in Windows PowerShell 3.0, as a security feature, `Import-Alias` does not overwrite existing aliases by default.</span></span>
<span data-ttu-id="e1090-111">Om du vill skriva över ett befintligt alias, när du har bevarat att innehållet i Ali Aset är säkert, använder du parametern **Force** .</span><span class="sxs-lookup"><span data-stu-id="e1090-111">To overwrite an existing alias, after assuring that the contents of the alias file is safe, use the **Force** parameter.</span></span>

## <span data-ttu-id="e1090-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="e1090-112">EXAMPLES</span></span>

### <span data-ttu-id="e1090-113">Exempel 1: importera alias från en fil</span><span class="sxs-lookup"><span data-stu-id="e1090-113">Example 1: Import aliases from a file</span></span>

```powershell
Import-Alias test.txt
```

<span data-ttu-id="e1090-114">Det här kommandot importerar Ali Aset information från en fil med namnet test.txt.</span><span class="sxs-lookup"><span data-stu-id="e1090-114">This command imports alias information from a file named test.txt.</span></span>

## <span data-ttu-id="e1090-115">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="e1090-115">PARAMETERS</span></span>

### <span data-ttu-id="e1090-116">-Force</span><span class="sxs-lookup"><span data-stu-id="e1090-116">-Force</span></span>

<span data-ttu-id="e1090-117">Tillåter att cmdleten importerar ett alias som redan har definierats eller är skrivskyddat.</span><span class="sxs-lookup"><span data-stu-id="e1090-117">Allows the cmdlet to import an alias that is already defined or is read only.</span></span>
<span data-ttu-id="e1090-118">Du kan använda följande kommando för att visa information om de för närvarande definierade aliasen:</span><span class="sxs-lookup"><span data-stu-id="e1090-118">You can use the following command to display information about the currently-defined aliases:</span></span>

`Get-Alias | Select-Object Name, Options`

<span data-ttu-id="e1090-119">Om motsvarande alias är skrivskyddat visas det i värdet för egenskapen **Options** .</span><span class="sxs-lookup"><span data-stu-id="e1090-119">If the corresponding alias is read-only, it will be displayed in the value of the **Options** property.</span></span>

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

### <span data-ttu-id="e1090-120">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="e1090-120">-LiteralPath</span></span>

<span data-ttu-id="e1090-121">Anger sökvägen till en fil som innehåller information om exporterat alias.</span><span class="sxs-lookup"><span data-stu-id="e1090-121">Specifies the path to a file that includes exported alias information.</span></span>
<span data-ttu-id="e1090-122">Till skillnad från parametern **Path** används värdet för parametern **LiteralPath** exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="e1090-122">Unlike the **Path** parameter, the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span>
<span data-ttu-id="e1090-123">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="e1090-123">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="e1090-124">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="e1090-124">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="e1090-125">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="e1090-125">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="e1090-126">– PassThru</span><span class="sxs-lookup"><span data-stu-id="e1090-126">-PassThru</span></span>

<span data-ttu-id="e1090-127">Returnerar ett objekt som representerar det objekt som du arbetar med.</span><span class="sxs-lookup"><span data-stu-id="e1090-127">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="e1090-128">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="e1090-128">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="e1090-129">-Path</span><span class="sxs-lookup"><span data-stu-id="e1090-129">-Path</span></span>

<span data-ttu-id="e1090-130">Anger sökvägen till en fil som innehåller information om exporterat alias.</span><span class="sxs-lookup"><span data-stu-id="e1090-130">Specifies the path to a file that includes exported alias information.</span></span>
<span data-ttu-id="e1090-131">Jokertecken tillåts, men de måste matcha ett enda namn.</span><span class="sxs-lookup"><span data-stu-id="e1090-131">Wildcards are allowed but they must resolve to a single name.</span></span>

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

### <span data-ttu-id="e1090-132">– Omfattning</span><span class="sxs-lookup"><span data-stu-id="e1090-132">-Scope</span></span>

<span data-ttu-id="e1090-133">Anger omfattningen som aliasen importeras till.</span><span class="sxs-lookup"><span data-stu-id="e1090-133">Specifies the scope into which the aliases are imported.</span></span>
<span data-ttu-id="e1090-134">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="e1090-134">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="e1090-135">Global</span><span class="sxs-lookup"><span data-stu-id="e1090-135">Global</span></span>
- <span data-ttu-id="e1090-136">Lokal</span><span class="sxs-lookup"><span data-stu-id="e1090-136">Local</span></span>
- <span data-ttu-id="e1090-137">Skript</span><span class="sxs-lookup"><span data-stu-id="e1090-137">Script</span></span>
- <span data-ttu-id="e1090-138">Ett tal i förhållande till det aktuella omfånget (0 till antalet omfattningar, där 0 är det aktuella omfånget och 1 är överordnat)</span><span class="sxs-lookup"><span data-stu-id="e1090-138">A number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent)</span></span>

<span data-ttu-id="e1090-139">Standardvärdet är Local.</span><span class="sxs-lookup"><span data-stu-id="e1090-139">The default is Local.</span></span>
<span data-ttu-id="e1090-140">Mer information finns i about_Scopes.</span><span class="sxs-lookup"><span data-stu-id="e1090-140">For more information, see about_Scopes.</span></span>

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

### <span data-ttu-id="e1090-141">-Confirm</span><span class="sxs-lookup"><span data-stu-id="e1090-141">-Confirm</span></span>

<span data-ttu-id="e1090-142">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="e1090-142">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="e1090-143">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="e1090-143">-WhatIf</span></span>

<span data-ttu-id="e1090-144">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="e1090-144">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="e1090-145">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="e1090-145">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="e1090-146">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e1090-146">CommonParameters</span></span>

<span data-ttu-id="e1090-147">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e1090-147">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e1090-148">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="e1090-148">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e1090-149">INDATA</span><span class="sxs-lookup"><span data-stu-id="e1090-149">INPUTS</span></span>

### <span data-ttu-id="e1090-150">System. String</span><span class="sxs-lookup"><span data-stu-id="e1090-150">System.String</span></span>

<span data-ttu-id="e1090-151">Du kan skicka vidare en sträng som innehåller en sökväg till `Import-Alias` .</span><span class="sxs-lookup"><span data-stu-id="e1090-151">You can pipe a string that contains a path to `Import-Alias`.</span></span>

## <span data-ttu-id="e1090-152">UTDATA</span><span class="sxs-lookup"><span data-stu-id="e1090-152">OUTPUTS</span></span>

### <span data-ttu-id="e1090-153">Ingen eller system. Management. Automation. AliasInfo</span><span class="sxs-lookup"><span data-stu-id="e1090-153">None or System.Management.Automation.AliasInfo</span></span>

<span data-ttu-id="e1090-154">När du använder parametern **Passthru** `Import-Alias` returneras ett objekt av **system. Management. Automation. AliasInfo** som representerar aliaset.</span><span class="sxs-lookup"><span data-stu-id="e1090-154">When you use the **Passthru** parameter, `Import-Alias` returns a **System.Management.Automation.AliasInfo** object that represents the alias.</span></span>
<span data-ttu-id="e1090-155">Annars genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="e1090-155">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="e1090-156">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="e1090-156">NOTES</span></span>

## <span data-ttu-id="e1090-157">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="e1090-157">RELATED LINKS</span></span>

[<span data-ttu-id="e1090-158">Exportera-alias</span><span class="sxs-lookup"><span data-stu-id="e1090-158">Export-Alias</span></span>](Export-Alias.md)

[<span data-ttu-id="e1090-159">Get-alias</span><span class="sxs-lookup"><span data-stu-id="e1090-159">Get-Alias</span></span>](Get-Alias.md)

[<span data-ttu-id="e1090-160">Nytt-alias</span><span class="sxs-lookup"><span data-stu-id="e1090-160">New-Alias</span></span>](New-Alias.md)

[<span data-ttu-id="e1090-161">Set-alias</span><span class="sxs-lookup"><span data-stu-id="e1090-161">Set-Alias</span></span>](Set-Alias.md)

