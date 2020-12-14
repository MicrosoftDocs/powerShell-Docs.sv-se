---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 10/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/convertto-securestring?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-SecureString
ms.openlocfilehash: 0f95f66bdd13fd57f71823f2d44a28a1323d0d15
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708737"
---
# ConvertTo-SecureString

## SAMMANFATTNING
Konverterar oformaterad text eller krypterade strängar för att skydda strängar.

## SYNTAX

### Säker (standard)

```
ConvertTo-SecureString [-String] <String> [[-SecureKey] <SecureString>] [<CommonParameters>]
```

### PlainText

```
ConvertTo-SecureString [-String] <String> [-AsPlainText] [-Force] [<CommonParameters>]
```

### Öppna

```
ConvertTo-SecureString [-String] <String> [-Key <Byte[]>] [<CommonParameters>]
```

## BESKRIVNING

`ConvertTo-SecureString`Cmdleten konverterar krypterade standard strängar till säkra strängar. Den kan också konvertera oformaterad text för att skydda strängar. Den används med `ConvertFrom-SecureString` och `Read-Host` . Den säkra sträng som skapas av cmdleten kan användas med cmdletar eller funktioner som kräver en parameter av typen **SecureString**. Den säkra strängen kan konverteras tillbaka till en krypterad standard sträng med hjälp av `ConvertFrom-SecureString` cmdleten. Detta gör att det kan lagras i en fil för senare användning.

Om standard strängen som konverterades har krypterats med `ConvertFrom-SecureString` en angiven nyckel måste samma nyckel anges som värde för parametern **Key** eller parametern **SecureKey** för `ConvertTo-SecureString` cmdleten.

