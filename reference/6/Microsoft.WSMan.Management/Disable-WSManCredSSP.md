---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/disable-wsmancredssp?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-WSManCredSSP
ms.openlocfilehash: 6b6cf6b4056dd5907f6a43cd9cf6d491bc7512b9
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263996"
---
# Disable-WSManCredSSP

## SAMMANFATTNING
Inaktiverar CredSSP-autentisering på en dator.

## SYNTAX

```
Disable-WSManCredSSP [-Role] <String> [<CommonParameters>]
```

## BESKRIVNING
Cmdlet **: en Disable-WSManCredSSP** inaktiverar CredSSP-autentisering (Credential Security Support Provider) på en klient eller på en serverdator.
När CredSSP-autentisering används skickas användarautentiseringsuppgifter till en fjärrdator som ska autentiseras.

Använd denna cmdlet för att inaktivera CredSSP på klienten genom att ange klienten i *roll* parametern.
Denna cmdlet utför följande åtgärder:

- Inaktiverar CredSSP på klienten. Denna cmdlet anger WS-Management inställningen **\<localhost|computername\> \Client\Auth\CredSSP** till false.
- Tar bort alla WSMan/*-inställningar från Windows CredSSP-principen **AllowFreshCredentials** på klienten.

Använd denna cmdlet för att inaktivera CredSSP på servern genom att ange server i *roll*.
Denna cmdlet utför följande åtgärd:

- Inaktiverar CredSSP på servern. Denna cmdlet anger WS-Management inställningen **\<localhost|computername\> \Service\Auth\CredSSP** till false.

Varning! CredSSP-autentisering delegerar användarautentiseringsuppgifter från den lokala datorn till en fjärrdator.
Den här metoden ökar säkerhets risken för Fjärråtgärden.
Om fjärrdatorn komprometteras, när autentiseringsuppgifter skickas till den, kan autentiseringsuppgifterna användas för att kontrol lera nätverks sessionen.

## EXEMPEL

### Exempel 1: inaktivera CredSSP på en klient

```
PS C:\> Disable-WSManCredSSP -Role Client
```

Det här kommandot inaktiverar CredSSP på klienten, vilket förhindrar delegering till servrar.

### Exempel 2: inaktivera CredSSP på en server

```
PS C:\> Disable-WSManCredSSP -Role Server
```

Det här kommandot inaktiverar CredSSP på servern, vilket förhindrar delegering från klienter.

## PARAMETRAR

### -Roll
Anger om CredSSP ska inaktive ras som en klient eller som en server.
De acceptabla värdena för den här parametern är: klient och server.

Om du anger klient utför denna cmdlet följande åtgärder:

- Inaktiverar CredSSP på klienten. Den här cmdleten anger WS-Management anger **\<localhost|computername\> \Client\Auth\CredSSP** till false.
- Tar bort alla WSMan/*-inställningar från Windows CredSSP-principen **AllowFreshCredentials** på klienten.

Om du anger Server utför denna cmdlet följande åtgärd:

- Inaktiverar CredSSP på servern. Denna cmdlet anger WS-Management inställningen **\<localhost|computername\> \Service\Auth\CredSSP** till false.

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

### Inget
Denna cmdlet genererar inga utdata.

## ANTECKNINGAR

* Använd Enable-WSManCredSSP-cmdleten om du vill aktivera CredSSP-autentisering.

*

## RELATERADE LÄNKAR

[Anslut-WSMan](Connect-WSMan.md)

[Koppla från-WSMan](Disconnect-WSMan.md)

[Aktivera – WSManCredSSP](Enable-WSManCredSSP.md)

[Get-WSManCredSSP](Get-WSManCredSSP.md)

[Get-WSManInstance](Get-WSManInstance.md)

[Invoke-WSManAction](Invoke-WSManAction.md)

[New-WSManInstance](New-WSManInstance.md)

[New-WSManSessionOption](New-WSManSessionOption.md)

[Remove-WSManInstance](Remove-WSManInstance.md)

[Set-WSManInstance](Set-WSManInstance.md)

[Set-WSManQuickConfig](Set-WSManQuickConfig.md)

[Test-WSMan](Test-WSMan.md)
