---
title: Definiera villkor för att visa Data | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c1e05821-6aec-437b-84a5-218a5727f88b
caps.latest.revision: 10
ms.openlocfilehash: 8a5b84b6a461e9fc340a5981578d95ca2ac6b9f7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846566"
---
# <a name="defining-conditions-for-displaying-data"></a><span data-ttu-id="ce09e-102">Definiera villkor för datavisning</span><span class="sxs-lookup"><span data-stu-id="ce09e-102">Defining Conditions for Displaying Data</span></span>

<span data-ttu-id="ce09e-103">När du definierar vilka data som visas genom en vy eller en kontroll måste ange du ett villkor som måste finnas för data som ska visas.</span><span class="sxs-lookup"><span data-stu-id="ce09e-103">When defining what data is displayed by a view or a control, you can specify a condition that must exist for the data to be displayed.</span></span> <span data-ttu-id="ce09e-104">Villkoret kan utlösas av en specifik egenskap, eller när ett skript eller egenskapsvärdet utvärderas till `true`.</span><span class="sxs-lookup"><span data-stu-id="ce09e-104">The condition can be triggered by a specific property, or when a script or property value evaluates to `true`.</span></span> <span data-ttu-id="ce09e-105">När val av villkor är uppfyllt, används definitionen av vyn eller kontroll.</span><span class="sxs-lookup"><span data-stu-id="ce09e-105">When the selection condition is met, the definition of the view or control is used.</span></span>

## <a name="specifying-a-selection-condition-for-a-definition"></a><span data-ttu-id="ce09e-106">Ange ett villkor för val av en definition</span><span class="sxs-lookup"><span data-stu-id="ce09e-106">Specifying a Selection Condition for a Definition</span></span>

<span data-ttu-id="ce09e-107">När du skapar en definition för en vy eller en kontroll, den `EntrySelectedBy` elementet används för att ange vilka objekt använder definitionen eller vilket villkor som måste finnas för definitionen som ska användas.</span><span class="sxs-lookup"><span data-stu-id="ce09e-107">When creating a definition for a view or control, the `EntrySelectedBy` element is used to specify which objects will use the definition or what condition must exist for the definition to be used.</span></span> <span data-ttu-id="ce09e-108">Villkoret har angetts av den `SelectionCondition` element.</span><span class="sxs-lookup"><span data-stu-id="ce09e-108">The condition is specified by the `SelectionCondition` element.</span></span>

<span data-ttu-id="ce09e-109">I exemplet nedan anges ett val av villkor för en definition av en tabellvy.</span><span class="sxs-lookup"><span data-stu-id="ce09e-109">In the following example, a selection condition is specified for a definition of a table view.</span></span> <span data-ttu-id="ce09e-110">I det här exemplet definitionen används endast när det angivna skriptet utvärderas till `true`.</span><span class="sxs-lookup"><span data-stu-id="ce09e-110">In this example, the definition is used only when the specified script is evaluated to `true`.</span></span>

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

<span data-ttu-id="ce09e-111">Det finns ingen gräns för hur många val av villkor som du kan ange en definition av en vy eller kontroll.</span><span class="sxs-lookup"><span data-stu-id="ce09e-111">There is no limit to the number of selection conditions that you can specify for a definition of a view or control.</span></span> <span data-ttu-id="ce09e-112">De enda kraven är följande:</span><span class="sxs-lookup"><span data-stu-id="ce09e-112">The only requirements are the following:</span></span>

- <span data-ttu-id="ce09e-113">Urvalsvillkoret måste ange ett egenskapsnamn och skript för att utlösa villkoret, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="ce09e-113">The selection condition must specify one property name or script to trigger the condition, but cannot specify both.</span></span>

- <span data-ttu-id="ce09e-114">Urvalsvillkoret kan ange valfritt antal typer i .NET eller val av anger, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="ce09e-114">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

## <a name="specifying-a-selection-condition-for-an-item"></a><span data-ttu-id="ce09e-115">Ange ett villkor för val av för ett objekt</span><span class="sxs-lookup"><span data-stu-id="ce09e-115">Specifying a Selection Condition for an Item</span></span>

<span data-ttu-id="ce09e-116">Du kan också ange när ett objekt av en listvy eller kontroll används genom att inkludera den `ItemSelectionCondition` element i definitionen av objektet.</span><span class="sxs-lookup"><span data-stu-id="ce09e-116">You can also specify when an item of a list view or control is used by including the `ItemSelectionCondition` element in the item definition.</span></span> <span data-ttu-id="ce09e-117">I exemplet nedan anges ett val av villkor för objekt av en listvy.</span><span class="sxs-lookup"><span data-stu-id="ce09e-117">In the following example, a selection condition is specified for an item of a list view.</span></span> <span data-ttu-id="ce09e-118">I det här exemplet artikeln används bara när skriptet har utvärderats till `true`.</span><span class="sxs-lookup"><span data-stu-id="ce09e-118">In this example, the item is used only when the script is evaluated to `true`.</span></span>

