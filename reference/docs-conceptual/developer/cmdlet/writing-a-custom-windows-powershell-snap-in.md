---
title: Skriva en anpassad Windows PowerShell-snapin-modul | Microsoft Docs
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
ms.openlocfilehash: aa6e4a4615f2681efa691008c86611f0df4e07d7
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870497"
---
# <a name="writing-a-custom-windows-powershell-snap-in"></a><span data-ttu-id="44c1a-102">Skriva en anpassad Windows PowerShell-snapin-modul</span><span class="sxs-lookup"><span data-stu-id="44c1a-102">Writing a Custom Windows PowerShell Snap-in</span></span>

<span data-ttu-id="44c1a-103">Det här exemplet visar hur du skriver en Windows PowerShell-snapin-modul som registrerar vissa cmdletar.</span><span class="sxs-lookup"><span data-stu-id="44c1a-103">This example shows how to write a Windows PowerShell snap-in that registers specific cmdlets.</span></span>

<span data-ttu-id="44c1a-104">Med den här typen av snapin-modul kan du ange vilka cmdlets, providers, typer eller format som ska registreras.</span><span class="sxs-lookup"><span data-stu-id="44c1a-104">With this type of snap-in, you specify which cmdlets, providers, types, or formats to register.</span></span> <span data-ttu-id="44c1a-105">Mer information om hur du skriver en snapin-modul som registrerar alla cmdlets och providers i en sammansättning finns i [skriva en Windows PowerShell-snapin-modul](./writing-a-windows-powershell-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="44c1a-105">For more information about how to write a snap-in that registers all the cmdlets and providers in an assembly, see [Writing a Windows PowerShell Snap-in](./writing-a-windows-powershell-snap-in.md).</span></span>

## <a name="to-write-a-windows-powershell-snap-in-that-registers-specific-cmdlets"></a><span data-ttu-id="44c1a-106">Att skriva en Windows PowerShell-snapin-modul som registrerar vissa cmdletar.</span><span class="sxs-lookup"><span data-stu-id="44c1a-106">To write a Windows PowerShell Snap-in that registers specific cmdlets.</span></span>

1. <span data-ttu-id="44c1a-107">Lägg till attributet RunInstallerAttribute.</span><span class="sxs-lookup"><span data-stu-id="44c1a-107">Add the RunInstallerAttribute attribute.</span></span>
2. <span data-ttu-id="44c1a-108">Skapa en offentlig klass som härleds från klassen [system. Management. Automation. Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) .</span><span class="sxs-lookup"><span data-stu-id="44c1a-108">Create a public class that derives from the [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) class.</span></span>

   <span data-ttu-id="44c1a-109">I det här exemplet är klass namnet "CustomPSSnapinTest".</span><span class="sxs-lookup"><span data-stu-id="44c1a-109">In this example, the class name is "CustomPSSnapinTest".</span></span>

3. <span data-ttu-id="44c1a-110">Lägg till en offentlig egenskap för namnet på snapin-modulen (obligatoriskt).</span><span class="sxs-lookup"><span data-stu-id="44c1a-110">Add a public property for the name of the snap-in (required).</span></span> <span data-ttu-id="44c1a-111">När du namnger snapin-moduler ska du inte använda något av följande tecken: `#`, `.`, `,`, `(`, `)`, `{`, `}`, `[`, `]`, `&`, `-`, `/`, `\`, `$`, `;`, `:`, `"`, `'`, `<`, `>`, `|`, `?`, `@`, `` ` ``, `*`</span><span class="sxs-lookup"><span data-stu-id="44c1a-111">When naming snap-ins, do not use any of the following characters: `#`, `.`, `,`, `(`, `)`, `{`, `}`, `[`, `]`, `&`, `-`, `/`, `\`, `$`, `;`, `:`, `"`, `'`, `<`, `>`, `|`, `?`, `@`, `` ` ``, `*`</span></span>

   <span data-ttu-id="44c1a-112">I det här exemplet är namnet på snapin-modulen "CustomPSSnapInTest".</span><span class="sxs-lookup"><span data-stu-id="44c1a-112">In this example, the name of the snap-in is "CustomPSSnapInTest".</span></span>

4. <span data-ttu-id="44c1a-113">Lägg till en offentlig egenskap för leverantören av snapin-modulen (obligatoriskt).</span><span class="sxs-lookup"><span data-stu-id="44c1a-113">Add a public property for the vendor of the snap-in (required).</span></span>

   <span data-ttu-id="44c1a-114">I det här exemplet är leverantören "Microsoft".</span><span class="sxs-lookup"><span data-stu-id="44c1a-114">In this example, the vendor is "Microsoft".</span></span>

5. <span data-ttu-id="44c1a-115">Lägg till en offentlig egenskap för leverantörs resursen för snapin-modulen (valfritt).</span><span class="sxs-lookup"><span data-stu-id="44c1a-115">Add a public property for the vendor resource of the snap-in (optional).</span></span>

   <span data-ttu-id="44c1a-116">I det här exemplet är leverantörs resursen "CustomPSSnapInTest, Microsoft".</span><span class="sxs-lookup"><span data-stu-id="44c1a-116">In this example, the vendor resource is "CustomPSSnapInTest,Microsoft".</span></span>

6. <span data-ttu-id="44c1a-117">Lägg till en offentlig egenskap för en beskrivning av snapin-modulen (krävs).</span><span class="sxs-lookup"><span data-stu-id="44c1a-117">Add a public property for the description of the snap-in (required).</span></span>

   <span data-ttu-id="44c1a-118">I det här exemplet är beskrivningen: "det här är en anpassad Windows PowerShell-snapin-modul som innehåller `Test-HelloWorld`-och `Test-CustomSnapinTest`-cmdletar".</span><span class="sxs-lookup"><span data-stu-id="44c1a-118">In this example, the description is: "This is a custom Windows PowerShell snap-in that includes the `Test-HelloWorld` and `Test-CustomSnapinTest` cmdlets".</span></span>

7. <span data-ttu-id="44c1a-119">Lägg till en offentlig egenskap för en beskrivnings resurs för snapin-modulen (valfritt).</span><span class="sxs-lookup"><span data-stu-id="44c1a-119">Add a public property for the description resource of the snap-in (optional).</span></span>

   <span data-ttu-id="44c1a-120">I det här exemplet är leverantörs resursen:</span><span class="sxs-lookup"><span data-stu-id="44c1a-120">In this example, the vendor resource is:</span></span>

   > <span data-ttu-id="44c1a-121">CustomPSSnapInTest är det här en anpassad Windows PowerShell-snapin-modul som innehåller cmdletarna test-HelloWorld och test-CustomSnapinTest.</span><span class="sxs-lookup"><span data-stu-id="44c1a-121">CustomPSSnapInTest, This is a custom Windows PowerShell snap-in that includes the Test-HelloWorld and Test-CustomSnapinTest cmdlets".</span></span>

8. <span data-ttu-id="44c1a-122">Ange de cmdlet: ar som tillhör den anpassade snapin-modulen (valfritt) med hjälp av klassen [system. Management. Automation. körnings utrymmen. Cmdletconfigurationentry](/dotnet/api/System.Management.Automation.Runspaces.CmdletConfigurationEntry) .</span><span class="sxs-lookup"><span data-stu-id="44c1a-122">Specify the cmdlets that belong to the custom snap-in (optional) using the [System.Management.Automation.Runspaces.Cmdletconfigurationentry](/dotnet/api/System.Management.Automation.Runspaces.CmdletConfigurationEntry) class.</span></span> <span data-ttu-id="44c1a-123">Den information som läggs till här inkluderar namnet på cmdleten, dess .NET-typ och namnet på cmdlet-hjälp filen (formatet för cmdlet hjälp filens namn ska vara` name.dll-help.xml`).</span><span class="sxs-lookup"><span data-stu-id="44c1a-123">The information added here includes the name of the cmdlet, its .NET type, and the cmdlet Help file name (the format of the cmdlet Help file name should be` name.dll-help.xml`).</span></span>

   <span data-ttu-id="44c1a-124">I det här exemplet läggs cmdletarna test-HelloWorld och TestCustomSnapinTest till.</span><span class="sxs-lookup"><span data-stu-id="44c1a-124">This example adds the Test-HelloWorld and TestCustomSnapinTest cmdlets.</span></span>

9. <span data-ttu-id="44c1a-125">Ange de providers som tillhör den anpassade snapin-modulen (valfritt).</span><span class="sxs-lookup"><span data-stu-id="44c1a-125">Specify the providers that belong to the custom snap-in (optional).</span></span>

   <span data-ttu-id="44c1a-126">I det här exemplet anges inga providrar.</span><span class="sxs-lookup"><span data-stu-id="44c1a-126">This example does not specify any providers.</span></span>

10. <span data-ttu-id="44c1a-127">Ange de typer som tillhör den anpassade snapin-modulen (valfritt).</span><span class="sxs-lookup"><span data-stu-id="44c1a-127">Specify the types that belong to the custom snap-in (optional).</span></span>

    <span data-ttu-id="44c1a-128">I det här exemplet anges inga typer.</span><span class="sxs-lookup"><span data-stu-id="44c1a-128">This example does not specify any types.</span></span>

11. <span data-ttu-id="44c1a-129">Ange de format som tillhör den anpassade snapin-modulen (valfritt).</span><span class="sxs-lookup"><span data-stu-id="44c1a-129">Specify the formats that belong to the custom snap-in (optional).</span></span>

    <span data-ttu-id="44c1a-130">I det här exemplet anges inga format.</span><span class="sxs-lookup"><span data-stu-id="44c1a-130">This example does not specify any formats.</span></span>

## <a name="example"></a><span data-ttu-id="44c1a-131">Exempel</span><span class="sxs-lookup"><span data-stu-id="44c1a-131">Example</span></span>

<span data-ttu-id="44c1a-132">Det här exemplet visar hur du skriver en anpassad Windows PowerShell-snapin-modul som kan användas för att registrera `Test-HelloWorld` och `Test-CustomSnapinTest`-cmdletar.</span><span class="sxs-lookup"><span data-stu-id="44c1a-132">This example shows how to write a Custom Windows PowerShell snap-in that can be used to register the `Test-HelloWorld` and `Test-CustomSnapinTest` cmdlets.</span></span> <span data-ttu-id="44c1a-133">Tänk på att i det här exemplet kan den kompletta sammansättningen innehålla andra cmdlets och providers som inte skulle registreras av den här snapin-modulen.</span><span class="sxs-lookup"><span data-stu-id="44c1a-133">Be aware that in this example, the complete assembly could contain other cmdlets and providers that would not be registered by this snap-in.</span></span>

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

<span data-ttu-id="44c1a-134">Mer information om hur du registrerar snapin-moduler finns i [så här registrerar du cmdlets, providers och värd program](/previous-versions/ms714644(v=vs.85)) i [Windows PowerShell Programmer ' s guide](../prog-guide/windows-powershell-programmer-s-guide.md).</span><span class="sxs-lookup"><span data-stu-id="44c1a-134">For more information about registering snap-ins, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions/ms714644(v=vs.85)) in the [Windows PowerShell Programmer's Guide](../prog-guide/windows-powershell-programmer-s-guide.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="44c1a-135">Se även</span><span class="sxs-lookup"><span data-stu-id="44c1a-135">See Also</span></span>

<span data-ttu-id="44c1a-136">[Registrera cmdlets, providers och värd program](/previous-versions/ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="44c1a-136">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions/ms714644(v=vs.85))</span></span>

[<span data-ttu-id="44c1a-137">Windows PowerShell Shell SDK</span><span class="sxs-lookup"><span data-stu-id="44c1a-137">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
