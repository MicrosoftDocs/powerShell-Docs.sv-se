---
ms.date: 03/30/2020
ms.topic: reference
title: Installera Windows PowerShell SDK:n
description: Installera Windows PowerShell SDK:n
ms.openlocfilehash: 07108ede640b8c6c02bea6d9e2b63116b5b8f969
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92657300"
---
# <a name="installing-the-windows-powershell-sdk"></a>Installera Windows PowerShell SDK:n

Gäller för: Windows PowerShell 2,0, Windows PowerShell 3,0

I följande avsnitt beskrivs hur du installerar PowerShell SDK i olika versioner av Windows.

## <a name="installing-windows-powershell-30-sdk-for-windows-8-and-windows-server-2012"></a>Installera Windows PowerShell 3,0 SDK för Windows 8 och Windows Server 2012

Windows PowerShell 3,0 installeras automatiskt med Windows 8 och Windows Server 2012. Dessutom kan du hämta och installera referens sammansättningarna för Windows PowerShell 3,0 som en del av Windows 8 SDK. Med dessa sammansättningar kan du skriva cmdlets, providers och värd program för Windows PowerShell 3,0. När du installerar Windows SDK för Windows 8 installeras Windows PowerShell-sammansättningarna automatiskt i mappen referens sammansättning i `\Program Files
(x86)\Reference Assemblies\Microsoft\WindowsPowerShell\3.0` . Mer information finns på webbplatsen för hämtning av Windows 8 SDK. Kod exempel för Windows PowerShell är också tillgängliga i databasen [PowerShell-SDK-samples](https://github.com/MicrosoftDocs/powershell-sdk-samples/tree/master/SDK-3.0) .

## <a name="installing-windows-powershell-30-sdk-for-windows-7-and-windows-server-2008-r2"></a>Installera Windows PowerShell 3,0 SDK för Windows 7 och Windows Server 2008 R2

PowerShell 2,0 installeras automatiskt av Windows 7 och Windows Server 2008 R2. Dessutom kan du installera PowerShell 3,0 på dessa system. Du kan också installera Windows 8 SDK på Windows 7 och Windows Server 2008 R2 enligt beskrivningen ovan.

## <a name="installing-windows-powershell-20-sdk-for-windows-7-vista-xp-server-2003-and-server-2008"></a>Installera Windows PowerShell 2,0 SDK för Windows 7, Vista, XP, Server 2003 och Server 2008

Windows PowerShell 2,0 SDK innehåller referens sammansättningar som behövs för att skriva cmdlets, providers och värdbaserade program och den innehåller C# exempel kod som kan användas som start punkt när du börjar skriva kod. Du kan hämta kod exemplen från [https://www.microsoft.com/download/details.aspx?id=2560](https://www.microsoft.com/download/details.aspx?id=2560) .

### <a name="reference-assemblies"></a>Referens sammansättningar

Referens sammansättningar installeras på följande plats som standard: `c:\Program Files\Reference
Assemblies\Microsoft\WindowsPowerShell\V1.0` .

> [!NOTE]
> Kod som kompileras mot Windows PowerShell 2,0-sammansättningar kan inte läsas in i Windows PowerShell 1,0-installationer. Men kod som kompileras mot Windows PowerShell 1,0-sammansättningar kan läsas in i Windows PowerShell 2,0-installationer.

### <a name="samples"></a>Exempel

Kod exempel installeras som standard på följande plats: `C:\Program Files\Microsoft
SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\` . Följande avsnitt innehåller en kort beskrivning av vad varje exempel gör.

#### <a name="cmdlet-samples"></a>Cmdlet-exempel

- GetProcessSample01 – visar hur du skriver en enkel cmdlet som hämtar alla processer på den lokala datorn.
- GetProcessSample02 – visar hur du lägger till parametrar till cmdleten. Cmdleten använder ett eller flera process namn och returnerar de matchande processerna.
- GetProcessSample03 – visar hur du lägger till parametrar som accepterar ininformation från pipelinen.
- GetProcessSample04 – visar hur du hanterar icke-avslutande fel.
- GetProcessSample05 – visar hur du visar en lista över angivna processer.
- MarkeraObjekt-visar hur du skriver ett filter för att endast välja vissa objekt.
- SelectString – visar hur du söker efter angivna mönster i filer.
- StopProcessSample01 – visar hur du implementerar en PassThru-parameter och hur du begär feedback från användare via anrop till ShouldProcess-och ShouldContinue-metoderna. Användare anger parametern PassThru när de vill tvinga cmdleten att returnera ett objekt,
- StopProcessSample02 – visar hur du stoppar en speciell process.
- StopProcessSample03 – visar hur du deklarerar alias för parametrar och hur du stöder jokertecken.
- StopProcessSample04 – visar hur du deklarerar parameter uppsättningar, vilket objekt som cmdleten ska använda som inmatad och hur du anger standard parameter uppsättningen som ska användas.

#### <a name="remoting-samples"></a>Remoting-exempel

- RemoteRunspace01 – visar hur du skapar en fjärran sluten körnings utrymme som används för att upprätta en fjärr anslutning.
- RemoteRunspacePool01 – visar hur du skapar en fjärran sluten körnings utrymme-pool och hur du kör flera kommandon samtidigt med hjälp av den här poolen.
- Serialization01 – visar hur du tittar på en befintlig .NET-klass och ser till att information från valda offentliga egenskaper för den här klassen bevaras i serialisering/deserialisering.
- Serialization02 – visar hur du tittar på en befintlig .NET-klass och ser till att information från en instans av den här klassen bevaras i serialisering/deserialisering om informationen inte finns tillgänglig i klassens offentliga egenskaper.
- Serialization03 – visar hur du tittar på en befintlig .NET-klass och ser till att instanser av den här klassen och härledda klasser deserialiseras (rehydratiseras) i aktiva .NET-objekt.

#### <a name="event-samples"></a>Händelse exempel

- Event01 – visar hur du skapar en cmdlet för händelse registrering genom att härleda från ObjectEventRegistrationBase.
- Event02 – visar hur du visar hur du får meddelanden om Windows PowerShell-händelser som genereras på fjärrdatorer. Den använder PSEventReceived-händelsen som exponeras via körnings utrymme-klassen.

#### <a name="hosting-application-samples"></a>Värdbaserade program exempel

- Runspace01 – visar hur du använder PowerShell-klassen för att köra `Get-Process` cmdleten synkront.
  `Get-Process`Cmdleten returnerar process objekt för varje process som körs på den lokala datorn.
- Runspace02 – visar hur du använder PowerShell-klassen för att köra `Get-Process` och- `Sort-Object` cmdlets synkront. `Get-Process`Cmdleten returnerar process objekt för varje process som körs på den lokala datorn och `Sort-Object` sorterar objekten baserat på deras ID-egenskap. Resultatet av dessa kommandon visas med hjälp av en DataGridView-kontroll.
- Runspace03 – visar hur du använder PowerShell-klassen för att köra ett skript synkront och hur du hanterar icke-avslutande fel. Skriptet tar emot en lista över process namn och hämtar sedan dessa processer. Resultatet av skriptet, inklusive eventuella icke-avslutande fel som genererades när skriptet kördes, visas i konsol fönstret.
- Runspace04 – visar hur du använder PowerShell-klassen för att köra kommandon och hur du fångar upp avslutande fel som genereras när du kör kommandona. Två kommandon körs och det sista kommandot skickas till ett parameter argument som inte är giltigt. Därför returneras inga objekt och ett avslutande fel genereras.
- Runspace05 – visar hur du lägger till en snapin-modul i ett InitialSessionState-objekt så att cmdleten för snapin-modulen är tillgänglig när körnings utrymme öppnas. Snapin-modulen innehåller en Get-Proc-cmdlet (definieras av GetProcessSample01-exemplet) som körs synkront med ett PowerShell-objekt.
- Runspace06 – visar hur du lägger till en modul i ett InitialSessionState-objekt så att modulen läses in när körnings utrymme öppnas. Modulen innehåller en Get-Proc-cmdlet (definieras av GetProcessSample02-exemplet) som körs synkront med ett PowerShell-objekt.
- Runspace07 – visar hur du skapar en körnings utrymme och använder sedan den körnings utrymme för att köra två cmdlets synkront med ett PowerShell-objekt.
- Runspace08 – visar hur du lägger till kommandon och argument i pipelinen för ett PowerShell-objekt och hur du kör kommandona synkront.
- Runspace09 – visar hur du lägger till ett skript i pipelinen för ett PowerShell-objekt och hur du kör skriptet asynkront. Händelser används för att hantera utdata från skriptet.
- Runspace10 – visar hur du skapar ett standard tillstånd för inledande session, hur du lägger till en cmdlet till InitialSessionState, hur du skapar en körnings utrymme som använder det inledande sessionstillståndet och hur du kör kommandot med hjälp av ett PowerShell-objekt.
- Runspace11 – visar hur du använder klassen ProxyCommand för att skapa ett proxy-kommando som anropar en befintlig cmdlet, men begränsar uppsättningen av tillgängliga parametrar. Kommandot proxy läggs sedan till i ett tillstånd för inledande session som används för att skapa en begränsad körnings utrymme. Det innebär att användaren endast kan komma åt funktionaliteten för cmdlet via kommandot proxy.
- PowerShell01 – visar hur du skapar en begränsad körnings utrymme med ett InitialSessionState-objekt.
- PowerShell02 – visar hur du använder en körnings utrymme-pool för att köra flera kommandon samtidigt.

#### <a name="host-samples"></a>Värd exempel

- Host01 – visar hur du implementerar ett värd program som använder en anpassad värd. I det här exemplet skapas en körnings utrymme som använder den anpassade värden och sedan används PowerShell-API: et för att köra ett skript som anropar `exit` . Värd programmet tittar sedan på utdata från skriptet och skriver ut resultaten.
- Host02 – visar hur du skriver ett värd program som använder Windows PowerShell-körningsmiljön tillsammans med en anpassad värd implementering. Värd programmet ställer in värd kulturen på tyska, kör `Get-Process` cmdleten och visar resultaten som du ser dem genom att använda pwrsh.exe och sedan skriva ut aktuella data och tid på tyska.
- Host03 – visar hur du skapar ett interaktivt konsolbaserade värd program som läser kommandon från kommando raden, kör kommandona och visar resultatet i-konsolen.
- Host04 – visar hur du skapar ett interaktivt konsolbaserade värd program som läser kommandon från kommando raden, kör kommandona och visar resultatet i-konsolen. Detta värd program har även stöd för att Visa prompter som gör att användaren kan ange flera alternativ.
- Host05 – visar hur du skapar ett interaktivt konsolbaserade värd program som läser kommandon från kommando raden, kör kommandona och visar resultatet i-konsolen. Detta värd program stöder även anrop till fjärrdatorer med hjälp `Enter-PsSession` av `Exit-PsSession` cmdletarna och.
- Host06 – visar hur du skapar ett interaktivt konsolbaserade värd program som läser kommandon från kommando raden, kör kommandona och visar resultatet i-konsolen. I det här exemplet används dessutom Tokenizer-API: er för att ange färgen på texten som anges av användaren.

#### <a name="provider-samples"></a>Exempel på providers

- AccessDBProviderSample01 – visar hur du deklarerar en leverantörs klass som härleds direkt från CmdletProvider-klassen. Den ingår bara här för fullständighet.

- AccessDBProviderSample02 – visar hur du skriver över NewDrive-och RemoveDrive-metoderna för att stödja anrop `New-PSDrive` till `Remove-PSDrive` cmdletarna och. Provider-klassen i det här exemplet härleds från klassen DriveCmdletProvider.

- AccessDBProviderSample03 – visar hur du skriver över getItem,-och SetItem-metoderna för att stödja anrop `Get-Item` till `Set-Item` cmdletarna och. Provider-klassen i det här exemplet härleds från klassen ItemCmdletProvider.

- AccessDBProviderSample04 – visar hur du skriver över container metoder för att stödja anrop till `Copy-Item` `Get-ChildItem` `New-Item` cmdletarna,, och `Remove-Item` . Dessa metoder bör implementeras när data lagret innehåller objekt som är behållare. En behållare är en grupp underordnade objekt under ett gemensamt överordnat objekt. Provider-klassen i det här exemplet härleds från klassen ItemCmdletProvider.

- AccessDBProviderSample05 – visar hur du skriver över container metoder för att stödja anrop till `Move-Item` `Join-Path` cmdletarna och. Dessa metoder bör implementeras när användaren behöver flytta objekt i en behållare och om data lagret innehåller kapslade behållare. Provider-klassen i det här exemplet härleds från klassen NavigationCmdletProvider.

- AccessDBProviderSample06 – visar hur du skriver över innehålls metoder för att stödja anrop till `Clear-Content` `Get-Content` `Set-Content` cmdletarna, och. Dessa metoder bör implementeras när användaren behöver hantera innehållet i objekten i data lagret. Provider-klassen i det här exemplet härleds från NavigationCmdletProvider-klassen och implementerar IContentCmdletProvider-gränssnittet.
