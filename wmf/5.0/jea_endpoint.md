---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 3acd266a75bc61ffe4bce467cfb804ac7865c629
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55687652"
---
# <a name="creating-and-connecting-to-a-jea-endpoint"></a>Skapa och ansluta till en JEA-slutpunkt

Om du vill skapa en JEA-slutpunkt, måste du skapa och registrera en speciellt konfigurerad PowerShell-Session konfigurationsfil, vilken kan genereras med den **New PSSessionConfigurationFile** cmdlet.

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -TranscriptDirectory "C:\ProgramData\JEATranscripts" -RunAsVirtualAccount -RoleDefinitions @{ 'CONTOSO\NonAdmin_Operators' = @{ RoleCapabilities = 'Maintenance' }} -Path "$env:ProgramData\JEAConfiguration\Demo.pssc"
```

Detta skapar en konfigurationsfil för sessionen som ser ut så här:

```powershell
@{

    # Version number of the schema used for this document
    SchemaVersion = '2.0.0.0'

    # ID used to uniquely identify this document
    GUID = 'a384fdd3-5830-4a2c-ac86-cdd1822c3afd'

    # Author of this document
    Author = 'Administrator'

    # Description of the functionality provided by these settings
    # Description = ''

    # Session type defaults to apply for this session configuration. Can be 'RestrictedRemoteServer' (recommended), 'Empty', or 'Default'
    SessionType = 'RestrictedRemoteServer'

    # Directory to place session transcripts for this session configuration
    TranscriptDirectory = 'C:\ProgramData\JEATranscripts'

    # Whether to run this session configuration as the machine's (virtual) administrator account
    RunAsVirtualAccount = $true

    # Groups associated with machine's (virtual) administrator account
    # RunAsVirtualAccountGroups = 'Remote Desktop Users', 'Remote Management Users'

    # Scripts to run when applied to a session
    # ScriptsToProcess = 'C:\ConfigData\InitScript1.ps1', 'C:\ConfigData\InitScript2.ps1'

    # User roles (security groups), and the Role Capabilities that should be applied to them when applied to a session
    RoleDefinitions = @{ 'CONTOSO\NonAdmin_Operators' = @{ 'RoleCapabilities' = 'Maintenance' } }
}
```

När du skapar en JEA-slutpunkt, måste du ange följande parametrar för kommandot (och motsvarande nycklar i filen):

1. SessionType till RestrictedRemoteServer
2. RunAsVirtualAccount till **$true**
3. TranscriptPath till katalogen där ”över axeln” avskrifter ska sparas efter varje session
4. RoleDefinitions till en hash-tabell som definierar vilka grupper som har åtkomst till vilka ”rollfunktioner”. Det här fältet definierar **som** kan göra **vad** på den här slutpunkten. Rollfunktioner är särskilda filer som förklaras inom kort.

Fältet RoleDefinitions definierar vilka grupper som hade tillgång till vilka rollfunktioner. En roll-funktionen är en fil som definierar en uppsättning funktioner som ska visas för användarna att ansluta.
Du kan skapa rollfunktioner med den **New PSRoleCapabilityFile** kommando.

```powershell
New-PSRoleCapabilityFile -Path "$env:ProgramFiles\WindowsPowerShell\Modules\DemoModule\RoleCapabilities\Maintenance.psrc"
```

Detta genererar en mall för roll-funktion som ser ut så här:

```powershell
@{
    # ID used to uniquely identify this document
    GUID = '9287a34f-3f0e-4fbe-9dd7-f1361ba9fd65'

    # Author of this document
    Author = 'Administrator'

    # Description of the functionality provided by these settings
    # Description = ''

    # Company associated with this document
    CompanyName = 'Unknown'

    # Copyright statement for this document
    Copyright = '(c) 2015 Administrator. All rights reserved.'

    # Modules to import when applied to a session
    # ModulesToImport = 'MyCustomModule', @{ ModuleName = 'MyCustomModule'; ModuleVersion = '1.0.0.0'; GUID = '4d30d5f0-cb16-4898-812d-f20a6c596bdf' }

    # Aliases to make visible when applied to a session
    # VisibleAliases = 'Item1', 'Item2'

    # Cmdlets to make visible when applied to a session
    # VisibleCmdlets = 'Invoke-Cmdlet1', @{ Name = 'Invoke-Cmdlet2'; Parameters = @{ Name = 'Parameter1'; ValidateSet = 'Item1', 'Item2' }, @{ Name = 'Parameter2'; ValidatePattern = 'L*' } }

    # Functions to make visible when applied to a session
    # VisibleFunctions = 'Invoke-Function1', @{ Name = 'Invoke-Function2'; Parameters = @{ Name = 'Parameter1'; ValidateSet = 'Item1', 'Item2' }, @{ Name = 'Parameter2'; ValidatePattern = 'L*' } }

    # External commands (scripts and applications) to make visible when applied to a session
    # VisibleExternalCommands = 'Item1', 'Item2'

    # Providers to make visible when applied to a session
    # VisibleProviders = 'Item1', 'Item2'

    # Scripts to run when applied to a session
    # ScriptsToProcess = 'C:\ConfigData\InitScript1.ps1', 'C:\ConfigData\InitScript2.ps1'

    # Aliases to be defined when applied to a session
    # AliasDefinitions = @{ Name = 'Alias1'; Value = 'Invoke-Alias1'}, @{ Name = 'Alias2'; Value = 'Invoke-Alias2'}

    # Functions to define when applied to a session
    # FunctionDefinitions = @{ Name = 'MyFunction'; ScriptBlock = { param($MyInput) $MyInput } }

    # Variables to define when applied to a session
    # VariableDefinitions = @{ Name = 'Variable1'; Value = { 'Dynamic' + 'InitialValue' } }, @{ Name = 'Variable2'; Value = 'StaticInitialValue' }

    # Environment variables to define when applied to a session
    # EnvironmentVariables = @{ Variable1 = 'Value1'; Variable2 = 'Value2' }

    # Type files (.ps1xml) to load when applied to a session
    # TypesToProcess = 'C:\ConfigData\MyTypes.ps1xml', 'C:\ConfigData\OtherTypes.ps1xml'

    # Format files (.ps1xml) to load when applied to a session
    # FormatsToProcess = 'C:\ConfigData\MyFormats.ps1xml', 'C:\ConfigData\OtherFormats.ps1xml'

    # Assemblies to load when applied to a session
    # AssembliesToLoad = 'System.Web', 'System.OtherAssembly, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a'

}
```

För att användas av en JEA-sessionskonfiguration måste rollfunktioner sparas som en giltig PowerShell-modul i en katalog med namnet ”RoleCapabilities”. En modul kan ha flera funktionsfiler för rollen, om så önskas.

Börja konfigurera vilka cmdlet: ar, funktioner, alias och skript som en användare kan komma åt när du ansluter till en JEA-session genom att lägga till dina egna regler till filen roll funktionen efter den kommenterade in mallar. En djupare inblick i hur du kan konfigurera rollfunktioner finns i fullständiga [uppleva guiden](http://aka.ms/JEA).

Slutligen, när du är klar med att anpassa sessionskonfigurationen och relaterade rollfunktioner registrera den här sessionskonfigurationen och skapa slutpunkten genom att köra `Register-PSSessionConfiguration`.

```powershell
Register-PSSessionConfiguration -Name Maintenance -Path "C:\ProgramData\JEAConfiguration\Demo.pssc"
```

## <a name="connect-to-a-jea-endpoint"></a>Ansluta till en JEA-slutpunkt

Ansluta till en JEA-slutpunkt fungerar på samma sätt som ansluter till alla andra PowerShell-endpoint-fungerar.
Du behöver bara ange din JEA-slutpunkt-namn som ”ConfigurationName”-parametern för **New-PSSession**, **Invoke-Command**, eller **Enter-PSSession**.

```powershell
Enter-PSSession -ConfigurationName Maintenance -ComputerName localhost
```

När du har anslutit till JEA-session kan begränsas du kör kommandon godkänd av roll-funktionerna som du har åtkomst till. Ett fel inträffar om du försöker köra alla kommandon som inte är tillåten för din roll.