---
ms.date: 09/12/2016
ms.topic: reference
title: HelpInfo-XML-schema
description: HelpInfo-XML-schema
ms.openlocfilehash: 157fd9c0f47c57efbaa9b7888fa174a34ad9567d
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92662009"
---
# <a name="helpinfo-xml-schema"></a>HelpInfo-XML-schema

Det här avsnittet innehåller XML-schemat för uppdaterings bara hjälp information filer, vanligt vis kallade "HelpInfo XML Files".

## <a name="helpinfo-xml-schema"></a>HelpInfo-XML-schema

HelpInfo XML-filer baseras på följande XML-schema.

```xml
<?xml version="1.0" encoding="utf-8"?>
<schema targetNamespace="http://schemas.microsoft.com/powershell/help/2010/05" xmlns="http://www.w3.org/2001/XMLSchema">
  <element name="HelpInfo">
    <complexType>
      <sequence>
        <element name="HelpContentURI" type="anyURI" minOccurs="1" maxOccurs="1" />
        <element name="SupportedUICultures" minOccurs="1" maxOccurs="1">
          <complexType>
            <sequence>
              <element name="UICulture" minOccurs="1" maxOccurs="unbounded">
                <complexType>
                  <sequence>
                    <element name="UICultureName" type="language" minOccurs="1" maxOccurs="1" />
                    <element name="UICultureVersion" type="string" minOccurs="1" maxOccurs="1" />
                  </sequence>
                </complexType>
              </element>
            </sequence>
          </complexType>
        </element>
      </sequence>
    </complexType>
  </element>
</schema>
```

## <a name="helpinfo-xml-elements"></a>HelpInfo XML-element

XML-filen HelpInfo innehåller följande element.

- **HelpContentURI** – innehåller URI för platsen för hjälpens CAB-filer för modulen. URI: n måste börja med http eller https. URI: n måste ange en Internet plats, men får inte innehålla CAB-filnamn. **HelpContentURI** -värdet kan vara samma eller något annat än värdet för **HelpInfoURI** .

- **SupportedUICultures** – visar modulens hjälpfiler i alla UI-kulturer. Innehåller **värdet** -element som representerar en uppsättning hjälpfiler för modulen i en angiven kultur för användar gränssnittet.

- **Värdet** – representerar en uppsättning hjälpfiler för modulen i en angiven användar gränssnitts kultur. Lägg till ett **värdet** -element för varje gränssnitts kultur där hjälpfilerna skrivs.

- **UICultureName** – innehåller språk koden för den gränssnitts kultur som hjälpfilerna skrivs till.

- **UICultureVersion** – innehåller ett 4-delar av versions numret i "N1. N2. N3. N4 "-format som representerar versionen av CAB-filen för hjälp i användar gränssnitts kulturen. Öka det här versions numret när du överför nya CAB-filer för hjälpfiler i användar gränssnitts kulturen som anges av **UICultureName**. Mer information om det här värdet finns i [versions klass](/dotnet/api/system.version).
