---
ms.date: 09/20/2019
keywords: DSC, PowerShell, konfiguration, installation
title: DSC WindowsOptionalFeatureSet-resurs
ms.openlocfilehash: f378006a6c362ee9890d70dd76fb552dd262a544
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71941189"
---
# <a name="dsc-windowsoptionalfeatureset-resource"></a><span data-ttu-id="7a254-103">DSC WindowsOptionalFeatureSet-resurs</span><span class="sxs-lookup"><span data-stu-id="7a254-103">DSC WindowsOptionalFeatureSet Resource</span></span>

> <span data-ttu-id="7a254-104">Gäller för: Windows PowerShell 5. x</span><span class="sxs-lookup"><span data-stu-id="7a254-104">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="7a254-105">**WindowsOptionalFeatureSet** -resursen i Windows PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att säkerställa att valfria funktioner aktive ras på en målnod.</span><span class="sxs-lookup"><span data-stu-id="7a254-105">The **WindowsOptionalFeatureSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that optional features are enabled on a target node.</span></span> <span data-ttu-id="7a254-106">Den här resursen är en [sammansatt resurs](../../../resources/authoringResourceComposite.md) som anropar [WindowsOptionalFeature-resursen](windowsOptionalFeatureResource.md) för varje funktion som anges i egenskapen **Name** .</span><span class="sxs-lookup"><span data-stu-id="7a254-106">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [WindowsOptionalFeature resource](windowsOptionalFeatureResource.md) for each feature specified in the **Name** property.</span></span>

<span data-ttu-id="7a254-107">Använd den här resursen när du vill konfigurera ett antal Windows-valfria funktioner till samma tillstånd.</span><span class="sxs-lookup"><span data-stu-id="7a254-107">Use this resource when you want to configure a number of Windows optional features to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="7a254-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="7a254-108">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="7a254-109">properties</span><span class="sxs-lookup"><span data-stu-id="7a254-109">Properties</span></span>

|<span data-ttu-id="7a254-110">Egenskap</span><span class="sxs-lookup"><span data-stu-id="7a254-110">Property</span></span> |<span data-ttu-id="7a254-111">Description</span><span class="sxs-lookup"><span data-stu-id="7a254-111">Description</span></span> |
|---|---|
|<span data-ttu-id="7a254-112">Name</span><span class="sxs-lookup"><span data-stu-id="7a254-112">Name</span></span> |<span data-ttu-id="7a254-113">Anger namnet på de funktioner som du vill se är aktiverade eller inaktiverade.</span><span class="sxs-lookup"><span data-stu-id="7a254-113">Indicates the name of the features that you want to ensure are enabled or disabled.</span></span> |
|<span data-ttu-id="7a254-114">Source</span><span class="sxs-lookup"><span data-stu-id="7a254-114">Source</span></span> |<span data-ttu-id="7a254-115">Inte implementerad.</span><span class="sxs-lookup"><span data-stu-id="7a254-115">Not implemented.</span></span> |
|<span data-ttu-id="7a254-116">NoWindowsUpdateCheck</span><span class="sxs-lookup"><span data-stu-id="7a254-116">NoWindowsUpdateCheck</span></span> |<span data-ttu-id="7a254-117">Anger om DISM-kontakter Windows Update (WU) vid sökning efter källfiler för att aktivera funktioner.</span><span class="sxs-lookup"><span data-stu-id="7a254-117">Specifies whether DISM contacts Windows Update (WU) when searching for the source files to enable features.</span></span> <span data-ttu-id="7a254-118">Om `$true`inte DISM kontaktar Wu.</span><span class="sxs-lookup"><span data-stu-id="7a254-118">If `$true`, DISM does not contact WU.</span></span> |
|<span data-ttu-id="7a254-119">RemoveFilesOnDisable</span><span class="sxs-lookup"><span data-stu-id="7a254-119">RemoveFilesOnDisable</span></span> |<span data-ttu-id="7a254-120">Ange till `$true` om du vill ta bort alla filer som är associerade med funktionerna när **Se** till att de är inställda på **frånvarande**.</span><span class="sxs-lookup"><span data-stu-id="7a254-120">Set to `$true` to remove all files associated with the features when **Ensure** is set to **Absent**.</span></span> |
|<span data-ttu-id="7a254-121">Loggnivå</span><span class="sxs-lookup"><span data-stu-id="7a254-121">LogLevel</span></span> |<span data-ttu-id="7a254-122">Den högsta utmatnings nivån som visas i loggarna.</span><span class="sxs-lookup"><span data-stu-id="7a254-122">The maximum output level shown in the logs.</span></span> <span data-ttu-id="7a254-123">Godkända värden är: **ErrorsOnly**, **ErrorsAndWarning**och **ErrorsAndWarningAndInformation**.</span><span class="sxs-lookup"><span data-stu-id="7a254-123">The accepted values are: **ErrorsOnly**, **ErrorsAndWarning**, and **ErrorsAndWarningAndInformation**.</span></span> |
|<span data-ttu-id="7a254-124">LogPath</span><span class="sxs-lookup"><span data-stu-id="7a254-124">LogPath</span></span> |<span data-ttu-id="7a254-125">Sökvägen till logg filen där du vill att resurs leverantören ska logga åtgärden.</span><span class="sxs-lookup"><span data-stu-id="7a254-125">The path to a log file where you want the resource provider to log the operation.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="7a254-126">Gemensamma egenskaper</span><span class="sxs-lookup"><span data-stu-id="7a254-126">Common properties</span></span>

