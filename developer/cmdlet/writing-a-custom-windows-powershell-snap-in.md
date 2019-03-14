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
# <a name="writing-a-custom-windows-powershell-snap-in"></a>Skriva en anpassad Windows PowerShell-snapin-modul

Det här exemplet visar hur du skriver en Windows PowerShell-snapin-modul som registrerar specifika cmdletar.

Med den här typen av snapin-modulen kan ange du vilka cmdlets, providers, typer eller format att registrera. Mer information om hur du skriver en snapin-modul som registrerar alla cmdletar och providers i en sammansättning finns [skriva en Windows PowerShell snapin-modul](./writing-a-windows-powershell-snap-in.md).

## <a name="to-write-a-windows-powershell-snap-in-that-registers-specific-cmdlets"></a>Om du vill skriva en Windows PowerShell snapin-modul registrerar som specifika cmdletar.

1. Lägg till attributet RunInstallerAttribute.

2. Skapa en offentlig klass som härleds från den [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) klass.

   I det här exemplet är namnet på klassen ”CustomPSSnapinTest”.

3. Lägg till en offentlig egenskap för namnet på snapin-modulen (krävs). När du namnger snapin-moduler, inte använda någon av följande tecken: #. , ( ) { } [ ] & - /\ $ ; : " ' \< > &#124; ? @ ` *

   I det här exemplet är namnet på snapin-modulen ”CustomPSSnapInTest”.

4. Lägga till en offentlig egenskap för leverantören av snapin-modulen (krävs).

   I det här exemplet är leverantören ”Microsoft”.

5. Lägg till en offentlig egenskap för resursen leverantör av snapin-modulen (valfritt).

   Leverantörsresurs-är ”CustomPSSnapInTest Microsoft” i det här exemplet.

6. Lägg till en offentlig egenskap för beskrivning av snapin-modulen (krävs).

   I det här exemplet är beskrivningen: ”Detta är en anpassad Windows PowerShell snapin-modul som innehåller Test-HelloWorld och Test-CustomSnapinTest cmdlets”.

7. Lägg till en offentlig egenskap för resursen beskrivning av snapin-modulen (valfritt).

   Leverantörsresurs-är ”CustomPSSnapInTest, detta är en anpassad Windows PowerShell snapin-modul som innehåller cmdlet: Test-HelloWorld och Test-CustomSnapinTest” i det här exemplet.

8. Ange de cmdletar som hör till den anpassade snapin-modulen (valfritt) med hjälp av den [System.Management.Automation.Runspaces.Cmdletconfigurationentry](/dotnet/api/System.Management.Automation.Runspaces.CmdletConfigurationEntry) klass. Den information som läggs till här innehåller namnet på cmdleten och dess .NET-typ cmdlet Help filnamnet (name.dll help.xml bör vara i formatet på namnet på cmdleten hjälp).

   Det här exemplet lägger till cmdlet: Test-HelloWorld och TestCustomSnapinTest.

9. Ange providers som hör till anpassade snapin-modulen (valfritt).

   Det här exemplet anger inte alla leverantörer.

10. Ange de typer som hör till anpassade snapin-modulen (valfritt).

    Det här exemplet anger inte några typer.

11. Ange de format som hör till anpassade snapin-modulen (valfritt).

    Det här exemplet anger inte någon format.

## <a name="example"></a>Exempel

Det här exemplet visar hur du skriver en anpassad Windows PowerShell-snapin-modul som kan användas för att registrera Test-HelloWorld och Test-CustomSnapinTest-cmdletar. Tänk på att i det här exemplet kompletta enheter kan innehålla andra cmdletar och providers som inte skulle har registrerats av snapin-modulen.

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

Mer information om hur du registrerar snapin-moduler finns i [hur du registrera Cmdlets och Providers värdprogram](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c) i den [Programmeringsguide för Windows PowerShell](../prog-guide/windows-powershell-programmer-s-guide.md).

## <a name="see-also"></a>Se även

[Hur du registrerar Cmdlets, Providers och vara värd för program](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
