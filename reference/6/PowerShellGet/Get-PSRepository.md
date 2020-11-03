---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/get-psrepository?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSRepository
ms.openlocfilehash: b4d786cdac183917428b0846ad3c88d41b083ac5
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266552"
---
# <span data-ttu-id="4a3a3-103">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="4a3a3-103">Get-PSRepository</span></span>

## <span data-ttu-id="4a3a3-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="4a3a3-104">SYNOPSIS</span></span>
<span data-ttu-id="4a3a3-105">Hämtar PowerShell-databaser.</span><span class="sxs-lookup"><span data-stu-id="4a3a3-105">Gets PowerShell repositories.</span></span>

## <span data-ttu-id="4a3a3-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4a3a3-106">SYNTAX</span></span>

```
Get-PSRepository [[-Name] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="4a3a3-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="4a3a3-107">DESCRIPTION</span></span>

<span data-ttu-id="4a3a3-108">Cmdlet **: en get-PSRepository** hämtar PowerShell-modulens databaser som är registrerade för den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="4a3a3-108">The **Get-PSRepository** cmdlet gets PowerShell module repositories that are registered for the current user.</span></span>

## <span data-ttu-id="4a3a3-109">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="4a3a3-109">EXAMPLES</span></span>

### <span data-ttu-id="4a3a3-110">Exempel 1: Hämta alla modul databaser</span><span class="sxs-lookup"><span data-stu-id="4a3a3-110">Example 1: Get all module repositories</span></span>

```
PS C:\> Get-PSRepository
Name                                     SourceLocation                                     OneGetProvider       InstallationPolicy
----                                     --------------                                     --------------       ------------------
PSGallery                                http://go.micro...                                 NuGet                Untrusted
myNuGetSource                            https://myget.c...                                 NuGet                Trusted
```

<span data-ttu-id="4a3a3-111">Det här kommandot hämtar alla modul-dataarkiv som registrerats för den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="4a3a3-111">This command gets all module repositories registered for the current user.</span></span>

### <span data-ttu-id="4a3a3-112">Exempel 2: Hämta modul Arkiv efter namn</span><span class="sxs-lookup"><span data-stu-id="4a3a3-112">Example 2: Get module repositories by name</span></span>

```
PS C:\> Get-PSRepository -Name "*NuGet*"
```

<span data-ttu-id="4a3a3-113">Det här kommandot hämtar alla modulblad som innehåller NuGet i sina namn.</span><span class="sxs-lookup"><span data-stu-id="4a3a3-113">This command gets all module repositories that include NuGet in their names.</span></span>

### <span data-ttu-id="4a3a3-114">Exempel 3: Hämta en modul-lagringsplats och formatera utdata</span><span class="sxs-lookup"><span data-stu-id="4a3a3-114">Example 3: Get a module repository and format the output</span></span>

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

<span data-ttu-id="4a3a3-115">Det här kommandot hämtar lagrings platsen med namnet Local01 och använder pipelinen-operatorn för att skicka objektet till Format-List-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="4a3a3-115">This command gets the repository named Local01 and uses the pipeline operator to pass that object to the Format-List cmdlet.</span></span>

## <span data-ttu-id="4a3a3-116">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="4a3a3-116">PARAMETERS</span></span>

### <span data-ttu-id="4a3a3-117">-Name</span><span class="sxs-lookup"><span data-stu-id="4a3a3-117">-Name</span></span>

<span data-ttu-id="4a3a3-118">Anger namnen på de databaser som ska hämtas.</span><span class="sxs-lookup"><span data-stu-id="4a3a3-118">Specifies the names of the repositories to get.</span></span>

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

### <span data-ttu-id="4a3a3-119">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4a3a3-119">CommonParameters</span></span>

<span data-ttu-id="4a3a3-120">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4a3a3-120">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4a3a3-121">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="4a3a3-121">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4a3a3-122">INDATA</span><span class="sxs-lookup"><span data-stu-id="4a3a3-122">INPUTS</span></span>

### <span data-ttu-id="4a3a3-123">System.String[]</span><span class="sxs-lookup"><span data-stu-id="4a3a3-123">System.String[]</span></span>

## <span data-ttu-id="4a3a3-124">UTDATA</span><span class="sxs-lookup"><span data-stu-id="4a3a3-124">OUTPUTS</span></span>

### <span data-ttu-id="4a3a3-125">System. Object</span><span class="sxs-lookup"><span data-stu-id="4a3a3-125">System.Object</span></span>

## <span data-ttu-id="4a3a3-126">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="4a3a3-126">NOTES</span></span>

## <span data-ttu-id="4a3a3-127">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="4a3a3-127">RELATED LINKS</span></span>

[<span data-ttu-id="4a3a3-128">Registrera – PSRepository</span><span class="sxs-lookup"><span data-stu-id="4a3a3-128">Register-PSRepository</span></span>](Register-PSRepository.md)

[<span data-ttu-id="4a3a3-129">Set-PSRepository</span><span class="sxs-lookup"><span data-stu-id="4a3a3-129">Set-PSRepository</span></span>](Set-PSRepository.md)

[<span data-ttu-id="4a3a3-130">Avregistrera-PSRepository</span><span class="sxs-lookup"><span data-stu-id="4a3a3-130">Unregister-PSRepository</span></span>](Unregister-PSRepository.md)
