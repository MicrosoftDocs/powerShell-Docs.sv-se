---
title: Snabb start för Windows PowerShell-värd | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5a134b81-bd0c-4e1c-a2f0-9acbe852745a
caps.latest.revision: 9
ms.openlocfilehash: 390eb2d0153c65967d8c0711c852aa6e13fe4660
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72352992"
---
# <a name="windows-powershell-host-quickstart"></a>Snabbstart för Windows PowerShell-värd

För att vara värd för Windows PowerShell i ditt program använder du klassen [system. Management. Automation. PowerShell](/dotnet/api/System.Management.Automation.PowerShell) .
Den här klassen innehåller metoder som skapar en pipeline med kommandon och sedan kör dessa kommandon i en körnings utrymme.
Det enklaste sättet att skapa ett värd program är att använda standard körnings utrymme.
Standard-körnings utrymme innehåller alla Windows PowerShell-kommandon i kärnan.
Om du vill att programmet endast ska exponera en delmängd av Windows PowerShell-kommandon måste du skapa en anpassad körnings utrymme.

## <a name="using-the-default-runspace"></a>Använda standard körnings utrymme

För att starta ska vi använda standard-körnings utrymme och använda metoderna i klassen [system. Management. Automation. PowerShell](/dotnet/api/System.Management.Automation.PowerShell) för att lägga till kommandon, parametrar, instruktioner och skript i en pipeline.

### <a name="addcommand"></a>AddCommand

Du använder metoden [system. Management. Automation. PowerShell. AddCommand](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) för att lägga till kommandon i pipelinen.
Anta till exempel att du vill hämta en lista över processer som körs på datorn.
Du kan köra det här kommandot på följande sätt.

1. Skapa ett [system. Management. Automation. PowerShell](/dotnet/api/System.Management.Automation.PowerShell) -objekt.

   ```csharp
   PowerShell ps = PowerShell.Create();
   ```

2. Lägg till kommandot som du vill köra.

   ```csharp
   ps.AddCommand("Get-Process");
   ```

3. Anropa kommandot.

   ```csharp
   ps.Invoke();
   ```

Om du anropar AddCommand-metoden mer än en gång innan du anropar metoden [system. Management. Automation. PowerShell. Invoke](/dotnet/api/System.Management.Automation.PowerShell.Invoke) , är resultatet av det första kommandot skickas till det andra, och så vidare.
Om du inte vill skicka vidare resultatet av ett tidigare kommando till ett kommando, lägger du till det genom att anropa [system. Management. Automation. PowerShell. AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) i stället.

### <a name="addparameter"></a>AddParameter

I föregående exempel körs ett enda kommando utan några parametrar.
Du kan lägga till parametrar till kommandot med hjälp av metoden [system. Management. Automation. PSCommand. AddParameter](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) .
Följande kod hämtar till exempel en lista över alla processer som heter `PowerShell` körs på datorn.

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

Du kan lägga till ytterligare parametrar genom att anropa metoden AddParameter upprepade gånger.

```csharp                   
PowerShell.Create().AddCommand("Get-ChildItem")
                   .AddParameter("Path", @"c:\Windows")
                   .AddParameter("Filter", "*.exe")
                   .Invoke();
```

Du kan också lägga till en ord lista med parameter namn och värden genom att anropa metoden [system. Management. Automation. PowerShell. AddParameters](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) .

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Path", @"c:\Windows");
parameters.Add("Filter", "*.exe");

PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a>AddStatement

Du kan simulera batching med hjälp av metoden [system. Management. Automation. PowerShell. AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) , som lägger till ytterligare en instruktion i slutet av pipelinen.
Följande kod hämtar en lista över processer som körs med namnet `PowerShell`och hämtar sedan listan över tjänster som körs.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a>AddScript

Du kan köra ett befintligt skript genom att anropa metoden [system. Management. Automation. PowerShell. AddScript](/dotnet/api/System.Management.Automation.PowerShell.AddScript) .
I följande exempel läggs ett skript till i pipelinen och körs.
Det här exemplet förutsätter att det redan finns ett skript med namnet `MyScript.ps1` i en mapp med namnet `D:\PSScripts`.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

