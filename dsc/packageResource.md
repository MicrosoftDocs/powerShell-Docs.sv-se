---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: DSC-Paketresurs
ms.openlocfilehash: 16f7f1b8fa7b84bcfdeb09fdc46db9c93113e70c
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/16/2018
---
# <a name="dsc-package-resource"></a><span data-ttu-id="1f137-103">DSC-Paketresurs</span><span class="sxs-lookup"><span data-stu-id="1f137-103">DSC Package Resource</span></span>

> <span data-ttu-id="1f137-104">Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="1f137-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="1f137-105">Den **paketet** resurs i Windows PowerShell önskad tillstånd Configuration (DSC) ger dig möjlighet att installera eller avinstallera paket, till exempel Windows Installer och setup.exe paket på målnoden.</span><span class="sxs-lookup"><span data-stu-id="1f137-105">The **Package** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall packages, such as Windows Installer and setup.exe packages, on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="1f137-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="1f137-106">Syntax</span></span>

```
Package [string] #ResourceName
{
    Name = [string]
    Path = [string]
    ProductId = [string]
    [ Arguments = [string] ]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ ReturnCode = [UInt32[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="1f137-107">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="1f137-107">Properties</span></span>
|  <span data-ttu-id="1f137-108">Egenskap</span><span class="sxs-lookup"><span data-stu-id="1f137-108">Property</span></span>  |  <span data-ttu-id="1f137-109">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="1f137-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="1f137-110">Namn</span><span class="sxs-lookup"><span data-stu-id="1f137-110">Name</span></span>| <span data-ttu-id="1f137-111">Anger namnet på paketet som du vill se till att ett visst tillstånd.</span><span class="sxs-lookup"><span data-stu-id="1f137-111">Indicates the name of the package for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="1f137-112">Sökväg</span><span class="sxs-lookup"><span data-stu-id="1f137-112">Path</span></span>| <span data-ttu-id="1f137-113">Anger sökvägen där paketet finns.</span><span class="sxs-lookup"><span data-stu-id="1f137-113">Indicates the path where the package resides.</span></span>|
| <span data-ttu-id="1f137-114">ProductId</span><span class="sxs-lookup"><span data-stu-id="1f137-114">ProductId</span></span>| <span data-ttu-id="1f137-115">Anger produkt-ID som unikt identifierar paketet.</span><span class="sxs-lookup"><span data-stu-id="1f137-115">Indicates the product ID that uniquely identifies the package.</span></span>|
| <span data-ttu-id="1f137-116">Argument</span><span class="sxs-lookup"><span data-stu-id="1f137-116">Arguments</span></span>| <span data-ttu-id="1f137-117">Visar en sträng med argument som exakt så som kommer att skickas till paketet.</span><span class="sxs-lookup"><span data-stu-id="1f137-117">Lists a string of arguments that will be passed to the package exactly as provided.</span></span>|
| <span data-ttu-id="1f137-118">autentiseringsuppgifter</span><span class="sxs-lookup"><span data-stu-id="1f137-118">Credential</span></span>| <span data-ttu-id="1f137-119">Tillhandahåller åtkomst till paketet på en fjärrkälla.</span><span class="sxs-lookup"><span data-stu-id="1f137-119">Provides access to the package on a remote source.</span></span> <span data-ttu-id="1f137-120">Den här egenskapen används inte för att installera paketet.</span><span class="sxs-lookup"><span data-stu-id="1f137-120">This property is not used to install the package.</span></span> <span data-ttu-id="1f137-121">Paketet installeras alltid på det lokala systemet.</span><span class="sxs-lookup"><span data-stu-id="1f137-121">The package is always installed on the local system.</span></span>|
| <span data-ttu-id="1f137-122">Se till att</span><span class="sxs-lookup"><span data-stu-id="1f137-122">Ensure</span></span>| <span data-ttu-id="1f137-123">Anger om paketet har installerats.</span><span class="sxs-lookup"><span data-stu-id="1f137-123">Indicates if the package is installed.</span></span> <span data-ttu-id="1f137-124">Ange den här egenskapen till ”saknas” för att se till att paketet inte är installerat (eller avinstallera paketet om det är installerat).</span><span class="sxs-lookup"><span data-stu-id="1f137-124">Set this property to "Absent" to ensure the package is not installed (or uninstall the package if it is installed).</span></span> <span data-ttu-id="1f137-125">Ange att ”finns” (standardvärdet) för att säkerställa att paketet har installerats.</span><span class="sxs-lookup"><span data-stu-id="1f137-125">Set it to "Present" (the default value) to ensure the package is installed.</span></span>|
| <span data-ttu-id="1f137-126">LogPath</span><span class="sxs-lookup"><span data-stu-id="1f137-126">LogPath</span></span>| <span data-ttu-id="1f137-127">Anger den fullständiga sökvägen där du vill att providern ska spara en loggfil för att installera eller avinstallera paketet.</span><span class="sxs-lookup"><span data-stu-id="1f137-127">Indicates the full path where you want the provider to save a log file to install or uninstall the package.</span></span>|
| <span data-ttu-id="1f137-128">dependsOn</span><span class="sxs-lookup"><span data-stu-id="1f137-128">DependsOn</span></span> | <span data-ttu-id="1f137-129">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats.</span><span class="sxs-lookup"><span data-stu-id="1f137-129">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="1f137-130">Om ID för resurskonfigurationen skriptblock som du vill köra först är exempelvis **ResourceName** och dess typ är **ResourceType**, syntaxen för den här egenskapen är ”DependsOn =” [ResourceType] ResourceName ”''.</span><span class="sxs-lookup"><span data-stu-id="1f137-130">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is \`DependsOn = "[ResourceType]ResourceName"\`\`.</span></span>|
| <span data-ttu-id="1f137-131">Returkod</span><span class="sxs-lookup"><span data-stu-id="1f137-131">ReturnCode</span></span>| <span data-ttu-id="1f137-132">Anger den förväntade kod.</span><span class="sxs-lookup"><span data-stu-id="1f137-132">Indicates the expected return code.</span></span> <span data-ttu-id="1f137-133">Om den faktiska returkod matchar inte det förväntade värdet som anges här, konfigurationen returneras ett fel.</span><span class="sxs-lookup"><span data-stu-id="1f137-133">If the actual return code does not match the expected value provided here, the configuration will return an error.</span></span>|

## <a name="example"></a><span data-ttu-id="1f137-134">Exempel</span><span class="sxs-lookup"><span data-stu-id="1f137-134">Example</span></span>

<span data-ttu-id="1f137-135">Det här exemplet kör MSI-installationsprogrammet som finns på den angivna sökvägen och har en angiven produkt-ID.</span><span class="sxs-lookup"><span data-stu-id="1f137-135">This example runs the .msi installer that is located at the specified path and has the specified product ID.</span></span>

```powershell
Configuration PackageTest
{
    Package PackageExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Path        = "$Env:SystemDrive\TestFolder\TestProject.msi"
        Name        = "TestPackage"
        ProductId   = "ACDDCDAF-80C6-41E6-A1B9-8ABD8A05027E"
    }
}
```