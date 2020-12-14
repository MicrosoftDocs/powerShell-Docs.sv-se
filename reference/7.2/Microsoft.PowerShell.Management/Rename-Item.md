---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/03/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/rename-item?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Rename-Item
ms.openlocfilehash: dec5c2c905486110e4885f29d236ab41d945fb96
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709936"
---
# Rename-Item

## SAMMANFATTNING
Byter namn på ett objekt i ett namn område i PowerShell-providern.

## SYNTAX

### ByPath (standard)

```
Rename-Item [-Path] <String> [-NewName] <String> [-Force] [-PassThru] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm]  [<CommonParameters>]
```

### ByLiteralPath

```
Rename-Item -LiteralPath <String> [-NewName] <String> [-Force] [-PassThru]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

## BESKRIVNING

`Rename-Item`Cmdleten byter namn på ett angivet objekt. Den här cmdleten påverkar inte innehållet i objektet som byter namn.

Du kan inte använda `Rename-Item` för att flytta ett objekt, t. ex. genom att ange en sökväg tillsammans med det nya namnet. Använd cmdleten om du vill flytta och byta namn på ett objekt `Move-Item` .

## EXEMPEL

### Exempel 1: Byt namn på en fil

Det här kommandot byter namn på filen `daily_file.txt` till `monday_file.txt` .

```powershell
Rename-Item -Path "c:\logfiles\daily_file.txt" -NewName "monday_file.txt"
```

### Exempel 2: Byt namn på och flytta ett objekt

Du kan inte använda `Rename-Item` både för att byta namn på och flytta ett objekt. Mer specifikt kan du inte ange en sökväg till värdet för parametern **Nyttnamn** , om inte sökvägen är identisk med sökvägen som anges i parametern **Path** . Annars tillåts endast ett nytt namn.

I det här exemplet görs ett försök att byta namn på `project.txt` filen i den aktuella katalogen till `old-project.txt` i `D:\Archive` katalogen. Resultatet är det fel som visas i utdata.

```powershell
Rename-Item -Path "project.txt" -NewName "d:\archive\old-project.txt"
```

```Output
Rename-Item : can't rename because the target specified represents a path or device name.
At line:1 char:12
+ Rename-Item <<<<  -path project.txt -NewName d:\archive\old-project.txt
+ CategoryInfo          : InvalidArgument: (:) [Rename-Item], PS>  Move-Item -Path "project.txt" -De
stination "d:\archive\old-project.txt"
```

### Exempel 3: Byt namn på en register nyckel

I det här exemplet byter vi namn på en register nyckel från **annonsering** till **marknadsföring**. När kommandot har slutförts får nyckeln ett nytt namn, men register posterna i nyckeln är oförändrade.

```powershell
Rename-Item -Path "HKLM:\Software\MyCompany\Advertising" -NewName "Marketing"
```

### Exempel 4: Byt namn på flera filer

I det här exemplet byter namn på alla `*.txt` filer i den aktuella katalogen till `*.log` .

```powershell
Get-ChildItem *.txt
```

```Output
    Directory: C:\temp\files

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        10/3/2019   7:47 AM           2918 Friday.TXT
-a----        10/3/2019   7:46 AM           2918 Monday.Txt
-a----        10/3/2019   7:47 AM           2918 Wednesday.txt
```

```powershell
Get-ChildItem *.txt | Rename-Item -NewName { $_.Name -replace '.txt','.log' }
Get-ChildItem *.log
```

```Output
    Directory: C:\temp\files

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        10/3/2019   7:47 AM           2918 Friday.log
-a----        10/3/2019   7:46 AM           2918 Monday.log
-a----        10/3/2019   7:47 AM           2918 Wednesday.log
```

`Get-ChildItem`Cmdlet: en hämtar alla filer i den aktuella mappen som har ett `.txt` fil namns tillägg och rör dem `Rename-Item` . Värdet för **Nyttnamn** är ett skript block som körs innan värdet skickas till parametern **Nyttnamn** .

I-skript blocket `$_` representerar den automatiska variabeln varje fil objekt när det kommer till kommandot via pipelinen. -Skript blocket använder `-replace` operatorn för att ersätta fil namns tillägget för varje fil med `.log` . Observera att matchning med `-replace` operatorn inte är Skift läges känsligt.

## PARAMETRAR

### -Credential

> [!NOTE]
> Den här parametern stöds inte av några providrar som installeras med PowerShell. Om du vill personifiera en annan användare eller öka dina autentiseringsuppgifter när du kör denna cmdlet, använder du [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).

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

### -Force

Tvingar cmdleten att byta namn på objekt som annars inte kan ändras, t. ex. dolda eller skrivskyddade filer eller skrivskyddade alias eller variabler. Cmdleten kan inte ändra konstanta alias eller variabler.
Implementeringen varierar från providern till providern. Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).

Även om du använder **Force** -parametern kan inte cmdlet: en åsidosätta säkerhets begränsningar.

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

### -LiteralPath

Anger en sökväg till en eller flera platser. Värdet för **LiteralPath** används exakt som det har angetts. Inga tecken tolkas som jokertecken. Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken. Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.

Mer information finns i [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).

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

### -Nyttnamn

Anger det nya namnet på objektet. Ange ett namn, inte en sökväg och ett namn. Om du anger en sökväg som skiljer sig från den sökväg som anges i parametern **Path** `Rename-Item` genererar ett fel.
Använd om du vill byta namn på och flytta ett objekt `Move-Item` .

Du kan inte använda jokertecken i värdet för parametern **Nyttnamn** . Om du vill ange ett namn för flera filer använder du **ersättnings** operatorn i ett reguljärt uttryck. Mer information om ersättnings operatorn finns [about_Comparison_Operators](../Microsoft.PowerShell.Core/About/about_Comparison_Operators.md).

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### – PassThru

Returnerar ett objekt som representerar objektet i pipelinen. Som standard genererar denna cmdlet inga utdata.

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

### -Path

Anger sökvägen till det objekt som ska bytas namn på.

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
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

Visar vad som skulle hända om cmdleten kördes.
Cmdleten körs inte.

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

### System. String

Du kan skicka vidare en sträng som innehåller en sökväg till denna cmdlet.

## UTDATA

### Ingen eller ett objekt som representerar det omdöpta objektet.

Den här cmdleten genererar ett objekt som representerar det omdöpta objektet om du anger parametern **Passthru** . Annars genererar denna cmdlet inga utdata.

## ANTECKNINGAR

`Rename-Item` är utformad för att fungera med data som exponeras av vilken provider som helst. Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PsProvider` . Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).

## RELATERADE LÄNKAR

[Rensa objekt](Clear-Item.md)

[Kopiera objekt](Copy-Item.md)

[Get-ChildItem](Get-ChildItem.md)

[Hämta objekt](Get-Item.md)

[Anropa-objekt](Invoke-Item.md)

[Flytta objekt](Move-Item.md)

[Nytt objekt](New-Item.md)

[Ta bort objekt](Remove-Item.md)

[Byt namn – ItemProperty](Rename-ItemProperty.md)

[Ange objekt](Set-Item.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

