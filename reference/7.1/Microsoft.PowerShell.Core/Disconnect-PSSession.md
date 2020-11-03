---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/disconnect-pssession?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disconnect-PSSession
ms.openlocfilehash: efe80ab22af8552860e3dfa8f9e2766b07bcfd5d
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/23/2020
ms.locfileid: "93268538"
---
# Disconnect-PSSession

## SAMMANFATTNING
Kopplar från en session.

## SYNTAX

### Session (standard)

```
Disconnect-PSSession [-Session] <PSSession[]> [-IdleTimeoutSec <Int32>]
 [-OutputBufferingMode <OutputBufferingMode>] [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### Name

```
Disconnect-PSSession [-IdleTimeoutSec <Int32>] [-OutputBufferingMode <OutputBufferingMode>]
 [-ThrottleLimit <Int32>] -Name <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InstanceId

```
Disconnect-PSSession [-IdleTimeoutSec <Int32>] [-OutputBufferingMode <OutputBufferingMode>]
 [-ThrottleLimit <Int32>] -InstanceId <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Id

```
Disconnect-PSSession [-IdleTimeoutSec <Int32>] [-OutputBufferingMode <OutputBufferingMode>]
 [-ThrottleLimit <Int32>] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING

`Disconnect-PSSession`Cmdleten kopplar från en PowerShell-session ("PSSession"), till exempel en som har startats med hjälp av `New-PSSession` cmdleten, från den aktuella sessionen. Därför är PSSession i frånkopplat läge. Du kan ansluta till den frånkopplade PSSession från den aktuella sessionen eller från en annan session på den lokala datorn eller en annan dator.

`Disconnect-PSSession`Cmdleten kopplar bara från öppna PSSessions som är anslutna till den aktuella sessionen. `Disconnect-PSSession` Det går inte att koppla från brutna eller stängda PSSessions eller interaktiva PSSessions som har startats med hjälp av `Enter-PSSession` cmdleten och kan inte koppla bort PSSessions som är anslutna till andra sessioner.

Om du vill återansluta till en frånkopplad PSSession använder du `Connect-PSSession` `Receive-PSSession` cmdletarna eller.

När en PSSession kopplas från fortsätter kommandona i PSSession att köras tills de har slutförts, om inte PSSession timeout-värde eller kommandon i PSSession blockeras av en fullständig utdatabuffert. Om du vill ändra tids gränsen för inaktivitet använder du parametern **IdleTimeoutSec** . Om du vill ändra utdata buffer-läget använder du parametern **OutputBufferingMode** . du kan också använda parametern **InDisconnectedSession** för `Invoke-Command` cmdleten för att köra ett kommando i en frånkopplad session.

Mer information om funktionen frånkopplade sessioner finns [about_Remote_Disconnected_Sessions](./About/about_Remote_Disconnected_Sessions.md).

Denna cmdlet introduceras i Windows PowerShell 3,0.

## EXEMPEL

### Exempel 1 – Koppla från en session efter namn

Det här kommandot kopplar från UpdateSession-PSSession på Server01-datorn från den aktuella sessionen. Kommandot använder parametern **Name** för att identifiera PSSession.

```
PS> Disconnect-PSSession -Name UpdateSession
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
1  UpdateSession   Server01        Disconnected  Microsoft.PowerShell          None
```

Utdata visar att försöket att koppla från lyckades. Sessionstillståndet är frånkopplat och tillgängligheten är ingen, vilket indikerar att sessionen inte är upptagen och kan återanslutas.

### Exempel 2 – Koppla från en session från en angiven dator

Det här kommandot kopplar från ITTask-PSSession på Server12-datorn från den aktuella sessionen.
ITTask-sessionen skapades i den aktuella sessionen och ansluts till Server12-datorn. Kommandot använder `Get-PSSession` cmdleten för att hämta sessionen och `Disconnect-PSSession` cmdleten för att koppla bort den.

