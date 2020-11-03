---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/07/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-verb?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Verb
ms.openlocfilehash: a1459c276d8d6b2d031bc4b4f7ab521f7582a4cb
ms.sourcegitcommit: 7d052985c20761fdf4c6d7ce4e04df4c551c36a3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/11/2020
ms.locfileid: "93269163"
---
# <span data-ttu-id="36714-103">Get-Verb</span><span class="sxs-lookup"><span data-stu-id="36714-103">Get-Verb</span></span>

## <span data-ttu-id="36714-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="36714-104">SYNOPSIS</span></span>
<span data-ttu-id="36714-105">Hämtar godkända PowerShell-verb.</span><span class="sxs-lookup"><span data-stu-id="36714-105">Gets approved PowerShell verbs.</span></span>

## <span data-ttu-id="36714-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="36714-106">SYNTAX</span></span>

```
Get-Verb [[-Verb] <String[]>] [[-Group] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="36714-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="36714-107">DESCRIPTION</span></span>

<span data-ttu-id="36714-108">`Get-Verb`Funktionen hämtar verb som har godkänts för användning i PowerShell-kommandon.</span><span class="sxs-lookup"><span data-stu-id="36714-108">The `Get-Verb` function gets verbs that are approved for use in PowerShell commands.</span></span>

<span data-ttu-id="36714-109">Vi rekommenderar att PowerShell-cmdlet och funktions namn har `Verb-Noun` formatet och innehåller ett godkänt verb.</span><span class="sxs-lookup"><span data-stu-id="36714-109">It is recommended that PowerShell cmdlet and function names have the `Verb-Noun` format and include an approved verb.</span></span> <span data-ttu-id="36714-110">Den här metoden gör kommando namn mer konsekventa, förutsägbara och enklare att använda.</span><span class="sxs-lookup"><span data-stu-id="36714-110">This practice makes command names more consistent, predictable, and easier to use.</span></span>

<span data-ttu-id="36714-111">Kommandon som använder icke godkända verb, körs fortfarande i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="36714-111">Commands that use unapproved verbs, still run in PowerShell.</span></span> <span data-ttu-id="36714-112">Men när du importerar en modul som innehåller ett kommando med ett ej godkänt verb i namnet, `Import-Module` visar kommandot ett varnings meddelande.</span><span class="sxs-lookup"><span data-stu-id="36714-112">However, when you import a module that includes a command with an unapproved verb in its name, the `Import-Module` command displays a warning message.</span></span>

> [!NOTE]
> <span data-ttu-id="36714-113">Verb listan som `Get-Verb` returneras kanske inte är fullständig.</span><span class="sxs-lookup"><span data-stu-id="36714-113">The verb list that `Get-Verb` returns might not be complete.</span></span> <span data-ttu-id="36714-114">En uppdaterad lista över godkända PowerShell-verb med beskrivningar finns i [godkända verb](../../docs-conceptual/developer/cmdlet/approved-verbs-for-windows-powershell-commands.md) i Microsoft docs.</span><span class="sxs-lookup"><span data-stu-id="36714-114">For an updated list of approved PowerShell verbs with descriptions, see [Approved Verbs](../../docs-conceptual/developer/cmdlet/approved-verbs-for-windows-powershell-commands.md) in the Microsoft Docs.</span></span>

## <span data-ttu-id="36714-115">Exempel</span><span class="sxs-lookup"><span data-stu-id="36714-115">Examples</span></span>

### <span data-ttu-id="36714-116">Exempel 1 – Hämta en lista över alla verb</span><span class="sxs-lookup"><span data-stu-id="36714-116">Example 1 - Get a list of all verbs</span></span>

```powershell
Get-Verb
```

### <span data-ttu-id="36714-117">Exempel 2 – Hämta en lista över godkända verb som börjar med "UN"</span><span class="sxs-lookup"><span data-stu-id="36714-117">Example 2 - Get a list of approved verbs that begin with "un"</span></span>

```powershell
Get-Verb un*
```

```Output
Verb       AliasPrefix Group     Description
----       ----------- -----     -----------
Undo       un          Common    Sets a resource to its previous state
Unlock     uk          Common    Releases a resource that was locked
Unpublish  ub          Data      Makes a resource unavailable to others
Uninstall  us          Lifecycle Removes a resource from an indicated location
Unregister ur          Lifecycle Removes the entry for a resource from a repository
Unblock    ul          Security  Removes restrictions to a resource
Unprotect  up          Security  Removes safeguards from a resource that were added to prevent it from attack or loss
```

### <span data-ttu-id="36714-118">Exempel 3 – hämta alla godkända verb i säkerhets gruppen</span><span class="sxs-lookup"><span data-stu-id="36714-118">Example 3 - Get all approved verbs in the Security group</span></span>

```powershell
Get-Verb -Group Security
```

```Output
Verb      AliasPrefix Group    Description
----      ----------- -----    -----------
Block     bl          Security Restricts access to a resource
Grant     gr          Security Allows access to a resource
Protect   pt          Security Safeguards a resource from attack or loss
Revoke    rk          Security Specifies an action that does not allow access to a resource
Unblock   ul          Security Removes restrictions to a resource
Unprotect up          Security Removes safeguards from a resource that were added to prevent it from attack or loss
```

### <span data-ttu-id="36714-119">Exempel 4 – hittar alla kommandon i en modul som har ej godkända verb</span><span class="sxs-lookup"><span data-stu-id="36714-119">Example 4 - Finds all commands in a module that have unapproved verbs</span></span>

```powershell
Get-Command -Module Microsoft.PowerShell.Utility | Where-Object Verb -NotIn (Get-Verb).Verb
```

```Output
CommandType     Name            Version    Source
-----------     ----            -------    ------
Cmdlet          Sort-Object     3.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Tee-Object      3.1.0.0    Microsoft.PowerShell.Utility
```

## <span data-ttu-id="36714-120">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="36714-120">PARAMETERS</span></span>

### <span data-ttu-id="36714-121">-Verb</span><span class="sxs-lookup"><span data-stu-id="36714-121">-Verb</span></span>

<span data-ttu-id="36714-122">Hämtar endast de angivna verben.</span><span class="sxs-lookup"><span data-stu-id="36714-122">Gets only the specified verbs.</span></span> <span data-ttu-id="36714-123">Ange namnet på ett verb eller ett namn mönster.</span><span class="sxs-lookup"><span data-stu-id="36714-123">Enter the name of a verb or a name pattern.</span></span> <span data-ttu-id="36714-124">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="36714-124">Wildcards are allowed.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:
Accepted values: Common, Communications, Data, Diagnostic, Lifecycle, Other, Security

Required: False
Position: 1
Default value: All groups
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="36714-125">– Grupp</span><span class="sxs-lookup"><span data-stu-id="36714-125">-Group</span></span>

<span data-ttu-id="36714-126">Hämtar endast de angivna grupperna.</span><span class="sxs-lookup"><span data-stu-id="36714-126">Gets only the specified groups.</span></span> <span data-ttu-id="36714-127">Ange namnet på en grupp.</span><span class="sxs-lookup"><span data-stu-id="36714-127">Enter the name of a group.</span></span> <span data-ttu-id="36714-128">Jokertecken är inte tillåtna.</span><span class="sxs-lookup"><span data-stu-id="36714-128">Wildcards are not allowed.</span></span>

<span data-ttu-id="36714-129">Den här parametern introducerades i PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="36714-129">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: All verbs
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="36714-130">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="36714-130">CommonParameters</span></span>

<span data-ttu-id="36714-131">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="36714-131">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="36714-132">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="36714-132">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="36714-133">INDATA</span><span class="sxs-lookup"><span data-stu-id="36714-133">INPUTS</span></span>

### <span data-ttu-id="36714-134">Inget</span><span class="sxs-lookup"><span data-stu-id="36714-134">None</span></span>

## <span data-ttu-id="36714-135">UTDATA</span><span class="sxs-lookup"><span data-stu-id="36714-135">OUTPUTS</span></span>

### <span data-ttu-id="36714-136">System. Management. Automation. VerbInfo</span><span class="sxs-lookup"><span data-stu-id="36714-136">System.Management.Automation.VerbInfo</span></span>

## <span data-ttu-id="36714-137">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="36714-137">NOTES</span></span>

<span data-ttu-id="36714-138">PowerShell-verb tilldelas en grupp baserat på den vanligaste användningen.</span><span class="sxs-lookup"><span data-stu-id="36714-138">PowerShell verbs are assigned to a group based on their most common use.</span></span> <span data-ttu-id="36714-139">Grupperna är utformade för att göra verben enkla att hitta och jämföra och inte begränsa användningen.</span><span class="sxs-lookup"><span data-stu-id="36714-139">The groups are designed to make the verbs easy to find and compare, not to restrict their use.</span></span> <span data-ttu-id="36714-140">Du kan använda valfritt godkänt verb för alla typer av kommandon.</span><span class="sxs-lookup"><span data-stu-id="36714-140">You can use any approved verb for any type of command.</span></span>

<span data-ttu-id="36714-141">Varje PowerShell-verb tilldelas en av följande grupper.</span><span class="sxs-lookup"><span data-stu-id="36714-141">Each PowerShell verb is assigned to one of the following groups.</span></span>

- <span data-ttu-id="36714-142">Common: Definiera allmänna åtgärder som kan gälla för nästan alla cmdletar, till exempel Add.</span><span class="sxs-lookup"><span data-stu-id="36714-142">Common: Define generic actions that can apply to almost any cmdlet, such as Add.</span></span>
- <span data-ttu-id="36714-143">Kommunikation: definiera åtgärder som gäller för kommunikation, till exempel Anslut.</span><span class="sxs-lookup"><span data-stu-id="36714-143">Communications: Define actions that apply to communications, such as Connect.</span></span>
- <span data-ttu-id="36714-144">Data: definiera åtgärder som gäller för data hantering, till exempel säkerhets kopiering.</span><span class="sxs-lookup"><span data-stu-id="36714-144">Data: Define actions that apply to data handling, such as Backup.</span></span>
- <span data-ttu-id="36714-145">Diagnostik: definiera åtgärder som gäller diagnostik, till exempel fel sökning.</span><span class="sxs-lookup"><span data-stu-id="36714-145">Diagnostic: Define actions that apply to diagnostics, such as Debug.</span></span>
- <span data-ttu-id="36714-146">Livs cykel: definiera åtgärder som gäller för livs cykeln för en cmdlet, till exempel fullständig.</span><span class="sxs-lookup"><span data-stu-id="36714-146">Lifecycle: Define actions that apply to the lifecycle of a cmdlet, such as Complete.</span></span>
- <span data-ttu-id="36714-147">Säkerhet: definiera åtgärder som ska vidtas för säkerhet, till exempel återkalla.</span><span class="sxs-lookup"><span data-stu-id="36714-147">Security: Define actions that apply to security, such as Revoke.</span></span>
- <span data-ttu-id="36714-148">Övrigt: definiera andra typer av åtgärder.</span><span class="sxs-lookup"><span data-stu-id="36714-148">Other: Define other types of actions.</span></span>

<span data-ttu-id="36714-149">Några av cmdletarna som installeras med PowerShell, till exempel `Tee-Object` och `Where-Object` , använder inte godkända verb.</span><span class="sxs-lookup"><span data-stu-id="36714-149">Some of the cmdlets that are installed with PowerShell, such as `Tee-Object` and `Where-Object`, use unapproved verbs.</span></span> <span data-ttu-id="36714-150">Dessa cmdletar är historiska undantag och deras verb klassificeras som **reserverade**.</span><span class="sxs-lookup"><span data-stu-id="36714-150">These cmdlets are historic exceptions and their verbs are classified as **reserved**.</span></span>

## <span data-ttu-id="36714-151">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="36714-151">RELATED LINKS</span></span>

[<span data-ttu-id="36714-152">Importera-modul</span><span class="sxs-lookup"><span data-stu-id="36714-152">Import-Module</span></span>](../microsoft.powershell.core/import-module.md)
