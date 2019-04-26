---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: DSC WindowsFeatureSet-resurs
ms.openlocfilehash: 8b7c7e72dd58459bd19cb723e5790a82841515c0
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076794"
---
# <a name="dsc-windowsfeatureset-resource"></a><span data-ttu-id="d8d95-103">DSC WindowsFeatureSet-resurs</span><span class="sxs-lookup"><span data-stu-id="d8d95-103">DSC WindowsFeatureSet Resource</span></span>

> <span data-ttu-id="d8d95-104">Gäller för: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="d8d95-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="d8d95-105">Den **WindowsFeatureSet** resursen i Windows PowerShell Desired State Configuration (DSC) är en mekanism för att säkerställa att roller och funktioner läggs till eller tas bort på målnoden.</span><span class="sxs-lookup"><span data-stu-id="d8d95-105">The **WindowsFeatureSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that roles and features are added or removed on a target node.</span></span>
<span data-ttu-id="d8d95-106">Den här resursen är en [sammansatta resource](../../../resources/authoringResourceComposite.md) som anropar den [WindowsFeature-resurs](windowsfeatureResource.md) för varje funktion som anges i den `Name` egenskapen.</span><span class="sxs-lookup"><span data-stu-id="d8d95-106">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [WindowsFeature resource](windowsfeatureResource.md) for each feature specified in the `Name` property.</span></span>

<span data-ttu-id="d8d95-107">Använd den här resursen när du vill konfigurera ett antal Windows-funktioner till samma tillstånd.</span><span class="sxs-lookup"><span data-stu-id="d8d95-107">Use this resource when you want to configure a number of Windows Features to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="d8d95-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="d8d95-108">Syntax</span></span>

```
WindowsFeatureSet [string] #ResourceName
{
    Name = [string[]]
    [ Ensure = [string] { Absent | Present }  ]
    [ Source = [string] ]
    [ IncludeAllSubFeature = [bool] ]
    [ Credential = [PSCredential] ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]

}
```

## <a name="properties"></a><span data-ttu-id="d8d95-109">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="d8d95-109">Properties</span></span>

|  <span data-ttu-id="d8d95-110">Egenskap</span><span class="sxs-lookup"><span data-stu-id="d8d95-110">Property</span></span>  |  <span data-ttu-id="d8d95-111">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d8d95-111">Description</span></span>   |
|---|---|
| <span data-ttu-id="d8d95-112">Namn</span><span class="sxs-lookup"><span data-stu-id="d8d95-112">Name</span></span>| <span data-ttu-id="d8d95-113">Namnen på de roller och funktioner som du vill kontrollera läggs till eller tas bort.</span><span class="sxs-lookup"><span data-stu-id="d8d95-113">The names of the roles or features that you want to ensure are added or removed.</span></span> <span data-ttu-id="d8d95-114">Det här är samma som den **namn** egenskapen för den [Get-WindowsFeature](https://technet.microsoft.com/en-us/library/jj205469.aspx) cmdlet, och inte visningsnamnet för roller eller funktioner.</span><span class="sxs-lookup"><span data-stu-id="d8d95-114">This is the same as the **Name** property of the [Get-WindowsFeature](https://technet.microsoft.com/en-us/library/jj205469.aspx) cmdlet, and not the display name of the roles or features.</span></span>|
| <span data-ttu-id="d8d95-115">Autentiseringsuppgifter</span><span class="sxs-lookup"><span data-stu-id="d8d95-115">Credential</span></span>| <span data-ttu-id="d8d95-116">Autentiseringsuppgifterna som används för att lägga till eller ta bort roller och funktioner.</span><span class="sxs-lookup"><span data-stu-id="d8d95-116">The credentials to use to add or remove the roles or features.</span></span>|
| <span data-ttu-id="d8d95-117">Se till att</span><span class="sxs-lookup"><span data-stu-id="d8d95-117">Ensure</span></span>| <span data-ttu-id="d8d95-118">Anger om roller och funktioner har lagts till.</span><span class="sxs-lookup"><span data-stu-id="d8d95-118">Indicates whether the roles or features are added.</span></span> <span data-ttu-id="d8d95-119">För att säkerställa att de roller och funktioner är har lagts till, ange den här egenskapen ”aktuella” för att säkerställa att bort roller och funktioner, egenskapen till ””.</span><span class="sxs-lookup"><span data-stu-id="d8d95-119">To ensure that the roles or features are added, set this property to "Present" To ensure that the roles or features are removed, set the property to "Absent".</span></span>|
| <span data-ttu-id="d8d95-120">IncludeAllSubFeature</span><span class="sxs-lookup"><span data-stu-id="d8d95-120">IncludeAllSubFeature</span></span>| <span data-ttu-id="d8d95-121">Den här egenskapen **$true** att inkludera alla nödvändiga underfunktioner med funktioner som du anger med den **namn** egenskapen.</span><span class="sxs-lookup"><span data-stu-id="d8d95-121">Set this property to **$true** to include all required subfeatures with of the features you specify with the **Name** property.</span></span>|
| <span data-ttu-id="d8d95-122">LogPath</span><span class="sxs-lookup"><span data-stu-id="d8d95-122">LogPath</span></span>| <span data-ttu-id="d8d95-123">Sökvägen till en loggfil där du vill att resursprovidern att logga in igen.</span><span class="sxs-lookup"><span data-stu-id="d8d95-123">The path to a log file where you want the resource provider to log the operation.</span></span>|
| <span data-ttu-id="d8d95-124">DependsOn</span><span class="sxs-lookup"><span data-stu-id="d8d95-124">DependsOn</span></span>| <span data-ttu-id="d8d95-125">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats.</span><span class="sxs-lookup"><span data-stu-id="d8d95-125">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="d8d95-126">Till exempel om ID för resurskonfigurationen skriptblock som du vill köra först är __ResourceName__ och är av typen __ResourceType__, syntaxen för den här egenskapen är `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="d8d95-126">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="d8d95-127">Källa</span><span class="sxs-lookup"><span data-stu-id="d8d95-127">Source</span></span>| <span data-ttu-id="d8d95-128">Anger platsen för källfilen för installationen, om det behövs.</span><span class="sxs-lookup"><span data-stu-id="d8d95-128">Indicates the location of the source file to use for installation, if necessary.</span></span>|

## <a name="example"></a><span data-ttu-id="d8d95-129">Exempel</span><span class="sxs-lookup"><span data-stu-id="d8d95-129">Example</span></span>

<span data-ttu-id="d8d95-130">Följande konfiguration garanterar att den **-webbserver** (IIS) och **SMTP-servern** funktioner och dess underfunktioner vardera, är installerade.</span><span class="sxs-lookup"><span data-stu-id="d8d95-130">The following configuration ensures that the **Web-Server** (IIS) and **SMTP Server** features, and all subfeatures of each, are installed.</span></span>

```powershell
configuration FeatureSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        WindowsFeatureSet WindowsFeatureSetExample
        {
            Name                    = @("SMTP-Server", "Web-Server")
            Ensure                  = 'Present'
            IncludeAllSubFeature    = $true
        }
    }
}
```
