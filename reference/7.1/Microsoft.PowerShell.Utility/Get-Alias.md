---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-alias?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Alias
ms.openlocfilehash: e0a08a4ee6f00702f765bc359a20bf9e30b9b1c5
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264411"
---
# <span data-ttu-id="5fc09-103">Get-Alias</span><span class="sxs-lookup"><span data-stu-id="5fc09-103">Get-Alias</span></span>

## <span data-ttu-id="5fc09-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="5fc09-104">SYNOPSIS</span></span>
<span data-ttu-id="5fc09-105">Hämtar alias för den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="5fc09-105">Gets the aliases for the current session.</span></span>

## <span data-ttu-id="5fc09-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="5fc09-106">SYNTAX</span></span>

### <span data-ttu-id="5fc09-107">Standard (standard)</span><span class="sxs-lookup"><span data-stu-id="5fc09-107">Default (Default)</span></span>

```
Get-Alias [[-Name] <String[]>] [-Exclude <String[]>] [-Scope <String>] [<CommonParameters>]
```

### <span data-ttu-id="5fc09-108">Definition</span><span class="sxs-lookup"><span data-stu-id="5fc09-108">Definition</span></span>

```
Get-Alias [-Exclude <String[]>] [-Scope <String>] [-Definition <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="5fc09-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="5fc09-109">DESCRIPTION</span></span>

<span data-ttu-id="5fc09-110">Cmdleten **Get-alias** hämtar alias i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="5fc09-110">The **Get-Alias** cmdlet gets the aliases in the current session.</span></span>
<span data-ttu-id="5fc09-111">Detta inkluderar inbyggda alias, alias som du har angett eller importerat och alias som du har lagt till i din PowerShell-profil.</span><span class="sxs-lookup"><span data-stu-id="5fc09-111">This includes built-in aliases, aliases that you have set or imported, and aliases that you have added to your PowerShell profile.</span></span>

<span data-ttu-id="5fc09-112">**Get-alias** tar som standard ett alias och returnerar kommando namnet.</span><span class="sxs-lookup"><span data-stu-id="5fc09-112">By default, **Get-Alias** takes an alias and returns the command name.</span></span>
<span data-ttu-id="5fc09-113">När du använder *definitions* parametern tar **Get-alias** ett kommando namn och returnerar dess alias.</span><span class="sxs-lookup"><span data-stu-id="5fc09-113">When you use the *Definition* parameter, **Get-Alias** takes a command name and returns its aliases.</span></span>

<span data-ttu-id="5fc09-114">Från och med Windows PowerShell 3,0 visar **Get-alias** icke-avstavade aliasnamn i ett `<alias> -> <definition>` format för att göra det ännu enklare att hitta den information som du behöver.</span><span class="sxs-lookup"><span data-stu-id="5fc09-114">Beginning in Windows PowerShell 3.0, **Get-Alias** displays non-hyphenated alias names in an `<alias> -> <definition>` format to make it even easier to find the information that you need.</span></span>

## <span data-ttu-id="5fc09-115">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="5fc09-115">EXAMPLES</span></span>

### <span data-ttu-id="5fc09-116">Exempel 1: Hämta alla alias i den aktuella sessionen</span><span class="sxs-lookup"><span data-stu-id="5fc09-116">Example 1: Get all aliases in the current session</span></span>

```
PS C:\> Get-Alias

