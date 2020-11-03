---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/test-connection?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-Connection
ms.openlocfilehash: 6a03d5a644e3d4be515a93a702d0ef0aff23a8d7
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263732"
---
# Test-Connection

## SAMMANFATTNING
Skickar ICMP Echo Request-paket, eller pingar, till en eller flera datorer.

## SYNTAX

### DefaultPing (standard)

```
Test-Connection [-TargetName] <string[]> [-Ping] [-IPv4] [-IPv6] [-ResolveDestination]
 [-Source <string>] [-MaxHops <int>] [-Count <int>] [-Delay <int>] [-BufferSize <int>]
 [-DontFragment] [-TimeoutSeconds <int>] [-Quiet] [<CommonParameters>]
```

### RepeatPing

```
Test-Connection [-TargetName] <string[]> -Repeat [-Ping] [-IPv4] [-IPv6] [-ResolveDestination]
 [-Source <string>] [-MaxHops <int>] [-Delay <int>] [-BufferSize <int>] [-DontFragment]
 [-TimeoutSeconds <int>] [-Quiet] [<CommonParameters>]
```

### MtuSizeDetect

```
Test-Connection [-TargetName] <string[]> -MtuSize [-IPv4] [-IPv6] [-ResolveDestination]
 [-TimeoutSeconds <int>] [-Quiet] [<CommonParameters>]
```

### TraceRoute

```
Test-Connection [-TargetName] <string[]> -Traceroute [-IPv4] [-IPv6] [-ResolveDestination]
 [-Source <string>] [-MaxHops <int>] [-TimeoutSeconds <int>] [-Quiet] [<CommonParameters>]
```

### TcpPort

```
Test-Connection [-TargetName] <string[]> -TcpPort <int> [-IPv4] [-IPv6] [-ResolveDestination]
 [-Source <string>] [-TimeoutSeconds <int>] [-Quiet] [<CommonParameters>]
```

## BESKRIVNING

`Test-Connection`Cmdleten skickar Internet Control Message Protocol (ICMP) eko begär paket, eller pingar, till en eller flera fjärrdatorer och returnerar svars Svaren för eko. Du kan använda den här cmdleten för att avgöra om en viss dator kan kontaktas i ett IP-nätverk.

Du kan använda parametrarna för `Test-Connection` för att ange både sändnings-och mottagnings datorer, köra kommandot som ett bakgrunds jobb för att ange ett timeout-värde och antalet pingar och för att konfigurera anslutningen och autentiseringen.

Till skillnad från det välkända **ping** -kommandot `Test-Connection` returnerar ett **TestConnectionCommand + PingStatus** -objekt som du kan undersöka i PowerShell. Parametern **quiet** returnerar ett **booleskt** värde i ett **system. Boolean** -objekt för varje testad anslutning. Om flera anslutningar testas returneras en matris med **booleska** värden.

## EXEMPEL

### Exempel 1: skicka eko förfrågningar till en fjärrdator

Det här exemplet skickar eko begär ande paket från den lokala datorn till Server01-datorn.

```powershell
Test-Connection -TargetName Server01 -IPv4
```

```Output
   Destination: Server01

Ping Source           Address                   Latency BufferSize Status
                                                   (ms)        (B)
---- ------           -------                   ------- ---------- ------
   1 ADMIN1           10.59.137.44                   24         32 Success
   2 ADMIN1           10.59.137.44                   39         32 Success
   3 ADMIN1           *                               *          * TimedOut
   4 ADMIN1           10.59.137.44                   28         32 Success
```

`Test-Connection` använder parametern **TargetName** för att ange Server01-datorn. **IPv4** -parametern anger protokollet för testet.

En serie med **TestConnectionCommand + PingStatus** -objekt skickas till utdataströmmen, ett objekt per ping-svar från mål datorn.

### Exempel 2: skicka eko förfrågningar till flera datorer

I det här exemplet skickas pingar från den lokala datorn till flera fjärrdatorer.

```powershell
Test-Connection -TargetName Server01, Server02, Server12
```

### Exempel 3: Använd parametrar för att anpassa test kommandot

I det här exemplet används parametrarna för `Test-Connection` för att anpassa kommandot. Den lokala datorn skickar ett ping-test till en fjärrdator.

```powershell
Test-Connection -TargetName Server01 -Count 3 -Delay 2 -MaxHops 255 -BufferSize 256
```

`Test-Connection` använder parametern **TargetName** för att ange Server01. Parametern **Count** anger att tre pingar skickas till Server01-datorn med en **fördröjning** på 2 sekunders intervall.

Du kan använda dessa alternativ när ping-svaret förväntas ta längre tid än vanligt, antingen på grund av ett utökat antal hopp eller ett nätverks tillstånd med hög trafik.

### Exempel 4: kör ett test som bakgrunds jobb

Det här exemplet visar hur du kör ett `Test-Connection` kommando som ett PowerShell-bakgrunds jobb.

```powershell
$job = Start-Job -ScriptBlock { Test-Connection -TargetName (Get-Content -Path "Servers.txt") }
$Results = Receive-Job $job -Wait
```

