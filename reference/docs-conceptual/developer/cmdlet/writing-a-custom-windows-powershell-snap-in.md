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
ms.openlocfilehash: 9cf4499ec2992c6cfea83fc5d0bf51d0bbfaa96a
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83556860"
---
# <a name="writing-a-custom-windows-powershell-snap-in"></a>Skriva en anpassad Windows PowerShell-snapin-modul

Det här exemplet visar hur du skriver en Windows PowerShell-snapin-modul som registrerar vissa cmdletar.

Med den här typen av snapin-modul kan du ange vilka cmdlets, providers, typer eller format som ska registreras. Mer information om hur du skriver en snapin-modul som registrerar alla cmdlets och providers i en sammansättning finns i [skriva en Windows PowerShell-snapin-modul](./writing-a-windows-powershell-snap-in.md).

## <a name="to-write-a-windows-powershell-snap-in-that-registers-specific-cmdlets"></a>Att skriva en Windows PowerShell-snapin-modul som registrerar vissa cmdletar.

1. Lägg till attributet RunInstallerAttribute.
2. Skapa en offentlig klass som härleds från klassen [system. Management. Automation. Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) .

   I det här exemplet är klass namnet "CustomPSSnapinTest".

3. Lägg till en offentlig egenskap för namnet på snapin-modulen (obligatoriskt). När du namnger snapin-moduler ska du inte använda något av följande tecken:,,,,,,,,, `#` `.` `,` `(` `)` `{` `}` `[` `]` `&` , `-` , `/` , `\` , `$` , `;` `:` `"` `'` `<` `>` `|` `?` `@` `` ` `` ,,,,,,,,,,,,,,,,,,`*`

   I det här exemplet är namnet på snapin-modulen "CustomPSSnapInTest".

4. Lägg till en offentlig egenskap för leverantören av snapin-modulen (obligatoriskt).

   I det här exemplet är leverantören "Microsoft".

5. Lägg till en offentlig egenskap för leverantörs resursen för snapin-modulen (valfritt).

   I det här exemplet är leverantörs resursen "CustomPSSnapInTest, Microsoft".

6. Lägg till en offentlig egenskap för en beskrivning av snapin-modulen (krävs).

   I det här exemplet är beskrivningen: "det här är en anpassad Windows PowerShell-snapin-modul som innehåller `Test-HelloWorld` `Test-CustomSnapinTest` cmdletarna och".

7. Lägg till en offentlig egenskap för en beskrivnings resurs för snapin-modulen (valfritt).

   I det här exemplet är leverantörs resursen:

   > CustomPSSnapInTest är det här en anpassad Windows PowerShell-snapin-modul som innehåller cmdletarna test-HelloWorld och test-CustomSnapinTest.

8. Ange de cmdlet: ar som tillhör den anpassade snapin-modulen (valfritt) med hjälp av klassen [system. Management. Automation. körnings utrymmen. Cmdletconfigurationentry](/dotnet/api/System.Management.Automation.Runspaces.CmdletConfigurationEntry) . Den information som läggs till här inkluderar namnet på cmdleten, dess .NET-typ och cmdlet-hjälpens fil namn (formatet för cmdletens hjälp fil namn ska vara `name.dll-help.xml` ).

   I det här exemplet läggs cmdletarna test-HelloWorld och TestCustomSnapinTest till.

9. Ange de providers som tillhör den anpassade snapin-modulen (valfritt).

   I det här exemplet anges inga providrar.

10. Ange de typer som tillhör den anpassade snapin-modulen (valfritt).

    I det här exemplet anges inga typer.

11. Ange de format som tillhör den anpassade snapin-modulen (valfritt).

    I det här exemplet anges inga format.

## <a name="example"></a>Exempel

Det här exemplet visar hur du skriver en anpassad Windows PowerShell-snapin-modul som kan användas för att `Test-HelloWorld` Registrera `Test-CustomSnapinTest` cmdletarna och. Tänk på att i det här exemplet kan den kompletta sammansättningen innehålla andra cmdlets och providers som inte skulle registreras av den här snapin-modulen.

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

Mer information om hur du registrerar snapin-moduler finns i [så här registrerar du cmdlets, providers och värd program](/previous-versions/ms714644(v=vs.85)) i [Windows PowerShell Programmer ' s guide](../prog-guide/windows-powershell-programmer-s-guide.md).

## <a name="see-also"></a>Se även

[Registrera cmdlets, providers och värd program](/previous-versions/ms714644(v=vs.85))

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
