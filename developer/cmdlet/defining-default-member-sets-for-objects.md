---
title: Definiera standardmedlemmen anger för objekt | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 77f94326-8ffe-4d40-bd2a-b79fb0b4a4e5
caps.latest.revision: 8
ms.openlocfilehash: e8185eb7221a3be0445eddc537dbca89478c74f2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849471"
---
# <a name="defining-default-member-sets-for-objects"></a><span data-ttu-id="41340-102">Definiera standardmedlemsuppsättningar för objekt</span><span class="sxs-lookup"><span data-stu-id="41340-102">Defining Default Member Sets for Objects</span></span>

<span data-ttu-id="41340-103">PSStandardMembers uppsättningen används av Windows PowerShell för att definiera de standard-egenskaperna för ett objekt.</span><span class="sxs-lookup"><span data-stu-id="41340-103">The PSStandardMembers member set is used by Windows PowerShell to define the default property sets for an object.</span></span> <span data-ttu-id="41340-104">Standardegenskapsuppsättningar kan användas av kommandon, till exempel formatering cmdletar för att visa endast de egenskaper som definieras av egenskapsuppsättningen.</span><span class="sxs-lookup"><span data-stu-id="41340-104">The default property sets can be used by commands such as the formatting cmdlets to display only those properties that are defined by the property set.</span></span> <span data-ttu-id="41340-105">De standard-egenskaperna är DefaultDisplayProperty, DefaultDisplayPropertySet och DefaultKeyPropertySet.</span><span class="sxs-lookup"><span data-stu-id="41340-105">The default property sets include DefaultDisplayProperty, DefaultDisplayPropertySet, and DefaultKeyPropertySet.</span></span> <span data-ttu-id="41340-106">Windows PowerShell ignorerar alla andra medlemsuppsättningar och andra egenskapsuppsättningar läggas till i PSStandardMembers medlem.</span><span class="sxs-lookup"><span data-stu-id="41340-106">Windows PowerShell ignores all other member sets and any other property sets added to the PSStandardMembers member set.</span></span>

## <a name="member-set-for-systemdiagnosticsprocess"></a><span data-ttu-id="41340-107">Uppsättningen för System.Diagnostics.Process</span><span class="sxs-lookup"><span data-stu-id="41340-107">Member Set for System.Diagnostics.Process</span></span>

<span data-ttu-id="41340-108">I följande exempel definierar PSStandardMembers uppsättningen egenskapsuppsättningen DefaultDisplayPropertySet för [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objekt.</span><span class="sxs-lookup"><span data-stu-id="41340-108">In the following example, the PSStandardMembers member set defines the DefaultDisplayPropertySet property set for [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objects.</span></span> <span data-ttu-id="41340-109">Den här egenskapen angiven används av den [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="41340-109">This property set is used by the [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span></span>
<span data-ttu-id="41340-110">I följande exempel definierar PSStandardMembers uppsättningen egenskapsuppsättningen DefaultDisplayPropertySet för [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objekt.</span><span class="sxs-lookup"><span data-stu-id="41340-110">In the following example, the PSStandardMembers member set defines the DefaultDisplayPropertySet property set for [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objects.</span></span> <span data-ttu-id="41340-111">Den här egenskapen angiven används av den [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="41340-111">This property set is used by the [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span></span>

```xml
<Type>
  <Name>System.Diagnostics.Process</Name>
  <Members>
    <MemberSet>
     <Name>PSStandardMembers</Name>
     <Members>
       <PropertySet>
         <Name>DefaultDisplayPropertySet</Name>
         <ReferencedProperties>
           <Name>Id</Name>
           <Name>Handles</Name>
           <Name>CPU</Name>
           <Name>Name</Name>
         </ReferencedProperties>
      </PropertySet>
    </Members>
  </MemberSet>
```

<span data-ttu-id="41340-112">Följande utdata visar standardegenskaperna som returneras av den [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="41340-112">The following output shows the default properties returned by the [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span></span> <span data-ttu-id="41340-113">Endast den `Id`, `Handles`, `CPU`, och `Name` egenskaper returneras för varje processobjekt.</span><span class="sxs-lookup"><span data-stu-id="41340-113">Only the `Id`, `Handles`, `CPU`, and `Name` properties are returned for each process object.</span></span>
<span data-ttu-id="41340-114">Följande utdata visar standardegenskaperna som returneras av den [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="41340-114">The following output shows the default properties returned by the [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span></span> <span data-ttu-id="41340-115">Endast den `Id`, `Handles`, `CPU`, och `Name` egenskaper returneras för varje processobjekt.</span><span class="sxs-lookup"><span data-stu-id="41340-115">Only the `Id`, `Handles`, `CPU`, and `Name` properties are returned for each process object.</span></span>

```powershell
Get-Process | format-list
```

```output
Id      : 2036
Handles : 27
CPU     :
Name    : AEADISRV

Id      : 272
Handles : 38
CPU     :
Name    : agrsmsvc
...
```

## <a name="see-also"></a><span data-ttu-id="41340-116">Se även</span><span class="sxs-lookup"><span data-stu-id="41340-116">See Also</span></span>

[<span data-ttu-id="41340-117">Skriva en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="41340-117">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
