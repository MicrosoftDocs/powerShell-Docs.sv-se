---
title: Medlems uppsättningar för utökade typ system
ms.date: 07/09/2020
ms.openlocfilehash: 3f4e44ed7b498bb7c4a71f7b131270ed4f2ef981
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786262"
---
# <a name="ets-member-sets"></a><span data-ttu-id="12d50-102">ETS medlems uppsättningar</span><span class="sxs-lookup"><span data-stu-id="12d50-102">ETS member sets</span></span>

<span data-ttu-id="12d50-103">Med medlems uppsättningar kan du partitionera medlemmar av **PSObject** -objektet i två del mängder så att medlemmar i under uppsättningarna kan refereras till tillsammans med deras delmängds namn.</span><span class="sxs-lookup"><span data-stu-id="12d50-103">Member sets allow you to partition the members of the **PSObject** object into two subsets so that the members of the subsets can be referenced together by their subset name.</span></span> <span data-ttu-id="12d50-104">De två typerna av del mängder inkluderar egenskaps uppsättningar och medlems uppsättningar.</span><span class="sxs-lookup"><span data-stu-id="12d50-104">The two types of subsets include property sets and member sets.</span></span> <span data-ttu-id="12d50-105">Ett exempel på hur PowerShell använder medlems uppsättningar finns i en viss egenskaps uppsättning med namnet **DefaultDisplayPropertySet** som används för att fastställa, vid körning, vilka egenskaper som ska visas för ett angivet **PSObject** -objekt.</span><span class="sxs-lookup"><span data-stu-id="12d50-105">For example of how PowerShell uses member sets, there is a specific property set named **DefaultDisplayPropertySet** that is used to determine, at runtime, which properties to display for a given **PSObject** object.</span></span>

## <a name="property-sets"></a><span data-ttu-id="12d50-106">Egenskaps uppsättningar</span><span class="sxs-lookup"><span data-stu-id="12d50-106">Property Sets</span></span>

<span data-ttu-id="12d50-107">Egenskaps uppsättningar kan innehålla valfritt antal egenskaper för en **PSObject** -typ.</span><span class="sxs-lookup"><span data-stu-id="12d50-107">Property sets can include any number of properties of an **PSObject** type.</span></span> <span data-ttu-id="12d50-108">I allmänhet kan en egenskaps uppsättning användas när en samling egenskaper (av samma typ) behövs.</span><span class="sxs-lookup"><span data-stu-id="12d50-108">In general, a property set can be used whenever a collection of properties (of the same type) is needed.</span></span> <span data-ttu-id="12d50-109">Egenskaps uppsättningen skapas genom att anropa `PSPropertySet(System.String,System.Collections.Generic.IEnumerable{System.String})` konstruktorn med namnet på egenskaps uppsättningen och namnen på de refererade egenskaperna.</span><span class="sxs-lookup"><span data-stu-id="12d50-109">The property set is created by calling the `PSPropertySet(System.String,System.Collections.Generic.IEnumerable{System.String})` constructor with the name of the property set and the names of the referenced properties.</span></span> <span data-ttu-id="12d50-110">Det skapade **PSPropertySet** -objektet kan sedan användas som ett alias som pekar på egenskaperna i uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="12d50-110">The created **PSPropertySet** object can then be used as an alias that points to the properties in the set.</span></span> <span data-ttu-id="12d50-111">[PSPropertySet](/dotnet/api/system.management.automation.pspropertyset) -klassen har följande egenskaper och metoder.</span><span class="sxs-lookup"><span data-stu-id="12d50-111">The [PSPropertySet](/dotnet/api/system.management.automation.pspropertyset) class has the following properties and methods.</span></span>

- <span data-ttu-id="12d50-112">**IsInstance** -egenskap: hämtar ett **booleskt** värde som anger egenskapens källa.</span><span class="sxs-lookup"><span data-stu-id="12d50-112">**IsInstance** property: Gets a **Boolean** value that indicates the source of the property.</span></span>
- <span data-ttu-id="12d50-113">**MemberType** -egenskap: hämtar typ av egenskaper i egenskaps uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="12d50-113">**MemberType** property: Gets the type of properties in the property set.</span></span>
- <span data-ttu-id="12d50-114">**Namn** egenskap: hämtar namnet på egenskaps uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="12d50-114">**Name** property: Gets the name of the property set.</span></span>
- <span data-ttu-id="12d50-115">**ReferencedPropertyNames** -egenskap: hämtar namnen på egenskaperna i egenskaps uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="12d50-115">**ReferencedPropertyNames** property: Gets the names of the properties in the property set.</span></span>
- <span data-ttu-id="12d50-116">**TypeNameOfValue** -egenskap: hämtar en **PropertySet** Enumeration-konstant som definierar den här uppsättningen som en egenskaps uppsättning.</span><span class="sxs-lookup"><span data-stu-id="12d50-116">**TypeNameOfValue** property: Gets a **PropertySet** enumeration constant that defines this set as a property set.</span></span>
- <span data-ttu-id="12d50-117">**Value** -egenskap: hämtar eller anger **PSPropertySet** -objektet.</span><span class="sxs-lookup"><span data-stu-id="12d50-117">**Value** property: Gets or sets the **PSPropertySet** object.</span></span>
- <span data-ttu-id="12d50-118">`PSPropertySet.Copy` metod: gör en exakt kopia av **PSPropertySet** -objektet.</span><span class="sxs-lookup"><span data-stu-id="12d50-118">`PSPropertySet.Copy` method: Makes an exact copy of the **PSPropertySet** object.</span></span>
- <span data-ttu-id="12d50-119">`PSMemberSet.ToString` metod: konverterar **PSPropertySet** -objektet till en sträng.</span><span class="sxs-lookup"><span data-stu-id="12d50-119">`PSMemberSet.ToString` method: Converts the **PSPropertySet** object to a string.</span></span>

