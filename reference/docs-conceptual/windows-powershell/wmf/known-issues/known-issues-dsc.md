---
ms.date: 06/12/2017
title: Kända problem och begränsningar för Desired State Configuration (DSC)
description: Kända problem och begränsningar i DSC i Windows PowerShell 5. x
ms.openlocfilehash: 1163ed9e130430f6bbca98405a8993bb054dd1a8
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92662050"
---
# <a name="desired-state-configuration-dsc-known-issues-and-limitations"></a>Kända problem och begränsningar för Desired State Configuration (DSC)

## <a name="breaking-change-certificates-used-to-encryptdecrypt-passwords-in-dsc-configurations-may-not-work-after-installing-wmf-50-rtm"></a>Bryta ändring: certifikat som används för att kryptera/dekryptera lösen ord i DSC-konfigurationer fungerar kanske inte efter installation av WMF 5,0 RTM

I WMF 4,0-och WMF 5,0 Preview-versioner tillåter DSC inte att lösen ord i konfigurationen är längre än 121 tecken. DSC tvingade sig använda korta lösen ord även om längd och starkt lösen ord önskas. Den här avbrytande ändringen innebär att lösen ord kan vara av godtycklig längd i DSC-konfigurationen.

**Lösning:** Återskapa certifikatet med användning av data kryptering eller nyckel kryptering och förbättrad nyckel användning för dokument kryptering (1.3.6.1.4.1.311.80.1). Mer information finns i [Protect-CmsMessage](/powershell/module/Microsoft.PowerShell.Security/Protect-CmsMessage).

## <a name="dsc-cmdlets-may-fail-after-installing-wmf-50-rtm"></a>DSC-cmdletar kan Miss lyckas efter installation av WMF 5,0 RTM

`Start-DscConfiguration` och andra DSC-cmdletar kan Miss lyckas efter installation av WMF 5,0 RTM med följande fel:

```Output
LCM failed to retrieve the property PendingJobStep from the object of class dscInternalCache .
+ CategoryInfo : ObjectNotFound: (root/Microsoft/...gurationManager:String) [], CimException
+ FullyQualifiedErrorId : MI RESULT 6
+ PSComputerName : localhost
```

**Lösning:** Ta bort DSCEngineCache. MOF genom att köra följande kommando i en upphöjd PowerShell-session (kör som administratör):

```powershell
Remove-Item -Path $env:SystemRoot\system32\Configuration\DSCEngineCache.mof
```

## <a name="dsc-cmdlets-may-not-work-if-wmf-50-rtm-is-installed-on-top-of-wmf-50-production-preview"></a>DSC-cmdletar fungerar kanske inte om WMF 5,0 RTM installeras ovanpå WMF 5,0 Product Preview

**Lösning:** Kör följande kommando i en upphöjd PowerShell-session (kör som administratör):

```powershell
mofcomp $env:windir\system32\wbem\DscCoreConfProv.mof
```

## <a name="lcm-can-go-into-an-unstable-state-while-using-get-dscconfiguration-in-debugmode"></a>LCM kan hamna i ett instabilt tillstånd när Get-DscConfiguration används i DebugMode

Om LCM finns i DebugMode, trycker du på CTRL + C för att stoppa bearbetningen av `Get-DscConfiguration` kan orsaka att LCM går in i ett instabilt tillstånd så att majoriteten av DSC-cmdlets inte fungerar.

**Lösning:** Tryck inte på CTRL + C vid fel sökning av `Get-DscConfiguration` cmdlet.

## <a name="stop-dscconfiguration-may-not-respond-in-debugmode"></a>Stop-DscConfiguration kan inte svara i DebugMode

Om LCM finns i DebugMode, `Stop-DscConfiguration` kan inte svara vid försök att stoppa en åtgärd som startats av `Get-DscConfiguration`

**Lösning:** Slutför fel sökningen av åtgärden som startades av `Get-DscConfiguration` som beskrivs i [Felsöka DSC-resurser](/powershell/scripting/dsc/troubleshooting/debugResource).

## <a name="no-verbose-error-messages-are-shown-in-debugmode"></a>Inga utförliga fel meddelanden visas i DebugMode

Om LCM finns i **DebugMode** , visas inga utförliga fel meddelanden från DSC-resurser.

**Lösning:** Inaktivera **DebugMode** för att se utförliga meddelanden från resursen

