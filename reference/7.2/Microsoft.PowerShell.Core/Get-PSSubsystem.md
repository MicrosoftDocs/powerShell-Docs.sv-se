---
external help file: System.Management.Automation.dll-Help.xml
Module Name: Microsoft.PowerShell.Core
ms.date: 10/15/2020
schema: 2.0.0
ms.openlocfilehash: 5cb8ddbd06f8b7fdbadae0b7c738e26a68ff5c48
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710897"
---
# <span data-ttu-id="1bb90-101">Get-PSSubsystem</span><span class="sxs-lookup"><span data-stu-id="1bb90-101">Get-PSSubsystem</span></span>

## <span data-ttu-id="1bb90-102">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="1bb90-102">SYNOPSIS</span></span>
<span data-ttu-id="1bb90-103">Hämtar information om de under system som registrerats i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1bb90-103">Retrieves information about the subsystems registered in PowerShell.</span></span>

## <span data-ttu-id="1bb90-104">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="1bb90-104">SYNTAX</span></span>

### <span data-ttu-id="1bb90-105">GetAllSet (standard)</span><span class="sxs-lookup"><span data-stu-id="1bb90-105">GetAllSet (Default)</span></span>

```
Get-PSSubsystem [<CommonParameters>]
```

### <span data-ttu-id="1bb90-106">GetByKindSet</span><span class="sxs-lookup"><span data-stu-id="1bb90-106">GetByKindSet</span></span>

```
Get-PSSubsystem -Kind <SubsystemKind> [<CommonParameters>]
```

### <span data-ttu-id="1bb90-107">GetByTypeSet</span><span class="sxs-lookup"><span data-stu-id="1bb90-107">GetByTypeSet</span></span>

```
Get-PSSubsystem -SubsystemType <Type> [<CommonParameters>]
```

## <span data-ttu-id="1bb90-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="1bb90-108">DESCRIPTION</span></span>

<span data-ttu-id="1bb90-109">Hämtar information om de under system som registrerats i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1bb90-109">Retrieves information about the subsystems registered in PowerShell.</span></span>

> [!NOTE]
> <span data-ttu-id="1bb90-110">Det här är en experimentell funktion.</span><span class="sxs-lookup"><span data-stu-id="1bb90-110">This is an experimental feature.</span></span> <span data-ttu-id="1bb90-111">Den här cmdleten är endast tillgänglig om `PSSubsystemPluginModel` funktionen är aktive rad.</span><span class="sxs-lookup"><span data-stu-id="1bb90-111">This cmdlet is only available when the `PSSubsystemPluginModel` feature is enabled.</span></span> <span data-ttu-id="1bb90-112">Mer information finns i [använda experimentella funktioner](/powershell/scripting/learn/experimental-features).</span><span class="sxs-lookup"><span data-stu-id="1bb90-112">For more information, see [Using Experimental Features](/powershell/scripting/learn/experimental-features).</span></span>

<span data-ttu-id="1bb90-113">Funktionen gör det möjligt att separera komponenter i `System.Management.Automation.dll` enskilda under system som finns i en egen sammansättning.</span><span class="sxs-lookup"><span data-stu-id="1bb90-113">The feature makes it possible to separate components of `System.Management.Automation.dll` into individual subsystems that reside in their own assembly.</span></span> <span data-ttu-id="1bb90-114">Den här separationen minskar den grundläggande PowerShell-motorns disk utrymme och gör att dessa komponenter blir valfria funktioner för en minimal PowerShell-installation.</span><span class="sxs-lookup"><span data-stu-id="1bb90-114">This separation reduces the disk footprint of the core PowerShell engine and allows these components to become optional features for a minimal PowerShell installation.</span></span>

<span data-ttu-id="1bb90-115">För närvarande stöds endast under systemet **CommandPredictor** .</span><span class="sxs-lookup"><span data-stu-id="1bb90-115">Currently, only the **CommandPredictor** subsystem is supported.</span></span> <span data-ttu-id="1bb90-116">Det här del systemet används tillsammans med PSReadLine-modulen för att tillhandahålla anpassade förutsägelse-plugin-program.</span><span class="sxs-lookup"><span data-stu-id="1bb90-116">This subsystem is used along with the PSReadLine module to provide custom prediction plugins.</span></span> <span data-ttu-id="1bb90-117">I framtiden kan **jobb**, **CommandCompleter**, **fjärr kommunikation** och andra komponenter delas upp i del system sammansättningar utanför `System.Management.Automation.dll` .</span><span class="sxs-lookup"><span data-stu-id="1bb90-117">In future, **Job**, **CommandCompleter**, **Remoting** and other components could be separated into subsystem assemblies outside of `System.Management.Automation.dll`.</span></span>

