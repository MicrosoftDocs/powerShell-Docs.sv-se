---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 08/25/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/copy-item?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Copy-Item
ms.openlocfilehash: ee2d8b8a3b736a59b5af4a81710a0d29dd2238d5
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709535"
---
# Copy-Item

## SAMMANFATTNING
Kopierar ett objekt från en plats till en annan.

## SYNTAX

### Sökväg (standard)

```
Copy-Item [-Path] <String[]> [[-Destination] <String>] [-Container] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Recurse] [-PassThru] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [-FromSession <PSSession>] [-ToSession <PSSession>] [<CommonParameters>]
```

### LiteralPath

```
Copy-Item -LiteralPath <String[]> [[-Destination] <String>] [-Container] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Recurse] [-PassThru] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [-FromSession <PSSession>] [-ToSession <PSSession>] [<CommonParameters>]
```

## BESKRIVNING

`Copy-Item`Cmdleten kopierar ett objekt från en plats till en annan plats i samma namnrymd.
Den kan till exempel kopiera en fil till en mapp, men den kan inte kopiera en fil till en certifikat enhet.

Den här cmdleten klipps inte ut eller raderas inte objekten som kopieras. De specifika objekt som cmdleten kan kopiera beror på vilken PowerShell-provider som exponerar objektet. Till exempel kan den kopiera filer och kataloger i en fil systemen het och register nycklar och poster i register enheten.

Denna cmdlet kan kopiera och byta namn på objekt i samma kommando. Om du vill byta namn på ett objekt anger du det nya namnet i värdet för **mål** parametern. Använd cmdleten om du vill byta namn på ett objekt och inte kopiera det `Rename-Item` .

## EXEMPEL

### Exempel 1: kopiera en fil till den angivna katalogen

I det här exemplet kopieras `mar1604.log.txt` filen till `C:\Presentation` katalogen. Den ursprungliga filen har inte tagits bort.

```powershell
Copy-Item "C:\Wabash\Logfiles\mar1604.log.txt" -Destination "C:\Presentation"
```

### Exempel 2: kopiera katalog innehåll till en befintlig katalog

I det här exemplet kopieras innehållet i `C:\Logfiles` katalogen till den befintliga `C:\Drawings` katalogen. `Logfiles`Katalogen har inte kopierats.

Om `Logfiles` katalogen innehåller filer i under kataloger, kopieras dessa under kataloger med sina fil träd intakta. Som standard anges **container** parametern till **True**, vilket bevarar katalog strukturen.

```powershell
Copy-Item -Path "C:\Logfiles\*" -Destination "C:\Drawings" -Recurse
```

> [!NOTE]
> Om du behöver inkludera `Logfiles` katalogen i kopian tar du bort den `\*` från **sökvägen**.
> Exempel:
>
> `Copy-Item -Path "C:\Logfiles" -Destination "C:\Drawings" -Recurse`

### Exempel 3: Kopiera katalogen och innehållet till en ny katalog

I det här exemplet kopieras innehållet i `C:\Logfiles` käll katalogen och en ny mål katalog skapas. Den nya mål katalogen `\Logs` skapas i `C:\Drawings` .

Om du vill inkludera käll katalogens namn kopierar du till en befintlig mål katalog som visas i **exempel 2**. Du kan också ge den nya mål katalogen samma namn som käll katalogen.

```powershell
Copy-Item -Path "C:\Logfiles" -Destination "C:\Drawings\Logs" -Recurse
```

> [!NOTE]
> Om **sökvägen** inkluderar `\*` kopieras alla katalogens fil innehåll, inklusive under katalog träd, till den nya mål katalogen. Exempel:
>
> `Copy-Item -Path "C:\Logfiles\*" -Destination "C:\Drawings\Logs" -Recurse`

### Exempel 4: kopiera en fil till den angivna katalogen och Byt namn på filen

I det här exemplet används `Copy-Item` cmdleten för att kopiera `Get-Widget.ps1` skriptet från `\\Server01\Share` katalogen till `\\Server12\ScriptArchive` katalogen. Som en del av kopierings åtgärden ändrar kommandot objekt namnet från `Get-Widget.ps1` till `Get-Widget.ps1.txt` , så att det kan bifogas e-postmeddelanden.

```powershell
Copy-Item "\\Server01\Share\Get-Widget.ps1" -Destination "\\Server12\ScriptArchive\Get-Widget.ps1.txt"
```

### Exempel 5: kopiera en fil till en fjärran sluten dator

En session skapas till fjärrdatorn med namnet **Server01** med autentiseringsuppgifterna för `Contoso\User01` och lagrar resultatet i variabeln med namnet `$Session` .

`Copy-Item`Cmdleten kopierar `test.log` från `D:\Folder001` mappen till `C:\Folder001_Copy` mappen på fjärrdatorn med hjälp av sessionsinformation som lagras i `$Session` variabeln. Den ursprungliga filen har inte tagits bort.

