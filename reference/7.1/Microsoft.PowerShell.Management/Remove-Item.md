---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-item?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Item
ms.openlocfilehash: c4a0243c528cbe1a28cad99cf6fa8d91018d9b3c
ms.sourcegitcommit: bf07cffb2a66dec94bf3576e197090f958701f18
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/19/2020
ms.locfileid: "97692677"
---
# Remove-Item

## SAMMANFATTNING
Tar bort de angivna objekten.

## SYNTAX

### Sökväg (standard)

```
Remove-Item [-Path] <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Recurse] [-Force] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-Stream <String[]>]
 [<CommonParameters>]
```

### LiteralPath

```
Remove-Item -LiteralPath <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Recurse] [-Force] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-Stream <String[]>]
 [<CommonParameters>]
```

## BESKRIVNING

`Remove-Item`Cmdleten tar bort ett eller flera objekt. Eftersom det stöds av många leverantörer kan den ta bort flera olika typer av objekt, inklusive filer, mappar, register nycklar, variabler, alias och funktioner.

## EXEMPEL

### Exempel 1: ta bort filer som har fil namns tillägget

Det här exemplet tar bort alla filer som har namn som innehåller en punkt ( `.` ) från `C:\Test` mappen. Eftersom kommandot anger en punkt tar kommandot inte bort mappar eller filer som inte har något fil namns tillägg.

```powershell
Remove-Item C:\Test\*.*
```

### Exempel 2: ta bort några av dokumentets filer i en mapp

Det här exemplet tar bort från den aktuella mappen alla filer som har ett `.doc` fil namns tillägg och ett namn som inte innehåller `*1*` .

```powershell
Remove-Item * -Include *.doc -Exclude *1*
```

Jokertecken ( `*` ) används för att ange innehållet i den aktuella mappen. Den använder parametrarna **include** och **exclude** för att ange vilka filer som ska tas bort.

### Exempel 3: ta bort dolda, skrivskyddade filer

Det här kommandot tar bort en fil som är både *dold* och *skrivskyddad*.

```powershell
Remove-Item -Path C:\Test\hidden-RO-file.txt -Force
```

Parametern **Path** används för att ange filen. Den använder **Force** -parametern för att ta bort den. Utan **Force** kan du inte ta bort _skrivskyddade_ eller _dolda_ filer.

### Exempel 4: ta bort filer i undermappar rekursivt

Det här kommandot tar bort alla CSV-filer i den aktuella mappen och alla undermappar rekursivt.

Eftersom **rekursivt** -parametern i `Remove-Item` har ett känt problem använder kommandot i det här exemplet `Get-ChildItem` för att hämta de önskade filerna och använder sedan pipeline-operatorn för att skicka dem till `Remove-Item` .

```powershell
Get-ChildItem * -Include *.csv -Recurse | Remove-Item
```

I `Get-ChildItem` kommandot har **sökvägen** värdet ( `*` ) som representerar innehållet i den aktuella mappen. Den använder **inkluderar** för att ange CSV-filtypen och använder **rekursivt** för att göra hämtningen rekursiv. Om du försöker ange en filtyp som sökväg, till exempel `-Path *.csv` , tolkar cmdleten ämnet för sökningen som en fil som inte har några underordnade objekt, och **rekursivt** Miss lyckas.

### Exempel 5: ta bort under nycklar rekursivt

Det här kommandot tar bort register nyckeln "OldApp" och alla dess under nycklar och värden. Den används `Remove-Item` för att ta bort nyckeln. Sökvägen anges, men det valfria parameter namnet (**sökväg**) utelämnas.

Parametern **rekursivt** tar bort allt innehåll i nyckeln "OldApp" rekursivt. Om nyckeln innehåller under nycklar och du utelämnar parametern **rekursivt** uppmanas du att bekräfta att du vill ta bort innehållet i nyckeln.

```powershell
Remove-Item HKLM:\Software\MyCompany\OldApp -Recurse
```

### Exempel 6: ta bort filer med specialtecken

