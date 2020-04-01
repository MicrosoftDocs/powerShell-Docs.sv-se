---
title: Skapa en Windows PowerShell-innehållsprovider
ms.date: 09/13/2016
ms.topic: article
ms.assetid: 3da88ff9-c4c7-4ace-aa24-0a29c8cfa060
ms.openlocfilehash: 149ddb5becf2e0237973e535323ddf8b03b86f24
ms.sourcegitcommit: 30ccbbb32915b551c4cd4c91ef1df96b5b7514c4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/01/2020
ms.locfileid: "80500845"
---
# <a name="creating-a-windows-powershell-content-provider"></a>Skapa en Windows PowerShell-innehållsprovider

I det här avsnittet beskrivs hur du skapar en Windows PowerShell-provider som gör det möjligt för användaren att ändra innehållet i objekten i ett data lager. En provider som kan manipulera innehållet i objekt kallas till exempel en Windows PowerShell-innehålls leverantör.

> [!NOTE]
> Du kan ladda ned C# käll filen (AccessDBSampleProvider06.CS) för den här providern med hjälp av Microsoft Windows Software Development Kit för Windows Vista och .NET Framework 3,0 Runtime-komponenter. Instruktioner för hämtning finns i [Installera Windows PowerShell och ladda ned Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).
> De hämtade källfilerna finns i mappen **\<PowerShell-exempel >** . Mer information om implementeringar av andra Windows PowerShell-leverantörer finns i [utforma din Windows PowerShell-Provider](./designing-your-windows-powershell-provider.md).

## <a name="define-the-windows-powershell-content-provider-class"></a>Definiera klassen för innehålls leverantörer för Windows PowerShell

En Windows PowerShell innehålls leverantör måste skapa en .NET-klass som stöder [system. Management. Automation. Provider. Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) -gränssnittet. Här är klass definitionen för den artikel leverantör som beskrivs i det här avsnittet.

[!code-csharp[AccessDBProviderSample06.cs](~/powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L32-L33 "AccessDBProviderSample06.cs")]

Observera att i den här klass definitionen innehåller attributet [system. Management. Automation. Provider. Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) två parametrar. Den första parametern anger ett användarvänligt namn för den provider som används av Windows PowerShell. Den andra parametern anger de Windows PowerShell-funktioner som providern exponerar för Windows PowerShell-körningsmiljön under kommando bearbetning. För den här providern finns det inga Windows PowerShell-funktioner som har lagts till.

## <a name="define-functionality-of-base-class"></a>Definiera funktionaliteten för Bask Lassen

Enligt beskrivningen i [utforma din Windows PowerShell-Provider](./designing-your-windows-powershell-provider.md)härleds klassen [system. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) från flera andra klasser som tillhandahöll olika funktioner i providern. En Windows PowerShell-innehålls leverantör definierar därför vanligt vis alla funktioner som tillhandahålls av dessa klasser.

Mer information om hur du implementerar funktioner för att lägga till datorspecifik initierings information och för att frigöra resurser som används av providern finns i [skapa en grundläggande Windows PowerShell-Provider](./creating-a-basic-windows-powershell-provider.md).
De flesta leverantörer, inklusive providern som beskrivs här, kan dock använda standard implementeringen av den här funktionen som tillhandahålls av Windows PowerShell.

För att få åtkomst till data lagret måste providern implementera metoderna i Bask Lassen [system. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) . Mer information om hur du implementerar dessa metoder finns i [skapa en provider för Windows PowerShell-enheter](./creating-a-windows-powershell-drive-provider.md).

Om du vill ändra objekt i ett data lager, till exempel hämta, ange och rensa objekt, måste providern implementera de metoder som tillhandahålls av Bask Lassen [system. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) . Mer information om hur du implementerar dessa metoder finns i [skapa en Windows PowerShell-dataprovider](./creating-a-windows-powershell-item-provider.md).

För att kunna arbeta med data lager med flera lager måste providern implementera de metoder som tillhandahålls av Bask Lassen [system. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) . Mer information om hur du implementerar dessa metoder finns i [skapa en Windows PowerShell container-Provider](./creating-a-windows-powershell-container-provider.md).

För att stödja rekursiva kommandon, kapslade behållare och relativa sökvägar måste providern implementera Bask Lassen [system. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) . Dessutom kan den här Windows PowerShell-innehålls leverantören ansluta till [system. Management. Automation. Provider. Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) -gränssnittet i Bask Lassen [system. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) och måste därför implementera de metoder som tillhandahålls av klassen. Mer information finns i [implementera en Windows PowerShell-Provider för navigering](./creating-a-windows-powershell-navigation-provider.md).