```
PS> Get-PSSession -ComputerName Server12 -Name ITTask |
  Disconnect-PSSession -OutputBufferingMode Drop -IdleTimeoutSec 86400
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
1  ITTask          Server12        Disconnected  ITTasks               None
```

`Disconnect-PSSession`Kommandot använder parametern **OutputBufferingMode** för att ange vilket utmatnings läge som ska **släppas**. Den här inställningen säkerställer att skriptet som körs i sessionen kan fortsätta att köras även om buffertens utdatabuffert är full. Eftersom skriptet skriver utdata till en rapport på en fil resurs kan andra utdata gå förlorade utan konsekvens.

Kommandot använder också parametern **IdleTimeoutSec** för att utöka tids gränsen för inaktivitet i sessionen till 24 timmar. Med den här inställningen kan administratören eller andra administratörer återansluta till sessionen för att kontrol lera att skriptet kördes och felsöka vid behov.

### Exempel 3 – använda flera PSSessions på flera datorer

Den här serien med kommandon visar hur `Disconnect-PSSession` cmdleten kan användas i ett företags scenario. I det här fallet startar en ny tekniker ett skript i en session på en fjärrdator och kan köras i ett problem. Teknikern kopplar från sessionen så att en mer erfaren hanterare kan ansluta till sessionen och lösa problemet.

```
PS> $s = New-PSSession -ComputerName Srv1, Srv2, Srv30 -Name ITTask
PS> Invoke-Command $s -FilePath \\Server01\Scripts\Get-PatchStatus.ps1
PS> Get-PSSession -Name ITTask -ComputerName Srv1 | Disconnect-PSSession
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
1 ITTask           Srv1            Disconnected  Microsoft.PowerShell          None

PS> Get-PSSession -ComputerName Srv1, Srv2, Srv30 -Name ITTask
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Srv1            Disconnected  Microsoft.PowerShell          None
 2 ITTask          Srv2            Opened        Microsoft.PowerShell     Available
 3 ITTask          Srv30           Opened        Microsoft.PowerShell     Available

PS> Get-PSSession -ComputerName Srv1 -Name ITTask -Credential Domain01\User01
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 1 ITTask          Srv1            Disconnected  Microsoft.PowerShell          None

PS> $s = Connect-PSSession -ComputerName Srv1 -Name ITTask -Credential Domain01\User01
PS> Invoke-Command -Session $s {dir $home\Scripts\PatchStatusOutput.ps1}
PS> Invoke-Command -Session $s {mkdir $home\Scripts\PatchStatusOutput}
PS> Invoke-Command -Session $s -FilePath \\Server01\Scripts\Get-PatchStatus.ps1
PS> Disconnect-PSSession -Session $s
```

Teknikern börjar genom att skapa sessioner på flera fjärranslutna datorer och köra ett skript i varje session. Det första kommandot använder `New-PSSession` cmdleten för att skapa ITTask-sessionen på tre fjärrdatorer. Kommandot sparar sessionerna i variabeln $s. Det andra kommandot använder parametern **sökväg** för `Invoke-Command` cmdleten för att köra ett skript i sessionerna i variabeln $s.

Det skript som körs på Srv1-datorn genererar oväntade fel. Teknikern kontaktar sin chef och ber om hjälp. Chefen instruerar teknikern att koppla från sessionen så att han kan undersöka den. Det andra kommandot använder `Get-PSSession` cmdleten för att hämta ITTask-sessionen på Srv1-datorn och `Disconnect-PSSession` cmdlet: en för att koppla bort den. Det här kommandot påverkar inte ITTask-sessionerna på de andra datorerna.

Det tredje kommandot använder `Get-PSSession` cmdleten för att hämta ITTask-sessionerna. Utdata visar att ITTask-sessionerna på Srv2-och Srv30-datorerna inte påverkades av kommandot för från koppling.

Chefen loggar in på sin hem dator, ansluter till företagets nätverk, startar PowerShell och använder `Get-PSSession` cmdleten för att hämta ITTask-sessionen på den Srv1 datorn. Han använder autentiseringsuppgifterna för teknikern för att få åtkomst till sessionen.

