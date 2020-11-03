---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 09/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-wmiobject?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-WmiObject
ms.openlocfilehash: ed759ff3d0dd35cd55f9dac5a2d76e36eac4dc6c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266103"
---
# Get-WmiObject

## SAMMANFATTNING
Hämtar instanser av Windows Management Instrumentation (WMI)-klasser eller information om tillgängliga klasser.

## SYNTAX

### fråga (standard)

```
Get-WmiObject [-Class] <String> [[-Property] <String[]>] [-Filter <String>] [-Amended] [-DirectRead]
 [-AsJob] [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>]
 [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>]
 [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>] [<CommonParameters>]
```

### lista

```
Get-WmiObject [[-Class] <String>] [-Recurse] [-Amended] [-List] [-AsJob]
 [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>] [-Locale <String>]
 [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [<CommonParameters>]
```

### WQLQuery

```
Get-WmiObject [-Amended] [-DirectRead] -Query <String> [-AsJob]
 [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>] [-Locale <String>]
 [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [<CommonParameters>]
```

### klass

```
Get-WmiObject [-Amended] [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges]
 [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [<CommonParameters>]
```

### path

```
Get-WmiObject [-Amended] [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges]
 [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [<CommonParameters>]
```

## BESKRIVNING

Från och med PowerShell 3,0 har denna cmdlet ersatts av `Get-CimInstance` .

`Get-WmiObject`Cmdlet: en hämtar instanser av WMI-klasser eller information om tillgängliga WMI-klasser. Om du vill ange en fjärrdator använder du parametern **computername** . Om **list** parametern anges, hämtar cmdleten information om de WMI-klasser som är tillgängliga i en angiven namnrymd. Om **Frågeparametern** anges kör cmdleten en WQL-instruktion (WMI Query Language).

`Get-WmiObject`Cmdlet: en använder inte Windows PowerShell-fjärrkommunikation för att utföra fjärråtgärder.
Du kan använda parametern **computername** för `Get-WmiObject` cmdleten även om datorn inte uppfyller kraven för Windows PowerShell-fjärrkommunikation eller inte har kon figurer ATS för fjärr kommunikation i Windows PowerShell.

Från och med Windows PowerShell 3,0 har egenskapen **__Server** för det objekt som `Get-WmiObject` returnerar ett **PSComputerName** -alias. Detta gör det enklare att inkludera käll datorns namn i utdata och rapporter.

## EXEMPEL

### Exempel 1: Hämta processer på den lokala datorn

Det här exemplet hämtar processerna på den lokala datorn.

```powershell
Get-WmiObject -Class Win32_Process
```

### Exempel 2: hämtar tjänster på en fjärrdator

Det här exemplet hämtar tjänsterna på en fjärrdator. Parametern **computername** anger IP-adressen för en fjärrdator. Som standard måste det aktuella användar kontot vara medlem i gruppen **Administratörer** på fjärrdatorn.

```powershell
Get-WmiObject -Class Win32_Service -ComputerName 10.1.4.62
```

### Exempel 3: hämta WMI-klasser i roten eller standard namn området för den lokala datorn

Det här exemplet hämtar WMI-klasserna i roten eller standard namn området för den lokala datorn.

```powershell
Get-WmiObject -Namespace "root/default" -List
```

### Exempel 4: Hämta en namngiven tjänst på flera datorer

Det här exemplet hämtar WinRM-tjänsten på de datorer som anges av värdet för parametern **computername** .

```powershell
Get-WmiObject -Query "select * from win32_service where name='WinRM'" -ComputerName Server01, Server02 |
  Format-List -Property PSComputerName, Name, ExitCode, Name, ProcessID, StartMode, State, Status
```

```Output
PSComputerName : SERVER01
Name           : WinRM
ExitCode       : 0
Name           : WinRM
ProcessID      : 844
StartMode      : Auto
State          : Running
Status         : OK

PSComputerName : SERVER02
Name           : WinRM
ExitCode       : 0
Name           : WinRM
ProcessID      : 932
StartMode      : Auto
State          : Running
Status         : OK
```

En pipeline-operator (|) skickar utdata till `Format-List` cmdleten, som lägger till egenskapen **PSComputerName** i standardutdata. **PSComputerName** är ett alias för egenskapen **__Server** för de objekt som `Get-WmiObject` returneras. Det här aliaset introducerades i PowerShell 3,0.

### Exempel 5: stoppa en tjänst på en fjärrdator

