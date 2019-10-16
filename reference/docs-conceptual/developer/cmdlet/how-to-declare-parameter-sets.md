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
# <a name="how-to-declare-parameter-sets"></a><span data-ttu-id="aa64d-102">Deklarera parameteruppsättningar</span><span class="sxs-lookup"><span data-stu-id="aa64d-102">How to Declare Parameter Sets</span></span>

<span data-ttu-id="aa64d-103">Det här exemplet visar hur du definierar två parameter uppsättningar när du deklarerar parametrarna för en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="aa64d-103">This example shows how to define two parameter sets when you declare the parameters for a cmdlet.</span></span> <span data-ttu-id="aa64d-104">Varje parameter uppsättning har både en unik parameter och en delad parameter som används av båda parameter uppsättningarna.</span><span class="sxs-lookup"><span data-stu-id="aa64d-104">Each parameter set has both a unique parameter and a shared parameter that is used by both parameter sets.</span></span> <span data-ttu-id="aa64d-105">Mer information om parameter uppsättningar, inklusive hur du anger standard parameter uppsättningen, finns i [cmdlet parameter](./cmdlet-parameter-sets.md)Sets.</span><span class="sxs-lookup"><span data-stu-id="aa64d-105">For more information about parameters sets, including how to specify the default parameter set, see [Cmdlet Parameter Sets](./cmdlet-parameter-sets.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="aa64d-106">När det är möjligt definierar du den unika parametern för en parameter uppsättning som en obligatorisk parameter.</span><span class="sxs-lookup"><span data-stu-id="aa64d-106">Whenever possible, define the unique parameter of a parameter set as a required parameter.</span></span> <span data-ttu-id="aa64d-107">Men om du vill att din cmdlet ska köras utan att ange några parametrar, kan den unika parametern vara en valfri parameter.</span><span class="sxs-lookup"><span data-stu-id="aa64d-107">However, if you want your cmdlet to run without specifying any parameters, the unique parameter can be an optional parameter.</span></span> <span data-ttu-id="aa64d-108">Till exempel är den unika parametern för cmdleten `Get-Command` valfri.</span><span class="sxs-lookup"><span data-stu-id="aa64d-108">For example, the unique parameter of the `Get-Command` cmdlet is optional.</span></span>

## <a name="how-to-define-two-parameter-sets"></a><span data-ttu-id="aa64d-109">Definiera två parameter uppsättningar</span><span class="sxs-lookup"><span data-stu-id="aa64d-109">How to Define Two Parameter Sets</span></span>

1. <span data-ttu-id="aa64d-110">Lägg till nyckelordet `ParameterSet` till attributet parameter för den unika parametern för den första parameter uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="aa64d-110">Add the `ParameterSet` keyword to the Parameter attribute for the unique parameter of the first parameter set.</span></span>

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

2. <span data-ttu-id="aa64d-111">Lägg till nyckelordet `ParameterSet` till attributet parameter för den unika parametern för den andra parameter uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="aa64d-111">Add the `ParameterSet` keyword to the Parameter attribute for the unique parameter of the second parameter set.</span></span>

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

3. <span data-ttu-id="aa64d-112">För den parameter som tillhör båda parameter uppsättningarna lägger du till ett parameter-attribut för varje parameter uppsättning och lägger sedan till nyckelordet `ParameterSet` i varje uppsättning.</span><span class="sxs-lookup"><span data-stu-id="aa64d-112">For the parameter that belongs to both parameter sets, add a Parameter attribute for each parameter set and then add the `ParameterSet` keyword to each set.</span></span> <span data-ttu-id="aa64d-113">I varje parameter-attribut kan du ange hur parametern definieras.</span><span class="sxs-lookup"><span data-stu-id="aa64d-113">In each Parameter attribute, you can specify how that parameter is defined.</span></span> <span data-ttu-id="aa64d-114">En parameter kan vara valfri i en uppsättning och obligatorisk i en annan.</span><span class="sxs-lookup"><span data-stu-id="aa64d-114">A parameter can be optional in one set and mandatory in another.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="aa64d-115">Se även</span><span class="sxs-lookup"><span data-stu-id="aa64d-115">See Also</span></span>

[<span data-ttu-id="aa64d-116">Cmdlet-parameter uppsättningar</span><span class="sxs-lookup"><span data-stu-id="aa64d-116">Cmdlet Parameter Sets</span></span>](./cmdlet-parameter-sets.md)

[<span data-ttu-id="aa64d-117">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="aa64d-117">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
