---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: DSC-Registerresurser
ms.openlocfilehash: 8d74473d167b70182c3a16c1d39d2a9e797afb1b
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/26/2018
ms.locfileid: "39267729"
---
# <a name="dsc-registry-resource"></a><span data-ttu-id="690b6-103">DSC-Registerresurser</span><span class="sxs-lookup"><span data-stu-id="690b6-103">DSC Registry Resource</span></span>

<span data-ttu-id="690b6-104">_Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0_</span><span class="sxs-lookup"><span data-stu-id="690b6-104">_Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0_</span></span>

<span data-ttu-id="690b6-105">Den **registret** resursen i Windows PowerShell Desired State Configuration (DSC) ger dig möjlighet att hantera registernycklar och värden på målnoden.</span><span class="sxs-lookup"><span data-stu-id="690b6-105">The **Registry** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage registry keys and values on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="690b6-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="690b6-106">Syntax</span></span>

```
Registry [string] #ResourceName
{
    Key = [string]
    ValueName = [string]
    [ Ensure = [string] { Present | Absent }  ]
    [ Force =  [bool]   ]
    [ Hex = [bool] ]
    [ DependsOn = [string[]] ]
    [ ValueData = [string[]] ]
    [ ValueType = [string] { Binary | Dword | ExpandString | MultiString | Qword | String }  ]
}
```

## <a name="properties"></a><span data-ttu-id="690b6-107">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="690b6-107">Properties</span></span>

