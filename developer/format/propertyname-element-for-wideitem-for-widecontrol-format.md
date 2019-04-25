---
title: PropertyName-Element för WideItem för WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3d91d0e6-bf18-4587-b651-db66849e5df5
caps.latest.revision: 6
ms.openlocfilehash: 326880834cd82ab826aadc409cd7a8f21cd36824
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064653"
---
# <a name="propertyname-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="e960f-102">PropertyName-element för WideItem för WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="e960f-102">PropertyName Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="e960f-103">Anger egenskapen för objektet vars värde visas i bred vy.</span><span class="sxs-lookup"><span data-stu-id="e960f-103">Specifies the property of the object whose value is displayed in the wide view.</span></span>

<span data-ttu-id="e960f-104">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format) PropertyName konfigurationselement för WideItem (Format)</span><span class="sxs-lookup"><span data-stu-id="e960f-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format) PropertyName Element for WideItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e960f-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="e960f-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e960f-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="e960f-106">Attributes and Elements</span></span>

<span data-ttu-id="e960f-107">I följande avsnitt beskrivs de attribut och underordnade element överordnade elementet i den `PropertyName` element.</span><span class="sxs-lookup"><span data-stu-id="e960f-107">The following sections describe the attributes, child elements, and parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e960f-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="e960f-108">Attributes</span></span>

<span data-ttu-id="e960f-109">Ingen.</span><span class="sxs-lookup"><span data-stu-id="e960f-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e960f-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="e960f-110">Child Elements</span></span>

<span data-ttu-id="e960f-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="e960f-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e960f-112">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="e960f-112">Parent Elements</span></span>

|<span data-ttu-id="e960f-113">Element</span><span class="sxs-lookup"><span data-stu-id="e960f-113">Element</span></span>|<span data-ttu-id="e960f-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e960f-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e960f-115">WideItem Element (Format)</span><span class="sxs-lookup"><span data-stu-id="e960f-115">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="e960f-116">Definierar egenskapen eller skript som vars värde visas i bred vy.</span><span class="sxs-lookup"><span data-stu-id="e960f-116">Defines the property or script whose value is displayed in the wide view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e960f-117">Textvärde</span><span class="sxs-lookup"><span data-stu-id="e960f-117">Text Value</span></span>

<span data-ttu-id="e960f-118">Ange namnet på egenskapen vars värde visas.</span><span class="sxs-lookup"><span data-stu-id="e960f-118">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="e960f-119">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="e960f-119">Remarks</span></span>

<span data-ttu-id="e960f-120">Mer information om komponenter för en bred vy finns i [skapar en bred vy](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="e960f-120">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="e960f-121">Exempel</span><span class="sxs-lookup"><span data-stu-id="e960f-121">Example</span></span>

<span data-ttu-id="e960f-122">Det här exemplet visar en bred vy som visar värdet för egenskapen ProcessName för den [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objekt.</span><span class="sxs-lookup"><span data-stu-id="e960f-122">This example shows a wide view that displays the value of the ProcessName property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="e960f-123">Se även</span><span class="sxs-lookup"><span data-stu-id="e960f-123">See Also</span></span>

[<span data-ttu-id="e960f-124">WideItem Element (Format)</span><span class="sxs-lookup"><span data-stu-id="e960f-124">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="e960f-125">Skapa en bred vy</span><span class="sxs-lookup"><span data-stu-id="e960f-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="e960f-126">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="e960f-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
