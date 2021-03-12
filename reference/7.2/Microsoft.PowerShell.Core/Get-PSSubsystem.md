---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 10/15/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-pssubsystem?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSSubsystem
ms.openlocfilehash: 19129eb8a0b478d10fdbf1e35f15b7f86969b5fb
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/12/2021
ms.locfileid: "103194996"
---
# <span data-ttu-id="32b28-102">Get-PSSubsystem</span><span class="sxs-lookup"><span data-stu-id="32b28-102">Get-PSSubsystem</span></span>

## <span data-ttu-id="32b28-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="32b28-103">SYNOPSIS</span></span>
<span data-ttu-id="32b28-104">Hämtar information om de under system som registrerats i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="32b28-104">Retrieves information about the subsystems registered in PowerShell.</span></span>

## <span data-ttu-id="32b28-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="32b28-105">SYNTAX</span></span>

### <span data-ttu-id="32b28-106">GetAllSet (standard)</span><span class="sxs-lookup"><span data-stu-id="32b28-106">GetAllSet (Default)</span></span>

```
Get-PSSubsystem [<CommonParameters>]
```

### <span data-ttu-id="32b28-107">GetByKindSet</span><span class="sxs-lookup"><span data-stu-id="32b28-107">GetByKindSet</span></span>

```
Get-PSSubsystem -Kind <SubsystemKind> [<CommonParameters>]
```

### <span data-ttu-id="32b28-108">GetByTypeSet</span><span class="sxs-lookup"><span data-stu-id="32b28-108">GetByTypeSet</span></span>

```
Get-PSSubsystem -SubsystemType <Type> [<CommonParameters>]
```

## <span data-ttu-id="32b28-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="32b28-109">DESCRIPTION</span></span>

<span data-ttu-id="32b28-110">Hämtar information om de under system som registrerats i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="32b28-110">Retrieves information about the subsystems registered in PowerShell.</span></span>

> [!NOTE]
> <span data-ttu-id="32b28-111">Det här är en experimentell funktion.</span><span class="sxs-lookup"><span data-stu-id="32b28-111">This is an experimental feature.</span></span> <span data-ttu-id="32b28-112">Den här cmdleten är endast tillgänglig om `PSSubsystemPluginModel` funktionen är aktive rad.</span><span class="sxs-lookup"><span data-stu-id="32b28-112">This cmdlet is only available when the `PSSubsystemPluginModel` feature is enabled.</span></span> <span data-ttu-id="32b28-113">Mer information finns i [använda experimentella funktioner](/powershell/scripting/learn/experimental-features).</span><span class="sxs-lookup"><span data-stu-id="32b28-113">For more information, see [Using Experimental Features](/powershell/scripting/learn/experimental-features).</span></span>

<span data-ttu-id="32b28-114">Funktionen gör det möjligt att separera komponenter i `System.Management.Automation.dll` enskilda under system som finns i en egen sammansättning.</span><span class="sxs-lookup"><span data-stu-id="32b28-114">The feature makes it possible to separate components of `System.Management.Automation.dll` into individual subsystems that reside in their own assembly.</span></span> <span data-ttu-id="32b28-115">Den här separationen minskar den grundläggande PowerShell-motorns disk utrymme och gör att dessa komponenter blir valfria funktioner för en minimal PowerShell-installation.</span><span class="sxs-lookup"><span data-stu-id="32b28-115">This separation reduces the disk footprint of the core PowerShell engine and allows these components to become optional features for a minimal PowerShell installation.</span></span>

<span data-ttu-id="32b28-116">För närvarande stöds endast under systemet **CommandPredictor** .</span><span class="sxs-lookup"><span data-stu-id="32b28-116">Currently, only the **CommandPredictor** subsystem is supported.</span></span> <span data-ttu-id="32b28-117">Det här del systemet används tillsammans med PSReadLine-modulen för att tillhandahålla anpassade förutsägelse-plugin-program.</span><span class="sxs-lookup"><span data-stu-id="32b28-117">This subsystem is used along with the PSReadLine module to provide custom prediction plugins.</span></span> <span data-ttu-id="32b28-118">I framtiden kan **jobb**, **CommandCompleter**, **fjärr kommunikation** och andra komponenter delas upp i del system sammansättningar utanför `System.Management.Automation.dll` .</span><span class="sxs-lookup"><span data-stu-id="32b28-118">In future, **Job**, **CommandCompleter**, **Remoting** and other components could be separated into subsystem assemblies outside of `System.Management.Automation.dll`.</span></span>

## <span data-ttu-id="32b28-119">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="32b28-119">EXAMPLES</span></span>

