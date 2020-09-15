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
# <a name="new-language-features-in-powershell-50"></a>Nya språk funktioner i PowerShell 5,0

PowerShell 5,0 har lagt till möjligheten att definiera klasser och andra användardefinierade typer med hjälp av formell syntax och semantiska objekt som andra objektorienterade programmeringsspråk. Målet är att göra det möjligt för utvecklare och IT-proffs att använda PowerShell för ett bredare utbud av användnings fall, förenkla utvecklingen av PowerShell-artefakter (till exempel DSC-resurser) och påskynda täckning av hanterings ytor.

PowerShell 5,0 introducerar följande nya språk element i PowerShell:

### <a name="class-keyword"></a>Klass nyckelord

`class`Nyckelordet definierar en ny klass. Detta är en True .NET Framework-typ. Klass medlemmar är offentliga, men endast offentliga inom modulens omfattning. Det går inte att referera till typnamn som en sträng (till exempel `New-Object` fungerar inte) och i den här versionen kan du inte använda en typ literal (till exempel `[MyClass]` ) utanför skriptet eller modulens fil som klassen är definierad i.

```powershell
class MyClass
{
    ...
}
```

### <a name="enum-keyword-and-enumerations"></a>Räkna upp nyckelord och uppräkningar

Stöd för `enum` nyckelordet har lagts till, vilket använder ny rad som avgränsare. För närvarande kan du inte definiera en uppräknare i termer av sig själv. Du kan dock initiera en uppräkning i termer av en annan uppräkning, som du ser i följande exempel. Bastypen kan inte heller anges. Det är alltid `[int]` .

```powershell
enum Color2
{
    Yellow = [Color]::Blue
}
```

Ett uppräknings värde måste vara en konstant för en parse. Det går inte att ställa in det till resultatet av ett anropat kommando.

```powershell
enum MyEnum
{
    Enum1
    Enum2
    Enum3 = 42
    Enum4 = [int]::MaxValue
}
```

Uppräkningar stöder aritmetiska åtgärder, som du ser i följande exempel.

```powershell
enum SomeEnum { Max = 42 }
enum OtherEnum { Max = [SomeEnum]::Max + 1 }
```

### <a name="import-dscresource"></a>Importera – Dscresource Keyword Supports

`Import-DscResource` är nu ett faktiskt dynamiskt nyckelord. PowerShell parsar den angivna modulens rotdomän, söker efter klasser som innehåller attributet **dscresource Keyword Supports** .

### <a name="implementingassembly"></a>ImplementingAssembly

Ett nytt fält, **ImplementingAssembly**, har lagts till i **ModuleInfo**. Den är inställd på den dynamiska sammansättning som skapats för en skript-modul om skriptet definierar klasser eller den inlästa sammansättningen för binära moduler. Den anges inte när **ModuleType** är **manifest**.

Reflektion i fältet **ImplementingAssembly** identifierar resurser i en modul. Det innebär att du kan identifiera resurser som skrivits på antingen PowerShell eller andra hanterade språk.

## <a name="further-reading"></a>Ytterligare läsning

- [about_Classes](/powershell/module/microsoft.powershell.core/about/about_classes)
- [about_Enum](/powershell/module/microsoft.powershell.core/about/about_enum)
- [about_Classes_and_DSC](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc)