`Start-Job`Kommandot använder `Test-Connection` cmdleten för att pinga många datorer i ett företag.
Värdet för parametern **TargetName** är ett `Get-Content` kommando som läser en lista med dator namn från `Servers.txt` filen. Kommandot använder `Start-Job` cmdleten för att köra kommandot som ett bakgrunds jobb och det sparar jobbet i `$job` variabeln.

`Receive-Job`Kommandot instrueras `-Wait` tills jobbet har slutförts och hämtar sedan resultaten och lagrar dem i `$Results` variabeln.

### Exempel 5: skapa endast en session om ett anslutnings test lyckas

I det här exemplet skapas en session på Server01-datorn endast om minst en av pingarna som skickats till datorn lyckas.

```powershell
if (Test-Connection -TargetName Server01 -Quiet) { New-PSSession -ComputerName Server01 }
```

`Test-Connection`Cmdlet: en pingar `Server01` datorn med parametern **quiet** angiven.
Det resulterande värdet är `$True` om någon av de fyra pingarna lyckas. Om inget av pingarna lyckas är värdet `$False` .

Om `Test-Connection` kommandot returnerar ett värde av `$True` använder kommandot `New-PSSession` cmdleten för att skapa **PSSession**.

### Exempel 6: Använd parametern traceroute

**Traceroute** -parametern har introducerats i PowerShell 6,0 och mappar en väg mellan den lokala datorn och fjärrdestinationen som du anger med parametern **TargetName** .

```powershell
Test-Connection -TargetName www.google.com -Traceroute
```

```Output
   Target: google.com

Hop Hostname                  Ping Latency Status           Source       TargetAddress
                                      (ms)
--- --------                  ---- ------- ------           ------       -------------
  1 172.20.0.1                   1       4 Success          Lira         172.217.9.174
  1 172.20.0.1                   2       3 Success          Lira         172.217.9.174
  1 172.20.0.1                   3       2 Success          Lira         172.217.9.174
  2 12.108.153.193               1       3 Success          Lira         172.217.9.174
  2 12.108.153.193               2       3 Success          Lira         172.217.9.174
  2 12.108.153.193               3       2 Success          Lira         172.217.9.174
  3 12.244.85.177                1      11 Success          Lira         172.217.9.174
  3 12.244.85.177                2      12 Success          Lira         172.217.9.174
  3 12.244.85.177                3      12 Success          Lira         172.217.9.174
  4 *                            1      14 DestinationNetw… Lira         172.217.9.174
  4 *                            2       * TimedOut         Lira         172.217.9.174
  4 *                            3      20 DestinationNetw… Lira         172.217.9.174
  5 *                            1       * TimedOut         Lira         172.217.9.174
  5 *                            2      15 DestinationNetw… Lira         172.217.9.174
  5 *                            3       * TimedOut         Lira         172.217.9.174
  6 *                            1      18 DestinationNetw… Lira         172.217.9.174
  6 *                            2       * TimedOut         Lira         172.217.9.174
  6 *                            3      16 DestinationNetw… Lira         172.217.9.174
  7 *                            1       * TimedOut         Lira         172.217.9.174
  7 *                            2       * TimedOut         Lira         172.217.9.174
  7 *                            3       * TimedOut         Lira         172.217.9.174
  8 *                            1       * TimedOut         Lira         172.217.9.174
  8 *                            2       * TimedOut         Lira         172.217.9.174
  8 *                            3       * TimedOut         Lira         172.217.9.174
  9 *                            1       * TimedOut         Lira         172.217.9.174
  9 *                            2       * TimedOut         Lira         172.217.9.174
  9 *                            3       * TimedOut         Lira         172.217.9.174
 10 *                            1       * TimedOut         Lira         172.217.9.174
 10 *                            2       * TimedOut         Lira         172.217.9.174
 10 *                            3       * TimedOut         Lira         172.217.9.174
 11 172.217.9.174                1      23 Success          Lira         172.217.9.174
 11 172.217.9.174                2      21 Success          Lira         172.217.9.174
 11 172.217.9.174                3      22 Success          Lira         172.217.9.174
```

`Test-Connection`Kommandot anropas med parametern **traceroute** . Resultaten, som är `[Microsoft.PowerShell.Commands.TestConnectionCommand+TraceStatus]` objekt, matas ut till den resulterande utdataströmmen. **Success**

## PARAMETRAR

### -BufferSize

Anger storlek, i byte, för den buffert som skickas med det här kommandot. Standardvärdet är 32.

```yaml
Type: System.Int32
Parameter Sets: DefaultPing, RepeatPing
Aliases: Size, Bytes, BS

Required: False
Position: Named
Default value: 32
Accept pipeline input: False
Accept wildcard characters: False
```

### -Upprepa

Gör att cmdleten skickar ping-begäranden kontinuerligt. Den här parametern kan inte användas med **Count** -parametern.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: RepeatPing
Aliases: Continuous

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Antal

Anger hur många eko-begäranden som ska skickas. Standardvärdet är 4.

```yaml
Type: System.Int32
Parameter Sets: DefaultPing
Aliases:

Required: False
Position: Named
Default value: 4
Accept pipeline input: False
Accept wildcard characters: False
```

