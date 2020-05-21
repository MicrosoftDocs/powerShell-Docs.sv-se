---
ms.date: 09/20/2019
keywords: DSC, PowerShell, konfiguration, installation
title: DSC WindowsOptionalFeatureSet-resurs
ms.openlocfilehash: 0930bd0c6d1955005ea607b610e004818c0ad06f
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560159"
---
# <a name="dsc-windowsoptionalfeatureset-resource"></a><span data-ttu-id="7e667-103">DSC WindowsOptionalFeatureSet-resurs</span><span class="sxs-lookup"><span data-stu-id="7e667-103">DSC WindowsOptionalFeatureSet Resource</span></span>

> <span data-ttu-id="7e667-104">Gäller för: Windows PowerShell 5. x</span><span class="sxs-lookup"><span data-stu-id="7e667-104">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="7e667-105">**WindowsOptionalFeatureSet** -resursen i Windows PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att säkerställa att valfria funktioner aktive ras på en målnod.</span><span class="sxs-lookup"><span data-stu-id="7e667-105">The **WindowsOptionalFeatureSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that optional features are enabled on a target node.</span></span> <span data-ttu-id="7e667-106">Den här resursen är en [sammansatt resurs](../../../resources/authoringResourceComposite.md) som anropar [WindowsOptionalFeature-resursen](windowsOptionalFeatureResource.md) för varje funktion som anges i egenskapen **Name** .</span><span class="sxs-lookup"><span data-stu-id="7e667-106">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [WindowsOptionalFeature resource](windowsOptionalFeatureResource.md) for each feature specified in the **Name** property.</span></span>

<span data-ttu-id="7e667-107">Använd den här resursen när du vill konfigurera ett antal Windows-valfria funktioner till samma tillstånd.</span><span class="sxs-lookup"><span data-stu-id="7e667-107">Use this resource when you want to configure a number of Windows optional features to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="7e667-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="7e667-108">Syntax</span></span>

