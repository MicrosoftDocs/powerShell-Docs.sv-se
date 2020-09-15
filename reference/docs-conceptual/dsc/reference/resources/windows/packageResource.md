---
ms.date: 07/16/2020
keywords: DSC, PowerShell, konfiguration, installation
title: Resurs för DSC-paket
ms.openlocfilehash: faeebc5bac7caad733600720f1c9f3d916d4c0a8
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464017"
---
# <a name="dsc-package-resource"></a><span data-ttu-id="1360a-103">Resurs för DSC-paket</span><span class="sxs-lookup"><span data-stu-id="1360a-103">DSC Package Resource</span></span>

> <span data-ttu-id="1360a-104">Gäller för: Windows PowerShell 4,0, Windows PowerShell 5. x</span><span class="sxs-lookup"><span data-stu-id="1360a-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="1360a-105">**Paket** resursen i Windows PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att installera eller avinstallera paket, till exempel Windows Installer och setup.exe paket, på en målnod.</span><span class="sxs-lookup"><span data-stu-id="1360a-105">The **Package** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall packages, such as Windows Installer and setup.exe packages, on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="1360a-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="1360a-106">Syntax</span></span>

```Syntax
Package [string] #ResourceName
{
    Name = [string]
    Path = [string]
    ProductId = [string]
    [ Arguments = [string] ]
    [ Credential = [PSCredential] ]
    [ LogPath = [string] ]
    [ ReturnCode = [UInt32[]] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="1360a-107">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="1360a-107">Properties</span></span>

|<span data-ttu-id="1360a-108">Egenskap</span><span class="sxs-lookup"><span data-stu-id="1360a-108">Property</span></span> |<span data-ttu-id="1360a-109">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="1360a-109">Description</span></span> |
|---|---|
|<span data-ttu-id="1360a-110">Name</span><span class="sxs-lookup"><span data-stu-id="1360a-110">Name</span></span> |<span data-ttu-id="1360a-111">Anger namnet på det paket som du vill säkerställa ett speciellt tillstånd för.</span><span class="sxs-lookup"><span data-stu-id="1360a-111">Indicates the name of the package for which you want to ensure a specific state.</span></span> |
|<span data-ttu-id="1360a-112">Sökväg</span><span class="sxs-lookup"><span data-stu-id="1360a-112">Path</span></span> |<span data-ttu-id="1360a-113">Anger sökvägen dit paketet finns.</span><span class="sxs-lookup"><span data-stu-id="1360a-113">Indicates the path where the package resides.</span></span> |
|<span data-ttu-id="1360a-114">ProductId</span><span class="sxs-lookup"><span data-stu-id="1360a-114">ProductId</span></span> |<span data-ttu-id="1360a-115">Anger det produkt-ID som unikt identifierar paketet.</span><span class="sxs-lookup"><span data-stu-id="1360a-115">Indicates the product ID that uniquely identifies the package.</span></span> |
|<span data-ttu-id="1360a-116">Argument</span><span class="sxs-lookup"><span data-stu-id="1360a-116">Arguments</span></span> |<span data-ttu-id="1360a-117">Visar en sträng med argument som skickas till paketet exakt som de anges.</span><span class="sxs-lookup"><span data-stu-id="1360a-117">Lists a string of arguments that will be passed to the package exactly as provided.</span></span> |
|<span data-ttu-id="1360a-118">Autentiseringsuppgift</span><span class="sxs-lookup"><span data-stu-id="1360a-118">Credential</span></span> |<span data-ttu-id="1360a-119">Ger åtkomst till paketet på en fjärran sluten källa.</span><span class="sxs-lookup"><span data-stu-id="1360a-119">Provides access to the package on a remote source.</span></span> <span data-ttu-id="1360a-120">Den här egenskapen används inte för att installera paketet.</span><span class="sxs-lookup"><span data-stu-id="1360a-120">This property is not used to install the package.</span></span> <span data-ttu-id="1360a-121">Paketet är alltid installerat på det lokala systemet.</span><span class="sxs-lookup"><span data-stu-id="1360a-121">The package is always installed on the local system.</span></span> |
|<span data-ttu-id="1360a-122">LogPath</span><span class="sxs-lookup"><span data-stu-id="1360a-122">LogPath</span></span> |<span data-ttu-id="1360a-123">Anger den fullständiga sökvägen dit du vill att providern ska spara en loggfil för att installera eller avinstallera paketet.</span><span class="sxs-lookup"><span data-stu-id="1360a-123">Indicates the full path where you want the provider to save a log file to install or uninstall the package.</span></span> |
|<span data-ttu-id="1360a-124">ReturnCode</span><span class="sxs-lookup"><span data-stu-id="1360a-124">ReturnCode</span></span> |<span data-ttu-id="1360a-125">Anger den förväntade retur koden.</span><span class="sxs-lookup"><span data-stu-id="1360a-125">Indicates the expected return code.</span></span> <span data-ttu-id="1360a-126">Om den faktiska retur koden inte matchar det förväntade värdet här, returnerar konfigurationen ett fel.</span><span class="sxs-lookup"><span data-stu-id="1360a-126">If the actual return code does not match the expected value provided here, the configuration will return an error.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="1360a-127">Gemensamma egenskaper</span><span class="sxs-lookup"><span data-stu-id="1360a-127">Common properties</span></span>

|<span data-ttu-id="1360a-128">Egenskap</span><span class="sxs-lookup"><span data-stu-id="1360a-128">Property</span></span> |<span data-ttu-id="1360a-129">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="1360a-129">Description</span></span> |
|---|---|
|<span data-ttu-id="1360a-130">DependsOn</span><span class="sxs-lookup"><span data-stu-id="1360a-130">DependsOn</span></span> |<span data-ttu-id="1360a-131">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS.</span><span class="sxs-lookup"><span data-stu-id="1360a-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="1360a-132">Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är syntaxen för att använda den här egenskapen `DependsOn = "[ResourceType]ResourceName"` .</span><span class="sxs-lookup"><span data-stu-id="1360a-132">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="1360a-133">Kontrol</span><span class="sxs-lookup"><span data-stu-id="1360a-133">Ensure</span></span> |<span data-ttu-id="1360a-134">Anger om paketet är installerat.</span><span class="sxs-lookup"><span data-stu-id="1360a-134">Indicates if the package is installed.</span></span> <span data-ttu-id="1360a-135">Ange den här egenskapen som **saknas** för att se till att paketet inte är installerat (eller avinstallera paketet om det är installerat).</span><span class="sxs-lookup"><span data-stu-id="1360a-135">Set this property to **Absent** to ensure the package is not installed (or uninstall the package if it is installed).</span></span> <span data-ttu-id="1360a-136">Ange att det är **tillgängligt** för att se till att paketet är installerat.</span><span class="sxs-lookup"><span data-stu-id="1360a-136">Set it to **Present** to ensure the package is installed.</span></span> <span data-ttu-id="1360a-137">Standardvärdet finns **.**</span><span class="sxs-lookup"><span data-stu-id="1360a-137">The default value is **Present**.</span></span> |
|<span data-ttu-id="1360a-138">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="1360a-138">PsDscRunAsCredential</span></span> |<span data-ttu-id="1360a-139">Anger autentiseringsuppgifter för att köra hela resursen som.</span><span class="sxs-lookup"><span data-stu-id="1360a-139">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="1360a-140">Den gemensamma egenskapen **PsDscRunAsCredential** har lagts till i WMF 5,0 för att tillåta körning av DSC-resurser i kontexten för andra autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="1360a-140">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="1360a-141">Mer information finns i [använda autentiseringsuppgifter med DSC-resurser](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="1360a-141">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="1360a-142">Exempel</span><span class="sxs-lookup"><span data-stu-id="1360a-142">Example</span></span>

<span data-ttu-id="1360a-143">Det här exemplet kör msi-installationsprogrammet som finns på den angivna sökvägen och har det angivna produkt-ID: t.</span><span class="sxs-lookup"><span data-stu-id="1360a-143">This example runs the .msi installer that is located at the specified path and has the specified product ID.</span></span>

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
