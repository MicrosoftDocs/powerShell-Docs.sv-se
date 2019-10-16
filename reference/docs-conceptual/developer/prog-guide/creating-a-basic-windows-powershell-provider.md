---
title: Skapa en grundläggande Windows PowerShell-Provider | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- base provider [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], base provider
ms.assetid: 11eeea41-15c8-47ad-9016-0f4b72573305
caps.latest.revision: 7
ms.openlocfilehash: e825581b96f0f33893b38f9f6499dd46a7bf38eb
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72352782"
---
# <a name="creating-a-basic-windows-powershell-provider"></a>Skapa en grundläggande Windows PowerShell-provider

Det här avsnittet är start punkten för att lära dig hur du skapar en Windows PowerShell-Provider. Den grundläggande providern som beskrivs här innehåller metoder för att starta och stoppa providern, men även om denna provider inte ger ett sätt att komma åt ett data lager eller för att hämta eller ange data i data lagret, innehåller den de grundläggande funktioner som krävs av alla leverantörer.

Som tidigare nämnts är den grundläggande providern som beskrivs här implementerar metoder för att starta och stoppa providern. Windows PowerShell-körningen anropar dessa metoder för att initiera och avinitiera providern.

> [!NOTE]
> Du hittar ett exempel på denna provider i AccessDBSampleProvider01.cs-filen från Windows PowerShell.

## <a name="defining-the-windows-powershell-provider-class"></a>Definiera klassen Windows PowerShell-Provider

Det första steget i att skapa en Windows PowerShell-Provider är att definiera dess .NET-klass. Den här grundläggande providern definierar en klass med namnet `AccessDBProvider` som är härledd från Bask Lassen [system. Management. Automation. Provider. Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) .

Vi rekommenderar att du placerar leverantörs klasserna i ett `Providers`-namnområde i API-namnrymden, till exempel xxx. PowerShell. providers. Den här providern använder namn området `Microsoft.Samples.PowerShell.Provider`, där alla exempel på Windows PowerShell-Provider körs.

> [!NOTE]
> Klassen för en Windows PowerShell-Provider måste markeras som offentlig. Klasser som inte är markerade som offentliga kommer att standardvärdet internt och hittas inte av Windows PowerShell-körningsmiljön.

Här är klass definitionen för den här grundläggande providern:

