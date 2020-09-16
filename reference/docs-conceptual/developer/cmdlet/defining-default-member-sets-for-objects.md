---
title: Definiera standard medlems uppsättningar för objekt | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 80e1f54890d3aac1702414699ead16fcf38271e1
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774634"
---
# <a name="defining-default-member-sets-for-objects"></a><span data-ttu-id="4e6a5-102">Definiera standardmedlemsuppsättningar för objekt</span><span class="sxs-lookup"><span data-stu-id="4e6a5-102">Defining Default Member Sets for Objects</span></span>

<span data-ttu-id="4e6a5-103">PSStandardMembers-medlems uppsättningen används av Windows PowerShell för att definiera standard egenskaps uppsättningar för ett objekt.</span><span class="sxs-lookup"><span data-stu-id="4e6a5-103">The PSStandardMembers member set is used by Windows PowerShell to define the default property sets for an object.</span></span> <span data-ttu-id="4e6a5-104">Standard egenskaps uppsättningarna kan användas av kommandon som till exempel-cmdletar för att visa endast de egenskaper som definieras av egenskaps uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="4e6a5-104">The default property sets can be used by commands such as the formatting cmdlets to display only those properties that are defined by the property set.</span></span> <span data-ttu-id="4e6a5-105">Standard egenskaps uppsättningarna är DefaultDisplayProperty, DefaultDisplayPropertySet och DefaultKeyPropertySet.</span><span class="sxs-lookup"><span data-stu-id="4e6a5-105">The default property sets include DefaultDisplayProperty, DefaultDisplayPropertySet, and DefaultKeyPropertySet.</span></span> <span data-ttu-id="4e6a5-106">Windows PowerShell ignorerar alla andra medlems uppsättningar och andra egenskaps uppsättningar som läggs till i PSStandardMembers-medlems uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="4e6a5-106">Windows PowerShell ignores all other member sets and any other property sets added to the PSStandardMembers member set.</span></span>

## <a name="member-set-for-systemdiagnosticsprocess"></a><span data-ttu-id="4e6a5-107">Medlems uppsättning för system. Diagnostics. process</span><span class="sxs-lookup"><span data-stu-id="4e6a5-107">Member Set for System.Diagnostics.Process</span></span>

<span data-ttu-id="4e6a5-108">I följande exempel definierar PSStandardMembers-medlems uppsättningen DefaultDisplayPropertySet-egenskapen som har angetts för [system. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) -objekt.</span><span class="sxs-lookup"><span data-stu-id="4e6a5-108">In the following example, the PSStandardMembers member set defines the DefaultDisplayPropertySet property set for [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objects.</span></span> <span data-ttu-id="4e6a5-109">Den här egenskaps uppsättningen används av cmdleten [format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) .</span><span class="sxs-lookup"><span data-stu-id="4e6a5-109">This property set is used by the [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span></span>

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

<span data-ttu-id="4e6a5-110">Följande utdata visar standard egenskaperna som returneras av cmdleten [format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) .</span><span class="sxs-lookup"><span data-stu-id="4e6a5-110">The following output shows the default properties returned by the [Format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) cmdlet.</span></span> <span data-ttu-id="4e6a5-111">Endast `Id` egenskaperna, `Handles` , `CPU` och `Name` returneras för varje process objekt.</span><span class="sxs-lookup"><span data-stu-id="4e6a5-111">Only the `Id`, `Handles`, `CPU`, and `Name` properties are returned for each process object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="4e6a5-112">Se även</span><span class="sxs-lookup"><span data-stu-id="4e6a5-112">See Also</span></span>

[<span data-ttu-id="4e6a5-113">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="4e6a5-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
