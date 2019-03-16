---
title: Cmdlet-indata metoderna | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- virtual methods (PowerShell SDK]
ms.assetid: b0bb8172-c9fa-454b-9f1b-57c3fe60671b
caps.latest.revision: 12
ms.openlocfilehash: 065214647dfa6d376b727930fe75140911095faf
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059379"
---
# <a name="cmdlet-input-processing-methods"></a><span data-ttu-id="683b6-102">Bearbetningsmetoder för cmdlet-indata</span><span class="sxs-lookup"><span data-stu-id="683b6-102">Cmdlet Input Processing Methods</span></span>

<span data-ttu-id="683b6-103">Cmdlet: ar måste åsidosätta en eller flera av indata metoderna som beskrivs i det här avsnittet för att utföra sitt arbete.</span><span class="sxs-lookup"><span data-stu-id="683b6-103">Cmdlets must override one or more of the input processing methods described in this topic to perform their work.</span></span> <span data-ttu-id="683b6-104">Dessa metoder kan cmdleten förväg bearbetnings åtgärder, inkommande bearbetningsåtgärder och efter bearbetningsåtgärder.</span><span class="sxs-lookup"><span data-stu-id="683b6-104">These methods allow the cmdlet to perform pre-processing operations, input processing operations, and post-processing operations.</span></span> <span data-ttu-id="683b6-105">Dessa metoder kan du stoppa cmdlet-bearbetning.</span><span class="sxs-lookup"><span data-stu-id="683b6-105">These methods also allow you to stop cmdlet processing.</span></span>

## <a name="pre-processing-tasks"></a><span data-ttu-id="683b6-106">Före bearbetnings uppgifter</span><span class="sxs-lookup"><span data-stu-id="683b6-106">Pre-Processing Tasks</span></span>

<span data-ttu-id="683b6-107">Cmdlet: ar ska åsidosätta den [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) metod för att lägga till alla förbearbetning åtgärder som gäller för alla poster som bearbetas senare av cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="683b6-107">Cmdlets should override the [System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) method to add any preprocessing operations that are valid for all the records that will be processed later by the cmdlet.</span></span> <span data-ttu-id="683b6-108">När Windows PowerShell bearbetar en kommando-pipeline, anropar Windows PowerShell den här metoden en gång för varje instans av cmdlet: en i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="683b6-108">When Windows PowerShell processes a command pipeline, Windows PowerShell calls this method once for each instance of the cmdlet in the pipeline.</span></span> <span data-ttu-id="683b6-109">Mer information om hur Windows PowerShell anropar kommando-pipeline finns i [Cmdlet bearbetar livscykel](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).</span><span class="sxs-lookup"><span data-stu-id="683b6-109">For more information about how Windows PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).</span></span>

<span data-ttu-id="683b6-110">Följande kod visar en implementering av den [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) metod.</span><span class="sxs-lookup"><span data-stu-id="683b6-110">The following code shows an implementation of the [System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) method.</span></span>

```csharp
protected override void BeginProcessing()
{
  // Replace the WriteObject method with the logic required
  // by your cmdlet. It is used here to generate the following
  // output:
  // "This is a test of the BeginProcessing template."
  WriteObject("This is a test of the BeginProcessing template.");
}
```

<span data-ttu-id="683b6-111">Ett mer detaljerat exempel på hur du använder den [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) metod, se [SelectStr självstudien](./selectstr-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="683b6-111">For a more detailed example of how to use the [System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) method, see [SelectStr Tutorial](./selectstr-tutorial.md).</span></span> <span data-ttu-id="683b6-112">I de här självstudierna i **väljer Str** cmdlet använder den [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) metod för att generera det reguljära uttrycket som används för att söka efter de indata som bearbetar poster.</span><span class="sxs-lookup"><span data-stu-id="683b6-112">In this tutorial, the **Select-Str** cmdlet uses the [System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) method to generate the regular expression that is used to search the input processing records.</span></span>

## <a name="input-processing-tasks"></a><span data-ttu-id="683b6-113">Ange uppgifter</span><span class="sxs-lookup"><span data-stu-id="683b6-113">Input Processing Tasks</span></span>

<span data-ttu-id="683b6-114">Cmdlet: ar kan åsidosätta den [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) metod för att bearbeta indata som ska skickas till cmdleten.</span><span class="sxs-lookup"><span data-stu-id="683b6-114">Cmdlets can override the [System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) method to process the input that is sent to the cmdlet.</span></span> <span data-ttu-id="683b6-115">När Windows PowerShell bearbetar en kommando-pipeline, anropar den här metoden för varje inkommande post som bearbetas av cmdlet: en i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="683b6-115">When Windows PowerShell processes a command pipeline, Windows PowerShell calls this method for each input record that is processed by the cmdlet.</span></span> <span data-ttu-id="683b6-116">Mer information om hur Windows PowerShell anropar kommando-pipeline finns i [Cmdlet bearbetar livscykel](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).</span><span class="sxs-lookup"><span data-stu-id="683b6-116">For more information about how Windows PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).</span></span>

