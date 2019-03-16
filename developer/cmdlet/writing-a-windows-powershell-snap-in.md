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
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057798"
---
# <a name="writing-a-windows-powershell-snap-in"></a>Skriva en Windows PowerShell-snapin-modul

Det här exemplet visar hur du skriver en Windows PowerShell-snapin-modul som kan användas för att registrera alla cmdletar och providers för Windows PowerShell i en sammansättning.

Med den här typen av snapin-modulen kan väljer du inte vilka cmdlets och providers som du vill registrera. Om du vill skriva en snapin-modul som kan du välja vad är registrerad, se [skriva en anpassad Windows PowerShell snapin-modul](./writing-a-custom-windows-powershell-snap-in.md).

### <a name="writing-a-windows-powershell-snap-in"></a>Skriva en Windows PowerShell-snapin-modul

1. Lägg till attributet RunInstallerAttribute.

2. Skapa en offentlig klass som härleds från den [System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) klass.

    I det här exemplet är namnet på klassen ”GetProcPSSnapIn01”.

3. Lägg till en offentlig egenskap för namnet på snapin-modulen (krävs). När du namnger snapin-moduler, inte använda någon av följande tecken: #. , ( ) { } [ ] & - /\ $ ; : " ' \< > ; ? @ ` *

    I det här exemplet är namnet på snapin-modulen ”GetProcPSSnapIn01”.

4. Lägga till en offentlig egenskap för leverantören av snapin-modulen (krävs).

    I det här exemplet är leverantören ”Microsoft”.

5. Lägg till en offentlig egenskap för resursen leverantör av snapin-modulen (valfritt).

    Leverantörsresurs-är ”GetProcPSSnapIn01 Microsoft” i det här exemplet.

6. Lägg till en offentlig egenskap för beskrivning av snapin-modulen (krävs).

    Beskrivningen är ”detta är en Windows PowerShell-snapin-modul som registrerar cmdleten get-proc” i det här exemplet.

7. Lägg till en offentlig egenskap för resursen beskrivning av snapin-modulen (valfritt).

    Leverantörsresurs-är ”GetProcPSSnapIn01, detta är en Windows PowerShell-snapin-modul som registrerar cmdleten get-proc” i det här exemplet.

## <a name="example"></a>Exempel

Det här exemplet visar hur du skriver en Windows PowerShell-snapin-modul som kan användas för att registrera cmdleten Get-processen i Windows PowerShell-gränssnittet. Tänk på att i det här exemplet fullständig sammansättningen innehåller endast GetProcPSSnapIn01 snapin-modulen klassen och klassen cmdlet Get-processen.

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

[Hur du registrerar Cmdlets, Providers och vara värd för program](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
