---
title: Definiera villkor för att visa data | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 13de078e681708b02e378b2c7d531032b2ffdc05
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774345"
---
# <a name="defining-conditions-for-displaying-data"></a><span data-ttu-id="7cc26-102">Definiera villkor för datavisning</span><span class="sxs-lookup"><span data-stu-id="7cc26-102">Defining Conditions for Displaying Data</span></span>

<span data-ttu-id="7cc26-103">När du definierar vilka data som visas i en vy eller en kontroll kan du ange ett villkor som måste finnas för att de data som ska visas.</span><span class="sxs-lookup"><span data-stu-id="7cc26-103">When defining what data is displayed by a view or a control, you can specify a condition that must exist for the data to be displayed.</span></span> <span data-ttu-id="7cc26-104">Villkoret kan utlösas av en speciell egenskap eller när ett skript eller egenskaps värde utvärderas till `true` .</span><span class="sxs-lookup"><span data-stu-id="7cc26-104">The condition can be triggered by a specific property, or when a script or property value evaluates to `true`.</span></span> <span data-ttu-id="7cc26-105">När urvals villkoret är uppfyllt används definitionen för vyn eller kontrollen.</span><span class="sxs-lookup"><span data-stu-id="7cc26-105">When the selection condition is met, the definition of the view or control is used.</span></span>

## <a name="specifying-a-selection-condition-for-a-definition"></a><span data-ttu-id="7cc26-106">Ange ett urvals villkor för en definition</span><span class="sxs-lookup"><span data-stu-id="7cc26-106">Specifying a Selection Condition for a Definition</span></span>

<span data-ttu-id="7cc26-107">När du skapar en definition för en vy eller kontroll, `EntrySelectedBy` används elementet för att ange vilka objekt som ska använda definitionen eller vilket villkor som måste finnas för att definitionen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="7cc26-107">When creating a definition for a view or control, the `EntrySelectedBy` element is used to specify which objects will use the definition or what condition must exist for the definition to be used.</span></span> <span data-ttu-id="7cc26-108">Villkoret anges av `SelectionCondition` elementet.</span><span class="sxs-lookup"><span data-stu-id="7cc26-108">The condition is specified by the `SelectionCondition` element.</span></span>

<span data-ttu-id="7cc26-109">I följande exempel anges ett urvals villkor för en definition av en tabellvy.</span><span class="sxs-lookup"><span data-stu-id="7cc26-109">In the following example, a selection condition is specified for a definition of a table view.</span></span> <span data-ttu-id="7cc26-110">I det här exemplet används definitionen endast när det angivna skriptet utvärderas till `true` .</span><span class="sxs-lookup"><span data-stu-id="7cc26-110">In this example, the definition is used only when the specified script is evaluated to `true`.</span></span>

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <SelectionCondition>
      <ScriptBlock>ScriptToEvaluate</ScriptBlock>
    </SelectionCondition>
  </EntrySelectedBy>
  <TableColumnItems>
  </TableColumnItems>
</TableRowEntry>

```

<span data-ttu-id="7cc26-111">Det finns ingen gräns för antalet urvals villkor som du kan ange för en definition av en vy eller kontroll.</span><span class="sxs-lookup"><span data-stu-id="7cc26-111">There is no limit to the number of selection conditions that you can specify for a definition of a view or control.</span></span> <span data-ttu-id="7cc26-112">De enda kraven är följande:</span><span class="sxs-lookup"><span data-stu-id="7cc26-112">The only requirements are the following:</span></span>

- <span data-ttu-id="7cc26-113">Markerings villkoret måste ange ett egenskaps namn eller skript för att utlösa villkoret, men det går inte att ange båda.</span><span class="sxs-lookup"><span data-stu-id="7cc26-113">The selection condition must specify one property name or script to trigger the condition, but cannot specify both.</span></span>

- <span data-ttu-id="7cc26-114">Urvals villkoret kan ange valfritt antal .NET-typer eller markerings uppsättningar, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="7cc26-114">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

## <a name="specifying-a-selection-condition-for-an-item"></a><span data-ttu-id="7cc26-115">Ange ett urvals villkor för ett objekt</span><span class="sxs-lookup"><span data-stu-id="7cc26-115">Specifying a Selection Condition for an Item</span></span>

<span data-ttu-id="7cc26-116">Du kan också ange när ett objekt i en listvy eller kontroll ska användas genom att inkludera `ItemSelectionCondition` elementet i objekt definitionen.</span><span class="sxs-lookup"><span data-stu-id="7cc26-116">You can also specify when an item of a list view or control is used by including the `ItemSelectionCondition` element in the item definition.</span></span> <span data-ttu-id="7cc26-117">I följande exempel anges ett urvals villkor för ett objekt i en listvy.</span><span class="sxs-lookup"><span data-stu-id="7cc26-117">In the following example, a selection condition is specified for an item of a list view.</span></span> <span data-ttu-id="7cc26-118">I det här exemplet används objektet bara när skriptet utvärderas till `true` .</span><span class="sxs-lookup"><span data-stu-id="7cc26-118">In this example, the item is used only when the script is evaluated to `true`.</span></span>

```xml
<ListItem>
  <ItemSelectionCondition>
    <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  </ItemSelectionCondition>
