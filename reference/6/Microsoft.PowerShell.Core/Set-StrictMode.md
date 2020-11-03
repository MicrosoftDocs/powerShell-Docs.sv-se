---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/09/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/set-strictmode?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-StrictMode
ms.openlocfilehash: d28ff57c864847658072c9b7a1979b2b513c04b3
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93267417"
---
# Set-StrictMode

## SAMMANFATTNING
Skapar och tillämpar kod regler i uttryck, skript och skript block.

## SYNTAX

### Version (standard)

```
Set-StrictMode -Version <Version> [<CommonParameters>]
```

### Av

```
Set-StrictMode [-Off] [<CommonParameters>]
```

## BESKRIVNING

`Set-StrictMode`Cmdleten konfigurerar strikt läge för det aktuella omfånget och alla underordnade scope och aktiverar och inaktiverar den. När strikt läge är på genererar PowerShell ett avslutande fel när innehållet i ett uttryck, skript eller skript block strider mot grundläggande kodnings regler för bästa praxis.

Använd **versions** parametern för att avgöra vilka kodnings regler som tillämpas.

`Set-PSDebug -Strict` cmdlet aktiverar strikt läge för det globala omfånget. `Set-StrictMode` påverkar endast det aktuella omfånget och dess underordnade omfång. Därför kan du använda den i ett skript eller en funktion för att åsidosätta inställningen som ärvts från det globala omfånget.

När `Set-StrictMode` är inaktiverat har PowerShell följande beteenden:

- Oinitierade variabler antas ha värdet 0 (noll) eller `$Null` , beroende på typ
- Referenser till obefintliga egenskaper returnerar `$Null`
- Resultatet av felaktig syntax i funktionen varierar med fel villkoren
- Försök att hämta ett värde med ett ogiltigt index i en matris returneras `$Null`

## EXEMPEL

### Exempel 1: Aktivera strikt läge som version 1,0

```powershell
# Strict mode is off by default.
$a -gt 5
```

```Output
False
```

```powershell
Set-StrictMode -Version 1.0
$a -gt 5
```

```Output
The variable $a cannot be retrieved because it has not been set yet.

At line:1 char:3
+ $a <<<<  -gt 5
+ CategoryInfo          : InvalidOperation: (a:Token) [], RuntimeException
+ FullyQualifiedErrorId : VariableIsUndefined
```

Med strikt läge inställt på version 1,0, försöker referera till variabler som inte initieras.

### Exempel 2: Aktivera strikt läge som version 2,0

```powershell
# Strict mode is off by default.
function add ($a, $b) {
    '$a = ' + $a
    '$b = ' + $b
    '$a+$b = ' + ($a + $b)
}
add 3 4
```

```Output
$a = 3
$b = 4
$a+$b = 7
```

```powershell
add(3,4)
```

```Output
$a = 3 4
$b =
$a+$b = 3 4
```

```powershell
Set-StrictMode -Version 2.0
add(3,4)
```

```Output
The function or command was called like a method. Parameters should be separated by spaces,
as described in 'Get-Help about_Parameter.'
At line:1 char:4
+ add <<<< (3,4)
+ CategoryInfo          : InvalidOperation: (:) [], RuntimeException
+ FullyQualifiedErrorId : StrictModeFunctionCallWithParens
```

```powershell
Set-StrictMode -Off
$string = "This is a string."
$string.Month -eq $null
```

```Output
True
```

```powershell
Set-StrictMode -Version 2.0
$string = "This is a string."
$string.Month -eq $null
```

```Output
Property 'Month' cannot be found on this object; make sure it exists.
At line:1 char:9
+ $string. <<<< month
+ CategoryInfo          : InvalidOperation: (.:OperatorToken) [], RuntimeException
+ FullyQualifiedErrorId : PropertyNotFoundStrict
```

Det här kommandot aktiverar strikt läge på och anger det till version 2,0. Det innebär att PowerShell returnerar ett fel om du använder Method syntax, som använder parenteser och kommatecken, för ett funktions anrop eller referera till oinitierade variabler eller obefintliga egenskaper.