[!code-csharp[AccessDBProviderSample01.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs#L23-L24 "AccessDBProviderSample01.cs")]

Precis som i klass definitionen måste du deklarera attributet [system. Management. Automation. Provider. Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) med syntaxen [CmdletProvider ()].

Du kan ange nyckelord för attribut för att ytterligare deklarera klassen om det behövs. Observera att attributet [system. Management. Automation. Provider. Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) som deklareras här inkluderar två parametrar. Den första parametern för attributet anger standardvänliga namn för providern, som användaren kan ändra senare. Den andra parametern anger de Windows PowerShell-definierade funktioner som providern exponerar för Windows PowerShell-körningsmiljön under kommando bearbetning. Möjliga värden för providerns funktioner definieras av [system. Management. Automation. Provider. ProviderCapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) -uppräkningen. Eftersom det här är en bas leverantör stöder den inte några funktioner.

> [!NOTE]
> Det fullständigt kvalificerade namnet för Windows PowerShell-providern innehåller sammansättnings namnet och andra attribut som fastställs av Windows PowerShell vid registreringen av providern.

## <a name="defining-provider-specific-state-information"></a>Definiera leverantörsspecifik statusinformation

Bask Lassen [system. Management. Automation. Provider. Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) och alla härledda klasser betraktas som tillstånds lösa eftersom Windows PowerShell-körningsmiljön endast skapar Provider-instanser som obligatoriska. Om din Provider kräver fullständig kontroll och tillstånds underhåll för providerspecifika data, måste det därför härleda en klass från klassen [system. Management. Automation. providerInfo](/dotnet/api/System.Management.Automation.ProviderInfo) . Den härledda klassen bör definiera de medlemmar som krävs för att upprätthålla statusen så att de providerspecifika data kan nås när Windows PowerShell-körningsmiljön anropar metoden [system. Management. Automation. Provider. Cmdletprovider. start *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) metoden för att initiera providern.

En Windows PowerShell-Provider kan också upprätthålla anslutnings-baserad status. Mer information om hur du upprätthåller anslutnings status finns i [skapa en PowerShell-enhets leverantör](./creating-a-windows-powershell-drive-provider.md).

## <a name="initializing-the-provider"></a>Providern initieras

För att initiera providern anropar Windows PowerShell-körningen [system. Management. Automation. Provider. Cmdletprovider. start *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) metoden när Windows PowerShell startas. För det mesta kan leverantören använda standard implementeringen av den här metoden, som bara returnerar objektet [system. Management. Automation. providerInfo](/dotnet/api/System.Management.Automation.ProviderInfo) som beskriver din Provider. Men om du vill lägga till ytterligare initierings information bör du implementera en egen [system. Management. Automation. Provider. Cmdletprovider. start *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) -metod som returnerar en modifierad version av [ System. Management. Automation. providerInfo](/dotnet/api/System.Management.Automation.ProviderInfo) -objektet som skickas till din Provider. I allmänhet bör den här metoden returnera det tillhandahållna [system. Management. Automation. providerInfo](/dotnet/api/System.Management.Automation.ProviderInfo) -objektet som skickas till det eller ett ändrat [system. Management. Automation. providerInfo](/dotnet/api/System.Management.Automation.ProviderInfo) -objekt som innehåller annan initierings information.

Den här grundläggande providern åsidosätter inte den här metoden. Följande kod visar dock standard implementeringen av den här metoden:

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderStart](Msh_samplesaccessdbprov01#accessdbprov01ProviderStart)]  -->

Providern kan underhålla den aktuella providerspecifika informationen enligt beskrivningen i [definiera providerspecifika data tillstånd](#defining-provider-specific-state-information). I så fall måste din implementering åsidosätta metoden [system. Management. Automation. Provider. Cmdletprovider. start *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) för att returnera en instans av den härledda klassen.

## <a name="start-dynamic-parameters"></a>Starta dynamiska parametrar

Din leverantörs implementering av metoden [system. Management. Automation. Provider. Cmdletprovider. start *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) kan kräva ytterligare parametrar. I det här fallet bör providern åsidosätta metoden [system. Management. Automation. Provider. Cmdletprovider. Startdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.StartDynamicParameters) och returnera ett objekt som har egenskaper och fält med parsande attribut som liknar en cmdlet-klass eller en [ Objektet system. Management. Automation. Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) .

Den här grundläggande providern åsidosätter inte den här metoden. Följande kod visar dock standard implementeringen av den här metoden:

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderDynamicParameters](Msh_samplesaccessdbprov01#accessdbprov01ProviderDynamicParameters)]  -->

## <a name="uninitializing-the-provider"></a>Providern initieras

Om du vill frigöra resurser som Windows PowerShell-providern använder bör leverantören implementera sin egen [system. Management. Automation. Provider. Cmdletprovider. stop *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Stop) -metod. Den här metoden anropas av Windows PowerShell-körningsmiljön för att avinitiera providern i slutet av en session.

Den här grundläggande providern åsidosätter inte den här metoden. Följande kod visar dock standard implementeringen av den här metoden:

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderStop](Msh_samplesaccessdbprov01#accessdbprov01ProviderStop)]  -->

## <a name="code-sample"></a>Kod exempel

Fullständig exempel kod finns i [kod exemplet för AccessDbProviderSample01](./accessdbprovidersample01-code-sample.md).

## <a name="testing-the-windows-powershell-provider"></a>Testa Windows PowerShell-providern

När din Windows PowerShell-provider har registrerats med Windows PowerShell kan du testa den genom att köra cmdlets som stöds på kommando raden. För den här grundläggande providern kör du det nya gränssnittet och använder cmdleten `Get-PSProvider` för att hämta listan över leverantörer och se till att AccessDb-providern finns.

```powershell
Get-PSProvider
```

Följande utdata visas:

```output
Name                 Capabilities                  Drives
----                 ------------                  ------
AccessDb             None                          {}
Alias                ShouldProcess                 {Alias}
Environment          ShouldProcess                 {Env}
FileSystem           Filter, ShouldProcess         {C, Z}
Function             ShouldProcess                 {function}
Registry             ShouldProcess                 {HKLM, HKCU}
```

## <a name="see-also"></a>Se även

[Skapa Windows PowerShell-leverantörer](./how-to-create-a-windows-powershell-provider.md)

[Designa din Windows PowerShell-Provider](./designing-your-windows-powershell-provider.md)
