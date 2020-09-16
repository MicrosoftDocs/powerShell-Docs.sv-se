---
ms.date: 08/28/2020
keywords: DSC, PowerShell, konfiguration, installation
title: DSC WindowsOptionalFeature-resurs
ms.openlocfilehash: f24173c1a9ed605bac43767a9da2d4dbded78883
ms.sourcegitcommit: 06b6f4012e4eca71d414733cdba23ef75535223c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/29/2020
ms.locfileid: "89093258"
---
# <a name="dsc-windowsoptionalfeature-resource"></a><span data-ttu-id="feb46-103">DSC WindowsOptionalFeature-resurs</span><span class="sxs-lookup"><span data-stu-id="feb46-103">DSC WindowsOptionalFeature Resource</span></span>

> <span data-ttu-id="feb46-104">Gäller för: Windows PowerShell 5. x</span><span class="sxs-lookup"><span data-stu-id="feb46-104">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="feb46-105">**WindowsOptionalFeature** -resursen i Windows PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att säkerställa att valfria funktioner aktive ras på en målnod.</span><span class="sxs-lookup"><span data-stu-id="feb46-105">The **WindowsOptionalFeature** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that optional features are enabled on a target node.</span></span>

> [!NOTE]
> <span data-ttu-id="feb46-106">**WindowsOptionalFeature** fungerar bara på Windows-klient datorer som Windows 10.</span><span class="sxs-lookup"><span data-stu-id="feb46-106">**WindowsOptionalFeature** only works on Windows client machines like Windows 10.</span></span>

## <a name="syntax"></a><span data-ttu-id="feb46-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="feb46-107">Syntax</span></span>

```Syntax
WindowsOptionalFeature [string] #ResourceName
{
    Name = [string]
    [ NoWindowsUpdateCheck = [bool] ]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Enable | Disable }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="feb46-108">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="feb46-108">Properties</span></span>

|<span data-ttu-id="feb46-109">Egenskap</span><span class="sxs-lookup"><span data-stu-id="feb46-109">Property</span></span> |<span data-ttu-id="feb46-110">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="feb46-110">Description</span></span> |
|---|---|
|<span data-ttu-id="feb46-111">Name</span><span class="sxs-lookup"><span data-stu-id="feb46-111">Name</span></span> |<span data-ttu-id="feb46-112">Anger namnet på den funktion som du vill se är aktive rad eller inaktive rad.</span><span class="sxs-lookup"><span data-stu-id="feb46-112">Indicates the name of the feature that you want to ensure is enabled or disabled.</span></span> |
|<span data-ttu-id="feb46-113">NoWindowsUpdateCheck</span><span class="sxs-lookup"><span data-stu-id="feb46-113">NoWindowsUpdateCheck</span></span> |<span data-ttu-id="feb46-114">Anger om DISM-kontakter Windows Update (WU) vid sökning efter källfiler för att aktivera en funktion.</span><span class="sxs-lookup"><span data-stu-id="feb46-114">Specifies whether DISM contacts Windows Update (WU) when searching for the source files to enable a feature.</span></span> <span data-ttu-id="feb46-115">Om inte `$true` DISM kontaktar Wu.</span><span class="sxs-lookup"><span data-stu-id="feb46-115">If `$true`, DISM does not contact WU.</span></span> |
|<span data-ttu-id="feb46-116">RemoveFilesOnDisable</span><span class="sxs-lookup"><span data-stu-id="feb46-116">RemoveFilesOnDisable</span></span> |<span data-ttu-id="feb46-117">Ange till `$true` om du vill ta bort alla filer som är associerade med funktionen när **Se** till att den är inställd på **frånvarande**.</span><span class="sxs-lookup"><span data-stu-id="feb46-117">Set to `$true` to remove all files associated with the feature when **Ensure** is set to **Absent**.</span></span> |
|<span data-ttu-id="feb46-118">Loggnivå</span><span class="sxs-lookup"><span data-stu-id="feb46-118">LogLevel</span></span> |<span data-ttu-id="feb46-119">Den högsta utmatnings nivån som visas i loggarna.</span><span class="sxs-lookup"><span data-stu-id="feb46-119">The maximum output level shown in the logs.</span></span> <span data-ttu-id="feb46-120">Godkända värden är: **ErrorsOnly**, **ErrorsAndWarning**och **ErrorsAndWarningAndInformation**.</span><span class="sxs-lookup"><span data-stu-id="feb46-120">The accepted values are: **ErrorsOnly**, **ErrorsAndWarning**, and **ErrorsAndWarningAndInformation**.</span></span> |
|<span data-ttu-id="feb46-121">LogPath</span><span class="sxs-lookup"><span data-stu-id="feb46-121">LogPath</span></span> |<span data-ttu-id="feb46-122">Sökvägen till logg filen där du vill att resurs leverantören ska logga åtgärden.</span><span class="sxs-lookup"><span data-stu-id="feb46-122">The path to a log file where you want the resource provider to log the operation.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="feb46-123">Gemensamma egenskaper</span><span class="sxs-lookup"><span data-stu-id="feb46-123">Common properties</span></span>

|<span data-ttu-id="feb46-124">Egenskap</span><span class="sxs-lookup"><span data-stu-id="feb46-124">Property</span></span> |<span data-ttu-id="feb46-125">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="feb46-125">Description</span></span> |
|---|---|
|<span data-ttu-id="feb46-126">DependsOn</span><span class="sxs-lookup"><span data-stu-id="feb46-126">DependsOn</span></span> |<span data-ttu-id="feb46-127">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS.</span><span class="sxs-lookup"><span data-stu-id="feb46-127">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="feb46-128">Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är syntaxen för att använda den här egenskapen `DependsOn = "[ResourceType]ResourceName"` .</span><span class="sxs-lookup"><span data-stu-id="feb46-128">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="feb46-129">Kontrol</span><span class="sxs-lookup"><span data-stu-id="feb46-129">Ensure</span></span> |<span data-ttu-id="feb46-130">Anger om funktionen är aktive rad.</span><span class="sxs-lookup"><span data-stu-id="feb46-130">Specifies whether the feature is enabled.</span></span> <span data-ttu-id="feb46-131">För att se till att funktionen är aktive rad ställer du in den här egenskapen på _Aktivera_.</span><span class="sxs-lookup"><span data-stu-id="feb46-131">To ensure that the feature is enabled, set this property to _Enable_.</span></span> <span data-ttu-id="feb46-132">För att se till att funktionen är inaktive rad ställer du in egenskapen på _inaktivera_.</span><span class="sxs-lookup"><span data-stu-id="feb46-132">To ensure that the feature is disabled, set the property to _Disable_.</span></span> <span data-ttu-id="feb46-133">Standardvärdet är _Enable_.</span><span class="sxs-lookup"><span data-stu-id="feb46-133">The default value is _Enable_.</span></span> |
|<span data-ttu-id="feb46-134">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="feb46-134">PsDscRunAsCredential</span></span> |<span data-ttu-id="feb46-135">Anger autentiseringsuppgifter för att köra hela resursen som.</span><span class="sxs-lookup"><span data-stu-id="feb46-135">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="feb46-136">Den gemensamma egenskapen **PsDscRunAsCredential** har lagts till i WMF 5,0 för att tillåta körning av DSC-resurser i kontexten för andra autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="feb46-136">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="feb46-137">Mer information finns i [använda autentiseringsuppgifter med DSC-resurser](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="feb46-137">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>