I det här exemplet stoppas WinRM-tjänsten på en fjärrdator. `Get-WmiObject` hämtar instansen av WinRM-tjänsteobjektet på Server01. Sedan anropar den **Stop** -metoden i **Win32_Service** WMI-klassen för objektet.

```powershell
(Get-WmiObject -Class Win32_Service -Filter "name='WinRM'" -ComputerName Server01).StopService()
```

Detta motsvarar att använda `Stop-Service` cmdleten.

### Exempel 6: Hämta BIOS på den lokala datorn

Det här exemplet hämtar BIOS-information från den lokala datorn. **Egenskaps** parametern för `Format-List` cmdleten används för att visa alla egenskaper för det returnerade objektet i en lista. Som standard visas endast en delmängd av de egenskaper som definierats i `Types.ps1xml` konfigurations filen.

```powershell
Get-WmiObject -Class Win32_Bios | Format-List -Property *
```

```Output
Status                : OK
Name                  : Phoenix ROM BIOS PLUS Version 1.10 A05
Caption               : Phoenix ROM BIOS PLUS Version 1.10 A05
SMBIOSPresent         : True
__GENUS               : 2
__CLASS               : Win32_BIOS
__SUPERCLASS          : CIM_BIOSElement
__DYNASTY             : CIM_ManagedSystemElement
__RELPATH             : Win32_BIOS.Name="Phoenix ROM BIOS PLUS Version 1.10
__PROPERTY_COUNT      : 27
__DERIVATION          : {CIM_BIOSElement, CIM_SoftwareElement, CIM_LogicalElement,
__SERVER              : Server01
__NAMESPACE           : root\cimv2
__PATH                : \\SERVER01\root\cimv2:Win32_BIOS.Name="Phoenix ROM BIOS
BiosCharacteristics   : {7, 9, 10, 11...}
BIOSVersion           : {DELL   - 15, Phoenix ROM BIOS PLUS Version 1.10 A05}
BuildNumber           :
CodeSet               :
CurrentLanguage       : en|US|iso8859-1
Description           : Phoenix ROM BIOS PLUS Version 1.10 A05
IdentificationCode    :
InstallableLanguages  : 1
InstallDate           :
LanguageEdition       :
ListOfLanguages       : {en|US|iso8859-1}
Manufacturer          : Dell Inc.
OtherTargetOS         :
PrimaryBIOS           : True
ReleaseDate           : 20101103000000.000000+000
SerialNumber          : 8VDM9P1
SMBIOSBIOSVersion     : A05
SMBIOSMajorVersion    : 2
SMBIOSMinorVersion    : 6
SoftwareElementID     : Phoenix ROM BIOS PLUS Version 1.10 A05
SoftwareElementState  : 3
TargetOperatingSystem : 0
Version               : DELL   - 15
Scope                 : System.Management.ManagementScope
Path                  : \\SERVER01\root\cimv2:Win32_BIOS.Name="Phoenix ROM BIOS
Options               : System.Management.ObjectGetOptions
ClassPath             : \\JUNE-PC\root\cimv2:Win32_BIOS
Properties            : {BiosCharacteristics, BIOSVersion, BuildNumber, Caption...}
SystemProperties      : {__GENUS, __CLASS, __SUPERCLASS, __DYNASTY...}
Qualifiers            : {dynamic, Locale, provider, UUID}
Site                  :
Container             :
```

### Exempel 7: Hämta tjänsterna på en fjärrdator

I det här exemplet används parametern **Credential** för `Get-WmiObject` cmdleten för att hämta tjänsterna på en fjärrdator. Värdet för parametern **Credential** är ett användar konto namn. Användaren uppmanas att ange ett lösen ord.

```powershell
Get-WmiObject Win32_Service -Credential FABRIKAM\administrator -ComputerName Fabrikam
```

> [!NOTE]
> Det går inte att använda autentiseringsuppgifter när den lokala datorn riktas mot.

## PARAMETRAR

### -Ändrad

Hämtar eller anger ett värde som anger om de objekt som returneras från WMI ska innehålla ändrad information. Normalt är den ändrade informationen lokaliserad information, till exempel beskrivningar av objekt och egenskaper, som är kopplade till WMI-objektet.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – AsJob

Kör kommandot som ett bakgrunds jobb. Använd den här parametern för att köra kommandon som tar lång tid att slutföra.

