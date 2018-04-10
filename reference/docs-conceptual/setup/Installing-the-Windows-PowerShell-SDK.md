---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Installera Windows PowerShell SDK:n
ms.assetid: c3636b45-61aa-4720-85f0-58312c4fc8f9
ms.openlocfilehash: 830b054c2cf2b49d935d3d96b79effa7131f6db2
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="installing-the-windows-powershell-sdk"></a>Installera Windows PowerShell SDK:n

Följande avsnitt beskriver hur du installerar PowerShell SDK på olika versioner av Windows.

## <a name="installing-windows-powershell-30-sdk-for-windows-8-and-windows-server-2012"></a>Installera Windows PowerShell 3.0 SDK för Windows 8 och Windows Server 2012

Windows PowerShell 3.0 installeras automatiskt med Windows 8 och Windows Server 2012.
Dessutom kan du hämta och installera referenssammansättningar för Windows PowerShell 3.0 ingår i Windows 8 SDK.
Dessa sammansättningar kan du skriva cmdlets och providers värd för program för Windows PowerShell 3.0.
När du installerar Windows SDK för Windows 8 installeras automatiskt Windows PowerShell-sammansättningarna i mappen referens sammansättningen i \Program filer (x86) \Reference Assemblies\Microsoft\WindowsPowerShell\3.0.
Mer information finns i [hämtningsplatsen för Windows 8 SDK](http://msdn.microsoft.com/windows/hardware/hh852363.aspx).
Windows PowerShell-kodexempel är också tillgängliga på Development Center.
Mer information finns i exempelsida skrivbord kod på den [Dev center-webbplatsen](http://code.msdn.microsoft.com/windowsdesktop/).

Dessutom Windows PowerShell 3.0 är bakåtkompatibla med Windows PowerShell 2.0 SDK, som innehåller ett antal kodexempel.
Mer information om hur du hämtar Windows PowerShell 2.0 SDK finns nedan.
(Observera att du kan installera Windows PowerShell 2.0 på Windows 8-plattformen medan 2.0 kodexemplen är kompatibla med Windows 8 och Windows PowerShell 3.0.)

##<a name="installing-windows-powershell-30-sdk-for-windows-7-and-windows-server-2008-r2"></a>Installera Windows PowerShell 3.0 SDK för Windows 7 och Windows Server 2008 R2

Windows 7 och Windows Server 2008 R2 har automatiskt PowerShell 2.0 installerat.
Dessutom kan du installera PowerShell 3.0 på dessa system.
(Mer information finns i [installera Windows PowerShell](Installing-Windows-PowerShell.md).).
Du kan också installera Windows 8 SDK för Windows 7 och Windows Server 2008 R2 som beskrivs ovan.

## <a name="installing-windows-powershell-20-sdk-for-windows-7-vista-xp-server-2003-and-server-2008"></a>Installera Windows PowerShell 2.0 SDK för Windows 7, Vista, XP, Server 2003 och Server 2008

Windows PowerShell 2.0 SDK innehåller referenssammansättningar som behövs för att skriva cmdlets och providers värd program, samt C# exempelkod som kan användas som utgångspunkt när du börjar skriva kod.

Om du vill installera SDK [Windows PowerShell 2.0 SDK](http://go.microsoft.com/fwlink/?LinkId=184611).

## <a name="reference-assemblies"></a>Referenssammansättningar

Referenssammansättningar installeras som standard på följande plats: `c:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\V1.0`.

> **Obs**: kod kompileras mot Windows PowerShell 2.0-sammansättningar kan inte läsas in i Windows PowerShell 1.0-installationer.
>Dock kan kod kompileras mot Windows PowerShell 1.0-sammansättningar läsas in i Windows PowerShell 2.0-installationer.

## <a name="samples"></a>Exempel

Kodexempel installeras som standard på följande plats: `C:\Program Files\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\`.

Följande avsnitt innehåller en kort beskrivning av vad varje prov gör.

## <a name="cmdlet-samples"></a>Cmdlet-exempel
**GetProcessSample01**

Visar hur du skriver en enkel cmdlet som hämtar alla processer på den lokala datorn.

**GetProcessSample02**

Visar hur du lägger till parametrar för cmdleten.
Cmdlet tar ett eller flera processnamn och returnerar matchande processer.

**GetProcessSample03**

Visar hur du lägger till parametrar som accepterar indata från pipeline.

**GetProcessSample04**

Visar hur du hanterar nonterminating fel.

**GetProcessSample05**

Visar hur du visar en lista över processer som anges.

**Markera objekt**

Visar hur du skriver ett filter för att välja endast vissa objekt.

**SelectString**

Visar hur du söker filer för angivna mönster.

**StopProcessSample01**

Visar hur du implementerar en *PassThru* parametern och hur du begär Användarfeedback genom anrop till den [ShouldProcess](https://technet.microsoft.com/library/system.management.automation.cmdlet.shouldprocess.aspx) och [ShouldContinue](https://technet.microsoft.com/library/system.management.automation.cmdlet.shouldcontinue.aspx) metoder.
Användare anger den *PassThru* parameter när de vill framtvinga för att returnera ett objekt

**StopProcessSample02**

Visar hur du stoppar en specifik process.

**StopProcessSample03**

Visar hur du deklarera alias för parametrar och stöder jokertecken.

**StopProcessSample04**

Visar hur du deklarera parametern anger det objekt som cmdleten tar som indata och hur du anger standardparametern inställd på att använda.

## <a name="remoting-samples"></a>Fjärrkommunikation prover

**RemoteRunspace01**

Visar hur du skapar ett fjärrkörningsutrymme som används för att upprätta en fjärranslutning.

**RemoteRunspacePool01**

Visar hur du skapar en fjärrkörningsutrymme pool och hur du kör flera kommandon samtidigt med hjälp av den här poolen.

**Serialization01**

Visar hur du titta på en befintlig .NET-klass och se till att information från valda offentliga egenskaper för den här klassen bevaras över serialisering/deserialisering.

**Serialization02**

Visar hur du titta på en befintlig .NET-klass och se till att information från en instans av den här klassen bevaras över serialisering/deserialisering när informationen inte är tillgänglig i offentliga egenskaper för klassen.

**Serialization03**

Visar hur du titta på en befintlig .NET-klass och se till att instanser av den här klassen och härledda klasser är avserialiseras (återställd) till live .NET-objekt.

## <a name="event-samples"></a>Händelse-exempel

**Event01**

Visar hur du skapar en cmdlet för Händelseregistrering med härleds från ObjectEventRegistrationBase.

**Event02**

Visar hur visar att ta emot meddelanden om Windows PowerShell-händelser som genereras på fjärrdatorer.
Den använder händelsen PSEventReceived exponeras via den [Runspace](https://technet.microsoft.com/library/system.management.automation.runspaces.runspace.aspx) klass.

## <a name="hosting-application-samples"></a>Värd för program-exempel

**Runspace01**

Visar hur du använder den [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) klass som ska köras den [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) cmdlet synkront.
Den [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) cmdlet returnerar [processen](https://technet.microsoft.com/library/system.diagnostics.process.aspx) objekt för varje process som körs på den lokala datorn.

**Runspace02**

Visar hur du använder den [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) klass som ska köras den [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) och [Sort-Object](http://go.microsoft.com/fwlink/?LinkID=113403) cmdlets synkront.
Den [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) cmdlet returnerar [processen](https://technet.microsoft.com/library/system.diagnostics.process.aspx) objekt för varje bearbeta körs på den lokala datorn och objektet Sortera Sorterar objekt baserat på deras [Id](https://technet.microsoft.com/library/system.diagnostics.process.id.aspx) egenskapen.
Resultatet av dessa kommandon visas med hjälp av en [DataGridView](https://technet.microsoft.com/library/system.windows.forms.datagridview.aspx) kontroll.

**Runspace03**

Visar hur du använder den [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) klassen för att köra ett skript synkront och hur du hantera icke avslutande fel.
Skriptet tar emot en lista över processnamn och hämtar sedan dessa processer.
Resultaten av skriptet, inklusive icke avslutar felmeddelanden som genererats när du kör skriptet visas i konsolfönstret.

**Runspace04**

Visar hur du använder den [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) klassen för att köra kommandon och hur du catch avslutande fel som uppstår när du kör kommandona.
Två kommandon körs och det sista kommandot skickas ett argument för parameter som inte är giltig.
Därför kan inga objekt returneras och ett avslutande fel genereras.

**Runspace05**

Visar hur du lägger till en snapin-modul i en [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx) objekt så att cmdleten i snapin-modulen är tillgänglig när runspace öppnas.
Snapin-modulen ger en cmdlet Get-procedur (definieras av den [GetProcessSample01 exempel](https://technet.microsoft.com/library/ff602028.aspx)) som körs synkront med hjälp av en [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) objekt.

**Runspace06**

Visar hur du lägger till en modul till en [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx) objekt så att modulen är inläst när runspace öppnas.
Modulen innehåller en cmdlet Get-procedur (definieras av den [GetProcessSample02 exempel](https://technet.microsoft.com/library/ff602027.aspx)) som körs synkront med hjälp av en [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) objekt.

**Runspace07**

Visar hur du skapar ett körningsutrymme och sedan använda den runspace för att köra två cmdlets synkront med hjälp av en [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) objekt.

**Runspace08**

Visar hur du lägger till kommandon och argument för pipeline för en [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) objekt och hur du kör kommandona synkront.

**Runspace09**

Visar hur du lägger till ett skript för pipeline för en [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) objekt och hur du kör skriptet asynkront.
Händelser som används för att hantera utdata från skriptet.

**Runspace10**

Visar hur du skapar en standard inledande sessionstillstånd, hur du lägger till en cmdlet till den [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx), hur du skapar en runspace som använder det första sessionstillståndet och hur du kör kommandot med hjälp av en [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx)objekt.

**Runspace11**

Visar hur du använder den [ProxyCommand](https://technet.microsoft.com/library/system.management.automation.proxycommand.aspx) klassen för att skapa en proxy-kommando som anropar en befintlig cmdlet, men begränsar uppsättningen av tillgängliga parametrar.
Kommandot proxy läggs sedan till en inledande sessionstillstånd som används för att skapa ett begränsat körningsutrymme.
Det innebär att användaren har åtkomst till funktionerna i cmdleten endast via kommandot proxy.

**PowerShell01**

Visar hur du skapar ett begränsat körningsutrymme som använder en [InitialSessionState](https://technet.microsoft.com/library/system.management.automation.runspaces.initialsessionstate.aspx) objekt.

**PowerShell02**

Visar hur du använder en runspace pool för att köra flera kommandon samtidigt.

## <a name="host-samples"></a>Host-exempel

**Host01**

Visar hur du implementerar en värdprogram som använder en anpassad värd.
I det här exemplet skapas en runspace som använder anpassade värden, och sedan den [PowerShell](https://technet.microsoft.com/library/system.management.automation.powershell.aspx) API används för att köra ett skript som anropar ”avsluta”.
Värdprogrammet sedan tittar på utdata från skriptet och skriver ut resultatet.

**Host02**

Visar hur du skriver ett program som använder Windows PowerShell-körningsmiljön tillsammans med en anpassad värd-implementering.
Värdprogrammet anger värden kulturen tyska, körs det [Get-Process](http://go.microsoft.com/fwlink/?LinkId=113324) cmdlet och visar resultatet som du ser dem med hjälp av pwrsh.exe och sedan visar aktuella data och tid i tyska.

**Host03**

Visar hur du skapar en interaktiv konsolbaserad värdprogrammet som läser kommandon från kommandoraden, kör kommandon och visar resultatet i konsolen.

**Host04**

Visar hur du skapar en interaktiv konsolbaserad värdprogrammet som läser kommandon från kommandoraden, kör kommandon och visar resultatet i konsolen.
Den här värdprogrammet har också stöd för visning prompter som används att ange flera alternativ.

**Host05**

Visar hur du skapar en interaktiv konsolbaserad värdprogrammet som läser kommandon från kommandoraden, kör kommandon och visar resultatet i konsolen.
Den här värdprogrammet stöder också anrop till fjärrdatorer genom att använda den [Enter-PsSession](http://go.microsoft.com/fwlink/?LinkId=135210) och [avsluta-PsSession](http://go.microsoft.com/fwlink/?LinkId=135212) cmdlets.

**Host06**

Visar hur du skapar en interaktiv konsolbaserad värdprogrammet som läser kommandon från kommandoraden, kör kommandon och visar resultatet i konsolen.
Det här exemplet använder dessutom Tokenizer-API: er för att ange färgen på texten som anges av användaren.

## <a name="provider-samples"></a>Provider-exempel

**AccessDBProviderSample01**

Visar hur du deklarera en providerklass som härleds direkt från den [CmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.cmdletprovider.aspx) klass.
Det är här ingår endast för fullständighetens skull.

**AccessDBProviderSample02**

Visar hur du skriver över den [NewDrive](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.newdrive.aspx) och [RemoveDrive](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.removedrive.aspx) metoder som stöder anrop till ny PSDrive och ta bort PSDrive-cmdlets.
Providerklassen i det här exemplet härleds från den [DriveCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.drivecmdletprovider.aspx) klass.

**AccessDBProviderSample03**

Visar hur du skriver över den [GetItem](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.getitem.aspx) och [SetItem](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.setitem.aspx) metoder som stöder anrop till cmdletarna Get-objekt och Set-objekt.
Providerklassen i det här exemplet härleds från den [ItemCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.aspx) klass.

**AccessDBProviderSample04**

Visar hur du skriver över behållaren metoder för att stödja anrop till Copy-Item, Get-ChildItem New-objekt och ta bort objektet cmdlets.
Dessa metoder ska genomföras när datalagret innehåller objekt som är behållare.
En behållare är en grupp av underordnade objekt under en gemensam överordnad artikel.
Providerklassen i det här exemplet härleds från den [ItemCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.itemcmdletprovider.aspx) klass.

**AccessDBProviderSample05**

Visar hur du skriva över behållaren metoder för att stödja anrop till flytta objekt och Join-Path-cmdlets.
Dessa metoder bör genomföras när användaren behöver flytta objekt i en behållare och om datalagret innehåller kapslade behållare.
Providerklassen i det här exemplet härleds från den [NavigationCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.navigationcmdletprovider.aspx) klass.

**AccessDBProviderSample06**

Visar hur du skriva över innehållet metoder för att stödja anrop till Rensa-innehåll, Get-innehåll och Set-Content-cmdlets.
Dessa metoder ska genomföras när användaren behöver hantera innehåll över hur objekten i datalagret.
Providerklassen i det här exemplet härleds från den [NavigationCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.navigationcmdletprovider.aspx) klassen och implementerar den [IContentCmdletProvider](https://technet.microsoft.com/library/system.management.automation.provider.icontentcmdletprovider.aspx) gränssnitt.