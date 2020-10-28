---
ms.date: 09/13/2016
ms.topic: reference
title: View-element (format)
description: View-element (format)
ms.openlocfilehash: 6fed1304d94339cc90b6ae53e06483c08d937c12
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92649735"
---
# <a name="view-element-format"></a><span data-ttu-id="08e43-103">View-element (format)</span><span class="sxs-lookup"><span data-stu-id="08e43-103">View Element (Format)</span></span>

<span data-ttu-id="08e43-104">Definierar en vy som visar ett eller flera .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="08e43-104">Defines a view that displays one or more .NET objects.</span></span> <span data-ttu-id="08e43-105">Det finns ingen gräns för hur många vyer som kan definieras i en textfil.</span><span class="sxs-lookup"><span data-stu-id="08e43-105">There is no limit to the number of views that can be defined in a formatting file.</span></span>

<span data-ttu-id="08e43-106">Konfigurations element (format) ViewDefinitions element (format) Visa element (format)</span><span class="sxs-lookup"><span data-stu-id="08e43-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="08e43-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="08e43-107">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="08e43-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="08e43-108">Attributes and Elements</span></span>

<span data-ttu-id="08e43-109">I följande avsnitt beskrivs attributen, underordnade element och `View` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="08e43-109">The following sections describe the attributes, child elements, and the parent element of the `View` element.</span></span> <span data-ttu-id="08e43-110">Du måste ange ett och endast ett av de underordnade elementen för kontrollen och du måste ange namnet på vyn och de objekt som använder vyn.</span><span class="sxs-lookup"><span data-stu-id="08e43-110">You must specify one and only one of the control child elements, and you must specify the name of the view and the objects that use the view.</span></span> <span data-ttu-id="08e43-111">Definiera anpassade kontroller, gruppera objekt och ange om vyn är out-of-band är valfri.</span><span class="sxs-lookup"><span data-stu-id="08e43-111">Defining custom controls, how to group objects, and specifying if the view is out-of-band are optional.</span></span>

### <a name="attributes"></a><span data-ttu-id="08e43-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="08e43-112">Attributes</span></span>

<span data-ttu-id="08e43-113">Inga.</span><span class="sxs-lookup"><span data-stu-id="08e43-113">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="08e43-114">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="08e43-114">Child Elements</span></span>

