---
ms.date: 2017-08-25
keywords: PowerShell-cmdlet
title: Objektet ObjectModelRoot
ms.openlocfilehash: eb3424ff147c35364fa08543d59ebd30f6d2d857
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/08/2017
---
# <a name="the-objectmodelroot-object"></a><span data-ttu-id="ef861-103">Objektet ObjectModelRoot</span><span class="sxs-lookup"><span data-stu-id="ef861-103">The ObjectModelRoot Object</span></span>

<span data-ttu-id="ef861-104">Den **$psISE** -objektet, vilket är det viktigaste rotobjektet i Windows PowerShell® Integrated Scripting Environment (ISE) är en instans av klassen Microsoft.PowerShell.Host.ISE.ObjectModelRoot.</span><span class="sxs-lookup"><span data-stu-id="ef861-104">The **$psISE** object, which is the principal root object in Windows PowerShell® Integrated Scripting Environment (ISE) is an instance of the Microsoft.PowerShell.Host.ISE.ObjectModelRoot class.</span></span>
<span data-ttu-id="ef861-105">Det här avsnittet beskriver egenskaperna för den **ObjectModelRoot** objekt.</span><span class="sxs-lookup"><span data-stu-id="ef861-105">This topic describes the properties of the **ObjectModelRoot** object.</span></span>

## <a name="properties"></a><span data-ttu-id="ef861-106">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="ef861-106">Properties</span></span>

### <a name="currentfile"></a><span data-ttu-id="ef861-107">CurrentFile</span><span class="sxs-lookup"><span data-stu-id="ef861-107">CurrentFile</span></span>

> <span data-ttu-id="ef861-108">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="ef861-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

<span data-ttu-id="ef861-109">Den skrivskyddade egenskapen som hämtar filen, som är associerat med denna Värdobjektet som har fokus för tillfället.</span><span class="sxs-lookup"><span data-stu-id="ef861-109">The read-only property that gets the file, which is associated with this host object that currently has the focus.</span></span>

### <a name="currentpowershelltab"></a><span data-ttu-id="ef861-110">CurrentPowerShellTab</span><span class="sxs-lookup"><span data-stu-id="ef861-110">CurrentPowerShellTab</span></span>

> <span data-ttu-id="ef861-111">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="ef861-111">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="ef861-112">Den skrivskyddade egenskapen som hämtar fliken PowerShell som har fokus.</span><span class="sxs-lookup"><span data-stu-id="ef861-112">The read-only property that gets the PowerShell tab that has the focus.</span></span>

### <a name="currentvisiblehorizontaltool"></a><span data-ttu-id="ef861-113">CurrentVisibleHorizontalTool</span><span class="sxs-lookup"><span data-stu-id="ef861-113">CurrentVisibleHorizontalTool</span></span>

> <span data-ttu-id="ef861-114">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="ef861-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="ef861-115">Skrivskyddad egenskap som hämtar synliga tilläggsverktyg för Windows PowerShell ISE som finns i verktygsfönstret vågräta längst ned i redigeraren.</span><span class="sxs-lookup"><span data-stu-id="ef861-115">The read-only property that gets the currently visible Windows PowerShell ISE add-on tool that is located in the horizontal tool pane at the bottom of the editor.</span></span>

### <a name="currentvisibleverticaltool"></a><span data-ttu-id="ef861-116">CurrentVisibleVerticalTool</span><span class="sxs-lookup"><span data-stu-id="ef861-116">CurrentVisibleVerticalTool</span></span>

> <span data-ttu-id="ef861-117">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="ef861-117">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

<span data-ttu-id="ef861-118">Skrivskyddad egenskap som hämtar synliga tilläggsverktyg för Windows PowerShell ISE som finns i verktygsfönstret lodräta på höger sida av redigeraren.</span><span class="sxs-lookup"><span data-stu-id="ef861-118">The read-only property that gets the currently visible Windows PowerShell ISE add-on tool that is located in the vertical tool pane on the right side of the editor.</span></span>

### <a name="options"></a><span data-ttu-id="ef861-119">Options</span><span class="sxs-lookup"><span data-stu-id="ef861-119">Options</span></span>

> <span data-ttu-id="ef861-120">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="ef861-120">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

<span data-ttu-id="ef861-121">Skrivskyddad egenskap som hämtar de olika alternativ som kan ändra inställningar i Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="ef861-121">The read-only property that gets the various options that can change settings in Windows PowerShell ISE.</span></span>

### <a name="powershelltabs"></a><span data-ttu-id="ef861-122">PowerShellTabs</span><span class="sxs-lookup"><span data-stu-id="ef861-122">PowerShellTabs</span></span>

> <span data-ttu-id="ef861-123">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="ef861-123">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

<span data-ttu-id="ef861-124">Den skrivskyddade egenskapen som hämtar insamling av PowerShell-flikar som är öppna i Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="ef861-124">The read-only property that gets the collection of the PowerShell tabs, which are open in Windows PowerShell ISE.</span></span> <span data-ttu-id="ef861-125">Det här objektet innehåller som standard en PowerShell-flik. Men du kan lägga till fler PowerShell flikar objektet med hjälp av skript eller genom att använda menyerna i Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="ef861-125">By default, this object contains one PowerShell tab. However, you can add more PowerShell tabs to this object by using scripts or by using the menus in Windows PowerShell ISE.</span></span>

## <a name="see-also"></a><span data-ttu-id="ef861-126">Se även</span><span class="sxs-lookup"><span data-stu-id="ef861-126">See Also</span></span>

- [<span data-ttu-id="ef861-127">Windows PowerShell ISE Scripting Object Model</span><span class="sxs-lookup"><span data-stu-id="ef861-127">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="ef861-128">Windows PowerShell ISE objektreferens modellen</span><span class="sxs-lookup"><span data-stu-id="ef861-128">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md)
- [<span data-ttu-id="ef861-129">Modellen objekthierarkin ISE</span><span class="sxs-lookup"><span data-stu-id="ef861-129">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
