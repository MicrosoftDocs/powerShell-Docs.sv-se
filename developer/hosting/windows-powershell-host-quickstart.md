---
title: Snabbstart för Windows PowerShell-värd | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5a134b81-bd0c-4e1c-a2f0-9acbe852745a
caps.latest.revision: 9
ms.openlocfilehash: cc014487a680747ad59437052f79d4576154a1cb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082557"
---
# <a name="windows-powershell-host-quickstart"></a>Snabbstart för Windows PowerShell-värd

Om du vill vara värd för Windows PowerShell i ditt program, som du använder den [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) klass. Den här klassen innehåller metoder som skapar en pipeline med kommandon och sedan köra dessa kommandon i ett körningsutrymme. Det enklaste sättet att skapa ett program är att använda standard-körningsutrymmet. Standard-körningsutrymme innehåller alla core Windows PowerShell-kommandon. Om du vill att programmet att exponera en delmängd av Windows PowerShell-kommandon, måste du skapa en anpassad körningsutrymme.

## <a name="using-the-default-runspace"></a>Med hjälp av standard-körningsutrymmet

Om du vill starta, vi använda standard-körningsutrymme och använda metoderna i den [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) klassen för att lägga till kommandon, parametrar, instruktioner och skript i en pipeline.

### <a name="addcommand"></a>AddCommand

Du använder den [System.Management.Automation.Powershell.AddCommand*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) -metoden för den [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) klassen för att lägga till kommandon i pipelinen. Anta exempelvis att du vill hämta en lista över processer som körs på datorn. Sättet att köra det här kommandot är som följer.

1. Skapa en [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) objekt.

   ```csharp
   PowerShell ps = PowerShell.Create();
   ```

2. Lägg till det kommando som du vill köra.

   ```csharp
   ps.AddCommand("Get-Process");
   ```

3. Anropa kommandot.

   ```csharp
   ps.Invoke();
   ```

Om du anropar den [System.Management.Automation.Powershell.AddCommand*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) metod som är mer än en gång innan du anropar den [System.Management.Automation.Powershell.Invoke*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) metod, resultatet av den första kommandot skickas till andra och så vidare. Om du inte vill skicka resultatet av en föregående kommando för att ett kommando lägger du till den genom att anropa den [System.Management.Automation.Powershell.AddStatement*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) i stället.

### <a name="addparameter"></a>AddParameter

Föregående exempel körs ett enda kommando utan några parametrar. Du kan lägga till parametrar i kommandot med hjälp av den [System.Management.Automation.PSCommand.AddParameter*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) metod till exempel följande kod hämtar en lista över alla processer som namnges `PowerShell` som körs på den datorn.

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

Du kan lägga till ytterligare parametrar genom att anropa [System.Management.Automation.PSCommand.AddParameter*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) upprepade gånger.

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .AddParameter("Id", "12768")
                   .Invoke();