## <a name="member-sets"></a><span data-ttu-id="12d50-120">Medlems uppsättningar</span><span class="sxs-lookup"><span data-stu-id="12d50-120">Member Sets</span></span>

<span data-ttu-id="12d50-121">Medlems uppsättningar kan innehålla valfritt antal utökade medlemmar av vilken typ som helst.</span><span class="sxs-lookup"><span data-stu-id="12d50-121">Member sets can include any number of extended members of any type.</span></span> <span data-ttu-id="12d50-122">Medlems uppsättningen skapas genom att anropar `PSMemberSet(System.String,System.Collections.Generic.IEnumerable{System.Management.Automation.PSMemberInfo})`</span><span class="sxs-lookup"><span data-stu-id="12d50-122">The member set is created by calling the `PSMemberSet(System.String,System.Collections.Generic.IEnumerable{System.Management.Automation.PSMemberInfo})`</span></span>
<span data-ttu-id="12d50-123">konstruktor med namnet på medlems uppsättningen och namnen på de medlemmar som refereras till.</span><span class="sxs-lookup"><span data-stu-id="12d50-123">constructor with the name of the member set and the names of the referenced members.</span></span> <span data-ttu-id="12d50-124">Det skapade **PSPropertySet** -objektet kan sedan användas som ett alias som pekar på medlemmarna i uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="12d50-124">The created **PSPropertySet** object can then be used as an alias that points to the members in the set.</span></span> <span data-ttu-id="12d50-125">[PSMemberSet](/dotnet/api/system.management.automation.psmemberset) -klassen har följande egenskaper och metoder.</span><span class="sxs-lookup"><span data-stu-id="12d50-125">The [PSMemberSet](/dotnet/api/system.management.automation.psmemberset) class has the following properties and methods.</span></span>

- <span data-ttu-id="12d50-126">**IsInstance** -egenskap: hämtar ett **booleskt** värde som anger medlemmens källa.</span><span class="sxs-lookup"><span data-stu-id="12d50-126">**IsInstance** property: Gets a **Boolean** value that indicates the source of the member.</span></span>
- <span data-ttu-id="12d50-127">**Medlems egenskap:** hämtar alla medlemmar i medlems uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="12d50-127">**Members** property: Gets all the members of the member set.</span></span>
- <span data-ttu-id="12d50-128">**MemberType** -egenskap: hämtar en **MemberSet** -uppräknings konstant som definierar den här uppsättningen som en medlems uppsättning.</span><span class="sxs-lookup"><span data-stu-id="12d50-128">**MemberType** property: Gets a **MemberSet** enumeration constant that defines this set as a member set.</span></span>
- <span data-ttu-id="12d50-129">Egenskapen **metoder** : hämtar de metoder som ingår i medlems uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="12d50-129">**Methods** property: Gets the methods included in the member set.</span></span>
- <span data-ttu-id="12d50-130">**Egenskaps egenskap:** hämtar egenskaperna som ingår i medlems uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="12d50-130">**Properties** property: Gets the properties included in the member set.</span></span>
- <span data-ttu-id="12d50-131">**TypeNameOfValue** -egenskap: hämtar en **MemberSet** -uppräknings konstant som definierar den här uppsättningen som en medlems uppsättning.</span><span class="sxs-lookup"><span data-stu-id="12d50-131">**TypeNameOfValue** property: Gets a **MemberSet** enumeration constant that defines this set as a member set.</span></span>
- <span data-ttu-id="12d50-132">**Värde** egenskap: hämtar **PSMemberSet** -objektet.</span><span class="sxs-lookup"><span data-stu-id="12d50-132">**Value** property: Gets the **PSMemberSet** object.</span></span>
- <span data-ttu-id="12d50-133">`PSMemberSet.Copy` metod: gör en exakt kopia av **PSMemberSet** -objektet.</span><span class="sxs-lookup"><span data-stu-id="12d50-133">`PSMemberSet.Copy` method: Makes an exact copy of the **PSMemberSet** object.</span></span>
- <span data-ttu-id="12d50-134">`PSMemberSet.ToString` metod: konverterar **PSMemberSet** -objektet till en sträng.</span><span class="sxs-lookup"><span data-stu-id="12d50-134">`PSMemberSet.ToString` method: Converts the **PSMemberSet** object to a string.</span></span>