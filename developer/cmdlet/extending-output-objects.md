---
title: Utöka utdata objekt | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a252e0ec-d456-42d7-bd49-d6b8bc57f388
caps.latest.revision: 11
ms.openlocfilehash: 9c9d50c880f843e21621e5735c800e3afb48b2ad
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850962"
---
# <a name="extending-output-objects"></a>Utöka utdataobjekt

Du kan utöka .NET Framework-objekt som returneras av cmdlet: ar, funktioner och skript med hjälp av typer filer (.ps1xml). Typer av filer är XML-baserade filer som låter dig lägga till egenskaper och metoder för befintliga objekt. Windows PowerShell innehåller till exempel filen Types.ps1xml, som lägger tillför element i flera befintliga .NET Framework-objekt. Filen Types.ps1xml finns i installationskatalogen för Windows PowerShell (`$pshome`). Du kan skapa en egen typer fil att utöka dessa objekt eller utöka andra objekt. När du utökar ett objekt med hjälp av en typer har valfri instans av objektet utökats med de nya elementen.

## <a name="extending-the-systemarray-object"></a>Utöka System.Array-objekt

I följande exempel visas hur Windows PowerShell utökar den [System.Array](/dotnet/api/System.Array) objekt i filen Types.ps1xml. Som standard [System.Array](/dotnet/api/System.Array) objekt har en `Length` egenskap som visar antalet objekt i matrisen. Men eftersom ”namnlängd” inte beskriver egenskapen tydligt, Windows PowerShell lägger till den `Count` alias-egenskapen, som visar samma värde som den `Length` egenskapen. Följande XML-filen lägger till den `Count` egenskap enligt den [System.Array](/dotnet/api/System.Array) typen.

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

Om du vill se den nya egenskapen alias, använda en [Get-Member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) kommandot på alla matris, som visas i följande exempel.

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
Du kan använda antingen den `Count` egenskapen eller `Length` egenskapen att avgöra hur många objekt som är i en matris. Till exempel:

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

## <a name="custom-types-files"></a>Anpassade filer

Starta genom att kopiera en befintlig typer-fil för att skapa en fil för anpassade typer. Den nya filen kan ha vilket namn, men den måste ha filnamnstillägget .ps1xml. När du kopierar filen, du kan placera den nya filen i en katalog som är tillgänglig för Windows PowerShell, men det är bra att placera filerna i installationskatalogen för Windows PowerShell (`$pshome`) eller i en underkatalog till installationskatalogen.

Om du vill lägga till egna utökade typer i filen, lägger du till en typer-element för varje objekt som du vill utöka. I följande avsnitt innehåller exempel.

- Läs mer om att lägga till egenskaper och egenskapsuppsättningar [utökade egenskaper](./extending-properties-for-objects.md)

- Läs mer om att lägga till metoder, [utökade metoder](./defining-default-methods-for-objects.md).

- Läs mer om att lägga till medlemmen uppsättningar [utökade medlem anger](./defining-default-member-sets-for-objects.md).

När du har definierat dina egna utökade typer kan du använda någon av följande metoder för att tillgängliggöra dina utökade objekt:

- Om du vill göra din fil för utökade typer som är tillgängliga för den aktuella sessionen, använda den [uppdatering TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet för att lägga till den nya filen. Om du vill att din typer för att få företräde framför de typer som definieras i andra typer (inklusive Types.ps1xml-fil), använder den `PrependData` -parametern för den [uppdatering TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet.
- För att göra din fil för utökade typer tillgängliga för alla framtida sessioner, lägga till filen typer till en modul, exportera den aktuella sessionen eller Lägg till den [uppdatering TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) kommandot Windows PowerShell-profil.

## <a name="signing-types-files"></a>Signerar typer filer

Typer av filer vara digitalt signerade att förhindra manipulation eftersom XML-filen kan innehålla skriptblock. Läs mer om att lägga till digitala signaturer [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing)

## <a name="see-also"></a>Se även

[Definiera standardegenskaperna för objekt](./extending-properties-for-objects.md)

[Definiera standard metoder för objekt](./defining-default-methods-for-objects.md)

[Definiera standard medlemsuppsättningar för objekt](./defining-default-member-sets-for-objects.md)

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
