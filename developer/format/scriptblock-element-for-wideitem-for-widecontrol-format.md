---
title: ScriptBlock Element för WideItem för WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e00e8f36-76f2-49a0-9b02-3a2a7fceb2dd
caps.latest.revision: 8
ms.openlocfilehash: 6534e9dbfbe0dedf60dadd6467cff9ad9b447ba4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064211"
---
# <a name="scriptblock-element-for-wideitem-for-widecontrol-format"></a><span data-ttu-id="4085b-102">ScriptBlock-element för WideItem för WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="4085b-102">ScriptBlock Element for WideItem for WideControl (Format)</span></span>

<span data-ttu-id="4085b-103">Anger skriptet vars värde visas i bred vy.</span><span class="sxs-lookup"><span data-stu-id="4085b-103">Specifies the script whose value is displayed in the wide view.</span></span>

<span data-ttu-id="4085b-104">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format) ScriptBlock konfigurationselement för WideItem (Format)</span><span class="sxs-lookup"><span data-stu-id="4085b-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) WideItem Element (Format) ScriptBlock Element for WideItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4085b-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="4085b-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToExecute</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4085b-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="4085b-106">Attributes and Elements</span></span>

<span data-ttu-id="4085b-107">I följande avsnitt beskrivs de attribut och underordnade element överordnade elementet i den `ScriptBlock` element.</span><span class="sxs-lookup"><span data-stu-id="4085b-107">The following sections describe the attributes, child elements, and parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4085b-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="4085b-108">Attributes</span></span>

<span data-ttu-id="4085b-109">Ingen.</span><span class="sxs-lookup"><span data-stu-id="4085b-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4085b-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="4085b-110">Child Elements</span></span>

<span data-ttu-id="4085b-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="4085b-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4085b-112">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="4085b-112">Parent Elements</span></span>

|<span data-ttu-id="4085b-113">Element</span><span class="sxs-lookup"><span data-stu-id="4085b-113">Element</span></span>|<span data-ttu-id="4085b-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="4085b-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4085b-115">WideItem Element (Format)</span><span class="sxs-lookup"><span data-stu-id="4085b-115">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="4085b-116">Definierar egenskapen eller skript blocket vars värde visas i bred vy.</span><span class="sxs-lookup"><span data-stu-id="4085b-116">Defines the property or script block whose value is displayed in the wide view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="4085b-117">Textvärde</span><span class="sxs-lookup"><span data-stu-id="4085b-117">Text Value</span></span>

<span data-ttu-id="4085b-118">Ange skriptet vars värde visas.</span><span class="sxs-lookup"><span data-stu-id="4085b-118">Specify the script whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="4085b-119">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="4085b-119">Remarks</span></span>

<span data-ttu-id="4085b-120">Mer information om komponenter för en bred vy finns i [skapar en bred vy](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="4085b-120">For more information about the components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="4085b-121">Exempel</span><span class="sxs-lookup"><span data-stu-id="4085b-121">Example</span></span>

<span data-ttu-id="4085b-122">Det här exemplet visar en `WideItem` -element som definierar ett skript som vars värde visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="4085b-122">This example shows a `WideItem` element that defines a script whose value is displayed in the view.</span></span>

```xml
<WideItem>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
</WideItem>
```

## <a name="see-also"></a><span data-ttu-id="4085b-123">Se även</span><span class="sxs-lookup"><span data-stu-id="4085b-123">See Also</span></span>

[<span data-ttu-id="4085b-124">WideItem Element (Format)</span><span class="sxs-lookup"><span data-stu-id="4085b-124">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="4085b-125">Skapa en bred vy</span><span class="sxs-lookup"><span data-stu-id="4085b-125">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="4085b-126">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="4085b-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
