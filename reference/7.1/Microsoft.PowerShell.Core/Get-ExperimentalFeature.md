---
external help file: System.Management.Automation.dll-Help.xml
Module Name: Microsoft.PowerShell.Core
ms.date: 03/01/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-experimentalfeature?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ExperimentalFeature
ms.openlocfilehash: 2d91c36c6fd6d2e1281fdadf95c3b83e27c36f60
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93267830"
---
# <span data-ttu-id="733b9-102">Get-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="733b9-102">Get-ExperimentalFeature</span></span>

## <span data-ttu-id="733b9-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="733b9-103">SYNOPSIS</span></span>
<span data-ttu-id="733b9-104">Hämtar experimentella funktioner.</span><span class="sxs-lookup"><span data-stu-id="733b9-104">Gets experimental features.</span></span>

## <span data-ttu-id="733b9-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="733b9-105">SYNTAX</span></span>

```
Get-ExperimentalFeature [[-Name] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="733b9-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="733b9-106">DESCRIPTION</span></span>

<span data-ttu-id="733b9-107">`Get-ExperimentalFeature`Cmdleten returnerar alla experimentella funktioner som identifieras av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="733b9-107">The `Get-ExperimentalFeature` cmdlet returns all experimental features discovered by PowerShell.</span></span>
<span data-ttu-id="733b9-108">Experimentella funktioner kan komma från moduler eller PowerShell-motorn.</span><span class="sxs-lookup"><span data-stu-id="733b9-108">Experimental features can come from modules or the PowerShell engine.</span></span> <span data-ttu-id="733b9-109">Experimentella funktioner gör det möjligt för användare att på ett säkert sätt testa nya funktioner och ge feedback (vanligt vis via GitHub) innan designen anses vara fullständig och eventuella ändringar kan bli en brytande ändring.</span><span class="sxs-lookup"><span data-stu-id="733b9-109">Experimental features allow users to safely test new features and provide feedback (typically via GitHub) before the design is considered complete and any changes can become a breaking change.</span></span>

## <span data-ttu-id="733b9-110">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="733b9-110">EXAMPLES</span></span>

### <span data-ttu-id="733b9-111">Exempel 1</span><span class="sxs-lookup"><span data-stu-id="733b9-111">Example 1</span></span>

<span data-ttu-id="733b9-112">Hämtar listan över aktuella registrerade experimentella funktioner och deras aktuella status.</span><span class="sxs-lookup"><span data-stu-id="733b9-112">Gets the list of currently registered experimental features and their current state.</span></span>

```powershell
Get-ExperimentalFeature
```

```Output
Name                         Enabled Source      Description
----                         ------- ------      -----------
PSImplicitRemotingBatching   False PSEngine      Batch implicit remoting proxy commands to improve performance
```

## <span data-ttu-id="733b9-113">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="733b9-113">PARAMETERS</span></span>

### <span data-ttu-id="733b9-114">-Name</span><span class="sxs-lookup"><span data-stu-id="733b9-114">-Name</span></span>

<span data-ttu-id="733b9-115">Namn eller namn på de speciella experimentella funktioner som ska returneras.</span><span class="sxs-lookup"><span data-stu-id="733b9-115">Name or names of specific experimental features to return.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="733b9-116">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="733b9-116">CommonParameters</span></span>

<span data-ttu-id="733b9-117">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="733b9-117">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="733b9-118">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="733b9-118">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="733b9-119">INDATA</span><span class="sxs-lookup"><span data-stu-id="733b9-119">INPUTS</span></span>

### <span data-ttu-id="733b9-120">System.String[]</span><span class="sxs-lookup"><span data-stu-id="733b9-120">System.String[]</span></span>

<span data-ttu-id="733b9-121">Namn eller namn på experimentella funktioner att returnera.</span><span class="sxs-lookup"><span data-stu-id="733b9-121">Name or names of experimental features to return.</span></span>

## <span data-ttu-id="733b9-122">UTDATA</span><span class="sxs-lookup"><span data-stu-id="733b9-122">OUTPUTS</span></span>

### <span data-ttu-id="733b9-123">ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="733b9-123">ExperimentalFeature</span></span>

<span data-ttu-id="733b9-124">Returnerar instanser som matchar de begärda namnen eller alla experimentella funktioner om inget namn har angetts.</span><span class="sxs-lookup"><span data-stu-id="733b9-124">Returns instances that match the requested names or all experimental features if no name is specified.</span></span>

## <span data-ttu-id="733b9-125">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="733b9-125">RELATED LINKS</span></span>

[<span data-ttu-id="733b9-126">Disable-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="733b9-126">Disable-ExperimentalFeature</span></span>](Disable-ExperimentalFeature.md)

[<span data-ttu-id="733b9-127">Aktivera – ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="733b9-127">Enable-ExperimentalFeature</span></span>](Enable-ExperimentalFeature.md)

