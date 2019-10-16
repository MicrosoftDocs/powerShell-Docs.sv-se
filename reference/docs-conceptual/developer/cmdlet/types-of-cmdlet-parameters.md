---
title: Typer av cmdlet-parametrar | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6602730d-3892-4656-80c7-7bca2d14337f
caps.latest.revision: 14
ms.openlocfilehash: f5781c0c03aca41d01a44598a9a8c00d6d21d2fd
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359180"
---
# <a name="types-of-cmdlet-parameters"></a>Typer av cmdlet-parametrar

I det här avsnittet beskrivs de olika typerna av parametrar som du kan deklarera i-cmdletar. Cmdlet-parametrar kan vara positions, namngivna, obligatoriska, valfria eller växla parametrar.

## <a name="positional-and-named-parameters"></a>Parametrar för position och namngivna

Alla cmdlet-parametrar är antingen namngivna eller positions parametrar. En namngiven parameter kräver att du anger parameter namnet och argumentet när du anropar cmdleten. En positions parameter kräver bara att du skriver argumenten i relativ ordning. Systemet mappar sedan det första argumentet utan namn till den första positions parametern. Systemet mappar det andra namnlösa argumentet till den andra namnlösa parametern och så vidare. Som standard är alla cmdlet-parametrar namngivna parametrar.

Om du vill definiera en namngiven parameter utelämnar du nyckelordet `Position` i **parameter** deklarationen, som du ser i följande parameter deklaration.

```csharp
[Parameter(ValueFromPipeline=true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

Om du vill definiera en positions parameter lägger du till nyckelordet `Position` i parameter deklarationen och anger sedan en position. I följande exempel deklareras parametern `UserName` som en positions parameter med position 0. Det innebär att det första argumentet för anropet automatiskt binds till den här parametern.

```csharp
[Parameter(Position = 0)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

> [!NOTE]
> Lämplig cmdlet-design rekommenderar att de mest använda parametrarna deklareras som positions parametrar så att användaren inte behöver ange parameter namnet när cmdleten körs.

Positions-och namngivna parametrar accepterar enskilda argument eller flera argument avgränsade med kommatecken. Flera argument tillåts endast om parametern accepterar en samling, till exempel en sträng mat ris. Du kan blanda positions-och namngivna parametrar i samma cmdlet. I det här fallet hämtar systemet de namngivna argumenten först och försöker sedan mappa de återstående namnlösa argumenten till positions parametrarna.

Följande kommandon visar de olika sätt som du kan använda för att ange enstaka och flera argument för parametrarna i `Get-Command`-cmdleten. Observera att i de två sista exemplen behöver inte **-Name** anges eftersom parametern `Name` definieras som en positions parameter.

```powershell
Get-Command -Name get-service
Get-Command -Name get-service,set-service
Get-Command get-service
Get-Command get-service,set-service
```

## <a name="mandatory-and-optional-parameters"></a>Obligatoriska och valfria parametrar

Du kan också definiera cmdlet-parametrar som obligatoriska eller valfria parametrar. (En obligatorisk parameter måste anges innan Windows PowerShell-körningsmiljön anropar cmdleten.)  Som standard definieras parametrar som valfria.

Om du vill definiera en obligatorisk parameter lägger du till nyckelordet `Mandatory` i parameter deklarationen och anger det till `true`, som du ser i följande parameter deklaration.

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

Om du vill definiera en valfri parameter utelämnar du nyckelordet `Mandatory` i **parameter** deklarationen, som du ser i följande parameter deklaration.

```csharp
[Parameter(Position = 0)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

## <a name="switch-parameters"></a>Växla parametrar

Windows PowerShell innehåller en typ av [system. Management. Automation. SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) som gör att du kan definiera en parameter vars värde anges automatiskt till `false` om parametern inte anges när cmdleten anropas. Använd när det är möjligt och Använd switch-parametrar i stället för booleska parametrar.

Överväg följande exempel. Som standard skickar flera Windows PowerShell-cmdlets inte ett utgående objekt nedåt i pipelinen. Dessa cmdletar har dock en `PassThru`-växel parameter som åsidosätter standard beteendet. Om parametern `PassThru` anges när dessa cmdletar anropas, returnerar cmdleten ett utgående objekt till pipelinen.

Om du behöver parametern för att ha standardvärdet `true` när parametern inte anges i anropet, bör du överväga att återställa meningen för parametern. I stället för att ange attributet parameter till ett booleskt värde för `true`, deklarera egenskapen som [system. Management. Automation. SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) -typ och ange sedan standardvärdet för parametern till `false`.

För att definiera en switch-parameter, deklarera egenskapen som [system. Management. Automation. SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) -typ, som du ser i följande exempel.

```csharp
[Parameter(Position = 1)]
public SwitchParameter GoodBye
{
  get { return goodbye; }
  set { goodbye = value; }
}
private bool goodbye;
```

Om du vill att cmdleten ska fungera på parametern när den har angetts använder du följande struktur i någon av metoderna för bearbetning av indata.

```csharp
protected override void ProcessRecord()
{
  WriteObject("Switch parameter test: " + userName + ".");
  if(goodbye)
  {
    WriteObject(" Goodbye!");
  }
} // End ProcessRecord
```

## <a name="see-also"></a>Se även

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)