CommandType     Name
-----------     ----
Alias           % -> ForEach-Object
Alias           ? -> Where-Object
Alias           ac -> Add-Content
Alias           asnp -> Add-PSSnapin
Alias           cat -> Get-Content
Alias           cd -> Set-Location
Alias           chdir -> Set-Location
Alias           clc -> Clear-Content
Alias           clear -> Clear-Host
Alias           clhy -> Clear-History
...
```

<span data-ttu-id="5fc09-117">Det här kommandot hämtar alla alias i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="5fc09-117">This command gets all aliases in the current session.</span></span>

<span data-ttu-id="5fc09-118">Utdata visar det `<alias> -> <definition>` format som introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="5fc09-118">The output shows the `<alias> -> <definition>` format that was introduced in Windows PowerShell 3.0.</span></span>
<span data-ttu-id="5fc09-119">Det här formatet används endast för alias som inte innehåller bindestreck, eftersom alias med bindestreck är vanligt vis önskade namn för cmdlets och functions, i stället för smek namn.</span><span class="sxs-lookup"><span data-stu-id="5fc09-119">This format is used only for aliases that do not include hyphens, because aliases with hyphens are typically preferred names for cmdlets and functions, rather than nicknames.</span></span>

### <span data-ttu-id="5fc09-120">Exempel 2: Hämta alias efter namn</span><span class="sxs-lookup"><span data-stu-id="5fc09-120">Example 2: Get aliases by name</span></span>

```powershell
Get-Alias -Name gp*, sp* -Exclude *ps
```

<span data-ttu-id="5fc09-121">Det här kommandot hämtar alla alias som börjar med GP eller SP, förutom alias som slutar med PS.</span><span class="sxs-lookup"><span data-stu-id="5fc09-121">This command gets all aliases that begin with gp or sp, except for aliases that end with ps.</span></span>

### <span data-ttu-id="5fc09-122">Exempel 3: Hämta alias för en cmdlet</span><span class="sxs-lookup"><span data-stu-id="5fc09-122">Example 3: Get aliases for a cmdlet</span></span>

```powershell
Get-Alias -Definition Get-ChildItem
```

<span data-ttu-id="5fc09-123">Det här kommandot hämtar aliasen för Get-ChildItem-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="5fc09-123">This command gets the aliases for the Get-ChildItem cmdlet.</span></span>

<span data-ttu-id="5fc09-124">Som standard hämtar cmdleten **Get-alias** objekt namnet när du känner till aliaset.</span><span class="sxs-lookup"><span data-stu-id="5fc09-124">By default, the **Get-Alias** cmdlet gets the item name when you know the alias.</span></span>
<span data-ttu-id="5fc09-125">*Definitions* parametern hämtar aliaset när du känner till objekt namnet.</span><span class="sxs-lookup"><span data-stu-id="5fc09-125">The *Definition* parameter gets the alias when you know the item name.</span></span>

### <span data-ttu-id="5fc09-126">Exempel 4: Hämta alias efter egenskap</span><span class="sxs-lookup"><span data-stu-id="5fc09-126">Example 4: Get aliases by property</span></span>

```powershell
Get-Alias | Where-Object {$_.Options -Match "ReadOnly"}
```

<span data-ttu-id="5fc09-127">Det här kommandot hämtar alla alias där värdet för egenskapen Options är ReadOnly.</span><span class="sxs-lookup"><span data-stu-id="5fc09-127">This command gets all aliases in which the value of the Options property is ReadOnly.</span></span>
<span data-ttu-id="5fc09-128">Det här kommandot är ett snabbt sätt att hitta de alias som är inbyggda i PowerShell, eftersom de har alternativet ReadOnly.</span><span class="sxs-lookup"><span data-stu-id="5fc09-128">This command provides a quick way to find the aliases that are built into PowerShell, because they have the ReadOnly option.</span></span>

<span data-ttu-id="5fc09-129">Alternativen är bara en egenskap hos de AliasInfo-objekt som **Get-alias** hämtar.</span><span class="sxs-lookup"><span data-stu-id="5fc09-129">Options is just one property of the AliasInfo objects that **Get-Alias** gets.</span></span>
<span data-ttu-id="5fc09-130">Om du vill hitta alla egenskaper och metoder för AliasInfo-objekt skriver du `Get-Alias | get-member` .</span><span class="sxs-lookup"><span data-stu-id="5fc09-130">To find all properties and methods of AliasInfo objects, type `Get-Alias | get-member`.</span></span>

### <span data-ttu-id="5fc09-131">Exempel 5: Hämta alias efter namn och filtrera efter start bokstav</span><span class="sxs-lookup"><span data-stu-id="5fc09-131">Example 5: Get aliases by name and filter by beginning letter</span></span>

```powershell
Get-Alias -Definition "*-PSSession" -Exclude e* -Scope Global
```

<span data-ttu-id="5fc09-132">Det här exemplet hämtar alias för kommandon som har namn som slutar med "-PSSession", förutom de som börjar med "e".</span><span class="sxs-lookup"><span data-stu-id="5fc09-132">This example gets aliases for commands that have names that end in "-PSSession", except for those that begin with "e".</span></span>

<span data-ttu-id="5fc09-133">Kommandot använder *omfattnings* parametern för att tillämpa kommandot i det globala omfånget.</span><span class="sxs-lookup"><span data-stu-id="5fc09-133">The command uses the *Scope* parameter to apply the command in the global scope.</span></span>
<span data-ttu-id="5fc09-134">Detta är användbart i skript när du vill hämta alias i sessionen.</span><span class="sxs-lookup"><span data-stu-id="5fc09-134">This is useful in scripts when you want to get the aliases in the session.</span></span>

## <span data-ttu-id="5fc09-135">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="5fc09-135">PARAMETERS</span></span>

### <span data-ttu-id="5fc09-136">-Definition</span><span class="sxs-lookup"><span data-stu-id="5fc09-136">-Definition</span></span>

<span data-ttu-id="5fc09-137">Hämtar alias för det angivna objektet.</span><span class="sxs-lookup"><span data-stu-id="5fc09-137">Gets the aliases for the specified item.</span></span>
<span data-ttu-id="5fc09-138">Ange namnet på en cmdlet, funktion, skript, fil eller körbar fil.</span><span class="sxs-lookup"><span data-stu-id="5fc09-138">Enter the name of a cmdlet, function, script, file, or executable file.</span></span>

<span data-ttu-id="5fc09-139">Den här parametern heter *definition* , eftersom den söker efter objekt namnet i egenskapen definition i objektet alias.</span><span class="sxs-lookup"><span data-stu-id="5fc09-139">This parameter is called *Definition* , because it searches for the item name in the Definition property of the alias object.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Definition
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="5fc09-140">-Undanta</span><span class="sxs-lookup"><span data-stu-id="5fc09-140">-Exclude</span></span>

<span data-ttu-id="5fc09-141">Utesluter de angivna objekten.</span><span class="sxs-lookup"><span data-stu-id="5fc09-141">Omits the specified items.</span></span>
<span data-ttu-id="5fc09-142">Värdet för den här parametern kvalificerar namn-och definitions parametrarna.</span><span class="sxs-lookup"><span data-stu-id="5fc09-142">The value of this parameter qualifies the Name and Definition parameters.</span></span>
<span data-ttu-id="5fc09-143">Ange ett namn, en definition eller ett mönster, till exempel "s \*".</span><span class="sxs-lookup"><span data-stu-id="5fc09-143">Enter a name, a definition, or a pattern, such as "s\*".</span></span>
<span data-ttu-id="5fc09-144">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="5fc09-144">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="5fc09-145">-Name</span><span class="sxs-lookup"><span data-stu-id="5fc09-145">-Name</span></span>

<span data-ttu-id="5fc09-146">Anger de alias som denna cmdlet hämtar.</span><span class="sxs-lookup"><span data-stu-id="5fc09-146">Specifies the aliases that this cmdlet gets.</span></span>
<span data-ttu-id="5fc09-147">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="5fc09-147">Wildcards are permitted.</span></span>
<span data-ttu-id="5fc09-148">Som standard `Get-Alias` hämtar alla alias som definierats för den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="5fc09-148">By default, `Get-Alias` retrieves all aliases defined for the current session.</span></span>
<span data-ttu-id="5fc09-149">Parameter namnets **namn** är valfritt.</span><span class="sxs-lookup"><span data-stu-id="5fc09-149">The parameter name **Name** is optional.</span></span>
<span data-ttu-id="5fc09-150">Du kan också skicka namn på alias till `Get-Alias` .</span><span class="sxs-lookup"><span data-stu-id="5fc09-150">You can also pipe alias names to `Get-Alias`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases:

Required: False
Position: 0
Default value: All aliases
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="5fc09-151">– Omfattning</span><span class="sxs-lookup"><span data-stu-id="5fc09-151">-Scope</span></span>

<span data-ttu-id="5fc09-152">Anger omfattningen som denna cmdlet hämtar alias för.</span><span class="sxs-lookup"><span data-stu-id="5fc09-152">Specifies the scope for which this cmdlet gets aliases.</span></span>
<span data-ttu-id="5fc09-153">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="5fc09-153">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="5fc09-154">Global</span><span class="sxs-lookup"><span data-stu-id="5fc09-154">Global</span></span>
- <span data-ttu-id="5fc09-155">Lokal</span><span class="sxs-lookup"><span data-stu-id="5fc09-155">Local</span></span>
- <span data-ttu-id="5fc09-156">Skript</span><span class="sxs-lookup"><span data-stu-id="5fc09-156">Script</span></span>
- <span data-ttu-id="5fc09-157">Ett tal i förhållande till det aktuella omfånget (0 till antalet omfattningar, där 0 är det aktuella omfånget och 1 är överordnat)</span><span class="sxs-lookup"><span data-stu-id="5fc09-157">A number relative to the current scope (0 through the number of scopes, where 0 is the current scope and 1 is its parent)</span></span>

<span data-ttu-id="5fc09-158">Lokalt är standard.</span><span class="sxs-lookup"><span data-stu-id="5fc09-158">Local is the default.</span></span>
<span data-ttu-id="5fc09-159">Mer information finns i about_Scopes.</span><span class="sxs-lookup"><span data-stu-id="5fc09-159">For more information, see about_Scopes.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Local
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5fc09-160">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5fc09-160">CommonParameters</span></span>

<span data-ttu-id="5fc09-161">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="5fc09-161">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5fc09-162">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="5fc09-162">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5fc09-163">INDATA</span><span class="sxs-lookup"><span data-stu-id="5fc09-163">INPUTS</span></span>

### <span data-ttu-id="5fc09-164">System. String</span><span class="sxs-lookup"><span data-stu-id="5fc09-164">System.String</span></span>

<span data-ttu-id="5fc09-165">Du kan hämta alias för att **Hämta alias**.</span><span class="sxs-lookup"><span data-stu-id="5fc09-165">You can pipe alias names to **Get-Alias**.</span></span>

## <span data-ttu-id="5fc09-166">UTDATA</span><span class="sxs-lookup"><span data-stu-id="5fc09-166">OUTPUTS</span></span>

### <span data-ttu-id="5fc09-167">System. Management. Automation. AliasInfo</span><span class="sxs-lookup"><span data-stu-id="5fc09-167">System.Management.Automation.AliasInfo</span></span>

<span data-ttu-id="5fc09-168">**Get-alias** returnerar ett objekt som representerar varje alias.</span><span class="sxs-lookup"><span data-stu-id="5fc09-168">**Get-Alias** returns an object that represents each alias.</span></span>
<span data-ttu-id="5fc09-169">**Get-alias** returnerar samma objekt för varje alias, men PowerShell använder ett pil-baserat format för att visa namnen på icke-avstavade alias.</span><span class="sxs-lookup"><span data-stu-id="5fc09-169">**Get-Alias** returns the same object for every alias, but PowerShell uses an arrow-based format to display the names of non-hyphenated aliases.</span></span>

## <span data-ttu-id="5fc09-170">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="5fc09-170">NOTES</span></span>

- <span data-ttu-id="5fc09-171">Om du vill skapa ett nytt alias använder Set-Alias eller New-alias.</span><span class="sxs-lookup"><span data-stu-id="5fc09-171">To create a new alias, use Set-Alias or New-Alias.</span></span> <span data-ttu-id="5fc09-172">Använd Remove-Item om du vill ta bort ett alias.</span><span class="sxs-lookup"><span data-stu-id="5fc09-172">To delete an alias, use Remove-Item.</span></span>
- <span data-ttu-id="5fc09-173">Formatet för den pilbaserade aliaset används inte för alias som innehåller bindestreck.</span><span class="sxs-lookup"><span data-stu-id="5fc09-173">The arrow-based alias name format is not used for aliases that include a hyphen.</span></span> <span data-ttu-id="5fc09-174">Detta är sannolikt att föredra ersättnings namn för cmdlets och functions, i stället för vanliga förkortningar eller smek namn.</span><span class="sxs-lookup"><span data-stu-id="5fc09-174">These are likely to be preferred substitute names for cmdlets and functions, instead of typical abbreviations or nicknames.</span></span>

## <span data-ttu-id="5fc09-175">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="5fc09-175">RELATED LINKS</span></span>

[<span data-ttu-id="5fc09-176">Exportera-alias</span><span class="sxs-lookup"><span data-stu-id="5fc09-176">Export-Alias</span></span>](Export-Alias.md)

[<span data-ttu-id="5fc09-177">Importera-alias</span><span class="sxs-lookup"><span data-stu-id="5fc09-177">Import-Alias</span></span>](Import-Alias.md)

[<span data-ttu-id="5fc09-178">Nytt-alias</span><span class="sxs-lookup"><span data-stu-id="5fc09-178">New-Alias</span></span>](New-Alias.md)

[<span data-ttu-id="5fc09-179">Set-alias</span><span class="sxs-lookup"><span data-stu-id="5fc09-179">Set-Alias</span></span>](Set-Alias.md)

[<span data-ttu-id="5fc09-180">Aliasresurspost</span><span class="sxs-lookup"><span data-stu-id="5fc09-180">Alias Provider</span></span>](../Microsoft.PowerShell.Core/About/about_Alias_Provider.md)

[<span data-ttu-id="5fc09-181">about_Aliases</span><span class="sxs-lookup"><span data-stu-id="5fc09-181">about_Aliases</span></span>](../Microsoft.PowerShell.Core/About/about_Aliases.md)