## <a name="implementing-a-content-reader"></a>Implementera en innehålls läsare

Om du vill läsa innehåll från ett objekt måste en provider implementera en innehålls läsar klass som är härledd från [system. Management. Automation. Provider. Icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader).
Innehålls läsaren för den här providern ger åtkomst till innehållet i en rad i en data tabell. Klassen Content Reader definierar en **Read** -metod som hämtar data från den angivna raden och returnerar en lista som representerar data, en **Sök** metod som flyttar innehålls läsaren, en **stängnings** metod som stänger innehålls läsaren och en **dispose** -metod.

[!code-csharp[AccessDBProviderSample06.cs](~/powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L2115-L2241
"AccessDBProviderSample06.cs")]

## <a name="implementing-a-content-writer"></a>Implementera en innehålls skrivare

Om du vill skriva innehåll till ett objekt måste en provider implementera klassen innehålls skrivare härleds från [system. Management. Automation. Provider. Icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter).
Klassen Content Writer definierar en **Skriv** metod som skriver det angivna rad innehållet, en **Sök** metod som flyttar innehålls skrivaren, en **stängnings** metod som stänger innehålls skrivaren och en **dispose** -metod.

[!code-csharp[AccessDBProviderSample06.cs](~/powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L2250-L2394 "AccessDBProviderSample06.cs")]

## <a name="retrieving-the-content-reader"></a>Hämtar innehålls läsaren

För att hämta innehåll från ett objekt måste providern implementera [system. Management. Automation. Provider. Icontentcmdletprovider. Getcontentreader *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) för att stödja `Get-Content`-cmdleten. Den här metoden returnerar innehålls läsaren för objektet som finns på den angivna sökvägen. Objektet Reader kan sedan öppnas för att läsa innehållet.

Här är implementeringen av [system. Management. Automation. Provider. Icontentcmdletprovider. Getcontentreader *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) för den här providern.

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

[!code-csharp[AccessDBProviderSample06.cs](~/powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1829-L1846 "AccessDBProviderSample06.cs")]

#### <a name="things-to-remember-about-implementing-getcontentreader"></a>Saker att komma ihåg om att implementera GetContentReader

Följande villkor kan gälla för en implementering av [system. Management. Automation. Provider. Icontentcmdletprovider. Getcontentreader *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader):

- När du definierar Provider-klassen kan en Windows PowerShell-innehålls leverantör deklarera ExpandWildcards, filtrera, ta med eller undanta från, från [system. Management. Automation. Provider. ProviderCapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) -uppräkningen. I dessa fall måste implementeringen av metoden [system. Management. Automation. Provider. Icontentcmdletprovider. Getcontentreader *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) se till att den sökväg som skickas till metoden uppfyller kraven för de angivna funktionerna. För att göra detta ska metoden komma åt lämplig egenskap, till exempel [system. Management. Automation. Provider. Cmdletprovider. exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) och [system. Management. Automation. Provider. Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) egenskaper.

- Åsidosättningar av den här metoden bör som standard inte hämta en läsare för objekt som är dolda från användaren, om inte egenskapen [system. Management. Automation. Provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) har angetts till `true`. Ett fel ska skrivas om sökvägen representerar ett objekt som är dolt från användaren och [system. Management. Automation. Provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) har angetts till `false`.

## <a name="attaching-dynamic-parameters-to-the-get-content-cmdlet"></a>Koppla dynamiska parametrar till cmdleten Get-Content

`Get-Content`-cmdlet kan kräva ytterligare parametrar som anges dynamiskt vid körning. För att tillhandahålla dessa dynamiska parametrar måste Windows PowerShell-innehålls leverantören implementera metoden [system. Management. Automation. Provider. Icontentcmdletprovider. Getcontentreaderdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) . Den här metoden hämtar dynamiska parametrar för objektet på den angivna sökvägen och returnerar ett objekt som har egenskaper och fält med parsande attribut som liknar en cmdlet-klass eller ett [system. Management. Automation. Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) -objekt. Windows PowerShell-körningsmiljön använder det returnerade objektet för att lägga till parametrarna i cmdleten.

Den här Windows PowerShell container-providern implementerar inte den här metoden. Följande kod är dock standard implementeringen av den här metoden.

```csharp
public object GetContentReaderDynamicParameters(string path)
{
    return null;
}
```

[!code-csharp[AccessDBProviderSample06.cs](~/powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1853-L1856 "AccessDBProviderSample06.cs")]

## <a name="retrieving-the-content-writer"></a>Hämtar innehålls skrivaren

