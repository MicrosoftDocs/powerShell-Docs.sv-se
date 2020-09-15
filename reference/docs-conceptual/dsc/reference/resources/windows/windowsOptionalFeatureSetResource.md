---
ms.date: 07/16/2020
keywords: DSC, PowerShell, konfiguration, installation
title: DSC WindowsOptionalFeatureSet-resurs
ms.openlocfilehash: e4f88f1cae6d7ddb3596ab4f27eb3766259f1a31
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464170"
---
# <a name="dsc-windowsoptionalfeatureset-resource"></a><span data-ttu-id="4335e-103">DSC WindowsOptionalFeatureSet-resurs</span><span class="sxs-lookup"><span data-stu-id="4335e-103">DSC WindowsOptionalFeatureSet Resource</span></span>

> <span data-ttu-id="4335e-104">Gäller för: Windows PowerShell 5. x</span><span class="sxs-lookup"><span data-stu-id="4335e-104">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="4335e-105">**WindowsOptionalFeatureSet** -resursen i Windows PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att säkerställa att valfria funktioner aktive ras på en målnod.</span><span class="sxs-lookup"><span data-stu-id="4335e-105">The **WindowsOptionalFeatureSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that optional features are enabled on a target node.</span></span> <span data-ttu-id="4335e-106">Den här resursen är en [sammansatt resurs](../../../resources/authoringResourceComposite.md) som anropar [WindowsOptionalFeature-resursen](windowsOptionalFeatureResource.md) för varje funktion som anges i egenskapen **Name** .</span><span class="sxs-lookup"><span data-stu-id="4335e-106">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [WindowsOptionalFeature resource](windowsOptionalFeatureResource.md) for each feature specified in the **Name** property.</span></span>

<span data-ttu-id="4335e-107">Använd den här resursen när du vill konfigurera ett antal Windows-valfria funktioner till samma tillstånd.</span><span class="sxs-lookup"><span data-stu-id="4335e-107">Use this resource when you want to configure a number of Windows optional features to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="4335e-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="4335e-108">Syntax</span></span>