|<span data-ttu-id="7a254-127">Egenskap</span><span class="sxs-lookup"><span data-stu-id="7a254-127">Property</span></span> |<span data-ttu-id="7a254-128">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7a254-128">Description</span></span> |
|---|---|
|<span data-ttu-id="7a254-129">DependsOn</span><span class="sxs-lookup"><span data-stu-id="7a254-129">DependsOn</span></span> |<span data-ttu-id="7a254-130">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS.</span><span class="sxs-lookup"><span data-stu-id="7a254-130">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="7a254-131">Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är `DependsOn = "[ResourceType]ResourceName"`syntaxen för att använda den här egenskapen.</span><span class="sxs-lookup"><span data-stu-id="7a254-131">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="7a254-132">Kontrol</span><span class="sxs-lookup"><span data-stu-id="7a254-132">Ensure</span></span> |<span data-ttu-id="7a254-133">Anger om funktionerna är aktiverade.</span><span class="sxs-lookup"><span data-stu-id="7a254-133">Specifies whether the features are enabled.</span></span> <span data-ttu-id="7a254-134">För att se till att funktionerna är aktiverade ställer du in egenskapen på **Aktivera**.</span><span class="sxs-lookup"><span data-stu-id="7a254-134">To ensure that the features are enabled, set this property to **Enable**.</span></span> <span data-ttu-id="7a254-135">För att se till att funktionerna är inaktiverade ställer du in egenskapen på **inaktivera**.</span><span class="sxs-lookup"><span data-stu-id="7a254-135">To ensure that the features are disabled, set the property to **Disable**.</span></span> <span data-ttu-id="7a254-136">Standardvärdet är **Enable**.</span><span class="sxs-lookup"><span data-stu-id="7a254-136">The default value is **Enable**.</span></span> |
|<span data-ttu-id="7a254-137">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="7a254-137">PsDscRunAsCredential</span></span> |<span data-ttu-id="7a254-138">Anger autentiseringsuppgifter för att köra hela resursen som.</span><span class="sxs-lookup"><span data-stu-id="7a254-138">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="7a254-139">Den gemensamma egenskapen **PsDscRunAsCredential** har lagts till i WMF 5,0 för att tillåta körning av DSC-resurser i kontexten för andra autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="7a254-139">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="7a254-140">Mer information finns i [använda autentiseringsuppgifter med DSC-resurser](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="7a254-140">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>