Därefter använder chefen `Connect-PSSession` cmdleten för att ansluta till ITTask-sessionen på datorn med Srv1. Kommandot sparar sessionen i variabeln $s.

Chefen använder `Invoke-Command` cmdleten för att köra vissa diagnostiska kommandon i sessionen i `$s` variabeln. Han känner av att skriptet misslyckades eftersom det inte gick att hitta en obligatorisk katalog.
Chefen använder `MkDir` funktionen för att skapa katalogen och startar sedan om `Get-PatchStatus.ps1` skriptet och kopplar från sessionen. Chefen rapporterar sina resultat till teknikern, vilket tyder på att han återansluter till sessionen för att slutföra uppgifterna och ber honom att lägga till ett kommando i `Get-PatchStatus.ps1` skriptet som skapar den nödvändiga katalogen om den inte finns.

### Exempel 4 – ändra timeout-värdet för en PSSession

Det här exemplet visar hur du korrigerar värdet för egenskapen **idleTimeout** för en session så att den kan kopplas från.

Egenskapen timeout för inaktivitet i en session är kritisk för frånkopplade sessioner, eftersom den fastställer hur länge en frånkopplad session upprätthålls innan den tas bort. Du kan ställa in timeout-alternativet för inaktivitet när du skapar en session och när du kopplar från den. Standardvärdena för tids gränsen för inaktivitet i en session ställs in i `$PSSessionOption` Preference-variabeln på den lokala datorn och i konfigurationen på fjärrdatorn. Värden som har ställts in för sessionen har företräde framför värden som anges i konfigurationen av sessionen, men sessionsgränser får inte överskrida kvoter som angetts i konfigurationen för sessionen, till exempel **MaxIdleTimeoutMs** -värdet.

```
PS> $Timeout = New-PSSessionOption -IdleTimeout 172800000
PS> $s = New-PSSession -Computer Server01 -Name ITTask -SessionOption $Timeout
PS> Disconnect-PSSession -Session $s
Disconnect-PSSession : The session ITTask cannot be disconnected because the specified
idle timeout value 172800(seconds) is either greater than the server maximum allowed
43200 (seconds) or less that the minimum allowed60(seconds).  Choose an idle time out
value that is within the allowed range and try again.

PS> Invoke-Command -ComputerName Server01 {Get-PSSessionConfiguration Microsoft.PowerShell} |
 Format-List -Property *

Architecture                  : 64
Filename                      : %windir%\system32\pwrshplugin.dll
ResourceUri                   : http://schemas.microsoft.com/powershell/microsoft.powershell
MaxConcurrentCommandsPerShell : 1000
UseSharedProcess              : false
ProcessIdleTimeoutSec         : 0
xmlns                         : http://schemas.microsoft.com/wbem/wsman/1/config/PluginConfiguration
MaxConcurrentUsers            : 5
lang                          : en-US
SupportsOptions               : true
ExactMatch                    : true
RunAsUser                     :
IdleTimeoutms                 : 7200000
PSVersion                     : 3.0
OutputBufferingMode           : Block
AutoRestart                   : false
SecurityDescriptorSddl        : O:NSG:BAD:P(A;;GA;;;BA)S:P(AU;FA;GA;;;WD)(AU;SA;GXGW;;;WD)
MaxMemoryPerShellMB           : 1024
MaxIdleTimeoutms              : 2147483647
Uri                           : http://schemas.microsoft.com/powershell/microsoft.powershell
SDKVersion                    : 2
Name                          : microsoft.powershell
XmlRenderingType              : text
Capability                    : {Shell}
RunAsPassword                 :
MaxProcessesPerShell          : 15
ParentResourceUri             : http://schemas.microsoft.com/powershell/microsoft.powershell
Enabled                       : true
MaxShells                     : 25
MaxShellsPerUser              : 25
Permission                    : BUILTIN\Administrators AccessAllowed
PSComputerName                : localhost
RunspaceId                    : aea84310-6dbf-4c21-90ac-13980039925a
PSShowComputerName            : True


PS> $s.Runspace.ConnectionInfo
ConnectionUri                     : http://Server01/wsman
ComputerName                      : Server01
Scheme                            : http
Port                              : 80
AppName                           : /wsman
Credential                        :
ShellUri                          : http://schemas.microsoft.com/powershell/Microsoft.PowerShell
AuthenticationMechanism           : Default
CertificateThumbprint             :
MaximumConnectionRedirectionCount : 5
MaximumReceivedDataSizePerCommand :
MaximumReceivedObjectSize         : 209715200
UseCompression                    : True
NoMachineProfile                  : False
ProxyAccessType                   : None
ProxyAuthentication               : Negotiate
ProxyCredential                   :
SkipCACheck                       : False
SkipCNCheck                       : False
SkipRevocationCheck               : False
NoEncryption                      : False
UseUTF16                          : False
OutputBufferingMode               : Drop
IncludePortInSPN                  : False
Culture                           : en-US
UICulture                         : en-US
OpenTimeout                       : 180000
CancelTimeout                     : 60000
OperationTimeout                  : 180000
IdleTimeout                       : 172800000

PS> Disconnect-PSSession $s -IdleTimeoutSec 43200
Id Name            ComputerName    State         ConfigurationName     Availability
-- ----            ------------    -----         -----------------     ------------
 4 ITTask          Server01        Disconnected  Microsoft.PowerShell          None

PS> $s.Runspace.ConnectionInfo.IdleTimeout
43200000
```

