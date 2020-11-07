---
external help file: Microsoft.PowerShell.Utility-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-sddlstring?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-SddlString
ms.openlocfilehash: 9c864ec46af9584f36eef3f3ba879cf314e0ca1c
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94347320"
---
# ConvertFrom-SddlString

## SAMMANFATTNING
Konverterar en SDDL-sträng till ett anpassat objekt.

## SYNTAX

### Alla

```
ConvertFrom-SddlString [-Sddl] <String> [-Type <AccessRightTypeNames>] [<CommonParameters>]
```

## BESKRIVNING

`ConvertFrom-SddlString`Cmdleten konverterar en språk sträng för en säkerhets beskrivnings definition till ett anpassat **PSCustomObject** -objekt med följande egenskaper: Owner, Group, DiscretionaryAcl, SystemAcl och RawDescriptor.

Egenskaperna Owner, Group, DiscretionaryAcl och SystemAcl innehåller en läsbar text representation av de åtkomst rättigheter som anges i en SDDL-sträng.

Denna cmdlet introducerades i PowerShell 5,0.

## EXEMPEL

### Exempel 1: konvertera SDDL för Access-behörigheter till en PSCustomObject

```powershell
$acl = Get-Acl -Path C:\Windows
ConvertFrom-SddlString -Sddl $acl.Sddl
```

Det första kommandot använder `Get-Acl` cmdleten för att hämta säkerhets beskrivningen för mappen C:\Windows och sparar den i variabeln.

Det andra kommandot använder `ConvertFrom-SddlString` cmdleten för att hämta text representationen av SDDL-strängen, som finns i SDDL-egenskapen för objektet som representerar säkerhets beskrivningen.

### Exempel 2: konvertera SDDL för register åtkomst behörigheter till en PSCustomObject

```powershell
$acl = Get-Acl HKLM:\SOFTWARE\Microsoft\
ConvertFrom-SddlString -Sddl $acl.Sddl -Type RegistryRights
```

Det första kommandot använder `Get-Acl` cmdleten för att hämta säkerhets beskrivningen för HKLM: \ SOFTWARE\Microsoft\-nyckeln och sparar den i variabeln.

Det andra kommandot använder `ConvertFrom-SddlString` cmdleten för att hämta text representationen av SDDL-strängen, som finns i SDDL-egenskapen för objektet som representerar säkerhets beskrivningen.

`-Type`Parametern används för att ange att SDDL-strängen representerar en säkerhets beskrivning för registret.

### Exempel 3: konvertera SDDL-behörighet för register åtkomst till en PSCustomObject med hjälp av ConvertFrom-SddlString med och utan `-Type` parametern

```powershell
$acl = Get-Acl -Path HKLM:\SOFTWARE\Microsoft\

ConvertFrom-SddlString -Sddl $acl.Sddl | Foreach-Object {$_.DiscretionaryAcl[0]}

BUILTIN\Administrators: AccessAllowed (ChangePermissions, CreateDirectories, Delete, ExecuteKey, FullControl, GenericExecute, GenericWrite, ListDirectory, ReadExtendedAttributes, ReadPermissions, TakeOwnership, Traverse, WriteData, WriteExtendedAttributes, WriteKey)

ConvertFrom-SddlString -Sddl $acl.Sddl -Type RegistryRights | Foreach-Object {$_.DiscretionaryAcl[0]}

BUILTIN\Administrators: AccessAllowed (ChangePermissions, CreateLink, CreateSubKey, Delete, EnumerateSubKeys, ExecuteKey, FullControl, GenericExecute, GenericWrite, Notify, QueryValues, ReadPermissions, SetValue, TakeOwnership, WriteKey)
```

Det första kommandot använder `Get-Acl` cmdleten för att hämta säkerhets beskrivningen för HKLM: \ SOFTWARE\Microsoft\-nyckeln och sparar den i variabeln.

Det andra kommandot använder `ConvertFrom-SddlString` cmdleten för att hämta text representationen av SDDL-strängen, som finns i SDDL-egenskapen för objektet som representerar säkerhets beskrivningen.

Den använder inte `-Type` parametern, så åtkomst rättigheterna som visas gäller för fil system.

Det tredje kommandot använder `ConvertFrom-SddlString` cmdleten med `-Type` parametern, så åtkomst rättigheterna som returneras är för registret.

## PARAMETRAR

### -SDDL

Anger den sträng som representerar säkerhets beskrivningen i SDDL-syntax.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Typ

Anger vilken typ av rättigheter som SDDL-sträng representerar.

De acceptabla värdena för den här parametern är:

- FileSystemRights
- RegistryRights
- ActiveDirectoryRights
- MutexRights
- SemaphoreRights
- CryptoKeyRights
- EventWaitHandleRights

Som standard använder cmdlet fil system rättigheter.

CryptoKeyRights och ActiveDirectoryRights stöds inte i PowerShell Core.

```yaml
Type: Microsoft.PowerShell.Commands.ConvertFromSddlStringCommand+AccessRightTypeNames
Parameter Sets: (All)
Aliases:
Accepted values: FileSystemRights, RegistryRights, ActiveDirectoryRights, MutexRights, SemaphoreRights, CryptoKeyRights, EventWaitHandleRights

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. String

Du kan skicka vidare en SDDL-sträng till `ConvertFrom-SddlString` .

## UTDATA

## ANTECKNINGAR

Den här cmdleten är endast tillgänglig på Windows-plattformar.

## RELATERADE LÄNKAR

[Språk för säkerhets beskrivnings definition](/windows/win32/secauthz/security-descriptor-definition-language)
