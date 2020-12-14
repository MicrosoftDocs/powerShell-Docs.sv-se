---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/07/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-verb?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Verb
ms.openlocfilehash: 6aba1c87a5d711cbfe84f9f6f6d1051acbcd524a
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710801"
---
# <span data-ttu-id="76f63-102">Get-Verb</span><span class="sxs-lookup"><span data-stu-id="76f63-102">Get-Verb</span></span>

## <span data-ttu-id="76f63-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="76f63-103">SYNOPSIS</span></span>
<span data-ttu-id="76f63-104">Hämtar godkända PowerShell-verb.</span><span class="sxs-lookup"><span data-stu-id="76f63-104">Gets approved PowerShell verbs.</span></span>

## <span data-ttu-id="76f63-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="76f63-105">SYNTAX</span></span>

```
Get-Verb [[-Verb] <String[]>] [[-Group] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="76f63-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="76f63-106">DESCRIPTION</span></span>

<span data-ttu-id="76f63-107">`Get-Verb`Funktionen hämtar verb som har godkänts för användning i PowerShell-kommandon.</span><span class="sxs-lookup"><span data-stu-id="76f63-107">The `Get-Verb` function gets verbs that are approved for use in PowerShell commands.</span></span>

<span data-ttu-id="76f63-108">Vi rekommenderar att PowerShell-cmdlet och funktions namn har `Verb-Noun` formatet och innehåller ett godkänt verb.</span><span class="sxs-lookup"><span data-stu-id="76f63-108">It is recommended that PowerShell cmdlet and function names have the `Verb-Noun` format and include an approved verb.</span></span> <span data-ttu-id="76f63-109">Den här metoden gör kommando namn mer konsekventa, förutsägbara och enklare att använda.</span><span class="sxs-lookup"><span data-stu-id="76f63-109">This practice makes command names more consistent, predictable, and easier to use.</span></span>

<span data-ttu-id="76f63-110">Kommandon som använder icke godkända verb, körs fortfarande i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="76f63-110">Commands that use unapproved verbs, still run in PowerShell.</span></span> <span data-ttu-id="76f63-111">Men när du importerar en modul som innehåller ett kommando med ett ej godkänt verb i namnet, `Import-Module` visar kommandot ett varnings meddelande.</span><span class="sxs-lookup"><span data-stu-id="76f63-111">However, when you import a module that includes a command with an unapproved verb in its name, the `Import-Module` command displays a warning message.</span></span>

> [!NOTE]
> <span data-ttu-id="76f63-112">Verb listan som `Get-Verb` returneras kanske inte är fullständig.</span><span class="sxs-lookup"><span data-stu-id="76f63-112">The verb list that `Get-Verb` returns might not be complete.</span></span> <span data-ttu-id="76f63-113">En uppdaterad lista över godkända PowerShell-verb med beskrivningar finns i [godkända verb](../../docs-conceptual/developer/cmdlet/approved-verbs-for-windows-powershell-commands.md) i Microsoft docs.</span><span class="sxs-lookup"><span data-stu-id="76f63-113">For an updated list of approved PowerShell verbs with descriptions, see [Approved Verbs](../../docs-conceptual/developer/cmdlet/approved-verbs-for-windows-powershell-commands.md) in the Microsoft Docs.</span></span>

## <span data-ttu-id="76f63-114">Exempel</span><span class="sxs-lookup"><span data-stu-id="76f63-114">Examples</span></span>

### <span data-ttu-id="76f63-115">Exempel 1 – Hämta en lista över alla verb</span><span class="sxs-lookup"><span data-stu-id="76f63-115">Example 1 - Get a list of all verbs</span></span>

```powershell
Get-Verb
```

### <span data-ttu-id="76f63-116">Exempel 2 – Hämta en lista över godkända verb som börjar med "UN"</span><span class="sxs-lookup"><span data-stu-id="76f63-116">Example 2 - Get a list of approved verbs that begin with "un"</span></span>

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

### <span data-ttu-id="76f63-117">Exempel 3 – hämta alla godkända verb i säkerhets gruppen</span><span class="sxs-lookup"><span data-stu-id="76f63-117">Example 3 - Get all approved verbs in the Security group</span></span>

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

### <span data-ttu-id="76f63-118">Exempel 4 – hittar alla kommandon i en modul som har ej godkända verb</span><span class="sxs-lookup"><span data-stu-id="76f63-118">Example 4 - Finds all commands in a module that have unapproved verbs</span></span>

```powershell
Get-Command -Module Microsoft.PowerShell.Utility | Where-Object Verb -NotIn (Get-Verb).Verb
```

```Output
CommandType     Name            Version    Source
-----------     ----            -------    ------
Cmdlet          Sort-Object     3.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Tee-Object      3.1.0.0    Microsoft.PowerShell.Utility
```

## <span data-ttu-id="76f63-119">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="76f63-119">PARAMETERS</span></span>

### <span data-ttu-id="76f63-120">-Verb</span><span class="sxs-lookup"><span data-stu-id="76f63-120">-Verb</span></span>

<span data-ttu-id="76f63-121">Hämtar endast de angivna verben.</span><span class="sxs-lookup"><span data-stu-id="76f63-121">Gets only the specified verbs.</span></span> <span data-ttu-id="76f63-122">Ange namnet på ett verb eller ett namn mönster.</span><span class="sxs-lookup"><span data-stu-id="76f63-122">Enter the name of a verb or a name pattern.</span></span> <span data-ttu-id="76f63-123">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="76f63-123">Wildcards are allowed.</span></span>

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

### <span data-ttu-id="76f63-124">– Grupp</span><span class="sxs-lookup"><span data-stu-id="76f63-124">-Group</span></span>

<span data-ttu-id="76f63-125">Hämtar endast de angivna grupperna.</span><span class="sxs-lookup"><span data-stu-id="76f63-125">Gets only the specified groups.</span></span> <span data-ttu-id="76f63-126">Ange namnet på en grupp.</span><span class="sxs-lookup"><span data-stu-id="76f63-126">Enter the name of a group.</span></span> <span data-ttu-id="76f63-127">Jokertecken är inte tillåtna.</span><span class="sxs-lookup"><span data-stu-id="76f63-127">Wildcards are not allowed.</span></span>

<span data-ttu-id="76f63-128">Den här parametern introducerades i PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="76f63-128">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="76f63-129">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="76f63-129">CommonParameters</span></span>

<span data-ttu-id="76f63-130">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="76f63-130">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="76f63-131">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="76f63-131">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="76f63-132">INDATA</span><span class="sxs-lookup"><span data-stu-id="76f63-132">INPUTS</span></span>

### <span data-ttu-id="76f63-133">Inga</span><span class="sxs-lookup"><span data-stu-id="76f63-133">None</span></span>

## <span data-ttu-id="76f63-134">UTDATA</span><span class="sxs-lookup"><span data-stu-id="76f63-134">OUTPUTS</span></span>

### <span data-ttu-id="76f63-135">System. Management. Automation. VerbInfo</span><span class="sxs-lookup"><span data-stu-id="76f63-135">System.Management.Automation.VerbInfo</span></span>

## <span data-ttu-id="76f63-136">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="76f63-136">NOTES</span></span>

<span data-ttu-id="76f63-137">PowerShell-verb tilldelas en grupp baserat på den vanligaste användningen.</span><span class="sxs-lookup"><span data-stu-id="76f63-137">PowerShell verbs are assigned to a group based on their most common use.</span></span> <span data-ttu-id="76f63-138">Grupperna är utformade för att göra verben enkla att hitta och jämföra och inte begränsa användningen.</span><span class="sxs-lookup"><span data-stu-id="76f63-138">The groups are designed to make the verbs easy to find and compare, not to restrict their use.</span></span> <span data-ttu-id="76f63-139">Du kan använda valfritt godkänt verb för alla typer av kommandon.</span><span class="sxs-lookup"><span data-stu-id="76f63-139">You can use any approved verb for any type of command.</span></span>

<span data-ttu-id="76f63-140">Varje PowerShell-verb tilldelas en av följande grupper.</span><span class="sxs-lookup"><span data-stu-id="76f63-140">Each PowerShell verb is assigned to one of the following groups.</span></span>

- <span data-ttu-id="76f63-141">Common: Definiera allmänna åtgärder som kan gälla för nästan alla cmdletar, till exempel Add.</span><span class="sxs-lookup"><span data-stu-id="76f63-141">Common: Define generic actions that can apply to almost any cmdlet, such as Add.</span></span>
- <span data-ttu-id="76f63-142">Kommunikation: definiera åtgärder som gäller för kommunikation, till exempel Anslut.</span><span class="sxs-lookup"><span data-stu-id="76f63-142">Communications: Define actions that apply to communications, such as Connect.</span></span>
- <span data-ttu-id="76f63-143">Data: definiera åtgärder som gäller för data hantering, till exempel säkerhets kopiering.</span><span class="sxs-lookup"><span data-stu-id="76f63-143">Data: Define actions that apply to data handling, such as Backup.</span></span>
- <span data-ttu-id="76f63-144">Diagnostik: definiera åtgärder som gäller diagnostik, till exempel fel sökning.</span><span class="sxs-lookup"><span data-stu-id="76f63-144">Diagnostic: Define actions that apply to diagnostics, such as Debug.</span></span>
- <span data-ttu-id="76f63-145">Livs cykel: definiera åtgärder som gäller för livs cykeln för en cmdlet, till exempel fullständig.</span><span class="sxs-lookup"><span data-stu-id="76f63-145">Lifecycle: Define actions that apply to the lifecycle of a cmdlet, such as Complete.</span></span>
- <span data-ttu-id="76f63-146">Säkerhet: definiera åtgärder som ska vidtas för säkerhet, till exempel återkalla.</span><span class="sxs-lookup"><span data-stu-id="76f63-146">Security: Define actions that apply to security, such as Revoke.</span></span>
- <span data-ttu-id="76f63-147">Övrigt: definiera andra typer av åtgärder.</span><span class="sxs-lookup"><span data-stu-id="76f63-147">Other: Define other types of actions.</span></span>

<span data-ttu-id="76f63-148">Några av cmdletarna som installeras med PowerShell, till exempel `Tee-Object` och `Where-Object` , använder inte godkända verb.</span><span class="sxs-lookup"><span data-stu-id="76f63-148">Some of the cmdlets that are installed with PowerShell, such as `Tee-Object` and `Where-Object`, use unapproved verbs.</span></span> <span data-ttu-id="76f63-149">Dessa cmdletar är historiska undantag och deras verb klassificeras som **reserverade**.</span><span class="sxs-lookup"><span data-stu-id="76f63-149">These cmdlets are historic exceptions and their verbs are classified as **reserved**.</span></span>

## <span data-ttu-id="76f63-150">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="76f63-150">RELATED LINKS</span></span>

[<span data-ttu-id="76f63-151">Importera-modul</span><span class="sxs-lookup"><span data-stu-id="76f63-151">Import-Module</span></span>](../microsoft.powershell.core/import-module.md)

