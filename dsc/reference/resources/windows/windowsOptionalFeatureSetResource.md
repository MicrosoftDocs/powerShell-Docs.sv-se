---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: DSC WindowsOptionalFeatureSet-resurs
ms.openlocfilehash: c27d026e01bbb443a82112e37f1d199fb3482e49
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55683949"
---
# <a name="dsc-windowsoptionalfeatureset-resource"></a><span data-ttu-id="5939b-103">DSC WindowsOptionalFeatureSet-resurs</span><span class="sxs-lookup"><span data-stu-id="5939b-103">DSC WindowsOptionalFeatureSet Resource</span></span>

> <span data-ttu-id="5939b-104">Gäller för: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="5939b-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="5939b-105">Den **WindowsOptionalFeatureSet** resursen i Windows PowerShell Desired State Configuration (DSC) är en mekanism för att säkerställa att valfria funktioner är aktiverade på målnoden.</span><span class="sxs-lookup"><span data-stu-id="5939b-105">The **WindowsOptionalFeatureSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that optional features are enabled on a target node.</span></span>
<span data-ttu-id="5939b-106">Den här resursen är en [sammansatta resource](../../../resources/authoringResourceComposite.md) som anropar den [WindowsOptionalFeature-resurs](windowsOptionalFeatureResource.md) för varje funktion som anges i den `Name` egenskapen.</span><span class="sxs-lookup"><span data-stu-id="5939b-106">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [WindowsOptionalFeature resource](windowsOptionalFeatureResource.md) for each feature specified in the `Name` property.</span></span>

<span data-ttu-id="5939b-107">Använd den här resursen när du vill konfigurera ett antal Windows valfria funktioner till samma tillstånd.</span><span class="sxs-lookup"><span data-stu-id="5939b-107">Use this resource when you want to configure a number of Windows optional features to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="5939b-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="5939b-108">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="5939b-109">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="5939b-109">Properties</span></span>

|  <span data-ttu-id="5939b-110">Egenskap</span><span class="sxs-lookup"><span data-stu-id="5939b-110">Property</span></span>  |  <span data-ttu-id="5939b-111">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5939b-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="5939b-112">Namn</span><span class="sxs-lookup"><span data-stu-id="5939b-112">Name</span></span>| <span data-ttu-id="5939b-113">Anger namnet på de funktioner som du vill se till att är aktiverade eller inaktiverade.</span><span class="sxs-lookup"><span data-stu-id="5939b-113">Indicates the name of the features that you want to ensure are enabled or disabled.</span></span>|
| <span data-ttu-id="5939b-114">Se till att</span><span class="sxs-lookup"><span data-stu-id="5939b-114">Ensure</span></span>| <span data-ttu-id="5939b-115">Anger om funktionerna är aktiverade.</span><span class="sxs-lookup"><span data-stu-id="5939b-115">Specifies whether the features are enabled.</span></span> <span data-ttu-id="5939b-116">För att säkerställa att funktionerna är aktiverade, ange den här egenskapen till ”aktivera” för att säkerställa att funktionerna är inaktiverade, egenskapen till ”inaktivera”.</span><span class="sxs-lookup"><span data-stu-id="5939b-116">To ensure that the features are enabled, set this property to "Enable" To ensure that the features are disabled, set the property to "Disable".</span></span>|
| <span data-ttu-id="5939b-117">Källa</span><span class="sxs-lookup"><span data-stu-id="5939b-117">Source</span></span>| <span data-ttu-id="5939b-118">Inte implementerat.</span><span class="sxs-lookup"><span data-stu-id="5939b-118">Not implemented.</span></span>|
| <span data-ttu-id="5939b-119">NoWindowsUpdateCheck</span><span class="sxs-lookup"><span data-stu-id="5939b-119">NoWindowsUpdateCheck</span></span>| <span data-ttu-id="5939b-120">Anger om DISM kontaktar Windows Update (WU) när du söker efter källfilerna för att aktivera funktioner.</span><span class="sxs-lookup"><span data-stu-id="5939b-120">Specifies whether DISM contacts Windows Update (WU) when searching for the source files to enable features.</span></span> <span data-ttu-id="5939b-121">Om $true DISM inte kontaktar WU.</span><span class="sxs-lookup"><span data-stu-id="5939b-121">If $true, DISM does not contact WU.</span></span>|
| <span data-ttu-id="5939b-122">RemoveFilesOnDisable</span><span class="sxs-lookup"><span data-stu-id="5939b-122">RemoveFilesOnDisable</span></span>| <span data-ttu-id="5939b-123">Inställd **$true** att ta bort alla filer som är associerade med funktioner när de är inaktiverade (det vill säga när **Kontrollera** anges till ””).</span><span class="sxs-lookup"><span data-stu-id="5939b-123">Set to **$true** to remove all files associated with the features when they are disabled (that is, when **Ensure** is set to "Absent").</span></span>|
| <span data-ttu-id="5939b-124">Loggnivå</span><span class="sxs-lookup"><span data-stu-id="5939b-124">LogLevel</span></span>| <span data-ttu-id="5939b-125">Den maximala utdatanivån som visas i loggarna.</span><span class="sxs-lookup"><span data-stu-id="5939b-125">The maximum output level shown in the logs.</span></span> <span data-ttu-id="5939b-126">Godkända värden är: ”ErrorsOnly” (endast fel loggas), ”ErrorsAndWarning” (fel och varningar loggas), och ”ErrorsAndWarningAndInformation” (fel, varningar och felsökningsinformation loggas).</span><span class="sxs-lookup"><span data-stu-id="5939b-126">The accepted values are: "ErrorsOnly" (only errors are logged), "ErrorsAndWarning" (errors and warnings are logged), and "ErrorsAndWarningAndInformation" (errors, warnings, and debug information are logged).</span></span>|
| <span data-ttu-id="5939b-127">LogPath</span><span class="sxs-lookup"><span data-stu-id="5939b-127">LogPath</span></span>| <span data-ttu-id="5939b-128">Sökvägen till en loggfil där du vill att resursprovidern att logga in igen.</span><span class="sxs-lookup"><span data-stu-id="5939b-128">The path to a log file where you want the resource provider to log the operation.</span></span>|
| <span data-ttu-id="5939b-129">DependsOn</span><span class="sxs-lookup"><span data-stu-id="5939b-129">DependsOn</span></span>| <span data-ttu-id="5939b-130">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats.</span><span class="sxs-lookup"><span data-stu-id="5939b-130">Specifies that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="5939b-131">Till exempel om ID för resurskonfigurationen skriptblock som du vill köra först är __ResourceName__ och är av typen __ResourceType__, syntaxen för den här egenskapen är `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="5939b-131">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
