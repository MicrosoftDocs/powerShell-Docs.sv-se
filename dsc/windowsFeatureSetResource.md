---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: DSC WindowsFeatureSet resurs
ms.openlocfilehash: a2bb008852ccfdc04998a57d3e64e08bf05e6433
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-windowsfeatureset-resource"></a><span data-ttu-id="87bcf-103">DSC WindowsFeatureSet resurs</span><span class="sxs-lookup"><span data-stu-id="87bcf-103">DSC WindowsFeatureSet Resource</span></span>

> <span data-ttu-id="87bcf-104">Gäller för: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="87bcf-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="87bcf-105">Den **WindowsFeatureSet** resurs i Windows PowerShell önskad tillstånd Configuration (DSC) tillhandahåller en mekanism för att säkerställa att roller och funktioner läggs till eller tas bort på målnoden.</span><span class="sxs-lookup"><span data-stu-id="87bcf-105">The **WindowsFeatureSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to ensure that roles and features are added or removed on a target node.</span></span>
<span data-ttu-id="87bcf-106">Den här resursen är en [sammansatta resurs](authoringResourceComposite.md) som anropar den [WindowsFeature resurs](windowsfeatureResource.md) för varje funktion som anges i den `Name` egenskapen.</span><span class="sxs-lookup"><span data-stu-id="87bcf-106">This resource is a [composite resource](authoringResourceComposite.md) that calls the [WindowsFeature resource](windowsfeatureResource.md) for each feature specified in the `Name` property.</span></span>

<span data-ttu-id="87bcf-107">Använd den här resursen när du vill konfigurera ett antal Windows-funktioner till samma tillstånd.</span><span class="sxs-lookup"><span data-stu-id="87bcf-107">Use this resource when you want to configure a number of Windows Features to the same state.</span></span>

## <a name="syntax"></a><span data-ttu-id="87bcf-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="87bcf-108">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="87bcf-109">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="87bcf-109">Properties</span></span>

|  <span data-ttu-id="87bcf-110">Egenskap</span><span class="sxs-lookup"><span data-stu-id="87bcf-110">Property</span></span>  |  <span data-ttu-id="87bcf-111">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="87bcf-111">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="87bcf-112">Namn</span><span class="sxs-lookup"><span data-stu-id="87bcf-112">Name</span></span>| <span data-ttu-id="87bcf-113">Namnen på de roller eller funktioner som du vill kontrollera läggs till eller tas bort.</span><span class="sxs-lookup"><span data-stu-id="87bcf-113">The names of the roles or features that you want to ensure are added or removed.</span></span> <span data-ttu-id="87bcf-114">Det här är samma som den **namn** -egenskapen för den [Get-WindowsFeature](https://technet.microsoft.com/en-us/library/jj205469.aspx) cmdlet, och inte visningsnamnet för roller eller funktioner.</span><span class="sxs-lookup"><span data-stu-id="87bcf-114">This is the same as the **Name** property of the [Get-WindowsFeature](https://technet.microsoft.com/en-us/library/jj205469.aspx) cmdlet, and not the display name of the roles or features.</span></span>| 
| <span data-ttu-id="87bcf-115">autentiseringsuppgifter</span><span class="sxs-lookup"><span data-stu-id="87bcf-115">Credential</span></span>| <span data-ttu-id="87bcf-116">Autentiseringsuppgifter som ska användas för att lägga till eller ta bort roller och funktioner.</span><span class="sxs-lookup"><span data-stu-id="87bcf-116">The credentials to use to add or remove the roles or features.</span></span>| 
| <span data-ttu-id="87bcf-117">Se till att</span><span class="sxs-lookup"><span data-stu-id="87bcf-117">Ensure</span></span>| <span data-ttu-id="87bcf-118">Anger om roller och funktioner har lagts till.</span><span class="sxs-lookup"><span data-stu-id="87bcf-118">Indicates whether the roles or features are added.</span></span> <span data-ttu-id="87bcf-119">För att säkerställa att de roller eller funktioner är tillagt, Ställ in den här egenskapen till ”finns” för att säkerställa att bort roller eller funktioner, egenskapen till ”saknas”.</span><span class="sxs-lookup"><span data-stu-id="87bcf-119">To ensure that the roles or features are added, set this property to "Present" To ensure that the roles or features are removed, set the property to "Absent".</span></span>| 
| <span data-ttu-id="87bcf-120">IncludeAllSubFeature</span><span class="sxs-lookup"><span data-stu-id="87bcf-120">IncludeAllSubFeature</span></span>| <span data-ttu-id="87bcf-121">Den här egenskapen **$true** att inkludera alla nödvändiga underfunktioner med funktioner som du anger med den **namn** egenskapen.</span><span class="sxs-lookup"><span data-stu-id="87bcf-121">Set this property to **$true** to include all required subfeatures with of the features you specify with the **Name** property.</span></span>| 
| <span data-ttu-id="87bcf-122">LogPath</span><span class="sxs-lookup"><span data-stu-id="87bcf-122">LogPath</span></span>| <span data-ttu-id="87bcf-123">Sökvägen till en loggfil där du vill att resursprovidern att logga in igen.</span><span class="sxs-lookup"><span data-stu-id="87bcf-123">The path to a log file where you want the resource provider to log the operation.</span></span>| 
| <span data-ttu-id="87bcf-124">dependsOn</span><span class="sxs-lookup"><span data-stu-id="87bcf-124">DependsOn</span></span>| <span data-ttu-id="87bcf-125">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats.</span><span class="sxs-lookup"><span data-stu-id="87bcf-125">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="87bcf-126">Om ID för resurskonfigurationen skriptblock som du vill köra först är exempelvis __ResourceName__ och dess typ är __ResourceType__, syntaxen för den här egenskapen är `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="87bcf-126">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 
| <span data-ttu-id="87bcf-127">Källa</span><span class="sxs-lookup"><span data-stu-id="87bcf-127">Source</span></span>| <span data-ttu-id="87bcf-128">Anger platsen för källfilen för installationen, om det behövs.</span><span class="sxs-lookup"><span data-stu-id="87bcf-128">Indicates the location of the source file to use for installation, if necessary.</span></span>| 

## <a name="example"></a><span data-ttu-id="87bcf-129">Exempel</span><span class="sxs-lookup"><span data-stu-id="87bcf-129">Example</span></span>

<span data-ttu-id="87bcf-130">Följande konfiguration ser till att den **Web Server** (IIS) och **SMTP-servern** funktioner och dess underfunktioner vardera, installeras.</span><span class="sxs-lookup"><span data-stu-id="87bcf-130">The following configuration ensures that the **Web-Server** (IIS) and **SMTP Server** features, and all subfeatures of each, are installed.</span></span>

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

