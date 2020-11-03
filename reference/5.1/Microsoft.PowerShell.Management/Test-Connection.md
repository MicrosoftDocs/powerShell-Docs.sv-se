---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/09/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/test-connection?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-Connection
ms.openlocfilehash: a8d3923db69a20cfada58391944b592cf999e6ef
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265317"
---
# Test-Connection

## SAMMANFATTNING
Skickar ICMP Echo Request-paket, eller pingar, till en eller flera datorer.

## SYNTAX

### Standard (standard)

```
Test-Connection [-AsJob] [-DcomAuthentication <AuthenticationLevel>] [-WsmanAuthentication <String>]
 [-Protocol <String>] [-BufferSize <Int32>] [-ComputerName] <String[]> [-Count <Int32>]
 [-Impersonation <ImpersonationLevel>] [-ThrottleLimit <Int32>] [-TimeToLive <Int32>]
 [-Delay <Int32>] [<CommonParameters>]
```

### Källa

```
Test-Connection [-AsJob] [-DcomAuthentication <AuthenticationLevel>] [-WsmanAuthentication <String>]
 [-Protocol <String>] [-BufferSize <Int32>] [-ComputerName] <String[]> [-Count <Int32>]
 [-Credential <PSCredential>] [-Source] <String[]> [-Impersonation <ImpersonationLevel>]
 [-ThrottleLimit <Int32>] [-TimeToLive <Int32>] [-Delay <Int32>] [<CommonParameters>]
```

### Tyst

```
Test-Connection [-DcomAuthentication <AuthenticationLevel>] [-WsmanAuthentication <String>]
 [-Protocol <String>] [-BufferSize <Int32>] [-ComputerName] <String[]> [-Count <Int32>]
 [-Impersonation <ImpersonationLevel>] [-TimeToLive <Int32>] [-Delay <Int32>] [-Quiet]
 [<CommonParameters>]
```

## BESKRIVNING

`Test-Connection`Cmdleten skickar Internet Control Message Protocol (ICMP) eko begär paket, eller pingar, till en eller flera fjärrdatorer och returnerar svars Svaren för eko. Du kan använda den här cmdleten för att avgöra om en viss dator kan kontaktas i ett IP-nätverk.

Du kan använda parametrarna för `Test-Connection` för att ange både sändnings-och mottagnings datorer, köra kommandot som ett bakgrunds jobb för att ange ett timeout-värde och antalet pingar och för att konfigurera anslutningen och autentiseringen.

Till skillnad från det välkända **ping** -kommandot `Test-Connection` returnerar ett **Win32_PingStatus** -objekt som du kan undersöka i PowerShell. Parametern **quiet** returnerar ett **booleskt** värde i ett **system. Boolean** -objekt för varje testad anslutning. Om flera anslutningar testas returneras en matris med **booleska** värden.

## EXEMPEL

### Exempel 1: skicka eko förfrågningar till en fjärrdator

Det här exemplet skickar eko begär ande paket från den lokala datorn till Server01-datorn.

```powershell
Test-Connection -ComputerName Server01
```

```Output
Source        Destination     IPV4Address     IPV6Address  Bytes    Time(ms)
------        -----------     -----------     -----------  -----    --------
ADMIN1        Server01         10.59.137.44                32       0
ADMIN1        Server01         10.59.137.44                32       0
ADMIN1        Server01         10.59.137.44                32       0
ADMIN1        Server01         10.59.137.44                32       1
```

`Test-Connection` använder parametern **computername** för att ange Server01-datorn.

### Exempel 2: skicka eko förfrågningar till flera datorer

I det här exemplet skickas pingar från den lokala datorn till flera fjärrdatorer.

```powershell
Test-Connection -ComputerName Server01, Server02, Server12
```

### Exempel 3: skicka eko förfrågningar från flera datorer till en dator

I det här exemplet skickas pingar från olika käll datorer till en enda fjärran sluten dator, Server01.

