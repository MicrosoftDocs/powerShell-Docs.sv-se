---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 05/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/clear-history?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-History
ms.openlocfilehash: c159262b21e39965f32db4a0fa736aa70de8e916
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263343"
---
# Clear-History

## SAMMANFATTNING
Tar bort poster från PowerShell-sessionens kommando historik.

## SYNTAX

### IDParameter (standard)

```
Clear-History [[-Id] <int[]>] [[-Count] <int>] [-Newest] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### CommandLineParameter

```
Clear-History [[-Count] <int>] [-CommandLine <string[]>] [-Newest] [-WhatIf] [-Confirm]
[<CommonParameters>]
```

## BESKRIVNING

`Clear-History` tar bort kommando historiken från en PowerShell-session. Varje PowerShell-session har en egen kommando historik. Om du vill visa kommando historiken använder du `Get-History` cmdleten.

Som standard `Clear-History` tar bort hela kommando historiken från en PowerShell-session. Du kan använda parametrar med `Clear-History` för att ta bort valda kommandon.

`Clear-History` tar inte bort `PSReadLine` kommando historik filen. `PSReadLine`Modulen lagrar en historik fil som innehåller alla PowerShell-kommandon från varje PowerShell-session. Från en PowerShell-kommandotolk använder du upp-och nedpilarna på tangent bordet för att bläddra genom kommando historiken. Om du vill visa `PSReadLine` konfigurationen för kommando historik använder du `Get-PSReadLineOption` .
`PSReadLine` levereras med PowerShell 5,0 och senare. Mer information finns i [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md).

## EXEMPEL

### Exempel 1: ta bort kommando historiken från en PowerShell-session

Det här kommandot tar bort alla kommandon från en PowerShell-sessions historik.

```powershell
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location .\Test
   2 Update-Help
   3 Set-Location C:\Test\Logs
   4 Get-Location
```

```powershell
Clear-History
Get-History
```

```Output
  Id CommandLine
  -- -----------
   5 Clear-History
```

`Get-History`Cmdleten visar PowerShell-sessionens historik. `Clear-History` tar bort hela kommando historiken. `Get-History` visar den uppdaterade kommando historiken och bekräftar att den tidigare historiken har tagits bort.

### Exempel 2: ta bort de nyaste kommandona

Det här kommandot använder **antalet** och de **senaste** parametrarna för att ta bort de senaste kommandona från en PowerShell-sessions historik.

```powershell
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-Command Clear-History
   3 Get-Command Clear-History -Syntax
   4 Get-Command Clear-History -ShowCommandInfo
   5 Get-Help Get-Alias
   6 Get-Command Get-ChildItem -Syntax
   7 Get-Help Clear-History
   8 Set-Location C:\Test\Logs
   9 Get-Help Get-Variable
  10 Get-Help Get-ChildItem
```

```powershell
Clear-History -Count 5 -Newest
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-Command Clear-History
   3 Get-Command Clear-History -Syntax
   4 Get-Command Clear-History -ShowCommandInfo
   5 Get-Help Get-Alias
  11 Clear-History -Count 5 -Newest
```

`Get-History`Cmdleten visar PowerShell-sessionens historik. `Clear-History` används för att ta bort kommando historiken. Parametern **Count** anger antalet kommandon som ska tas bort, inklusive det angivna ID: **t**. Den **senaste** parametern anger att de nyaste kommandona tas bort från historiken. `Get-History`visar den uppdaterade kommando historiken och bekräftar att de fem senaste kommandona har tagits bort, **ID 6**  -  **ID 10**.

### Exempel 3: ta bort kommandon som matchar vissa villkor

Det här kommandot tar bort kommandon som matchar de kriterier som har definierats av **kommando rads** parametern.

```powershell
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-Command Clear-History
   3 Get-Command Clear-History -Syntax
   4 Get-Command Clear-History -ShowCommandInfo
   5 Get-Help Get-Alias
   6 Get-Command Get-ChildItem -Syntax
   7 Get-Help Clear-History
```

```powershell
Clear-History -CommandLine *Help*, *Syntax
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-Command Clear-History
   4 Get-Command Clear-History -ShowCommandInfo
   8 Clear-History -CommandLine *Help*, *Syntax
```

`Get-History`Cmdleten visar PowerShell-sessionens historik. `Clear-History` tar bort kommando historiken. Parametern **CommandLine** anger kommandon som innehåller **Hjälp** eller slutar med **syntax**. `Get-History` visar den uppdaterade kommando historiken och bekräftar att kommando **-ID 3** , **ID 5** , **ID 6** och **ID 7** har tagits bort.

### Exempel 4: ta bort kommandon efter ID-nummer

Detta kommando tar bort vissa historik objekt med hjälp av **ID**. Om du vill ta bort flera kommandon skickar du en kommaavgränsad lista med **ID-** nummer.

```powershell
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-History
   3 Get-Help Get-Alias
   4 Get-Command Clear-History
   5 Get-Command Clear-History -Syntax
   6 Get-Command Clear-History -ShowCommandInfo
```

```powershell
Clear-History -Id 3, 5
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-History
   4 Get-Command Clear-History
   6 Get-Command Clear-History -ShowCommandInfo
   7 Get-History
   8 Clear-History -Id 3, 5
