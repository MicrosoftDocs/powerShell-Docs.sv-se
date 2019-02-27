---
title: Offentlig resursschemat | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e67298ee-a773-4402-8afb-d97ad0e030e5
caps.latest.revision: 4
ms.openlocfilehash: a9204ca7b28fc5792ef9bd18f6b0b24964de7386
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849296"
---
# <a name="public-resource-schema"></a><span data-ttu-id="fa62f-102">Schema för offentliga resurser</span><span class="sxs-lookup"><span data-stu-id="fa62f-102">Public Resource Schema</span></span>

<span data-ttu-id="fa62f-103">Management OData använder MOF för att definiera resurser och deras egenskaper.</span><span class="sxs-lookup"><span data-stu-id="fa62f-103">Management OData uses MOF to define resources and their properties.</span></span> <span data-ttu-id="fa62f-104">Egenskaperna för en Management OData-entitet motsvarar egenskaperna för hanterad typ som returnerats av cmdleten underliggande.</span><span class="sxs-lookup"><span data-stu-id="fa62f-104">The properties of a Management OData entity correspond directly to the properties of the managed type returned by the underlying cmdlet.</span></span>

## <a name="defining-a-resource"></a><span data-ttu-id="fa62f-105">Definiera en resurs</span><span class="sxs-lookup"><span data-stu-id="fa62f-105">Defining a resource</span></span>

<span data-ttu-id="fa62f-106">Varje resurs motsvarar ett objekt som returneras av en Windows PowerShell-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fa62f-106">Each resource corresponds to an object returned by a Windows PowerShell cmdlet.</span></span> <span data-ttu-id="fa62f-107">I publc resource MOF-filen definierar du en resurs genom att deklarera en klass.</span><span class="sxs-lookup"><span data-stu-id="fa62f-107">In the publc resource MOF file, you define a resource by declaring a class.</span></span> <span data-ttu-id="fa62f-108">Klassen består av egenskaper som motsvarar egenskaperna för objektet.</span><span class="sxs-lookup"><span data-stu-id="fa62f-108">The class consists of properties that correspond to the properties of the object.</span></span> <span data-ttu-id="fa62f-109">Till exempel i följande exempel visas den [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) klass representeras av följande MOF.</span><span class="sxs-lookup"><span data-stu-id="fa62f-109">For example, in the following example, the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) class is represented by the following MOF.</span></span>

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

<span data-ttu-id="fa62f-110">Varje egenskapsnamn föregås av en datatyp.</span><span class="sxs-lookup"><span data-stu-id="fa62f-110">Each property name is preceded by a data type.</span></span> <span data-ttu-id="fa62f-111">Datatyper i det här exemplet motsvarar primitiva CLR-datatyper i .NET Framework-program, men egenskaperna kan också vara referenser till andra resurser och komplexa typer som är både beskrivs senare.</span><span class="sxs-lookup"><span data-stu-id="fa62f-111">The data types in this example correspond to primitive CLR data types in the .NET Frameworks, but properties can also be references to other resources or complex types, which are both described later.</span></span>

<span data-ttu-id="fa62f-112">Den `Key` kvalificerare anger att en egenskap som unikt identifierar en resursinstans.</span><span class="sxs-lookup"><span data-stu-id="fa62f-112">The `Key` qualifier indicates that a property is used to uniquely identify a resource instance.</span></span> <span data-ttu-id="fa62f-113">En resurs kan ha fler än en nyckel.</span><span class="sxs-lookup"><span data-stu-id="fa62f-113">A resource can have more than one key.</span></span>

<span data-ttu-id="fa62f-114">Den `Required` kvalificerare anger att egenskapen är obligatoriskt.</span><span class="sxs-lookup"><span data-stu-id="fa62f-114">The `Required` qualifier indicates that the property is required.</span></span> <span data-ttu-id="fa62f-115">Om en egenskap är märkt med den `Key` kvalificerare, anses det krävs, och `Required` kvalificerare är inte nödvändigt.</span><span class="sxs-lookup"><span data-stu-id="fa62f-115">If a property is labeled with the `Key` qualifier, it is considered to be required, and the `Required` qualifier is not necessary.</span></span>

