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
ms.openlocfilehash: c7e20ff0f36e8cab2d414ff2e5924b3359ad9c60
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72356814"
---
# <a name="public-resource-schema"></a><span data-ttu-id="96a92-102">Schema för offentliga resurser</span><span class="sxs-lookup"><span data-stu-id="96a92-102">Public Resource Schema</span></span>

<span data-ttu-id="96a92-103">Hantering av OData använder MOF för att definiera resurser och deras egenskaper.</span><span class="sxs-lookup"><span data-stu-id="96a92-103">Management OData uses MOF to define resources and their properties.</span></span> <span data-ttu-id="96a92-104">Egenskaperna för en OData-enhet för hantering motsvarar direkt till egenskaperna för den hanterade typ som returneras av den underliggande cmdleten.</span><span class="sxs-lookup"><span data-stu-id="96a92-104">The properties of a Management OData entity correspond directly to the properties of the managed type returned by the underlying cmdlet.</span></span>

## <a name="defining-a-resource"></a><span data-ttu-id="96a92-105">Definiera en resurs</span><span class="sxs-lookup"><span data-stu-id="96a92-105">Defining a resource</span></span>

<span data-ttu-id="96a92-106">Varje resurs motsvarar ett objekt som returneras av en Windows PowerShell-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="96a92-106">Each resource corresponds to an object returned by a Windows PowerShell cmdlet.</span></span> <span data-ttu-id="96a92-107">I MOF-filen för offentlig resurs definierar du en resurs genom att deklarera en klass.</span><span class="sxs-lookup"><span data-stu-id="96a92-107">In the public resource MOF file, you define a resource by declaring a class.</span></span> <span data-ttu-id="96a92-108">Klassen består av egenskaper som motsvarar egenskaperna för objektet.</span><span class="sxs-lookup"><span data-stu-id="96a92-108">The class consists of properties that correspond to the properties of the object.</span></span> <span data-ttu-id="96a92-109">I följande exempel representeras klassen [system. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) av följande MOF.</span><span class="sxs-lookup"><span data-stu-id="96a92-109">For example, in the following example, the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) class is represented by the following MOF.</span></span>

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

<span data-ttu-id="96a92-110">Varje egenskaps namn föregås av en datatyp.</span><span class="sxs-lookup"><span data-stu-id="96a92-110">Each property name is preceded by a data type.</span></span> <span data-ttu-id="96a92-111">Data typerna i det här exemplet motsvarar primitiva CLR-datatyper i .NET Framework, men egenskaper kan också vara referenser till andra resurser eller komplexa typer, vilka beskrivs senare.</span><span class="sxs-lookup"><span data-stu-id="96a92-111">The data types in this example correspond to primitive CLR data types in the .NET Frameworks, but properties can also be references to other resources or complex types, which are both described later.</span></span>

<span data-ttu-id="96a92-112">Kvalificeraren `Key` anger att en egenskap används för att unikt identifiera en resurs instans.</span><span class="sxs-lookup"><span data-stu-id="96a92-112">The `Key` qualifier indicates that a property is used to uniquely identify a resource instance.</span></span> <span data-ttu-id="96a92-113">En resurs kan ha mer än en nyckel.</span><span class="sxs-lookup"><span data-stu-id="96a92-113">A resource can have more than one key.</span></span>

<span data-ttu-id="96a92-114">Kvalificeraren `Required` anger att egenskapen är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="96a92-114">The `Required` qualifier indicates that the property is required.</span></span> <span data-ttu-id="96a92-115">Om en egenskap är märkt med kvalificeraren `Key`, anses den vara obligatorisk och kvalificeraren `Required` är inte nödvändig.</span><span class="sxs-lookup"><span data-stu-id="96a92-115">If a property is labeled with the `Key` qualifier, it is considered to be required, and the `Required` qualifier is not necessary.</span></span>

### <a name="complex-data-types"></a><span data-ttu-id="96a92-116">Komplexa data typer</span><span class="sxs-lookup"><span data-stu-id="96a92-116">Complex data types</span></span>

<span data-ttu-id="96a92-117">Egenskaper för entiteter kan ha komplexa data typer.</span><span class="sxs-lookup"><span data-stu-id="96a92-117">Properties of entities can have complex data types.</span></span> <span data-ttu-id="96a92-118">Komplexa data typer är typer som består av andra typer, ungefär som structs i programmeringsspråket C.</span><span class="sxs-lookup"><span data-stu-id="96a92-118">Complex data types are types that are made up of other types, similar to structs in the C programming language.</span></span> <span data-ttu-id="96a92-119">En komplex typ deklareras i MOF-filen som en klass med kvalificeraren `ComplexType`, som i följande exempel.</span><span class="sxs-lookup"><span data-stu-id="96a92-119">A complex type is declared in the MOF file as a class with the `ComplexType` qualifier, as in the following example.</span></span>

```csharp
[ComplexType]
class PswsTest_ProcessModule
{
    String ModuleName;
    String FileName;
};
```

<span data-ttu-id="96a92-120">Om du vill deklarera en entitets egenskap som en komplex typ deklarerar du den som en `string`-typ med kvalificeraren `EmbeddedInstance`, inklusive namnet på den komplexa typen.</span><span class="sxs-lookup"><span data-stu-id="96a92-120">To declare an entity property as a complex type, you declare it as a `string` type with the `EmbeddedInstance` qualifier, including the name of the complex type.</span></span> <span data-ttu-id="96a92-121">I följande exempel visas en förklaring av en egenskap för den `PswsTest_ProcessModule`-typ som har deklarerats i föregående exempel.</span><span class="sxs-lookup"><span data-stu-id="96a92-121">The following example shows the declaration of a property of the `PswsTest_ProcessModule` type declared in the previous example.</span></span>

```csharp
[Required, EmbeddedInstance("PswsTest_ProcessModule")] String Modules[];
```

### <a name="associating-entities"></a><span data-ttu-id="96a92-122">Kopplar entiteter</span><span class="sxs-lookup"><span data-stu-id="96a92-122">Associating entities</span></span>

<span data-ttu-id="96a92-123">Du kan associera två entiteter med associerings-och AssociationClass-kvalificerarna.</span><span class="sxs-lookup"><span data-stu-id="96a92-123">You can associate two entities by using the Association and AssociationClass qualifiers.</span></span> <span data-ttu-id="96a92-124">Mer information finns i [associera hantering OData-entiteter](./associating-management-odata-entities.md).</span><span class="sxs-lookup"><span data-stu-id="96a92-124">For more information, see [Associating Management OData Entities](./associating-management-odata-entities.md).</span></span>

### <a name="derived-types"></a><span data-ttu-id="96a92-125">Härledda typer</span><span class="sxs-lookup"><span data-stu-id="96a92-125">Derived types</span></span>

<span data-ttu-id="96a92-126">Du kan härleda en typ från en annan typ.</span><span class="sxs-lookup"><span data-stu-id="96a92-126">You can derive a type from another type.</span></span> <span data-ttu-id="96a92-127">Den härledda typen ärver alla egenskaper av den typ som den är härledd från, utöver de egenskaper som uttryckligen härleds.</span><span class="sxs-lookup"><span data-stu-id="96a92-127">The derived type inherits all of the properties of the type from which it derives in addition to any properties explicitly derived.</span></span> <span data-ttu-id="96a92-128">I följande exempel visas en typ deklaration och en deklaration av två typer som härletts från den typen.</span><span class="sxs-lookup"><span data-stu-id="96a92-128">The following example shows a type declaration and then a declaration of two types derived from that type.</span></span>

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