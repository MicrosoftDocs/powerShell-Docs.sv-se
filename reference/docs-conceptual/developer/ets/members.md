---
ms.date: 07/09/2020
ms.topic: reference
title: Medlemmar i utökad typ system klass
description: Medlemmar i utökad typ system klass
ms.openlocfilehash: 06488ce423f363a285ab53b21ab45989654346dc
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666849"
---
# <a name="extended-type-system-class-members"></a><span data-ttu-id="1a1b7-103">Medlemmar i utökad typ system klass</span><span class="sxs-lookup"><span data-stu-id="1a1b7-103">Extended Type System class members</span></span>

<span data-ttu-id="1a1b7-104">ETS refererar till ett antal olika typer av medlemmar vars typer definieras av **PSMemberTypes** -uppräkningen.</span><span class="sxs-lookup"><span data-stu-id="1a1b7-104">ETS refers to a number of different kinds of members whose types are defined by the **PSMemberTypes** enumeration.</span></span> <span data-ttu-id="1a1b7-105">Dessa medlems typer innehåller egenskaper, metoder, medlemmar och medlems uppsättningar som definieras av deras egna CLR-typ.</span><span class="sxs-lookup"><span data-stu-id="1a1b7-105">These member types include properties, methods, members, and member sets that are each defined by their own CLR type.</span></span> <span data-ttu-id="1a1b7-106">En **NoteProperty** definieras till exempel av en egen **PSNoteProperty** -typ.</span><span class="sxs-lookup"><span data-stu-id="1a1b7-106">For example, a **NoteProperty** is defined by its own **PSNoteProperty** type.</span></span> <span data-ttu-id="1a1b7-107">Dessa enskilda CLR-typer har både egna unika egenskaper och gemensamma egenskaper som ärvs från PSMemberInfo- [klassen](/dotnet/api/system.management.automation.psmemberinfo).</span><span class="sxs-lookup"><span data-stu-id="1a1b7-107">These individual CLR types have both their own unique properties and common properties that are inherited from the [PSMemberInfo class](/dotnet/api/system.management.automation.psmemberinfo).</span></span>

## <a name="the-psmemberinfo-class"></a><span data-ttu-id="1a1b7-108">PSMemberInfo-klassen</span><span class="sxs-lookup"><span data-stu-id="1a1b7-108">The PSMemberInfo class</span></span>

<span data-ttu-id="1a1b7-109">**PSMemberInfo** -klassen fungerar som en basklass för alla typer av ETS-medlemmar.</span><span class="sxs-lookup"><span data-stu-id="1a1b7-109">The **PSMemberInfo** class serves as a base class for all ETS member types.</span></span> <span data-ttu-id="1a1b7-110">Den här klassen ger följande grundläggande egenskaper till alla medlems CLR-typer.</span><span class="sxs-lookup"><span data-stu-id="1a1b7-110">This class provides the following base properties to all member CLR types.</span></span>

- <span data-ttu-id="1a1b7-111">**Namn** egenskap: medlemmens namn.</span><span class="sxs-lookup"><span data-stu-id="1a1b7-111">**Name** property: The name of the member.</span></span> <span data-ttu-id="1a1b7-112">Det här namnet kan definieras av Bask-objektet eller definieras av PowerShell när anpassade medlemmar eller utökade medlemmar exponeras.</span><span class="sxs-lookup"><span data-stu-id="1a1b7-112">This name can be defined by the base-object or defined by PowerShell when adapted members or extended members are exposed.</span></span>
- <span data-ttu-id="1a1b7-113">**Value** -egenskap: det värde som returneras från en viss medlem.</span><span class="sxs-lookup"><span data-stu-id="1a1b7-113">**Value** property: The value returned from the particular member.</span></span> <span data-ttu-id="1a1b7-114">Varje medlems typ definierar hur den hanterar sitt medlems värde.</span><span class="sxs-lookup"><span data-stu-id="1a1b7-114">Each member type defines how it handles its member value.</span></span>
- <span data-ttu-id="1a1b7-115">**TypeNameOfValue** -egenskap: Detta är namnet på CLR-typen för det värde som returneras av value-egenskapen.</span><span class="sxs-lookup"><span data-stu-id="1a1b7-115">**TypeNameOfValue** property: This is the name of the CLR type of the value that is returned by the Value property.</span></span>

## <a name="accessing-members"></a><span data-ttu-id="1a1b7-116">Åtkomst till medlemmar</span><span class="sxs-lookup"><span data-stu-id="1a1b7-116">Accessing members</span></span>

<span data-ttu-id="1a1b7-117">Samlingar med medlemmar kan nås via egenskaperna **members**, **Method** och **Properties** för **PSObject** -objektet.</span><span class="sxs-lookup"><span data-stu-id="1a1b7-117">Collections of members can be accessed through the **Members**, **Methods**, and **Properties** properties of the **PSObject** object.</span></span>

## <a name="ets-properties"></a><span data-ttu-id="1a1b7-118">ETS-egenskaper</span><span class="sxs-lookup"><span data-stu-id="1a1b7-118">ETS properties</span></span>

<span data-ttu-id="1a1b7-119">ETS-egenskaper är medlemmar som kan hanteras som en egenskap.</span><span class="sxs-lookup"><span data-stu-id="1a1b7-119">ETS properties are members that can be treated as a property.</span></span> <span data-ttu-id="1a1b7-120">De kan egentligen visas till vänster i ett uttryck.</span><span class="sxs-lookup"><span data-stu-id="1a1b7-120">Essentially, they can appear on the left-hand side of an expression.</span></span> <span data-ttu-id="1a1b7-121">De innehåller egenskaper för alias, kod egenskaper, PowerShell-egenskaper, antecknings egenskaper och skript egenskaper.</span><span class="sxs-lookup"><span data-stu-id="1a1b7-121">They include alias properties, code properties, PowerShell properties, note properties, and script properties.</span></span> <span data-ttu-id="1a1b7-122">Mer information om dessa typer av egenskaper finns i [ETS-egenskaper](properties.md).</span><span class="sxs-lookup"><span data-stu-id="1a1b7-122">For more information about these types of properties, see [ETS properties](properties.md).</span></span>

## <a name="ets-methods"></a><span data-ttu-id="1a1b7-123">ETS-metoder</span><span class="sxs-lookup"><span data-stu-id="1a1b7-123">ETS methods</span></span>

<span data-ttu-id="1a1b7-124">ETS-metoder är medlemmar som kan ta argument, kan returnera resultat och får inte visas till vänster i ett uttryck.</span><span class="sxs-lookup"><span data-stu-id="1a1b7-124">ETS methods are members that can take arguments, may return results, and cannot appear on the left-hand side of an expression.</span></span> <span data-ttu-id="1a1b7-125">De innehåller kod metoder, PowerShell-metoder och skript metoder.</span><span class="sxs-lookup"><span data-stu-id="1a1b7-125">They include code methods, PowerShell methods, and script methods.</span></span>
<span data-ttu-id="1a1b7-126">Mer information om dessa typer av metoder finns i [ETS-metoder](methods.md).</span><span class="sxs-lookup"><span data-stu-id="1a1b7-126">For more information about these types of methods, see [ETS methods](methods.md).</span></span>
