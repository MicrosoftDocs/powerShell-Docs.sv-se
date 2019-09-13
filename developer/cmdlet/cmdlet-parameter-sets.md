---
title: Cmdlet-parameter uppsättningar | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f902fd4d-8f6e-4ef1-b07f-59983039a0d1
caps.latest.revision: 10
ms.openlocfilehash: d8c00c7ffd369a32af151836785a2c5f47b05a68
ms.sourcegitcommit: 889b93d170aeb3d444288e7ccf67e62ce822cb7c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/12/2019
ms.locfileid: "70936192"
---
# <a name="cmdlet-parameter-sets"></a><span data-ttu-id="581de-102">Cmdlet-parameter uppsättningar</span><span class="sxs-lookup"><span data-stu-id="581de-102">Cmdlet parameter sets</span></span>

<span data-ttu-id="581de-103">PowerShell använder parameter uppsättningar för att ge dig möjlighet att skriva en enda cmdlet som kan utföra olika åtgärder för olika scenarier.</span><span class="sxs-lookup"><span data-stu-id="581de-103">PowerShell uses parameter sets to enable you to write a single cmdlet that can do different actions for different scenarios.</span></span> <span data-ttu-id="581de-104">Parameter uppsättningar gör att du kan exponera olika parametrar för användaren.</span><span class="sxs-lookup"><span data-stu-id="581de-104">Parameter sets enable you to expose different parameters to the user.</span></span> <span data-ttu-id="581de-105">Och för att returnera annan information baserat på de parametrar som anges av användaren.</span><span class="sxs-lookup"><span data-stu-id="581de-105">And, to return different information based on the parameters specified by the user.</span></span>

## <a name="examples-of-parameter-sets"></a><span data-ttu-id="581de-106">Exempel på parameter uppsättningar</span><span class="sxs-lookup"><span data-stu-id="581de-106">Examples of parameter sets</span></span>

<span data-ttu-id="581de-107">PowerShell `Get-EventLog` -cmdleten returnerar till exempel olika uppgifter beroende på om användaren anger **listan** eller parametern **LogName** .</span><span class="sxs-lookup"><span data-stu-id="581de-107">For example, the PowerShell `Get-EventLog` cmdlet returns different information depending on whether the user specifies the **List** or **LogName** parameter.</span></span> <span data-ttu-id="581de-108">Om **list** parametern anges, returnerar cmdleten information om själva loggfilerna, men inte den händelse information som de innehåller.</span><span class="sxs-lookup"><span data-stu-id="581de-108">If the **List** parameter is specified, the cmdlet returns information about the log files themselves but not the event information they contain.</span></span> <span data-ttu-id="581de-109">Om parametern **LogName** anges returnerar cmdleten information om händelserna i en specifik händelse logg.</span><span class="sxs-lookup"><span data-stu-id="581de-109">If the **LogName** parameter is specified, the cmdlet returns information about the events in a specific event log.</span></span> <span data-ttu-id="581de-110">**List** -och **LogName** -parametrarna identifierar två separata parameter uppsättningar.</span><span class="sxs-lookup"><span data-stu-id="581de-110">The **List** and **LogName** parameters identify two separate parameter sets.</span></span>

## <a name="unique-parameter"></a><span data-ttu-id="581de-111">Unik parameter</span><span class="sxs-lookup"><span data-stu-id="581de-111">Unique parameter</span></span>

<span data-ttu-id="581de-112">Varje parameter uppsättning måste ha en unik parameter som PowerShell-körningsmiljön använder för att exponera rätt parameter uppsättning.</span><span class="sxs-lookup"><span data-stu-id="581de-112">Each parameter set must have a unique parameter that the PowerShell runtime uses to expose the appropriate parameter set.</span></span> <span data-ttu-id="581de-113">Om möjligt ska den unika parametern vara en obligatorisk parameter.</span><span class="sxs-lookup"><span data-stu-id="581de-113">If possible, the unique parameter should be a mandatory parameter.</span></span> <span data-ttu-id="581de-114">När en parameter är obligatorisk måste användaren ange parametern och PowerShell-körningsmiljön använder den parametern för att identifiera parameter uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="581de-114">When a parameter is mandatory, the user must specify the parameter, and the PowerShell runtime uses that parameter to identify the parameter set.</span></span> <span data-ttu-id="581de-115">Den unika parametern kan inte vara obligatorisk om din cmdlet är avsedd att köras utan att några parametrar anges.</span><span class="sxs-lookup"><span data-stu-id="581de-115">The unique parameter can't be mandatory if your cmdlet is designed to run without specifying any parameters.</span></span>

