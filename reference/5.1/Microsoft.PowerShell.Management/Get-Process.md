---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-process?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Process
ms.openlocfilehash: d1a576ce9c718561718bac5fee065983a057d458
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388305"
---
# Get-Process

## SAMMANFATTNING
Hämtar de processer som körs på den lokala datorn eller en fjärrdator.

## SYNTAX

### Namn (standard)

```
Get-Process [[-Name] <String[]>] [-ComputerName <String[]>] [-Module] [-FileVersionInfo] [<CommonParameters>]
```

### NameWithUserName

```
Get-Process [[-Name] <String[]>] [-IncludeUserName] [<CommonParameters>]
```

### IdWithUserName

```
Get-Process -Id <Int32[]> [-IncludeUserName] [<CommonParameters>]
```

### Id

```
Get-Process -Id <Int32[]> [-ComputerName <String[]>] [-Module] [-FileVersionInfo] [<CommonParameters>]
```

### InputObjectWithUserName

```
Get-Process -InputObject <Process[]> [-IncludeUserName] [<CommonParameters>]
```

### InputObject

```
Get-Process -InputObject <Process[]> [-ComputerName <String[]>] [-Module] [-FileVersionInfo]
 [<CommonParameters>]
```

## BESKRIVNING

`Get-Process`Cmdleten hämtar processerna på en lokal dator eller fjärrdator.

Utan parametrar hämtar denna cmdlet alla processer på den lokala datorn. Du kan också ange en viss process efter process namn eller process-ID (PID) eller skicka ett process objekt via pipelinen till denna cmdlet.

Som standard returnerar denna cmdlet ett process objekt med detaljerad information om processen och stöder metoder som gör att du kan starta och stoppa processen. Du kan också använda parametrarna för `Get-Process` cmdleten för att hämta fil versions information för programmet som körs i processen och för att hämta de moduler som processen läste in.

## EXEMPEL

### Exempel 1: Hämta en lista över alla aktiva processer på den lokala datorn

```powershell
Get-Process
```