```powershell
$Session = New-PSSession -ComputerName "Server01" -Credential "Contoso\User01"
Copy-Item "D:\Folder001\test.log" -Destination "C:\Folder001_Copy\" -ToSession $Session
```

### Exempel 6: kopiera en mapp till en fjärran sluten dator

En session skapas till fjärrdatorn med namnet **Server01** med autentiseringsuppgifterna för `Contoso\User01` och lagrar resultatet i variabeln med namnet `$Session` .

`Copy-Item`Cmdleten kopierar `D:\Folder002` mappen till `C:\Folder002_Copy` katalogen på fjärrdatorn med hjälp av sessionsinformation som lagras i `$Session` variabeln. Eventuella undermappar eller filer kopieras inte utan att använda **rekursivt** -växeln.
Åtgärden skapar `Folder002_Copy` mappen om den inte redan finns.

```powershell
$Session = New-PSSession -ComputerName "Server02" -Credential "Contoso\User01"
Copy-Item "D:\Folder002\" -Destination "C:\Folder002_Copy\" -ToSession $Session
```

### Exempel 7: kopiera hela innehållet i en mapp till en fjärrdator rekursivt

En session skapas till fjärrdatorn med namnet **Server01** med autentiseringsuppgifterna för `Contoso\User01` och lagrar resultatet i variabeln med namnet `$Session` .

`Copy-Item`Cmdleten kopierar hela innehållet från `D:\Folder003` mappen till `C:\Folder003_Copy` katalogen på fjärrdatorn med hjälp av sessionsinformation som lagras i `$Session` variabeln. Undermapparna kopieras med sina fil träd intakta. Åtgärden skapar `Folder003_Copy` mappen om den inte redan finns.

```powershell
$Session = New-PSSession -ComputerName "Server04" -Credential "Contoso\User01"
Copy-Item "D:\Folder003\" -Destination "C:\Folder003_Copy\" -ToSession $Session -Recurse
```

### Exempel 8: kopiera en fil till en fjärrdator och byt sedan namn på filen

En session skapas till fjärrdatorn med namnet **Server01** med autentiseringsuppgifterna för `Contoso\User01` och lagrar resultatet i variabeln med namnet `$Session` .

`Copy-Item`Cmdleten kopierar `scriptingexample.ps1` från `D:\Folder004` mappen till `C:\Folder004_Copy` mappen på fjärrdatorn med hjälp av sessionsinformation som lagras i `$Session` variabeln. Som en del av kopierings åtgärden ändrar kommandot objekt namnet från `scriptingexample.ps1` till `scriptingexample_copy.ps1` , så att det kan bifogas e-postmeddelanden. Den ursprungliga filen har inte tagits bort.

```powershell
$Session = New-PSSession -ComputerName "Server04" -Credential "Contoso\User01"
Copy-Item "D:\Folder004\scriptingexample.ps1" -Destination "C:\Folder004_Copy\scriptingexample_copy.ps1" -ToSession $Session
```

### Exempel 9: kopiera en fjärrfil till den lokala datorn

En session skapas till fjärrdatorn med namnet **Server01** med autentiseringsuppgifterna för `Contoso\User01` och lagrar resultatet i variabeln med namnet `$Session` .

`Copy-Item`Cmdleten kopierar `test.log` från fjärrplatsen `C:\MyRemoteData\` till den lokala `D:\MyLocalData` mappen med hjälp av sessionsinformation som lagras i `$Session` variabeln. Den ursprungliga filen har inte tagits bort.

```powershell
$Session = New-PSSession -ComputerName "Server01" -Credential "Contoso\User01"
Copy-Item "C:\MyRemoteData\test.log" -Destination "D:\MyLocalData\" -FromSession $Session
```

### Exempel 10: kopiera hela innehållet i en fjärran sluten mapp till den lokala datorn

En session skapas till fjärrdatorn med namnet **Server01** med autentiseringsuppgifterna för `Contoso\User01` och lagrar resultatet i variabeln med namnet `$Session` .

`Copy-Item`Cmdleten kopierar hela innehållet från `C:\MyRemoteData\scripts` fjärrmappen till den lokala `D:\MyLocalData` mappen med hjälp av sessionsinformation som lagras i `$Session` variabeln. Om mappen Scripts innehåller filer i undermappar, kopieras dessa undermappar med sina fil träd intakta.

```powershell
$Session = New-PSSession -ComputerName "Server01" -Credential "Contoso\User01"
Copy-Item "C:\MyRemoteData\scripts" -Destination "D:\MyLocalData\" -FromSession $Session
```

### Exempel 11: kopiera hela innehållet i en fjärrmapp till den lokala datorn rekursivt

En session skapas till fjärrdatorn med namnet **Server01** med autentiseringsuppgifterna för `Contoso\User01` och lagrar resultatet i variabeln med namnet `$Session` .

`Copy-Item`Cmdleten kopierar hela innehållet från `C:\MyRemoteData\scripts` fjärrmappen till den lokala `D:\MyLocalData\scripts` mappen med hjälp av sessionsinformation som lagras i `$Session` variabeln. Eftersom parametern **rekursivt** används skapar åtgärden scripts-mappen om den inte redan finns. Om mappen Scripts innehåller filer i undermappar, kopieras dessa undermappar med sina fil träd intakta.

```powershell
$Session = New-PSSession -ComputerName "Server01" -Credential "Contoso\User01"
Copy-Item "C:\MyRemoteData\scripts" -Destination "D:\MyLocalData\scripts" -FromSession $Session -Recurse
```

### Exempel 12: kopiera filer rekursivt från ett mappträd till den aktuella mappen

Det här exemplet visar hur du kopierar filer från en mappstruktur på flera nivåer till en enda platt mapp.
De tre första kommandona visar den befintliga mappstrukturen och innehållet i två filer, båda namnen `file3.txt` .

```powershell
PS C:\temp\test> (Get-ChildItem C:\temp\tree -Recurse).FullName
C:\temp\tree\subfolder
C:\temp\tree\file1.txt
C:\temp\tree\file2.txt
C:\temp\tree\file3.txt
C:\temp\tree\subfolder\file3.txt
C:\temp\tree\subfolder\file4.txt
C:\temp\tree\subfolder\file5.txt