<span data-ttu-id="683b6-117">Följande kod visar en implementering av den [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) metod.</span><span class="sxs-lookup"><span data-stu-id="683b6-117">The following code shows an implementation of the [System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) method.</span></span>

```csharp
protected override void ProcessRecord()
{
  // Replace the WriteObject method with the logic required
  // by your cmdlet. It is used here to generate the following
  // output:
  // "This is a test of the ProcessRecord template."
  WriteObject("This is a test of the ProcessRecord template.");
}
```

<span data-ttu-id="683b6-118">Ett mer detaljerat exempel på hur du använder den [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) metod, se [SelectStr självstudien](./selectstr-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="683b6-118">For a more detailed example of how to use the [System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) method, see [SelectStr Tutorial](./selectstr-tutorial.md).</span></span>

## <a name="post-processing-tasks"></a><span data-ttu-id="683b6-119">Efterbearbetning</span><span class="sxs-lookup"><span data-stu-id="683b6-119">Post-Processing Tasks</span></span>

<span data-ttu-id="683b6-120">Cmdlet: ar ska åsidosätta den [System.Management.Automation.Cmdlet.Endprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) metod för att lägga till alla efterbearbetning åtgärder som gäller för alla poster som bearbetats av cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="683b6-120">Cmdlets should override the [System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) method to add any post-processing operations that are valid for all the records that were processed by the cmdlet.</span></span> <span data-ttu-id="683b6-121">Till exempel cmdlet: kan behöva Rensa objektvariabler när den har slutförts bearbetning.</span><span class="sxs-lookup"><span data-stu-id="683b6-121">For example, your cmdlet might have to clean up object variables after it is finished processing.</span></span>

<span data-ttu-id="683b6-122">När Windows PowerShell bearbetar en kommando-pipeline, anropar Windows PowerShell den här metoden en gång för varje instans av cmdlet: en i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="683b6-122">When Windows PowerShell processes a command pipeline, Windows PowerShell calls this method once for each instance of the cmdlet in the pipeline.</span></span> <span data-ttu-id="683b6-123">Det är dock viktigt att komma ihåg att Windows PowerShell-runtime inte anropar den [System.Management.Automation.Cmdlet.Endprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) metoden om cmdlet: en har avbrutits mitt via dess inkommande bearbetning eller om avslutande fel uppstår i någon del av cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="683b6-123">However, it is important to remember that the Windows PowerShell runtime will not call the [System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) method if the cmdlet is canceled midway through its input processing or if a terminating error occurs in any part of the cmdlet.</span></span> <span data-ttu-id="683b6-124">Därför bör en cmdlet som kräver objektet Rensa implementera hela [System.IDisposable](/dotnet/api/System.IDisposable) mönstret, inklusive en finaliserare så att körningen kan anropa både den [ System.Management.Automation.Cmdlet.Endprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) och [System.IDisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) metoder i slutet av bearbetning.</span><span class="sxs-lookup"><span data-stu-id="683b6-124">For this reason, a cmdlet that requires object cleanup should implement the complete [System.IDisposable](/dotnet/api/System.IDisposable) pattern, including a finalizer, so that the runtime can call both the [System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) and [System.IDisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) methods at the end of processing.</span></span> <span data-ttu-id="683b6-125">Mer information om hur Windows PowerShell anropar kommando-pipeline finns i [Cmdlet bearbetar livscykel](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).</span><span class="sxs-lookup"><span data-stu-id="683b6-125">For more information about how Windows PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).</span></span>

<span data-ttu-id="683b6-126">Följande kod visar en implementering av den [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) metod.</span><span class="sxs-lookup"><span data-stu-id="683b6-126">The following code shows an implementation of the [System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) method.</span></span>

```csharp
protected override void EndProcessing()
{
  // Replace the WriteObject method with the logic required
  // by your cmdlet. It is used here to generate the following
  // output:
  // "This is a test of the EndProcessing template."
  WriteObject("This is a test of the EndProcessing template.");
}
```

<span data-ttu-id="683b6-127">Ett mer detaljerat exempel på hur du använder den [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) metod, se [SelectStr självstudien](./selectstr-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="683b6-127">For a more detailed example of how to use the [System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) method, see [SelectStr Tutorial](./selectstr-tutorial.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="683b6-128">Se även</span><span class="sxs-lookup"><span data-stu-id="683b6-128">See Also</span></span>

[<span data-ttu-id="683b6-129">System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname</span><span class="sxs-lookup"><span data-stu-id="683b6-129">System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname</span></span>](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0)

[<span data-ttu-id="683b6-130">System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname</span><span class="sxs-lookup"><span data-stu-id="683b6-130">System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname</span></span>](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0)

[<span data-ttu-id="683b6-131">System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname</span><span class="sxs-lookup"><span data-stu-id="683b6-131">System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname</span></span>](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0)

[<span data-ttu-id="683b6-132">System.IDisposable</span><span class="sxs-lookup"><span data-stu-id="683b6-132">System.IDisposable</span></span>](/dotnet/api/System.IDisposable)

[<span data-ttu-id="683b6-133">Windows PowerShell Shell SDK</span><span class="sxs-lookup"><span data-stu-id="683b6-133">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
