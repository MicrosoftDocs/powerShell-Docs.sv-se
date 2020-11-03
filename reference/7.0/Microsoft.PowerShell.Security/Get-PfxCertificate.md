---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-pfxcertificate?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PfxCertificate
ms.openlocfilehash: 1642f30579e71835233431438172ffc1000c4203
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93262809"
---
# Get-PfxCertificate

## SAMMANFATTNING
Hämtar information om PFX-certifikatfiler på datorn.

## SYNTAX

### ByPath (standard)

```
Get-PfxCertificate [-FilePath] <String[]> [-Password <SecureString>] [-NoPromptForPassword]
 [<CommonParameters>]
```

### ByLiteralPath

```
Get-PfxCertificate -LiteralPath <String[]> [-Password <SecureString>] [-NoPromptForPassword]
 [<CommonParameters>]
```

## BESKRIVNING

`Get-PfxCertificate`Cmdlet: en hämtar ett objekt som representerar varje angiven PFX-certifikatfil.
En PFX-fil innehåller både certifikatet och en privat nyckel.

## EXEMPEL

### Exempel 1: Hämta ett PFX-certifikat

```powershell
Get-PfxCertificate -FilePath "C:\windows\system32\Test.pfx"
```

```output
Password: ******
Signer Certificate:      David Chew (Self Certificate)
Time Certificate:
Time Stamp:
Path:                    C:\windows\system32\zap.pfx
```

Det här kommandot hämtar information om certifikat filen test. pfx i systemet.

### Exempel 2: Hämta ett PFX-certifikat från en fjärran sluten dator

```powershell
Invoke-Command -ComputerName "Server01" -ScriptBlock {Get-PfxCertificate -FilePath "C:\Text\TestNoPassword.pfx"} -Authentication CredSSP
```

Det här kommandot hämtar en PFX-certifikatfil från fjärrdatorn Server01. Den använder `Invoke-Command` för att köra ett `Get-PfxCertificate` kommando via fjärr anslutning.

När PFX-certifikatarkivet inte är lösenordsskyddad måste värdet för parametern **Authentication** `Invoke-Command` vara CredSSP.

## PARAMETRAR

### -Sökväg

Anger den fullständiga sökvägen till PFX-filen för den skyddade filen. Om du anger ett värde för den här parametern behöver du inte skriva `-FilePath` på kommando raden.

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -LiteralPath

Den fullständiga sökvägen till PFX-filen för den skyddade filen. Till skillnad från **sökväg** , används värdet för parametern **LiteralPath** exakt som det har angetts. Inga tecken tolkas som jokertecken. Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken. Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -NoPromptForPassword

Förhindrar att du uppmanas att ange ett lösen ord.

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

### -Password

Anger ett lösen ord som krävs för att komma åt en `.pfx` certifikat fil.

Den här parametern introducerades i PowerShell 6,1.

> [!NOTE]
> Mer information om **SecureString** -data skydd finns i [hur säker är SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).

```yaml
Type: System.Security.SecureString
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

### System. String

Du kan skicka vidare en sträng som innehåller en fil Sök väg till `Get-PfxCertificate` .

## UTDATA

### System. Security. Cryptography. X509Certificates. X509Certificate2

`Get-PfxCertificate` Returnerar ett objekt för varje certifikat som det får.

## ANTECKNINGAR

När du använder `Invoke-Command` cmdleten för att köra ett `Get-PfxCertificate` kommando via fjärr anslutning och PFX-certifikatarkivet inte är lösenordsskyddat, måste värdet för **autentiseringsmetoden** för parametern `Invoke-Command` vara CredSSP.

## RELATERADE LÄNKAR

[Get-AuthenticodeSignature](Get-AuthenticodeSignature.md)

[Set-AuthenticodeSignature](Set-AuthenticodeSignature.md)
