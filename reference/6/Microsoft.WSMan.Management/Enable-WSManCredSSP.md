---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 08/20/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/enable-wsmancredssp?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-WSManCredSSP
ms.openlocfilehash: 48429114a8e174351f4323acb501f89261e4a40a
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/23/2020
ms.locfileid: "93268479"
---
# Enable-WSManCredSSP

## SAMMANFATTNING
Aktiverar autentisering med CredSSP (Credential Security Support Provider) på en dator.

## SYNTAX

### Alla

```
Enable-WSManCredSSP [[-DelegateComputer] <String[]>] [-Force] [-Role] <String> [<CommonParameters>]
```

## BESKRIVNING

`Enable-WSManCredSSP`Cmdlet: en aktiverar CredSSP-autentisering på en klient eller på en serverdator.
När CredSSP-autentisering används skickas användarautentiseringsuppgifter till en fjärrdator som ska autentiseras. Den här typen av autentisering är utformad för kommandon som skapar en fjärrsession från en annan fjärran sluten session. Om du till exempel vill köra ett bakgrunds jobb på en fjärrdator använder du den här typen av autentisering.

`Enable-WSManCredSSP` kan aktivera CredSSP på en **klient** eller **Server**. Om du vill aktivera CredSSP på en klient anger du **client** i **roll** parametern. Klienterna delegerar explicita autentiseringsuppgifter till en server när serverautentisering uppnås. Om du vill aktivera CredSSP på en server anger du **Server** i **roll** parametern. En server fungerar som ett ombud för-klienter. Mer information finns i **roll** i avsnittet parametrar.

> [!CAUTION]
> CredSSP-autentisering delegerar användarautentiseringsuppgifter från den lokala datorn till en fjärrdator. Den här metoden ökar säkerhets risken för Fjärråtgärden. Om fjärrdatorn komprometteras, när autentiseringsuppgifter skickas till den, kan autentiseringsuppgifterna användas för att kontrol lera nätverks sessionen.

## EXEMPEL

### Exempel 1: delegera klientautentiseringsuppgifter

Det här exemplet gör att klientautentiseringsuppgifterna kan delegeras till en dator genom att använda det fullständigt kvalificerade domän namnet.

```powershell
Enable-WSManCredSSP -Role "Client" -DelegateComputer "Server02.fabrikam.com"
```

```Output
cfg         : http://schemas.microsoft.com/wbem/wsman/1/config/client/auth
lang        : en-US
Basic       : true
Digest      : true
Kerberos    : true
Negotiate   : true
Certificate : true
CredSSP     : true
```

### Exempel 2: delegera klientautentiseringsuppgifter till alla datorer i en domän

Det här exemplet gör att klientautentiseringsuppgifterna kan delegeras till alla datorer i **fabrikam.com** -domänen. Jokertecknet asterisk ( `*` ) anger alla datorer.

> [!NOTE]
> Med jokertecken med parametern **DelegateComputer** kan du aktivera CredSSP på fler datorer än vad som behövs.

```powershell
Enable-WSManCredSSP -Role "Client" -DelegateComputer "*.fabrikam.com"
```

```Output
cfg         : http://schemas.microsoft.com/wbem/wsman/1/config/client/auth
lang        : en-US
Basic       : true
Digest      : true
Kerberos    : true
Negotiate   : true
Certificate : true
CredSSP     : true
```

### Exempel 3: delegera klientautentiseringsuppgifter till flera datorer

Det här exemplet gör att klientautentiseringsuppgifterna kan delegeras till flera datorer.

```powershell
$servers = "server02.fabrikam.com", "server03.fabrikam.com", "server04.fabrikam.com"
Enable-WSManCredSSP -Role "Client" -DelegateComputer $servers
```

```Output
cfg         : http://schemas.microsoft.com/wbem/wsman/1/config/client/auth
lang        : en-US
Basic       : true
Digest      : true
Kerberos    : true
Negotiate   : true
Certificate : true
CredSSP     : true
```

`$servers`Variabeln innehåller en lista över Server namn. `Enable-WSManCredSSP` använder **roll** parametern för att ange **klient** rollen. **DelegateComputer** hämtar dator namnen från `$servers` variabeln.

