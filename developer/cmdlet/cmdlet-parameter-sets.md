---
title: Cmdletens parameteruppsättningar | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f902fd4d-8f6e-4ef1-b07f-59983039a0d1
caps.latest.revision: 10
ms.openlocfilehash: a5822ef1ed3c9efb5957c20255783d515de8957a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847700"
---
# <a name="cmdlet-parameter-sets"></a><span data-ttu-id="eee8a-102">Cmdlet-parameteruppsättningar</span><span class="sxs-lookup"><span data-stu-id="eee8a-102">Cmdlet Parameter Sets</span></span>

<span data-ttu-id="eee8a-103">Windows PowerShell använder parameteruppsättningar så att du kan skriva en enda cmdlet som kan utföra olika åtgärder för olika scenarier.</span><span class="sxs-lookup"><span data-stu-id="eee8a-103">Windows PowerShell uses parameter sets to enable you to write a single cmdlet that can perform different actions for different scenarios.</span></span> <span data-ttu-id="eee8a-104">Parameteruppsättningar kan du exponera olika parametrar för användaren och för att returnera olika typer av information baserat på de parametrar som angetts av användaren.</span><span class="sxs-lookup"><span data-stu-id="eee8a-104">Parameter sets enable you to expose different parameters to the user and to return different information based on the parameters specified by the user.</span></span>

## <a name="examples-of-parameter-sets"></a><span data-ttu-id="eee8a-105">Exempel på parameteruppsättningar</span><span class="sxs-lookup"><span data-stu-id="eee8a-105">Examples of Parameter Sets</span></span>

<span data-ttu-id="eee8a-106">Till exempel den `Get-EventLog` cmdlet (som anges av Windows PowerShell) returnerar olika typer av information beroende på om användaren anger den `List` eller `LogName` parametern.</span><span class="sxs-lookup"><span data-stu-id="eee8a-106">For example, the `Get-EventLog` cmdlet (provided by Windows PowerShell) returns different information depending on whether the user specifies the `List` or `LogName` parameter.</span></span> <span data-ttu-id="eee8a-107">Om den `List` parameter har angetts, cmdleten returnerar information om loggfilerna själva men inte händelseinformationen de innehåller.</span><span class="sxs-lookup"><span data-stu-id="eee8a-107">If the `List` parameter is specified, the cmdlet returns information about the log files themselves but not the event information they contain.</span></span> <span data-ttu-id="eee8a-108">Om den `LogName` parameter har angetts, returnerar cmdleten information om händelser i en specifik händelselogg.</span><span class="sxs-lookup"><span data-stu-id="eee8a-108">If the `LogName` parameter is specified, the cmdlet returns information about the events in a specific event log.</span></span> <span data-ttu-id="eee8a-109">Den `List` och `LogName` parametrar identifiera två separata parameteruppsättningar.</span><span class="sxs-lookup"><span data-stu-id="eee8a-109">The `List` and `LogName` parameters identify two separate parameter sets.</span></span>

## <a name="unique-parameter"></a><span data-ttu-id="eee8a-110">Unikt parametern</span><span class="sxs-lookup"><span data-stu-id="eee8a-110">Unique Parameter</span></span>

<span data-ttu-id="eee8a-111">Varje parameteruppsättningen måste ha en unik parameter som Windows PowerShell-runtime kan använda för att visa rätt parameteruppsättningen.</span><span class="sxs-lookup"><span data-stu-id="eee8a-111">Each parameter set must have a unique parameter that the Windows PowerShell runtime can use to expose the appropriate parameter set.</span></span> <span data-ttu-id="eee8a-112">Om möjligt måste unika parametern vara en obligatorisk parameter.</span><span class="sxs-lookup"><span data-stu-id="eee8a-112">If possible, the unique parameter should be a mandatory parameter.</span></span> <span data-ttu-id="eee8a-113">När parametern är obligatorisk om användaren tvingas att ange parametern och Windows PowerShell-runtime använda parametern för att identifiera parametern inställd på att använda.</span><span class="sxs-lookup"><span data-stu-id="eee8a-113">When a parameter is mandatory, the user is forced to specify the parameter, and the Windows PowerShell runtime can use that parameter to identify the parameter set to use.</span></span> <span data-ttu-id="eee8a-114">Den unika parametern får inte vara obligatorisk om cmdlet: är avsedd att köras utan att ange några parametrar.</span><span class="sxs-lookup"><span data-stu-id="eee8a-114">The unique parameter cannot be mandatory if your cmdlet is designed to be run without specifying any parameters.</span></span>