```

`Get-History`Cmdleten visar PowerShell-sessionens historik. `Clear-History` tar bort kommando historiken. Parametern **ID** anger vilka kommandon som ska tas bort. `Get-History` visar den uppdaterade kommando historiken och bekräftar att **ID 3** och **ID 5** har tagits bort.

### Exempel 5: ta bort kommandon efter ID-nummer och antal

Det här kommandot använder parametrarna **ID** och **Count** för att ta bort kommando historiken. Kommandon tas bort från det angivna **ID: t** i omvänd ordning, nyaste till äldsta.

```powershell
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-Command Clear-History
   3 Get-Command Clear-History -Syntax
   4 Get-Command Clear-History -ShowCommandInfo
   5 Get-Help Get-Alias
   6 Get-Command Get-ChildItem -Syntax
   7 Get-Help Clear-History
   8 Set-Location C:\Test\Logs
   9 Get-Help Get-Variable
  10 Get-Help Get-ChildItem
```

```powershell
Clear-History -Id 7 -Count 5
Get-History
```

```Output
  Id CommandLine
  -- -----------
   1 Set-Location C:\Test\
   2 Get-Command Clear-History
   8 Set-Location C:\Test\Logs
   9 Get-Help Get-Variable
  10 Get-Help Get-ChildItem
  11 Clear-History -Id 7 -Count 5
```

`Get-History`Cmdleten visar PowerShell-sessionens historik. `Clear-History` tar bort kommando historiken. **ID-** parametern anger att börjar med **ID 7**. Parametern **Count** anger att fem kommandon ska tas bort, inklusive det angivna **ID: t**. `Get-History`visar den uppdaterade kommando historiken och bekräftar att fem kommandon har tagits bort, **ID 3**  -  **ID 7**.

## PARAMETRAR

### -Kommandorad

Tar bort kommando historik från en PowerShell-session. Strängen måste vara en exakt matchning eller använda jokertecken för att matcha kommandon i PowerShell-sessionens historik som visas av `Get-History` . Om du anger mer än en sträng `Clear-History` tar bort kommandon som matchar någon av strängarna. **Kommando rads** parametern kan användas med **Count**.

Använd enkla offerter för strängar med ett blank steg. Mer information finns i [about_Quoting_Rules](About/about_Quoting_Rules.md).

```yaml
Type: System.String[]
Parameter Sets: CommandLineParameter
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Antal

Anger antalet historik poster som `Clear-History` tas bort. Kommandona tas bort i ordning, från och med den äldsta posten i historiken.

Parametrarna **Count** och **ID** kan användas tillsammans. Parametern **Count** anger antalet kommandon som ska tas bort, inklusive det angivna ID: **t**. Från och med det angivna **ID: t** raderas kommandon i omvänd ordning. Om **ID:** t till exempel är 30 och **antalet** är 10, `Clear-History` tar bort objekt 21 till 30.

Parametrarna **Count** och **CommandLine** kan användas tillsammans. **Count** anger antalet kommandon som ska tas bort och som matchar parameter värde för **kommando raden** . Kommandona tas bort i sekventiell ordning.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ID

Anger det **ID** för kommando historik som `Clear-History` tar bort. Använd cmdleten om du vill visa **ID-** nummer `Get-History` . **ID-** numren är sekventiella och kommandon behåller sina **ID-** nummer i en PowerShell-session. **ID-** parametern kan användas med **Count** och **nyast**.

```yaml
Type: System.Int32[]
Parameter Sets: IDParameter
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Nyaste

När den **senaste** parametern används `Clear-History` raderas de senaste posterna i historiken. Som standard `Clear-History` raderas de äldsta posterna i historiken.

Den **senaste** parametern kan användas med **ID** och **Count**. Parametern **Count** anger antalet kommandon som ska tas bort, inklusive det angivna ID: **t**. Från och med det angivna **ID: t** raderas kommandon i sekventiell ordning. Om **ID:** t till exempel är 30 och **antalet** är 10, `Clear-History` tar bort objekt 30 till 39.

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

### -Confirm

Du uppmanas att bekräfta innan du kör `Clear-History` cmdleten.

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

Visar vad som händer om `Clear-History` cmdleten körs. Cmdleten körs inte.

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

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## INDATA

### Inget

Det går inte att skicka pipe-objekt till `Clear-History` .

## UTDATA

### Inget

`Clear-History` genererar inga utdata.

## ANTECKNINGAR

PowerShell-sessionens historik är en lista över kommandon som angavs under en PowerShell-session. Du kan visa historik, Lägg till och ta bort kommandon och köra kommandon från historiken. Mer information finns i [about_History](About/about_History.md).

Historiken för sessionen hanteras separat från historiken som underhålls av **PSReadLine** -modulen.
Båda historiken är tillgängliga i sessioner där **PSReadLine** har lästs in. Den här cmdleten fungerar bara med tidigare session. Mer information finns i [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md).

## RELATERADE LÄNKAR

[about_History](About/about_History.md)

[about_PSReadLine](../PSReadLine/About/about_PSReadLine.md)

[about_Quoting_Rules](About/about_Quoting_Rules.md)

[Lägg till-historik](Add-History.md)

[Hämta historik](Get-History.md)

[Anropa-historik](Invoke-History.md)

[Get-PSReadLineOption](/powershell/module/psreadline/get-psreadlineoption)

[Set-PSReadLineOption](/powershell/module/psreadline/set-psreadlineoption)