```xml
<ListItem>
  <ItemSelectionCondition>
    <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  </ItemSelectionCondition>
</ListItem>

```

<span data-ttu-id="ce09e-119">Du kan ange endast en urvalsvillkoret för ett objekt.</span><span class="sxs-lookup"><span data-stu-id="ce09e-119">You can specify only one selection condition for an item.</span></span> <span data-ttu-id="ce09e-120">Och villkoret måste ange ett egenskapsnamn och skript för att utlösa villkoret, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="ce09e-120">And the condition must specify one property name or script to trigger the condition, but cannot specify both.</span></span>

## <a name="xml-elements"></a><span data-ttu-id="ce09e-121">XML-element</span><span class="sxs-lookup"><span data-stu-id="ce09e-121">XML Elements</span></span>

 <span data-ttu-id="ce09e-122">Följande XML-element används för att skapa ett val av villkor.</span><span class="sxs-lookup"><span data-stu-id="ce09e-122">The following XML elements are used to create a selection condition.</span></span>

- <span data-ttu-id="ce09e-123">Följande element anger val av villkor för vydefinitioner:</span><span class="sxs-lookup"><span data-stu-id="ce09e-123">The following elements specify selection conditions for view definitions:</span></span>

    - [<span data-ttu-id="ce09e-124">SelectionCondition Element för EntrySelectedBy för TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="ce09e-124">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

    - [<span data-ttu-id="ce09e-125">SelectionCondition Element för EntrySelectedBy för ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="ce09e-125">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

    - [<span data-ttu-id="ce09e-126">SelectionCondition Element för EntrySelectedBy för WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="ce09e-126">SelectionCondition Element for EntrySelectedBy for WideControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

    - [<span data-ttu-id="ce09e-127">SelectionCondition Element för EntrySelectedBy för anpassad kontroll (Format)</span><span class="sxs-lookup"><span data-stu-id="ce09e-127">SelectionCondition Element for EntrySelectedBy for CustomControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-customcontrol-format.md)

- <span data-ttu-id="ce09e-128">Följande element anger val av villkor för gemensamma och visa styra definitioner:</span><span class="sxs-lookup"><span data-stu-id="ce09e-128">The following elements specify selection conditions for common and view control definitions:</span></span>

    - [<span data-ttu-id="ce09e-129">SelectionCondition Element för EntrySelectedBy för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="ce09e-129">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

    - [<span data-ttu-id="ce09e-130">SelectionCondition Element för EntrySelectedBy för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="ce09e-130">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-view-format.md)

- <span data-ttu-id="ce09e-131">Följande element anger urvalsvillkoret för att expandera samlingen objekt:</span><span class="sxs-lookup"><span data-stu-id="ce09e-131">The following element specifies the selection condition for expanding collection objects:</span></span>

    - [<span data-ttu-id="ce09e-132">SelectionCondition Element för EntrySelectedBy för EnumerableExpansion (Format)</span><span class="sxs-lookup"><span data-stu-id="ce09e-132">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

- <span data-ttu-id="ce09e-133">Följande element anger urvalsvillkoret för att visa en ny grupp av data:</span><span class="sxs-lookup"><span data-stu-id="ce09e-133">The following element specifies the selection condition for displaying a new group of data:</span></span>

    - [<span data-ttu-id="ce09e-134">SelectionCondition Element för EntrySelectedBy för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="ce09e-134">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

- <span data-ttu-id="ce09e-135">Följande element anger ett villkor för val av objekt för en listvy:</span><span class="sxs-lookup"><span data-stu-id="ce09e-135">The following element specifies an item selection condition for a list view:</span></span>

    - [<span data-ttu-id="ce09e-136">ItemSelectionCondition Element för ListItem för ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="ce09e-136">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)

- <span data-ttu-id="ce09e-137">Följande element ange ett villkor för val av objekt för kontroller:</span><span class="sxs-lookup"><span data-stu-id="ce09e-137">The following elements specify an item selection condition for controls:</span></span>

    - [<span data-ttu-id="ce09e-138">ItemSelectionCondition Element för ExpressionBinding för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="ce09e-138">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

    - [<span data-ttu-id="ce09e-139">ItemSelectionCondition Element för ExpressionBinding för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="ce09e-139">ItemSelectionCondition Element for ExpressionBinding for Controls for View (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-view-format.md)

    - [<span data-ttu-id="ce09e-140">ItemSelectionCondition Element för ExpressionBinding för anpassad kontroll (Format)</span><span class="sxs-lookup"><span data-stu-id="ce09e-140">ItemSelectionCondition Element for ExpressionBinding for CustomControl (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-customcontrol-format.md)

## <a name="see-also"></a><span data-ttu-id="ce09e-141">Se även</span><span class="sxs-lookup"><span data-stu-id="ce09e-141">See Also</span></span>

[<span data-ttu-id="ce09e-142">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="ce09e-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
