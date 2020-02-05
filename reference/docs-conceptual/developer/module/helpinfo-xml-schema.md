---
title: HelpInfo XML-schema | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 74dcb396-c295-4457-b84c-4432bdaa8df3
caps.latest.revision: 7
ms.openlocfilehash: 8142a620f0f71de3d2a6b33fc2e45092b5743a54
ms.sourcegitcommit: bc9a4904c2b1561386d748fc9ac242699d2f1694
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/04/2020
ms.locfileid: "76996010"
---
# <a name="helpinfo-xml-schema"></a>HelpInfo-XML-schema

Det här avsnittet innehåller XML-schemat för uppdaterings bara hjälp information filer, vanligt vis kallade "HelpInfo XML Files".

## <a name="helpinfo-xml-schema"></a>HelpInfo-XML-schema

HelpInfo XML-filer baseras på följande XML-schema.

```xml
<?xml version="1.0" encoding="utf-8"?>
<schema targetNamespace="https://schemas.microsoft.com/powershell/help/2010/05" xmlns="http://www.w3.org/2001/XMLSchema">
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

HelpContentURI innehåller URI för platsen för hjälpens CAB-filer för modulen. URI: n måste börja med http eller https. URI: n måste ange en Internet plats, men får inte innehålla CAB-filnamn. **HelpContentURI** -värdet kan vara samma eller något annat än värdet för **HelpInfoURI** .

SupportedUICultures representerar modulens hjälpfiler i alla UI-kulturer. Innehåller **värdet** -element som representerar en uppsättning hjälpfiler för modulen i en angiven kultur för användar gränssnittet.

Värdet representerar en uppsättning hjälpfiler för modulen i en angiven användar gränssnitts kultur. Lägg till ett **värdet** -element för varje gränssnitts kultur där hjälpfilerna skrivs.

UICultureName innehåller språk koden för den GRÄNSSNITTs kultur som hjälpfilerna skrivs till.

UICultureVersion innehåller 4 delar av versions nummer i "N1. N2. N3. N4 "-format som representerar versionen av CAB-filen för hjälp i användar gränssnitts kulturen. Öka det här versions numret när du överför nya CAB-filer för hjälpfiler i användar gränssnitts kulturen som anges av **UICultureName**. Mer information om det här värdet finns i "versions klass (system)" i MSDN.