## <a name="multiple-parameter-sets"></a><span data-ttu-id="eee8a-115">Flera parameteruppsättningar</span><span class="sxs-lookup"><span data-stu-id="eee8a-115">Multiple Parameter Sets</span></span>

<span data-ttu-id="eee8a-116">I följande bild visar den vänstra kolumnen tre giltig parameteruppsättningar.</span><span class="sxs-lookup"><span data-stu-id="eee8a-116">In the following illustration, the left column shows three valid parameter sets.</span></span> <span data-ttu-id="eee8a-117">Parametern A är unika för den första parameteruppsättningen parametern B är unika för den andra parameteruppsättningen och parametern C är unika för den tredje parameteruppsättningen.</span><span class="sxs-lookup"><span data-stu-id="eee8a-117">Parameter A is unique to the first parameter set, parameter B is unique to the second parameter set, and parameter C is unique to the third parameter set.</span></span> <span data-ttu-id="eee8a-118">I den högra kolumnen har parameteruppsättningar men inte en unik parameter.</span><span class="sxs-lookup"><span data-stu-id="eee8a-118">However, in the right column, the parameter sets do not have a unique parameter.</span></span>

![ps_parametersets](../media/ps-parametersets.gif)

## <a name="parameter-set-requirements"></a><span data-ttu-id="eee8a-120">Parameteruppsättning krav</span><span class="sxs-lookup"><span data-stu-id="eee8a-120">Parameter Set Requirements</span></span>

<span data-ttu-id="eee8a-121">Följande krav gäller för alla parameteruppsättningar.</span><span class="sxs-lookup"><span data-stu-id="eee8a-121">The following requirements apply to all parameter sets.</span></span>

- <span data-ttu-id="eee8a-122">Varje parameteruppsättningen måste ha minst en unik parameter.</span><span class="sxs-lookup"><span data-stu-id="eee8a-122">Each parameter set must have at least one unique parameter.</span></span> <span data-ttu-id="eee8a-123">Se den här parametern om möjligt en obligatorisk parameter.</span><span class="sxs-lookup"><span data-stu-id="eee8a-123">If possible, make this parameter a mandatory parameter.</span></span>

- <span data-ttu-id="eee8a-124">En parameteruppsättning som innehåller flera namngivna parametrar måste definiera unika positioner för varje parameter.</span><span class="sxs-lookup"><span data-stu-id="eee8a-124">A parameter set that contains multiple positional parameters must define unique positions for each parameter.</span></span> <span data-ttu-id="eee8a-125">Inga två namngivna parametrar kan ange samma plats.</span><span class="sxs-lookup"><span data-stu-id="eee8a-125">No two positional parameters can specify the same position.</span></span>

- <span data-ttu-id="eee8a-126">Endast en parameter i en mängd kan deklarera den `ValueFromPipeline` nyckelord med värdet `true`.</span><span class="sxs-lookup"><span data-stu-id="eee8a-126">Only one parameter in a set can declare the `ValueFromPipeline` keyword with a value of `true`.</span></span> <span data-ttu-id="eee8a-127">Flera parametrar kan definiera den `ValueFromPipelineByPropertyName` nyckelord med värdet `true`.</span><span class="sxs-lookup"><span data-stu-id="eee8a-127">Multiple parameters can define the `ValueFromPipelineByPropertyName` keyword with a value of `true`.</span></span>

- <span data-ttu-id="eee8a-128">Om inga parameteruppsättning har angetts för en parameter, tillhör parametern alla parameteruppsättningar.</span><span class="sxs-lookup"><span data-stu-id="eee8a-128">If no parameter set is specified for a parameter, the parameter belongs to all parameter sets.</span></span>

