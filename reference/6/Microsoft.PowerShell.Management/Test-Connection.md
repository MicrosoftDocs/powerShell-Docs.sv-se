---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 11/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/test-connection?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-Connection
ms.openlocfilehash: 54ba1d7db60db7b4bb64f3161bba9c1fba124219
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263738"
---
# Test-Connection

## SAMMANFATTNING
Skickar ICMP Echo Request-paket, eller pingar, till en eller flera datorer.

## SYNTAX

### PingCount (standard)

```
Test-Connection [-Ping] [-IPv4] [-IPv6] [-ResolveDestination] [-Source <String>] [-MaxHops <Int32>]
 [-Count <Int32>] [-Delay <Int32>] [-BufferSize <Int32>] [-DontFragment] [-TimeoutSeconds <Int32>]
 [-TargetName] <String[]> [-Quiet] [<CommonParameters>]
```

### PingContinues

```
Test-Connection [-Ping] [-IPv4] [-IPv6] [-ResolveDestination] [-Source <String>] [-MaxHops <Int32>]
 [-Delay <Int32>] [-BufferSize <Int32>] [-DontFragment] [-Continues] [-TimeoutSeconds <Int32>]
 [-TargetName] <String[]> [-Quiet] [<CommonParameters>]
```

### DetectionOfMTUSize

```
Test-Connection [-IPv4] [-IPv6] [-ResolveDestination] [-TimeoutSeconds <Int32>]
 [-TargetName] <String[]> -MTUSizeDetect [-Quiet] [<CommonParameters>]
```

### TraceRoute

```
Test-Connection [-IPv4] [-IPv6] [-ResolveDestination] [-Source <String>] [-MaxHops <Int32>]
 [-TimeoutSeconds <Int32>] [-TargetName] <String[]> -Traceroute [-Quiet] [<CommonParameters>]
```

### ConnectionByTCPPort

```
Test-Connection [-IPv4] [-IPv6] [-ResolveDestination] [-Source <String>] [-TimeoutSeconds <Int32>]
 [-TargetName] <String[]> -TCPPort <Int32> [-Quiet] [<CommonParameters>]
```

## BESKRIVNING

`Test-Connection`Cmdleten skickar Internet Control Message Protocol (ICMP) eko begär paket, eller pingar, till en eller flera fjärrdatorer och returnerar svars Svaren för eko. Du kan använda den här cmdleten för att avgöra om en viss dator kan kontaktas i ett IP-nätverk.

Du kan använda parametrarna för `Test-Connection` för att ange både sändnings-och mottagnings datorer, köra kommandot som ett bakgrunds jobb för att ange ett timeout-värde och antalet pingar och för att konfigurera anslutningen och autentiseringen.

Till skillnad från det välkända **ping** -kommandot `Test-Connection` returnerar ett **TestConnectionCommand + PingReport** -objekt som du kan undersöka i PowerShell. Parametern **quiet** returnerar ett **booleskt** värde i ett **system. Boolean** -objekt för varje testad anslutning. Om flera anslutningar testas returneras en matris med **booleska** värden.

## EXEMPEL

### Exempel 1: skicka eko förfrågningar till en fjärrdator

Det här exemplet skickar eko begär ande paket från den lokala datorn till Server01-datorn.

```powershell
Test-Connection -TargetName Server01 -IPv4
```

```Output
Pinging Server01 [10.59.137.44] with 32 bytes of data:
Reply from 10.59.137.44: bytes=32 time=0ms TTL=128
Reply from 10.59.137.44: bytes=32 time=0ms TTL=128
Reply from 10.59.137.44: bytes=32 time=0ms TTL=128
Reply from 10.59.137.44: bytes=32 time=0ms TTL=128
Ping complete.

Source     Destination Replies
------     ----------- -------
Server01   Server01    {System.Net.NetworkInformation.PingReply, System.Net.NetworkInformation ...
```

`Test-Connection` använder parametern **TargetName** för att ange Server01-datorn. **IPv4** -parametern anger protokollet för testet.

Ping-utdata skickas till **informations** data strömmen medan **TestConnectionCommand + PingReport** -objektet skickas **till den** resulterande data strömmen. Mer information om utdata strömmar finns [about_Redirection](../microsoft.powershell.core/about/about_redirection.md).

### Exempel 2: skicka eko förfrågningar till flera datorer

I det här exemplet skickas pingar från den lokala datorn till flera fjärrdatorer.

```powershell
Test-Connection -TargetName Server01, Server02, Server12
```

### Exempel 3: skicka eko förfrågningar från flera datorer till en dator

I det här exemplet skickas pingar från olika käll datorer till en enda fjärran sluten dator, Server01.

