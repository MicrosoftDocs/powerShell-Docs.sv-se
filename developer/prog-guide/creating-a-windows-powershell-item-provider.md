---
title: Skapa en Windows PowerShell-dataprovider | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- item providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], item provider
ms.assetid: a5a304ce-fc99-4a5b-a779-de7d85e031fe
caps.latest.revision: 6
ms.openlocfilehash: c60da62a06fcb40b6970d4209e991e57af733f33
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71323200"
---
# <a name="creating-a-windows-powershell-item-provider"></a>Skapa en Windows PowerShell-objektprovider

I det här avsnittet beskrivs hur du skapar en Windows PowerShell-provider som kan manipulera data i ett data lager. I det här avsnittet kallas elementen för data i arkivet som "objekt" i data lagret. Därför kallas en provider som kan manipulera data i arkivet som en Windows PowerShell-DataProvider.

> [!NOTE]
> Du kan ladda ned C# käll filen (AccessDBSampleProvider03.CS) för den här providern med hjälp av Microsoft Windows Software Development Kit för Windows Vista och .NET Framework 3,0 Runtime-komponenter. Instruktioner för hämtning finns i [Installera Windows PowerShell och ladda ned Windows POWERSHELL SDK](/powershell/developer/installing-the-windows-powershell-sdk).
>
> De hämtade källfilerna är tillgängliga i  **\<PowerShell-exemplen >** Directory.
>
> Mer information om implementeringar av andra Windows PowerShell-leverantörer finns i [utforma din Windows PowerShell-Provider](./designing-your-windows-powershell-provider.md).

Windows PowerShell-dataleverantören som beskrivs i det här avsnittet hämtar data objekt från en Access-databas. I det här fallet är ett "objekt" antingen en tabell i Access-databasen eller en rad i en tabell.

## <a name="defining-the-windows-powershell-item-provider-class"></a>Definiera Windows PowerShell-klassen för objekt leverantörer

En Windows PowerShell-dataprovider måste definiera en .NET-klass som är härledd från Bask Lassen [system. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) . Följande är klass definitionen för den artikel leverantör som beskrivs i det här avsnittet.

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L34-L36 "AccessDBProviderSample03.cs")]

Observera att i den här klass definitionen innehåller attributet [system. Management. Automation. Provider. Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) två parametrar. Den första parametern anger ett användarvänligt namn för den provider som används av Windows PowerShell. Den andra parametern anger de Windows PowerShell-funktioner som providern exponerar för Windows PowerShell-körningsmiljön under kommando bearbetning. För den här providern finns det inga Windows PowerShell-funktioner som har lagts till.

## <a name="defining-base-functionality"></a>Definiera grundläggande funktioner

Enligt beskrivningen i [utforma din Windows PowerShell-Provider](./designing-your-windows-powershell-provider.md)härleds klassen [system. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) från flera andra klasser som tillhandahöll olika funktioner i providern. En Windows PowerShell-dataprovider måste därför definiera alla funktioner som tillhandahålls av dessa klasser.

Mer information om hur du implementerar funktioner för att lägga till datorspecifik initierings information och för att frigöra resurser som används av providern finns i [skapa en grundläggande Windows PowerShell-Provider](./creating-a-basic-windows-powershell-provider.md). De flesta leverantörer, inklusive providern som beskrivs här, kan dock använda standard implementeringen av den här funktionen som tillhandahålls av Windows PowerShell.

Innan Windows PowerShell-dataleverantören kan manipulera objekten i arkivet måste den implementera metoderna i Bask Lassen [system. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) för att få åtkomst till data lagret. Mer information om hur du implementerar den här klassen finns i [skapa en provider för Windows PowerShell-enheter](./creating-a-windows-powershell-drive-provider.md).

## <a name="checking-for-path-validity"></a>Söker efter Sök vägs giltighet

När du letar efter ett data objekt, tillhandahåller Windows PowerShell-körningsmiljön en Windows PowerShell-sökväg till providern, enligt definitionen i avsnittet "PSPath-koncept" i [hur Windows PowerShell fungerar](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58). En Windows PowerShell-dataprovider måste verifiera syntaktisk och semantisk giltigheten för alla vägar som skickas till den genom att implementera metoden [system. Management. Automation. Provider. Itemcmdletprovider. Isvalidpath *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) . Den här metoden `true` returnerar om sökvägen är giltig och `false` annars. Tänk på att implementeringen av den här metoden inte ska verifiera att objektet finns på sökvägen, men bara att sökvägen är syntaktiskt och semantiskt korrekt.

