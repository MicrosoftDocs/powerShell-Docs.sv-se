---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 08/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/start-process?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Process
ms.openlocfilehash: ade80115f85cb241fdf0dc4e829daa5b381644ef
ms.sourcegitcommit: 4fc8cf397cb725ae973751d1d5d542f34f0db2d7
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/03/2020
ms.locfileid: "93268851"
---
# Start-Process

## SAMMANFATTNING
Startar en eller flera processer på den lokala datorn.

## SYNTAX

### Standard (standard)

```
Start-Process [-FilePath] <String> [[-ArgumentList] <String[]>] [-Credential <PSCredential>]
 [-WorkingDirectory <String>] [-LoadUserProfile] [-NoNewWindow] [-PassThru]
 [-RedirectStandardError <String>] [-RedirectStandardInput <String>]
 [-RedirectStandardOutput <String>] [-WindowStyle <ProcessWindowStyle>] [-Wait] [-UseNewEnvironment]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### UseShellExecute

```
Start-Process [-FilePath] <String> [[-ArgumentList] <String[]>] [-WorkingDirectory <String>]
 [-PassThru] [-Verb <String>] [-WindowStyle <ProcessWindowStyle>] [-Wait] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## BESKRIVNING

`Start-Process`Cmdleten startar en eller flera processer på den lokala datorn. Som standard `Start-Process` skapar en ny process som ärver alla miljövariabler som definieras i den aktuella processen.

Ange det program som körs i processen genom att ange en körbar fil eller skript fil, eller en fil som kan öppnas med hjälp av ett program på datorn. Om du anger en fil som inte är körbar `Start-Process` startar programmet som är associerat med filen, ungefär som- `Invoke-Item` cmdleten.

Du kan använda parametrarna för `Start-Process` för att ange alternativ, till exempel att läsa in en användar profil, starta processen i ett nytt fönster eller använda alternativa autentiseringsuppgifter.

## EXEMPEL

### Exempel 1: starta en process som använder standardvärden

I det här exemplet startas en process som använder `Sort.exe` filen i den aktuella mappen. Kommandot använder alla standardvärden, inklusive standard fönster format, arbetsmapp och autentiseringsuppgifter.

```powershell
Start-Process -FilePath "sort.exe"
```

### Exempel 2: skriva ut en textfil

I det här exemplet startas en process som skriver ut `C:\PS-Test\MyFile.txt` filen.

```powershell
Start-Process -FilePath "myfile.txt" -WorkingDirectory "C:\PS-Test" -Verb Print
```

### Exempel 3: starta en process för att sortera objekt till en ny fil

I det här exemplet startas en process som sorterar objekten i `Testsort.txt` filen och returnerar de sorterade objekten i `Sorted.txt` filerna. Eventuella fel skrivs till `SortError.txt` filen.

```powershell
Start-Process -FilePath "Sort.exe" -RedirectStandardInput "Testsort.txt" -RedirectStandardOutput "Sorted.txt" -RedirectStandardError "SortError.txt" -UseNewEnvironment
```

Parametern **UseNewEnvironment** anger att processen körs med egna miljövariabler.

### Exempel 4: starta en process i ett maximerat fönster

Det här exemplet startar `Notepad.exe` processen. Det maximerar fönstret och bevarar fönstret tills processen har slutförts.

```powershell
Start-Process -FilePath "notepad" -Wait -WindowStyle Maximized
```

### Exempel 5: starta PowerShell som administratör

Det här exemplet startar PowerShell med alternativet **Kör som administratör** .

```powershell
Start-Process -FilePath "powershell" -Verb RunAs
```

### Exempel 6: använda olika verb för att starta en process

Det här exemplet visar hur du hittar de verb som kan användas när du startar en process. Tillgängliga verb bestäms av fil namns tillägget för filen som körs i processen.

```powershell
$startExe = New-Object System.Diagnostics.ProcessStartInfo -Args PowerShell.exe
$startExe.verbs
```

```Output
open
runas
runasuser
```