```powershell
Test-Connection -Source Server02, Server12, localhost -ComputerName Server01 -Credential Domain01\Admin01
```

`Test-Connection` använder parametern **Credential** för att ange autentiseringsuppgifterna för en användare som har behörighet att skicka en ping-begäran från käll datorerna. Använd det här kommando formatet för att testa svars tiden för anslutningar från flera punkter.

### Exempel 4: Använd parametrar för att anpassa test kommandot

I det här exemplet används parametrarna för `Test-Connection` för att anpassa kommandot. Den lokala datorn skickar ett ping-test till en fjärrdator.

```powershell
Test-Connection -ComputerName Server01 -Count 3 -Delay 2 -TTL 255 -BufferSize 256 -ThrottleLimit 32
```

`Test-Connection` använder parametern **computername** för att ange Server01. Parametern **Count** anger att tre pingar skickas till Server01-datorn med en **fördröjning** på 2 sekunders intervall.

Du kan använda dessa alternativ när ping-svaret förväntas ta längre tid än vanligt, antingen på grund av ett utökat antal hopp eller ett nätverks tillstånd med hög trafik.

### Exempel 5: köra ett test som bakgrunds jobb

Det här exemplet visar hur du kör ett `Test-Connection` kommando som ett PowerShell-bakgrunds jobb.

```powershell
$job = Test-Connection -ComputerName (Get-Content Servers.txt) -AsJob
if ($job.JobStateInfo.State -ne "Running") {$Results = Receive-Job $job}
```

`Test-Connection`Kommandot pingar många datorer i ett företag. Värdet för parametern **computername** är ett `Get-Content` kommando som läser en lista med dator namn från `Servers.txt file` . Kommandot använder parametern **AsJob** för att köra kommandot som ett bakgrunds jobb och det sparar jobbet i `$job` variabeln.

`if`Kommandot kontrollerar att jobbet fortfarande inte körs. Om jobbet inte körs `Receive-Job` hämtar resultatet och lagrar dem i `$Results` variabeln.

### Exempel 6: pinga en fjärrdator med autentiseringsuppgifter

Det här kommandot använder `Test-Connection` cmdleten för att pinga en fjärrdator.

```powershell
Test-Connection Server55 -Credential Domain55\User01 -Impersonation Identify
```

Kommandot använder parametern **Credential** för att ange ett användar konto som har behörighet att pinga fjärrdatorn och **personifieringstoken** -parametern för att ändra personifieringsnivån som ska **identifieras**.

### Exempel 7: skapa en session endast om ett anslutnings test lyckas

I det här exemplet skapas en session på Server01-datorn endast om minst en av pingarna som skickats till datorn lyckas.

```powershell
if (Test-Connection -ComputerName Server01 -Quiet) {New-PSSession Server01}
```

`if`Kommandot använder `Test-Connection` cmdleten för att pinga Server01-datorn. Kommandot använder parametern **quiet** , som returnerar ett **booleskt** värde, i stället för ett **Win32_PingStatus** -objekt. Värdet är `$True` om någon av de fyra pingarna lyckas och är, i annat fall, `$False` .

Om `Test-Connection` kommandot returnerar ett värde av `$True` använder kommandot `New-PSSession` cmdleten för att skapa **PSSession**.

## PARAMETRAR

### – AsJob

Anger att denna cmdlet körs som ett bakgrunds jobb.

Om du vill använda den här parametern måste lokal och fjärran sluten dator konfigureras för fjärr kommunikation och, i Windows Vista och senare versioner av Windows-operativsystemet, måste du öppna PowerShell med alternativet **Kör som administratör** . Mer information finns i [about_Remote_Requirements](../microsoft.powershell.core/about/about_remote_requirements.md).

När du anger parametern **AsJob** returnerar kommandot omedelbart ett objekt som representerar bakgrunds jobbet. Du kan fortsätta att arbeta i sessionen medan jobbet är klart. Jobbet skapas på den lokala datorn och resultaten från fjärrdatorer returneras automatiskt till den lokala datorn. Använd cmdleten för att hämta jobb resultatet `Receive-Job` .

