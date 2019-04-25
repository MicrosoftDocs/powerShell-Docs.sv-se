---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 883f80a5c8c99f2ab9886558a7aebfe1204f3be6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085175"
---
# <a name="desired-state-configuration-dsc-known-issues-and-limitations"></a>Desired State Configuration (DSC) kända problem och begränsningar

## <a name="breaking-change-certificates-used-to-encryptdecrypt-passwords-in-dsc-configurations-may-not-work-after-installing-wmf-50-rtm"></a>Icke-bakåtkompatibel ändring: Certifikat som används för att kryptera/dekryptera lösenord i DSC-konfigurationer kanske inte fungerar när du har installerat WMF 5.0 RTM

I utgåvor av WMF 4.0 och WMF 5.0 Preview DSC inte tillåter lösenord i konfigurationen med längden mer än 121 tecken. DSC tvingande använda korta lösenord, även om långvariga och starka lösenord har önskad. Den här stor förändring kan lösenord ska vara av godtycklig längd i DSC-konfigurationen.

**Lösning:** Återskapa certifikatet med Datachiffrering eller chiffrering nyckeln användnings- och dokumentet kryptering förbättrad nyckelanvändning (1.3.6.1.4.1.311.80.1). TechNet-artikeln <https://technet.microsoft.com/library/dn807171.aspx> innehåller mer information.

## <a name="dsc-cmdlets-may-fail-after-installing-wmf-50-rtm"></a>DSC-cmdletar misslyckas när du har installerat WMF 5.0 RTM

Start-DscConfiguration och andra DSC-cmdletar misslyckas när du har installerat WMF 5.0 RTM med följande fel:
```powershell
    LCM failed to retrieve the property PendingJobStep from the object of class dscInternalCache .
    + CategoryInfo : ObjectNotFound: (root/Microsoft/...gurationManager:String) [], CimException
    + FullyQualifiedErrorId : MI RESULT 6
    + PSComputerName : localhost
```

**Lösning:** Ta bort DSCEngineCache.mof genom att köra följande kommando i en upphöjd PowerShell-session (Kör som administratör):

```powershell
Remove-Item -Path $env:SystemRoot\system32\Configuration\DSCEngineCache.mof
```

## <a name="dsc-cmdlets-may-not-work-if-wmf-50-rtm-is-installed-on-top-of-wmf-50-production-preview"></a>DSC-cmdlets fungerar inte om WMF 5.0 RTM installeras ovanpå WMF 5.0 produktion förhandsversion

**Lösning:** Kör följande kommando i en upphöjd PowerShell-session (Kör som administratör):
```powershell
    mofcomp $env:windir\system32\wbem\DscCoreConfProv.mof
```

## <a name="lcm-can-go-into-an-unstable-state-while-using-get-dscconfiguration-in-debugmode"></a>LCM går i ett instabilt tillstånd och Använd Get-DscConfiguration DebugMode

Om LCM finns i DebugMode, att trycka på CTRL + C för att stoppa bearbetningen av Get-DscConfiguration kan orsaka MGM om du vill gå till ett instabilt tillstånd sådana som merparten av DSC-cmdlets fungerar inte.

**Lösning:** Inte på CTRL + C när du felsöker Get-DscConfiguration-cmdleten.

## <a name="stop-dscconfiguration-may-not-respond-in-debugmode"></a>Stop-DscConfiguration svarar inte i DebugMode

Om LCM finns i DebugMode, kanske Stop-DscConfiguration inte svarar när försök att stoppa en åtgärd startas av Get-DscConfiguration

