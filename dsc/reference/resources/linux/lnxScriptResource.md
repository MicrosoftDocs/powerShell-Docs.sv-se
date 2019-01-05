---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: DSC för Linux nxScript resurs
ms.openlocfilehash: 339968512ab1c16c4c3785a3a19b00c3fbbf9ea1
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048657"
---
# <a name="dsc-for-linux-nxscript-resource"></a><span data-ttu-id="66fd9-103">DSC för Linux nxScript resurs</span><span class="sxs-lookup"><span data-stu-id="66fd9-103">DSC for Linux nxScript Resource</span></span>

<span data-ttu-id="66fd9-104">Den **nxScript** resurs i PowerShell Desired State Configuration (DSC) är en mekanism för att köra Linux-skript på en Linux-nod.</span><span class="sxs-lookup"><span data-stu-id="66fd9-104">The **nxScript** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to run Linux scripts on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="66fd9-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="66fd9-105">Syntax</span></span>

```
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

## <a name="properties"></a><span data-ttu-id="66fd9-106">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="66fd9-106">Properties</span></span>

|  <span data-ttu-id="66fd9-107">Egenskap</span><span class="sxs-lookup"><span data-stu-id="66fd9-107">Property</span></span> |  <span data-ttu-id="66fd9-108">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="66fd9-108">Description</span></span> |
|---|---|
| <span data-ttu-id="66fd9-109">GetScript</span><span class="sxs-lookup"><span data-stu-id="66fd9-109">GetScript</span></span>| <span data-ttu-id="66fd9-110">Innehåller ett skript som körs när du anropar den [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="66fd9-110">Provides a script that runs when you invoke the [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521625.aspx) cmdlet.</span></span> <span data-ttu-id="66fd9-111">Skriptet måste börja med en shebang, till exempel #! / bin/bash.</span><span class="sxs-lookup"><span data-stu-id="66fd9-111">The script must begin with a shebang, such as #!/bin/bash.</span></span>|
| <span data-ttu-id="66fd9-112">SetScript</span><span class="sxs-lookup"><span data-stu-id="66fd9-112">SetScript</span></span>| <span data-ttu-id="66fd9-113">Innehåller ett skript.</span><span class="sxs-lookup"><span data-stu-id="66fd9-113">Provides a script.</span></span> <span data-ttu-id="66fd9-114">När du anropar den [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet, den **TestScript** körs första.</span><span class="sxs-lookup"><span data-stu-id="66fd9-114">When you invoke the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet, the **TestScript** runs first.</span></span> <span data-ttu-id="66fd9-115">Om den **TestScript** block returnerar slutkoden än 0, den **SetScript** blocket körs.</span><span class="sxs-lookup"><span data-stu-id="66fd9-115">If the **TestScript** block returns an exit code other than 0, the **SetScript** block will run.</span></span> <span data-ttu-id="66fd9-116">Om den **TestScript** returnerar slutkoden 0, den **SetScript** körs inte.</span><span class="sxs-lookup"><span data-stu-id="66fd9-116">If the **TestScript** returns an exit code of 0, the **SetScript** will not run.</span></span> <span data-ttu-id="66fd9-117">Skriptet måste börja med en shebang som `#!/bin/bash`.</span><span class="sxs-lookup"><span data-stu-id="66fd9-117">The script must begin with a shebang, such as `#!/bin/bash`.</span></span>|
| <span data-ttu-id="66fd9-118">TestScript</span><span class="sxs-lookup"><span data-stu-id="66fd9-118">TestScript</span></span>| <span data-ttu-id="66fd9-119">Innehåller ett skript.</span><span class="sxs-lookup"><span data-stu-id="66fd9-119">Provides a script.</span></span> <span data-ttu-id="66fd9-120">När du anropar den [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet, det här skriptet körs.</span><span class="sxs-lookup"><span data-stu-id="66fd9-120">When you invoke the [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx) cmdlet, this script runs.</span></span> <span data-ttu-id="66fd9-121">Om den returnerar en slutkod än 0, körs SetScript.</span><span class="sxs-lookup"><span data-stu-id="66fd9-121">If it returns an exit code other than 0, the SetScript will run.</span></span> <span data-ttu-id="66fd9-122">Om den returnerar slutkoden 0, den **SetScript** körs inte.</span><span class="sxs-lookup"><span data-stu-id="66fd9-122">If it returns an exit code of 0, the **SetScript** will not run.</span></span> <span data-ttu-id="66fd9-123">Den **TestScript** körs även när du anropar den [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="66fd9-123">The **TestScript** also runs when you invoke the [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx) cmdlet.</span></span> <span data-ttu-id="66fd9-124">Men i det här fallet den **SetScript** inte körs, oavsett vilka avslutskoden returneras från den **TestScript**.</span><span class="sxs-lookup"><span data-stu-id="66fd9-124">However, in this case, the **SetScript** will not run, no matter what exit code is returned from the **TestScript**.</span></span> <span data-ttu-id="66fd9-125">Den **TestScript** måste returnera slutkoden 0 om den faktiska konfigurationen matchar aktuella önskad tillståndskonfiguration, och en avsluta code än 0 om det inte matchar.</span><span class="sxs-lookup"><span data-stu-id="66fd9-125">The **TestScript** must return an exit code of 0 if the actual configuration matches the current desired state configuration, and an exit code other than 0 if it does not match.</span></span> <span data-ttu-id="66fd9-126">(Den aktuella konfigurationen av önskat tillstånd är den senaste konfigurationen trätt i kraft på den nod som använder DSC).</span><span class="sxs-lookup"><span data-stu-id="66fd9-126">(The current desired state configuration is the last configuration enacted on the node that is using DSC).</span></span> <span data-ttu-id="66fd9-127">Skriptet måste börja med en shebang, till exempel 1#!/bin/bash.1</span><span class="sxs-lookup"><span data-stu-id="66fd9-127">The script must begin with a shebang, such as 1#!/bin/bash.1</span></span>|
| <span data-ttu-id="66fd9-128">Användare</span><span class="sxs-lookup"><span data-stu-id="66fd9-128">User</span></span>| <span data-ttu-id="66fd9-129">Användaren att köra skriptet som.</span><span class="sxs-lookup"><span data-stu-id="66fd9-129">The user to run the script as.</span></span>|
| <span data-ttu-id="66fd9-130">Grupp</span><span class="sxs-lookup"><span data-stu-id="66fd9-130">Group</span></span>| <span data-ttu-id="66fd9-131">Gruppen att köra skriptet som.</span><span class="sxs-lookup"><span data-stu-id="66fd9-131">The group to run the script as.</span></span>|
| <span data-ttu-id="66fd9-132">DependsOn</span><span class="sxs-lookup"><span data-stu-id="66fd9-132">DependsOn</span></span> | <span data-ttu-id="66fd9-133">Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats.</span><span class="sxs-lookup"><span data-stu-id="66fd9-133">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="66fd9-134">Till exempel om den **ID** för resursen configuration-skriptblock som du vill köra först är **ResourceName** och är av typen **ResourceType**, syntaxen för detta Egenskapen är `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="66fd9-134">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="66fd9-135">Exempel</span><span class="sxs-lookup"><span data-stu-id="66fd9-135">Example</span></span>

<span data-ttu-id="66fd9-136">I följande exempel visar hur du använder den **nxScript** resurs att genomföra ytterligare konfiguration.</span><span class="sxs-lookup"><span data-stu-id="66fd9-136">The following example demonstrates the use of the **nxScript** resource to perform additional configuration management.</span></span>

```
Import-DSCResource -Module nx

Node $node {
nxScript KeepDirEmpty{

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