Det första kommandot använder `New-PSSessionOption` cmdleten för att skapa ett session alternativ-objekt. Den använder **idleTimeout** -parametern för att ange en tids gräns för inaktivitet på 48 timmar (172800000 millisekunder). Kommandot sparar objektet Session-alternativ i variabeln $Timeout.

Det andra kommandot använder `New-PSSession` cmdleten för att skapa ITTask-sessionen på Server01-datorn. Kommandot sparar sessionen i variabeln $s. Värdet för parametern **SessionOption** är tids gränsen på 48 timmar för inaktivitet i $timeout variabeln.

Det tredje kommandot kopplar från ITTask-sessionen i variabeln $s. Kommandot Miss lyckas eftersom tids gränsen för inaktivitet i sessionen överskrider **MaxIdleTimeoutMs** kvoten i sessionen. Eftersom tids gränsen för inaktivitet inte används förrän sessionen kopplas från, kan denna överträdelse gå ur bruk medan sessionen används.

Det fjärde kommandot använder `Invoke-Command` cmdleten för att köra ett `Get-PSSessionConfiguration` kommando för konfigurationen av Microsoft. PowerShell-sessionen på Server01-datorn. Kommandot använder `Format-List` cmdleten för att visa alla egenskaper för sessionens konfiguration i en lista. Utdata visar att egenskapen **MaxIdleTimeoutMS** , som upprättar det högsta tillåtna **idleTimeout** -värdet för sessioner som använder sessionen, är 43200000 millisekunder (12 timmar).

Det femte kommandot hämtar sessionens alternativ värden i variabeln $s. Värdena för många session-alternativ är egenskaper för egenskapen **ConnectionInfo** för sessionens **körnings utrymme** -egenskap. Utdata visar att värdet för egenskapen **idleTimeout** i sessionen är 172800000 millisekunder (48 timmar), vilket bryter mot **MaxIdleTimeoutMs** -kvoten på 12 timmar i konfigurationen av sessionen. Du kan lösa den här konflikten genom att använda parametern **ConfigurationName** för att välja en annan sessions konfiguration eller använda **idleTimeout** -parametern för att minska tids gränsen för inaktivitet för sessionen.

Det sjätte kommandot kopplar från sessionen. Parametern **IdleTimeoutSec** används för att ange tids gränsen för inaktivitet till maximalt 12 timmar.