Här är implementeringen av metoden [system. Management. Automation. Provider. Itemcmdletprovider. Isvalidpath *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) för den här providern. Observera att den här implementeringen anropar en NormalizePath Helper-metod för att konvertera alla avgränsare i sökvägen till en enhetlig.

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L274-L298 "AccessDBProviderSample03.cs")]

## <a name="determining-if-an-item-exists"></a>Avgöra om ett objekt finns

När du har verifierat sökvägen måste Windows PowerShell-körningsmiljön avgöra om ett data objekt finns på den sökvägen. För att stödja den här typen av fråga implementerar Windows PowerShell-dataprovidern [system. Management. Automation. Provider. Itemcmdletprovider. Itemexists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) -metoden. Den här metoden `true` returnerar ett objekt som finns på den angivna sökvägen `false` och (standard).

Här är implementeringen av metoden [system. Management. Automation. Provider. Itemcmdletprovider. Itemexists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) för den här providern. Observera att den här metoden anropar metoderna PathIsDrive, ChunkPath och GetTable Helper och använder ett Provider definierat DatabaseTableInfo-objekt.

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L229-L267 "AccessDBProviderSample03.cs")]

#### <a name="things-to-remember-about-implementing-itemexists"></a>Saker att komma ihåg om att implementera ItemExists

Följande villkor kan gälla för din implementering av [system. Management. Automation. Provider. Itemcmdletprovider. Itemexists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists):

- När du definierar Provider-klassen kan en Windows PowerShell-dataprovider deklarera ExpandWildcards, filtrera, ta med eller undanta från, från [system. Management. Automation. Provider. ProviderCapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) -uppräkningen. I dessa fall måste implementeringen av metoden [system. Management. Automation. Provider. Itemcmdletprovider. Itemexists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) se till att den sökväg som skickas till metoden uppfyller kraven för de angivna funktionerna. För att göra detta ska metoden komma åt lämplig egenskap, till exempel [system. Management. Automation. Provider. Cmdletprovider. exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) och [system. Management. Automation. Provider. Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) egenskaper.

- Implementeringen av den här metoden bör hantera alla former av åtkomst till objektet som kan göra objektet synligt för användaren. Om en användare till exempel har Skriv behörighet till en fil via fil systemets Provider (som tillhandahålls av Windows PowerShell), men inte Läs åtkomst, finns filen fortfarande och [system. Management. Automation. Provider. Itemcmdletprovider. Itemexists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) returnerar `true`. Din implementering kan kräva att ett överordnat objekt kontrol leras för att se om det underordnade objektet kan räknas upp.

## <a name="attaching-dynamic-parameters-to-the-test-path-cmdlet"></a>Bifoga dynamiska parametrar till test-Path-cmdleten

Ibland kräver cmdleten som anropar [system. Management. Automation. Provider. Itemcmdletprovider. Itemexists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) ytterligare parametrar som anges dynamiskt vid körning. `Test-Path` För att tillhandahålla dessa dynamiska parametrar måste Windows PowerShell-dataleverantören implementera metoden [system. Management. Automation. Provider. Itemcmdletprovider. Itemexistsdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExistsDynamicParameters) . Den här metoden hämtar dynamiska parametrar för objektet på den angivna sökvägen och returnerar ett objekt som har egenskaper och fält med parsande attribut som liknar en cmdlet-klass eller en [system. Management. Automation. Runtimedefinedparameterdictionary ](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)objekt. Windows PowerShell-körningsmiljön använder det returnerade objektet för att lägga till parametrarna `Test-Path` i cmdleten.

Den här Windows PowerShell-dataprovidern implementerar inte den här metoden. Följande kod är dock standard implementeringen av den här metoden.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovideritemexistdynamicparameters](Msh_samplestestcmdlets#testprovideritemexistdynamicparameters)]  -->

## <a name="retrieving-an-item"></a>Hämtar ett objekt

För att hämta ett objekt, måste Windows PowerShell-dataleverantören åsidosätta metoden [system. Management. Automation. Provider. Itemcmdletprovider. getItem, *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) för att `Get-Item` stödja anrop från cmdleten. Med den här metoden skrivs objektet med hjälp av metoden [system. Management. Automation. Provider. Cmdletprovider. Writeitemobject *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) .

Här är implementeringen av metoden [system. Management. Automation. Provider. Itemcmdletprovider. getItem, *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) för den här providern. Observera att den här metoden använder GetTable-och GetRow-hjälp metoder för att hämta objekt som är antingen tabeller i Access-databasen eller-raderna i en data tabell.

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L132-L163 "AccessDBProviderSample03.cs")]

