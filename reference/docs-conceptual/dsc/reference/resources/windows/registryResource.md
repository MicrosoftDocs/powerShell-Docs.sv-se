---
ms.date: 09/20/2019
keywords: DSC, PowerShell, konfiguration, installation
title: DSC register resurs
ms.openlocfilehash: be2f9134368784ad2d208362104ce046c49492e0
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71941336"
---
# <a name="dsc-registry-resource"></a><span data-ttu-id="51062-103">DSC register resurs</span><span class="sxs-lookup"><span data-stu-id="51062-103">DSC Registry Resource</span></span>

> <span data-ttu-id="51062-104">Gäller för: Windows PowerShell 4,0, Windows PowerShell 5. x</span><span class="sxs-lookup"><span data-stu-id="51062-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="51062-105">**Register** resursen i Windows PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att hantera register nycklar och värden på en målnod.</span><span class="sxs-lookup"><span data-stu-id="51062-105">The **Registry** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage registry keys and values on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="51062-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="51062-106">Syntax</span></span>

```Syntax
Registry [string] #ResourceName
{
    Key = [string]
    ValueName = [string]
    [ Force =  [bool]   ]
    [ Hex = [bool] ]
    [ ValueData = [string[]] ]
    [ ValueType = [string] { Binary | Dword | ExpandString | MultiString | Qword | String }  ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Present | Absent }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="51062-107">properties</span><span class="sxs-lookup"><span data-stu-id="51062-107">Properties</span></span>

|<span data-ttu-id="51062-108">Egenskap</span><span class="sxs-lookup"><span data-stu-id="51062-108">Property</span></span> |<span data-ttu-id="51062-109">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="51062-109">Description</span></span> |
|---|---|
|<span data-ttu-id="51062-110">Nyckel</span><span class="sxs-lookup"><span data-stu-id="51062-110">Key</span></span> |<span data-ttu-id="51062-111">Anger sökvägen till den register nyckel för vilken du vill säkerställa ett angivet tillstånd.</span><span class="sxs-lookup"><span data-stu-id="51062-111">Indicates the path of the registry key for which you want to ensure a specific state.</span></span> <span data-ttu-id="51062-112">Den här sökvägen måste innehålla Hive.</span><span class="sxs-lookup"><span data-stu-id="51062-112">This path must include the hive.</span></span> |
|<span data-ttu-id="51062-113">Värdets namn</span><span class="sxs-lookup"><span data-stu-id="51062-113">ValueName</span></span> |<span data-ttu-id="51062-114">Anger namnet på registervärdet.</span><span class="sxs-lookup"><span data-stu-id="51062-114">Indicates the name of the registry value.</span></span> <span data-ttu-id="51062-115">Om du vill lägga till eller ta bort en register nyckel anger du den här egenskapen som en tom sträng utan att ange **ValueType** eller **ValueData**.</span><span class="sxs-lookup"><span data-stu-id="51062-115">To add or remove a registry key, specify this property as an empty string without specifying **ValueType** or **ValueData**.</span></span> <span data-ttu-id="51062-116">Om du vill ändra eller ta bort standardvärdet för en register nyckel anger du den här egenskapen som en tom sträng och även anger **ValueType** eller **ValueData**.</span><span class="sxs-lookup"><span data-stu-id="51062-116">To modify or remove the default value of a registry key, specify this property as an empty string while also specifying **ValueType** or **ValueData**.</span></span> |
|<span data-ttu-id="51062-117">Force</span><span class="sxs-lookup"><span data-stu-id="51062-117">Force</span></span> |<span data-ttu-id="51062-118">Om den angivna register nyckeln **finns skrivs den** över med det nya värdet.</span><span class="sxs-lookup"><span data-stu-id="51062-118">If the specified registry key is present, **Force** overwrites it with the new value.</span></span> <span data-ttu-id="51062-119">Om du tar bort en register nyckel med under nycklar måste detta vara `$true`.</span><span class="sxs-lookup"><span data-stu-id="51062-119">If deleting a registry key with subkeys, this needs to be `$true`.</span></span> |
|<span data-ttu-id="51062-120">Hexadecimal</span><span class="sxs-lookup"><span data-stu-id="51062-120">Hex</span></span> |<span data-ttu-id="51062-121">Anger om data ska uttryckas i hexadecimalt format.</span><span class="sxs-lookup"><span data-stu-id="51062-121">Indicates if data will be expressed in hexadecimal format.</span></span> <span data-ttu-id="51062-122">Om det här alternativet anges visas DWORD/QWORD-värdet i hexadecimalt format.</span><span class="sxs-lookup"><span data-stu-id="51062-122">If specified, the DWORD/QWORD value data is presented in hexadecimal format.</span></span> <span data-ttu-id="51062-123">Inte giltigt för andra typer.</span><span class="sxs-lookup"><span data-stu-id="51062-123">Not valid for other types.</span></span> <span data-ttu-id="51062-124">Standardvärdet är `$false`.</span><span class="sxs-lookup"><span data-stu-id="51062-124">The default value is `$false`.</span></span> |
|<span data-ttu-id="51062-125">ValueData</span><span class="sxs-lookup"><span data-stu-id="51062-125">ValueData</span></span> |<span data-ttu-id="51062-126">Data för registervärdet.</span><span class="sxs-lookup"><span data-stu-id="51062-126">The data for the registry value.</span></span> |
|<span data-ttu-id="51062-127">Värdetyp</span><span class="sxs-lookup"><span data-stu-id="51062-127">ValueType</span></span> |<span data-ttu-id="51062-128">Anger typen för värdet.</span><span class="sxs-lookup"><span data-stu-id="51062-128">Indicates the type of the value.</span></span> <span data-ttu-id="51062-129">De typer som stöds är: **Sträng** (REG_SZ), **binär** (REG-Binary), **DWORD** (32-bit REG_DWORD), **QWORD** (64-bitars REG_QWORD), **multisträng** (REG_MULTI_SZ), **ExpandString** (REG_EXPAND_SZ).</span><span class="sxs-lookup"><span data-stu-id="51062-129">The supported types are: **String** (REG_SZ), **Binary** (REG-BINARY), **Dword** (32-bit REG_DWORD), **Qword** (64-bit REG_QWORD), **MultiString** (REG_MULTI_SZ), **ExpandString** (REG_EXPAND_SZ).</span></span> |

## <a name="common-properties"></a><span data-ttu-id="51062-130">Gemensamma egenskaper</span><span class="sxs-lookup"><span data-stu-id="51062-130">Common properties</span></span>

|<span data-ttu-id="51062-131">Egenskap</span><span class="sxs-lookup"><span data-stu-id="51062-131">Property</span></span> |<span data-ttu-id="51062-132">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="51062-132">Description</span></span> |
|---|---|
|<span data-ttu-id="51062-133">DependsOn</span><span class="sxs-lookup"><span data-stu-id="51062-133">DependsOn</span></span> |<span data-ttu-id="51062-134">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS.</span><span class="sxs-lookup"><span data-stu-id="51062-134">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="51062-135">Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är `DependsOn = "[ResourceType]ResourceName"`syntaxen för att använda den här egenskapen.</span><span class="sxs-lookup"><span data-stu-id="51062-135">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="51062-136">Kontrol</span><span class="sxs-lookup"><span data-stu-id="51062-136">Ensure</span></span> |<span data-ttu-id="51062-137">Anger om nyckeln och värdet finns.</span><span class="sxs-lookup"><span data-stu-id="51062-137">Indicates if the key and value exist.</span></span> <span data-ttu-id="51062-138">För att se till att de gör det anger du att den här egenskapen är **tillgänglig**.</span><span class="sxs-lookup"><span data-stu-id="51062-138">To ensure that they do, set this property to **Present**.</span></span> <span data-ttu-id="51062-139">För att säkerställa att de inte finns, ställer du in egenskapen på **saknas**.</span><span class="sxs-lookup"><span data-stu-id="51062-139">To ensure that they do not exist, set the property to **Absent**.</span></span> <span data-ttu-id="51062-140">Standardvärdet finns **.**</span><span class="sxs-lookup"><span data-stu-id="51062-140">The default value is **Present**.</span></span> |
|<span data-ttu-id="51062-141">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="51062-141">PsDscRunAsCredential</span></span> |<span data-ttu-id="51062-142">Anger autentiseringsuppgifter för att köra hela resursen som.</span><span class="sxs-lookup"><span data-stu-id="51062-142">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="51062-143">Den gemensamma egenskapen **PsDscRunAsCredential** har lagts till i WMF 5,0 för att tillåta körning av DSC-resurser i kontexten för andra autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="51062-143">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="51062-144">Mer information finns i [använda autentiseringsuppgifter med DSC-resurser](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="51062-144">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="51062-145">Exempel</span><span class="sxs-lookup"><span data-stu-id="51062-145">Example</span></span>

<span data-ttu-id="51062-146">Det här exemplet ser till att en nyckel med namnet "ExampleKey" finns **i\_den\_lokala** datahive-datorns Hive.</span><span class="sxs-lookup"><span data-stu-id="51062-146">This example ensures that a key named "ExampleKey" is present in the **HKEY\_LOCAL\_MACHINE** hive.</span></span>

```powershell
Configuration RegistryTest
{
    Registry RegistryExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Key         = "HKEY_LOCAL_MACHINE\SOFTWARE\ExampleKey"
        ValueName   = "TestValue"
        ValueData   = "TestData"
    }
}
```

> [!NOTE]
> <span data-ttu-id="51062-147">Att ändra en register inställning i `HKEY_CURRENT_USER` Hive kräver att konfigurationen körs med användarautentiseringsuppgifter, i stället för som systemet.</span><span class="sxs-lookup"><span data-stu-id="51062-147">Changing a registry setting in the `HKEY_CURRENT_USER` hive requires that the configuration runs with user credentials, rather than as the system.</span></span> <span data-ttu-id="51062-148">Du kan använda egenskapen **PsDscRunAsCredential** för att ange användarautentiseringsuppgifter för konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="51062-148">You can use the **PsDscRunAsCredential** property to specify user credentials for the configuration.</span></span> <span data-ttu-id="51062-149">Ett exempel finns i [köra DSC med](../../../configurations/runAsUser.md)användarautentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="51062-149">For an example, see [Running DSC with user credentials](../../../configurations/runAsUser.md).</span></span>