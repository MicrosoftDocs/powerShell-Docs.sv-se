---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/unregister-psrepository?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unregister-PSRepository
ms.openlocfilehash: 908a43506bfbff964cfbdd8eea270b1fa42c3e77
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708579"
---
# <span data-ttu-id="e47a4-102">Unregister-PSRepository</span><span class="sxs-lookup"><span data-stu-id="e47a4-102">Unregister-PSRepository</span></span>

## <span data-ttu-id="e47a4-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="e47a4-103">SYNOPSIS</span></span>
<span data-ttu-id="e47a4-104">Avregistrerar en lagrings plats.</span><span class="sxs-lookup"><span data-stu-id="e47a4-104">Unregisters a repository.</span></span>

## <span data-ttu-id="e47a4-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e47a4-105">SYNTAX</span></span>

```
Unregister-PSRepository [-Name] <String[]> [<CommonParameters>]
```

## <span data-ttu-id="e47a4-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="e47a4-106">DESCRIPTION</span></span>

<span data-ttu-id="e47a4-107">`Unregister-PSRepository`Cmdleten avregistrerar en lagrings plats för den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="e47a4-107">The `Unregister-PSRepository` cmdlet unregisters a repository for the current user.</span></span>

## <span data-ttu-id="e47a4-108">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="e47a4-108">EXAMPLES</span></span>

### <span data-ttu-id="e47a4-109">Exempel 1: avregistrera en lagrings plats</span><span class="sxs-lookup"><span data-stu-id="e47a4-109">Example 1: Unregister a repository</span></span>

<span data-ttu-id="e47a4-110">Det här exemplet avregistrerar lagrings platsen med namnet myNuGetSource.</span><span class="sxs-lookup"><span data-stu-id="e47a4-110">This example unregisters the repository named myNuGetSource.</span></span>

```powershell
Unregister-PSRepository -Name "myNuGetSource"
```

### <span data-ttu-id="e47a4-111">Exempel 2: avregistrera alla databaser</span><span class="sxs-lookup"><span data-stu-id="e47a4-111">Example 2: Unregister all repositories</span></span>

<span data-ttu-id="e47a4-112">Det här exemplet använder `Get-PSRepository` för att hämta alla registrerade databaser och använder pipelinen för att skicka dem till `Unregister-PSRepository` avregistrera dem.</span><span class="sxs-lookup"><span data-stu-id="e47a4-112">This example uses `Get-PSRepository` to get all registered repositories, and uses the pipeline operator to pass them to `Unregister-PSRepository` to unregister them.</span></span>

```powershell
Get-PSRepository | Unregister-PSRepository
```

## <span data-ttu-id="e47a4-113">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="e47a4-113">PARAMETERS</span></span>

### <span data-ttu-id="e47a4-114">-Name</span><span class="sxs-lookup"><span data-stu-id="e47a4-114">-Name</span></span>

<span data-ttu-id="e47a4-115">Anger en matris med namnen på de databaser som ska tas bort.</span><span class="sxs-lookup"><span data-stu-id="e47a4-115">Specifies an array of names of the repositories to remove.</span></span>

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

### <span data-ttu-id="e47a4-116">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e47a4-116">CommonParameters</span></span>

<span data-ttu-id="e47a4-117">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e47a4-117">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e47a4-118">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="e47a4-118">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e47a4-119">INDATA</span><span class="sxs-lookup"><span data-stu-id="e47a4-119">INPUTS</span></span>

### <span data-ttu-id="e47a4-120">System.String[]</span><span class="sxs-lookup"><span data-stu-id="e47a4-120">System.String[]</span></span>

## <span data-ttu-id="e47a4-121">UTDATA</span><span class="sxs-lookup"><span data-stu-id="e47a4-121">OUTPUTS</span></span>

### <span data-ttu-id="e47a4-122">System. Object</span><span class="sxs-lookup"><span data-stu-id="e47a4-122">System.Object</span></span>

## <span data-ttu-id="e47a4-123">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="e47a4-123">NOTES</span></span>

## <span data-ttu-id="e47a4-124">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="e47a4-124">RELATED LINKS</span></span>

[<span data-ttu-id="e47a4-125">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="e47a4-125">Get-PSRepository</span></span>](Get-PSRepository.md)

[<span data-ttu-id="e47a4-126">Registrera – PSRepository</span><span class="sxs-lookup"><span data-stu-id="e47a4-126">Register-PSRepository</span></span>](Register-PSRepository.md)

[<span data-ttu-id="e47a4-127">Set-PSRepository</span><span class="sxs-lookup"><span data-stu-id="e47a4-127">Set-PSRepository</span></span>](Set-PSRepository.md)
