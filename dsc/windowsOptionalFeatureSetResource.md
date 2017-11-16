---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: DSC WindowsOptionalFeatureSet resurs
ms.openlocfilehash: 3bf6a993d0ec9ce71c1e9222ddaa3bb429accb15
ms.sourcegitcommit: 79e8f03afb8d0b0bb0a167e56464929b27f51990
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/26/2017
---
# <a name="dsc-windowsoptionalfeatureset-resource"></a><span data-ttu-id="7e2ef-103">DSC WindowsOptionalFeatureSet resurs</span><span class="sxs-lookup"><span data-stu-id="7e2ef-103">DSC WindowsOptionalFeatureSet Resource</span></span>

> <span data-ttu-id="7e2ef-104">Gäller för: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="7e2ef-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="7e2ef-105">Den **WindowsOptionalFeatureSet** resurs i Windows PowerShell önskad tillstånd Configuration (DSC) tillhandahåller en mekanism för att säkerställa att valfria funktioner är aktiverade på målnoden.</span><span class="sxs-lookup"><span data-stu-id="7e2ef-105">The **WindowsOptionalFeatureSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that optional features are enabled on a target node.</span></span> <span data-ttu-id="7e2ef-106">Den här resursen är en [sammansatta resurs](authoringResourceComposite.md) som anropar den [WindowsOptionalFeature resurs](windowsOptionalFeatureResource.md) för varje funktion som anges i den `Name` egenskapen.</span><span class="sxs-lookup"><span data-stu-id="7e2ef-106">This resource is a [composite resource](authoringResourceComposite.md) that calls the [WindowsOptionalFeature resource](windowsOptionalFeatureResource.md) for each feature specified in the `Name` property.</span></span>

<span data-ttu-id="7e2ef-107">Använd den här resursen när du vill konfigurera ett antal Windows valfria funktioner till samma tillstånd.</span><span class="sxs-lookup"><span data-stu-id="7e2ef-107">Use this resource when you want to configure a number of Windows optional features to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="7e2ef-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="7e2ef-108">Syntax</span></span>

```
WindowsOptionalFeature [string] #ResourceName
{
    Name = [string[]]
    [ Ensure = [string] { Enable | Disable }  ]
    [ Source = [string] ] 
    [ RemoveFilesOnDisable = [bool] ]  
    [ LogPath = [string] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ DependsOn = [string[]] ]
    
}
```

## <a name="properties"></a><span data-ttu-id="7e2ef-109">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="7e2ef-109">Properties</span></span>

|  <span data-ttu-id="7e2ef-110">Egenskap</span><span class="sxs-lookup"><span data-stu-id="7e2ef-110">Property</span></span>  |  <span data-ttu-id="7e2ef-111">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7e2ef-111">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="7e2ef-112">Namn</span><span class="sxs-lookup"><span data-stu-id="7e2ef-112">Name</span></span>| <span data-ttu-id="7e2ef-113">Anger namnet på de funktioner som du vill kontrollera är aktiverade eller inaktiverade.</span><span class="sxs-lookup"><span data-stu-id="7e2ef-113">Indicates the name of the features that you want to ensure are enabled or disabled.</span></span>| 
| <span data-ttu-id="7e2ef-114">Se till att</span><span class="sxs-lookup"><span data-stu-id="7e2ef-114">Ensure</span></span>| <span data-ttu-id="7e2ef-115">Anger om funktionerna är aktiverade.</span><span class="sxs-lookup"><span data-stu-id="7e2ef-115">Specifies whether the features are enabled.</span></span> <span data-ttu-id="7e2ef-116">För att säkerställa att funktionerna är aktiverade, ange den här egenskapen till ”aktivera” för att säkerställa att funktionerna är inaktiverade, egenskapen till ”inaktivera”.</span><span class="sxs-lookup"><span data-stu-id="7e2ef-116">To ensure that the features are enabled, set this property to "Enable" To ensure that the features are disabled, set the property to "Disable".</span></span>|
| <span data-ttu-id="7e2ef-117">Källa</span><span class="sxs-lookup"><span data-stu-id="7e2ef-117">Source</span></span>| <span data-ttu-id="7e2ef-118">Inte implementerat.</span><span class="sxs-lookup"><span data-stu-id="7e2ef-118">Not implemented.</span></span>|
| <span data-ttu-id="7e2ef-119">NoWindowsUpdateCheck</span><span class="sxs-lookup"><span data-stu-id="7e2ef-119">NoWindowsUpdateCheck</span></span>| <span data-ttu-id="7e2ef-120">Anger om DISM kontaktar Windows Update (WU) när du söker efter källfilerna för att aktivera funktioner.</span><span class="sxs-lookup"><span data-stu-id="7e2ef-120">Specifies whether DISM contacts Windows Update (WU) when searching for the source files to enable features.</span></span> <span data-ttu-id="7e2ef-121">Om $true DISM inte kontaktar WU.</span><span class="sxs-lookup"><span data-stu-id="7e2ef-121">If $true, DISM does not contact WU.</span></span>|
| <span data-ttu-id="7e2ef-122">RemoveFilesOnDisable</span><span class="sxs-lookup"><span data-stu-id="7e2ef-122">RemoveFilesOnDisable</span></span>| <span data-ttu-id="7e2ef-123">Värdet **$true** att ta bort alla filer som är associerat med funktioner när de är inaktiverade (det vill säga när **Kontrollera** anges till ”saknas”).</span><span class="sxs-lookup"><span data-stu-id="7e2ef-123">Set to **$true** to remove all files associated with the features when they are disabled (that is, when **Ensure** is set to "Absent").</span></span>|
| <span data-ttu-id="7e2ef-124">Loggnivå</span><span class="sxs-lookup"><span data-stu-id="7e2ef-124">LogLevel</span></span>| <span data-ttu-id="7e2ef-125">Den maximala utdatanivån som visas i loggarna.</span><span class="sxs-lookup"><span data-stu-id="7e2ef-125">The maximum output level shown in the logs.</span></span> <span data-ttu-id="7e2ef-126">De giltiga värdena är: ”ErrorsOnly” (endast fel loggas), ”ErrorsAndWarning” (fel och varningar loggas), och ”ErrorsAndWarningAndInformation” (fel, varningar och felsökningsinformation loggas).</span><span class="sxs-lookup"><span data-stu-id="7e2ef-126">The accepted values are: "ErrorsOnly" (only errors are logged), "ErrorsAndWarning" (errors and warnings are logged), and "ErrorsAndWarningAndInformation" (errors, warnings, and debug information are logged).</span></span>|
| <span data-ttu-id="7e2ef-127">LogPath</span><span class="sxs-lookup"><span data-stu-id="7e2ef-127">LogPath</span></span>| <span data-ttu-id="7e2ef-128">Sökvägen till en loggfil där du vill att resursprovidern att logga in igen.</span><span class="sxs-lookup"><span data-stu-id="7e2ef-128">The path to a log file where you want the resource provider to log the operation.</span></span>| 
| <span data-ttu-id="7e2ef-129">dependsOn</span><span class="sxs-lookup"><span data-stu-id="7e2ef-129">DependsOn</span></span>| <span data-ttu-id="7e2ef-130">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats.</span><span class="sxs-lookup"><span data-stu-id="7e2ef-130">Specifies that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="7e2ef-131">Om ID för resurskonfigurationen skriptblock som du vill köra först är exempelvis __ResourceName__ och dess typ är __ResourceType__, syntaxen för den här egenskapen är `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="7e2ef-131">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 
 



