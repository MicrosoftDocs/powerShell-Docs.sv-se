---
description: Beskriver snapin-moduler för Windows PowerShell och visar hur du använder och hanterar dem.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pssnapins?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PSSnapins
ms.openlocfilehash: cc22f8de0b9d8a55dcfa12f3b47f3852d891e67b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93271521"
---
# <a name="about-pssnapins"></a>Om PSSnapins

## <a name="short-description"></a>KORT BESKRIVNING

Beskriver snapin-moduler för Windows PowerShell och visar hur du använder och hanterar dem.

## <a name="long-description"></a>LÅNG BESKRIVNING

En Windows PowerShell-snapin-modul är en Microsoft .NET Ramverks sammansättning som innehåller Windows PowerShell-leverantörer och- \/ cmdletar. Windows PowerShell innehåller en uppsättning grundläggande snapin-moduler, men du kan utöka kraften och värdet i Windows PowerShell genom att lägga till snapin-moduler som innehåller providrar och cmdlets som du skapar eller hämtar från andra.

När du lägger till en snapin-modul är de cmdletar och providrar som den innehåller omedelbart tillgängliga för användning i den aktuella sessionen, men ändringen påverkar bara den aktuella sessionen.

Om du vill lägga till snapin-modulen i alla framtida sessioner sparar du den i din Windows PowerShell-profil. Du kan också använda Export-Console-cmdlet: en för att spara namn på snapin-modulen till en konsol fil och sedan använda den i framtida sessioner. Du kan till och med spara flera konsolfiler, var och en med en annan uppsättning snapin-moduler.

Obs! snapin-moduler för Windows PowerShell (PSSnapins) är tillgängliga för användning i Windows PowerShell 3,0 och Windows PowerShell 2,0. De kan vara ändrade eller inte tillgängliga i senare versioner. Använd moduler för att paketera Windows PowerShell-cmdlets och providers. Information om hur du skapar moduler och konverterar snapin-moduler till moduler finns i [skriva en Windows PowerShell-modul](/powershell/scripting/developer/module/writing-a-windows-powershell-module).

### <a name="finding-snap-ins"></a>HITTA SNAPIN-MODULER

Om du vill hämta en lista över Windows PowerShell-snapin-modulerna på datorn skriver du:

```powershell
Get-PSSnapin
```

Om du vill hämta snapin-modulen för varje Windows PowerShell-Provider skriver du:

```powershell
Get-PSProvider | Format-List name, pssnapin
```

Om du vill hämta en lista över cmdletarna i en Windows PowerShell-snapin-modul skriver du:

```powershell
Get-Command -Module <snap-in_name>
```

### <a name="installing-a-snap-in"></a>INSTALLERA EN SNAPIN-MODUL

De inbyggda snapin-modulerna är registrerade i systemet och läggs till i Standardsessionen när du startar Windows PowerShell. Du måste dock registrera snapin-moduler som du skapar eller hämtar från andra och sedan lägga till snapin-modulerna i sessionen.

### <a name="registering-a-snap-in"></a>REGISTRERA EN SNAPIN-MODUL

En Windows PowerShell-snapin-modul är ett program som skrivits i ett .NET Framework språk som är kompilerat i en. dll-fil. Om du vill använda providers och cmdlets i en snapin-modul måste du först registrera snapin-modulen (Lägg till i registret).

