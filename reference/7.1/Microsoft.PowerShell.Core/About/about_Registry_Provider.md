---
description: Register
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_registry_provider?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register leverantör
ms.openlocfilehash: e97fc607c456909dc0abdb50cb7dd5b5847998a0
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93272222"
---
# <a name="registry-provider"></a>Register leverantör

## <a name="provider-name"></a>Providernamn

Register

## <a name="drives"></a>Enheter

`HKLM:`, `HKCU:`

## <a name="capabilities"></a>Funktioner

**ShouldProcess** , **UseTransactions**

## <a name="short-description"></a>Kort beskrivning

Ger åtkomst till register nycklar, poster och värden i PowerShell.

## <a name="detailed-description"></a>Detaljerad beskrivning

Med PowerShell- **registerposten** kan du hämta, lägga till, ändra, rensa och ta bort register nycklar, poster och värden i PowerShell.

**Register** enheterna är ett hierarkiskt namn område som innehåller register nycklar och under nycklar på din dator. Register poster och värden är inte komponenter i den hierarkin. De är i stället egenskaper för var och en av nycklarna.

**Registry** -providern stöder följande cmdlets, som beskrivs i den här artikeln.

- [Get-location](xref:Microsoft.PowerShell.Management.Get-Location)
- [Ange plats](xref:Microsoft.PowerShell.Management.Set-Location)
- [Hämta objekt](xref:Microsoft.PowerShell.Management.Get-Item)
- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)
- [Anropa-objekt](xref:Microsoft.PowerShell.Management.Invoke-Item)
- [Flytta objekt](xref:Microsoft.PowerShell.Management.Move-Item)
- [Nytt objekt](xref:Microsoft.PowerShell.Management.New-Item)
- [Ta bort objekt](xref:Microsoft.PowerShell.Management.Remove-Item)
- [Get-ItemProperty](xref:Microsoft.PowerShell.Management.Get-ItemProperty)
- [Set-ItemProperty](xref:Microsoft.PowerShell.Management.Set-ItemProperty)
- [Remove-ItemProperty](xref:Microsoft.PowerShell.Management.Remove-ItemProperty)
- [Clear-ItemProperty](xref:Microsoft.PowerShell.Management.Clear-ItemProperty)
- [Get-ACL](xref:Microsoft.PowerShell.Security.Get-Acl)
- [Ange ACL](xref:Microsoft.PowerShell.Security.Set-Acl)

## <a name="types-exposed-by-this-provider"></a>Typer som exponeras av denna provider

Register nycklar representeras som instanser av klassen [Microsoft. Win32. RegistryKey](/dotnet/api/microsoft.win32.registrykey) . Register poster representeras som instanser av klassen [PSCustomObject](/dotnet/api/system.management.automation.pscustomobject) .

## <a name="navigating-the-registry-drives"></a>Navigera i register enheterna

**Register** leverantören exponerar data lagret som två standard enheter. Register platsen HKEY_LOCAL_MACHINE mappas till `HKLM:` enheten och HKEY_CURRENT_USER mappas till `HKCU:` enheten. Om du vill arbeta med registret kan du ändra platsen till `HKLM:` enheten med hjälp av följande kommando.

```powershell
Set-Location HKLM:
```

Om du vill återgå till en fil systemen het skriver du enhetens namn. Skriv till exempel:

```powershell
Set-Location C:
```

Du kan också arbeta med **registrerings** leverantören från andra PowerShell-enheter. Om du vill referera till en register nyckel från en annan plats använder du enhets namnet ( `HKLM:` , `HKCU:` ) i sökvägen. Använd ett omvänt snedstreck ( \\ ) eller ett snedstreck (/) för att ange en nivå för **register** enheten.

```powershell
PS C:\> cd HKLM:\Software
```

