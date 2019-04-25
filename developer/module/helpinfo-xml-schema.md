---
title: HelpInfo XML-Schema | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 74dcb396-c295-4457-b84c-4432bdaa8df3
caps.latest.revision: 7
ms.openlocfilehash: 0f965f4ee1ef92a6a538b52b4348c04366cabf66
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082472"
---
# <a name="helpinfo-xml-schema"></a>HelpInfo-XML-schema

Det här avsnittet innehåller XML-schemat för uppdateringsbar hjälp Information filer, ofta kallade ”HelpInfo XML-filer”.

## <a name="helpinfo-xml-schema"></a>HelpInfo-XML-schema

HelpInfo XML-filer baserat på följande XML-schema.

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

HelpInfo XML-filen innehåller följande element.

HelpContentURI innehåller URI för platsen för hjälp CAB-filer för modulen. URI: N måste börja med ”http” eller ”https”. URI: N ska ange en plats på Internet, men får inte innehålla namnet på CAB-filen. Den **HelpContentURI** värdet kan vara samma eller olika från den **HelpInfoURI** värde.

SupportedUICultures representerar modulen hjälpfiler i alla kulturer i Användargränssnittet. Innehåller **UICulture** element, som representerar en uppsättning hjälpfilerna för modulen i en angiven UI-kultur.

UICulture representerar en uppsättning hjälpfilerna för modulen i en angiven UI-kultur. Lägg till en **UICulture** element för varje UI-kultur där hjälpfilerna skrivs.

UICultureName innehåller språkkod för kultur för Användargränssnittet där hjälpfilerna skrivs.

UICultureVersion innehåller ett versionsnummer för 4 delar i ”N1. N2. N3. N4 ”tidsformat som representerar versionen av CAB-hjälpfilen i kultur för Användargränssnittet. Öka det här versionsnumret när du laddar upp ny hjälp CAB-filer i kultur för Användargränssnittet som anges av **UICultureName**. Mer information om det här värdet finns i ”Version Class (System)” i MSDN.