Om du vill skriva innehåll till ett objekt måste providern implementera [system. Management. Automation. Provider. Icontentcmdletprovider. Getcontentwriter *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) för att stödja `Set-Content`-och `Add-Content`-cmdletar. Den här metoden returnerar innehålls skrivaren för objektet som finns på den angivna sökvägen.

Här är implementeringen av [system. Management. Automation. Provider. Icontentcmdletprovider. Getcontentwriter *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) för den här metoden.

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

[!code-csharp[AccessDBProviderSample06.cs](~/powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1863-L1880 "AccessDBProviderSample06.cs")]

#### <a name="things-to-remember-about-implementing-getcontentwriter"></a>Saker att komma ihåg om att implementera GetContentWriter

Följande villkor kan gälla för din implementering av [system. Management. Automation. Provider. Icontentcmdletprovider. Getcontentwriter *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter):

- När du definierar Provider-klassen kan en Windows PowerShell-innehålls leverantör deklarera ExpandWildcards, filtrera, ta med eller undanta från, från [system. Management. Automation. Provider. ProviderCapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) -uppräkningen. I dessa fall måste implementeringen av metoden [system. Management. Automation. Provider. Icontentcmdletprovider. Getcontentwriter *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) se till att den sökväg som skickas till metoden uppfyller kraven för de angivna funktionerna. För att göra detta ska metoden komma åt lämplig egenskap, till exempel [system. Management. Automation. Provider. Cmdletprovider. exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) och [system. Management. Automation. Provider. Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) egenskaper.

- Åsidosättningar av den här metoden bör som standard inte hämta en skrivare för objekt som är dolda från användaren, om inte egenskapen [system. Management. Automation. Provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) har angetts till `true`. Ett fel ska skrivas om sökvägen representerar ett objekt som är dolt från användaren och [system. Management. Automation. Provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) har angetts till `false`.

## <a name="attaching-dynamic-parameters-to-the-add-content-and-set-content-cmdlets"></a>Koppla dynamiska parametrar till cmdletarna Add-Content och set-Contents

`Add-Content`-och `Set-Content`-cmdletar kan kräva ytterligare dynamiska parametrar som lägger till en körning. För att tillhandahålla dessa dynamiska parametrar måste Windows PowerShell-innehålls leverantören implementera metoden [system. Management. Automation. Provider. Icontentcmdletprovider. Getcontentwriterdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) för att hantera dessa parametrar. Den här metoden hämtar dynamiska parametrar för objektet på den angivna sökvägen och returnerar ett objekt som har egenskaper och fält med parsande attribut som liknar en cmdlet-klass eller ett [system. Management. Automation. Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) -objekt. Windows PowerShell-körningsmiljön använder det returnerade objektet för att lägga till parametrarna i cmdletarna.

Den här Windows PowerShell container-providern implementerar inte den här metoden. Följande kod är dock standard implementeringen av den här metoden.

[!code-csharp[AccessDBProviderSample06.cs](~/powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1887-L1890 "AccessDBProviderSample06.cs")]

## <a name="clearing-content"></a>Rensar innehåll

Innehålls leverantören implementerar metoden [system. Management. Automation. Provider. Icontentcmdletprovider. Clearcontent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) i stöd för cmdleten `Clear-Content`. Den här metoden tar bort innehållet i objektet på den angivna sökvägen, men lämnar objektet intakt.

Här är implementeringen av metoden [system. Management. Automation. Provider. Icontentcmdletprovider. Clearcontent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) för den här providern.

[!code-csharp[AccessDBProviderSample06.cs](~/powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1775-L1812 "AccessDBProviderSample06.cs")]

#### <a name="things-to-remember-about-implementing-clearcontent"></a>Saker att komma ihåg om att implementera ClearContent

Följande villkor kan gälla för en implementering av [system. Management. Automation. Provider. Icontentcmdletprovider. Clearcontent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent):

- När du definierar Provider-klassen kan en Windows PowerShell-innehålls leverantör deklarera ExpandWildcards, filtrera, ta med eller undanta från, från [system. Management. Automation. Provider. ProviderCapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) -uppräkningen. I dessa fall måste implementeringen av metoden [system. Management. Automation. Provider. Icontentcmdletprovider. Clearcontent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) se till att den sökväg som skickas till metoden uppfyller kraven för de angivna funktionerna. För att göra detta ska metoden komma åt lämplig egenskap, till exempel [system. Management. Automation. Provider. Cmdletprovider. exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) och [system. Management. Automation. Provider. Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) egenskaper.

- Åsidosättningar av den här metoden bör som standard inte ta bort innehållet i objekt som är dolda från användaren, om inte egenskapen [system. Management. Automation. Provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) har angetts till `true`. Ett fel ska skrivas om sökvägen representerar ett objekt som är dolt från användaren och [system. Management. Automation. Provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) har angetts till `false`.

