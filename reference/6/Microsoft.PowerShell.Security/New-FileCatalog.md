---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 11/02/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/new-filecatalog?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-FileCatalog
ms.openlocfilehash: 861733acd34523ae0d0065f6923948aa45f66f04
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93267213"
---
# New-FileCatalog

## SAMMANFATTNING
`New-FileCatalog` skapar en katalog fil med filhashar som kan användas för att verifiera äktheten för en fil.

## SYNTAX

```
New-FileCatalog [-CatalogVersion <Int32>] [-CatalogFilePath] <String> [[-Path] <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## BESKRIVNING

`New-FileCatalog` skapar en [Windows Catalog-fil](/windows-hardware/drivers/install/catalog-files) för en uppsättning mappar och filer.
Den här katalog filen innehåller hash-värden för alla filer i de angivna Sök vägarna.
Användarna kan sedan distribuera katalogen med sina filer så att användarna kan verifiera om några ändringar har gjorts i mapparna sedan katalog skapande tiden.

Katalog version 1 och 2 stöds. Version 1 använder den (föråldrade) SHA1-hashalgoritmen för att skapa filhasher och version 2 använder SHA256.
Katalog version 2 stöds inte i Windows Server 2008 R2 eller Windows 7.
Du bör använda katalog version 2 på Windows 8, Windows Server 2012 och senare operativ system.

## EXEMPEL

### Exempel 1: skapa en fil katalog för `Microsoft.PowerShell.Utility`

```powershell
New-FileCatalog -Path $PSHOME\Modules\Microsoft.PowerShell.Utility -CatalogFilePath \temp\Microsoft.PowerShell.Utility.cat -CatalogVersion 2.0
```

```Output
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----         11/2/2018 11:58 AM            950 Microsoft.PowerShell.Utility.cat
```

## PARAMETRAR

### -CatalogFilePath

En sökväg till en fil eller mapp där katalog filen (. cat) ska placeras.
Om en mappsökväg anges används standard fil namnet `catalog.cat` .

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -CatalogVersion

Accepterar `1.0` eller `2.0` som möjliga värden för att ange katalog versionen.
`1.0` bör undvikas när det är möjligt, eftersom det använder sig av den oskyddade SHA-1-hashalgoritmen, medan använder sig av `2.0` Secure SHA-1 256-algoritmen, men `1.0` är den enda algoritm som stöds på Windows 7 och Server 2008R2.

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

### -Path

Accepterar en sökväg eller en matris med sökvägar till filer eller mappar som ska ingå i katalog filen.
Om en mapp anges tas även alla filer i mappen med.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
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

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. String

Pipelinen tar en sträng som används som katalog fil namn.

## UTDATA

### System. IO. FileInfo

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Test-FileCatalog](Test-FileCatalog.md)

[PowerShellGet](/powerShell/module/powershellget)
