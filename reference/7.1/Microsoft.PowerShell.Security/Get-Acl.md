---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 03/25/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-acl?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Acl
ms.openlocfilehash: 118c3e563743cee03dc7a75ca68e0979c1522f07
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94347082"
---
# Get-Acl

## SAMMANFATTNING
Hämtar säkerhets beskrivningen för en resurs, till exempel en fil eller register nyckel.

## SYNTAX

### ByPath (standard)

```
Get-Acl [[-Path] <String[]>] [-Audit] [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [<CommonParameters>]
```

### ByInputObject

```
Get-Acl -InputObject <PSObject> [-Audit] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [<CommonParameters>]
```

### ByLiteralPath

```
Get-Acl [-LiteralPath <String[]>] [-Audit] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [<CommonParameters>]
```

## BESKRIVNING

`Get-Acl`Cmdleten hämtar objekt som representerar säkerhets beskrivningen för en fil eller resurs. Säkerhets beskrivningen innehåller åtkomst kontrol listorna (ACL) för resursen. ACL: en anger de behörigheter som användare och användar grupper har åtkomst till resursen.

Från och med Windows PowerShell 3,0 kan du använda **InputObject** -parametern för `Get-Acl` för att hämta säkerhets beskrivningen för objekt som inte har en sökväg.

## EXEMPEL

### Exempel 1 – Hämta en ACL för en mapp

Det här exemplet hämtar katalogens säkerhets Beskrivning `C:\Windows` .

```powershell
Get-Acl C:\Windows
```

### Exempel 2 – Hämta en ACL för en mapp med jokertecken

Det här exemplet hämtar PowerShell-sökvägen och SDDL för alla `.log` filer i `C:\Windows` katalogen vars namn börjar med `s` .

```powershell
Get-Acl C:\Windows\s*.log | Format-List -Property PSPath, Sddl
```

Kommandot använder `Get-Acl` cmdleten för att hämta objekt som representerar säkerhets beskrivare för varje loggfil. Den använder en pipeline-operator ( `|` ) för att skicka resultatet till- `Format-List` cmdleten. Kommandot använder **egenskaps** parametern för `Format-List` för att endast visa egenskaperna **PsPath** och **SDDL** för varje säkerhets beskrivnings objekt.

Listor används ofta i PowerShell, eftersom långa värden visas trunkerade i tabeller.

**SDDL** -värdena är värdefulla för system administratörer eftersom de är enkla text strängar som innehåller all information i säkerhets beskrivningen. De är därför enkla att skicka och lagra, och de kan tolkas vid behov.

### Exempel 3 – Hämta antal gransknings poster för en ACL

Det här exemplet hämtar säkerhets beskrivare för `.log` filerna i `C:\Windows` katalogen vars namn börjar med `s` .

```powershell
Get-Acl C:\Windows\s*.log -Audit | ForEach-Object { $_.Audit.Count }
```

Den använder **gransknings** parametern för att hämta gransknings poster från SACL i säkerhets beskrivningen.
Sedan använder den `ForEach-Object` cmdleten för att räkna antalet gransknings poster som är associerade med varje fil. Resultatet är en lista med tal som representerar antalet gransknings poster för varje loggfil.

### Exempel 4 – Hämta en ACL för en register nyckel

I det här exemplet används `Get-Acl` cmdleten för att hämta säkerhets beskrivningen för registrets kontroll under nyckel ( `HKLM:\SYSTEM\CurrentControlSet\Control` ).

```powershell
Get-Acl -Path HKLM:\System\CurrentControlSet\Control | Format-List
```

Parametern **Path** anger kontroll under nyckeln. Pipelinen ( `|` ) skickar den säkerhets beskrivning som `Get-Acl` `Format-List` kommer till kommandot, som formaterar egenskaperna för säkerhets beskrivningen som en lista så att de är lätta att läsa.

### Exempel 5 – Hämta en ACL med **InputObject**

