---
title: Visa element (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d837d5d4-ed2e-4d84-a306-0b5d2ad2d0bf
caps.latest.revision: 24
ms.openlocfilehash: 2361c1117757569bef0815018c75764430a9e7a8
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72353447"
---
# <a name="view-element-format"></a><span data-ttu-id="735f7-102">View-element (format)</span><span class="sxs-lookup"><span data-stu-id="735f7-102">View Element (Format)</span></span>

<span data-ttu-id="735f7-103">Definierar en vy som visar ett eller flera .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="735f7-103">Defines a view that displays one or more .NET objects.</span></span> <span data-ttu-id="735f7-104">Det finns ingen gräns för hur många vyer som kan definieras i en textfil.</span><span class="sxs-lookup"><span data-stu-id="735f7-104">There is no limit to the number of views that can be defined in a formatting file.</span></span>

<span data-ttu-id="735f7-105">Konfigurations element (format) ViewDefinitions element (format) Visa element (format)</span><span class="sxs-lookup"><span data-stu-id="735f7-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="735f7-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="735f7-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="735f7-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="735f7-107">Attributes and Elements</span></span>

<span data-ttu-id="735f7-108">I följande avsnitt beskrivs attributen, underordnade element och det överordnade elementet i `View`-elementet.</span><span class="sxs-lookup"><span data-stu-id="735f7-108">The following sections describe the attributes, child elements, and the parent element of the `View` element.</span></span> <span data-ttu-id="735f7-109">Du måste ange ett och endast ett av de underordnade elementen för kontrollen och du måste ange namnet på vyn och de objekt som använder vyn.</span><span class="sxs-lookup"><span data-stu-id="735f7-109">You must specify one and only one of the control child elements, and you must specify the name of the view and the objects that use the view.</span></span> <span data-ttu-id="735f7-110">Definiera anpassade kontroller, gruppera objekt och ange om vyn är out-of-band är valfri.</span><span class="sxs-lookup"><span data-stu-id="735f7-110">Defining custom controls, how to group objects, and specifying if the view is out-of-band are optional.</span></span>

### <a name="attributes"></a><span data-ttu-id="735f7-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="735f7-111">Attributes</span></span>

<span data-ttu-id="735f7-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="735f7-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="735f7-113">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="735f7-113">Child Elements</span></span>

|<span data-ttu-id="735f7-114">Element</span><span class="sxs-lookup"><span data-stu-id="735f7-114">Element</span></span>|<span data-ttu-id="735f7-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="735f7-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="735f7-116">Styr element för vy (format)</span><span class="sxs-lookup"><span data-stu-id="735f7-116">Controls Element for View (Format)</span></span>](./controls-element-for-view-format.md)|<span data-ttu-id="735f7-117">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="735f7-117">Optional element.</span></span><br /><br /> <span data-ttu-id="735f7-118">Definierar en uppsättning kontroller som kan refereras till av deras namn inifrån vyn.</span><span class="sxs-lookup"><span data-stu-id="735f7-118">Defines a set of controls that can be referenced by their name from within the view.</span></span>|
|[<span data-ttu-id="735f7-119">CustomControl-element (format)</span><span class="sxs-lookup"><span data-stu-id="735f7-119">CustomControl Element (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="735f7-120">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="735f7-120">Optional element.</span></span><br /><br /> <span data-ttu-id="735f7-121">Definierar ett anpassat kontroll format för vyn.</span><span class="sxs-lookup"><span data-stu-id="735f7-121">Defines a custom control format for the view.</span></span>|
|[<span data-ttu-id="735f7-122">GroupBy-element för vy (format)</span><span class="sxs-lookup"><span data-stu-id="735f7-122">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)|<span data-ttu-id="735f7-123">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="735f7-123">Optional element.</span></span><br /><br /> <span data-ttu-id="735f7-124">Definierar hur medlemmarna i .NET-objekten grupperas.</span><span class="sxs-lookup"><span data-stu-id="735f7-124">Defines how the members of the .NET objects are grouped.</span></span>|
|[<span data-ttu-id="735f7-125">ListControl-element (format)</span><span class="sxs-lookup"><span data-stu-id="735f7-125">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)|<span data-ttu-id="735f7-126">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="735f7-126">Optional element.</span></span><br /><br /> <span data-ttu-id="735f7-127">Definierar ett List format för vyn.</span><span class="sxs-lookup"><span data-stu-id="735f7-127">Defines a list format for the view.</span></span>|
|[<span data-ttu-id="735f7-128">Namn element för vy (format)</span><span class="sxs-lookup"><span data-stu-id="735f7-128">Name Element for View (Format)</span></span>](./name-element-for-view-format.md)|<span data-ttu-id="735f7-129">Nödvändigt element.</span><span class="sxs-lookup"><span data-stu-id="735f7-129">Required element.</span></span><br /><br /> <span data-ttu-id="735f7-130">Anger namnet som används för att referera till vyn.</span><span class="sxs-lookup"><span data-stu-id="735f7-130">Specifies the name used to reference the view.</span></span>|
|[<span data-ttu-id="735f7-131">TableControl-element (format)</span><span class="sxs-lookup"><span data-stu-id="735f7-131">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="735f7-132">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="735f7-132">Optional element.</span></span><br /><br /> <span data-ttu-id="735f7-133">Definierar ett tabell format för vyn.</span><span class="sxs-lookup"><span data-stu-id="735f7-133">Defines a table format for the view.</span></span>|
|[<span data-ttu-id="735f7-134">ViewSelectedBy-element för vy (format)</span><span class="sxs-lookup"><span data-stu-id="735f7-134">ViewSelectedBy Element for View (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="735f7-135">Nödvändigt element.</span><span class="sxs-lookup"><span data-stu-id="735f7-135">Required element.</span></span><br /><br /> <span data-ttu-id="735f7-136">Definierar de .NET-objekt som visas i den här vyn.</span><span class="sxs-lookup"><span data-stu-id="735f7-136">Defines the .NET objects that this view displays.</span></span>|
|[<span data-ttu-id="735f7-137">WideControl-element (format)</span><span class="sxs-lookup"><span data-stu-id="735f7-137">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)|<span data-ttu-id="735f7-138">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="735f7-138">Optional element.</span></span><br /><br /> <span data-ttu-id="735f7-139">Definierar ett brett List format (enskilt värde) för vyn.</span><span class="sxs-lookup"><span data-stu-id="735f7-139">Defines a wide (single value) list format for the view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="735f7-140">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="735f7-140">Parent Elements</span></span>

|<span data-ttu-id="735f7-141">Element</span><span class="sxs-lookup"><span data-stu-id="735f7-141">Element</span></span>|<span data-ttu-id="735f7-142">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="735f7-142">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="735f7-143">ViewDefinitions-element (format)</span><span class="sxs-lookup"><span data-stu-id="735f7-143">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)|<span data-ttu-id="735f7-144">Definierar de vyer som används för att visa objekt.</span><span class="sxs-lookup"><span data-stu-id="735f7-144">Defines the views used to display objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="735f7-145">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="735f7-145">Remarks</span></span>

<span data-ttu-id="735f7-146">Mer information om komponenterna i olika vyer och anpassade kontroller finns i följande avsnitt:</span><span class="sxs-lookup"><span data-stu-id="735f7-146">For more information about the components of different views and custom controls, see the following topics:</span></span>

- [<span data-ttu-id="735f7-147">Table View-komponenter</span><span class="sxs-lookup"><span data-stu-id="735f7-147">Table View Components</span></span>](./creating-a-table-view.md)

- [<span data-ttu-id="735f7-148">Visa List komponenter</span><span class="sxs-lookup"><span data-stu-id="735f7-148">List View Components</span></span>](./creating-a-list-view.md)

- [<span data-ttu-id="735f7-149">Wide View-komponenter</span><span class="sxs-lookup"><span data-stu-id="735f7-149">Wide View Components</span></span>](./creating-a-wide-view.md)

- [<span data-ttu-id="735f7-150">Anpassade kontroller</span><span class="sxs-lookup"><span data-stu-id="735f7-150">Custom Controls</span></span>](./creating-custom-controls.md)

## <a name="example"></a><span data-ttu-id="735f7-151">Exempel</span><span class="sxs-lookup"><span data-stu-id="735f7-151">Example</span></span>

<span data-ttu-id="735f7-152">I det här exemplet visas ett `View`-element som definierar en tabellvy för objektet [system. serviceprocess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) .</span><span class="sxs-lookup"><span data-stu-id="735f7-152">This example shows a `View` element that defines a table view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="735f7-153">Se även</span><span class="sxs-lookup"><span data-stu-id="735f7-153">See Also</span></span>

[<span data-ttu-id="735f7-154">ViewDefinitions-element (format)</span><span class="sxs-lookup"><span data-stu-id="735f7-154">ViewDefinitions Element (Format)</span></span>](./viewdefinitions-element-format.md)

[<span data-ttu-id="735f7-155">Namn element för vy (format)</span><span class="sxs-lookup"><span data-stu-id="735f7-155">Name Element for View (Format)</span></span>](./name-element-for-view-format.md)

[<span data-ttu-id="735f7-156">ViewSelectedBy-element (format)</span><span class="sxs-lookup"><span data-stu-id="735f7-156">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="735f7-157">Styr element för vy (format)</span><span class="sxs-lookup"><span data-stu-id="735f7-157">Controls Element for View (Format)</span></span>](./controls-element-for-view-format.md)

[<span data-ttu-id="735f7-158">GroupBy-element för vy (format)</span><span class="sxs-lookup"><span data-stu-id="735f7-158">GroupBy Element for View (Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="735f7-159">TableControl-element (format)</span><span class="sxs-lookup"><span data-stu-id="735f7-159">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="735f7-160">ListControl-element (format)</span><span class="sxs-lookup"><span data-stu-id="735f7-160">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)

[<span data-ttu-id="735f7-161">WideControl-element (format)</span><span class="sxs-lookup"><span data-stu-id="735f7-161">WideControl Element (Format)</span></span>](./widecontrol-element-format.md)

[<span data-ttu-id="735f7-162">CustomControl-element (format)</span><span class="sxs-lookup"><span data-stu-id="735f7-162">CustomControl Element (Format)</span></span>](./customcontrol-element-for-groupby-format.md)

[<span data-ttu-id="735f7-163">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="735f7-163">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
