---
title: Så här deklarerar du parameter uppsättningar | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e6d06a9a78356693fe7a338dc5c9207044b23441
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784171"
---
# <a name="how-to-declare-parameter-sets"></a><span data-ttu-id="29048-102">Deklarera parameteruppsättningar</span><span class="sxs-lookup"><span data-stu-id="29048-102">How to Declare Parameter Sets</span></span>

<span data-ttu-id="29048-103">Det här exemplet visar hur du definierar två parameter uppsättningar när du deklarerar parametrarna för en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="29048-103">This example shows how to define two parameter sets when you declare the parameters for a cmdlet.</span></span> <span data-ttu-id="29048-104">Varje parameter uppsättning har både en unik parameter och en delad parameter som används av båda parameter uppsättningarna.</span><span class="sxs-lookup"><span data-stu-id="29048-104">Each parameter set has both a unique parameter and a shared parameter that is used by both parameter sets.</span></span> <span data-ttu-id="29048-105">Mer information om parameter uppsättningar, inklusive hur du anger standard parameter uppsättningen, finns i [cmdlet parameter](./cmdlet-parameter-sets.md)Sets.</span><span class="sxs-lookup"><span data-stu-id="29048-105">For more information about parameters sets, including how to specify the default parameter set, see [Cmdlet Parameter Sets](./cmdlet-parameter-sets.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="29048-106">När det är möjligt definierar du den unika parametern för en parameter uppsättning som en obligatorisk parameter.</span><span class="sxs-lookup"><span data-stu-id="29048-106">Whenever possible, define the unique parameter of a parameter set as a required parameter.</span></span> <span data-ttu-id="29048-107">Men om du vill att din cmdlet ska köras utan att ange några parametrar, kan den unika parametern vara en valfri parameter.</span><span class="sxs-lookup"><span data-stu-id="29048-107">However, if you want your cmdlet to run without specifying any parameters, the unique parameter can be an optional parameter.</span></span> <span data-ttu-id="29048-108">Till exempel är den unika parametern för `Get-Command` cmdleten valfri.</span><span class="sxs-lookup"><span data-stu-id="29048-108">For example, the unique parameter of the `Get-Command` cmdlet is optional.</span></span>

## <a name="how-to-define-two-parameter-sets"></a><span data-ttu-id="29048-109">Definiera två parameter uppsättningar</span><span class="sxs-lookup"><span data-stu-id="29048-109">How to Define Two Parameter Sets</span></span>

1. <span data-ttu-id="29048-110">Lägg till `ParameterSet` nyckelordet till attributet parameter för den unika parametern för den första parameter uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="29048-110">Add the `ParameterSet` keyword to the Parameter attribute for the unique parameter of the first parameter set.</span></span>

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

2. <span data-ttu-id="29048-111">Lägg till `ParameterSet` nyckelordet till attributet parameter för den unika parametern för den andra parameter uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="29048-111">Add the `ParameterSet` keyword to the Parameter attribute for the unique parameter of the second parameter set.</span></span>

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

3. <span data-ttu-id="29048-112">För den parameter som tillhör båda parameter uppsättningarna lägger du till ett parameter-attribut för varje parameter uppsättning och lägger sedan till `ParameterSet` nyckelordet i varje uppsättning.</span><span class="sxs-lookup"><span data-stu-id="29048-112">For the parameter that belongs to both parameter sets, add a Parameter attribute for each parameter set and then add the `ParameterSet` keyword to each set.</span></span> <span data-ttu-id="29048-113">I varje parameter-attribut kan du ange hur parametern definieras.</span><span class="sxs-lookup"><span data-stu-id="29048-113">In each Parameter attribute, you can specify how that parameter is defined.</span></span> <span data-ttu-id="29048-114">En parameter kan vara valfri i en uppsättning och obligatorisk i en annan.</span><span class="sxs-lookup"><span data-stu-id="29048-114">A parameter can be optional in one set and mandatory in another.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="29048-115">Se även</span><span class="sxs-lookup"><span data-stu-id="29048-115">See Also</span></span>

[<span data-ttu-id="29048-116">Cmdlet-parameteruppsättningar</span><span class="sxs-lookup"><span data-stu-id="29048-116">Cmdlet Parameter Sets</span></span>](./cmdlet-parameter-sets.md)

[<span data-ttu-id="29048-117">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="29048-117">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