```Syntax
WindowsOptionalFeatureSet [string] #ResourceName
{
    Name = [string[]]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogPath = [string] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Enable | Disable }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="4335e-109">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="4335e-109">Properties</span></span>

|<span data-ttu-id="4335e-110">Egenskap</span><span class="sxs-lookup"><span data-stu-id="4335e-110">Property</span></span> |<span data-ttu-id="4335e-111">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="4335e-111">Description</span></span> |
|---|---|
|<span data-ttu-id="4335e-112">Name</span><span class="sxs-lookup"><span data-stu-id="4335e-112">Name</span></span> |<span data-ttu-id="4335e-113">Anger namnet på de funktioner som du vill se är aktiverade eller inaktiverade.</span><span class="sxs-lookup"><span data-stu-id="4335e-113">Indicates the name of the features that you want to ensure are enabled or disabled.</span></span> |
|<span data-ttu-id="4335e-114">NoWindowsUpdateCheck</span><span class="sxs-lookup"><span data-stu-id="4335e-114">NoWindowsUpdateCheck</span></span> |<span data-ttu-id="4335e-115">Anger om DISM-kontakter Windows Update (WU) vid sökning efter källfiler för att aktivera funktioner.</span><span class="sxs-lookup"><span data-stu-id="4335e-115">Specifies whether DISM contacts Windows Update (WU) when searching for the source files to enable features.</span></span> <span data-ttu-id="4335e-116">Om inte `$true` DISM kontaktar Wu.</span><span class="sxs-lookup"><span data-stu-id="4335e-116">If `$true`, DISM does not contact WU.</span></span> |
|<span data-ttu-id="4335e-117">RemoveFilesOnDisable</span><span class="sxs-lookup"><span data-stu-id="4335e-117">RemoveFilesOnDisable</span></span> |<span data-ttu-id="4335e-118">Ange till `$true` om du vill ta bort alla filer som är associerade med funktionerna när **Se** till att de är inställda på **frånvarande**.</span><span class="sxs-lookup"><span data-stu-id="4335e-118">Set to `$true` to remove all files associated with the features when **Ensure** is set to **Absent**.</span></span> |
|<span data-ttu-id="4335e-119">Loggnivå</span><span class="sxs-lookup"><span data-stu-id="4335e-119">LogLevel</span></span> |<span data-ttu-id="4335e-120">Den högsta utmatnings nivån som visas i loggarna.</span><span class="sxs-lookup"><span data-stu-id="4335e-120">The maximum output level shown in the logs.</span></span> <span data-ttu-id="4335e-121">Godkända värden är: **ErrorsOnly**, **ErrorsAndWarning**och **ErrorsAndWarningAndInformation**.</span><span class="sxs-lookup"><span data-stu-id="4335e-121">The accepted values are: **ErrorsOnly**, **ErrorsAndWarning**, and **ErrorsAndWarningAndInformation**.</span></span> |
|<span data-ttu-id="4335e-122">LogPath</span><span class="sxs-lookup"><span data-stu-id="4335e-122">LogPath</span></span> |<span data-ttu-id="4335e-123">Sökvägen till logg filen där du vill att resurs leverantören ska logga åtgärden.</span><span class="sxs-lookup"><span data-stu-id="4335e-123">The path to a log file where you want the resource provider to log the operation.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="4335e-124">Gemensamma egenskaper</span><span class="sxs-lookup"><span data-stu-id="4335e-124">Common properties</span></span>

|<span data-ttu-id="4335e-125">Egenskap</span><span class="sxs-lookup"><span data-stu-id="4335e-125">Property</span></span> |<span data-ttu-id="4335e-126">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="4335e-126">Description</span></span> |
|---|---|
|<span data-ttu-id="4335e-127">DependsOn</span><span class="sxs-lookup"><span data-stu-id="4335e-127">DependsOn</span></span> |<span data-ttu-id="4335e-128">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS.</span><span class="sxs-lookup"><span data-stu-id="4335e-128">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="4335e-129">Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är syntaxen för att använda den här egenskapen `DependsOn = "[ResourceType]ResourceName"` .</span><span class="sxs-lookup"><span data-stu-id="4335e-129">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="4335e-130">Kontrol</span><span class="sxs-lookup"><span data-stu-id="4335e-130">Ensure</span></span> |<span data-ttu-id="4335e-131">Anger om funktionerna är aktiverade.</span><span class="sxs-lookup"><span data-stu-id="4335e-131">Specifies whether the features are enabled.</span></span> <span data-ttu-id="4335e-132">För att se till att funktionerna är aktiverade ställer du in egenskapen på **Aktivera**.</span><span class="sxs-lookup"><span data-stu-id="4335e-132">To ensure that the features are enabled, set this property to **Enable**.</span></span> <span data-ttu-id="4335e-133">För att se till att funktionerna är inaktiverade ställer du in egenskapen på **inaktivera**.</span><span class="sxs-lookup"><span data-stu-id="4335e-133">To ensure that the features are disabled, set the property to **Disable**.</span></span> <span data-ttu-id="4335e-134">Standardvärdet är **Enable**.</span><span class="sxs-lookup"><span data-stu-id="4335e-134">The default value is **Enable**.</span></span> |
|<span data-ttu-id="4335e-135">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="4335e-135">PsDscRunAsCredential</span></span> |<span data-ttu-id="4335e-136">Anger autentiseringsuppgifter för att köra hela resursen som.</span><span class="sxs-lookup"><span data-stu-id="4335e-136">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="4335e-137">Den gemensamma egenskapen **PsDscRunAsCredential** har lagts till i WMF 5,0 för att tillåta körning av DSC-resurser i kontexten för andra autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="4335e-137">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="4335e-138">Mer information finns i [använda autentiseringsuppgifter med DSC-resurser](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="4335e-138">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>
