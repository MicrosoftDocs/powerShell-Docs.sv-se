---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-item?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Item
ms.openlocfilehash: 50a7dba8c4e9cb1cfabd42f39e9fdfb43f22f9b1
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263306"
---
# New-Item

## SAMMANFATTNING
Skapar ett nytt objekt.

## SYNTAX

### pathSet (standard)

```
New-Item [-Path] <String[]> [-ItemType <String>] [-Value <Object>] [-Force] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### nameSet

```
New-Item [[-Path] <String[]>] -Name <String> [-ItemType <String>] [-Value <Object>] [-Force]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING

`New-Item`Cmdleten skapar ett nytt objekt och anger dess värde. Vilka typer av objekt som kan skapas beror på objektets plats. I fil systemet skapas till exempel `New-Item` filer och mappar. I registret `New-Item` skapas register nycklar och poster.

`New-Item` kan också ange värdet för de objekt som skapas. Till exempel, när den skapar en ny fil, `New-Item` kan lägga till det ursprungliga innehållet i filen.

## EXEMPEL

### Exempel 1: skapa en fil i den aktuella katalogen

Det här kommandot skapar en textfil med namnet "testfile1.txt" i den aktuella katalogen. Punkten (".") i värdet för parametern **Path** anger den aktuella katalogen. Den citerade text som följer **värde** parametern läggs till i filen som innehåll.

```powershell
New-Item -Path . -Name "testfile1.txt" -ItemType "file" -Value "This is a text string."
```

### Exempel 2: skapa en katalog

Det här kommandot skapar en katalog med namnet "LogFiles" på `C:` enheten. Parametern **itemType** anger att det nya objektet är en katalog, inte en fil eller något annat fil Systems objekt.

```powershell
New-Item -Path "c:\" -Name "logfiles" -ItemType "directory"
```

### Exempel 3: skapa en profil

Det här kommandot skapar en PowerShell-profil i den sökväg som anges av `$profile` variabeln.

Du kan använda profiler för att anpassa PowerShell. `$profile` är en automatisk (inbyggd) variabel som lagrar sökvägen och fil namnet för profilen "CurrentUser/CurrentHost". Profilen finns inte som standard, även om PowerShell lagrar en sökväg och ett fil namn för den.

I det här kommandot `$profile` representerar variabeln sökvägen till filen. Parametern **itemType** anger att kommandot skapar en fil. Med parametern **Force** kan du skapa en fil i profil Sök vägen, även om katalogerna i sökvägen inte finns.

När du har skapat en profil kan du ange alias, funktioner och skript i profilen för att anpassa ditt gränssnitt.

Mer information finns i [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md) och [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).

```powershell
New-Item -Path $profile -ItemType "file" -Force
```

### Exempel 4: skapa en katalog i en annan katalog

I det här exemplet skapas en ny skript katalog i katalogen "C:\PS-Test".

Namnet på det nya katalog objektet, "skript", ingår i värdet för parametern **Path** i stället för att anges i värdet för **namnet**. Som anges av syntaxen är kommando formuläret giltiga.

```powershell
New-Item -ItemType "directory" -Path "c:\ps-test\scripts"
```

### Exempel 5: skapa flera filer

I det här exemplet skapas filer i två olika kataloger. Eftersom **sökvägen** tar flera strängar kan du använda den för att skapa flera objekt.

```powershell
New-Item -ItemType "file" -Path "c:\ps-test\test.txt", "c:\ps-test\Logs\test.log"
```

### Exempel 6: Använd jokertecken för att skapa filer i flera kataloger

`New-Item`Cmdleten stöder jokertecken i parametern **Path** . Följande kommando skapar en `temp.txt` fil i alla kataloger som anges av jokertecknen i parametern **Path** .

```powershell
Get-ChildItem -Path C:\Temp\
```

```Output
    Directory:  C:\Temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d-----        5/15/2019   6:45 AM        1   One
d-----        5/15/2019   6:45 AM        1   Two
d-----        5/15/2019   6:45 AM        1   Three
```

```powershell
New-Item -Path * -Name temp.txt -ItemType File | Select-Object FullName
```

```Output
FullName
--------
C:\Temp\One\temp.txt
C:\Temp\Three\temp.txt
C:\Temp\Two\temp.txt
```

`Get-ChildItem`Cmdleten visar tre kataloger under `C:\Temp` katalogen. Med jokertecken `New-Item` skapar cmdleten en `temp.txt` fil i alla kataloger under den aktuella katalogen. `New-Item`Cmdleten matar ut de objekt som du har skapat, vilket är skickas för `Select-Object` att verifiera Sök vägarna för de filer som skapats nyligen.

### Exempel 7: skapa en symbolisk länk till en fil eller mapp

I det här exemplet skapas en symbolisk länk till Notice.txt-filen i den aktuella mappen.

```powershell
$link = New-Item -ItemType SymbolicLink -Path .\link -Target .\Notice.txt
$link | Select-Object LinkType, Target
```

```Output
LinkType     Target
--------     ------
SymbolicLink {.\Notice.txt}
```

I det här exemplet är **målet** ett alias för **värde** parametern. Målet för den symboliska länken kan vara en relativ sökväg. Innan PowerShell v 6.2 måste målet vara en fullständigt kvalificerad sökväg.

