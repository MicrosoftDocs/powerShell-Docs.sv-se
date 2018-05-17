---
ms.date: 06/12/2017
keywords: jea powershell säkerhet
title: Använda JEA
ms.openlocfilehash: 891e4be4c3fadceeff5ede7ac5cab04a5f80e5c1
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/16/2018
---
# <a name="using-jea"></a>Använda JEA

> Gäller för: Windows PowerShell 5.0

Det här avsnittet beskrivs de olika sätt som du kan ansluta till och använda en JEA slutpunkt.

## <a name="using-jea-interactively"></a>Använda JEA interaktivt

Om du vill testa konfigurationen JEA eller har enkla uppgifter för användare att utföra kan du använda JEA på samma sätt som en vanlig PowerShell-session för fjärrkommunikation.
För komplexa fjärrkommunikation aktiviteter, rekommenderas att använda [implicit fjärrkommunikation](#using-jea-with-implicit-remoting) i stället för att göra det enklare för användarna genom att tillåta användare att arbeta med data objekt lokalt.

Om du vill använda JEA interaktivt, behöver du:
- Namnet på den dator som du ansluter till (kan vara den lokala datorn)
- Namnet på slutpunkten JEA registrerad på datorn
- Autentiseringsuppgifter för datorn som har åtkomst till JEA slutpunkten

Med informationen i manuellt, kan du starta en JEA sessionen med hjälp av [New-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSSession) eller [Enter-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/enter-pssession).

```powershell
$nonAdminCred = Get-Credential
Enter-PSSession -ComputerName localhost -ConfigurationName JEAMaintenance -Credential $nonAdminCred
```

Om det konto som du är för närvarande inloggad som har åtkomst till JEA slutpunkten kan du utelämna den `-Credential` parameter.

När PowerShell fråga ändringar `[localhost]: PS>` vet du att du nu interagerar med JEA fjärrsessionen.
Du kan köra `Get-Command` att kontrollera vilka kommandon som är tillgängliga.
Du måste kontakta din administratör om du vill veta om det finns några begränsningar på tillgängliga parametrar eller tillåtna parametervärden.

Som en påminnelse drivas JEA sessioner i NoLanguage läge, så att några av de sätt som du vanligtvis använder PowerShell inte kanske tillgänglig.
Du kan inte exempelvis använda variabler för att lagra data eller kontrollera egenskaperna för objekt som returnerades från cmdlets.
Den nedan exempel visas ett exempel på hur du kan använda PowerShell idag och två sätt att få samma kommando arbetar i NoLanguage läge.

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

## <a name="using-jea-with-implicit-remoting"></a>JEA med implicit fjärrkommunikation

PowerShell stöder ett alternativt fjärrkommunikation modell där du kan importera cmdlet: ar från en fjärrdator på den lokala datorn och interagera med dem som om de vore lokala kommandon.
Detta kallas för implicit fjärrkommunikation och beskrivs också i [detta *artikel från Hey, Scripting Guy!* blogginlägget](https://blogs.technet.microsoft.com/heyscriptingguy/2013/09/08/remoting-the-implicit-way/).
Implicit fjärrkommunikation är särskilt användbar när du arbetar med JEA eftersom du kan arbeta med JEA cmdlets i ett läge för fullständig språk.
Det innebär att du kan använda flikavslutande, variabler, ändra objekt och även använda lokala skript för att lättare för att automatisera mot en JEA slutpunkt.
När du anropar en proxy-kommandot skickas till slutpunkten JEA på fjärrdatorn data och utförs där.

Implicit fjärrkommunikation fungerar genom att importera cmdlet: ar från en befintlig PowerShell-session.
Du kan välja att prefixet substantiven för varje proxy-cmdlet med en sträng som du väljer att skilja vilka kommandon som för fjärrsystemet.
En tillfällig skriptmodul som innehåller alla kommandon som proxy skapas och kan användas för hela din lokala PowerShell-session.

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Import the entire PSSession and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA'

# Invoke "Get-Command" on the remote JEA endpoint using the proxy cmdlet
Get-JEACommand
```

> [!IMPORTANT]
> Vissa datorer kan inte importera en hel JEA-session på grund av begränsningar i standard JEA-cmdlets.
> För att komma runt detta Importera endast de kommandon som krävs från JEA-session genom att explicit ange namnen på de `-CommandName` parameter.
> En framtida uppdatering kan lösa problemet med att importera hela JEA sessioner på en dator.

Om det inte går att importera en JEA session på grund av begränsningar i standardparametrarna för JEA kan följa du stegen nedan för att filtrera bort standard kommandon från den importera uppsättningen.
Du kommer fortfarande att kunna använda kommandon som `Select-Object` --ska du bara använda den lokala versionen installerad på datorn i stället för det fjärranslutna i JEA-sessionen.

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

Du kan också spara via proxy cmdlets från implicit fjärrkommunikation med [Export-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/Export-PSSession).
Ta en titt i hjälpen för mer information om implicit fjärrkommunikation [Import-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/import-pssession) och [Import-Module](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/import-module).

## <a name="using-jea-programatically"></a>Med hjälp av JEA genom att programmera

JEA kan också användas i automatiseringssystem och program, till exempel interna supportavdelningen appar och webbplatser.
Metoden är densamma som för att skapa appar som kommunicerar med obegränsad PowerShell slutpunkter med den begränsning att programmet ska vara medveten om att JEA är att begränsa de kommandon som kan köras i fjärrsessionen.

Du kan använda för enkla, oneoff uppgifter [Invoke-Command](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/invoke-command) att köra en uppsättning kommandon med hjälp av JEA.

```powershell
Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Process; Get-Service }
```

Om du vill kontrollera vilka kommandon som är tillgängliga för användning när du ansluter till en session JEA kör `Get-Command` och gå igenom de resultat som ska eftersökas tillåtna parametrar.

```powershell
$allowedCommands = Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Command }
$allowedCommands | Where-Object { $_.CommandType -in 'Function', 'Cmdlet' } | Format-Table Name, Parameters
```

Om du skapar en C#-app, kan du skapa ett PowerShell-körningsutrymme som ansluter till en JEA-session genom att ange konfigurationsnamnet i en [WSManConnectionInfo](https://msdn.microsoft.com/en-us/library/system.management.automation.runspaces.wsmanconnectioninfo(v=vs.85).aspx) objekt.

```csharp

