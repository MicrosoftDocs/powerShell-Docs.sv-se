---
title: Visa Element (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d837d5d4-ed2e-4d84-a306-0b5d2ad2d0bf
caps.latest.revision: 24
ms.openlocfilehash: 2361c1117757569bef0815018c75764430a9e7a8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846916"
---
# <a name="view-element-format"></a><span data-ttu-id="51a59-102">View-element (format)</span><span class="sxs-lookup"><span data-stu-id="51a59-102">View Element (Format)</span></span>

<span data-ttu-id="51a59-103">Definierar en vy som visar en eller flera .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="51a59-103">Defines a view that displays one or more .NET objects.</span></span> <span data-ttu-id="51a59-104">Det finns ingen gräns för antal vyer som kan definieras i en fil med formatering.</span><span class="sxs-lookup"><span data-stu-id="51a59-104">There is no limit to the number of views that can be defined in a formatting file.</span></span>

<span data-ttu-id="51a59-105">Elementet (Format) ViewDefinitions Element (Format) visa konfigurationselement (Format)</span><span class="sxs-lookup"><span data-stu-id="51a59-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="51a59-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="51a59-106">Syntax</span></span>

```xml
<View>
  <Name>Friendly name of view.</Name>
  <ViewSelectedBy>...</ViewSelectedBy>
  <Controls>...</Controls>
  <GroupBy>...</GroupBy>
  <TableControl>...</TableControl>
  <ListControl>...</ListControl>
  <WideControl>...</WideControl>
  <CustomControl>...</CustomControl>
</View>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="51a59-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="51a59-107">Attributes and Elements</span></span>

<span data-ttu-id="51a59-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `View` element.</span><span class="sxs-lookup"><span data-stu-id="51a59-108">The following sections describe the attributes, child elements, and the parent element of the `View` element.</span></span> <span data-ttu-id="51a59-109">Du måste ange endast en av kontroll underordnade element och du måste ange namnet på vyn och de objekt som använder vyn.</span><span class="sxs-lookup"><span data-stu-id="51a59-109">You must specify one and only one of the control child elements, and you must specify the name of the view and the objects that use the view.</span></span> <span data-ttu-id="51a59-110">Definiera anpassade kontroller, gruppering objekt och ange om vyn är out-of-band är valfria.</span><span class="sxs-lookup"><span data-stu-id="51a59-110">Defining custom controls, how to group objects, and specifying if the view is out-of-band are optional.</span></span>

### <a name="attributes"></a><span data-ttu-id="51a59-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="51a59-111">Attributes</span></span>

<span data-ttu-id="51a59-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="51a59-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="51a59-113">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="51a59-113">Child Elements</span></span>

|<span data-ttu-id="51a59-114">Element</span><span class="sxs-lookup"><span data-stu-id="51a59-114">Element</span></span>|<span data-ttu-id="51a59-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="51a59-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="51a59-116">Kontroller Element för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="51a59-116">Controls Element for View (Format)</span></span>](./controls-element-for-view-format.md)|<span data-ttu-id="51a59-117">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="51a59-117">Optional element.</span></span><br /><br /> <span data-ttu-id="51a59-118">Definierar en uppsättning kontroller som kan refereras av deras namn från i vyn.</span><span class="sxs-lookup"><span data-stu-id="51a59-118">Defines a set of controls that can be referenced by their name from within the view.</span></span>|
|[<span data-ttu-id="51a59-119">Anpassad kontroll Element (Format)</span><span class="sxs-lookup"><span data-stu-id="51a59-119">CustomControl Element (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="51a59-120">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="51a59-120">Optional element.</span></span><br /><br /> <span data-ttu-id="51a59-121">Definierar en anpassad kontroll format för vyn.</span><span class="sxs-lookup"><span data-stu-id="51a59-121">Defines a custom control format for the view.</span></span>|
|[<span data-ttu-id="51a59-122">GroupBy-Element för Visa (Format)</span><span class="sxs-lookup"><span data-stu-id="51a59-122">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="51a59-123">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="51a59-123">Optional element.</span></span><br /><br /> <span data-ttu-id="51a59-124">Definierar hur medlemmarna i .NET-objekt grupperas.</span><span class="sxs-lookup"><span data-stu-id="51a59-124">Defines how the members of the .NET objects are grouped.</span></span>|
|[<span data-ttu-id="51a59-125">ListControl Element (Format)</span><span class="sxs-lookup"><span data-stu-id="51a59-125">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)|<span data-ttu-id="51a59-126">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="51a59-126">Optional element.</span></span><br /><br /> <span data-ttu-id="51a59-127">Definierar ett listformat för vyn.</span><span class="sxs-lookup"><span data-stu-id="51a59-127">Defines a list format for the view.</span></span>|
|[<span data-ttu-id="51a59-128">Namnelement för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="51a59-128">Name Element for View (Format)</span></span>](./name-element-for-view-format.md)|<span data-ttu-id="51a59-129">Element som krävs.</span><span class="sxs-lookup"><span data-stu-id="51a59-129">Required element.</span></span><br /><br /> <span data-ttu-id="51a59-130">Anger namnet som refererar till vyn.</span><span class="sxs-lookup"><span data-stu-id="51a59-130">Specifies the name used to reference the view.</span></span>|
|[<span data-ttu-id="51a59-131">TableControl Element (Format)</span><span class="sxs-lookup"><span data-stu-id="51a59-131">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="51a59-132">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="51a59-132">Optional element.</span></span><br /><br /> <span data-ttu-id="51a59-133">Definierar ett tabellformat för vyn.</span><span class="sxs-lookup"><span data-stu-id="51a59-133">Defines a table format for the view.</span></span>|
|[<span data-ttu-id="51a59-134">ViewSelectedBy Element för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="51a59-134">ViewSelectedBy Element for View (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="51a59-135">Element som krävs.</span><span class="sxs-lookup"><span data-stu-id="51a59-135">Required element.</span></span><br /><br /> <span data-ttu-id="51a59-136">Definierar de .NET-objekt som den här vyn visas.</span><span class="sxs-lookup"><span data-stu-id="51a59-136">Defines the .NET objects that this view displays.</span></span>|
|[<span data-ttu-id="51a59-137">WideControl Element (Format)</span><span class="sxs-lookup"><span data-stu-id="51a59-137">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="51a59-138">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="51a59-138">Optional element.</span></span><br /><br /> <span data-ttu-id="51a59-139">Definierar en bred (enstaka värde) listformat för vyn.</span><span class="sxs-lookup"><span data-stu-id="51a59-139">Defines a wide (single value) list format for the view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="51a59-140">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="51a59-140">Parent Elements</span></span>

|<span data-ttu-id="51a59-141">Element</span><span class="sxs-lookup"><span data-stu-id="51a59-141">Element</span></span>|<span data-ttu-id="51a59-142">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="51a59-142">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="51a59-143">ViewDefinitions Element (Format)</span><span class="sxs-lookup"><span data-stu-id="51a59-143">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)|<span data-ttu-id="51a59-144">Definierar de vyer som används för att visa objekt.</span><span class="sxs-lookup"><span data-stu-id="51a59-144">Defines the views used to display objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="51a59-145">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="51a59-145">Remarks</span></span>

<span data-ttu-id="51a59-146">Mer information om komponenter av olika vyer och anpassade kontroller finns i följande avsnitt:</span><span class="sxs-lookup"><span data-stu-id="51a59-146">For more information about the components of different views and custom controls, see the following topics:</span></span>

- [<span data-ttu-id="51a59-147">Tabell visa komponenter</span><span class="sxs-lookup"><span data-stu-id="51a59-147">Table View Components</span></span>](./creating-a-table-view.md)

- [<span data-ttu-id="51a59-148">Listan Visa komponenter</span><span class="sxs-lookup"><span data-stu-id="51a59-148">List View Components</span></span>](./creating-a-list-view.md)

- [<span data-ttu-id="51a59-149">Bred vy komponenter</span><span class="sxs-lookup"><span data-stu-id="51a59-149">Wide View Components</span></span>](./creating-a-wide-view.md)

- [<span data-ttu-id="51a59-150">Anpassade kontroller</span><span class="sxs-lookup"><span data-stu-id="51a59-150">Custom Controls</span></span>](./creating-custom-controls.md)

## <a name="example"></a><span data-ttu-id="51a59-151">Exempel</span><span class="sxs-lookup"><span data-stu-id="51a59-151">Example</span></span>

<span data-ttu-id="51a59-152">Det här exemplet visar en `View` -element som definierar en tabellvy för den [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) objekt.</span><span class="sxs-lookup"><span data-stu-id="51a59-152">This example shows a `View` element that defines a table view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

```xml
<ViewDefinitions>
  <View>
    <Name>service</Name>
    <ViewSelectedBy>
      <TypeName>System.ServiceProcess.ServiceController</TypeName>
    </ViewSelectedBy>
    <TableControl>...</TableControl>
  </View>
</ViewDefinitions>

```

## <a name="see-also"></a><span data-ttu-id="51a59-153">Se även</span><span class="sxs-lookup"><span data-stu-id="51a59-153">See Also</span></span>

[<span data-ttu-id="51a59-154">ViewDefinitions Element (Format)</span><span class="sxs-lookup"><span data-stu-id="51a59-154">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)

[<span data-ttu-id="51a59-155">Namnelement för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="51a59-155">Name Element for View (Format)</span></span>](./name-element-for-view-format.md)

[<span data-ttu-id="51a59-156">ViewSelectedBy Element (Format)</span><span class="sxs-lookup"><span data-stu-id="51a59-156">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="51a59-157">Kontroller Element för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="51a59-157">Controls Element for View (Format)</span></span>](./controls-element-for-view-format.md)

[<span data-ttu-id="51a59-158">GroupBy-Element för Visa (Format)</span><span class="sxs-lookup"><span data-stu-id="51a59-158">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="51a59-159">TableControl Element (Format)</span><span class="sxs-lookup"><span data-stu-id="51a59-159">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="51a59-160">ListControl Element (Format)</span><span class="sxs-lookup"><span data-stu-id="51a59-160">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)

[<span data-ttu-id="51a59-161">WideControl Element (Format)</span><span class="sxs-lookup"><span data-stu-id="51a59-161">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="51a59-162">Anpassad kontroll Element (Format)</span><span class="sxs-lookup"><span data-stu-id="51a59-162">CustomControl Element (Format)</span></span>](./customcontrol-element-for-groupby-format.md)

[<span data-ttu-id="51a59-163">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="51a59-163">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
