---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/12/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-location?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Location
ms.openlocfilehash: 235c775e2da4188213f4eb35612c469947b5e2fc
ms.sourcegitcommit: fe1e20f8523e3663d68546093aaf3670182337b8
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/14/2020
ms.locfileid: "93269193"
---
# Get-Location

## SAMMANFATTNING
Hämtar information om den aktuella arbets platsen eller en plats stack.

## SYNTAX

### Plats (standard)

```
Get-Location [-PSProvider <String[]>] [-PSDrive <String[]>] [<CommonParameters>]
```

### Stack

```
Get-Location [-Stack] [-StackName <String[]>] [<CommonParameters>]
```

## BESKRIVNING

`Get-Location`Cmdleten hämtar ett objekt som representerar den aktuella katalogen, ungefär som utskrifts arbets katalog kommandot (PWD).

När du flyttar mellan PowerShell-enheter behåller PowerShell din plats i varje enhet. Du kan använda den här cmdleten för att hitta din plats på varje enhet.

Du kan använda den här cmdleten för att hämta den aktuella katalogen vid körning och använda den i funktioner och skript, till exempel i en funktion som visar den aktuella katalogen i PowerShell-prompten.

Du kan också använda den här cmdleten för att Visa platserna i en plats stack. Mer information finns i anteckningarna och beskrivningarna av parametrarna **stack** och **StackName** .

## EXEMPEL

### Exempel 1: Visa din aktuella enhets plats

Det här kommandot visar din plats i den aktuella PowerShell-enheten.

```powershell
PS C:\Windows> Get-Location
```

```Output
Path
----
C:\Windows
```

Om du till exempel befinner dig i `Windows` `C:` enhetens katalog visas sökvägen till den katalogen.

### Exempel 2: Visa din aktuella plats för olika enheter

Det här exemplet visar hur `Get-Location` du använder för att visa din aktuella plats i olika PowerShell-enheter. `Set-Location` används för att ändra platsen till flera olika sökvägar på olika PSDrives.

```powershell
PS C:\> Set-Location C:\Windows
PS C:\Windows> Set-Location HKLM:\Software\Microsoft
PS HKLM:\Software\Microsoft> Set-Location "HKCU:\Control Panel\Input Method"
PS HKCU:\Control Panel\Input Method> Get-Location -PSDrive C

Path
----
C:\Windows

PS HKCU:\Control Panel\Input Method> Get-Location -PSDrive HKLM

Path
----
HKLM:\Software\Microsoft

PS HKCU:\Control Panel\Input Method> Set-Location C:
PS C:\Windows> Get-Location -PSProvider Registry

Path
----
HKCU:\Control Panel\Input Method
```

### Exempel 3: Hämta platser med hjälp av stackar

Det här exemplet visar hur du använder **stack** -och **StackName** -parametrarna för `Get-Location` för att visa en lista över platserna i den aktuella platsens stack och alternativa plats stackar.

`Push-Location`Cmdleten används för att ändra till tre olika platser. Den tredje push-enheten använder ett annat stack namn. **Stack** -parametern för `Get-Location` visar innehållet i standard stacken. Parametern **StackName** i `Get-Location` visar innehållet i stacken med namnet `Stack2` .

```powershell
PS C:\> Push-Location C:\Windows
PS C:\Windows>Push-Location System32
PS C:\Windows\System32>Push-Location WindowsPowerShell -StackName Stack2
C:\Windows\System32\WindowsPowerShell>Get-Location -Stack

Path
----
C:\Windows
C:\

C:\Windows\System32\WindowsPowerShell>Get-Location -StackName Stack2

Path
----
C:\Windows\System32
```

### Exempel 4: anpassa PowerShell-prompten

Det här exemplet visar hur du anpassar PowerShell-prompten.

```powershell
PS C:\>
function prompt { 'PowerShell: ' + (Get-Location) + '> '}
PowerShell: C:\>
```

Funktionen som definierar prompten innehåller ett `Get-Location` -kommando som körs när meddelandet visas i-konsolen.

Formatet för standard-PowerShell-prompten definieras av en särskild funktion med namnet `prompt` . Du kan ändra prompten i-konsolen genom att skapa en ny funktion med namnet `prompt` .

Skriv följande kommando för att se den aktuella prompt-funktionen: `Get-Content Function:\prompt`

## PARAMETRAR

### -PSDrive

Hämtar den aktuella platsen i den angivna PowerShell-enheten.

Om du till exempel är i `Cert:` enheten kan du använda den här parametern för att hitta din aktuella plats i `C:` enheten.

