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
ms.openlocfilehash: 2d634e7638ec0e0117d65ca0b2d08e68f0068a03
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068257"
---
# <a name="defining-default-member-sets-for-objects"></a><span data-ttu-id="d6386-102">Definiera standardmedlemsuppsättningar för objekt</span><span class="sxs-lookup"><span data-stu-id="d6386-102">Defining Default Member Sets for Objects</span></span>

<span data-ttu-id="d6386-103">PSStandardMembers uppsättningen används av Windows PowerShell för att definiera de standard-egenskaperna för ett objekt.</span><span class="sxs-lookup"><span data-stu-id="d6386-103">The PSStandardMembers member set is used by Windows PowerShell to define the default property sets for an object.</span></span> <span data-ttu-id="d6386-104">Standardegenskapsuppsättningar kan användas av kommandon, till exempel formatering cmdletar för att visa endast de egenskaper som definieras av egenskapsuppsättningen.</span><span class="sxs-lookup"><span data-stu-id="d6386-104">The default property sets can be used by commands such as the formatting cmdlets to display only those properties that are defined by the property set.</span></span> <span data-ttu-id="d6386-105">De standard-egenskaperna är DefaultDisplayProperty, DefaultDisplayPropertySet och DefaultKeyPropertySet.</span><span class="sxs-lookup"><span data-stu-id="d6386-105">The default property sets include DefaultDisplayProperty, DefaultDisplayPropertySet, and DefaultKeyPropertySet.</span></span> <span data-ttu-id="d6386-106">Windows PowerShell ignorerar alla andra medlemsuppsättningar och andra egenskapsuppsättningar läggas till i PSStandardMembers medlem.</span><span class="sxs-lookup"><span data-stu-id="d6386-106">Windows PowerShell ignores all other member sets and any other property sets added to the PSStandardMembers member set.</span></span>

## <a name="member-set-for-systemdiagnosticsprocess"></a><span data-ttu-id="d6386-107">Uppsättningen för System.Diagnostics.Process</span><span class="sxs-lookup"><span data-stu-id="d6386-107">Member Set for System.Diagnostics.Process</span></span>

<span data-ttu-id="d6386-108">I följande exempel definierar PSStandardMembers uppsättningen egenskapsuppsättningen DefaultDisplayPropertySet för [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objekt.</span><span class="sxs-lookup"><span data-stu-id="d6386-108">In the following example, the PSStandardMembers member set defines the DefaultDisplayPropertySet property set for [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objects.</span></span> <span data-ttu-id="d6386-109">Den här egenskapen angiven används av den [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d6386-109">This property set is used by the [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span></span>

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

<span data-ttu-id="d6386-110">Följande utdata visar standardegenskaperna som returneras av den [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d6386-110">The following output shows the default properties returned by the [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span></span> <span data-ttu-id="d6386-111">Endast den `Id`, `Handles`, `CPU`, och `Name` egenskaper returneras för varje processobjekt.</span><span class="sxs-lookup"><span data-stu-id="d6386-111">Only the `Id`, `Handles`, `CPU`, and `Name` properties are returned for each process object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d6386-112">Se även</span><span class="sxs-lookup"><span data-stu-id="d6386-112">See Also</span></span>

[<span data-ttu-id="d6386-113">Skriva en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="d6386-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
