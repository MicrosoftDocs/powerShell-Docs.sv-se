---
title: Typer av Cmdlet-parametrarna | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6602730d-3892-4656-80c7-7bca2d14337f
caps.latest.revision: 14
ms.openlocfilehash: f5781c0c03aca41d01a44598a9a8c00d6d21d2fd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067203"
---
# <a name="types-of-cmdlet-parameters"></a>Typer av cmdlet-parametrar

Det här avsnittet beskrivs de olika typerna av parametrar som du kan deklarera i cmdlet: ar. Cmdlet-parametrarna kan vara namngivna, namngivna, obligatorisk, valfri eller växla parametrar.

## <a name="positional-and-named-parameters"></a>Namngivna och namngivna parametrar

Alla cmdlet-parametrarna är namngivna eller namngivna parametrar. En namngiven parameter uppmanas att ange parameternamnet och argumentet när du anropar cmdleten. Namngivna parametern kräver endast att du skriver argumenten i relativa ordning. Systemet mappar sedan det första argumentet för Namnlös till den första namngivna parametern. Systemet mappar det andra argumentet för Namnlös till andra icke namngivna parametern och så vidare. Som standard är alla cmdlet-parametrarna namngivna parametrar.

För att definiera en namngiven parameter, utelämnar den `Position` nyckelord i den **parametern** attributet deklarationen enligt följande parameterdeklaration.

```csharp
[Parameter(ValueFromPipeline=true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

För att definiera en namngivna parametern, lägger du till den `Position` nyckelord i parametern attributet deklarationen och ange sedan en plats. I följande exempel och den `UserName` parametern deklareras som en namngivna parametern med position 0. Det innebär att det första argumentet för anropet automatiskt kommer att bindas till den här parametern.

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
> Cmdlet: en bra design rekommenderas att de mest använda parametrarna deklareras som positionsparametrar så att användaren inte behöver ange parameternamnet när cmdleten körs.

Namngivna och namngivna parametrar godkänner enda argument eller flera argument avgränsade med kommatecken. Flera argument tillåts endast om parametern accepterar en samling, till exempel en matris med strängar. Du kan blanda namngivna och namngivna parametrar i samma cmdlet. I det här fallet systemet hämtar namngivna argument först och sedan försöker mappa de återstående icke namngivna argument till de namngivna parametrarna.

Kommandona i följande visar olika sätt som du kan ange enstaka eller flera argument för parametrarna för den `Get-Command` cmdlet. Observera att i de två senaste samplingarna **-namnet** behöver inte anges eftersom den `Name` parametern har definierats som en namngivna parametern.

```powershell
Get-Command -Name get-service
Get-Command -Name get-service,set-service
Get-Command get-service
Get-Command get-service,set-service
```

## <a name="mandatory-and-optional-parameters"></a>Obligatoriska och valfria parametrar

Du kan också definiera parametrar för cmdleten som obligatoriska eller valfria parametrar. (En obligatorisk parameter måste anges innan Windows PowerShell-runtime anropar cmdlet: en.)  Som standard definieras parametrar som valfria.

För att definiera en obligatorisk parameter, lägger du till den `Mandatory` nyckelord i parametern attributet deklarationen och ange den till `true`, enligt följande parameterdeklaration.

```csharp
[Parameter(Position = 0, Mandatory = true)]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

För att definiera en valfri parameter, utelämnar den `Mandatory` nyckelord i den **parametern** attributet deklarationen enligt följande parameterdeklaration.

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

Windows PowerShell tillhandahåller en [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) typ som kan du definiera en parameter vars värde ställs automatiskt in `false` om parametern inte anges när cmdlet anropas. När det är möjligt använda växeln parametrar i stället för booleska parametrar.

Överväg följande exempel. Som standard skickar inte ett utdataobjekt av pipelinen i flera Windows PowerShell-cmdletar. Dessa cmdletar har dock en `PassThru` växla parametern som åsidosätter standardbeteendet. Om den `PassThru` parametern anges när dessa cmdletar kallas, cmdleten returnerar ett utdataobjekt till pipelinen.

Om du behöver ha ett standardvärde för parametern `true` om parametern inte anges i anropet du överväga att byta plats uppfattning parametern. För exemplet, i stället för ett booleskt värde för att ställa in parameterattributet `true`, deklarera egenskapen som den [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) skriver och sedan ange standardvärdet för parametern ska `false`.

Om du vill definiera en växlingsparametern deklarera egenskapen som den [System.Management.Automation.SwitchParameter](/dotnet/api/System.Management.Automation.SwitchParameter) skriver, enligt följande exempel.

```csharp
[Parameter(Position = 1)]
public SwitchParameter GoodBye
{
  get { return goodbye; }
  set { goodbye = value; }
}
private bool goodbye;
```

Använd följande struktur inom någon av metoderna indata för att göra cmdleten agera på parametern när det har angetts.

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

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