// using System.Management.Automation;
var computerName = "SERVER01";
var configName   = "JEAMaintenance";
var creds        = // create a PSCredential object here (https://msdn.microsoft.com/en-us/library/system.management.automation.pscredential(v=vs.85).aspx)

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

## <a name="using-jea-with-powershell-direct"></a>Med PowerShell Direct JEA

Hyper-V i Windows 10 och Windows Server 2016 erbjuder [PowerShell Direct](https://msdn.microsoft.com/en-us/virtualization/hyperv_on_windows/user_guide/vmsession), en funktion som gör att Hyper-V-administratörer att hantera virtuella datorer med PowerShell oavsett nätverkskonfiguration eller fjärrhantering inställningarna på den virtuella datorn.

Du kan använda PowerShell direkt med JEA för att ge en Hyper-V begränsad administratörsåtkomst till den virtuella datorn, vilket kan vara användbart om du förlorar nätverksanslutningen till den virtuella datorn och behöver en datacenter-administratör att åtgärda nätverksinställningarna.

Ingen ytterligare konfiguration krävs för att använda JEA via PowerShell direkt, men operativsystemet som körs på den virtuella datorn måste vara Windows 10 eller Windows Server 2016.
Hyper-V-administratör kan ansluta till JEA slutpunkten med hjälp av den `-VMName` eller `-VMId` för PSRemoting-cmdlets:

```powershell
# Entering a JEA session using PowerShell Direct when the VM name is unique
Enter-PSSession -VMName 'SQL01' -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'

# Entering a JEA session using PowerShell Direct using VM ids
$vm = Get-VM -VMName 'MyVM' | Select-Object -First 1
Enter-PSSession -VMId $vm.VMId -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'
```

Det rekommenderas starkt att du skapar en dedikerad lokal användare med ingen behörighet att hantera system för Hyper-V-administratörer använder.
Kom ihåg att även en icke-privilegierade användare kan fortfarande logga in på en Windows-dator som standard med obegränsad PowerShell.
Som gör att de kan bläddra (del av) filsystemet och lär dig mer om OS-miljön.
Om du vill låsa en Hyper-V-administratör att endast få åtkomst till en virtuell dator med hjälp av PowerShell direkt med JEA behöver du neka lokal inloggningsrättigheter till Hyper-V-administratörens JEA konto.