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
ms.openlocfilehash: 3e2a113e120c61fab1ba76c4fd897ded67d13319
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/23/2020
ms.locfileid: "83810836"
---
# <a name="helpinfo-xml-schema"></a><span data-ttu-id="ff143-102">HelpInfo-XML-schema</span><span class="sxs-lookup"><span data-stu-id="ff143-102">HelpInfo XML Schema</span></span>

<span data-ttu-id="ff143-103">Det här avsnittet innehåller XML-schemat för uppdaterings bara hjälp information filer, vanligt vis kallade "HelpInfo XML Files".</span><span class="sxs-lookup"><span data-stu-id="ff143-103">This topic contains the XML schema for Updatable Help Information files, commonly known as "HelpInfo XML files."</span></span>

## <a name="helpinfo-xml-schema"></a><span data-ttu-id="ff143-104">HelpInfo-XML-schema</span><span class="sxs-lookup"><span data-stu-id="ff143-104">HelpInfo XML Schema</span></span>

<span data-ttu-id="ff143-105">HelpInfo XML-filer baseras på följande XML-schema.</span><span class="sxs-lookup"><span data-stu-id="ff143-105">HelpInfo XML files are based on the following XML schema.</span></span>

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

## <a name="helpinfo-xml-elements"></a><span data-ttu-id="ff143-106">HelpInfo XML-element</span><span class="sxs-lookup"><span data-stu-id="ff143-106">HelpInfo XML Elements</span></span>

<span data-ttu-id="ff143-107">XML-filen HelpInfo innehåller följande element.</span><span class="sxs-lookup"><span data-stu-id="ff143-107">The HelpInfo XML file includes the following elements.</span></span>

<span data-ttu-id="ff143-108">HelpContentURI innehåller URI för platsen för hjälpens CAB-filer för modulen.</span><span class="sxs-lookup"><span data-stu-id="ff143-108">HelpContentURI Contains the URI of the location of the help CAB files for the module.</span></span> <span data-ttu-id="ff143-109">URI: n måste börja med http eller https.</span><span class="sxs-lookup"><span data-stu-id="ff143-109">The URI must begin with "http" or "https".</span></span> <span data-ttu-id="ff143-110">URI: n måste ange en Internet plats, men får inte innehålla CAB-filnamn.</span><span class="sxs-lookup"><span data-stu-id="ff143-110">The URI should specify an Internet location, but must not include the CAB file name.</span></span> <span data-ttu-id="ff143-111">**HelpContentURI** -värdet kan vara samma eller något annat än värdet för **HelpInfoURI** .</span><span class="sxs-lookup"><span data-stu-id="ff143-111">The **HelpContentURI** value can be the  same or different from the **HelpInfoURI** value.</span></span>

<span data-ttu-id="ff143-112">SupportedUICultures representerar modulens hjälpfiler i alla UI-kulturer.</span><span class="sxs-lookup"><span data-stu-id="ff143-112">SupportedUICultures Represents the module help files in all UI cultures.</span></span> <span data-ttu-id="ff143-113">Innehåller **värdet** -element som representerar en uppsättning hjälpfiler för modulen i en angiven kultur för användar gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="ff143-113">Contains **UICulture** elements, each of which represents a set of help files for the module in a specified UI culture.</span></span>

<span data-ttu-id="ff143-114">Värdet representerar en uppsättning hjälpfiler för modulen i en angiven användar gränssnitts kultur.</span><span class="sxs-lookup"><span data-stu-id="ff143-114">UICulture Represents a set of help files for the module in a specified UI culture.</span></span> <span data-ttu-id="ff143-115">Lägg till ett **värdet** -element för varje gränssnitts kultur där hjälpfilerna skrivs.</span><span class="sxs-lookup"><span data-stu-id="ff143-115">Add a **UICulture** element for each UI culture in which the help files are written.</span></span>

<span data-ttu-id="ff143-116">UICultureName innehåller språk koden för den GRÄNSSNITTs kultur som hjälpfilerna skrivs till.</span><span class="sxs-lookup"><span data-stu-id="ff143-116">UICultureName Contains the language code for the UI culture in which the help files are written.</span></span>

<span data-ttu-id="ff143-117">UICultureVersion innehåller 4 delar av versions nummer i "N1. N2. N3. N4 "-format som representerar versionen av CAB-filen för hjälp i användar gränssnitts kulturen.</span><span class="sxs-lookup"><span data-stu-id="ff143-117">UICultureVersion Contains a 4-part version number in "N1.N2.N3.N4" format that represents the version of the help CAB file in the UI culture.</span></span> <span data-ttu-id="ff143-118">Öka det här versions numret när du överför nya CAB-filer för hjälpfiler i användar gränssnitts kulturen som anges av **UICultureName**.</span><span class="sxs-lookup"><span data-stu-id="ff143-118">Increment this version number whenever you upload new help CAB files in the UI culture that is specified by **UICultureName**.</span></span> <span data-ttu-id="ff143-119">Mer information om det här värdet finns i "versions klass (system)" i MSDN.</span><span class="sxs-lookup"><span data-stu-id="ff143-119">For more information about this value, see "Version Class (System)" in MSDN.</span></span>
