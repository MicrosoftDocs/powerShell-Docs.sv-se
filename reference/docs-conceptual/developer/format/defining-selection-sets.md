---
title: Definiera urvals uppsättningar | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 58c812b69f92c33304bf7fc7b2891cc2a0227918
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774311"
---
# <a name="defining-selection-sets"></a><span data-ttu-id="ad283-102">Definiera valuppsättningar</span><span class="sxs-lookup"><span data-stu-id="ad283-102">Defining Selection Sets</span></span>

<span data-ttu-id="ad283-103">När du skapar flera vyer och kontroller kan du definiera uppsättningar av objekt som kallas urvals uppsättningar.</span><span class="sxs-lookup"><span data-stu-id="ad283-103">When creating multiple views and controls, you can define sets of objects that are referred to as selection sets.</span></span> <span data-ttu-id="ad283-104">Med en urvals uppsättning kan du definiera objekten en gång, utan att behöva definiera dem flera gånger för varje vy eller kontroll.</span><span class="sxs-lookup"><span data-stu-id="ad283-104">A selection set enables you to define the objects one time, without having to define them repeatedly for each view or control.</span></span> <span data-ttu-id="ad283-105">Normalt används urvals uppsättningar när du har en uppsättning relaterade .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="ad283-105">Typically, selection sets are used when you have a set of related .NET objects.</span></span> <span data-ttu-id="ad283-106">`FileSystem`Format filen (FileSystem.format.ps1XML) definierar till exempel en urvals uppsättning av de fil system typer som flera vyer använder.</span><span class="sxs-lookup"><span data-stu-id="ad283-106">For example, The `FileSystem` formatting file (FileSystem.format.ps1xml) defines a selection set of the file system types that several views use.</span></span>

## <a name="where-selection-sets-are-defined-and-referenced"></a><span data-ttu-id="ad283-107">Där urvals uppsättningar definieras och refereras till</span><span class="sxs-lookup"><span data-stu-id="ad283-107">Where Selection Sets are Defined and Referenced</span></span>

<span data-ttu-id="ad283-108">Du definierar urvals uppsättningar som en del av vanliga data som kan användas av alla vyer och kontroller som definierats i format filen.</span><span class="sxs-lookup"><span data-stu-id="ad283-108">You define selection sets as part of the common data that can be used by all the views and controls defined in the formatting file.</span></span> <span data-ttu-id="ad283-109">I följande exempel visas hur du definierar tre urvals uppsättningar.</span><span class="sxs-lookup"><span data-stu-id="ad283-109">The following example shows how to define three selection sets.</span></span>

```xml
<Configuration>
  <SelectionSets>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
  </SelectionSets>
</Configuration>
```

<span data-ttu-id="ad283-110">Du kan referera till en urvals uppsättning på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="ad283-110">You can reference a selection sets in the following ways:</span></span>

- <span data-ttu-id="ad283-111">Varje vy har ett- `ViewSelectedBy` element som definierar vilka objekt som visas med hjälp av vyn.</span><span class="sxs-lookup"><span data-stu-id="ad283-111">Each view has a `ViewSelectedBy` element that defines which objects are displayed by using the view.</span></span> <span data-ttu-id="ad283-112">`ViewSelectedBy`Elementet har ett `SelectionSetName` underordnat element som anger den markerings uppsättning som alla definitioner för vyn använder.</span><span class="sxs-lookup"><span data-stu-id="ad283-112">The `ViewSelectedBy` element has a `SelectionSetName` child element that specifies the selection set that all the definitions of the view use.</span></span> <span data-ttu-id="ad283-113">Det finns ingen begränsning för antalet markerings uppsättningar som du kan referera till från en vy.</span><span class="sxs-lookup"><span data-stu-id="ad283-113">There is no restriction on the number of selection sets that you can reference from a view.</span></span>

- <span data-ttu-id="ad283-114">I varje definition av en vy eller kontroll `EntrySelectedBy` definierar elementet vilka objekt som visas genom att använda den definitionen.</span><span class="sxs-lookup"><span data-stu-id="ad283-114">In each definition of a view or control, the `EntrySelectedBy` element defines which objects are displayed by using that definition.</span></span> <span data-ttu-id="ad283-115">Normalt har en vy eller kontroll bara en definition så objekten definieras av `ViewSelectedBy` elementet.</span><span class="sxs-lookup"><span data-stu-id="ad283-115">Typically a view or control has only one definition so the objects are defined by the `ViewSelectedBy` element.</span></span> <span data-ttu-id="ad283-116">`EntrySelectedBy`Elementet i definitionen har ett `SelectionSetName` underordnat element som anger urvals uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="ad283-116">The `EntrySelectedBy` element of the definition has a `SelectionSetName` child element that specifies the selection set.</span></span> <span data-ttu-id="ad283-117">Om du anger urvals uppsättningen för en definition kan du inte ange något av de andra underordnade elementen för- `EntrySelectedBy` elementet.</span><span class="sxs-lookup"><span data-stu-id="ad283-117">If you specify the selection set for a definition, you cannot specify any of the other child elements of the `EntrySelectedBy` element.</span></span>

