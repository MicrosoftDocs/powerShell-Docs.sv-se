---
title: Script block-element för WideItem för WideControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e00e8f36-76f2-49a0-9b02-3a2a7fceb2dd
caps.latest.revision: 8
ms.openlocfilehash: 6534e9dbfbe0dedf60dadd6467cff9ad9b447ba4
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72353846"
---
# <a name="scriptblock-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="f318d-102">ScriptBlock-element för WideItem för WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="f318d-102">ScriptBlock Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="f318d-103">Anger det skript vars värde visas i den breda vyn.</span><span class="sxs-lookup"><span data-stu-id="f318d-103">Specifies the script whose value is displayed in the wide view.</span></span>

<span data-ttu-id="f318d-104">Konfigurations element (format) ViewDefinitions element (format) View-element (format) WideControl-element (format) WideEntries-element (format) WideEntry-element (format) WideItem element (format) script block-element för WideItem (format)</span><span class="sxs-lookup"><span data-stu-id="f318d-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format) ScriptBlock Element for WideItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f318d-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="f318d-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToExecute</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f318d-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="f318d-106">Attributes and Elements</span></span>

<span data-ttu-id="f318d-107">I följande avsnitt beskrivs attributen, underordnade element och det överordnade elementet i `ScriptBlock`-elementet.</span><span class="sxs-lookup"><span data-stu-id="f318d-107">The following sections describe the attributes, child elements, and parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f318d-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="f318d-108">Attributes</span></span>

<span data-ttu-id="f318d-109">Ingen.</span><span class="sxs-lookup"><span data-stu-id="f318d-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f318d-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="f318d-110">Child Elements</span></span>

<span data-ttu-id="f318d-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="f318d-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f318d-112">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="f318d-112">Parent Elements</span></span>

|<span data-ttu-id="f318d-113">Element</span><span class="sxs-lookup"><span data-stu-id="f318d-113">Element</span></span>|<span data-ttu-id="f318d-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="f318d-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f318d-115">WideItem-element (format)</span><span class="sxs-lookup"><span data-stu-id="f318d-115">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="f318d-116">Definierar egenskapen eller skript blocket vars värde visas i den breda vyn.</span><span class="sxs-lookup"><span data-stu-id="f318d-116">Defines the property or script block whose value is displayed in the wide view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f318d-117">Textvärde</span><span class="sxs-lookup"><span data-stu-id="f318d-117">Text Value</span></span>

<span data-ttu-id="f318d-118">Ange det skript vars värde visas.</span><span class="sxs-lookup"><span data-stu-id="f318d-118">Specify the script whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="f318d-119">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="f318d-119">Remarks</span></span>

<span data-ttu-id="f318d-120">Mer information om komponenterna i en bred vy finns i [skapa en bred vy](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="f318d-120">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="f318d-121">Exempel</span><span class="sxs-lookup"><span data-stu-id="f318d-121">Example</span></span>

<span data-ttu-id="f318d-122">I det här exemplet visas ett `WideItem`-element som definierar ett skript vars värde visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="f318d-122">This example shows a `WideItem` element that defines a script whose value is displayed in the view.</span></span>

```xml
<WideItem>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
</WideItem>
```

## <a name="see-also"></a><span data-ttu-id="f318d-123">Se även</span><span class="sxs-lookup"><span data-stu-id="f318d-123">See Also</span></span>

[<span data-ttu-id="f318d-124">WideItem-element (format)</span><span class="sxs-lookup"><span data-stu-id="f318d-124">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="f318d-125">Skapa en bred vy</span><span class="sxs-lookup"><span data-stu-id="f318d-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="f318d-126">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="f318d-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