```Syntax
WindowsOptionalFeatureSet [string] #ResourceName
{
    Name = [string[]]
    [ Source = [string] ]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogPath = [string] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Enable | Disable }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="7e667-109">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="7e667-109">Properties</span></span>

|<span data-ttu-id="7e667-110">Egenskap</span><span class="sxs-lookup"><span data-stu-id="7e667-110">Property</span></span> |<span data-ttu-id="7e667-111">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7e667-111">Description</span></span> |
|---|---|
|<span data-ttu-id="7e667-112">Name</span><span class="sxs-lookup"><span data-stu-id="7e667-112">Name</span></span> |<span data-ttu-id="7e667-113">Anger namnet på de funktioner som du vill se är aktiverade eller inaktiverade.</span><span class="sxs-lookup"><span data-stu-id="7e667-113">Indicates the name of the features that you want to ensure are enabled or disabled.</span></span> |
|<span data-ttu-id="7e667-114">Källa</span><span class="sxs-lookup"><span data-stu-id="7e667-114">Source</span></span> |<span data-ttu-id="7e667-115">Inte implementerat.</span><span class="sxs-lookup"><span data-stu-id="7e667-115">Not implemented.</span></span> |
|<span data-ttu-id="7e667-116">NoWindowsUpdateCheck</span><span class="sxs-lookup"><span data-stu-id="7e667-116">NoWindowsUpdateCheck</span></span> |<span data-ttu-id="7e667-117">Anger om DISM-kontakter Windows Update (WU) vid sökning efter källfiler för att aktivera funktioner.</span><span class="sxs-lookup"><span data-stu-id="7e667-117">Specifies whether DISM contacts Windows Update (WU) when searching for the source files to enable features.</span></span> <span data-ttu-id="7e667-118">Om inte `$true` DISM kontaktar Wu.</span><span class="sxs-lookup"><span data-stu-id="7e667-118">If `$true`, DISM does not contact WU.</span></span> |
|<span data-ttu-id="7e667-119">RemoveFilesOnDisable</span><span class="sxs-lookup"><span data-stu-id="7e667-119">RemoveFilesOnDisable</span></span> |<span data-ttu-id="7e667-120">Ange till `$true` om du vill ta bort alla filer som är associerade med funktionerna när **Se** till att de är inställda på **frånvarande**.</span><span class="sxs-lookup"><span data-stu-id="7e667-120">Set to `$true` to remove all files associated with the features when **Ensure** is set to **Absent**.</span></span> |
|<span data-ttu-id="7e667-121">Loggnivå</span><span class="sxs-lookup"><span data-stu-id="7e667-121">LogLevel</span></span> |<span data-ttu-id="7e667-122">Den högsta utmatnings nivån som visas i loggarna.</span><span class="sxs-lookup"><span data-stu-id="7e667-122">The maximum output level shown in the logs.</span></span> <span data-ttu-id="7e667-123">Godkända värden är: **ErrorsOnly**, **ErrorsAndWarning**och **ErrorsAndWarningAndInformation**.</span><span class="sxs-lookup"><span data-stu-id="7e667-123">The accepted values are: **ErrorsOnly**, **ErrorsAndWarning**, and **ErrorsAndWarningAndInformation**.</span></span> |
|<span data-ttu-id="7e667-124">LogPath</span><span class="sxs-lookup"><span data-stu-id="7e667-124">LogPath</span></span> |<span data-ttu-id="7e667-125">Sökvägen till logg filen där du vill att resurs leverantören ska logga åtgärden.</span><span class="sxs-lookup"><span data-stu-id="7e667-125">The path to a log file where you want the resource provider to log the operation.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="7e667-126">Gemensamma egenskaper</span><span class="sxs-lookup"><span data-stu-id="7e667-126">Common properties</span></span>

|<span data-ttu-id="7e667-127">Egenskap</span><span class="sxs-lookup"><span data-stu-id="7e667-127">Property</span></span> |<span data-ttu-id="7e667-128">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7e667-128">Description</span></span> |
|---|---|
|<span data-ttu-id="7e667-129">DependsOn</span><span class="sxs-lookup"><span data-stu-id="7e667-129">DependsOn</span></span> |<span data-ttu-id="7e667-130">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS.</span><span class="sxs-lookup"><span data-stu-id="7e667-130">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="7e667-131">Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är syntaxen för att använda den här egenskapen `DependsOn = "[ResourceType]ResourceName"` .</span><span class="sxs-lookup"><span data-stu-id="7e667-131">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="7e667-132">Kontrol</span><span class="sxs-lookup"><span data-stu-id="7e667-132">Ensure</span></span> |<span data-ttu-id="7e667-133">Anger om funktionerna är aktiverade.</span><span class="sxs-lookup"><span data-stu-id="7e667-133">Specifies whether the features are enabled.</span></span> <span data-ttu-id="7e667-134">För att se till att funktionerna är aktiverade ställer du in egenskapen på **Aktivera**.</span><span class="sxs-lookup"><span data-stu-id="7e667-134">To ensure that the features are enabled, set this property to **Enable**.</span></span> <span data-ttu-id="7e667-135">För att se till att funktionerna är inaktiverade ställer du in egenskapen på **inaktivera**.</span><span class="sxs-lookup"><span data-stu-id="7e667-135">To ensure that the features are disabled, set the property to **Disable**.</span></span> <span data-ttu-id="7e667-136">Standardvärdet är **Enable**.</span><span class="sxs-lookup"><span data-stu-id="7e667-136">The default value is **Enable**.</span></span> |
|<span data-ttu-id="7e667-137">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="7e667-137">PsDscRunAsCredential</span></span> |<span data-ttu-id="7e667-138">Anger autentiseringsuppgifter för att köra hela resursen som.</span><span class="sxs-lookup"><span data-stu-id="7e667-138">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="7e667-139">Den gemensamma egenskapen **PsDscRunAsCredential** har lagts till i WMF 5,0 för att tillåta körning av DSC-resurser i kontexten för andra autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="7e667-139">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="7e667-140">Mer information finns i [använda autentiseringsuppgifter med DSC-resurser](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="7e667-140">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>
