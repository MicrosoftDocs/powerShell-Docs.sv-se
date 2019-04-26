---
title: Hur du deklarera parameteruppsättningar | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 46905eb9-64d7-4c55-9c2a-7bc7bf04e14b
caps.latest.revision: 10
ms.openlocfilehash: 6c2e5891a8e3f24969c12a2e57dc5ae8caa68e41
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067900"
---
# <a name="how-to-declare-parameter-sets"></a>Deklarera parameteruppsättningar

Det här exemplet visar hur du definierar två parameteruppsättningar när du deklarerar parametrar för en cmdlet. Varje parameteruppsättning har både en unik parameter och en delad parameter som används av både parameteruppsättningar. Läs mer om parametrar uppsättningar, inklusive hur du anger en standarduppsättning av parametern [cmdlet: en Parameter anger](./cmdlet-parameter-sets.md).

> [!IMPORTANT]
> Definiera parametern unikt för en parameter som angetts som en obligatorisk parameter när det är möjligt. Om du vill att din cmdleten ska köras utan att ange parametrar kan parametern unika vara en valfri parameter. Till exempel unika parametern till den `Get-Command` cmdlet är valfritt.

## <a name="how-to-define-two-parameter-sets"></a>Hur du definierar två parameteruppsättningar

1. Lägg till den `ParameterSet` nyckelord till parametern-attributet för parametern unikt för den första parameteruppsättningen.

   ```csharp
   [Parameter(Position = 0, Mandatory = true,
              ParameterSetName = "Test01")]
   public string UserName
   {
     get { return userName; }
     set { userName = value; }
   }
   private string userName;
   ```

2. Lägg till den `ParameterSet` nyckelord till parametern-attributet för unik parametern för den andra parameteruppsättningen.

   ```csharp
   [Parameter(Position = 0, Mandatory = true,
              ParameterSetName = "Test02")]
   public string ComputerName
   {
     get { return computerName; }
     set { computerName = value; }
   }
   private string computerName;
   ```

3. Lägg till en Parameter-attribut för varje parameter parameter som hör till båda parameteruppsättningar och Lägg sedan till den `ParameterSet` nyckelord till varje uppsättning. Du kan ange hur parametern har definierats i varje Parameter-attribut. En parameter kan vara valfritt i en uppsättning och obligatoriska i en annan.

   ```csharp
   [Parameter(Mandatory= true, ParameterSetName = "Test01")]
   [Parameter(ParameterSetName = "Test02")]
   public string SharedParam
   {
       get { return sharedParam; }
       set { sharedParam = value; }
   }
   private string sharedParam;
   ```

## <a name="see-also"></a>Se även

[Cmdletens parameteruppsättningar](./cmdlet-parameter-sets.md)

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