</ListItem>

```

<span data-ttu-id="7cc26-119">Du kan bara ange ett markerings villkor för ett objekt.</span><span class="sxs-lookup"><span data-stu-id="7cc26-119">You can specify only one selection condition for an item.</span></span> <span data-ttu-id="7cc26-120">Villkoret måste ange ett egenskaps namn eller skript för att utlösa villkoret, men det går inte att ange båda.</span><span class="sxs-lookup"><span data-stu-id="7cc26-120">And the condition must specify one property name or script to trigger the condition, but cannot specify both.</span></span>

## <a name="xml-elements"></a><span data-ttu-id="7cc26-121">XML-element</span><span class="sxs-lookup"><span data-stu-id="7cc26-121">XML Elements</span></span>

 <span data-ttu-id="7cc26-122">Följande XML-element används för att skapa ett urvals villkor.</span><span class="sxs-lookup"><span data-stu-id="7cc26-122">The following XML elements are used to create a selection condition.</span></span>

- <span data-ttu-id="7cc26-123">Följande element anger urvals villkor för visnings definitioner:</span><span class="sxs-lookup"><span data-stu-id="7cc26-123">The following elements specify selection conditions for view definitions:</span></span>

  - [<span data-ttu-id="7cc26-124">SelectionCondition-element för EntrySelectedBy för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="7cc26-124">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

  - [<span data-ttu-id="7cc26-125">SelectionCondition-element för EntrySelectedBy för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="7cc26-125">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

  - [<span data-ttu-id="7cc26-126">SelectionCondition-element för EntrySelectedBy för WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="7cc26-126">SelectionCondition Element for EntrySelectedBy for WideControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

  - [<span data-ttu-id="7cc26-127">SelectionCondition-element för EntrySelectedBy för CustomControl (format)</span><span class="sxs-lookup"><span data-stu-id="7cc26-127">SelectionCondition Element for EntrySelectedBy for CustomControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

- <span data-ttu-id="7cc26-128">Följande element anger urvals villkor för vanliga och Visa kontroll definitioner:</span><span class="sxs-lookup"><span data-stu-id="7cc26-128">The following elements specify selection conditions for common and view control definitions:</span></span>

  - [<span data-ttu-id="7cc26-129">SelectionCondition-element för EntrySelectedBy för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="7cc26-129">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

  - [<span data-ttu-id="7cc26-130">SelectionCondition-element för EntrySelectedBy för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="7cc26-130">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

- <span data-ttu-id="7cc26-131">Följande element anger urvals villkoret för att expandera samlings objekt:</span><span class="sxs-lookup"><span data-stu-id="7cc26-131">The following element specifies the selection condition for expanding collection objects:</span></span>

  - [<span data-ttu-id="7cc26-132">SelectionCondition-element för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="7cc26-132">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

- <span data-ttu-id="7cc26-133">Följande element anger urvals villkoret för att visa en ny grupp med data:</span><span class="sxs-lookup"><span data-stu-id="7cc26-133">The following element specifies the selection condition for displaying a new group of data:</span></span>

  - [<span data-ttu-id="7cc26-134">SelectionCondition-element för EntrySelectedBy för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="7cc26-134">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

- <span data-ttu-id="7cc26-135">Följande element anger ett objekt urvals villkor för en listvy:</span><span class="sxs-lookup"><span data-stu-id="7cc26-135">The following element specifies an item selection condition for a list view:</span></span>

  - [<span data-ttu-id="7cc26-136">ItemSelectionCondition-element för ListItem för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="7cc26-136">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

- <span data-ttu-id="7cc26-137">Följande element anger ett objekt urvals villkor för kontroller:</span><span class="sxs-lookup"><span data-stu-id="7cc26-137">The following elements specify an item selection condition for controls:</span></span>

  - [<span data-ttu-id="7cc26-138">ItemSelectionCondition-element för ExpressionBinding för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="7cc26-138">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

  - [<span data-ttu-id="7cc26-139">ItemSelectionCondition-element för ExpressionBinding för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="7cc26-139">ItemSelectionCondition Element for ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

  - [<span data-ttu-id="7cc26-140">ItemSelectionCondition-element för ExpressionBinding för CustomControl (format)</span><span class="sxs-lookup"><span data-stu-id="7cc26-140">ItemSelectionCondition Element for ExpressionBinding for CustomControl (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

## <a name="see-also"></a><span data-ttu-id="7cc26-141">Se även</span><span class="sxs-lookup"><span data-stu-id="7cc26-141">See Also</span></span>

[<span data-ttu-id="7cc26-142">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="7cc26-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
