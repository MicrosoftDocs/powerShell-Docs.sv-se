---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 02/07/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-pssessionoption?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSSessionOption
ms.openlocfilehash: 10f086c3fc2090681f669d481eb880d81ea9d245
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266859"
---
# New-PSSessionOption

## SAMMANFATTNING
Skapar ett objekt som innehåller avancerade alternativ för en PSSession.

## SYNTAX

```
New-PSSessionOption [-MaximumRedirection <Int32>] [-NoCompression] [-NoMachineProfile] [-Culture <CultureInfo>]
 [-UICulture <CultureInfo>] [-MaximumReceivedDataSizePerCommand <Int32>] [-MaximumReceivedObjectSize <Int32>]
 [-OutputBufferingMode <OutputBufferingMode>] [-MaxConnectionRetryCount <Int32>]
 [-ApplicationArguments <PSPrimitiveDictionary>] [-OpenTimeout <Int32>] [-CancelTimeout <Int32>]
 [-IdleTimeout <Int32>] [-ProxyAccessType <ProxyAccessType>] [-ProxyAuthentication <AuthenticationMechanism>]
 [-ProxyCredential <PSCredential>] [-SkipCACheck] [-SkipCNCheck] [-SkipRevocationCheck]
 [-OperationTimeout <Int32>] [-NoEncryption] [-UseUTF16] [-IncludePortInSPN] [<CommonParameters>]
```

## BESKRIVNING

`New-PSSessionOption`Cmdleten skapar ett objekt som innehåller avancerade alternativ för en **PSSession** (User-Managed session). Du kan använda objektet som värdet för parametern **SessionOption** för cmdletar som skapar en **PSSession** , till exempel, `New-PSSession` `Enter-PSSession` och `Invoke-Command` .

Utan parametrar `New-PSSessionOption` genererar ett objekt som innehåller standardvärdena för alla alternativ. Eftersom alla egenskaper kan redige ras kan du använda det resulterande objektet som mall och skapa standard alternativ objekt för ditt företag.

Du kan också spara ett alternativ för session i `$PSSessionOption` Preference-variabeln. Värdena för den här variabeln upprättar nya standardvärden för session-alternativen. De träder i kraft när inga sessionsinställningar har ställts in för sessionen och de har företräde framför alternativ som angetts i konfigurationen av sessionen, men du kan åsidosätta dem genom att ange sessionsinställningar eller ett alternativ objekt för session i en cmdlet som skapar en session. Mer information om `$PSSessionOption` variabeln Preference finns [about_Preference_Variables](About/about_Preference_Variables.md).

När du använder ett alternativ objekt för session i en cmdlet som skapar en session, prioriteras värdena för sessions-alternativ framför standardvärden för sessioner som angetts i variabeln $PSSessionOption och i konfigurationen av sessionen. De har dock inte företräde framför maximala värden, kvoter eller gränser som angetts i konfigurationen av sessionen. För ytterligare information om sessionskonfigurationer, se [about_Session_Configurations](About/about_Session_Configurations.md).

## EXEMPEL

### Exempel 1: skapa ett standard alternativ för session

Det här kommandot skapar ett alternativ för session som innehåller alla standardvärden.

```powershell
New-PSSessionOption
```

```Output
MaximumConnectionRedirectionCount : 5
NoCompression                     : False
NoMachineProfile                  : False
ProxyAccessType                   : IEConfig
ProxyAuthentication               : Negotiate
ProxyCredential                   :
SkipCACheck                       : False
SkipCNCheck                       : False
SkipRevocationCheck               : False
OperationTimeout                  : 00:03:00
NoEncryption                      : False
UseUTF16                          : False
Culture                           :
UICulture                         :
MaximumReceivedDataSizePerCommand :
MaximumReceivedObjectSize         :
ApplicationArguments              :
OpenTimeout                       : 00:03:00
CancelTimeout                     : 00:01:00
IdleTimeout                       : 00:04:00
```

