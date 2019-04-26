---
title: Definiera inställningarna | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 00dbb5ee-93d4-4914-a082-ef4d8b236b5c
caps.latest.revision: 16
ms.openlocfilehash: 596212f2e64401a751cf3dca0ee7d60b80912c00
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066319"
---
# <a name="defining-selection-sets"></a><span data-ttu-id="f3c35-102">Definiera valuppsättningar</span><span class="sxs-lookup"><span data-stu-id="f3c35-102">Defining Selection Sets</span></span>

<span data-ttu-id="f3c35-103">När du skapar flera vyer och kontroller, kan du definiera uppsättningar med objekt som refereras som inställningarna.</span><span class="sxs-lookup"><span data-stu-id="f3c35-103">When creating multiple views and controls, you can define sets of objects that are referred to as selection sets.</span></span> <span data-ttu-id="f3c35-104">En kan du definiera objekt en gång utan att behöva definiera dem flera gånger för varje vy eller kontroll.</span><span class="sxs-lookup"><span data-stu-id="f3c35-104">A selection set enables you to define the objects one time, without having to define them repeatedly for each view or control.</span></span> <span data-ttu-id="f3c35-105">Inställningarna används vanligtvis när du har en uppsättning relaterade .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="f3c35-105">Typically, selection sets are used when you have a set of related .NET objects.</span></span> <span data-ttu-id="f3c35-106">Till exempel den `FileSystem` formatering fil (FileSystem.format.ps1xml) definierar en uppsättning system filtyper som använder flera vyer val.</span><span class="sxs-lookup"><span data-stu-id="f3c35-106">For example, The `FileSystem` formatting file (FileSystem.format.ps1xml) defines a selection set of the file system types that several views use.</span></span>

## <a name="where-selection-sets-are-defined-and-referenced"></a><span data-ttu-id="f3c35-107">Var inställningarna finns definierade och refererat</span><span class="sxs-lookup"><span data-stu-id="f3c35-107">Where Selection Sets are Defined and Referenced</span></span>

<span data-ttu-id="f3c35-108">Du definierar inställningarna som en del av de vanliga data som kan användas av alla vyer och kontroller som definieras i filen formatering.</span><span class="sxs-lookup"><span data-stu-id="f3c35-108">You define selection sets as part of the common data that can be used by all the views and controls defined in the formatting file.</span></span> <span data-ttu-id="f3c35-109">I följande exempel visas hur du definierar tre val av uppsättningar.</span><span class="sxs-lookup"><span data-stu-id="f3c35-109">The following example shows how to define three selection sets.</span></span>

```xml
<Configuration>
  <SelectionSets>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
  </SelectionSets>
</Configuration>
```

<span data-ttu-id="f3c35-110">Du kan referera till en markering anger på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="f3c35-110">You can reference a selection sets in the following ways:</span></span>

- <span data-ttu-id="f3c35-111">Varje vy har en `ViewSelectedBy` element som definierar vilka objekt visas med hjälp av vyn.</span><span class="sxs-lookup"><span data-stu-id="f3c35-111">Each view has a `ViewSelectedBy` element that defines which objects are displayed by using the view.</span></span> <span data-ttu-id="f3c35-112">Den `ViewSelectedBy` elementet har en `SelectionSetName` underordnade elementet som anger markeringen inställt som alla definitioner för att visa.</span><span class="sxs-lookup"><span data-stu-id="f3c35-112">The `ViewSelectedBy` element has a `SelectionSetName` child element that specifies the selection set that all the definitions of the view use.</span></span> <span data-ttu-id="f3c35-113">Det finns ingen begränsning för hur många val av uppsättningar som du kan referera till från en vy.</span><span class="sxs-lookup"><span data-stu-id="f3c35-113">There is no restriction on the number of selection sets that you can reference from a view.</span></span>

