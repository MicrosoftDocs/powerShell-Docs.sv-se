---
ms.date: 09/13/2016
ms.topic: reference
title: Cmdlet-parameteruppsättningar
description: Cmdlet-parameteruppsättningar
ms.openlocfilehash: e84af7faf5b7459d8dbe06847526efe804e2c5e1
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92668294"
---
# <a name="cmdlet-parameter-sets"></a>Cmdlet-parameter uppsättningar

PowerShell använder parameter uppsättningar för att ge dig möjlighet att skriva en enda cmdlet som kan utföra olika åtgärder för olika scenarier. Parameter uppsättningar gör att du kan exponera olika parametrar för användaren. Och för att returnera annan information baserat på de parametrar som anges av användaren.

## <a name="examples-of-parameter-sets"></a>Exempel på parameter uppsättningar

PowerShell- `Get-EventLog` cmdleten returnerar till exempel olika uppgifter beroende på om användaren anger **listan** eller parametern **LogName** . Om **list** parametern anges, returnerar cmdleten information om själva loggfilerna, men inte den händelse information som de innehåller. Om parametern **LogName** anges returnerar cmdleten information om händelserna i en specifik händelse logg. **List** -och **LogName** -parametrarna identifierar två separata parameter uppsättningar.

## <a name="unique-parameter"></a>Unik parameter

Varje parameter uppsättning måste ha en unik parameter som PowerShell-körningsmiljön använder för att exponera rätt parameter uppsättning. Om möjligt ska den unika parametern vara en obligatorisk parameter. När en parameter är obligatorisk måste användaren ange parametern och PowerShell-körningsmiljön använder den parametern för att identifiera parameter uppsättningen. Den unika parametern kan inte vara obligatorisk om din cmdlet är avsedd att köras utan att några parametrar anges.

## <a name="multiple-parameter-sets"></a>Flera parameter uppsättningar

I följande bild visas tre giltiga parameter uppsättningar i den vänstra kolumnen. **Parametern A** är unik för den första parameter uppsättningen, **parametern B** är unik för den andra parameter uppsättningen och **parametern C** är unik för den tredje parameter uppsättningen. Parameter uppsättningarna i den högra kolumnen har ingen unik parameter.

![Bild av parameter uppsättningar](media/cmdlet-parameter-sets/ps-parametersets.gif)

## <a name="parameter-set-requirements"></a>Krav för parameter uppsättning

Följande krav gäller för alla parameter uppsättningar.

- Varje parameter uppsättning måste ha minst en unik parameter. Om möjligt ska du göra denna parameter till en obligatorisk parameter.

- En parameter uppsättning som innehåller flera positions parametrar måste definiera unika positioner för varje parameter. Det går inte att ange samma position med två positions parametrar.

- Endast en parameter i en mängd kan deklarera `ValueFromPipeline` nyckelordet med värdet `true` .
  Flera parametrar kan definiera `ValueFromPipelineByPropertyName` nyckelordet med värdet `true` .

- Om ingen parameter uppsättning anges för en parameter, tillhör parametern alla parameter uppsättningar.

> [!NOTE]
> För en cmdlet eller funktion finns det en gräns på 32 parameter uppsättningar.

## <a name="default-parameter-sets"></a>Standard parameter uppsättningar

När du har definierat flera parameter uppsättningar kan du `DefaultParameterSetName` Ange standard parameter uppsättningen genom att använda nyckelordet för **cmdlet** -attributet. PowerShell använder standard parameter uppsättningen om den inte kan avgöra vilken parameter som ska användas baserat på den information som tillhandahålls av kommandot. Mer information om **cmdlet** -attributet finns i [deklaration av cmdlet-attribut](./cmdlet-attribute-declaration.md).

## <a name="declaring-parameter-sets"></a>Deklarera parameter uppsättningar

Om du vill skapa en parameter uppsättning måste du ange `ParameterSetName` nyckelordet när du deklarerar attributet **parameter** för varje parameter i parameter uppsättningen. För parametrar som tillhör flera parameter uppsättningar lägger du till ett **parameter** -attribut för varje parameter uppsättning. Med det här attributet kan du definiera parametern på olika sätt för varje parameter uppsättning. Du kan till exempel definiera en parameter som obligatorisk i en uppsättning och valfri i en annan. Varje parameter uppsättning måste dock innehålla en unik parameter. Mer information finns i [deklaration av parameter attribut](parameter-attribute-declaration.md).

I följande exempel är parametern **username** den unika parametern för `Test01` parameter uppsättningen och parametern **computername** är den unika parametern för `Test02` parameter uppsättningen. Parametern **SharedParam** tillhör båda uppsättningarna och är obligatorisk för `Test01` parameter uppsättningen men valfritt för `Test02` parameter uppsättningen.

```csharp
[Parameter(Position = 0, Mandatory = true, ParameterSetName = "Test01")]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;

[Parameter(Position = 0, Mandatory = true, ParameterSetName = "Test02")]
public string ComputerName
{
  get { return computerName; }
  set { computerName = value; }
}
private string computerName;

[Parameter(Mandatory= true, ParameterSetName = "Test01")]
[Parameter(ParameterSetName = "Test02")]
public string SharedParam
{
    get { return sharedParam; }
    set { sharedParam = value; }
}
private string sharedParam;
```
