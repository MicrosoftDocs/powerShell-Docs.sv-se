---
ms.date: 08/25/2017
keywords: PowerShell-cmdlet
title: ObjectModelRoot-objektet
ms.openlocfilehash: 2670321ebac1eac4ecc8457afb796f9f260da471
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="the-objectmodelroot-object"></a><span data-ttu-id="90135-103">ObjectModelRoot-objektet</span><span class="sxs-lookup"><span data-stu-id="90135-103">The ObjectModelRoot Object</span></span>

<span data-ttu-id="90135-104">Den **$psISE** -objektet, vilket är det viktigaste rotobjektet i Windows PowerShell® Integrated Scripting Environment (ISE) är en instans av klassen Microsoft.PowerShell.Host.ISE.ObjectModelRoot.</span><span class="sxs-lookup"><span data-stu-id="90135-104">The **$psISE** object, which is the principal root object in Windows PowerShell® Integrated Scripting Environment (ISE) is an instance of the Microsoft.PowerShell.Host.ISE.ObjectModelRoot class.</span></span>
<span data-ttu-id="90135-105">Det här avsnittet beskriver egenskaperna för den **ObjectModelRoot** objekt.</span><span class="sxs-lookup"><span data-stu-id="90135-105">This topic describes the properties of the **ObjectModelRoot** object.</span></span>

## <a name="properties"></a><span data-ttu-id="90135-106">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="90135-106">Properties</span></span>

### <a name="currentfile"></a><span data-ttu-id="90135-107">CurrentFile</span><span class="sxs-lookup"><span data-stu-id="90135-107">CurrentFile</span></span>

> <span data-ttu-id="90135-108">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="90135-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="90135-109">Den skrivskyddade egenskapen som hämtar filen, som är associerat med denna Värdobjektet som har fokus för tillfället.</span><span class="sxs-lookup"><span data-stu-id="90135-109">The read-only property that gets the file, which is associated with this host object that currently has the focus.</span></span>

### <a name="currentpowershelltab"></a><span data-ttu-id="90135-110">CurrentPowerShellTab</span><span class="sxs-lookup"><span data-stu-id="90135-110">CurrentPowerShellTab</span></span>

> <span data-ttu-id="90135-111">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="90135-111">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="90135-112">Den skrivskyddade egenskapen som hämtar fliken PowerShell som har fokus.</span><span class="sxs-lookup"><span data-stu-id="90135-112">The read-only property that gets the PowerShell tab that has the focus.</span></span>

### <a name="currentvisiblehorizontaltool"></a><span data-ttu-id="90135-113">CurrentVisibleHorizontalTool</span><span class="sxs-lookup"><span data-stu-id="90135-113">CurrentVisibleHorizontalTool</span></span>

> <span data-ttu-id="90135-114">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="90135-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="90135-115">Skrivskyddad egenskap som hämtar synliga tilläggsverktyg för Windows PowerShell ISE som finns i verktygsfönstret vågräta längst ned i redigeraren.</span><span class="sxs-lookup"><span data-stu-id="90135-115">The read-only property that gets the currently visible Windows PowerShell ISE add-on tool that is located in the horizontal tool pane at the bottom of the editor.</span></span>

### <a name="currentvisibleverticaltool"></a><span data-ttu-id="90135-116">CurrentVisibleVerticalTool</span><span class="sxs-lookup"><span data-stu-id="90135-116">CurrentVisibleVerticalTool</span></span>

> <span data-ttu-id="90135-117">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="90135-117">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="90135-118">Skrivskyddad egenskap som hämtar synliga tilläggsverktyg för Windows PowerShell ISE som finns i verktygsfönstret lodräta på höger sida av redigeraren.</span><span class="sxs-lookup"><span data-stu-id="90135-118">The read-only property that gets the currently visible Windows PowerShell ISE add-on tool that is located in the vertical tool pane on the right side of the editor.</span></span>

### <a name="options"></a><span data-ttu-id="90135-119">Options</span><span class="sxs-lookup"><span data-stu-id="90135-119">Options</span></span>

> <span data-ttu-id="90135-120">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="90135-120">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="90135-121">Skrivskyddad egenskap som hämtar de olika alternativ som kan ändra inställningar i Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="90135-121">The read-only property that gets the various options that can change settings in Windows PowerShell ISE.</span></span>

### <a name="powershelltabs"></a><span data-ttu-id="90135-122">PowerShellTabs</span><span class="sxs-lookup"><span data-stu-id="90135-122">PowerShellTabs</span></span>

> <span data-ttu-id="90135-123">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="90135-123">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="90135-124">Den skrivskyddade egenskapen som hämtar insamling av PowerShell-flikar som är öppna i Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="90135-124">The read-only property that gets the collection of the PowerShell tabs, which are open in Windows PowerShell ISE.</span></span> <span data-ttu-id="90135-125">Det här objektet innehåller som standard en PowerShell-flik. Men du kan lägga till fler PowerShell flikar objektet med hjälp av skript eller genom att använda menyerna i Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="90135-125">By default, this object contains one PowerShell tab. However, you can add more PowerShell tabs to this object by using scripts or by using the menus in Windows PowerShell ISE.</span></span>

## <a name="see-also"></a><span data-ttu-id="90135-126">Se även</span><span class="sxs-lookup"><span data-stu-id="90135-126">See Also</span></span>

- [<span data-ttu-id="90135-127">Syftet med Windows PowerShell ISE Scripting Object Model</span><span class="sxs-lookup"><span data-stu-id="90135-127">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="90135-128">Hierarki för ISE-objektmodellen</span><span class="sxs-lookup"><span data-stu-id="90135-128">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)