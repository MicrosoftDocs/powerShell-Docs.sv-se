---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Guid
ms.openlocfilehash: 80d30b5c3b33c3e4f8125db3a158166a00f7e816
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/02/2020
ms.locfileid: "93261587"
---
# <span data-ttu-id="8e5b8-103">New-Guid</span><span class="sxs-lookup"><span data-stu-id="8e5b8-103">New-Guid</span></span>

## <span data-ttu-id="8e5b8-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="8e5b8-104">SYNOPSIS</span></span>
<span data-ttu-id="8e5b8-105">Skapar ett GUID.</span><span class="sxs-lookup"><span data-stu-id="8e5b8-105">Creates a GUID.</span></span>

## <span data-ttu-id="8e5b8-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8e5b8-106">SYNTAX</span></span>

```
New-Guid [<CommonParameters>]
```

## <span data-ttu-id="8e5b8-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="8e5b8-107">DESCRIPTION</span></span>

<span data-ttu-id="8e5b8-108">Cmdlet: en **New-GUID** skapar en slumpmässig globalt unik IDENTIFIERARE (GUID).</span><span class="sxs-lookup"><span data-stu-id="8e5b8-108">The **New-Guid** cmdlet creates a random globally unique identifier (GUID).</span></span>
<span data-ttu-id="8e5b8-109">Om du behöver ett unikt ID i ett skript kan du skapa ett GUID om det behövs.</span><span class="sxs-lookup"><span data-stu-id="8e5b8-109">If you need a unique ID in a script, you can create a GUID, as needed.</span></span>

## <span data-ttu-id="8e5b8-110">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="8e5b8-110">EXAMPLES</span></span>

### <span data-ttu-id="8e5b8-111">Exempel 1: skapa en GUID</span><span class="sxs-lookup"><span data-stu-id="8e5b8-111">Example 1: Create a GUID</span></span>

```
PS C:\> New-Guid
Guid
----
0352cf0f-2e7a-4aee-801d-7f27f8344c77
```

<span data-ttu-id="8e5b8-112">Det här kommandot skapar ett slumpmässigt GUID.</span><span class="sxs-lookup"><span data-stu-id="8e5b8-112">This command creates a random GUID.</span></span>
<span data-ttu-id="8e5b8-113">Alternativt kan du lagra utdata från denna cmdlet i en variabel som ska användas någon annan stans i ett skript.</span><span class="sxs-lookup"><span data-stu-id="8e5b8-113">Alternatively, you could store the output of this cmdlet in a variable to use elsewhere in a script.</span></span>

## <span data-ttu-id="8e5b8-114">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="8e5b8-114">PARAMETERS</span></span>

### <span data-ttu-id="8e5b8-115">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8e5b8-115">CommonParameters</span></span>

<span data-ttu-id="8e5b8-116">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="8e5b8-116">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8e5b8-117">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="8e5b8-117">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8e5b8-118">INDATA</span><span class="sxs-lookup"><span data-stu-id="8e5b8-118">INPUTS</span></span>

## <span data-ttu-id="8e5b8-119">UTDATA</span><span class="sxs-lookup"><span data-stu-id="8e5b8-119">OUTPUTS</span></span>

### <span data-ttu-id="8e5b8-120">System. GUID</span><span class="sxs-lookup"><span data-stu-id="8e5b8-120">System.Guid</span></span>

<span data-ttu-id="8e5b8-121">Denna cmdlet returnerar ett GUID.</span><span class="sxs-lookup"><span data-stu-id="8e5b8-121">This cmdlet returns a GUID.</span></span>

## <span data-ttu-id="8e5b8-122">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="8e5b8-122">NOTES</span></span>

## <span data-ttu-id="8e5b8-123">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="8e5b8-123">RELATED LINKS</span></span>