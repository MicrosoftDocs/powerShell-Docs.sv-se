---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 02/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/get-localuser?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-LocalUser
ms.openlocfilehash: 34210145bcddc8d9420552d637a6cd6e5f8e61cc
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263505"
---
# Get-LocalUser

## SAMMANFATTNING
Hämtar lokala användar konton.

## SYNTAX

### Standard (standard)

```
Get-LocalUser [[-Name] <String[]>] [<CommonParameters>]
```

### SecurityIdentifier

```
Get-LocalUser [[-SID] <SecurityIdentifier[]>] [<CommonParameters>]
```

## BESKRIVNING

`Get-LocalUser`Cmdlet: en hämtar lokala användar konton. Denna cmdlet hämtar inbyggda standard användar konton, lokala användar konton som du har skapat och lokala konton som du har anslutit till Microsoft-konton.

> [!NOTE]
> Modulen Microsoft. PowerShell. LocalAccounts är inte tillgänglig i 32-bitars PowerShell på ett 64-bitars system.

## EXEMPEL

### Exempel 1: Hämta ett konto med hjälp av dess namn

I det här exemplet får du ett användar konto med namnet AdminContoso02.

```powershell
Get-LocalUser -Name "AdminContoso02"
```

```Output
Name             Enabled Description
----             ------- -----------
AdminContoso02   True    Description of this account.
```

### Exempel 2: Hämta ett konto som är anslutet till en Microsoft-konto

I det här exemplet får du ett användar konto som är anslutet till en Microsoft-konto. I det här exemplet används ett placeholder-värde för användar namnet för ett konto på Outlook.com.

```powershell
Get-LocalUser -Name "MicrosoftAccount\username@Outlook.com"
```

```Output
Name                                    Enabled  Description
----                                    -------  -----------
MicrosoftAccount\username@outlook.com  True     Description of this account.
```

### Exempel 3: Hämta ett konto som är anslutet till en Microsoft-konto

Det här exemplet hämtar ett lokalt användar konto som har angivet SID.

```powershell
Get-LocalUser -SID S-1-5-21-9526073513-1762370368-3942940353-500
```

```Output
Name          Enabled Description
----          ------- -----------
Administrator True    Built-in account for administering the computer/domain
```

## PARAMETRAR

### -Name

Anger en matris med namn på de användar konton som denna cmdlet hämtar. Du kan använda jokertecknet.

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -SID

Anger en matris med säkerhets-ID: n (sid) för de användar konton som denna cmdlet hämtar.

```yaml
Type: System.Security.Principal.SecurityIdentifier[]
Parameter Sets: SecurityIdentifier
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. String, system. Security. Principal. SecurityIdentifier

Du kan skicka vidare en sträng eller SID till denna cmdlet.

## UTDATA

### System. Management. Automation. SecurityAccountsManager. lokal användare []

Den här cmdleten returnerar lokala användar konton.

## ANTECKNINGAR

**PrincipalSource** -egenskapen för **lokal användare** -, **localgroup** -och **LocalPrincipal** -objekten beskriver objektets källa. De möjliga källorna är följande:

- Lokal
- Active Directory
- Azure Active Directory grupp
- Microsoft-konto

**PrincipalSource** stöds endast av Windows 10, windows Server 2016 och senare versioner av operativ systemet Windows. För tidigare versioner är egenskapen tom.

## RELATERADE LÄNKAR

[Disable-lokal användare](Disable-LocalUser.md)

[Aktivera – lokal användare](Enable-LocalUser.md)

[New-lokal användare](New-LocalUser.md)

[Remove-lokal användare](Remove-LocalUser.md)

[Byt namn – lokal användare](Rename-LocalUser.md)

[Set-lokal användare](Set-LocalUser.md)
