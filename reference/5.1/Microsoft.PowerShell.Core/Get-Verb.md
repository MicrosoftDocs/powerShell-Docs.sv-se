---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
ms.date: 09/07/2018
Module Name: Microsoft.PowerShell.Core
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/functions/get-verb?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Verb
ms.openlocfilehash: 4474bb50c2bf3be10e72d2554190208e956f9040
ms.sourcegitcommit: 7d052985c20761fdf4c6d7ce4e04df4c551c36a3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/11/2020
ms.locfileid: "93269157"
---
# <span data-ttu-id="97533-103">Get-Verb</span><span class="sxs-lookup"><span data-stu-id="97533-103">Get-Verb</span></span>

## <span data-ttu-id="97533-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="97533-104">SYNOPSIS</span></span>
<span data-ttu-id="97533-105">Hämtar godkända PowerShell-verb.</span><span class="sxs-lookup"><span data-stu-id="97533-105">Gets approved PowerShell verbs.</span></span>

## <span data-ttu-id="97533-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="97533-106">SYNTAX</span></span>

```
Get-Verb [[-verb] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="97533-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="97533-107">DESCRIPTION</span></span>

<span data-ttu-id="97533-108">`Get-Verb`Funktionen hämtar verb som har godkänts för användning i PowerShell-kommandon.</span><span class="sxs-lookup"><span data-stu-id="97533-108">The `Get-Verb` function gets verbs that are approved for use in PowerShell commands.</span></span>

<span data-ttu-id="97533-109">PowerShell rekommenderar att cmdlet-och funktions namn har Verb-Noun format och innehåller ett godkänt verb.</span><span class="sxs-lookup"><span data-stu-id="97533-109">PowerShell recommends cmdlet and function names have the Verb-Noun format and include an approved verb.</span></span> <span data-ttu-id="97533-110">Den här metoden gör kommando namn mer konsekventa, förutsägbara och enklare att använda.</span><span class="sxs-lookup"><span data-stu-id="97533-110">This practice makes command names more consistent, predictable, and easier to use.</span></span>

<span data-ttu-id="97533-111">Kommandon som använder icke godkända verb körs i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="97533-111">Commands that use unapproved verbs run in PowerShell.</span></span> <span data-ttu-id="97533-112">Men när du importerar en modul som innehåller ett kommando med ett ej godkänt verb i namnet, `Import-Module` visar kommandot ett varnings meddelande.</span><span class="sxs-lookup"><span data-stu-id="97533-112">However, when you import a module that includes a command with an unapproved verb in its name, the `Import-Module` command displays a warning message.</span></span>

> [!NOTE]
> <span data-ttu-id="97533-113">Verb listan som `Get-Verb` returneras kanske inte är fullständig.</span><span class="sxs-lookup"><span data-stu-id="97533-113">The verb list that `Get-Verb` returns might not be complete.</span></span> <span data-ttu-id="97533-114">En uppdaterad lista över godkända PowerShell-verb med beskrivningar finns i [godkända verb](../../docs-conceptual/developer/cmdlet/approved-verbs-for-windows-powershell-commands.md) i Microsoft docs.</span><span class="sxs-lookup"><span data-stu-id="97533-114">For an updated list of approved PowerShell verbs with descriptions, see [Approved Verbs](../../docs-conceptual/developer/cmdlet/approved-verbs-for-windows-powershell-commands.md) in the Microsoft Docs.</span></span>

## <span data-ttu-id="97533-115">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="97533-115">EXAMPLES</span></span>

### <span data-ttu-id="97533-116">Exempel 1 – Hämta en lista över alla verb</span><span class="sxs-lookup"><span data-stu-id="97533-116">Example 1 - Get a list of all verbs</span></span>

```powershell
Get-Verb
```

### <span data-ttu-id="97533-117">Exempel 2 – Hämta en lista över godkända verb som börjar med "UN"</span><span class="sxs-lookup"><span data-stu-id="97533-117">Example 2 - Get a list of approved verbs that begin with "un"</span></span>

```powershell
Get-Verb un*
```

```Output
Verb                 Group
----                 -----
Undo                 Common
Unlock               Common
Unpublish            Data
Uninstall            Lifecycle
Unregister           Lifecycle
Unblock              Security
Unprotect            Security
```

### <span data-ttu-id="97533-118">Exempel 3 – hämta alla godkända verb i säkerhets gruppen</span><span class="sxs-lookup"><span data-stu-id="97533-118">Example 3 - Get all approved verbs in the Security group</span></span>

```powershell
Get-Verb | Where-Object Group -EQ Security
```

```Output
Verb      Group
----      -----
Block     Security
Grant     Security
Protect   Security
Revoke    Security
Unblock   Security
Unprotect Security
```

### <span data-ttu-id="97533-119">Exempel 4 – hittar alla kommandon i en modul som har ej godkända verb</span><span class="sxs-lookup"><span data-stu-id="97533-119">Example 4 - Finds all commands in a module that have unapproved verbs</span></span>

```powershell
Get-Command -Module Microsoft.PowerShell.Utility | Where-Object Verb -NotIn (Get-Verb).Verb
```

```Output
CommandType     Name            Version    Source
-----------     ----            -------    ------
Cmdlet          Sort-Object     3.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Tee-Object      3.1.0.0    Microsoft.PowerShell.Utility
```

## <span data-ttu-id="97533-120">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="97533-120">PARAMETERS</span></span>

### <span data-ttu-id="97533-121">-verb</span><span class="sxs-lookup"><span data-stu-id="97533-121">-verb</span></span>

<span data-ttu-id="97533-122">Hämtar endast de angivna verben.</span><span class="sxs-lookup"><span data-stu-id="97533-122">Gets only the specified verbs.</span></span>
<span data-ttu-id="97533-123">Ange namnet på ett verb eller ett namn mönster.</span><span class="sxs-lookup"><span data-stu-id="97533-123">Enter the name of a verb or a name pattern.</span></span>
<span data-ttu-id="97533-124">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="97533-124">Wildcards are allowed.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: All verbs
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

## <span data-ttu-id="97533-125">INDATA</span><span class="sxs-lookup"><span data-stu-id="97533-125">INPUTS</span></span>

### <span data-ttu-id="97533-126">Inget</span><span class="sxs-lookup"><span data-stu-id="97533-126">None</span></span>

## <span data-ttu-id="97533-127">UTDATA</span><span class="sxs-lookup"><span data-stu-id="97533-127">OUTPUTS</span></span>

### <span data-ttu-id="97533-128">Markerat. Microsoft. PowerShell. commands. MemberDefinition</span><span class="sxs-lookup"><span data-stu-id="97533-128">Selected.Microsoft.PowerShell.Commands.MemberDefinition</span></span>

## <span data-ttu-id="97533-129">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="97533-129">NOTES</span></span>

<span data-ttu-id="97533-130">`Get-Verb` Returnerar en modifierad version av ett Microsoft. PowerShell. commands. MemberDefinition-objekt.</span><span class="sxs-lookup"><span data-stu-id="97533-130">`Get-Verb` returns a modified version of a Microsoft.PowerShell.Commands.MemberDefinition object.</span></span>
<span data-ttu-id="97533-131">Objektet har inte standard egenskaperna för ett MemberDefinition-objekt.</span><span class="sxs-lookup"><span data-stu-id="97533-131">The object does not have the standard properties of a MemberDefinition object.</span></span> <span data-ttu-id="97533-132">I stället har det verb-och grupp egenskaper.</span><span class="sxs-lookup"><span data-stu-id="97533-132">Instead it has Verb and Group properties.</span></span> <span data-ttu-id="97533-133">Verb-egenskapen innehåller en sträng med verbets namn.</span><span class="sxs-lookup"><span data-stu-id="97533-133">The Verb property contains a string with the verb name.</span></span> <span data-ttu-id="97533-134">Grupp egenskapen innehåller en sträng med gruppen verb.</span><span class="sxs-lookup"><span data-stu-id="97533-134">The Group property contains a string with the verb group.</span></span>

<span data-ttu-id="97533-135">PowerShell-verb tilldelas en grupp baserat på den vanligaste användningen.</span><span class="sxs-lookup"><span data-stu-id="97533-135">PowerShell verbs are assigned to a group based on their most common use.</span></span> <span data-ttu-id="97533-136">Grupperna är utformade för att göra verben enkla att hitta och jämföra och inte begränsa användningen.</span><span class="sxs-lookup"><span data-stu-id="97533-136">The groups are designed to make the verbs easy to find and compare, not to restrict their use.</span></span> <span data-ttu-id="97533-137">Du kan använda valfritt godkänt verb för alla typer av kommandon.</span><span class="sxs-lookup"><span data-stu-id="97533-137">You can use any approved verb for any type of command.</span></span>

<span data-ttu-id="97533-138">Varje PowerShell-verb tilldelas en av följande grupper.</span><span class="sxs-lookup"><span data-stu-id="97533-138">Each PowerShell verb is assigned to one of the following groups.</span></span>

- <span data-ttu-id="97533-139">Common: Definiera allmänna åtgärder som kan gälla för nästan alla cmdletar, till exempel Add.</span><span class="sxs-lookup"><span data-stu-id="97533-139">Common: Define generic actions that can apply to almost any cmdlet, such as Add.</span></span>
- <span data-ttu-id="97533-140">Kommunikation: definiera åtgärder som gäller för kommunikation, till exempel Anslut.</span><span class="sxs-lookup"><span data-stu-id="97533-140">Communications:  Define actions that apply to communications, such as Connect.</span></span>
- <span data-ttu-id="97533-141">Data: definiera åtgärder som gäller för data hantering, till exempel säkerhets kopiering.</span><span class="sxs-lookup"><span data-stu-id="97533-141">Data:  Define actions that apply to data handling, such as Backup.</span></span>
- <span data-ttu-id="97533-142">Diagnostik: definiera åtgärder som gäller diagnostik, till exempel fel sökning.</span><span class="sxs-lookup"><span data-stu-id="97533-142">Diagnostic: Define actions that apply to diagnostics, such as Debug.</span></span>
- <span data-ttu-id="97533-143">Livs cykel: definiera åtgärder som gäller för livs cykeln för en cmdlet, till exempel fullständig.</span><span class="sxs-lookup"><span data-stu-id="97533-143">Lifecycle: Define actions that apply to the lifecycle of a cmdlet, such as Complete.</span></span>
- <span data-ttu-id="97533-144">Säkerhet: definiera åtgärder som ska vidtas för säkerhet, till exempel återkalla.</span><span class="sxs-lookup"><span data-stu-id="97533-144">Security: Define actions that apply to security, such as Revoke.</span></span>
- <span data-ttu-id="97533-145">Övrigt: definiera andra typer av åtgärder.</span><span class="sxs-lookup"><span data-stu-id="97533-145">Other: Define other types of actions.</span></span>

<span data-ttu-id="97533-146">Några av cmdletarna som installeras med PowerShell, till exempel `Tee-Object` och `Where-Object` , använder inte godkända verb.</span><span class="sxs-lookup"><span data-stu-id="97533-146">Some of the cmdlets that are installed with PowerShell, such as `Tee-Object` and `Where-Object`, use unapproved verbs.</span></span> <span data-ttu-id="97533-147">Dessa cmdletar är historiska undantag och deras verb klassificeras som **reserverade**.</span><span class="sxs-lookup"><span data-stu-id="97533-147">These cmdlets are historic exceptions and their verbs are classified as **reserved**.</span></span>

## <span data-ttu-id="97533-148">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="97533-148">RELATED LINKS</span></span>

[<span data-ttu-id="97533-149">Importera-modul</span><span class="sxs-lookup"><span data-stu-id="97533-149">Import-Module</span></span>](import-module.md)
