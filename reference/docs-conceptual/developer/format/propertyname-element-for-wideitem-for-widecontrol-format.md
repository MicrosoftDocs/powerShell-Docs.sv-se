---
title: PropertyName-element för WideItem för WideControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3d91d0e6-bf18-4587-b651-db66849e5df5
caps.latest.revision: 6
ms.openlocfilehash: 326880834cd82ab826aadc409cd7a8f21cd36824
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355883"
---
# <a name="propertyname-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="3562d-102">PropertyName-element för WideItem för WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="3562d-102">PropertyName Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="3562d-103">Anger egenskapen för det objekt vars värde visas i den bred vyn.</span><span class="sxs-lookup"><span data-stu-id="3562d-103">Specifies the property of the object whose value is displayed in the wide view.</span></span>

<span data-ttu-id="3562d-104">Konfigurations element (format) ViewDefinitions element (format) View-element (format) WideControl-element (format) WideEntries-element (format) WideEntry-element (format) WideItem element (format) PropertyName-element för WideItem (format)</span><span class="sxs-lookup"><span data-stu-id="3562d-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format) PropertyName Element for WideItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3562d-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="3562d-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3562d-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="3562d-106">Attributes and Elements</span></span>

<span data-ttu-id="3562d-107">I följande avsnitt beskrivs attributen, underordnade element och det överordnade elementet i `PropertyName`-elementet.</span><span class="sxs-lookup"><span data-stu-id="3562d-107">The following sections describe the attributes, child elements, and parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3562d-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="3562d-108">Attributes</span></span>

<span data-ttu-id="3562d-109">Ingen.</span><span class="sxs-lookup"><span data-stu-id="3562d-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3562d-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="3562d-110">Child Elements</span></span>

<span data-ttu-id="3562d-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="3562d-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="3562d-112">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="3562d-112">Parent Elements</span></span>

|<span data-ttu-id="3562d-113">Element</span><span class="sxs-lookup"><span data-stu-id="3562d-113">Element</span></span>|<span data-ttu-id="3562d-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="3562d-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3562d-115">WideItem-element (format)</span><span class="sxs-lookup"><span data-stu-id="3562d-115">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="3562d-116">Definierar egenskapen eller skriptet vars värde visas i den breda vyn.</span><span class="sxs-lookup"><span data-stu-id="3562d-116">Defines the property or script whose value is displayed in the wide view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="3562d-117">Text värde</span><span class="sxs-lookup"><span data-stu-id="3562d-117">Text Value</span></span>

<span data-ttu-id="3562d-118">Ange namnet på den egenskap vars värde visas.</span><span class="sxs-lookup"><span data-stu-id="3562d-118">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="3562d-119">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="3562d-119">Remarks</span></span>

<span data-ttu-id="3562d-120">Mer information om komponenterna i en bred vy finns i [skapa en bred vy](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="3562d-120">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="3562d-121">Exempel</span><span class="sxs-lookup"><span data-stu-id="3562d-121">Example</span></span>

<span data-ttu-id="3562d-122">I det här exemplet visas en bred vy som visar värdet för egenskapen ProcessName för objektet [system. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) .</span><span class="sxs-lookup"><span data-stu-id="3562d-122">This example shows a wide view that displays the value of the ProcessName property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
View>
  <Name>process</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>
    <WideEntries>
      <WideEntry>
        <WideItem>
          <PropertyName>ProcessName</PropertyName>
        </WideItem>
      </WideEntry>
    </WideEntries>
  </WideControl>
</View>

```

## <a name="see-also"></a><span data-ttu-id="3562d-123">Se även</span><span class="sxs-lookup"><span data-stu-id="3562d-123">See Also</span></span>

[<span data-ttu-id="3562d-124">WideItem-element (format)</span><span class="sxs-lookup"><span data-stu-id="3562d-124">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="3562d-125">Skapa en bred vy</span><span class="sxs-lookup"><span data-stu-id="3562d-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="3562d-126">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="3562d-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
