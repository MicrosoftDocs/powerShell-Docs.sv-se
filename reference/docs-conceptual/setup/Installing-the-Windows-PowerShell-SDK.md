---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Installera Windows PowerShell SDK:n
ms.assetid: c3636b45-61aa-4720-85f0-58312c4fc8f9
ms.openlocfilehash: fa876bac0c1afac24f93d11dd2e7ecfb1165cf5f
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893546"
---
# <a name="installing-the-windows-powershell-sdk"></a>Installera Windows PowerShell SDK:n

Följande avsnitt beskriver hur du installerar PowerShell SDK i olika versioner av Windows.

## <a name="installing-windows-powershell-30-sdk-for-windows-8-and-windows-server-2012"></a>Installera Windows PowerShell 3.0 SDK för Windows 8 och Windows Server 2012

Windows PowerShell 3.0 installeras automatiskt med Windows 8 och Windows Server 2012.
Dessutom kan du hämta och installera referenssammansättningar för Windows PowerShell 3.0 ingår i Windows 8 SDK.
Dessa sammansättningar kan du skriva cmdlets och providers värd program för Windows PowerShell 3.0.
När du installerar Windows SDK för Windows 8, Windows PowerShell-sammansättningar installeras automatiskt i i mappen referens sammansättningen i `\Program Files (x86)\Reference Assemblies\Microsoft\WindowsPowerShell\3.0`.
Mer information finns i den [hämtningsplats för Windows 8 SDK](https://developer.microsoft.com/en-us/windows/downloads/sdk-archive).
Kodexempel för Windows PowerShell är också tillgängliga på Development Center.
Mer information finns i exemplet för skrivbord teckentabellen på den [Dev center plats](https://code.msdn.microsoft.com:443/windowsdesktop/).

Dessutom Windows PowerShell 3.0 är bakåtkompatibla med Windows PowerShell 2.0 SDK, som innehåller ett antal kodexempel.
Mer information om hur du hämtar Windows PowerShell 2.0 SDK finns nedan.
(Observera att du inte kan installera Windows PowerShell 2.0 på en Windows 8-plattformen 2.0 kodexemplen är kompatibelt med Windows 8 och Windows PowerShell 3.0,.)

## <a name="installing-windows-powershell-30-sdk-for-windows-7-and-windows-server-2008-r2"></a>Installera Windows PowerShell 3.0 SDK för Windows 7 och Windows Server 2008 R2

Windows 7 och Windows Server 2008 R2 har automatiskt PowerShell 2.0 är installerat.
Dessutom kan du installera PowerShell 3.0 på dessa system.
(Mer information finns i [installera Windows PowerShell](Installing-Windows-PowerShell.md).).
Enligt beskrivningen ovan, kan du också installera Windows 8 SDK på Windows 7 och Windows Server 2008 R2.

## <a name="installing-windows-powershell-20-sdk-for-windows-7-vista-xp-server-2003-and-server-2008"></a>Installera Windows PowerShell 2.0 SDK för Windows 7, Vista-, XP-, Server 2003- och Server 2008

Windows PowerShell 2.0 SDK innehåller referenssammansättningar som behövs för att skriva cmdlets och providers värdbaserade program och ger C# exempelkod som du kan använda som startpunkt när du börjar skriva kod.

Detta SDK Se [Windows PowerShell 2.0 SDK](http://www.microsoft.com/en-us/download/details.aspx?id=2560).

## <a name="reference-assemblies"></a>Referenssammansättningar

Referenssammansättningar installeras på följande plats som standard: `c:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\V1.0`.

> [!NOTE] 
> Kod som kompileras mot Windows PowerShell 2.0-sammansättningar kan inte läsas in i Windows PowerShell 1.0-installationer.
> Dock kan kod kompileras mot Windows PowerShell 1.0-sammansättningar läsas in i Windows PowerShell 2.0-installationer.

## <a name="samples"></a>Exempel

Kodexempel som är installerade på följande plats som standard: `C:\Program Files\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\`.

Följande avsnitt innehåller en kort beskrivning av vad varje exempel gör.

## <a name="cmdlet-samples"></a>Cmdlet-exempel

### <a name="getprocesssample01"></a>GetProcessSample01

Visar hur du skriver en enkel cmdlet som hämtar alla processer på den lokala datorn.

### <a name="getprocesssample02"></a>GetProcessSample02

Visar hur du lägger till parametrar till cmdleten.
Cmdlet: en tar en eller flera processnamn och returnerar de matchande processerna.

### <a name="getprocesssample03"></a>GetProcessSample03

Visar hur du lägger till parametrar som accepterar indata från pipeline.

### <a name="getprocesssample04"></a>GetProcessSample04

Visar hur du hanterar oändliga fel.

### <a name="getprocesssample05"></a>GetProcessSample05

Visar hur du vill visa en lista över angivna processer.

### <a name="selectobject"></a>Markera objekt

Visar hur du skriver ett filter för att välja endast vissa objekt.

### <a name="selectstring"></a>SelectString

Visar hur du söker efter filer för angivna mönster.

### <a name="stopprocesssample01"></a>StopProcessSample01

Visar hur du implementerar en *PassThru* parameter och hur du begär Användarfeedback efter anrop till den [ShouldProcess](/dotnet/api/system.management.automation.cmdlet.shouldprocess) och [ShouldContinue](/dotnet/api/system.management.automation.cmdlet.shouldcontinue) metoder.
Användarna ange den *PassThru* parametern när de vill tvinga cmdlet för att returnera ett-objekt

### <a name="stopprocesssample02"></a>StopProcessSample02

Visar hur du stoppar en särskild process.

### <a name="stopprocesssample03"></a>StopProcessSample03

Visar hur du deklarera alias för parametrar och ge stöd för jokertecken.

### <a name="stopprocesssample04"></a>StopProcessSample04

Visar hur du deklarera parameteruppsättningar det objekt som cmdlet: en tar som indata och hur du anger standardparametern inställd på att använda.

## <a name="remoting-samples"></a>Fjärrkommunikation-exempel

### <a name="remoterunspace01"></a>RemoteRunspace01

Visar hur du skapar ett fjärrkörningsutrymme som används för att upprätta en fjärranslutning.

### <a name="remoterunspacepool01"></a>RemoteRunspacePool01

Visar hur du skapar poolen fjärrkörningsutrymme och hur du kör flera kommandon samtidigt med hjälp av den här poolen.

### <a name="serialization01"></a>Serialization01

Visar hur du tittar på en befintlig .NET-klass och se till att information från valda offentliga egenskaper för den här klassen bevaras i serialisering/deserialisering.

### <a name="serialization02"></a>Serialization02

Visar hur du tittar på en befintlig .NET-klass och se till att information från instans av den här klassen bevaras i serialisering/deserialisering när informationen inte är tillgänglig i offentliga egenskaper i klassen.

### <a name="serialization03"></a>Serialization03

Visar hur du tittar på en befintlig .NET-klass och se till att instanser av den här klassen och härledda klasser avserialiseras (extraheras) till live .NET-objekt.

## <a name="event-samples"></a>Händelse-exempel

### <a name="event01"></a>Event01

Visar hur du skapar en cmdlet för Händelseregistrering med som härleds från ObjectEventRegistrationBase.

### <a name="event02"></a>Event02

Visar hur du visar hur du får meddelanden om Windows PowerShell-händelser som genereras på fjärrdatorer.
Den använder händelsen PSEventReceived exponeras via den [Körningsutrymme](/dotnet/api/system.management.automation.runspaces.runspace) klass.

## <a name="hosting-application-samples"></a>Som är värd för program-exempel

### <a name="runspace01"></a>Runspace01

Visar hur du använder den [PowerShell](/dotnet/api/system.management.automation.powershell) klassen för att köra den [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet synkront.
Den [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet returnerar [processen](https://technet.microsoft.com/library/system.diagnostics.process.aspx) objekt för varje process som körs på den lokala datorn.

### <a name="runspace02"></a>Runspace02

Visar hur du använder den [PowerShell](/dotnet/api/system.management.automation.powershell) klassen för att köra den [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) och [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) cmdletar synkront.
Den [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet returnerar [processen](https://technet.microsoft.com/library/system.diagnostics.process.aspx) objekt för varje process som körs på den lokala datorn och `Sort-Object` sorterar objekt baserat på deras [Id](https://technet.microsoft.com/library/system.diagnostics.process.id.aspx) Egenskapen.
Resultatet av dessa kommandon visas med hjälp av en [DataGridView](https://technet.microsoft.com/library/system.windows.forms.datagridview.aspx) kontroll.

### <a name="runspace03"></a>Runspace03

Visar hur du använder den [PowerShell](/dotnet/api/system.management.automation.powershell) klassen för att köra ett skript synkront och hur du hanterar icke-avslutande fel.
Skriptet tar emot en lista över processnamn och hämtar sedan dessa processer.
Resultatet av skriptet, inklusive eventuella icke-avslutande fel som genererades när du kör skriptet, visas i ett konsolfönster.

### <a name="runspace04"></a>Runspace04

Visar hur du använder den [PowerShell](/dotnet/api/system.management.automation.powershell) klassen för att köra kommandon, och hur du catch avslutande fel som kan uppkomma när du kör kommandona.
Två kommandon körs och det sista kommandot skickas ett argument för parametern som inte är giltig.
Därför kan inga objekt returneras och ett avslutande fel genereras.

### <a name="runspace05"></a>Runspace05

Visar hur du lägger till en snapin-modul till en [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate) objektet så att cmdleten av snapin-modulen är tillgänglig när körningsutrymmet öppnas.
Snapin-modulen innehåller en cmdlet Get-processen (definieras av den [GetProcessSample01 exempel](https://technet.microsoft.com/library/ff602028.aspx)) som körs synkront med hjälp av en [PowerShell](/dotnet/api/system.management.automation.powershell) objekt.

### <a name="runspace06"></a>Runspace06

Visar hur du lägger till en modul till en [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate) objektet så att modulen läses in när körningsutrymmet öppnas.
Modulen innehåller en cmdlet Get-processen (definieras av den [GetProcessSample02 exempel](https://technet.microsoft.com/library/ff602027.aspx)) som körs synkront med hjälp av en [PowerShell](/dotnet/api/system.management.automation.powershell) objekt.

### <a name="runspace07"></a>Runspace07

Visar hur du skapar ett körningsutrymme och sedan använda den körningsutrymme för körning synkront två cmdlet: ar med hjälp av en [PowerShell](/dotnet/api/system.management.automation.powershell) objekt.

### <a name="runspace08"></a>Runspace08

Visar hur du lägger till och argument till pipelinen för en [PowerShell](/dotnet/api/system.management.automation.powershell) objekt och hur du kör kommandona synkront.

### <a name="runspace09"></a>Runspace09

Visar hur du lägger till ett skript till pipelinen för en [PowerShell](/dotnet/api/system.management.automation.powershell) objekt och hur du kör skriptet asynkront.
Händelser används för att hantera utdata från skriptet.

### <a name="runspace10"></a>Runspace10

Visar hur du skapar en standard inledande sessionstillstånd, hur du lägger till en cmdlet för att den [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate), hur du skapar ett körningsutrymme som använder det första sessionstillståndet och hur du kör kommandot med hjälp av en [PowerShell](/dotnet/api/system.management.automation.powershell)objekt.

### <a name="runspace11"></a>Runspace11

Visar hur du använder den [ProxyCommand](/dotnet/api/system.management.automation.proxycommand) klassen för att skapa en proxy-kommando som anropar en befintlig cmdlet, men begränsar uppsättningen av tillgängliga parametrar.
Kommandot proxy läggs sedan till en inledande sessionstillstånd som används för att skapa ett begränsat körningsutrymme.
Det innebär att användaren har åtkomst till funktionerna i cmdlet: en endast via kommandot proxy.

### <a name="powershell01"></a>PowerShell01

Visar hur du skapar en begränsad körningsutrymme med hjälp av en [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate) objekt.

### <a name="powershell02"></a>PowerShell02

Visar hur du använder en körningsutrymme pool för att köra flera kommandon samtidigt.

## <a name="host-samples"></a>Host-exempel

### <a name="host01"></a>Host01

Visar hur du implementerar ett program som använder en anpassad värd.
I det här exemplet skapas ett körningsutrymme som använder den anpassa värden, och sedan den [PowerShell](/dotnet/api/system.management.automation.powershell) API används för att köra ett skript som anropar ”avsluta”.
Värdprogrammet sedan tittar på utdata från skriptet och skriver ut resultaten.

### <a name="host02"></a>Host02

Lär dig skriva ett program som använder Windows PowerShell-runtime tillsammans med implementering av anpassade värden.
Värdprogrammet anger kulturen värden till tyska, körs den [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet och visar resultat som du ser dem med hjälp av pwrsh.exe och sedan visar du aktuella datum och tidpunkt på tyska.

### <a name="host03"></a>Host03

Visar hur du skapar en interaktiv konsol-baserad värd-App som läser kommandon från kommandoraden, kör kommandona och visar resultatet i konsolen.

### <a name="host04"></a>Host04

Visar hur du skapar en interaktiv konsol-baserad värd-App som läser kommandon från kommandoraden, kör kommandona och visar resultatet i konsolen.
Den här värdprogrammet stöder också med frågor som används att ange flera val.

### <a name="host05"></a>Host05

Visar hur du skapar en interaktiv konsol-baserad värd-App som läser kommandon från kommandoraden, kör kommandona och visar resultatet i konsolen.
Den här värdprogrammet stöder också anrop till fjärrdatorer med hjälp av den [Enter-PsSession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) och [avsluta-PsSession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) cmdletar.

### <a name="host06"></a>Host06

Visar hur du skapar en interaktiv konsol-baserad värd-App som läser kommandon från kommandoraden, kör kommandona och visar resultatet i konsolen.
Det här exemplet använder dessutom Tokenizer-API: er för att ange färgen på texten som anges av användaren.

## <a name="provider-samples"></a>Provider-exempel

### <a name="accessdbprovidersample01"></a>AccessDBProviderSample01

Visar hur du deklarera en providerklass som härleds direkt från den [CmdletProvider](/dotnet/api/system.management.automation.provider.cmdletprovider) klass.
Det är här ingår endast för fullständighetens skull.

### <a name="accessdbprovidersample02"></a>AccessDBProviderSample02

Visar hur du skriva över den [NewDrive](/dotnet/api/system.management.automation.provider.drivecmdletprovider.newdrive) och [RemoveDrive](/dotnet/api/system.management.automation.provider.drivecmdletprovider.removedrive) metoder som stöder anrop till den `New-PSDrive` och `Remove-PSDrive` cmdletar.
Providerklass i det här exemplet kommer från den [DriveCmdletProvider](/dotnet/api/system.management.automation.provider.drivecmdletprovider) klass.

### <a name="accessdbprovidersample03"></a>AccessDBProviderSample03

Visar hur du skriva över den [GetItem](/dotnet/api/system.management.automation.provider.itemcmdletprovider.getitem) och [SetItem](/dotnet/api/system.management.automation.provider.itemcmdletprovider.setitem) metoder som stöder anrop till den `Get-Item` och `Set-Item` cmdletar.
Providerklass i det här exemplet kommer från den [ItemCmdletProvider](/dotnet/api/system.management.automation.provider.itemcmdletprovider) klass.

### <a name="accessdbprovidersample04"></a>AccessDBProviderSample04

Visar hur du skriver över behållare metoder för att stödja anrop till den `Copy-Item`, `Get-ChildItem`, `New-Item`, och `Remove-Item` cmdletar.
Dessa metoder bör implementeras när datalagret innehåller objekt som är behållare.
En behållare är en grupp med underordnade objekt under en gemensam överordnad artikel.
Providerklass i det här exemplet kommer från den [ItemCmdletProvider](/dotnet/api/system.management.automation.provider.itemcmdletprovider) klass.

### <a name="accessdbprovidersample05"></a>AccessDBProviderSample05

Visar hur du skriver över behållare metoder för att stödja anrop till den `Move-Item` och `Join-Path` cmdletar.
Dessa metoder bör implementeras när användaren behöver för att flytta objekt i en behållare och om datalagret innehåller kapslade behållare.
Providerklass i det här exemplet kommer från den [NavigationCmdletProvider](/dotnet/api/system.management.automation.provider.navigationcmdletprovider) klass.

### <a name="accessdbprovidersample06"></a>AccessDBProviderSample06

Visar hur du skriva över innehållet metoder för att stödja anrop till den `Clear-Content`, `Get-Content`, och `Set-Content` cmdletar.
Dessa metoder bör implementeras när användaren behöver för att hantera innehåll över hur objekten i datalagret.
Providerklass i det här exemplet kommer från den [NavigationCmdletProvider](/dotnet/api/system.management.automation.provider.navigationcmdletprovider) klass och det implementerar den [IContentCmdletProvider](/dotnet/api/system.management.automation.provider.icontentcmdletprovider) gränssnitt.