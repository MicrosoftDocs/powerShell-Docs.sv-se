---
ms.date: 09/20/2019
keywords: DSC, PowerShell, konfiguration, installation
title: DSC WindowsOptionalFeature-resurs
ms.openlocfilehash: bca6294db74c92a2c1940cfbe00305542a1c5d19
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83565374"
---
# <a name="dsc-windowsoptionalfeature-resource"></a><span data-ttu-id="7624b-103">DSC WindowsOptionalFeature-resurs</span><span class="sxs-lookup"><span data-stu-id="7624b-103">DSC WindowsOptionalFeature Resource</span></span>

> <span data-ttu-id="7624b-104">Gäller för: Windows PowerShell 5. x</span><span class="sxs-lookup"><span data-stu-id="7624b-104">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="7624b-105">**WindowsOptionalFeature** -resursen i Windows PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att säkerställa att valfria funktioner aktive ras på en målnod.</span><span class="sxs-lookup"><span data-stu-id="7624b-105">The **WindowsOptionalFeature** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that optional features are enabled on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="7624b-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="7624b-106">Syntax</span></span>

```Syntax
WindowsOptionalFeature [string] #ResourceName
{
    Name = [string]
    [ Source = [string[]] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Enable | Disable }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="7624b-107">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="7624b-107">Properties</span></span>

|<span data-ttu-id="7624b-108">Egenskap</span><span class="sxs-lookup"><span data-stu-id="7624b-108">Property</span></span> |<span data-ttu-id="7624b-109">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7624b-109">Description</span></span> |
|---|---|
|<span data-ttu-id="7624b-110">Name</span><span class="sxs-lookup"><span data-stu-id="7624b-110">Name</span></span> |<span data-ttu-id="7624b-111">Anger namnet på den funktion som du vill se är aktive rad eller inaktive rad.</span><span class="sxs-lookup"><span data-stu-id="7624b-111">Indicates the name of the feature that you want to ensure is enabled or disabled.</span></span> |
|<span data-ttu-id="7624b-112">Källa</span><span class="sxs-lookup"><span data-stu-id="7624b-112">Source</span></span> |<span data-ttu-id="7624b-113">Inte implementerat.</span><span class="sxs-lookup"><span data-stu-id="7624b-113">Not implemented.</span></span> |
|<span data-ttu-id="7624b-114">NoWindowsUpdateCheck</span><span class="sxs-lookup"><span data-stu-id="7624b-114">NoWindowsUpdateCheck</span></span> |<span data-ttu-id="7624b-115">Anger om DISM-kontakter Windows Update (WU) vid sökning efter källfiler för att aktivera en funktion.</span><span class="sxs-lookup"><span data-stu-id="7624b-115">Specifies whether DISM contacts Windows Update (WU) when searching for the source files to enable a feature.</span></span> <span data-ttu-id="7624b-116">Om inte `$true` DISM kontaktar Wu.</span><span class="sxs-lookup"><span data-stu-id="7624b-116">If `$true`, DISM does not contact WU.</span></span> |
|<span data-ttu-id="7624b-117">RemoveFilesOnDisable</span><span class="sxs-lookup"><span data-stu-id="7624b-117">RemoveFilesOnDisable</span></span> |<span data-ttu-id="7624b-118">Ange till `$true` om du vill ta bort alla filer som är associerade med funktionen när **Se** till att den är inställd på **frånvarande**.</span><span class="sxs-lookup"><span data-stu-id="7624b-118">Set to `$true` to remove all files associated with the feature when **Ensure** is set to **Absent**.</span></span> |
|<span data-ttu-id="7624b-119">Loggnivå</span><span class="sxs-lookup"><span data-stu-id="7624b-119">LogLevel</span></span> |<span data-ttu-id="7624b-120">Den högsta utmatnings nivån som visas i loggarna.</span><span class="sxs-lookup"><span data-stu-id="7624b-120">The maximum output level shown in the logs.</span></span> <span data-ttu-id="7624b-121">Godkända värden är: **ErrorsOnly**, **ErrorsAndWarning**och **ErrorsAndWarningAndInformation**.</span><span class="sxs-lookup"><span data-stu-id="7624b-121">The accepted values are: **ErrorsOnly**, **ErrorsAndWarning**, and **ErrorsAndWarningAndInformation**.</span></span> |
|<span data-ttu-id="7624b-122">LogPath</span><span class="sxs-lookup"><span data-stu-id="7624b-122">LogPath</span></span> |<span data-ttu-id="7624b-123">Sökvägen till logg filen där du vill att resurs leverantören ska logga åtgärden.</span><span class="sxs-lookup"><span data-stu-id="7624b-123">The path to a log file where you want the resource provider to log the operation.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="7624b-124">Gemensamma egenskaper</span><span class="sxs-lookup"><span data-stu-id="7624b-124">Common properties</span></span>

|<span data-ttu-id="7624b-125">Egenskap</span><span class="sxs-lookup"><span data-stu-id="7624b-125">Property</span></span> |<span data-ttu-id="7624b-126">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7624b-126">Description</span></span> |
|---|---|
|<span data-ttu-id="7624b-127">DependsOn</span><span class="sxs-lookup"><span data-stu-id="7624b-127">DependsOn</span></span> |<span data-ttu-id="7624b-128">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS.</span><span class="sxs-lookup"><span data-stu-id="7624b-128">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="7624b-129">Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är syntaxen för att använda den här egenskapen `DependsOn = "[ResourceType]ResourceName"` .</span><span class="sxs-lookup"><span data-stu-id="7624b-129">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="7624b-130">Kontrol</span><span class="sxs-lookup"><span data-stu-id="7624b-130">Ensure</span></span> |<span data-ttu-id="7624b-131">Anger om funktionen är aktive rad.</span><span class="sxs-lookup"><span data-stu-id="7624b-131">Specifies whether the feature is enabled.</span></span> <span data-ttu-id="7624b-132">För att se till att funktionen är aktive rad ställer du in den här egenskapen på _Aktivera_.</span><span class="sxs-lookup"><span data-stu-id="7624b-132">To ensure that the feature is enabled, set this property to _Enable_.</span></span> <span data-ttu-id="7624b-133">För att se till att funktionen är inaktive rad ställer du in egenskapen på _inaktivera_.</span><span class="sxs-lookup"><span data-stu-id="7624b-133">To ensure that the feature is disabled, set the property to _Disable_.</span></span> <span data-ttu-id="7624b-134">Standardvärdet är _Enable_.</span><span class="sxs-lookup"><span data-stu-id="7624b-134">The default value is _Enable_.</span></span> |
|<span data-ttu-id="7624b-135">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="7624b-135">PsDscRunAsCredential</span></span> |<span data-ttu-id="7624b-136">Anger autentiseringsuppgifter för att köra hela resursen som.</span><span class="sxs-lookup"><span data-stu-id="7624b-136">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="7624b-137">Den gemensamma egenskapen **PsDscRunAsCredential** har lagts till i WMF 5,0 för att tillåta körning av DSC-resurser i kontexten för andra autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="7624b-137">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="7624b-138">Mer information finns i [använda autentiseringsuppgifter med DSC-resurser](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="7624b-138">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>
