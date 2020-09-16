---
title: Kontroll element för konfigurations kontroll (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 9447efac84cff3cc33468aeebc97a8bdd6137518
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783831"
---
# <a name="control-element-for-controls-for-configuration-format"></a><span data-ttu-id="82f95-102">Control-element för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="82f95-102">Control Element for Controls for Configuration (Format)</span></span>

<span data-ttu-id="82f95-103">Definierar en gemensam kontroll som kan användas av alla vyer i format filen och det namn som används för att referera till kontrollen.</span><span class="sxs-lookup"><span data-stu-id="82f95-103">Defines a common control that can be used by all the views of the formatting file and the name that is used to reference the control.</span></span>

<span data-ttu-id="82f95-104">Konfigurations element (format) styr element i konfigurations-(format) kontroll element för konfigurations inställningar (format)</span><span class="sxs-lookup"><span data-stu-id="82f95-104">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="82f95-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="82f95-105">Syntax</span></span>

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="82f95-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="82f95-106">Attributes and Elements</span></span>

<span data-ttu-id="82f95-107">I följande avsnitt beskrivs attributen, underordnade element och `Control` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="82f95-107">The following sections describe the attributes, child elements, and the parent element for the `Control` element.</span></span> <span data-ttu-id="82f95-108">Du måste ange ett av varje underordnat element.</span><span class="sxs-lookup"><span data-stu-id="82f95-108">You must specify only one of each child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="82f95-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="82f95-109">Attributes</span></span>

<span data-ttu-id="82f95-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="82f95-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="82f95-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="82f95-111">Child Elements</span></span>

|<span data-ttu-id="82f95-112">Element</span><span class="sxs-lookup"><span data-stu-id="82f95-112">Element</span></span>|<span data-ttu-id="82f95-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="82f95-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="82f95-114">CustomControl-element för Control för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="82f95-114">CustomControl Element for Control for Controls for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="82f95-115">Nödvändigt element.</span><span class="sxs-lookup"><span data-stu-id="82f95-115">Required element.</span></span><br /><br /> <span data-ttu-id="82f95-116">Definierar kontrollen.</span><span class="sxs-lookup"><span data-stu-id="82f95-116">Defines the control.</span></span>|
|[<span data-ttu-id="82f95-117">Namn element för kontroll av konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="82f95-117">Name Element for Control for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="82f95-118">Nödvändigt element.</span><span class="sxs-lookup"><span data-stu-id="82f95-118">Required element.</span></span><br /><br /> <span data-ttu-id="82f95-119">Anger det namn som ska användas för att referera till kontrollen.</span><span class="sxs-lookup"><span data-stu-id="82f95-119">Specifies the name used to reference the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="82f95-120">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="82f95-120">Parent Elements</span></span>

|<span data-ttu-id="82f95-121">Element</span><span class="sxs-lookup"><span data-stu-id="82f95-121">Element</span></span>|<span data-ttu-id="82f95-122">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="82f95-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="82f95-123">Kontrollerar konfigurations element (format)</span><span class="sxs-lookup"><span data-stu-id="82f95-123">Controls Element of Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)|<span data-ttu-id="82f95-124">Definierar de vanliga kontroller som kan användas av alla vyer i formaterings filen eller av andra kontroller.</span><span class="sxs-lookup"><span data-stu-id="82f95-124">Defines the common controls that can be used by all views of the formatting file or by other controls.</span></span>|

## <a name="remarks"></a><span data-ttu-id="82f95-125">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="82f95-125">Remarks</span></span>

<span data-ttu-id="82f95-126">Det namn som ges till den här kontrollen kan refereras till i följande element:</span><span class="sxs-lookup"><span data-stu-id="82f95-126">The name given to this control can be referenced in the following elements:</span></span>

- [<span data-ttu-id="82f95-127">ExpressionBinding-element för CustomItem (format)</span><span class="sxs-lookup"><span data-stu-id="82f95-127">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- [<span data-ttu-id="82f95-128">GroupBy-element för vy (format)</span><span class="sxs-lookup"><span data-stu-id="82f95-128">GroupBy Element for View(Format)</span></span>](./groupby-element-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="82f95-129">Se även</span><span class="sxs-lookup"><span data-stu-id="82f95-129">See Also</span></span>

[<span data-ttu-id="82f95-130">Kontrollerar konfigurations element (format)</span><span class="sxs-lookup"><span data-stu-id="82f95-130">Controls Element of Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)

[<span data-ttu-id="82f95-131">CustomControl-element för kontroll av konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="82f95-131">CustomControl element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="82f95-132">ExpressionBinding-element för CustomItem (format)</span><span class="sxs-lookup"><span data-stu-id="82f95-132">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="82f95-133">GroupBy-element för vy (format)</span><span class="sxs-lookup"><span data-stu-id="82f95-133">GroupBy Element for View(Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="82f95-134">Name-element för Control för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="82f95-134">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="82f95-135">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="82f95-135">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
