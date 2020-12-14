---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/21/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/out-file?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-File
ms.openlocfilehash: e3a066957ab1e6935049003f8ccf55aee8bb7c94
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709072"
---
# Out-File

## SAMMANFATTNING
Skickar utdata till en fil.

## SYNTAX

### ByPath (standard)

```
Out-File [-FilePath] <string> [[-Encoding] <Encoding>] [-Append] [-Force] [-NoClobber]
 [-Width <int>] [-NoNewline] [-InputObject <psobject>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByLiteralPath

```
Out-File [[-Encoding] <Encoding>] -LiteralPath <string> [-Append] [-Force] [-NoClobber]
 [-Width <int>] [-NoNewline] [-InputObject <psobject>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING

`Out-File`Cmdleten skickar utdata till en fil. Den använder implicit PowerShell: s format system för att skriva till filen. Filen får samma visnings representation som i terminalen. Det innebär att utmatningen kanske inte är idealisk för programmatisk bearbetning om inte alla indata är strängar.
När du behöver ange parametrar för utdata använder du `Out-File` istället för omdirigerings operatorn ( `>` ). Mer information om omdirigering finns i [about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md).

## EXEMPEL

### Exempel 1: skicka utdata och skapa en fil

Det här exemplet visar hur du skickar en lista över den lokala datorns processer till en fil. Om filen inte finns `Out-File` skapas filen på den angivna sökvägen.

```powershell
Get-Process | Out-File -FilePath .\Process.txt
Get-Content -Path .\Process.txt
```

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     29    22.39      35.40      10.98   42764   9 Application
     53    99.04     113.96       0.00   32664   0 CcmExec
     27    96.62     112.43     113.00   17720   9 Code
```

`Get-Process`Cmdleten hämtar listan över processer som körs på den lokala datorn. **Process** objekt skickas ned pipelinen till `Out-File` cmdleten. `Out-File` använder parametern **sökväg** och skapar en fil i den aktuella katalogen med namnet **Process.txt**. `Get-Content`Kommandot hämtar innehåll från filen och visar det i PowerShell-konsolen.

### Exempel 2: förhindra att en befintlig fil skrivs över

Det här exemplet förhindrar att en befintlig fil skrivs över. Som standard `Out-File` skriver över befintliga filer.

```powershell
Get-Process | Out-File -FilePath .\Process.txt -NoClobber
```

```Output
Out-File : The file 'C:\Test\Process.txt' already exists.
At line:1 char:15
+ Get-Process | Out-File -FilePath .\Process.txt -NoClobber
+               ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
```

`Get-Process`Cmdleten hämtar listan över processer som körs på den lokala datorn. **Process** objekt skickas ned pipelinen till `Out-File` cmdleten. `Out-File` använder parametern **sökväg** och försöker skriva till en fil i den aktuella katalogen med namnet **Process.txt**. Parametern **NoClobber** förhindrar att filen skrivs över och visar ett meddelande om att filen redan finns.

### Exempel 3: skicka utdata till en fil i ASCII-format

Det här exemplet visar hur du kodar utdata med en speciell kodnings typ.

```powershell
$Procs = Get-Process
Out-File -FilePath .\Process.txt -InputObject $Procs -Encoding ASCII -Width 50
```

`Get-Process`Cmdleten hämtar listan över processer som körs på den lokala datorn. **Process** objekt lagras i variabeln `$Procs` . `Out-File` använder parametern **sökväg** och skapar en fil i den aktuella katalogen med namnet **Process.txt**. **InputObject** -parametern överför process objekt `$Procs` till filen **Process.txt**. **Encoding** -parametern konverterar utdata till **ASCII** -format. Parametern **width** begränsar varje rad i filen till 50 tecken så att vissa data kan trunkeras.

### Exempel 4: Använd en provider och skicka utdata till en fil

Det här exemplet visar hur du använder `Out-File` cmdleten när du inte befinner dig i en **fil för fil Systems** leverantör. Använd `Get-PSProvider` cmdleten för att Visa providers på den lokala datorn. Mer information finns i [about_Providers](../Microsoft.Powershell.Core/About/about_Providers.md).

```
PS> Set-Location -Path Alias:

PS> Get-Location

Path
----
Alias:\

PS> Get-ChildItem | Out-File -FilePath C:\TestDir\AliasNames.txt

PS> Get-Content -Path C:\TestDir\AliasNames.txt

CommandType     Name
-----------     ----
Alias           % -> ForEach-Object
Alias           ? -> Where-Object
Alias           ac -> Add-Content
Alias           cat -> Get-Content
```

`Set-Location`Kommandot använder parametern **Path** för att ange den aktuella platsen för register leverantören `Alias:` . `Get-Location`Cmdleten visar den fullständiga sökvägen för `Alias:` .
`Get-ChildItem` skickar objekt nedåt i pipeline till `Out-File` cmdleten. `Out-File` använder parametern **sökväg** för att ange den fullständiga sökvägen och fil namnet för utdata, **C:\TestDir\AliasNames.txt**. `Get-Content`Cmdleten använder parametern **Path** och visar filens innehåll i PowerShell-konsolen.

## PARAMETRAR

### -Lägg till

Lägger till utdata i slutet av en befintlig fil.

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

### -Encoding

Anger typ av kodning för mål filen. Standardvärdet är `utf8NoBOM`.

De acceptabla värdena för den här parametern är följande:

- `ascii`: Använder kodningen för ASCII-teckenuppsättningen (7 bitar).
- `bigendianunicode`: Kodar i UTF-16-format med big-endian byte-ordning.
- `bigendianutf32`: Kodar i UTF-32-format med big-endian-dataordningen.
- `oem`: Använder standard kodning för MS-DOS-och-konsol program.
- `unicode`: Kodar i UTF-16-format med lite-endian-dataordning.
- `utf7`: Kodar i UTF-7-format.
- `utf8`: Kodar i UTF-8-format.
- `utf8BOM`: Kodar i UTF-8-format med byte ordnings tecken (BOM)
- `utf8NoBOM`: Kodar i UTF-8-format utan byte ordnings tecken (BOM)
- `utf32`: Kodar i UTF-32-format.

Från och med PowerShell 6,2 tillåter **encoding** -parametern även numeriska ID: n för registrerade tecken tabeller (som `-Encoding 1251` ) eller sträng namn för registrerade tecken tabeller (som `-Encoding "windows-1251"` ). Mer information finns i .NET-dokumentationen för [encoding. codepage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).

> [!NOTE]
> **UTF-7** _ rekommenderas inte längre att använda. I PowerShell 7,1 skrivs en varning om du anger `utf7` för parametern _ *encoding**.

```yaml
Type: System.Text.Encoding
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, BigEndianUTF32, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: 1
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### -Sökväg

Anger sökvägen till utdatafilen.

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases: Path

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Åsidosätter det skrivskyddade attributet och skriver över en befintlig skrivskyddad fil. **Force** -parametern åsidosätter inte säkerhets begränsningar.

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

### – InputObject

Anger de objekt som ska skrivas till filen. Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten.

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

### -LiteralPath

Anger sökvägen till utdatafilen. Parametern **LiteralPath** används exakt som den har angetts.
Jokertecken accepteras inte. Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken. Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser. Mer information finns i [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -NoClobber

**NoClobber** förhindrar att en befintlig fil skrivs över och visar ett meddelande om att filen redan finns. Om en fil finns på den angivna sökvägen skrivs filen som standard `Out-File` utan varning.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NoOverwrite

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – NoNewline

Anger att innehållet som skrivs till filen inte slutar med ett rad matnings tecknet. Sträng representationerna av indata-objekten sammanfogas för att bilda utdata. Inga blank steg eller newlines infogas mellan utgående strängar. Ingen ny rad läggs till efter den sista utgående strängen.

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

### -Bredd

Anger antalet tecken i varje rad utdata. Eventuella ytterligare tecken trunkeras, inte omslutna. Om den här parametern inte används bestäms bredden av egenskaperna för värden. Standardvärdet för PowerShell-konsolen är 80 tecken.

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

### -Confirm

Uppmanar dig att bekräfta innan du kör cmdleten.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

Visar vad som skulle hända om cmdleten kördes. Cmdleten körs inte.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. Management. Automation. PSObject

Du kan skicka vidare alla objekt till `Out-File` .

## UTDATA

### Inga

`Out-File` genererar inga utdata.

## ANTECKNINGAR

Inmatnings objekt formateras automatiskt som de skulle vara i terminalen, men du kan använda en- `Format-*` cmdlet för att styra formateringen av utdata direkt till filen. Till exempel `Get-Date | Format-List | Out-File out.txt`

Använd pipelinen om du vill skicka ett PowerShell-kommandos utdata till `Out-File` cmdleten. Alternativt kan du lagra data i en variabel och använda parametern **InputObject** för att skicka data till `Out-File` cmdleten.

`Out-File` sparar data till en fil, men genererar inga utdata-objekt till pipelinen.

## RELATERADE LÄNKAR

[about_Providers](../Microsoft.Powershell.Core/About/about_Providers.md)

[about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)

[Ut-standard](../Microsoft.PowerShell.Core/Out-Default.md)

[Ut-värd](../Microsoft.PowerShell.Core/Out-Host.md)

[Ut-null](../Microsoft.PowerShell.Core/Out-Null.md)

[Out-sträng](Out-String.md)

[Tee – objekt](Tee-Object.md)

