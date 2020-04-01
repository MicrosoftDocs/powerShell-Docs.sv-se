---
title: Skapa en Windows PowerShell-navigeringsprovider
ms.date: 09/13/2016
ms.topic: article
ms.assetid: 8bd3224d-ca6f-4640-9464-cb4d9f4e13b1
ms.openlocfilehash: 7ca7e3ca6feeba018ad793d074caf67cd9506a68
ms.sourcegitcommit: 30ccbbb32915b551c4cd4c91ef1df96b5b7514c4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/01/2020
ms.locfileid: "80500810"
---
# <a name="creating-a-windows-powershell-navigation-provider"></a>Skapa en Windows PowerShell-navigeringsprovider

I det här avsnittet beskrivs hur du skapar en Windows PowerShell-navigerings leverantör som kan navigera i data lagret. Den här typen av provider stöder rekursiva kommandon, kapslade behållare och relativa sökvägar.

> [!NOTE]
> Du kan ladda ned C# käll filen (AccessDBSampleProvider05.CS) för den här providern med hjälp av Microsoft Windows Software Development Kit för Windows Vista och .NET Framework 3,0 Runtime-komponenter. Instruktioner för hämtning finns i [Installera Windows PowerShell och ladda ned Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).
> De hämtade källfilerna finns i mappen **\<PowerShell-exempel >** . Mer information om implementeringar av andra Windows PowerShell-leverantörer finns i [utforma din Windows PowerShell-Provider](./designing-your-windows-powershell-provider.md).

Leverantören som beskrivs här aktiverar användaren som hanterar en Access-databas som en enhet så att användaren kan navigera till data tabellerna i databasen. När du skapar en egen navigerings leverantör kan du implementera metoder som kan göra enhets kvalificerade sökvägar nödvändiga för navigering, normalisera relativa sökvägar, flytta objekt i data lagret, samt metoder som får underordnade namn, hämta den överordnade sökvägen till ett objekt och testa för att identifiera om ett objekt är en behållare.

> [!CAUTION]
> Tänk på att den här designen förutsätter en databas som har ett fält med namn-ID, och att fält typen är LongInteger.

## <a name="define-the-windows-powershell-provider"></a>Definiera Windows PowerShell-providern

En Windows PowerShell-navigerings leverantör måste skapa en .NET-klass som härleds från Bask Lassen [system. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) . Här är klass definitionen för den navigerings leverantör som beskrivs i det här avsnittet.

