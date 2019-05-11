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
ms.openlocfilehash: a28c8d3df19bc72bf338d6abc4e02768c5097209
ms.sourcegitcommit: 00cf9a99972ce40db7c25b9a3fc6152dec6bddb6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/28/2019
ms.locfileid: "64670312"
---
# <a name="cmdlet-input-processing-methods"></a><span data-ttu-id="af4e0-102">Bearbetningsmetoder för cmdlet-indata</span><span class="sxs-lookup"><span data-stu-id="af4e0-102">Cmdlet Input Processing Methods</span></span>

<span data-ttu-id="af4e0-103">Cmdlet: ar måste åsidosätta en eller flera av indata metoderna som beskrivs i det här avsnittet för att utföra sitt arbete.</span><span class="sxs-lookup"><span data-stu-id="af4e0-103">Cmdlets must override one or more of the input processing methods described in this topic to perform their work.</span></span>
<span data-ttu-id="af4e0-104">Dessa metoder kan cmdleten för att utföra åtgärder för förbearbetning, inkommande bearbetning och efterbearbeta.</span><span class="sxs-lookup"><span data-stu-id="af4e0-104">These methods allow the cmdlet to perform operations of pre-processing, input processing, and post-processing.</span></span>
<span data-ttu-id="af4e0-105">Dessa metoder kan du stoppa cmdlet-bearbetning.</span><span class="sxs-lookup"><span data-stu-id="af4e0-105">These methods also allow you to stop cmdlet processing.</span></span>
<span data-ttu-id="af4e0-106">Ett mer detaljerat exempel på hur du använder dessa metoder, se [SelectStr självstudien](selectstr-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="af4e0-106">For a more detailed example of how to use these methods, see [SelectStr Tutorial](selectstr-tutorial.md).</span></span>

## <a name="pre-processing-operations"></a><span data-ttu-id="af4e0-107">Före bearbetnings åtgärder</span><span class="sxs-lookup"><span data-stu-id="af4e0-107">Pre-Processing Operations</span></span>

<span data-ttu-id="af4e0-108">Cmdlet: ar ska åsidosätta den [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) metod för att lägga till alla förbearbetning åtgärder som gäller för alla poster som bearbetas senare av cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="af4e0-108">Cmdlets should override the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method to add any preprocessing operations that are valid for all the records that will be processed later by the cmdlet.</span></span>
<span data-ttu-id="af4e0-109">När PowerShell bearbetar en kommando-pipeline, anropar PowerShell den här metoden en gång för varje instans av cmdlet: en i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="af4e0-109">When PowerShell processes a command pipeline, PowerShell calls this method once for each instance of the cmdlet in the pipeline.</span></span>
<span data-ttu-id="af4e0-110">Mer information om hur PowerShell anropar kommando-pipeline finns i [Cmdlet bearbetar livscykel](/previous-versions/ms714429(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="af4e0-110">For more information about how PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](/previous-versions/ms714429(v=vs.85)).</span></span>

<span data-ttu-id="af4e0-111">Följande kod visar en implementering av metoden BeginProcessing.</span><span class="sxs-lookup"><span data-stu-id="af4e0-111">The following code shows an implementation of the BeginProcessing method.</span></span>

```csharp
protected override void BeginProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the BeginProcessing template.");
}
```

## <a name="input-processing-operations"></a><span data-ttu-id="af4e0-112">Bearbetning av indata</span><span class="sxs-lookup"><span data-stu-id="af4e0-112">Input Processing Operations</span></span>

<span data-ttu-id="af4e0-113">Cmdlet: ar kan åsidosätta den [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metod för att bearbeta indata som ska skickas till cmdleten.</span><span class="sxs-lookup"><span data-stu-id="af4e0-113">Cmdlets can override the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to process the input that is sent to the cmdlet.</span></span>
<span data-ttu-id="af4e0-114">När PowerShell bearbetar en kommando-pipeline, anropar den här metoden för varje inkommande post som bearbetas av cmdlet: en med hjälp av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="af4e0-114">When PowerShell processes a command pipeline, PowerShell calls this method for each input record that is processed by the cmdlet.</span></span>
<span data-ttu-id="af4e0-115">Mer information om hur PowerShell anropar kommando-pipeline finns i [Cmdlet bearbetar livscykel](/previous-versions/ms714429(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="af4e0-115">For more information about how PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](/previous-versions/ms714429(v=vs.85)).</span></span>

<span data-ttu-id="af4e0-116">Följande kod visar en implementering av metoden ProcessRecord.</span><span class="sxs-lookup"><span data-stu-id="af4e0-116">The following code shows an implementation of the ProcessRecord method.</span></span>

```csharp
protected override void ProcessRecord()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the ProcessRecord template.");
}
```

## <a name="post-processing-operations"></a><span data-ttu-id="af4e0-117">Efterbearbetning åtgärder</span><span class="sxs-lookup"><span data-stu-id="af4e0-117">Post-Processing Operations</span></span>

<span data-ttu-id="af4e0-118">Cmdlet: ar ska åsidosätta den [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) metod för att lägga till alla efterbearbetning åtgärder som gäller för alla poster som bearbetats av cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="af4e0-118">Cmdlets should override the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method to add any post-processing operations that are valid for all the records that were processed by the cmdlet.</span></span>
<span data-ttu-id="af4e0-119">Till exempel cmdlet: kan behöva Rensa objektvariabler när den har slutförts bearbetning.</span><span class="sxs-lookup"><span data-stu-id="af4e0-119">For example, your cmdlet might have to clean up object variables after it is finished processing.</span></span>

<span data-ttu-id="af4e0-120">När PowerShell bearbetar en kommando-pipeline, anropar PowerShell den här metoden en gång för varje instans av cmdlet: en i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="af4e0-120">When PowerShell processes a command pipeline, PowerShell calls this method once for each instance of the cmdlet in the pipeline.</span></span>
<span data-ttu-id="af4e0-121">Det är dock viktigt att komma ihåg att PowerShell-runtime inte anropa metoden EndProcessing om cmdleten avbryts mitt via dess inkommande bearbetning eller om ett avslutande fel som inträffar i någon del av cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="af4e0-121">However, it is important to remember that the PowerShell runtime will not call the EndProcessing method if the cmdlet is canceled midway through its input processing or if a terminating error occurs in any part of the cmdlet.</span></span>
<span data-ttu-id="af4e0-122">Därför bör en cmdlet som kräver objektet Rensa implementera hela [System.IDisposable](/dotnet/api/System.IDisposable) mönstret, inklusive en finaliserare så att körningen kan anropa både EndProcessing och [ System.IDisposable.Dispose](/dotnet/api/System.IDisposable.Dispose) metoder i slutet av bearbetning.</span><span class="sxs-lookup"><span data-stu-id="af4e0-122">For this reason, a cmdlet that requires object cleanup should implement the complete [System.IDisposable](/dotnet/api/System.IDisposable) pattern, including a finalizer, so that the runtime can call both the EndProcessing and [System.IDisposable.Dispose](/dotnet/api/System.IDisposable.Dispose) methods at the end of processing.</span></span>
<span data-ttu-id="af4e0-123">Mer information om hur PowerShell anropar kommando-pipeline finns i [Cmdlet bearbetar livscykel](/previous-versions/ms714429(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="af4e0-123">For more information about how PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](/previous-versions/ms714429(v=vs.85)).</span></span>

<span data-ttu-id="af4e0-124">Följande kod visar en implementering av metoden EndProcessing.</span><span class="sxs-lookup"><span data-stu-id="af4e0-124">The following code shows an implementation of the EndProcessing method.</span></span>

```csharp
protected override void EndProcessing()
{
  // Replace the WriteObject method with the logic required by your cmdlet.
  WriteObject("This is a test of the EndProcessing template.");
}
```

## <a name="see-also"></a><span data-ttu-id="af4e0-125">Se även</span><span class="sxs-lookup"><span data-stu-id="af4e0-125">See Also</span></span>

[<span data-ttu-id="af4e0-126">System.Management.Automation.Cmdlet.BeginProcessing</span><span class="sxs-lookup"><span data-stu-id="af4e0-126">System.Management.Automation.Cmdlet.BeginProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[<span data-ttu-id="af4e0-127">System.Management.Automation.Cmdlet.ProcessRecord</span><span class="sxs-lookup"><span data-stu-id="af4e0-127">System.Management.Automation.Cmdlet.ProcessRecord</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="af4e0-128">System.Management.Automation.Cmdlet.EndProcessing</span><span class="sxs-lookup"><span data-stu-id="af4e0-128">System.Management.Automation.Cmdlet.EndProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[<span data-ttu-id="af4e0-129">SelectStr självstudien</span><span class="sxs-lookup"><span data-stu-id="af4e0-129">SelectStr Tutorial</span></span>](selectstr-tutorial.md)

[<span data-ttu-id="af4e0-130">System.IDisposable</span><span class="sxs-lookup"><span data-stu-id="af4e0-130">System.IDisposable</span></span>](/dotnet/api/System.IDisposable)

[<span data-ttu-id="af4e0-131">Windows PowerShell Shell SDK</span><span class="sxs-lookup"><span data-stu-id="af4e0-131">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