**Lösning:** Slutför felsökning av åtgärden startas av Get-DscConfiguration som beskrivs i avsnittet ”[felsökning DSC-resurser](https://msdn.microsoft.com/powershell/dsc/debugresource)'.

## <a name="no-verbose-error-messages-are-shown-in-debugmode"></a>Inga utförlig felmeddelanden visas i DebugMode

Om LCM finns i DebugMode, visas inga utförlig felmeddelanden från DSC-resurser.

**Lösning:** Inaktivera *DebugMode* att visa utförliga meddelanden från resursen

## <a name="invoke-dscresource-operations-cannot-be-retrieved-by-get-dscconfigurationstatus-cmdlet"></a>Anropa DscResource åtgärder kan inte hämtas med cmdleten Get-DscConfigurationStatus

När du använder cmdleten Invoke-DscResource direkt anropa metoder för en resurs, går inte poster i en sådan åtgärd att hämta via Get-DscConfigurationStatus vid ett senare tillfälle.

**Lösning:** Ingen.

## <a name="get-dscconfigurationstatus-returns-pull-cycle-operations-as-type-consistency"></a>Get-DscConfigurationStatus returnerar pull cykel åtgärder som typen *konsekvens*

När en nod har angetts till PULL uppdatera läge för varje pull-åtgärder som utförs, Get-DscConfigurationStatus cmdlet rapporterar åtgärdstypen som *konsekvens* i stället för *inledande*

**Lösning:** Ingen.

## <a name="invoke-dscresource-cmdlet-does-not-return-message-in-the-order-they-were-produced"></a>Anropa DscResource cmdlet returnerar inte meddelandet i den ordning som de skapas

Cmdleten Invoke-DscResource returnerar inte utförlig, varning, och felmeddelanden i den ordning som de har producerats av LCM eller DSC-resurs.

**Lösning:** Ingen.

## <a name="dsc-resources-cannot-be-debugged-easily-when-used-with-invoke-dscresource"></a>DSC-resurser kan inte felsökas enkelt när det används med Invoke-DscResource

När LCM körs i felsökningsläge (se [felsökning DSC-resurser](https://msdn.microsoft.com/powershell/dsc/debugresource) för mer information), Invoke-DscResource cmdlet ger inte information om körningsutrymme att ansluta till för felsökning.
**Lösning:** Identifiera och ansluta till körningsutrymme med hjälp av cmdlet: ar **Get-PSHostProcessInfo**, **RETUR PSHostProcess** , **Get-Körningsutrymme** och **Debug-Körningsutrymme** felsöka DSC-resurs.

```powershell
# Find all the processes hosting PowerShell
Get-PSHostProcessInfo

ProcessName ProcessId AppDomainName
----------- --------- -------------
powershell 3932 DefaultAppDomain
powershell_ise 2304 DefaultAppDomain
WmiPrvSE 3396 DscPsPluginWkr_AppDomain

# Enter the process that is hosting DSC engine (WMI process with DscPsPluginWkr_Appdomain)
Enter-PSHostProcess -Id 3396 -AppDomainName DscPsPluginWkr_AppDomain

# Find all the available rusnspaces in that process
Get-Runspace

Id Name ComputerName Type State Availability
-- ---- ------------ ---- ----- ------------
2 Runspace2 localhost Local Opened InBreakpoint
5 RemoteHost localhost Local Opened Busy

# Debug the runspace that is in **InBreakpoint** availability state
Debug-Runspace -Id 2
```

## <a name="various-partial-configuration-documents-for-same-node-cannot-have-identical-resource-names"></a>Olika partiell konfiguration dokumenten för samma nod kan inte ha identiska resursnamn

För flera partiella konfigurationer som har distribuerats till en enda nod, kör identiska namn för resurser orsak fel.

**Lösning:** Använda olika namn för även samma resurser i olika partiella konfigurationer.

## <a name="start-dscconfiguration-useexisting-does-not-work-with--credential"></a>Start-DscConfiguration – UseExisting fungerar inte med - autentiseringsuppgifter

När du använder Start-DscConfiguration med parametern – UseExisting – Credential parametern ignoreras. DSC använder standard-ID för att fortsätta åtgärden. Detta orsakar fel när andra autentiseringsuppgifter krävs för att fortsätta på fjärrnoden.

**Lösning:** Använda CIM-session för DSC-fjärråtgärder:
```powershell
$session = New-CimSession -ComputerName $node -Credential $credential
Start-DscConfiguration -UseExisting -CimSession $session
```

## <a name="ipv6-addresses-as-node-names-in-dsc-configurations"></a>IPv6-adresser som nodnamn i DSC-konfigurationer

IPv6-adresser som noden i DSC-konfigurationsskript stöds inte i den här versionen.

**Lösning:** Ingen.

## <a name="debugging-of-class-based-dsc-resources"></a>Felsökning av klassbaserade DSC-resurser

Felsökning av klassbaserade DSC-resurser stöds inte i den här versionen.

**Lösning:** Ingen.

## <a name="variables--functions-defined-in-script-scope-in-dsc-class-based-resource-are-not-preserved-across-multiple-calls-to-a-dsc-resource"></a>Variabler & funktioner som definierats i $script omfånget i DSC MOF-baserade Resource bevaras inte mellan flera anrop till en DSC-resurs

Flera på varandra följande anrop till Start-DSCConfiguration misslyckas om konfigurationen använder en MOF-baserade resurs som har variabler eller funktioner som definierats i $script omfånget.

**Lösning:** Definiera alla variabler och funktioner i DSC resursklass själva. No $script omfång variabler/funktioner.

## <a name="dsc-resource-debugging-when-a-resource-is-using-psdscrunascredential"></a>DSC-resurs felsökning när en resurs använder PSDscRunAsCredential

DSC-resurs felsökning när en resurs använder den *PSDscRunAsCredential* -egenskapen i konfigurationen stöds inte i den här versionen.

**Lösning:** Ingen.

## <a name="psdscrunascredential-is-not-supported-for-dsc-composite-resources"></a>PsDscRunAsCredential stöds inte för DSC sammansatta resurser

**Lösning:** Använda Credential-egenskapen om det är tillgängligt. Exempel ServiceSet och WindowsFeatureSet

## <a name="get-dscresource--syntax-does-not-reflect-psdscrunascredential-correctly"></a>*Get-DscResource-Syntax* PsDscRunAsCredential avspeglar inte korrekt

Get-DscResource-Syntax avspeglar inte PsDscRunAsCredential korrekt när resursen markeras som obligatoriska eller har inte stöd för den.

**Lösning:** Ingen. Dock visar redigera konfigurationen i ISE rätt metadata om PsDscRunAsCredential egenskapen när du använder IntelliSense.

## <a name="windowsoptionalfeature-is-not-available-in-windows-7"></a>WindowsOptionalFeature är inte tillgänglig i Windows 7

WindowsOptionalFeature DSC-resursen är inte tillgänglig i Windows 7. Den här resursen kräver DISM-modulen och DISM-cmdletar som är tillgängliga från och med Windows 8 och senare versioner av Windows-operativsystemet.

## <a name="for-class-based-dsc-resources-import-dscresource--moduleversion-may-not-work-as-expected"></a>Klassbaserade DSC-resurser, kanske Import-DscResource - ModuleVersion inte fungerar som förväntat

Om noden kompilering har flera version av en klassbaserade DSC-Resursmodul, `Import-DscResource -ModuleVersion` inte hämtar den angivna versionen och resulterar i följande kompileringsfel.

```
ImportClassResourcesFromModule : Exception calling "ImportClassResourcesFromModule" with "3" argument(s): "Keyword 'MyTestResource' already defined in the configuration."
At C:\Windows\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\PSDesiredStateConfiguration.psm1:2035 char:35
+ ... rcesFound = ImportClassResourcesFromModule -Module $mod -Resources $r ...
+                 ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [ImportClassResourcesFromModule], MethodInvocationException
    + FullyQualifiedErrorId : PSInvalidOperationException,ImportClassResourcesFromModule
```

**Lösning:** Importera versionen som krävs genom att definiera den *ModuleSpecification* objekt till den `-ModuleName` med `RequiredVersion` nyckeln som anges på följande sätt:

``` PowerShell
Import-DscResource -ModuleName @{ModuleName='MyModuleName';RequiredVersion='1.2'}
```

## <a name="some-dsc-resources-like-registry-resource-may-start-to-take-a-long-time-to-process-the-request"></a>Vissa DSC-resurser som Registerresurser kan börja ta lång tid att bearbeta begäran.

**Resolution1:** Skapa en schemalagd aktivitet som rensar upp följande mapp med jämna mellanrum.

``` PowerShell
$env:windir\system32\config\systemprofile\AppData\Local\Microsoft\Windows\PowerShell\CommandAnalysis
```

**Resolution2:** Ändra DSC-konfiguration för att rensa den *CommandAnalysis* mappen i slutet av konfigurationen.

``` PowerShell
Configuration $configName
{

   # User Data
    Registry SetRegisteredOwner
    {
        Ensure = 'Present'
        Force = $True
        Key = $Node.RegisteredKey
        ValueName = $Node.RegisteredOwnerValue
        ValueType = 'String'
        ValueData = $Node.RegisteredOwnerData
    }
    #
    # Script to delete the config
    #
    script DeleteCommandAnalysisCache
    {
        DependsOn="[Registry]SetRegisteredOwner"
        getscript="@{}"
        testscript = 'Remove-Item -Path $env:windir\system32\config\systemprofile\AppData\Local\Microsoft\Windows\PowerShell\CommandAnalysis -Force -Recurse -ErrorAction SilentlyContinue -ErrorVariable ev | out-null;$true'
        setscript = '$true'
    }
}
```