## <a name="default-parameter-sets"></a><span data-ttu-id="eee8a-129">Standard parameteruppsättningar</span><span class="sxs-lookup"><span data-stu-id="eee8a-129">Default Parameter Sets</span></span>

<span data-ttu-id="eee8a-130">När flera parameteruppsättningar har definierats kan du använda den `DefaultParameterSetName` nyckelordet för Cmdlet-attribut som anger den standard-parameteruppsättningen.</span><span class="sxs-lookup"><span data-stu-id="eee8a-130">When multiple parameter sets are defined, you can use the `DefaultParameterSetName` keyword of the Cmdlet attribute to specify the default parameter set.</span></span> <span data-ttu-id="eee8a-131">Windows PowerShell använder standardparameter som anger om den inte kan avgöra parametern inställd på att använda utifrån den information som tillhandahålls av kommandot.</span><span class="sxs-lookup"><span data-stu-id="eee8a-131">Windows PowerShell uses the default parameter set if it cannot determine the parameter set to use based on the information provided by the command.</span></span> <span data-ttu-id="eee8a-132">Läs mer om attributet Cmdlet [Cmdlet attributet deklarationen](./cmdlet-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="eee8a-132">For more information about the Cmdlet attribute, see [Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md).</span></span>

## <a name="declaring-parameter-sets"></a><span data-ttu-id="eee8a-133">Deklarera parameteruppsättningar</span><span class="sxs-lookup"><span data-stu-id="eee8a-133">Declaring Parameter Sets</span></span>

<span data-ttu-id="eee8a-134">Om du vill skapa en parameteruppsättning, måste du ange den `ParameterSetName` nyckelord när du deklarerar parameterattributet för varje parameter i parameteruppsättningen.</span><span class="sxs-lookup"><span data-stu-id="eee8a-134">To create a parameter set, you must specify the `ParameterSetName` keyword when you declare the Parameter attribute for every parameter in the parameter set.</span></span> <span data-ttu-id="eee8a-135">Lägga till en Parameter attribut för varje parameteruppsättningen för parametrar som tillhör flera parameteruppsättningar.</span><span class="sxs-lookup"><span data-stu-id="eee8a-135">For parameters that belong to multiple parameter sets, add a Parameter attribute for each parameter set.</span></span> <span data-ttu-id="eee8a-136">På så sätt kan du definiera parametern olika för varje parameteruppsättningen.</span><span class="sxs-lookup"><span data-stu-id="eee8a-136">This enables you to define the parameter differently for each parameter set.</span></span> <span data-ttu-id="eee8a-137">Du kan till exempel definiera en parameter som obligatoriskt i en uppsättning och en valfri i en annan.</span><span class="sxs-lookup"><span data-stu-id="eee8a-137">For example, you can define a parameter as mandatory in one set and optional in another.</span></span> <span data-ttu-id="eee8a-138">Varje parameteruppsättningen måste dock innehålla en unik parameter.</span><span class="sxs-lookup"><span data-stu-id="eee8a-138">However, each parameter set must contain one unique parameter.</span></span>

<span data-ttu-id="eee8a-139">I följande exempel visas den `UserName` parametern är unikt parametern för parameteruppsättningen Test01 och `ComputerName` parametern är unikt parametern för Test02 parameteruppsättningen.</span><span class="sxs-lookup"><span data-stu-id="eee8a-139">In the following example, the `UserName` parameter is the unique parameter of the Test01 parameter set, and the `ComputerName` parameter is the unique parameter of the Test02 parameter set.</span></span> <span data-ttu-id="eee8a-140">Den `SharedParam` parametern hör till båda uppsättningarna och är obligatoriskt för Test01 parameteruppsättning men valfritt för Test02 parameteruppsättningen.</span><span class="sxs-lookup"><span data-stu-id="eee8a-140">The `SharedParam` parameter belongs to both sets and is mandatory for the Test01 parameter set but optional for the Test02 parameter set.</span></span>

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
private string sharedParam;    [Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test01")]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```