I det här exemplet används parametern **InputObject** för `Get-Acl` för att hämta säkerhets beskrivningen för ett underlag rings system objekt.

```powershell
Get-Acl -InputObject (Get-StorageSubSystem -Name S087)
```

## PARAMETRAR

### -Granska

Hämtar gransknings data för säkerhets beskrivningen från system åtkomst kontrol listan (SACL).

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

### -Undanta

Utesluter de angivna objekten. Värdet för den här parametern kvalificerar parametern **Path** . Ange ett Sök vägs element eller ett mönster, till exempel `*.txt` . Jokertecken är tillåtna.

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

Anger ett filter i providerns format eller språk. Värdet för den här parametern kvalificerar parametern **Path** . Syntaxen för filtret, inklusive användning av jokertecken, beror på providern. Filter är mer effektiva än andra parametrar, eftersom providern tillämpar dem när objekten hämtas, i stället för att ha PowerShell filtrera objekten när de har hämtats.

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

### -Inkludera

Hämtar endast de angivna objekten. Värdet för den här parametern kvalificerar parametern **Path** . Ange ett Sök vägs element eller ett mönster, till exempel `*.txt` . Jokertecken är tillåtna.

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

### -Path

Anger sökvägen till en resurs. `Get-Acl` hämtar säkerhets beskrivningen för den resurs som anges av sökvägen. Jokertecken är tillåtna. Om du utelämnar parametern **Path** , `Get-Acl` hämtas säkerhets beskrivningen för den aktuella katalogen.

Parameter namnet ("sökväg") är valfritt.

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### – InputObject

Hämtar säkerhets beskrivningen för det angivna objektet. Ange en variabel som innehåller objektet eller ett kommando som hämtar objektet.

Det går inte att skicka ett objekt, förutom en sökväg, till `Get-Acl` . Använd i stället parametern **InputObject** explicit i kommandot.

Den här parametern introduceras i Windows PowerShell 3,0.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: ByInputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LiteralPath

Anger sökvägen till en resurs. Till skillnad från **sökväg** används värdet för parametern **LiteralPath** exakt som det har angetts. Inga tecken tolkas som jokertecken. Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken. Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.

Den här parametern introduceras i Windows PowerShell 3,0.

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. String

Du kan skicka vidare en sträng som innehåller en sökväg till `Get-Acl` .

## UTDATA

### System. Security. AccessControl. FileSecurity, system. Security. AccessControl. DirectorySecurity, system. Security. AccessControl. RegistrySecurity

`Get-Acl` Returnerar ett objekt som representerar de ACL: er som det hämtar. Objekt typen beror på ACL-typen.

## ANTECKNINGAR

Den här cmdleten är endast tillgänglig på Windows-plattformar.

Som standard `Get-Acl` visar PowerShell-sökvägen till resursen ( `<provider>::<resource-path>` ), ägaren till resursen och "åtkomst", en lista (matris) av åtkomst kontroll POSTERNA i DACL (Discretionary Access Control List) för resursen. DACL-listan styrs av resurs ägaren.

När du formaterar resultatet som en lista, ( `Get-Acl | Format-List` ), utöver sökvägen, ägaren och åtkomst listan, visar PowerShell följande egenskaper och egenskaps värden:

- **Grupp** : ägarens säkerhets grupp.
- **Granskning** : en lista (matris) med poster i system åtkomst kontrol listan (SACL). SACL anger de typer av åtkomst försök som Windows genererar gransknings poster för.
- **SDDL** : säkerhets beskrivningen för den resurs som visas i en enskild text sträng i språk format för säkerhets beskrivnings definition. PowerShell använder **GetSddlForm** -metoden för säkerhets beskrivningar för att hämta dessa data.

Eftersom `Get-Acl` stöds av fil systemet och register leverantörer kan du använda `Get-Acl` för att Visa ACL: en för fil system objekt, till exempel filer och kataloger samt register objekt, till exempel register nycklar och poster.

## RELATERADE LÄNKAR

[Ange ACL](Set-Acl.md)
