---
ms.date: 08/25/2017
keywords: PowerShell, cmdlet
title: ObjectModelRoot-objektet
ms.openlocfilehash: 0b04bdb3127edaac7b504556843efb64ee65ed13
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "75736036"
---
# <a name="the-objectmodelroot-object"></a><span data-ttu-id="63625-103">ObjectModelRoot-objektet</span><span class="sxs-lookup"><span data-stu-id="63625-103">The ObjectModelRoot Object</span></span>

<span data-ttu-id="63625-104">`$psISE` Objektet, som är huvud rotens objekt i Windows POWERSHELL® Ise (Integrated Scripting Environment) är en instans av klassen Microsoft. PowerShell. Host. ISE. ObjectModelRoot.</span><span class="sxs-lookup"><span data-stu-id="63625-104">The `$psISE` object, which is the principal root object in Windows PowerShell® Integrated Scripting Environment (ISE) is an instance of the Microsoft.PowerShell.Host.ISE.ObjectModelRoot class.</span></span> <span data-ttu-id="63625-105">I det här avsnittet beskrivs egenskaperna för **ObjectModelRoot** -objektet.</span><span class="sxs-lookup"><span data-stu-id="63625-105">This topic describes the properties of the **ObjectModelRoot** object.</span></span>

## <a name="properties"></a><span data-ttu-id="63625-106">Egenskaper</span><span class="sxs-lookup"><span data-stu-id="63625-106">Properties</span></span>

### <a name="currentfile"></a><span data-ttu-id="63625-107">CurrentFile</span><span class="sxs-lookup"><span data-stu-id="63625-107">CurrentFile</span></span>

> <span data-ttu-id="63625-108">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="63625-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="63625-109">Den skrivskyddade egenskapen som hämtar filen, som är associerad med det här värd objektet som för närvarande är i fokus.</span><span class="sxs-lookup"><span data-stu-id="63625-109">The read-only property that gets the file, which is associated with this host object that currently has the focus.</span></span>

### <a name="currentpowershelltab"></a><span data-ttu-id="63625-110">CurrentPowerShellTab</span><span class="sxs-lookup"><span data-stu-id="63625-110">CurrentPowerShellTab</span></span>

> <span data-ttu-id="63625-111">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="63625-111">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="63625-112">Den skrivskyddade egenskapen som hämtar PowerShell-fliken som har fokus.</span><span class="sxs-lookup"><span data-stu-id="63625-112">The read-only property that gets the PowerShell tab that has the focus.</span></span>

### <a name="currentvisiblehorizontaltool"></a><span data-ttu-id="63625-113">CurrentVisibleHorizontalTool</span><span class="sxs-lookup"><span data-stu-id="63625-113">CurrentVisibleHorizontalTool</span></span>

> <span data-ttu-id="63625-114">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="63625-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="63625-115">Den skrivskyddade egenskapen som hämtar det för närvarande synliga Windows PowerShell ISE tilläggs verktyget som finns i det vågräta verktygs fönstret längst ned i redigeraren.</span><span class="sxs-lookup"><span data-stu-id="63625-115">The read-only property that gets the currently visible Windows PowerShell ISE add-on tool that is located in the horizontal tool pane at the bottom of the editor.</span></span>

### <a name="currentvisibleverticaltool"></a><span data-ttu-id="63625-116">CurrentVisibleVerticalTool</span><span class="sxs-lookup"><span data-stu-id="63625-116">CurrentVisibleVerticalTool</span></span>

> <span data-ttu-id="63625-117">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="63625-117">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="63625-118">Den skrivskyddade egenskapen som hämtar det för närvarande synliga Windows PowerShell ISE tilläggs verktyget som finns i det lodräta verktygs fönstret till höger i redigeraren.</span><span class="sxs-lookup"><span data-stu-id="63625-118">The read-only property that gets the currently visible Windows PowerShell ISE add-on tool that is located in the vertical tool pane on the right side of the editor.</span></span>

### <a name="options"></a><span data-ttu-id="63625-119">Alternativ</span><span class="sxs-lookup"><span data-stu-id="63625-119">Options</span></span>

> <span data-ttu-id="63625-120">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="63625-120">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="63625-121">Den skrivskyddade egenskapen som hämtar de olika alternativen som kan ändra inställningarna i Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="63625-121">The read-only property that gets the various options that can change settings in Windows PowerShell ISE.</span></span>

### <a name="powershelltabs"></a><span data-ttu-id="63625-122">PowerShellTabs</span><span class="sxs-lookup"><span data-stu-id="63625-122">PowerShellTabs</span></span>

> <span data-ttu-id="63625-123">Stöds i Windows PowerShell ISE 2,0 och senare.</span><span class="sxs-lookup"><span data-stu-id="63625-123">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="63625-124">Den skrivskyddade egenskapen som hämtar insamlingen av PowerShell-flikar, som är öppna i Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="63625-124">The read-only property that gets the collection of the PowerShell tabs, which are open in Windows PowerShell ISE.</span></span> <span data-ttu-id="63625-125">Som standard innehåller det här objektet en PowerShell-flik. Du kan dock lägga till fler PowerShell-flikar i objektet med hjälp av skript eller genom att använda menyerna i Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="63625-125">By default, this object contains one PowerShell tab. However, you can add more PowerShell tabs to this object by using scripts or by using the menus in Windows PowerShell ISE.</span></span>

## <a name="see-also"></a><span data-ttu-id="63625-126">Se även</span><span class="sxs-lookup"><span data-stu-id="63625-126">See Also</span></span>

- [<span data-ttu-id="63625-127">Användningsområden för Windows PowerShell ISE-skriptobjektmodellen</span><span class="sxs-lookup"><span data-stu-id="63625-127">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="63625-128">Objekt modells-hierarkin för ISE</span><span class="sxs-lookup"><span data-stu-id="63625-128">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)