---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/get-wsmancredssp?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-WSManCredSSP
ms.openlocfilehash: ce2046a9df5d4d02d718d6408c7a196a753c9914
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/21/2020
ms.locfileid: "93273152"
---
# Get-WSManCredSSP

## SAMMANFATTNING
Hämtar den-relaterade konfigurationen för Credential Security Support providern för klienten.

## SYNTAX

```
Get-WSManCredSSP [<CommonParameters>]
```

## BESKRIVNING
**Get-WSManCredSSP** -cmdlet: en hämtar providerns säkerhets support för Credential-relaterad konfiguration av klienten och servern.
Utdata visar om CredSSP-autentisering (Credential Security Support Provider) är aktive rad eller inaktive rad.
Denna cmdlet visar också konfigurations information för **AllowFreshCredentials** -principen för CredSSP.

När du använder CredSSP-autentisering skickas användarautentiseringsuppgifter till en fjärrdator som ska autentiseras.
Den här typen av autentisering är utformad för kommandon som skapar en fjärrsession från en annan fjärran sluten session.
Om du till exempel vill köra ett bakgrunds jobb på en fjärrdator använder du den här typen av autentisering.

Cmdlet: en utför följande åtgärder:

- Hämtar inställningen för WS-Management CredSSP på klienten ( **\<localhost|computername\> \Client\Auth\CredSSP** ).
- Hämtar princip inställningen för Windows CredSSP **AllowFreshCredentials**.
- Hämtar inställningen för WS-Management CredSSP på servern ( **\<localhost|computername\> \Service\Auth\CredSSP** ).

Varning! CredSSP-autentisering delegerar användarautentiseringsuppgifter från den lokala datorn till en fjärrdator.
Den här metoden ökar säkerhets risken för Fjärråtgärden.
Om fjärrdatorn komprometteras, när autentiseringsuppgifter skickas till den, kan autentiseringsuppgifterna användas för att kontrol lera nätverks sessionen.

## EXEMPEL

### Exempel 1: Visa CredSSP-konfiguration

```
PS C:\> Get-WSManCredSSP
```

Det här kommandot visar information om CredSSP-konfigurationen för både klienten och servern.

Utdata identifierar att datorn är eller inte har kon figurer ATS för CredSSP.

Om datorn är konfigurerad för CredSSP är detta utdata:

`The machine is configured to allow delegating fresh credentials to the following target(s): wsman/server02.accounting.fabrikam.com`

Om datorn inte är konfigurerad för CredSSP är detta utdata:

`The machine is not configured to allow delegating fresh credentials.`

## PARAMETRAR

### CommonParameters
Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Inget
Denna cmdlet accepterar inte några indatatyper.

## UTDATA

### Inget
Denna cmdlet genererar inga utdata.

## ANTECKNINGAR

* Använd Disable-WSManCredSSP-cmdleten om du vill inaktivera CredSSP-autentisering. Använd Enable-WSManCredSSP-cmdleten om du vill aktivera CredSSP-autentisering.

## RELATERADE LÄNKAR

[Anslut-WSMan](Connect-WSMan.md)

[Disable-WSManCredSSP](Disable-WSManCredSSP.md)

[Koppla från-WSMan](Disconnect-WSMan.md)

[Aktivera – WSManCredSSP](Enable-WSManCredSSP.md)

[Get-WSManInstance](Get-WSManInstance.md)

[Invoke-WSManAction](Invoke-WSManAction.md)

[New-WSManInstance](New-WSManInstance.md)

[New-WSManSessionOption](New-WSManSessionOption.md)

[Remove-WSManInstance](Remove-WSManInstance.md)

[Set-WSManInstance](Set-WSManInstance.md)

[Set-WSManQuickConfig](Set-WSManQuickConfig.md)

[Test-WSMan](Test-WSMan.md)
