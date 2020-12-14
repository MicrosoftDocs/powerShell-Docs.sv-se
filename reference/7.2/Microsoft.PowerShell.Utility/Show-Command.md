---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/29/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/show-command?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Show-Command
ms.openlocfilehash: 87bdd5a9610267b8fce9e391431d24872a77e2de
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709745"
---
# Show-Command

## SAMMANFATTNING
Visar PowerShell-kommando information i ett grafiskt fönster.

## SYNTAX

```
Show-Command [[-Name] <String>] [-Height <Double>] [-Width <Double>] [-NoCommonParameter]
 [-ErrorPopup] [-PassThru] [<CommonParameters>]
```

## BESKRIVNING

Med `Show-Command` cmdleten kan du skapa ett PowerShell-kommando i ett kommando fönster. Du kan använda funktionerna i kommando fönstret för att köra kommandot eller låta det returnera kommandot till dig.

`Show-Command` är ett mycket användbart undervisnings-och utbildnings verktyg. `Show-Command` fungerar på alla kommando typer, inklusive cmdlets, functions, arbetsflöden och CIM-kommandon.

Utan parametrar `Show-Command` visar ett kommando fönster som visar alla tillgängliga kommandon i alla installerade moduler. Om du vill hitta kommandona i en modul väljer du modulen i list rutan moduler. Klicka på kommando namnet för att välja ett kommando.

Om du vill använda kommando fönstret väljer du ett kommando, antingen genom att använda namnet eller genom att klicka på kommando namnet i listan **kommandon** . Varje parameter uppsättning visas på en separat flik. Asterisker visar de obligatoriska parametrarna. Ange värden för en parameter genom att skriva värdet i text rutan eller välja värdet i list rutan. Klicka för att markera kryss rutan parameter för att lägga till en växlings parameter.

När du är klar kan du klicka på **Kopiera** för att kopiera kommandot som du har skapat till Urklipp eller klicka på **Kör** för att köra kommandot. Du kan också använda parametern **Passthru** för att returnera kommandot till värd programmet, till exempel PowerShell-konsolen. Om du vill avbryta kommando markeringen och återgå till vyn som visar alla kommandon, trycker du på CTRL och klickar på det valda kommandot.

I PowerShell ISE (Integrated Scripting Environment) visas en variant av `Show-Command` fönstret som standard. Information om hur du använder det här kommando fönstret finns i hjälp avsnitten för PowerShell ISE.

Den här cmdleten introducerades om i PowerShell 7.

Eftersom denna cmdlet kräver ett användar gränssnitt fungerar den inte på Windows Server Core eller Windows Nano Server. Den här cmdleten är endast tillgänglig på Windows-system som stöder Windows-skrivbordet.

## EXEMPEL

### Exempel 1: Öppna kommando fönstret

I det här exemplet visas standardvyn för `Show-Command` fönstret. **Kommando** fönstret visar en lista över alla kommandon i alla moduler som är installerade på datorn.

```powershell
Show-Command
```

### Exempel 2: öppna en cmdlet i kommando fönstret

I det här exemplet visas `Invoke-Command` cmdlet: en i **kommando** fönstret. Du kan använda den här vyn för att köra `Invoke-Command` kommandon.

```powershell
Show-Command -Name "Invoke-Command"
```

### Exempel 3: öppna en cmdlet med angivna parametrar

Det här kommandot öppnar ett `Show-Command` fönster för `Connect-PSSession` cmdleten.

```powershell
Show-Command -Name "Connect-PSSession" -Height 700 -Width 1000 -ErrorPopup
```

Parametrarna **height** och **width** anger dimensionen för kommando fönstret. **ErrorPopup** -parametern visar fel kommando fönstret.

När du klickar på **Kör** `Connect-PSSession` körs kommandot, precis som om du skrev `Connect-PSSession` kommandot på kommando raden.

### Exempel 4: Ange nya standard parameter värden för en cmdlet

I det här exemplet används den `$PSDefaultParameterValues` automatiska variabeln för att ange nya standardvärden för parametrarna **height**, **width** och **ErrorPopup** för `Show-Command` cmdleten.

```powershell
$PSDefaultParameterValues = @{
    "Show-Command:Height" = 700
    "Show-Command:Width" = 1000
    "Show-Command:ErrorPopup" = $True
}
```

Nu när du kör ett `Show-Command` kommando tillämpas de nya standardvärdena automatiskt. Om du vill använda standardvärdena i varje PowerShell-session lägger du till `$PSDefaultParameterValues` variabeln i din PowerShell-profil. Mer information finns i [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md) och [about_Parameters_Default_Values](../Microsoft.PowerShell.Core/About/about_Parameters_Default_Values.md).

### Exempel 5: skicka utdata till en rutnätsvy

Det här kommandot visar hur du använder- `Show-Command` och- `Out-GridView` cmdletarna tillsammans.

```powershell
Show-Command Get-ChildItem | Out-GridView
```

Kommandot använder `Show-Command` cmdleten för att öppna ett kommando fönster för `Get-ChildItem` cmdleten.
När du klickar på **Kör** -knappen `Get-ChildItem` körs kommandot och genererar utdata. Pipeline-operatorn (|) skickar utdata från `Get-ChildItem` kommandot till `Out-GridView` cmdleten, som visar `Get-ChildItem` utdata i ett interaktivt fönster.

### Exempel 6: Visa ett kommando som du skapar i kommando fönstret