### Exempel 2: Konfigurera en session med hjälp av ett session alternativ-objekt

I det här exemplet visas hur du konfigurerar en session med hjälp av ett alternativ objekt för session.

```powershell
$pso = New-PSSessionOption -Culture "fr-fr" -MaximumReceivedObjectSize 10MB
New-PSSession -ComputerName Server01 -SessionOption $pso
```

Det första kommandot skapar ett nytt alternativ för session och sparar det i `$pso` variabelns värde. Det andra kommandot använder `New-PSSession` cmdleten för att skapa en session på Server01-fjärrdatorn. Kommandot använder Session-objektet i värdet för `$pso` variabeln som värdet för parametern **SessionOption** för kommandot.

### Exempel 3: starta en interaktiv session

Det här kommandot använder `Enter-PSSession` cmdleten för att starta en interaktiv session med Server01-datorn.

```powershell
Enter-PSSession -ComputerName Server01 -SessionOption (New-PSSessionOption -NoEncryption -NoCompression)
```

Värdet för parametern **SessionOption** är ett `New-PSSessionOption` kommando som har parametrarna Encryption och **nocompression** . **NoEncryption**

`New-PSSessionOption`Kommandot omges av parenteser för att kontrol lera att det körs före `Enter-PSSession` kommandot.

### Exempel 4: ändra ett alternativ objekt för session

Det här exemplet visar att du kan ändra objektet Session-alternativ. Alla egenskaper har läs-/skriv värden.

```powershell
$a = New-PSSessionOption
$a.OpenTimeout
```

```Output
Days              : 0
Hours             : 0
Minutes           : 3
Seconds           : 0
Milliseconds      : 0
Ticks             : 1800000000
TotalDays         : 0.00208333333333333
TotalHours        : 0.05
TotalMinutes      : 3
TotalSeconds      : 180
TotalMilliseconds : 180000
```

```powershell
$a.UICulture = (Get-UICulture)
$a.OpenTimeout = (New-Timespan -Minutes 4)
$a.MaximumConnectionRedirectionCount = 1
$a
```

```Output
MaximumConnectionRedirectionCount : 1
NoCompression                     : False
NoMachineProfile                  : False
ProxyAccessType                   : IEConfig
ProxyAuthentication               : Negotiate
ProxyCredential                   :
SkipCACheck                       : False
SkipCNCheck                       : False
SkipRevocationCheck               : False
OperationTimeout                  : 00:03:00
NoEncryption                      : False
UseUTF16                          : False
Culture                           :
UICulture                         : en-US
MaximumReceivedDataSizePerCommand :
MaximumReceivedObjectSize         :
ApplicationArguments              :
OpenTimeout                       : 00:04:00
CancelTimeout                     : 00:01:00
IdleTimeout                       : 00:04:00
```

Använd den här metoden för att skapa ett standard-sessionsobjekt för ditt företag och skapa sedan anpassade versioner av det för specifika användnings områden.

### Exempel 5: skapa en inställnings variabel

Det här kommandot skapar en `$PSSessionOption` inställnings variabel.

```powershell
$PSSessionOption = New-PSSessionOption -OpenTimeOut 120000
```

När `$PSSessionOption` Preference-variabeln inträffar i sessionen, fastställer den standardvärden för alternativ i de sessioner som skapas med hjälp av `New-PSSession` `Enter-PSSession` cmdletarna,, och `Invoke-Command` .

Om du vill göra `$PSSessionOption` variabeln tillgänglig i alla sessioner lägger du till den i din PowerShell-session och i din PowerShell-profil.

Mer information om `$PSSessionOption` variabeln Preference finns [about_Preference_Variables](About/about_Preference_Variables.md).
Mer information om profiler finns [about_Profiles](About/about_Profiles.md).

### Exempel 6: uppfylla kraven för en fjärrsessions-konfiguration

Det här exemplet visar hur du använder ett **SessionOption** -objekt för att uppfylla kraven för en fjärrsessions-konfiguration.

