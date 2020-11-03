---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/unblock-file?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unblock-File
ms.openlocfilehash: 1f56dce193cc3c7c8b6af3a7854021b420107255
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264812"
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

Med cmdleten **upplåsningskod-File** kan du öppna filer som har hämtats från Internet.
Den blockerar PowerShell-skriptfiler som hämtades från Internet så att du kan köra dem, även när PowerShell-körnings principen är **RemoteSigned**.
Som standard blockeras de här filerna för att skydda datorn från ej betrodda filer.

Innan du använder **Avblocks-File-** cmdleten granskar du filen och dess källa och kontrollerar att den är säker att öppna.

Internt tar **Avblocks fil-** cmdleten bort zonen. identifierare, alternativ data ström som har värdet "3" för att indikera att den har hämtats från Internet.

Mer information om körnings principer för PowerShell finns i [about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md).

Den här cmdleten introducerades i Windows PowerShell 3,0.

## EXEMPEL

### Exempel 1: avblockera en fil

```
PS C:\> Unblock-File -Path C:\Users\User01\Documents\Downloads\PowerShellTips.chm
```

Det här kommandot avblockerar filen PowerShellTips. chm.

### Exempel 2: avblockera flera filer

```
PS C:\> dir C:\Downloads\*PowerShell* | Unblock-File
```

Detta kommando avblockerar alla filer i C:\Downloads-katalogen vars namn innehåller "PowerShell".
Kör inte något kommando som det här förrän du har kontrollerat att alla filer är säkra.

### Exempel 3: Sök och avblockera skript

```
The first command uses the *Stream* parameter of the Get-Item cmdlet get files with the Zone.Identifier stream.Although you could pipe the output directly to the **Unblock-File** cmdlet (Get-Item * -Stream "Zone.Identifier" -ErrorAction SilentlyContinue | ForEach {Unblock-File $_.FileName}), it is prudent to review the file and confirm that it is safe before unblocking.
PS C:\> Get-Item * -Stream "Zone.Identifier" -ErrorAction SilentlyContinue
   FileName: C:\ps-test\Start-ActivityTracker.ps1

Stream                   Length
------                   ------
Zone.Identifier              26

The second command shows what happens when you run a blocked script in a PowerShell session in which the execution policy is **RemoteSigned**. The RemoteSigned policy prevents you from running scripts that are downloaded from the Internet unless they are digitally signed.
PS C:\> C:\ps-test\Start-ActivityTracker.ps1
c:\ps-test\Start-ActivityTracker.ps1 : File c:\ps-test\Start-ActivityTracker.ps1 cannot
be loaded. The file c:\ps-test\Start-ActivityTracker.ps1 is not digitally signed. The script
will not execute on the system. For more information, see about_Execution_Policies.

At line:1 char:1
+ c:\ps-test\Start-ActivityTracker.ps1
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : SecurityError: (:) [], PSSecurityException
    + FullyQualifiedErrorId : UnauthorizedAccess

The third command uses the **Unblock-File** cmdlet to unblock the script so it can run in the session.
PS C:\> Get-Item C:\ps-test\Start-ActivityTracker.ps1 | Unblock-File
```

Det här kommandot visar hur du hittar och avblockerar PowerShell-skript.

## PARAMETRAR

### -LiteralPath
Anger de filer som ska avblockeras.
Till skillnad från *sökväg* används värdet för parametern *LiteralPath* exakt som det har angetts.
Inga tecken tolkas som jokertecken.
Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.
Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path
Anger de filer som ska avblockeras.
Jokertecken stöds.

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

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. String

Du kan skicka en fil Sök väg till **unblock-File**.

## UTDATA

### Inget

Denna cmdlet genererar inga utdata.

## ANTECKNINGAR

* Cmdlet: en **Avblocks fil** fungerar bara i fil system enheter.
* **Unblock-File** utför samma åtgärd som knappen **Häv blockering** i dialog rutan **Egenskaper** i Utforskaren i Utforskaren.
* Om du använder cmdleten **upplåsningskod-File** på en fil som inte är blockerad, har kommandot ingen påverkan på den ej blockerade filen och cmdleten genererar inga fel.

## RELATERADE LÄNKAR

[about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)

[Hämta objekt](../Microsoft.PowerShell.Management/Get-Item.md)

[Ut-fil](Out-File.md)

[FileSystem-Provider](../Microsoft.PowerShell.Core/about/about_FileSystem_Provider.md)