### Exempel 4: Tillåt att en dator fungerar som ett ombud

I det här exemplet kan en dator fungera som ett ombud för en annan. `Enable-WSManCredSSP`Cmdleten, som visas i de tidigare exemplen, aktiverar endast CredSSP-autentisering på klienten och anger de fjärrdatorer som kan agera för dess räkning. För att fjärrdatorn ska fungera som ett ombud för klienten måste CredSSP-objektet i noden **tjänst** för WSMan anges till true. I det här exemplet anges CredSSP-objektet i **tjänst-** noden för WSMan till true.

```powershell
Enable-WSManCredSSP -Role "Server"
```

### Exempel 5: Tillåt att en dator fungerar som ett ombud med hjälp av Set-Item

I det här exemplet kan en dator fungera som ett ombud för en annan dator. `Enable-WSManCredSSP`Kommandona, som visas i de tidigare exemplen, aktiverar endast CredSSP-autentisering på klient datorn och de anger fjärrdatorer som kan agera för klient datorns räkning. För att fjärrdatorn ska fungera som ett ombud för klient datorn måste CredSSP-objektet i tjänst katalogen för WSMan-providern anges till sant.

```powershell
Connect-WSMan -ComputerName "server02"
Set-Item -Path "WSMan:\server02\service\auth\credSSP" -Value $True
```

`Connect-WSMan` skapar en anslutning till fjärrdatorn, server02. `Set-Item` använder parametern **Path** för att ange platsen för **WSMan** -providern. Parametern **Value** anger **tjänst** inställningen till true.

## PARAMETRAR

### -DelegateComputer

Anger servrar som klientautentiseringsuppgifterna är delegerade till. Det bästa sättet är att använda fullständigt kvalificerade domän namn.

Jokertecken accepteras, men kan aktivera CredSSP på fler datorer än vad som behövs.

Om **roll** parametern är **klient** måste du ange den här parametern. Ange inte den här parametern om **rollen** är **Server**.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Force

Tvingar kommandot att köras utan att fråga användaren om bekräftelse.

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

### -Roll

Anger om CredSSP ska aktive ras som en klient eller som en server. De acceptabla värdena för den här parametern är: **klient** och **Server**.

Om du anger **klient** utförs följande åtgärder. De här inställningarna gör att klienten kan delegera explicita autentiseringsuppgifter till en server när serverautentisering uppnås.

- Aktiverar CredSSP på klienten.
- Ställer in WS-Management inställningen `\<localhost|computername\>\Client\Auth\CredSSP` till sant.
- Anger Windows CredSSP-principen **AllowFreshCredentials** till **WSMan/delegaten** på klienten.

Om du anger **Server** utförs följande åtgärder. Med den här princip inställningen kan servern agera som ombud för klienter.

- Aktiverar CredSSP på servern.
- Ställer in WS-Management inställningen `\<localhost|computername\>\Service\Auth\CredSSP` till sant.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Client, Server

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Inget

Denna cmdlet accepterar inte några indatatyper.

## UTDATA

### System.Xml.Xml-element

Om CredSSP-autentisering har Aktiver ATS genererar denna cmdlet ett **XMLElement** -objekt.

## ANTECKNINGAR

Använd cmdleten om du vill inaktivera CredSSP-autentisering `Disable-WSManCredSSP` .

## RELATERADE LÄNKAR

[Anslut-WSMan](Connect-WSMan.md)

[Disable-WSManCredSSP](Disable-WSManCredSSP.md)

[Koppla från-WSMan](Disconnect-WSMan.md)

[Get-WSManCredSSP](Get-WSManCredSSP.md)

[Get-WSManInstance](Get-WSManInstance.md)

[Invoke-WSManAction](Invoke-WSManAction.md)

[New-WSManInstance](New-WSManInstance.md)

[New-WSManSessionOption](New-WSManSessionOption.md)

[Remove-WSManInstance](Remove-WSManInstance.md)

[Set-WSManInstance](Set-WSManInstance.md)

[Set-WSManQuickConfig](Set-WSManQuickConfig.md)

[Test-WSMan](Test-WSMan.md)