```powershell
$skipCN = New-PSSessionOption -SkipCNCheck
New-PSSession -ComputerName 171.09.21.207 -UseSSL -Credential Domain01\User01 -SessionOption $SkipCN
```

Det första kommandot använder `New-PSSessionOption` cmdleten för att skapa ett session-objekt som har egenskapen **SkipCNCheck** . Kommandot sparar det resulterande sessions-objektet i `$skipCN` variabeln.

Det andra kommandot använder `New-PSSession` cmdleten för att skapa en ny session på en fjärrdator. `$skipCN`Check variabeln används i värdet för parametern **SessionOption** .

Eftersom datorn identifieras med IP-adressen matchar inte värdet för parametern **computername** något av de gemensamma namnen i certifikatet som används för Secure SOCKETS Layer (SSL). Därför krävs alternativet **SkipCNCheck** .

### Exempel 7: gör argument tillgängliga för en fjärrsession

Det här exemplet visar hur du använder **ApplicationArguments** -parametern för `New-PSSessionOption` cmdleten för att göra ytterligare data tillgängliga för fjärrsessionen.

```powershell
$team = @{Team="IT"; Use="Testing"}
$TeamOption = New-PSSessionOption -ApplicationArguments $team
$s = New-PSSession -ComputerName Server01 -SessionOption $TeamOption
Invoke-Command -Session $s {$PSSenderInfo.ApplicationArguments}
```

```Output
Name                 Value
----                 -----
Team                 IT
Use                  Testing
PSVersionTable       {CLRVersion, BuildVersion, PSVersion, WSManStackVersion...}
```

```powershell
Invoke-Command -Session $s {
  if ($PSSenderInfo.ApplicationArguments.Use -ne "Testing") {
    .\logFiles.ps1
  }
  else {
    "Just testing."
  }
}
```

```Output
Just testing.
```

Det första kommandot skapar en hash-tabell med två nycklar, **team** och **användning**. Kommandot sparar hash-tabellen i `$team` variabeln. Mer information om hash-tabeller finns i [about_Hash_Tables](about/about_Hash_Tables.md).

Därefter `New-PSSessionOption` skapar cmdleten med hjälp av parametern **ApplicationArguments** ett alternativ för session som sparats i `$team` variabeln. När `New-PSSessionOption` skapar objektet Session, konverterar det automatiskt hash-tabellen i värdet för parametern **ApplicationArguments** till en primitiv ord lista så att data kan överföras till fjärrsessionen på ett tillförlitligt sätt.

`New-PSSession`Cmdleten startar en session på Server01-datorn. Parametern **SessionOption** används för att inkludera alternativen i `$teamOption` variabeln.

`Invoke-Command`Cmdleten visar att data i `$team` variabeln är tillgängliga för kommandon i fjärrsessionen. Data visas i egenskapen **ApplicationArguments** för den `$PSSenderInfo` automatiska variabeln.

Den slutgiltiga `Invoke-Command` visar hur data kan användas.

## PARAMETRAR

### -ApplicationArguments

Anger en primitiv ord lista som skickas till fjärrsessionen. Kommandon och skript i fjärrsessionen, inklusive start skript i konfigurationen av sessionen, kan hitta den här ord listan i egenskapen **ApplicationArguments** för den `$PSSenderInfo` automatiska variabeln. Du kan använda den här parametern för att skicka data till fjärrsessionen.

Mer information finns i [about_Hash_Tables](about/about_Hash_Tables.md), [about_Session_Configurations](About/about_Session_Configurations.md)och [about_Automatic_Variables](about/about_Automatic_Variables.md).

```yaml
Type: System.Management.Automation.PSPrimitiveDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CancelTimeout

Anger hur lång tid PowerShell väntar på att en avbrotts åtgärd (CTRL + C) ska slutföras innan den slutar.
Ange ett värde i millisekunder.

Standardvärdet är 60000 (en minut). Värdet 0 (noll) innebär ingen tids gräns. kommandot fortsätter på obestämd tid.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: CancelTimeoutMSec

Required: False
Position: Named
Default value: 60000
Accept pipeline input: False
Accept wildcard characters: False
```

