---
title: Skriva en anpassad Windows PowerShell snapin-modulen | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- snap-ins [PowerShell SDK], custom PSSnapin example
- cmdlets [PowerShell SDK], specified in snap-ins
ms.assetid: 55c8b5cb-8ee2-4080-afc4-3f09c9f20128
caps.latest.revision: 6
ms.openlocfilehash: 4d50ef4dcd75d5c0ba802fbcfe2d7d1d7c954707
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795597"
---
# <a name="writing-a-custom-windows-powershell-snap-in"></a><span data-ttu-id="d71b7-102">Skriva en anpassad Windows PowerShell-snapin-modul</span><span class="sxs-lookup"><span data-stu-id="d71b7-102">Writing a Custom Windows PowerShell Snap-in</span></span>

<span data-ttu-id="d71b7-103">Det här exemplet visar hur du skriver en Windows PowerShell-snapin-modul som registrerar specifika cmdletar.</span><span class="sxs-lookup"><span data-stu-id="d71b7-103">This example shows how to write a Windows PowerShell snap-in that registers specific cmdlets.</span></span>

<span data-ttu-id="d71b7-104">Med den här typen av snapin-modulen kan ange du vilka cmdlets, providers, typer eller format att registrera.</span><span class="sxs-lookup"><span data-stu-id="d71b7-104">With this type of snap-in, you specify which cmdlets, providers, types, or formats to register.</span></span> <span data-ttu-id="d71b7-105">Mer information om hur du skriver en snapin-modul som registrerar alla cmdletar och providers i en sammansättning finns [skriva en Windows PowerShell snapin-modul](./writing-a-windows-powershell-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="d71b7-105">For more information about how to write a snap-in that registers all the cmdlets and providers in an assembly, see [Writing a Windows PowerShell Snap-in](./writing-a-windows-powershell-snap-in.md).</span></span>

## <a name="to-write-a-windows-powershell-snap-in-that-registers-specific-cmdlets"></a><span data-ttu-id="d71b7-106">Om du vill skriva en Windows PowerShell snapin-modul registrerar som specifika cmdletar.</span><span class="sxs-lookup"><span data-stu-id="d71b7-106">To write a Windows PowerShell Snap-in that registers specific cmdlets.</span></span>

1. <span data-ttu-id="d71b7-107">Lägg till attributet RunInstallerAttribute.</span><span class="sxs-lookup"><span data-stu-id="d71b7-107">Add the RunInstallerAttribute attribute.</span></span>

2. <span data-ttu-id="d71b7-108">Skapa en offentlig klass som härleds från den [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) klass.</span><span class="sxs-lookup"><span data-stu-id="d71b7-108">Create a public class that derives from the [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) class.</span></span>

   <span data-ttu-id="d71b7-109">I det här exemplet är namnet på klassen ”CustomPSSnapinTest”.</span><span class="sxs-lookup"><span data-stu-id="d71b7-109">In this example, the class name is "CustomPSSnapinTest".</span></span>

3. <span data-ttu-id="d71b7-110">Lägg till en offentlig egenskap för namnet på snapin-modulen (krävs).</span><span class="sxs-lookup"><span data-stu-id="d71b7-110">Add a public property for the name of the snap-in (required).</span></span> <span data-ttu-id="d71b7-111">När du namnger snapin-moduler, inte använda någon av följande tecken: #.</span><span class="sxs-lookup"><span data-stu-id="d71b7-111">When naming snap-ins, do not use any of the following characters: # .</span></span> <span data-ttu-id="d71b7-112">, ( ) { } [ ] & - /\ $ ; : " ' \< > &#124; ?</span><span class="sxs-lookup"><span data-stu-id="d71b7-112">, ( ) { } [ ] & - /\ $ ; : " ' \< > &#124; ?</span></span> <span data-ttu-id="d71b7-113">@ \` \*</span><span class="sxs-lookup"><span data-stu-id="d71b7-113">@ \` \*</span></span>

   <span data-ttu-id="d71b7-114">I det här exemplet är namnet på snapin-modulen ”CustomPSSnapInTest”.</span><span class="sxs-lookup"><span data-stu-id="d71b7-114">In this example, the name of the snap-in is "CustomPSSnapInTest".</span></span>

4. <span data-ttu-id="d71b7-115">Lägga till en offentlig egenskap för leverantören av snapin-modulen (krävs).</span><span class="sxs-lookup"><span data-stu-id="d71b7-115">Add a public property for the vendor of the snap-in (required).</span></span>

   <span data-ttu-id="d71b7-116">I det här exemplet är leverantören ”Microsoft”.</span><span class="sxs-lookup"><span data-stu-id="d71b7-116">In this example, the vendor is "Microsoft".</span></span>

5. <span data-ttu-id="d71b7-117">Lägg till en offentlig egenskap för resursen leverantör av snapin-modulen (valfritt).</span><span class="sxs-lookup"><span data-stu-id="d71b7-117">Add a public property for the vendor resource of the snap-in (optional).</span></span>

   <span data-ttu-id="d71b7-118">Leverantörsresurs-är ”CustomPSSnapInTest Microsoft” i det här exemplet.</span><span class="sxs-lookup"><span data-stu-id="d71b7-118">In this example, the vendor resource is "CustomPSSnapInTest,Microsoft".</span></span>

6. <span data-ttu-id="d71b7-119">Lägg till en offentlig egenskap för beskrivning av snapin-modulen (krävs).</span><span class="sxs-lookup"><span data-stu-id="d71b7-119">Add a public property for the description of the snap-in (required).</span></span>

   <span data-ttu-id="d71b7-120">I det här exemplet är beskrivningen: ”Detta är en anpassad Windows PowerShell snapin-modul som innehåller Test-HelloWorld och Test-CustomSnapinTest cmdlets”.</span><span class="sxs-lookup"><span data-stu-id="d71b7-120">In this example, the description is: "This is a custom Windows PowerShell snap-in that includes the Test-HelloWorld and Test-CustomSnapinTest cmdlets".</span></span>

7. <span data-ttu-id="d71b7-121">Lägg till en offentlig egenskap för resursen beskrivning av snapin-modulen (valfritt).</span><span class="sxs-lookup"><span data-stu-id="d71b7-121">Add a public property for the description resource of the snap-in (optional).</span></span>

   <span data-ttu-id="d71b7-122">Leverantörsresurs-är ”CustomPSSnapInTest, detta är en anpassad Windows PowerShell snapin-modul som innehåller cmdlet: Test-HelloWorld och Test-CustomSnapinTest” i det här exemplet.</span><span class="sxs-lookup"><span data-stu-id="d71b7-122">In this example, the vendor resource is "CustomPSSnapInTest, This is a custom Windows PowerShell snap-in that includes the Test-HelloWorld and Test-CustomSnapinTest cmdlets".</span></span>

8. <span data-ttu-id="d71b7-123">Ange de cmdletar som hör till den anpassade snapin-modulen (valfritt) med hjälp av den [System.Management.Automation.Runspaces.Cmdletconfigurationentry](/dotnet/api/System.Management.Automation.Runspaces.CmdletConfigurationEntry) klass.</span><span class="sxs-lookup"><span data-stu-id="d71b7-123">Specify the cmdlets that belong to the custom snap-in (optional) using the [System.Management.Automation.Runspaces.Cmdletconfigurationentry](/dotnet/api/System.Management.Automation.Runspaces.CmdletConfigurationEntry) class.</span></span> <span data-ttu-id="d71b7-124">Den information som läggs till här innehåller namnet på cmdleten och dess .NET-typ cmdlet Help filnamnet (name.dll help.xml bör vara i formatet på namnet på cmdleten hjälp).</span><span class="sxs-lookup"><span data-stu-id="d71b7-124">The information added here includes the name of the cmdlet, its .NET type, and the cmdlet Help file name (the format of the cmdlet Help file name should be name.dll-help.xml).</span></span>

   <span data-ttu-id="d71b7-125">Det här exemplet lägger till cmdlet: Test-HelloWorld och TestCustomSnapinTest.</span><span class="sxs-lookup"><span data-stu-id="d71b7-125">This example adds the Test-HelloWorld and TestCustomSnapinTest cmdlets.</span></span>

9. <span data-ttu-id="d71b7-126">Ange providers som hör till anpassade snapin-modulen (valfritt).</span><span class="sxs-lookup"><span data-stu-id="d71b7-126">Specify the providers that belong to the custom snap-in (optional).</span></span>

   <span data-ttu-id="d71b7-127">Det här exemplet anger inte alla leverantörer.</span><span class="sxs-lookup"><span data-stu-id="d71b7-127">This example does not specify any providers.</span></span>

10. <span data-ttu-id="d71b7-128">Ange de typer som hör till anpassade snapin-modulen (valfritt).</span><span class="sxs-lookup"><span data-stu-id="d71b7-128">Specify the types that belong to the custom snap-in (optional).</span></span>

    <span data-ttu-id="d71b7-129">Det här exemplet anger inte några typer.</span><span class="sxs-lookup"><span data-stu-id="d71b7-129">This example does not specify any types.</span></span>

11. <span data-ttu-id="d71b7-130">Ange de format som hör till anpassade snapin-modulen (valfritt).</span><span class="sxs-lookup"><span data-stu-id="d71b7-130">Specify the formats that belong to the custom snap-in (optional).</span></span>

    <span data-ttu-id="d71b7-131">Det här exemplet anger inte någon format.</span><span class="sxs-lookup"><span data-stu-id="d71b7-131">This example does not specify any formats.</span></span>

## <a name="example"></a><span data-ttu-id="d71b7-132">Exempel</span><span class="sxs-lookup"><span data-stu-id="d71b7-132">Example</span></span>

<span data-ttu-id="d71b7-133">Det här exemplet visar hur du skriver en anpassad Windows PowerShell-snapin-modul som kan användas för att registrera Test-HelloWorld och Test-CustomSnapinTest-cmdletar.</span><span class="sxs-lookup"><span data-stu-id="d71b7-133">This example shows how to write a Custom Windows PowerShell snap-in that can be used to register the Test-HelloWorld and Test-CustomSnapinTest cmdlets.</span></span> <span data-ttu-id="d71b7-134">Tänk på att i det här exemplet kompletta enheter kan innehålla andra cmdletar och providers som inte skulle har registrerats av snapin-modulen.</span><span class="sxs-lookup"><span data-stu-id="d71b7-134">Be aware that in this example, the complete assembly could contain other cmdlets and providers that would not be registered by this snap-in.</span></span>

```csharp
[RunInstaller(true)]
public class CustomPSSnapinTest : CustomPSSnapIn
{
  /// <summary>
  /// Creates an instance of CustomPSSnapInTest class.
  /// </summary>
  public CustomPSSnapinTest()
          : base()
  {
  }

  /// <summary>
  /// Specify the name of the custom PowerShell snap-in.
  /// </summary>
  public override string Name
  {
    get
    {
      return "CustomPSSnapInTest";
    }
  }

  /// <summary>
  /// Specify the vendor for the custom PowerShell snap-in.
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
  /// Use the format: resourceBaseName,resourceName.
  /// </summary>
  public override string VendorResource
  {
    get
    {
        return "CustomPSSnapInTest,Microsoft";
    }
  }

  /// <summary>
  /// Specify a description of the custom PowerShell snap-in.
  /// </summary>
  public override string Description
  {
    get
    {
      return "This is a custom PowerShell snap-in that includes the Test-HelloWorld and Test-CustomSnapinTest cmdlets.";
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
        return "CustomPSSnapInTest,This is a custom PowerShell snap-in that includes the Test-HelloWorld and Test-CustomSnapinTest cmdlets.";
    }
  }

  /// <summary>
  /// Specify the cmdlets that belong to this custom PowerShell snap-in.
  /// </summary>
  private Collection<CmdletConfigurationEntry> _cmdlets;
  public override Collection<CmdletConfigurationEntry> Cmdlets
  {
    get
    {
      if (_cmdlets == null)
      {
        _cmdlets = new Collection<CmdletConfigurationEntry>();
        _cmdlets.Add(new CmdletConfigurationEntry("test-customsnapintest", typeof(TestCustomSnapinTest), "TestCmdletHelp.dll-help.xml"));
        _cmdlets.Add(new CmdletConfigurationEntry("test-helloworld", typeof(TestHelloWorld), "HelloWorldHelp.dll-help.xml"));
      }

      return _cmdlets;
    }
  }

  /// <summary>
  /// Specify the providers that belong to this custom PowerShell snap-in.
  /// </summary>
  private Collection<ProviderConfigurationEntry> _providers;
  public override Collection<ProviderConfigurationEntry> Providers
  {
    get
    {
      if (_providers == null)
      {
        _providers = new Collection<ProviderConfigurationEntry>();
      }

      return _providers;
    }
  }

  /// <summary>
  /// Specify the types that belong to this custom PowerShell snap-in.
  /// </summary>
  private Collection<TypeConfigurationEntry> _types;
  public override Collection<TypeConfigurationEntry> Types
  {
    get
    {
      if (_types == null)
      {
        _types = new Collection<TypeConfigurationEntry>();
      }

      return _types;
    }
  }

  /// <summary>
  /// Specify the formats that belong to this custom PowerShell snap-in.
  /// </summary>
  private Collection<FormatConfigurationEntry> _formats;
  public override Collection<FormatConfigurationEntry> Formats
  {
    get
    {
      if (_formats == null)
      {
        _formats = new Collection<FormatConfigurationEntry>();
      }

      return _formats;
    }
  }
}
```

<span data-ttu-id="d71b7-135">Mer information om hur du registrerar snapin-moduler finns i [hur du registrera Cmdlets och Providers värdprogram](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c) i den [Programmeringsguide för Windows PowerShell](../prog-guide/windows-powershell-programmer-s-guide.md).</span><span class="sxs-lookup"><span data-stu-id="d71b7-135">For more information about registering snap-ins, see [How to Register Cmdlets, Providers, and Host Applications](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c) in the [Windows PowerShell Programmer's Guide](../prog-guide/windows-powershell-programmer-s-guide.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d71b7-136">Se även</span><span class="sxs-lookup"><span data-stu-id="d71b7-136">See Also</span></span>

[<span data-ttu-id="d71b7-137">Hur du registrerar Cmdlets, Providers och vara värd för program</span><span class="sxs-lookup"><span data-stu-id="d71b7-137">How to Register Cmdlets, Providers, and Host Applications</span></span>](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="d71b7-138">Windows PowerShell Shell SDK</span><span class="sxs-lookup"><span data-stu-id="d71b7-138">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
