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
# <a name="helpinfo-xml-schema"></a><span data-ttu-id="47091-103">HelpInfo-XML-schema</span><span class="sxs-lookup"><span data-stu-id="47091-103">HelpInfo XML Schema</span></span>

<span data-ttu-id="47091-104">Det här avsnittet innehåller XML-schemat för uppdaterings bara hjälp information filer, vanligt vis kallade "HelpInfo XML Files".</span><span class="sxs-lookup"><span data-stu-id="47091-104">This topic contains the XML schema for Updatable Help Information files, commonly known as "HelpInfo XML files."</span></span>

## <a name="helpinfo-xml-schema"></a><span data-ttu-id="47091-105">HelpInfo-XML-schema</span><span class="sxs-lookup"><span data-stu-id="47091-105">HelpInfo XML Schema</span></span>

<span data-ttu-id="47091-106">HelpInfo XML-filer baseras på följande XML-schema.</span><span class="sxs-lookup"><span data-stu-id="47091-106">HelpInfo XML files are based on the following XML schema.</span></span>

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

## <a name="helpinfo-xml-elements"></a><span data-ttu-id="47091-107">HelpInfo XML-element</span><span class="sxs-lookup"><span data-stu-id="47091-107">HelpInfo XML Elements</span></span>

<span data-ttu-id="47091-108">XML-filen HelpInfo innehåller följande element.</span><span class="sxs-lookup"><span data-stu-id="47091-108">The HelpInfo XML file includes the following elements.</span></span>

- <span data-ttu-id="47091-109">**HelpContentURI** – innehåller URI för platsen för hjälpens CAB-filer för modulen.</span><span class="sxs-lookup"><span data-stu-id="47091-109">**HelpContentURI** - Contains the URI of the location of the help CAB files for the module.</span></span> <span data-ttu-id="47091-110">URI: n måste börja med http eller https.</span><span class="sxs-lookup"><span data-stu-id="47091-110">The URI must begin with "http" or "https".</span></span> <span data-ttu-id="47091-111">URI: n måste ange en Internet plats, men får inte innehålla CAB-filnamn.</span><span class="sxs-lookup"><span data-stu-id="47091-111">The URI should specify an internet location, but must not include the CAB filename.</span></span> <span data-ttu-id="47091-112">**HelpContentURI** -värdet kan vara samma eller något annat än värdet för **HelpInfoURI** .</span><span class="sxs-lookup"><span data-stu-id="47091-112">The **HelpContentURI** value can be the same or different from the **HelpInfoURI** value.</span></span>

- <span data-ttu-id="47091-113">**SupportedUICultures** – visar modulens hjälpfiler i alla UI-kulturer.</span><span class="sxs-lookup"><span data-stu-id="47091-113">**SupportedUICultures** - Represents the module help files in all UI cultures.</span></span> <span data-ttu-id="47091-114">Innehåller **värdet** -element som representerar en uppsättning hjälpfiler för modulen i en angiven kultur för användar gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="47091-114">Contains **UICulture** elements, each of which represents a set of help files for the module in a specified UI culture.</span></span>

- <span data-ttu-id="47091-115">**Värdet** – representerar en uppsättning hjälpfiler för modulen i en angiven användar gränssnitts kultur.</span><span class="sxs-lookup"><span data-stu-id="47091-115">**UICulture** - Represents a set of help files for the module in a specified UI culture.</span></span> <span data-ttu-id="47091-116">Lägg till ett **värdet** -element för varje gränssnitts kultur där hjälpfilerna skrivs.</span><span class="sxs-lookup"><span data-stu-id="47091-116">Add a **UICulture** element for each UI culture in which the help files are written.</span></span>

- <span data-ttu-id="47091-117">**UICultureName** – innehåller språk koden för den gränssnitts kultur som hjälpfilerna skrivs till.</span><span class="sxs-lookup"><span data-stu-id="47091-117">**UICultureName** - Contains the language code for the UI culture in which the help files are written.</span></span>

- <span data-ttu-id="47091-118">**UICultureVersion** – innehåller ett 4-delar av versions numret i "N1. N2. N3. N4 "-format som representerar versionen av CAB-filen för hjälp i användar gränssnitts kulturen.</span><span class="sxs-lookup"><span data-stu-id="47091-118">**UICultureVersion** - Contains a 4-part version number in "N1.N2.N3.N4" format that represents the version of the help CAB file in the UI culture.</span></span> <span data-ttu-id="47091-119">Öka det här versions numret när du överför nya CAB-filer för hjälpfiler i användar gränssnitts kulturen som anges av **UICultureName**.</span><span class="sxs-lookup"><span data-stu-id="47091-119">Increment this version number whenever you upload new help CAB files in the UI culture that is specified by **UICultureName**.</span></span> <span data-ttu-id="47091-120">Mer information om det här värdet finns i [versions klass](/dotnet/api/system.version).</span><span class="sxs-lookup"><span data-stu-id="47091-120">For more information about this value, see [Version Class](/dotnet/api/system.version).</span></span>
