---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/tee-object?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Tee-Object
ms.openlocfilehash: fdfbb75bf95c8dc248441b6399312ed0592f62de
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263420"
---
# Tee-Object

## SAMMANFATTNING
Sparar kommandoutdata i en fil eller variabel och skickar det sedan till pipelinen.

## SYNTAX

### Fil (standard)

```
Tee-Object [-InputObject <PSObject>] [-FilePath] <String> [-Append] [<CommonParameters>]
```

### LiteralFile

```
Tee-Object [-InputObject <PSObject>] -LiteralPath <String> [<CommonParameters>]
```

### Variabel

```
Tee-Object [-InputObject <PSObject>] -Variable <String> [<CommonParameters>]
```

## BESKRIVNING

`Tee-Object`Cmdleten omdirigerar utdata, det vill säga skickar utdata från ett kommando i två riktningar (t. ex. bokstaven T). Den lagrar utdata i en fil eller variabel och skickar den sedan nedåt i pipelinen. Om `Tee-Object` är det sista kommandot i pipelinen visas kommandots utdata i prompten.

## EXEMPEL

### Exempel 1: utmatnings processer till en fil och till konsolen

Det här exemplet hämtar en lista över processerna som körs på datorn och skickar resultatet till en fil.
Eftersom en andra sökväg inte anges visas även processerna i-konsolen.

```powershell
Get-Process | Tee-Object -FilePath "C:\Test1\testfile2.txt"
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)    Id ProcessName
-------  ------    -----      ----- -----   ------    -- -----------
83       4     2300       4520    39     0.30    4032 00THotkey
272      6     1400       3944    34     0.06    3088 alg
81       3      804       3284    21     2.45     148 ApntEx
81       4     2008       5808    38     0.75    3684 Apoint
...
```

### Exempel 2: utmatnings processer till en variabel och `Select-Object`

Det här exemplet hämtar en lista över processer som körs på datorn, sparar dem i `$proc` variabeln och rör dem `Select-Object` .

```powershell
Get-Process notepad | Tee-Object -Variable proc | Select-Object processname,handles
```

```Output
ProcessName                              Handles
-----------                              -------
notepad                                  43
notepad                                  37
notepad                                  38
notepad                                  38
```

`Select-Object`Cmdleten väljer **processname** och **hanterar** egenskaperna. Observera att `$proc` variabeln innehåller den standard information som returneras av `Get-Process` .

### Exempel 3: Spara systemfiler till två loggfiler

I det här exemplet sparas en lista över systemfiler i två loggfiler, en ackumulerad fil och en aktuell fil.

```powershell
Get-ChildItem -Path D: -File -System -Recurse |
  Tee-Object -FilePath "c:\test\AllSystemFiles.txt" -Append |
    Out-File c:\test\NewSystemFiles.txt
```

Kommandot använder `Get-ChildItem` cmdleten för att göra en rekursiv sökning efter systemfiler på enheten D:. En pipeline-operator (|) skickar listan till `Tee-Object` , som lägger till listan i AllSystemFiles.txt-filen och skickar listan nedåt till `Out-File` cmdleten, som sparar listan i NewSystemFiles.txts filen.

## PARAMETRAR

### -Lägg till

Anger att cmdleten lägger till utdata i den angivna filen. Utan den här parametern ersätter det nya innehållet det befintliga innehållet i filen utan varning.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: File
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Sökväg

Anger en fil som denna cmdlet sparar objektet i jokertecken tillåts, men måste matcha en enskild fil.

```yaml
Type: System.String
Parameter Sets: File
Aliases: Path

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### – InputObject

Anger det objekt som ska sparas och visas. Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten. Du kan också skicka ett objekt till `Tee-Object` .

När du använder parametern **InputObject** i `Tee-Object` , i stället för att skicka kommando resultat till `Tee-Object` , behandlas **InputObject** -värdet som ett enskilt objekt, även om värdet är en samling.

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

Anger en fil som denna cmdlet sparar objektet i. Till skillnad från **sökväg** , används värdet för parametern **LiteralPath** exakt som det har angetts. Inga tecken tolkas som jokertecken. Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken. Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.

```yaml
Type: System.String
Parameter Sets: LiteralFile
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Variabel

Anger en variabel som cmdleten sparar objektet i. Ange ett variabel namn utan föregående dollar tecken ( `$` ).

```yaml
Type: System.String
Parameter Sets: Variable
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. Management. Automation. PSObject

Du kan skicka pipe-objekt till `Tee-Object` .

## UTDATA

### System. Management. Automation. PSObject

`Tee-Object` Returnerar det objekt som omdirigeras.

## ANTECKNINGAR

Du kan också använda `Out-File` cmdleten eller omdirigerings operatorn, som båda sparar utdata i en fil, men som inte skickar den till pipelinen.

Från och med PowerShell 6 `Tee-Object` använder BOM-mindre UTF-8-kodning när den skriver till filer. Om du behöver en annan kodning använder du `Out-File` cmdleten med parametern **encoding** .

## RELATERADE LÄNKAR

[Jämför objekt](Compare-Object.md)

[-Objekt](../Microsoft.PowerShell.Core/ForEach-Object.md)

[Gruppera objekt](Group-Object.md)

[Mått – objekt](Measure-Object.md)

[Nytt – objekt](New-Object.md)

[Select-Object](Select-Object.md)

[Sortera objekt](Sort-Object.md)

[Where-objekt](../Microsoft.PowerShell.Core/Where-Object.md)

[about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md)

