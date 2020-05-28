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
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/23/2020
ms.locfileid: "83811116"
---
# <a name="writing-a-windows-powershell-snap-in"></a>Skriva en Windows PowerShell-snapin-modul

Det här exemplet visar hur du skriver en Windows PowerShell-snapin-modul som kan användas för att registrera alla cmdlets och Windows PowerShell-providers i en sammansättning.

Med den här typen av snapin-modul väljer du inte vilka cmdletar och leverantörer du vill registrera. Om du vill skriva en snapin-modul där du kan välja vad som är registrerat, se [skriva en anpassad Windows PowerShell-snapin-modul](./writing-a-custom-windows-powershell-snap-in.md).

### <a name="writing-a-windows-powershell-snap-in"></a>Skriva en Windows PowerShell-snapin-modul

1. Lägg till attributet RunInstallerAttribute.

2. Skapa en offentlig klass som härleds från klassen [system. Management. Automation. PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) .

    I det här exemplet är klass namnet "GetProcPSSnapIn01".

3. Lägg till en offentlig egenskap för namnet på snapin-modulen (obligatoriskt). När du namnger snapin-moduler ska du inte använda något av följande tecken:,,,,,,,,, `#` `.` `,` `(` `)` `{` `}` `[` `]` `&` , `-` , `/` , `\` , `$` , `;` `:` `"` `'` `<` `>` `|` `?` `@` `` ` `` ,,,,,,,,,,,,,,,,,,`*`

    I det här exemplet är namnet på snapin-modulen "GetProcPSSnapIn01".

4. Lägg till en offentlig egenskap för leverantören av snapin-modulen (obligatoriskt).

    I det här exemplet är leverantören "Microsoft".

5. Lägg till en offentlig egenskap för leverantörs resursen för snapin-modulen (valfritt).

    I det här exemplet är leverantörs resursen "GetProcPSSnapIn01, Microsoft".

6. Lägg till en offentlig egenskap för en beskrivning av snapin-modulen (krävs).

    I det här exemplet är beskrivningen "det här är en Windows PowerShell-snapin-modul som registrerar cmdleten Get-proc".

7. Lägg till en offentlig egenskap för en beskrivnings resurs för snapin-modulen (valfritt).

    I det här exemplet är leverantörs resursen "GetProcPSSnapIn01, det här är en Windows PowerShell-snapin-modul som registrerar cmdleten Get-proc".

## <a name="example"></a>Exempel

Det här exemplet visar hur du skriver en Windows PowerShell-snapin-modul som kan användas för att registrera cmdleten Get-proc i Windows PowerShell-gränssnittet. Tänk på att i det här exemplet skulle den kompletta sammansättningen endast innehålla snapin-GetProcPSSnapIn01 och `Get-Proc` cmdlet-klassen.

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

## <a name="see-also"></a>Se även

[Registrera cmdlets, providers och värd program](/previous-versions/ms714644(v=vs.85))

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)