Det sjunde kommandot hämtar värdet för egenskapen **idleTimeout** för den frånkopplade sessionen, som mäts i millisekunder. Resultatet bekräftar att kommandot har slutförts.

## PARAMETRAR

### -ID

Kopplar från sessioner med angivet sessions-ID. Skriv ett eller flera ID: n (avgränsade med kommatecken) eller Använd intervall operatorn (..) för att ange ett intervall med ID: n.

Använd cmdleten för att hämta ID för en session `Get-PSSession` . Instans-ID: t lagras i sessionens **ID-** egenskap.

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -IdleTimeoutSec

Ändrar timeout-värdet för inaktivitet för den frånkopplade PSSession. Ange ett värde i sekunder. Det minsta värdet är 60 (1 minut).

Tids gränsen för inaktivitet avgör hur länge den frånkopplade PSSession upprätthålls på fjärrdatorn. När tids gränsen går ut tas PSSession bort.

Frånkopplade PSSessions anses vara inaktiva från det ögonblick då de kopplas från, även om kommandon körs i den frånkopplade sessionen.

Standardvärdet för tids gränsen för inaktivitet i en session anges av värdet för **IdleTimeoutMs** -egenskapen i konfigurationen för sessionen. Standardvärdet är 7200000 millisekunder (2 timmar).

Värdet för den här parametern prioriteras över värdet för egenskapen **idleTimeout** i variabeln $PSSessionOption och standardvärdet för tids gräns för inaktivitet i sessionen. Värdet får dock inte överstiga värdet för **MaxIdleTimeoutMs** -egenskapen i konfigurationen av sessionen. Standardvärdet för **MaxIdleTimeoutMs** är 12 timmar (43200000 millisekunder).

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 60
Accept pipeline input: False
Accept wildcard characters: False
```

### -InstanceId

Kopplar från sessioner med angivet instans-ID.

Instans-ID är ett GUID som unikt identifierar en session på en lokal dator eller fjärrdator. Instans-ID: t är unikt, även över flera sessioner på flera datorer.

Använd cmdleten för att hämta instans-ID för en session `Get-PSSession` . Instans-ID: t lagras i sessionens **InstanceID** -egenskap.

```yaml
Type: System.Guid[]
Parameter Sets: InstanceId
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

Kopplar från sessioner med angivna egna namn. Jokertecken är tillåtna.

Använd cmdleten för att hämta det egna namnet på en session `Get-PSSession` . Det egna namnet lagras i sessionens **namn** -egenskap.

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### – Session

Kopplar från den angivna PSSessions. Ange PSSession-objekt, till exempel de som `New-PSSession` cmdleten returnerar. Du kan också skicka ett PSSession-objekt till `Disconnect-PSSession` .

`Get-PSSession`Cmdleten kan hämta alla PSSessions som avslutas på en fjärrdator, inklusive PSSessions som är frånkopplade och PSSessions som är anslutna till andra sessioner på andra datorer. `Disconnect-PSSession` kopplar bara från PSSession som är anslutna till den aktuella sessionen. Om du rör andra PSSessions till `Disconnect-PSSession` `Disconnect-PSSession` Miss lyckas kommandot.

```yaml
Type: System.Management.Automation.Runspaces.PSSession[]
Parameter Sets: Session
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -ThrottleLimit

Anger begränsnings begränsningen för `Disconnect-PSSession` kommandot.

Begränsnings gränsen är det maximala antalet samtidiga anslutningar som kan upprättas för att köra det här kommandot. Om du utelämnar den här parametern eller anger värdet 0, används standardvärdet 32.

Begränsnings gränsen gäller endast för det aktuella kommandot, inte för sessionen eller datorn.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 32
Accept pipeline input: False
Accept wildcard characters: False
```

### -OutputBufferingMode

Anger hur kommandoutdata hanteras i den frånkopplade sessionen när utdatabufferten är full. Standardvärdet är **block**.