## <a name="invoke-dscresource-operations-cannot-be-retrieved-by-get-dscconfigurationstatus-cmdlet"></a>Invoke-DscResource åtgärder kan inte hämtas av Get-DscConfigurationStatus cmdlet

När `Invoke-DscResource` du har använt cmdlet för att direkt anropa alla resurs metoder går det inte att hämta posterna för sådan åtgärd via `Get-DscConfigurationStatus` .

**Lösning:** Alternativet.

## <a name="get-dscconfigurationstatus-returns-pull-cycle-operations-as-type-consistency"></a>Get-DscConfigurationStatus returnerar pull-cykel åtgärder som typ **konsekvens**

När en nod ställs in på Hämta uppdaterings läge, `Get-DscConfigurationStatus` rapporterar cmdleten åtgärds typen som **konsekvens** i stället för *initialt* för varje pull-åtgärd.

**Lösning:** Alternativet.

## <a name="invoke-dscresource-cmdlet-does-not-return-message-in-the-order-they-were-produced"></a>Invoke-DscResource cmdlet returnerar inte meddelandet i den ordning de skapades

`Invoke-DscResource`Cmdleten returnerar inte utförliga, varnings-och fel meddelanden i den ordning som de producerade av LCM eller DSC-resursen.

**Lösning:** Alternativet.

## <a name="dsc-resources-cannot-be-debugged-easily-when-used-with-invoke-dscresource"></a>DSC-resurser kan inte felsökas enkelt när de används med Invoke-DscResource

När LCM körs i fel söknings läge `Invoke-DscResource` ger cmdleten inte information om körnings utrymme för att ansluta till för fel sökning. Mer information finns i [fel sökning av DSC-resurser](/powershell/scripting/dsc/troubleshooting/debugResource).

**Lösning:** Identifiera och Anslut till körnings utrymme med cmdlet: ar `Get-PSHostProcessInfo` , `Enter-PSHostProcess` `Get-Runspace` och `Debug-Runspace` för att felsöka DSC-resursen.

```powershell
# Find all the processes hosting PowerShell
Get-PSHostProcessInfo

ProcessName    ProcessId AppDomainName
-----------    --------- -------------
powershell          3932 DefaultAppDomain
powershell_ise      2304 DefaultAppDomain
WmiPrvSE            3396 DscPsPluginWkr_AppDomain

# Enter the process that is hosting DSC engine (WMI process with DscPsPluginWkr_Appdomain)
Enter-PSHostProcess -Id 3396 -AppDomainName DscPsPluginWkr_AppDomain

# Find all the available rusnspaces in that process
Get-Runspace

Id Name       ComputerName Type  State  Availability
-- ----       ------------ ----  -----  ------------
 2 Runspace2  localhost    Local Opened InBreakpoint
 5 RemoteHost localhost    Local Opened Busy

# Debug the runspace that is in **InBreakpoint** availability state
Debug-Runspace -Id 2
```

## <a name="various-partial-configuration-documents-for-same-node-cannot-have-identical-resource-names"></a>Olika konfigurations dokument för samma nod får inte ha identiska resurs namn

För flera delar av konfigurationer som distribueras till en enda nod kan identiska namn på resurser orsaka körnings tids fel.

**Lösning:** Använd olika namn för även samma resurser i olika delar av konfigurationer.

## <a name="start-dscconfiguration-useexisting-does-not-work-with--credential"></a>Start-DscConfiguration – UseExisting fungerar inte med-Credential

När `Start-DscConfiguration` du använder med parametern **UseExisting** ignoreras parametern **Credential** . DSC använder standard process identitet för att fortsätta åtgärden. Detta orsakar fel när en annan autentiseringsuppgift krävs för att fortsätta till fjärrnoden.

**Lösning:** Använd CIM-session för fjärran sluten DSC-åtgärder:

```powershell
$session = New-CimSession -ComputerName $node -Credential $credential
Start-DscConfiguration -UseExisting -CimSession $session
```

## <a name="ipv6-addresses-as-node-names-in-dsc-configurations"></a>IPv6-adresser som nodnamn i DSC-konfigurationer

IPv6-adresser som nodnamn i DSC-konfigurations skript stöds inte i den här versionen.

**Lösning:** Alternativet.

## <a name="debugging-of-class-based-dsc-resources"></a>Fel sökning av `Class-Based` DSC-resurser

Fel sökning av klassbaserade DSC-resurser stöds inte i den här versionen.

**Lösning:** Alternativet.

