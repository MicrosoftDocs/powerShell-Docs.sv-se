---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-variable?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Variable
ms.openlocfilehash: 6db5d6693e7e42b5563baa3dbaebb495f97f53a6
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264914"
---
# New-Variable

## SAMMANFATTNING
Skapar en ny variabel.

## SYNTAX

```
New-Variable [-Name] <String> [[-Value] <Object>] [-Description <String>] [-Option <ScopedItemOptions>]
 [-Visibility <SessionStateEntryVisibility>] [-Force] [-PassThru] [-Scope <String>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## BESKRIVNING
Cmdleten **New-Variable** skapar en ny variabel i Windows PowerShell.
Du kan tilldela ett värde till variabeln när du skapar den, eller tilldela eller ändra värdet när det har skapats.

Du kan använda parametrarna för **New-Variable** för att ange egenskaperna för variabeln, ange en variabels omfång och avgöra om variablerna är offentliga eller privata.

Normalt skapar du en ny variabel genom att skriva variabel namnet och dess värde, till exempel `$Var = 3` , men du kan använda cmdleten **New-Variable** för att använda dess parametrar.

## EXEMPEL

### Exempel 1: skapa en variabel

```
PS C:\> New-Variable days
```

Det här kommandot skapar en ny variabel med namnet dagar.
Du behöver inte ange *namn* parametern.

### Exempel 2: skapa en variabel och tilldela den ett värde

```
PS C:\> New-Variable -Name "zipcode" -Value 98033
```

Det här kommandot skapar en variabel med namnet Postummer och tilldelar den värdet 98033.

### Exempel 3: skapa en variabel med alternativet ReadOnly

```
PS C:\> New-Variable -Name Max -Value 256 -Option ReadOnly
PS C:\> New-Variable -Name max -Value 1024

New-Variable : A variable with name 'max' already exists.
At line:1 char:1
+ New-Variable -Name max -Value 1024
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ResourceExists: (max:String) [New-Variable], SessionStateException
    + FullyQualifiedErrorId : VariableAlreadyExists,Microsoft.PowerShell.Commands.NewVariableCommand

PS C:\> New-Variable -Name max -Value 1024 -Force
```

Det här exemplet visar hur du använder alternativet ReadOnly för **New-Variable** för att skydda en variabel från att skrivas över.

Det första kommandot skapar en ny variabel med namnet max och anger dess värde till 256.
Den använder *alternativ* parametern med värdet ReadOnly.

Det andra kommandot försöker skapa en andra variabel med samma namn.
Det här kommandot returnerar ett fel eftersom det skrivskyddade alternativet är inställt på variabeln.

Det tredje kommandot använder *Force* -parametern för att åsidosätta det skrivskyddade skyddet på variabeln.
I det här fallet slutförs kommandot för att skapa en ny variabel med samma namn.

### Exempel 4: skapa en privat variabel

```
PS C:\> New-Variable -Name counter -Visibility Private

#Effect of private variable in a module.

PS C:\> Get-Variable c*

Name                           Value
----                           -----
Culture                        en-US
ConsoleFileName
ConfirmPreference              High
CommandLineParameters          {}

PS C:\> $counter
"Cannot access the variable '$counter' because it is a private variable"
At line:1 char:1
+ $counter
+ ~~~~~~~~
    + CategoryInfo          : PermissionDenied: (counter:String) [], SessionStateException
    + FullyQualifiedErrorId : VariableIsPrivate

PS C:\> Get-Counter
Name         Value
----         -----
Counter1     3.1415
...
```

Det här kommandot visar beteendet för en privat variabel i en modul.
Modulen innehåller Get-Counter-cmdleten, som har en privat variabel med namnet Counter.
Kommandot använder parametern *visibility* med värdet Private för att skapa variabeln.

Exempel resultatet visar beteendet för en privat variabel.
Användaren som har läst in modulen kan inte Visa eller ändra värdet för Counter-variabeln, men räknar variabeln kan läsas och ändras av kommandona i modulen.

### Exempel 5: skapa en variabel med ett blank steg

```
PS C:\> New-Variable -Name 'with space' -Value 'abc123xyz'

PS C:\> Get-Variable -Name 'with space'

Name                           Value
----                           -----
with space                     abc123xyz

