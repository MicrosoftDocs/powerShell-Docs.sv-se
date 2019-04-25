---
title: ScriptBlock Element för SelectionCondition för kontroller för konfiguration (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bb032dfc-9ef6-403c-b557-5858617e3483
caps.latest.revision: 6
ms.openlocfilehash: 102987970152420896a0c986f0973280ae209623
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064432"
---
# <a name="scriptblock-element-for-selectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="df4ed-102">ScriptBlock-element för SelectionCondition för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="df4ed-102">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="df4ed-103">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="df4ed-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="df4ed-104">När det här skriptet ska utvärderas till `true`villkoret uppfylls och definitionen används.</span><span class="sxs-lookup"><span data-stu-id="df4ed-104">When this script is evaluated to `true`, the condition is met, and the definition is used.</span></span> <span data-ttu-id="df4ed-105">Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i filen formatering.</span><span class="sxs-lookup"><span data-stu-id="df4ed-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="df4ed-106">Konfigurationselementet Element (Format) kontroller av (Format) kontroll konfigurationselement för kontroller för (Format) anpassad kontroll konfigurationselement för kontroll för (Format) CustomEntries konfigurationselement för anpassad kontroll för konfiguration ( Format) CustomEntry Element för anpassad kontroll för kontroller för (Format) EntrySelectedBy konfigurationselement för CustomEntry för kontroller för (Format) SelectionCondition konfigurationselement för EntrySelectedBy för kontroller för konfiguration (Format) ScriptBlock Element för SelectionCondition för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="df4ed-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format) ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="df4ed-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="df4ed-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="df4ed-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="df4ed-108">Attributes and Elements</span></span>

<span data-ttu-id="df4ed-109">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `ScriptBlock` element.</span><span class="sxs-lookup"><span data-stu-id="df4ed-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="df4ed-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="df4ed-110">Attributes</span></span>

<span data-ttu-id="df4ed-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="df4ed-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="df4ed-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="df4ed-112">Child Elements</span></span>

<span data-ttu-id="df4ed-113">Ingen.</span><span class="sxs-lookup"><span data-stu-id="df4ed-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="df4ed-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="df4ed-114">Parent Elements</span></span>

|<span data-ttu-id="df4ed-115">Element</span><span class="sxs-lookup"><span data-stu-id="df4ed-115">Element</span></span>|<span data-ttu-id="df4ed-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="df4ed-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="df4ed-117">SelectionCondition Element för EntrySelectedBy för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="df4ed-117">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|<span data-ttu-id="df4ed-118">Definierar ett villkor som måste finnas för de gemensamma definitionerna för kontrollen som ska användas.</span><span class="sxs-lookup"><span data-stu-id="df4ed-118">Defines a condition that must exist for the common control definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="df4ed-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="df4ed-119">Text Value</span></span>

<span data-ttu-id="df4ed-120">Ange det skript som ska utvärderas.</span><span class="sxs-lookup"><span data-stu-id="df4ed-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="df4ed-121">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="df4ed-121">Remarks</span></span>

<span data-ttu-id="df4ed-122">Urvalsvillkoret måste ange ett minst ett skript eller egenskapen namn för att utvärdera, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="df4ed-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="df4ed-123">Läs mer om hur du kan använda villkor för val av [definiera villkor för att visa Data](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="df4ed-123">For more information about how selection conditions can be used, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="df4ed-124">Se även</span><span class="sxs-lookup"><span data-stu-id="df4ed-124">See Also</span></span>

[<span data-ttu-id="df4ed-125">SelectionCondition Element för EntrySelectedBy för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="df4ed-125">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[<span data-ttu-id="df4ed-126">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="df4ed-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
