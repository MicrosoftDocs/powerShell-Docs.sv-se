---
title: Skapa en Windows PowerShell-objekt-Provider | Microsoft Docs
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
ms.openlocfilehash: 30b4dbcd281f712bba8d8e3540d2282d527388e4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851060"
---
# <a name="creating-a-windows-powershell-item-provider"></a>Skapa en Windows PowerShell-objektprovider

Det här avsnittet beskriver hur du skapar en Windows PowerShell-provider som kan manipulera data i ett datalager. I det här avsnittet kallas elementen i data i store för lagring av som ”objekt” av data. Det betyder kallas en provider som kan manipulera data i store en provider för Windows PowerShell-objekt.

> [!NOTE]
> Du kan ladda ned den C# källfilen (AccessDBSampleProvider03.cs) för den här providern med hjälp av Microsoft Windows Software Development Kit för Windows Vista och .NET Framework 3.0 Runtime-komponenter. Hämta anvisningar finns i [hur du installerar Windows PowerShell och ladda ned Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).
> Du kan ladda ned den C# källfilen (AccessDBSampleProvider03.cs) för den här providern med hjälp av Microsoft Windows Software Development Kit för Windows Vista och .NET Framework 3.0 Runtime-komponenter. Hämta anvisningar finns i [hur du installerar Windows PowerShell och ladda ned Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Hämtade källfilerna är tillgängliga i den  **\<PowerShell-exempel >** directory.
>
> Läs mer om andra Windows PowerShell-providern implementeringar [designa din Windows PowerShell-providern](./designing-your-windows-powershell-provider.md).

Windows PowerShell-objekt-providern som beskrivs i det här avsnittet hämtar dataobjekt från en Access-databas. I det här fallet är ett ”objekt” antingen en tabell i Access-databas eller en rad i en tabell.

I följande lista innehåller avsnitt i det här avsnittet. Om du är bekant med att skriva en provider för Windows PowerShell-objekt, läsa dessa avsnitt i den ordning som de visas. Om du är bekant med att skriva en provider för Windows PowerShell-objekt, gå direkt till den information du behöver:

