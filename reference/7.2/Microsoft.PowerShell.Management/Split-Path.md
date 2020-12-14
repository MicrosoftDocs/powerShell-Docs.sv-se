---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/split-path?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Split-Path
ms.openlocfilehash: e2498c02d42123e207b49e622654d3cb881fc0fc
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710386"
---
# Split-Path

## SAMMANFATTNING
Returnerar den angivna delen av en sökväg.

## SYNTAX

### ParentSet (standard)

```
Split-Path [-Path] <String[]> [-Parent] [-Resolve] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### LeafSet

```
Split-Path [-Path] <String[]> -Leaf [-Resolve] [-Credential <PSCredential>] [<CommonParameters>]
```

### LeafBaseSet

```
Split-Path [-Path] <String[]> -LeafBase [-Resolve] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### ExtensionSet

```
Split-Path [-Path] <String[]> -Extension [-Resolve] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### QualifierSet

```
Split-Path [-Path] <String[]> -Qualifier [-Resolve] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### NoQualifierSet

```
Split-Path [-Path] <String[]> -NoQualifier [-Resolve] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### IsAbsoluteSet

```
Split-Path [-Path] <String[]> [-Resolve] -IsAbsolute [-Credential <PSCredential>]
 [<CommonParameters>]
```

### LiteralPathSet

```
Split-Path -LiteralPath <String[]> [-Resolve] [-Credential <PSCredential>] [<CommonParameters>]
```

## BESKRIVNING

`Split-Path`Cmdleten returnerar bara den angivna delen av en sökväg, till exempel den överordnade mappen, en undermapp eller ett fil namn. Det kan också hämta objekt som refereras av den delade sökvägen och se om sökvägen är relativ eller absolut.

Du kan använda den här cmdleten för att hämta eller skicka endast en markerad del av en sökväg.

## EXEMPEL

### Exempel 1: Hämta en sökvägs kvalificerare

```powershell
Split-Path -Path "HKCU:\Software\Microsoft" -Qualifier
```

```Output
HKCU:
```

Det här kommandot returnerar bara kvalificeraren för sökvägen. Kvalificeraren är enheten.

### Exempel 2: Visa fil namn

```powershell
Split-Path -Path "C:\Test\Logs\*.log" -Leaf -Resolve
```

```Output
Pass1.log
Pass2.log
...
```

Det här kommandot visar de filer som refereras av den delade sökvägen. Eftersom den här sökvägen är delad till det sista objektet, även kallat lövnod, visar kommandot bara fil namnen.

Parametern **matcha** visar `Split-Path` de objekt som den delade sökvägen refererar till, i stället för att Visa delnings Sök vägen.

Precis som alla `Split-Path` kommandon returnerar det här kommandot strängar. Den returnerar inte **fileinfo** -objekt som representerar filerna.

### Exempel 3: hämta den överordnade behållaren

```powershell
Split-Path -Path "C:\WINDOWS\system32\WindowsPowerShell\V1.0\about_*.txt"
```

```Output
C:\WINDOWS\system32\WindowsPowerShell\V1.0
```

Det här kommandot returnerar bara de överordnade behållarna för sökvägen. Eftersom den inte innehåller några parametrar för att ange delning, `Split-Path` använder standard delnings platsen, som är **överordnad**.

### Exempel 4: avgör om en sökväg är absolut

```powershell
Split-Path -Path ".\My Pictures\*.jpg" -IsAbsolute
```

```Output
False
```

Det här kommandot avgör om sökvägen är relativ eller absolut. I det här fallet, eftersom sökvägen är relativ till den aktuella mappen, som representeras av en punkt ( `.` ), returneras `$False` .

### Exempel 5: ändra plats till en angiven sökväg

```powershell
PS C:\> Set-Location (Split-Path -Path $profile)
PS C:\Documents and Settings\User01\My Documents\WindowsPowerShell>
```

Det här kommandot ändrar platsen till den mapp som innehåller PowerShell-profilen.

Kommandot inom parenteser använder `Split-Path` för att bara returnera den överordnade sökvägen till sökvägen som lagras i den inbyggda `$Profile` variabeln. Den **överordnade** parametern är standard parametern för delad plats.
Därför kan du utelämna det från kommandot. Parenteserna Direct PowerShell för att köra kommandot först. Detta är ett bra sätt att flytta till en mapp som har ett långt Sök vägs namn.

### Exempel 6: dela en bana med hjälp av pipelinen

```powershell
'C:\Documents and Settings\User01\My Documents\My Pictures' | Split-Path
```

```Output
C:\Documents and Settings\User01\My Documents
```

Det här kommandot använder en pipeline-operator ( `|` ) för att skicka en sökväg till `Split-Path` . Sökvägen omges av citat tecken för att ange att den är en enskild token.

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
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Tillägg

Anger att denna cmdlet bara returnerar tillägg för bladet. I sökvägen returneras till exempel `C:\Test\Logs\Pass1.log` bara `.log` .

Den här parametern introducerades i PowerShell 6,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ExtensionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -IsAbsolute

Anger att denna cmdlet returnerar $True om sökvägen är absolut och $False om den är relativ. En absolut sökväg har en längd som är större än noll och använder inte en punkt ( `.` ) för att ange den aktuella sökvägen.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: IsAbsoluteSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Löv

Anger att denna cmdlet endast returnerar det sista objektet eller behållaren i sökvägen. I sökvägen returnerar till exempel `C:\Test\Logs\Pass1.log` bara Pass1. log.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LeafSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -LeafBase

Anger att denna cmdlet returnerar endast bas namnet för löv. I sökvägen returneras till exempel `C:\Test\Logs\Pass1.log` bara `Pass1` .

Den här parametern introducerades i PowerShell 6,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LeafBaseSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -LiteralPath

Anger vilka sökvägar som ska delas. Till skillnad från **sökväg** används värdet för **LiteralPath** exakt som det har angetts. Inga tecken tolkas som jokertecken. Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken. Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.

```yaml
Type: System.String[]
Parameter Sets: LiteralPathSet
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Nokvalificerare

