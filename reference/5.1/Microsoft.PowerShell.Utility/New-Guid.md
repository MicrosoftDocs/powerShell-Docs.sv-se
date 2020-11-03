---
external help file: Microsoft.PowerShell.Utility-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Guid
ms.openlocfilehash: 6e8903d6ee1b9bb38c42abd866a1657e86d2f3ac
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/02/2020
ms.locfileid: "93261535"
---
# <span data-ttu-id="54d0b-103">New-Guid</span><span class="sxs-lookup"><span data-stu-id="54d0b-103">New-Guid</span></span>

## <span data-ttu-id="54d0b-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="54d0b-104">SYNOPSIS</span></span>
<span data-ttu-id="54d0b-105">Skapar ett GUID.</span><span class="sxs-lookup"><span data-stu-id="54d0b-105">Creates a GUID.</span></span>

## <span data-ttu-id="54d0b-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="54d0b-106">SYNTAX</span></span>

```
New-Guid [<CommonParameters>]
```

## <span data-ttu-id="54d0b-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="54d0b-107">DESCRIPTION</span></span>
<span data-ttu-id="54d0b-108">Cmdlet: en **New-GUID** skapar en slumpmässig globalt unik IDENTIFIERARE (GUID).</span><span class="sxs-lookup"><span data-stu-id="54d0b-108">The **New-Guid** cmdlet creates a random globally unique identifier (GUID).</span></span>
<span data-ttu-id="54d0b-109">Om du behöver ett unikt ID i ett skript kan du skapa ett GUID om det behövs.</span><span class="sxs-lookup"><span data-stu-id="54d0b-109">If you need a unique ID in a script, you can create a GUID, as needed.</span></span>

## <span data-ttu-id="54d0b-110">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="54d0b-110">EXAMPLES</span></span>

### <span data-ttu-id="54d0b-111">Exempel 1: skapa en GUID</span><span class="sxs-lookup"><span data-stu-id="54d0b-111">Example 1: Create a GUID</span></span>

```
PS C:\> New-Guid
Guid
----
0352cf0f-2e7a-4aee-801d-7f27f8344c77
```

<span data-ttu-id="54d0b-112">Det här kommandot skapar ett slumpmässigt GUID.</span><span class="sxs-lookup"><span data-stu-id="54d0b-112">This command creates a random GUID.</span></span>
<span data-ttu-id="54d0b-113">Alternativt kan du lagra utdata från denna cmdlet i en variabel som ska användas någon annan stans i ett skript.</span><span class="sxs-lookup"><span data-stu-id="54d0b-113">Alternatively, you could store the output of this cmdlet in a variable to use elsewhere in a script.</span></span>

## <span data-ttu-id="54d0b-114">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="54d0b-114">PARAMETERS</span></span>

### <span data-ttu-id="54d0b-115">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="54d0b-115">CommonParameters</span></span>
<span data-ttu-id="54d0b-116">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="54d0b-116">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="54d0b-117">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="54d0b-117">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="54d0b-118">INDATA</span><span class="sxs-lookup"><span data-stu-id="54d0b-118">INPUTS</span></span>

## <span data-ttu-id="54d0b-119">UTDATA</span><span class="sxs-lookup"><span data-stu-id="54d0b-119">OUTPUTS</span></span>

### <span data-ttu-id="54d0b-120">System. GUID</span><span class="sxs-lookup"><span data-stu-id="54d0b-120">System.Guid</span></span>
<span data-ttu-id="54d0b-121">Denna cmdlet returnerar ett GUID.</span><span class="sxs-lookup"><span data-stu-id="54d0b-121">This cmdlet returns a GUID.</span></span>

## <span data-ttu-id="54d0b-122">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="54d0b-122">NOTES</span></span>

## <span data-ttu-id="54d0b-123">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="54d0b-123">RELATED LINKS</span></span>