PS C:\> ${with space}
abc123xyz
```

Det här kommandot visar att variabler med blank steg kan skapas.
Du kan komma åt variablerna med hjälp av cmdleten **Get-Variable** eller direkt genom att begränsa en variabel med klammerparenteser.

## PARAMETRAR

### -Beskrivning
Anger en beskrivning av variabeln.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force
Anger att cmdleten skapar en variabel med samma namn som en befintlig skrivskyddad variabel.

Som standard kan du skriva över en variabel om inte variabeln har ett alternativ värde av ReadOnly eller konstant.
Mer information finns i *alternativ* parametern.

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

### -Name
Anger ett namn för den nya variabeln.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Alternativ
Anger värdet för egenskapen **Options** för variabeln. De acceptabla värdena för den här parametern är:

- Inga.
Anger inga alternativ.
(Ingen är standard.)
- ReadOnly.
Kan tas bort.
Kan inte ändras, med undantag för parametern *Force* .
- Personligt.
Variabeln är endast tillgänglig i det aktuella omfånget.
- AllScope.
Variabeln kopieras till alla nya omfattningar som skapas.
- Konstant.
Kan inte tas bort eller ändras.
Konstant är bara giltig när du skapar en variabel.
Det går inte att ändra alternativen för en befintlig variabel till konstant.

Om du vill se egenskapen **alternativ** för alla variabler i sessionen skriver du `Get-Variable | Format-Table -Property name, options -autosize` .

```yaml
Type: System.Management.Automation.ScopedItemOptions
Parameter Sets: (All)
Aliases:
Accepted values: None, ReadOnly, Constant, Private, AllScope, Unspecified

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – PassThru
Returnerar ett objekt som representerar det objekt som du arbetar med.
Som standard genererar denna cmdlet inga utdata.

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

### – Omfattning
Anger omfånget för den nya variabeln.
De acceptabla värdena för den här parametern är:

- EAN.
Variabler som skapas i det globala omfånget är tillgängliga överallt i en PowerShell-process.
- Inställningar.
Det lokala omfånget refererar till det aktuella omfånget. Detta kan vara vilken omfattning som helst, beroende på kontexten.
- Över.
Variabler som skapas i skript omfånget är endast tillgängliga inom skript filen eller modulen de skapas i.
- Personligt.
Det går inte att komma åt variabler som har skapats i det privata området utanför den omfattning som de finns i.
Du kan använda privat omfattning för att skapa en privat version av ett objekt med samma namn i ett annat omfång.
- Ett tal i förhållande till det aktuella omfånget (0 till antalet omfattningar, där 0 är det aktuella omfånget, 1 är överordnat, 2 överordnat till det överordnade omfånget osv.).
Det går inte att använda negativa tal.

Lokalt är standard omfånget när omfångs parametern inte anges.

Mer information finns i about_Scopes.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Värde
Anger det inledande värdet för variabeln.

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Synlighet
Bestämmer om variabeln är synlig utanför den session där den skapades.
Den här parametern är avsedd för användning i skript och kommandon som skickas till andra användare.
De acceptabla värdena för den här parametern är:

- Folkhälsan.
Variabeln är synlig.
(Offentlig är standard.)
- Personligt.
Variabeln är inte synlig.

När en variabel är privat visas den inte i listor med variabler, t. ex. de som returneras av Get-Variable eller som visas i variabeln: enhet.
Kommandon för att läsa eller ändra värdet för en privat variabel returnerar ett fel.
Användaren kan dock köra kommandon som använder en privat variabel om kommandona skrevs i den session där variabeln definierades.

```yaml
Type: System.Management.Automation.SessionStateEntryVisibility
Parameter Sets: (All)
Aliases:
Accepted values: Public, Private

Required: False
Position: Named
Default value: None
Accept pipeline input: False
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

### System. Object
Du kan skicka vidare ett värde till **New-Variable**.

## UTDATA

### Ingen eller system. Management. Automation. PSVariable
När du använder parametern *Passthru* genererar **New-variabel** ett **system. Management. Automation. PSVariable** -objekt som representerar den nya variabeln.
Annars genererar denna cmdlet inga utdata.

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Clear-Variable](Clear-Variable.md)

[Get-Variable](Get-Variable.md)

[Ta bort variabel](Remove-Variable.md)

[Set-Variable](Set-Variable.md)