### <a name="complex-data-types"></a><span data-ttu-id="fa62f-116">Komplexa datatyper</span><span class="sxs-lookup"><span data-stu-id="fa62f-116">Complex data types</span></span>

<span data-ttu-id="fa62f-117">Egenskaper för entiteter kan ha komplexa datatyper.</span><span class="sxs-lookup"><span data-stu-id="fa62f-117">Properties of entities can have complex data types.</span></span> <span data-ttu-id="fa62f-118">Komplexa datatyper är typer som består av andra typer, liknar Struct-datatyperna i programmeringsspråket C.</span><span class="sxs-lookup"><span data-stu-id="fa62f-118">Complex data types are types that are made up of other types, similar to structs in the C programming language.</span></span> <span data-ttu-id="fa62f-119">En komplex typ har deklarerats i MOF-filen som en klass med den `ComplexType` kvalificerare som i följande exempel.</span><span class="sxs-lookup"><span data-stu-id="fa62f-119">A complex type is declared in the MOF file as a class with the `ComplexType` qualifier, as in the following example.</span></span>

```csharp
[ComplexType]
class PswsTest_ProcessModule
{
    String ModuleName;
    String FileName;
};
```

<span data-ttu-id="fa62f-120">För att deklarera en entitetsegenskap som en komplex typ, kan du ange den som en `string` typ med den `EmbeddedInstance` kvalificerare, inklusive namnet på den komplexa typen.</span><span class="sxs-lookup"><span data-stu-id="fa62f-120">To declare an entity property as a complex type, you declare it as a `string` type with the `EmbeddedInstance` qualifier, including the name of the complex type.</span></span> <span data-ttu-id="fa62f-121">I följande exempel hshows deklarationen för en egenskap för den `PswsTest_ProcessModule` typen deklarerade i föregående exempel.</span><span class="sxs-lookup"><span data-stu-id="fa62f-121">The following example hshows the declaration of a property of the `PswsTest_ProcessModule` type declared in the previous example.</span></span>

```csharp
[Required, EmbeddedInstance("PswsTest_ProcessModule")] String Modules[];
```

### <a name="associating-entities"></a><span data-ttu-id="fa62f-122">Associera entiteter</span><span class="sxs-lookup"><span data-stu-id="fa62f-122">Associating entities</span></span>

<span data-ttu-id="fa62f-123">Du kan associera två entiteter med hjälp av kopplingen och AssocationClass kvalificerare.</span><span class="sxs-lookup"><span data-stu-id="fa62f-123">You can associate two entities by using the Association and AssocationClass qualifiers.</span></span> <span data-ttu-id="fa62f-124">Mer information finns i [associera Management OData entiteter](./associating-management-odata-entities.md).</span><span class="sxs-lookup"><span data-stu-id="fa62f-124">For more information, see [Associating Management OData Entities](./associating-management-odata-entities.md).</span></span>

### <a name="derived-types"></a><span data-ttu-id="fa62f-125">Härledda typer</span><span class="sxs-lookup"><span data-stu-id="fa62f-125">Derived types</span></span>

<span data-ttu-id="fa62f-126">Du kan härleda en typ från en annan typ.</span><span class="sxs-lookup"><span data-stu-id="fa62f-126">You can derive a type from another type.</span></span> <span data-ttu-id="fa62f-127">Den härledda typen ärver alla egenskaper av typen från vilket det kommer utöver eventuella egenskaper som härleds uttryckligen.</span><span class="sxs-lookup"><span data-stu-id="fa62f-127">The derived type inherits all of the properties of the type from which it derives in addition to any properties explicitly derived.</span></span> <span data-ttu-id="fa62f-128">I följande exempel visas en typdeklaration och sedan en deklaration av två typer som härletts från den typen.</span><span class="sxs-lookup"><span data-stu-id="fa62f-128">The following example shows a type declaration and then a declaration of two types derived from that type.</span></span>

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