> [!NOTE]
> Observera att innehållet i en SecureString inte krypteras på andra datorer än Windows-datorer per [dotNet](/dotnet/api/system.security.securestring#remarks).

## EXEMPEL

### Exempel 1: konvertera en säker sträng till en krypterad sträng

Det här exemplet visar hur du skapar en säker sträng från användarindata, konverterar den säkra strängen till en krypterad standard sträng och sedan konverterar den krypterade standard strängen tillbaka till en säker sträng.

```powershell
PS C:\> $Secure = Read-Host -AsSecureString
PS C:\> $Secure
System.Security.SecureString
PS C:\> $Encrypted = ConvertFrom-SecureString -SecureString $Secure
PS C:\> $Encrypted
01000000d08c9ddf0115d1118c7a00c04fc297eb010000001a114d45b8dd3f4aa11ad7c0abdae98000000000
02000000000003660000a8000000100000005df63cea84bfb7d70bd6842e7efa79820000000004800000a000
000010000000f10cd0f4a99a8d5814d94e0687d7430b100000008bf11f1960158405b2779613e9352c6d1400
0000e6b7bf46a9d485ff211b9b2a2df3bd6eb67aae41
PS C:\> $Secure2 = ConvertTo-SecureString -String $Encrypted
PS C:\> $Secure2
System.Security.SecureString
```

Det första kommandot använder **AsSecureString** -parametern för `Read-Host` cmdleten för att skapa en säker sträng. När du har angett kommandot konverteras alla tecken som du skriver till en säker sträng och sparas sedan i `$Secure` variabeln.

Det andra kommandot visar innehållet i `$Secure` variabeln. Eftersom `$Secure` variabeln innehåller en säker sträng visar PowerShell endast **system. Security. SecureString** -typen.

Det tredje kommandot använder `ConvertFrom-SecureString` cmdleten för att konvertera den säkra strängen i `$Secure` variabeln till en krypterad standard sträng. Resultatet sparas i `$Encrypted` variabeln.

Det fjärde kommandot visar den krypterade strängen i värdet för `$Encrypted` variabeln.

Det femte kommandot använder `ConvertTo-SecureString` cmdleten för att konvertera den krypterade standard strängen i `$Encrypted` variabeln tillbaka till en säker sträng. Resultatet sparas i `$Secure2` variabeln.
Det sjätte kommandot visar värdet för `$Secure2` variabeln. Typen SecureString anger att kommandot lyckades.

### Exempel 2: skapa en säker sträng från en krypterad sträng i en fil

Det här exemplet visar hur du skapar en säker sträng från en krypterad standard sträng som sparas i en fil.

```powershell
$Secure = Read-Host -AsSecureString
$Encrypted = ConvertFrom-SecureString -SecureString $Secure -Key (1..16)
$Encrypted | Set-Content Encrypted.txt
$Secure2 = Get-Content Encrypted.txt | ConvertTo-SecureString -Key (1..16)
```

Det första kommandot använder **AsSecureString** -parametern för `Read-Host` cmdleten för att skapa en säker sträng. När du har angett kommandot konverteras alla tecken som du skriver till en säker sträng och sparas sedan i `$Secure` variabeln.

Det andra kommandot använder `ConvertFrom-SecureString` cmdleten för att konvertera den säkra strängen i `$Secure` variabeln till en krypterad standard sträng med hjälp av den angivna nyckeln. Innehållet sparas i `$Encrypted` variabeln.

Det tredje kommandot använder en pipeline-operator ( `|` ) för att skicka värdet för `$Encrypted` variabeln till `Set-Content` cmdleten, vilket sparar värdet i Encrypted.txt-filen.

Det fjärde kommandot använder `Get-Content` cmdleten för att hämta den krypterade standard strängen i Encrypted.txt-filen. Kommandot använder en pipeline-operator för att skicka den krypterade strängen till `ConvertTo-SecureString` cmdleten, vilket konverterar den till en säker sträng med hjälp av den angivna nyckeln.
Resultaten sparas i `$Secure2` variabeln.

### Exempel 3: konvertera en oformaterad text sträng till en säker sträng

Det här kommandot konverterar den oformaterade text strängen `P@ssW0rD!` till en säker sträng och lagrar resultatet i `$Secure_String_Pwd` variabeln. Om du vill använda parametern **Disklar text** måste även **Force** -parametern ingå i kommandot.

```powershell
$Secure_String_Pwd = ConvertTo-SecureString "P@ssW0rD!" -AsPlainText -Force
```

> [!CAUTION]
> Undvik att använda oformaterade text strängar i skript eller på kommando raden. Den oformaterade texten kan visas i händelse loggar och kommando historik loggar.

## PARAMETRAR

### -Klar text

Anger en oformaterad text sträng som ska konverteras till en säker sträng. De säkra sträng-cmdletarna skyddar konfidentiell text. Texten krypteras för sekretess och tas bort från dator minnet när den har använts. Om du använder den här parametern för att ange oformaterad text som inmatade kan systemet inte skydda dessa inmatade på det här sättet. Om du vill använda den här parametern måste du även ange **Force** -parametern.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PlainText
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Bekräftar att du förstår konsekvenserna av att använda parametern **Disklar text** och fortfarande vill använda den.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PlainText
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Nyckel

Anger den krypterings nyckel som används för att konvertera den ursprungliga säkra strängen till den krypterade standard strängen. Giltiga nyckel längder är 16, 24 och 32 byte.

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

Anger den krypterings nyckel som används för att konvertera den ursprungliga säkra strängen till den krypterade standard strängen. Nyckeln måste anges i formatet för en säker sträng. Den säkra strängen kommer att konverteras till en byte mat ris som ska användas som nyckel. Giltiga längder för säkra nycklar är 8, 12 och 16 kod punkter.

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

### – Sträng

Anger den sträng som ska konverteras till en säker sträng.

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

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. String

Du kan skicka vidare en krypterad standard sträng till `ConvertTo-SecureString` .

## UTDATA

### System. Security. SecureString

`ConvertTo-SecureString` Returnerar ett **SecureString** -objekt.

## ANTECKNINGAR

Vissa tecken, till exempel uttrycks symboler, motsvarar flera kod punkter i den sträng som innehåller dem. Undvik att använda dessa tecken eftersom de kan orsaka problem och fel som är felförstå när de används i ett lösen ord.

## RELATERADE LÄNKAR

[ConvertFrom – SecureString](ConvertFrom-SecureString.md)

[Read-Host](../Microsoft.PowerShell.Utility/Read-Host.md)