## <a name="variables-and-functions-defined-in-script-scope-in-dsc-class-based-resource-are-not-preserved-across-multiple-calls-to-a-dsc-resource"></a>Variabler och funktioner som definieras i $script omfång i DSC-Class-Based resurs bevaras inte över flera anrop till en DSC-resurs

Flera anrop i följd `Start-DSCConfiguration` Miss lyckas om konfigurationen använder en klassbaserade resurs som har variabler eller funktioner definierade i `$script` området.

**Lösning:** Definiera alla variabler och funktioner i själva DSC-resurs klassen. Inga `$script` omfångs-variabler/-funktioner.

## <a name="dsc-resource-debugging-when-a-resource-is-using-psdscrunascredential"></a>Fel sökning av DSC-resurs när en resurs använder PSDscRunAsCredential

DSC-resurs fel sökning när en resurs använder egenskapen **PSDscRunAsCredential** i konfigurationen stöds inte i den här versionen.

**Lösning:** Alternativet.

## <a name="psdscrunascredential-is-not-supported-for-dsc-composite-resources"></a>PsDscRunAsCredential stöds inte för sammansatta DSC-resurser

**Lösning:** Använd egenskapen autentiseringsuppgifter om den är tillgänglig. Exempel på ServiceSet och WindowsFeatureSet

## <a name="get-dscresource--syntax-does-not-reflect-psdscrunascredential-correctly"></a>Get-DscResource-syntaxen visar inte PsDscRunAsCredential korrekt

Parametern **syntax** reflekterar inte **PsDscRunAsCredential** korrekt när resursen markerar den som obligatorisk eller inte stöder den.

**Lösning:** Alternativet. Redigering av konfiguration i ISE visar dock korrekta metadata om **PsDscRunAsCredential** -egenskapen när du använder IntelliSense.

## <a name="windowsoptionalfeature-is-not-available-in-windows-7"></a>WindowsOptionalFeature är inte tillgängligt i Windows 7

**WindowsOptionalFeature** DSC-resursen är inte tillgänglig i Windows 7. Den här resursen kräver DISM-modulen och DISM-cmdletar som är tillgängliga från och med Windows 8 och nyare versioner av Windows operativ system.

## <a name="for-class-based-dsc-resources-import-dscresource--moduleversion-may-not-work-as-expected"></a>Import-DscResource-ModuleVersion kanske inte fungerar som förväntat för klassbaserade DSC-resurser

Om noden kompilering har flera versioner av en klass-baserad DSC-resurs, `Import-DscResource -ModuleVersion` väljer inte den angivna versionen och resulterar i följande kompileringsfel.

```Output
ImportClassResourcesFromModule : Exception calling "ImportClassResourcesFromModule" with "3" argument(s):
 "Keyword 'MyTestResource' already defined in the configuration."
At C:\Windows\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\PSDesiredStateConfiguration.psm1:2035 char:35
+ ... rcesFound = ImportClassResourcesFromModule -Module $mod -Resources $r ...
+                 ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [ImportClassResourcesFromModule], MethodInvocationException
    + FullyQualifiedErrorId : PSInvalidOperationException,ImportClassResourcesFromModule
```

**Lösning:** Importera den version som krävs genom att definiera **ModuleSpecification** -objektet till **Modulnamn** -parametern med **RequiredVersion** -nyckeln angiven enligt följande:

```powershell
Import-DscResource -ModuleName @{ModuleName='MyModuleName';RequiredVersion='1.2'}
```

## <a name="some-dsc-resources-like-registry-resource-may-start-to-take-a-long-time-to-process-the-request"></a>Vissa DSC-resurser som register resurser kan ta lång tid att bearbeta begäran.

**Lösning 1:** Skapa en schema aktivitet som rensar upp följande mapp med jämna mellanrum.

```powershell
$env:windir\system32\config\systemprofile\AppData\Local\Microsoft\Windows\PowerShell\CommandAnalysis
```

**Lösning 2:** Ändra DSC-konfigurationen för att rensa mappen *CommandAnalysis* i slutet av konfigurationen.

```powershell
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
        DependsOn = "[Registry]SetRegisteredOwner"
        getscript = "@{}"
        testscript = 'Remove-Item -Path $env:windir\system32\config\systemprofile\AppData\Local\Microsoft\Windows\PowerShell\CommandAnalysis -Force -Recurse -ErrorAction SilentlyContinue -ErrorVariable ev | out-null;$true'
        setscript = '$true'
    }
}
```
