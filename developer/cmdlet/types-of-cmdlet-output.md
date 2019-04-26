---
title: Typer av Cmdlet-utdata | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell SDK], output
ms.assetid: 547e6695-e936-4cac-a90b-417d0dab393d
caps.latest.revision: 12
ms.openlocfilehash: 3efa98c7aa22fdaee8042bae99282aea0618ef5f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067238"
---
# <a name="types-of-cmdlet-output"></a>Typer av cmdlet-utdata

PowerShell erbjuder flera metoder som kan anropas av cmdlet: ar för att generera utdata. Dessa metoder använder en viss åtgärd för att skriva sina utdata till en specifik dataström, till exempel dataströmmen lyckades eller fel dataströmmen. Den här artikeln beskrivs vilka typer av utdata och de metoder som används för att generera dem.

## <a name="types-of-output"></a>Typer av utdata

### <a name="success-output"></a>Lyckad utdata

Cmdlet: ar kan rapportera lyckades genom att returnera ett objekt som kan bearbetas av nästa kommando i pipelinen. När åtgärden har utförts för cmdlet: en, cmdleten anropar den [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) metod. Vi rekommenderar att du anropar den här metoden i stället för den [System.Console.WriteLine](/dotnet/api/System.Console.WriteLine) eller [System.Management.Automation.Host.PSHostUserInterface.WriteLine](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface.WriteLine) metoder.

Du kan ange en **PassThru** växla parametern för cmdlet: ar som normalt inte returnerar objekt.
När den **PassThru** växlingsparametern har angetts på kommandoraden, cmdleten ombeds att returnera ett-objekt. Ett exempel på en cmdlet som har en **PassThru** parameter, se [Lägg till historik](/powershell/module/Microsoft.PowerShell.Core/Add-History).

### <a name="error-output"></a>Utdata vid fel

Cmdlet: ar kan rapportera fel. När det uppstår ett avslutande fel kan utlöser cmdleten ett undantag. När ett icke-avslutande fel inträffar, cmdleten anropar den [System.Management.Automation.Provider.CmdletProvider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) metod för att skicka en Felpost till dataströmmen fel. Mer information om felrapportering finns i [fel Reporting begrepp](./error-reporting-concepts.md).

### <a name="verbose-output"></a>Utförliga utdata

Cmdlet: ar kan ge värdefull information till dig, medan cmdlet: en är korrekt bearbetar poster genom att anropa den [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) metod. Metoden genererar utförliga meddelanden som indikerar hur åtgärden pågår.

Som standard visas inte utförliga meddelanden. Du kan ange den **utförlig** parameter när cmdleten körs för att visa dessa meddelanden. **Utförlig** är en gemensam parameter som är tillgänglig för alla cmdletar.

### <a name="progress-output"></a>Förlopp

Cmdlet: ar kan ge statusinformation till dig när cmdlet utför uppgifter som tar lång tid att slutföra, till exempel kopiera en åsidosattes rekursivt. Att visa statusinformation cmdleten anropar den [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) metod.

### <a name="debug-output"></a>Utdata för felsökning

Cmdlet: ar kan ge felsökningsmeddelanden som är användbara när du felsöker cmdlet-kod. Visa felsökningsinformation cmdleten anropar den [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) metod.

Som standard visas inte felsökningsmeddelanden. Du kan ange den **felsöka** parameter när cmdleten körs för att visa dessa meddelanden. **Felsöka** är en gemensam parameter som är tillgänglig för alla cmdletar.

### <a name="warning-output"></a>Varning-utdata

Cmdlet: ar kan visa varningsmeddelanden genom att anropa den [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) metod.

Varningsmeddelanden visas som standard. Du kan dock konfigurera varningsmeddelanden genom att använda den `$WarningPreference` variabel eller med hjälp av den **utförlig** och **felsöka** parametrar när cmdlet anropas.

## <a name="displaying-output"></a>Visa utdata

För alla write-metodanrop bestäms det innehåll som visningen av specifika körningsvariabler. Undantaget är den [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) metod. Med dessa variabler kan du de aktuella Skriv anropet på rätt plats i din kod och inte bekymra dig om när eller om utdata visas.

## <a name="accessing-the-output-functionality-of-a-host-application"></a>Åtkomst till utdata-funktionerna i ett program

Du kan också utforma en cmdlet för direkt åtkomst till utdata-funktionerna i ett program till PowerShell-körning. Med värden för API: er som tillhandahålls av PowerShell i stället för [System.Console](/dotnet/api/System.Console) eller [System.Windows.Forms](/dotnet/api/System.Windows.Forms) säkerställer att din cmdlet kommer att fungera med en rad olika värdar. Till exempel: den **powershell.exe** konsolvärden, den **powershell_ise.exe** grafiska värden, PowerShell-fjärrkommunikation värden och tredjeparts-värdar.

## <a name="see-also"></a>Se även

[Fel Reporting begrepp](./error-reporting-concepts.md)

[Cmdlet-översikt](./cmdlet-overview.md)

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)