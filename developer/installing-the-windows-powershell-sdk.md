---
title: Installera Windows PowerShell SDK:n
ms.date: 09/13/2016
ms.topic: article
ms.openlocfilehash: da1b3dbb8a599aee2cdbab9115aedcab0b4c78c9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082489"
---
# <a name="installing-the-windows-powershell-sdk"></a>Installera Windows PowerShell SDK:n

Gäller för: Windows PowerShell 2.0, Windows PowerShell 3.0

Följande avsnitt beskriver hur du installerar PowerShell SDK i olika versioner av Windows.

## <a name="installing-windows-powershell-30-sdk-for-windows-8-and-windows-server-2012"></a>Installera Windows PowerShell 3.0 SDK för Windows 8 och Windows Server 2012

Windows PowerShell 3.0 installeras automatiskt med Windows 8 och Windows Server 2012. Dessutom kan du hämta och installera referenssammansättningar för Windows PowerShell 3.0 ingår i Windows 8 SDK. Dessa sammansättningar kan du skriva cmdlets och providers värd program för Windows PowerShell 3.0. När du installerar Windows SDK för Windows 8 installeras automatiskt Windows PowerShell-sammansättningarna i mappen referens sammansättningen i \Program filer (x86) \Reference Assemblies\Microsoft\WindowsPowerShell\3.0. Mer information finns i Windows 8 SDK hämtningswebbplats. Kodexempel för Windows PowerShell är också tillgängliga på Development Center.
Mer information finns i exemplet för skrivbord teckentabellen på webbplatsen Dev center.

Dessutom Windows PowerShell 3.0 är bakåtkompatibla med Windows PowerShell 2.0 SDK, som innehåller ett antal kodexempel. Mer information om hur du hämtar Windows PowerShell 2.0 SDK finns nedan. (Observera att du inte kan installera Windows PowerShell 2.0 på en Windows 8-plattformen 2.0 kodexemplen är kompatibelt med Windows 8 och Windows PowerShell 3.0,.)

## <a name="installing-windows-powershell-30-sdk-for-windows-7-and-windows-server-2008-r2"></a>Installera Windows PowerShell 3.0 SDK för Windows 7 och Windows Server 2008 R2

Windows 7 och Windows Server 2008 R2 har automatiskt PowerShell 2.0 är installerat. Dessutom kan du installera PowerShell 3.0 på dessa system. (Mer information finns i installera Windows PowerShell.). Enligt beskrivningen ovan, kan du också installera Windows 8 SDK på Windows 7 och Windows Server 2008 R2.

## <a name="installing-windows-powershell-20-sdk-for-windows-7-vista-xp-server-2003-and-server-2008"></a>Installera Windows PowerShell 2.0 SDK för Windows 7, Vista-, XP-, Server 2003- och Server 2008

Windows PowerShell 2.0 SDK innehåller referenssammansättningar som behövs för att skriva cmdlets och providers värdbaserade program och ger C# exempelkoden som du kan använda som startpunkt när du börjar skriva kod.

Se Windows PowerShell 2.0 SDK för att installera denna SDK.

### <a name="reference-assemblies"></a>Referenssammansättningar

Referenssammansättningar installeras på följande plats som standard: c:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\V1.0.

> [!NOTE]
>
> Kod som kompileras mot Windows PowerShell 2.0-sammansättningar kan inte läsas in i Windows PowerShell 1.0-installationer. Dock kan kod kompileras mot Windows PowerShell 1.0-sammansättningar läsas in i Windows PowerShell 2.0-installationer.


### <a name="samples"></a>Exempel

Kodexempel installeras som standard på följande plats: C:\Program Files\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\. Följande avsnitt innehåller en kort beskrivning av vad varje exempel gör.

#### <a name="cmdlet-samples"></a>Cmdlet-exempel

- GetProcessSample01 - visar hur du skriver en enkel cmdlet som hämtar alla processer på den lokala datorn.
- GetProcessSample02 - visar hur du lägger till parametrar till cmdleten. Cmdlet: en tar en eller flera processnamn och returnerar de matchande processerna.
- GetProcessSample03 - visar hur du lägger till parametrar som accepterar indata från pipeline.
- GetProcessSample04 - visar hur du hanterar oändliga fel.
- GetProcessSample05 - visar hur du vill visa en lista över angivna processer.
- Markera objekt – visar hur du skriver ett filter för att välja endast vissa objekt.
- SelectString - visar hur du söker efter filer för angivna mönster.
- StopProcessSample01 - visar hur du implementerar en PassThru-parametern och hur du begär Användarfeedback genom anrop till metoder som ShouldProcess och ShouldContinue. Användarna ange PassThru-parametern när de vill tvinga cmdlet för att returnera ett-objekt
- StopProcessSample02 - visar hur du stoppar en särskild process.
- StopProcessSample03 - visar hur du deklarera alias för parametrar och ge stöd för jokertecken.
- StopProcessSample04 - visar hur du deklarera parameteruppsättningar det objekt som cmdlet: en tar som indata och hur du anger standardparametern inställd på att använda.

