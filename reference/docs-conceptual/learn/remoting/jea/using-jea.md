---
ms.date: 07/10/2019
keywords: Jea, PowerShell, säkerhet
title: Använda JEA
ms.openlocfilehash: 1c424eb4a476dd0db3cc69c0e6f14c89a3c523ba
ms.sourcegitcommit: 30ccbbb32915b551c4cd4c91ef1df96b5b7514c4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/01/2020
ms.locfileid: "80500523"
---
# <a name="using-jea"></a>Använda JEA

I den här artikeln beskrivs de olika sätt som du kan ansluta till och använda en JEA-slutpunkt.

## <a name="using-jea-interactively"></a>Använda JEA interaktivt

Om du testar din JEA-konfiguration eller har enkla uppgifter för användare kan du använda JEA på samma sätt som du skulle göra med en vanlig PowerShell-fjärrsession. För komplexa fjärr kommunikations uppgifter rekommenderar vi att du använder [implicit fjärr kommunikation](#using-jea-with-implicit-remoting). Implicit fjärr kommunikation gör att användare kan arbeta med data objekt lokalt.

Om du vill använda JEA interaktivt måste du:

- Namnet på datorn som du ansluter till (kan vara den lokala datorn)
- Namnet på den JEA-slutpunkt som är registrerad på datorn
- Autentiseringsuppgifter som har åtkomst till JEA-slutpunkten på den här datorn

Med den informationen kan du starta en JEA-session med cmdletarna [New-PSSession](/powershell/module/microsoft.powershell.core/New-PSSession) eller [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) .

```powershell
$nonAdminCred = Get-Credential
Enter-PSSession -ComputerName localhost -ConfigurationName JEAMaintenance -Credential $nonAdminCred
```

Om det aktuella användar kontot har åtkomst till JEA-slutpunkten kan du utelämna parametern för **autentiseringsuppgifter** .

När PowerShell-prompten ändras till `[localhost]: PS>` du veta att du nu interagerar med den fjärranslutna JEA-sessionen. Du kan köra `Get-Command` för att kontrol lera vilka kommandon som är tillgängliga. Kontakta administratören om du vill veta om det finns några begränsningar för de tillgängliga parametrarna eller tillåtna parameter värden.

Kom ihåg att JEA-sessioner körs i nolanguage-läge. Några av de sätt som du vanligt vis använder PowerShell är kanske inte tillgängliga. Du kan till exempel inte använda variabler för att lagra data eller granska egenskaperna för objekt som returneras från-cmdletar. I följande exempel visas två metoder för att få samma kommandon att fungera i läget nolanguage.

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

För mer komplexa kommando anrop som gör den här metoden svår, kan du överväga att använda [implicit fjärr kommunikation](#using-jea-with-implicit-remoting) eller [skapa anpassade funktioner](role-capabilities.md#creating-custom-functions) som omsluter de funktioner du behöver.

## <a name="using-jea-with-implicit-remoting"></a>Använda JEA med implicit fjärr kommunikation

PowerShell har en implicit fjärr kommunikations modell som låter dig importera proxy-cmdletar från en fjärrdator och interagera med dem som om de var lokala kommandon. Implicit fjärr kommunikation förklaras i den här **Hey, Scripting Guy!** [blogg inlägg](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/).
Implicit fjärr kommunikation är användbart när du arbetar med JEA eftersom det gör att du kan arbeta med JEA-cmdlets i ett fullständigt språk läge. Du kan använda ifyllning, variabler, manipulera objekt och till och med använda lokala skript för att automatisera uppgifter mot en JEA-slutpunkt. När du anropar ett proxy-kommando skickas data till JEA-slutpunkten på fjärrdatorn och körs där.

Implicit fjärr kommunikation fungerar genom att importera cmdletar från en befintlig PowerShell-session. Du kan välja att ange prefix för varje proxy-cmdlet med en valfri sträng som du väljer. Med prefixet kan du skilja på kommandona för fjärrsystemet. En tillfällig skript-modul som innehåller alla proxy-kommandon skapas och importeras under den lokala PowerShell-sessionens varaktighet.

```powershell
# Create a new PSSession to your JEA endpoint
$jeasession = New-PSSession -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance'

# Import the entire PSSession and prefix each imported cmdlet with "JEA"
Import-PSSession -Session $jeasession -Prefix 'JEA'

# Invoke "Get-Command" on the remote JEA endpoint using the proxy cmdlet
Get-JEACommand
```

> [!IMPORTANT]
> Vissa system kanske inte kan importera en hel JEA-session på grund av begränsningar i standard-cmdletarna för JEA. Du kan komma runt detta genom att bara importera de kommandon du behöver från JEA-sessionen genom att uttryckligen ange namnen på `-CommandName`-parametern. En framtida uppdatering löser problemet med att importera hela JEA-sessioner på berörda system.

Om du inte kan importera en JEA-session på grund av JEA-begränsningar på standard parametrarna följer du stegen nedan för att filtrera bort standard kommandona från den importerade uppsättningen. Du kan fortsätta använda kommandon som `Select-Object`, men du kommer bara att använda den lokala versionen som är installerad på datorn i stället för den som importer ATS från JEA-sessionen.

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

Du kan också spara proxy-cmdletar från implicit fjärr kommunikation med hjälp av [export-PSSession](/powershell/module/microsoft.powershell.utility/Export-PSSession).
Mer information om implicit fjärr kommunikation finns i dokumentationen för [import-PSSession](/powershell/module/microsoft.powershell.utility/import-pssession) och [import-module](/powershell/module/microsoft.powershell.core/import-module).

## <a name="using-jea-programmatically"></a>Använda JEA program mässigt

JEA kan också användas i Automation-system och i användar program, t. ex. interna Helpdesk-appar och webbplatser. Metoden är densamma som för att skapa appar som kommunicerar med obegränsade PowerShell-slutpunkter. Se till att programmet är utformat för att fungera med begränsning från JEA.

För enkla, enkelriktade uppgifter kan du använda [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) för att köra kommandon i en Jea-session.

```powershell
Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Process; Get-Service }
```

Du kan kontrol lera vilka kommandon som är tillgängliga för användning när du ansluter till en JEA-session genom att köra `Get-Command` och iterera genom resultaten för att kontrol lera de tillåtna parametrarna.

```powershell
$allowedCommands = Invoke-Command -ComputerName 'SERVER01' -ConfigurationName 'JEAMaintenance' -ScriptBlock { Get-Command }
$allowedCommands | Where-Object { $_.CommandType -in 'Function', 'Cmdlet' } | Format-Table Name, Parameters
```

Om du skapar en C# app kan du skapa en PowerShell-körnings utrymme som ansluter till en Jea-session genom att ange konfigurations namnet i ett [WSManConnectionInfo](/dotnet/api/system.management.automation.runspaces.wsmanconnectioninfo) -objekt.

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
    string.Format(CultureInfo.InvariantCulture, "https://schemas.microsoft.com/powershell/{0}", configName),
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

## <a name="using-jea-with-powershell-direct"></a>Använda JEA med PowerShell Direct

Hyper-V i Windows 10 och Windows Server 2016 erbjuder [PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct), en funktion som gör att Hyper-v-administratörer kan hantera virtuella datorer med PowerShell oavsett nätverks konfigurationen eller inställningar för fjärrhantering på den virtuella datorn.

Du kan använda PowerShell Direct med JEA för att ge en Hyper-V-administratör begränsad åtkomst till den virtuella datorn.
Detta kan vara användbart om du tappar bort nätverks anslutningen till den virtuella datorn och behöver en data Center administratör för att åtgärda nätverks inställningarna.

Ingen ytterligare konfiguration krävs för att använda JEA via PowerShell Direct. Men gäst operativ systemet som körs i den virtuella datorn måste vara Windows 10, Windows Server 2016 eller senare. Hyper-V-administratören kan ansluta till JEA-slutpunkten med hjälp av `-VMName`-eller `-VMId`-parametrarna på PSRemoting-cmdlet: ar:

```powershell
# Entering a JEA session using PowerShell Direct when the VM name is unique
Enter-PSSession -VMName 'SQL01' -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'

# Entering a JEA session using PowerShell Direct using VM ids
$vm = Get-VM -VMName 'MyVM' | Select-Object -First 1
Enter-PSSession -VMId $vm.VMId -ConfigurationName 'NICMaintenance' -Credential 'localhost\JEAformyHoster'
```

Vi rekommenderar att du skapar ett dedikerat användar konto med den minsta behörighet som krävs för att hantera systemet för användning av en Hyper-V-administratör. Kom ihåg att även om en obehörig användare kan logga in på en Windows-dator som standard, inklusive att använda obegränsade PowerShell. Detta gör att de kan bläddra i fil systemet och lära sig mer om din operativ system miljö. Om du vill låsa en Hyper-V-administratör och begränsa dem till endast åtkomst till en virtuell dator med hjälp av PowerShell Direct med JEA, måste du neka lokala inloggnings rättigheter till Hyper-V-administratörens JEA-konto.
