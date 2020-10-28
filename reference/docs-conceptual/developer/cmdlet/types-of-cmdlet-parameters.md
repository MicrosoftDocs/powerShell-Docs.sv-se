---
ms.date: 09/13/2016
ms.topic: reference
title: Typer av cmdlet-parametrar
description: Typer av cmdlet-parametrar
ms.openlocfilehash: 8daaa3c778396e06a826de3b93e0610c51160fb4
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92660491"
---
# <a name="types-of-cmdlet-parameters"></a>Typer av cmdlet-parametrar

I det här avsnittet beskrivs de olika typerna av parametrar som du kan deklarera i-cmdletar. Cmdlet-parametrar kan vara positions, namngivna, obligatoriska, valfria eller växla parametrar.

## <a name="positional-and-named-parameters"></a>Parametrar för position och namngivna

Alla cmdlet-parametrar är antingen namngivna eller positions parametrar. En namngiven parameter kräver att du anger parameter namnet och argumentet när du anropar cmdleten. En positions parameter kräver bara att du skriver argumenten i relativ ordning. Systemet mappar sedan det första argumentet utan namn till den första positions parametern. Systemet mappar det andra namnlösa argumentet till den andra namnlösa parametern och så vidare. Som standard är alla cmdlet-parametrar namngivna parametrar.

Om du vill definiera en namngiven parameter utelämnar du `Position` nyckelordet i **parameter** -attributets deklaration, som du ser i följande parameter deklaration.

```csharp
[Parameter(ValueFromPipeline=true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

Om du vill definiera en positions parameter lägger du till `Position` nyckelordet i parametern parameter attribut och anger sedan en position. I följande exempel `UserName` deklareras parametern som en positions parameter med position 0. Det innebär att det första argumentet för anropet automatiskt binds till den här parametern.

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

Följande kommandon visar de olika sätt som du kan använda för att ange enstaka och flera argument för `Get-Command` cmdlet: en. Observera att i de två sista exemplen behöver **-namn** inte anges eftersom `Name` parametern definieras som en positions parameter.

```powershell
Get-Command -Name get-service
Get-Command -Name get-service,set-service
Get-Command get-service
Get-Command get-service,set-service
```

## <a name="mandatory-and-optional-parameters"></a>Obligatoriska och valfria parametrar

Du kan också definiera cmdlet-parametrar som obligatoriska eller valfria parametrar. (En obligatorisk parameter måste anges innan Windows PowerShell-körningsmiljön anropar cmdleten.)  Som standard definieras parametrar som valfria.

Om du vill definiera en obligatorisk parameter lägger du till `Mandatory` nyckelordet i parametern parameter-attribut och anger det till `true` , som du ser i följande parameter deklaration.

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

Om du vill definiera en valfri parameter utelämnar du `Mandatory` nyckelordet i **parameter** -attributets deklaration, som du ser i följande parameter deklaration.

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

Windows PowerShell tillhandahåller en [system. Management. Automation. SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) -typ som gör att du kan definiera en parameter vars värde automatiskt anges till `false` om parametern inte anges när cmdleten anropas. Använd när det är möjligt och Använd switch-parametrar i stället för booleska parametrar.

Överväg följande exempel. Som standard skickar flera Windows PowerShell-cmdlets inte ett utgående objekt nedåt i pipelinen. Dessa cmdletar har dock en `PassThru` växel parameter som åsidosätter standard beteendet. Om `PassThru` parametern anges när dessa cmdletar anropas, returnerar cmdleten ett utgående objekt till pipelinen.

Om du behöver parametern för att ha ett standardvärde för `true` när parametern inte anges i anropet, bör du överväga att återställa meningen för parametern. För exempel, i stället för att ange parametervärdet till ett booleskt värde `true` , deklarerar du egenskapen som [system. Management. Automation. SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) -typ och anger sedan standardvärdet för parametern till `false` .

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
