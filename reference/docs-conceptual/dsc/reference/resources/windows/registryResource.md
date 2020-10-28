---
ms.date: 07/16/2020
ms.topic: reference
title: DSC register resurs
description: DSC register resurs
ms.openlocfilehash: d2b88a4aefe704aa4d337ec53202669b43412802
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92661558"
---
# <a name="dsc-registry-resource"></a><span data-ttu-id="f8910-103">DSC register resurs</span><span class="sxs-lookup"><span data-stu-id="f8910-103">DSC Registry Resource</span></span>

> <span data-ttu-id="f8910-104">Gäller för: Windows PowerShell 4,0, Windows PowerShell 5. x</span><span class="sxs-lookup"><span data-stu-id="f8910-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="f8910-105">**Register** resursen i Windows PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att hantera register nycklar och värden på en målnod.</span><span class="sxs-lookup"><span data-stu-id="f8910-105">The **Registry** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage registry keys and values on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="f8910-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="f8910-106">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="f8910-107">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="f8910-107">Properties</span></span>

|<span data-ttu-id="f8910-108">Egenskap</span><span class="sxs-lookup"><span data-stu-id="f8910-108">Property</span></span> |<span data-ttu-id="f8910-109">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="f8910-109">Description</span></span> |
|---|---|
|<span data-ttu-id="f8910-110">Nyckel</span><span class="sxs-lookup"><span data-stu-id="f8910-110">Key</span></span> |<span data-ttu-id="f8910-111">Anger sökvägen till den register nyckel för vilken du vill säkerställa ett angivet tillstånd.</span><span class="sxs-lookup"><span data-stu-id="f8910-111">Indicates the path of the registry key for which you want to ensure a specific state.</span></span> <span data-ttu-id="f8910-112">Den här sökvägen måste innehålla Hive.</span><span class="sxs-lookup"><span data-stu-id="f8910-112">This path must include the hive.</span></span> |
|<span data-ttu-id="f8910-113">Värdets namn</span><span class="sxs-lookup"><span data-stu-id="f8910-113">ValueName</span></span> |<span data-ttu-id="f8910-114">Anger namnet på registervärdet.</span><span class="sxs-lookup"><span data-stu-id="f8910-114">Indicates the name of the registry value.</span></span> <span data-ttu-id="f8910-115">Om du vill lägga till eller ta bort en register nyckel anger du den här egenskapen som en tom sträng utan att ange **ValueType** eller **ValueData** .</span><span class="sxs-lookup"><span data-stu-id="f8910-115">To add or remove a registry key, specify this property as an empty string without specifying **ValueType** or **ValueData** .</span></span> <span data-ttu-id="f8910-116">Om du vill ändra eller ta bort standardvärdet för en register nyckel anger du den här egenskapen som en tom sträng och även anger **ValueType** eller **ValueData** .</span><span class="sxs-lookup"><span data-stu-id="f8910-116">To modify or remove the default value of a registry key, specify this property as an empty string while also specifying **ValueType** or **ValueData** .</span></span> |
|<span data-ttu-id="f8910-117">Force</span><span class="sxs-lookup"><span data-stu-id="f8910-117">Force</span></span> |<span data-ttu-id="f8910-118">Om den angivna register nyckeln **finns skrivs den** över med det nya värdet.</span><span class="sxs-lookup"><span data-stu-id="f8910-118">If the specified registry key is present, **Force** overwrites it with the new value.</span></span> <span data-ttu-id="f8910-119">Om du tar bort en register nyckel med under nycklar måste detta vara `$true` .</span><span class="sxs-lookup"><span data-stu-id="f8910-119">If deleting a registry key with subkeys, this needs to be `$true`.</span></span> |
|<span data-ttu-id="f8910-120">Hexadecimal</span><span class="sxs-lookup"><span data-stu-id="f8910-120">Hex</span></span> |<span data-ttu-id="f8910-121">Anger om data ska uttryckas i hexadecimalt format.</span><span class="sxs-lookup"><span data-stu-id="f8910-121">Indicates if data will be expressed in hexadecimal format.</span></span> <span data-ttu-id="f8910-122">Om det här alternativet anges visas DWORD/QWORD-värdet i hexadecimalt format.</span><span class="sxs-lookup"><span data-stu-id="f8910-122">If specified, the DWORD/QWORD value data is presented in hexadecimal format.</span></span> <span data-ttu-id="f8910-123">Inte giltigt för andra typer.</span><span class="sxs-lookup"><span data-stu-id="f8910-123">Not valid for other types.</span></span> <span data-ttu-id="f8910-124">Standardvärdet är `$false`.</span><span class="sxs-lookup"><span data-stu-id="f8910-124">The default value is `$false`.</span></span> |
|<span data-ttu-id="f8910-125">ValueData</span><span class="sxs-lookup"><span data-stu-id="f8910-125">ValueData</span></span> |<span data-ttu-id="f8910-126">Data för registervärdet.</span><span class="sxs-lookup"><span data-stu-id="f8910-126">The data for the registry value.</span></span> |
|<span data-ttu-id="f8910-127">Värdetyp</span><span class="sxs-lookup"><span data-stu-id="f8910-127">ValueType</span></span> |<span data-ttu-id="f8910-128">Anger typen för värdet.</span><span class="sxs-lookup"><span data-stu-id="f8910-128">Indicates the type of the value.</span></span> <span data-ttu-id="f8910-129">De typer som stöds är **: sträng** (REG_SZ), **binärt** (REG-Binary), **Dword** (32-bitars REG_DWORD), **QWORD** (64-bitars REG_QWORD), **Multistring** (REG_MULTI_SZ), **ExpandString** (REG_EXPAND_SZ).</span><span class="sxs-lookup"><span data-stu-id="f8910-129">The supported types are: **String** (REG_SZ), **Binary** (REG-BINARY), **Dword** (32-bit REG_DWORD), **Qword** (64-bit REG_QWORD), **MultiString** (REG_MULTI_SZ), **ExpandString** (REG_EXPAND_SZ).</span></span> |

