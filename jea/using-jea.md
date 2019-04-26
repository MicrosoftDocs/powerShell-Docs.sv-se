---
ms.date: 06/12/2017
keywords: jea, powershell, säkerhet
title: Använda JEA
ms.openlocfilehash: fa3d3a3c8bc0090ec9ad788585ec5df933134173
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084053"
---
# <a name="using-jea"></a>Använda JEA

> Gäller för: Windows PowerShell 5.0

Det här avsnittet beskrivs de olika sätt du kan ansluta till och använda en JEA-slutpunkt.

## <a name="using-jea-interactively"></a>Använda JEA interaktivt

Om du vill testa din JEA-konfiguration eller har enkla uppgifter för användare att utföra, kan du använda JEA på samma sätt som en vanlig PowerShell-session för fjärrkommunikation.
För komplexa fjärrkommunikation aktiviteter, rekommenderar vi att du använder [implicit fjärrkommunikation](#using-jea-with-implicit-remoting) i stället för att göra det enklare för användarna genom att tillåta användare att arbeta med data objekt lokalt.

Om du vill använda JEA interaktivt, behöver du:
- Namnet på den dator som du ansluter till (kan vara den lokala datorn)
- Namnet på JEA-slutpunkt som registrerats på datorn
- Autentiseringsuppgifter för datorn som har åtkomst till JEA-slutpunkt

Med den informationen till hands kan du starta en JEA-session med [New-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSSession) eller [Enter-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/enter-pssession).

```powershell
$nonAdminCred = Get-Credential
Enter-PSSession -ComputerName localhost -ConfigurationName JEAMaintenance -Credential $nonAdminCred
```

Om det konto som du är för närvarande inloggad som har åtkomst till JEA-slutpunkt, kan du utesluta den `-Credential` parametern.

När PowerShell frågar ändringar `[localhost]: PS>` vet du att du nu interagerar med JEA fjärrsessionen.
Du kan köra `Get-Command` att kontrollera vilka kommandon är tillgängliga.
Du måste kontakta administratören om du vill lära dig om det finns några begränsningar på tillgängliga parametrar eller tillåten parametervärden.

Som en påminnelse JEA-sessioner som arbetar i NoLanguage läge, så att några sätt som du använder vanligtvis PowerShell inte kanske tillgänglig.
Du kan inte exempelvis använda variabler för att lagra data eller kontrollera egenskaperna för objekt som returneras från cmdlet: ar.
Den nedan exempel visar ett exempel på hur du använder PowerShell idag och två metoder för att få samma kommando arbetar i NoLanguage läge.

```powershell
# Using variables in NoLanguage mode is disallowed, so the following will not work
# $vm = Get-VM -Name 'SQL01'
# Start-VM -VM $vm

# You can use pipes to pass data through to commands that accept input from the pipeline
Get-VM -Name 'SQL01' | Start-VM

# You can also wrap subcommands in parentheses and enter them inline as arguments
Start-VM -VM (Get-VM -Name 'SQL01')

# Better yet, use parameter sets that don't require extra data to be passed in when possible
Start-VM -VMName 'SQL01'
```

Överväg att använda för mer komplexa kommando-anrop som gör den här metoden svårt [implicit fjärrkommunikation](#using-jea-with-implicit-remoting) eller [skapa anpassade funktioner](role-capabilities.md#creating-custom-functions) som omsluter funktioner som du önskar.

## <a name="using-jea-with-implicit-remoting"></a>Använda JEA med implicit fjärrkommunikation

PowerShell har stöd för en annan fjärrkommunikation modell där du kan importera proxy-cmdlet: ar från en fjärrdator på den lokala datorn och interagerar med dem som om de vore lokala kommandon.
Detta kallas för implicit fjärrkommunikation och förklaras även i [detta *Hey, Scripting Guy!* blogginlägget](https://blogs.technet.microsoft.com/heyscriptingguy/2013/09/08/remoting-the-implicit-way/).
Implicit fjärrkommunikation är särskilt användbart när du arbetar med JEA eftersom den tillåter dig att arbeta med JEA-cmdletar i ett språkläge med fullständig.
Det innebär att du kan använda tabbifyllning, variabler, manipulera objekt och även använda lokala skript för att enkelt automatisera mot en JEA-slutpunkt.
Varje gång du anropar en proxy-kommandot data skickas till JEA-slutpunkt på fjärrdatorn och det körs.

Implicit fjärrkommunikation fungerar genom att importera cmdlet: ar från en befintlig PowerShell-session.
Du kan välja att prefixet substantiven för varje proxy-cmdlet med en sträng med valfritt att skilja på vilka kommandon är för fjärrsystemet.
En tillfällig skriptmodul som innehåller alla proxy kommandon kommer att skapas och kan användas för varaktigheten för din lokala PowerShell-session.

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Import the entire PSSession and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA'

# Invoke "Get-Command" on the remote JEA endpoint using the proxy cmdlet
Get-JEACommand
```

> [!IMPORTANT]
> Vissa system kanske inte att importera en hel JEA-session på grund av begränsningar i standard JEA-cmdlets.
> För att undvika detta, bara importera de kommandon som du behöver från JEA-sessionen genom att uttryckligen ange namnen till de `-CommandName` parametern.
> En kommande uppdatering kan lösa problemet med att importera hela JEA-sessioner på en dator.

Om det inte går att importera en JEA-session på grund av begränsningar i standardparametrarna för JEA kan följa du stegen nedan för att filtrera bort standardkommandona från importerade uppsättningen.
Du kommer fortfarande att kunna använda kommandon som `Select-Object` --du bara använder den lokala versionen som installerats på datorn i stället för den fjärranslutna i JEA-session.

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Get a list of all the commands on the JEA endpoint
$commands = Invoke-Command -Session $jeasession -ScriptBlock { Get-Command }

# Filter out the default cmdlets
$jeaDefaultCmdlets = 'Clear-Host', 'Exit-PSSession', 'Get-Command', 'Get-FormatData', 'Get-Help', 'Measure-Object', 'Out-Default', 'Select-Object'
$filteredCommands = $commands.Name | Where-Object { $jeaDefaultCmdlets -notcontains $_ }

# Import only commands explicitly added in role capabilities and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA' -CommandName $filteredCommands
```

Du kan också spara via proxy-cmdletar från implicit fjärrkommunikation med [Export-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/Export-PSSession).
Mer information om implicit fjärrkommunikation finns i hjälpen [Import-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/import-pssession) och [Import-Module](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/import-module).

## <a name="using-jea-programmatically"></a>Använda JEA programmässigt

JEA kan också användas i automatiseringssystem och användarprogram, till exempel interna supportavdelningen appar och webbplatser.
Metoden som är detsamma som för att skapa appar som kommunicerar med obegränsad PowerShell-slutpunkter, med villkor för att programmet ska vara medveten om att JEA begränsar de kommandon som kan köras i fjärrsessionen.

Du kan använda enkla, oneoff aktivitetsinformation, [Invoke-Command](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/invoke-command) att köra en uppsättning kommandon med hjälp av JEA.

```powershell
Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Process; Get-Service }
```

Du kan kontrollera vilka kommandon är tillgängliga för användning när du ansluter till en JEA-session genom att köra `Get-Command` och gå igenom de resultat att söka efter de tillåtna parametrarna.

```powershell
$allowedCommands = Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Command }
$allowedCommands | Where-Object { $_.CommandType -in 'Function', 'Cmdlet' } | Format-Table Name, Parameters
```

Om du skapar en C# app, kan du skapa ett PowerShell-körningsutrymme som ansluter till en JEA-session genom att ange konfigurationsnamnet i en [WSManConnectionInfo](https://msdn.microsoft.com/library/system.management.automation.runspaces.wsmanconnectioninfo(v=vs.85).aspx) objekt.

```csharp
// using System.Management.Automation;
var computerName = "SERVER01";
var configName   = "JEAMaintenance";
var creds        = // create a PSCredential object here (https://msdn.microsoft.com/library/system.management.automation.pscredential(v=vs.85).aspx)

WSManConnectionInfo connectionInfo = new WSManConnectionInfo(
                    false,                 // Use SSL
                    computerName,          // Computer name
                    5985,                  // WSMan Port
                    "/wsman",              // WSMan Path
                    string.Format(CultureInfo.InvariantCulture, "http://schemas.microsoft.com/powershell/{0}", configName),  // Connection URI with config name
                    creds);                // Credentials
// Now, use the connection info to create a runspace where you can run the commands
using (Runspace runspace = RunspaceFactory.CreateRunspace(connectionInfo))
{
    // Open the runspace
    runspace.Open();

    using (PowerShell ps = PowerShell.Create())
    {
        // Set the PowerShell object to use the JEA runspace
        ps.Runspace = runspace;

        // Now you can add and invoke commands
        ps.AddCommand("Get-Command");
        foreach (var result in ps.Invoke())
        {
            Console.WriteLine(result);
        }
    }

    // Close the runspace
    runspace.Close();
}
```

## <a name="using-jea-with-powershell-direct"></a>Använda JEA med PowerShell direkt

Hyper-V i Windows 10 och Windows Server 2016 erbjuder [PowerShell Direct](https://msdn.microsoft.com/virtualization/hyperv_on_windows/user_guide/vmsession), en funktion som gör att Hyper-V-administratörer att hantera virtuella datorer med PowerShell oavsett nätverkskonfiguration eller fjärrhantering inställningarna på den virtuella datorn.

Du kan använda PowerShell Direct med JEA för att ge en Hyper-V begränsad administratörsåtkomst till den virtuella datorn, vilket kan vara användbart om du förlorar nätverksanslutningen till den virtuella datorn och behöver en datacenter-administratör att åtgärda nätverksinställningarna.

Ingen ytterligare konfiguration krävs för att använda JEA via PowerShell Direct, men det operativsystem som körs på den virtuella datorn måste vara Windows 10 eller Windows Server 2016.
Hyper-V-administratören kan ansluta till JEA-slutpunkt med hjälp av den `-VMName` eller `-VMId` parametrar om PSRemoting-cmdletar:

```powershell
# Entering a JEA session using PowerShell Direct when the VM name is unique
Enter-PSSession -VMName 'SQL01' -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'

# Entering a JEA session using PowerShell Direct using VM ids
$vm = Get-VM -VMName 'MyVM' | Select-Object -First 1
Enter-PSSession -VMId $vm.VMId -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'
```

Vi rekommenderar starkt att du skapar en dedikerad lokal användare med inga andra rättigheter att hantera system för dina Hyper-V-administratörer använder.
Kom ihåg att även en icke-privilegierade användare kan fortfarande logga in på en Windows-dator som standard, inklusive med obegränsad PowerShell.
Som så att de kan bläddra (del av) filsystemet och lär dig mer om din OS-miljö.
För att låsa en Hyper-V-administratör för att bara åtkomst till en virtuell dator med PowerShell Direct med JEA kommer du behöva Neka lokal inloggningsrättigheter till Hyper-V-administratörens JEA-konto.
