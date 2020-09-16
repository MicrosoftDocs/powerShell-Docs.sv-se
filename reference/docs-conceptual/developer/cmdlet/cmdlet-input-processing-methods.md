---
title: Metoder för bearbetning av cmdlet-indata | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- virtual methods (PowerShell SDK]
ms.openlocfilehash: e69c5a366b2d74ddd92c844bda0b1e3a65539c10
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784460"
---
# <a name="cmdlet-input-processing-methods"></a><span data-ttu-id="9ca9c-102">Bearbetningsmetoder för cmdlet-indata</span><span class="sxs-lookup"><span data-stu-id="9ca9c-102">Cmdlet Input Processing Methods</span></span>

<span data-ttu-id="9ca9c-103">Cmdletar måste åsidosätta en eller flera av de metoder för bearbetning av indata som beskrivs i det här avsnittet för att utföra sitt arbete.</span><span class="sxs-lookup"><span data-stu-id="9ca9c-103">Cmdlets must override one or more of the input processing methods described in this topic to perform their work.</span></span>
<span data-ttu-id="9ca9c-104">Dessa metoder tillåter att cmdleten utför åtgärder för för bearbetning, bearbetning av indata och efter bearbetning.</span><span class="sxs-lookup"><span data-stu-id="9ca9c-104">These methods allow the cmdlet to perform operations of pre-processing, input processing, and post-processing.</span></span>
<span data-ttu-id="9ca9c-105">Med dessa metoder kan du även stoppa cmdlet-bearbetning.</span><span class="sxs-lookup"><span data-stu-id="9ca9c-105">These methods also allow you to stop cmdlet processing.</span></span>
<span data-ttu-id="9ca9c-106">Ett mer detaljerat exempel på hur du använder dessa metoder finns i [självstudier om SelectStr](selectstr-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="9ca9c-106">For a more detailed example of how to use these methods, see [SelectStr Tutorial](selectstr-tutorial.md).</span></span>

## <a name="pre-processing-operations"></a><span data-ttu-id="9ca9c-107">För bearbetnings åtgärder</span><span class="sxs-lookup"><span data-stu-id="9ca9c-107">Pre-Processing Operations</span></span>

<span data-ttu-id="9ca9c-108">-Cmdletar ska åsidosätta metoden [system. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) för att lägga till eventuella för bearbetnings åtgärder som är giltiga för alla poster som ska bearbetas senare av cmdleten.</span><span class="sxs-lookup"><span data-stu-id="9ca9c-108">Cmdlets should override the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method to add any preprocessing operations that are valid for all the records that will be processed later by the cmdlet.</span></span>
<span data-ttu-id="9ca9c-109">När PowerShell bearbetar en kommando pipeline anropar PowerShell denna metod en gång för varje instans av cmdlet: en i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="9ca9c-109">When PowerShell processes a command pipeline, PowerShell calls this method once for each instance of the cmdlet in the pipeline.</span></span>
<span data-ttu-id="9ca9c-110">Mer information om hur PowerShell anropar kommando pipelinen finns i [cmdlet bearbetning livs cykel](/previous-versions/ms714429(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="9ca9c-110">For more information about how PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](/previous-versions/ms714429(v=vs.85)).</span></span>

<span data-ttu-id="9ca9c-111">Följande kod visar en implementering av BeginProcessing-metoden.</span><span class="sxs-lookup"><span data-stu-id="9ca9c-111">The following code shows an implementation of the BeginProcessing method.</span></span>

```csharp
protected override void BeginProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the BeginProcessing template.");
}
```

## <a name="input-processing-operations"></a><span data-ttu-id="9ca9c-112">Åtgärder för bearbetning av aktiviteter</span><span class="sxs-lookup"><span data-stu-id="9ca9c-112">Input Processing Operations</span></span>

<span data-ttu-id="9ca9c-113">-Cmdletar kan åsidosätta metoden [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) för att bearbeta InInformationen som skickas till cmdleten.</span><span class="sxs-lookup"><span data-stu-id="9ca9c-113">Cmdlets can override the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to process the input that is sent to the cmdlet.</span></span>
<span data-ttu-id="9ca9c-114">När PowerShell bearbetar en kommando pipeline anropar PowerShell den här metoden för varje indatamängd som bearbetas av cmdleten.</span><span class="sxs-lookup"><span data-stu-id="9ca9c-114">When PowerShell processes a command pipeline, PowerShell calls this method for each input record that is processed by the cmdlet.</span></span>
<span data-ttu-id="9ca9c-115">Mer information om hur PowerShell anropar kommando pipelinen finns i [cmdlet bearbetning livs cykel](/previous-versions/ms714429(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="9ca9c-115">For more information about how PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](/previous-versions/ms714429(v=vs.85)).</span></span>

<span data-ttu-id="9ca9c-116">Följande kod visar en implementering av ProcessRecord-metoden.</span><span class="sxs-lookup"><span data-stu-id="9ca9c-116">The following code shows an implementation of the ProcessRecord method.</span></span>

```csharp
protected override void ProcessRecord()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the ProcessRecord template.");
}
```

## <a name="post-processing-operations"></a><span data-ttu-id="9ca9c-117">Efter bearbetnings åtgärder</span><span class="sxs-lookup"><span data-stu-id="9ca9c-117">Post-Processing Operations</span></span>

<span data-ttu-id="9ca9c-118">Cmdletar ska åsidosätta metoden [system. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) för att lägga till eventuella efter bearbetnings åtgärder som är giltiga för alla poster som bearbetats av cmdleten.</span><span class="sxs-lookup"><span data-stu-id="9ca9c-118">Cmdlets should override the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method to add any post-processing operations that are valid for all the records that were processed by the cmdlet.</span></span>
<span data-ttu-id="9ca9c-119">Din cmdlet kan till exempel behöva rensa objektvariabler när den har bearbetats.</span><span class="sxs-lookup"><span data-stu-id="9ca9c-119">For example, your cmdlet might have to clean up object variables after it is finished processing.</span></span>

<span data-ttu-id="9ca9c-120">När PowerShell bearbetar en kommando pipeline anropar PowerShell denna metod en gång för varje instans av cmdlet: en i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="9ca9c-120">When PowerShell processes a command pipeline, PowerShell calls this method once for each instance of the cmdlet in the pipeline.</span></span>
<span data-ttu-id="9ca9c-121">Det är dock viktigt att komma ihåg att PowerShell-körningen inte anropar EndProcessing-metoden om cmdleten avbryts halvvägs genom indata-bearbetningen eller om ett avslutande fel inträffar i någon del av cmdleten.</span><span class="sxs-lookup"><span data-stu-id="9ca9c-121">However, it is important to remember that the PowerShell runtime will not call the EndProcessing method if the cmdlet is canceled midway through its input processing or if a terminating error occurs in any part of the cmdlet.</span></span>
<span data-ttu-id="9ca9c-122">Därför bör en cmdlet som kräver rensning av objekt implementera hela [system. IDisposable](/dotnet/api/System.IDisposable) -mönstret, inklusive en slutförd, så att körningen kan anropa både EndProcessing-och [system. IDisposable. Dispose](/dotnet/api/System.IDisposable.Dispose) -metoderna i slutet av bearbetningen.</span><span class="sxs-lookup"><span data-stu-id="9ca9c-122">For this reason, a cmdlet that requires object cleanup should implement the complete [System.IDisposable](/dotnet/api/System.IDisposable) pattern, including a finalizer, so that the runtime can call both the EndProcessing and [System.IDisposable.Dispose](/dotnet/api/System.IDisposable.Dispose) methods at the end of processing.</span></span>
<span data-ttu-id="9ca9c-123">Mer information om hur PowerShell anropar kommando pipelinen finns i [cmdlet bearbetning livs cykel](/previous-versions/ms714429(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="9ca9c-123">For more information about how PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](/previous-versions/ms714429(v=vs.85)).</span></span>

<span data-ttu-id="9ca9c-124">Följande kod visar en implementering av metoden EndProcessing.</span><span class="sxs-lookup"><span data-stu-id="9ca9c-124">The following code shows an implementation of the EndProcessing method.</span></span>

```csharp
protected override void EndProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the EndProcessing template.");
}
```

## <a name="see-also"></a><span data-ttu-id="9ca9c-125">Se även</span><span class="sxs-lookup"><span data-stu-id="9ca9c-125">See Also</span></span>

[<span data-ttu-id="9ca9c-126">System. Management. Automation. cmdlet. BeginProcessing</span><span class="sxs-lookup"><span data-stu-id="9ca9c-126">System.Management.Automation.Cmdlet.BeginProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[<span data-ttu-id="9ca9c-127">System. Management. Automation. cmdlet. ProcessRecord</span><span class="sxs-lookup"><span data-stu-id="9ca9c-127">System.Management.Automation.Cmdlet.ProcessRecord</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="9ca9c-128">System. Management. Automation. cmdlet. EndProcessing</span><span class="sxs-lookup"><span data-stu-id="9ca9c-128">System.Management.Automation.Cmdlet.EndProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[<span data-ttu-id="9ca9c-129">Självstudie om SelectStr</span><span class="sxs-lookup"><span data-stu-id="9ca9c-129">SelectStr Tutorial</span></span>](selectstr-tutorial.md)

[<span data-ttu-id="9ca9c-130">System. IDisposable</span><span class="sxs-lookup"><span data-stu-id="9ca9c-130">System.IDisposable</span></span>](/dotnet/api/System.IDisposable)

[<span data-ttu-id="9ca9c-131">Windows PowerShell Shell SDK</span><span class="sxs-lookup"><span data-stu-id="9ca9c-131">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