När du använder parametern **AsJob** returnerar kommandot ett objekt som representerar bakgrunds jobbet och visar sedan kommando tolken. Du kan fortsätta att arbeta i sessionen medan jobbet är klart. Om `Get-WmiObject` används på en fjärrdator skapas jobbet på den lokala datorn och resultaten från fjärrdatorer returneras automatiskt till den lokala datorn. Använd cmdlet: arna som innehåller jobb-cmdletar för att hantera jobbet. Använd cmdleten för att hämta jobb resultatet `Receive-Job` .

> [!NOTE]
> Om du vill använda den här parametern med fjärrdatorer måste lokala och fjärranslutna datorer konfigureras för fjärr kommunikation. Dessutom måste du starta Windows PowerShell med alternativet "kör som administratör" i Windows Vista och senare versioner av Windows. Mer information finns i [about_Remote_Requirements](../Microsoft.PowerShell.Core/about/about_Remote_Requirements.md).

Mer information om bakgrunds jobb i Windows PowerShell finns i [about_Jobs](../Microsoft.PowerShell.Core/about/about_Jobs.md) och [about_Remote_Jobs](../Microsoft.PowerShell.Core/about/about_Remote_Jobs.md).

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Autentisering

Anger den autentiseringsnivå som ska användas med WMI-anslutningen.
Giltiga värden är:

- -1: oförändrad
- 0: standard
- 1: ingen (ingen autentisering utförs)
- 2: Anslut (autentisering utförs endast när klienten upprättar en relation med programmet.)
- 3: anrop (autentisering utförs endast i början av varje anrop när programmet tar emot begäran.)
- 4: paket (autentisering utförs på alla data som tas emot från klienten).
- 5: PacketIntegrity (alla data som överförs mellan klienten och programmet autentiseras och verifieras.)
- 6: PacketPrivacy (egenskaperna för de andra autentiseringsnivåer används och alla data krypteras.)

```yaml
Type: System.Management.AuthenticationLevel
Parameter Sets: (All)
Aliases:
Accepted values: Default, None, Connect, Call, Packet, PacketIntegrity, PacketPrivacy, Unchanged

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Authority

Anger den auktoritet som ska användas för att autentisera WMI-anslutningen. Du kan ange standard-NTLM eller Kerberos-autentisering. Om du vill använda NTLM anger du auktoritets inställningen till `ntlmdomain:<DomainName>` , där `<DomainName>` identifierar ett giltigt NTLM-domännamn. Om du vill använda Kerberos anger du `kerberos:<DomainName>\<ServerName>` . Du kan inte inkludera auktoritets inställningen när du ansluter till den lokala datorn.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Klass

Anger namnet på en WMI-klass. När den här parametern används hämtar cmdleten instanser av WMI-klassen.

```yaml
Type: System.String
Parameter Sets: query, list
Aliases: ClassName

Required: True (query), False (list)
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

Anger mål datorn för hanterings åtgärden. Ange ett fullständigt kvalificerat domän namn (FQDN), ett NetBIOS-namn eller en IP-adress. När fjärrdatorn finns i en annan domän än den lokala datorn krävs det fullständigt kvalificerade domän namnet.

Standard är den lokala datorn. Om du vill ange den lokala datorn, till exempel i en lista över dator namn, använder du "localhost", namnet på den lokala datorn eller en punkt (.).

Den här parametern är inte beroende av Windows PowerShell-fjärrkommunikation, som använder WS-Management. Du kan använda parametern **computername** för `Get-WmiObject` även om datorn inte är konfigurerad för att köra WS-Management fjärrkommandon.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Cn

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential

Anger ett användar konto som har behörighet att utföra den här åtgärden. Standard är den aktuella användaren. Ange ett användar namn, till exempel "user01", "Domain01\User01" eller User@Contoso.com . Eller ange ett **PSCredential** -objekt, till exempel ett objekt som returneras av `Get-Credential` cmdleten. När du anger ett användar namn uppmanas du att ange ett lösen ord. Det går inte att använda autentiseringsuppgifter när den lokala datorn riktas mot.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DirectRead

Anger om direkt åtkomst till WMI-providern begärs för den angivna klassen utan hänsyn till dess basklass eller dess härledda klasser.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: query, WQLQuery
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -EnableAllPrivileges

Aktiverar alla behörigheter för den aktuella användaren innan kommandot gör WMI-anropet.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Filter

Anger en **WHERE** -sats som ska användas som ett filter. Använder syntaxen för WMI Query Language (WQL).

