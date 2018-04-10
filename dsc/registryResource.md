---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: Resurs för DSC-registret
ms.openlocfilehash: fcd24b1dd729dbb0abd697a4a628dce01fdd5422
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-registry-resource"></a><span data-ttu-id="4da5a-103">Resurs för DSC-registret</span><span class="sxs-lookup"><span data-stu-id="4da5a-103">DSC Registry Resource</span></span>

> <span data-ttu-id="4da5a-104">Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="4da5a-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="4da5a-105">Den **registret** resurs i Windows PowerShell önskad tillstånd Configuration (DSC) tillhandahåller en mekanism för att hantera registernycklar och värden på målnoden.</span><span class="sxs-lookup"><span data-stu-id="4da5a-105">The **Registry** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage registry keys and values on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="4da5a-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="4da5a-106">Syntax</span></span>

```
Registry [string] #ResourceName
{
    Key = [string]
    ValueName = [string]
    [ Ensure = [string] { Enable | Disable }  ]
    [ Force =  [bool]   ]
    [ Hex = [bool] ]
    [ DependsOn = [string[]] ]
    [ ValueData = [string[]] ]
    [ ValueType = [string] { Binary | Dword | ExpandString | MultiString | Qword | String }  ]
}
```

## <a name="properties"></a><span data-ttu-id="4da5a-107">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="4da5a-107">Properties</span></span>
|  <span data-ttu-id="4da5a-108">Egenskap</span><span class="sxs-lookup"><span data-stu-id="4da5a-108">Property</span></span>  |  <span data-ttu-id="4da5a-109">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="4da5a-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="4da5a-110">Tangent</span><span class="sxs-lookup"><span data-stu-id="4da5a-110">Key</span></span>| <span data-ttu-id="4da5a-111">Anger sökvägen till registernyckeln som du vill se till att ett visst tillstånd.</span><span class="sxs-lookup"><span data-stu-id="4da5a-111">Indicates the path of the registry key for which you want to ensure a specific state.</span></span> <span data-ttu-id="4da5a-112">Den här sökvägen måste innehålla strukturen.</span><span class="sxs-lookup"><span data-stu-id="4da5a-112">This path must include the hive.</span></span>|
| <span data-ttu-id="4da5a-113">Värdenamn</span><span class="sxs-lookup"><span data-stu-id="4da5a-113">ValueName</span></span>| <span data-ttu-id="4da5a-114">Anger namnet på registervärdet.</span><span class="sxs-lookup"><span data-stu-id="4da5a-114">Indicates the name of the registry value.</span></span> <span data-ttu-id="4da5a-115">Ange den här egenskapen om du vill lägga till eller ta bort en registernyckel, en tom sträng utan att ange ValueType eller ValueData.</span><span class="sxs-lookup"><span data-stu-id="4da5a-115">To add or remove a registry key, specify this property as an empty string without specifying ValueType or ValueData.</span></span> <span data-ttu-id="4da5a-116">Om du vill ändra eller ta bort en registernyckel standardvärdet, anger du den här egenskapen som en tom sträng när du anger också ValueType eller ValueData.</span><span class="sxs-lookup"><span data-stu-id="4da5a-116">To modify or remove the default value of a registry key, specify this property as an empty string while also specifying ValueType or ValueData.</span></span>|
| <span data-ttu-id="4da5a-117">Se till att</span><span class="sxs-lookup"><span data-stu-id="4da5a-117">Ensure</span></span>| <span data-ttu-id="4da5a-118">Anger om nyckel och värde finns.</span><span class="sxs-lookup"><span data-stu-id="4da5a-118">Indicates if the key and value exist.</span></span> <span data-ttu-id="4da5a-119">Ange egenskapen ”aktuella” för att säkerställa att de gör.</span><span class="sxs-lookup"><span data-stu-id="4da5a-119">To ensure that they do, set this property to "Present".</span></span> <span data-ttu-id="4da5a-120">Ange egenskapen till ”saknas” för att säkerställa att de inte finns.</span><span class="sxs-lookup"><span data-stu-id="4da5a-120">To ensure that they do not exist, set the property to "Absent".</span></span> <span data-ttu-id="4da5a-121">Standardvärdet är ”saknas”.</span><span class="sxs-lookup"><span data-stu-id="4da5a-121">The default value is "Present".</span></span>|
| <span data-ttu-id="4da5a-122">Force</span><span class="sxs-lookup"><span data-stu-id="4da5a-122">Force</span></span>| <span data-ttu-id="4da5a-123">Om den angivna registernyckeln finns, __kraft__ skriver över den med det nya värdet.</span><span class="sxs-lookup"><span data-stu-id="4da5a-123">If the specified registry key is present, __Force__ overwrites it with the new value.</span></span> <span data-ttu-id="4da5a-124">Om du tar bort en registernyckel med undernycklar, det måste vara __$true__</span><span class="sxs-lookup"><span data-stu-id="4da5a-124">If deleting a registry key with subkeys, this needs to be __$true__</span></span>|
| <span data-ttu-id="4da5a-125">Hex</span><span class="sxs-lookup"><span data-stu-id="4da5a-125">Hex</span></span>| <span data-ttu-id="4da5a-126">Anger om data ska anges i hexadecimalt format.</span><span class="sxs-lookup"><span data-stu-id="4da5a-126">Indicates if data will be expressed in hexadecimal format.</span></span> <span data-ttu-id="4da5a-127">Om anges visas värdedata DWORD/QWORD i hexadecimalt format.</span><span class="sxs-lookup"><span data-stu-id="4da5a-127">If specified, the DWORD/QWORD value data is presented in hexadecimal format.</span></span> <span data-ttu-id="4da5a-128">Gäller inte för andra typer.</span><span class="sxs-lookup"><span data-stu-id="4da5a-128">Not valid for other types.</span></span> <span data-ttu-id="4da5a-129">Standardvärdet är __$false__.</span><span class="sxs-lookup"><span data-stu-id="4da5a-129">The default value is __$false__.</span></span>|
| <span data-ttu-id="4da5a-130">dependsOn</span><span class="sxs-lookup"><span data-stu-id="4da5a-130">DependsOn</span></span>| <span data-ttu-id="4da5a-131">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats.</span><span class="sxs-lookup"><span data-stu-id="4da5a-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="4da5a-132">Om ID för resurskonfigurationen skriptblock som du vill köra först är exempelvis __ResourceName__ och dess typ är __ResourceType__, syntaxen för den här egenskapen är `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="4da5a-132">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="4da5a-133">ValueData</span><span class="sxs-lookup"><span data-stu-id="4da5a-133">ValueData</span></span>| <span data-ttu-id="4da5a-134">Data för registervärdet.</span><span class="sxs-lookup"><span data-stu-id="4da5a-134">The data for the registry value.</span></span>|
| <span data-ttu-id="4da5a-135">Värdetyp</span><span class="sxs-lookup"><span data-stu-id="4da5a-135">ValueType</span></span>| <span data-ttu-id="4da5a-136">Anger vilken typ av värdet.</span><span class="sxs-lookup"><span data-stu-id="4da5a-136">Indicates the type of the value.</span></span> <span data-ttu-id="4da5a-137">Typerna som stöds är:</span><span class="sxs-lookup"><span data-stu-id="4da5a-137">The supported types are:</span></span>
<ul><li><span data-ttu-id="4da5a-138">String (REG_SZ)</span><span class="sxs-lookup"><span data-stu-id="4da5a-138">String (REG_SZ)</span></span></li>


