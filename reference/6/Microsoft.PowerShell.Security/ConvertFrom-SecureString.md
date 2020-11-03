---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 04/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/convertfrom-securestring?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-SecureString
ms.openlocfilehash: 8a151da1b60b1956e580f9a0393d4eb137ef3447
ms.sourcegitcommit: b0488ca6557501184f20c8343b0ed5147b09e3fe
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/09/2020
ms.locfileid: "93268010"
---
# ConvertFrom-SecureString

## SAMMANFATTNING
Konverterar en säker sträng till en krypterad standard sträng.

## SYNTAX

### Säker (standard)

```
ConvertFrom-SecureString [-SecureString] <SecureString> [[-SecureKey] <SecureString>] [<CommonParameters>]
```

### Öppna

```
ConvertFrom-SecureString [-SecureString] <SecureString> [-Key <Byte[]>] [<CommonParameters>]
```

## BESKRIVNING

**ConvertFrom-SecureString-** cmdlet: en konverterar en säker sträng ( **system. Security. SecureString** ) till en krypterad standard sträng ( **system. String** ). Till skillnad från en säker sträng kan en krypterad standard sträng sparas i en fil för senare användning. Den krypterade standard strängen kan konverteras tillbaka till dess skyddade sträng format med hjälp av `ConvertTo-SecureString` cmdleten.

Om en krypterings nyckel anges med hjälp av **nyckel** -eller **SecureKey** -parametrarna används krypteringsalgoritmen Advanced Encryption Standard (AES). Den angivna nyckeln måste ha en längd på 128, 192 eller 256 bitar eftersom de är de nyckel längder som stöds av AES-krypteringsalgoritmen. Om ingen nyckel anges används Windows Data Protection API (DPAPI) för att kryptera standard sträng representationen.

> [!NOTE]
> Observera att innehållet i en SecureString inte krypteras på andra datorer än Windows-datorer per [dotNet](/dotnet/api/system.security.securestring?view=netcore-2.1#remarks).

## EXEMPEL

### Exempel 1: skapa en säker sträng

```powershell
$SecureString = Read-Host -AsSecureString
```

Det här kommandot skapar en säker sträng från tecken som du skriver i kommando tolken. När du har angett kommandot skriver du strängen som du vill lagra som en säker sträng. En asterisk ( `*` ) visas som representerar varje specialtecken som du skriver.

### Exempel 2: konvertera en säker sträng till en krypterad standard sträng

```powershell
$StandardString = ConvertFrom-SecureString $SecureString
```

Det här kommandot konverterar den säkra strängen i `$SecureString` variabeln till en krypterad standard sträng. Den resulterande krypterade standard strängen lagras i `$StandardString` variabeln.

### Exempel 3: konvertera en säker sträng till en krypterad standard sträng med en 192-bitars nyckel

```powershell
$Key = (3,4,2,3,56,34,254,222,1,1,2,23,42,54,33,233,1,34,2,7,6,5,35,43)
$StandardString = ConvertFrom-SecureString $SecureString -Key $Key
```

Dessa kommandon använder algoritmen Advanced Encryption Standard (AES) för att konvertera den säkra sträng som lagras i `$SecureString` variabeln till en krypterad standard sträng med en 192-bitars nyckel. Den resulterande krypterade standard strängen lagras i `$StandardString` variabeln.

Det första kommandot lagrar en nyckel i `$Key` variabeln. Nyckeln är en matris med 24 decimaler som var och en måste vara mindre än 256 för att få plats i en ensignd byte.

Eftersom varje decimal tal representerar en enda byte (8 bitar) har nyckeln 24 siffror för totalt 192 bitar (8 x 24). Detta är en giltig nyckel längd för AES-algoritmen.

Det andra kommandot använder nyckeln i `$Key` variabeln för att konvertera den säkra strängen till en krypterad standard sträng.

## PARAMETRAR

### -Nyckel

Anger krypterings nyckeln som en byte mat ris.

```yaml
Type: System.Byte[]
Parameter Sets: Open
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SecureKey

Anger krypterings nyckeln som en säker sträng. Värdet för den säkra strängen konverteras till en byte mat ris innan det används som nyckel.

```yaml
Type: System.Security.SecureString
Parameter Sets: Secure
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – SecureString

Anger den säkra sträng som ska konverteras till en krypterad standard sträng.

```yaml
Type: System.Security.SecureString
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet stöder de gemensamma parametrarna:,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` , och `-WarningVariable` .
Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. Security. SecureString

Du kan skicka ett **SecureString** -objekt till ConvertFrom-SecureString.

## UTDATA

### System. String

ConvertFrom-SecureString returnerar ett standard sträng objekt.

## ANTECKNINGAR

- Om du vill skapa en säker sträng från tecken som skrivs i kommando tolken använder du parametern **AsSecureString** för `Read-Host` cmdleten.
- När du använder **Key** -eller **SecureKey** -parametrarna för att ange en nyckel måste nyckel längden vara korrekt. Till exempel kan en nyckel på 128 bitar anges som en byte-matris med 16 decimal siffror.
  På samma sätt motsvarar 192-bitars-och 256-bitars nycklar byte mat ris med 24 respektive 32 decimal siffror.
- Vissa tecken, till exempel uttrycks symboler, motsvarar flera kod punkter i den sträng som innehåller dem. Undvik att använda dessa tecken eftersom de kan orsaka problem och fel som är felförstå när de används i ett lösen ord.

## RELATERADE LÄNKAR

[ConvertTo – SecureString](ConvertTo-SecureString.md)

[Read-Host](../Microsoft.PowerShell.Utility/Read-Host.md)
