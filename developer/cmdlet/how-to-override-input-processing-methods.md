---
title: Åsidosätta indata metoderna | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1a1ad921-5816-4937-acf1-ed4760fae740
caps.latest.revision: 8
ms.openlocfilehash: cfee55576518cf9ce38501192872ce94054f5213
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056404"
---
# <a name="how-to-override-input-processing-methods"></a><span data-ttu-id="4234b-102">Åsidosätta bearbetningsmetoder för indata</span><span class="sxs-lookup"><span data-stu-id="4234b-102">How to Override Input Processing Methods</span></span>

<span data-ttu-id="4234b-103">De här exemplen visar hur du skriva över den inkommande metoderna i en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4234b-103">These examples show how to overwrite the input processing methods within a cmdlet.</span></span> <span data-ttu-id="4234b-104">Dessa metoder används för att utföra följande åtgärder:</span><span class="sxs-lookup"><span data-stu-id="4234b-104">These methods are used to perform the following operations:</span></span>

- <span data-ttu-id="4234b-105">Den [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) metod för att utföra en start-åtgärder som gäller för alla objekt som bearbetas av cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="4234b-105">The [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method is used to perform one-time startup operations that are valid for all the objects processed by the cmdlet.</span></span> <span data-ttu-id="4234b-106">Windows PowerShell-runtime anropar den här metoden bara en gång.</span><span class="sxs-lookup"><span data-stu-id="4234b-106">The Windows PowerShell runtime calls this method only once.</span></span>

- <span data-ttu-id="4234b-107">Den [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metod för att bearbeta objekt som överförs till cmdleten.</span><span class="sxs-lookup"><span data-stu-id="4234b-107">The [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method is used to process the objects passed to the cmdlet.</span></span> <span data-ttu-id="4234b-108">Windows PowerShell-runtime anropar den här metoden för varje objekt som skickas till cmdleten.</span><span class="sxs-lookup"><span data-stu-id="4234b-108">The Windows PowerShell runtime calls this method for each object passed to the cmdlet.</span></span>

- <span data-ttu-id="4234b-109">Den [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) metod för att utföra åtgärder för bearbetning av enstaka inlägget.</span><span class="sxs-lookup"><span data-stu-id="4234b-109">The [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method is used to perform one-time post processing operations.</span></span> <span data-ttu-id="4234b-110">Windows PowerShell-runtime anropar den här metoden bara en gång.</span><span class="sxs-lookup"><span data-stu-id="4234b-110">The Windows PowerShell runtime calls this method only once.</span></span>

## <a name="to-override-the-beginprocessing-method"></a><span data-ttu-id="4234b-111">Åsidosätta metoden BeginProcessing</span><span class="sxs-lookup"><span data-stu-id="4234b-111">To override the BeginProcessing method</span></span>

- <span data-ttu-id="4234b-112">Deklarera en skyddad åsidosättning av den [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) metod.</span><span class="sxs-lookup"><span data-stu-id="4234b-112">Declare a protected override of the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method.</span></span>

<span data-ttu-id="4234b-113">Följande klass skriver ett exempelmeddelande.</span><span class="sxs-lookup"><span data-stu-id="4234b-113">The following class prints a sample message.</span></span> <span data-ttu-id="4234b-114">Om du vill använda den här klassen ändra verb och substantiv i Cmdlet-attribut, ändra namnet på klassen för att återspegla den nya verb och substantiv och Lägg sedan till vilka funktioner du behöver du åsidosättandet av den [System.Management.Automation.Cmdlet.BeginProcessing ](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) metod.</span><span class="sxs-lookup"><span data-stu-id="4234b-114">To use this class, change the verb and noun in the Cmdlet attribute, change the name of the class to reflect the new verb and noun, and then add the functionality you require to the override of the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method.</span></span>

```csharp
[Cmdlet(VerbsDiagnostic.Test, "BeginProcessingClass")]
public class TestBeginProcessingClassTemplate : Cmdlet
{
  // Override the BeginProcessing method to add preprocessing
  //operations to the cmdlet.
  protected override void BeginProcessing()
  {
    // Replace the WriteObject method with the logic required
    // by your cmdlet. It is used here to generate the following
    // output:
    // "This is a test of the BeginProcessing template."
    WriteObject("This is a test of the BeginProcessing template.");
  }
}
```

## <a name="to-override-the-processrecord-method"></a><span data-ttu-id="4234b-115">Åsidosätta metoden ProcessRecord</span><span class="sxs-lookup"><span data-stu-id="4234b-115">To override the ProcessRecord method</span></span>

- <span data-ttu-id="4234b-116">Deklarera en skyddad åsidosättning av den [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metod.</span><span class="sxs-lookup"><span data-stu-id="4234b-116">Declare a protected override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

<span data-ttu-id="4234b-117">Följande klass skriver ett exempelmeddelande.</span><span class="sxs-lookup"><span data-stu-id="4234b-117">The following class prints a sample message.</span></span> <span data-ttu-id="4234b-118">Om du vill använda den här klassen ändra verb och substantiv i Cmdlet-attribut, ändra namnet på klassen för att återspegla den nya verb och substantiv och Lägg sedan till vilka funktioner du behöver du åsidosättandet av den [System.Management.Automation.Cmdlet.ProcessRecord ](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metod.</span><span class="sxs-lookup"><span data-stu-id="4234b-118">To use this class, change the verb and noun in the Cmdlet attribute, change the name of the class to reflect the new verb and noun, and then add the functionality you require to the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

```csharp
[Cmdlet(VerbsDiagnostic.Test, "ProcessRecordClass")]
public class TestProcessRecordClassTemplate : Cmdlet
{
    // Override the ProcessRecord method to add processing
    //operations to the cmdlet.
    protected override void ProcessRecord()
    {
        // Replace the WriteObject method with the logic required
        // by your cmdlet. It is used here to generate the following
        // output:
        // "This is a test of the ProcessRecord template."
        WriteObject("This is a test of the ProcessRecord template.");
    }
}

```

## <a name="to-override-the-endprocessing-method"></a><span data-ttu-id="4234b-119">Åsidosätta metoden EndProcessing</span><span class="sxs-lookup"><span data-stu-id="4234b-119">To override the EndProcessing method</span></span>

- <span data-ttu-id="4234b-120">Deklarera en skyddad åsidosättning av den [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) metod.</span><span class="sxs-lookup"><span data-stu-id="4234b-120">Declare a protected override of the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span>

<span data-ttu-id="4234b-121">Följande klass skriver ett exempel.</span><span class="sxs-lookup"><span data-stu-id="4234b-121">The following class prints a sample.</span></span> <span data-ttu-id="4234b-122">Om du vill använda den här klassen ändra verb och substantiv i Cmdlet-attribut, ändra namnet på klassen för att återspegla den nya verb och substantiv och Lägg sedan till vilka funktioner du behöver du åsidosättandet av den [System.Management.Automation.Cmdlet.EndProcessing ](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) metod.</span><span class="sxs-lookup"><span data-stu-id="4234b-122">To use this class, change the verb and noun in the Cmdlet attribute, change the name of the class to reflect the new verb and noun, and then add the functionality you require to the override of the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span>

```csharp
[Cmdlet(VerbsDiagnostic.Test, "EndProcessingClass")]
public class TestEndProcessingClassTemplate : Cmdlet
{
  // Override the EndProcessing method to add postprocessing
  //operations to the cmdlet.
  protected override void EndProcessing()
  {
    // Replace the WriteObject method with the logic required
    // by your cmdlet. It is used here to generate the following
    // output:
    // "This is a test of the BeginProcessing template."
    WriteObject("This is a test of the EndProcessing template.");
  }
}
```

## <a name="see-also"></a><span data-ttu-id="4234b-123">Se även</span><span class="sxs-lookup"><span data-stu-id="4234b-123">See Also</span></span>

[<span data-ttu-id="4234b-124">System.Management.Automation.Cmdlet.BeginProcessing</span><span class="sxs-lookup"><span data-stu-id="4234b-124">System.Management.Automation.Cmdlet.BeginProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[<span data-ttu-id="4234b-125">System.Management.Automation.Cmdlet.EndProcessing</span><span class="sxs-lookup"><span data-stu-id="4234b-125">System.Management.Automation.Cmdlet.EndProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[<span data-ttu-id="4234b-126">System.Management.Automation.Cmdlet.ProcessRecord</span><span class="sxs-lookup"><span data-stu-id="4234b-126">System.Management.Automation.Cmdlet.ProcessRecord</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="4234b-127">Skriva en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="4234b-127">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
