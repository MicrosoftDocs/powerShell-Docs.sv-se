---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/unblock-file?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unblock-File
ms.openlocfilehash: 56fe7affdc6b64af53f179b438375fcec8f01227
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94344141"
---
# Unblock-File

## SAMMANFATTNING
Avblockerar filer som har hämtats från Internet.

## SYNTAX

### ByPath (standard)

```
Unblock-File [-Path] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByLiteralPath

```
Unblock-File -LiteralPath <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING

Med `Unblock-File` cmdleten kan du öppna filer som har hämtats från Internet. Den blockerar PowerShell-skriptfiler som hämtades från Internet så att du kan köra dem, även när PowerShell-körnings principen är **RemoteSigned**. Som standard blockeras de här filerna för att skydda datorn från ej betrodda filer.

Innan du använder `Unblock-File` cmdleten granskar du filen och dess källa och kontrollerar att den är säker att öppna.

Internt `Unblock-File` tar cmdleten bort zonen. identifierare, alternativ data ström som har värdet "3" för att indikera att den har hämtats från Internet.

Mer information om körnings principer för PowerShell finns i [about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md).

Den här cmdleten introducerades i Windows PowerShell 3,0.

## EXEMPEL

### Exempel 1: avblockera en fil

Det här kommandot avblockerar filen PowerShellTips. chm.

```
PS C:\> Unblock-File -Path C:\Users\User01\Documents\Downloads\PowerShellTips.chm
```

### Exempel 2: avblockera flera filer

Detta kommando avblockerar alla filer i `C:\Downloads` katalogen med namn som innehåller "PowerShell". Kör inte något kommando som det här förrän du har kontrollerat att alla filer är säkra.

```
PS C:\> dir C:\Downloads\*PowerShell* | Unblock-File
```

### Exempel 3: Sök och avblockera skript

Det här kommandot visar hur du hittar och avblockerar PowerShell-skript.

Det första kommandot använder **Stream** -parametern för cmdleten *Get-item* för att hämta filer med zonen. identifierarens data ström.

Det andra kommandot visar vad som händer när du kör ett blockerat skript i en PowerShell-session där körnings principen är **RemoteSigned**. RemoteSigned-principen förhindrar att du kör skript som har hämtats från Internet om de inte har signerats digitalt.

Det tredje kommandot använder `Unblock-File` cmdleten för att avblockera skriptet så att det kan köras i sessionen.

```
PS C:\> Get-Item * -Stream "Zone.Identifier" -ErrorAction SilentlyContinue
   FileName: C:\ps-test\Start-ActivityTracker.ps1

Stream                   Length
------                   ------
Zone.Identifier              26

PS C:\> C:\ps-test\Start-ActivityTracker.ps1
c:\ps-test\Start-ActivityTracker.ps1 : File c:\ps-test\Start-ActivityTracker.ps1 cannot
be loaded. The file c:\ps-test\Start-ActivityTracker.ps1 is not digitally signed. The script
will not execute on the system. For more information, see about_Execution_Policies.

At line:1 char:1
+ c:\ps-test\Start-ActivityTracker.ps1
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : SecurityError: (:) [], PSSecurityException
    + FullyQualifiedErrorId : UnauthorizedAccess

PS C:\> Get-Item C:\ps-test\Start-ActivityTracker.ps1 | Unblock-File
```

## PARAMETRAR

### -LiteralPath

Anger de filer som ska avblockeras. Till skillnad från **sökväg** används värdet för parametern **LiteralPath** exakt som det har angetts. Inga tecken tolkas som jokertecken. Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken. Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

Anger de filer som ska avblockeras. Jokertecken stöds.

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
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

### System. String

Du kan skicka en fil Sök väg till `Unblock-File` .

## UTDATA

### Inget

Denna cmdlet genererar inga utdata.

## ANTECKNINGAR

- Stöd för macOS lades till i PowerShell 7.
- `Unblock-File`Cmdleten fungerar bara i fil system enheter.
- `Unblock-File` utför samma åtgärd som knappen **Häv blockering** i dialog rutan **Egenskaper** i Utforskaren i Utforskaren.
- Om du använder `Unblock-File` cmdleten på en fil som inte är blockerad har kommandot ingen påverkan på den ej blockerade filen och cmdleten genererar inga fel.

## RELATERADE LÄNKAR

[about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)

[Hämta objekt](../Microsoft.PowerShell.Management/Get-Item.md)

[Ut-fil](Out-File.md)

[FileSystem-Provider](../Microsoft.PowerShell.Core/about/about_FileSystem_Provider.md)