### – Kultur

Anger kulturen som ska användas för sessionen. Ange ett kultur namn i `<languagecode2>-<country/regioncode2>` formatet (t `ja-JP` . ex.), en variabel som innehåller ett **CultureInfo** -objekt eller ett kommando som hämtar ett **CultureInfo** -objekt.

Standardvärdet är `$Null` och kulturen som anges i operativ systemet används i sessionen.

```yaml
Type: System.Globalization.CultureInfo
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -IdleTimeout

Anger hur länge sessionen förblir öppen om fjärrdatorn inte får någon kommunikation från den lokala datorn. Detta inkluderar pulsslags signalen. När intervallet går ut stängs sessionen.

Värdet för tids gräns för inaktivitet är av stor betydelse om du vill koppla från och återansluta till en session. Du kan bara återansluta om sessionen inte har uppnådde sin tids gräns.

Ange ett värde i millisekunder. Det minsta värdet är 60000 (1 minut). Det maximala värdet är värdet för **MaxIdleTimeoutms** -egenskapen i konfigurationen av sessionen. Standardvärdet,-1, anger inte en tids gräns för inaktivitet.

Sessionen använder tids gränsen för inaktivitet som anges i sessionens alternativ, om det finns några. Om inget anges (-1) använder sessionen värdet för **IdleTimeoutMs** -egenskapen i sessionen eller värdet för WSMan-gränssnittets timeout ( `WSMan:\<ComputerName>\Shell\IdleTimeout` ), beroende på vilket som är kortast.

Om tids gränsen för inaktivitet som anges i session-alternativen överskrider värdet för **MaxIdleTimeoutMs** -egenskapen i konfigurationen för sessionen, Miss lyckas kommandot för att skapa en session.

**IdleTimeoutMs** -värdet för standard konfigurationen av **Microsoft. PowerShell** -sessionen är 7200000 millisekunder (2 timmar). Dess **MaxIdleTimeoutMs** -värde är 2147483647 millisekunder ( \> 24 dagar). Standardvärdet för WSMan-gränssnittets inaktiva timeout ( `WSMan:\<ComputerName>\Shell\IdleTimeout` ) är 7200000 millisekunder (2 timmar).

Timeout-värdet för inaktivitet i en session kan också ändras när du kopplar från en-session eller återansluter till en session. Mer information finns i `Disconnect-PSSession` och `Connect-PSSession`.

I Windows PowerShell 2,0 är standardvärdet för **idleTimeout** -parametern 240000 (4 minuter).

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: IdleTimeoutMSec

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -IncludePortInSPN

Inkluderar port numret i tjänstens huvud namn (SPN) som används för Kerberos-autentisering, till exempel `HTTP://<ComputerName>:5985` . Det här alternativet tillåter en klient som använder ett SPN-namn som inte är standard för att autentisera mot en fjärrdator som använder Kerberos-autentisering.

Alternativet är utformat för företag där flera tjänster som stöder Kerberos-autentisering körs under olika användar konton. Till exempel kan ett IIS-program som tillåter Kerberos-autentisering kräva att standard-SPN registreras på ett användar konto som skiljer sig från dator kontot. I sådana fall kan PowerShell-fjärrkommunikation inte använda Kerberos för att autentisera eftersom det kräver ett SPN som är registrerat på dator kontot. För att lösa det här problemet kan administratörer skapa olika SPN-namn, till exempel genom att använda **Setspn.exe** som är registrerade för olika användar konton och kan skilja mellan dem genom att inkludera port numret i SPN.

Mer information finns i [Översikt över Setspn](/previous-versions/windows/it-pro/windows-server-2003/cc773257(v=ws.10)).

Den här parametern introducerades i Windows PowerShell 3,0.

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

### -MaxConnectionRetryCount

Anger hur många gånger PowerShell försöker upprätta en anslutning till en måldator om det aktuella försöket Miss lyckas på grund av nätverks problem. Standardvärdet är 5.

