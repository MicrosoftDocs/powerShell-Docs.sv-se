---
title: Utökar utmatnings objekt | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a252e0ec-d456-42d7-bd49-d6b8bc57f388
caps.latest.revision: 11
ms.openlocfilehash: 9c9d50c880f843e21621e5735c800e3afb48b2ad
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359328"
---
# <a name="extending-output-objects"></a>Utöka utdataobjekt

Du kan utöka .NET Framework objekt som returneras av cmdlets, Functions och scripts genom att använda typer filer (. ps1xml). Filtyper är XML-baserade filer som gör att du kan lägga till egenskaper och metoder i befintliga objekt. Windows PowerShell tillhandahåller till exempel filen types. ps1xml, som lägger till element i flera befintliga .NET Framework-objekt. Filen types. ps1xml finns i installations katalogen för Windows PowerShell (`$pshome`). Du kan skapa en egen typ fil för att ytterligare utöka objekten eller för att utöka andra objekt. När du utökar ett objekt med hjälp av en typ fil utökas alla instanser av objektet med de nya elementen.

## <a name="extending-the-systemarray-object"></a>Utöka system. Array-objektet

I följande exempel visas hur Windows PowerShell utökar [system. Array](/dotnet/api/System.Array) -objektet i filen types. ps1xml. Som standard har [system. Array](/dotnet/api/System.Array) -objekt en `Length`-egenskap som visar antalet objekt i matrisen. Men eftersom namnet "Length" inte tydligt beskriver egenskapen, lägger Windows PowerShell till egenskapen `Count` alias som visar samma värde som egenskapen `Length`. Följande XML lägger till egenskapen `Count` till typen [system. mat ris](/dotnet/api/System.Array) .

```xml
<Type>
  <Name>System.Array</Name>
  <Members>
    <AliasProperty>
      <Name>Count</Name>
      <ReferencedMemberName>Length</ReferencedMemberName>
    </AliasProperty>
  </Members>
</Type>

```

Om du vill se den nya egenskapen alias använder du kommandot [Get-Member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) på valfri matris, som du ser i följande exempel.

```powershell
Get-Member -InputObject (1,2,3,4)
```

Kommandot returnerar följande resultat.
```output
Name           MemberType    Definition
----           ----------    ----------
Count          AliasProperty Count = Length
Address        Method        System.Object& Address(Int32 )
Clone          Method        System.Object Clone()
CopyTo         Method        System.Void CopyTo(Array array, Int32 index):
Equals         Method        System.Boolean Equals(Object obj)
Get            Method        System.Object Get(Int32 )
...
Length         Property      System.Int32 Length {get;}
```
Du kan använda antingen egenskapen `Count` eller egenskapen `Length` för att avgöra hur många objekt som finns i en matris. Till exempel:

```powershell
PS> (1, 2, 3, 4).Count
```

```output
4
```

```powershell
PS> (1, 2, 3, 4).Length
```

```output
4
```

## <a name="custom-types-files"></a>Filer för anpassade typer

Börja med att kopiera en befintlig typ fil för att skapa en anpassad typ. Den nya filen kan ha vilket namn som helst, men den måste ha fil namns tillägget. ps1xml. När du kopierar filen kan du placera den nya filen i valfri katalog som är tillgänglig för Windows PowerShell, men det är användbart att placera filerna i installations katalogen för Windows PowerShell (`$pshome`) eller i en under katalog i installations katalogen.

Om du vill lägga till dina egna utökade typer i filen lägger du till ett typ element för varje objekt som du vill utöka. I följande avsnitt finns exempel.

- Mer information om hur du lägger till egenskaper och egenskaps uppsättningar finns i [utökade egenskaper](./extending-properties-for-objects.md)

- Mer information om hur du lägger till metoder finns i [utökade metoder](./defining-default-methods-for-objects.md).

- Mer information om hur du lägger till medlems uppsättningar finns i [utökade medlems uppsättningar](./defining-default-member-sets-for-objects.md).

När du har definierat dina egna utökade typer kan du använda någon av följande metoder för att göra dina utökade objekt tillgängliga:

- Använd cmdleten [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) för att lägga till den nya filen för att göra din utökade typ av fil tillgänglig för den aktuella sessionen. Om du vill att typerna ska prioriteras över de typer som har definierats i andra typer av filer (inklusive filen types. ps1xml) använder du parametern `PrependData` för cmdleten [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) .
- Om du vill göra din utöknings bara fil tillgänglig för alla framtida sessioner lägger du till typ filen i en modul, exporterar den aktuella sessionen eller lägger till kommandot [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) i Windows PowerShell-profilen.

## <a name="signing-types-files"></a>Filer för signerings typer

Filtyper ska signeras digitalt för att förhindra manipulering eftersom XML-filen kan innehålla skript block. Mer information om hur du lägger till digitala signaturer finns [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing)

## <a name="see-also"></a>Se även

[Definiera standard egenskaper för objekt](./extending-properties-for-objects.md)

[Definiera standard metoder för objekt](./defining-default-methods-for-objects.md)

[Definiera standard medlems uppsättningar för objekt](./defining-default-member-sets-for-objects.md)

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)