- <span data-ttu-id="f3c35-114">I varje definitionen för en vy eller en kontroll, den `EntrySelectedBy` elementet definierar vilka objekt visas med hjälp av den definitionen.</span><span class="sxs-lookup"><span data-stu-id="f3c35-114">In each definition of a view or control, the `EntrySelectedBy` element defines which objects are displayed by using that definition.</span></span> <span data-ttu-id="f3c35-115">En vy eller en kontroll har normalt bara en definition så att objekt som definieras av den `ViewSelectedBy` element.</span><span class="sxs-lookup"><span data-stu-id="f3c35-115">Typically a view or control has only one definition so the objects are defined by the `ViewSelectedBy` element.</span></span> <span data-ttu-id="f3c35-116">Den `EntrySelectedBy` element i definitionen har en `SelectionSetName` underordnat element som definierar vilka val.</span><span class="sxs-lookup"><span data-stu-id="f3c35-116">The `EntrySelectedBy` element of the definition has a `SelectionSetName` child element that specifies the selection set.</span></span> <span data-ttu-id="f3c35-117">Om du anger alternativet för en definition, du kan inte ange någon av de andra underordnade elementen i `EntrySelectedBy` element.</span><span class="sxs-lookup"><span data-stu-id="f3c35-117">If you specify the selection set for a definition, you cannot specify any of the other child elements of the `EntrySelectedBy` element.</span></span>

