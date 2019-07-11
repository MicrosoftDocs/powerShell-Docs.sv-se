---
ms.date: 07/10/2019
keywords: jea, powershell, säkerhet
title: Använda JEA
ms.openlocfilehash: 8f3cc9186c61a2ae5b64eb3dc4f72ca83f1a58c5
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734219"
---
# <a name="using-jea"></a>Använda JEA

Den här artikeln beskrivs de olika sätt du kan ansluta till och använda en JEA-slutpunkt.

## <a name="using-jea-interactively"></a>Använda JEA interaktivt

Om du testar din JEA-konfiguration eller har enkla uppgifter för användare, kan du använda JEA på samma sätt som en vanlig PowerShell-session för fjärrkommunikation. För komplexa fjärrkommunikation aktiviteter, rekommenderar vi för att använda [implicit fjärrkommunikation](#using-jea-with-implicit-remoting). Implicit fjärrkommunikation tillåter användare att arbeta med dataobjekt lokalt.

Om du vill använda JEA interaktivt, behöver du:

- Namnet på den dator som du ansluter till (kan vara den lokala datorn)
- Namnet på JEA-slutpunkt som registrerats på datorn
- Autentiseringsuppgifter som har åtkomst till JEA-slutpunkt på datorn

Med den här informationen kan du starta en JEA-session med den [New-PSSession](/powershell/module/microsoft.powershell.core/New-PSSession) eller [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) cmdletar.

```powershell
$nonAdminCred = Get-Credential
Enter-PSSession -ComputerName localhost -ConfigurationName JEAMaintenance -Credential $nonAdminCred
```

Om det aktuella användarkontot har åtkomst till JEA-slutpunkt, kan du utesluta den **Credential** parametern.

När PowerShell frågar ändringar `[localhost]: PS>` du vet att du nu interagerar med JEA fjärrsessionen. Du kan köra `Get-Command` att kontrollera vilka kommandon är tillgängliga. Kontakta administratören om du vill lära dig om det finns några begränsningar på tillgängliga parametrar eller tillåtna parametervärden.

Kom ihåg att JEA-sessioner som arbetar i NoLanguage läge. Exempel på hur du använder vanligtvis PowerShell kanske inte tillgänglig. Du kan inte exempelvis använda variabler för att lagra data eller kontrollera egenskaperna för objekt som returneras från cmdlet: ar. I följande exempel visas två metoder för att få samma kommandon för att arbeta i NoLanguage läge.

```powershell
# Using variables is prohibited in NoLanguage mode. The following will not work:
# $vm = Get-VM -Name 'SQL01'
# Start-VM -VM $vm

# You can use pipes to pass data through to commands that accept input from the pipeline
Get-VM -Name 'SQL01' | Start-VM

# You can also wrap subcommands in parentheses and enter them inline as arguments
Start-VM -VM (Get-VM -Name 'SQL01')

# You can also use parameter sets that don't require extra data to be passed in
Start-VM -VMName 'SQL01'
```

Överväg att använda för mer komplexa kommando-anrop som gör den här metoden svårt [implicit fjärrkommunikation](#using-jea-with-implicit-remoting) eller [skapa anpassade funktioner](role-capabilities.md#creating-custom-functions) som omsluter vilka funktioner du behöver.

## <a name="using-jea-with-implicit-remoting"></a>Använda JEA med implicit fjärrkommunikation

PowerShell har en modell för implicit fjärrkommunikation som kan du importera proxy-cmdlet: ar från en fjärrdator och interagera med dem som om de vore lokala kommandon. Implicit fjärrkommunikation förklaras i det här **Hey, Scripting Guy!** [blogginlägget](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/).
Implicit fjärrkommunikation är användbart när du arbetar med JEA eftersom den tillåter dig att arbeta med JEA-cmdletar i ett språkläge med fullständig. Du kan använda tabbifyllning, variabler, manipulera objekt och även använda lokala skript för att automatisera åtgärder mot en JEA-slutpunkt. Varje gång du anropar en proxy-kommandot data skickas till JEA-slutpunkt på fjärrdatorn och det körs.

Implicit fjärrkommunikation fungerar genom att importera cmdlet: ar från en befintlig PowerShell-session. Du kan välja att prefixet substantiven för varje proxy-cmdlet med en sträng med valfritt. Prefixet kan du skilja kommandon som är för fjärrsystemet. En tillfällig skriptmodul som innehåller alla proxy kommandon skapas och importeras för varaktigheten för din lokala PowerShell-session.

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Import the entire PSSession and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA'

# Invoke "Get-Command" on the remote JEA endpoint using the proxy cmdlet
Get-JEACommand
```

> [!IMPORTANT]
> Vissa system kanske inte att importera en hel JEA-session på grund av begränsningar i standard JEA-cmdlets. För att undvika detta, bara importera de kommandon som du behöver från JEA-sessionen genom att uttryckligen ange namnen till de `-CommandName` parametern. En kommande uppdatering kan lösa problemet med att importera hela JEA-sessioner på en dator.

Om det inte går att importera en JEA-session på grund av begränsningar av JEA i standardparametrarna, följer du stegen nedan för att filtrera bort standardkommandona från importerade uppsättningen. Du kan fortsätta använda kommandon som `Select-Object`, men ska du bara använda den lokala versionen som installerats på datorn i stället för den som importerats från JEA fjärrsessionen.

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

Du kan också spara via proxy-cmdletar från implicit fjärrkommunikation med [Export-PSSession](/powershell/microsoft.powershell.utility/Export-PSSession).
Mer information om implicit fjärrkommunikation finns i dokumentationen för [Import-PSSession](/powershell/microsoft.powershell.utility/import-pssession) och [Import-Module](/powershell/microsoft.powershell.core/import-module).

## <a name="using-jea-programmatically"></a>Använda JEA programmässigt

JEA kan också användas i automatiseringssystem och användarprogram, till exempel interna supportavdelningen appar och webbplatser. Metoden är samma som för att bygga appar som kommunicerar med obegränsad PowerShell-slutpunkter. Se till att programmet har utformats för att arbeta med begränsningar som införts av JEA.

Du kan använda enkla, oneoff aktivitetsinformation, [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) att köra kommandon i en JEA-session.

```powershell
Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Process; Get-Service }
```

Du kan kontrollera vilka kommandon är tillgängliga för användning när du ansluter till en JEA-session genom att köra `Get-Command` och gå igenom de resultat att söka efter de tillåtna parametrarna.

```powershell
$allowedCommands = Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Command }
$allowedCommands | Where-Object { $_.CommandType -in 'Function', 'Cmdlet' } | Format-Table Name, Parameters
```

Om du bygger en C# app, kan du skapa ett PowerShell-körningsutrymme som ansluter till en JEA-session genom att ange konfigurationsnamnet i en [WSManConnectionInfo](/dotnet/api/system.management.automation.runspaces.wsmanconnectioninfo) objekt.

```csharp
// using System.Management.Automation;
var computerName = "SERVER01";
var configName   = "JEAMaintenance";
// See https://docs.microsoft.com/dotnet/api/system.management.automation.pscredential
var creds        = // create a PSCredential object here

