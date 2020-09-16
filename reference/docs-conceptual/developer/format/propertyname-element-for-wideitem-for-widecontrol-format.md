---
title: PropertyName-element för WideItem för WideControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 7728f960a67faa99eaafb4a4934674e119b8af27
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780482"
---
# <a name="propertyname-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="f50f5-102">PropertyName-element för WideItem för WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="f50f5-102">PropertyName Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="f50f5-103">Anger egenskapen för det objekt vars värde visas i den bred vyn.</span><span class="sxs-lookup"><span data-stu-id="f50f5-103">Specifies the property of the object whose value is displayed in the wide view.</span></span>

<span data-ttu-id="f50f5-104">Konfigurations element (format) ViewDefinitions element (format) View-element (format) WideControl-element (format) WideEntries-element (format) WideEntry-element (format) WideItem element (format) PropertyName-element för WideItem (format)</span><span class="sxs-lookup"><span data-stu-id="f50f5-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format) PropertyName Element for WideItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f50f5-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="f50f5-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f50f5-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="f50f5-106">Attributes and Elements</span></span>

<span data-ttu-id="f50f5-107">I följande avsnitt beskrivs attributen, underordnade element och `PropertyName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="f50f5-107">The following sections describe the attributes, child elements, and parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f50f5-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="f50f5-108">Attributes</span></span>

<span data-ttu-id="f50f5-109">Inga.</span><span class="sxs-lookup"><span data-stu-id="f50f5-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f50f5-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="f50f5-110">Child Elements</span></span>

<span data-ttu-id="f50f5-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="f50f5-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f50f5-112">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="f50f5-112">Parent Elements</span></span>

|<span data-ttu-id="f50f5-113">Element</span><span class="sxs-lookup"><span data-stu-id="f50f5-113">Element</span></span>|<span data-ttu-id="f50f5-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="f50f5-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f50f5-115">WideItem-element (format)</span><span class="sxs-lookup"><span data-stu-id="f50f5-115">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="f50f5-116">Definierar egenskapen eller skriptet vars värde visas i den breda vyn.</span><span class="sxs-lookup"><span data-stu-id="f50f5-116">Defines the property or script whose value is displayed in the wide view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f50f5-117">Textvärde</span><span class="sxs-lookup"><span data-stu-id="f50f5-117">Text Value</span></span>

<span data-ttu-id="f50f5-118">Ange namnet på den egenskap vars värde visas.</span><span class="sxs-lookup"><span data-stu-id="f50f5-118">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="f50f5-119">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="f50f5-119">Remarks</span></span>

<span data-ttu-id="f50f5-120">Mer information om komponenterna i en bred vy finns i [skapa en bred vy](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="f50f5-120">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="f50f5-121">Exempel</span><span class="sxs-lookup"><span data-stu-id="f50f5-121">Example</span></span>

<span data-ttu-id="f50f5-122">I det här exemplet visas en bred vy som visar värdet för egenskapen ProcessName för objektet [system. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) .</span><span class="sxs-lookup"><span data-stu-id="f50f5-122">This example shows a wide view that displays the value of the ProcessName property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="f50f5-123">Se även</span><span class="sxs-lookup"><span data-stu-id="f50f5-123">See Also</span></span>

[<span data-ttu-id="f50f5-124">WideItem-element (format)</span><span class="sxs-lookup"><span data-stu-id="f50f5-124">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="f50f5-125">Skapa en bred vy</span><span class="sxs-lookup"><span data-stu-id="f50f5-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="f50f5-126">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="f50f5-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