Det finns också en version av AddScript-metoden som tar en boolesk parameter med namnet `useLocalScope`.
Om den här parametern är inställd på `true`körs skriptet i det lokala omfånget.
Följande kod kommer att köra skriptet i det lokala omfånget.

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

## <a name="creating-a-custom-runspace"></a>Skapa en anpassad körnings utrymme

Även om standard-körnings utrymme som används i föregående exempel läser in alla viktiga Windows PowerShell-kommandon, kan du skapa en anpassad körnings utrymme som endast läser in en viss delmängd av alla kommandon.
Du kanske vill göra detta för att förbättra prestandan (att läsa in ett stort antal kommandon är en prestanda träff) eller att begränsa möjligheten för användaren att utföra åtgärder.
En körnings utrymme som visar bara ett begränsat antal kommandon kallas för en begränsad körnings utrymme.
Om du vill skapa en begränsad körnings utrymme använder du klasserna [system. Management. Automation. körnings utrymmen. körnings utrymme](/dotnet/api/System.Management.Automation.Runspaces.Runspace) och [system. Management. Automation. körnings utrymmen. InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) .

### <a name="creating-an-initialsessionstate-object"></a>Skapa ett InitialSessionState-objekt

Om du vill skapa en anpassad körnings utrymme måste du först skapa ett [system. Management. Automation. körnings utrymmen. InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -objekt.
I följande exempel använder vi [system. Management. Automation. körnings utrymmen. RunspaceFactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) för att skapa en körnings utrymme när du har skapat ett standard InitialSessionState-objekt.

```csharp
InitialSessionState iss = InitialSessionState.CreateDefault();
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
PowerShell ps = PowerShell.Create();
ps.Runspace = rs;
ps.AddCommand("Get-Command");
ps.Invoke();
```

### <a name="constraining-the-runspace"></a>Begränsa körnings utrymme

I föregående exempel skapade vi ett standard [system. Management. Automation. körnings utrymmen. InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -objekt som läser in alla inbyggda kärnor i Windows PowerShell.
Vi kan också ha anropat metoden [system. Management. Automation. körnings utrymmen. InitialSessionState. CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) för att skapa ett InitialSessionState-objekt som endast läser in kommandona i snapin-modulen Microsoft. PowerShell. Core.
Om du vill skapa en mer begränsad körnings utrymme måste du skapa ett tomt InitialSessionState-objekt genom att anropa metoden [system. Management. Automation. körnings utrymmen. InitialSessionState. Create](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) och sedan lägga till kommandon i InitialSessionState.

Om du använder en körnings utrymme som bara läser in de kommandon som du anger får du avsevärt bättre prestanda.

Du kan använda metoderna i klassen [system. Management. Automation. körnings utrymmen. SessionStateCmdletEntry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) för att definiera cmdletar för det första sessionstillståndet.
I följande exempel skapas ett tomt tillstånd för inledande session och sedan definieras och läggs till `Get-Command` och `Import-Module` kommandon i det första sessionstillståndet.
Vi skapar sedan en körnings utrymme som är begränsad av det första sessionstillståndet och kör kommandona i den körnings utrymme.

Skapa det första sessionstillståndet.

```csharp
InitialSessionState iss = InitialSessionState.Create();
```

Definiera och Lägg till kommandon i det första sessionstillståndet.

```csharp
SessionStateCmdletEntry getCommand = new SessionStateCmdletEntry(
        "Get-Command", typeof(Microsoft.PowerShell.Commands.GetCommandCommand), "");
SessionStateCmdletEntry importModule = new SessionStateCmdletEntry(
        "Import-Module", typeof(Microsoft.PowerShell.Commands.ImportModuleCommand), "");
iss.Commands.Add(getCommand);
iss.Commands.Add(importModule);
```

Skapa och öppna körnings utrymme.

```csharp
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
```

Kör ett kommando och visa resultatet.

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

När det körs kommer utdata från den här koden att se ut så här.

```powershell
Get-Command
Import-Module
```