#### <a name="things-to-remember-about-implementing-getitem"></a>Saker att komma ihåg om att implementera getItem,

Följande villkor kan gälla för en implementering av [system. Management. Automation. Provider. Itemcmdletprovider. getItem, *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem):

- När du definierar Provider-klassen kan en Windows PowerShell-dataprovider deklarera ExpandWildcards, filtrera, ta med eller undanta från, från [system. Management. Automation. Provider. ProviderCapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) -uppräkningen. I dessa fall måste implementeringen av [system. Management. Automation. Provider. Itemcmdletprovider. getItem, *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) se till att den sökväg som skickas till metoden uppfyller dessa krav. För att göra detta ska metoden komma åt lämplig egenskap, till exempel [system. Management. Automation. Provider. Cmdletprovider. exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) och [system. Management. Automation. Provider. Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) egenskaper.

- Åsidosättningar av den här metoden bör som standard inte hämta objekt som är allmänt dolda från användaren, om inte egenskapen [system. Management. Automation. Provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) har angetts till `true`. Till exempel kontrollerar [system. Management. Automation. Provider. Itemcmdletprovider. getItem, *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) -metoden för fil system providern [system. Management. Automation. Provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) -egenskapen innan den försöker anropa [System. Management. Automation. Provider. Cmdletprovider. Writeitemobject *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) för dolda filer eller systemfiler.

## <a name="attaching-dynamic-parameters-to-the-get-item-cmdlet"></a>Koppla dynamiska parametrar till cmdleten Get-Item

Ibland kräver `Get-Item` cmdleten ytterligare parametrar som anges dynamiskt vid körning. För att tillhandahålla dessa dynamiska parametrar måste Windows PowerShell-dataleverantören implementera metoden [system. Management. Automation. Provider. Itemcmdletprovider. Getitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) . Den här metoden hämtar dynamiska parametrar för objektet på den angivna sökvägen och returnerar ett objekt som har egenskaper och fält med parsande attribut som liknar en cmdlet-klass eller en [system. Management. Automation. Runtimedefinedparameterdictionary ](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)objekt. Windows PowerShell-körningsmiljön använder det returnerade objektet för att lägga till parametrarna `Get-Item` i cmdleten.