WSManConnectionInfo connectionInfo = new WSManConnectionInfo(
    false,                 // Use SSL
    computerName,          // Computer name
    5985,                  // WSMan Port
    "/wsman",              // WSMan Path
                           // Connection URI with config name
    string.Format(CultureInfo.InvariantCulture, "http://schemas.microsoft.com/powershell/{0}", configName),
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

Hyper-V i Windows 10 och Windows Server 2016 erbjuder [PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct), en funktion som gör att Hyper-V-administratörer att hantera virtuella datorer med PowerShell oavsett nätverkskonfiguration eller fjärrhantering inställningarna på den virtuella datorn.

Du kan använda PowerShell Direct med JEA för att ge en Hyper-V begränsad administratörsåtkomst till den virtuella datorn.
Detta kan vara användbart om du förlorar nätverksanslutningen till den virtuella datorn och behöver en datacenter-administratör att åtgärda nätverksinställningarna.

Ingen ytterligare konfiguration krävs för att använda JEA via PowerShell Direct. Gästoperativsystemet som körs på den virtuella datorn måste dock vara Windows 10, Windows Server 2016 eller senare. Hyper-V-administratören kan ansluta till JEA-slutpunkt med hjälp av den `-VMName` eller `-VMId` parametrar om PSRemoting-cmdletar:

```powershell
# Entering a JEA session using PowerShell Direct when the VM name is unique
Enter-PSSession -VMName 'SQL01' -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'

# Entering a JEA session using PowerShell Direct using VM ids
$vm = Get-VM -VMName 'MyVM' | Select-Object -First 1
Enter-PSSession -VMId $vm.VMId -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'
```

Du bör du skapa ett dedikerat användarkonto med lägsta behörighet som krävs för att hantera system för användning av en Hyper-V-administratör. Kom ihåg att även en icke-privilegierade användare kan logga in på en Windows-dator som standard, inklusive med obegränsad PowerShell. Som gör att de kan bläddra i filsystemet och lär dig mer om din OS-miljö. För att låsa en Hyper-V-administratör och begränsa dem för att bara åtkomst till en virtuell dator med PowerShell Direct med JEA, måste du neka lokal inloggningsrättigheter till Hyper-V-administratörens JEA-konto.
