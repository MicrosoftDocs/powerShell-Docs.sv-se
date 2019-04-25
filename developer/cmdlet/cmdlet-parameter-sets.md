---
title: Cmdletens parameteruppsättningar | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f902fd4d-8f6e-4ef1-b07f-59983039a0d1
caps.latest.revision: 10
ms.openlocfilehash: a5822ef1ed3c9efb5957c20255783d515de8957a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068530"
---
# <a name="cmdlet-parameter-sets"></a>Cmdlet-parameteruppsättningar

Windows PowerShell använder parameteruppsättningar så att du kan skriva en enda cmdlet som kan utföra olika åtgärder för olika scenarier. Parameteruppsättningar kan du exponera olika parametrar för användaren och för att returnera olika typer av information baserat på de parametrar som angetts av användaren.

## <a name="examples-of-parameter-sets"></a>Exempel på parameteruppsättningar

Till exempel den `Get-EventLog` cmdlet (som anges av Windows PowerShell) returnerar olika typer av information beroende på om användaren anger den `List` eller `LogName` parametern. Om den `List` parameter har angetts, cmdleten returnerar information om loggfilerna själva men inte händelseinformationen de innehåller. Om den `LogName` parameter har angetts, returnerar cmdleten information om händelser i en specifik händelselogg. Den `List` och `LogName` parametrar identifiera två separata parameteruppsättningar.

## <a name="unique-parameter"></a>Unikt parametern

Varje parameteruppsättningen måste ha en unik parameter som Windows PowerShell-runtime kan använda för att visa rätt parameteruppsättningen. Om möjligt måste unika parametern vara en obligatorisk parameter. När parametern är obligatorisk om användaren tvingas att ange parametern och Windows PowerShell-runtime använda parametern för att identifiera parametern inställd på att använda. Den unika parametern får inte vara obligatorisk om cmdlet: är avsedd att köras utan att ange några parametrar.

## <a name="multiple-parameter-sets"></a>Flera parameteruppsättningar

I följande bild visar den vänstra kolumnen tre giltig parameteruppsättningar. Parametern A är unika för den första parameteruppsättningen parametern B är unika för den andra parameteruppsättningen och parametern C är unika för den tredje parameteruppsättningen. I den högra kolumnen har parameteruppsättningar men inte en unik parameter.

![ps_parametersets](../media/ps-parametersets.gif)

## <a name="parameter-set-requirements"></a>Parameteruppsättning krav

Följande krav gäller för alla parameteruppsättningar.

- Varje parameteruppsättningen måste ha minst en unik parameter. Se den här parametern om möjligt en obligatorisk parameter.

- En parameteruppsättning som innehåller flera namngivna parametrar måste definiera unika positioner för varje parameter. Inga två namngivna parametrar kan ange samma plats.

- Endast en parameter i en mängd kan deklarera den `ValueFromPipeline` nyckelord med värdet `true`. Flera parametrar kan definiera den `ValueFromPipelineByPropertyName` nyckelord med värdet `true`.

- Om inga parameteruppsättning har angetts för en parameter, tillhör parametern alla parameteruppsättningar.

## <a name="default-parameter-sets"></a>Standard parameteruppsättningar

När flera parameteruppsättningar har definierats kan du använda den `DefaultParameterSetName` nyckelordet för Cmdlet-attribut som anger den standard-parameteruppsättningen. Windows PowerShell använder standardparameter som anger om den inte kan avgöra parametern inställd på att använda utifrån den information som tillhandahålls av kommandot. Läs mer om attributet Cmdlet [Cmdlet attributet deklarationen](./cmdlet-attribute-declaration.md).

## <a name="declaring-parameter-sets"></a>Deklarera parameteruppsättningar

Om du vill skapa en parameteruppsättning, måste du ange den `ParameterSetName` nyckelord när du deklarerar parameterattributet för varje parameter i parameteruppsättningen. Lägga till en Parameter attribut för varje parameteruppsättningen för parametrar som tillhör flera parameteruppsättningar. På så sätt kan du definiera parametern olika för varje parameteruppsättningen. Du kan till exempel definiera en parameter som obligatoriskt i en uppsättning och en valfri i en annan. Varje parameteruppsättningen måste dock innehålla en unik parameter.

I följande exempel visas den `UserName` parametern är unikt parametern för parameteruppsättningen Test01 och `ComputerName` parametern är unikt parametern för Test02 parameteruppsättningen. Den `SharedParam` parametern hör till båda uppsättningarna och är obligatoriskt för Test01 parameteruppsättning men valfritt för Test02 parameteruppsättningen.

```csharp
[Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test01")]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;

[Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test02")]
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
private string sharedParam;    [Parameter(Position = 0, Mandatory = true,
           ParameterSetName = "Test01")]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```