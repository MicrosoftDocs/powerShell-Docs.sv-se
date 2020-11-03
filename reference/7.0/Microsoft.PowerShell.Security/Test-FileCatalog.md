---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 11/02/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/test-filecatalog?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-FileCatalog
ms.openlocfilehash: 01b349ab76ee1d661edd0d30ac23202555575485
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93263024"
---
# Test-FileCatalog

## SAMMANFATTNING
`Test-FileCatalog` verifierar om hash-värdena i en katalog fil (. cat) matchar hasharna för de faktiska filerna för att verifiera deras äkthet.

Denna cmdlet stöds bara i Windows.

## SYNTAX

```
Test-FileCatalog [-Detailed] [-FilesToSkip <String[]>] [-CatalogFilePath] <String> [[-Path] <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING

`Test-FileCatalog` verifierar filens äkthet genom att jämföra hash-filerna för en katalog fil (. cat) med hash-värdena för faktiska filer på disk.
Om det upptäcker eventuella avvikelser returneras statusen som ValidationFailed. Användare kan hämta all den här informationen med hjälp av parametern-detaljerad.
Den visar också signerings status för katalogen i egenskapen signatur som motsvarar anrop av `Get-AuthenticodeSignature` cmdleten i katalog filen.
Användare kan även hoppa över alla filer under valideringen med hjälp av parametern-FilesToSkip.

Denna cmdlet stöds bara i Windows.

## EXEMPEL

### Exempel 1: skapa och validera en fil katalog

```powershell
New-FileCatalog -Path $PSHOME\Modules\Microsoft.PowerShell.Utility -CatalogFilePath \temp\Microsoft.PowerShell.Utility.cat -CatalogVersion 2.0

Test-FileCatalog -CatalogFilePath \temp\Microsoft.PowerShell.Utility.cat -Path "$PSHome\Modules\Microsoft.PowerShell.Utility\"
```

```Output
Valid
```

### Exempel 2: verifiera en fil katalog med detaljerade utdata

```powershell
Test-FileCatalog -CatalogFilePath \temp\Microsoft.PowerShell.Utility.cat -Path "$PSHome\Modules\Microsoft.PowerShell.Utility\"
```

```Output
Status        : Valid
HashAlgorithm : SHA256
CatalogItems  : {[Microsoft.PowerShell.Utility.psd1,
                A7028BD54018AE519381CDF5BF91F3B0417BD9345478086089ACBFAD05C899FC], [Microsoft.PowerShell.Utility.psm1,
                1127E8151FB86BCB683F932E8F6538552F7195816ED351A28AE07A753B8F20DE]}
PathItems     : {[Microsoft.PowerShell.Utility.psd1,
                A7028BD54018AE519381CDF5BF91F3B0417BD9345478086089ACBFAD05C899FC], [Microsoft.PowerShell.Utility.psm1,
                1127E8151FB86BCB683F932E8F6538552F7195816ED351A28AE07A753B8F20DE]}
Signature     : System.Management.Automation.Signature
```

## PARAMETRAR

### -CatalogFilePath

En sökväg till en katalog fil (. cat) som innehåller de hashar som ska användas för verifiering.

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

### -Detaljerad

Returnerar mer information ett mer detaljerat `CatalogInformation` objekt som innehåller de testade filerna, deras förväntade/faktiska hash-värden och en Authenticode-signatur i katalog filen om den är signerad.

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

### -FilesToSkip

En matris med sökvägar som inte ska testas som en del av verifieringen.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

En mapp eller en matris med filer som ska val IDE ras mot katalog filen.

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

### System. IO. DirectoryInfo [], system. string []

Pipelinen accepterar en matris med strängar eller `DirectoryInfo` objekt som representerar sökvägar till de filer som behöver verifieras.

## UTDATA

### System. Management. Automation. CatalogValidationStatus

Standard retur typen som innehåller värdet antingen `Valid` eller `ValidationFailed` .

### System. Management. Automation. CatalogInformation

Ett mer detaljerat objekt som returneras när `-Detailed` du använder som kan användas för att analysera särskilda filer som kanske inte har godkänts av verifiering, vilka hash-värden som förväntades jämfört med och upptäcktes, och algoritmen som används i katalogen.

## ANTECKNINGAR

## RELATERADE LÄNKAR

[New-FileCatalog](New-FileCatalog.md)

[PowerShellGet](/powershell/module/PowerShellGet)