```powershell
Test-Connection -Source Server02, Server12, localhost -TargetName Server01
```

Använd det här kommando formatet för att testa svars tiden för anslutningar från flera punkter.

### Exempel 4: Använd parametrar för att anpassa test kommandot

I det här exemplet används parametrarna för `Test-Connection` för att anpassa kommandot. Den lokala datorn skickar ett ping-test till en fjärrdator.

```powershell
Test-Connection -TargetName Server01 -Count 3 -Delay 2 -MaxHops 255 -BufferSize 256
```

`Test-Connection` använder parametern **TargetName** för att ange Server01. Parametern **Count** anger att tre pingar skickas till Server01-datorn med en **fördröjning** på 2 sekunders intervall.

Du kan använda dessa alternativ när ping-svaret förväntas ta längre tid än vanligt, antingen på grund av ett utökat antal hopp eller ett nätverks tillstånd med hög trafik.

### Exempel 5: köra ett test som bakgrunds jobb

Det här exemplet visar hur du kör ett `Test-Connection` kommando som ett PowerShell-bakgrunds jobb.

```powershell
$job = Start-Job -ScriptBlock { Test-Connection -TargetName (Get-Content "Servers.txt") }
if ($job.JobStateInfo.State -ne "Running") { $Results = Receive-Job $job }
```

`Start-Job`Kommandot använder `Test-Connection` cmdleten för att pinga många datorer i ett företag.
Värdet för parametern **TargetName** är ett `Get-Content` kommando som läser en lista med dator namn från `Servers.txt` filen. Kommandot använder `Start-Job` cmdleten för att köra kommandot som ett bakgrunds jobb och det sparar jobbet i `$job` variabeln.

`if`Kommandot kontrollerar att jobbet fortfarande inte körs. Om jobbet inte körs `Receive-Job` hämtar resultatet och lagrar dem i `$Results` variabeln.

### Exempel 6: skapa endast en session om ett anslutnings test lyckas

I det här exemplet skapas en session på Server01-datorn endast om minst en av pingarna som skickats till datorn lyckas.

```powershell
if (Test-Connection -TargetName Server01 -Quiet) {New-PSSession Server01}
```

`if`Kommandot använder `Test-Connection` cmdleten för att pinga Server01-datorn. Kommandot använder parametern **quiet** , som returnerar ett **booleskt** värde, i stället för ett **TestConnectionCommand + PingReport** -objekt.

Värdet är `$True` om någon av de fyra pingarna lyckas. Om inget av pingarna lyckas är värdet `$False` .

Om `Test-Connection` kommandot returnerar ett värde av `$True` använder kommandot `New-PSSession` cmdleten för att skapa **PSSession**.

### Exempel 7: Använd parametern traceroute

Från och med PowerShell 6,0 mappar **traceroute** -parametern en väg mellan den lokala datorn och fjärrmålet som du anger med parametern **TargetName** .

```powershell
Test-Connection -TargetName www.microsoft.com -Traceroute | ForEach-Object {
  $_ | Format-Table Source, DestinationAddress, DestinationHost
  $_.Replies | ForEach-Object {
      $_ | Format-Table Hop, ReplyRouterAddress
      $_.PingReplies | Format-Table
  }
}
```

```Output
Tracing route to www.microsoft.com [96.6.27.90] over a maximum of 128 hops:
  1   0 ms   0 ms   0 ms   192.168.0.3 [192.168.0.3]
  2   0 ms   0 ms   0 ms   192.168.1.1 [192.168.1.1]
  3   3 ms   29 ms   4 ms   96.6.27.90 [96.6.27.90]
Trace complete.

Source      DestinationAddress DestinationHost   Replies
------      ------------------ ---------------   -------
SERVER01    96.6.27.90         www.microsoft.com {, , }

Hop ReplyRouterAddress
--- ------------------
  1 192.168.0.3

    Status Address      RoundtripTime Options Buffer
    ------ -------      ------------- ------- ------
TtlExpired 192.168.86.1             0         {}
TtlExpired 192.168.86.1             0         {}
TtlExpired 192.168.86.1             0         {}

Hop ReplyRouterAddress
--- ------------------
  2 192.168.1.1

    Status Address     RoundtripTime Options Buffer
    ------ -------     ------------- ------- ------
TtlExpired 192.168.1.1             0         {}
TtlExpired 192.168.1.1             0         {}
TtlExpired 192.168.1.1             0         {}

Hop ReplyRouterAddress
--- ------------------
  3 96.6.27.90

 Status Address    RoundtripTime Options                                   Buffer
 ------ -------    ------------- -------                                   ------
Success 96.6.27.90             3 System.Net.NetworkInformation.PingOptions {97, 98, 99, 100…}
Success 96.6.27.90             2 System.Net.NetworkInformation.PingOptions {97, 98, 99, 100…}
Success 96.6.27.90             4 System.Net.NetworkInformation.PingOptions {97, 98, 99, 100…}
```

