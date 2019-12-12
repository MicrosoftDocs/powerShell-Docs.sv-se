---
title: Kontrollerar element för konfiguration (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4d4ef63d-5866-4319-ba00-7ed96de26821
caps.latest.revision: 18
ms.openlocfilehash: ac9f7ff08f6e87ef83b5a2fe23fc58ee2651566d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359097"
---
# <a name="controls-element-for-configuration-format"></a><span data-ttu-id="064df-102">Controls-element för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="064df-102">Controls Element for Configuration (Format)</span></span>

<span data-ttu-id="064df-103">Definierar de gemensamma kontroller som kan användas av alla vyer i formaterings filen.</span><span class="sxs-lookup"><span data-stu-id="064df-103">Defines the common controls that can be used by all views of the formatting file.</span></span>

<span data-ttu-id="064df-104">Konfigurations element (format) styr elementet i konfigurationen (format)</span><span class="sxs-lookup"><span data-stu-id="064df-104">Configuration Element (Format) Controls Element of Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="064df-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="064df-105">Syntax</span></span>

```xml
<Controls>
  <Control>...</Control>
</Controls>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="064df-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="064df-106">Attributes and Elements</span></span>

<span data-ttu-id="064df-107">I följande avsnitt beskrivs attributen, underordnade element och det överordnade elementet i `Controls`-elementet.</span><span class="sxs-lookup"><span data-stu-id="064df-107">The following sections describe the attributes, child elements, and the parent element of the `Controls` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="064df-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="064df-108">Attributes</span></span>

<span data-ttu-id="064df-109">Ingen.</span><span class="sxs-lookup"><span data-stu-id="064df-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="064df-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="064df-110">Child Elements</span></span>

|<span data-ttu-id="064df-111">Element</span><span class="sxs-lookup"><span data-stu-id="064df-111">Element</span></span>|<span data-ttu-id="064df-112">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="064df-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="064df-113">Kontroll element för konfigurations kontroll (format)</span><span class="sxs-lookup"><span data-stu-id="064df-113">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)|<span data-ttu-id="064df-114">Nödvändigt element.</span><span class="sxs-lookup"><span data-stu-id="064df-114">Required element.</span></span><br /><br /> <span data-ttu-id="064df-115">Definierar en gemensam kontroll som kan användas av alla vyer i formaterings filen.</span><span class="sxs-lookup"><span data-stu-id="064df-115">Defines a common control that can be used by all views of the formatting file.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="064df-116">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="064df-116">Parent Elements</span></span>

|<span data-ttu-id="064df-117">Element</span><span class="sxs-lookup"><span data-stu-id="064df-117">Element</span></span>|<span data-ttu-id="064df-118">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="064df-118">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="064df-119">Konfigurations element (format)</span><span class="sxs-lookup"><span data-stu-id="064df-119">Configuration Element (Format)</span></span>](./configuration-element-format.md)|<span data-ttu-id="064df-120">Representerar det översta elementet i en textfil.</span><span class="sxs-lookup"><span data-stu-id="064df-120">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="064df-121">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="064df-121">Remarks</span></span>

<span data-ttu-id="064df-122">Du kan skapa valfritt antal vanliga kontroller.</span><span class="sxs-lookup"><span data-stu-id="064df-122">You can create any number of common controls.</span></span> <span data-ttu-id="064df-123">För varje kontroll måste du ange det namn som ska användas för att referera till kontrollen och kontrollens komponenter.</span><span class="sxs-lookup"><span data-stu-id="064df-123">For each control, you must specify the name that is used to reference the control and the components of the control.</span></span>

## <a name="see-also"></a><span data-ttu-id="064df-124">Se även</span><span class="sxs-lookup"><span data-stu-id="064df-124">See Also</span></span>

[<span data-ttu-id="064df-125">Konfigurations element (format)</span><span class="sxs-lookup"><span data-stu-id="064df-125">Configuration Element (Format)</span></span>](./configuration-element-format.md)

[<span data-ttu-id="064df-126">Kontroll element för konfigurations kontroll (format)</span><span class="sxs-lookup"><span data-stu-id="064df-126">Control Element for Controls for Configuration (Format)</span></span>](./control-element-for-controls-for-configuration-format.md)

[<span data-ttu-id="064df-127">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="064df-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
