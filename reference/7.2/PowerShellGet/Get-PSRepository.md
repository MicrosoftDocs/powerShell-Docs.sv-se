---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/get-psrepository?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSRepository
ms.openlocfilehash: 66f840d99b107da22b6771e6327ab68d33a1b368
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710284"
---
# <span data-ttu-id="75fcf-102">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="75fcf-102">Get-PSRepository</span></span>

## <span data-ttu-id="75fcf-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="75fcf-103">SYNOPSIS</span></span>
<span data-ttu-id="75fcf-104">Hämtar PowerShell-databaser.</span><span class="sxs-lookup"><span data-stu-id="75fcf-104">Gets PowerShell repositories.</span></span>

## <span data-ttu-id="75fcf-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="75fcf-105">SYNTAX</span></span>

```
Get-PSRepository [[-Name] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="75fcf-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="75fcf-106">DESCRIPTION</span></span>

<span data-ttu-id="75fcf-107">Cmdlet **: en get-PSRepository** hämtar PowerShell-modulens databaser som är registrerade för den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="75fcf-107">The **Get-PSRepository** cmdlet gets PowerShell module repositories that are registered for the current user.</span></span>

## <span data-ttu-id="75fcf-108">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="75fcf-108">EXAMPLES</span></span>

### <span data-ttu-id="75fcf-109">Exempel 1: Hämta alla modul databaser</span><span class="sxs-lookup"><span data-stu-id="75fcf-109">Example 1: Get all module repositories</span></span>

```
PS C:\> Get-PSRepository
Name                                     SourceLocation                                     OneGetProvider       InstallationPolicy
----                                     --------------                                     --------------       ------------------
PSGallery                                http://go.micro...                                 NuGet                Untrusted
myNuGetSource                            https://myget.c...                                 NuGet                Trusted
```

<span data-ttu-id="75fcf-110">Det här kommandot hämtar alla modul-dataarkiv som registrerats för den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="75fcf-110">This command gets all module repositories registered for the current user.</span></span>

### <span data-ttu-id="75fcf-111">Exempel 2: Hämta modul Arkiv efter namn</span><span class="sxs-lookup"><span data-stu-id="75fcf-111">Example 2: Get module repositories by name</span></span>

```
PS C:\> Get-PSRepository -Name "*NuGet*"
```

<span data-ttu-id="75fcf-112">Det här kommandot hämtar alla modulblad som innehåller NuGet i sina namn.</span><span class="sxs-lookup"><span data-stu-id="75fcf-112">This command gets all module repositories that include NuGet in their names.</span></span>

### <span data-ttu-id="75fcf-113">Exempel 3: Hämta en modul-lagringsplats och formatera utdata</span><span class="sxs-lookup"><span data-stu-id="75fcf-113">Example 3: Get a module repository and format the output</span></span>

```
PS C:\> Get-PSRepository -Name "Local01" | Format-List * -Force
Name                      : local01
SourceLocation            : http://manikb-dev:8765/api/v2/
Trusted                   : True
Registered                : True
InstallationPolicy        : Trusted
PackageManagementProvider : NuGet
PublishLocation           : http://pattif-dev:8765/api/v2/package/
ScriptSourceLocation      : http://pattif-dev:8765/api/v2/artifacts/psscript
ScriptPublishLocation     : http://pattif-dev:8765/api/v2/package/
ProviderOptions           : {}
```

<span data-ttu-id="75fcf-114">Det här kommandot hämtar lagrings platsen med namnet Local01 och använder pipelinen-operatorn för att skicka objektet till Format-List-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="75fcf-114">This command gets the repository named Local01 and uses the pipeline operator to pass that object to the Format-List cmdlet.</span></span>

## <span data-ttu-id="75fcf-115">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="75fcf-115">PARAMETERS</span></span>

### <span data-ttu-id="75fcf-116">-Name</span><span class="sxs-lookup"><span data-stu-id="75fcf-116">-Name</span></span>

<span data-ttu-id="75fcf-117">Anger namnen på de databaser som ska hämtas.</span><span class="sxs-lookup"><span data-stu-id="75fcf-117">Specifies the names of the repositories to get.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="75fcf-118">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="75fcf-118">CommonParameters</span></span>

<span data-ttu-id="75fcf-119">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="75fcf-119">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="75fcf-120">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="75fcf-120">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="75fcf-121">INDATA</span><span class="sxs-lookup"><span data-stu-id="75fcf-121">INPUTS</span></span>

### <span data-ttu-id="75fcf-122">System.String[]</span><span class="sxs-lookup"><span data-stu-id="75fcf-122">System.String[]</span></span>

## <span data-ttu-id="75fcf-123">UTDATA</span><span class="sxs-lookup"><span data-stu-id="75fcf-123">OUTPUTS</span></span>

### <span data-ttu-id="75fcf-124">System. Object</span><span class="sxs-lookup"><span data-stu-id="75fcf-124">System.Object</span></span>

## <span data-ttu-id="75fcf-125">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="75fcf-125">NOTES</span></span>

## <span data-ttu-id="75fcf-126">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="75fcf-126">RELATED LINKS</span></span>

[<span data-ttu-id="75fcf-127">Registrera – PSRepository</span><span class="sxs-lookup"><span data-stu-id="75fcf-127">Register-PSRepository</span></span>](Register-PSRepository.md)

[<span data-ttu-id="75fcf-128">Set-PSRepository</span><span class="sxs-lookup"><span data-stu-id="75fcf-128">Set-PSRepository</span></span>](Set-PSRepository.md)

[<span data-ttu-id="75fcf-129">Avregistrera-PSRepository</span><span class="sxs-lookup"><span data-stu-id="75fcf-129">Unregister-PSRepository</span></span>](Unregister-PSRepository.md)