- <span data-ttu-id="f3c35-118">I varje definitionen för en vy eller en kontroll, den `SelectionCondition` element kan användas för att ange ett villkor för när definitionen används.</span><span class="sxs-lookup"><span data-stu-id="f3c35-118">In each definition of a view or control, the `SelectionCondition` element can be used to specify a condition for when the definition is used.</span></span> <span data-ttu-id="f3c35-119">Den `SelectionCondition` elementet har en `SelectionSetName` underordnat element som anger markeringen ange som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="f3c35-119">The `SelectionCondition` element has a `SelectionSetName` child element that specifies the selection set that triggers the condition.</span></span> <span data-ttu-id="f3c35-120">Villkoret utlöses när någon av de objekt som definierats i uppsättningen markeringen visas.</span><span class="sxs-lookup"><span data-stu-id="f3c35-120">The condition is triggered when any of the objects defined in the selection set are displayed.</span></span> <span data-ttu-id="f3c35-121">Mer information om hur du anger dessa villkor finns i [definiera villkor för när Data visas](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="f3c35-121">For more information about how to set these conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="selection-set-example"></a><span data-ttu-id="f3c35-122">Val av Set-exempel</span><span class="sxs-lookup"><span data-stu-id="f3c35-122">Selection Set Example</span></span>

<span data-ttu-id="f3c35-123">I följande exempel visas en markering uppsättning som tagits direkt från den `FileSystem` formatering fil som tillhandahålls av Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f3c35-123">The following example shows a selection set that is taken directly from the `FileSystem` formatting file provided by Windows PowerShell.</span></span> <span data-ttu-id="f3c35-124">Mer information om andra Windows PowerShell formatering filer finns i [Windows PowerShell-formatering filer](./powershell-formatting-files.md).</span><span class="sxs-lookup"><span data-stu-id="f3c35-124">For more information about other Windows PowerShell formatting files, see [Windows PowerShell Formatting Files](./powershell-formatting-files.md).</span></span>

```xml
<SelectionSets>
  <SelectionSet>
    <Name>FileSystemTypes</Name>
    <Types>
     <TypeName>System.IO.DirectoryInfo</TypeName>
     <TypeName>System.IO.FileInfo</TypeName>
     <TypeName>Deserialized.System.IO.DirectoryInfo</TypeName>
     <TypeName>Deserialized.System.IO.FileInfo</TypeName>
    </Types>
  </SelectionSet>
</SelectionSets>
```

<span data-ttu-id="f3c35-125">Den tidigare val av uppsättningen refereras till i den `ViewSelectedBy` element i en tabellvy.</span><span class="sxs-lookup"><span data-stu-id="f3c35-125">The previous selection set is referenced in the `ViewSelectedBy` element of a table view.</span></span>

```xml
<ViewDefinitions>
  <View>
    <Name>Files</Name>
    <ViewSelectedBy>
      <SelectionSetName>FileSystemTypes</SelectionSetName>
    </ViewSelectedBy>
    <TableControl>...</TableControl>
  </View>
</ViewDefinitions>

```

## <a name="xml-elements"></a><span data-ttu-id="f3c35-126">XML-element</span><span class="sxs-lookup"><span data-stu-id="f3c35-126">XML Elements</span></span>

 <span data-ttu-id="f3c35-127">Det finns ingen gräns för hur många val av uppsättningar som du kan definiera.</span><span class="sxs-lookup"><span data-stu-id="f3c35-127">There is no limit to the number of selection sets that you can define.</span></span> <span data-ttu-id="f3c35-128">Följande XML-element används för att skapa en.</span><span class="sxs-lookup"><span data-stu-id="f3c35-128">The following XML elements are used to create a selection set.</span></span>

- <span data-ttu-id="f3c35-129">Den [SelectionSets](./selectionsets-element-format.md) elementet definierar uppsättningar med .NET-objekt som refereras av vyer och kontroller av filen formatering.</span><span class="sxs-lookup"><span data-stu-id="f3c35-129">The [SelectionSets](./selectionsets-element-format.md) element defines the sets of .NET objects that are referenced by the views and controls of the formatting file.</span></span>

- <span data-ttu-id="f3c35-130">Den [SelectionSet](./selectionset-element-format.md) elementet definierar en uppsättning med .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="f3c35-130">The [SelectionSet](./selectionset-element-format.md) element defines a single set of .NET objects.</span></span>

- <span data-ttu-id="f3c35-131">Den [namn](./name-element-for-selectionset-format.md) elementet anger namnet som används för att referera till val av uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="f3c35-131">The [Name](./name-element-for-selectionset-format.md) element specifies the name that is used to reference the selection set.</span></span>

- <span data-ttu-id="f3c35-132">Den [typer](./types-element-for-selectionset-format.md) elementet anger vilka .NET-typer av objekt för val av uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="f3c35-132">The [Types](./types-element-for-selectionset-format.md) element specifies the .NET types of the objects of the selection set.</span></span> <span data-ttu-id="f3c35-133">(Inom formatering filer objekt anges efter typ .NET.)</span><span class="sxs-lookup"><span data-stu-id="f3c35-133">(Within formatting files, objects are specified by their .NET type.)</span></span>

 <span data-ttu-id="f3c35-134">Följande XML-element för att ange en.</span><span class="sxs-lookup"><span data-stu-id="f3c35-134">The following XML elements are used to specify a selection set.</span></span>

- <span data-ttu-id="f3c35-135">Följande element anger valet inställd på att använda i alla definitioner av vyn:</span><span class="sxs-lookup"><span data-stu-id="f3c35-135">The following element specifies the selection set to use in all the definitions of the view:</span></span>

    - [<span data-ttu-id="f3c35-136">SelectionSetName Element för ViewSelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="f3c35-136">SelectionSetName Element for ViewSelectedBy (Format)</span></span>](./selectionsetname-element-for-viewselectedby-format.md)

    - [<span data-ttu-id="f3c35-137">SelectionSetName Element för EntrySelectedBy för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="f3c35-137">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

- <span data-ttu-id="f3c35-138">Följande element ange val av uppsättningen som används av en enda vy-definition:</span><span class="sxs-lookup"><span data-stu-id="f3c35-138">The following elements specify the selection set used by a single view definition:</span></span>

    - [<span data-ttu-id="f3c35-139">SelectionSetName Element för EntrySelectedBy för ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="f3c35-139">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

    - [<span data-ttu-id="f3c35-140">SelectionSetName Element för EntrySelectedBy för TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="f3c35-140">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

    - [<span data-ttu-id="f3c35-141">SelectionSetName Element för EntrySelectedBy för WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="f3c35-141">SelectionSetName Element for EntrySelectedBy for WideControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

    - [<span data-ttu-id="f3c35-142">SelectionSetName Element för EntrySelectedBy för anpassad kontroll för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="f3c35-142">SelectionSetName Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

- <span data-ttu-id="f3c35-143">Följande element anger du de val som angivits av gemensamma och visa kontroll definitioner:</span><span class="sxs-lookup"><span data-stu-id="f3c35-143">The following elements specify the selection set used by common and view control definitions:</span></span>

    - [<span data-ttu-id="f3c35-144">SelectionSetName Element för EntrySelectedBy för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="f3c35-144">SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)

    - [<span data-ttu-id="f3c35-145">SelectionSetName Element för EntrySelectedBy för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="f3c35-145">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format.md)

- <span data-ttu-id="f3c35-146">Följande element ange de val som angivits när du definierar vilka objekt att expandera:</span><span class="sxs-lookup"><span data-stu-id="f3c35-146">The following elements specify the selection set used when you define which object to expand:</span></span>

    - [<span data-ttu-id="f3c35-147">SelectionSetName Element för EntrySelectedBy för EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="f3c35-147">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

- <span data-ttu-id="f3c35-148">Följande element ange de val som angivits av val av villkor.</span><span class="sxs-lookup"><span data-stu-id="f3c35-148">The following elements specify the selection set used by selection conditions.</span></span>

    - [<span data-ttu-id="f3c35-149">SelectionSetName Element för SelectionCondition för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="f3c35-149">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

    - [<span data-ttu-id="f3c35-150">SelectionSetName Element för SelectionCondition för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="f3c35-150">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

    - [<span data-ttu-id="f3c35-151">SelectionSetName Element för SelectionCondition för anpassad kontroll för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="f3c35-151">SelectionSetName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

    - [<span data-ttu-id="f3c35-152">SelectionSetName Element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="f3c35-152">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

    - [<span data-ttu-id="f3c35-153">SelectionSetName Element för SelectionCondition för EntrySelectedBy för ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="f3c35-153">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)

    - [<span data-ttu-id="f3c35-154">SelectionSetName Element för SelectionCondition för EntrySelectedBy för TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="f3c35-154">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

    - [<span data-ttu-id="f3c35-155">SelectionSetName Element för SelectionCondition för EntrySelectedBy för WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="f3c35-155">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

    - [<span data-ttu-id="f3c35-156">SelectionSetName Element för SelectionCondition för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="f3c35-156">SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)

## <a name="see-also"></a><span data-ttu-id="f3c35-157">Se även</span><span class="sxs-lookup"><span data-stu-id="f3c35-157">See Also</span></span>

[<span data-ttu-id="f3c35-158">SelectionSets</span><span class="sxs-lookup"><span data-stu-id="f3c35-158">SelectionSets</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="f3c35-159">SelectionSet</span><span class="sxs-lookup"><span data-stu-id="f3c35-159">SelectionSet</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="f3c35-160">Namn</span><span class="sxs-lookup"><span data-stu-id="f3c35-160">Name</span></span>](./name-element-for-selectionset-format.md)

[<span data-ttu-id="f3c35-161">Typer</span><span class="sxs-lookup"><span data-stu-id="f3c35-161">Types</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="f3c35-162">PowerShell-formatering filer</span><span class="sxs-lookup"><span data-stu-id="f3c35-162">PowerShell Formatting Files</span></span>](./powershell-formatting-files.md)

[<span data-ttu-id="f3c35-163">Definiera villkor för när Data visas</span><span class="sxs-lookup"><span data-stu-id="f3c35-163">Defining Conditions for when Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="f3c35-164">Skriva ett PowerShell-formatering och typer fil</span><span class="sxs-lookup"><span data-stu-id="f3c35-164">Writing a PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