Mer information om PowerShell-bakgrunds jobb finns i [about_Jobs](../Microsoft.PowerShell.Core/About/about_jobs.md) och [about_Remote_Jobs](../Microsoft.PowerShell.Core/About/about_remote_jobs.md).

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Default, Source
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -BufferSize

Anger storlek, i byte, för den buffert som skickas med det här kommandot. Standardvärdet är 32.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: Size, Bytes, BS

Required: False
Position: Named
Default value: 32
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

Anger vilka datorer som pingas. Ange dator namnen eller ange IP-adresser i IPv4-eller IPv6-format. Jokertecken tillåts inte. Den här parametern är obligatorisk.

Den här parametern är inte beroende av PowerShell-fjärrkommunikation. Du kan använda parametern **computername** även om datorn inte är konfigurerad för att köra fjärrkommandon.

> [!NOTE]
> Parametern **computername** byter namn till **TargetName** i PowerShell 6,0 och senare.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN, IPAddress, __SERVER, Server, Destination

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Antal

Anger hur många eko-begäranden som ska skickas. Standardvärdet är 4.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 4
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential

Anger ett användar konto som har behörighet att skicka en ping-begäran från käll datorn. Ange ett användar namn, till exempel user01 eller Domain01\User01, eller ange ett **PSCredential** -objekt, till exempel ett från `Get-Credential` cmdleten.

Parametern **Credential** är bara giltig när **käll** parametern används i kommandot. Autentiseringsuppgifterna påverkar inte mål datorn.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: Source
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### -DcomAuthentication

Anger den autentiseringsnivå som denna cmdlet använder med WMI.
`Test-Connection` använder WMI.
De acceptabla värdena för den här parametern är:

- **Standard**. Windows-autentisering
- **Ingen**. Ingen COM-autentisering
- **Anslut**. COM-autentisering på anslutnings nivå
- **Anropa**. COM-autentisering på anrops nivå
- **Paket**. COM-autentisering på paket nivå
- **PacketIntegrity**. COM-autentisering på paket integritets nivå
- **PacketPrivacy**. COM-autentisering för paket sekretess nivå
- **Oförändrad**. Samma som föregående kommando

Standardvärdet är **paket** som har ett uppräknat värde på **4**. Mer information om värdena för den här parametern finns i [AuthenticationLevel](/dotnet/api/system.management.authenticationlevel) -uppräkning.

```yaml
Type: System.Management.AuthenticationLevel
Parameter Sets: (All)
Aliases: Authentication
Accepted values: Default, None, Connect, Call, Packet, PacketIntegrity, PacketPrivacy, Unchanged

Required: False
Position: Named
Default value: Packet (enumerated value of 4)
Accept pipeline input: False
Accept wildcard characters: False
```

### -Fördröjning

Anger intervallet mellan pingar, i sekunder.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 1 (second)
Accept pipeline input: False
Accept wildcard characters: False
```

### -Personifiering

Anger personifieringsnivån som ska användas när den här cmdleten anropar WMI. `Test-Connection` använder WMI.

De acceptabla värdena för den här parametern är följande:

- **Standard**. Standard personifiering.
- **Anonym**. Döljer anroparens identitet.
- **Identifiera**. Tillåter att objekt frågar efter anroparens autentiseringsuppgifter.
- **Personifiera**. Tillåter att objekt använder autentiseringsuppgifterna för anroparen.

Standardvärdet är **personifierat**.

```yaml
Type: System.Management.ImpersonationLevel
Parameter Sets: (All)
Aliases:
Accepted values: Default, Anonymous, Identify, Impersonate, Delegate

