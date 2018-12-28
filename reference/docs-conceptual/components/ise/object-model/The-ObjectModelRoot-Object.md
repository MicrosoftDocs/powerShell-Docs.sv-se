---
ms.date: 08/25/2017
keywords: PowerShell cmdlet
title: ObjectModelRoot-objektet
ms.openlocfilehash: 2670321ebac1eac4ecc8457afb796f9f260da471
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53406033"
---
# <a name="the-objectmodelroot-object"></a><span data-ttu-id="b9559-103">ObjectModelRoot-objektet</span><span class="sxs-lookup"><span data-stu-id="b9559-103">The ObjectModelRoot Object</span></span>

<span data-ttu-id="b9559-104">Den **$psISE** -objektet, vilket är huvudnamn rotobjektet i Windows PowerShell® Integrated Scripting Environment (ISE) är en instans av klassen Microsoft.PowerShell.Host.ISE.ObjectModelRoot.</span><span class="sxs-lookup"><span data-stu-id="b9559-104">The **$psISE** object, which is the principal root object in Windows PowerShell® Integrated Scripting Environment (ISE) is an instance of the Microsoft.PowerShell.Host.ISE.ObjectModelRoot class.</span></span>
<span data-ttu-id="b9559-105">Det här avsnittet beskriver egenskaperna för den **ObjectModelRoot** objekt.</span><span class="sxs-lookup"><span data-stu-id="b9559-105">This topic describes the properties of the **ObjectModelRoot** object.</span></span>

## <a name="properties"></a><span data-ttu-id="b9559-106">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="b9559-106">Properties</span></span>

### <a name="currentfile"></a><span data-ttu-id="b9559-107">CurrentFile</span><span class="sxs-lookup"><span data-stu-id="b9559-107">CurrentFile</span></span>

> <span data-ttu-id="b9559-108">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="b9559-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="b9559-109">Den skrivskyddade egenskapen som hämtar filen, som är associerad med den här värdobjekt som för närvarande har fokus.</span><span class="sxs-lookup"><span data-stu-id="b9559-109">The read-only property that gets the file, which is associated with this host object that currently has the focus.</span></span>

### <a name="currentpowershelltab"></a><span data-ttu-id="b9559-110">CurrentPowerShellTab</span><span class="sxs-lookup"><span data-stu-id="b9559-110">CurrentPowerShellTab</span></span>

> <span data-ttu-id="b9559-111">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="b9559-111">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="b9559-112">Den skrivskyddade egenskapen som hämtar fliken PowerShell som är markerat.</span><span class="sxs-lookup"><span data-stu-id="b9559-112">The read-only property that gets the PowerShell tab that has the focus.</span></span>

### <a name="currentvisiblehorizontaltool"></a><span data-ttu-id="b9559-113">CurrentVisibleHorizontalTool</span><span class="sxs-lookup"><span data-stu-id="b9559-113">CurrentVisibleHorizontalTool</span></span>

> <span data-ttu-id="b9559-114">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="b9559-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="b9559-115">Skrivskyddad egenskap som hämtar synliga Windows PowerShell ISE-tilläggsverktyg som finns i verktygsfönstret vågrät längst ned i redigeraren.</span><span class="sxs-lookup"><span data-stu-id="b9559-115">The read-only property that gets the currently visible Windows PowerShell ISE add-on tool that is located in the horizontal tool pane at the bottom of the editor.</span></span>

### <a name="currentvisibleverticaltool"></a><span data-ttu-id="b9559-116">CurrentVisibleVerticalTool</span><span class="sxs-lookup"><span data-stu-id="b9559-116">CurrentVisibleVerticalTool</span></span>

> <span data-ttu-id="b9559-117">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="b9559-117">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="b9559-118">Skrivskyddad egenskap som hämtar synliga Windows PowerShell ISE-tilläggsverktyg som finns i den lodräta verktygsfönstret på höger sida av redigeraren.</span><span class="sxs-lookup"><span data-stu-id="b9559-118">The read-only property that gets the currently visible Windows PowerShell ISE add-on tool that is located in the vertical tool pane on the right side of the editor.</span></span>

### <a name="options"></a><span data-ttu-id="b9559-119">Options</span><span class="sxs-lookup"><span data-stu-id="b9559-119">Options</span></span>

> <span data-ttu-id="b9559-120">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="b9559-120">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="b9559-121">Skrivskyddad egenskap som hämtar de olika alternativen som kan ändra inställningarna i Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="b9559-121">The read-only property that gets the various options that can change settings in Windows PowerShell ISE.</span></span>

### <a name="powershelltabs"></a><span data-ttu-id="b9559-122">PowerShellTabs</span><span class="sxs-lookup"><span data-stu-id="b9559-122">PowerShellTabs</span></span>

> <span data-ttu-id="b9559-123">Stöds i Windows PowerShell ISE 2.0 och senare.</span><span class="sxs-lookup"><span data-stu-id="b9559-123">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="b9559-124">Den skrivskyddade egenskapen som hämtar uppsättning PowerShell-flikar som är öppna i Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="b9559-124">The read-only property that gets the collection of the PowerShell tabs, which are open in Windows PowerShell ISE.</span></span> <span data-ttu-id="b9559-125">Det här objektet innehåller som standard en PowerShell-flik. Men du kan lägga till fler PowerShell flikar det här objektet med hjälp av skript eller genom att använda menyerna i Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="b9559-125">By default, this object contains one PowerShell tab. However, you can add more PowerShell tabs to this object by using scripts or by using the menus in Windows PowerShell ISE.</span></span>

## <a name="see-also"></a><span data-ttu-id="b9559-126">Se även</span><span class="sxs-lookup"><span data-stu-id="b9559-126">See Also</span></span>

- [<span data-ttu-id="b9559-127">Syftet med den Windows PowerShell ISE-Skriptobjektmodellen</span><span class="sxs-lookup"><span data-stu-id="b9559-127">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="b9559-128">Hierarki för ISE-objektmodellen</span><span class="sxs-lookup"><span data-stu-id="b9559-128">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)