I det här exemplet visas kommandot som du skapade i `Show-Command` fönstret. Kommandot använder parametern **Passthru** , som returnerar `Show-Command` resultatet i en sträng.

```powershell
Show-Command -PassThru
```

```Output
Get-EventLog -LogName "Windows PowerShell" -Newest 5
```

Om du till exempel använder `Show-Command` fönstret för att skapa ett `Get-EventLog` kommando som hämtar de fem senaste händelserna i händelse loggen i Windows PowerShell, och sedan klickar på **OK**, returnerar kommandot de utdata som visas ovan. Du kan lära dig mer om PowerShell genom att visa kommando strängen.

### Exempel 7: Spara ett kommando till en variabel

Det här exemplet visar hur du kör kommando strängen som du får när du använder **Passthru** -parametern för `Show-Command` cmdleten. Med den här strategin kan du se kommandot och använda det.

```powershell
$C = Show-Command -PassThru
$C
Invoke-Expression $C
```

```Output
Get-EventLog -LogName "PowerShell" -Newest 5

Index Time          EntryType   Source                 InstanceID Message
----- ----          ---------   ------                 ---------- -------
11520 Dec 16 16:37  Information Windows PowerShell            400 Engine state is changed from None to Available...
11519 Dec 16 16:37  Information Windows PowerShell            600 Provider "Variable" is Started. ...
11518 Dec 16 16:37  Information Windows PowerShell            600 Provider "Registry" is Started. ...
11517 Dec 16 16:37  Information Windows PowerShell            600 Provider "Function" is Started. ...
11516 Dec 16 16:37  Information Windows PowerShell            600 Provider "FileSystem" is Started. ...
```

Det första kommandot använder **Passthru** -parametern för `Show-Command` cmdleten och sparar resultatet av kommandot i `$C` variabeln. I det här fallet använder vi `Show-Command` fönstret för att skapa ett `Get-EventLog` kommando som hämtar de fem senaste händelserna i händelse loggen i Windows PowerShell. När du klickar på OK `Show-Command` returneras kommando strängen som sparas i `$C` variabeln.

### Exempel 8: spara utdata från ett kommando till en variabel

I det här exemplet används parametern **ErrorPopup** för att spara utdata från ett kommando i en variabel.

```powershell
$P = Show-Command Get-Process -ErrorPopup
$P
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    473      33    94096     112532   709     2.06   4492 powershell
```

Förutom att visa fel i ett fönster returnerar **ErrorPopup** kommandoutdata till det aktuella kommandot, i stället för att skapa ett nytt kommando. När du kör det här kommandot `Show-Command` öppnas fönstret. Du kan använda fönster funktionerna för att ange parameter värden. Kör kommandot genom att klicka på knappen **Kör** i `Show-Command` fönstret.

## PARAMETRAR

### -ErrorPopup

Anger att cmdleten visar fel i ett popup-fönster, förutom att visa dem på kommando raden. Som standard visas felet bara på kommando raden när ett kommando som körs i ett `Show-Command` fönster genererar ett fel.

När du kör kommandot (med knappen **Kör** i `Show-Command` fönstret) returnerar parametern **ErrorPopup** kommando resultatet till det aktuella kommandot, i stället för att köra kommandot och returnera utdata till ett nytt kommando. Du kan använda den här funktionen för att spara kommando resultatet i en variabel.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Höjd

Anger `Show-Command` fönstrets höjd i bild punkter. Ange ett värde mellan 300 och antalet bild punkter i skärmupplösningen. Om värdet är för stort för att visa kommando fönstret på skärmen `Show-Command` genererar ett fel. Standard höjden är 600 bild punkter. För ett `Show-Command` kommando som innehåller parametern **Name** är standard höjden 300 bild punkter.

```yaml
Type: System.Double
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Visar ett kommando fönster för det angivna kommandot. Ange namnet på ett kommando, till exempel namnet på ett cmdlet-, Function-eller CIM-kommando. Om du utelämnar den här parametern `Show-Command` visas ett kommando fönster som visar alla PowerShell-kommandon i alla moduler som är installerade på datorn.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: CommandName

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NoCommonParameter

Anger att denna cmdlet utelämnar avsnittet gemensamma parametrar i kommando visningen. Som standard visas de gemensamma parametrarna i ett expanderat avsnitt längst ned i kommando fönstret.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### – PassThru

Returnerar ett objekt som representerar det objekt som du arbetar med. Som standard genererar denna cmdlet inga utdata. Om du vill köra kommando strängen kopierar du och klistrar in den i kommando tolken eller sparar den i en variabel och använder `Invoke-Expression` cmdleten för att köra strängen i variabeln.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Bredd

Anger `Show-Command` fönstrets bredd i bild punkter. Ange ett värde mellan 300 och antalet bild punkter i skärmupplösningen. Om värdet är för stort för att visa kommando fönstret på skärmen `Show-Command` genererar ett fel. Standard bredden är 300 bild punkter.

```yaml
Type: System.Double
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

### Inga

Du kan inte skicka pipe-ininformation till `Show-Command` .

## UTDATA

### Ingen, system. String, system. Object

När du använder parametern **Passthru** `Show-Command` returneras en kommando sträng. När du använder parametern **ErrorPopup** `Show-Command` returneras kommandoutdata (alla objekt). Annars `Show-Command` genererar inga utdata.

## ANTECKNINGAR

Den här cmdleten är endast tillgänglig på Windows-plattformar.

`Show-Command` fungerar inte i fjärrsessioner.

## RELATERADE LÄNKAR