Exempel resultatet visar effekterna av strikt läge för version 2,0.

Utan version 2,0 strikt läge tolkas "(3, 4)"-värdet som ett enskilt Array-objekt som inget läggs till i. Genom att använda version 2,0 strikt läge tolkas det korrekt som felaktig syntax för att skicka två värden.

Utan version 2,0 returnerar referensen till den icke-befintliga **månads** egenskapen för en sträng `$Null` . Genom att använda version 2,0 tolkas den korrekt som ett referens fel.

### Exempel 3: Aktivera strikt läge som version 3,0

Med strikt läge inställt på **av** , ogiltigt eller utanför intervall index resulterar resultatet av null-värden.

```powershell
# Strict mode is off by default.
$a = @(1)
$a[2] -eq $null
$a['abc'] -eq $null
```

```Output
True
True
```

```powershell
Set-StrictMode -Version 3
$a = @(1)
$a[2] -eq $null
$a['abc'] -eq $null
```

```Output
Index was outside the bounds of the array.
At line:1 char:1
+ $a[2] -eq $null
+ ~~~~~~~~~~~~~~~
    + CategoryInfo          : OperationStopped: (:) [], IndexOutOfRangeException
    + FullyQualifiedErrorId : System.IndexOutOfRangeException

Cannot convert value "abc" to type "System.Int32". Error: "Input string was not in a correct format."
At line:1 char:1
+ $a['abc'] -eq $null
+ ~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [], RuntimeException
    + FullyQualifiedErrorId : InvalidCastFromStringToInteger
```

Med strikt läge inställt på version 3 eller högre, är ogiltiga eller utanför gräns index resulterar i fel.

## PARAMETRAR

### -Av

Anger att den här cmdleten inaktiverar strikt läge för det aktuella omfånget och alla underordnade scope.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Off
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Version

Anger de villkor som orsakar ett fel i strikt läge. Den här parametern accepterar ett giltigt PowerShell-versions nummer. Alla tal som är större än 3 behandlas som **senaste**.

De effektiva värdena för den här parametern är:

- 1,0
  - Förhindrar referenser till oinitierade variabler, förutom oinitierade variabler i strängar.
- 2.0
  - Förhindrar referenser till oinitierade variabler. Detta inkluderar oinitierade variabler i strängar.
  - Förhindrar referenser till obefintliga egenskaper för ett objekt.
  - Förhindrar funktions anrop som använder syntaxen för att anropa metoder.
- 3.0
  - Förhindrar referenser till oinitierade variabler. Detta inkluderar oinitierade variabler i strängar.
  - Förhindrar referenser till obefintliga egenskaper för ett objekt.
  - Förhindrar funktions anrop som använder syntaxen för att anropa metoder.
  - Förhindra att matriser utanför gränser eller inte går att matcha.
- Senast
  - Väljer den senaste versionen som är tillgänglig. Den senaste versionen är den mest strikta. Använd det här värdet för att kontrol lera att skript använder den striktaste tillgängliga versionen, även när nya versioner läggs till i PowerShell.

> [!CAUTION]
> Använda en **version** av de **senaste** i skripten. Betydelsen av **senaste** kan ändra i nya versioner av PowerShell. Ett skript som skrivits för en äldre version av PowerShell som använder omfattas därför av `Set-StrictMode -Version Latest` mer restriktiva regler när de körs i en senare version av PowerShell.

```yaml
Type: System.Version
Parameter Sets: Version
Aliases: v

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Inget

Du kan inte skicka pipe-ininformation till denna cmdlet.

## UTDATA

### Inget

Denna cmdlet returnerar inga utdata.

## ANTECKNINGAR

`Set-StrictMode` är endast effektivt i det omfång där det har angetts och i dess underordnade omfång. Mer information om omfång i PowerShell finns [about_Scopes](about/about_Scopes.md).

## RELATERADE LÄNKAR

[Set-PSDebug](Set-PSDebug.md)