> [!IMPORTANT]
> Ta inte med nyckelordet **WHERE** i värdet för parametern. Följande kommandon returnerar till exempel bara de logiska diskar som har en **DeviceID** av "c:" och tjänster som har namnet "WinRM" utan att använda nyckelordet **WHERE** .

`Get-WmiObject Win32_LogicalDisk -filter "DeviceID = 'c:' "`

`Get-WmiObject win32_service -filter "name='WinRM'"`

```yaml
Type: System.String
Parameter Sets: query
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Personifiering

Anger personifieringsnivån som ska användas.

De acceptabla värdena för den här parametern är:

- 0: standard. Läser det lokala registret för standard personifieringsnivån. Standardvärdet är inställt på att **Personifiera**.
- 1: Anonym. Döljer anroparens autentiseringsuppgifter.
- 2: identifiera. Tillåter att objekt frågar efter anroparens autentiseringsuppgifter.
- 3: personifiera. Tillåter att objekt använder autentiseringsuppgifterna för anroparen.
- 4: delegera. Tillåter objekt att tillåta att andra objekt använder autentiseringsuppgifterna för anroparen.

```yaml
Type: System.Management.ImpersonationLevel
Parameter Sets: (All)
Aliases:
Accepted values: Default, Anonymous, Identify, Impersonate, Delegate

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Lista

Hämtar namnen på WMI-klasserna i namn området för WMI-lagringsplatsen som anges av **namn områdes** parametern.

Om du anger **list** parametern, men inte **namn områdes** parametern, `Get-WmiObject` använder **Root\Cimv2** -namnområdet som standard. Denna cmdlet använder inte **standard namn områdets** register post i `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\WBEM\Scripting` register nyckeln för att fastställa standard namn området.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Locale

Anger det önskade språket för WMI-objekt.
Ange ett värde i MS_ \<LCID\> format.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Namnrymd

När den används med **klassen Class** , anger **namespace** -parametern namn området för WMI-lagringsplatsen där den angivna WMI-klassen finns. När det används med parametern **list** anger den det namn område som information om WMI-klass ska samlas in från.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: NS

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Egenskap

Anger egenskaper för WMI-klass som denna cmdlet hämtar information från. Ange egenskaps namnen.

```yaml
Type: System.String[]
Parameter Sets: query
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Fråga

Kör den angivna WQL-instruktionen (WMI Query Language). Den här parametern stöder inte händelse frågor.

```yaml
Type: System.String
Parameter Sets: WQLQuery
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Rekursivt

Söker efter det aktuella namn området och alla andra namn områden för klass namnet som anges av **klass** parametern.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit

Anger det maximala antalet WMI-åtgärder som kan köras samtidigt. Den här parametern är endast giltig när parametern **AsJob** används i kommandot.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Inget

Du kan inte skicka pipe-ininformation till `Get-WmiObject` .

## UTDATA

### PSObject eller system. Management. Automation. RemotingJob

När du använder parametern **AsJob** , returnerar cmdleten ett Job-objekt. Annars är det objekt som `Get-WmiObject` returnerar beroende av värdet för **klass** parametern.

## ANTECKNINGAR

För att få åtkomst till WMI-information på en fjärrdator måste cmdleten köras under ett konto som är medlem i den lokala gruppen Administratörer på fjärrdatorn. Eller så kan standard åtkomst kontrollen i WMI-namnrymden för fjärrlagringsplatsen ändras för att ge åtkomst behörighet till andra konton.

Endast några av egenskaperna för varje WMI-klass visas som standard. Uppsättningen egenskaper som visas för varje WMI-klass anges i Types.ps1XML-konfigurationsfilen. Använd cmdletarna eller för att hämta alla egenskaper för ett WMI-objekt `Get-Member` `Format-List` .

## RELATERADE LÄNKAR

[Invoke-WmiMethod](Invoke-WmiMethod.md)

[Remove-WmiObject](Remove-WmiObject.md)

[Set-WmiInstance](Set-WmiInstance.md)

[Get-WSManInstance](../Microsoft.WsMan.Management/Get-WSManInstance.md)

[Invoke-WSManAction](../Microsoft.WsMan.Management/Invoke-WSManAction.md)

[New-WSManInstance](../Microsoft.WsMan.Management/New-WSManInstance.md)

[Remove-WSManInstance](../Microsoft.WsMan.Management/Remove-WSManInstance.md)