De flesta snapin-moduler innehåller ett installations program (en. exe-eller. msi-fil) som registrerar DLL-filen åt dig. Men om du får en snapin-modul som en. dll-fil kan du registrera den på systemet. Mer information finns i [så här registrerar du cmdlets, providers och värd program](https://go.microsoft.com/fwlink/?LinkID=143619) i MSDN-biblioteket.

Om du vill hämta alla registrerade snapin-moduler i systemet eller kontrol lera att en snapin-modul är registrerad, skriver du:

```powershell
Get-PSSnapin -registered
```

### <a name="adding-the-snap-in-to-the-current-session"></a>LÄGGA TILL SNAPIN-MODULEN I DEN AKTUELLA SESSIONEN

Använd Add-PsSnapin-cmdleten om du vill lägga till en registrerad snapin-modul till den aktuella sessionen. Om du till exempel vill lägga till Microsoft SQL Server snapin-modulen till sessionen skriver du:

```powershell
Add-PSSnapin sql
```

När kommandot har slutförts är leverantörerna och cmdletarna i snapin-modulen tillgängliga i sessionen. De är dock bara tillgängliga i den aktuella sessionen om du inte sparar dem.

### <a name="saving-the-snap-ins"></a>SPARA SNAPIN-MODULERNA

Om du vill använda en snapin-modul i framtida Windows PowerShell-sessioner lägger du till kommandot Add-PsSnapin i Windows PowerShell-profilen. Du kan också exportera namnet på snapin-modulen till en konsol fil.

Om du lägger till kommandot Add-PSSnapin i din profil, är det tillgängligt i alla framtida Windows PowerShell-sessioner. Om du exporterar namnen på snapin-modulerna i din session kan du bara använda export filen när du behöver snapin-modulerna.

Om du vill lägga till kommandot Add-PsSnapin till din Windows PowerShell-profil öppnar du din profil, klistrar in eller skriver kommandot och sparar sedan profilen. Mer information finns i about_Profiles.

Använd Export-Console-cmdleten för att spara snapin-modulerna från en session i konsol filen (. psc1). Om du till exempel vill spara snapin-modulerna i den aktuella sessionen till filen NewConsole. psc1 i den aktuella katalogen skriver du:

```powershell
Export-Console NewConsole
```

Mer information finns i export-Console.

### <a name="opening-windows-powershell-with-a-console-file"></a>ÖPPNA WINDOWS POWERSHELL MED EN KONSOL FIL

Om du vill använda en konsol fil som innehåller snapin-modulen startar du Windows PowerShell (PowerShell.exe) från kommando tolken i Cmd.exe eller i en annan Windows PowerShell-session. Använd parametern PsConsoleFile för att ange konsol filen som innehåller snapin-modulen. Följande kommando startar till exempel Windows PowerShell med konsol filen NewConsole. psc1:

```powershell
PowerShell.exe -psconsolefile NewConsole.psc1
```

Providers och cmdlets i snapin-modulen är nu tillgängliga för användning i sessionen.

### <a name="removing-a-snap-in"></a>TA BORT EN SNAPIN-MODUL

Använd Remove-PsSnapin-cmdleten om du vill ta bort en Windows PowerShell-snapin-modul från den aktuella sessionen. Om du till exempel vill ta bort snapin-modulen SQL Server från den aktuella sessionen skriver du:

```powershell
Remove-PSSnapin sql
```

Denna cmdlet tar bort snapin-modulen från sessionen. Snapin-modulen är fortfarande inläst, men de providers och cmdlets som stöds inte längre är tillgängliga.

### <a name="built-in-commands"></a>INBYGGDA KOMMANDON

I Windows PowerShell 2,0 och i äldre värd program i Windows PowerShell 3,0 och senare, paketeras de inbyggda kommandon som installeras med Windows PowerShell i snapin-moduler som läggs till automatiskt till alla Windows PowerShell-sessioner.

Från och med Windows PowerShell 3,0 i nyare typ värd program – de som startar sessioner med hjälp av metoden InitialSessionState. CreateDefault2 – de inbyggda kommandona paketeras i moduler. Undantaget är Microsoft. PowerShell. Core, som alltid visas som en snapin-modul. Snapin-modulen Core ingår i varje session som standard. De inbyggda modulerna läses in automatiskt vid första användning.

Obs! fjärrsessioner, inklusive sessioner som startas med hjälp av New-PSSession-cmdleten, är äldre sessioner där de inbyggda kommandona paketeras i snapin-moduler.

Följande snapin-moduler (eller moduler) installeras med Windows PowerShell.

- Microsoft. PowerShell. Core – innehåller providrar och cmdlets som används för att hantera de grundläggande funktionerna i Windows PowerShell. Det omfattar fil namns-, register-, alias-, miljö-, funktions-och variabel leverantörer och grundläggande cmdlets, till exempel Get-Help, Get-Command och get-History.

- Microsoft. PowerShell. Host-innehåller cmdletar som används av Windows PowerShell-värden, till exempel Start-Transcript och stopp-avskrift.

- Microsoft. PowerShell. Management – innehåller cmdlets, till exempel Get-Service och Get-ChildItem som används för att hantera Windows-baserade funktioner.

- Microsoft. PowerShell. Security – innehåller den certifikat leverantör och de cmdletar som används för att hantera Windows PowerShell-säkerhet, till exempel get-ACL, get-AuthenticodeSignature och ConvertTo-SecureString.

- Microsoft. PowerShell. Utility – innehåller cmdletar som används för att manipulera objekt och data, till exempel Get-Member, Write-Host och format-List.

- Microsoft. WSMan. Management – innehåller WSMan-providern och cmdletar som hanterar tjänsten Windows Remote Management, till exempel Connect-WSMan och enable-WSManCredSSP.

## <a name="logging-snap-in-events"></a>LOGGA SNAPIN-HÄNDELSER

Från och med Windows PowerShell 3,0 kan du registrera körnings händelser för cmdletarna i Windows PowerShell-moduler och snapin-moduler genom att ange egenskapen LogPipelineExecutionDetails för moduler och snapin-moduler till sant. Mer information finns i [about_EventLogs](about_EventLogs.md).

## <a name="see-also"></a>SE ÄVEN

[Add-PsSnapin](xref:Microsoft.PowerShell.Core.Add-PSSnapin)

[Get-PsSnapin](xref:Microsoft.PowerShell.Core.Get-PSSnapin)

[Remove-PsSnapin](xref:Microsoft.PowerShell.Core.Remove-PSSnapin)

[Exportera-konsol](xref:Microsoft.PowerShell.Core.Export-Console)

[Get-Command](xref:Microsoft.PowerShell.Core.Get-Command)

[about_Profiles](about_Profiles.md)

[about_Modules](about_Modules.md)

## <a name="keywords"></a>RESERVERADE

about_Snapins, about_Snap_ins, about_Snap-moduler