- Din implementering av metoden [system. Management. Automation. Provider. Icontentcmdletprovider. Clearcontent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) ska anropa [system. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) och verifiera dess retur värde innan du gör några ändringar i data lagret. Den här metoden används för att bekräfta körning av en åtgärd när en ändring görs i data lagret, till exempel att rensa innehåll. Metoden [system. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) skickar namnet på resursen som ska ändras till användaren, med Windows PowerShell-körningsmiljön som hanterar alla kommando rads inställningar eller variabler för att fastställa vad som ska visas.

  Efter att anropet till [system. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) returnerar `true`, ska metoden system [. Management. Automation. Provider. Icontentcmdletprovider. Clearcontent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) anropa metoden [system. Management. Automation. Provider. Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) . Den här metoden skickar ett meddelande till användaren för att tillåta feedback för att kontrol lera om åtgärden ska fortsätta. Anropet till [system. Management. Automation. Provider. Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) tillåter ytterligare kontroll av potentiellt skadliga system ändringar.

## <a name="attaching-dynamic-parameters-to-the-clear-content-cmdlet"></a>Bifoga dynamiska parametrar till cmdleten Clear-Content

`Clear-Content`-cmdlet kan kräva ytterligare dynamiska parametrar som läggs till vid körning. För att tillhandahålla dessa dynamiska parametrar måste Windows PowerShell-innehålls leverantören implementera metoden [system. Management. Automation. Provider. Icontentcmdletprovider. Clearcontentdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) för att hantera dessa parametrar. Den här metoden hämtar parametrarna för objektet på den angivna sökvägen. Den här metoden hämtar dynamiska parametrar för objektet på den angivna sökvägen och returnerar ett objekt som har egenskaper och fält med parsande attribut som liknar en cmdlet-klass eller ett [system. Management. Automation. Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) -objekt. Windows PowerShell-körningsmiljön använder det returnerade objektet för att lägga till parametrarna i cmdleten.

Den här Windows PowerShell container-providern implementerar inte den här metoden. Följande kod är dock standard implementeringen av den här metoden.

```csharp
public object ClearContentDynamicParameters(string path)
{
    return null;
}
```

[!code-csharp[AccessDBProviderSample06.cs](~/powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1819-L1822 "AccessDBProviderSample06.cs")]

## <a name="code-sample"></a>Kod exempel

Fullständig exempel kod finns i [kod exemplet för AccessDbProviderSample06](./accessdbprovidersample06-code-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definiera objekt typer och formatering

När du skriver en provider kan det vara nödvändigt att lägga till medlemmar i befintliga objekt eller definiera nya objekt. När detta är färdigt måste du skapa en typ fil som Windows PowerShell kan använda för att identifiera medlemmar i objektet och en format fil som definierar hur objektet visas. Mer information finns i [utöka objekt typer och formatering](/previous-versions/ms714665(v=vs.85)).

## <a name="building-the-windows-powershell-provider"></a>Skapa Windows PowerShell-providern

Se [hur du registrerar cmdlets, providers och värd program](/previous-versions/ms714644(v=vs.85)).

## <a name="testing-the-windows-powershell-provider"></a>Testa Windows PowerShell-providern

När din Windows PowerShell-provider har registrerats med Windows PowerShell kan du testa den genom att köra cmdlets som stöds på kommando raden. Testa t. ex. exempel innehålls leverantören.

Använd `Get-Content`-cmdlet för att hämta innehållet i det angivna objektet i databas tabellen på den sökväg som anges av parametern `Path`. Parametern `ReadCount` anger antalet objekt som den definierade innehålls läsaren ska läsa (standard 1). Med följande kommando post hämtar cmdleten två rader (objekt) från tabellen och visar deras innehåll. Observera att följande exempel på utdata använder en fiktiv Access-databas.

```powershell
Get-Content -Path mydb:\Customers -ReadCount 2
```

```Output
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

[Skapa Windows PowerShell-leverantörer](./how-to-create-a-windows-powershell-provider.md)

[Utforma din Windows PowerShell-Provider](./designing-your-windows-powershell-provider.md)

[Utöka objekt typer och formatering](/previous-versions//ms714665(v=vs.85))

[Implementera en Windows PowerShell-Provider för navigering](./creating-a-windows-powershell-navigation-provider.md)

[Registrera cmdlets, providers och värd program](/previous-versions/ms714644(v=vs.85))

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Windows PowerShell Programmer ' s guide](./windows-powershell-programmer-s-guide.md)