## <span data-ttu-id="1bb90-118">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="1bb90-118">EXAMPLES</span></span>

### <span data-ttu-id="1bb90-119">Exempel 1 – Visa alla tillgängliga under system</span><span class="sxs-lookup"><span data-stu-id="1bb90-119">Example 1 - Display all available subsystems</span></span>

```powershell
Get-PSSubsystem
```

```Output
Kind              SubsystemType     IsRegistered Implementations
----              -------------     ------------ ---------------
CommandPredictor  ICommandPredictor        False {}
```

### <span data-ttu-id="1bb90-120">Exempel 2 – Visa alla tillgängliga del system av en viss typ</span><span class="sxs-lookup"><span data-stu-id="1bb90-120">Example 2 - Display all available subsystems of a specific kind</span></span>

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

## <span data-ttu-id="1bb90-121">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="1bb90-121">PARAMETERS</span></span>

### <span data-ttu-id="1bb90-122">– Typ</span><span class="sxs-lookup"><span data-stu-id="1bb90-122">-Kind</span></span>


<span data-ttu-id="1bb90-123">Anger vilken typ av under system som ska returneras.</span><span class="sxs-lookup"><span data-stu-id="1bb90-123">Specifies the kind of subsystem to be returned.</span></span> <span data-ttu-id="1bb90-124">Giltiga värden är: `CommandPredictor` .</span><span class="sxs-lookup"><span data-stu-id="1bb90-124">Valid values are: `CommandPredictor`.</span></span>

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

### <span data-ttu-id="1bb90-125">-SubsystemType</span><span class="sxs-lookup"><span data-stu-id="1bb90-125">-SubsystemType</span></span>

<span data-ttu-id="1bb90-126">Anger vilken typ av under system som ska returneras.</span><span class="sxs-lookup"><span data-stu-id="1bb90-126">Specifies the type of subsystem to be returned.</span></span>

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

### <span data-ttu-id="1bb90-127">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1bb90-127">CommonParameters</span></span>

<span data-ttu-id="1bb90-128">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1bb90-128">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1bb90-129">Mer information finns i [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="1bb90-129">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1bb90-130">INDATA</span><span class="sxs-lookup"><span data-stu-id="1bb90-130">INPUTS</span></span>

### <span data-ttu-id="1bb90-131">System. Management. Automation. Subsystem. SubsystemKind</span><span class="sxs-lookup"><span data-stu-id="1bb90-131">System.Management.Automation.Subsystem.SubsystemKind</span></span>

### <span data-ttu-id="1bb90-132">System. Type</span><span class="sxs-lookup"><span data-stu-id="1bb90-132">System.Type</span></span>

## <span data-ttu-id="1bb90-133">UTDATA</span><span class="sxs-lookup"><span data-stu-id="1bb90-133">OUTPUTS</span></span>

### <span data-ttu-id="1bb90-134">System. Management. Automation. Subsystem. SubsystemInfo</span><span class="sxs-lookup"><span data-stu-id="1bb90-134">System.Management.Automation.Subsystem.SubsystemInfo</span></span>

## <span data-ttu-id="1bb90-135">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="1bb90-135">NOTES</span></span>

## <span data-ttu-id="1bb90-136">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="1bb90-136">RELATED LINKS</span></span>

[<span data-ttu-id="1bb90-137">about_experimental_features</span><span class="sxs-lookup"><span data-stu-id="1bb90-137">about_experimental_features</span></span>](about/about_experimental_features.md)

[<span data-ttu-id="1bb90-138">Disable-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="1bb90-138">Disable-ExperimentalFeature</span></span>](Disable-ExperimentalFeature.md)

[<span data-ttu-id="1bb90-139">Aktivera – ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="1bb90-139">Enable-ExperimentalFeature</span></span>](Get-ExperimentalFeature.md)

[<span data-ttu-id="1bb90-140">Get-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="1bb90-140">Get-ExperimentalFeature</span></span>](Get-ExperimentalFeature.md)

[<span data-ttu-id="1bb90-141">Använda experimentella funktioner</span><span class="sxs-lookup"><span data-stu-id="1bb90-141">Using Experimental Features</span></span>](/powershell/scripting/learn/experimental-features)
