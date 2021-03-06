---
ms.date: 09/13/2016
ms.topic: reference
title: Deklarera parameteruppsättningar
description: Deklarera parameteruppsättningar
ms.openlocfilehash: bd4d504a9fe6c7f7626901c49bc08851244f0995
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667070"
---
# <a name="how-to-declare-parameter-sets"></a>Deklarera parameteruppsättningar

Det här exemplet visar hur du definierar två parameter uppsättningar när du deklarerar parametrarna för en cmdlet. Varje parameter uppsättning har både en unik parameter och en delad parameter som används av båda parameter uppsättningarna. Mer information om parameter uppsättningar, inklusive hur du anger standard parameter uppsättningen, finns i [cmdlet parameter](./cmdlet-parameter-sets.md)Sets.

> [!IMPORTANT]
> När det är möjligt definierar du den unika parametern för en parameter uppsättning som en obligatorisk parameter. Men om du vill att din cmdlet ska köras utan att ange några parametrar, kan den unika parametern vara en valfri parameter. Till exempel är den unika parametern för `Get-Command` cmdleten valfri.

## <a name="how-to-define-two-parameter-sets"></a>Definiera två parameter uppsättningar

1. Lägg till `ParameterSet` nyckelordet till attributet parameter för den unika parametern för den första parameter uppsättningen.

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

2. Lägg till `ParameterSet` nyckelordet till attributet parameter för den unika parametern för den andra parameter uppsättningen.

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

3. För den parameter som tillhör båda parameter uppsättningarna lägger du till ett parameter-attribut för varje parameter uppsättning och lägger sedan till `ParameterSet` nyckelordet i varje uppsättning. I varje parameter-attribut kan du ange hur parametern definieras. En parameter kan vara valfri i en uppsättning och obligatorisk i en annan.

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

[Cmdlet-parameteruppsättningar](./cmdlet-parameter-sets.md)

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)