### -Fördröjning

Anger intervallet mellan pingar, i sekunder.

```yaml
Type: System.Int32
Parameter Sets: DefaultPing, RepeatPing
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DontFragment

Den här parametern anger flaggan **Fragmentera inte** i IP-huvudet. Du kan använda den här parametern med parametern **BufferSize** för att testa MTU-storleken för sökvägen. Mer information om MTU för sökvägen finns i artikeln [sökväg för MTU-identifiering](https://wikipedia.org/wiki/Path_MTU_Discovery) i wikipedia.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DefaultPing, RepeatPing
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### – IPv4

Tvingar cmdleten att använda IPv4-protokollet för testet.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -IPv6

Tvingar cmdleten att använda IPv6-protokollet för testet.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaxHops

Anger maximalt antal hopp som ett meddelande om ICMP-begäran kan skickas. Standardvärdet styrs av operativ systemet. Standardvärdet för Windows 10 är 128 hopp.

```yaml
Type: System.Int32
Parameter Sets: DefaultPing, RepeatPing, TraceRoute
Aliases: Ttl, TimeToLive, Hops

Required: False
Position: Named
Default value: 128 hops in Windows 10
Accept pipeline input: False
Accept wildcard characters: False
```

### -Ping

Gör att cmdleten gör ett ping-test. Detta är standard läget för `Test-Connection` cmdleten.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DefaultPing, RepeatPing
Aliases:

Required: False
Position: Named
Default value: True
Accept pipeline input: False
Accept wildcard characters: False
```

### – Tyst

Parametern **quiet** returnerar ett **booleskt** värde. Om du använder den här parametern utelämnas alla fel.

Varje anslutning som testas returnerar ett **booleskt** värde. Om parametern **TargetName** anger flera datorer returneras en matris med **booleska** värden.

Om **ett** ping till ett specifikt mål lyckas `$True` returneras.

Om **alla** pingar till ett angivet mål inte fungerar `$False` returneras.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -ResolveDestination

Gör att cmdleten försöker matcha målets DNS-namn. När det används tillsammans med **traceroute** -parametern, kommer DNS-namnen för alla mellanliggande värdar också att hämtas, om möjligt.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Source

Anger namnen på de datorer där pingen kommer. Ange en kommaavgränsad lista med dator namn. Standard är den lokala datorn.

**Obs:** Den här parametern fungerar inte i PowerShell-versionerna 6 och uppåt.
Om du anger den här parametern påverkas inte kommandot.

```yaml
Type: System.String
Parameter Sets: DefaultPing, RepeatPing, TraceRoute, TcpPort
Aliases:

Required: False
Position: Named
Default value: Local computer
Accept pipeline input: False
Accept wildcard characters: False
```

### -TargetName

Anger vilken eller vilka datorer som ska testas. Ange dator namnen eller ange IP-adresser i IPv4-eller IPv6-format.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: ComputerName

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -TimeoutSeconds

Anger timeout-värdet för testet. Testet Miss lyckas om ett svar inte tas emot innan tids gränsen upphör att gälla. Standardvärdet är fem sekunder.

Den här parametern introducerades i PowerShell 6,0.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 5 seconds
Accept pipeline input: False
Accept wildcard characters: False
```

### – Traceroute

Gör att cmdleten gör ett traceroute-test. När den här parametern används returnerar cmdleten ett- `TestConnectionCommand+TraceStatus` objekt.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TraceRoute
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -MtuSize

Den här parametern används för att identifiera MTU-storleken för sökvägen. Cmdleten returnerar ett **PingReply # MTUSize** -objekt som innehåller sökvägen till MÅLETs MTU-storlek. Mer information om MTU för sökvägen finns i artikeln [sökväg för MTU-identifiering](https://wikipedia.org/wiki/Path_MTU_Discovery) i wikipedia.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: MtuSizeDetect
Aliases: MtuSizeDetect

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### – TcpPort

Anger TCP-portnumret på det mål som ska användas vid testet av TCP-anslutningen. Cmdleten kommer att försöka upprätta en TCP-anslutning till den angivna porten på målet.

Om en anslutning kan upprättas `$True` returneras.

Om det inte går att upprätta en anslutning `$False` returneras.

```yaml
Type: System.Int32
Parameter Sets: TcpPort
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Inget

Du kan inte skicka pipe-ininformation till denna cmdlet.

## UTDATA

### TestConnectionCommand + PingStatus, TestConnectionCommand + TraceStatus, Boolean, TestConnectionCommand + PingMtuStatus

Som standard `Test-Connection` returnerar ett **TestConnectionCommand + PingStatus** -objekt för varje ping-svar.

Om du anger parametern **traceroute** returnerar cmdleten ett **TestConnectionCommand + TraceStatus** -objekt för varje ping-svar längs vägen.

Om du anger parametrarna **quiet** eller **TcpPort** returneras ett **booleskt** värde. Om flera anslutningar testas returneras en matris med **booleska** värden.

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Starta om datorn](Restart-Computer.md)

[Stoppa – dator](Stop-Computer.md)

