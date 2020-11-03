---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-wmiinstance?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-WmiInstance
ms.openlocfilehash: 03288a2ffbef416937b2c92a7d08a5aed49ffb43
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265376"
---
# Set-WmiInstance

## SAMMANFATTNING
Skapar eller uppdaterar en instans av en befintlig Windows Management Instrumentation (WMI)-klass.

## SYNTAX

### klass (standard)

```
Set-WmiInstance [-Class] <String> [-Arguments <Hashtable>] [-PutType <PutType>] [-AsJob]
 [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>] [-Locale <String>]
 [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### objekt

```
Set-WmiInstance -InputObject <ManagementObject> [-Arguments <Hashtable>] [-PutType <PutType>] [-AsJob]
 [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### path

```
Set-WmiInstance -Path <String> [-Arguments <Hashtable>] [-PutType <PutType>] [-AsJob]
 [-Impersonation <ImpersonationLevel>] [-Authentication <AuthenticationLevel>] [-Locale <String>]
 [-EnableAllPrivileges] [-Authority <String>] [-Credential <PSCredential>] [-ThrottleLimit <Int32>]
 [-ComputerName <String[]>] [-Namespace <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### WQLQuery

```
Set-WmiInstance [-PutType <PutType>] [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### DocumentDB

```
Set-WmiInstance [-PutType <PutType>] [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### lista

```
Set-WmiInstance [-PutType <PutType>] [-AsJob] [-Impersonation <ImpersonationLevel>]
 [-Authentication <AuthenticationLevel>] [-Locale <String>] [-EnableAllPrivileges] [-Authority <String>]
 [-Credential <PSCredential>] [-ThrottleLimit <Int32>] [-ComputerName <String[]>] [-Namespace <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING
`Set-WmiInstance`Cmdleten skapar eller uppdaterar en instans av en befintlig Windows Management Instrumentation (WMI)-klass.
Den skapade eller uppdaterade instansen skrivs till WMI-lagringsplatsen.

Nya CIM-cmdletar, introducerade Windows PowerShell 3,0, utför samma uppgifter som WMI-cmdlets.
CIM-cmdletar följer WS-Management (WSMan)-standarder och med Common Information Model (CIM)-standarden.
Detta gör att cmdlets kan använda samma metoder för att hantera Windows-baserade datorer och de som kör andra operativ system.
I stället för att använda bör `Set-WmiInstance` du överväga att använda cmdletarna [set-CimInstance](/powershell/module/cimcmdlets/set-ciminstance) eller [New-CimInstance](/powershell/module/cimcmdlets/new-ciminstance) .

## EXEMPEL

### Exempel 1: ange nivån för WMI-loggning

```
PS C:\> Set-WmiInstance -Class Win32_WMISetting -Argument @{LoggingLevel=2}
__GENUS                        : 2
__CLASS                        : Win32_WMISetting
__SUPERCLASS                   : CIM_Setting
__DYNASTY                      : CIM_Setting
__RELPATH                      : Win32_WMISetting=@
__PROPERTY_COUNT               : 27
__DERIVATION                   : {CIM_Setting}
__SERVER                       : SYSTEM01
__NAMESPACE                    : root\cimv2
__PATH                         : \\SYSTEM01\root\cimv2:Win32_WMISetting=@
ASPScriptDefaultNamespace      : \\root\cimv2
ASPScriptEnabled               : False
AutorecoverMofs                : {%windir%\system32\wbem\cimwin32.mof, %windir%\system32\wbem\ncprov.mof, %windir%\syst
em32\wbem\wmipcima.mof, %windir%\system32\wbem\secrcw32.mof...}
AutoStartWin9X                 :
BackupInterval                 :
BackupLastTime                 :
BuildVersion                   : 6001.18000
Caption                        :
DatabaseDirectory              : C:\Windows\system32\wbem\repository
DatabaseMaxSize                :
Description                    :
EnableAnonWin9xConnections     :
EnableEvents                   : False
EnableStartupHeapPreallocation : False
HighThresholdOnClientObjects   :
HighThresholdOnEvents          : 20000000
InstallationDirectory          : C:\Windows\system32\wbem
LastStartupHeapPreallocation   :
LoggingDirectory               : C:\Windows\system32\wbem\Logs\
LoggingLevel                   : 2
LowThresholdOnClientObjects    :
LowThresholdOnEvents           : 10000000
MaxLogFileSize                 : 65536
MaxWaitOnClientObjects         :
MaxWaitOnEvents                : 2000
MofSelfInstallDirectory        :
SettingID                      :
```

Det här kommandot anger WMI-loggnings nivån till 2.
Kommandot skickar egenskapen som ska ställas in och värdet, som tillsammans betraktas som ett värde par, i argument parametern.
Parametern använder en hash-tabell som definieras av konstruktionen @ {Property = Value}.
Den klass information som returneras visar det nya värdet.

### Exempel 2: skapa en miljö variabel och dess värde

```
PS C:\> Set-WmiInstance -Class win32_environment -Argument @{Name="testvar";VariableValue="testvalue";UserName="<SYSTEM>"}
__GENUS          : 2
__CLASS          : Win32_Environment
__SUPERCLASS     : CIM_SystemResource
__DYNASTY        : CIM_ManagedSystemElement
__RELPATH        : Win32_Environment.Name="testvar",UserName="<SYSTEM>"
__PROPERTY_COUNT : 8
__DERIVATION     : {CIM_SystemResource, CIM_LogicalElement, CIM_ManagedSystemElement}
__SERVER         : SYSTEM01
__NAMESPACE      : root\cimv2
__PATH           : \\SYSTEM01\root\cimv2:Win32_Environment.Name="testvar",UserName="<SYSTEM>"
Caption          : <SYSTEM>\testvar
Description      : <SYSTEM>\testvar
InstallDate      :
Name             : testvar
Status           : OK
SystemVariable   : True
UserName         : <SYSTEM>
VariableValue    : testvalue
```

Det här kommandot skapar testvar-miljövariabeln som har värdet TestValue.
Det gör du genom att skapa en ny instans av klassen **Win32_Environment** WMI.
Den här åtgärden kräver lämpliga autentiseringsuppgifter och du kan behöva starta om Windows PowerShell för att se den nya miljövariabeln.

### Exempel 3: ange nivån för WMI-loggning för flera fjärrdatorer

```
PS C:\> Set-WmiInstance -Class Win32_WMISetting -Argument @{LoggingLevel=2} -Computername "system01", "system02", "system03"
__GENUS                        : 2
__CLASS                        : Win32_WMISetting
__SUPERCLASS                   : CIM_Setting
__DYNASTY                      : CIM_Setting
__RELPATH                      : Win32_WMISetting=@
__PROPERTY_COUNT               : 27
__DERIVATION                   : {CIM_Setting}
__SERVER                       : SYSTEM01
__NAMESPACE                    : root\cimv2
__PATH                         : \\SYSTEM01\root\cimv2:Win32_WMISetting=@
ASPScriptDefaultNamespace      : \\root\cimv2
ASPScriptEnabled               : False
AutorecoverMofs                : {%windir%\system32\wbem\cimwin32.mof, %windir%\system32\wbem\ncprov.mof, %windir%\syst
em32\wbem\wmipcima.mof, %windir%\system32\wbem\secrcw32.mof...}
AutoStartWin9X                 :
BackupInterval                 :
BackupLastTime                 :
BuildVersion                   : 6001.18000
Caption                        :
DatabaseDirectory              : C:\Windows\system32\wbem\repository
DatabaseMaxSize                :
Description                    :
EnableAnonWin9xConnections     :
EnableEvents                   : False
EnableStartupHeapPreallocation : False
HighThresholdOnClientObjects   :
HighThresholdOnEvents          : 20000000
InstallationDirectory          : C:\Windows\system32\wbem
LastStartupHeapPreallocation   :
LoggingDirectory               : C:\Windows\system32\wbem\Logs\
LoggingLevel                   : 2
LowThresholdOnClientObjects    :
LowThresholdOnEvents           : 10000000
MaxLogFileSize                 : 65536
MaxWaitOnClientObjects         :
MaxWaitOnEvents                : 2000
MofSelfInstallDirectory        :
SettingID                      :
...
```

Det här kommandot anger WMI-loggnings nivån till 2.
Kommandot skickar egenskapen som ska ställas in och värdet, som tillsammans betraktas som ett värde par, i argument parametern.
Parametern använder en hash-tabell som definieras av konstruktionen @ {Property = Value}.
Den returnerade klass informationen visar det nya värdet.

## PARAMETRAR

### -Argument
Anger namnet på den egenskap som ska ändras och det nya värdet för den egenskapen.
Namnet och värdet måste vara ett namn-värde-par.
Namn-värde-paret skickas till kommando raden som en hash-tabell.
Ett exempel:

`@{Setting1=1; Setting2=5; Setting3="test"}`

```yaml
Type: System.Collections.Hashtable
Parameter Sets: class, object, path
Aliases: Args, Property

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – AsJob
Anger att den här cmdket körs som ett bakgrunds jobb.
Använd den här parametern för att köra kommandon som tar lång tid att slutföra.

När du anger parametern *AsJob* , returnerar kommandot ett objekt som representerar bakgrunds jobbet och visar sedan kommando tolken.
Du kan fortsätta att arbeta i sessionen medan jobbet är klart.
Om **set-WmiInstance** används för en fjärrdator, skapas jobbet på den lokala datorn och resultaten från fjärrdatorer returneras automatiskt till den lokala datorn.
Om du vill hantera jobbet använder du de cmdlet: ar som innehåller **jobbet** Substantiv ( **jobb** -cmdletarna).
Använd Receive-Job-cmdleten för att hämta jobb resultatet.

Om du vill använda den här parametern tillsammans med fjärrdatorer måste lokala och fjärranslutna datorer konfigureras för fjärr kommunikation.
Dessutom måste du starta Windows PowerShell med alternativet Kör som administratör i Windows Vista och senare versioner av Windows operativ system.
Mer information finns i about_Remote_Requirements.

Mer information om bakgrunds jobb i Windows PowerShell finns i about_Jobs och about_Remote_Jobs.

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
Anger den autentiseringsnivå som måste användas med WMI-anslutningen.
De acceptabla värdena för den här parametern är:

- -1: oförändrad.
- 0: standard.
- 1: ingen.
Ingen autentisering utförs.
- 2: Anslut.
Autentisering utförs endast när klienten upprättar en relation med programmet.
- 3: anropa.
Autentisering utförs endast i början av varje anrop när programmet tar emot begäran.
- 4: paket.
Autentisering utförs på alla data som tas emot från klienten.
- 5: PacketIntegrity.
Alla data som överförs mellan klienten och programmet autentiseras och verifieras.
- 6: PacketPrivacy.
Egenskaperna för de andra autentiseringsnivåer används och alla data krypteras.

```yaml
Type: System.Management.AuthenticationLevel
Parameter Sets: class, path, WQLQuery, query, list
Aliases:
Accepted values: Default, None, Connect, Call, Packet, PacketIntegrity, PacketPrivacy, Unchanged

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Authority
Anger den auktoritet som ska användas för att autentisera WMI-anslutningen.
Du kan ange standard-NTLM eller Kerberos-autentisering.
Om du vill använda NTLM ställer du in inställningen auktoritet på ntlmdomain: \<DomainName\> , där \<DomainName\> identifierar ett giltigt NTLM-domännamn.
Ange Kerberos om du vill använda Kerberos: \<DomainName\> \\ \<ServerName\> .
Du kan inte inkludera auktoritets inställningen när du ansluter till den lokala datorn.

```yaml
Type: System.String
Parameter Sets: class, path, WQLQuery, query, list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Klass
Anger namnet på en WMI-klass.

```yaml
Type: System.String
Parameter Sets: class
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName
Anger namnet på den dator där cmdleten körs.
Standard är den lokala datorn.

Ange NetBIOS-namn, en IP-adress eller ett fullständigt kvalificerat domän namn för en eller flera datorer.
Om du vill ange den lokala datorn skriver du datorns namn, en punkt (.) eller localhost.

Den här parametern är inte beroende av Windows PowerShell-fjärrkommunikation.
Du kan använda parametern *computername* även om datorn inte är konfigurerad för att köra fjärrkommandon.

```yaml
Type: System.String[]
Parameter Sets: class, path, WQLQuery, query, list
Aliases: Cn

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential
Anger ett användar konto som har behörighet att utföra den här åtgärden.
Standard är den aktuella användaren.

Ange ett användar namn, till exempel user01 eller Domain01\User01, eller ange ett **PSCredential** -objekt, till exempel ett som genereras av Get-Credential cmdlet.
Om du anger ett användar namn uppmanas du att ange ett lösen ord i den här cmdleten.

Den här parametern stöds inte av någon provider som har installerats med en parameter som inte stöds av några leverantörer som installeras med Windows PowerShell.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: class, path, WQLQuery, query, list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -EnableAllPrivileges
Anger att denna cmdlet aktiverar alla behörigheter för den aktuella användaren innan det kommando som gör WMI-anropet.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: class, path, WQLQuery, query, list
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

- 0: standard.
Läser det lokala registret för standard personifieringsnivån, som vanligt vis anges till 3: personifiera.
- 1: Anonym.
Döljer anroparens autentiseringsuppgifter.
- 2: identifiera.
Tillåter att objekt frågar efter anroparens autentiseringsuppgifter.
- 3: personifiera.
Tillåter att objekt använder autentiseringsuppgifterna för anroparen.
- 4: delegera.
Tillåter objekt att tillåta att andra objekt använder autentiseringsuppgifterna för anroparen.

```yaml
Type: System.Management.ImpersonationLevel
Parameter Sets: class, path, WQLQuery, query, list
Aliases:
Accepted values: Default, Anonymous, Identify, Impersonate, Delegate

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – InputObject
Anger ett **ManagementObject** -objekt som ska användas som indatamängd.
När den här parametern används ignoreras alla andra parametrar, förutom *argument* parametern,.

```yaml
Type: System.Management.ManagementObject
Parameter Sets: object
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Locale
Anger det önskade språket för WMI-objekt.
Parametern *locale* anges i en matris i MS_ \<LCID\> formatet i den ordning som du föredrar.

```yaml
Type: System.String
Parameter Sets: class, path, WQLQuery, query, list
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Namnrymd
Anger namn området för WMI-lagringsplatsen där den refererade WMI-klassen finns när den används med *klass* parametern.

```yaml
Type: System.String
Parameter Sets: class, path, WQLQuery, query, list
Aliases: NS

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path
Anger en sökväg till WMI-objektet för den instans som du vill skapa eller uppdatera.

```yaml
Type: System.String
Parameter Sets: path
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PutType
Anger om WMI-instansen ska skapas eller uppdateras.
De acceptabla värdena för den här parametern är:

- UpdateOnly.
Uppdaterar en befintlig WMI-instans.
- CreateOnly.
Skapar en ny WMI-instans.
- UpdateOrCreate.
Uppdaterar WMI-instansen om den finns eller skapar en ny instans om en instans inte finns.

```yaml
Type: System.Management.PutType
Parameter Sets: (All)
Aliases:
Accepted values: None, UpdateOnly, CreateOnly, UpdateOrCreate

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit
Anger det maximala antalet samtidiga anslutningar som kan upprättas för att köra det här kommandot.
Den här parametern används tillsammans med parametern *AsJob* .
Begränsnings gränsen gäller endast för det aktuella kommandot, inte för sessionen eller datorn.

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
Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Inget
Denna cmdlet accepterar inte indatatyper.

## UTDATA

### Inget
Denna cmdlet genererar inga utdata.

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Get-WmiObject](Get-WmiObject.md)

[Invoke-WmiMethod](Invoke-WmiMethod.md)

[Remove-WmiObject](Remove-WmiObject.md)
