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
ms.openlocfilehash: 19cc3817016d96e1412a5f3506e9d694ba55b48d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850850"
---
# <a name="creating-a-basic-windows-powershell-provider"></a>Skapa en grundläggande Windows PowerShell-provider

Det här avsnittet är startpunkten för att lära dig hur du skapar en Windows PowerShell-providern. Grundläggande providern som beskrivs här ger metoder för att starta och stoppa providern, och även om den här leverantören inte ger ett sätt att få åtkomst till ett datalager eller för att hämta eller ange data i datalagret kan det tillhandahåller grundläggande funktioner som krävs av alla leverantörer.

Som nämnts tidigare grundläggande providern som beskrivs här implementerar metoderna för att starta och stoppa providern. Windows PowerShell-runtime anropar dessa metoder för att initiera och uninitialize providern.

> [!NOTE]
> Du hittar ett exempel på den här providern i filen AccessDBSampleProvider01.cs som tillhandahålls av Windows PowerShell.

Följande: avsnitt i det här avsnittet

- [Definiera klassen Windows PowerShell-providern](#Defining-the-Windows-PowerShell-Provider-Class)

- [Definiera Provider-specifik statusinformation](#Defining-Provider-Specific-State-Information)

- [Initiering av providern](#Initializing-the-Provider)

- [Starta dynamiska parametrar](#Start-Dynamic-Parameters)

- [Avinitierar providern](#Uninitializing-the-Provider)

- [Kodexempel](#Code-Sample)

- [Testa Windows PowerShell-providern](#Testing-the-Windows-PowerShell-Provider)

## <a name="defining-the-windows-powershell-provider-class"></a>Definiera klassen Windows PowerShell-providern

Det första steget i att skapa en Windows PowerShell-providern är att definiera dess .NET-klass. Den här grundläggande providern definierar en klass med namnet `AccessDBProvider` som härleds från den [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) basklassen.

Vi rekommenderar att du placerar dina providerklasser i en `Providers` namnområdet för ditt API-namnområde, till exempel xxx. PowerShell.Providers. Den här providern använder det `Microsoft.Samples.PowerShell.Provider` namnområdet, där alla exempel i Windows PowerShell-providern körs.

> [!NOTE]
> Klass för en Windows PowerShell-providern måste uttryckligen markeras som offentliga. Klasser som inte har markerats som offentliga som standard till interna och kommer inte att hitta av Windows PowerShell-körningen.

Här är klassdefinitionen för den här grundläggande providern:

[!code-csharp[AccessDBProviderSample01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs#L23-L24 "AccessDBProviderSample01.cs")]

Precis före klassdefinitionen, måste du deklarera den [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attributet med syntaxen [CmdletProvider()].

Du kan ange attributet nyckelord för ytterligare deklarera klassen om det behövs. Observera att den [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribut som deklarerats här innehåller två parametrar. Den första parametern för attributet anger standard-eget namn för providern som användaren kan ändra senare. Den andra parametern anger de Windows PowerShell-definierade funktioner som providern visar Windows PowerShell-runtime under bearbetning av kommandot. De möjliga värdena för funktioner för providern definieras av den [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) uppräkning. Eftersom det här är en bas-provider stöder inga funktioner.

> [!NOTE]
> Det fullständigt kvalificerade namnet på Windows PowerShell-providern innehåller sammansättningsnamnet och andra attribut som bestäms av Windows PowerShell vid registreringen av providern.

## <a name="defining-provider-specific-state-information"></a>Definiera Provider-specifik statusinformation

Den [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) basklass och alla härledda klasser anses tillståndslösa eftersom Windows PowerShell-runtime skapar instanser av providern vid behov. Därför, om din leverantör kräver full kontroll och underhåll av tillstånd för provider-specifik data, den måste härleda en klass från den [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) klass. Den härledda klassen bör definiera medlemmarna som behövs för att upprätthålla tillståndet så att data provider-specifik kan användas när Windows PowerShell-runtime anropar den [System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) metod för att initiera providern.

En Windows PowerShell-providern kan också upprätthålla anslutningsbaserade tillstånd. Läs mer om hur du underhåller anslutningsläge [skapar PowerShell Drive Provider](./creating-a-windows-powershell-drive-provider.md).

## <a name="initializing-the-provider"></a>Initiering av providern

Att initiera providern, Windows PowerShell runtime-anrop i [System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) metod när Windows PowerShell startas. För det mesta din provider kan använda standardimplementering av den här metoden returnerar bara den [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) objekt som beskriver din provider. Men i fall där du vill lägga till ytterligare initieringsinformation bör du implementera egna [System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) metod som returnerar en modifierad version av [ System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) objekt som skickas till din provider. I allmänhet den här metoden ska returnera de angivna [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) objekt skickades till den eller en ändrad [System.Management.Automation.Providerinfo](/dotnet/api/System.Management.Automation.ProviderInfo) objekt som innehåller initieringsinformation om andra.

Den här grundläggande providern åsidosätts inte den här metoden. Följande kod visar dock standardimplementering av den här metoden:

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderStart](Msh_samplesaccessdbprov01#accessdbprov01ProviderStart)]  -->

Providern kan upprätthålla tillståndet för provider-specifik information som beskrivs i [definiera Provider-specifik Data tillstånd](#Defining-Provider-Specific-State-Information). I det här fallet din implementering måste åsidosätta de [System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) metod för att returnera en instans av den härledda klassen.

## <a name="start-dynamic-parameters"></a>Starta dynamiska parametrar

Din provider-implementering av den [System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) metoden kan kräva ytterligare parametrar. I det här fallet providern ska åsidosätta den [System.Management.Automation.Provider.Cmdletprovider.Startdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.StartDynamicParameters) metoden och returnera ett objekt med egenskaper och fält med parsning attribut liknar en cmdlet: en klass eller en [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objekt.

Den här grundläggande providern åsidosätts inte den här metoden. Följande kod visar dock standardimplementering av den här metoden:

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderDynamicParameters](Msh_samplesaccessdbprov01#accessdbprov01ProviderDynamicParameters)]  -->

## <a name="uninitializing-the-provider"></a>Avinitierar providern

Du kan frigöra resurser som använder Windows PowerShell-providern genom din leverantör bör implementera en egen [System.Management.Automation.Provider.Cmdletprovider.Stop*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Stop) metod. Den här metoden anropas av Windows PowerShell-körning för att uninitialize providern i avslutar en session.

Den här grundläggande providern åsidosätts inte den här metoden. Följande kod visar dock standardimplementering av den här metoden:

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesaccessdbprov01#accessdbprov01ProviderStop](Msh_samplesaccessdbprov01#accessdbprov01ProviderStop)]  -->

## <a name="code-sample"></a>Kodexempel

Komplett exempel finns i [AccessDbProviderSample01 kodexempel](./accessdbprovidersample01-code-sample.md).

## <a name="testing-the-windows-powershell-provider"></a>Testa Windows PowerShell-providern

När din Windows PowerShell-provider har registrerats med Windows PowerShell kan testa du den genom att köra cmdletarna stöds på kommandoraden. Kör det nya gränssnittet för den här grundläggande providern och använder den `Get-PSProvider` cmdlet för att hämta listan med providers och kontrollera att providern AccessDb finns.

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

[Skapa Windows PowerShell-Providers](./how-to-create-a-windows-powershell-provider.md)

[Designa din Windows PowerShell-providern](./designing-your-windows-powershell-provider.md)