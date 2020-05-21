---
title: Offentligt resurs schema | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e67298ee-a773-4402-8afb-d97ad0e030e5
caps.latest.revision: 4
ms.openlocfilehash: 52244ee7496b99e11f0306e93728736fc9c51be5
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83564711"
---
# <a name="public-resource-schema"></a><span data-ttu-id="23511-102">Schema för offentliga resurser</span><span class="sxs-lookup"><span data-stu-id="23511-102">Public Resource Schema</span></span>

<span data-ttu-id="23511-103">Hantering av OData använder MOF för att definiera resurser och deras egenskaper.</span><span class="sxs-lookup"><span data-stu-id="23511-103">Management OData uses MOF to define resources and their properties.</span></span> <span data-ttu-id="23511-104">Egenskaperna för en OData-enhet för hantering motsvarar direkt till egenskaperna för den hanterade typ som returneras av den underliggande cmdleten.</span><span class="sxs-lookup"><span data-stu-id="23511-104">The properties of a Management OData entity correspond directly to the properties of the managed type returned by the underlying cmdlet.</span></span>

## <a name="defining-a-resource"></a><span data-ttu-id="23511-105">Definiera en resurs</span><span class="sxs-lookup"><span data-stu-id="23511-105">Defining a resource</span></span>

<span data-ttu-id="23511-106">Varje resurs motsvarar ett objekt som returneras av en Windows PowerShell-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="23511-106">Each resource corresponds to an object returned by a Windows PowerShell cmdlet.</span></span> <span data-ttu-id="23511-107">I MOF-filen för offentlig resurs definierar du en resurs genom att deklarera en klass.</span><span class="sxs-lookup"><span data-stu-id="23511-107">In the public resource MOF file, you define a resource by declaring a class.</span></span> <span data-ttu-id="23511-108">Klassen består av egenskaper som motsvarar egenskaperna för objektet.</span><span class="sxs-lookup"><span data-stu-id="23511-108">The class consists of properties that correspond to the properties of the object.</span></span> <span data-ttu-id="23511-109">I följande exempel representeras klassen [system. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) av följande MOF.</span><span class="sxs-lookup"><span data-stu-id="23511-109">For example, in the following example, the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) class is represented by the following MOF.</span></span>

```csharp
class PswsTest_Process
{
    [Key] SInt32 Id;
    [Required] SInt32 BasePriority;
    [Required] SInt32 HandleCount;
    [Required] string MachineName;
    [Required] SInt32 MainWindowHandle;

    ...
};
```

<span data-ttu-id="23511-110">Varje egenskaps namn föregås av en datatyp.</span><span class="sxs-lookup"><span data-stu-id="23511-110">Each property name is preceded by a data type.</span></span> <span data-ttu-id="23511-111">Data typerna i det här exemplet motsvarar primitiva CLR-datatyper i .NET Framework, men egenskaper kan också vara referenser till andra resurser eller komplexa typer, vilka beskrivs senare.</span><span class="sxs-lookup"><span data-stu-id="23511-111">The data types in this example correspond to primitive CLR data types in the .NET Frameworks, but properties can also be references to other resources or complex types, which are both described later.</span></span>

<span data-ttu-id="23511-112">`Key`Kvalificeraren anger att en egenskap används för att unikt identifiera en resurs instans.</span><span class="sxs-lookup"><span data-stu-id="23511-112">The `Key` qualifier indicates that a property is used to uniquely identify a resource instance.</span></span> <span data-ttu-id="23511-113">En resurs kan ha mer än en nyckel.</span><span class="sxs-lookup"><span data-stu-id="23511-113">A resource can have more than one key.</span></span>

<span data-ttu-id="23511-114">`Required`Kvalificeraren anger att egenskapen är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="23511-114">The `Required` qualifier indicates that the property is required.</span></span> <span data-ttu-id="23511-115">Om en egenskap är märkt med `Key` kvalificeraren anses den vara obligatorisk och `Required` kvalificeraren är inte nödvändig.</span><span class="sxs-lookup"><span data-stu-id="23511-115">If a property is labeled with the `Key` qualifier, it is considered to be required, and the `Required` qualifier is not necessary.</span></span>

