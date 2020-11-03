---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/export-modulemember?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-ModuleMember
ms.openlocfilehash: ed08e68279b436ea5a3c040729d70990700ebdfa
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93267471"
---
# Export-ModuleMember

## SAMMANFATTNING
Anger de modul medlemmar som exporteras.

## SYNTAX

```
Export-ModuleMember [[-Function] <String[]>] [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>]
 [<CommonParameters>]
```

## BESKRIVNING

Cmdlet: en **export-ModuleMember** anger de modul medlemmar som exporteras från en skriptfil (. psm1) eller från en dynamisk modul som skapats med hjälp av New-Module cmdlet.
Modul medlemmar är cmdlets, functions, Variables och alias.
Denna cmdlet kan endast användas i en skript fil eller en dynamisk modul.

Om en skript-modul inte innehåller ett **export-ModuleMember-** kommando, exporteras funktionerna och aliasen i modulen skript, men variablerna är inte.
När en skript-modul innehåller **export-ModuleMember-** kommandon, exporteras bara de medlemmar som anges i **export-ModuleMember-** kommandona.
Du kan också använda **export-ModuleMember** för att undertrycka eller exportera medlemmar som-modulen importerar från andra moduler.

Ett **export-ModuleMember-** kommando är valfritt, men det är en bra metod.
Även om kommandot bekräftar standardvärdena, visar det avsikten med modulens författare.

## EXEMPEL

### Exempel 1: exportera funktioner och alias i en skriptbaserad modul

```powershell
Export-ModuleMember -Function * -Alias *
```

Det här kommandot exporterar alla funktioner och alias som definierats i modulen script.

### Exempel 2: exportera vissa alias och funktioner

```powershell
Export-ModuleMember -Function Get-Test, New-Test, Start-Test -Alias gtt, ntt, stt
```

Det här kommandot exporterar tre alias och tre funktioner som definierats i modulen script.

Du kan använda det här kommando formatet för att ange namnen på modul medlemmar.

### Exempel 3: exportera inga medlemmar

```powershell
Export-ModuleMember
```

Det här kommandot anger att inga medlemmar som har definierats i modulen för skript ska exporteras.

Det här kommandot förhindrar att modul medlemmar exporteras, men döljer inte medlemmarna.
Användare kan läsa och kopiera module-medlemmar eller använda anrops operatorn (&) för att anropa modul medlemmar som inte exporteras.

### Exempel 4: exportera en speciell variabel

```powershell
Export-ModuleMember -Variable increment
```

Det här kommandot exporterar endast $increment-variabeln från modulen script.
Inga andra medlemmar exporteras.

Om du vill exportera en variabel, förutom att exportera funktionerna i en modul, måste kommandot **export-ModuleMember** innehålla namnen på alla funktioner och namnet på variabeln.

### Exempel 5: flera export kommandon

```powershell
# From TestModule.psm1
Function New-Test
{
    Write-Output 'I am New-Test function'
}
Export-ModuleMember -Function New-Test

function Validate-Test
{
    Write-Output 'I am Validate-Test function'
}
function Start-Test
{
    Write-Output 'I am Start-Test function'
}
Set-Alias stt Start-Test
Export-ModuleMember -Function Start-Test -Alias stt
```

De här kommandona visar hur flera **export-ModuleMember** -kommandon tolkas i en skriptfil (. psm1)-fil.

Dessa kommandon skapar tre funktioner och ett alias och exporterar sedan två av funktionerna och aliaset.

Utan **export-ModuleMember-** kommandona exporteras alla tre funktionerna och aliaset.
Med **export-ModuleMember-** kommandona exporteras endast funktionerna **New-test** och **Start-test** och STT alias.

### Exempel 6: exportera medlemmar i en dynamisk modul

```powershell
New-Module -Script {function SayHello {"Hello!"}; Set-Alias Hi SayHello; Export-ModuleMember -Alias Hi -Function SayHello}
```

Det här kommandot visar hur du använder Export-ModuleMember i en dynamisk modul som skapas med hjälp av cmdleten **New-module** .

I det här exemplet används **export-ModuleMember** för att exportera både det Hi-alias och **SayHello** -funktionen i den dynamiska modulen.

### Exempel 7: deklarera och exportera en funktion i ett enda kommando

```powershell
# From TestModule.psm1
function Export
{
  param (
    [Parameter(Mandatory=$true)]
    [ValidateSet("function","variable")]
    $Type,
    [Parameter(Mandatory=$true)]
    $Name,
    [Parameter(Mandatory=$true)]
    $Value
    )

    if ($Type -eq "function")
    {
        Set-item "function:script:$Name" $Value
        Export-ModuleMember $Name
    }
    else
    {
    Set-Variable -scope Script $Name $Value
    Export-ModuleMember -variable $Name
    }
}

Export function New-Test {Write-Output 'I am New-Test function'}
function helper {Write-Output 'I am helper function'}

Export variable Interval 0
$Interval = 2
```

Det här exemplet innehåller en funktion med namnet **export** som deklarerar en funktion eller skapar en variabel och skriver sedan ett `Export-ModuleMember` kommando för funktionen eller variabeln.
På så sätt kan du deklarera och exportera en funktion eller variabel i ett enda kommando.

Om du vill använda funktionen **Exportera** inkluderar du den i modulen skript.
Om du vill exportera en funktion skriver du in `Export` före nyckelordet **Function** .

Om du vill exportera en variabel använder du följande format för att deklarera variabeln och ange dess värde:

`Export variable <variable-name> <value>`

Kommandona i exemplet visar rätt format.
I det här exemplet exporteras endast funktionen **New-test** och $Interval variabeln.

## PARAMETRAR

### -Alias

Anger de alias som exporteras från filen script module.
Ange namnen på alias.
Jokertecken är tillåtna.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Cmdlet

Anger de cmdletar som exporteras från filen script module.
Ange cmdlet-namnen.
Jokertecken är tillåtna.

Det går inte att skapa cmdletar i en skript fil, men du kan importera cmdletar från en binär modul till en-modul och exportera dem igen från-modulen.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### – Funktion

Anger de funktioner som exporteras från filen script module.
Ange funktions namnen.
Jokertecken är tillåtna.
Du kan också använda funktions namn strängar för att **Exportera-ModuleMember**.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### – Variabel

Anger de variabler som exporteras från filen script module.
Ange variabel namn, utan dollar tecken.
Jokertecken är tillåtna.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. String

Du kan skicka funktions namn strängar till denna cmdlet.

## UTDATA

### Inget

Denna cmdlet genererar inga utdata.

## ANTECKNINGAR

* Om du vill undanta en medlem från listan över exporterade medlemmar lägger du till ett **export-ModuleMember-** kommando som visar alla andra medlemmar men utelämnar den medlem som du vill undanta.

## RELATERADE LÄNKAR

[Hämta modul](Get-Module.md)

[Importera-modul](Import-Module.md)

[Ta bort modul](Remove-Module.md)