```yaml
Type: System.String[]
Parameter Sets: Location
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PSProvider

Hämtar den aktuella platsen i enheten som stöds av den angivna PowerShell-providern.
Om den angivna providern har stöd för mer än en enhet, returnerar denna cmdlet platsen på den senast använda enheten.

Om du till exempel är i `C:` enheten kan du använda den här parametern för att hitta din aktuella plats i diskarna i PowerShell- **registerposten** .

```yaml
Type: System.String[]
Parameter Sets: Location
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Stack

Anger att den här cmdleten visar de platser som lagts till i den aktuella plats stacken. Du kan lägga till platser i stackar med hjälp av `Push-Location` cmdleten.

Om du vill visa platserna i en annan plats stack använder du parametern **StackName** . Information om plats stackar finns i [anteckningarna](#notes).

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Stack
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -StackName

Anger, som en sträng mat ris, stacken för den namngivna platsen. Ange ett eller flera plats stack namn.

Om du vill visa platserna i den aktuella plats stacken använder du **stack** -parametern. Använd cmdleten för att skapa en plats stack för den aktuella plats stacken `Set-Location` .

Denna cmdlet kan inte Visa platserna i den namnlösa standardstacken om den inte är den aktuella stacken.

```yaml
Type: System.String[]
Parameter Sets: Stack
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Inget

Du kan inte skicka pipe-ininformation till denna cmdlet.

## UTDATA

### System. Management. Automation. PathInfo eller system. Management. Automation. PathInfoStack

Om du använder **stack** -eller **StackName** -parametrarna returnerar denna cmdlet ett **PathInfoStack** -objekt. Annars returnerar den ett **PathInfo** -objekt.

## ANTECKNINGAR

PowerShell stöder flera körnings utrymmen per process. Varje körnings utrymme har sin egen _aktuella katalog_.
Detta är inte samma som `[System.Environment]::CurrentDirectory` . Det här problemet kan vara ett problem när du anropar .NET-API: er eller kör ursprungliga program utan att ange explicita katalog Sök vägar.
`Get-Location`Cmdleten returnerar den aktuella katalogen för den aktuella PowerShell-körnings utrymme.

Denna cmdlet är utformad för att fungera med data som exponeras av vilken provider som helst. Om du vill visa en lista över providers i din session skriver du `Get-PSProvider` . Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).

Hur **PSProvider** -, **PSDrive** -, **stack** -och **StackName** -parametrarna interagerar beror på providern. Vissa kombinationer resulterar i fel, t. ex. att ange både en enhet och en provider som inte visar den enheten. Om inga parametrar anges returnerar denna cmdlet **PathInfo** -objektet för den provider som innehåller den aktuella arbets platsen.

En stack är en sista ingångs punkt som endast det objekt som lagts till senast har åtkomst till. Du lägger till objekt i en stack i den ordning som du använder dem och hämtar dem sedan för användning i omvänd ordning. Med PowerShell kan du lagra leverantörs platser i plats stackar. PowerShell skapar en namnlös standard plats stack och du kan skapa flera namngivna plats stackar. Om du inte anger något stack namn använder PowerShell den aktuella plats stacken. Som standard är den namnlösa standard platsen den aktuella plats stacken, men du kan använda `Set-Location` cmdleten för att ändra den aktuella plats stacken.

Om du vill hantera plats stackar använder du PowerShell `*-Location` -cmdletarna enligt följande.

- Om du vill lägga till en plats i en plats stack använder du `Push-Location` cmdleten.

- Använd cmdleten för att hämta en plats från en plats stack `Pop-Location` .

- Om du vill visa platserna i den aktuella platsens stack, använder du cmdlet-parametern **stack** `Get-Location` . Om du vill visa platserna i en namngiven plats stack använder du parametern **StackName** för `Get-Location` cmdleten.

- Om du vill skapa en ny plats stack använder du parametern **StackName** för `Push-Location` cmdleten.
  Om du anger en stack som inte finns `Push-Location` skapar stacken.

- Om du vill skapa en plats stack för den aktuella plats stacken använder du parametern **StackName** för `Set-Location` cmdleten.

Den namnlösa standard plats stacken är endast tillgänglig när den är den aktuella plats stacken.
Om du skapar en namngiven plats stack för den aktuella plats stacken kan du inte längre använda `Push-Location` `Pop-Location` cmdletarna eller för att lägga till eller hämta objekt från standard stacken eller använda denna cmdlet för att Visa platserna i den namnlösa stacken. Om du vill göra den namnlösa stacken till den aktuella stacken använder du parametern **StackName** för `Set-Location` cmdleten med värdet `$null` eller en tom sträng ( `""` ).

## RELATERADE LÄNKAR

[Pop-location](Pop-Location.md)

[Push-plats](Push-Location.md)

[Ange plats](Set-Location.md)
