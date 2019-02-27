---
title: Skapa en Windows PowerShell-innehållsleverantör | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- content providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], content provider
ms.assetid: 3da88ff9-c4c7-4ace-aa24-0a29c8cfa060
caps.latest.revision: 6
ms.openlocfilehash: 6e5d79487539d4f58922e2686f1fdba08797f305
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846328"
---
# <a name="creating-a-windows-powershell-content-provider"></a>Skapa en Windows PowerShell-innehållsprovider

Det här avsnittet beskriver hur du skapar en Windows PowerShell-provider som gör att användaren kan ändra innehållet i objekten i ett datalager. Det betyder kallas en provider som kan ändra innehållet i objekt en innehållsleverantör för Windows PowerShell.

> [!NOTE]
> Du kan ladda ned den C# källfilen (AccessDBSampleProvider06.cs) för den här providern med hjälp av Microsoft Windows Software Development Kit för Windows Vista och .NET Framework 3.0 Runtime-komponenter. Hämta anvisningar finns i [hur du installerar Windows PowerShell och ladda ned Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).
> Du kan ladda ned den C# källfilen (AccessDBSampleProvider06.cs) för den här providern med hjälp av Microsoft Windows Software Development Kit för Windows Vista och .NET Framework 3.0 Runtime-komponenter. Hämta anvisningar finns i [hur du installerar Windows PowerShell och ladda ned Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Hämtade källfilerna är tillgängliga i den  **\<PowerShell-exempel >** directory.
>
> Läs mer om andra Windows PowerShell-providern implementeringar [designa din Windows PowerShell-providern](./designing-your-windows-powershell-provider.md).

I följande lista innehåller avsnitt i det här avsnittet. Om du är bekant med att skriva en Windows PowerShell-innehållsleverantör, Läs avsnitten i den ordning som de visas. Om du är bekant med att skriva en Windows PowerShell-innehållsleverantör, gå direkt till den information du behöver.