Exemplet använder `New-Object` för att skapa ett **system. Diagnostics. ProcessStartInfo** -objekt för **PowerShell.exe** , den fil som körs i PowerShell-processen. Egenskapen **verb** för **ProcessStartInfo** -objektet visar att du kan använda **Open** -och **runas** -verben med `PowerShell.exe` eller med en process som kör en `.exe` fil.

### Exempel 7: ange argument för processen

Båda kommandona startar Windows kommando tolken och utfärdar ett `dir` kommando i `Program Files` mappen. Eftersom den här mappnamn innehåller ett blank steg måste värdet omges av Escaped citat tecken.
Observera att det första kommandot anger en sträng som **argument List**. Det andra kommandot är en sträng mat ris.

```powershell
Start-Process -FilePath "$env:comspec" -ArgumentList "/c dir `"%systemdrive%\program files`""
Start-Process -FilePath "$env:comspec" -ArgumentList "/c","dir","`"%systemdrive%\program files`""
```

## PARAMETRAR

### – Argument List

Anger parametrar eller parameter värden som ska användas när denna cmdlet startar processen. Argument kan godkännas som en enskild sträng med argumenten avgränsade med blank steg eller som en matris med strängar avgränsade med kommatecken.

Om parametrar eller parameter värden innehåller ett blank steg måste de omges av Escaped dubbla citat tecken. Mer information finns i [about_Quoting_Rules](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md).

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Args

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential

Anger ett användar konto som har behörighet att utföra den här åtgärden. Som standard använder cmdleten autentiseringsuppgifterna för den aktuella användaren.

Ange ett användar namn, till exempel **user01** eller **Domain01\User01** , eller ange ett **PSCredential** -objekt som genererats av `Get-Credential` cmdleten. Om du anger ett användar namn uppmanas du att ange lösen ordet.

Autentiseringsuppgifterna lagras i ett [PSCredential](/dotnet/api/system.management.automation.pscredential) -objekt och lösen ordet lagras som en [SecureString](/dotnet/api/system.security.securestring).

