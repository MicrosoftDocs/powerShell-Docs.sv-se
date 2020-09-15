---
ms.date: 07/29/2020
title: Nya språk funktioner i PowerShell 5,0
ms.openlocfilehash: dada39c4121a810c7ce87a642f232934152104e5
ms.sourcegitcommit: 339e5fc8a4cc18b4ff6956fe5180343588e40e30
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/29/2020
ms.locfileid: "87410180"
---
# <a name="new-language-features-in-powershell-50"></a><span data-ttu-id="c6fe7-102">Nya språk funktioner i PowerShell 5,0</span><span class="sxs-lookup"><span data-stu-id="c6fe7-102">New language features in PowerShell 5.0</span></span>

<span data-ttu-id="c6fe7-103">PowerShell 5,0 har lagt till möjligheten att definiera klasser och andra användardefinierade typer med hjälp av formell syntax och semantiska objekt som andra objektorienterade programmeringsspråk.</span><span class="sxs-lookup"><span data-stu-id="c6fe7-103">PowerShell 5.0 added the ability to define classes and other user-defined types using formal syntax and semantics like other object-oriented programming languages.</span></span> <span data-ttu-id="c6fe7-104">Målet är att göra det möjligt för utvecklare och IT-proffs att använda PowerShell för ett bredare utbud av användnings fall, förenkla utvecklingen av PowerShell-artefakter (till exempel DSC-resurser) och påskynda täckning av hanterings ytor.</span><span class="sxs-lookup"><span data-stu-id="c6fe7-104">The goal is to enable developers and IT professionals to embrace PowerShell for a wider range of use cases, simplify development of PowerShell artifacts (such as DSC resources), and accelerate coverage of management surfaces.</span></span>

<span data-ttu-id="c6fe7-105">PowerShell 5,0 introducerar följande nya språk element i PowerShell:</span><span class="sxs-lookup"><span data-stu-id="c6fe7-105">PowerShell 5.0 introduces the following new language elements in PowerShell:</span></span>

### <a name="class-keyword"></a><span data-ttu-id="c6fe7-106">Klass nyckelord</span><span class="sxs-lookup"><span data-stu-id="c6fe7-106">Class keyword</span></span>

<span data-ttu-id="c6fe7-107">`class`Nyckelordet definierar en ny klass.</span><span class="sxs-lookup"><span data-stu-id="c6fe7-107">The `class` keyword defines a new class.</span></span> <span data-ttu-id="c6fe7-108">Detta är en True .NET Framework-typ.</span><span class="sxs-lookup"><span data-stu-id="c6fe7-108">This is a true .NET Framework type.</span></span> <span data-ttu-id="c6fe7-109">Klass medlemmar är offentliga, men endast offentliga inom modulens omfattning.</span><span class="sxs-lookup"><span data-stu-id="c6fe7-109">Class members are public, but only public within the module scope.</span></span> <span data-ttu-id="c6fe7-110">Det går inte att referera till typnamn som en sträng (till exempel `New-Object` fungerar inte) och i den här versionen kan du inte använda en typ literal (till exempel `[MyClass]` ) utanför skriptet eller modulens fil som klassen är definierad i.</span><span class="sxs-lookup"><span data-stu-id="c6fe7-110">You can't refer to the type name as a string (for example, `New-Object` doesn't work), and in this release, you can't use a type literal (for example, `[MyClass]`) outside the script or module file in which the class is defined.</span></span>

```powershell
class MyClass
{
    ...
}
```

### <a name="enum-keyword-and-enumerations"></a><span data-ttu-id="c6fe7-111">Räkna upp nyckelord och uppräkningar</span><span class="sxs-lookup"><span data-stu-id="c6fe7-111">Enum keyword and enumerations</span></span>

<span data-ttu-id="c6fe7-112">Stöd för `enum` nyckelordet har lagts till, vilket använder ny rad som avgränsare.</span><span class="sxs-lookup"><span data-stu-id="c6fe7-112">Support for the `enum` keyword has been added, which uses newline as the delimiter.</span></span> <span data-ttu-id="c6fe7-113">För närvarande kan du inte definiera en uppräknare i termer av sig själv.</span><span class="sxs-lookup"><span data-stu-id="c6fe7-113">Currently, you cannot define an enumerator in terms of itself.</span></span> <span data-ttu-id="c6fe7-114">Du kan dock initiera en uppräkning i termer av en annan uppräkning, som du ser i följande exempel.</span><span class="sxs-lookup"><span data-stu-id="c6fe7-114">However, you can initialize an enum in terms of another enum, as shown in the following example.</span></span> <span data-ttu-id="c6fe7-115">Bastypen kan inte heller anges. Det är alltid `[int]` .</span><span class="sxs-lookup"><span data-stu-id="c6fe7-115">Also, the base type cannot be specified; it is always `[int]`.</span></span>