| <span data-ttu-id="690b6-108">Egenskap</span><span class="sxs-lookup"><span data-stu-id="690b6-108">Property</span></span> | <span data-ttu-id="690b6-109">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="690b6-109">Description</span></span> |
| --- | --- |
| <span data-ttu-id="690b6-110">Tangent</span><span class="sxs-lookup"><span data-stu-id="690b6-110">Key</span></span>| <span data-ttu-id="690b6-111">Anger sökvägen till registernyckeln som du vill se till att ett visst tillstånd.</span><span class="sxs-lookup"><span data-stu-id="690b6-111">Indicates the path of the registry key for which you want to ensure a specific state.</span></span> <span data-ttu-id="690b6-112">Den här sökvägen måste innehålla hive.</span><span class="sxs-lookup"><span data-stu-id="690b6-112">This path must include the hive.</span></span>|
| <span data-ttu-id="690b6-113">Värdenamn</span><span class="sxs-lookup"><span data-stu-id="690b6-113">ValueName</span></span>| <span data-ttu-id="690b6-114">Anger namnet på registervärdet.</span><span class="sxs-lookup"><span data-stu-id="690b6-114">Indicates the name of the registry value.</span></span> <span data-ttu-id="690b6-115">Om du vill lägga till eller ta bort en registernyckel, anger du den här egenskapen som en tom sträng utan att ange ValueType eller ValueData.</span><span class="sxs-lookup"><span data-stu-id="690b6-115">To add or remove a registry key, specify this property as an empty string without specifying ValueType or ValueData.</span></span> <span data-ttu-id="690b6-116">Om du vill ändra eller ta bort en registernyckel standardvärdet, anger du den här egenskapen som en tom sträng när du anger också ValueType eller ValueData.</span><span class="sxs-lookup"><span data-stu-id="690b6-116">To modify or remove the default value of a registry key, specify this property as an empty string while also specifying ValueType or ValueData.</span></span>|
| <span data-ttu-id="690b6-117">Se till att</span><span class="sxs-lookup"><span data-stu-id="690b6-117">Ensure</span></span>| <span data-ttu-id="690b6-118">Anger om nyckeln och värdet finns.</span><span class="sxs-lookup"><span data-stu-id="690b6-118">Indicates if the key and value exist.</span></span> <span data-ttu-id="690b6-119">Säkerställ att de gör det genom att ange egenskapen ”aktuella”.</span><span class="sxs-lookup"><span data-stu-id="690b6-119">To ensure that they do, set this property to "Present".</span></span> <span data-ttu-id="690b6-120">För att säkerställa att de inte finns, ange egenskapen till ””.</span><span class="sxs-lookup"><span data-stu-id="690b6-120">To ensure that they do not exist, set the property to "Absent".</span></span> <span data-ttu-id="690b6-121">Standardvärdet är ”tillgänglig”.</span><span class="sxs-lookup"><span data-stu-id="690b6-121">The default value is "Present".</span></span>|
| <span data-ttu-id="690b6-122">Force</span><span class="sxs-lookup"><span data-stu-id="690b6-122">Force</span></span>| <span data-ttu-id="690b6-123">Om den angivna registernyckeln finns, **kraft** skrivs över med det nya värdet.</span><span class="sxs-lookup"><span data-stu-id="690b6-123">If the specified registry key is present, **Force** overwrites it with the new value.</span></span> <span data-ttu-id="690b6-124">Om du tar bort en registernyckel med undernycklar, det här måste vara **$true**</span><span class="sxs-lookup"><span data-stu-id="690b6-124">If deleting a registry key with subkeys, this needs to be **$true**</span></span> |
| <span data-ttu-id="690b6-125">Hex</span><span class="sxs-lookup"><span data-stu-id="690b6-125">Hex</span></span>| <span data-ttu-id="690b6-126">Anger om data anges i hexadecimalt format.</span><span class="sxs-lookup"><span data-stu-id="690b6-126">Indicates if data will be expressed in hexadecimal format.</span></span> <span data-ttu-id="690b6-127">Om anges visas värdedata DWORD/QWORD i hexadecimalt format.</span><span class="sxs-lookup"><span data-stu-id="690b6-127">If specified, the DWORD/QWORD value data is presented in hexadecimal format.</span></span> <span data-ttu-id="690b6-128">Gäller inte för andra typer.</span><span class="sxs-lookup"><span data-stu-id="690b6-128">Not valid for other types.</span></span> <span data-ttu-id="690b6-129">Standardvärdet är **$false**.</span><span class="sxs-lookup"><span data-stu-id="690b6-129">The default value is **$false**.</span></span>|
| <span data-ttu-id="690b6-130">DependsOn</span><span class="sxs-lookup"><span data-stu-id="690b6-130">DependsOn</span></span>| <span data-ttu-id="690b6-131">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats.</span><span class="sxs-lookup"><span data-stu-id="690b6-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="690b6-132">Till exempel om ID för resurskonfigurationen skriptblock som du vill köra först är **ResourceName** och är av typen **ResourceType**, syntaxen för den här egenskapen är `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="690b6-132">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="690b6-133">ValueData</span><span class="sxs-lookup"><span data-stu-id="690b6-133">ValueData</span></span>| <span data-ttu-id="690b6-134">Data för registervärdet.</span><span class="sxs-lookup"><span data-stu-id="690b6-134">The data for the registry value.</span></span>|
| <span data-ttu-id="690b6-135">Värdetyp</span><span class="sxs-lookup"><span data-stu-id="690b6-135">ValueType</span></span>| <span data-ttu-id="690b6-136">Anger vilken typ av värdet.</span><span class="sxs-lookup"><span data-stu-id="690b6-136">Indicates the type of the value.</span></span> <span data-ttu-id="690b6-137">Typer som stöds är: sträng (REG_SZ), Binary (REG-BINARY), Dword 32-bitars (REG_DWORD), Qword 64-bitars (REG_QWORD), multisträng (REG_MULTI_SZ), utbyggbara sträng (REG_EXPAND_SZ)</span><span class="sxs-lookup"><span data-stu-id="690b6-137">The supported types are: String (REG_SZ), Binary (REG-BINARY), Dword 32-bit (REG_DWORD), Qword 64-bit (REG_QWORD), Multi-string (REG_MULTI_SZ), Expandable string (REG_EXPAND_SZ)</span></span> |

## <a name="example"></a><span data-ttu-id="690b6-138">Exempel</span><span class="sxs-lookup"><span data-stu-id="690b6-138">Example</span></span>

<span data-ttu-id="690b6-139">Det här exemplet ser du till att det finns en nyckel med namnet ”ExampleKey” i den **HKEY\_lokala\_datorn** hive.</span><span class="sxs-lookup"><span data-stu-id="690b6-139">This example ensures that a key named "ExampleKey" is present in the **HKEY\_LOCAL\_MACHINE** hive.</span></span>

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
> <span data-ttu-id="690b6-140">Ändra en registerinställning i den `HKEY\CURRENT\USER` hive kräver att konfigurationen körs med autentiseringsuppgifterna för användaren, i stället för systemet.</span><span class="sxs-lookup"><span data-stu-id="690b6-140">Changing a registry setting in the `HKEY\CURRENT\USER` hive requires that the configuration runs with user credentials, rather than as the system.</span></span> <span data-ttu-id="690b6-141">Du kan använda den **PsDscRunAsCredential** egenskapen att ange autentiseringsuppgifter för konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="690b6-141">You can use the **PsDscRunAsCredential** property to specify user credentials for the configuration.</span></span> <span data-ttu-id="690b6-142">Ett exempel finns i [kör DSC med autentiseringsuppgifterna för användaren](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="690b6-142">For an example, see [Running DSC with user credentials](runAsUser.md).</span></span>