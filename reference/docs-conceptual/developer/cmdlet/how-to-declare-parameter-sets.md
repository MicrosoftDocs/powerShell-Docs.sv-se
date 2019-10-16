---
title: Så här deklarerar du parameter uppsättningar | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 46905eb9-64d7-4c55-9c2a-7bc7bf04e14b
caps.latest.revision: 10
ms.openlocfilehash: 6c2e5891a8e3f24969c12a2e57dc5ae8caa68e41
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72356352"
---
# <a name="how-to-declare-parameter-sets"></a>Deklarera parameteruppsättningar

Det här exemplet visar hur du definierar två parameter uppsättningar när du deklarerar parametrarna för en cmdlet. Varje parameter uppsättning har både en unik parameter och en delad parameter som används av båda parameter uppsättningarna. Mer information om parameter uppsättningar, inklusive hur du anger standard parameter uppsättningen, finns i [cmdlet parameter](./cmdlet-parameter-sets.md)Sets.

> [!IMPORTANT]
> När det är möjligt definierar du den unika parametern för en parameter uppsättning som en obligatorisk parameter. Men om du vill att din cmdlet ska köras utan att ange några parametrar, kan den unika parametern vara en valfri parameter. Till exempel är den unika parametern för cmdleten `Get-Command` valfri.

## <a name="how-to-define-two-parameter-sets"></a>Definiera två parameter uppsättningar

1. Lägg till nyckelordet `ParameterSet` till attributet parameter för den unika parametern för den första parameter uppsättningen.

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

2. Lägg till nyckelordet `ParameterSet` till attributet parameter för den unika parametern för den andra parameter uppsättningen.

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

3. För den parameter som tillhör båda parameter uppsättningarna lägger du till ett parameter-attribut för varje parameter uppsättning och lägger sedan till nyckelordet `ParameterSet` i varje uppsättning. I varje parameter-attribut kan du ange hur parametern definieras. En parameter kan vara valfri i en uppsättning och obligatorisk i en annan.

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

[Cmdlet-parameter uppsättningar](./cmdlet-parameter-sets.md)

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)