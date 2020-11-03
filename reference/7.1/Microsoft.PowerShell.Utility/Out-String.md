---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/29/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/out-string?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-String
ms.openlocfilehash: 16dc25e3468eaf3126b3286cfd71bfea9627c015
ms.sourcegitcommit: c8d1ffeab215e74e87ea1b0af8cd606c1a6a80ab
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/29/2020
ms.locfileid: "93269619"
---
# Out-String

## SAMMANFATTNING
Matar in indata-objekt som en sträng.

## SYNTAX

### NoNewLineFormatting (standard)

```
Out-String [-Width <Int32>] [-NoNewline] [-InputObject <PSObject>] [<CommonParameters>]
```

### StreamFormatting

```
Out-String [-Stream] [-Width <Int32>] [-InputObject <PSObject>] [<CommonParameters>]
```

## BESKRIVNING

`Out-String`Cmdleten konverterar inmatade objekt till strängar. Som standard `Out-String` ackumuleras strängarna och returneras som en enskild sträng, men du kan använda **Stream** -parametern för att dirigera `Out-String` för att returnera en rad i taget eller skapa en sträng mat ris. Med den här cmdleten kan du söka efter och manipulera sträng utdata som i traditionella skal när objekt manipulation är mindre användbart.

## EXEMPEL

### Exempel 1: hämta den aktuella kulturen och konvertera data till strängar

Det här exemplet hämtar de nationella inställningarna för den aktuella användaren och konverterar objekt data till strängar.

```powershell
$C = Get-Culture | Select-Object -Property *
Out-String -InputObject $C -Width 100
```

```Output
Parent                         : en
LCID                           : 1033
KeyboardLayoutId               : 1033
Name                           : en-US
IetfLanguageTag                : en-US
DisplayName                    : English (United States)
NativeName                     : English (United States)
EnglishName                    : English (United States)
TwoLetterISOLanguageName       : en
ThreeLetterISOLanguageName     : eng
ThreeLetterWindowsLanguageName : ENU
CompareInfo                    : CompareInfo - en-US
TextInfo                       : TextInfo - en-US
IsNeutralCulture               : False
CultureTypes                   : SpecificCultures, InstalledWin32Cultures, FrameworkCultures
NumberFormat                   : System.Globalization.NumberFormatInfo
DateTimeFormat                 : System.Globalization.DateTimeFormatInfo
Calendar                       : System.Globalization.GregorianCalendar
OptionalCalendars              : {System.Globalization.GregorianCalendar,
                                 System.Globalization.GregorianCalendar}
UseUserOverride                : True
IsReadOnly                     : False
```

`$C`Variabeln lagrar en **Selected.System. Globaliserings-. CultureInfo** -objekt. Objektet är resultatet av `Get-Culture` att skicka utdata nedåt i pipeline till `Select-Object` . **Egenskaps** parametern använder en asterisk ( `*` ) som jokertecken för att ange alla egenskaper som finns i objektet.

`Out-String` använder parametern **InputObject** för att ange det **CultureInfo** -objekt som lagras i `$C` variabeln. Objekten i `$C` konverteras till en sträng.

> [!NOTE]
> Om du vill visa `Out-String` matrisen lagrar du utdata till en variabel och använder ett mat ris index för att Visa elementen. Mer information om mat ris index finns [about_Arrays](../microsoft.powershell.core/about/about_arrays.md).
>
> `$str = Out-String -InputObject $C -Width 100`

### Exempel 2: arbeta med objekt

Det här exemplet visar skillnaden mellan att arbeta med objekt och att arbeta med strängar. Kommandot visar ett alias som innehåller texten **GCM** , alias för `Get-Command` .

```powershell
Get-Alias | Out-String -Stream | Select-String -Pattern "gcm"
```

```Output
Alias           gcm -> Get-Command
```

`Get-Alias` hämtar objekten **system. Management. Automation. AliasInfo** , ett för varje alias och skickar objekten nedåt i pipelinen. `Out-String` använder **Stream** -parametern för att konvertera varje objekt till en sträng, och sammanfogar alla objekt till en enda sträng. **System. String** -objekten skickas ned pipelinen och `Select-String` använder **mönster** parametern för att hitta matchningar för texten **GCM**.

> [!NOTE]
> Om du utelämnar parametern **Stream** visar kommandot alla alias eftersom `Select-String` söker efter texten **GCM** i den enskilda strängen som `Out-String` returnerar.

### Exempel 3: Använd parametern width för att förhindra trunkering.

Medan de flesta utdata från `Out-String` radbryts till nästa rad finns det scenarier där utdata trunkeras av formaterings systemet innan de skickas till `Out-String` . Du kan undvika trunkering med parametern **width** .

```powershell
PS> @{TestKey = ('x' * 200)} | Out-String
Name                           Value
----                           -----
TestKey                        xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx...

PS> @{TestKey = ('x' * 200)} | Out-String -Width 250

Name                           Value
----                           -----
TestKey                        xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

## PARAMETRAR

### – InputObject

Anger de objekt som ska skrivas till en sträng. Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### – NoNewline

Tar bort alla newlines från utdata som genereras av PowerShell-formateraren. Newlines som är en del av String-objekten bevaras.

Den här parametern introducerades i PowerShell 6,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NoNewLineFormatting
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Stream

Anger att cmdleten skickar en separat sträng för varje rad i ett indatamängds objekt. Som standard samlas strängarna för varje objekt in och skickas som en enskild sträng.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: StreamFormatting
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Bredd

Anger antalet tecken i varje rad utdata. Eventuella ytterligare tecken radbryts till nästa rad eller trunkeras beroende på vilken cmdlet som används. Parametern **width** gäller bara för objekt som formateras. Om du utelämnar den här parametern bestäms bredden av egenskaperna för värd programmet. I Terminal-fönster (konsol) används den aktuella fönster bredden som standardvärdet. PowerShell-konsolens fönster är standard bredden på 80 tecken vid installation.

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

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. Management. Automation. PSObject

Du kan skicka objekt nedåt i pipelinen till `Out-String` .

## UTDATA

### System. String

`Out-String` Returnerar den sträng som skapas från det inmatade objektet.

## ANTECKNINGAR

De cmdletar som innehåller `Out` verbet formaterar inte objekt. `Out`Cmdletarna skickar objekt till Formatter för det angivna visnings målet.

## RELATERADE LÄNKAR

[about_Formatting](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md)

[Ut-standard](../Microsoft.PowerShell.Core/Out-Default.md)

[Ut-fil](Out-File.md)

[Ut-värd](../Microsoft.PowerShell.Core/Out-Host.md)

[Ut-null](../Microsoft.PowerShell.Core/Out-Null.md)

[Out-GridView](Out-GridView.md)

[Out-Printer](Out-Printer.md)
