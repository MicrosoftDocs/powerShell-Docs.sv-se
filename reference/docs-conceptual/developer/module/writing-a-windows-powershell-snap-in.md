---
ms.date: 09/13/2016
ms.topic: reference
title: Skriva en Windows PowerShell-snapin-modul
description: Skriva en Windows PowerShell-snapin-modul
ms.openlocfilehash: f658c2fa1211bfb77d2e8edd3999ce7f92df13bb
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92659448"
---
# <a name="writing-a-windows-powershell-snap-in"></a><span data-ttu-id="c73ef-103">Skriva en Windows PowerShell-snapin-modul</span><span class="sxs-lookup"><span data-stu-id="c73ef-103">Writing a Windows PowerShell Snap-in</span></span>

<span data-ttu-id="c73ef-104">Det här exemplet visar hur du skriver en Windows PowerShell-snapin-modul som kan användas för att registrera alla cmdlets och Windows PowerShell-providers i en sammansättning.</span><span class="sxs-lookup"><span data-stu-id="c73ef-104">This example shows how to write a Windows PowerShell snap-in that can be used to register all the cmdlets and Windows PowerShell providers in an assembly.</span></span>

<span data-ttu-id="c73ef-105">Med den här typen av snapin-modul väljer du inte vilka cmdletar och leverantörer du vill registrera.</span><span class="sxs-lookup"><span data-stu-id="c73ef-105">With this type of snap-in, you do not select which cmdlets and providers you want to register.</span></span> <span data-ttu-id="c73ef-106">Om du vill skriva en snapin-modul där du kan välja vad som är registrerat, se [skriva en anpassad Windows PowerShell-snapin-modul](./writing-a-custom-windows-powershell-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="c73ef-106">To write a snap-in that allows you to select what is registered, see [Writing a Custom Windows PowerShell Snap-in](./writing-a-custom-windows-powershell-snap-in.md).</span></span>

### <a name="writing-a-windows-powershell-snap-in"></a><span data-ttu-id="c73ef-107">Skriva en Windows PowerShell-snapin-modul</span><span class="sxs-lookup"><span data-stu-id="c73ef-107">Writing a Windows PowerShell Snap-in</span></span>

1. <span data-ttu-id="c73ef-108">Lägg till attributet RunInstallerAttribute.</span><span class="sxs-lookup"><span data-stu-id="c73ef-108">Add the RunInstallerAttribute attribute.</span></span>

2. <span data-ttu-id="c73ef-109">Skapa en offentlig klass som härleds från klassen [system. Management. Automation. PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) .</span><span class="sxs-lookup"><span data-stu-id="c73ef-109">Create a public class that derives from the [System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) class.</span></span>

    <span data-ttu-id="c73ef-110">I det här exemplet är klass namnet "GetProcPSSnapIn01".</span><span class="sxs-lookup"><span data-stu-id="c73ef-110">In this example, the class name is "GetProcPSSnapIn01".</span></span>

3. <span data-ttu-id="c73ef-111">Lägg till en offentlig egenskap för namnet på snapin-modulen (obligatoriskt).</span><span class="sxs-lookup"><span data-stu-id="c73ef-111">Add a public property for the name of the snap-in (required).</span></span> <span data-ttu-id="c73ef-112">När du namnger snapin-moduler ska du inte använda något av följande tecken:,,,,,,,,, `#` `.` `,` `(` `)` `{` `}` `[` `]` `&` , `-` , `/` , `\` , `$` , `;` `:` `"` `'` `<` `>` `|` `?` `@` `` ` `` ,,,,,,,,,,,,,,,,,, `*`</span><span class="sxs-lookup"><span data-stu-id="c73ef-112">When naming snap-ins, do not use any of the following characters: `#`, `.`, `,`, `(`, `)`, `{`, `}`, `[`, `]`, `&`, `-`, `/`, `\`, `$`, `;`, `:`, `"`, `'`, `<`, `>`, `|`, `?`, `@`, `` ` ``, `*`</span></span>

    <span data-ttu-id="c73ef-113">I det här exemplet är namnet på snapin-modulen "GetProcPSSnapIn01".</span><span class="sxs-lookup"><span data-stu-id="c73ef-113">In this example, the name of the snap-in is "GetProcPSSnapIn01".</span></span>

4. <span data-ttu-id="c73ef-114">Lägg till en offentlig egenskap för leverantören av snapin-modulen (obligatoriskt).</span><span class="sxs-lookup"><span data-stu-id="c73ef-114">Add a public property for the vendor of the snap-in (required).</span></span>

    <span data-ttu-id="c73ef-115">I det här exemplet är leverantören "Microsoft".</span><span class="sxs-lookup"><span data-stu-id="c73ef-115">In this example, the vendor is "Microsoft".</span></span>

5. <span data-ttu-id="c73ef-116">Lägg till en offentlig egenskap för leverantörs resursen för snapin-modulen (valfritt).</span><span class="sxs-lookup"><span data-stu-id="c73ef-116">Add a public property for the vendor resource of the snap-in (optional).</span></span>

    <span data-ttu-id="c73ef-117">I det här exemplet är leverantörs resursen "GetProcPSSnapIn01, Microsoft".</span><span class="sxs-lookup"><span data-stu-id="c73ef-117">In this example, the vendor resource is "GetProcPSSnapIn01,Microsoft".</span></span>

6. <span data-ttu-id="c73ef-118">Lägg till en offentlig egenskap för en beskrivning av snapin-modulen (krävs).</span><span class="sxs-lookup"><span data-stu-id="c73ef-118">Add a public property for the description of the snap-in (required).</span></span>

    <span data-ttu-id="c73ef-119">I det här exemplet är beskrivningen "det här är en Windows PowerShell-snapin-modul som registrerar cmdleten Get-proc".</span><span class="sxs-lookup"><span data-stu-id="c73ef-119">In this example, the description is "This is a Windows PowerShell snap-in that registers the  get-proc cmdlet".</span></span>

7. <span data-ttu-id="c73ef-120">Lägg till en offentlig egenskap för en beskrivnings resurs för snapin-modulen (valfritt).</span><span class="sxs-lookup"><span data-stu-id="c73ef-120">Add a public property for the description resource of the snap-in (optional).</span></span>

    <span data-ttu-id="c73ef-121">I det här exemplet är leverantörs resursen "GetProcPSSnapIn01, det här är en Windows PowerShell-snapin-modul som registrerar cmdleten Get-proc".</span><span class="sxs-lookup"><span data-stu-id="c73ef-121">In this example, the vendor resource is "GetProcPSSnapIn01,This is a Windows PowerShell snap-in  that registers the get-proc cmdlet".</span></span>

## <a name="example"></a><span data-ttu-id="c73ef-122">Exempel</span><span class="sxs-lookup"><span data-stu-id="c73ef-122">Example</span></span>

<span data-ttu-id="c73ef-123">Det här exemplet visar hur du skriver en Windows PowerShell-snapin-modul som kan användas för att registrera Get-Proc-cmdleten i Windows PowerShell-gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="c73ef-123">This example shows how to write a Windows PowerShell snap-in that can be used to register the Get-Proc cmdlet in the Windows PowerShell shell.</span></span> <span data-ttu-id="c73ef-124">Tänk på att i det här exemplet skulle den kompletta sammansättningen endast innehålla snapin-GetProcPSSnapIn01 och `Get-Proc` cmdlet-klassen.</span><span class="sxs-lookup"><span data-stu-id="c73ef-124">Be aware that in this example, the complete assembly would contain only the GetProcPSSnapIn01 snap-in class and the `Get-Proc` cmdlet class.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c73ef-125">Se även</span><span class="sxs-lookup"><span data-stu-id="c73ef-125">See Also</span></span>

<span data-ttu-id="c73ef-126">[Registrera cmdlets, providers och värd program](/previous-versions/ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="c73ef-126">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions/ms714644(v=vs.85))</span></span>

[<span data-ttu-id="c73ef-127">Windows PowerShell Shell SDK</span><span class="sxs-lookup"><span data-stu-id="c73ef-127">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
