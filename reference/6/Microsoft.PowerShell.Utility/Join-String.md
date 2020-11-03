---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Module Name: Microsoft.PowerShell.Utility
ms.date: 12/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/join-string?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Join-String
ms.openlocfilehash: e1ec8933f70fab666baa4ce865297deeec37fff9
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265755"
---
# Join-String

## SAMMANFATTNING
Kombinerar objekt från pipelinen till en enda sträng.

## SYNTAX

### Standard (standard)

```
Join-String [[-Property] <PSPropertyExpression>] [[-Separator] <String>] [-OutputPrefix <String>]
 [-OutputSuffix <String>] [-UseCulture] [-InputObject <PSObject[]>] [<CommonParameters>]
```

### SingleQuote

```
Join-String [[-Property] <PSPropertyExpression>] [[-Separator] <String>] [-OutputPrefix <String>]
 [-OutputSuffix <String>] [-SingleQuote] [-UseCulture] [-InputObject <PSObject[]>]
 [<CommonParameters>]
```

### DoubleQuote

```
Join-String [[-Property] <PSPropertyExpression>] [[-Separator] <String>] [-OutputPrefix <String>]
 [-OutputSuffix <String>] [-DoubleQuote] [-UseCulture] [-InputObject <PSObject[]>]
 [<CommonParameters>]
```

### Format

```
Join-String [[-Property] <PSPropertyExpression>] [[-Separator] <String>] [-OutputPrefix <String>]
 [-OutputSuffix <String>] [-FormatString <String>] [-UseCulture] [-InputObject <PSObject[]>]
 [<CommonParameters>]
```

## BESKRIVNING

`Join-String`Cmdleten ansluter till eller kombinerar text från pipeline-objekt till en enda sträng.

Om inga parametrar anges, konverteras pipeliniska objekt till en sträng och kopplas till standard avgränsaren `$OFS` .

Genom att ange ett egenskaps namn konverteras egenskapens värde till en sträng och sammanfogas till en sträng.

I stället för ett egenskaps namn kan ett skript block användas. Skript blockets resultat konverteras till en sträng innan det kopplas till resultatet. Den kan antingen kombinera texten i ett objekts egenskap eller resultatet av det objekt som konverterats till en sträng.

Denna cmdlet introducerades i PowerShell 6,2.

## EXEMPEL

### Exempel 1: Anslut till katalog namn

<!-- markdownlint-disable MD038 -->
Det här exemplet ansluter till katalog namn, omsluter utdata i dubbla citat tecken och avgränsar katalog namnen med kommatecken och blank steg ( `, ` ). Utdata är ett String-objekt.

```powershell
Get-ChildItem -Directory C:\ | Join-String -Property Name -DoubleQuote -Separator ', '
```

```Output
"PerfLogs", "Program Files", "Program Files (x86)", "Users", "Windows"
```

`Get-ChildItem` använder **katalog** parametern för att hämta alla katalog namn för `C:\` enheten.
Objekten skickas ned pipelinen till `Join-String` . **Egenskaps** parametern anger katalog namnen. Parametern **DoubleQuote** radbryts katalog namnen med dubbla citat tecken.
**Avgränsnings** parametern anger att du vill använda ett kommatecken och blank steg ( `, ` ) för att avgränsa katalog namnen.

`Get-ChildItem`Objekten är **system. io. DirectoryInfo** och `Join-String` konverterar objekten till **system. String**.

### Exempel 2: Använd en egenskaps under sträng för att ansluta katalog namn

I det här exemplet används en substring-metod för att hämta de första fyra bokstäverna i katalog namn, omsluter utdata i enkla citat tecken och avgränsar katalog namnen med semikolon ( `;` ).

```powershell
Get-ChildItem -Directory C:\ | Join-String -Property {$_.Name.SubString(0,4)} -SingleQuote -Separator ';'
```

```Output
'Perf';'Prog';'Prog';'User';'Wind'
```

`Get-ChildItem` använder **katalog** parametern för att hämta alla katalog namn för `C:\` enheten.
Objekten skickas ned pipelinen till `Join-String` .

**Egenskaps** parameterns skript block använder automatisk variabel ( `$_` ) för att ange varje objekts **namn** egenskap under sträng. Under strängen hämtar de fyra första bokstäverna i varje katalog namn. Under strängen anger tecken start-och slut position. Parametern **SingleQuote** radbryts katalog namnen med enkla tecken. **Avgränsnings** parametern anger att ett semikolon ( `;` ) ska användas för att avgränsa katalog namnen.

Mer information om automatiska variabler och del strängar finns i [about_Automatic_Variables](../microsoft.powershell.core/about/about_automatic_variables.md) och under [sträng](/dotnet/api/system.string.substring).

### Exempel 3: Visa sammanfogning av utdata på en separat rad

Det här exemplet ansluter tjänst namn till varje tjänst på en separat rad och indragna av en flik.

```powershell
Get-Service -Name se* | Join-String -Property Name -Separator "`r`n`t" -OutputPrefix "Services:`n`t"
```

```Output
Services:
    seclogon
    SecurityHealthService
    SEMgrSvc
    SENS
    Sense
    SensorDataService
    SensorService
    SensrSvc
    SessionEnv