[!code-csharp[AccessDBProviderSample05.cs](~/powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample05/AccessDBProviderSample05.cs#L31-L32 "AccessDBProviderSample05.cs")]

Observera att i den här providern innehåller attributet [system. Management. Automation. Provider. Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) två parametrar. Den första parametern anger ett användarvänligt namn för den provider som används av Windows PowerShell. Den andra parametern anger de Windows PowerShell-funktioner som providern exponerar för Windows PowerShell-körningsmiljön under kommando bearbetning. Det finns inga Windows PowerShell-funktioner som har lagts till för den här providern.

## <a name="defining-base-functionality"></a>Definiera grundläggande funktioner

Enligt beskrivningen i [utforma din PS-Provider](./designing-your-windows-powershell-provider.md)härleds klassen [system. Management. Automation. Provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) från flera andra klasser som tillhandahöll olika funktioner i providern. En Windows PowerShell-navigerings leverantör måste därför definiera alla funktioner som tillhandahålls av dessa klasser.

Om du vill implementera funktioner för att lägga till datorspecifik initierings information och släppa resurser som används av providern, se [skapa en grundläggande PS-Provider](./creating-a-basic-windows-powershell-provider.md). De flesta leverantörer (inklusive leverantören som beskrivs här) kan dock använda standard implementeringen av den här funktionen i Windows PowerShell.

För att få åtkomst till data lagret via en Windows PowerShell-enhet måste du implementera metoderna i Bask Lassen [system. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) . Mer information om hur du implementerar dessa metoder finns i [skapa en provider för Windows PowerShell-enheter](./creating-a-windows-powershell-drive-provider.md).

Om du vill ändra objekt i ett data lager, till exempel hämta, ange och rensa objekt, måste providern implementera de metoder som tillhandahålls av Bask Lassen [system. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) . Mer information om hur du implementerar dessa metoder finns i [skapa en Windows PowerShell-dataprovider](./creating-a-windows-powershell-item-provider.md).

För att komma till underordnade objekt, eller deras namn, för data lagret, samt metoder för att skapa, kopiera, byta namn på och ta bort objekt, måste du implementera de metoder som tillhandahålls av Bask Lassen [system. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) . Mer information om hur du implementerar dessa metoder finns i [skapa en Windows PowerShell container-Provider](./creating-a-windows-powershell-container-provider.md).

## <a name="creating-a-windows-powershell-path"></a>Skapa en Windows PowerShell-sökväg

Windows PowerShell-navigerings leverantör använder en provider-intern Windows PowerShell-sökväg för att navigera i objekt i data lagret. För att skapa en provider – intern sökväg måste providern implementera metoden [system. Management. Automation. Provider. Navigationcmdletprovider. Makepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) för att stödja anrop från cmdlet: en kombinations Sök väg. Den här metoden kombinerar en överordnad och underordnad sökväg till en provider – intern sökväg med en providerspecifika Sök vägs avgränsare mellan de överordnade och underordnade Sök vägarna.

Standard implementeringen tar sökvägar med "/" eller "\\" som Sök vägs avgränsare, normaliserar Sök vägs avgränsaren till "\\", kombinerar den överordnade och underordnade sökvägen med avgränsaren, och returnerar sedan en sträng som innehåller de kombinerade Sök vägarna.

Den här navigerings leverantören implementerar inte den här metoden. Följande kod är dock standard implementeringen av metoden [system. Management. Automation. Provider. Navigationcmdletprovider. Makepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) .

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermakepath](Msh_samplestestcmdlets#testprovidermakepath)]  -->

#### <a name="things-to-remember-about-implementing-makepath"></a>Saker att komma ihåg om att implementera MakePath

Följande villkor kan gälla för din implementering av [system. Management. Automation. Provider. Navigationcmdletprovider. Makepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath):

- Din implementering av metoden [system. Management. Automation. Provider. Navigationcmdletprovider. Makepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) ska inte verifiera sökvägen som en giltig fullständig sökväg i namn området för providern. Tänk på att varje parameter bara kan representera en del av en sökväg, och de kombinerade delarna kanske inte genererar en fullständigt kvalificerad sökväg. Till exempel kan metoden [system. Management. Automation. Provider. Navigationcmdletprovider. Makepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) för fil systemets Provider ta emot "Windows\System32" i parametern `parent` och "ABC. dll" i `child`-parametern. Metoden ansluter till dessa värden med avgränsaren "\\" och returnerar "windows\system32\abc.dll", vilket inte är en fullständigt kvalificerad fil system Sök väg.

  > [!IMPORTANT]
  > De Sök vägs delar som anges i anropet till [system. Management. Automation. Provider. Navigationcmdletprovider. Makepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) kan innehålla tecken som inte tillåts i Providerns namn område. Dessa tecken används förmodligen för expansion av jokertecken och implementeringen av den här metoden bör inte ta bort dem.

## <a name="retrieving-the-parent-path"></a>Hämtar överordnad sökväg

Windows PowerShell-navigerings leverantörer implementerar metoden [system. Management. Automation. Provider. Navigationcmdletprovider. Getparentpath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) för att hämta den överordnade delen av den angivna fullständiga eller delvis providerspecifika sökvägen. Metoden tar bort den underordnade delen av sökvägen och returnerar den överordnade Sök vägs delen. Parametern `root` anger den fullständigt kvalificerade sökvägen till roten på en enhet. Den här parametern kan vara null eller tom om en monterad enhet inte används för hämtnings åtgärden. Om en rot anges måste metoden returnera en sökväg till en behållare i samma träd som roten.

Exempel navigerings leverantören åsidosätter inte den här metoden, men använder standard implementeringen.
Den accepterar sökvägar som använder både "/" och "\\" som Sök vägs avgränsare. Det normaliserar först sökvägen till att bara ha "\\"-avgränsare och delar sedan upp den överordnade sökvägen på den sista "\\" och returnerar den överordnade sökvägen.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetparentpath](Msh_samplestestcmdlets#testprovidergetparentpath)]  -->

#### <a name="to-remember-about-implementing-getparentpath"></a>Kom ihåg att implementera GetParentPath

Din implementering av metoden [system. Management. Automation. Provider. Navigationcmdletprovider. Getparentpath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) ska dela upp sökvägen lexikalt på Sök vägs avgränsaren för Providerns namn område. Till exempel använder fil namns leverantören den här metoden för att söka efter den senaste "\\" och returnerar allt till vänster om avgränsaren.

## <a name="retrieve-the-child-path-name"></a>Hämta namnet på den underordnade sökvägen

Navigerings leverantören implementerar metoden [system. Management. Automation. Provider. Navigationcmdletprovider. Getchildname *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) för att hämta namnet (löv element) för underordnat objekt som finns på den angivna fullständiga eller delvis providerspecifika sökvägen.

Exempel navigerings leverantören åsidosätter inte den här metoden. Standard implementeringen visas nedan. Den accepterar sökvägar som använder både "/" och "\\" som Sök vägs avgränsare. Det normaliserar först sökvägen till att bara ha "\\"-avgränsare och delar sedan upp den överordnade sökvägen på den sista "\\" och returnerar namnet på den underordnade Sök vägs delen.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchildname](Msh_samplestestcmdlets#testprovidergetchildname)]  -->

#### <a name="things-to-remember-about-implementing-getchildname"></a>Saker att komma ihåg om att implementera GetChildName

Din implementering av metoden [system. Management. Automation. Provider. Navigationcmdletprovider. Getchildname *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) ska dela upp sökvägen lexikalt på Sök vägs avgränsaren. Om den angivna sökvägen inte innehåller några Sök vägs avgränsare ska metoden returnera sökvägen oförändrad.

> [!IMPORTANT]
> Sökvägen som anges i anropet till den här metoden kan innehålla tecken som är ogiltiga i namn området för providern. De här tecknen används förmodligen för matchning av jokertecken eller reguljära uttryck, och implementeringen av den här metoden bör inte ta bort dem.

## <a name="determining-if-an-item-is-a-container"></a>Avgöra om ett objekt är en behållare

Navigerings leverantören kan implementera metoden [system. Management. Automation. Provider. Navigationcmdletprovider. Isitemcontainer *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) för att avgöra om den angivna sökvägen indikerar en behållare. Det returnerar true om sökvägen representerar en behållare och annars FALSE. Användaren behöver den här metoden för att kunna använda `Test-Path`-cmdleten för den angivna sökvägen.

Följande kod visar implementeringen [system. Management. Automation. Provider. Navigationcmdletprovider. Isitemcontainer *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) i vår exempel navigerings leverantör. Metoden kontrollerar att den angivna sökvägen är korrekt och om tabellen finns och returnerar true om sökvägen indikerar en behållare.

[!code-csharp[AccessDBProviderSample05.cs](~/powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample05/AccessDBProviderSample05.cs#L847-L872 "AccessDBProviderSample05.cs")]

#### <a name="things-to-remember-about-implementing-isitemcontainer"></a>Saker att komma ihåg om att implementera IsItemContainer

Din navigerings leverantörs .NET-klass kan deklarera leverantörs funktioner i ExpandWildcards, filtrera, ta med eller undanta, från uppräkningen [system. Management. Automation. Provider. ProviderCapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . I det här fallet måste implementeringen av [system. Management. Automation. Provider. Navigationcmdletprovider. Isitemcontainer *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) se till att den angivna sökvägen uppfyller kraven. För att göra detta ska metoden komma åt lämplig egenskap, till exempel egenskapen [system. Management. Automation. Provider. Cmdletprovider. exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) .

## <a name="moving-an-item"></a>Flytta ett objekt

Som stöd för `Move-Item`-cmdlet implementerar navigerings leverantören metoden [system. Management. Automation. Provider. Navigationcmdletprovider. Moveitem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) . Den här metoden flyttar det objekt som anges av parametern `path` till behållaren på den sökväg som anges i parametern `destination`.

Exempel navigerings leverantören åsidosätter inte metoden [system. Management. Automation. Provider. Navigationcmdletprovider. Moveitem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) . Följande är standard implementeringen.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermoveitem](Msh_samplestestcmdlets#testprovidermoveitem)]  -->

#### <a name="things-to-remember-about-implementing-moveitem"></a>Saker att komma ihåg om att implementera MoveItem

Din navigerings leverantörs .NET-klass kan deklarera leverantörs funktioner i ExpandWildcards, filtrera, ta med eller undanta, från uppräkningen [system. Management. Automation. Provider. ProviderCapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) . I det här fallet måste implementeringen av [system. Management. Automation. Provider. Navigationcmdletprovider. Moveitem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) se till att den angivna sökvägen uppfyller kraven. För att göra detta ska metoden komma åt lämplig egenskap, till exempel egenskapen **CmdletProvider. exclud** .

Åsidosättningar av den här metoden bör som standard inte flytta objekt över befintliga objekt om inte egenskapen [system. Management. Automation. Provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) anges till `true`. Till exempel kommer inte fil Systems leverantören att kopiera c:\temp\abc.txt över en befintlig c:\bar.txt-fil om inte egenskapen [system. Management. Automation. Provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) anges till `true`. Om sökvägen som anges i parametern `destination` finns och är en behållare, krävs inte egenskapen [system. Management. Automation. Provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) . I det här fallet ska [system. Management. Automation. Provider. Navigationcmdletprovider. Moveitem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) flytta objektet som anges av parametern `path` till den behållare som anges av parametern `destination` som underordnad.

Din implementering av metoden [system. Management. Automation. Provider. Navigationcmdletprovider. Moveitem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) ska anropa [system. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) och kontrol lera dess retur värde innan du gör några ändringar i data lagret. Den här metoden används för att bekräfta körning av en åtgärd när en ändring görs i system tillstånd, t. ex. borttagning av filer.
[System. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) skickar namnet på den resurs som ska ändras till användaren, med Windows PowerShell-körningsmiljön med hänsyn till eventuella kommando rads inställningar eller variabler för att fastställa vad som ska visas för användaren.

Efter att anropet till [system. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) returnerar `true`, ska metoden system [. Management. Automation. Provider. Navigationcmdletprovider. Moveitem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) anropa metoden [system. Management. Automation. Provider. Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) . Den här metoden skickar ett meddelande till användaren för att ge feedback till att säga om åtgärden bör fortsätta. Leverantören bör anropa [system. Management. Automation. Provider. Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) som en ytterligare kontroll för potentiellt skadliga system ändringar.

## <a name="attaching-dynamic-parameters-to-the-move-item-cmdlet"></a>Bifoga dynamiska parametrar till flytt-item-cmdleten

Ibland kräver `Move-Item` cmdlet ytterligare parametrar som anges dynamiskt vid körning. För att tillhandahålla dessa dynamiska parametrar, måste navigerings leverantören implementera metoden [system. Management. Automation. Provider. Navigationcmdletprovider. Moveitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) för att hämta de parameter värden som krävs från objektet vid den angivna sökvägen och returnera ett objekt som har egenskaper och fält med parsande attribut som liknar en cmdlet-klass eller ett [system. Management. Automation. Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) -objekt.

Den här navigerings leverantören implementerar inte den här metoden. Följande kod är dock standard implementeringen av [system. Management. Automation. Provider. Navigationcmdletprovider. Moveitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermoveitemdynamicparameters](Msh_samplestestcmdlets#testprovidermoveitemdynamicparameters)]  -->

## <a name="normalizing-a-relative-path"></a>Normalisera en relativ sökväg

Navigerings leverantören implementerar metoden [system. Management. Automation. Provider. Navigationcmdletprovider. Normalizerelativepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) för att normalisera den fullständigt kvalificerade sökvägen som anges i parametern `path` som relativ till den sökväg som anges av parametern `basePath`. Metoden returnerar en sträng representation av den normaliserade sökvägen. Det skriver ett fel om parametern `path` anger en sökväg som inte finns.

Exempel navigerings leverantören åsidosätter inte den här metoden. Följande är standard implementeringen.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernormalizepath](Msh_samplestestcmdlets#testprovidernormalizepath)]  -->

#### <a name="things-to-remember-about-implementing-normalizerelativepath"></a>Saker att komma ihåg om att implementera NormalizeRelativePath

Din implementering av [system. Management. Automation. Provider. Navigationcmdletprovider. Normalizerelativepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) ska parsa `path` parameter, men den behöver inte använda helt syntaktisk tolkning. Du uppmanas att utforma den här metoden för att använda sökvägen för att leta upp Sök vägs informationen i data lagret och skapa en sökväg som matchar Skift läget och syntaxen för standardiserad sökväg.

## <a name="code-sample"></a>Kod exempel

Fullständig exempel kod finns i [kod exemplet för AccessDbProviderSample05](./accessdbprovidersample05-code-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definiera objekt typer och formatering

Det är möjligt för en provider att lägga till medlemmar i befintliga objekt eller definiera nya objekt. Mer information finns i[utöka objekt typer och formatering](/previous-versions/ms714665(v=vs.85)).

## <a name="building-the-windows-powershell-provider"></a>Skapa Windows PowerShell-providern

Mer information finns i [så här registrerar du cmdlets, providers och värd program](/previous-versions/ms714644(v=vs.85)).

## <a name="testing-the-windows-powershell-provider"></a>Testa Windows PowerShell-providern

När din Windows PowerShell-provider har registrerats med Windows PowerShell kan du testa den genom att köra cmdlets som stöds på kommando raden, inklusive cmdletar som gjorts tillgängliga av härledning. I det här exemplet kommer exempel navigerings leverantören att testa.

1. Kör det nya gränssnittet och Använd `Set-Location` cmdlet för att ange sökvägen för att ange Access-databasen.

   ```powershell
   Set-Location mydb:
   ```

2. Kör nu `Get-Childitem` cmdlet för att hämta en lista över databas objekt, som är tillgängliga databas tabeller. För varje tabell hämtar denna cmdlet också antalet tabell rader.

   ```powershell
   Get-ChildItem | Format-Table rowcount,name -AutoSize
   ```

   ```Output
   RowCount   Name
   --------   ----
        180   MSysAccessObjects
          0   MSysACEs
          1   MSysCmdbars
          0   MSysIMEXColumns
          0   MSysIMEXSpecs
          0   MSysObjects
          0   MSysQueries
          7   MSysRelationships
          8   Categories
         91   Customers
          9   Employees
       2155   Order Details
        830   Orders
         77   Products
          3   Shippers
         29   Suppliers
   ```

3. Använd `Set-Location`-cmdleten igen för att ange platsen för tabellen anställdas data.

   ```powershell
   Set-Location Employees
   ```

4. Nu ska vi använda `Get-Location` cmdlet för att hämta sökvägen till tabellen anställda.

   ```powershell
   Get-Location
   ```

   ```Output
   Path
   ----
   mydb:\Employees
   ```

5. Använd nu `Get-Childitem` cmdlet-skickas till `Format-Table`-cmdleten. Den här uppsättningen cmdlet: ar hämtar objekten för data tabellen anställda, som är tabell rader. De är formaterade som de anges av `Format-Table`-cmdleten.

   ```powershell
   Get-ChildItem | Format-Table rownumber,psiscontainer,data -AutoSize
   ```

   ```Output
   RowNumber   PSIsContainer   Data
   ---------   --------------   ----
   0           False            System.Data.DataRow
   1           False            System.Data.DataRow
   2           False            System.Data.DataRow
   3           False            System.Data.DataRow
   4           False            System.Data.DataRow
   5           False            System.Data.DataRow
   6           False            System.Data.DataRow
   7           False            System.Data.DataRow
   8           False            System.Data.DataRow
   ```

6. Nu kan du köra cmdleten `Get-Item` för att hämta objekten för rad 0 i tabellen anställdas data.

   ```powershell
   Get-Item 0
   ```

   ```Output
   PSPath        : AccessDB::C:\PS\Northwind.mdb\Employees\0
   PSParentPath  : AccessDB::C:\PS\Northwind.mdb\Employees
   PSChildName   : 0
   PSDrive       : mydb
   PSProvider    : System.Management.Automation.ProviderInfo
   PSIsContainer : False
   Data           : System.Data.DataRow
   RowNumber      : 0
   ```

7. Använd `Get-Item` cmdlet igen för att hämta medarbetar data för objekten på rad 0.

   ```powershell
   (Get-Item 0).data
   ```

   ```Output
   EmployeeID      : 1
   LastName        : Davis
   FirstName       : Sara
   Title           : Sales Representative
   TitleOfCourtesy : Ms.
   BirthDate       : 12/8/1968 12:00:00 AM
   HireDate        : 5/1/1992 12:00:00 AM
   Address         : 4567 Main Street
                     Apt. 2A
   City            : Buffalo
   Region          : NY
   PostalCode      : 98052
   Country         : USA
   HomePhone       : (206) 555-9857
   Extension       : 5467
   Photo           : EmpID1.bmp
   Notes           : Education includes a BA in psychology from
                     Colorado State University. She also completed "The
                     Art of the Cold Call."  Nancy is a member of
                     Toastmasters International.
   ReportsTo       : 2
   ```

## <a name="see-also"></a>Se även

[Skapa Windows PowerShell-leverantörer](./how-to-create-a-windows-powershell-provider.md)

[Utforma din Windows PowerShell-Provider](./designing-your-windows-powershell-provider.md)

[Utöka objekt typer och formatering](/previous-versions/ms714665(v=vs.85))

[Implementera en container Windows PowerShell-Provider](./creating-a-windows-powershell-container-provider.md)

[Registrera cmdlets, providers och värd program](/previous-versions/ms714644(v=vs.85))

[Windows PowerShell Programmer ' s guide](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