I följande exempel visas hur du tar bort filer som innehåller specialtecken som hakparenteser eller parenteser.

```powershell
Get-ChildItem
```

```Output
    Directory: C:\temp\Downloads

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a---          6/1/2018  12:19 PM           1362 myFile.txt
-a---          6/1/2018  12:30 PM           1132 myFile[1].txt
-a---          6/1/2018  12:19 PM           1283 myFile[2].txt
-a---          6/1/2018  12:19 PM           1432 myFile[3].txt

```

```powershell
Get-ChildItem | Where-Object Name -Like '*`[*'
```

```Output
    Directory: C:\temp\Downloads

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a---          6/1/2018  12:30 PM           1132 myFile[1].txt
-a---          6/1/2018  12:19 PM           1283 myFile[2].txt
-a---          6/1/2018  12:19 PM           1432 myFile[3].txt

```

```powershell
Get-ChildItem | Where-Object Name -Like '*`[*' | ForEach-Object { Remove-Item -LiteralPath $_.Name }
Get-ChildItem
```

```Output
    Directory: C:\temp\Downloads

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a---          6/1/2018  12:19 PM           1362 myFile.txt
```

### Exempel 7: ta bort en alternativ data ström

Det här exemplet visar hur du använder den dynamiska **Stream** -parametern för `Remove-Item` cmdleten för att ta bort en alternativ data ström. Data Ströms parametern introduceras i Windows PowerShell 3,0.

```powershell
Get-Item C:\Test\Copy-Script.ps1 -Stream Zone.Identifier
```

```Output
   FileName: \\C:\Test\Copy-Script.ps1

Stream                   Length
------                   ------
Zone.Identifier              26

```

```powershell
Remove-Item C:\Test\Copy-Script.ps1 -Stream Zone.Identifier
Get-Item C:\Test\Copy-Script.ps1 -Stream Zone.Identifier
```

```Output
Get-Item : Could not open alternate data stream 'Zone.Identifier' of file 'C:\Test\Copy-Script.ps1'.
At line:1 char:1
+ Get-Item 'C:\Test\Copy-Script.ps1' -Stream Zone.Identifier
+ [!INCLUDE[]()][!INCLUDE[]()][!INCLUDE[]()][!INCLUDE[]()][!INCLUDE[]()]~~
    + CategoryInfo          : ObjectNotFound: (C:\Test\Copy-Script.ps1:String) [Get-Item], FileNotFoundE
   xception
    + FullyQualifiedErrorId : AlternateDataStreamNotFound,Microsoft.PowerShell.Commands.GetItemCommand

```

**Stream** -parametern `Get-Item` hämtar `Zone.Identifier` filens data ström `Copy-Script.ps1` . `Remove-Item` använder **Stream** -parametern för att ta bort `Zone.Identifier` filens data ström. Slutligen `Get-Item` visar cmdleten att `Zone.Identifier` strömmen har tagits bort.

## PARAMETRAR

### -Credential

> [!NOTE]
> Den här parametern stöds inte av några providrar som installeras med PowerShell.
> Om du vill personifiera en annan användare eller öka dina autentiseringsuppgifter när du kör denna cmdlet, använder du [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Undanta

Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet exkluderar i åtgärden. Värdet för den här parametern kvalificerar parametern **Path** . Ange ett Sök vägs element eller ett mönster, till exempel `*.txt` . Jokertecken är tillåtna. Parametern **exclude** är endast effektiv när kommandot innehåller innehållet i ett objekt, t. ex `C:\Windows\*` ., där jokertecknet anger innehållet i `C:\Windows` katalogen.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Filter

Anger ett filter för att kvalificera **Sök vägs** parametern. [Fil Systems](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) leverantören är den enda installerade PowerShell-providern som stöder användningen av filter. Du kan hitta syntaxen för filter språket för **fil systemet** i [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md). Filter är mer effektiva än andra parametrar, eftersom providern tillämpar dem när cmdleten hämtar objekten i stället för att ha PowerShell filtrera objekten när de har hämtats.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Force

Tvingar cmdleten att ta bort objekt som inte kan ändras på annat sätt, t. ex. dolda eller skrivskyddade filer eller skrivskyddade alias eller variabler. Cmdleten kan inte ta bort konstanta alias eller variabler.
Implementeringen varierar från providern till providern. Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md). Även om du använder **Force** -parametern kan inte cmdlet: en åsidosätta säkerhets begränsningar.

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

### -Inkludera

Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet inkluderar i åtgärden. Värdet för den här parametern kvalificerar parametern **Path** . Ange ett Sök vägs element eller ett mönster, till exempel `"*.txt"` . Jokertecken är tillåtna. Parametern **include** är endast effektiv när kommandot innehåller innehållet i ett objekt, t. ex `C:\Windows\*` ., där jokertecknet anger innehållet i `C:\Windows` katalogen.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -LiteralPath

Anger en sökväg till en eller flera platser. Värdet för **LiteralPath** används exakt som det har angetts. Inga tecken tolkas som jokertecken. Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken. Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.

Mer information finns i [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

Anger en sökväg till de objekt som tas bort.
Jokertecken är tillåtna.

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### – Rekursivt

Anger att denna cmdlet tar bort objekten på de angivna platserna och i alla underordnade objekt på platserna.

När den används med parametern **include** kanske **rekursivt** -parametern inte tar bort alla undermappar eller alla underordnade objekt. Detta är ett känt problem. Som en lösning kan `Get-ChildItem -Recurse` du prova att skicka kommandots resultat till `Remove-Item` , enligt beskrivningen i "exempel 4" i det här avsnittet.

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

### -Stream

> [!NOTE]
> Den här parametern är endast tillgänglig i Windows.

**Stream** -parametern är en dynamisk parameter som fil Systems leverantören lägger till i `Remove-Item` .
Den här parametern fungerar bara i fil system enheter.

Du kan använda `Remove-Item` för att ta bort en alternativ data ström, till exempel `Zone.Identifier` .
Det är dock inte det rekommenderade sättet att eliminera säkerhets kontroller som blockerar filer som hämtas från Internet. Om du verifierar att en Hämtad fil är säker använder du `Unblock-File` cmdleten.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Confirm

Uppmanar dig att bekräfta innan du kör cmdleten. Mer information finns i följande artiklar:

- [about_Preference_Variables](../microsoft.powershell.core/about/about_preference_variables.md#confirmpreference)
- [about_Functions_CmdletBindingAttribute](../microsoft.powershell.core/about/about_functions_cmdletbindingattribute.md?#confirmimpact)

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

### System. String

Du kan skicka vidare en sträng som innehåller en sökväg, men inte en literal sökväg, till denna cmdlet.

## UTDATA

### Inget

Denna cmdlet returnerar inga utdata.

## ANTECKNINGAR

`Remove-Item`Cmdleten är utformad för att fungera med data som exponeras av vilken provider som helst. Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PsProvider` . Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).

När du försöker ta bort en mapp som innehåller objekt utan att använda parametern **rekursivt** , uppmanas cmdleten att bekräfta. `-Confirm:$false`Om du använder ignoreras inte prompten. Det här är avsiktligt.

## RELATERADE LÄNKAR

[Rensa objekt](Clear-Item.md)

[Kopiera objekt](Copy-Item.md)

[Hämta objekt](Get-Item.md)

[Anropa-objekt](Invoke-Item.md)

[Flytta objekt](Move-Item.md)

[Nytt objekt](New-Item.md)

[Remove-ItemProperty](Remove-ItemProperty.md)

[Byt namn – objekt](Rename-Item.md)

[Ange objekt](Set-Item.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

[about_Preference_Variables](../microsoft.powershell.core/about/about_preference_variables.md#confirmpreference)

[about_Functions_CmdletBindingAttribute](../microsoft.powershell.core/about/about_functions_cmdletbindingattribute.md?#confirmimpact)