Från och med PowerShell 7,1 kan du nu skapa en **SymbolicLink** till en mapp i Windows med hjälp av en relativ sökväg.

### Exempel 8: Använd parametern-Force för att försöka återskapa mappar

I det här exemplet skapas en mapp med en fil i. Försöker sedan skapa samma mapp med `-Force` . Mappen skrivs inte över, men returnerar bara det befintliga objektet med filen som skapats intakt.

```powershell
PS> New-Item -Path .\TestFolder -ItemType Directory
PS> New-Item -Path .\TestFolder\TestFile.txt -ItemType File

PS> New-Item -Path .\TestFolder -ItemType Directory -Force

    Directory: C:\
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----         5/1/2020   8:03 AM                TestFolder

PS> Get-ChildItem .\TestFolder\

    Directory: C:\TestFolder
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----         5/1/2020   8:03 AM              0 TestFile.txt
```

### Exempel 9: Använd parametern-Force för att skriva över befintliga filer

Det här exemplet skapar en fil med ett värde och återskapar sedan filen med hjälp av `-Force` . Den befintliga filen skrivs över och den kommer att förlora innehållet som du kan se i egenskapen length

```powershell
PS> New-Item ./TestFile.txt -ItemType File -Value 'This is just a test file'

    Directory: C:\Source\Test
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----         5/1/2020   8:32 AM             24 TestFile.txt

New-Item ./TestFile.txt -ItemType File -Force

    Directory: C:\Source\Test
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----         5/1/2020   8:32 AM              0 TestFile.txt
```

> [!NOTE]
> När `New-Item` du använder med `-Force` växeln för att skapa register nycklar, fungerar kommandot likadant som när du skriver över en fil. Om register nyckeln redan finns kommer nyckeln och alla egenskaper och värden att skrivas över med en tom register nyckel.

## PARAMETRAR

### -Credential

> [!NOTE]
> Den här parametern stöds inte av några providrar som installeras med PowerShell. Använd för att personifiera en annan användare eller öka dina autentiseringsuppgifter när du kör denna cmdlet `Invoke-Command` .

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

Tvingar denna cmdlet att skapa ett objekt som skriver över ett befintligt skrivskyddat objekt. Implementeringen varierar från providern till providern. Även om du använder **Force** -parametern kan inte cmdlet: en åsidosätta säkerhets begränsningar.

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

### -ItemType

Anger providerns angivna typ för det nya objektet. De tillgängliga värdena för den här parametern är beroende av den aktuella provider som du använder.

Om platsen finns i en `FileSystem` enhet tillåts följande värden:

- Fil
- Katalog
- SymbolicLink
- Knutpunkt
- HardLink

> [!NOTE]
> Att skapa en `SymbolicLink` typ i Windows kräver utökade privilegier som administratör. Windows 10 (version 14972 eller senare) med utvecklarläge aktiverat kräver dock inte längre utökade privilegier för att skapa symboliska länkar.

I en `Certificate` enhet är dessa värden som du kan ange:

- Certifikat leverantör
- Certifikat
- Lagringsplats
- StoreLocation

Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Type

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

Anger namnet på det nya objektet. Du kan ange namnet på det nya objektet i parametervärdet för **namn** eller **sökväg** och du kan ange sökvägen till det nya objektet i värdet **namn** eller **sökväg** . Objekt namn som skickas med parametern **Name** skapas i förhållande till värdet för parametern **Path** .

```yaml
Type: System.String
Parameter Sets: nameSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

Anger sökvägen till platsen för det nya objektet. Standardvärdet är den aktuella platsen när **sökvägen** utelämnas. Du kan ange namnet på det nya objektet i **namn** eller ta med det i **sökvägen**. Objekt namn som skickas med parametern **Name** skapas i förhållande till värdet för parametern **Path** .

För den här cmdleten fungerar **Sök vägs** parametern som parametern **LiteralPath** för andra cmdletar.
Jokertecken tolkas inte. Alla tecken skickas till platsens Provider. Providern kanske inte har stöd för alla tecken. Du kan till exempel inte skapa ett fil namn som innehåller en asterisk ( `*` )-bokstav.

```yaml
Type: System.String[]
Parameter Sets: pathSet
Aliases:

Required: True (pathSet), False (nameSet)
Position: 0
Default value: Current location
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Värde

Anger värdet för det nya objektet. Du kan också skicka ett värde till `New-Item` .

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases: Target

Required: False
Position: Named
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

Denna cmdlet stöder de gemensamma parametrarna:,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` , och `-WarningVariable` . Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## INDATA

### System. Object

Du kan skicka ett värde för det nya objektet till denna cmdlet.

## UTDATA

### System. Object

Den här cmdleten returnerar det objekt som skapas.

## ANTECKNINGAR

`New-Item` är utformad för att fungera med data som exponeras av vilken provider som helst. Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PsProvider` . Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).

## RELATERADE LÄNKAR

[Rensa objekt](Clear-Item.md)

[Kopiera objekt](Copy-Item.md)

[Hämta objekt](Get-Item.md)

[Anropa-objekt](Invoke-Item.md)

[Flytta objekt](Move-Item.md)

[Ta bort objekt](Remove-Item.md)

[Byt namn – objekt](Rename-Item.md)

[Ange objekt](Set-Item.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

