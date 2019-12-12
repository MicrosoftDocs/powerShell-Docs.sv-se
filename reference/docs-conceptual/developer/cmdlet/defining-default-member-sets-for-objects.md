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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359383"
---
# <a name="defining-default-member-sets-for-objects"></a>Definiera standardmedlemsuppsättningar för objekt

PSStandardMembers-medlems uppsättningen används av Windows PowerShell för att definiera standard egenskaps uppsättningar för ett objekt. Standard egenskaps uppsättningarna kan användas av kommandon som till exempel-cmdletar för att visa endast de egenskaper som definieras av egenskaps uppsättningen. Standard egenskaps uppsättningarna är DefaultDisplayProperty, DefaultDisplayPropertySet och DefaultKeyPropertySet. Windows PowerShell ignorerar alla andra medlems uppsättningar och andra egenskaps uppsättningar som läggs till i PSStandardMembers-medlems uppsättningen.

## <a name="member-set-for-systemdiagnosticsprocess"></a>Medlems uppsättning för system. Diagnostics. process

I följande exempel definierar PSStandardMembers-medlems uppsättningen DefaultDisplayPropertySet-egenskapen som har angetts för [system. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) -objekt. Den här egenskaps uppsättningen används av cmdleten [format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) .

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

Följande utdata visar standard egenskaperna som returneras av cmdleten [format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) . Endast egenskaperna `Id`, `Handles`, `CPU`och `Name` returneras för varje process objekt.

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

## <a name="see-also"></a>Se även

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)
