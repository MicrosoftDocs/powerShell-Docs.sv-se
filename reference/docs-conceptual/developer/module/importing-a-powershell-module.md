---
ms.date: 02/03/2020
ms.topic: reference
title: Importera en PowerShell-modul
description: Importera en PowerShell-modul
ms.openlocfilehash: 688509c0943a9a0289e75b80543f278e16cfedfe
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92658790"
---
# <a name="importing-a-powershell-module"></a>Importera en PowerShell-modul

När du har installerat en modul i ett system vill du förmodligen importera modulen. Import är den process som läser in modulen i Active Memory, så att en användare kan komma åt modulen i sin PowerShell-session. I PowerShell 2,0 kan du importera en nyligen installerad PowerShell-modul med ett anrop till cmdleten [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) . I PowerShell 3,0 kan PowerShell importera en modul implicit när en av funktionerna eller cmdletarna i modulen anropas av en användare. Observera att båda versionerna förutsätter att du installerar modulen på en plats där PowerShell kan hitta den. Mer information finns i [installera en PowerShell-modul](./installing-a-powershell-module.md).
Du kan använda ett modul manifest för att begränsa vilka delar av modulen som exporteras och du kan använda parametrar för `Import-Module` anropet för att begränsa vilka delar som importeras.

## <a name="importing-a-snap-in-powershell-10"></a>Importera en Snap-In (PowerShell 1,0)

Modulerna fanns inte i PowerShell 1,0: i stället var du tvungen att registrera och använda snapin-moduler. Vi rekommenderar dock inte att du använder den här tekniken eftersom moduler ofta är enklare att installera och importera. Mer information finns i [så här skapar du en Windows PowerShell-snapin-modul](../cmdlet/how-to-create-a-windows-powershell-snap-in.md).

## <a name="importing-a-module-with-import-module-powershell-20"></a>Importera en modul med Import-Module (PowerShell 2,0)

PowerShell 2,0 använder lämplig-namngiven cmdlet för [import-modul](/powershell/module/Microsoft.PowerShell.Core/Import-Module) för att importera moduler. När den här cmdleten körs söker Windows PowerShell efter den angivna modulen i de kataloger som anges i `PSModulePath` variabeln. När den angivna katalogen hittas söker Windows PowerShell efter filer i följande ordning: modul manifest Files (. psd1), skriptfiler (. psm1), filer för binär modul (. dll). Mer information om hur du lägger till kataloger i sökningen finns i [ändra installations Sök vägen för PSModulePath](./modifying-the-psmodulepath-installation-path.md).
I följande kod beskrivs hur du importerar en modul:

```powershell
Import-Module myModule
```

Förutsatt att modulen finns i `PSModulePath` , skulle PowerShell läsa in modulen i aktivt minne. Om modulen inte fanns på en `PSModulePath` sökväg, kunde du fortfarande uttryckligen meddela PowerShell var du hittar den:

```powershell
Import-Module -Name C:\myRandomDirectory\myModule -Verbose
```

Du kan också använda- `-Verbose` parametern för att identifiera vad som exporteras från modulen och vad som importeras till det aktiva minnet. Både export och import begränsar vad som visas för användaren: skillnaden är vem som styr synligheten. I princip styrs exporten av kod i modulen. Som kontrast styrs import av `Import-Module` anropet. Mer information finns i **begränsa medlemmar som importeras** nedan.

## <a name="implicitly-importing-a-module-powershell-30"></a>Importera en modul implicit (PowerShell 3,0)

Från och med Windows PowerShell 3,0 importeras moduler automatiskt när en cmdlet eller funktion i modulen används i ett kommando. Den här funktionen fungerar på alla moduler i en katalog som ingår i värdet för **PSModulePath** -miljövariabeln. Om du inte sparar modulen på en giltig sökväg kan du dock fortfarande läsa in dem med hjälp av alternativet explicit [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) , som beskrivs ovan.

Följande åtgärder utlöser automatisk import av en modul, även kallat "automatisk inläsning av modul".

- Använda en cmdlet i ett kommando. Skriv till exempel `Get-ExecutionPolicy` importerar modulen Microsoft. PowerShell. Security som innehåller `Get-ExecutionPolicy` cmdleten.

- Hämta kommandot med hjälp av cmdleten [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) . Skriv till exempel `Get-Command Get-JobTrigger` importerar **PSScheduledJob** -modulen som innehåller `Get-JobTrigger` cmdleten. Ett `Get-Command` kommando som innehåller jokertecken betraktas som identifiering och utlöser inte import av en modul.

- Använd cmdleten [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) för att få hjälp med en cmdlet. Skriv till exempel `Get-Help Get-WinEvent` importerar modulen Microsoft. PowerShell. Diagnostics som innehåller `Get-WinEvent` cmdleten.

För att stödja automatisk import av moduler, `Get-Command` hämtar cmdlet alla cmdletar och funktioner i alla installerade moduler, även om modulen inte importeras till sessionen. Mer information finns i hjälp avsnittet för cmdleten [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) .

## <a name="the-importing-process"></a>Import processen

När en modul importeras skapas ett nytt sessionstillstånd för modulen och ett [system. Management. Automation. PSModuleInfo](/dotnet/api/System.Management.Automation.PSModuleInfo) -objekt skapas i minnet. Ett sessionstillstånd skapas för varje modul som importeras (Detta inkluderar rotnoden och eventuella kapslade moduler). De medlemmar som exporteras från modulen root, inklusive alla medlemmar som exporter ATS till rotnoden av eventuella kapslade moduler, importeras sedan till anroparens sessionstillstånd.

Metadata för medlemmar som exporteras från en modul har egenskapen modulnamn. Den här egenskapen fylls med namnet på den modul som exporterade dem.

> [!WARNING]
> Om namnet på en exporterad medlem använder ett icke godkänt verb eller om namnet på medlemmen använder begränsade tecken visas en varning när cmdleten [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) körs.

Som standard returnerar cmdleten [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) inga objekt till pipelinen. Cmdleten stöder dock en **Passthru** -parameter som kan användas för att returnera ett [system. Management. Automation. PSModuleInfo](/dotnet/api/System.Management.Automation.PSModuleInfo) -objekt för varje modul som importeras. Användarna ska kunna skicka utdata till värden genom att köra cmdleten [Write-Host](/powershell/module/Microsoft.PowerShell.Utility/Write-Host) .

## <a name="restricting--the-members-that-are-imported"></a>Begränsa de medlemmar som importeras

När en modul importeras med hjälp av cmdleten [import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) , importeras alla medlemmar som exporter ATS till sessionen, inklusive alla kommandon som exporteras till modulen av en kapslad modul. Som standard exporteras inte variabler och alias. Om du vill begränsa vilka medlemmar som exporteras använder du ett [modul manifest](./how-to-write-a-powershell-module-manifest.md).
Om du vill begränsa vilka medlemmar som importeras använder du följande parametrar för `Import-Module` cmdleten.

- **Funktion** : den här parametern begränsar vilka funktioner som exporteras. (Om du använder ett modul-manifest, se FunctionsToExport-nyckeln.)

- `**Cmdlet** : den här parametern begränsar de cmdlet: ar som exporteras (om du använder ett modul manifest, se CmdletsToExport-nyckeln).

- **Variabel** : den här parametern begränsar de variabler som exporteras (om du använder ett modul-manifest, se VariablesToExport-nyckeln).

- **Alias** : den här parametern begränsar de alias som exporteras (om du använder ett modul manifest, se AliasesToExport-nyckeln).

## <a name="see-also"></a>Se även

[Skriva en Windows PowerShell-modul](./writing-a-windows-powershell-module.md)