### <span data-ttu-id="32b28-120">Exempel 1 – Visa alla tillgängliga under system</span><span class="sxs-lookup"><span data-stu-id="32b28-120">Example 1 - Display all available subsystems</span></span>

```powershell
Get-PSSubsystem
```

```Output
Kind              SubsystemType     IsRegistered Implementations
----              -------------     ------------ ---------------
CommandPredictor  ICommandPredictor        False {}
```

### <span data-ttu-id="32b28-121">Exempel 2 – Visa alla tillgängliga del system av en viss typ</span><span class="sxs-lookup"><span data-stu-id="32b28-121">Example 2 - Display all available subsystems of a specific kind</span></span>

```powershell
PS> Get-PSSubsystem -Kind CommandPredictor | Format-List
```

```Output
Kind                      : CommandPredictor
SubsystemType             : System.Management.Automation.Subsystem.ICommandPredictor
AllowUnregistration       : True
AllowMultipleRegistration : True
RequiredCmdlets           : {}
RequiredFunctions         : {}
IsRegistered              : False
Implementations           : {}
```

## <span data-ttu-id="32b28-122">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="32b28-122">PARAMETERS</span></span>

### <span data-ttu-id="32b28-123">– Typ</span><span class="sxs-lookup"><span data-stu-id="32b28-123">-Kind</span></span>


<span data-ttu-id="32b28-124">Anger vilken typ av under system som ska returneras.</span><span class="sxs-lookup"><span data-stu-id="32b28-124">Specifies the kind of subsystem to be returned.</span></span> <span data-ttu-id="32b28-125">Giltiga värden är: `CommandPredictor` .</span><span class="sxs-lookup"><span data-stu-id="32b28-125">Valid values are: `CommandPredictor`.</span></span>

```yaml
Type: System.Management.Automation.Subsystem.SubsystemKind
Parameter Sets: GetByKindSet
Aliases:
Accepted values: CommandPredictor

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="32b28-126">-SubsystemType</span><span class="sxs-lookup"><span data-stu-id="32b28-126">-SubsystemType</span></span>

<span data-ttu-id="32b28-127">Anger vilken typ av under system som ska returneras.</span><span class="sxs-lookup"><span data-stu-id="32b28-127">Specifies the type of subsystem to be returned.</span></span>

```yaml
Type: System.Type
Parameter Sets: GetByTypeSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="32b28-128">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="32b28-128">CommonParameters</span></span>

<span data-ttu-id="32b28-129">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="32b28-129">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="32b28-130">Mer information finns i [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="32b28-130">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="32b28-131">INDATA</span><span class="sxs-lookup"><span data-stu-id="32b28-131">INPUTS</span></span>

### <span data-ttu-id="32b28-132">System. Management. Automation. Subsystem. SubsystemKind</span><span class="sxs-lookup"><span data-stu-id="32b28-132">System.Management.Automation.Subsystem.SubsystemKind</span></span>

### <span data-ttu-id="32b28-133">System. Type</span><span class="sxs-lookup"><span data-stu-id="32b28-133">System.Type</span></span>

## <span data-ttu-id="32b28-134">UTDATA</span><span class="sxs-lookup"><span data-stu-id="32b28-134">OUTPUTS</span></span>

### <span data-ttu-id="32b28-135">System. Management. Automation. Subsystem. SubsystemInfo</span><span class="sxs-lookup"><span data-stu-id="32b28-135">System.Management.Automation.Subsystem.SubsystemInfo</span></span>

## <span data-ttu-id="32b28-136">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="32b28-136">NOTES</span></span>

## <span data-ttu-id="32b28-137">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="32b28-137">RELATED LINKS</span></span>

[<span data-ttu-id="32b28-138">about_experimental_features</span><span class="sxs-lookup"><span data-stu-id="32b28-138">about_experimental_features</span></span>](about/about_experimental_features.md)

[<span data-ttu-id="32b28-139">Disable-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="32b28-139">Disable-ExperimentalFeature</span></span>](Disable-ExperimentalFeature.md)

[<span data-ttu-id="32b28-140">Aktivera – ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="32b28-140">Enable-ExperimentalFeature</span></span>](Get-ExperimentalFeature.md)

[<span data-ttu-id="32b28-141">Get-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="32b28-141">Get-ExperimentalFeature</span></span>](Get-ExperimentalFeature.md)

[<span data-ttu-id="32b28-142">Använda experimentella funktioner</span><span class="sxs-lookup"><span data-stu-id="32b28-142">Using Experimental Features</span></span>](/powershell/scripting/learn/experimental-features)