Den här parametern har lagts till för PowerShell version 5,0.

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

### -MaximumReceivedDataSizePerCommand

Anger det maximala antalet byte som den lokala datorn kan ta emot från fjärrdatorn i ett enda kommando. Ange ett värde i byte. Som standard finns det ingen data storleks gräns.

Det här alternativet är utformat för att skydda resurserna på klient datorn.

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

### -MaximumReceivedObjectSize

Anger den maximala storleken på ett objekt som den lokala datorn kan ta emot från fjärrdatorn. Det här alternativet är utformat för att skydda resurserna på klient datorn. Ange ett värde i byte.

Om du utelämnar den här parametern i Windows PowerShell 2,0 finns det ingen storleks gräns för objekt. Från och med Windows PowerShell 3,0 är standardvärdet 200 MB om du utelämnar den här parametern.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 200 MB
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaximumRedirection

Anger hur många gånger PowerShell omdirigerar en anslutning till en alternativ Uniform Resource Identifier (URI) innan anslutningen Miss lyckas. Standardvärdet är 5. Värdet 0 (noll) förhindrar all omdirigering.

Det här alternativet används endast i sessionen när parametern **AllowRedirection** används i kommandot som skapar sessionen.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 5
Accept pipeline input: False
Accept wildcard characters: False
```

### -Nocompression

Inaktiverar paket komprimering i sessionen. Komprimering använder fler processor cykler, men det gör överföringen snabbare.

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

### – Encryption

Inaktiverar data kryptering.

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

### -NoMachineProfile

Förhindrar inläsning av användarens Windows-användarprofil. Därför kan sessionen skapas snabbare, men användarspecifika register inställningar, objekt som miljövariabler och certifikat är inte tillgängliga i sessionen.

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

### -Opentimey

Anger hur länge klient datorn väntar på att sessionen ska upprättas. När intervallet går ut Miss lyckas kommandot för att upprätta anslutningen. Ange ett värde i millisekunder.

Standardvärdet är 180000 (3 minuter). Värdet 0 (noll) innebär ingen tids gräns. kommandot fortsätter på obestämd tid.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: OpenTimeoutMSec

Required: False
Position: Named
Default value: 180000 (3 minutes)
Accept pipeline input: False
Accept wildcard characters: False
```

### -OperationTimeout

Fastställer den längsta tid som en åtgärd i sessionen kan köras. När intervallet går ut Miss lyckas åtgärden. Ange ett värde i millisekunder.

Standardvärdet är 180000 (3 minuter). Värdet 0 (noll) innebär ingen tids gräns. åtgärden fortsätter på obestämd tid.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: OperationTimeoutMSec

Required: False
Position: Named
Default value: 180000 (3 minutes)
Accept pipeline input: False
Accept wildcard characters: False
```

### -OutputBufferingMode

Anger hur kommandoutdata hanteras i frånkopplade sessioner när utdatabufferten blir full.

Om buffring av utdata inte har ställts in i sessionen eller i konfigurationen av sessionen är standardvärdet **block**. Användare kan också ändra läget för buffring av utdata när de kopplar från sessionen.

Om du utelämnar den här parametern, är värdet för **OutputBufferingMode** för Session-objektet none. Värdet **block** eller **Drop** åsidosätter transport alternativet utdata buffer i konfigurationen av sessionen. De acceptabla värdena för den här parametern är:

- Undantaget. När utdatabufferten är full pausas körningen tills bufferten är klar.
- Skugg. När utdatabufferten är full fortsätter körningen. När nya utdata sparas, ignoreras det äldsta resultatet.
- Inga. Inget utdata buffer-läge har angetts.

Mer information om transport alternativet för buffring av utdata finns i `New-PSTransportOption` .

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Management.Automation.Runspaces.OutputBufferingMode
Parameter Sets: (All)
Aliases:
Accepted values: None, Drop, Block

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProxyAccessType

Bestämmer vilken mekanism som används för att matcha värd namnet. De acceptabla värdena för den här parametern är:

- IEConfig
- WinHttpConfig
- Identifiera automatiskt
- NoProxyServer
- Inget

Standardvärdet är none.

Information om värdena för den här parametern finns i [ProxyAccessType-uppräkning](/dotnet/api/system.management.automation.remoting.proxyaccesstype?redirectedfrom=MSDN&view=powershellsdk-1.1.0).

```yaml
Type: System.Management.Automation.Remoting.ProxyAccessType
Parameter Sets: (All)
Aliases:
Accepted values: None, IEConfig, WinHttpConfig, AutoDetect, NoProxyServer

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProxyAuthentication

