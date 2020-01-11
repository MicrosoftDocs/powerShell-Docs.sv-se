---
title: Skriva en Windows PowerShell-snapin-modul | Microsoft Docs
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
ms.openlocfilehash: d12a66e354a23041fffb0f8fa286c849849ec2b0
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870480"
---
# <a name="writing-a-windows-powershell-snap-in"></a><span data-ttu-id="8deb7-102">Skriva en Windows PowerShell-snapin-modul</span><span class="sxs-lookup"><span data-stu-id="8deb7-102">Writing a Windows PowerShell Snap-in</span></span>

<span data-ttu-id="8deb7-103">Det här exemplet visar hur du skriver en Windows PowerShell-snapin-modul som kan användas för att registrera alla cmdlets och Windows PowerShell-providers i en sammansättning.</span><span class="sxs-lookup"><span data-stu-id="8deb7-103">This example shows how to write a Windows PowerShell snap-in that can be used to register all the cmdlets and Windows PowerShell providers in an assembly.</span></span>

<span data-ttu-id="8deb7-104">Med den här typen av snapin-modul väljer du inte vilka cmdletar och leverantörer du vill registrera.</span><span class="sxs-lookup"><span data-stu-id="8deb7-104">With this type of snap-in, you do not select which cmdlets and providers you want to register.</span></span> <span data-ttu-id="8deb7-105">Om du vill skriva en snapin-modul där du kan välja vad som är registrerat, se [skriva en anpassad Windows PowerShell-snapin-modul](./writing-a-custom-windows-powershell-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="8deb7-105">To write a snap-in that allows you to select what is registered, see [Writing a Custom Windows PowerShell Snap-in](./writing-a-custom-windows-powershell-snap-in.md).</span></span>

### <a name="writing-a-windows-powershell-snap-in"></a><span data-ttu-id="8deb7-106">Skriva en Windows PowerShell-snapin-modul</span><span class="sxs-lookup"><span data-stu-id="8deb7-106">Writing a Windows PowerShell Snap-in</span></span>

1. <span data-ttu-id="8deb7-107">Lägg till attributet RunInstallerAttribute.</span><span class="sxs-lookup"><span data-stu-id="8deb7-107">Add the RunInstallerAttribute attribute.</span></span>

2. <span data-ttu-id="8deb7-108">Skapa en offentlig klass som härleds från klassen [system. Management. Automation. PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) .</span><span class="sxs-lookup"><span data-stu-id="8deb7-108">Create a public class that derives from the [System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) class.</span></span>

    <span data-ttu-id="8deb7-109">I det här exemplet är klass namnet "GetProcPSSnapIn01".</span><span class="sxs-lookup"><span data-stu-id="8deb7-109">In this example, the class name is "GetProcPSSnapIn01".</span></span>

3. <span data-ttu-id="8deb7-110">Lägg till en offentlig egenskap för namnet på snapin-modulen (obligatoriskt).</span><span class="sxs-lookup"><span data-stu-id="8deb7-110">Add a public property for the name of the snap-in (required).</span></span> <span data-ttu-id="8deb7-111">När du namnger snapin-moduler ska du inte använda något av följande tecken: `#`, `.`, `,`, `(`, `)`, `{`, `}`, `[`, `]`, `&`, `-`, `/`, `\`, `$`, `;`, `:`, `"`, `'`, `<`, `>`, `|`, `?`, `@`, `` ` ``, `*`</span><span class="sxs-lookup"><span data-stu-id="8deb7-111">When naming snap-ins, do not use any of the following characters: `#`, `.`, `,`, `(`, `)`, `{`, `}`, `[`, `]`, `&`, `-`, `/`, `\`, `$`, `;`, `:`, `"`, `'`, `<`, `>`, `|`, `?`, `@`, `` ` ``, `*`</span></span>

    <span data-ttu-id="8deb7-112">I det här exemplet är namnet på snapin-modulen "GetProcPSSnapIn01".</span><span class="sxs-lookup"><span data-stu-id="8deb7-112">In this example, the name of the snap-in is "GetProcPSSnapIn01".</span></span>

4. <span data-ttu-id="8deb7-113">Lägg till en offentlig egenskap för leverantören av snapin-modulen (obligatoriskt).</span><span class="sxs-lookup"><span data-stu-id="8deb7-113">Add a public property for the vendor of the snap-in (required).</span></span>

    <span data-ttu-id="8deb7-114">I det här exemplet är leverantören "Microsoft".</span><span class="sxs-lookup"><span data-stu-id="8deb7-114">In this example, the vendor is "Microsoft".</span></span>

5. <span data-ttu-id="8deb7-115">Lägg till en offentlig egenskap för leverantörs resursen för snapin-modulen (valfritt).</span><span class="sxs-lookup"><span data-stu-id="8deb7-115">Add a public property for the vendor resource of the snap-in (optional).</span></span>

    <span data-ttu-id="8deb7-116">I det här exemplet är leverantörs resursen "GetProcPSSnapIn01, Microsoft".</span><span class="sxs-lookup"><span data-stu-id="8deb7-116">In this example, the vendor resource is "GetProcPSSnapIn01,Microsoft".</span></span>

6. <span data-ttu-id="8deb7-117">Lägg till en offentlig egenskap för en beskrivning av snapin-modulen (krävs).</span><span class="sxs-lookup"><span data-stu-id="8deb7-117">Add a public property for the description of the snap-in (required).</span></span>

    <span data-ttu-id="8deb7-118">I det här exemplet är beskrivningen "det här är en Windows PowerShell-snapin-modul som registrerar cmdleten Get-proc".</span><span class="sxs-lookup"><span data-stu-id="8deb7-118">In this example, the description is "This is a Windows PowerShell snap-in that registers the  get-proc cmdlet".</span></span>

7. <span data-ttu-id="8deb7-119">Lägg till en offentlig egenskap för en beskrivnings resurs för snapin-modulen (valfritt).</span><span class="sxs-lookup"><span data-stu-id="8deb7-119">Add a public property for the description resource of the snap-in (optional).</span></span>

    <span data-ttu-id="8deb7-120">I det här exemplet är leverantörs resursen "GetProcPSSnapIn01, det här är en Windows PowerShell-snapin-modul som registrerar cmdleten Get-proc".</span><span class="sxs-lookup"><span data-stu-id="8deb7-120">In this example, the vendor resource is "GetProcPSSnapIn01,This is a Windows PowerShell snap-in  that registers the get-proc cmdlet".</span></span>

## <a name="example"></a><span data-ttu-id="8deb7-121">Exempel</span><span class="sxs-lookup"><span data-stu-id="8deb7-121">Example</span></span>

<span data-ttu-id="8deb7-122">Det här exemplet visar hur du skriver en Windows PowerShell-snapin-modul som kan användas för att registrera cmdleten Get-proc i Windows PowerShell-gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="8deb7-122">This example shows how to write a Windows PowerShell snap-in that can be used to register the Get-Proc cmdlet in the Windows PowerShell shell.</span></span> <span data-ttu-id="8deb7-123">Tänk på att i det här exemplet skulle den kompletta sammansättningen endast innehålla snapin-GetProcPSSnapIn01 och klassen `Get-Proc`-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8deb7-123">Be aware that in this example, the complete assembly would contain only the GetProcPSSnapIn01 snap-in class and the `Get-Proc` cmdlet class.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="8deb7-124">Se även</span><span class="sxs-lookup"><span data-stu-id="8deb7-124">See Also</span></span>

<span data-ttu-id="8deb7-125">[Registrera cmdlets, providers och värd program](/previous-versions/ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="8deb7-125">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions/ms714644(v=vs.85))</span></span>

[<span data-ttu-id="8deb7-126">Windows PowerShell Shell SDK</span><span class="sxs-lookup"><span data-stu-id="8deb7-126">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
