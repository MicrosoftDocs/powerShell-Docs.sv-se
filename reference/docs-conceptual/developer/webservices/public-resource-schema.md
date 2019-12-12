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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72356814"
---
# <a name="public-resource-schema"></a>Schema för offentliga resurser

Hantering av OData använder MOF för att definiera resurser och deras egenskaper. Egenskaperna för en OData-enhet för hantering motsvarar direkt till egenskaperna för den hanterade typ som returneras av den underliggande cmdleten.

## <a name="defining-a-resource"></a>Definiera en resurs

Varje resurs motsvarar ett objekt som returneras av en Windows PowerShell-cmdlet. I MOF-filen för offentlig resurs definierar du en resurs genom att deklarera en klass. Klassen består av egenskaper som motsvarar egenskaperna för objektet. I följande exempel representeras klassen [system. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) av följande MOF.

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

Varje egenskaps namn föregås av en datatyp. Data typerna i det här exemplet motsvarar primitiva CLR-datatyper i .NET Framework, men egenskaper kan också vara referenser till andra resurser eller komplexa typer, vilka beskrivs senare.

`Key`-kvalificeraren anger att en egenskap används för att unikt identifiera en resurs instans. En resurs kan ha mer än en nyckel.

`Required`-kvalificeraren anger att egenskapen är obligatorisk. Om en egenskap är märkt med `Key`-kvalificeraren anses den vara obligatorisk och `Required` kvalificeraren är inte nödvändig.

### <a name="complex-data-types"></a>Komplexa data typer

Egenskaper för entiteter kan ha komplexa data typer. Komplexa data typer är typer som består av andra typer, ungefär som structs i programmeringsspråket C. En komplex typ deklareras i MOF-filen som en klass med `ComplexType`-kvalificeraren, som i följande exempel.

```csharp
[ComplexType]
class PswsTest_ProcessModule
{
    String ModuleName;
    String FileName;
};
```

Om du vill deklarera en entitets egenskap som en komplex typ deklarerar du den som en `string` typ med `EmbeddedInstance` kvalificeraren, inklusive namnet på den komplexa typen. I följande exempel visas en deklaration av en egenskap för den `PswsTest_ProcessModule` typ som har deklarerats i föregående exempel.

```csharp
[Required, EmbeddedInstance("PswsTest_ProcessModule")] String Modules[];
```

### <a name="associating-entities"></a>Kopplar entiteter

Du kan associera två entiteter med associerings-och AssociationClass-kvalificerarna. Mer information finns i [associera hantering OData-entiteter](./associating-management-odata-entities.md).

### <a name="derived-types"></a>Härledda typer

Du kan härleda en typ från en annan typ. Den härledda typen ärver alla egenskaper av den typ som den är härledd från, utöver de egenskaper som uttryckligen härleds. I följande exempel visas en typ deklaration och en deklaration av två typer som härletts från den typen.

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