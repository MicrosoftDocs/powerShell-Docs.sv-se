---
title: ScriptBlock Element för ItemSeclectionCondition för kontroller för konfiguration (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 51f7aec9-7b01-4370-84f4-1e58508a851f
caps.latest.revision: 6
ms.openlocfilehash: e92b2dfff07358132c480c47c34279e5365fe400
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064449"
---
# <a name="scriptblock-element-for-itemseclectioncondition-for-controls-for-configuration-format"></a><span data-ttu-id="e3adb-102">ScriptBlock-element för ItemSeclectionCondition för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="e3adb-102">ScriptBlock Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>

<span data-ttu-id="e3adb-103">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="e3adb-103">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="e3adb-104">När det här skriptet ska utvärderas till `true`villkoret uppfylls och kontrollen används.</span><span class="sxs-lookup"><span data-stu-id="e3adb-104">When this script is evaluated to `true`, the condition is met, and the control is used.</span></span> <span data-ttu-id="e3adb-105">Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i filen formatering.</span><span class="sxs-lookup"><span data-stu-id="e3adb-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="e3adb-106">Konfigurationselementet Element (Format) kontroller av (Format) kontroll konfigurationselement för kontroller för (Format) anpassad kontroll konfigurationselement för kontroll för (Format) CustomEntries konfigurationselement för anpassad kontroll för konfiguration ( Format) CustomEntry Element för anpassad kontroll för kontroller för (Format) CustomItem konfigurationselement för CustomEntry för kontroller för ExpressionBinding konfigurationselement för CustomItem för kontroller för konfiguration (Format) ItemSelectionCondition Element för ExpressionBinding för kontroller för (Format) ScriptBlock konfigurationselement för ItemSelectionCondition för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="e3adb-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration ExpressionBinding Element for CustomItem for Controls for Configuration (Format) ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format) ScriptBlock Element for ItemSelectionCondition for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e3adb-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="e3adb-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e3adb-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="e3adb-108">Attributes and Elements</span></span>

<span data-ttu-id="e3adb-109">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `ScriptBlock` element.</span><span class="sxs-lookup"><span data-stu-id="e3adb-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e3adb-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="e3adb-110">Attributes</span></span>

<span data-ttu-id="e3adb-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="e3adb-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e3adb-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="e3adb-112">Child Elements</span></span>

<span data-ttu-id="e3adb-113">Ingen.</span><span class="sxs-lookup"><span data-stu-id="e3adb-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e3adb-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="e3adb-114">Parent Elements</span></span>

|<span data-ttu-id="e3adb-115">Element</span><span class="sxs-lookup"><span data-stu-id="e3adb-115">Element</span></span>|<span data-ttu-id="e3adb-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e3adb-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e3adb-117">ItemSelectionCondition Element för ExpressionBinding för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="e3adb-117">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)|<span data-ttu-id="e3adb-118">Definierar de villkor som måste finnas för den här kontrollen som ska användas.</span><span class="sxs-lookup"><span data-stu-id="e3adb-118">Defines the condition that must exist for this control to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e3adb-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="e3adb-119">Text Value</span></span>

<span data-ttu-id="e3adb-120">Ange det skript som ska utvärderas.</span><span class="sxs-lookup"><span data-stu-id="e3adb-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="e3adb-121">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="e3adb-121">Remarks</span></span>

<span data-ttu-id="e3adb-122">Om det här elementet används som du kan inte ange den [PropertyName](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) element när du definierar urvalsvillkoret.</span><span class="sxs-lookup"><span data-stu-id="e3adb-122">If this element is used, you cannot specify the [PropertyName](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md) element when defining the selection condition.</span></span>

## <a name="see-also"></a><span data-ttu-id="e3adb-123">Se även</span><span class="sxs-lookup"><span data-stu-id="e3adb-123">See Also</span></span>

[<span data-ttu-id="e3adb-124">PropertyName-Element för ItemSeclectionCondition för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="e3adb-124">PropertyName Element for ItemSeclectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-itemseclectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="e3adb-125">ItemSelectionCondition Element för ExpressionBinding för kontroller för konfiguration (Format)</span><span class="sxs-lookup"><span data-stu-id="e3adb-125">ItemSelectionCondition Element for ExpressionBinding for Controls for Configuration (Format)</span></span>](./itemselectioncondition-element-for-expressionbinding-for-controls-for-configuration-format.md)

[<span data-ttu-id="e3adb-126">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="e3adb-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
