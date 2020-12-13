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
# <a name="how-to-declare-parameter-sets"></a><span data-ttu-id="6b89d-103">Deklarera parameteruppsättningar</span><span class="sxs-lookup"><span data-stu-id="6b89d-103">How to Declare Parameter Sets</span></span>

<span data-ttu-id="6b89d-104">Det här exemplet visar hur du definierar två parameter uppsättningar när du deklarerar parametrarna för en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6b89d-104">This example shows how to define two parameter sets when you declare the parameters for a cmdlet.</span></span> <span data-ttu-id="6b89d-105">Varje parameter uppsättning har både en unik parameter och en delad parameter som används av båda parameter uppsättningarna.</span><span class="sxs-lookup"><span data-stu-id="6b89d-105">Each parameter set has both a unique parameter and a shared parameter that is used by both parameter sets.</span></span> <span data-ttu-id="6b89d-106">Mer information om parameter uppsättningar, inklusive hur du anger standard parameter uppsättningen, finns i [cmdlet parameter](./cmdlet-parameter-sets.md)Sets.</span><span class="sxs-lookup"><span data-stu-id="6b89d-106">For more information about parameters sets, including how to specify the default parameter set, see [Cmdlet Parameter Sets](./cmdlet-parameter-sets.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6b89d-107">När det är möjligt definierar du den unika parametern för en parameter uppsättning som en obligatorisk parameter.</span><span class="sxs-lookup"><span data-stu-id="6b89d-107">Whenever possible, define the unique parameter of a parameter set as a required parameter.</span></span> <span data-ttu-id="6b89d-108">Men om du vill att din cmdlet ska köras utan att ange några parametrar, kan den unika parametern vara en valfri parameter.</span><span class="sxs-lookup"><span data-stu-id="6b89d-108">However, if you want your cmdlet to run without specifying any parameters, the unique parameter can be an optional parameter.</span></span> <span data-ttu-id="6b89d-109">Till exempel är den unika parametern för `Get-Command` cmdleten valfri.</span><span class="sxs-lookup"><span data-stu-id="6b89d-109">For example, the unique parameter of the `Get-Command` cmdlet is optional.</span></span>

## <a name="how-to-define-two-parameter-sets"></a><span data-ttu-id="6b89d-110">Definiera två parameter uppsättningar</span><span class="sxs-lookup"><span data-stu-id="6b89d-110">How to Define Two Parameter Sets</span></span>

1. <span data-ttu-id="6b89d-111">Lägg till `ParameterSet` nyckelordet till attributet parameter för den unika parametern för den första parameter uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="6b89d-111">Add the `ParameterSet` keyword to the Parameter attribute for the unique parameter of the first parameter set.</span></span>

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

2. <span data-ttu-id="6b89d-112">Lägg till `ParameterSet` nyckelordet till attributet parameter för den unika parametern för den andra parameter uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="6b89d-112">Add the `ParameterSet` keyword to the Parameter attribute for the unique parameter of the second parameter set.</span></span>

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

3. <span data-ttu-id="6b89d-113">För den parameter som tillhör båda parameter uppsättningarna lägger du till ett parameter-attribut för varje parameter uppsättning och lägger sedan till `ParameterSet` nyckelordet i varje uppsättning.</span><span class="sxs-lookup"><span data-stu-id="6b89d-113">For the parameter that belongs to both parameter sets, add a Parameter attribute for each parameter set and then add the `ParameterSet` keyword to each set.</span></span> <span data-ttu-id="6b89d-114">I varje parameter-attribut kan du ange hur parametern definieras.</span><span class="sxs-lookup"><span data-stu-id="6b89d-114">In each Parameter attribute, you can specify how that parameter is defined.</span></span> <span data-ttu-id="6b89d-115">En parameter kan vara valfri i en uppsättning och obligatorisk i en annan.</span><span class="sxs-lookup"><span data-stu-id="6b89d-115">A parameter can be optional in one set and mandatory in another.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="6b89d-116">Se även</span><span class="sxs-lookup"><span data-stu-id="6b89d-116">See Also</span></span>

[<span data-ttu-id="6b89d-117">Cmdlet-parameteruppsättningar</span><span class="sxs-lookup"><span data-stu-id="6b89d-117">Cmdlet Parameter Sets</span></span>](./cmdlet-parameter-sets.md)

[<span data-ttu-id="6b89d-118">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="6b89d-118">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