> [!NOTE]
> PowerShell använder alias för att ge dig ett välbekant sätt att arbeta med providerns sökvägar. Kommandon som `dir` och är `ls` nu alias för [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` är ett alias för [set-location](xref:Microsoft.PowerShell.Management.Set-Location)och `pwd` är ett alias för [Get-location](xref:Microsoft.PowerShell.Management.Get-Location).

I det sista exemplet visas en annan sökväg för sökvägen som du kan använda för att navigera i **register** leverantören. Den här syntaxen använder Providerns namn, följt av två kolon `::` . Med den här syntaxen kan du använda det fullständiga HIVE-namnet i stället för namnet på den mappade enheten `HKLM` .

```powershell
cd "Registry::HKEY_LOCAL_MACHINE\Software"
```

## <a name="displaying-the-contents-of-registry-keys"></a>Visar innehållet i register nycklar

Registret är indelat i nycklar, under nycklar och poster. Mer information om register strukturen finns i [strukturen för registret](/windows/desktop/sysinfo/structure-of-the-registry).

I en **register** enhet är varje nyckel en behållare. En nyckel kan innehålla valfritt antal nycklar. En register nyckel som har en överordnad nyckel kallas för en under nyckel. Du kan använda `Get-ChildItem` för att Visa register nycklar och `Set-Location` navigera till en nyckel Sök väg.

Register värden är attribut för en register nyckel. I **register** enheten kallas de för **objekt egenskaper**. En register nyckel kan ha både underordnade nycklar och objekt egenskaper.

I det här exemplet visas skillnaden mellan `Get-Item` och `Get-ChildItem` . När du använder `Get-Item` på register nyckeln "Spooler" kan du se dess egenskaper.

```
PS C:\ > Get-Item -Path HKLM:\SYSTEM\CurrentControlSet\Services\Spooler


    Hive: HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services


Name        Property
----        --------
Spooler     DependOnService    : {RPCSS, http}
            Description        : @%systemroot%\system32\spoolsv.exe,-2
            DisplayName        : @%systemroot%\system32\spoolsv.exe,-1
            ErrorControl       : 1
            FailureActions     : {16, 14, 0, 0...}
            Group              : SpoolerGroup
            ImagePath          : C:\WINDOWS\System32\spoolsv.exe
            ObjectName         : LocalSystem
            RequiredPrivileges : {SeTcbPrivilege, SeImpersonatePrivilege, ...
            ServiceSidType     : 1
            Start              : 2
            Type               : 27
```

Varje register nyckel kan också ha under nycklar. Under `Get-Item` nycklarna visas inte när du använder på en register nyckel. I `Get-ChildItem` cmdleten visas underordnade objekt i nyckeln "Spooler", inklusive egenskaperna för varje under nyckel. Egenskaperna för överordnade nycklar visas inte när du använder `Get-ChildItem` .

```
PS C:\> Get-ChildItem -Path HKLM:\SYSTEM\CurrentControlSet\Services\Spooler


    Hive: HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Spooler


Name             Property
----             --------
Performance      Close           : PerfClose
                 Collect         : PerfCollect
                 Collect Timeout : 2000
                 Library         : C:\Windows\System32\winspool.drv
                 Object List     : 1450
                 Open            : PerfOpen
                 Open Timeout    : 4000
Security         Security : {1, 0, 20, 128...}
```

`Get-Item`Cmdleten kan också användas på den aktuella platsen. I följande exempel navigerar du till register nyckeln Spooler (Spooler) och hämtar objekt egenskaperna.
Punkten `.` används för att ange den aktuella platsen.

```
PS C:\> cd HKLM:\System\CurrentControlSet\Services\Spooler
PS HKLM:\SYSTEM\CurrentControlSet\Services\Spooler> Get-Item .

    Hive: HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services

Name             Property
----             --------
Spooler          DependOnService    : {RPCSS, http}
                 Description        : @%systemroot%\system32\spoolsv.exe,-2
...
```

Mer information om de cmdlets som beskrivs i det här avsnittet finns i följande artiklar.

-[Hämta objekt](xref:Microsoft.PowerShell.Management.Get-Item) 
- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)

## <a name="viewing-registry-key-values"></a>Visa register nyckel värden

Register nyckel värden lagras som egenskaper för varje register nyckel. `Get-ItemProperty`Cmdleten visar register nyckel egenskaperna med det namn som du anger. Resultatet är en **PSCustomObject** som innehåller de egenskaper som du anger.

I följande exempel används `Get-ItemProperty` cmdleten för att visa alla egenskaper. Genom att lagra det resulterande objektet i en variabel kan du komma åt önskat egenskaps värde.

```powershell
$p = Get-ItemProperty -Path HKLM:\SYSTEM\CurrentControlSet\Services\Spooler
$p.DependOnService
```

```output
RPCSS
http
```

Om du anger ett värde för `-Name` parametern väljs de egenskaper som du anger och returnerar **PSCustomObject**.  I följande exempel visas skillnaden i utdata när du använder- `-Name` parametern.

```
PS C:\> Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Wbem

BUILD                      : 17134.1
Installation Directory     : C:\WINDOWS\system32\WBEM
MOF Self-Install Directory : C:\WINDOWS\system32\WBEM\MOF
PSPath                     : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Wbem
PSParentPath               : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft
PSChildName                : Wbem
PSDrive                    : HKLM
PSProvider                 : Microsoft.PowerShell.Core\Registry

PS C:\> Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Wbem -Name BUILD

BUILD        : 17134.1
PSPath       : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Wbem
PSParentPath : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft
PSChildName  : Wbem
PSDrive      : HKLM
PSProvider   : Microsoft.PowerShell.Core\Registry
```

Från och med PowerShell 5,0 `Get-ItemPropertyValue` returnerar cmdleten bara värdet för den egenskap som du anger.

```powershell
Get-ItemPropertyValue -Path HKLM:\SOFTWARE\Microsoft\Wbem -Name BUILD
```

```output
17134.1
```

Mer information om de cmdlets som används i det här avsnittet finns i följande artiklar.

- [Get-ItemProperty](xref:Microsoft.PowerShell.Management.Get-ItemProperty)
- [Get-ItemPropertyValue](xref:Microsoft.PowerShell.Management.Get-ItemProperty)

## <a name="changing-registry-key-values"></a>Ändra register nyckel värden

`Set-ItemProperty`Cmdlet: en kommer att ange attribut för register nycklar. I följande exempel används `Set-ItemProperty` för att ändra start typen för Spooler-tjänsten till manuell. Exemplet ändrar **StartType** tillbaka till *automatiskt* med hjälp av `Set-Service` cmdleten.

```
PS C:\> Get-Service spooler | Select-Object Name, StartMode

Name    StartType
----    ---------
spooler Automatic

PS C:\> $path = "HKLM:\SYSTEM\CurrentControlSet\Services\Spooler\"
PS C:\> Set-ItemProperty -Path $path -Name Start -Value 3
PS C:\> Get-Service spooler | Select-Object Name, StartMode

Name    StartType
----    ---------
spooler    Manual

PS C:\> Set-Service -Name Spooler -StartupType Automatic
```

Varje register nyckel har ett *Standardvärde* . Du kan ändra *standardvärdet* för en register nyckel med antingen `Set-Item` eller `Set-ItemProperty` .

```powershell
Set-ItemProperty -Path HKLM:\SOFTWARE\Contoso -Name "(default)" -Value "one"
Set-Item -Path HKLM:\SOFTWARE\Contoso -Value "two"
```

Mer information om de cmdlets som används i det här avsnittet finns i följande artiklar.

- [Ange objekt](xref:Microsoft.PowerShell.Management.Set-Item)
- [Set-ItemProperty](xref:Microsoft.PowerShell.Management.Set-ItemProperty)

## <a name="creating-registry-keys-and-values"></a>Skapa register nycklar och värden

`New-Item`Cmdleten skapar register nycklar med ett namn som du anger.
Du kan också använda `mkdir` funktionen som anropar `New-Item` cmdleten internt.

```
PS HKLM:\SOFTWARE\> mkdir ContosoCompany

    Hive: HKEY_LOCAL_MACHINE\SOFTWARE

Name                           Property
----                           --------
ContosoCompany
```

Du kan använda `New-ItemProperty` cmdleten för att skapa värden i en register nyckel som du anger. I följande exempel skapas ett nytt DWORD-värde i register nyckeln ContosoCompany.

```powershell
$path = "HKLM:\SOFTWARE\ContosoCompany"
New-ItemProperty -Path  -Name Test -Type DWORD -Value 1
```

> [!NOTE]
> Läs avsnittet dynamiska parametrar i den här artikeln för andra tillåtna typ värden.

Detaljerad cmdlet-användning finns i [New-ItemProperty](xref:Microsoft.PowerShell.Management.New-ItemProperty).

## <a name="copying-registry-keys-and-values"></a>Kopiera register nycklar och värden

I **Registry** -providern använder du `Copy-Item` cmdleten för att kopiera register nycklar och värden. Använd `Copy-ItemProperty` cmdleten för att endast kopiera register värden.
Följande kommando kopierar register nyckeln "contoso" och dess egenskaper till den angivna platsen "HKLM: \ Software\Fabrikam".

`Copy-Item` skapar mål nyckeln om den inte finns. Om mål nyckeln finns `Copy-Item` skapar en dubblett av käll nyckeln som ett underordnat objekt (under nyckel) för mål nyckeln.

```powershell
Copy-Item -Path  HKLM:\Software\Contoso -Destination HKLM:\Software\Fabrikam
```

Följande kommando använder `Copy-ItemProperty` cmdleten för att kopiera "Server"-värdet från "contoso"-nyckeln till "Fabrikam"-nyckeln.

```powershell
$source = "HKLM:\SOFTWARE\Contoso"
$dest = "HKLM:\SOFTWARE\Fabrikam"
Copy-ItemProperty -Path $source -Destination $dest -Name Server
```

Mer information om de cmdlets som används i det här avsnittet finns i följande artiklar.

- [Kopiera objekt](xref:Microsoft.PowerShell.Management.Copy-Item)
- [Kopiera – ItemProperty](xref:Microsoft.PowerShell.Management.Copy-ItemProperty)

## <a name="moving-registry-keys-and-values"></a>Flytta register nycklar och värden

`Move-Item` `Move-ItemProperty` Cmdletarna och beter sig som deras "kopiering"-motsvarigheter. Om målet finns `Move-Item` flyttar käll nyckeln under mål nyckeln. Om mål nyckeln inte finns, flyttas käll nyckeln till mål Sök vägen.

Följande kommando flyttar "contoso"-nyckeln till sökvägen "HKLM: \ SOFTWARE\Fabrikam".

```powershell
Move-Item -Path HKLM:\SOFTWARE\Contoso -Destination HKLM:\SOFTWARE\Fabrikam
```

Detta kommando flyttar alla egenskaper från "HKLM: \ SOFTWARE\ContosoCompany" till "HKLM: \ SOFTWARE\Fabrikam".

```powershell
$source = "HKLM:\SOFTWARE\Contoso"
$dest = "HKLM:\SOFTWARE\Fabrikam"
Move-ItemProperty -Path $source -Destination $dest -Name *
```

Mer information om de cmdlets som används i det här avsnittet finns i följande artiklar.

- [Flytta objekt](xref:Microsoft.PowerShell.Management.Move-Item)
- [Move-ItemProperty](xref:Microsoft.PowerShell.Management.Move-ItemProperty)

## <a name="renaming-registry-keys-and-values"></a>Byta namn på register nycklar och värden

Du kan byta namn på register nycklar och värden precis som du skulle göra med filer och mappar.
`Rename-Item` byter namn på register nycklar och `Rename-ItemProperty` byter namn på register värden.

```powershell
$path = "HKLM:\SOFTWARE\Contoso"
Rename-ItemProperty -Path $path -Name ContosoTest -NewName FabrikamTest
Rename-Item -Path $path -NewName Fabrikam
```

## <a name="changing-security-descriptors"></a>Ändra säkerhets beskrivningar

Du kan begränsa åtkomsten till register nycklar med hjälp av `Get-Acl` `Set-Acl` cmdletarna och. I följande exempel läggs en ny användare till med fullständig behörighet till register nyckeln "HKLM: \ SOFTWARE\Contoso".

```powershell
$acl = Get-Acl -Path HKLM:\SOFTWARE\Contoso
$rule = New-Object System.Security.AccessControl.RegistryAccessRule `
("CONTOSO\jsmith", "FullControl", "Allow")
$acl.SetAccessRule($rule)
$acl | Set-Acl -Path HKLM:\SOFTWARE\Contoso
```

Fler exempel och information om cmdlet-användning finns i följande artiklar.

- [Get-ACL](xref:Microsoft.PowerShell.Security.Get-Acl)
- [Ange ACL](xref:Microsoft.PowerShell.Security.Set-Acl)

## <a name="removing-and-clearing-registry-keys-and-values"></a>Ta bort och rensa register nycklar och värden

Du kan ta bort objekt som finns med hjälp av **Remove-item** , men du uppmanas att bekräfta borttagningen om objektet innehåller något annat. Följande exempel försöker ta bort en nyckel "HKLM: \ SOFTWARE\Contoso".

```
PS C:\> dir HKLM:\SOFTWARE\Contoso\

    Hive: HKEY_LOCAL_MACHINE\SOFTWARE\Contoso

Name                           Property
----                           --------
ChildKey

PS C:\> Remove-Item -Path HKLM:\SOFTWARE\Contoso

Confirm
The item at HKLM:\SOFTWARE\Contoso has children and the -Recurse
parameter was not specified. If you continue, all children will be removed
with the item. Are you sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

Om du vill ta bort de objekt som finns utan att göra det anger du `-Recurse` parametern.

```powershell
Remove-Item -Path HKLM:\SOFTWARE\Contoso -Recurse
```

Om du vill ta bort alla objekt inom "HKLM: \ SOFTWARE\Contoso" men inte "HKLM: \ SOFTWARE\Contoso", använder du ett avslutande omvänt snedstreck `\` följt av ett jokertecken.

```powershell
Remove-Item -Path HKLM:\SOFTWARE\Contoso\* -Recurse
```

Det här kommandot tar bort registervärdet "ContosoTest" från register nyckeln "HKLM: \ SOFTWARE\Contoso".

```powershell
Remove-ItemProperty -Path HKLM:\SOFTWARE\Contoso -Name ContosoTest
```

`Clear-Item` tar bort alla register värden för en nyckel. I följande exempel rensas alla värden från register nyckeln "HKLM: \ SOFTWARE\Contoso". Om du bara vill rensa en speciell egenskap använder du `Clear-ItemProperty` .

```
PS HKLM:\SOFTWARE\> Get-Item .\Contoso\

    Hive: HKEY_LOCAL_MACHINE\SOFTWARE

Name           Property
----           --------
Contoso        Server     : {a, b, c}
               HereString : {This is text which contains
               newlines. It also contains "quoted" strings}
               (default)  : 1

PS HKLM:\SOFTWARE\> Clear-Item .\Contoso\
PS HKLM:\SOFTWARE\> Get-Item .\Contoso\

    Hive: HKEY_LOCAL_MACHINE\SOFTWARE

Name                           Property
----                           --------
Contoso
```

Fler exempel och information om cmdlet-användning finns i följande artiklar.

- [Rensa objekt](xref:Microsoft.PowerShell.Management.Clear-Item)
- [Clear-ItemProperty](xref:Microsoft.PowerShell.Management.Clear-ItemProperty)
- [Ta bort objekt](xref:Microsoft.PowerShell.Management.Remove-Item)
- [Remove-ItemProperty](xref:Microsoft.PowerShell.Management.Remove-ItemProperty)

## <a name="dynamic-parameters"></a>Dynamiska parametrar

Dynamiska parametrar är cmdlet-parametrar som läggs till av en PowerShell-Provider och är bara tillgängliga när cmdleten används i den provider-aktiverade enheten.

### <a name="type-microsoftwin32registryvaluekind"></a>Skriv <Microsoft. Win32. RegistryValueKind>

Skapar eller ändrar data typen för ett register värde. Standardvärdet är `String` (REG_SZ).

Den här parametern fungerar som den är utformad på cmdleten [Set-ItemProperty](xref:Microsoft.PowerShell.Management.Set-ItemProperty) . Den är också tillgänglig på cmdleten [set-item](xref:Microsoft.PowerShell.Management.Set-Item) i register enheterna, men den har ingen påverkan.

|Värde | Beskrivning |
| ---- | ----------- |
| `String` | Anger en null-avslutad sträng. Motsvarar REG_SZ. |
| `ExpandString` | Anger en null-avslutad sträng som innehåller expanderad |
|                | referenser till miljövariabler som expanderas när |
|                | Värdet hämtas. Motsvarar REG_EXPAND_SZ. |
| `Binary` | Anger binära data i alla former. Motsvarar REG_BINARY. |
| `DWord` | Anger ett 32-bitars binärt tal. Motsvarar REG_DWORD. |
| `MultiString` | Anger en matris med null-terminerade strängar som avslut ATS av |
|               | två NULL-tecken. Motsvarar REG_MULTI_SZ. |
| `QWord` | Anger ett 64-bitars binärt tal. Motsvarar REG_QWORD. |
| `Unknown` | Anger en register data typ som inte stöds, till exempel |
|           | REG_RESOURCE_LIST. |

#### <a name="cmdlets-supported"></a>Cmdlets som stöds

- [Ange objekt](xref:Microsoft.PowerShell.Management.Set-Item)
- [Set-ItemProperty](xref:Microsoft.PowerShell.Management.Set-ItemProperty)

## <a name="using-the-pipeline"></a>Använda pipelinen

Provider-cmdletar accepterar pipeline-ininformation. Du kan använda pipelinen för att förenkla uppgiften genom att skicka leverantörs data från en cmdlet till en annan provider-cmdlet. Mer information om hur du använder pipelinen med Provider-cmdletar finns i cmdlet-referenser som finns i den här artikeln.

## <a name="getting-help"></a>Få hjälp

Från och med Windows PowerShell 3,0 kan du hämta anpassade hjälp avsnitt för provider-cmdletar som förklarar hur dessa cmdletar fungerar i en fil systemen het.

Om du vill få hjälp avsnitten som är anpassade för fil system enheten kör du ett `Get-Help` kommando i en fil system enhet eller använder parametern **Path** för att ange en fil system enhet.

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path HKLM:
```

## <a name="see-also"></a>Se även

 [about_Providers](../About/about_Providers.md)