<li><span data-ttu-id="4da5a-139">Binary (REG-BINARY)</span><span class="sxs-lookup"><span data-stu-id="4da5a-139">Binary (REG-BINARY)</span></span></li>


<li><span data-ttu-id="4da5a-140">DWORD 32-bitars (REG_DWORD)</span><span class="sxs-lookup"><span data-stu-id="4da5a-140">Dword 32-bit (REG_DWORD)</span></span></li>


<li><span data-ttu-id="4da5a-141">Qword 64-bitars (REG_QWORD)</span><span class="sxs-lookup"><span data-stu-id="4da5a-141">Qword 64-bit (REG_QWORD)</span></span></li>


<li><span data-ttu-id="4da5a-142">Multi-string (REG_MULTI_SZ)</span><span class="sxs-lookup"><span data-stu-id="4da5a-142">Multi-string (REG_MULTI_SZ)</span></span></li>


<li><span data-ttu-id="4da5a-143">Utbyggbara sträng (REG_EXPAND_SZ)</span><span class="sxs-lookup"><span data-stu-id="4da5a-143">Expandable string (REG_EXPAND_SZ)</span></span></li></ul>

## <a name="example"></a><span data-ttu-id="4da5a-144">Exempel</span><span class="sxs-lookup"><span data-stu-id="4da5a-144">Example</span></span>
<span data-ttu-id="4da5a-145">Det här exemplet ser till att det finns en nyckel med namnet ”ExampleKey” i den **HKEY\_lokala\_datorn** hive.</span><span class="sxs-lookup"><span data-stu-id="4da5a-145">This example ensures that a key named "ExampleKey" is present in the **HKEY\_LOCAL\_MACHINE** hive.</span></span>
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

><span data-ttu-id="4da5a-146">**Obs:** ändra en registerinställning i den **HKEY\_aktuella\_användaren** hive kräver att konfigurationen körs med autentiseringsuppgifterna för användaren i stället för som system.</span><span class="sxs-lookup"><span data-stu-id="4da5a-146">**Note:** Changing a registry setting in the **HKEY\_CURRENT\_USER** hive requires that the configuration runs with user credentials, rather than as the system.</span></span>
><span data-ttu-id="4da5a-147">Du kan använda den **PsDscRunAsCredential** att ange autentiseringsuppgifter för konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="4da5a-147">You can use the **PsDscRunAsCredential** property to specify user credentials for the configuration.</span></span> <span data-ttu-id="4da5a-148">Ett exempel finns [kör DSC med autentiseringsuppgifterna för användaren](runAsUser.md)</span><span class="sxs-lookup"><span data-stu-id="4da5a-148">For an example, see [Running DSC with user credentials](runAsUser.md)</span></span>