PS C:\temp\test> Get-Content C:\temp\tree\file3.txt
This is file3.txt in the root folder

PS C:\temp\test> Get-Content C:\temp\tree\subfolder\file3.txt
This is file3.txt in the subfolder

PS C:\temp\test> Copy-Item -Path C:\temp\tree -Filter *.txt -Recurse -Container:$false
PS C:\temp\test> (Get-ChildItem . -Recurse).FullName
C:\temp\test\subfolder
C:\temp\test\file1.txt
C:\temp\test\file2.txt
C:\temp\test\file3.txt
C:\temp\test\file4.txt
C:\temp\test\file5.txt

PS C:\temp\test> Get-Content .\file3.txt
This is file3.txt in the subfolder
```

`Copy-Item`Parametern **container** har angetts till `$false` . Detta gör att innehållet i källmappen kopieras, men inte att mappstrukturen bevaras. Observera att filer med samma namn skrivs över i målmappen.

## PARAMETRAR

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

### -Container

Anger att den här cmdleten bevarar behållar objekt under kopierings åtgärden. Som standard anges **container** parametern till **True**.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: True
Accept pipeline input: False
Accept wildcard characters: False
```

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

### -Mål

Anger sökvägen till den nya platsen. Standardvärdet är den aktuella katalogen.

Om du vill byta namn på objektet som kopieras anger du ett nytt namn i värdet för **mål** parametern.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: Current directory
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

Anger ett filter för att kvalificera **Sök vägs** parametern. [Fil Systems](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) leverantören är den enda installerade PowerShell-providern som stöder användningen av filter. Du kan hitta syntaxen för filter språket för **fil systemet** i [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).
Filter är mer effektiva än andra parametrar, eftersom providern tillämpar dem när cmdleten hämtar objekten i stället för att ha PowerShell filtrera objekten efter att de har hämtats.

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

Anger att den här cmdleten kopierar objekt som inte kan ändras på annat sätt, t. ex. kopiera över en skrivskyddad fil eller ett alias.

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

### -FromSession

Anger det **PSSession** -objekt som en fjärrfil kopieras från. När du använder den här parametern, refererar **sökvägen** och **LiteralPath** -parametrarna till den lokala sökvägen på fjärrdatorn.

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
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

### – PassThru

Returnerar ett objekt som representerar det objekt som du arbetar med. Som standard genererar denna cmdlet inga utdata.

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

Anger, som en sträng mat ris, sökvägen till de objekt som ska kopieras. Jokertecken är tillåtna.

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

Anger att denna cmdlet gör en rekursiv kopia.

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

### -ToSession

Anger det **PSSession** -objekt som en fjärrfil kopieras till. När du använder den här parametern refererar **mål** parametern till den lokala sökvägen på fjärrdatorn.

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
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

Denna cmdlet stöder de gemensamma parametrarna:,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` , och `-WarningVariable` . Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. String

Du kan skicka vidare en sträng som innehåller en sökväg till denna cmdlet.

## UTDATA

### Ingen eller ett objekt som representerar det kopierade objektet

När du använder parametern **Passthru** , returnerar denna cmdlet ett objekt som representerar det kopierade objektet. Annars genererar denna cmdlet inga utdata.

## ANTECKNINGAR

Denna cmdlet är utformad för att fungera med data som exponeras av vilken provider som helst. Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PSProvider` . Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).

## RELATERADE LÄNKAR

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

[Rensa objekt](Clear-Item.md)

[Hämta objekt](Get-Item.md)

[Get-PSProvider](Get-PSProvider.md)

[Anropa-objekt](Invoke-Item.md)

[Flytta objekt](Move-Item.md)

[Nytt objekt](New-Item.md)

[Ta bort objekt](Remove-Item.md)

[Byt namn – objekt](Rename-Item.md)

[Ange objekt](Set-Item.md)

