---
title: Skriva ett Windows PowerShell snapin-modulen | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- snap-ins [PowerShell SDK], PSSnapin example
ms.assetid: 875024f4-e02b-4416-80b9-af5e5b50aad6
caps.latest.revision: 7
ms.openlocfilehash: 0c99f4bcfe5e2d34d31714dc85a53b5e8abe0925
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066965"
---
# <a name="writing-a-windows-powershell-snap-in"></a><span data-ttu-id="189c2-102">Skriva en Windows PowerShell-snapin-modul</span><span class="sxs-lookup"><span data-stu-id="189c2-102">Writing a Windows PowerShell Snap-in</span></span>

<span data-ttu-id="189c2-103">Det här exemplet visar hur du skriver en Windows PowerShell-snapin-modul som kan användas för att registrera alla cmdletar och providers för Windows PowerShell i en sammansättning.</span><span class="sxs-lookup"><span data-stu-id="189c2-103">This example shows how to write a Windows PowerShell snap-in that can be used to register all the cmdlets and Windows PowerShell providers in an assembly.</span></span>

<span data-ttu-id="189c2-104">Med den här typen av snapin-modulen kan väljer du inte vilka cmdlets och providers som du vill registrera.</span><span class="sxs-lookup"><span data-stu-id="189c2-104">With this type of snap-in, you do not select which cmdlets and providers you want to register.</span></span> <span data-ttu-id="189c2-105">Om du vill skriva en snapin-modul som kan du välja vad är registrerad, se [skriva en anpassad Windows PowerShell snapin-modul](./writing-a-custom-windows-powershell-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="189c2-105">To write a snap-in that allows you to select what is registered, see [Writing a Custom Windows PowerShell Snap-in](./writing-a-custom-windows-powershell-snap-in.md).</span></span>

### <a name="writing-a-windows-powershell-snap-in"></a><span data-ttu-id="189c2-106">Skriva en Windows PowerShell-snapin-modul</span><span class="sxs-lookup"><span data-stu-id="189c2-106">Writing a Windows PowerShell Snap-in</span></span>

1. <span data-ttu-id="189c2-107">Lägg till attributet RunInstallerAttribute.</span><span class="sxs-lookup"><span data-stu-id="189c2-107">Add the RunInstallerAttribute attribute.</span></span>

2. <span data-ttu-id="189c2-108">Skapa en offentlig klass som härleds från den [System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) klass.</span><span class="sxs-lookup"><span data-stu-id="189c2-108">Create a public class that derives from the [System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) class.</span></span>

    <span data-ttu-id="189c2-109">I det här exemplet är namnet på klassen ”GetProcPSSnapIn01”.</span><span class="sxs-lookup"><span data-stu-id="189c2-109">In this example, the class name is "GetProcPSSnapIn01".</span></span>

3. <span data-ttu-id="189c2-110">Lägg till en offentlig egenskap för namnet på snapin-modulen (krävs).</span><span class="sxs-lookup"><span data-stu-id="189c2-110">Add a public property for the name of the snap-in (required).</span></span> <span data-ttu-id="189c2-111">När du namnger snapin-moduler, inte använda någon av följande tecken: #.</span><span class="sxs-lookup"><span data-stu-id="189c2-111">When naming snap-ins, do not use any of the following characters: # .</span></span> <span data-ttu-id="189c2-112">, ( ) { } [ ] & - /\ $ ; : " ' \< > ; ?</span><span class="sxs-lookup"><span data-stu-id="189c2-112">, ( ) { } [ ] & - /\ $ ; : " ' \< > ; ?</span></span> <span data-ttu-id="189c2-113">@ \` \*</span><span class="sxs-lookup"><span data-stu-id="189c2-113">@ \` \*</span></span>

    <span data-ttu-id="189c2-114">I det här exemplet är namnet på snapin-modulen ”GetProcPSSnapIn01”.</span><span class="sxs-lookup"><span data-stu-id="189c2-114">In this example, the name of the snap-in is "GetProcPSSnapIn01".</span></span>

4. <span data-ttu-id="189c2-115">Lägga till en offentlig egenskap för leverantören av snapin-modulen (krävs).</span><span class="sxs-lookup"><span data-stu-id="189c2-115">Add a public property for the vendor of the snap-in (required).</span></span>

    <span data-ttu-id="189c2-116">I det här exemplet är leverantören ”Microsoft”.</span><span class="sxs-lookup"><span data-stu-id="189c2-116">In this example, the vendor is "Microsoft".</span></span>

5. <span data-ttu-id="189c2-117">Lägg till en offentlig egenskap för resursen leverantör av snapin-modulen (valfritt).</span><span class="sxs-lookup"><span data-stu-id="189c2-117">Add a public property for the vendor resource of the snap-in (optional).</span></span>

    <span data-ttu-id="189c2-118">Leverantörsresurs-är ”GetProcPSSnapIn01 Microsoft” i det här exemplet.</span><span class="sxs-lookup"><span data-stu-id="189c2-118">In this example, the vendor resource is "GetProcPSSnapIn01,Microsoft".</span></span>

6. <span data-ttu-id="189c2-119">Lägg till en offentlig egenskap för beskrivning av snapin-modulen (krävs).</span><span class="sxs-lookup"><span data-stu-id="189c2-119">Add a public property for the description of the snap-in (required).</span></span>

    <span data-ttu-id="189c2-120">Beskrivningen är ”detta är en Windows PowerShell-snapin-modul som registrerar cmdleten get-proc” i det här exemplet.</span><span class="sxs-lookup"><span data-stu-id="189c2-120">In this example, the description is "This is a Windows PowerShell snap-in that registers the get-proc cmdlet".</span></span>

7. <span data-ttu-id="189c2-121">Lägg till en offentlig egenskap för resursen beskrivning av snapin-modulen (valfritt).</span><span class="sxs-lookup"><span data-stu-id="189c2-121">Add a public property for the description resource of the snap-in (optional).</span></span>

    <span data-ttu-id="189c2-122">Leverantörsresurs-är ”GetProcPSSnapIn01, detta är en Windows PowerShell-snapin-modul som registrerar cmdleten get-proc” i det här exemplet.</span><span class="sxs-lookup"><span data-stu-id="189c2-122">In this example, the vendor resource is "GetProcPSSnapIn01,This is a Windows PowerShell snap-in that registers the get-proc cmdlet".</span></span>

## <a name="example"></a><span data-ttu-id="189c2-123">Exempel</span><span class="sxs-lookup"><span data-stu-id="189c2-123">Example</span></span>

<span data-ttu-id="189c2-124">Det här exemplet visar hur du skriver en Windows PowerShell-snapin-modul som kan användas för att registrera cmdleten Get-processen i Windows PowerShell-gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="189c2-124">This example shows how to write a Windows PowerShell snap-in that can be used to register the Get-Proc cmdlet in the Windows PowerShell shell.</span></span> <span data-ttu-id="189c2-125">Tänk på att i det här exemplet fullständig sammansättningen innehåller endast GetProcPSSnapIn01 snapin-modulen klassen och klassen cmdlet Get-processen.</span><span class="sxs-lookup"><span data-stu-id="189c2-125">Be aware that in this example, the complete assembly would contain only the GetProcPSSnapIn01 snap-in class and the Get-Proc cmdlet class.</span></span>

```csharp
[RunInstaller(true)]
public class GetProcPSSnapIn01 : PSSnapIn
{
  /// <summary>
  /// Create an instance of the GetProcPSSnapIn01 class.
  /// </summary>
  public GetProcPSSnapIn01()
         : base()
  {
  }

  /// <summary>
  /// Specify the name of the PowerShell snap-in.
  /// </summary>
  public override string Name
  {
    get
    {
      return "GetProcPSSnapIn01";
    }
  }

  /// <summary>
  /// Specify the vendor for the PowerShell snap-in.
  /// </summary>
  public override string Vendor
  {
    get
    {
      return "Microsoft";
    }
  }

  /// <summary>
  /// Specify the localization resource information for the vendor.
  /// Use the format: resourceBaseName,VendorName.
  /// </summary>
  public override string VendorResource
  {
    get
    {
      return "GetProcPSSnapIn01,Microsoft";
    }
  }

  /// <summary>
  /// Specify a description of the PowerShell snap-in.
  /// </summary>
  public override string Description
  {
    get
    {
      return "This is a PowerShell snap-in that includes the get-proc cmdlet.";
    }
  }

  /// <summary>
  /// Specify the localization resource information for the description.
  /// Use the format: resourceBaseName,Description.
  /// </summary>
  public override string DescriptionResource
  {
    get
    {
      return "GetProcPSSnapIn01,This is a PowerShell snap-in that includes the get-proc cmdlet.";
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="189c2-126">Se även</span><span class="sxs-lookup"><span data-stu-id="189c2-126">See Also</span></span>

[<span data-ttu-id="189c2-127">Hur du registrerar Cmdlets, Providers och vara värd för program</span><span class="sxs-lookup"><span data-stu-id="189c2-127">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="189c2-128">Windows PowerShell Shell SDK</span><span class="sxs-lookup"><span data-stu-id="189c2-128">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
