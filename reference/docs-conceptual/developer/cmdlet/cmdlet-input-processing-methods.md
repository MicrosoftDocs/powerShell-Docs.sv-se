---
ms.date: 09/13/2016
ms.topic: reference
title: Bearbetningsmetoder för cmdlet-indata
description: Bearbetningsmetoder för cmdlet-indata
ms.openlocfilehash: e1a7b58517d6285250edbf16d14810388c242218
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92653388"
---
# <a name="cmdlet-input-processing-methods"></a><span data-ttu-id="ef4d1-103">Bearbetningsmetoder för cmdlet-indata</span><span class="sxs-lookup"><span data-stu-id="ef4d1-103">Cmdlet Input Processing Methods</span></span>

<span data-ttu-id="ef4d1-104">Cmdletar måste åsidosätta en eller flera av de metoder för bearbetning av indata som beskrivs i det här avsnittet för att utföra sitt arbete.</span><span class="sxs-lookup"><span data-stu-id="ef4d1-104">Cmdlets must override one or more of the input processing methods described in this topic to perform their work.</span></span>
<span data-ttu-id="ef4d1-105">Dessa metoder tillåter att cmdleten utför åtgärder för för bearbetning, bearbetning av indata och efter bearbetning.</span><span class="sxs-lookup"><span data-stu-id="ef4d1-105">These methods allow the cmdlet to perform operations of pre-processing, input processing, and post-processing.</span></span>
<span data-ttu-id="ef4d1-106">Med dessa metoder kan du även stoppa cmdlet-bearbetning.</span><span class="sxs-lookup"><span data-stu-id="ef4d1-106">These methods also allow you to stop cmdlet processing.</span></span>
<span data-ttu-id="ef4d1-107">Ett mer detaljerat exempel på hur du använder dessa metoder finns i [självstudier om SelectStr](selectstr-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="ef4d1-107">For a more detailed example of how to use these methods, see [SelectStr Tutorial](selectstr-tutorial.md).</span></span>

## <a name="pre-processing-operations"></a><span data-ttu-id="ef4d1-108">För bearbetnings åtgärder</span><span class="sxs-lookup"><span data-stu-id="ef4d1-108">Pre-Processing Operations</span></span>

<span data-ttu-id="ef4d1-109">-Cmdletar ska åsidosätta metoden [system. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) för att lägga till eventuella för bearbetnings åtgärder som är giltiga för alla poster som ska bearbetas senare av cmdleten.</span><span class="sxs-lookup"><span data-stu-id="ef4d1-109">Cmdlets should override the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method to add any preprocessing operations that are valid for all the records that will be processed later by the cmdlet.</span></span>
<span data-ttu-id="ef4d1-110">När PowerShell bearbetar en kommando pipeline anropar PowerShell denna metod en gång för varje instans av cmdlet: en i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="ef4d1-110">When PowerShell processes a command pipeline, PowerShell calls this method once for each instance of the cmdlet in the pipeline.</span></span>
<span data-ttu-id="ef4d1-111">Mer information om hur PowerShell anropar kommando pipelinen finns i [cmdlet bearbetning livs cykel](/previous-versions/ms714429(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="ef4d1-111">For more information about how PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](/previous-versions/ms714429(v=vs.85)).</span></span>

<span data-ttu-id="ef4d1-112">Följande kod visar en implementering av BeginProcessing-metoden.</span><span class="sxs-lookup"><span data-stu-id="ef4d1-112">The following code shows an implementation of the BeginProcessing method.</span></span>

```csharp
protected override void BeginProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the BeginProcessing template.");
}
```

## <a name="input-processing-operations"></a><span data-ttu-id="ef4d1-113">Åtgärder för bearbetning av aktiviteter</span><span class="sxs-lookup"><span data-stu-id="ef4d1-113">Input Processing Operations</span></span>

<span data-ttu-id="ef4d1-114">-Cmdletar kan åsidosätta metoden [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) för att bearbeta InInformationen som skickas till cmdleten.</span><span class="sxs-lookup"><span data-stu-id="ef4d1-114">Cmdlets can override the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to process the input that is sent to the cmdlet.</span></span>
<span data-ttu-id="ef4d1-115">När PowerShell bearbetar en kommando pipeline anropar PowerShell den här metoden för varje indatamängd som bearbetas av cmdleten.</span><span class="sxs-lookup"><span data-stu-id="ef4d1-115">When PowerShell processes a command pipeline, PowerShell calls this method for each input record that is processed by the cmdlet.</span></span>
<span data-ttu-id="ef4d1-116">Mer information om hur PowerShell anropar kommando pipelinen finns i [cmdlet bearbetning livs cykel](/previous-versions/ms714429(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="ef4d1-116">For more information about how PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](/previous-versions/ms714429(v=vs.85)).</span></span>

<span data-ttu-id="ef4d1-117">Följande kod visar en implementering av ProcessRecord-metoden.</span><span class="sxs-lookup"><span data-stu-id="ef4d1-117">The following code shows an implementation of the ProcessRecord method.</span></span>

```csharp
protected override void ProcessRecord()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the ProcessRecord template.");
}
```

## <a name="post-processing-operations"></a><span data-ttu-id="ef4d1-118">Efter bearbetnings åtgärder</span><span class="sxs-lookup"><span data-stu-id="ef4d1-118">Post-Processing Operations</span></span>

<span data-ttu-id="ef4d1-119">Cmdletar ska åsidosätta metoden [system. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) för att lägga till eventuella efter bearbetnings åtgärder som är giltiga för alla poster som bearbetats av cmdleten.</span><span class="sxs-lookup"><span data-stu-id="ef4d1-119">Cmdlets should override the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method to add any post-processing operations that are valid for all the records that were processed by the cmdlet.</span></span>
<span data-ttu-id="ef4d1-120">Din cmdlet kan till exempel behöva rensa objektvariabler när den har bearbetats.</span><span class="sxs-lookup"><span data-stu-id="ef4d1-120">For example, your cmdlet might have to clean up object variables after it is finished processing.</span></span>

<span data-ttu-id="ef4d1-121">När PowerShell bearbetar en kommando pipeline anropar PowerShell denna metod en gång för varje instans av cmdlet: en i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="ef4d1-121">When PowerShell processes a command pipeline, PowerShell calls this method once for each instance of the cmdlet in the pipeline.</span></span>
<span data-ttu-id="ef4d1-122">Det är dock viktigt att komma ihåg att PowerShell-körningen inte anropar EndProcessing-metoden om cmdleten avbryts halvvägs genom indata-bearbetningen eller om ett avslutande fel inträffar i någon del av cmdleten.</span><span class="sxs-lookup"><span data-stu-id="ef4d1-122">However, it is important to remember that the PowerShell runtime will not call the EndProcessing method if the cmdlet is canceled midway through its input processing or if a terminating error occurs in any part of the cmdlet.</span></span>
<span data-ttu-id="ef4d1-123">Därför bör en cmdlet som kräver rensning av objekt implementera hela [system. IDisposable](/dotnet/api/System.IDisposable) -mönstret, inklusive en slutförd, så att körningen kan anropa både EndProcessing-och [system. IDisposable. Dispose](/dotnet/api/System.IDisposable.Dispose) -metoderna i slutet av bearbetningen.</span><span class="sxs-lookup"><span data-stu-id="ef4d1-123">For this reason, a cmdlet that requires object cleanup should implement the complete [System.IDisposable](/dotnet/api/System.IDisposable) pattern, including a finalizer, so that the runtime can call both the EndProcessing and [System.IDisposable.Dispose](/dotnet/api/System.IDisposable.Dispose) methods at the end of processing.</span></span>
<span data-ttu-id="ef4d1-124">Mer information om hur PowerShell anropar kommando pipelinen finns i [cmdlet bearbetning livs cykel](/previous-versions/ms714429(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="ef4d1-124">For more information about how PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](/previous-versions/ms714429(v=vs.85)).</span></span>

<span data-ttu-id="ef4d1-125">Följande kod visar en implementering av metoden EndProcessing.</span><span class="sxs-lookup"><span data-stu-id="ef4d1-125">The following code shows an implementation of the EndProcessing method.</span></span>

```csharp
protected override void EndProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the EndProcessing template.");
}
```

## <a name="see-also"></a><span data-ttu-id="ef4d1-126">Se även</span><span class="sxs-lookup"><span data-stu-id="ef4d1-126">See Also</span></span>

[<span data-ttu-id="ef4d1-127">System. Management. Automation. cmdlet. BeginProcessing</span><span class="sxs-lookup"><span data-stu-id="ef4d1-127">System.Management.Automation.Cmdlet.BeginProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[<span data-ttu-id="ef4d1-128">System. Management. Automation. cmdlet. ProcessRecord</span><span class="sxs-lookup"><span data-stu-id="ef4d1-128">System.Management.Automation.Cmdlet.ProcessRecord</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="ef4d1-129">System. Management. Automation. cmdlet. EndProcessing</span><span class="sxs-lookup"><span data-stu-id="ef4d1-129">System.Management.Automation.Cmdlet.EndProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[<span data-ttu-id="ef4d1-130">Självstudie om SelectStr</span><span class="sxs-lookup"><span data-stu-id="ef4d1-130">SelectStr Tutorial</span></span>](selectstr-tutorial.md)

[<span data-ttu-id="ef4d1-131">System. IDisposable</span><span class="sxs-lookup"><span data-stu-id="ef4d1-131">System.IDisposable</span></span>](/dotnet/api/System.IDisposable)

[<span data-ttu-id="ef4d1-132">Windows PowerShell Shell SDK</span><span class="sxs-lookup"><span data-stu-id="ef4d1-132">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
