---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: Resurs för DSC-WindowsOptionalFeature
ms.openlocfilehash: 4cb59151d69adb2a01b7c4bdcaf0e961c24b29a6
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-windowsoptionalfeature-resource"></a><span data-ttu-id="0caec-103">Resurs för DSC-WindowsOptionalFeature</span><span class="sxs-lookup"><span data-stu-id="0caec-103">DSC WindowsOptionalFeature Resource</span></span>

> <span data-ttu-id="0caec-104">Gäller för: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="0caec-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="0caec-105">Den **WindowsOptionalFeature** resurs i Windows PowerShell önskad tillstånd Configuration (DSC) tillhandahåller en mekanism för att säkerställa att valfria funktioner är aktiverade på målnoden.</span><span class="sxs-lookup"><span data-stu-id="0caec-105">The **WindowsOptionalFeature** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that optional features are enabled on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="0caec-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="0caec-106">Syntax</span></span>

```
WindowsOptionalFeature [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Enable | Disable }  ]
    [ Source = [string] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]

}
```

## <a name="properties"></a><span data-ttu-id="0caec-107">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="0caec-107">Properties</span></span>

|  <span data-ttu-id="0caec-108">Egenskap</span><span class="sxs-lookup"><span data-stu-id="0caec-108">Property</span></span>  |  <span data-ttu-id="0caec-109">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0caec-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="0caec-110">Namn</span><span class="sxs-lookup"><span data-stu-id="0caec-110">Name</span></span>| <span data-ttu-id="0caec-111">Anger namnet på funktionen som du vill kontrollera är aktiverat eller inaktiverat.</span><span class="sxs-lookup"><span data-stu-id="0caec-111">Indicates the name of the feature that you want to ensure is enabled or disabled.</span></span>|
| <span data-ttu-id="0caec-112">Se till att</span><span class="sxs-lookup"><span data-stu-id="0caec-112">Ensure</span></span>| <span data-ttu-id="0caec-113">Anger om funktionen är aktiverad.</span><span class="sxs-lookup"><span data-stu-id="0caec-113">Specifies whether the feature is enabled.</span></span> <span data-ttu-id="0caec-114">För att säkerställa att funktionen är aktiverad, Ställ in den här egenskapen till ”aktivera” för att säkerställa att funktionen är inaktiverad, egenskapen till ”inaktivera”.</span><span class="sxs-lookup"><span data-stu-id="0caec-114">To ensure that the feature is enabled, set this property to "Enable" To ensure that the feature is disabled, set the property to "Disable".</span></span>|
| <span data-ttu-id="0caec-115">Källa</span><span class="sxs-lookup"><span data-stu-id="0caec-115">Source</span></span>| <span data-ttu-id="0caec-116">Inte implementerat.</span><span class="sxs-lookup"><span data-stu-id="0caec-116">Not implemented.</span></span>|
| <span data-ttu-id="0caec-117">NoWindowsUpdateCheck</span><span class="sxs-lookup"><span data-stu-id="0caec-117">NoWindowsUpdateCheck</span></span>| <span data-ttu-id="0caec-118">Anger om DISM kontaktar Windows Update (WU) när du söker efter källfilerna för att aktivera en funktion.</span><span class="sxs-lookup"><span data-stu-id="0caec-118">Specifies whether DISM contacts Windows Update (WU) when searching for the source files to enable a feature.</span></span> <span data-ttu-id="0caec-119">Om $true DISM inte kontaktar WU.</span><span class="sxs-lookup"><span data-stu-id="0caec-119">If $true, DISM does not contact WU.</span></span>|
| <span data-ttu-id="0caec-120">RemoveFilesOnDisable</span><span class="sxs-lookup"><span data-stu-id="0caec-120">RemoveFilesOnDisable</span></span>| <span data-ttu-id="0caec-121">Värdet **$true** att ta bort alla filer som är associerade med funktionen när den är inaktiverad (det vill säga när **Kontrollera** anges till ”saknas”).</span><span class="sxs-lookup"><span data-stu-id="0caec-121">Set to **$true** to remove all files associated with the feature when it is disabled (that is, when **Ensure** is set to "Absent").</span></span>|
| <span data-ttu-id="0caec-122">Loggnivå</span><span class="sxs-lookup"><span data-stu-id="0caec-122">LogLevel</span></span>| <span data-ttu-id="0caec-123">Den maximala utdatanivån som visas i loggarna.</span><span class="sxs-lookup"><span data-stu-id="0caec-123">The maximum output level shown in the logs.</span></span> <span data-ttu-id="0caec-124">De giltiga värdena är: ”ErrorsOnly” (endast fel loggas), ”ErrorsAndWarning” (fel och varningar loggas), och ”ErrorsAndWarningAndInformation” (fel, varningar och felsökningsinformation loggas).</span><span class="sxs-lookup"><span data-stu-id="0caec-124">The accepted values are: "ErrorsOnly" (only errors are logged), "ErrorsAndWarning" (errors and warnings are logged), and "ErrorsAndWarningAndInformation" (errors, warnings, and debug information are logged).</span></span>|
| <span data-ttu-id="0caec-125">LogPath</span><span class="sxs-lookup"><span data-stu-id="0caec-125">LogPath</span></span>| <span data-ttu-id="0caec-126">Sökvägen till en loggfil där du vill att resursprovidern att logga in igen.</span><span class="sxs-lookup"><span data-stu-id="0caec-126">The path to a log file where you want the resource provider to log the operation.</span></span>|
| <span data-ttu-id="0caec-127">dependsOn</span><span class="sxs-lookup"><span data-stu-id="0caec-127">DependsOn</span></span>| <span data-ttu-id="0caec-128">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats.</span><span class="sxs-lookup"><span data-stu-id="0caec-128">Specifies that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="0caec-129">Om ID för resurskonfigurationen skriptblock som du vill köra först är exempelvis __ResourceName__ och dess typ är __ResourceType__, syntaxen för den här egenskapen är `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="0caec-129">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|