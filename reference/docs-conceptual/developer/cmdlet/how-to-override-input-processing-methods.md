---
ms.date: 09/13/2016
ms.topic: reference
title: Åsidosätta bearbetningsmetoder för indata
description: Åsidosätta bearbetningsmetoder för indata
ms.openlocfilehash: 4e8d71a34a1480ce63435ac6cc5dce60d4219c03
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92667019"
---
# <a name="how-to-override-input-processing-methods"></a><span data-ttu-id="aa74d-103">Åsidosätta bearbetningsmetoder för indata</span><span class="sxs-lookup"><span data-stu-id="aa74d-103">How to Override Input Processing Methods</span></span>

<span data-ttu-id="aa74d-104">I de här exemplen visas hur du skriver över metoderna för bearbetning av indata i en-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="aa74d-104">These examples show how to overwrite the input processing methods within a cmdlet.</span></span> <span data-ttu-id="aa74d-105">Dessa metoder används för att utföra följande åtgärder:</span><span class="sxs-lookup"><span data-stu-id="aa74d-105">These methods are used to perform the following operations:</span></span>

- <span data-ttu-id="aa74d-106">Metoden [system. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) används för att utföra start åtgärder vid en tidpunkt som är giltiga för alla objekt som bearbetas av cmdleten.</span><span class="sxs-lookup"><span data-stu-id="aa74d-106">The [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method is used to perform one-time startup operations that are valid for all the objects processed by the cmdlet.</span></span> <span data-ttu-id="aa74d-107">Windows PowerShell-körningen anropar den här metoden bara en gång.</span><span class="sxs-lookup"><span data-stu-id="aa74d-107">The Windows PowerShell runtime calls this method only once.</span></span>

- <span data-ttu-id="aa74d-108">Metoden [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) används för att bearbeta de objekt som skickas till cmdleten.</span><span class="sxs-lookup"><span data-stu-id="aa74d-108">The [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method is used to process the objects passed to the cmdlet.</span></span> <span data-ttu-id="aa74d-109">Windows PowerShell-körningen anropar den här metoden för varje objekt som skickas till cmdleten.</span><span class="sxs-lookup"><span data-stu-id="aa74d-109">The Windows PowerShell runtime calls this method for each object passed to the cmdlet.</span></span>

- <span data-ttu-id="aa74d-110">Metoden [system. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) används för att utföra bearbetnings åtgärder vid enstaka tidpunkter.</span><span class="sxs-lookup"><span data-stu-id="aa74d-110">The [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method is used to perform one-time post processing operations.</span></span> <span data-ttu-id="aa74d-111">Windows PowerShell-körningen anropar den här metoden bara en gång.</span><span class="sxs-lookup"><span data-stu-id="aa74d-111">The Windows PowerShell runtime calls this method only once.</span></span>

## <a name="to-override-the-beginprocessing-method"></a><span data-ttu-id="aa74d-112">För att åsidosätta metoden BeginProcessing</span><span class="sxs-lookup"><span data-stu-id="aa74d-112">To override the BeginProcessing method</span></span>

- <span data-ttu-id="aa74d-113">Deklarera en skyddad åsidosättning av metoden [system. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) .</span><span class="sxs-lookup"><span data-stu-id="aa74d-113">Declare a protected override of the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method.</span></span>

<span data-ttu-id="aa74d-114">Följande klass skriver ut ett exempel meddelande.</span><span class="sxs-lookup"><span data-stu-id="aa74d-114">The following class prints a sample message.</span></span> <span data-ttu-id="aa74d-115">Om du vill använda den här klassen ändrar du verbet och Substantiv i cmdlet-attributet, ändrar namnet på klassen så att det visar det nya verbet och Substantiv och lägger sedan till de funktioner du behöver för att åsidosätta metoden [system. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) .</span><span class="sxs-lookup"><span data-stu-id="aa74d-115">To use this class, change the verb and noun in the Cmdlet attribute, change the name of the class to reflect the new verb and noun, and then add the functionality you require to the override of the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method.</span></span>

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

## <a name="to-override-the-processrecord-method"></a><span data-ttu-id="aa74d-116">För att åsidosätta metoden ProcessRecord</span><span class="sxs-lookup"><span data-stu-id="aa74d-116">To override the ProcessRecord method</span></span>

- <span data-ttu-id="aa74d-117">Deklarera en skyddad åsidosättning av metoden [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) .</span><span class="sxs-lookup"><span data-stu-id="aa74d-117">Declare a protected override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

<span data-ttu-id="aa74d-118">Följande klass skriver ut ett exempel meddelande.</span><span class="sxs-lookup"><span data-stu-id="aa74d-118">The following class prints a sample message.</span></span> <span data-ttu-id="aa74d-119">Om du vill använda den här klassen ändrar du verbet och Substantiv i cmdlet-attributet, ändrar namnet på klassen så att det visar det nya verbet och Substantiv och lägger sedan till de funktioner du behöver för att åsidosätta metoden [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) .</span><span class="sxs-lookup"><span data-stu-id="aa74d-119">To use this class, change the verb and noun in the Cmdlet attribute, change the name of the class to reflect the new verb and noun, and then add the functionality you require to the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

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

## <a name="to-override-the-endprocessing-method"></a><span data-ttu-id="aa74d-120">Åsidosätta EndProcessing-metoden</span><span class="sxs-lookup"><span data-stu-id="aa74d-120">To override the EndProcessing method</span></span>

- <span data-ttu-id="aa74d-121">Deklarera en skyddad åsidosättning av metoden [system. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) .</span><span class="sxs-lookup"><span data-stu-id="aa74d-121">Declare a protected override of the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span>

<span data-ttu-id="aa74d-122">Följande klass skriver ut ett exempel.</span><span class="sxs-lookup"><span data-stu-id="aa74d-122">The following class prints a sample.</span></span> <span data-ttu-id="aa74d-123">Om du vill använda den här klassen ändrar du verbet och Substantiv i cmdlet-attributet, ändrar namnet på klassen så att det visar det nya verbet och Substantiv och lägger sedan till de funktioner du behöver för att åsidosätta metoden [system. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) .</span><span class="sxs-lookup"><span data-stu-id="aa74d-123">To use this class, change the verb and noun in the Cmdlet attribute, change the name of the class to reflect the new verb and noun, and then add the functionality you require to the override of the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="aa74d-124">Se även</span><span class="sxs-lookup"><span data-stu-id="aa74d-124">See Also</span></span>

[<span data-ttu-id="aa74d-125">System. Management. Automation. cmdlet. BeginProcessing</span><span class="sxs-lookup"><span data-stu-id="aa74d-125">System.Management.Automation.Cmdlet.BeginProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[<span data-ttu-id="aa74d-126">System. Management. Automation. cmdlet. EndProcessing</span><span class="sxs-lookup"><span data-stu-id="aa74d-126">System.Management.Automation.Cmdlet.EndProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[<span data-ttu-id="aa74d-127">System. Management. Automation. cmdlet. ProcessRecord</span><span class="sxs-lookup"><span data-stu-id="aa74d-127">System.Management.Automation.Cmdlet.ProcessRecord</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="aa74d-128">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="aa74d-128">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