|<span data-ttu-id="08e43-115">Element</span><span class="sxs-lookup"><span data-stu-id="08e43-115">Element</span></span>|<span data-ttu-id="08e43-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="08e43-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="08e43-117">Controls-element för View (format)</span><span class="sxs-lookup"><span data-stu-id="08e43-117">Controls Element for View (Format)</span></span>](./controls-element-for-view-format.md)|<span data-ttu-id="08e43-118">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="08e43-118">Optional element.</span></span><br /><br /> <span data-ttu-id="08e43-119">Definierar en uppsättning kontroller som kan refereras till av deras namn inifrån vyn.</span><span class="sxs-lookup"><span data-stu-id="08e43-119">Defines a set of controls that can be referenced by their name from within the view.</span></span>|
|[<span data-ttu-id="08e43-120">CustomControl-element (format)</span><span class="sxs-lookup"><span data-stu-id="08e43-120">CustomControl Element (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="08e43-121">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="08e43-121">Optional element.</span></span><br /><br /> <span data-ttu-id="08e43-122">Definierar ett anpassat kontroll format för vyn.</span><span class="sxs-lookup"><span data-stu-id="08e43-122">Defines a custom control format for the view.</span></span>|
|[<span data-ttu-id="08e43-123">GroupBy-element för View (format)</span><span class="sxs-lookup"><span data-stu-id="08e43-123">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="08e43-124">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="08e43-124">Optional element.</span></span><br /><br /> <span data-ttu-id="08e43-125">Definierar hur medlemmarna i .NET-objekten grupperas.</span><span class="sxs-lookup"><span data-stu-id="08e43-125">Defines how the members of the .NET objects are grouped.</span></span>|
|[<span data-ttu-id="08e43-126">ListControl-element (format)</span><span class="sxs-lookup"><span data-stu-id="08e43-126">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)|<span data-ttu-id="08e43-127">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="08e43-127">Optional element.</span></span><br /><br /> <span data-ttu-id="08e43-128">Definierar ett List format för vyn.</span><span class="sxs-lookup"><span data-stu-id="08e43-128">Defines a list format for the view.</span></span>|
|[<span data-ttu-id="08e43-129">Name-element för View (format)</span><span class="sxs-lookup"><span data-stu-id="08e43-129">Name Element for View (Format)</span></span>](./name-element-for-view-format.md)|<span data-ttu-id="08e43-130">Nödvändigt element.</span><span class="sxs-lookup"><span data-stu-id="08e43-130">Required element.</span></span><br /><br /> <span data-ttu-id="08e43-131">Anger namnet som används för att referera till vyn.</span><span class="sxs-lookup"><span data-stu-id="08e43-131">Specifies the name used to reference the view.</span></span>|
|[<span data-ttu-id="08e43-132">TableControl-element (format)</span><span class="sxs-lookup"><span data-stu-id="08e43-132">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="08e43-133">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="08e43-133">Optional element.</span></span><br /><br /> <span data-ttu-id="08e43-134">Definierar ett tabell format för vyn.</span><span class="sxs-lookup"><span data-stu-id="08e43-134">Defines a table format for the view.</span></span>|
|[<span data-ttu-id="08e43-135">ViewSelectedBy-element för vy (format)</span><span class="sxs-lookup"><span data-stu-id="08e43-135">ViewSelectedBy Element for View (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="08e43-136">Nödvändigt element.</span><span class="sxs-lookup"><span data-stu-id="08e43-136">Required element.</span></span><br /><br /> <span data-ttu-id="08e43-137">Definierar de .NET-objekt som visas i den här vyn.</span><span class="sxs-lookup"><span data-stu-id="08e43-137">Defines the .NET objects that this view displays.</span></span>|
|[<span data-ttu-id="08e43-138">WideControl-element (format)</span><span class="sxs-lookup"><span data-stu-id="08e43-138">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="08e43-139">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="08e43-139">Optional element.</span></span><br /><br /> <span data-ttu-id="08e43-140">Definierar ett brett List format (enskilt värde) för vyn.</span><span class="sxs-lookup"><span data-stu-id="08e43-140">Defines a wide (single value) list format for the view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="08e43-141">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="08e43-141">Parent Elements</span></span>

|<span data-ttu-id="08e43-142">Element</span><span class="sxs-lookup"><span data-stu-id="08e43-142">Element</span></span>|<span data-ttu-id="08e43-143">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="08e43-143">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="08e43-144">ViewDefinitions-element (format)</span><span class="sxs-lookup"><span data-stu-id="08e43-144">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)|<span data-ttu-id="08e43-145">Definierar de vyer som används för att visa objekt.</span><span class="sxs-lookup"><span data-stu-id="08e43-145">Defines the views used to display objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="08e43-146">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="08e43-146">Remarks</span></span>

<span data-ttu-id="08e43-147">Mer information om komponenterna i olika vyer och anpassade kontroller finns i följande avsnitt:</span><span class="sxs-lookup"><span data-stu-id="08e43-147">For more information about the components of different views and custom controls, see the following topics:</span></span>

- [<span data-ttu-id="08e43-148">Table View-komponenter</span><span class="sxs-lookup"><span data-stu-id="08e43-148">Table View Components</span></span>](./creating-a-table-view.md)

- [<span data-ttu-id="08e43-149">Visa List komponenter</span><span class="sxs-lookup"><span data-stu-id="08e43-149">List View Components</span></span>](./creating-a-list-view.md)

- [<span data-ttu-id="08e43-150">Wide View-komponenter</span><span class="sxs-lookup"><span data-stu-id="08e43-150">Wide View Components</span></span>](./creating-a-wide-view.md)

- [<span data-ttu-id="08e43-151">Anpassade kontroller</span><span class="sxs-lookup"><span data-stu-id="08e43-151">Custom Controls</span></span>](./creating-custom-controls.md)

## <a name="example"></a><span data-ttu-id="08e43-152">Exempel</span><span class="sxs-lookup"><span data-stu-id="08e43-152">Example</span></span>

<span data-ttu-id="08e43-153">Det här exemplet visar ett- `View` element som definierar en tabellvy för objektet [system. serviceprocess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) .</span><span class="sxs-lookup"><span data-stu-id="08e43-153">This example shows a `View` element that defines a table view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="08e43-154">Se även</span><span class="sxs-lookup"><span data-stu-id="08e43-154">See Also</span></span>

[<span data-ttu-id="08e43-155">ViewDefinitions-element (format)</span><span class="sxs-lookup"><span data-stu-id="08e43-155">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)

[<span data-ttu-id="08e43-156">Name-element för View (format)</span><span class="sxs-lookup"><span data-stu-id="08e43-156">Name Element for View (Format)</span></span>](./name-element-for-view-format.md)

[<span data-ttu-id="08e43-157">ViewSelectedBy-element (format)</span><span class="sxs-lookup"><span data-stu-id="08e43-157">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="08e43-158">Controls-element för View (format)</span><span class="sxs-lookup"><span data-stu-id="08e43-158">Controls Element for View (Format)</span></span>](./controls-element-for-view-format.md)

[<span data-ttu-id="08e43-159">GroupBy-element för View (format)</span><span class="sxs-lookup"><span data-stu-id="08e43-159">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="08e43-160">TableControl-element (format)</span><span class="sxs-lookup"><span data-stu-id="08e43-160">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="08e43-161">ListControl-element (format)</span><span class="sxs-lookup"><span data-stu-id="08e43-161">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)

[<span data-ttu-id="08e43-162">WideControl-element (format)</span><span class="sxs-lookup"><span data-stu-id="08e43-162">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="08e43-163">CustomControl-element (format)</span><span class="sxs-lookup"><span data-stu-id="08e43-163">CustomControl Element (Format)</span></span>](./customcontrol-element-for-groupby-format.md)

[<span data-ttu-id="08e43-164">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="08e43-164">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
