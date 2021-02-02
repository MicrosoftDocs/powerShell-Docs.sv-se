---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-pscallstack?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSCallStack
ms.openlocfilehash: 607e3999a1dbe9a4f22a751f11ac93ee3f9d9409
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708630"
---
# <span data-ttu-id="42969-102">Get-PSCallStack</span><span class="sxs-lookup"><span data-stu-id="42969-102">Get-PSCallStack</span></span>

## <span data-ttu-id="42969-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="42969-103">SYNOPSIS</span></span>
<span data-ttu-id="42969-104">Visar den aktuella anrops stacken.</span><span class="sxs-lookup"><span data-stu-id="42969-104">Displays the current call stack.</span></span>

## <span data-ttu-id="42969-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="42969-105">SYNTAX</span></span>

```
Get-PSCallStack [<CommonParameters>]
```

## <span data-ttu-id="42969-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="42969-106">DESCRIPTION</span></span>

<span data-ttu-id="42969-107">Cmdlet: en **Get-PSCallStack** visar den aktuella anrops stacken.</span><span class="sxs-lookup"><span data-stu-id="42969-107">The **Get-PSCallStack** cmdlet displays the current call stack.</span></span>

<span data-ttu-id="42969-108">Även om den är avsedd att användas med PowerShell-felsökaren kan du använda denna cmdlet för att Visa anrops stacken i ett skript eller en funktion utanför fel söknings programmet.</span><span class="sxs-lookup"><span data-stu-id="42969-108">Although it is designed to be used with the PowerShell debugger, you can use this cmdlet to display the call stack in a script or function outside of the debugger.</span></span>

<span data-ttu-id="42969-109">Om du vill köra kommandot **Get-PSCallStack** när du är i fel söknings programmet skriver du `k` eller `Get-PSCallStack` .</span><span class="sxs-lookup"><span data-stu-id="42969-109">To run a **Get-PSCallStack** command while in the debugger, type `k` or `Get-PSCallStack`.</span></span>

## <span data-ttu-id="42969-110">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="42969-110">EXAMPLES</span></span>

### <span data-ttu-id="42969-111">Exempel 1: Hämta anrops stacken för en funktion</span><span class="sxs-lookup"><span data-stu-id="42969-111">Example 1: Get the call stack for a function</span></span>

```
PS C:\> function my-alias {
$p = $args[0]
Get-Alias | where {$_.definition -like "*$p"} | format-table definition, name -auto
}
PS C:\ps-test> Set-PSBreakpoint -Command my-alias
Command    : my-alias
Action     :
Enabled    : True
HitCount   : 0
Id         : 0
Script     : prompt PS C:\> my-alias Get-Content

Entering debug mode. Use h or ? for help.
Hit Command breakpoint on 'prompt:my-alias'
my-alias get-content
[DBG]: PS C:\ps-test> s
$p = $args[0]
DEBUG: Stepped to ':    $p = $args[0]    '
[DBG]: PS C:\ps-test> s
get-alias | Where {$_.Definition -like "*$p*"} | format-table Definition,
[DBG]: PS C:\ps-test>get-pscallstack

Name        CommandLineParameters         UnboundArguments              Location
----        ---------------------         ----------------              --------
prompt      {}                            {}                            prompt
my-alias    {}                            {get-content}                 prompt
prompt      {}                            {}                            prompt PS C:\> [DBG]: PS C:\ps-test> o
Definition  Name
----------  ----
Get-Content gc
Get-Content cat
Get-Content type
```

<span data-ttu-id="42969-112">Detta kommando använder **Get-PSCallStack** -cmdleten för att Visa anrops stacken för mitt alias, en enkel funktion som hämtar alias för ett cmdlet-namn.</span><span class="sxs-lookup"><span data-stu-id="42969-112">This command uses the **Get-PSCallStack** cmdlet to display the call stack for My-Alias, a simple function that gets the aliases for a cmdlet name.</span></span>