## <a name="common-properties"></a><span data-ttu-id="f8910-130">Gemensamma egenskaper</span><span class="sxs-lookup"><span data-stu-id="f8910-130">Common properties</span></span>

|<span data-ttu-id="f8910-131">Egenskap</span><span class="sxs-lookup"><span data-stu-id="f8910-131">Property</span></span> |<span data-ttu-id="f8910-132">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="f8910-132">Description</span></span> |
|---|---|
|<span data-ttu-id="f8910-133">DependsOn</span><span class="sxs-lookup"><span data-stu-id="f8910-133">DependsOn</span></span> |<span data-ttu-id="f8910-134">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS.</span><span class="sxs-lookup"><span data-stu-id="f8910-134">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="f8910-135">Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är syntaxen för att använda den här egenskapen `DependsOn = "[ResourceType]ResourceName"` .</span><span class="sxs-lookup"><span data-stu-id="f8910-135">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="f8910-136">Kontrol</span><span class="sxs-lookup"><span data-stu-id="f8910-136">Ensure</span></span> |<span data-ttu-id="f8910-137">Anger om nyckeln och värdet finns.</span><span class="sxs-lookup"><span data-stu-id="f8910-137">Indicates if the key and value exist.</span></span> <span data-ttu-id="f8910-138">För att se till att de gör det anger du att den här egenskapen är **tillgänglig** .</span><span class="sxs-lookup"><span data-stu-id="f8910-138">To ensure that they do, set this property to **Present** .</span></span> <span data-ttu-id="f8910-139">För att säkerställa att de inte finns, ställer du in egenskapen på **saknas** .</span><span class="sxs-lookup"><span data-stu-id="f8910-139">To ensure that they do not exist, set the property to **Absent** .</span></span> <span data-ttu-id="f8910-140">Standardvärdet finns **.**</span><span class="sxs-lookup"><span data-stu-id="f8910-140">The default value is **Present** .</span></span> |
|<span data-ttu-id="f8910-141">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="f8910-141">PsDscRunAsCredential</span></span> |<span data-ttu-id="f8910-142">Anger autentiseringsuppgifter för att köra hela resursen som.</span><span class="sxs-lookup"><span data-stu-id="f8910-142">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="f8910-143">Den gemensamma egenskapen **PsDscRunAsCredential** har lagts till i WMF 5,0 för att tillåta körning av DSC-resurser i kontexten för andra autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="f8910-143">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="f8910-144">Mer information finns i [använda autentiseringsuppgifter med DSC-resurser](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="f8910-144">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="examples"></a><span data-ttu-id="f8910-145">Exempel</span><span class="sxs-lookup"><span data-stu-id="f8910-145">Examples</span></span>

### <a name="example-1-ensure-specified-value-and-data-under-specified-registry-key"></a><span data-ttu-id="f8910-146">Exempel 1: kontrol lera att det angivna värdet och data under angiven register nyckel</span><span class="sxs-lookup"><span data-stu-id="f8910-146">Example 1: Ensure specified Value and Data under specified registry key</span></span>

<span data-ttu-id="f8910-147">I det här exemplet ser du till att registervärdet "TestValue" under en nyckel med namnet "ExampleKey1" finns i `HKEY\_LOCAL\_MACHINE` Hive och innehåller data "testdata".</span><span class="sxs-lookup"><span data-stu-id="f8910-147">This example ensures that the registry value "TestValue" under a key named "ExampleKey1" is present in the `HKEY\_LOCAL\_MACHINE` hive and has the data "TestData".</span></span>

```powershell
Configuration RegistryTest
{
    Registry RegistryExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Key         = "HKEY_LOCAL_MACHINE\SOFTWARE\ExampleKey1"
        ValueName   = "TestValue"
        ValueData   = "TestData"
    }
}
```

### <a name="example-2-ensure-specified-registry-key-exists"></a><span data-ttu-id="f8910-148">Exempel 2: kontrol lera att den angivna register nyckeln finns</span><span class="sxs-lookup"><span data-stu-id="f8910-148">Example 2: Ensure specified registry key exists</span></span>

<span data-ttu-id="f8910-149">Det här exemplet ser till att en nyckel med namnet "ExampleKey2" finns i den lokala datahive- **\_ \_ datorns** Hive.</span><span class="sxs-lookup"><span data-stu-id="f8910-149">This example ensures that a key named "ExampleKey2" is present in the **HKEY\_LOCAL\_MACHINE** hive.</span></span>

```powershell
Configuration RegistryTest
{
    Registry RegistryExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Key         = "HKEY_LOCAL_MACHINE\SOFTWARE\ExampleKey2"
        ValueName   = ""
    }
}
```

> [!NOTE]
> <span data-ttu-id="f8910-150">Att ändra en register inställning i `HKEY_CURRENT_USER` Hive kräver att konfigurationen körs med användarautentiseringsuppgifter, i stället för som systemet.</span><span class="sxs-lookup"><span data-stu-id="f8910-150">Changing a registry setting in the `HKEY_CURRENT_USER` hive requires that the configuration runs with user credentials, rather than as the system.</span></span> <span data-ttu-id="f8910-151">Du kan använda egenskapen **PsDscRunAsCredential** för att ange användarautentiseringsuppgifter för konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="f8910-151">You can use the **PsDscRunAsCredential** property to specify user credentials for the configuration.</span></span> <span data-ttu-id="f8910-152">Ett exempel finns i [köra DSC med](../../../configurations/runAsUser.md)användarautentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="f8910-152">For an example, see [Running DSC with user credentials](../../../configurations/runAsUser.md).</span></span>