#### <a name="remoting-samples"></a>Fjärrkommunikation-exempel

- RemoteRunspace01 - visar hur du skapar ett fjärrkörningsutrymme som används för att upprätta en fjärranslutning.
- RemoteRunspacePool01 - visar hur du skapar poolen fjärrkörningsutrymme och hur du kör flera kommandon samtidigt med hjälp av den här poolen.
- Serialization01 - visar hur du tittar på en befintlig .NET-klass och se till att information från valda offentliga egenskaper för den här klassen bevaras i serialisering/deserialisering.
- Serialization02 - visar hur du tittar på en befintlig .NET-klass och se till att information från instans av den här klassen bevaras i serialisering/deserialisering när informationen inte är tillgänglig i offentliga egenskaper i klassen.
- Serialization03 - visar hur du tittar på en befintlig .NET-klass och se till att instanser av den här klassen och härledda klasser avserialiseras (extraheras) till live .NET-objekt.

#### <a name="event-samples"></a>Händelse-exempel

- Event01 - visar hur du skapar en cmdlet för Händelseregistrering med som härleds från ObjectEventRegistrationBase.
- Event02 - visar hur du visar hur du får meddelanden om Windows PowerShell-händelser som genereras på fjärrdatorer. Det använder händelsen PSEventReceived exponeras via klassen Körningsutrymme.

#### <a name="hosting-application-samples"></a>Som är värd för program-exempel

- Runspace01 - visar hur du använder klassen PowerShell för att köra den `Get-Process` cmdlet synkront.
Den `Get-Process` cmdlet returnerar processen objekt för varje process som körs på den lokala datorn.
- Runspace02 - visar hur du använder klassen PowerShell för att köra den `Get-Process` och `Sort-Object` cmdletar synkront. Den `Get-Process` cmdlet returnerar processen objekt för varje process som körs på den lokala datorn och `Sort-Object` sorterar objekten baserat på deras Id-egenskap. Resultatet av dessa kommandon visas med hjälp av en DataGridView-kontroll.
- Runspace03 - visar hur du använder klassen PowerShell för att köra ett skript synkront och hur du hanterar icke-avslutande fel. Skriptet tar emot en lista över processnamn och hämtar sedan dessa processer. Resultatet av skriptet, inklusive eventuella icke-avslutande fel som genererades när du kör skriptet, visas i ett konsolfönster.
- Runspace04 - visar hur du använder klassen PowerShell för att köra kommandon och hur du fånga upp avslutande fel som kan uppkomma när du kör kommandona. Två kommandon körs och det sista kommandot skickas ett argument för parametern som inte är giltig. Därför kan inga objekt returneras och ett avslutande fel genereras.
- Runspace05 - visar hur du lägger till snapin-modulen till ett InitialSessionState objekt så att cmdleten av snapin-modulen är tillgänglig när körningsutrymmet öppnas. Snapin-modulen innehåller en Get-Proc cmdlet (definieras av exemplet GetProcessSample01) som körs synkront med hjälp av ett PowerShell-objekt.
- Runspace06 - visar hur du lägger till en modul till ett InitialSessionState objekt så att modulen läses in när körningsutrymmet öppnas. Modulen innehåller en Get-Proc cmdlet (definieras av exemplet GetProcessSample02) som körs synkront med hjälp av ett PowerShell-objekt.
- Runspace07 - visar hur du skapar ett körningsutrymme och sedan använda den körningsutrymme för körning synkront två cmdlet: ar med hjälp av ett PowerShell-objekt.
- Runspace08 - visar hur du lägger till och argument pipelinen av ett PowerShell-objekt och hur du kör kommandona synkront.
- Runspace09 - visar hur du lägger till ett skript till pipelinen av ett PowerShell-objekt och hur du kör skriptet asynkront. Händelser används för att hantera utdata från skriptet.
- Runspace10 - visar hur du skapar en standard inledande sessionstillstånd, hur du lägger till en cmdlet i InitialSessionState, hur du skapar ett körningsutrymme som använder det första sessionstillståndet och hur du kör kommandot med hjälp av ett PowerShell-objekt.
- Runspace11 - visar hur du använder klassen ProxyCommand för att skapa en proxy-kommando som anropar en befintlig cmdlet, men begränsar uppsättningen av tillgängliga parametrar. Kommandot proxy läggs sedan till en inledande sessionstillstånd som används för att skapa ett begränsat körningsutrymme. Det innebär att användaren har åtkomst till funktionerna i cmdlet: en endast via kommandot proxy.
- PowerShell01 - visar hur du skapar en begränsad körningsutrymme med hjälp av ett InitialSessionState-objekt.
- PowerShell02 - visar hur du använder en körningsutrymme pool för att köra flera kommandon samtidigt.