<span data-ttu-id="42969-113">Det första kommandot anger funktionen vid PowerShell-prompten.</span><span class="sxs-lookup"><span data-stu-id="42969-113">The first command enters the function at the PowerShell prompt.</span></span>
<span data-ttu-id="42969-114">Det andra kommandot använder cmdleten Set-PSBreakpoint för att ange en Bryt punkt för funktionen My-Alias.</span><span class="sxs-lookup"><span data-stu-id="42969-114">The second command uses the Set-PSBreakpoint cmdlet to set a breakpoint on the My-Alias function.</span></span>
<span data-ttu-id="42969-115">Det tredje kommandot använder funktionen My-Alias för att hämta alla alias i den aktuella sessionen för Get-Content-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="42969-115">The third command uses the My-Alias function to get all of the aliases in the current session for the Get-Content cmdlet.</span></span>

<span data-ttu-id="42969-116">Fel söknings verktyget bryts i vid funktions anropet.</span><span class="sxs-lookup"><span data-stu-id="42969-116">The debugger breaks in at the function call.</span></span>
<span data-ttu-id="42969-117">Två steg i följd av steg-till-kommandon börjar köra funktions raden per rad.</span><span class="sxs-lookup"><span data-stu-id="42969-117">Two consecutive step-into (s) commands begin executing the function line by line.</span></span>
<span data-ttu-id="42969-118">Sedan används kommandot **Get-PSCallStack** för att hämta anrops stacken.</span><span class="sxs-lookup"><span data-stu-id="42969-118">Then, a **Get-PSCallStack** command is used to retrieve the call stack.</span></span>

<span data-ttu-id="42969-119">Det sista kommandot är ett Step-Out kommando (o) som avslutar fel söknings programmet och fortsätter att köra skriptet för att slutföras.</span><span class="sxs-lookup"><span data-stu-id="42969-119">The final command is a Step-Out command (o) that exits the debugger and continues executing the script to completion.</span></span>

## <span data-ttu-id="42969-120">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="42969-120">PARAMETERS</span></span>

### <span data-ttu-id="42969-121">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="42969-121">CommonParameters</span></span>

<span data-ttu-id="42969-122">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="42969-122">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="42969-123">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="42969-123">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="42969-124">INDATA</span><span class="sxs-lookup"><span data-stu-id="42969-124">INPUTS</span></span>

### <span data-ttu-id="42969-125">Inga</span><span class="sxs-lookup"><span data-stu-id="42969-125">None</span></span>

<span data-ttu-id="42969-126">Det går inte att skicka pipe-objekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="42969-126">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="42969-127">UTDATA</span><span class="sxs-lookup"><span data-stu-id="42969-127">OUTPUTS</span></span>

### <span data-ttu-id="42969-128">System. Management. Automation. CallStackFrame</span><span class="sxs-lookup"><span data-stu-id="42969-128">System.Management.Automation.CallStackFrame</span></span>

<span data-ttu-id="42969-129">**Get-PSCallStack** returnerar ett objekt som representerar objekten i anrops stacken.</span><span class="sxs-lookup"><span data-stu-id="42969-129">**Get-PSCallStack** returns an object that represents the items in the call stack.</span></span>

## <span data-ttu-id="42969-130">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="42969-130">NOTES</span></span>

## <span data-ttu-id="42969-131">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="42969-131">RELATED LINKS</span></span>

[<span data-ttu-id="42969-132">Disable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="42969-132">Disable-PSBreakpoint</span></span>](Disable-PSBreakpoint.md)

[<span data-ttu-id="42969-133">Aktivera – PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="42969-133">Enable-PSBreakpoint</span></span>](Enable-PSBreakpoint.md)

[<span data-ttu-id="42969-134">Format-Table</span><span class="sxs-lookup"><span data-stu-id="42969-134">Format-Table</span></span>](Format-Table.md)

[<span data-ttu-id="42969-135">Get-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="42969-135">Get-PSBreakpoint</span></span>](Get-PSBreakpoint.md)

[<span data-ttu-id="42969-136">Remove-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="42969-136">Remove-PSBreakpoint</span></span>](Remove-PSBreakpoint.md)

[<span data-ttu-id="42969-137">Set-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="42969-137">Set-PSBreakpoint</span></span>](Set-PSBreakpoint.md)