## <a name="multiple-parameter-sets"></a><span data-ttu-id="581de-116">Flera parameter uppsättningar</span><span class="sxs-lookup"><span data-stu-id="581de-116">Multiple parameter sets</span></span>

<span data-ttu-id="581de-117">I följande bild visas tre giltiga parameter uppsättningar i den vänstra kolumnen.</span><span class="sxs-lookup"><span data-stu-id="581de-117">In the following illustration, the left column shows three valid parameter sets.</span></span> <span data-ttu-id="581de-118">**Parametern A** är unik för den första parameter uppsättningen, **parametern B** är unik för den andra parameter uppsättningen och **parametern C** är unik för den tredje parameter uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="581de-118">**Parameter A** is unique to the first parameter set, **parameter B** is unique to the second parameter set, and **parameter C** is unique to the third parameter set.</span></span> <span data-ttu-id="581de-119">Parameter uppsättningarna i den högra kolumnen har ingen unik parameter.</span><span class="sxs-lookup"><span data-stu-id="581de-119">In the right column, the parameter sets don't have a unique parameter.</span></span>

![ps_parametersets](../media/ps-parametersets.gif)

## <a name="parameter-set-requirements"></a><span data-ttu-id="581de-121">Krav för parameter uppsättning</span><span class="sxs-lookup"><span data-stu-id="581de-121">Parameter set requirements</span></span>

<span data-ttu-id="581de-122">Följande krav gäller för alla parameter uppsättningar.</span><span class="sxs-lookup"><span data-stu-id="581de-122">The following requirements apply to all parameter sets.</span></span>

- <span data-ttu-id="581de-123">Varje parameter uppsättning måste ha minst en unik parameter.</span><span class="sxs-lookup"><span data-stu-id="581de-123">Each parameter set must have at least one unique parameter.</span></span> <span data-ttu-id="581de-124">Om möjligt ska du göra denna parameter till en obligatorisk parameter.</span><span class="sxs-lookup"><span data-stu-id="581de-124">If possible, make this parameter a mandatory parameter.</span></span>

- <span data-ttu-id="581de-125">En parameter uppsättning som innehåller flera positions parametrar måste definiera unika positioner för varje parameter.</span><span class="sxs-lookup"><span data-stu-id="581de-125">A parameter set that contains multiple positional parameters must define unique positions for each parameter.</span></span> <span data-ttu-id="581de-126">Det går inte att ange samma position med två positions parametrar.</span><span class="sxs-lookup"><span data-stu-id="581de-126">No two positional parameters can specify the same position.</span></span>

- <span data-ttu-id="581de-127">Endast en parameter i en mängd kan deklarera `ValueFromPipeline` nyckelordet med `true`värdet.</span><span class="sxs-lookup"><span data-stu-id="581de-127">Only one parameter in a set can declare the `ValueFromPipeline` keyword with a value of `true`.</span></span>
  <span data-ttu-id="581de-128">Flera parametrar kan definiera `ValueFromPipelineByPropertyName` nyckelordet med `true`värdet.</span><span class="sxs-lookup"><span data-stu-id="581de-128">Multiple parameters can define the `ValueFromPipelineByPropertyName` keyword with a value of `true`.</span></span>

- <span data-ttu-id="581de-129">Om ingen parameter uppsättning anges för en parameter, tillhör parametern alla parameter uppsättningar.</span><span class="sxs-lookup"><span data-stu-id="581de-129">If no parameter set is specified for a parameter, the parameter belongs to all parameter sets.</span></span>

> [!NOTE]
> <span data-ttu-id="581de-130">För en cmdlet eller funktion finns det en gräns på 32 parameter uppsättningar.</span><span class="sxs-lookup"><span data-stu-id="581de-130">For a cmdlet or function, there is a limit of 32 parameter sets.</span></span>

