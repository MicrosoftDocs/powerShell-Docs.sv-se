---
ms.date: 09/13/2016
ms.topic: reference
title: Definiera standardmedlemsuppsättningar för objekt
description: Definiera standardmedlemsuppsättningar för objekt
ms.openlocfilehash: 919f7ba65322c6a56a27e046fb211bde151abf7d
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92653126"
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

Följande utdata visar standard egenskaperna som returneras av cmdleten [format-List](/powershell/module/Microsoft.PowerShell.Utility/Format-List) . Endast `Id` egenskaperna, `Handles` , `CPU` och `Name` returneras för varje process objekt.

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
