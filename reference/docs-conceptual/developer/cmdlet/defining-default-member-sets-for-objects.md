---
title: Definiera standard medlems uppsättningar för objekt | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 77f94326-8ffe-4d40-bd2a-b79fb0b4a4e5
caps.latest.revision: 8
ms.openlocfilehash: 2d634e7638ec0e0117d65ca0b2d08e68f0068a03
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359383"
---
# <a name="defining-default-member-sets-for-objects"></a><span data-ttu-id="1c32f-102">Definiera standardmedlemsuppsättningar för objekt</span><span class="sxs-lookup"><span data-stu-id="1c32f-102">Defining Default Member Sets for Objects</span></span>

<span data-ttu-id="1c32f-103">PSStandardMembers-medlems uppsättningen används av Windows PowerShell för att definiera standard egenskaps uppsättningar för ett objekt.</span><span class="sxs-lookup"><span data-stu-id="1c32f-103">The PSStandardMembers member set is used by Windows PowerShell to define the default property sets for an object.</span></span> <span data-ttu-id="1c32f-104">Standard egenskaps uppsättningarna kan användas av kommandon som till exempel-cmdletar för att visa endast de egenskaper som definieras av egenskaps uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="1c32f-104">The default property sets can be used by commands such as the formatting cmdlets to display only those properties that are defined by the property set.</span></span> <span data-ttu-id="1c32f-105">Standard egenskaps uppsättningarna är DefaultDisplayProperty, DefaultDisplayPropertySet och DefaultKeyPropertySet.</span><span class="sxs-lookup"><span data-stu-id="1c32f-105">The default property sets include DefaultDisplayProperty, DefaultDisplayPropertySet, and DefaultKeyPropertySet.</span></span> <span data-ttu-id="1c32f-106">Windows PowerShell ignorerar alla andra medlems uppsättningar och andra egenskaps uppsättningar som läggs till i PSStandardMembers-medlems uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="1c32f-106">Windows PowerShell ignores all other member sets and any other property sets added to the PSStandardMembers member set.</span></span>

## <a name="member-set-for-systemdiagnosticsprocess"></a><span data-ttu-id="1c32f-107">Medlems uppsättning för system. Diagnostics. process</span><span class="sxs-lookup"><span data-stu-id="1c32f-107">Member Set for System.Diagnostics.Process</span></span>

<span data-ttu-id="1c32f-108">I följande exempel definierar PSStandardMembers-medlems uppsättningen DefaultDisplayPropertySet-egenskapen som har angetts för [system. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) -objekt.</span><span class="sxs-lookup"><span data-stu-id="1c32f-108">In the following example, the PSStandardMembers member set defines the DefaultDisplayPropertySet property set for [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objects.</span></span> <span data-ttu-id="1c32f-109">Den här egenskaps uppsättningen används av cmdleten [format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) .</span><span class="sxs-lookup"><span data-stu-id="1c32f-109">This property set is used by the [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span></span>

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

<span data-ttu-id="1c32f-110">Följande utdata visar standard egenskaperna som returneras av cmdleten [format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) .</span><span class="sxs-lookup"><span data-stu-id="1c32f-110">The following output shows the default properties returned by the [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span></span> <span data-ttu-id="1c32f-111">Endast egenskaperna `Id`, `Handles`, `CPU` och `Name` returneras för varje process objekt.</span><span class="sxs-lookup"><span data-stu-id="1c32f-111">Only the `Id`, `Handles`, `CPU`, and `Name` properties are returned for each process object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="1c32f-112">Se även</span><span class="sxs-lookup"><span data-stu-id="1c32f-112">See Also</span></span>

[<span data-ttu-id="1c32f-113">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="1c32f-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