```

Du kan också lägga till en ordlista över parameternamn och värden som genom att anropa den [System.Management.Automation.PowerShell.AddParameters*](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) metod.

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Name", "PowerShell");

parameters.Add("Id", "12768");
PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a>AddStatement

Du kan simulera batchbearbetning med hjälp av den [System.Management.Automation.PowerShell.AddStatement*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) metod, som lägger till en ytterligare instruktion i slutet av din pipeline för följande kod hämtar en lista över processer som körs med namnet `PowerShell`, och sedan hämtar listan över aktiva tjänster.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a>AddScript

Du kan köra ett befintligt skript genom att anropa den [System.Management.Automation.PowerShell.AddScript*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) metod. I följande exempel lägger till ett skript till pipelinen och kör den. Det här exemplet förutsätter att det finns redan ett skript som heter `MyScript.ps1` i en mapp med namnet `D:\PSScripts`.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

Det finns också en version av den [System.Management.Automation.PowerShell.AddScript*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) metod som tar en boolesk parameter som heter `useLocalScope`. Om den här parametern anges till `true`, och sedan skriptet körs i det lokala scopet. Följande kod körs skriptet i det lokala scopet.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

## <a name="creating-a-custom-runspace"></a>Skapa en anpassad körningsutrymme

Du kan skapa ett anpassat körningsutrymme som läser in endast en delmängd av alla kommandon som angivna medan standard-körningsutrymmet som används i föregående exempel har lästs in alla core Windows PowerShell-kommandon. Du kanske vill göra detta för att förbättra prestanda (läser in fler kommandon är en träff prestanda), eller för att begränsa möjligheterna för användaren att utföra åtgärder. Ett körningsutrymme som exponerar endast ett begränsat antal kommandon kallas för ett begränsat körningsutrymme. Om du vill skapa ett begränsat körningsutrymme som du använder den [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) och [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) klasser.

### <a name="creating-an-initialsessionstate-object"></a>Skapa ett InitialSessionState-objekt

Om du vill skapa en anpassad körningsutrymme, måste du först skapa en [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objekt. I följande exempel använder vi den [System.Management.Automation.Runspaces.RunspaceFactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) att skapa ett körningsutrymme när du har skapat en standard [System.Management.Automation.Runspaces.InitialSessionState ](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objekt.

```csharp
InitialSessionState iss = InitialSessionState.CreateDefault();
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
PowerShell ps = PowerShell.Create();
ps.Runspace = rs;
ps.AddCommand("Get-Command");
ps.Invoke();
```

### <a name="constraining-the-runspace"></a>Begränsa körningsutrymmet

I exemplet ovan skapade vi en standard [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objekt som läser in alla av de inbyggda grundläggande Windows PowerShell. Vi också har anropat den [System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) metod för att skapa ett InitialSessionState-objekt som skulle läsa in kommandona i Microsoft.PowerShell.Core snapin-modulen. Om du vill skapa en mer begränsad körningsutrymme, måste du skapa en tom [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) objekt genom att anropa den [ System.Management.Automation.Runspaces.InitialSessionState.Create*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) metoden och lägger sedan till kommandon i InitialSessionState.

Med hjälp av ett körningsutrymme som läser in endast de kommandon som du anger ger betydligt bättre prestanda.

Du använder metoderna i den [System.Management.Automation.Runspaces.SessionStateCmdletEntry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) klassen för att definiera-cmdletar för inledande sessionens tillstånd. I följande exempel skapar en tom inledande sessionstillstånd, och sedan definierar och lägger till den `Get-Command` och `Import-Module` kommandon för att det inledande sessionstillståndet. Vi sedan skapa ett körningsutrymme begränsas av den första sessionstillstånd och kör kommandon i den körningsutrymme.

Skapa det första sessionstillståndet.

```csharp
InitialSessionState iss = InitialSessionState.Create();
```

Definiera och Lägg till kommandon till det första sessionstillståndet.

```csharp
SessionStateCmdletEntry getCommand = new SessionStateCmdletEntry(
        "Get-Command", typeof(Microsoft.PowerShell.Commands.GetCommandCommand), "");
SessionStateCmdletEntry importModule = new SessionStateCmdletEntry(
        "Import-Module", typeof(Microsoft.PowerShell.Commands.ImportModuleCommand), "");
iss.Commands.Add(getCommand);
iss.Commands.Add(importModule);
```

Skapa och öppna körningsutrymmet.

```csharp
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
```

Köra ett kommando och visa resultatet.

```csharp
PowerShell ps = PowerShell.Create();
ps.Runspace = rs;
ps.AddCommand("Get-Command");
Collection<CommandInfo> result = ps.Invoke<CommandInfo>();
foreach (var entry in result)
{
       Console.WriteLine(entry.Name);
}
```

När du kör, resultatet av den här koden ska se ut så här.

```powershell
Get-Command
Import-Module
```
