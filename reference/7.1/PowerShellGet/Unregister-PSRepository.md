---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/unregister-psrepository?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unregister-PSRepository
ms.openlocfilehash: 769d1ac91cbbc580b3488ba84d14a759b6ef65d4
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265580"
---
# <span data-ttu-id="5cb61-103">Unregister-PSRepository</span><span class="sxs-lookup"><span data-stu-id="5cb61-103">Unregister-PSRepository</span></span>

## <span data-ttu-id="5cb61-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="5cb61-104">SYNOPSIS</span></span>
<span data-ttu-id="5cb61-105">Avregistrerar en lagrings plats.</span><span class="sxs-lookup"><span data-stu-id="5cb61-105">Unregisters a repository.</span></span>

## <span data-ttu-id="5cb61-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="5cb61-106">SYNTAX</span></span>

```
Unregister-PSRepository [-Name] <String[]> [<CommonParameters>]
```

## <span data-ttu-id="5cb61-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="5cb61-107">DESCRIPTION</span></span>

<span data-ttu-id="5cb61-108">`Unregister-PSRepository`Cmdleten avregistrerar en lagrings plats för den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="5cb61-108">The `Unregister-PSRepository` cmdlet unregisters a repository for the current user.</span></span>

## <span data-ttu-id="5cb61-109">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="5cb61-109">EXAMPLES</span></span>

### <span data-ttu-id="5cb61-110">Exempel 1: avregistrera en lagrings plats</span><span class="sxs-lookup"><span data-stu-id="5cb61-110">Example 1: Unregister a repository</span></span>

<span data-ttu-id="5cb61-111">Det här exemplet avregistrerar lagrings platsen med namnet myNuGetSource.</span><span class="sxs-lookup"><span data-stu-id="5cb61-111">This example unregisters the repository named myNuGetSource.</span></span>

```powershell
Unregister-PSRepository -Name "myNuGetSource"
```

### <span data-ttu-id="5cb61-112">Exempel 2: avregistrera alla databaser</span><span class="sxs-lookup"><span data-stu-id="5cb61-112">Example 2: Unregister all repositories</span></span>

<span data-ttu-id="5cb61-113">Det här exemplet använder `Get-PSRepository` för att hämta alla registrerade databaser och använder pipelinen för att skicka dem till `Unregister-PSRepository` avregistrera dem.</span><span class="sxs-lookup"><span data-stu-id="5cb61-113">This example uses `Get-PSRepository` to get all registered repositories, and uses the pipeline operator to pass them to `Unregister-PSRepository` to unregister them.</span></span>

```powershell
Get-PSRepository | Unregister-PSRepository
```

## <span data-ttu-id="5cb61-114">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="5cb61-114">PARAMETERS</span></span>

### <span data-ttu-id="5cb61-115">-Name</span><span class="sxs-lookup"><span data-stu-id="5cb61-115">-Name</span></span>

<span data-ttu-id="5cb61-116">Anger en matris med namnen på de databaser som ska tas bort.</span><span class="sxs-lookup"><span data-stu-id="5cb61-116">Specifies an array of names of the repositories to remove.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="5cb61-117">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5cb61-117">CommonParameters</span></span>

<span data-ttu-id="5cb61-118">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="5cb61-118">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5cb61-119">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="5cb61-119">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5cb61-120">INDATA</span><span class="sxs-lookup"><span data-stu-id="5cb61-120">INPUTS</span></span>

### <span data-ttu-id="5cb61-121">System.String[]</span><span class="sxs-lookup"><span data-stu-id="5cb61-121">System.String[]</span></span>

## <span data-ttu-id="5cb61-122">UTDATA</span><span class="sxs-lookup"><span data-stu-id="5cb61-122">OUTPUTS</span></span>

### <span data-ttu-id="5cb61-123">System. Object</span><span class="sxs-lookup"><span data-stu-id="5cb61-123">System.Object</span></span>

## <span data-ttu-id="5cb61-124">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="5cb61-124">NOTES</span></span>

## <span data-ttu-id="5cb61-125">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="5cb61-125">RELATED LINKS</span></span>

[<span data-ttu-id="5cb61-126">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="5cb61-126">Get-PSRepository</span></span>](Get-PSRepository.md)

[<span data-ttu-id="5cb61-127">Registrera – PSRepository</span><span class="sxs-lookup"><span data-stu-id="5cb61-127">Register-PSRepository</span></span>](Register-PSRepository.md)

[<span data-ttu-id="5cb61-128">Set-PSRepository</span><span class="sxs-lookup"><span data-stu-id="5cb61-128">Set-PSRepository</span></span>](Set-PSRepository.md)
