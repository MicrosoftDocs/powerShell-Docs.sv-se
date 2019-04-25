---
title: Importera en PowerShell-modul | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 697791b3-2135-4a39-b9d7-8566ed67acf2
caps.latest.revision: 13
ms.openlocfilehash: bb5d036e5658c365a4fafa2cac05c0bba9f87019
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082257"
---
# <a name="importing-a-powershell-module"></a>Importera en PowerShell-modul

När din har installerat en modul på ett system, vill du förmodligen att importera modulen. Importera är den process som läser in modulen i active minne, så att en användare kan komma åt denna modul i sina PowerShell-session. I PowerShell 2.0, kan du importera en nyinstallerad PowerShell-modulen med ett anrop till [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet. PowerShell är implicit importera en modul när en av funktioner eller cmdlets i modulen anropas av en användare i PowerShell 3.0. Observera att båda versionerna förutsätter att du installerar din modul på en plats där PowerShell är att hitta den. Mer information finns i [installerar ett PowerShell-modulen](./installing-a-powershell-module.md). Du kan använda ett modulmanifest för att begränsa vilka delar av din modul exporteras och du kan använda parametrarna för den `Import-Module` anrop för att begränsa vilka delar importeras.

## <a name="importing-a-snap-in-powershell-10"></a>Importera en snapin-modul (PowerShell 1.0)

Moduler fanns inte i PowerShell 1.0: i stället var du tvungen att registrera och använda snapin-moduler. Men rekommenderas det inte att du använder den här tekniken nu, som moduler är vanligtvis enklare att installera och importera. Mer information finns i [så här skapar du en Windows PowerShell snapin-modul](../cmdlet/how-to-create-a-windows-powershell-snap-in.md).

## <a name="importing-a-module-with-import-module-powershell-20"></a>Importera en modul med Import-Module (PowerShell 2.0)

PowerShell 2.0 använder den på rätt sätt heter [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet för att importera moduler. När denna cmdlet körs Windows PowerShell söker efter den angivna modulen i kataloger som anges i den `PSModulePath` variabeln. När den angivna katalogen finns Windows PowerShell söker efter filer i följande ordning: modulen manifestfiler (.psd1), skriptfiler modulen (.psm1), binära modulen filer (.dll). Läs mer om att lägga till kataloger till search [ändra installationssökvägen PSModulePath](./modifying-the-psmodulepath-installation-path.md). Följande kod beskriver hur du importerar en modul:

```powershell
Import-Module myModule
```

Om vi antar att myModule fanns i den `PSModulePath`, PowerShell skulle läsa in myModule i active minnet. Om myModule inte var finns på en `PSModulePath` sökväg, du kan fortfarande uttryckligen begära att PowerShell var du hittar det:

```powershell
Import-Module -Name C:\myRandomDirectory\myModule -Verbose
```

Du kan också använda-verbose parametern för att identifiera vad som ska exporteras utanför modulen och vad som importeras till active minne. Både export och import begränsa vad visas för användaren: skillnaden är som styr synligheten. I princip styrs exporter av kod i modulen. Däremot import styrs av den `Import-Module` anropa. Mer information finns i **att begränsa medlemmar att importeras**nedan.

## <a name="implicitly-importing-a-module-powershell-30"></a>Implicit importera en modul (PowerShell 3.0)

Från och med Windows PowerShell 3.0 importeras moduler automatiskt när någon cmdlet eller en funktion i modulen används i ett kommando. Den här funktionen fungerar på alla moduler i en katalog som detta ingår i värdet för den **PSModulePath** miljövariabeln. Om du inte sparar din modul på en giltig sökväg men, du kan fortfarande läsa in dem med hjälp av den explicita [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) alternativet, som beskrivs ovan.

Följande åtgärder utlösa automatisk import av en modul, även kallat ”modul automatisk inläsning”.

- Med hjälp av en cmdlet i ett kommando. Till exempel skriva `Get-ExecutionPolicy` den Microsoft.PowerShell.Security-modul som innehåller den `Get-ExecutionPolicy` cmdlet.

- Med hjälp av den [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet för att hämta kommandot.  Till exempel skriva `Get-Command Get-JobTrigger` importerar den **PSScheduledJob** modul som innehåller den `Get-JobTrigger` cmdlet. En `Get-Command` kommando som innehåller jokertecken anses vara identifiering och inte utlöser import av en modul.

- Med hjälp av den [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet för att få hjälp med en cmdlet. Till exempel skriva `Get-Help Get-WinEvent` den Microsoft.PowerShell.Diagnostics-modul som innehåller den `Get-WinEvent` cmdlet.

Stöd för automatisk import av moduler, den `Get-Command` cmdlet hämtar alla cmdletar och funktioner i alla installerade moduler, även om modulen inte har importerats till sessionen. Mer information finns i hjälpavsnittet för den [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet.

## <a name="the-importing-process"></a>Import-processen

När en modul importeras skapas en ny sessionstillstånd för modulen, och en [System.Management.Automation.PSModuleInfo](/dotnet/api/System.Management.Automation.PSModuleInfo) objekt skapas i minnet. En sessionstillstånd skapas för varje modul som importeras (Detta omfattar rot-modulen och eventuella kapslade moduler). De medlemmar som exporteras från rotmodul, inklusive alla medlemmar som exporterades till rotmodul av eventuella kapslade moduler importeras sedan till anroparens sessionstillstånd.

Metadata för medlemmar som exporteras från en modul har en ModuleName-egenskap. Den här egenskapen fylls med namnet på den modul som exporteras dem.

> [!WARNING]
> Om namnet på en exporterad medlem använder en icke-godkända verb eller om namnet på medlemmen använder specialtecken, visas en varning när den [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdleten körs.

Som standard den [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet inte returnerar några objekt till pipelinen. Cmdleten stöder dock en `PassThru` parameter som kan användas för att returnera en [System.Management.Automation.PSModuleInfo](/dotnet/api/System.Management.Automation.PSModuleInfo) objekt för varje modul som importeras. Om du vill skicka utdata till värden, ska användare köra den [Write-Host](/powershell/module/Microsoft.PowerShell.Utility/Write-Host) cmdlet.

## <a name="restricting--the-members-that-are-imported"></a>Att begränsa de medlemmar som har importerats

När en modul importeras med hjälp av den [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet, som standard alla exporterade modulen medlemmar har importerats till sessionen, inklusive kommandon som exporteras till modulen av en kapslad modul. Som standard exporteras variabler och alias inte. Om du vill begränsa de medlemmar som exporteras, använda en [modulmanifestet](./how-to-write-a-powershell-module-manifest.md). Om du vill begränsa de medlemmar som har importerats, använder du följande parametrar för den `Import-Module` cmdlet.

- `Function`: Den här parametern begränsar de funktioner som exporteras. (Om du använder ett modulmanifest Se nyckeln FunctionsToExport.)

- `Cmdlet`: Den här parametern begränsar de cmdletar som exporteras (om du använder en modul manifest, finns i nyckeln CmdletsToExport.)

- `Variable`: Den här parametern begränsar de variabler som exporteras (om du använder en modul manifest, finns i nyckeln VariablesToExport.)

- `Alias`: Den här parametern begränsar alias som exporteras (om du använder en modul manifest, finns i nyckeln AliasesToExport.)

## <a name="see-also"></a>Se även

[Skriva ett Windows PowerShell-modul](./writing-a-windows-powershell-module.md)