- <span data-ttu-id="ad283-118">I varje definition av en vy eller kontroll `SelectionCondition` kan elementet användas för att ange ett villkor för när definitionen används.</span><span class="sxs-lookup"><span data-stu-id="ad283-118">In each definition of a view or control, the `SelectionCondition` element can be used to specify a condition for when the definition is used.</span></span> <span data-ttu-id="ad283-119">`SelectionCondition`Elementet har ett `SelectionSetName` underordnat element som anger den urvals uppsättning som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="ad283-119">The `SelectionCondition` element has a `SelectionSetName` child element that specifies the selection set that triggers the condition.</span></span> <span data-ttu-id="ad283-120">Villkoret utlöses när något av de objekt som definieras i urvals uppsättningen visas.</span><span class="sxs-lookup"><span data-stu-id="ad283-120">The condition is triggered when any of the objects defined in the selection set are displayed.</span></span> <span data-ttu-id="ad283-121">Mer information om hur du anger dessa villkor finns i [definiera villkor för när data visas](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="ad283-121">For more information about how to set these conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="selection-set-example"></a><span data-ttu-id="ad283-122">Exempel på urvals uppsättning</span><span class="sxs-lookup"><span data-stu-id="ad283-122">Selection Set Example</span></span>

<span data-ttu-id="ad283-123">I följande exempel visas en urvals uppsättning som tas direkt från den `FileSystem` fil format som tillhandahålls av Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ad283-123">The following example shows a selection set that is taken directly from the `FileSystem` formatting file provided by Windows PowerShell.</span></span> <span data-ttu-id="ad283-124">Mer information om andra Windows PowerShell-filer finns i [filer för Windows PowerShell-formatering](./powershell-formatting-files.md).</span><span class="sxs-lookup"><span data-stu-id="ad283-124">For more information about other Windows PowerShell formatting files, see [Windows PowerShell Formatting Files](./powershell-formatting-files.md).</span></span>

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

<span data-ttu-id="ad283-125">Den tidigare urvals uppsättningen refereras till i `ViewSelectedBy` elementet i en tabellvy.</span><span class="sxs-lookup"><span data-stu-id="ad283-125">The previous selection set is referenced in the `ViewSelectedBy` element of a table view.</span></span>

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

## <a name="xml-elements"></a><span data-ttu-id="ad283-126">XML-element</span><span class="sxs-lookup"><span data-stu-id="ad283-126">XML Elements</span></span>

 <span data-ttu-id="ad283-127">Det finns ingen gräns för antalet markerings uppsättningar som du kan definiera.</span><span class="sxs-lookup"><span data-stu-id="ad283-127">There is no limit to the number of selection sets that you can define.</span></span> <span data-ttu-id="ad283-128">Följande XML-element används för att skapa en urvals uppsättning.</span><span class="sxs-lookup"><span data-stu-id="ad283-128">The following XML elements are used to create a selection set.</span></span>

- <span data-ttu-id="ad283-129">[SelectionSets](./selectionsets-element-format.md) -elementet definierar de uppsättningar av .net-objekt som refereras till i vyernas vyer och kontroller.</span><span class="sxs-lookup"><span data-stu-id="ad283-129">The [SelectionSets](./selectionsets-element-format.md) element defines the sets of .NET objects that are referenced by the views and controls of the formatting file.</span></span>

- <span data-ttu-id="ad283-130">[SelectionSet](./selectionset-element-format.md) -elementet definierar en enda uppsättning .net-objekt.</span><span class="sxs-lookup"><span data-stu-id="ad283-130">The [SelectionSet](./selectionset-element-format.md) element defines a single set of .NET objects.</span></span>

- <span data-ttu-id="ad283-131">Elementet [Name](./name-element-for-selectionset-format.md) anger namnet som används för att referera till urvals uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="ad283-131">The [Name](./name-element-for-selectionset-format.md) element specifies the name that is used to reference the selection set.</span></span>

- <span data-ttu-id="ad283-132">Elementet [types](./types-element-for-selectionset-format.md) anger .net-typerna för objekt i urvals uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="ad283-132">The [Types](./types-element-for-selectionset-format.md) element specifies the .NET types of the objects of the selection set.</span></span> <span data-ttu-id="ad283-133">(I formateringsattribut anges objekt av deras .NET-typ.)</span><span class="sxs-lookup"><span data-stu-id="ad283-133">(Within formatting files, objects are specified by their .NET type.)</span></span>

 <span data-ttu-id="ad283-134">Följande XML-element används för att ange en urvals uppsättning.</span><span class="sxs-lookup"><span data-stu-id="ad283-134">The following XML elements are used to specify a selection set.</span></span>

- <span data-ttu-id="ad283-135">Följande element anger den urvals uppsättning som ska användas i alla definitioner för vyn:</span><span class="sxs-lookup"><span data-stu-id="ad283-135">The following element specifies the selection set to use in all the definitions of the view:</span></span>

  - [<span data-ttu-id="ad283-136">SelectionSetName-element för ViewSelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="ad283-136">SelectionSetName Element for ViewSelectedBy (Format)</span></span>](./selectionsetname-element-for-viewselectedby-format.md)

  - [<span data-ttu-id="ad283-137">SelectionSetName-element för EntrySelectedBy för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="ad283-137">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

- <span data-ttu-id="ad283-138">Följande element anger den urvals uppsättning som används av en enda View-definition:</span><span class="sxs-lookup"><span data-stu-id="ad283-138">The following elements specify the selection set used by a single view definition:</span></span>

  - [<span data-ttu-id="ad283-139">SelectionSetName-element för EntrySelectedBy för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="ad283-139">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

  - [<span data-ttu-id="ad283-140">SelectionSetName-element för EntrySelectedBy för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="ad283-140">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

  - [<span data-ttu-id="ad283-141">SelectionSetName-element för EntrySelectedBy för WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="ad283-141">SelectionSetName Element for EntrySelectedBy for WideControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

  - [<span data-ttu-id="ad283-142">SelectionSetName-element för EntrySelectedBy för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="ad283-142">SelectionSetName Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

- <span data-ttu-id="ad283-143">Följande element anger den urvals uppsättning som används av vanliga och Visa kontroll definitioner:</span><span class="sxs-lookup"><span data-stu-id="ad283-143">The following elements specify the selection set used by common and view control definitions:</span></span>

  - [<span data-ttu-id="ad283-144">SelectionSetName-element för EntrySelectedBy för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="ad283-144">SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)

  - [<span data-ttu-id="ad283-145">SelectionSetName-element för EntrySelectedBy för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="ad283-145">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format.md)

- <span data-ttu-id="ad283-146">Följande element anger den urvals uppsättning som används när du definierar vilket objekt som ska expanderas:</span><span class="sxs-lookup"><span data-stu-id="ad283-146">The following elements specify the selection set used when you define which object to expand:</span></span>

  - [<span data-ttu-id="ad283-147">SelectionSetName-element för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="ad283-147">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

- <span data-ttu-id="ad283-148">Följande element anger den urvals uppsättning som används av urvals villkor.</span><span class="sxs-lookup"><span data-stu-id="ad283-148">The following elements specify the selection set used by selection conditions.</span></span>

  - [<span data-ttu-id="ad283-149">SelectionSetName-element för SelectionCondition för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="ad283-149">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

  - [<span data-ttu-id="ad283-150">SelectionSetName-element för SelectionCondition för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="ad283-150">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

  - [<span data-ttu-id="ad283-151">SelectionSetName-element för SelectionCondition för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="ad283-151">SelectionSetName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

  - [<span data-ttu-id="ad283-152">SelectionSetName-element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="ad283-152">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

  - [<span data-ttu-id="ad283-153">SelectionSetName-element för SelectionCondition för EntrySelectedBy för ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="ad283-153">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)

  - [<span data-ttu-id="ad283-154">SelectionSetName-element för SelectionCondition för EntrySelectedBy för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="ad283-154">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

  - [<span data-ttu-id="ad283-155">SelectionSetName-element för SelectionCondition för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="ad283-155">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

  - [<span data-ttu-id="ad283-156">SelectionSetName-element för SelectionCondition för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="ad283-156">SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)

## <a name="see-also"></a><span data-ttu-id="ad283-157">Se även</span><span class="sxs-lookup"><span data-stu-id="ad283-157">See Also</span></span>

[<span data-ttu-id="ad283-158">SelectionSets</span><span class="sxs-lookup"><span data-stu-id="ad283-158">SelectionSets</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="ad283-159">SelectionSet</span><span class="sxs-lookup"><span data-stu-id="ad283-159">SelectionSet</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="ad283-160">Namn</span><span class="sxs-lookup"><span data-stu-id="ad283-160">Name</span></span>](./name-element-for-selectionset-format.md)

[<span data-ttu-id="ad283-161">Typer</span><span class="sxs-lookup"><span data-stu-id="ad283-161">Types</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="ad283-162">PowerShell-formateringsfiler</span><span class="sxs-lookup"><span data-stu-id="ad283-162">PowerShell Formatting Files</span></span>](./powershell-formatting-files.md)

[<span data-ttu-id="ad283-163">Definiera villkor för när data visas</span><span class="sxs-lookup"><span data-stu-id="ad283-163">Defining Conditions for when Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="ad283-164">Skriva en PowerShell-formatering och en typ fil</span><span class="sxs-lookup"><span data-stu-id="ad283-164">Writing a PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
