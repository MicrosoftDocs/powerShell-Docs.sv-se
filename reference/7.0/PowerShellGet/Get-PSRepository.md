---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/get-psrepository?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSRepository
ms.openlocfilehash: cc92188384497b5e7534e3dc7daa4fc73c314a36
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93262293"
---
# <span data-ttu-id="4b203-103">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="4b203-103">Get-PSRepository</span></span>

## <span data-ttu-id="4b203-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="4b203-104">SYNOPSIS</span></span>
<span data-ttu-id="4b203-105">Hämtar PowerShell-databaser.</span><span class="sxs-lookup"><span data-stu-id="4b203-105">Gets PowerShell repositories.</span></span>

## <span data-ttu-id="4b203-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4b203-106">SYNTAX</span></span>

```
Get-PSRepository [[-Name] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="4b203-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="4b203-107">DESCRIPTION</span></span>

<span data-ttu-id="4b203-108">Cmdlet **: en get-PSRepository** hämtar PowerShell-modulens databaser som är registrerade för den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="4b203-108">The **Get-PSRepository** cmdlet gets PowerShell module repositories that are registered for the current user.</span></span>

## <span data-ttu-id="4b203-109">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="4b203-109">EXAMPLES</span></span>

### <span data-ttu-id="4b203-110">Exempel 1: Hämta alla modul databaser</span><span class="sxs-lookup"><span data-stu-id="4b203-110">Example 1: Get all module repositories</span></span>

```
PS C:\> Get-PSRepository
Name                                     SourceLocation                                     OneGetProvider       InstallationPolicy
----                                     --------------                                     --------------       ------------------
PSGallery                                http://go.micro...                                 NuGet                Untrusted
myNuGetSource                            https://myget.c...                                 NuGet                Trusted
```

<span data-ttu-id="4b203-111">Det här kommandot hämtar alla modul-dataarkiv som registrerats för den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="4b203-111">This command gets all module repositories registered for the current user.</span></span>

### <span data-ttu-id="4b203-112">Exempel 2: Hämta modul Arkiv efter namn</span><span class="sxs-lookup"><span data-stu-id="4b203-112">Example 2: Get module repositories by name</span></span>

```
PS C:\> Get-PSRepository -Name "*NuGet*"
```

<span data-ttu-id="4b203-113">Det här kommandot hämtar alla modulblad som innehåller NuGet i sina namn.</span><span class="sxs-lookup"><span data-stu-id="4b203-113">This command gets all module repositories that include NuGet in their names.</span></span>

### <span data-ttu-id="4b203-114">Exempel 3: Hämta en modul-lagringsplats och formatera utdata</span><span class="sxs-lookup"><span data-stu-id="4b203-114">Example 3: Get a module repository and format the output</span></span>

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

<span data-ttu-id="4b203-115">Det här kommandot hämtar lagrings platsen med namnet Local01 och använder pipelinen-operatorn för att skicka objektet till Format-List-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="4b203-115">This command gets the repository named Local01 and uses the pipeline operator to pass that object to the Format-List cmdlet.</span></span>

## <span data-ttu-id="4b203-116">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="4b203-116">PARAMETERS</span></span>

### <span data-ttu-id="4b203-117">-Name</span><span class="sxs-lookup"><span data-stu-id="4b203-117">-Name</span></span>

<span data-ttu-id="4b203-118">Anger namnen på de databaser som ska hämtas.</span><span class="sxs-lookup"><span data-stu-id="4b203-118">Specifies the names of the repositories to get.</span></span>

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

### <span data-ttu-id="4b203-119">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4b203-119">CommonParameters</span></span>

<span data-ttu-id="4b203-120">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4b203-120">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4b203-121">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="4b203-121">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4b203-122">INDATA</span><span class="sxs-lookup"><span data-stu-id="4b203-122">INPUTS</span></span>

### <span data-ttu-id="4b203-123">System.String[]</span><span class="sxs-lookup"><span data-stu-id="4b203-123">System.String[]</span></span>

## <span data-ttu-id="4b203-124">UTDATA</span><span class="sxs-lookup"><span data-stu-id="4b203-124">OUTPUTS</span></span>

### <span data-ttu-id="4b203-125">System. Object</span><span class="sxs-lookup"><span data-stu-id="4b203-125">System.Object</span></span>

## <span data-ttu-id="4b203-126">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="4b203-126">NOTES</span></span>

## <span data-ttu-id="4b203-127">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="4b203-127">RELATED LINKS</span></span>

[<span data-ttu-id="4b203-128">Registrera – PSRepository</span><span class="sxs-lookup"><span data-stu-id="4b203-128">Register-PSRepository</span></span>](Register-PSRepository.md)

[<span data-ttu-id="4b203-129">Set-PSRepository</span><span class="sxs-lookup"><span data-stu-id="4b203-129">Set-PSRepository</span></span>](Set-PSRepository.md)

[<span data-ttu-id="4b203-130">Avregistrera-PSRepository</span><span class="sxs-lookup"><span data-stu-id="4b203-130">Unregister-PSRepository</span></span>](Unregister-PSRepository.md)