- [Definiera providerklass för Windows PowerShell-innehåll](#Define-the-Windows-PowerShell-Content-Provider-Class)

- [Definiera grundfunktionen](#Define-Functionality-of-Base-Class)

- [Implementera en Content läsare](#Implementing-a-Content-Reader)

- [Implementera en Content-skrivare](#Implementing-a-Content-Writer)

- [Hämtning av innehåll läsaren](#Retrieving-the-Content-Reader)

- [Koppla dynamiska parametrar till den `Get-Content` Cmdlet](#Attaching-Dynamic-Parameters-to-the-Get-Content-Cmdlet)

- [Hämtning av innehåll skrivaren](#Retrieving-the-Content-Writer)

- [Den dynamiska parametrar till Add_Content och `Set-Content` cmdlet: ar](#Attaching-Dynamic-Parameters-to-the-Add-Content-and-Set-Content-Cmdlets)

- [Rensa innehåll](#Clearing-Content)

- [Koppla dynamiska parametrar till den `Clear-Content` Cmdlet](#Attaching-Dynamic-Parameters-to-the-Clear-Content-Cmdlet)

- [Kodexempel](#Code-Sample)

- [Definiera objekttyper och formatering]()

- [Att skapa Windows PowerShell-providern](#Building-the-Windows-PowerShell-Provider)

- [Testa Windows PowerShell-providern](#Testing-the-Windows-PowerShell-Provider)

## <a name="define-the-windows-powershell-content-provider-class"></a>Definiera providerklass för Windows PowerShell-innehåll

En Windows PowerShell-innehållsleverantören måste skapa en .NET-klass som har stöd för den [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) gränssnitt. Här är klassdefinitionen för providern objektet som beskrivs i det här avsnittet.

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L32-L33 "AccessDBProviderSample06.cs")]

Observera att i det här klassdefinitionen, den [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribut innehåller två parametrar. Den första parametern anger ett användarvänligt namn för providern som används av Windows PowerShell. Den andra parametern anger de specifika funktioner i Windows PowerShell som providern visar Windows PowerShell-runtime under bearbetning av kommandot. Det finns inga har lagts till specifika funktioner för Windows PowerShell för den här providern.

## <a name="define-functionality-of-base-class"></a>Definiera funktionerna i basklass

Mer information finns i [Design Your Windows PowerShell-providern](./designing-your-windows-powershell-provider.md), [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) klassen härleds från flera klasser som angetts annan provider-funktionalitet. En Windows PowerShell-innehållsleverantören därför definierar vanligtvis alla funktioner som tillhandahålls av dessa klasser.

Mer information om hur du implementerar funktioner för att lägga till sessionen-specifika initieringsinformation och för att frisläppa resurser som används av providern finns i [skapar en grundläggande Windows PowerShell-providern](./creating-a-basic-windows-powershell-provider.md). De flesta leverantörer, inklusive providern som beskrivs här, kan dock använda standardimplementering av den här funktionen som tillhandahålls av Windows PowerShell.

För att komma åt data store providern måste implementera-metoderna i den [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) basklassen. Läs mer om hur du implementerar dessa metoder, [skapar en Windows PowerShell Drive Provider](./creating-a-windows-powershell-drive-provider.md).

Om du vill manipulera objekten i ett datalager, till exempel komma, inställningen och rensar objekt providern måste implementera de metoder som tillhandahålls av den [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) basklassen. Läs mer om hur du implementerar dessa metoder, [skapar en Windows PowerShell-providern för objektet](./creating-a-windows-powershell-item-provider.md).

Om du vill arbeta med flera lager datalager, providern måste implementera de metoder som tillhandahålls av den [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) basklassen. Läs mer om hur du implementerar dessa metoder, [skapar en Windows PowerShell-providern för behållaren](./creating-a-windows-powershell-container-provider.md).

För att stödja rekursiv kommandon, kapslade behållare och relativa sökvägar, providern måste implementera de [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) basklassen. Dessutom kan den här Windows PowerShell-innehållsleverantören bifogar [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) gränssnitt till den [ System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) basklassen och därför måste implementera de metoder som tillhandahålls av den klassen. Mer information finns i implementerar dessa metoder, se [implementera en navigering Windows PowerShell-providern](./creating-a-windows-powershell-navigation-provider.md).

## <a name="implementing-a-content-reader"></a>Implementera en Content läsare

Om du vill läsa innehåll från ett objekt, måste en provider implementerar en content reader-klass som härleds från [System.Management.Automation.Provider.Icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader). Innehåll läsare för den här providern tillåter åtkomst till innehållet i en rad i en datatabell. Klassen innehåll läsare definierar en **Läs** metod som hämtar data från den angivna raden och returnerar en lista som representerar dessa data, en **Målsökning** metod som flyttar innehåll läsaren en  **Stäng** metod som stänger läsaren innehåll och en **ta bort** metod.

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L2115-L2241 "AccessDBProviderSample06.cs")]

## <a name="implementing-a-content-writer"></a>Implementera en Content-skrivare

Om du vill skriva innehåll till ett objekt, en leverantören måste implementera en innehåll skrivaren klassen härleds från [System.Management.Automation.Provider.Icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter). Klassen innehåll skrivaren definierar en **skriva** metod som skriver det angivna raden innehållet, en **Målsökning** metod som flyttar innehåll författaren, en **Stäng** metod som stänger den Content-skrivare och en **ta bort** metod.

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L2250-L2394 "AccessDBProviderSample06.cs")]

## <a name="retrieving-the-content-reader"></a>Hämtning av innehåll läsaren

För att hämta innehåll från ett objekt, providern måste implementera de [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) att stödja den `Get-Content` cmdlet. Den här metoden returnerar content läsare för det objekt som finns på den angivna sökvägen. Sedan du kan öppna reader-objektet för att läsa innehållet.

Här är implementeringen av [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) för den här metoden för den här providern.

```csharp
public IContentReader GetContentReader(string path)
{
    string tableName;
    int rowNumber;

    PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

    if (type == PathType.Invalid)
    {
        ThrowTerminatingInvalidPathException(path);
    }
    else if (type == PathType.Row)
    {
        throw new InvalidOperationException("contents can be obtained only for tables");
    }

    return new AccessDBContentReader(path, this);
} // GetContentReader
```

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1829-L1846 "AccessDBProviderSample06.cs")]

#### <a name="things-to-remember-about-implementing-getcontentreader"></a>Kom ihåg följande om hur du implementerar GetContentReader

Följande villkor kan gälla för en implementering av [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader):

- När du definierar providerklassen, en Windows PowerShell-innehållsleverantören kan deklarera provider-funktionerna i ExpandWildcards, Filter, inkludera eller exkludera, från den [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)uppräkning. I dessa fall är implementeringen av den [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) metod måste se till att sökvägen skickas till metoden uppfyller kraven för den angivna funktioner. Gör detta genom metoden ska komma åt egenskapen lämplig, till exempel, [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) och [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) egenskaper.

- Som standard åsidosättningar av den här metoden ska inte att hämta en läsare för objekt som är dolda från användaren, såvida inte den [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) är inställd på `true`. Ett fel ska skrivas om sökvägen representerar ett objekt som är dolda från användaren och [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) är inställd på `false`.

## <a name="attaching-dynamic-parameters-to-the-get-content-cmdlet"></a>Bifoga dynamiska parametrar till cmdleten Get-innehåll

Den `Get-Content` cmdlet kan kräva ytterligare parametrar som anges dynamiskt vid körning. För att ge dessa dynamiska parametrar, Windows PowerShell innehållsleverantören måste implementera de [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreaderdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) metod. Den här metoden hämtar dynamiska parametrar för objektet på den angivna sökvägen och returnerar ett objekt med egenskaper och fält med parsning attribut som liknar en cmdlet-klass eller en [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objekt. Windows PowerShell-runtime använder det returnerade objektet för att lägga till parametrar till cmdleten.

Den här behållaren Windows PowerShell-providern implementerar inte den här metoden. Följande kod är dock standardimplementering av den här metoden.

```csharp
public object GetContentReaderDynamicParameters(string path)
{
    return null;
}
```

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1853-L1856 "AccessDBProviderSample06.cs")]

## <a name="retrieving-the-content-writer"></a>Hämtning av innehåll skrivaren

Om du vill skriva innehåll till ett objekt, providern måste implementera de [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) att stödja den `Set-Content` och `Add-Content` cmdletar. Den här metoden returnerar content-skrivaren för det objekt som finns på den angivna sökvägen.

Här är implementeringen av [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) för den här metoden.

```csharp
public IContentWriter GetContentWriter(string path)
{
    string tableName;
    int rowNumber;

    PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

    if (type == PathType.Invalid)
    {
        ThrowTerminatingInvalidPathException(path);
    }
    else if (type == PathType.Row)
    {
        throw new InvalidOperationException("contents can be added only to tables");
    }

    return new AccessDBContentWriter(path, this);
}
```

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1863-L1880 "AccessDBProviderSample06.cs")]

#### <a name="things-to-remember-about-implementing-getcontentwriter"></a>Kom ihåg följande om hur du implementerar GetContentWriter

Följande villkor kan tillkomma för din implementering av [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter):

- När du definierar providerklassen, en Windows PowerShell-innehållsleverantören kan deklarera provider-funktionerna i ExpandWildcards, Filter, inkludera eller exkludera, från den [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)uppräkning. I dessa fall är implementeringen av den [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) metod måste se till att sökvägen skickas till metoden uppfyller kraven för den angivna funktioner. Gör detta genom metoden ska komma åt egenskapen lämplig, till exempel, [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) och [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) egenskaper.

- Som standard åsidosättningar av den här metoden ska inte att hämta en skrivare för objekt som är dolda från användaren, såvida inte den [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) är inställd på `true`. Ett fel ska skrivas om sökvägen representerar ett objekt som är dolda från användaren och [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) är inställd på `false`.

## <a name="attaching-dynamic-parameters-to-the-add-content-and-set-content-cmdlets"></a>Bifoga dynamiska parametrar till cmdlet: lägga till innehåll och Set-innehåll

Den `Add-Content` och `Set-Content` cmdlets kan kräva ytterligare dynamiska parametrar som läggs en körning. För att ge dessa dynamiska parametrar, Windows PowerShell innehållsleverantören måste implementera de [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriterdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) metod för att hantera dessa parametrar. Den här metoden hämtar dynamiska parametrar för objektet på den angivna sökvägen och returnerar ett objekt med egenskaper och fält med parsning attribut som liknar en cmdlet-klass eller en [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objekt. Windows PowerShell-runtime använder det returnerade objektet för att lägga till parametrar till cmdlets.

Den här behållaren Windows PowerShell-providern implementerar inte den här metoden. Följande kod är dock standardimplementering av den här metoden.

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1887-L1890 "AccessDBProviderSample06.cs")]

## <a name="clearing-content"></a>Rensa innehåll

Din innehållsleverantören implementerar den [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) metoden stöd i `Clear-Content` cmdlet. Den här metoden tar du bort innehållet i objektet på den angivna sökvägen, men objektet förblir intakta.

Här är implementeringen av den [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) metod för den här providern.

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1775-L1812 "AccessDBProviderSample06.cs")]