- [Definiera providerklass för Windows PowerShell-objekt](#Defining-the-Windows-PowerShell-Item-Provider-Class)

- [Definiera grundfunktionen](#Defining-Base-Functionality)

- [Söker efter sökväg giltighet](#Checking-for-Path-Validity)

- [Avgör om det finns ett objekt](#Determining-if-an-Item-Exists)

- [Koppla dynamiska parametrar till den `Test-Path` Cmdlet](#Attaching-Dynamic-Parameters-to-the-Test-Path-Cmdlet)

- [Hämtar ett objekt](#Retrieving-an-Item)

- [Koppla dynamiska parametrar till den `Get-Item` Cmdlet](#Attaching-Dynamic-Parameters-to-the-Get-Item-Cmdlet)

- [Ange ett objekt](#Setting-an-Item)

- [Koppla dynamiska parametrar till den `Set-Item` Cmdlet](#Retrieving-Dynamic-Parameters-for-SetItem)

- [Om du avmarkerar ett objekt](#Clearing-an-Item)

- [Bifoga dynamiska parametrar till cmdleten Cler-objekt](#Retrieve-Dynamic-Parameters-for-ClearItem)

- [Utför en standardåtgärd för ett objekt](#Performing-a-Default-Action-for-an-Item)

- [Hämtning av dynamiska parametrar för InvokeDefaultAction](#Retrieve-Dynamic-Parameters-for-InvokeDefaultAction)

- [Implementera Hjälpmetoder och klasser](#Implementing-Helper-Methods-and-Classes)

- [Kodexempel](#Code-Sample)

- [Definiera objekttyper och formatering](#Defining-Object-Types-and-Formatting)

- [Att skapa Windows PowerShell-providern](#Building-the-Windows-PowerShell-provider)

- [Testa Windows PowerShell-providern](#Testing-the-Windows-PowerShell-provider)

## <a name="defining-the-windows-powershell-item-provider-class"></a>Definiera providerklass för Windows PowerShell-objekt

En provider för Windows PowerShell-objekt måste definiera en .NET-klass som härleds från den [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) basklassen. Följande är klassdefinitionen för providern objektet som beskrivs i det här avsnittet.

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L34-L36 "AccessDBProviderSample03.cs")]

Observera att i det här klassdefinitionen, den [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribut innehåller två parametrar. Den första parametern anger ett användarvänligt namn för providern som används av Windows PowerShell. Den andra parametern anger de specifika funktioner i Windows PowerShell som providern visar Windows PowerShell-runtime under bearbetning av kommandot. Det finns inga har lagts till specifika funktioner för Windows PowerShell för den här providern.

## <a name="defining-base-functionality"></a>Definiera grundfunktionen

Mer information finns i [Design Your Windows PowerShell-providern](./designing-your-windows-powershell-provider.md), [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) klassen härleds från flera klasser som angav olika Provider-funktionalitet. En provider för Windows PowerShell-objekt, därför måste definiera alla funktioner som tillhandahålls av dessa klasser.

Mer information om hur du implementerar funktioner för att lägga till sessionen-specifika initieringsinformation och för att frisläppa resurser som används av providern finns i [skapar en grundläggande Windows PowerShell-providern](./creating-a-basic-windows-powershell-provider.md). De flesta leverantörer, inklusive providern som beskrivs här, kan dock använda standardimplementering av den här funktionen som tillhandahålls av Windows PowerShell.

Innan en provider för Windows PowerShell-objekt kan manipulera objekt i arkivet, den måste implementera-metoderna i den [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) basklassen får tillgång till datalagret. Läs mer om hur du implementerar den här klassen [skapar en Windows PowerShell Drive Provider](./creating-a-windows-powershell-drive-provider.md).

## <a name="checking-for-path-validity"></a>Söker efter sökväg giltighet

När du letar efter en datapost, Windows PowerShell-runtime inkluderar en Windows PowerShell-sökväg till providern, enligt definitionen i avsnittet ”PSPath begrepp” i [hur Windows PowerShell fungerar](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58). En provider för Windows PowerShell-objekt måste kontrollera syntaktiska och semantisk giltigheten för alla sökvägar som skickas till den genom att implementera den [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) metod. Den här metoden returnerar `true` om sökvägen är giltig och `false` annars. Vara medveten om att implementeringen av den här metoden inte ska verifiera att objektet på sökvägen, men endast som sökvägen är syntaktiskt och semantiskt korrekt.
När du letar efter en datapost, Windows PowerShell-runtime inkluderar en Windows PowerShell-sökväg till providern, enligt definitionen i avsnittet ”PSPath begrepp” i [hur Windows PowerShell fungerar](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58). En provider för Windows PowerShell-objekt måste kontrollera syntaktiska och semantisk giltigheten för alla sökvägar som skickas till den genom att implementera den [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) metod. Den här metoden returnerar `true` om sökvägen är giltig och `false` annars. Vara medveten om att implementeringen av den här metoden inte ska verifiera att objektet på sökvägen, men endast som sökvägen är syntaktiskt och semantiskt korrekt.

Här är implementeringen av den [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) metod för den här providern. Observera att den här implementeringen anropar en NormalizePath helper-metod för att konvertera alla avgränsare i sökvägen till en enhetlig.

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L274-L298 "AccessDBProviderSample03.cs")]

## <a name="determining-if-an-item-exists"></a>Avgör om det finns ett objekt

När du har verifierat sökvägen, måste Windows PowerShell-runtime bestämma om det finns ett objekt av data i sökvägen. För att stödja den här typen av fråga, provider för Windows PowerShell-objektet implementerar den [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) metod. Den här metoden returnerar `true` ett objekt påträffades vid den angivna sökvägen och `false` (standard) annars.

Här är implementeringen av den [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) metod för den här providern. Observera att den här metoden anropar hjälpmetoder PathIsDrive och ChunkPath GetTable och använder en provider definierats DatabaseTableInfo objekt.

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L229-L267 "AccessDBProviderSample03.cs")]

#### <a name="things-to-remember-about-implementing-itemexists"></a>Kom ihåg följande om hur du implementerar ItemExists

Följande villkor kan tillkomma för din implementering av [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists):

- När du definierar providerklassen, en provider för Windows PowerShell-objekt kan deklarera provider-funktionerna i ExpandWildcards, Filter, inkludera eller exkludera, från den [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)uppräkning. I dessa fall är implementeringen av den [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) metod måste se till att sökvägen skickas till metoden uppfyller kraven för de angivna funktionerna. Gör detta genom metoden ska komma åt egenskapen lämplig, till exempel, [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) och [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) egenskaper.

- Implementeringen av den här metoden bör hantera någon form av åtkomst till det objekt som kan göra objektet som är synliga för användaren. Till exempel om en användare har skrivbehörighet till en fil via filsystemet provider (som tillhandahålls av Windows PowerShell), men inte läsbehörighet kan filen fortfarande finns och [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) returnerar `true`. Implementeringen kan kräva kontrollerar en överordnad artikel om du vill se om det underordnade objektet kan ingå.

## <a name="attaching-dynamic-parameters-to-the-test-path-cmdlet"></a>Bifoga dynamiska parametrar till cmdleten Test-Path

Ibland den `Test-Path` cmdlet: en som anropar [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) kräver ytterligare parametrar som anges dynamiskt vid körning. Att tillhandahålla dessa dynamiska parametrar i Windows PowerShell objekt leverantören måste implementera de [System.Management.Automation.Provider.Itemcmdletprovider.Itemexistsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExistsDynamicParameters) metod. Den här metoden hämtar de dynamiska parametrarna för objektet på den angivna sökvägen och returnerar ett objekt med egenskaper och fält med parsning attribut som liknar en cmdlet-klass eller en [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objekt. Windows PowerShell-runtime använder det returnerade objektet för att lägga till parametrar till den `Test-Path` cmdlet.

Den här providern för Windows PowerShell-objektet implementerar inte den här metoden. Följande kod är dock standardimplementering av den här metoden.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovideritemexistdynamicparameters](Msh_samplestestcmdlets#testprovideritemexistdynamicparameters)]  -->

## <a name="retrieving-an-item"></a>Hämtar ett objekt

Om du vill hämta ett objekt, provider för Windows PowerShell-objekt måste åsidosätta [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) metod för att stödja anrop från den `Get-Item` cmdlet. Den här metoden skriver objekt med den [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) metod.

Här är implementeringen av den [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) metod för den här providern. Observera att den här metoden använder hjälpmetoder GetTable och GetRow för att hämta objekt som är antingen tabeller i Access-databas eller rader i en datatabell.

[!code-csharp[AccessDBProviderSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample03/AccessDBProviderSample03.cs#L132-L163 "AccessDBProviderSample03.cs")]

#### <a name="things-to-remember-about-implementing-getitem"></a>Kom ihåg följande om hur du implementerar GetItem

Följande villkor kan gälla för en implementering av [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem):

- När du definierar providerklassen, en provider för Windows PowerShell-objekt kan deklarera provider-funktionerna i ExpandWildcards, Filter, inkludera eller exkludera, från den [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)uppräkning. I dessa fall är implementeringen av [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) måste se till att sökvägen skickas till metoden uppfyller dessa krav. Gör detta genom metoden ska komma åt egenskapen lämplig, till exempel, [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) och [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) egenskaper.

- Som standard åsidosättningar av den här metoden ska inte att hämta objekt som vanligtvis är dolda från användaren, såvida inte den [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) är inställd på `true`. Till exempel den [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) metod för filsystem providern kontrollerar den [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) egenskapen innan den försöker anropa [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) efter dolda filer.

## <a name="attaching-dynamic-parameters-to-the-get-item-cmdlet"></a>Bifoga dynamiska parametrar till cmdleten Get-objekt

Ibland den `Get-Item` cmdlet kräver ytterligare parametrar som anges dynamiskt vid körning. Att tillhandahålla dessa dynamiska parametrar i Windows PowerShell objekt leverantören måste implementera de [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) metod. Den här metoden hämtar de dynamiska parametrarna för objektet på den angivna sökvägen och returnerar ett objekt med egenskaper och fält med parsning attribut som liknar en cmdlet-klass eller en [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objekt. Windows PowerShell-runtime använder det returnerade objektet för att lägga till parametrar till den `Get-Item` cmdlet.

Den här providern implementerar inte den här metoden. Följande kod är dock standardimplementering av den här metoden.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetitemdynamicparameters](Msh_samplestestcmdlets#testprovidergetitemdynamicparameters)]  -->

## <a name="setting-an-item"></a>Ange ett objekt

Om du vill ange ett objekt, provider för Windows PowerShell-objekt måste åsidosätta de [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) metod för att stödja anrop från den `Set-Item` cmdlet. Den här metoden anger värdet för objektet på den angivna sökvägen.

Den här leverantören inte ger en åsidosättning för den [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) metod. Följande är dock standardimplementering av den här metoden.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidersetitem](Msh_samplestestcmdlets#testprovidersetitem)]  -->

#### <a name="things-to-remember-about-implementing-setitem"></a>Kom ihåg följande om hur du implementerar SetItem

Följande villkor kan tillkomma för din implementering av [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem):

- När du definierar providerklassen, en provider för Windows PowerShell-objekt kan deklarera provider-funktionerna i ExpandWildcards, Filter, inkludera eller exkludera, från den [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)uppräkning. I dessa fall är implementeringen av [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) måste se till att sökvägen skickas till metoden uppfyller dessa krav. Gör detta genom metoden ska komma åt egenskapen lämplig, till exempel, [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) och [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) egenskaper.

- Som standard åsidosättningar av den här metoden inte ställa in eller skriva objekt som är dolda från användaren, såvida inte den [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) är inställd på `true`. Ett fel ska skickas till den [System.Management.Automation.Provider.Cmdletprovider.Writeerror*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) metod om sökvägen representerar ett dolda objekt och [ System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) är inställd på `false`.

- Implementeringen av den [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) metoden ska anropa [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)och verifiera dess returvärdet innan du gör några ändringar i datalagret. Den här metoden används för att bekräfta körning av en åtgärd när en ändring görs till datalagret, till exempel ta bort filer. Den [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) metoden skickar namnet på resursen som ska ändras för användaren med Windows PowerShell-körning med hänsyn till eventuella kommandoradsinställningar eller preferensvariabler avgöra vad som ska visas.

  Efter anropet till [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) returnerar `true`, [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)metoden ska anropa den [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) metod. Den här metoden skickar ett meddelande till användaren att godkänna feedback för att kontrollera om åtgärden bör behållas. Anropet till [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) kan ytterligare en kontroll efter ändringar av potentiellt skadliga system.

## <a name="retrieving-dynamic-parameters-for-setitem"></a>Hämtning av dynamiska parametrar för SetItem

Ibland den `Set-Item` cmdlet kräver ytterligare parametrar som anges dynamiskt vid körning. Att tillhandahålla dessa dynamiska parametrar i Windows PowerShell objekt leverantören måste implementera de [System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) metod. Den här metoden hämtar de dynamiska parametrarna för objektet på den angivna sökvägen och returnerar ett objekt med egenskaper och fält med parsning attribut som liknar en cmdlet-klass eller en [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objekt. Windows PowerShell-runtime använder det returnerade objektet för att lägga till parametrar till den `Set-Item` cmdlet.

Den här providern implementerar inte den här metoden. Följande kod är dock standardimplementering av den här metoden.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidersetitemdynamicparameters](Msh_samplestestcmdlets#testprovidersetitemdynamicparameters)]  -->

## <a name="clearing-an-item"></a>Om du avmarkerar ett objekt

Om du vill avmarkera ett objekt av Windows PowerShell-providern för objektet implementerar den [System.Management.Automation.Provider.Itemcmdletprovider.Clearitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) metod för att stödja anrop från den `Clear-Item` cmdlet. Den här metoden raderar dataobjektet på den angivna sökvägen.

Den här providern implementerar inte den här metoden. Följande kod är dock standardimplementering av den här metoden.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderclearitem](Msh_samplestestcmdlets#testproviderclearitem)]  -->

#### <a name="things-to-remember-about-implementing-clearitem"></a>Kom ihåg följande om hur du implementerar ClearItem

Följande villkor kan gälla för en implementering av [System.Management.Automation.Provider.Itemcmdletprovider.Clearitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem):

- När du definierar providerklassen, en provider för Windows PowerShell-objekt kan deklarera provider-funktionerna i ExpandWildcards, Filter, inkludera eller exkludera, från den [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)uppräkning. I dessa fall är implementeringen av [System.Management.Automation.Provider.Itemcmdletprovider.Clearitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItem) måste se till att sökvägen skickas till metoden uppfyller dessa krav. Gör detta genom metoden ska komma åt egenskapen lämplig, till exempel, [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) och [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) egenskaper.

- Som standard åsidosättningar av den här metoden inte ställa in eller skriva objekt som är dolda från användaren, såvida inte den [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) är inställd på `true`. Ett fel ska skickas till den [System.Management.Automation.Provider.Cmdletprovider.Writeerror*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) metod om sökvägen representerar ett objekt som är dolda från användaren och [ System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) är inställd på `false`.

- Implementeringen av den [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) metoden ska anropa [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)och verifiera dess returvärdet innan du gör några ändringar i datalagret. Den här metoden används för att bekräfta körning av en åtgärd när en ändring görs till datalagret, till exempel ta bort filer. Den [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) metoden skickar namnet på resursen som ska ändras till användaren med Windows PowerShell-runtime och hantera alla kommandoradsinställningar och inställningar variabler avgöra vad som ska visas.

  Efter anropet till [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) returnerar `true`, [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem)metoden ska anropa den [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) metod. Den här metoden skickar ett meddelande till användaren att godkänna feedback för att kontrollera om åtgärden bör behållas. Anropet till [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) kan ytterligare en kontroll efter ändringar av potentiellt skadliga system.

## <a name="retrieve-dynamic-parameters-for-clearitem"></a>Hämta dynamiska parametrar för ClearItem

Ibland den `Clear-Item` cmdlet kräver ytterligare parametrar som anges dynamiskt vid körning. Att tillhandahålla dessa dynamiska parametrar i Windows PowerShell objekt leverantören måste implementera de [System.Management.Automation.Provider.Itemcmdletprovider.Clearitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) metod. Den här metoden hämtar de dynamiska parametrarna för objektet på den angivna sökvägen och returnerar ett objekt med egenskaper och fält med parsning attribut som liknar en cmdlet-klass eller en [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objekt. Windows PowerShell-runtime använder det returnerade objektet för att lägga till parametrar till den `Clear-Item` cmdlet.

Den här providern objektet implementerar inte den här metoden. Följande kod är dock standardimplementering av den här metoden.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderclearitemdynamicparameters](Msh_samplestestcmdlets#testproviderclearitemdynamicparameters)]  -->

## <a name="performing-a-default-action-for-an-item"></a>Utför en standardåtgärd för ett objekt

En provider för Windows PowerShell-objekt kan implementera den [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) metod för att stödja anrop från den `Invoke-Item` cmdleten, där leverantören att Utför en standardåtgärd för objektet på den angivna sökvägen. Filsystem-providern kan till exempel använda den här metoden för att anropa ShellExecute för ett specifikt objekt.

Den här providern implementerar inte den här metoden. Följande kod är dock standardimplementering av den här metoden.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinvokedefaultaction](Msh_samplestestcmdlets#testproviderinvokedefaultaction)]  -->

#### <a name="things-to-remember-about-implementing-invokedefaultaction"></a>Kom ihåg följande om hur du implementerar InvokeDefaultAction

Följande villkor kan gälla för en implementering av [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction):

- När du definierar providerklassen, en provider för Windows PowerShell-objekt kan deklarera provider-funktionerna i ExpandWildcards, Filter, inkludera eller exkludera, från den [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)uppräkning. I dessa fall är implementeringen av [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultaction*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultAction) måste se till att sökvägen skickas till metoden uppfyller dessa krav. Gör detta genom metoden ska komma åt egenskapen lämplig, till exempel, [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) och [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) egenskaper.

- Som standard åsidosättningar av den här metoden inte ställa in eller skriva objekt som är dolda från användaren, såvida inte den [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) är inställd på `true`. Ett fel ska skickas till den [System.Management.Automation.Provider.Cmdletprovider.Writeerror*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) metod om sökvägen representerar ett objekt som är dolda från användaren och [ System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) är inställd på `false`.

## <a name="retrieve-dynamic-parameters-for-invokedefaultaction"></a>Hämta dynamiska parametrar för InvokeDefaultAction

Ibland den `Invoke-Item` cmdlet kräver ytterligare parametrar som anges dynamiskt vid körning. Att tillhandahålla dessa dynamiska parametrar i Windows PowerShell objekt leverantören måste implementera de [System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultactiondynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) metod. Den här metoden hämtar de dynamiska parametrarna för objektet på den angivna sökvägen och returnerar ett objekt med egenskaper och fält med parsning attribut som liknar en cmdlet-klass eller en [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objekt. Windows PowerShell-runtime använder det returnerade objektet för att lägga till dynamiska parametrar till den `Invoke-Item` cmdlet.

Den här providern objektet implementerar inte den här metoden. Följande kod är dock standardimplementering av den här metoden.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinvokedefaultactiondynamicparameters](Msh_samplestestcmdlets#testproviderinvokedefaultactiondynamicparameters)]  -->

## <a name="implementing-helper-methods-and-classes"></a>Implementera Hjälpmetoder och klasser

Den här providern objektet implementerar flera hjälpmetoder och klasser som används av offentligt åsidosätta metoder som definieras av Windows PowerShell. Koden för dessa hjälpmetoder och klasser som visas i den [kodexempel](#Code-Sample) avsnittet.

### <a name="normalizepath-method"></a>NormalizePath metod

Den här providern objektet implementerar en NormalizePath helper-metod för att kontrollera att sökvägen har ett enhetligt format. Det format som anges använder ett omvänt snedstreck (\\) som avgränsare.

### <a name="pathisdrive-method"></a>PathIsDrive metod

Den här providern objektet implementerar en PathIsDrive helper-metod för att avgöra om den angivna sökvägen är faktiskt enhetsnamnet.

### <a name="chunkpath-method"></a>ChunkPath metod

Den här providern objektet implementerar en ChunkPath hjälpkomponentmetod som bryter den angivna sökvägen så att providern kan identifiera dess enskilda element. Returnerar en matris bestående av sökväg-element.

### <a name="gettable-method"></a>GetTable metod

Den här providern objektet implementerar helper GetTables-metoden som returnerar ett DatabaseTableInfo-objekt som representerar information om den tabellen som angetts i anropet.

### <a name="getrow-method"></a>GetRow-metoden

Den [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) av providern objektet anropar GetRows helper-metod. Den här helper-metoden hämtar ett DatabaseRowInfo-objekt som representerar information om den angivna raden i tabellen.

### <a name="databasetableinfo-class"></a>DatabaseTableInfo-klass

Den här providern objektet definierar en DatabaseTableInfo-klass som representerar en samling av informationen i en datatabell i databasen. Den här klassen liknar den [System.IO.Directoryinfo](/dotnet/api/System.IO.DirectoryInfo) klass.

Objekt-providern exemplet definierar en DatabaseTableInfo.GetTables-metod som returnerar en uppsättning tabellobjekt definierar tabellerna i databasen. Den här metoden innehåller ett try-/ catch-block för att säkerställa att alla databasfel visas som en rad med noll poster.

### <a name="databaserowinfo-class"></a>DatabaseRowInfo-klass

Den här providern objektet definierar DatabaseRowInfo fonthelper-klass som representerar en rad i en tabell i databasen. Den här klassen liknar den [System.IO.Fileinfo](/dotnet/api/System.IO.FileInfo) klass.

Exempel-leverantör definierar en DatabaseRowInfo.GetRows metod för att returnera en samling rad information objekt för den angivna tabellen. Den här metoden innehåller ett try-/ catch-block för att fånga undantag. Eventuella fel leder ingen information om raden.

## <a name="code-sample"></a>Kodexempel

Komplett exempel finns i [AccessDbProviderSample03 kodexempel](./accessdbprovidersample03-code-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definiera objekttyper och formatering

När du skriver en provider, kan det vara nödvändigt att lägga till medlemmar i befintliga objekt eller definiera nya objekt. Skapa en fil för typer som Windows PowerShell kan använda för att identifiera medlemmarna i objektet och en formatfil som definierar hur objektet visas när du är klar. Läs mer om [utöka objekttyper och formatering](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).
När du skriver en provider, kan det vara nödvändigt att lägga till medlemmar i befintliga objekt eller definiera nya objekt. Skapa en fil för typer som Windows PowerShell kan använda för att identifiera medlemmarna i objektet och en formatfil som definierar hur objektet visas när du är klar. Läs mer om [utöka objekttyper och formatering](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-windows-powershell-provider"></a>Att skapa Windows PowerShell-providern

Se [hur du registrerar Cmdlets, Providers och vara värd för program](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).
Se [hur du registrerar Cmdlets, Providers och vara värd för program](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-windows-powershell-provider"></a>Testa Windows PowerShell-providern

När den här artikeln Windows PowerShell-providern är registrerad med Windows PowerShell du bara testa basic och driva funktionerna i providern. Om du vill testa manipulering av objekt, måste du även implementera container-funktioner som beskrivs i [implementera en behållare Windows PowerShell-providern](./creating-a-windows-powershell-container-provider.md).

## <a name="see-also"></a>Se även

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Programmeringsguide för Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Skapa Windows PowerShell-Providers](./how-to-create-a-windows-powershell-provider.md)

[Designa din Windows PowerShell-providern](./designing-your-windows-powershell-provider.md)

[Utöka objekttyper och formatering](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Utöka objekttyper och formatering](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Så här fungerar Windows PowerShell](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[Så här fungerar Windows PowerShell](http://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[Skapa en behållare Windows PowerShell-provider](./creating-a-windows-powershell-container-provider.md)

[Skapa en enhet med Windows PowerShell-provider](./creating-a-windows-powershell-drive-provider.md)

[Hur du registrerar Cmdlets, Providers och vara värd för program](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Hur du registrerar Cmdlets, Providers och vara värd för program](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)