Den här providern implementerar inte den här metoden. Följande kod är dock standard implementeringen av den här metoden.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetitemdynamicparameters](Msh_samplestestcmdlets#testprovidergetitemdynamicparameters)]  -->

## <a name="setting-an-item"></a>Ange ett objekt

Om du vill ange ett objekt måste Windows PowerShell-dataleverantören åsidosätta metoden [system. Management. Automation. Provider. Itemcmdletprovider. setItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) för att stödja `Set-Item` anrop från cmdleten. Den här metoden anger värdet för objektet på den angivna sökvägen.

Den här providern ger ingen åsidosättning för metoden [system. Management. Automation. Provider. Itemcmdletprovider. setItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) . Följande är dock standard implementeringen av den här metoden.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidersetitem](Msh_samplestestcmdlets#testprovidersetitem)]  -->

#### <a name="things-to-remember-about-implementing-setitem"></a>Saker att komma ihåg om att implementera SetItem

Följande villkor kan gälla för din implementering av [system. Management. Automation. Provider. Itemcmdletprovider. setItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem):

- När du definierar Provider-klassen kan en Windows PowerShell-dataprovider deklarera ExpandWildcards, filtrera, ta med eller undanta från, från [system. Management. Automation. Provider. ProviderCapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) -uppräkningen. I dessa fall måste implementeringen av [system. Management. Automation. Provider. Itemcmdletprovider. setItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) se till att den sökväg som skickas till metoden uppfyller dessa krav. För att göra detta ska metoden komma åt lämplig egenskap, till exempel [system. Management. Automation. Provider. Cmdletprovider. exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) och [system. Management. Automation. Provider. Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) egenskaper.

- Åsidosättningar av den här metoden bör som standard inte ange eller skriva objekt som är dolda från användaren, om inte egenskapen [system. Management. Automation. Provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) anges till `true`. Ett fel bör skickas till metoden [system. Management. Automation. Provider. Cmdletprovider. WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) om sökvägen representerar ett dolt objekt och [system. Management. Automation. Provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) har angetts till `false`.

- Din implementering av metoden [system. Management. Automation. Provider. Itemcmdletprovider. setItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) måste anropa [system. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) och verifiera dess retur värde innan du gör eventuella ändringar i data lagret. Den här metoden används för att bekräfta körning av en åtgärd när en ändring görs i data lagret, t. ex. borttagning av filer. Metoden [system. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) skickar namnet på resursen som ska ändras till användaren, med Windows PowerShell-körningsmiljön med hänsyn till alla kommando rads inställningar eller variabler i bestämmer vad som ska visas.

  Efter att anropet till [system. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) returnerar `true`, anropar [metoden system. Management. Automation. Provider. Itemcmdletprovider. setItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) [metoden Metoden system. Management. Automation. Provider. Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) . Den här metoden skickar ett meddelande till användaren för att tillåta feedback för att kontrol lera om åtgärden ska fortsätta. Anropet till [system. Management. Automation. Provider. Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) tillåter ytterligare kontroll av potentiellt skadliga system ändringar.

## <a name="retrieving-dynamic-parameters-for-setitem"></a>Hämtar dynamiska parametrar för SetItem

Ibland kräver `Set-Item` cmdleten ytterligare parametrar som anges dynamiskt vid körning. För att tillhandahålla dessa dynamiska parametrar måste Windows PowerShell-dataleverantören implementera metoden [system. Management. Automation. Provider. Itemcmdletprovider. Setitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) . Den här metoden hämtar dynamiska parametrar för objektet på den angivna sökvägen och returnerar ett objekt som har egenskaper och fält med parsande attribut som liknar en cmdlet-klass eller en [system. Management. Automation. Runtimedefinedparameterdictionary ](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)objekt. Windows PowerShell-körningsmiljön använder det returnerade objektet för att lägga till parametrarna `Set-Item` i cmdleten.

Den här providern implementerar inte den här metoden. Följande kod är dock standard implementeringen av den här metoden.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidersetitemdynamicparameters](Msh_samplestestcmdlets#testprovidersetitemdynamicparameters)]  -->

## <a name="clearing-an-item"></a>Rensa ett objekt

För att rensa ett objekt implementerar Windows PowerShell-dataprovidern [system. Management. Automation. Provider. Itemcmdletprovider. Clearitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) -metoden för att stödja anrop `Clear-Item` från cmdleten. Med den här metoden raderas dataobjektet vid den angivna sökvägen.

Den här providern implementerar inte den här metoden. Följande kod är dock standard implementeringen av den här metoden.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderclearitem](Msh_samplestestcmdlets#testproviderclearitem)]  -->

#### <a name="things-to-remember-about-implementing-clearitem"></a>Saker att komma ihåg om att implementera ClearItem

Följande villkor kan gälla för en implementering av [system. Management. Automation. Provider. Itemcmdletprovider. Clearitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem):

- När du definierar Provider-klassen kan en Windows PowerShell-dataprovider deklarera ExpandWildcards, filtrera, ta med eller undanta från, från [system. Management. Automation. Provider. ProviderCapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) -uppräkningen. I dessa fall måste implementeringen av [system. Management. Automation. Provider. Itemcmdletprovider. Clearitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) se till att den sökväg som skickas till metoden uppfyller dessa krav. För att göra detta ska metoden komma åt lämplig egenskap, till exempel [system. Management. Automation. Provider. Cmdletprovider. exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) och [system. Management. Automation. Provider. Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) egenskaper.

- Åsidosättningar av den här metoden bör som standard inte ange eller skriva objekt som är dolda från användaren, om inte egenskapen [system. Management. Automation. Provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) anges till `true`. Ett fel bör skickas till metoden [system. Management. Automation. Provider. Cmdletprovider. WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) om sökvägen representerar ett objekt som är dolt från användaren och [system. Management. Automation. Provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) är Ange till `false`.

- Din implementering av metoden [system. Management. Automation. Provider. Itemcmdletprovider. setItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) måste anropa [system. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) och verifiera dess retur värde innan du gör eventuella ändringar i data lagret. Den här metoden används för att bekräfta körning av en åtgärd när en ändring görs i data lagret, t. ex. borttagning av filer. Metoden [system. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) skickar namnet på resursen som ska ändras till användaren, med Windows PowerShell-körningsmiljön och hanterar alla kommando rads inställningar eller variabler i bestämmer vad som ska visas.

  Efter att anropet till [system. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) returnerar `true`, anropar [metoden system. Management. Automation. Provider. Itemcmdletprovider. setItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) [metoden Metoden system. Management. Automation. Provider. Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) . Den här metoden skickar ett meddelande till användaren för att tillåta feedback för att kontrol lera om åtgärden ska fortsätta. Anropet till [system. Management. Automation. Provider. Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) tillåter ytterligare kontroll av potentiellt skadliga system ändringar.

## <a name="retrieve-dynamic-parameters-for-clearitem"></a>Hämta dynamiska parametrar för ClearItem

Ibland kräver `Clear-Item` cmdleten ytterligare parametrar som anges dynamiskt vid körning. För att tillhandahålla dessa dynamiska parametrar måste Windows PowerShell-dataleverantören implementera metoden [system. Management. Automation. Provider. Itemcmdletprovider. Clearitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) . Den här metoden hämtar dynamiska parametrar för objektet på den angivna sökvägen och returnerar ett objekt som har egenskaper och fält med parsande attribut som liknar en cmdlet-klass eller en [system. Management. Automation. Runtimedefinedparameterdictionary ](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)objekt. Windows PowerShell-körningsmiljön använder det returnerade objektet för att lägga till parametrarna `Clear-Item` i cmdleten.

Den här objekt leverantören implementerar inte den här metoden. Följande kod är dock standard implementeringen av den här metoden.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderclearitemdynamicparameters](Msh_samplestestcmdlets#testproviderclearitemdynamicparameters)]  -->

## <a name="performing-a-default-action-for-an-item"></a>Utföra en standard åtgärd för ett objekt

En Windows PowerShell-dataprovider kan implementera metoden [system. Management. Automation. Provider. Itemcmdletprovider. Invokedefaultaction *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) för att stödja anrop från `Invoke-Item` cmdleten, vilket gör att providern kan utföra en standard åtgärd för objektet på den angivna sökvägen. Fil Systems leverantören kan till exempel använda den här metoden för att anropa ShellExecute för ett enskilt objekt.

Den här providern implementerar inte den här metoden. Följande kod är dock standard implementeringen av den här metoden.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinvokedefaultaction](Msh_samplestestcmdlets#testproviderinvokedefaultaction)]  -->

#### <a name="things-to-remember-about-implementing-invokedefaultaction"></a>Saker att komma ihåg om att implementera InvokeDefaultAction

Följande villkor kan gälla för en implementering av [system. Management. Automation. Provider. Itemcmdletprovider. Invokedefaultaction *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction):

- När du definierar Provider-klassen kan en Windows PowerShell-dataprovider deklarera ExpandWildcards, filtrera, ta med eller undanta från, från [system. Management. Automation. Provider. ProviderCapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) -uppräkningen. I dessa fall måste implementeringen av [system. Management. Automation. Provider. Itemcmdletprovider. Invokedefaultaction *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) se till att den sökväg som skickas till metoden uppfyller dessa krav. För att göra detta ska metoden komma åt lämplig egenskap, till exempel [system. Management. Automation. Provider. Cmdletprovider. exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) och [system. Management. Automation. Provider. Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) egenskaper.

- Åsidosättningar av den här metoden bör som standard inte ange eller skriva dolda objekt från användaren om inte egenskapen [system. Management. Automation. Provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) anges till `true`. Ett fel bör skickas till metoden [system. Management. Automation. Provider. Cmdletprovider. WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) om sökvägen representerar ett objekt som är dolt från användaren och [system. Management. Automation. Provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) är Ange till `false`.

## <a name="retrieve-dynamic-parameters-for-invokedefaultaction"></a>Hämta dynamiska parametrar för InvokeDefaultAction

Ibland kräver `Invoke-Item` cmdleten ytterligare parametrar som anges dynamiskt vid körning. För att tillhandahålla dessa dynamiska parametrar måste Windows PowerShell-dataleverantören implementera metoden [system. Management. Automation. Provider. Itemcmdletprovider. Invokedefaultactiondynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) . Den här metoden hämtar dynamiska parametrar för objektet på den angivna sökvägen och returnerar ett objekt som har egenskaper och fält med parsande attribut som liknar en cmdlet-klass eller en [system. Management. Automation. Runtimedefinedparameterdictionary ](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary)objekt. Windows PowerShell-körningsmiljön använder det returnerade objektet för att lägga till dynamiska parametrar `Invoke-Item` till cmdleten.

Den här objekt leverantören implementerar inte den här metoden. Följande kod är dock standard implementeringen av den här metoden.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinvokedefaultactiondynamicparameters](Msh_samplestestcmdlets#testproviderinvokedefaultactiondynamicparameters)]  -->

## <a name="implementing-helper-methods-and-classes"></a>Implementera hjälp metoder och klasser

Den här objekt leverantören implementerar flera hjälp metoder och klasser som används av de metoder för allmän åsidosättning som definieras av Windows PowerShell. Koden för dessa hjälp metoder och klasser visas i avsnittet [kod exempel](#code-sample) .

### <a name="normalizepath-method"></a>NormalizePath-metod

Den här objekt leverantören implementerar en NormalizePath Helper-metod för att se till att sökvägen har ett enhetligt format. Det angivna formatet använder ett omvänt\\snedstreck () som avgränsare.

### <a name="pathisdrive-method"></a>PathIsDrive-metod

Den här artikel leverantören implementerar en PathIsDrive Helper-metod för att avgöra om den angivna sökvägen faktiskt är enhets namnet.

### <a name="chunkpath-method"></a>ChunkPath-metod

Den här objekt leverantören implementerar en ChunkPath Helper-metod som delar upp den angivna sökvägen så att providern kan identifiera de enskilda elementen. Den returnerar en matris som består av Sök vägs elementen.

### <a name="gettable-method"></a>GetTable-metod

Den här objekt leverantören implementerar GetTables Helper-metoden som returnerar ett DatabaseTableInfo-objekt som representerar information om den tabell som anges i anropet.

### <a name="getrow-method"></a>GetRow-metod

Metoden [system. Management. Automation. Provider. Itemcmdletprovider. getItem, *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) för den här objekt leverantören anropar GetRows Helper-metoden. Den här hjälp metoden hämtar ett DatabaseRowInfo-objekt som representerar information om den angivna raden i tabellen.

### <a name="databasetableinfo-class"></a>DatabaseTableInfo-klass

Den här objekt leverantören definierar en DatabaseTableInfo-klass som representerar en samling information i en data tabell i databasen. Den här klassen liknar klassen [system. io. Directoryinfo](/dotnet/api/System.IO.DirectoryInfo) .

Exempel objekt leverantören definierar en DatabaseTableInfo. GetTables-metod som returnerar en samling tabell informations objekt som definierar tabellerna i databasen. Den här metoden inkluderar ett try/catch-block för att se till att alla databas fel visas som en rad med noll poster.

### <a name="databaserowinfo-class"></a>DatabaseRowInfo-klass

Den här objekt leverantören definierar DatabaseRowInfo Helper-klassen som representerar en rad i en tabell i databasen. Den här klassen liknar klassen [system. io. fileinfo](/dotnet/api/System.IO.FileInfo) .

Exempel leverantören definierar en DatabaseRowInfo. GetRows-metod för att returnera en samling rad informations objekt för den angivna tabellen. Den här metoden inkluderar ett try/catch-block för trap-undantag. Eventuella fel ger ingen rad information.

## <a name="code-sample"></a>Kod exempel

Fullständig exempel kod finns i [kod exemplet för AccessDbProviderSample03](./accessdbprovidersample03-code-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definiera objekt typer och formatering

När du skriver en provider kan det vara nödvändigt att lägga till medlemmar i befintliga objekt eller definiera nya objekt. När du är färdig skapar du en typ fil som Windows PowerShell kan använda för att identifiera medlemmar i objektet och en format fil som definierar hur objektet visas. Mer information om finns i [utöka objekt typer och formatering](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-windows-powershell-provider"></a>Skapa Windows PowerShell-providern

Se [hur du registrerar cmdlets, providers och värd program](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-windows-powershell-provider"></a>Testa Windows PowerShell-providern

När den här Windows PowerShell-dataleverantören har registrerats med Windows PowerShell kan du bara testa bas-och enhets funktionerna i providern. Om du vill testa manipuleringen av objekt måste du också implementera behållar funktioner som beskrivs i [implementera en container Windows PowerShell-Provider](./creating-a-windows-powershell-container-provider.md).

## <a name="see-also"></a>Se även

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Windows PowerShell Programmer ' s guide](./windows-powershell-programmer-s-guide.md)

[Skapa Windows PowerShell-leverantörer](./how-to-create-a-windows-powershell-provider.md)

[Designa din Windows PowerShell-Provider](./designing-your-windows-powershell-provider.md)

[Utöka objekt typer och formatering](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Så här fungerar Windows PowerShell](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[Skapa en container Windows PowerShell-Provider](./creating-a-windows-powershell-container-provider.md)

[Skapa en Windows PowerShell-Provider för enhet](./creating-a-windows-powershell-drive-provider.md)

[Registrera cmdlets, providers och värd program](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)