#### <a name="host-samples"></a>Host-exempel

- Host01 - visar hur du implementerar ett program som använder en anpassad värd. I det här exemplet skapas ett körningsutrymme som använder anpassade värden och sedan PowerShell-API används för att köra ett skript som anropar ”avsluta”. Värdprogrammet sedan tittar på utdata från skriptet och skriver ut resultaten.
- Host02 - visar hur du skriver ett program som använder Windows PowerShell-runtime tillsammans med implementering av anpassade värden. Värdprogrammet anger kulturen värden till tyska, körs den `Get-Process` cmdlet och visar resultat som du ser dem med hjälp av pwrsh.exe och sedan visar du aktuella datum och tidpunkt på tyska.
- Host03 - visar hur du skapar en interaktiv konsol-baserad värd-App som läser kommandon från kommandoraden, kör kommandona och visar resultatet i konsolen.
- Host04 - visar hur du skapar en interaktiv konsol-baserad värd-App som läser kommandon från kommandoraden, kör kommandona och visar resultatet i konsolen. Den här värdprogrammet stöder också med frågor som används att ange flera val.
- Host05 - visar hur du skapar en interaktiv konsol-baserad värd-App som läser kommandon från kommandoraden, kör kommandona och visar resultatet i konsolen. Den här värdprogrammet stöder också anrop till fjärrdatorer med hjälp av den `Enter-PsSession` och `Exit-PsSession` cmdletar.
- Host06 - visar hur du skapar en interaktiv konsol-baserad värd-App som läser kommandon från kommandoraden, kör kommandona och visar resultatet i konsolen. Det här exemplet använder dessutom Tokenizer-API: er för att ange färgen på texten som anges av användaren.

#### <a name="provider-samples"></a>Provider-exempel

- AccessDBProviderSample01 - visar hur du deklarera en providerklass som härleds direkt från klassen CmdletProvider. Det är här ingår endast för fullständighetens skull.

- AccessDBProviderSample02 - visar hur du skriver över metoderna NewDrive och RemoveDrive för att stödja anrop till den `New-PSDrive` och `Remove-PSDrive` cmdletar. Providerklass i det här exemplet härleds från klassen DriveCmdletProvider.

- AccessDBProviderSample03 - visar hur du skriver över metoderna GetItem och SetItem för att stödja anrop till den `Get-Item` och `Set-Item` cmdletar. Providerklass i det här exemplet härleds från klassen ItemCmdletProvider.

- AccessDBProviderSample04 - visar hur du skriver över behållare metoder för att stödja anrop till den `Copy-Item`, `Get-ChildItem`, `New-Item`, och `Remove-Item` cmdletar. Dessa metoder bör implementeras när datalagret innehåller objekt som är behållare. En behållare är en grupp med underordnade objekt under en gemensam överordnad artikel. Providerklass i det här exemplet härleds från klassen ItemCmdletProvider.

- AccessDBProviderSample05 - visar hur du skriver över behållare metoder för att stödja anrop till den `Move-Item` och `Join-Path` cmdletar. Dessa metoder bör implementeras när användaren behöver för att flytta objekt i en behållare och om datalagret innehåller kapslade behållare. Providerklass i det här exemplet härleds från klassen NavigationCmdletProvider.

- AccessDBProviderSample06 - visar hur du skriva över innehållet metoder för att stödja anrop till den `Clear-Content`, `Get-Content`, och `Set-Content` cmdletar. Dessa metoder bör implementeras när användaren behöver för att hantera innehåll över hur objekten i datalagret. Providerklass i det här exemplet härleds från klassen NavigationCmdletProvider och den implementerar gränssnittet IContentCmdletProvider.