Required: False
Position: Named
Default value: Impersonate
Accept pipeline input: False
Accept wildcard characters: False
```

### -Protocol

Anger ett protokoll. De acceptabla värdena för den här parametern är DCOM och WSMan.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: DCOM, WSMan

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Tyst

Parametern **quiet** returnerar ett **booleskt** värde i ett **system. Boolean** -objekt. Om du använder den här parametern utelämnas alla fel.

Varje anslutning som testas returnerar ett **booleskt** värde. Om parametern **computername** anger flera datorer returneras en matris med **booleska** värden.

Om **några** pingar lyckas `$True` returneras.

Om **alla** pingar inte fungerar `$False` returneras.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Quiet
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Source

Anger namnen på de datorer där pingen kommer. Ange en kommaavgränsad lista med dator namn. Standard är den lokala datorn.

```yaml
Type: System.String[]
Parameter Sets: Source
Aliases: FCN, SRC

Required: True
Position: 1
Default value: Local computer
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit

Anger det maximala antalet samtidiga anslutningar som kan upprättas för att köra det här kommandot.
Om du utelämnar den här parametern eller anger värdet 0, används standardvärdet 32.

Begränsnings gränsen gäller endast för det aktuella kommandot, inte för sessionen eller datorn.

```yaml
Type: System.Int32
Parameter Sets: Default, Source
Aliases:

Required: False
Position: Named
Default value: 32
Accept pipeline input: False
Accept wildcard characters: False
```

### – TimeToLive

Anger det maximala antal gånger som ett paket kan vidarebefordras. För varje hopp i Gateway, routrar osv. **TimeToLive** -värdet minskas med ett. Vid noll ignoreras paketet och ett fel returneras.
I **Windows** är standardvärdet **128**. Aliaset för parametern **TimeToLive** är **TTL**.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: TTL

Required: False
Position: Named
Default value: 128 in Windows
Accept pipeline input: False
Accept wildcard characters: False
```

### -WsmanAuthentication

Anger den mekanism som används för att autentisera användarautentiseringsuppgifter när denna cmdlet använder WSMan-protokollet.
De acceptabla värdena för den här parametern är:

- Basic
- CredSSP
- Default
- Sammandrag
- Kerberos
- Fram.

Standardvärdet är default.

Mer information om värdena för den här parametern finns i [AuthenticationMechanism-uppräkning](/dotnet/api/system.management.automation.runspaces.authenticationmechanism?view=powershellsdk-1.1.0).

Varning! autentisering med Credential Security Service Provider (CredSSP), där autentiseringsuppgifterna skickas till en fjärrdator som ska autentiseras, är utformad för kommandon som kräver autentisering på fler än en resurs, till exempel åtkomst till en fjärran sluten nätverks resurs.
Den här mekanismen ökar säkerhets risken för Fjärråtgärden.
Om fjärrdatorn har komprometterats kan de autentiseringsuppgifter som skickas till den användas för att kontrol lera nätverks sessionen.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Default, Basic, Negotiate, CredSSP, Digest, Kerberos

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Inget

Du kan inte skicka pipe-ininformation till denna cmdlet.

## UTDATA

### System. Management. ManagementObject # root\cimv2\ Win32_PingStatus, system. Management. Automation. RemotingJob, system. Boolean

Den här cmdleten returnerar ett jobb objekt, om du anger parametern **AsJob** .

Om du anger en **quiet** -parameter returneras ett **booleskt** värde. Om flera anslutningar testas returneras en matris med **booleska** värden. Annars `Test-Connection` returneras ett **Win32_PingStatus** -objekt för varje ping.

## ANTECKNINGAR

Denna cmdlet använder klassen **Win32_PingStatus** . Ett `Get-WMIObject Win32_PingStatus` kommando motsvarar ett `Test-Connection` kommando.

**Käll** parameter uppsättningen introducerades i PowerShell 3,0.

## RELATERADE LÄNKAR

[Lägg till dator](Add-Computer.md)

[Starta om datorn](Restart-Computer.md)

[Stoppa – dator](Stop-Computer.md)
