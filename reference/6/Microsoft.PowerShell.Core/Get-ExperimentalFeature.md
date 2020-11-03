---
external help file: System.Management.Automation.dll-Help.xml
Module Name: Microsoft.PowerShell.Core
ms.date: 03/01/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-experimentalfeature?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ExperimentalFeature
ms.openlocfilehash: 993cc47f9c95fc39d717bb3b76b3de01f16ad47e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93267465"
---
# <span data-ttu-id="0edb6-102">Get-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="0edb6-102">Get-ExperimentalFeature</span></span>

## <span data-ttu-id="0edb6-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="0edb6-103">SYNOPSIS</span></span>
<span data-ttu-id="0edb6-104">Hämtar experimentella funktioner.</span><span class="sxs-lookup"><span data-stu-id="0edb6-104">Gets experimental features.</span></span>

## <span data-ttu-id="0edb6-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="0edb6-105">SYNTAX</span></span>

```
Get-ExperimentalFeature [[-Name] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="0edb6-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="0edb6-106">DESCRIPTION</span></span>

<span data-ttu-id="0edb6-107">`Get-ExperimentalFeature`Cmdleten returnerar alla experimentella funktioner som identifieras av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0edb6-107">The `Get-ExperimentalFeature` cmdlet returns all experimental features discovered by PowerShell.</span></span>
<span data-ttu-id="0edb6-108">Experimentella funktioner kan komma från moduler eller PowerShell-motorn.</span><span class="sxs-lookup"><span data-stu-id="0edb6-108">Experimental features can come from modules or the PowerShell engine.</span></span> <span data-ttu-id="0edb6-109">Experimentella funktioner gör det möjligt för användare att på ett säkert sätt testa nya funktioner och ge feedback (vanligt vis via GitHub) innan designen anses vara fullständig och eventuella ändringar kan bli en brytande ändring.</span><span class="sxs-lookup"><span data-stu-id="0edb6-109">Experimental features allow users to safely test new features and provide feedback (typically via GitHub) before the design is considered complete and any changes can become a breaking change.</span></span>

## <span data-ttu-id="0edb6-110">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="0edb6-110">EXAMPLES</span></span>

### <span data-ttu-id="0edb6-111">Exempel 1</span><span class="sxs-lookup"><span data-stu-id="0edb6-111">Example 1</span></span>

<span data-ttu-id="0edb6-112">Hämtar listan över aktuella registrerade experimentella funktioner och deras aktuella status.</span><span class="sxs-lookup"><span data-stu-id="0edb6-112">Gets the list of currently registered experimental features and their current state.</span></span>

```powershell
Get-ExperimentalFeature
```

```Output
Name                         Enabled Source      Description
----                         ------- ------      -----------
PSImplicitRemotingBatching   False PSEngine      Batch implicit remoting proxy commands to improve performance
```

## <span data-ttu-id="0edb6-113">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="0edb6-113">PARAMETERS</span></span>

### <span data-ttu-id="0edb6-114">-Name</span><span class="sxs-lookup"><span data-stu-id="0edb6-114">-Name</span></span>

<span data-ttu-id="0edb6-115">Namn eller namn på de speciella experimentella funktioner som ska returneras.</span><span class="sxs-lookup"><span data-stu-id="0edb6-115">Name or names of specific experimental features to return.</span></span>

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

### <span data-ttu-id="0edb6-116">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0edb6-116">CommonParameters</span></span>

<span data-ttu-id="0edb6-117">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="0edb6-117">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0edb6-118">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="0edb6-118">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="0edb6-119">INDATA</span><span class="sxs-lookup"><span data-stu-id="0edb6-119">INPUTS</span></span>

### <span data-ttu-id="0edb6-120">System.String[]</span><span class="sxs-lookup"><span data-stu-id="0edb6-120">System.String[]</span></span>

<span data-ttu-id="0edb6-121">Namn eller namn på experimentella funktioner att returnera.</span><span class="sxs-lookup"><span data-stu-id="0edb6-121">Name or names of experimental features to return.</span></span>

## <span data-ttu-id="0edb6-122">UTDATA</span><span class="sxs-lookup"><span data-stu-id="0edb6-122">OUTPUTS</span></span>

### <span data-ttu-id="0edb6-123">ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="0edb6-123">ExperimentalFeature</span></span>

<span data-ttu-id="0edb6-124">Returnerar instanser som matchar de begärda namnen eller alla experimentella funktioner om inget namn har angetts.</span><span class="sxs-lookup"><span data-stu-id="0edb6-124">Returns instances that match the requested names or all experimental features if no name is specified.</span></span>

## <span data-ttu-id="0edb6-125">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="0edb6-125">NOTES</span></span>

## <span data-ttu-id="0edb6-126">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="0edb6-126">RELATED LINKS</span></span>

[<span data-ttu-id="0edb6-127">Disable-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="0edb6-127">Disable-ExperimentalFeature</span></span>](Disable-ExperimentalFeature.md)

[<span data-ttu-id="0edb6-128">Aktivera – ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="0edb6-128">Enable-ExperimentalFeature</span></span>](Enable-ExperimentalFeature.md)