Anger att denna cmdlet returnerar sökvägen utan kvalificeraren. För fil systemet eller register leverantörer är kvalificeraren enhet för providerns sökväg, till exempel `C:` eller `HKCU:` . I sökvägen returneras till exempel `C:\Test\Logs\Pass1.log` bara `\Test\Logs\Pass1.log` .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NoQualifierSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### – Överordnad

Anger att denna cmdlet endast returnerar överordnade behållare för objektet eller den behållare som anges av sökvägen. I sökvägen returneras till exempel `C:\Test\Logs\Pass1.log` `C:\Test\Logs` .
Den **överordnade** parametern är standard parametern för delad plats.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ParentSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

Anger vilka sökvägar som ska delas. Jokertecken är tillåtna. Om sökvägen innehåller blank steg, omger du den med citat tecken. Du kan också skicka en sökväg till denna cmdlet.

```yaml
Type: System.String[]
Parameter Sets: ParentSet, LeafSet, LeafBaseSet, ExtensionSet, QualifierSet, NoQualifierSet, IsAbsoluteSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -Kvalificerare

Anger att denna cmdlet bara returnerar kvalificeraren för den angivna sökvägen. För fil systemet eller register leverantörer är kvalificeraren enhet för providerns sökväg, till exempel `C:` eller `HKCU:` .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: QualifierSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Lös

Anger att den här cmdleten visar objekt som refereras till av den resulterande delade sökvägen i stället för att Visa Sök vägs elementen.

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

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. String

Du kan skicka vidare en sträng som innehåller en sökväg till denna cmdlet.

## UTDATA

### System. String, system. Boolean

`Split-Path` returnerar text strängar. När du anger parametern **matcha** `Split-Path` returneras en sträng som beskriver objektets placering. det returnerar inte objekt som representerar objekten, till exempel ett **fileinfo** -eller **RegistryKey** -objekt.

 `Split-Path` Returnerar ett **booleskt** värde när du anger parametern IsAbsolute.

## ANTECKNINGAR

- Parametrarna för delad plats (**kvalificerare**, **överordnad**, **tillägg**, **löv**, **LeafBase** och **noqualifier**) är exklusiva. Du kan bara använda ett i varje kommando.

- Cmdlet: arna som innehåller **sökvägen** Substantiv ( **Sök vägs** -cmdletarna) fungerar med Sök vägs namn och returnerar namnen i ett koncist format som alla PowerShell-leverantörer kan tolka. De är utformade för användning i program och skript där du vill visa hela eller delar av ett Sök vägs namn i ett visst format. Använd dem på det sätt som du använder **logsdirectory**, **Normpath**, **realpath**, **Join** eller andra Sök vägs manipulerare.

- Du kan använda **Sök vägs** -cmdletarna tillsammans med flera providers. Dessa omfattar fil systemet system, register och certifikat.

- `Split-Path` är utformad för att fungera med data som exponeras av vilken provider som helst. Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PSProvider` . Mer information finns i about_Providers.

## RELATERADE LÄNKAR

[Konvertera-sökväg](Convert-Path.md)

[Anslut till sökväg](Join-Path.md)

[Lös-sökväg](Resolve-Path.md)

[Test-sökväg](Test-Path.md)