## <a name="default-parameter-sets"></a><span data-ttu-id="581de-131">Standard parameter uppsättningar</span><span class="sxs-lookup"><span data-stu-id="581de-131">Default parameter sets</span></span>

<span data-ttu-id="581de-132">När du har definierat flera parameter uppsättningar kan du ange standard `DefaultParameterSetName` parameter uppsättningen genom att använda nyckelordet för **cmdlet** -attributet.</span><span class="sxs-lookup"><span data-stu-id="581de-132">When multiple parameter sets are defined, you can use the `DefaultParameterSetName` keyword of the **Cmdlet** attribute to specify the default parameter set.</span></span> <span data-ttu-id="581de-133">PowerShell använder standard parameter uppsättningen om den inte kan avgöra vilken parameter som ska användas baserat på den information som tillhandahålls av kommandot.</span><span class="sxs-lookup"><span data-stu-id="581de-133">PowerShell uses the default parameter set if it can't determine the parameter set to use based on the information provided by the command.</span></span> <span data-ttu-id="581de-134">Mer information om **cmdlet** -attributet finns i [deklaration av cmdlet-attribut](./cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="581de-134">For more information about the **Cmdlet** attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="declaring-parameter-sets"></a><span data-ttu-id="581de-135">Deklarera parameter uppsättningar</span><span class="sxs-lookup"><span data-stu-id="581de-135">Declaring parameter sets</span></span>

<span data-ttu-id="581de-136">Om du vill skapa en parameter uppsättning måste du ange `ParameterSetName` nyckelordet när du deklarerar attributet **parameter** för varje parameter i parameter uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="581de-136">To create a parameter set, you must specify the `ParameterSetName` keyword when you declare the **Parameter** attribute for every parameter in the parameter set.</span></span> <span data-ttu-id="581de-137">För parametrar som tillhör flera parameter uppsättningar lägger du till ett **parameter** -attribut för varje parameter uppsättning.</span><span class="sxs-lookup"><span data-stu-id="581de-137">For parameters that belong to multiple parameter sets, add a **Parameter** attribute for each parameter set.</span></span> <span data-ttu-id="581de-138">Med det här attributet kan du definiera parametern på olika sätt för varje parameter uppsättning.</span><span class="sxs-lookup"><span data-stu-id="581de-138">This attribute enables you to define the parameter differently for each parameter set.</span></span> <span data-ttu-id="581de-139">Du kan till exempel definiera en parameter som obligatorisk i en uppsättning och valfri i en annan.</span><span class="sxs-lookup"><span data-stu-id="581de-139">For example, you can define a parameter as mandatory in one set and optional in another.</span></span> <span data-ttu-id="581de-140">Varje parameter uppsättning måste dock innehålla en unik parameter.</span><span class="sxs-lookup"><span data-stu-id="581de-140">However, each parameter set must contain one unique parameter.</span></span> <span data-ttu-id="581de-141">Mer information finns i [deklaration av parameter attribut](parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="581de-141">For more information, see [Parameter Attribute Declaration](parameter-attribute-declaration.md).</span></span>

<span data-ttu-id="581de-142">I följande exempel är parametern **username** den unika parametern för `Test01` parameter uppsättningen och parametern **computername** `Test02` är den unika parametern för parameter uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="581de-142">In the following example, the **UserName** parameter is the unique parameter of the `Test01` parameter set, and the **ComputerName** parameter is the unique parameter of the `Test02` parameter set.</span></span> <span data-ttu-id="581de-143">Parametern **SharedParam** tillhör båda uppsättningarna och är obligatorisk för `Test01` parameter uppsättningen `Test02` men valfritt för parameter uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="581de-143">The **SharedParam** parameter belongs to both sets and is mandatory for the `Test01` parameter set but optional for the `Test02` parameter set.</span></span>

```csharp
[Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test01")]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;

[Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test02")]
public string ComputerName
{
  get { return computerName; }
  set { computerName = value; }
}
private string computerName;

[Parameter(Mandatory= true, ParameterSetName = "Test01")]
[Parameter(ParameterSetName = "Test02")]
public string SharedParam
{
    get { return sharedParam; }
    set { sharedParam = value; }
}
private string sharedParam;
```
