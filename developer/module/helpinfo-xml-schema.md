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
# <a name="helpinfo-xml-schema"></a><span data-ttu-id="c2332-102">HelpInfo-XML-schema</span><span class="sxs-lookup"><span data-stu-id="c2332-102">HelpInfo XML Schema</span></span>

<span data-ttu-id="c2332-103">Det här avsnittet innehåller XML-schemat för uppdateringsbar hjälp Information filer, ofta kallade ”HelpInfo XML-filer”.</span><span class="sxs-lookup"><span data-stu-id="c2332-103">This topic contains the XML schema for Updatable Help Information files, commonly known as "HelpInfo XML files."</span></span>

## <a name="helpinfo-xml-schema"></a><span data-ttu-id="c2332-104">HelpInfo-XML-schema</span><span class="sxs-lookup"><span data-stu-id="c2332-104">HelpInfo XML Schema</span></span>

<span data-ttu-id="c2332-105">HelpInfo XML-filer baserat på följande XML-schema.</span><span class="sxs-lookup"><span data-stu-id="c2332-105">HelpInfo XML files are based on the following XML schema.</span></span>

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

## <a name="helpinfo-xml-elements"></a><span data-ttu-id="c2332-106">HelpInfo XML-element</span><span class="sxs-lookup"><span data-stu-id="c2332-106">HelpInfo XML Elements</span></span>

<span data-ttu-id="c2332-107">HelpInfo XML-filen innehåller följande element.</span><span class="sxs-lookup"><span data-stu-id="c2332-107">The HelpInfo XML file includes the following elements.</span></span>

<span data-ttu-id="c2332-108">HelpContentURI innehåller URI för platsen för hjälp CAB-filer för modulen.</span><span class="sxs-lookup"><span data-stu-id="c2332-108">HelpContentURI Contains the URI of the location of the help CAB files for the module.</span></span> <span data-ttu-id="c2332-109">URI: N måste börja med ”http” eller ”https”.</span><span class="sxs-lookup"><span data-stu-id="c2332-109">The URI must begin with "http" or "https".</span></span> <span data-ttu-id="c2332-110">URI: N ska ange en plats på Internet, men får inte innehålla namnet på CAB-filen.</span><span class="sxs-lookup"><span data-stu-id="c2332-110">The URI should specify an Internet location, but must not include the CAB file name.</span></span> <span data-ttu-id="c2332-111">Den **HelpContentURI** värdet kan vara samma eller olika från den **HelpInfoURI** värde.</span><span class="sxs-lookup"><span data-stu-id="c2332-111">The **HelpContentURI** value can be the  same or different from the **HelpInfoURI** value.</span></span>

<span data-ttu-id="c2332-112">SupportedUICultures representerar modulen hjälpfiler i alla kulturer i Användargränssnittet.</span><span class="sxs-lookup"><span data-stu-id="c2332-112">SupportedUICultures Represents the module help files in all UI cultures.</span></span> <span data-ttu-id="c2332-113">Innehåller **UICulture** element, som representerar en uppsättning hjälpfilerna för modulen i en angiven UI-kultur.</span><span class="sxs-lookup"><span data-stu-id="c2332-113">Contains **UICulture** elements, each of which represents a set of help files for the module in a specified UI culture.</span></span>

<span data-ttu-id="c2332-114">UICulture representerar en uppsättning hjälpfilerna för modulen i en angiven UI-kultur.</span><span class="sxs-lookup"><span data-stu-id="c2332-114">UICulture Represents a set of help files for the module in a specified UI culture.</span></span> <span data-ttu-id="c2332-115">Lägg till en **UICulture** element för varje UI-kultur där hjälpfilerna skrivs.</span><span class="sxs-lookup"><span data-stu-id="c2332-115">Add a **UICulture** element for each UI culture in which the help files are written.</span></span>

<span data-ttu-id="c2332-116">UICultureName innehåller språkkod för kultur för Användargränssnittet där hjälpfilerna skrivs.</span><span class="sxs-lookup"><span data-stu-id="c2332-116">UICultureName Contains the language code for the UI culture in which the help files are written.</span></span>

<span data-ttu-id="c2332-117">UICultureVersion innehåller ett versionsnummer för 4 delar i ”N1. N2. N3. N4 ”tidsformat som representerar versionen av CAB-hjälpfilen i kultur för Användargränssnittet.</span><span class="sxs-lookup"><span data-stu-id="c2332-117">UICultureVersion Contains a 4-part version number in "N1.N2.N3.N4" format that represents the version of the help CAB file in the UI culture.</span></span> <span data-ttu-id="c2332-118">Öka det här versionsnumret när du laddar upp ny hjälp CAB-filer i kultur för Användargränssnittet som anges av **UICultureName**.</span><span class="sxs-lookup"><span data-stu-id="c2332-118">Increment this version number whenever you upload new help CAB files in the UI culture that is specified by **UICultureName**.</span></span> <span data-ttu-id="c2332-119">Mer information om det här värdet finns i ”Version Class (System)” i MSDN.</span><span class="sxs-lookup"><span data-stu-id="c2332-119">For more information about this value, see "Version Class (System)" in MSDN.</span></span>