#### <a name="things-to-remember-about-implementing-clearcontent"></a>Kom ihåg följande om hur du implementerar ClearContent

Följande villkor kan gälla för en implementering av [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent):

- När du definierar providerklassen, en Windows PowerShell-innehållsleverantören kan deklarera provider-funktionerna i ExpandWildcards, Filter, inkludera eller exkludera, från den [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)uppräkning. I dessa fall är implementeringen av den [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) metod måste se till att sökvägen skickas till metoden uppfyller kraven för den angivna funktioner. Gör detta genom metoden ska komma åt egenskapen lämplig, till exempel, [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) och [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) egenskaper.

- Åsidosättningar av den här metoden ska som standard inte radera innehållet i objekt som är dolda från användaren, såvida inte den [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) är inställd på `true`. Ett fel ska skrivas om sökvägen representerar ett objekt som är dolda från användaren och [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) är inställd på `false`.

- Implementeringen av den [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) metoden ska anropa [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess* ](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) och verifiera dess returvärdet innan du gör några ändringar i datalagret. Den här metoden används för att bekräfta körning av en åtgärd när en ändring görs i datalagret som t.ex Rensa innehåll. Den [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) metoden skickar namnet på resursen som ska ändras för användaren med Windows PowerShell-runtime hantering av alla kommandoradsinställningar eller inställning variabler avgöra vad som ska visas.

  Efter anropet till [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) returnerar `true`, [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent* ](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) metoden ska anropa den [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) metod. Den här metoden skickar ett meddelande till användaren att godkänna feedback för att kontrollera om åtgärden bör behållas. Anropet till [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) kan ytterligare en kontroll efter ändringar av potentiellt skadliga system.