Om kommandot i den frånkopplade sessionen returnerar utdata och utdata buffrar, avgör värdet för parametern effektivt om kommandot fortsätter att köras medan sessionen kopplas från. Värdet **block** pausar kommandot tills sessionen återansluts. Ett **Drop** -värde gör att kommandot kan slutföras, men data kan gå förlorade. När du använder **Drop** -värdet dirigerar du om kommandots utdata till en fil på disk.

Giltiga värden är:

- **Blockera** : när utdatabufferten är full pausas körningen tills bufferten är klar.
- **Drop** : när utdatabufferten är full fortsätter körningen. När nya utdata sparas, ignoreras det äldsta resultatet.
- **Ingen** : inget utdata buffer-läge har angetts. Värdet för **OutputBufferingMode** -egenskapen i konfigurationen används för den frånkopplade sessionen.

```yaml
Type: System.Management.Automation.Runspaces.OutputBufferingMode
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Block
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm

Uppmanar dig att bekräfta innan du kör cmdleten.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

Visar vad som skulle hända om cmdleten kördes.
Cmdleten körs inte.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](./About/about_CommonParameters.md).

## INDATA

### System. Management. Automation. körnings utrymmen. PSSession

Du kan skicka vidare en session till `Disconnect-PSSession` .

## UTDATA

### System. Management. Automation. körnings utrymmen. PSSession

`Disconnect-PSSession` Returnerar ett objekt som representerar sessionen som den kopplades från.

## ANTECKNINGAR

- `Disconnect-PSSession`Cmdleten fungerar bara när lokala och fjärranslutna datorer kör PowerShell 3,0 eller senare.
- Om du använder `Disconnect-PSSession` cmdleten i en frånkopplad session har kommandot ingen påverkan på sessionen och det genererar inga fel.
- Frånkopplade loopback-sessioner med interaktiva säkerhetstoken (de som skapats med parametern **EnableNetworkAccess** ) kan bara återanslutas från den dator där sessionen skapades. Den här begränsningen skyddar datorn från skadlig åtkomst.
- När du kopplar från en PSSession **kopplas sessionstillståndet ned** och tillgängligheten är **ingen**.

  Värdet för egenskapen **State** är i förhållande till den aktuella sessionen. Därför innebär värdet **frånkopplat** att PSSession inte är ansluten till den aktuella sessionen. Det innebär dock inte att PSSession är frånkopplad från alla sessioner. Den kan vara ansluten till en annan session. Använd egenskapen **tillgänglighet** för att avgöra om du kan ansluta eller återansluta till sessionen.

  **Tillgänglighet** svärdet **none** anger att du kan ansluta till sessionen. Värdet **upptagen** anger att du inte kan ansluta till PSSession eftersom det är anslutet till en annan session.

  Mer information om värdena för egenskapen **State** för sessioner finns i [RunspaceState-uppräkning](/dotnet/api/system.management.automation.runspaces.runspacestate).

  Mer information om värdena för egenskapen **Availability** för sessioner finns i [RunspaceAvailability-uppräkning](/dotnet/api/system.management.automation.runspaces.runspaceavailability).

## RELATERADE LÄNKAR

[Anslut – PSSession](Connect-PSSession.md)

[Retur-PSSession](Enter-PSSession.md)

[Avsluta-PSSession](Exit-PSSession.md)

[Get-PSSession](Get-PSSession.md)

[Get-PSSessionConfiguration](Get-PSSessionConfiguration.md)

[New-PSSession](New-PSSession.md)

[New-PSSessionOption](New-PSSessionOption.md)

[New-PSTransportOption](New-PSTransportOption.md)

[Ta emot – PSSession](Receive-PSSession.md)

[Registrera – PSSessionConfiguration](Register-PSSessionConfiguration.md)

[Remove-PSSession](Remove-PSSession.md)

[about_PSSessions](About/about_PSSessions.md)

[about_Remote](About/about_Remote.md)

[about_Remote_Disconnected_Sessions](About/about_Remote_Disconnected_Sessions.md)