`Test-Connection`Kommandot använder parametern **traceroute** . Resultaten, som är `[Microsoft.PowerShell.Commands.TestConnectionCommand+TraceRouteResult]` objekt, är skickas till `ForEach-Object` cmdleten. `ForEach-Object` skapar ett strukturerat utdata från de inneslutna `[Microsoft.PowerShell.Commands.TestConnectionCommand+TraceRouteReply]` objekten och efterföljande `[System.Net.NetworkInformation.PingReply]` objekt.

## PARAMETRAR

### -BufferSize

Anger storlek, i byte, för den buffert som skickas med det här kommandot. Standardvärdet är 32.

```yaml
Type: System.Int32
Parameter Sets: PingCount, PingContinues
Aliases: Size, Bytes, BS

Required: False
Position: Named
Default value: 32
Accept pipeline input: False
Accept wildcard characters: False
```

### -Antal

Anger hur många eko-begäranden som ska skickas. Standardvärdet är 4.

```yaml
Type: System.Int32
Parameter Sets: PingCount
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
Parameter Sets: PingCount, PingContinues
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
Parameter Sets: PingCount, PingContinues
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
Parameter Sets: PingCount, PingContinues, TraceRoute
Aliases: Ttl, TimeToLive, Hops

Required: False
Position: Named
Default value: 128 hops in Windows 10
Accept pipeline input: False
Accept wildcard characters: False
```

### -Ping

Gör att cmdleten gör ett ping-test, vilket är standard åtgärden.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PingCount, PingContinues
Aliases:

Required: False
Position: Named
Default value: Ping test
Accept pipeline input: False
Accept wildcard characters: False
```

### – Tyst

Parametern **quiet** returnerar ett **booleskt** värde i ett **system. Boolean** -objekt. Om du använder den här parametern utelämnas alla fel.

Varje anslutning som testas returnerar ett **booleskt** värde. Om parametern **TargetName** anger flera datorer returneras en matris med **booleska** värden.

Om **några** pingar lyckas `$True` returneras.

Om **alla** pingar inte fungerar `$False` returneras.

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

Gör att cmdleten försöker matcha målets DNS-namn.

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

```yaml
Type: System.String
Parameter Sets: PingCount, PingContinues, TraceRoute, ConnectionByTCPPort
Aliases:

Required: False
Position: Named
Default value: Local computer
Accept pipeline input: False
Accept wildcard characters: False
```

### -TargetName

Anger vilka datorer som ska testas. Ange dator namnen eller ange IP-adresser i IPv4-eller IPv6-format. Jokertecken är inte tillåtna. Den här parametern är obligatorisk. **Computername** är ett alias för den här parametern.

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

### – TCPPort

Anger TCP-portnumret på det mål som ska användas vid testet av TCP-anslutningen. Cmdleten kommer att försöka upprätta en TCP-anslutning till den angivna porten på målet.

```yaml
Type: System.Int32
Parameter Sets: ConnectionByTCPPort
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
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

Gör att cmdleten gör ett traceroute-test. När den här parametern används returnerar cmdleten ett- `TestConnectionCommand+TraceRouteResult` objekt.

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

### – Fortsätter

Gör att cmdleten skickar ping-begäranden kontinuerligt. Den här parametern kan inte användas med **Count** -parametern.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PingContinues
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MTUSizeDetect

Den här parametern används för att identifiera MTU-storleken för sökvägen. Cmdleten returnerar ett **PingReply # MTUSize** -objekt som innehåller sökvägen till MÅLETs MTU-storlek. Mer information om MTU för sökvägen finns i artikeln [sökväg för MTU-identifiering](https://wikipedia.org/wiki/Path_MTU_Discovery) i wikipedia.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DetectionOfMTUSize
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Inget

Du kan inte skicka pipe-ininformation till denna cmdlet.

## UTDATA

### TestConnectionCommand + PingReport, TestConnectionCommand + TraceRouteResult, Boolean, PingReply # MTUSize

Om du anger en **quiet** -parameter returneras ett **booleskt** värde. Om flera anslutningar testas returneras en matris med **booleska** värden. Annars `Test-Connection` returnerar ett **TestConnectionCommand + PingReport** -objekt för varje ping.

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Starta om datorn](Restart-Computer.md)

[Stoppa – dator](Stop-Computer.md)