### <a name="complex-data-types"></a><span data-ttu-id="23511-116">Komplexa data typer</span><span class="sxs-lookup"><span data-stu-id="23511-116">Complex data types</span></span>

<span data-ttu-id="23511-117">Egenskaper för entiteter kan ha komplexa data typer.</span><span class="sxs-lookup"><span data-stu-id="23511-117">Properties of entities can have complex data types.</span></span> <span data-ttu-id="23511-118">Komplexa data typer är typer som består av andra typer, ungefär som structs i programmeringsspråket C.</span><span class="sxs-lookup"><span data-stu-id="23511-118">Complex data types are types that are made up of other types, similar to structs in the C programming language.</span></span> <span data-ttu-id="23511-119">En komplex typ deklareras i MOF-filen som en klass med `ComplexType` kvalificeraren, som i följande exempel.</span><span class="sxs-lookup"><span data-stu-id="23511-119">A complex type is declared in the MOF file as a class with the `ComplexType` qualifier, as in the following example.</span></span>

```csharp
[ComplexType]
class PswsTest_ProcessModule
{
    String ModuleName;
    String FileName;
};
```

<span data-ttu-id="23511-120">Om du vill deklarera en entitets egenskap som en komplex typ deklarerar du den som en `string` typ med `EmbeddedInstance` kvalificeraren, inklusive namnet på den komplexa typen.</span><span class="sxs-lookup"><span data-stu-id="23511-120">To declare an entity property as a complex type, you declare it as a `string` type with the `EmbeddedInstance` qualifier, including the name of the complex type.</span></span> <span data-ttu-id="23511-121">I följande exempel visas en deklaration av en egenskap av den `PswsTest_ProcessModule` typ som har deklarerats i föregående exempel.</span><span class="sxs-lookup"><span data-stu-id="23511-121">The following example shows the declaration of a property of the `PswsTest_ProcessModule` type declared in the previous example.</span></span>

```csharp
[Required, EmbeddedInstance("PswsTest_ProcessModule")] String Modules[];
```

### <a name="associating-entities"></a><span data-ttu-id="23511-122">Kopplar entiteter</span><span class="sxs-lookup"><span data-stu-id="23511-122">Associating entities</span></span>

<span data-ttu-id="23511-123">Du kan associera två entiteter med associerings-och AssociationClass-kvalificerarna.</span><span class="sxs-lookup"><span data-stu-id="23511-123">You can associate two entities by using the Association and AssociationClass qualifiers.</span></span> <span data-ttu-id="23511-124">Mer information finns i [associera hantering OData-entiteter](./associating-management-odata-entities.md).</span><span class="sxs-lookup"><span data-stu-id="23511-124">For more information, see [Associating Management OData Entities](./associating-management-odata-entities.md).</span></span>

### <a name="derived-types"></a><span data-ttu-id="23511-125">Härledda typer</span><span class="sxs-lookup"><span data-stu-id="23511-125">Derived types</span></span>

<span data-ttu-id="23511-126">Du kan härleda en typ från en annan typ.</span><span class="sxs-lookup"><span data-stu-id="23511-126">You can derive a type from another type.</span></span> <span data-ttu-id="23511-127">Den härledda typen ärver alla egenskaper av den typ som den är härledd från, utöver de egenskaper som uttryckligen härleds.</span><span class="sxs-lookup"><span data-stu-id="23511-127">The derived type inherits all of the properties of the type from which it derives in addition to any properties explicitly derived.</span></span> <span data-ttu-id="23511-128">I följande exempel visas en typ deklaration och en deklaration av två typer som härletts från den typen.</span><span class="sxs-lookup"><span data-stu-id="23511-128">The following example shows a type declaration and then a declaration of two types derived from that type.</span></span>

```csharp
Class Product {

    [Key] String ProductName;

};

Class DairyProduct : Product {

    Uint16 PercentFat;
};
Class POPProduct : Product {

    Boolean IsCarbonated;
};
```