```

`Get-Service` använder parametern **Name** med för att ange tjänster som börjar med `se*` . Asterisken ( `*` ) är ett jokertecken för alla bokstäver.

Objekten skickas ned pipelinen till `Join-String` som använder **egenskaps** parametern för att ange tjänst namnen. **Avgränsnings** parametern anger tre specialtecken som representerar en vagn retur ( `` `r `` ), ny rad ( `` `n `` ) och TABB ( `` `t `` ). **OutputPrefix** infogar en etikett **tjänst:** med en ny rad och flik före den första raden i utdata.

Mer information om specialtecken finns [about_Special_Characters](..//microsoft.powershell.core/about/about_special_characters.md).

### Exempel 4: skapa en klass definition från ett objekt

I det här exemplet skapas en PowerShell-klass definition med ett befintligt objekt som mall.

I det här kod exemplet används ihopbuntning för att minska rad längden och förbättra läsbarheten. Mer information finns i [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md).

```powershell
$obj = [pscustomobject] @{Name = "Joe"; Age = 42}
$parms = @{
  Property = "Name"
  FormatString = '  ${0}'
  OutputPrefix = "class {`n"
  OutputSuffix = "`n}`n"
  Separator = "`n"
}
$obj.PSObject.Properties | Join-String @parms
```

```Output
class {
  $Name
  $Age
}
```

## PARAMETRAR

### -DoubleQuote

Omsluter strängvärdet för varje pipeline-objekt i dubbla citat tecken.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: DoubleQuote
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### – FormatString

En format sträng som anger hur varje objekt ska formateras.

```yaml
Type: System.String
Parameter Sets: Format
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – InputObject

Anger den text som ska sammanfogas. Ange en variabel som innehåller texten eller Skriv ett kommando eller uttryck som hämtar objekten för att ansluta till strängar.

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -OutputPrefix

Text som infogas före den utgående strängen. Strängen kan innehålla specialtecken, till exempel vagn retur ( `` `r `` ), rad matning ( `` `n `` ) och TABB ( `` `t `` ).

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: op

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -OutputSuffix

Text som läggs till i den utgående strängen. Strängen kan innehålla specialtecken, till exempel vagn retur ( `` `r `` ), rad matning ( `` `n `` ) och TABB ( `` `t `` ).

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: os

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Egenskap

Namnet på en egenskap, eller ett egenskaps uttryck, som kommer att projicera pipeline-objektet till text.

```yaml
Type: Microsoft.PowerShell.Commands.PSPropertyExpression
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Avgränsare

Text eller tecken, till exempel ett komma eller semikolon som infogas mellan texten för varje pipeline-objekt.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SingleQuote

Radbryter strängvärdet för varje pipeline-objekt i enkla citat tecken.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: SingleQuote
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseCulture

Använder list avgränsaren för den aktuella kulturen som objekt avgränsare. Använd följande kommando för att hitta List avgränsaren för en kultur: `(Get-Culture).TextInfo.ListSeparator` .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

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

## UTDATA

### System. String

## ANTECKNINGAR

## RELATERADE LÄNKAR

[about_Automatic_Variables](../microsoft.powershell.core/about/about_automatic_variables.md)

[about_Special_Characters](..//microsoft.powershell.core/about/about_special_characters.md)

[Under sträng](/dotnet/api/system.string.substring)
