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
# <a name="how-to-declare-parameter-sets"></a><span data-ttu-id="527cb-102">Deklarera parameteruppsättningar</span><span class="sxs-lookup"><span data-stu-id="527cb-102">How to Declare Parameter Sets</span></span>

<span data-ttu-id="527cb-103">Det här exemplet visar hur du definierar två parameteruppsättningar när du deklarerar parametrar för en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="527cb-103">This example shows how to define two parameter sets when you declare the parameters for a cmdlet.</span></span> <span data-ttu-id="527cb-104">Varje parameteruppsättning har både en unik parameter och en delad parameter som används av både parameteruppsättningar.</span><span class="sxs-lookup"><span data-stu-id="527cb-104">Each parameter set has both a unique parameter and a shared parameter that is used by both parameter sets.</span></span> <span data-ttu-id="527cb-105">Läs mer om parametrar uppsättningar, inklusive hur du anger en standarduppsättning av parametern [cmdlet: en Parameter anger](./cmdlet-parameter-sets.md).</span><span class="sxs-lookup"><span data-stu-id="527cb-105">For more information about parameters sets, including how to specify the default parameter set, see [Cmdlet Parameter Sets](./cmdlet-parameter-sets.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="527cb-106">Definiera parametern unikt för en parameter som angetts som en obligatorisk parameter när det är möjligt.</span><span class="sxs-lookup"><span data-stu-id="527cb-106">Whenever possible, define the unique parameter of a parameter set as a required parameter.</span></span> <span data-ttu-id="527cb-107">Om du vill att din cmdleten ska köras utan att ange parametrar kan parametern unika vara en valfri parameter.</span><span class="sxs-lookup"><span data-stu-id="527cb-107">However, if you want your cmdlet to run without specifying any parameters, the unique parameter can be an optional parameter.</span></span> <span data-ttu-id="527cb-108">Till exempel unika parametern till den `Get-Command` cmdlet är valfritt.</span><span class="sxs-lookup"><span data-stu-id="527cb-108">For example, the unique parameter of the `Get-Command` cmdlet is optional.</span></span>

## <a name="how-to-define-two-parameter-sets"></a><span data-ttu-id="527cb-109">Hur du definierar två parameteruppsättningar</span><span class="sxs-lookup"><span data-stu-id="527cb-109">How to Define Two Parameter Sets</span></span>

1. <span data-ttu-id="527cb-110">Lägg till den `ParameterSet` nyckelord till parametern-attributet för parametern unikt för den första parameteruppsättningen.</span><span class="sxs-lookup"><span data-stu-id="527cb-110">Add the `ParameterSet` keyword to the Parameter attribute for the unique parameter of the first parameter set.</span></span>

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

2. <span data-ttu-id="527cb-111">Lägg till den `ParameterSet` nyckelord till parametern-attributet för unik parametern för den andra parameteruppsättningen.</span><span class="sxs-lookup"><span data-stu-id="527cb-111">Add the `ParameterSet` keyword to the Parameter attribute for the unique parameter of the second parameter set.</span></span>

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

3. <span data-ttu-id="527cb-112">Lägg till en Parameter-attribut för varje parameter parameter som hör till båda parameteruppsättningar och Lägg sedan till den `ParameterSet` nyckelord till varje uppsättning.</span><span class="sxs-lookup"><span data-stu-id="527cb-112">For the parameter that belongs to both parameter sets, add a Parameter attribute for each parameter set and then add the `ParameterSet` keyword to each set.</span></span> <span data-ttu-id="527cb-113">Du kan ange hur parametern har definierats i varje Parameter-attribut.</span><span class="sxs-lookup"><span data-stu-id="527cb-113">In each Parameter attribute, you can specify how that parameter is defined.</span></span> <span data-ttu-id="527cb-114">En parameter kan vara valfritt i en uppsättning och obligatoriska i en annan.</span><span class="sxs-lookup"><span data-stu-id="527cb-114">A parameter can be optional in one set and mandatory in another.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="527cb-115">Se även</span><span class="sxs-lookup"><span data-stu-id="527cb-115">See Also</span></span>

[<span data-ttu-id="527cb-116">Cmdletens parameteruppsättningar</span><span class="sxs-lookup"><span data-stu-id="527cb-116">Cmdlet Parameter Sets</span></span>](./cmdlet-parameter-sets.md)

[<span data-ttu-id="527cb-117">Skriva en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="527cb-117">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