```powershell
enum Color2
{
    Yellow = [Color]::Blue
}
```

<span data-ttu-id="c6fe7-116">Ett uppräknings värde måste vara en konstant för en parse.</span><span class="sxs-lookup"><span data-stu-id="c6fe7-116">An enumerator value must be a parse time constant.</span></span> <span data-ttu-id="c6fe7-117">Det går inte att ställa in det till resultatet av ett anropat kommando.</span><span class="sxs-lookup"><span data-stu-id="c6fe7-117">You cannot set it to the result of an invoked command.</span></span>

```powershell
enum MyEnum
{
    Enum1
    Enum2
    Enum3 = 42
    Enum4 = [int]::MaxValue
}
```

<span data-ttu-id="c6fe7-118">Uppräkningar stöder aritmetiska åtgärder, som du ser i följande exempel.</span><span class="sxs-lookup"><span data-stu-id="c6fe7-118">Enums support arithmetic operations, as shown in the following example.</span></span>

```powershell
enum SomeEnum { Max = 42 }
enum OtherEnum { Max = [SomeEnum]::Max + 1 }
```

### <a name="import-dscresource"></a><span data-ttu-id="c6fe7-119">Importera – Dscresource Keyword Supports</span><span class="sxs-lookup"><span data-stu-id="c6fe7-119">Import-DscResource</span></span>

<span data-ttu-id="c6fe7-120">`Import-DscResource` är nu ett faktiskt dynamiskt nyckelord.</span><span class="sxs-lookup"><span data-stu-id="c6fe7-120">`Import-DscResource` is now a true dynamic keyword.</span></span> <span data-ttu-id="c6fe7-121">PowerShell parsar den angivna modulens rotdomän, söker efter klasser som innehåller attributet **dscresource Keyword Supports** .</span><span class="sxs-lookup"><span data-stu-id="c6fe7-121">PowerShell parses the specified module's root module, searching for classes that contain the **DscResource** attribute.</span></span>

### <a name="implementingassembly"></a><span data-ttu-id="c6fe7-122">ImplementingAssembly</span><span class="sxs-lookup"><span data-stu-id="c6fe7-122">ImplementingAssembly</span></span>

<span data-ttu-id="c6fe7-123">Ett nytt fält, **ImplementingAssembly**, har lagts till i **ModuleInfo**.</span><span class="sxs-lookup"><span data-stu-id="c6fe7-123">A new field, **ImplementingAssembly**, has been added to **ModuleInfo**.</span></span> <span data-ttu-id="c6fe7-124">Den är inställd på den dynamiska sammansättning som skapats för en skript-modul om skriptet definierar klasser eller den inlästa sammansättningen för binära moduler.</span><span class="sxs-lookup"><span data-stu-id="c6fe7-124">It is set to the dynamic assembly created for a script module if the script defines classes, or the loaded assembly for binary modules.</span></span> <span data-ttu-id="c6fe7-125">Den anges inte när **ModuleType** är **manifest**.</span><span class="sxs-lookup"><span data-stu-id="c6fe7-125">It is not set when **ModuleType** is **Manifest**.</span></span>

<span data-ttu-id="c6fe7-126">Reflektion i fältet **ImplementingAssembly** identifierar resurser i en modul.</span><span class="sxs-lookup"><span data-stu-id="c6fe7-126">Reflection on the **ImplementingAssembly** field discovers resources in a module.</span></span> <span data-ttu-id="c6fe7-127">Det innebär att du kan identifiera resurser som skrivits på antingen PowerShell eller andra hanterade språk.</span><span class="sxs-lookup"><span data-stu-id="c6fe7-127">This means you can discover resources written in either PowerShell or other managed languages.</span></span>

## <a name="further-reading"></a><span data-ttu-id="c6fe7-128">Ytterligare läsning</span><span class="sxs-lookup"><span data-stu-id="c6fe7-128">Further reading</span></span>

- [<span data-ttu-id="c6fe7-129">about_Classes</span><span class="sxs-lookup"><span data-stu-id="c6fe7-129">about_Classes</span></span>](/powershell/module/microsoft.powershell.core/about/about_classes)
- [<span data-ttu-id="c6fe7-130">about_Enum</span><span class="sxs-lookup"><span data-stu-id="c6fe7-130">about_Enum</span></span>](/powershell/module/microsoft.powershell.core/about/about_enum)
- [<span data-ttu-id="c6fe7-131">about_Classes_and_DSC</span><span class="sxs-lookup"><span data-stu-id="c6fe7-131">about_Classes_and_DSC</span></span>](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc)