## <a name="attaching-dynamic-parameters-to-the-clear-content-cmdlet"></a>Bifoga dynamiska parametrar till cmdleten Clear-innehåll

Den `Clear-Content` cmdlet kan kräva ytterligare dynamiska parametrar som läggs till vid körning. För att ge dessa dynamiska parametrar, Windows PowerShell innehållsleverantören måste implementera de [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontentdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) metod för att hantera dessa parametrar. Den här metoden hämtar parametrarna för objektet på den angivna sökvägen. Den här metoden hämtar dynamiska parametrar för objektet på den angivna sökvägen och returnerar ett objekt med egenskaper och fält med parsning attribut som liknar en cmdlet-klass eller en [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objekt. Windows PowerShell-runtime använder det returnerade objektet för att lägga till parametrar till cmdleten.

Den här behållaren Windows PowerShell-providern implementerar inte den här metoden. Följande kod är dock standardimplementering av den här metoden.

```csharp
public object ClearContentDynamicParameters(string path)
{
    return null;
}
```

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1819-L1822 "AccessDBProviderSample06.cs")]

## <a name="code-sample"></a>Kodexempel

Komplett exempel finns i [AccessDbProviderSample06 kodexempel](./accessdbprovidersample06-code-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definiera objekttyper och formatering

När du skriver en provider, kan det vara nödvändigt att lägga till medlemmar i befintliga objekt eller definiera nya objekt. När det är klart måste du skapa en fil för typer som Windows PowerShell kan använda för att identifiera medlemmarna i objektet och en formatfil som definierar hur objektet visas. Mer information finns i [utöka objekttyper och formatering](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).
När du skriver en provider, kan det vara nödvändigt att lägga till medlemmar i befintliga objekt eller definiera nya objekt. När det är klart måste du skapa en fil för typer som Windows PowerShell kan använda för att identifiera medlemmarna i objektet och en formatfil som definierar hur objektet visas. Mer information finns i [utöka objekttyper och formatering](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-windows-powershell-provider"></a>Att skapa Windows PowerShell-providern

Se [hur du registrerar Cmdlets, Providers och vara värd för program](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).
Se [hur du registrerar Cmdlets, Providers och vara värd för program](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-windows-powershell-provider"></a>Testa Windows PowerShell-providern

När din Windows PowerShell-provider har registrerats med Windows PowerShell kan testa du den genom att köra cmdletarna stöds på kommandoraden. Till exempel testa innehållsleverantören exemplet.

Använd den `Get-Content` cmdlet för att hämta innehållet i angivna objektet i databastabellen i sökvägen som angetts av den `Path` parametern. Den `ReadCount` parametern anger antalet objekt för definierade innehåll läsaren att läsa (standardinställning 1). Med följande kommando-post cmdlet: en hämtar två rader (objekt) från tabellen och visar deras innehåll. Observera att följande Exempelutdata används en fiktiv Access-databas.

```powershell
Get-Content -Path mydb:\Customers -ReadCount 2
```

```output
ID        : 1
FirstName : Eric
LastName  : Gruber
Email     : ericgruber@fabrikam.com
Title     : President
Company   : Fabrikam
WorkPhone : (425) 555-0100
Address   : 4567 Main Street
City      : Buffalo
State     : NY
Zip       : 98052
Country   : USA
ID        : 2
FirstName : Eva
LastName  : Corets
Email     : evacorets@cohowinery.com
Title     : Sales Representative
Company   : Coho Winery
WorkPhone : (360) 555-0100
Address   : 8910 Main Street
City      : Cabmerlot
State     : WA
Zip       : 98089
Country   : USA
```

## <a name="see-also"></a>Se även

[Skapa Windows PowerShell-providers](./how-to-create-a-windows-powershell-provider.md)

[Utforma din Windows PowerShell-providern](./designing-your-windows-powershell-provider.md)

[Utöka objekttyper och formatering](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Utöka objekttyper och formatering](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Implementera en navigering Windows PowerShell-providern](./creating-a-windows-powershell-navigation-provider.md)

[Hur du registrerar Cmdlets, Providers och vara värd för program](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Hur du registrerar Cmdlets, Providers och vara värd för program](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Programmeringsguide för Windows PowerShell](./windows-powershell-programmer-s-guide.md)
