---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/unregister-psrepository?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unregister-PSRepository
ms.openlocfilehash: 0f1173cbfab139438d55ff49272f9625579820dc
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93263120"
---
# <span data-ttu-id="adf3e-103">Unregister-PSRepository</span><span class="sxs-lookup"><span data-stu-id="adf3e-103">Unregister-PSRepository</span></span>

## <span data-ttu-id="adf3e-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="adf3e-104">SYNOPSIS</span></span>
<span data-ttu-id="adf3e-105">Avregistrerar en lagrings plats.</span><span class="sxs-lookup"><span data-stu-id="adf3e-105">Unregisters a repository.</span></span>

## <span data-ttu-id="adf3e-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="adf3e-106">SYNTAX</span></span>

```
Unregister-PSRepository [-Name] <String[]> [<CommonParameters>]
```

## <span data-ttu-id="adf3e-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="adf3e-107">DESCRIPTION</span></span>

<span data-ttu-id="adf3e-108">`Unregister-PSRepository`Cmdleten avregistrerar en lagrings plats för den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="adf3e-108">The `Unregister-PSRepository` cmdlet unregisters a repository for the current user.</span></span>

## <span data-ttu-id="adf3e-109">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="adf3e-109">EXAMPLES</span></span>

### <span data-ttu-id="adf3e-110">Exempel 1: avregistrera en lagrings plats</span><span class="sxs-lookup"><span data-stu-id="adf3e-110">Example 1: Unregister a repository</span></span>

<span data-ttu-id="adf3e-111">Det här exemplet avregistrerar lagrings platsen med namnet myNuGetSource.</span><span class="sxs-lookup"><span data-stu-id="adf3e-111">This example unregisters the repository named myNuGetSource.</span></span>

```powershell
Unregister-PSRepository -Name "myNuGetSource"
```

### <span data-ttu-id="adf3e-112">Exempel 2: avregistrera alla databaser</span><span class="sxs-lookup"><span data-stu-id="adf3e-112">Example 2: Unregister all repositories</span></span>

<span data-ttu-id="adf3e-113">Det här exemplet använder `Get-PSRepository` för att hämta alla registrerade databaser och använder pipelinen för att skicka dem till `Unregister-PSRepository` avregistrera dem.</span><span class="sxs-lookup"><span data-stu-id="adf3e-113">This example uses `Get-PSRepository` to get all registered repositories, and uses the pipeline operator to pass them to `Unregister-PSRepository` to unregister them.</span></span>

```powershell
Get-PSRepository | Unregister-PSRepository
```

## <span data-ttu-id="adf3e-114">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="adf3e-114">PARAMETERS</span></span>

### <span data-ttu-id="adf3e-115">-Name</span><span class="sxs-lookup"><span data-stu-id="adf3e-115">-Name</span></span>

<span data-ttu-id="adf3e-116">Anger en matris med namnen på de databaser som ska tas bort.</span><span class="sxs-lookup"><span data-stu-id="adf3e-116">Specifies an array of names of the repositories to remove.</span></span>

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

### <span data-ttu-id="adf3e-117">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="adf3e-117">CommonParameters</span></span>

<span data-ttu-id="adf3e-118">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="adf3e-118">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="adf3e-119">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="adf3e-119">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="adf3e-120">INDATA</span><span class="sxs-lookup"><span data-stu-id="adf3e-120">INPUTS</span></span>

### <span data-ttu-id="adf3e-121">System.String[]</span><span class="sxs-lookup"><span data-stu-id="adf3e-121">System.String[]</span></span>

## <span data-ttu-id="adf3e-122">UTDATA</span><span class="sxs-lookup"><span data-stu-id="adf3e-122">OUTPUTS</span></span>

### <span data-ttu-id="adf3e-123">System. Object</span><span class="sxs-lookup"><span data-stu-id="adf3e-123">System.Object</span></span>

## <span data-ttu-id="adf3e-124">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="adf3e-124">NOTES</span></span>

## <span data-ttu-id="adf3e-125">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="adf3e-125">RELATED LINKS</span></span>

[<span data-ttu-id="adf3e-126">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="adf3e-126">Get-PSRepository</span></span>](Get-PSRepository.md)

[<span data-ttu-id="adf3e-127">Registrera – PSRepository</span><span class="sxs-lookup"><span data-stu-id="adf3e-127">Register-PSRepository</span></span>](Register-PSRepository.md)

[<span data-ttu-id="adf3e-128">Set-PSRepository</span><span class="sxs-lookup"><span data-stu-id="adf3e-128">Set-PSRepository</span></span>](Set-PSRepository.md)
