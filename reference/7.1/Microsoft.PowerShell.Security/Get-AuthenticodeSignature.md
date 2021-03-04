---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 04/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-authenticodesignature?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-AuthenticodeSignature
ms.openlocfilehash: b1b470fb1dd23cd404b7f5fea4981b39f206ae87
ms.sourcegitcommit: 1dfd5554b70c7e8f4e3df19e29c384a9c0a4b227
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/03/2021
ms.locfileid: "101685334"
---
# Get-AuthenticodeSignature

## SAMMANFATTNING
Hämtar information om Authenticode-signaturen för en fil.

## SYNTAX

### ByPath (standard)

```
Get-AuthenticodeSignature [-FilePath] <String[]> [<CommonParameters>]
```

### ByLiteralPath

```
Get-AuthenticodeSignature -LiteralPath <String[]> [<CommonParameters>]
```

### ByContent

```
Get-AuthenticodeSignature -SourcePathOrExtension <String[]> -Content <Byte[]> [<CommonParameters>]
```

## BESKRIVNING

`Get-AuthenticodeSignature`Cmdleten hämtar information om Authenticode-signaturen för en fil eller ett fil innehåll som en byte mat ris.
Om filen är både inbäddad signerad och Windows Catalog signerad, används Windows Catalog-signaturen.
Om filen inte är signerad hämtas informationen, men fälten är tomma.

## EXEMPEL

### Exempel 1: Hämta Authenticode-signaturen för en fil

```powershell
Get-AuthenticodeSignature -FilePath "C:\Test\NewScript.ps1"
```

Det här kommandot hämtar information om Authenticode-signaturen i NewScript.ps1-filen. Parametern **sökväg** används för att ange filen.

### Exempel 2: Hämta Authenticode-signaturen för flera filer

```powershell
Get-AuthenticodeSignature test.ps1, test1.ps1, sign-file.ps1, makexml.ps1
```

Det här kommandot hämtar information om Authenticode-signaturen för de fyra filerna som anges på kommando raden. I det här exemplet utelämnas namnet på parametern **sökväg** , som är valfritt.

### Exempel 3: Hämta endast giltiga Authenticode-signaturer för flera filer

```powershell
Get-ChildItem $PSHOME\*.* | ForEach-object {Get-AuthenticodeSignature $_} | Where-Object {$_.status -eq "Valid"}
```

Detta kommando visar alla filer i `$PSHOME` katalogen som har en giltig Authenticode-signatur. Den `$PSHOME` automatiska variabeln innehåller sökvägen till PowerShell-katalogen för installationen.

Kommandot använder `Get-ChildItem` cmdleten för att hämta filerna i `$PSHOME` katalogen. Det använder ett mönster i *.* Om du vill utesluta kataloger (även om det också utesluter filer utan en punkt i fil namnet).

Kommandot använder en pipeline-operator ( `|` ) för att skicka filerna `$PSHOME` till `ForEach-Object` -cmdleten, där `Get-AuthenticodeSignature` anropas för varje fil.

Resultatet av `Get-AuthenticodeSignature` kommandot skickas till ett `Where-Object` kommando som bara väljer de signaturkrav som har statusen giltig.

### Exempel 4: Hämta Authenticode-signaturen för ett fil innehåll som anges som byte mat ris

```powershell
Get-AuthenticodeSignature -Content (Get-Content foo.ps1 -AsByteStream) -SourcePathorExtension ps1
```

Det här kommandot hämtar information om Authenticode-signaturen för innehållet i en fil. I det här exemplet anges fil namns tillägget tillsammans med filens innehåll.

## PARAMETRAR

### – Innehåll

Innehållet i en fil som en byte-matris för vilken Authenticode-signaturen hämtas. Den här parametern måste användas med parametern **SourcePathOrExtension** . Filens innehåll måste vara i Unicode-format (UTF-16LE).

```yaml
Type: System.Byte[]
Parameter Sets: ByContent
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Sökväg

Anger sökvägen till filen som ska granskas. Jokertecken tillåts, men de måste leda till en enda fil. Du behöver inte skriva in **sökväg** på kommando raden när du anger ett värde för den här parametern.

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -LiteralPath

Anger sökvägen till den fil som ska undersökas. Till skillnad från **sökväg**, används värdet för parametern **LiteralPath** exakt som det har angetts. Inga tecken tolkas som jokertecken. Om sökvägen innehåller ett escape-tecken omger du det med enkla citat tecken. Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-tecken.

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

### -SourcePathOrExtension

Sökväg till filen eller filtypen för det innehåll som Authenticode-signaturen hämtas för. Den här parametern används med **innehåll** där fil innehåll skickas som en byte mat ris.

```yaml
Type: System.String[]
Parameter Sets: ByContent
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## INDATA

### System. String

Du kan skicka vidare en sträng som innehåller en fil Sök väg till `Get-AuthenticodeSignature` .

## UTDATA

### System. Management. Automation. signatur

`Get-AuthenticodeSignature` Returnerar ett signatur objekt för varje signatur som det får.

## ANTECKNINGAR

Den här cmdleten är endast tillgänglig på Windows-plattformar.

Information om Authenticode-signaturer i PowerShell finns [about_Signing](../Microsoft.PowerShell.Core/About/about_Signing.md).

## RELATERADE LÄNKAR

[Get-ExecutionPolicy](Get-ExecutionPolicy.md)

[Set-AuthenticodeSignature](Set-AuthenticodeSignature.md)

[Set-ExecutionPolicy](Set-ExecutionPolicy.md)

[about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)

[about_Signing](../Microsoft.PowerShell.Core/About/about_Signing.md)
