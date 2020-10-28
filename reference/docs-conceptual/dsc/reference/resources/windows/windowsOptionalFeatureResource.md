---
ms.date: 08/28/2020
ms.topic: reference
title: DSC WindowsOptionalFeature-resurs
description: DSC WindowsOptionalFeature-resurs
ms.openlocfilehash: edaa69f956033e6036b88f63b6b40832ad3a32f9
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92656603"
---
# <a name="dsc-windowsoptionalfeature-resource"></a><span data-ttu-id="1e665-103">DSC WindowsOptionalFeature-resurs</span><span class="sxs-lookup"><span data-stu-id="1e665-103">DSC WindowsOptionalFeature Resource</span></span>

> <span data-ttu-id="1e665-104">Gäller för: Windows PowerShell 5. x</span><span class="sxs-lookup"><span data-stu-id="1e665-104">Applies To: Windows PowerShell 5.x</span></span>

<span data-ttu-id="1e665-105">**WindowsOptionalFeature** -resursen i Windows PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att säkerställa att valfria funktioner aktive ras på en målnod.</span><span class="sxs-lookup"><span data-stu-id="1e665-105">The **WindowsOptionalFeature** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that optional features are enabled on a target node.</span></span>

> [!NOTE]
> <span data-ttu-id="1e665-106">**WindowsOptionalFeature** fungerar bara på Windows-klient datorer som Windows 10.</span><span class="sxs-lookup"><span data-stu-id="1e665-106">**WindowsOptionalFeature** only works on Windows client machines like Windows 10.</span></span>

## <a name="syntax"></a><span data-ttu-id="1e665-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="1e665-107">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="1e665-108">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="1e665-108">Properties</span></span>

|<span data-ttu-id="1e665-109">Egenskap</span><span class="sxs-lookup"><span data-stu-id="1e665-109">Property</span></span> |<span data-ttu-id="1e665-110">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="1e665-110">Description</span></span> |
|---|---|
|<span data-ttu-id="1e665-111">Namn</span><span class="sxs-lookup"><span data-stu-id="1e665-111">Name</span></span> |<span data-ttu-id="1e665-112">Anger namnet på den funktion som du vill se är aktive rad eller inaktive rad.</span><span class="sxs-lookup"><span data-stu-id="1e665-112">Indicates the name of the feature that you want to ensure is enabled or disabled.</span></span> |
|<span data-ttu-id="1e665-113">NoWindowsUpdateCheck</span><span class="sxs-lookup"><span data-stu-id="1e665-113">NoWindowsUpdateCheck</span></span> |<span data-ttu-id="1e665-114">Anger om DISM-kontakter Windows Update (WU) vid sökning efter källfiler för att aktivera en funktion.</span><span class="sxs-lookup"><span data-stu-id="1e665-114">Specifies whether DISM contacts Windows Update (WU) when searching for the source files to enable a feature.</span></span> <span data-ttu-id="1e665-115">Om inte `$true` DISM kontaktar Wu.</span><span class="sxs-lookup"><span data-stu-id="1e665-115">If `$true`, DISM does not contact WU.</span></span> |
|<span data-ttu-id="1e665-116">RemoveFilesOnDisable</span><span class="sxs-lookup"><span data-stu-id="1e665-116">RemoveFilesOnDisable</span></span> |<span data-ttu-id="1e665-117">Ange till `$true` om du vill ta bort alla filer som är associerade med funktionen när **Se** till att den är inställd på **frånvarande** .</span><span class="sxs-lookup"><span data-stu-id="1e665-117">Set to `$true` to remove all files associated with the feature when **Ensure** is set to **Absent** .</span></span> |
|<span data-ttu-id="1e665-118">Loggnivå</span><span class="sxs-lookup"><span data-stu-id="1e665-118">LogLevel</span></span> |<span data-ttu-id="1e665-119">Den högsta utmatnings nivån som visas i loggarna.</span><span class="sxs-lookup"><span data-stu-id="1e665-119">The maximum output level shown in the logs.</span></span> <span data-ttu-id="1e665-120">Godkända värden är: **ErrorsOnly** , **ErrorsAndWarning** och **ErrorsAndWarningAndInformation** .</span><span class="sxs-lookup"><span data-stu-id="1e665-120">The accepted values are: **ErrorsOnly** , **ErrorsAndWarning** , and **ErrorsAndWarningAndInformation** .</span></span> |
|<span data-ttu-id="1e665-121">LogPath</span><span class="sxs-lookup"><span data-stu-id="1e665-121">LogPath</span></span> |<span data-ttu-id="1e665-122">Sökvägen till logg filen där du vill att resurs leverantören ska logga åtgärden.</span><span class="sxs-lookup"><span data-stu-id="1e665-122">The path to a log file where you want the resource provider to log the operation.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="1e665-123">Gemensamma egenskaper</span><span class="sxs-lookup"><span data-stu-id="1e665-123">Common properties</span></span>

|<span data-ttu-id="1e665-124">Egenskap</span><span class="sxs-lookup"><span data-stu-id="1e665-124">Property</span></span> |<span data-ttu-id="1e665-125">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="1e665-125">Description</span></span> |
|---|---|
|<span data-ttu-id="1e665-126">DependsOn</span><span class="sxs-lookup"><span data-stu-id="1e665-126">DependsOn</span></span> |<span data-ttu-id="1e665-127">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS.</span><span class="sxs-lookup"><span data-stu-id="1e665-127">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="1e665-128">Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är syntaxen för att använda den här egenskapen `DependsOn = "[ResourceType]ResourceName"` .</span><span class="sxs-lookup"><span data-stu-id="1e665-128">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="1e665-129">Kontrol</span><span class="sxs-lookup"><span data-stu-id="1e665-129">Ensure</span></span> |<span data-ttu-id="1e665-130">Anger om funktionen är aktive rad.</span><span class="sxs-lookup"><span data-stu-id="1e665-130">Specifies whether the feature is enabled.</span></span> <span data-ttu-id="1e665-131">För att se till att funktionen är aktive rad ställer du in den här egenskapen på _Aktivera_ .</span><span class="sxs-lookup"><span data-stu-id="1e665-131">To ensure that the feature is enabled, set this property to _Enable_ .</span></span> <span data-ttu-id="1e665-132">För att se till att funktionen är inaktive rad ställer du in egenskapen på _inaktivera_ .</span><span class="sxs-lookup"><span data-stu-id="1e665-132">To ensure that the feature is disabled, set the property to _Disable_ .</span></span> <span data-ttu-id="1e665-133">Standardvärdet är _Enable_ .</span><span class="sxs-lookup"><span data-stu-id="1e665-133">The default value is _Enable_ .</span></span> |
|<span data-ttu-id="1e665-134">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="1e665-134">PsDscRunAsCredential</span></span> |<span data-ttu-id="1e665-135">Anger autentiseringsuppgifter för att köra hela resursen som.</span><span class="sxs-lookup"><span data-stu-id="1e665-135">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="1e665-136">Den gemensamma egenskapen **PsDscRunAsCredential** har lagts till i WMF 5,0 för att tillåta körning av DSC-resurser i kontexten för andra autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="1e665-136">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="1e665-137">Mer information finns i [använda autentiseringsuppgifter med DSC-resurser](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="1e665-137">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>
