---
ms.date: 09/20/2019
keywords: DSC, PowerShell, konfiguration, installation
title: DSC för Linux nxScript-resurs
ms.openlocfilehash: a7f2114aba47bb581cdd19168e784b79dfc5b6ad
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71941413"
---
# <a name="dsc-for-linux-nxscript-resource"></a><span data-ttu-id="54b5e-103">DSC för Linux nxScript-resurs</span><span class="sxs-lookup"><span data-stu-id="54b5e-103">DSC for Linux nxScript Resource</span></span>

<span data-ttu-id="54b5e-104">**NxScript** -resursen i PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att köra Linux-skript på en Linux-nod.</span><span class="sxs-lookup"><span data-stu-id="54b5e-104">The **nxScript** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to run Linux scripts on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="54b5e-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="54b5e-105">Syntax</span></span>

```Syntax
nxScript <string> #ResourceName
{
    GetScript = <string>
    SetScript = <string>
    TestScript = <string>
    [ User = <string> ]
    [ Group = <string> ]
    [ DependsOn = <string[]> ]
}
```

## <a name="properties"></a><span data-ttu-id="54b5e-106">properties</span><span class="sxs-lookup"><span data-stu-id="54b5e-106">Properties</span></span>

|<span data-ttu-id="54b5e-107">Egenskap</span><span class="sxs-lookup"><span data-stu-id="54b5e-107">Property</span></span> |<span data-ttu-id="54b5e-108">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="54b5e-108">Description</span></span> |
|---|---|
|<span data-ttu-id="54b5e-109">GetScript</span><span class="sxs-lookup"><span data-stu-id="54b5e-109">GetScript</span></span> |<span data-ttu-id="54b5e-110">Innehåller ett skript för att returnera datorns aktuella status.</span><span class="sxs-lookup"><span data-stu-id="54b5e-110">Provides a script to return current status of the machine.</span></span> <span data-ttu-id="54b5e-111">Det här skriptet körs när du anropar [GetDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) -skriptet.</span><span class="sxs-lookup"><span data-stu-id="54b5e-111">This script runs when you invoke the [GetDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) script.</span></span> <span data-ttu-id="54b5e-112">Skriptet måste börja med en Shebang, till exempel `#!/bin/bash`.</span><span class="sxs-lookup"><span data-stu-id="54b5e-112">The script must begin with a shebang, such as `#!/bin/bash`.</span></span> |
|<span data-ttu-id="54b5e-113">SetScript</span><span class="sxs-lookup"><span data-stu-id="54b5e-113">SetScript</span></span> |<span data-ttu-id="54b5e-114">Innehåller ett skript som placerar datorn i korrekt tillstånd.</span><span class="sxs-lookup"><span data-stu-id="54b5e-114">Provides a script that puts the machine in the correct state.</span></span> <span data-ttu-id="54b5e-115">När du anropar [StartDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) -skriptet körs **TestScript** först.</span><span class="sxs-lookup"><span data-stu-id="54b5e-115">When you invoke the [StartDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) script, the **TestScript** runs first.</span></span> <span data-ttu-id="54b5e-116">Om **TestScript** -blocket returnerar en annan slutkod än 0, kommer **SetScript** -blocket att köras.</span><span class="sxs-lookup"><span data-stu-id="54b5e-116">If the **TestScript** block returns an exit code other than 0, the **SetScript** block will run.</span></span> <span data-ttu-id="54b5e-117">Om **TestScript** returnerar slut koden 0 så körs inte **SetScript** .</span><span class="sxs-lookup"><span data-stu-id="54b5e-117">If the **TestScript** returns an exit code of 0, the **SetScript** will not run.</span></span> <span data-ttu-id="54b5e-118">Skriptet måste börja med en Shebang, till exempel `#!/bin/bash`.</span><span class="sxs-lookup"><span data-stu-id="54b5e-118">The script must begin with a shebang, such as `#!/bin/bash`.</span></span> |
|<span data-ttu-id="54b5e-119">TestScript</span><span class="sxs-lookup"><span data-stu-id="54b5e-119">TestScript</span></span> |<span data-ttu-id="54b5e-120">Innehåller ett skript som utvärderar om noden för närvarande är i rätt tillstånd.</span><span class="sxs-lookup"><span data-stu-id="54b5e-120">Provides a script that evaluates whether the node is currently in the correct state.</span></span> <span data-ttu-id="54b5e-121">När du anropar [StartDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) -skriptet körs det här skriptet.</span><span class="sxs-lookup"><span data-stu-id="54b5e-121">When you invoke the [StartDscConfiguration.py](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) script, this script runs.</span></span> <span data-ttu-id="54b5e-122">Om den returnerar en annan slutkod än 0, kommer **SetScript** att köras.</span><span class="sxs-lookup"><span data-stu-id="54b5e-122">If it returns an exit code other than 0, the **SetScript** will run.</span></span> <span data-ttu-id="54b5e-123">Om den returnerar slut koden 0 körs inte **SetScript** .</span><span class="sxs-lookup"><span data-stu-id="54b5e-123">If it returns an exit code of 0, the **SetScript** will not run.</span></span> <span data-ttu-id="54b5e-124">**TestScript** körs också när du anropar [TestDscConfiguration](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) -skriptet.</span><span class="sxs-lookup"><span data-stu-id="54b5e-124">The **TestScript** also runs when you invoke the [TestDscConfiguration](https://github.com/Microsoft/PowerShell-DSC-for-Linux#performing-dsc-operations-from-the-linux-computer) script.</span></span> <span data-ttu-id="54b5e-125">I det här fallet kommer dock **SetScript** inte att köras, oavsett vilken slutkod som returneras från **TestScript**.</span><span class="sxs-lookup"><span data-stu-id="54b5e-125">However, in this case, the **SetScript** will not run, no matter what exit code is returned from the **TestScript**.</span></span> <span data-ttu-id="54b5e-126">**TestScript** måste innehålla innehåll och måste returnera avslutnings koden 0 om den faktiska konfigurationen matchar den aktuella önskade tillstånds konfigurationen och en annan slutkod än 0 om den inte matchar.</span><span class="sxs-lookup"><span data-stu-id="54b5e-126">The **TestScript** must contain content and must return an exit code of 0 if the actual configuration matches the current desired state configuration, and an exit code other than 0 if it does not match.</span></span> <span data-ttu-id="54b5e-127">Den aktuella önskade tillstånds konfigurationen är den sista konfigurationen som används på den nod som använder DSC.</span><span class="sxs-lookup"><span data-stu-id="54b5e-127">The current desired state configuration is the last configuration enacted on the node that is using DSC.</span></span> <span data-ttu-id="54b5e-128">Skriptet måste börja med en Shebang, till exempel `#!/bin/bash`.</span><span class="sxs-lookup"><span data-stu-id="54b5e-128">The script must begin with a shebang, such as `#!/bin/bash`.</span></span> |
|<span data-ttu-id="54b5e-129">Användare</span><span class="sxs-lookup"><span data-stu-id="54b5e-129">User</span></span> |<span data-ttu-id="54b5e-130">Användaren att köra skriptet som.</span><span class="sxs-lookup"><span data-stu-id="54b5e-130">The user to run the script as.</span></span> |
|<span data-ttu-id="54b5e-131">Grupp</span><span class="sxs-lookup"><span data-stu-id="54b5e-131">Group</span></span> |<span data-ttu-id="54b5e-132">Gruppen att köra skriptet som.</span><span class="sxs-lookup"><span data-stu-id="54b5e-132">The group to run the script as.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="54b5e-133">Gemensamma egenskaper</span><span class="sxs-lookup"><span data-stu-id="54b5e-133">Common properties</span></span>

|<span data-ttu-id="54b5e-134">Egenskap</span><span class="sxs-lookup"><span data-stu-id="54b5e-134">Property</span></span> |<span data-ttu-id="54b5e-135">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="54b5e-135">Description</span></span> |
|---|---|
|<span data-ttu-id="54b5e-136">DependsOn</span><span class="sxs-lookup"><span data-stu-id="54b5e-136">DependsOn</span></span> |<span data-ttu-id="54b5e-137">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS.</span><span class="sxs-lookup"><span data-stu-id="54b5e-137">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="54b5e-138">Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är `DependsOn = "[ResourceType]ResourceName"`syntaxen för att använda den här egenskapen.</span><span class="sxs-lookup"><span data-stu-id="54b5e-138">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |

## <a name="example"></a><span data-ttu-id="54b5e-139">Exempel</span><span class="sxs-lookup"><span data-stu-id="54b5e-139">Example</span></span>

<span data-ttu-id="54b5e-140">I följande exempel demonstreras användningen av **nxScript** -resursen för att utföra ytterligare konfigurations hantering.</span><span class="sxs-lookup"><span data-stu-id="54b5e-140">The following example demonstrates the use of the **nxScript** resource to perform additional configuration management.</span></span>

```powershell
Import-DSCResource -Module nx

Node $node
{
    nxScript KeepDirEmpty {

    GetScript = @"
#!/bin/bash
ls /tmp/mydir/ | wc -l
"@

    SetScript = @"
#!/bin/bash
rm -rf /tmp/mydir/*
"@

    TestScript = @'
#!/bin/bash
filecount=`ls /tmp/mydir | wc -l`
if [ $filecount -gt 0 ]
then
    exit 1
else
    exit 0
fi
'@
    }
}
```