Det här kommandot hämtar en lista över alla aktiva processer som körs på den lokala datorn. En definition av varje kolumn finns i avsnittet om [anteckningar](#notes) .

### Exempel 2: Hämta alla tillgängliga data om en eller flera processer

```powershell
Get-Process winword, explorer | Format-List *
```

Det här kommandot hämtar alla tillgängliga data om Winword-och Utforskaren-processer på datorn. Den använder **Name** -parametern för att ange processerna, men utelämnar det valfria parameter namnet. Pipeline-operatorn `|` skickar data till `Format-List` cmdleten, som visar alla tillgängliga egenskaper `*` för process objekt i Winword och Utforskaren.

Du kan också identifiera processerna efter process-ID. Till exempel `Get-Process -Id 664, 2060` .

### Exempel 3: Hämta alla processer med en arbets mängd som är större än en angiven storlek

```powershell
Get-Process | Where-Object {$_.WorkingSet -gt 20000000}
```

Det här kommandot hämtar alla processer som har en arbets mängd som är större än 20 MB. Den använder `Get-Process` cmdleten för att hämta alla processer som körs. Pipeline-operatorn `|` överför process objekt till `Where-Object` cmdleten, som endast väljer objektet med ett värde som är större än 20 000 000 byte för den **aktiva** egenskapen.

Den **aktiva** processen är en av många egenskaper för process objekt. Om du vill se alla egenskaper skriver du `Get-Process | Get-Member` . Som standard är värdena för alla mängd egenskaper i byte, även om standard visningen visar dem i kilobyte och megabyte.

### Exempel 4: Visa en lista över processer på datorn i grupper baserat på prioritet

```powershell
$A = Get-Process
$A | Get-Process | Format-Table -View priority
```

De här kommandona visar processerna på datorn i grupper baserat på deras prioritets klass. Det första kommandot hämtar alla processer på datorn och lagrar dem sedan i `$A` variabeln.

Det andra kommandot rör objektet **process** som lagras i `$A` variabeln till `Get-Process` cmdleten, sedan till `Format-Table` cmdleten, som formaterar processerna med hjälp av vyn **prioritet** .

Vyn **prioritet** , och andra vyer, definieras i PS1XML-format-filer i PowerShell-arbetskatalogen ( `$pshome` ).

### Exempel 5: Lägg till en egenskap till standard visningen Get-Process utdata

```powershell
Get-Process powershell -ComputerName S1, localhost | Format-Table `
    @{Label = "NPM(K)"; Expression = {[int]($_.NPM / 1024)}},
    @{Label = "PM(K)"; Expression = {[int]($_.PM / 1024)}},
    @{Label = "WS(K)"; Expression = {[int]($_.WS / 1024)}},
    @{Label = "VM(M)"; Expression = {[int]($_.VM / 1MB)}},
    @{Label = "CPU(s)"; Expression = {if ($_.CPU) {$_.CPU.ToString("N")}}},
    Id, MachineName, ProcessName -AutoSize
```

```Output
NPM(K) PM(K) WS(K) VM(M) CPU(s)   Id MachineName ProcessName
------ ----- ----- ----- ------   -- ----------- -----------
     6 23500 31340   142 1.70   1980 S1          powershell
     6 23500 31348   142 2.75   4016 S1          powershell
    27 54572 54520   576 5.52   4428 localhost   powershell
```

I det här exemplet hämtas processer från den lokala datorn och en fjärrdator (S1). De hämtade processerna är skickas till `Format-Table` kommandot som lägger till egenskapen **MachineName** i `Get-Process` standardutdata-visningen.

### Exempel 6: Hämta versions information för en process

```powershell
Get-Process powershell -FileVersionInfo
```

```Output
ProductVersion   FileVersion      FileName
--------------   -----------      --------
6.1.6713.1       6.1.6713.1 (f... C:\WINDOWS\system32\WindowsPowerShell\v1.0\powershell.exe
```

Detta kommando använder parametern **FileVersionInfo** för att hämta versions information för den powershell.exe-fil som är huvud-till-modul för PowerShell-processen.

Om du vill köra det här kommandot med processer som du inte äger i Windows Vista och senare versioner av Windows, måste du öppna PowerShell med alternativet Kör som administratör.

### Exempel 7: Hämta moduler som lästs in med den angivna processen

```powershell
Get-Process SQL* -Module
```

Det här kommandot använder **modulen modul** för att hämta de moduler som har lästs in av processen.
Det här kommandot hämtar modulerna för de processer som har namn som börjar med SQL.

Om du vill köra det här kommandot på Windows Vista och senare versioner av Windows med processer som du inte äger måste du starta PowerShell med alternativet Kör som administratör.

### Exempel 8: hitta ägaren till en process

```powershell
Get-Process pwsh -IncludeUserName
```

```Output
Handles      WS(K)   CPU(s)     Id UserName            ProcessName
-------      -----   ------     -- --------            -----------
    782     132080     2.08   2188 DOMAIN01\user01     powershell
```

```powershell
$p = Get-WmiObject Win32_Process -Filter "name='powershell.exe'"
$p.GetOwner()
```

```Output
__GENUS          : 2
__CLASS          : __PARAMETERS
__SUPERCLASS     :
__DYNASTY        : __PARAMETERS
__RELPATH        :
__PROPERTY_COUNT : 3
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
Domain           : DOMAIN01
ReturnValue      : 0
User             : user01
```

Det första kommandot visar hur du hittar en processs ägare. **IncludeUserName** -parametern kräver förhöjda användar rättigheter (kör som administratör). Utdata visar att ägaren är Domain01\user01.

Det andra och tredje kommandot är ett annat sätt att hitta ägaren till en process.

Det andra kommandot använder `Get-WmiObject` för att hämta PowerShell-processen.
Den sparar den i `$p` variabeln.

Det tredje kommandot använder metoden GetOwner för att hämta processens ägare i `$p` . Utdata visar att ägaren är Domain01\user01.

### Exempel 9: Använd en automatisk variabel för att identifiera processen som är värd för den aktuella sessionen

```powershell
Get-Process powershell
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
308      26        52308      61780   567     3.18   5632 powershell
377      26        62676      63384   575     3.88   5888 powershell
```

```powershell
Get-Process -Id $PID
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
396      26        56488      57236   575     3.90   5888 powershell
```

De här kommandona visar hur du använder den `$PID` automatiska variabeln för att identifiera den process som är värd för den aktuella PowerShell-sessionen. Du kan använda den här metoden för att skilja värd processen från andra PowerShell-processer som du kanske vill stoppa eller stänga.

Det första kommandot hämtar alla PowerShell-processer i den aktuella sessionen.

Det andra kommandot hämtar PowerShell-processen som är värd för den aktuella sessionen.

### Exempel 10: Hämta alla processer som har en huvud fönster rubrik och visa dem i en tabell

```powershell
Get-Process | Where-Object {$_.mainWindowTitle} | Format-Table Id, Name, mainWindowtitle -AutoSize
```

Det här kommandot hämtar alla processer som har en huvud fönster rubrik och visar dem i en tabell med process-ID och process namnet.

Egenskapen **mainWindowTitle** är bara en av många användbara egenskaper för det **process** objekt som `Get-Process` returnerar. Om du vill visa alla egenskaper, rör du resultatet av ett `Get-Process` kommando till `Get-Member` cmdleten `Get-Process | Get-Member` .

## PARAMETRAR

### -ComputerName

Anger de datorer för vilka denna cmdlet hämtar aktiva processer. Standard är den lokala datorn.

Ange NetBIOS-namn, en IP-adress eller ett fullständigt kvalificerat domän namn (FQDN) för en eller flera datorer. Om du vill ange den lokala datorn skriver du datorns namn, en punkt (.) eller localhost.

Den här parametern är inte beroende av Windows PowerShell-fjärrkommunikation. Du kan använda parametern **computername** för denna cmdlet även om datorn inte är konfigurerad för att köra fjärrkommandon.

```yaml
Type: System.String[]
Parameter Sets: Name, Id, InputObject
Aliases: Cn

Required: False
Position: Named
Default value: Local computer
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -FileVersionInfo

Anger att denna cmdlet hämtar fil versions information för programmet som körs i processen.

I Windows Vista och senare versioner av Windows måste du öppna PowerShell med alternativet Kör som administratör för att kunna använda den här parametern på processer som du inte äger.

Du kan inte använda parametrarna **FileVersionInfo** och **computername** för `Get-Process` cmdleten i samma kommando.

Använd cmdleten för att hämta fil versions information för en process på en fjärrdator `Invoke-Command` .

Att använda den här parametern motsvarar att hämta egenskapen **MainModule. FileVersionInfo** för varje process objekt. När du använder den här parametern `Get-Process` returnerar en **FileVersionInfo** Object **system. Diagnostics. FileVersionInfo** , inte ett process objekt. Därför kan du inte skicka kommandots utdata till en cmdlet som förväntar sig ett process objekt, till exempel `Stop-Process` .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Name, Id, InputObject
Aliases: FV, FVI

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -ID

Anger en eller flera processer efter process-ID (PID). Använd kommatecken för att avgränsa ID: n för att ange flera ID: n. Om du vill hitta ett process-ID skriver du `Get-Process` .

```yaml
Type: System.Int32[]
Parameter Sets: IdWithUserName, Id
Aliases: PID

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -IncludeUserName

Anger **att objektets** username-värde returneras med kommandots resultat.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NameWithUserName, IdWithUserName, InputObjectWithUserName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – InputObject

Anger ett eller flera process objekt. Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten.

```yaml
Type: System.Diagnostics.Process[]
Parameter Sets: InputObjectWithUserName, InputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### – Modul

Anger att denna cmdlet hämtar de moduler som har lästs in av processerna.

I Windows Vista och senare versioner av Windows måste du öppna PowerShell med alternativet **Kör som administratör** för att kunna använda den här parametern på processer som du inte äger.

Använd cmdleten för att hämta moduler som har lästs in av en process på en fjärrdator `Invoke-Command` .

Den här parametern motsvarar att hämta egenskapen **modules** för varje process objekt. När du använder den här parametern returnerar denna cmdlet en **ProcessModule** Object **system. Diagnostics. ProcessModule** , inte ett process objekt. Därför kan du inte skicka kommandots utdata till en cmdlet som förväntar sig ett process objekt, till exempel `Stop-Process` .

När du använder både *modulen* och **FileVersionInfo** -parametrarna i samma kommando, returnerar denna cmdlet ett **FileVersionInfo** -objekt med information om fil versionen för alla moduler.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Name, Id, InputObject
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Anger en eller flera processer efter process namn. Du kan ange flera process namn (avgränsade med kommatecken) och använda jokertecken. Parameter namnet ("namn") är valfritt.

```yaml
Type: System.String[]
Parameter Sets: Name, NameWithUserName
Aliases: ProcessName

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## INDATA

### System. Diagnostics. process

Du kan skicka vidare ett process objekt till denna cmdlet.

## UTDATA

### System. Diagnostics. process, system. Diagnostics. FileVersionInfo, system. Diagnostics. ProcessModule

Som standard returnerar denna cmdlet ett **system. Diagnostics. process** -objekt. Om du använder parametern **FileVersionInfo** returneras ett **system. Diagnostics. FileVersionInfo** -objekt. Om du använder parametern **modul** , utan parametern **FileVersionInfo** , returneras ett **system. Diagnostics. ProcessModule** -objekt.

## ANTECKNINGAR

- Du kan också referera till den här cmdleten med dess inbyggda alias, PS och GPS. Mer information finns i [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).
- På datorer som kör en 64-bitars version av Windows får 64-bitars versionen av PowerShell bara 64-bitars process-moduler och 32-bitars versionen av PowerShell får bara 32-bitars process moduler.
- Du kan använda egenskaper och metoder för Win32_Process-objektet Windows Management Instrumentation (WMI) i PowerShell. Mer information finns i `Get-WmiObject` och WMI SDK.
- Standard visningen av en process är en tabell som innehåller följande kolumner. En beskrivning av alla egenskaper för process objekt finns i [process egenskaper](/dotnet/api/system.diagnostics.process).
  - Handtag: antalet referenser som processen har öppnat.
  - NPM (K): mängden icke växlings Bart minne som processen använder, i kilobyte.
  - PM (K): hur mycket växlings Bart minne som processen använder, i kilobyte.
  - WS (K): storleken på processens arbets minne i kilobyte.
    Den aktiva arbets minnet består av de sidor i minnet som nyligen refererats av processen.
  - Virtuell dator (M): mängden virtuellt minne som processen använder, i megabyte.
    Virtuellt minne innehåller lagrings utrymme i växlingsfilerna på disk.
  - PROCESSOR (er): mängden processor tid som processen har använt på alla processorer, i sekunder.
  - ID: process-ID (PID) för processen.
  - ProcessName: namnet på processen. Förklaringar av begreppen som rör processer finns i ord listan i hjälp-och Support Center och i hjälpen för aktivitets hanteraren.
- Du kan också använda de inbyggda alternativa vyerna för de processer som är tillgängliga med `Format-Table` , t. ex. **StartTime** och **Priority** , och du kan skapa egna vyer.

## RELATERADE LÄNKAR

[Fel sökning – process](Debug-Process.md)

[Hämta process](Get-Process.md)

[Start process](Start-Process.md)

[Stoppa – process](Stop-Process.md)

[Vänta-process](Wait-Process.md)
