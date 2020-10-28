---
ms.date: 09/13/2016
ms.topic: reference
title: PropertyName-element för WideItem för WideControl (format)
description: PropertyName-element för WideItem för WideControl (format)
ms.openlocfilehash: 1d4d5eaf7708dfbd7997122fac156a36487538ea
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92665625"
---
# <a name="propertyname-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="015a6-103">PropertyName-element för WideItem för WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="015a6-103">PropertyName Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="015a6-104">Anger egenskapen för det objekt vars värde visas i den bred vyn.</span><span class="sxs-lookup"><span data-stu-id="015a6-104">Specifies the property of the object whose value is displayed in the wide view.</span></span>

<span data-ttu-id="015a6-105">Konfigurations element (format) ViewDefinitions element (format) View-element (format) WideControl-element (format) WideEntries-element (format) WideEntry-element (format) WideItem element (format) PropertyName-element för WideItem (format)</span><span class="sxs-lookup"><span data-stu-id="015a6-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format) PropertyName Element for WideItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="015a6-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="015a6-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="015a6-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="015a6-107">Attributes and Elements</span></span>

<span data-ttu-id="015a6-108">I följande avsnitt beskrivs attributen, underordnade element och `PropertyName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="015a6-108">The following sections describe the attributes, child elements, and parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="015a6-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="015a6-109">Attributes</span></span>

<span data-ttu-id="015a6-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="015a6-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="015a6-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="015a6-111">Child Elements</span></span>

<span data-ttu-id="015a6-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="015a6-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="015a6-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="015a6-113">Parent Elements</span></span>

|<span data-ttu-id="015a6-114">Element</span><span class="sxs-lookup"><span data-stu-id="015a6-114">Element</span></span>|<span data-ttu-id="015a6-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="015a6-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="015a6-116">WideItem-element (format)</span><span class="sxs-lookup"><span data-stu-id="015a6-116">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="015a6-117">Definierar egenskapen eller skriptet vars värde visas i den breda vyn.</span><span class="sxs-lookup"><span data-stu-id="015a6-117">Defines the property or script whose value is displayed in the wide view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="015a6-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="015a6-118">Text Value</span></span>

<span data-ttu-id="015a6-119">Ange namnet på den egenskap vars värde visas.</span><span class="sxs-lookup"><span data-stu-id="015a6-119">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="015a6-120">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="015a6-120">Remarks</span></span>

<span data-ttu-id="015a6-121">Mer information om komponenterna i en bred vy finns i [skapa en bred vy](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="015a6-121">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="015a6-122">Exempel</span><span class="sxs-lookup"><span data-stu-id="015a6-122">Example</span></span>

<span data-ttu-id="015a6-123">I det här exemplet visas en bred vy som visar värdet för egenskapen ProcessName för objektet [system. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) .</span><span class="sxs-lookup"><span data-stu-id="015a6-123">This example shows a wide view that displays the value of the ProcessName property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="015a6-124">Se även</span><span class="sxs-lookup"><span data-stu-id="015a6-124">See Also</span></span>

[<span data-ttu-id="015a6-125">WideItem-element (format)</span><span class="sxs-lookup"><span data-stu-id="015a6-125">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="015a6-126">Skapa en bred vy</span><span class="sxs-lookup"><span data-stu-id="015a6-126">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="015a6-127">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="015a6-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