> [!NOTE]
> Mer information om **SecureString** -data skydd finns i [hur säker är SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: Default
Aliases: RunAs

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### -Sökväg

Anger den valfria sökvägen och fil namnet för det program som körs i processen. Ange namnet på en körbar fil eller ett dokument, till exempel en `.txt` eller `.doc` -fil, som är associerad med ett program på datorn. Den här parametern är obligatorisk.

Om du bara anger ett fil namn använder du parametern **WorkingDirectory** för att ange sökvägen.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSPath, Path

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – LoadUserProfile

Anger att denna cmdlet läser in Windows-användarprofilen som lagras i `HKEY_USERS` register nyckeln för den aktuella användaren. Parametern gäller inte för system som inte är Windows-datorer.

Den här parametern påverkar inte PowerShell-profilerna. Mer information finns i [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Default
Aliases: Lup

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NoNewWindow

Starta den nya processen i det aktuella konsol fönstret. Som standard öppnas ett nytt fönster i PowerShell i Windows. På andra datorer än Windows-system får du aldrig ett nytt terminalfönster.

Du kan inte använda parametrarna **NoNewWindow** och **windowstyle** i samma kommando.

Parametern gäller inte för system som inte är Windows-datorer.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Default
Aliases: nnw

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – PassThru

Returnerar ett process objekt för varje process som cmdleten startade. Som standard genererar denna cmdlet inga utdata.

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

### -RedirectStandardError

Anger en fil. Den här cmdleten skickar eventuella fel som genereras av processen till en fil som du anger.
Ange sökväg och fil namn. Som standard visas felen i-konsolen.

```yaml
Type: System.String
Parameter Sets: Default
Aliases: RSE

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RedirectStandardInput

Anger en fil. Denna cmdlet läser indata från den angivna filen. Ange sökväg och fil namn för indatafilen. Som standard hämtas den inmatade processen från tangent bordet.

```yaml
Type: System.String
Parameter Sets: Default
Aliases: RSI

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RedirectStandardOutput

Anger en fil. Denna cmdlet skickar de utdata som genereras av processen till en fil som du anger.
Ange sökväg och fil namn. Som standard visas utdata i-konsolen.

```yaml
Type: System.String
Parameter Sets: Default
Aliases: RSO

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseNewEnvironment

Anger att denna cmdlet använder nya miljövariabler som har angetts för processen. Som standard körs den startade processen med miljövariablerna som ärvts från den överordnade processen.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Default
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Verb

Anger ett verb som ska användas när denna cmdlet startar processen. Vilka verb som är tillgängliga beror på fil namns tillägget för filen som körs i processen.

I följande tabell visas verben för vissa vanliga process fil typer.

| Filtyp |                Verb                |
| --------- | ----------------------------------- |
| .cmd      | Redigera, öppna, skriva ut, RunAs, RunAsUser |
| .exe      | Öppna, RunAs, RunAsUser              |
| .txt      | Öppna, skriva ut, PrintTo                |
| .wav      | Öppna, spela upp                          |

Om du vill hitta de verb som kan användas med den fil som körs i en process använder du `New-Object` cmdleten för att skapa ett **system. Diagnostics. ProcessStartInfo** -objekt för filen. Tillgängliga verb finns i egenskapen **verbs** i **ProcessStartInfo** -objektet. Mer information finns i exemplen.

Parametern gäller inte för system som inte är Windows-datorer.

```yaml
Type: System.String
Parameter Sets: UseShellExecute
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Vänta

Anger att denna cmdlet väntar på att den angivna processen och dess underordnade ska slutföras innan fler indatatyper accepteras. Den här parametern förhindrar kommando tolken eller behåller fönstret tills processerna har slutförts.

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

### – WindowStyle

Anger status för det fönster som används för den nya processen. De acceptabla värdena för den här parametern är: **Normal** , **dold** , **minimerad** och **maximerad**. Standardvärdet är **Normal**.

Du kan inte använda parametrarna **windowstyle** och **NoNewWindow** i samma kommando.

Parametern gäller inte för system som inte är Windows-datorer.

```yaml
Type: System.Diagnostics.ProcessWindowStyle
Parameter Sets: (All)
Aliases:
Accepted values: Normal, Hidden, Minimized, Maximized

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – WorkingDirectory

Anger den plats som den nya processen ska starta i. Standardvärdet är platsen för den körbara filen eller det dokument som startas. Den angivna sökvägen behandlas som en literal sökväg. Jokertecken stöds inte. Du måste omge sökvägen med enkla citat tecken ( `'` ) om Sök vägs namnet innehåller tecken som skulle tolkas som jokertecken.

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

### -Confirm

Uppmanar dig att bekräfta innan du kör cmdleten.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

Visar vad som skulle hända om cmdleten kördes. Cmdleten körs inte.

Den här parametern introducerades i PowerShell 6,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
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

### Ingen, system. Diagnostics. process

Denna cmdlet genererar ett **system. Diagnostics. process** -objekt, om du anger parametern **Passthru** . Annars returnerar denna cmdlet inga utdata.

## ANTECKNINGAR

- Denna cmdlet implementeras med hjälp av metoden **Start** i klassen **system. Diagnostics. process** . Mer information om den här metoden finns i [metoden process. start](/dotnet/api/system.diagnostics.process.start#overloads).

- När du använder **UseNewEnvironment** i Windows, börjar den nya processen bara att innehålla de standard miljö variabler som definierats för **dator** omfånget. Detta har samma effekt som `$env:USERNAME` är inställd på **system**. Ingen av variablerna från **användar** omfånget ingår.

- I Windows är det vanligaste användnings fallet för `Start-Process` att använda parametern **wait** för att blockera förloppet tills den nya processen avslutas. På andra datorer än Windows-system behövs detta sällan eftersom standard beteendet för kommando rads program är lika med `Start-Process -Wait` .

- När `Start-Process` du använder på andra datorer än Windows-system får du aldrig ett nytt terminalfönster.

## RELATERADE LÄNKAR

[about_Quoting_Rules](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md)

[Fel sökning – process](Debug-Process.md)

[Hämta process](Get-Process.md)

[Start-Service](Start-Service.md)

[Stoppa – process](Stop-Process.md)

[Vänta-process](Wait-Process.md)
