---
ms.date: 09/20/2019
keywords: DSC, PowerShell, konfiguration, installation
title: DSC WindowsOptionalFeature-resurs
ms.openlocfilehash: 7312edcaeb47427bf4736f466a9ed41bd7c31f6a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71942435"
---
# <a name="dsc-windowsoptionalfeature-resource"></a><span data-ttu-id="e6b36-103">DSC WindowsOptionalFeature-resurs</span><span class="sxs-lookup"><span data-stu-id="e6b36-103">DSC WindowsOptionalFeature Resource</span></span>

> <span data-ttu-id="e6b36-104">Gäller för: Windows PowerShell 5. x</span><span class="sxs-lookup"><span data-stu-id="e6b36-104">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="e6b36-105">**WindowsOptionalFeature** -resursen i Windows PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att säkerställa att valfria funktioner aktive ras på en målnod.</span><span class="sxs-lookup"><span data-stu-id="e6b36-105">The **WindowsOptionalFeature** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that optional features are enabled on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="e6b36-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="e6b36-106">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="e6b36-107">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="e6b36-107">Properties</span></span>

|<span data-ttu-id="e6b36-108">Egenskap</span><span class="sxs-lookup"><span data-stu-id="e6b36-108">Property</span></span> |<span data-ttu-id="e6b36-109">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e6b36-109">Description</span></span> |
|---|---|
|<span data-ttu-id="e6b36-110">Namn</span><span class="sxs-lookup"><span data-stu-id="e6b36-110">Name</span></span> |<span data-ttu-id="e6b36-111">Anger namnet på den funktion som du vill se är aktive rad eller inaktive rad.</span><span class="sxs-lookup"><span data-stu-id="e6b36-111">Indicates the name of the feature that you want to ensure is enabled or disabled.</span></span> |
|<span data-ttu-id="e6b36-112">Källa</span><span class="sxs-lookup"><span data-stu-id="e6b36-112">Source</span></span> |<span data-ttu-id="e6b36-113">Inte implementerat.</span><span class="sxs-lookup"><span data-stu-id="e6b36-113">Not implemented.</span></span> |
|<span data-ttu-id="e6b36-114">NoWindowsUpdateCheck</span><span class="sxs-lookup"><span data-stu-id="e6b36-114">NoWindowsUpdateCheck</span></span> |<span data-ttu-id="e6b36-115">Anger om DISM-kontakter Windows Update (WU) vid sökning efter källfiler för att aktivera en funktion.</span><span class="sxs-lookup"><span data-stu-id="e6b36-115">Specifies whether DISM contacts Windows Update (WU) when searching for the source files to enable a feature.</span></span> <span data-ttu-id="e6b36-116">Om `$true`kan DISM inte kontakta WU.</span><span class="sxs-lookup"><span data-stu-id="e6b36-116">If `$true`, DISM does not contact WU.</span></span> |
|<span data-ttu-id="e6b36-117">RemoveFilesOnDisable</span><span class="sxs-lookup"><span data-stu-id="e6b36-117">RemoveFilesOnDisable</span></span> |<span data-ttu-id="e6b36-118">Ange till `$true` om du vill ta bort alla filer som är associerade med funktionen när **Se** till att den är inställd på **frånvarande**.</span><span class="sxs-lookup"><span data-stu-id="e6b36-118">Set to `$true` to remove all files associated with the feature when **Ensure** is set to **Absent**.</span></span> |
|<span data-ttu-id="e6b36-119">Loggnivå</span><span class="sxs-lookup"><span data-stu-id="e6b36-119">LogLevel</span></span> |<span data-ttu-id="e6b36-120">Den högsta utmatnings nivån som visas i loggarna.</span><span class="sxs-lookup"><span data-stu-id="e6b36-120">The maximum output level shown in the logs.</span></span> <span data-ttu-id="e6b36-121">Godkända värden är: **ErrorsOnly**, **ErrorsAndWarning**och **ErrorsAndWarningAndInformation**.</span><span class="sxs-lookup"><span data-stu-id="e6b36-121">The accepted values are: **ErrorsOnly**, **ErrorsAndWarning**, and **ErrorsAndWarningAndInformation**.</span></span> |
|<span data-ttu-id="e6b36-122">LogPath</span><span class="sxs-lookup"><span data-stu-id="e6b36-122">LogPath</span></span> |<span data-ttu-id="e6b36-123">Sökvägen till logg filen där du vill att resurs leverantören ska logga åtgärden.</span><span class="sxs-lookup"><span data-stu-id="e6b36-123">The path to a log file where you want the resource provider to log the operation.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="e6b36-124">Gemensamma egenskaper</span><span class="sxs-lookup"><span data-stu-id="e6b36-124">Common properties</span></span>

|<span data-ttu-id="e6b36-125">Egenskap</span><span class="sxs-lookup"><span data-stu-id="e6b36-125">Property</span></span> |<span data-ttu-id="e6b36-126">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e6b36-126">Description</span></span> |
|---|---|
|<span data-ttu-id="e6b36-127">DependsOn</span><span class="sxs-lookup"><span data-stu-id="e6b36-127">DependsOn</span></span> |<span data-ttu-id="e6b36-128">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS.</span><span class="sxs-lookup"><span data-stu-id="e6b36-128">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="e6b36-129">Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är syntaxen för att använda den här egenskapen `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="e6b36-129">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="e6b36-130">Kontrol</span><span class="sxs-lookup"><span data-stu-id="e6b36-130">Ensure</span></span> |<span data-ttu-id="e6b36-131">Anger om funktionen är aktive rad.</span><span class="sxs-lookup"><span data-stu-id="e6b36-131">Specifies whether the feature is enabled.</span></span> <span data-ttu-id="e6b36-132">För att se till att funktionen är aktive rad ställer du in den här egenskapen på _Aktivera_.</span><span class="sxs-lookup"><span data-stu-id="e6b36-132">To ensure that the feature is enabled, set this property to _Enable_.</span></span> <span data-ttu-id="e6b36-133">För att se till att funktionen är inaktive rad ställer du in egenskapen på _inaktivera_.</span><span class="sxs-lookup"><span data-stu-id="e6b36-133">To ensure that the feature is disabled, set the property to _Disable_.</span></span> <span data-ttu-id="e6b36-134">Standardvärdet är _Enable_.</span><span class="sxs-lookup"><span data-stu-id="e6b36-134">The default value is _Enable_.</span></span> |
|<span data-ttu-id="e6b36-135">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="e6b36-135">PsDscRunAsCredential</span></span> |<span data-ttu-id="e6b36-136">Anger autentiseringsuppgifter för att köra hela resursen som.</span><span class="sxs-lookup"><span data-stu-id="e6b36-136">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="e6b36-137">Den gemensamma egenskapen **PsDscRunAsCredential** har lagts till i WMF 5,0 för att tillåta körning av DSC-resurser i kontexten för andra autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="e6b36-137">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="e6b36-138">Mer information finns i [använda autentiseringsuppgifter med DSC-resurser](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="e6b36-138">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>