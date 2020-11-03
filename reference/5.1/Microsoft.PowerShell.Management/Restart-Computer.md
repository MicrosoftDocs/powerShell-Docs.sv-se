---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 6/17/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/restart-computer?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Restart-Computer
ms.openlocfilehash: 553b61c9669afab325e9feec101d701c2b9a7c83
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/23/2020
ms.locfileid: "93268233"
---
# Restart-Computer

## SAMMANFATTNING
Startar om operativ systemet på lokala och fjärranslutna datorer.

## SYNTAX

### DefaultSet (standard)

```
Restart-Computer [-DcomAuthentication <AuthenticationLevel>] [-Impersonation <ImpersonationLevel>]
 [-WsmanAuthentication <String>] [-Protocol <String>] [[-ComputerName] <String[]>]
 [[-Credential] <PSCredential>] [-Force] [-Wait] [-Timeout <Int32>] [-For <WaitForServiceTypes>]
 [-Delay <Int16>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### AsJobSet

```
Restart-Computer [-AsJob] [-DcomAuthentication <AuthenticationLevel>]
 [-Impersonation <ImpersonationLevel>] [[-ComputerName] <String[]>] [[-Credential] <PSCredential>]
 [-Force] [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING

`Restart-Computer`Cmdleten startar om operativ systemet på lokala datorer och fjärrdatorer.

Du kan använda parametrarna för `Restart-Computer` för att köra omstarts åtgärderna som ett bakgrunds jobb, för att ange autentiseringsnivåer och alternativa autentiseringsuppgifter, för att begränsa de åtgärder som körs samtidigt, och framtvinga en omedelbar omstart.

Från och med Windows PowerShell 3,0 kan du vänta på att omstarten ska slutföras innan du kör nästa kommando. Ange ett timeout-värde och frågeintervall för väntan och vänta tills vissa tjänster är tillgängliga på den omstartade datorn. Den här funktionen gör det praktiskt att använda `Restart-Computer` i skript och funktioner.

Du kan använda WS-Management-protokollet (WSMan) för att starta om datorn, om DCOM-anrop (Distributed Component Object Model) blockeras, till exempel av en Enterprise-brandvägg. Mer information finns i [WS-Management-protokollet](/windows/desktop/WinRM/ws-management-protocol).

Denna cmdlet kräver Windows PowerShell-fjärrkommunikation endast när du använder parametern **AsJob** i ett kommando.

## EXEMPEL

### Exempel 1: starta om den lokala datorn

`Restart-Computer` startar om den lokala datorn.

```powershell
Restart-Computer
```

### Exempel 2: starta om flera datorer

`Restart-Computer` kan starta om fjärrdatorer och lokala datorer. Parametern **computername** accepterar en matris med dator namn.

```powershell
Restart-Computer -ComputerName Server01, Server02, localhost
```

### Exempel 3: starta om datorer som ett bakgrunds jobb

Kommandona kör ett `Restart-Computer` kommando som bakgrunds jobb på två fjärrdatorer och hämtar sedan resultaten.

Eftersom **AsJob** skapar jobbet på den lokala datorn och automatiskt returnerar resultaten till den lokala datorn, kan du köra `Receive-Job` som ett lokalt kommando.

```powershell
$Job = Restart-Computer -ComputerName "Server01", "Server02" -AsJob
$Job | Receive-Job
```

`Restart-Computer` använder parametern **computername** för att ange **Server01** och **Server02**. Parametern **AsJob** kör kommandot som ett bakgrunds jobb. Jobbobjektet lagras i `$Job` variabeln. `$Job` skickas pipelinen till den `Receive-Job` cmdlet som hämtar resultatet.

### Exempel 4: starta om en fjärrdator

`Restart-Computer` startar om en fjärrdator med anpassade inställningar för personifiering och autentisering.

```powershell
Restart-Computer -ComputerName Server01 -Impersonation Anonymous -DcomAuthentication PacketIntegrity
```

`Restart-Computer` använder parametern **computername** för att ange **Server01**. **Personifiering** -parametern anger anonym för att dölja beställarens identitet. Parametern **DcomAuthentication** anger PacketIntegrity som anslutningens autentiseringsnivå.

### Exempel 5: Framtvinga omstart av datorer som anges i en textfil

Det här exemplet tvingar fram en omedelbar omstart av de datorer som anges i `Domain01.txt` filen. Dator namnen från text filen lagras i en variabel. Force-parametern tvingar **fram** en omedelbar omstart och **ThrottleLimit** -parametern begränsar antalet samtidiga anslutningar.

```powershell
$Names = Get-Content -Path C:\Domain01.txt
$Creds = Get-Credential
Restart-Computer -ComputerName $Names -Credential $Creds -Force -ThrottleLimit 10
```

`Get-Content` använder parametern **Path** för att hämta en lista över dator namn från en textfil **Domain01.txt**. Dator namnen lagras i variabeln `$Names` . `Get-Credential` du uppmanas att ange ett användar namn och lösen ord och lagrar värdena i variabeln `$Creds` . `Restart-Computer` använder parametrarna **computername** och **Credential** med deras variabler. **Force** -parametern orsakar en omedelbar omstart av varje dator. Parametern **ThrottleLimit** begränsar kommandot till 10 samtidiga anslutningar.

### Exempel 6: starta om en fjärrdator och vänta på PowerShell

`Restart-Computer` startar om fjärrdatorn och väntar sedan upp till 5 minuter (300 sekunder) för att PowerShell ska bli tillgängligt på den omstartade datorn innan den fortsätter.

```powershell
Restart-Computer -ComputerName Server01 -Wait -For PowerShell -Timeout 300 -Delay 2
```

`Restart-Computer` använder parametern **computername** för att ange **Server01**. Parametern **wait** väntar på att omstarten ska slutföras. **For** anger att PowerShell kan köra kommandon på fjärrdatorn. Parametern **timeout** anger en vänte tid på fem minuter. Parametern **Delay** frågar den fjärranslutna datorn varannan sekund för att avgöra om den startas om.

### Exempel 7: starta om en dator med hjälp av WSMan-protokollet

`Restart-Computer` startar om fjärrdatorn med hjälp av WSMan-protokollet i stället för standard DCOM. Kerberos-autentisering avgör om den aktuella användaren har behörighet att starta om fjärrdatorn.

De här inställningarna är utformade för företag där DCOM-baserade omstarter inte fungerar eftersom DCOM är blockerad. Till exempel av en brand vägg.

```powershell
Restart-Computer -ComputerName Server01 -Protocol WSMan -WsmanAuthentication Kerberos
```

`Restart-Computer` använder parametern **computername** för att ange fjärrdatorn **Server01**.
**Protokoll** parametern anger att WSMan-protokollet ska användas. Parametern **WsmanAuthentication** anger autentiseringsmetoden som **Kerberos**.

## PARAMETRAR

### – AsJob

Anger att `Restart-Computer` körs som ett bakgrunds jobb.

Om du vill använda den här parametern måste lokala och fjärranslutna datorer konfigureras för fjärr kommunikation. I Windows Vista och senare versioner av operativ systemet Windows måste du öppna PowerShell med alternativet **Kör som administratör** . Mer information finns i [about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md).

När du anger parametern **AsJob** returnerar kommandot omedelbart ett objekt som representerar bakgrunds jobbet. Du kan fortsätta att arbeta i sessionen medan jobbet är klart. Jobbet skapas på den lokala datorn och resultaten från fjärrdatorer returneras automatiskt till den lokala datorn. Använd **jobb** -cmdletar för att hantera jobbet. Använd cmdleten för att hämta jobb resultatet `Receive-Job` .

Mer information om bakgrunds jobb i Windows PowerShell finns i [about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md) och [about_Remote_Jobs](../Microsoft.PowerShell.Core/About/about_Remote_Jobs.md).

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AsJobSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

Anger ett dator namn eller en kommaavgränsad matris med dator namn. `Restart-Computer` accepterar **computername** -objekt från pipelinen eller variablerna.

Ange NetBIOS-namn, en IP-adress eller ett fullständigt kvalificerat domän namn för en fjärrdator. Om du vill ange den lokala datorn skriver du datorns namn, en punkt `.` eller localhost.

Den här parametern är inte beroende av PowerShell-fjärrkommunikation. Du kan använda parametern **computername** även om datorn inte är konfigurerad för att köra fjärrkommandon.

Om parametern **computername** inte anges startar om `Restart-Computer` den lokala datorn.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN, __SERVER, Server, IPAddress

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Credential

Anger ett användar konto som har behörighet att utföra den här åtgärden. Standard är den aktuella användaren.

Ange ett användar namn, till exempel **user01** eller **Domain01\User01** , eller ange ett **PSCredential** -objekt som genererats av `Get-Credential` cmdleten. Om du anger ett användar namn uppmanas du att ange lösen ordet.

Autentiseringsuppgifterna lagras i ett [PSCredential](/dotnet/api/system.management.automation.pscredential) -objekt och lösen ordet lagras som en [SecureString](/dotnet/api/system.security.securestring).

> [!NOTE]
> Mer information om **SecureString** -data skydd finns i [hur säker är SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### -DcomAuthentication

Anger den autentiseringsnivå som används för WMI-anslutningen. `Restart-Computer` använder WMI.

Giltiga värden är:

- **Anropa** : com-autentisering på anrops nivå
- **Anslut** : com-autentisering på anslutnings nivå
- **Standard** : Windows-autentisering
- **Ingen** : ingen com-autentisering
- **Paket** : com-autentisering på paket nivå.
- **PacketIntegrity** : com-autentisering på paket integritets nivå
- **PacketPrivacy** : com-autentisering på paket sekretess nivå.
- **Oförändrad** : autentiseringsnivån är samma som föregående kommando.

Mer information finns i [AuthenticationLevel-uppräkning](/dotnet/api/system.management.authenticationlevel).

Den här parametern introduceras i Windows PowerShell 3,0.

```yaml
Type: System.Management.AuthenticationLevel
Parameter Sets: (All)
Aliases: Authentication
Accepted values: Default, None, Connect, Call, Packet, PacketIntegrity, PacketPrivacy, Unchanged

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Fördröjning

Anger frekvensen för frågor, i sekunder. PowerShell frågar tjänsten som anges av **for** -parametern för att avgöra om tjänsten är tillgänglig efter att datorn startats om.

Den här parametern är endast giltig tillsammans med parametrarna **wait** och **for** .

Den här parametern introducerades i Windows PowerShell 3,0.

Om **förskjutnings** parametern inte anges, `Restart-Computer` använder en fördröjning på fem sekunder.

```yaml
Type: System.Int16
Parameter Sets: DefaultSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – För

Anger PowerShell-beteendet som väntar på att den angivna tjänsten eller funktionen ska bli tillgänglig när datorn har startats om. Den här parametern är endast giltig med parametern **wait** .

De acceptabla värdena för den här parametern är:

- **Standard** : väntar på att PowerShell ska starta om.
- **PowerShell** : kan köra kommandon i en PowerShell-fjärrsession på datorn.
- **WMI** : tar emot ett svar på en Win32_ComputerSystem fråga för datorn.
- **WinRM** : kan upprätta en fjärrsession till datorn med hjälp av WS-Management.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: Microsoft.PowerShell.Commands.WaitForServiceTypes
Parameter Sets: DefaultSet
Aliases:
Accepted values: Wmi, WinRM, PowerShell

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Tvingar en omedelbar omstart av datorn.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: f

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Personifiering

Anger personifieringsnivån som denna cmdlet använder för att anropa WMI. `Restart-Computer` använder WMI.
De acceptabla värdena för den här parametern är:

- **Standard** : standard-personifiering. Trots namnet är detta inte standardvärdet.
- **Anonym** : döljer anroparens identitet.
- **Identifiera** : tillåter objekt att fråga om autentiseringsuppgifterna för anroparen.
- **Personifiera** : tillåter att objekt använder autentiseringsuppgifterna för anroparen.

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

### -Protocol

Anger vilket protokoll som ska användas för att starta om datorerna. Giltiga värden är **WSMan** och **DCOM**.

Den här parametern introduceras i Windows PowerShell 3,0.

```yaml
Type: System.String
Parameter Sets: DefaultSet
Aliases:
Accepted values: DCOM, WSMan

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit

Anger det maximala antalet samtidiga anslutningar som kan upprättas för att köra det här kommandot.
Begränsnings gränsen gäller endast för det aktuella kommandot, inte för sessionen eller datorn.

Om parametern **ThrottleLimit** inte anges eller värdet 0 används, `Restart-Computer` använder högst 32 samtidiga anslutningar.

```yaml
Type: System.Int32
Parameter Sets: AsJobSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Timeout

Anger vänte tiden i sekunder för vänte tiden. När tids gränsen har gått `Restart-Computer` tillbaka återgår till kommando tolken även om datorerna inte startas om.

Parametern **timeout** är bara giltig med parametern **wait** . **Tids gränsen** åsidosätter **wait** -parameterns obestämda vänte tid.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Int32
Parameter Sets: DefaultSet
Aliases: TimeoutSec

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Vänta

`Restart-Computer` ignorerar PowerShell-prompten och blockerar pipelinen tills datorerna har startats om. Du kan använda den här parametern i ett skript för att starta om datorer och sedan fortsätta att bearbeta när omstarten är färdig.

Parametern **wait** väntar på obestämd tid för datorerna som ska startas om. Du kan använda **timeout** för att justera tiden och parametrarna **for** och **Delay** för att vänta tills vissa tjänster blir tillgängliga på de omstartade datorerna.

Parametern **wait** är inte giltig när du startar om den lokala datorn. Om värdet för parametern **computername** innehåller namnen på fjärrdatorer och den lokala datorn `Restart-Computer` genererar ett icke-avslutande fel som **väntar** på den lokala datorn, men väntar på att fjärrdatorerna ska starta om.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DefaultSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WsmanAuthentication

Anger den mekanism som används för att autentisera användarautentiseringsuppgifter. Den här parametern introducerades i Windows PowerShell 3,0.

De acceptabla värdena för den här parametern är: **Basic** , **CredSSP** , **default** , **Digest** , **Kerberos** och **Negotiate**.

Mer information finns i [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).

> [!WARNING]
> Autentisering av Credential Security Service Provider (CredSSP), där användarautentiseringsuppgifterna skickas till en fjärrdator som ska autentiseras, är utformad för kommandon som kräver autentisering på fler än en resurs, till exempel åtkomst till en fjärran sluten nätverks resurs. Den här mekanismen ökar säkerhets risken för Fjärråtgärden. Om fjärrdatorn har komprometterats kan de autentiseringsuppgifter som skickas till den användas för att kontrol lera nätverks sessionen.

```yaml
Type: System.String
Parameter Sets: DefaultSet
Aliases:
Accepted values: Basic, CredSSP, Default, Digest, Kerberos, Negotiate

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm

Du uppmanas att bekräfta innan du kör `Restart-Computer` .

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

Visar vad som händer om `Restart-Computer` körningarna körs. `Restart-Computer`Cmdleten körs inte.

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

### System. String

`Restart-Computer` accepterar dator namn från pipelinen eller variablerna.

I Windows PowerShell 2,0 tar parametern **computername** in från pipelinen endast efter egenskaps namn. I Windows PowerShell 3,0 och senare tas parametern **computername** in från pipelinen efter värde.

## UTDATA

### Ingen, system. Management. Automation. RemotingJob

Om du anger parametern **AsJob** `Restart-Computer` returneras ett jobb objekt. Annars genereras inga utdata.

## ANTECKNINGAR

- `Restart-Computer` fungerar endast på datorer som kör Windows och kräver att WinRM och WMI stänger av ett system, inklusive det lokala systemet.
- `Restart-Computer` använder [Win32Shutdown-metoden](/windows/desktop/CIMWin32Prov/win32shutdown-method-in-class-win32-operatingsystem) för [Win32_OperatingSystems](/windows/desktop/CIMWin32Prov/win32-operatingsystem) klassen Windows Management Instrumentation (WMI).  Den här metoden kräver att **SeShutdownPrivilege** -behörighet aktive ras för det användar konto som används för att starta om datorn.

I Windows PowerShell 2,0 fungerar inte **AsJob** -parametern som tillförlitlig när du startar om eller stoppar fjärrdatorer. I Windows PowerShell 3,0 ändras implementeringen för att lösa problemet.

## RELATERADE LÄNKAR

[Om Windows Remote Management](/windows/desktop/WinRM/about-windows-remote-management)

[Get-Credential](../Microsoft.PowerShell.Security/Get-Credential.md)

[WS-Managementprotokollet](/windows/desktop/WinRM/ws-management-protocol)
