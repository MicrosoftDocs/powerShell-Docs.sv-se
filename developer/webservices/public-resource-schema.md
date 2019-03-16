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
ms.openlocfilehash: c7e20ff0f36e8cab2d414ff2e5924b3359ad9c60
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057254"
---
# <a name="public-resource-schema"></a>Schema för offentliga resurser

Management OData använder MOF för att definiera resurser och deras egenskaper. Egenskaperna för en Management OData-entitet motsvarar egenskaperna för hanterad typ som returnerats av cmdleten underliggande.

## <a name="defining-a-resource"></a>Definiera en resurs

Varje resurs motsvarar ett objekt som returneras av en Windows PowerShell-cmdlet. I den offentliga resursen MOF-filen definierar du en resurs genom att deklarera en klass. Klassen består av egenskaper som motsvarar egenskaperna för objektet. Till exempel i följande exempel visas den [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) klass representeras av följande MOF.

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

Varje egenskapsnamn föregås av en datatyp. Datatyper i det här exemplet motsvarar primitiva CLR-datatyper i .NET Framework-program, men egenskaperna kan också vara referenser till andra resurser och komplexa typer som är både beskrivs senare.

Den `Key` kvalificerare anger att en egenskap som unikt identifierar en resursinstans. En resurs kan ha fler än en nyckel.

Den `Required` kvalificerare anger att egenskapen är obligatoriskt. Om en egenskap är märkt med den `Key` kvalificerare, anses det krävs, och `Required` kvalificerare är inte nödvändigt.

### <a name="complex-data-types"></a>Komplexa datatyper

Egenskaper för entiteter kan ha komplexa datatyper. Komplexa datatyper är typer som består av andra typer, liknar Struct-datatyperna i programmeringsspråket C. En komplex typ har deklarerats i MOF-filen som en klass med den `ComplexType` kvalificerare som i följande exempel.

```csharp
[ComplexType]
class PswsTest_ProcessModule
{
    String ModuleName;
    String FileName;
};
```

För att deklarera en entitetsegenskap som en komplex typ, kan du ange den som en `string` typ med den `EmbeddedInstance` kvalificerare, inklusive namnet på den komplexa typen. I följande exempel visas deklarationen av en egenskap för den `PswsTest_ProcessModule` typen deklarerade i föregående exempel.

```csharp
[Required, EmbeddedInstance("PswsTest_ProcessModule")] String Modules[];
```

### <a name="associating-entities"></a>Associera entiteter

Du kan associera två entiteter med hjälp av kopplingen och Associeringsklass kvalificerare. Mer information finns i [associera Management OData entiteter](./associating-management-odata-entities.md).

### <a name="derived-types"></a>Härledda typer

Du kan härleda en typ från en annan typ. Den härledda typen ärver alla egenskaper av typen från vilket det kommer utöver eventuella egenskaper som härleds uttryckligen. I följande exempel visas en typdeklaration och sedan en deklaration av två typer som härletts från den typen.

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