Anger den autentiseringsmetod som används för proxy-matchning. De acceptabla värdena för den här parametern är: **Basic** , **Digest** och **Negotiate**. Standardvärdet är **Negotiate**.

Mer information om värdena för den här parametern finns i [AuthenticationMechanism-uppräkning](/dotnet/api/system.management.automation.runspaces.authenticationmechanism?redirectedfrom=MSDN&view=powershellsdk-1.1.0).

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: (All)
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: Negotiate
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProxyCredential

Anger de autentiseringsuppgifter som ska användas för proxyautentisering. Ange en variabel som innehåller ett **PSCredential** -objekt eller ett kommando som hämtar ett **PSCredential** -objekt, t `Get-Credential` . ex. ett kommando. Om det här alternativet inte anges anges inga autentiseringsuppgifter.

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

### -SkipCACheck

Anger att när den ansluter via HTTPS, verifierar inte klienten att Server certifikatet är signerat av en betrodd certifikat utfärdare (CA).

Använd bara det här alternativet när fjärrdatorn är betrodd genom att använda en annan mekanism, till exempel när fjärrdatorn är en del av ett nätverk som är fysiskt säkert och isolerat eller när fjärrdatorn visas som en betrodd värd i en WinRM-konfiguration.

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

### -SkipCNCheck

Anger att serverns certifikats allmänna namn inte behöver matcha serverns värdnamn. Det här alternativet används endast i fjärråtgärder som använder HTTPS-protokollet.

Använd endast det här alternativet för betrodda datorer.

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

### -SkipRevocationCheck

Verifierar inte Server certifikatets återkallnings status.

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

### – Värdet

Anger användar gränssnitts kulturen som ska användas för sessionen.

Giltiga värden är:

- Ett kultur namn i `<languagecode2>-<country/regioncode2>` format, t. ex. `ja-JP`
- En variabel som innehåller ett **CultureInfo** -objekt
- Ett kommando som hämtar ett **CultureInfo** -objekt, till exempel `Get-Culture`

Standardvärdet är `$null` och den användar gränssnitts kultur som anges i operativ systemet när sessionen skapas används i sessionen.

```yaml
Type: System.Globalization.CultureInfo
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseUTF16

Anger att denna cmdlet kodar begäran i UTF16-format istället för UTF8-format.

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

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Inget

Du kan inte skicka pipe-ininformation till denna cmdlet.

## UTDATA

### System. Management. Automation. Remoting. PSSessionOption

## ANTECKNINGAR

Om parametern **SessionOption** inte används i ett kommando för att skapa en **PSSession** , bestäms sessions alternativen av egenskapsvärdena för `$PSSessionOption` Preference-variabeln, om den har angetts. Mer information om `$PSSessionOption` variabeln finns i [about_Preference_Variables](About/about_Preference_Variables.md).

Egenskaperna för ett konfigurations objekt för en session varierar beroende på vilka alternativ som har angetts för konfigurationen av sessionen och värdena för dessa alternativ. Dessutom har sessionsinställningar som använder en konfigurations fil för sessionen ytterligare egenskaper.

## RELATERADE LÄNKAR

[Retur-PSSession](Enter-PSSession.md)

[Invoke-kommando](Invoke-Command.md)

[New-PSSession](New-PSSession.md)
