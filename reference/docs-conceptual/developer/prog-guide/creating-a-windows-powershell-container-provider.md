---
title: Skapa en Windows PowerShell-containerprovider
ms.date: 09/13/2016
ms.topic: article
ms.openlocfilehash: eec92d526ad78d2351eef6679eaa0df19900715b
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80978499"
---
# <a name="creating-a-windows-powershell-container-provider"></a>Skapa en Windows PowerShell-containerprovider

I det här avsnittet beskrivs hur du skapar en Windows PowerShell-provider som kan arbeta med data lager i flera lager. För den här typen av data lager innehåller lagrings platsen på den högsta nivån rot objekten och varje efterföljande nivå kallas nod för underordnade objekt. Genom att tillåta att användaren arbetar på dessa underordnade noder kan en användare interagera hierarkiskt via data lagret.

Leverantörer som kan arbeta med data lager på flera nivåer kallas Windows PowerShell container providers. Tänk dock på att en Windows PowerShell container-Provider bara kan användas när det finns en behållare (inga kapslade behållare) med objekten i den. Om det finns kapslade behållare måste du implementera en Windows PowerShell-navigerings-Provider. Mer information om hur du implementerar Windows PowerShell-navigerings-providern finns i [skapa en Windows PowerShell-navigerings leverantör](./creating-a-windows-powershell-navigation-provider.md).

> [!NOTE]
> Du kan ladda ned C# käll filen (AccessDBSampleProvider04.CS) för den här providern med hjälp av Microsoft Windows Software Development Kit för Windows Vista och .NET Framework 3,0 Runtime-komponenter. Instruktioner för hämtning finns i [Installera Windows PowerShell och ladda ned Windows POWERSHELL SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).
> De hämtade källfilerna finns i mappen **\<PowerShell-exempel >** . Mer information om implementeringar av andra Windows PowerShell-leverantörer finns i [utforma din Windows PowerShell-Provider](./designing-your-windows-powershell-provider.md).

Windows PowerShell container-providern som beskrivs här definierar databasen som dess enda behållare, med tabeller och rader i databasen som definierats som objekt i behållaren.

> [!CAUTION]
> Tänk på att den här designen förutsätter en databas som har ett fält med namn-ID, och att fält typen är LongInteger.

## <a name="defining-a-windows-powershell-container-provider-class"></a>Definiera en klass för Windows PowerShell container Provider

En Windows PowerShell container-Provider måste definiera en .NET-klass som är härledd från Bask Lassen [system. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) . Här är klass definitionen för Windows PowerShell container-providern som beskrivs i det här avsnittet.

```csharp
[CmdletProvider("AccessDB", ProviderCapabilities.None)]
public class AccessDBProvider : ContainerCmdletProvider
```

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs" range="34-35":::

Observera att i den här klass definitionen innehåller attributet [system. Management. Automation. Provider. Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) två parametrar. Den första parametern anger ett användarvänligt namn för den provider som används av Windows PowerShell. Den andra parametern anger de Windows PowerShell-funktioner som providern exponerar för Windows PowerShell-körningsmiljön under kommando bearbetning. Det finns inga Windows PowerShell-funktioner som har lagts till för den här providern.

## <a name="defining-base-functionality"></a>Definiera grundläggande funktioner

Enligt beskrivningen i [utforma din Windows PowerShell-Provider](./designing-your-windows-powershell-provider.md)härleds klassen [system. Management. Automation. Provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) från flera andra klasser som tillhandahöll olika funktioner i providern. En Windows PowerShell container-Provider måste därför definiera alla funktioner som tillhandahålls av dessa klasser.

Om du vill implementera funktioner för att lägga till datorspecifik initierings information och släppa resurser som används av providern, se [skapa en grundläggande Windows PowerShell-Provider](./creating-a-basic-windows-powershell-provider.md).
De flesta leverantörer (inklusive providern som beskrivs här) kan dock använda standard implementeringen av den här funktionen som tillhandahålls av Windows PowerShell.

För att få åtkomst till data lagret måste providern implementera metoderna i Bask Lassen [system. Management. Automation. Provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) . Mer information om hur du implementerar dessa metoder finns i [skapa en provider för Windows PowerShell-enheter](./creating-a-windows-powershell-drive-provider.md).

Om du vill ändra objekt i ett data lager, till exempel hämta, ange och rensa objekt, måste providern implementera de metoder som tillhandahålls av Bask Lassen [system. Management. Automation. Provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) . Mer information om hur du implementerar dessa metoder finns i [skapa en Windows PowerShell-dataprovider](./creating-a-windows-powershell-item-provider.md).

## <a name="retrieving-child-items"></a>Underordnade objekt hämtas

För att hämta ett underordnat objekt, måste Windows PowerShell container Provider åsidosätta metoden [system. Management. Automation. Provider. Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) för att stödja anrop från `Get-ChildItem` cmdlet. Den här metoden hämtar underordnade objekt från data lagret och skriver dem till pipelinen som objekt. Om parametern `recurse` för cmdleten anges hämtar metoden alla underordnade oavsett vilken nivå de befinner sig på. Om parametern `recurse` inte anges hämtar metoden bara en nivå med underordnade.

Här är implementeringen av metoden [system. Management. Automation. Provider. Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) för den här providern. Observera att den här metoden hämtar underordnade objekt i alla databas tabeller när sökvägen visar Access-databasen och hämtar de underordnade objekten från raderna i tabellen om sökvägen indikerar en data tabell.

```csharp
protected override void GetChildItems(string path, bool recurse)
{
    // If path represented is a drive then the children in the path are
    // tables. Hence all tables in the drive represented will have to be
    // returned
    if (PathIsDrive(path))
    {
        foreach (DatabaseTableInfo table in GetTables())
        {
            WriteItemObject(table, path, true);

            // if the specified item exists and recurse has been set then
            // all child items within it have to be obtained as well
            if (ItemExists(path) && recurse)
            {
                GetChildItems(path + pathSeparator + table.Name, recurse);
            }
        } // foreach (DatabaseTableInfo...
    } // if (PathIsDrive...
    else
    {
        // Get the table name, row number and type of path from the
        // path specified
        string tableName;
        int rowNumber;

        PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

        if (type == PathType.Table)
        {
            // Obtain all the rows within the table
            foreach (DatabaseRowInfo row in GetRows(tableName))
            {
                WriteItemObject(row, path + pathSeparator + row.RowNumber,
                        false);
            } // foreach (DatabaseRowInfo...
        }
        else if (type == PathType.Row)
        {
            // In this case the user has directly specified a row, hence
            // just give that particular row
            DatabaseRowInfo row = GetRow(tableName, rowNumber);
            WriteItemObject(row, path + pathSeparator + row.RowNumber,
                        false);
        }
        else
        {
            // In this case, the path specified is not valid
            ThrowTerminatingInvalidPathException(path);
        }
    } // else
} // GetChildItems
```

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs" range="311-362":::

#### <a name="things-to-remember-about-implementing-getchilditems"></a>Saker att komma ihåg om att implementera GetChildItems

Följande villkor kan gälla för din implementering av [system. Management. Automation. Provider. Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems):

- När du definierar Provider-klassen kan en Windows PowerShell container-Provider deklarera ExpandWildcards, filtrera, ta med eller undanta från, från [system. Management. Automation. Provider. ProviderCapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) -uppräkningen. I dessa fall måste implementeringen av metoden [system. Management. Automation. Provider. Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) se till att den sökväg som skickas till metoden uppfyller kraven för de angivna funktionerna. För att göra detta ska metoden komma åt lämplig egenskap, till exempel [system. Management. Automation. Provider. Cmdletprovider. exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) och [system. Management. Automation. Provider. Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) egenskaper.

- Implementeringen av den här metoden bör ta hänsyn till alla former av åtkomst till objektet som kan göra objektet synligt för användaren. Om en användare till exempel har Skriv behörighet till en fil via fil systemets Provider (som tillhandahålls av Windows PowerShell), men inte Läs åtkomst, finns filen fortfarande och [system. Management. Automation. Provider. Itemcmdletprovider. Itemexists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) returnerar `true`. Din implementering kan kräva att ett överordnat objekt kontrol leras för att se om det underordnade kan räknas upp.

- När du skriver flera objekt kan metoden [system. Management. Automation. Provider. Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) ta lite tid. Du kan utforma din Provider för att skriva objekt med hjälp av metoden [system. Management. Automation. Provider. Cmdletprovider. Writeitemobject *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) i taget. Med den här metoden visas objekten för användaren i en data ström.

- Din implementering av [system. Management. Automation. Provider. Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) ansvarar för att förhindra oändlig rekursion när det finns cirkel länkar och liknande. Ett lämpligt avslutande undantag bör utsättas för att avspegla ett sådant villkor.

## <a name="attaching-dynamic-parameters-to-the-get-childitem-cmdlet"></a>Koppla dynamiska parametrar till get-ChildItem-cmdleten

Ibland kräver den `Get-ChildItem`-cmdlet som anropar [system. Management. Automation. Provider. Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) ytterligare parametrar som anges dynamiskt vid körning. För att tillhandahålla dessa dynamiska parametrar måste Windows PowerShell container Provider implementera metoden [system. Management. Automation. Provider. Containercmdletprovider. Getchilditemsdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) . Den här metoden hämtar dynamiska parametrar för objektet på den angivna sökvägen och returnerar ett objekt som har egenskaper och fält med parsande attribut som liknar en cmdlet-klass eller ett [system. Management. Automation. Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) -objekt. Windows PowerShell-körningsmiljön använder det returnerade objektet för att lägga till parametrarna i `Get-ChildItem`-cmdleten.

Den här Windows PowerShell container-providern implementerar inte den här metoden. Följande kod är dock standard implementeringen av den här metoden.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchilditemsdynamicparameters](Msh_samplestestcmdlets#testprovidergetchilditemsdynamicparameters)]  -->

## <a name="retrieving-child-item-names"></a>Hämtar underordnade objekt namn

För att hämta namnen på underordnade objekt, måste Windows PowerShell container Provider åsidosätta metoden [system. Management. Automation. Provider. Containercmdletprovider. Getchildnames *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) för att stödja anrop från `Get-ChildItem` cmdlet när dess `Name`-parameter har angetts. Med den här metoden hämtas namnen på de underordnade objekten för den angivna sökvägen eller underordnade objekt namn för alla behållare om parametern `returnAllContainers` för cmdlet: en anges. Ett underordnat namn är löv delen av en sökväg. Till exempel är det underordnade namnet för sökvägen c:\windows\system32\abc.dll "ABC. dll". Det underordnade namnet för katalogen c:\Windows\System32 är "system32".

Här är implementeringen av metoden [system. Management. Automation. Provider. Containercmdletprovider. Getchildnames *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) för den här providern. Observera att metoden hämtar tabell namn om den angivna sökvägen anger åtkomst databasen (enhet) och rad nummer om sökvägen indikerar en tabell.

```csharp
protected override void GetChildNames(string path,
                            ReturnContainers returnContainers)
{
    // If the path represented is a drive, then the child items are
    // tables. get the names of all the tables in the drive.
    if (PathIsDrive(path))
    {
        foreach (DatabaseTableInfo table in GetTables())
        {
            WriteItemObject(table.Name, path, true);
        } // foreach (DatabaseTableInfo...
    } // if (PathIsDrive...
    else
    {
        // Get type, table name and row number from path specified
        string tableName;
        int rowNumber;

        PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

        if (type == PathType.Table)
        {
            // Get all the rows in the table and then write out the
            // row numbers.
            foreach (DatabaseRowInfo row in GetRows(tableName))
            {
                WriteItemObject(row.RowNumber, path, false);
            } // foreach (DatabaseRowInfo...
        }
        else if (type == PathType.Row)
        {
            // In this case the user has directly specified a row, hence
            // just give that particular row
            DatabaseRowInfo row = GetRow(tableName, rowNumber);

            WriteItemObject(row.RowNumber, path, false);
        }
        else
        {
            ThrowTerminatingInvalidPathException(path);
        }
    } // else
} // GetChildNames
```

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs" range="369-411":::

#### <a name="things-to-remember-about-implementing-getchildnames"></a>Saker att komma ihåg om att implementera GetChildNames

Följande villkor kan gälla för din implementering av [system. Management. Automation. Provider. Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems):

- När du definierar Provider-klassen kan en Windows PowerShell container-Provider deklarera ExpandWildcards, filtrera, ta med eller undanta från, från [system. Management. Automation. Provider. ProviderCapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) -uppräkningen. I dessa fall måste implementeringen av metoden [system. Management. Automation. Provider. Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) se till att den sökväg som skickas till metoden uppfyller kraven för de angivna funktionerna. För att göra detta ska metoden komma åt lämplig egenskap, till exempel [system. Management. Automation. Provider. Cmdletprovider. exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) och [system. Management. Automation. Provider. Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) egenskaper.

  > [!NOTE]
  > Ett undantag till den här regeln inträffar när parametern `returnAllContainers` för cmdleten anges. I det här fallet ska metoden hämta ett underordnat namn för en behållare, även om den inte matchar värdena i [system. Management. Automation. Provider. Cmdletprovider. filter *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Filter), [system. Management. Automation. Provider. Cmdletprovider. include](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)*, eller [system. Management. Automation. Provider. Cmdletprovider. exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) Properties.

- Åsidosättningar av den här metoden bör som standard inte hämta namn på objekt som är allmänt dolda från användaren, om inte egenskapen [system. Management. Automation. Provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) anges. Om den angivna sökvägen indikerar en behållare krävs inte egenskapen [system. Management. Automation. Provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) .

- Din implementering av [system. Management. Automation. Provider. Containercmdletprovider. Getchildnames *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) ansvarar för att förhindra oändlig rekursion när det finns cirkel länkar och liknande. Ett lämpligt avslutande undantag bör utsättas för att avspegla ett sådant villkor.

## <a name="attaching-dynamic-parameters-to-the-get-childitem-cmdlet-name"></a>Bifoga dynamiska parametrar till get-ChildItem-cmdleten (namn)

Ibland kräver `Get-ChildItem`-cmdlet (med parametern `Name`) ytterligare parametrar som anges dynamiskt vid körning. För att tillhandahålla dessa dynamiska parametrar måste Windows PowerShell container Provider implementera metoden [system. Management. Automation. Provider. Containercmdletprovider. Getchildnamesdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) . Den här metoden hämtar dynamiska parametrar för objektet på den angivna sökvägen och returnerar ett objekt som har egenskaper och fält med parsande attribut som liknar en cmdlet-klass eller ett [system. Management. Automation. Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) -objekt. Windows PowerShell-körningsmiljön använder det returnerade objektet för att lägga till parametrarna i `Get-ChildItem`-cmdleten.

Den här providern implementerar inte den här metoden. Följande kod är dock standard implementeringen av den här metoden.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchildnamesdynamicparameters](Msh_samplestestcmdlets#testprovidergetchildnamesdynamicparameters)]  -->

## <a name="renaming-items"></a>Byta namn på objekt

Om du vill byta namn på ett objekt, måste en Windows PowerShell container-Provider åsidosätta metoden [system. Management. Automation. Provider. Containercmdletprovider. RenameItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) för att stödja anrop från `Rename-Item` cmdlet. Den här metoden ändrar namnet på objektet på den angivna sökvägen till det nya namn som anges. Det nya namnet måste alltid vara relativt till det överordnade objektet (behållaren).

Denna provider åsidosätter inte metoden [system. Management. Automation. Provider. Containercmdletprovider. RenameItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) . Följande är dock standard implementeringen.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderrenameitem](Msh_samplestestcmdlets#testproviderrenameitem)]  -->

#### <a name="things-to-remember-about-implementing-renameitem"></a>Saker att komma ihåg om att implementera RenameItem

Följande villkor kan gälla för din implementering av [system. Management. Automation. Provider. Containercmdletprovider. RenameItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem):

- När du definierar Provider-klassen kan en Windows PowerShell container-Provider deklarera ExpandWildcards, filtrera, ta med eller undanta från, från [system. Management. Automation. Provider. ProviderCapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) -uppräkningen. I dessa fall måste implementeringen av metoden [system. Management. Automation. Provider. Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) se till att den sökväg som skickas till metoden uppfyller kraven för de angivna funktionerna. För att göra detta ska metoden komma åt lämplig egenskap, till exempel [system. Management. Automation. Provider. Cmdletprovider. exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) och [system. Management. Automation. Provider. Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) egenskaper.

- Metoden [system. Management. Automation. Provider. Containercmdletprovider. RenameItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) är avsedd för att ändra namnet på ett objekt och inte för flytt åtgärder.
  Din implementering av metoden ska skriva ett fel om parametern `newName` innehåller Sök vägs avgränsare eller om det annars skulle medföra att objektet ändrar dess överordnade plats.

- Åsidosättningar av den här metoden bör som standard inte byta namn på objekt om inte egenskapen [system. Management. Automation. Provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) anges. Om den angivna sökvägen indikerar en behållare krävs inte egenskapen [system. Management. Automation. Provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) .

- Din implementering av metoden [system. Management. Automation. Provider. Containercmdletprovider. RenameItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) ska anropa [system. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) och kontrol lera dess retur värde innan du gör några ändringar i data lagret. Den här metoden används för att bekräfta körning av en åtgärd när en ändring görs i system tillstånd, till exempel att byta namn på filer.
  [System. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) skickar namnet på resursen som ska ändras till användaren, med Windows PowerShell-körningsmiljön med hänsyn till eventuella kommando rads inställningar eller variabler för att fastställa vad som ska visas.

  Efter att anropet till [system. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) returnerar `true`, ska metoden system [. Management. Automation. Provider. Containercmdletprovider. RenameItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) anropa metoden [system. Management. Automation. Provider. Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) . Den här metoden skickar ett meddelande till användaren för att tillåta ytterligare feedback för att säga om åtgärden bör fortsätta. En provider bör anropa [system. Management. Automation. Provider. Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) som ytterligare kontroll för potentiellt skadliga system ändringar.

## <a name="attaching-dynamic-parameters-to-the-rename-item-cmdlet"></a>Koppla dynamiska parametrar till cmdleten Rename-Item

Ibland kräver `Rename-Item` cmdlet ytterligare parametrar som anges dynamiskt vid körning. För att tillhandahålla dessa dynamiska parametrar måste Windows PowerShell container Provider implementera metoden [system. Management. Automation. Provider. Containercmdletprovider. Renameitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) . Den här metoden hämtar parametrarna för objektet vid den angivna sökvägen och returnerar ett objekt som har egenskaper och fält med parsande attribut som liknar en cmdlet-klass eller ett [system. Management. Automation. Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) -objekt. Windows PowerShell-körningsmiljön använder det returnerade objektet för att lägga till parametrarna i `Rename-Item`-cmdleten.

Den här behållar leverantören implementerar inte den här metoden. Följande kod är dock standard implementeringen av den här metoden.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderrenameitemdynamicparameters](Msh_samplestestcmdlets#testproviderrenameitemdynamicparameters)]  -->

## <a name="creating-new-items"></a>Nya objekt skapas

För att kunna skapa nya objekt måste en container leverantör implementera metoden [system. Management. Automation. Provider. Containercmdletprovider. NewItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) för att stödja anrop från `New-Item`-cmdlet. Den här metoden skapar ett data objekt som finns på den angivna sökvägen. Parametern `type` för cmdleten innehåller den providertyp som definierats för det nya objektet. Till exempel använder fil Systems leverantören en `type` parameter med värdet "File" eller "Directory". Parametern `newItemValue` för cmdleten anger ett providerspecifika värde för det nya objektet.

Här är implementeringen av metoden [system. Management. Automation. Provider. Containercmdletprovider. NewItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) för den här providern.

```csharp
protected override void NewItem( string path, string type, object newItemValue )
{
    // Create the new item here after
    // performing necessary validations
    //
    // WriteItemObject(newItemValue, path, false);

    // Example
    //
    // if (ShouldProcess(path, "new item"))
    // {
    //      // Create a new item and then call WriteObject
    //      WriteObject(newItemValue, path, false);
    // }

} // NewItem
```

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs" range="939-955":::

#### <a name="things-to-remember-about-implementing-newitem"></a>Saker att komma ihåg om att implementera NewItem

Följande villkor kan gälla för din implementering av [system. Management. Automation. Provider. Containercmdletprovider. NewItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem):

- Metoden [system. Management. Automation. Provider. Containercmdletprovider. NewItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) måste utföra en Skift läges okänslig jämförelse av strängen som skickas i `type`-parametern.
  Den bör också tillåta minst tvetydiga matchningar. För typerna "File" och "Directory" krävs till exempel bara den första bokstaven i disambiguate. Om parametern `type` anger en typ som providern inte kan skapa, ska metoden [system. Management. Automation. Provider. Containercmdletprovider. NewItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) skriva en ArgumentException med ett meddelande som anger vilka typer som providern kan skapa.

- För parametern `newItemValue` rekommenderas implementering av metoden [system. Management. Automation. Provider. Containercmdletprovider. NewItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) för att acceptera strängarna. Det bör också acceptera den typ av objekt som hämtas av metoden [system. Management. Automation. Provider. Itemcmdletprovider. getItem, *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) för samma sökväg. Metoden [system. Management. Automation. Provider. Containercmdletprovider. NewItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) kan använda metoden [system. Management. Automation. Languageprimitives. ConvertTo *](/dotnet/api/System.Management.Automation.LanguagePrimitives.ConvertTo) för att konvertera typer till önskad typ.

- Din implementering av metoden [system. Management. Automation. Provider. Containercmdletprovider. NewItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) ska anropa [system. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) och kontrol lera dess retur värde innan du gör några ändringar i data lagret. Efter anropet till [system. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) returnerar true, metoden [system. Management. Automation. Provider. Containercmdletprovider. NewItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) anropa metoden [system. Management. Automation. Provider. Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) som ytterligare kontroll för potentiellt skadliga system ändringar.

## <a name="attaching-dynamic-parameters-to-the-new-item-cmdlet"></a>Koppla dynamiska parametrar till cmdleten New-Item

Ibland kräver `New-Item` cmdlet ytterligare parametrar som anges dynamiskt vid körning. För att tillhandahålla dessa dynamiska parametrar måste container leverantören implementera metoden [system. Management. Automation. Provider. Containercmdletprovider. Newitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) . Den här metoden hämtar parametrarna för objektet vid den angivna sökvägen och returnerar ett objekt som har egenskaper och fält med parsande attribut som liknar en cmdlet-klass eller ett [system. Management. Automation. Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) -objekt. Windows PowerShell-körningsmiljön använder det returnerade objektet för att lägga till parametrarna i `New-Item`-cmdleten.

Den här providern implementerar inte den här metoden. Följande kod är dock standard implementeringen av den här metoden.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernewitemdynamicparameters](Msh_samplestestcmdlets#testprovidernewitemdynamicparameters)]  -->

## <a name="removing-items"></a>Tar bort objekt

För att ta bort objekt, måste Windows PowerShell-providern åsidosätta metoden [system. Management. Automation. Provider. Containercmdletprovider. RemoveItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) för att stödja anrop från `Remove-Item`-cmdleten. Den här metoden tar bort ett objekt från data lagret på den angivna sökvägen. Om parametern `recurse` för `Remove-Item`-cmdlet är inställd på `true`, tar metoden bort alla underordnade objekt oavsett deras nivå. Om parametern är inställd på `false`, tar metoden bara bort ett enstaka objekt på den angivna sökvägen.

Den här providern stöder inte borttagning av objekt. Följande kod är dock standard implementeringen av [system. Management. Automation. Provider. Containercmdletprovider. RemoveItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderremoveitem](Msh_samplestestcmdlets#testproviderremoveitem)]  -->

#### <a name="things-to-remember-about-implementing-removeitem"></a>Saker att komma ihåg om att implementera RemoveItem

Följande villkor kan gälla för din implementering av [system. Management. Automation. Provider. Containercmdletprovider. NewItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem):

- När du definierar Provider-klassen kan en Windows PowerShell container-Provider deklarera ExpandWildcards, filtrera, ta med eller undanta från, från [system. Management. Automation. Provider. ProviderCapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) -uppräkningen. I dessa fall måste implementeringen av metoden [system. Management. Automation. Provider. Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) se till att den sökväg som skickas till metoden uppfyller kraven för de angivna funktionerna. För att göra detta ska metoden komma åt lämplig egenskap, till exempel [system. Management. Automation. Provider. Cmdletprovider. exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) och [system. Management. Automation. Provider. Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) egenskaper.

- Åsidosättningar av den här metoden bör som standard inte ta bort objekt om inte egenskapen [system. Management. Automation. Provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) anges till true. Om den angivna sökvägen indikerar en behållare krävs inte egenskapen [system. Management. Automation. Provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) .

- Din implementering av [system. Management. Automation. Provider. Containercmdletprovider. RemoveItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) ansvarar för att förhindra oändlig rekursion när det finns cirkel länkar och liknande. Ett lämpligt avslutande undantag bör utsättas för att avspegla ett sådant villkor.

- Din implementering av metoden [system. Management. Automation. Provider. Containercmdletprovider. RemoveItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) ska anropa [system. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) och kontrol lera dess retur värde innan du gör några ändringar i data lagret. Efter att anropet till [system. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) returnerar `true`, returnerar system. Management. Automation. Provider. [Containercmdletprovider. RemoveItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) metoden [system. Management. Automation. Provider. Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) -metoden som ytterligare kontroll för potentiellt skadliga system ändringar.

## <a name="attaching-dynamic-parameters-to-the-remove-item-cmdlet"></a>Bifoga dynamiska parametrar till cmdleten Remove-Item

Ibland kräver `Remove-Item` cmdlet ytterligare parametrar som anges dynamiskt vid körning. För att tillhandahålla dessa dynamiska parametrar måste container leverantören implementera metoden [system. Management. Automation. Provider. Containercmdletprovider. Removeitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) för att hantera dessa parametrar. Den här metoden hämtar dynamiska parametrar för objektet på den angivna sökvägen och returnerar ett objekt som har egenskaper och fält med parsande attribut som liknar en cmdlet-klass eller ett [system. Management. Automation. Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) -objekt. Windows PowerShell-körningsmiljön använder det returnerade objektet för att lägga till parametrarna i `Remove-Item`-cmdleten.

Den här behållar leverantören implementerar inte den här metoden. Följande kod är dock standard implementeringen av [system. Management. Automation. Provider. Containercmdletprovider. Removeitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderremoveitemdynamicparameters](Msh_samplestestcmdlets#testproviderremoveitemdynamicparameters)]  -->

## <a name="querying-for-child-items"></a>Fråga efter underordnade objekt

För att kontrol lera om underordnade objekt finns på den angivna sökvägen, måste Windows PowerShell container Provider åsidosätta metoden [system. Management. Automation. Provider. Containercmdletprovider. Haschilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) . Den här metoden returnerar `true` om objektet har underordnade objekt och `false` annars. För en sökväg som är null eller tom anser metoden att alla objekt i data lagret är underordnade och returnerar `true`.

Här är åsidosättningen för metoden [system. Management. Automation. Provider. Containercmdletprovider. Haschilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) . Om det finns fler än två Sök vägs delar som skapats av ChunkPath Helper-metoden returnerar metoden `false`, eftersom bara en databas behållare och en tabell behållare definieras. Mer information om den här hjälp metoden finns i ChunkPath-metoden beskrivs i [skapa en Windows PowerShell-dataprovider](./creating-a-windows-powershell-item-provider.md).

```csharp
protected override bool HasChildItems( string path )
{
    return false;
} // HasChildItems
```

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs" range="1094-1097":::

#### <a name="things-to-remember-about-implementing-haschilditems"></a>Saker att komma ihåg om att implementera HasChildItems

Följande villkor kan gälla för din implementering av [system. Management. Automation. Provider. Containercmdletprovider. Haschilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems):

- Om behållar leverantören visar en rot som innehåller intressanta monterings punkter ska implementeringen av metoden [system. Management. Automation. Provider. Containercmdletprovider. Haschilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) returnera `true` när ett null-värde eller en tom sträng skickas in för sökvägen.

## <a name="copying-items"></a>Objekt kopieras

För att kunna kopiera objekt måste container leverantören implementera metoden [system. Management. Automation. Provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) för att stödja anrop från `Copy-Item`-cmdleten. Den här metoden kopierar ett data objekt från den plats som anges av parametern `path` för cmdleten till den plats som anges av parametern `copyPath`. Om parametern `recurse` anges kopierar metoden alla under behållare. Om parametern inte anges kopierar metoden bara en nivå av objekt.

Den här providern implementerar inte den här metoden. Följande kod är dock standard implementeringen av [system. Management. Automation. Provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidercopyitem](Msh_samplestestcmdlets#testprovidercopyitem)]  -->

#### <a name="things-to-remember-about-implementing-copyitem"></a>Saker att komma ihåg om att implementera CopyItem

Följande villkor kan gälla för din implementering av [system. Management. Automation. Provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem):

- När du definierar Provider-klassen kan en Windows PowerShell container-Provider deklarera ExpandWildcards, filtrera, ta med eller undanta från, från [system. Management. Automation. Provider. ProviderCapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) -uppräkningen. I dessa fall måste implementeringen av metoden [system. Management. Automation. Provider. Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) se till att den sökväg som skickas till metoden uppfyller kraven för de angivna funktionerna. För att göra detta ska metoden komma åt lämplig egenskap, till exempel [system. Management. Automation. Provider. Cmdletprovider. exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) och [system. Management. Automation. Provider. Cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) egenskaper.

- Åsidosättningar av den här metoden bör som standard inte kopiera objekt över befintliga objekt om inte egenskapen [system. Management. Automation. Provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) anges till `true`. Till exempel kommer inte fil Systems leverantören att kopiera c:\temp\abc.txt över en befintlig c:\abc.txt-fil om inte egenskapen [system. Management. Automation. Provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) anges till `true`. Om sökvägen som anges i parametern `copyPath` finns och indikerar en behållare, krävs inte egenskapen [system. Management. Automation. Provider. Cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) . I det här fallet ska [system. Management. Automation. Provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) kopiera objektet som anges av parametern `path` till den behållare som anges av parametern `copyPath` som underordnad.

- Din implementering av [system. Management. Automation. Provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) ansvarar för att förhindra oändlig rekursion när det finns cirkel länkar, och liknande. Ett lämpligt avslutande undantag bör utsättas för att avspegla ett sådant villkor.

- Din implementering av metoden [system. Management. Automation. Provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) ska anropa [system. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) och kontrol lera dess retur värde innan du gör några ändringar i data lagret. Efter anropet till [system. Management. Automation. Provider. Cmdletprovider. ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) returnerar true, metoden system. Management. Automation. Provider [. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) ska anropa metoden [system. Management. Automation. Provider. Cmdletprovider. ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) som en ytterligare kontroll för potentiellt skadliga system ändringar. Mer information om hur du anropar dessa metoder finns i avsnittet [byta namn på objekt](#renaming-items).

## <a name="attaching-dynamic-parameters-to-the-copy-item-cmdlet"></a>Koppla dynamiska parametrar till cmdleten Copy-Item

Ibland kräver `Copy-Item` cmdlet ytterligare parametrar som anges dynamiskt vid körning. För att tillhandahålla dessa dynamiska parametrar måste Windows PowerShell container Provider implementera metoden [system. Management. Automation. Provider. Containercmdletprovider. Copyitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) för att hantera dessa parametrar. Den här metoden hämtar parametrarna för objektet vid den angivna sökvägen och returnerar ett objekt som har egenskaper och fält med parsande attribut som liknar en cmdlet-klass eller ett [system. Management. Automation. Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) -objekt. Windows PowerShell-körningsmiljön använder det returnerade objektet för att lägga till parametrarna i `Copy-Item`-cmdleten.

Den här providern implementerar inte den här metoden. Följande kod är dock standard implementeringen av [system. Management. Automation. Provider. Containercmdletprovider. Copyitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidercopyitemdynamicparameters](Msh_samplestestcmdlets#testprovidercopyitemdynamicparameters)]  -->

## <a name="code-sample"></a>Kod exempel

Fullständig exempel kod finns i [kod exemplet för AccessDbProviderSample04](./accessdbprovidersample04-code-sample.md).

## <a name="building-the-windows-powershell-provider"></a>Skapa Windows PowerShell-providern

Se [hur du registrerar cmdlets, providers och värd program](/previous-versions/ms714644(v=vs.85)).

## <a name="testing-the-windows-powershell-provider"></a>Testa Windows PowerShell-providern

När din Windows PowerShell-provider har registrerats med Windows PowerShell kan du testa den genom att köra cmdlets som stöds på kommando raden. Tänk på att följande exempel på utdata använder en fiktiv Access-databas.

1. Kör cmdleten `Get-ChildItem` för att hämta listan över underordnade objekt från en kund tabell i Access-databasen.

   ```powershell
   Get-ChildItem mydb:customers
   ```

   Följande utdata visas.

   ```output
   PSPath        : AccessDB::customers
   PSDrive       : mydb
   PSProvider    : System.Management.Automation.ProviderInfo
   PSIsContainer : True
   Data          : System.Data.DataRow
   Name          : Customers
   RowCount      : 91
   Columns       :
   ```

2. Kör cmdleten `Get-ChildItem` igen för att hämta data för en tabell.

   ```powershell
   (Get-ChildItem mydb:customers).data
   ```

   Följande utdata visas.

   ```output
   TABLE_CAT   : c:\PS\northwind
   TABLE_SCHEM :
   TABLE_NAME  : Customers
   TABLE_TYPE  : TABLE
   REMARKS     :
   ```

3. Använd nu `Get-Item`-cmdlet: en för att hämta objekten på rad 0 i data tabellen.

   ```powershell
   Get-Item mydb:\customers\0
   ```

   Följande utdata visas.

   ```output
   PSPath        : AccessDB::customers\0
   PSDrive       : mydb
   PSProvider    : System.Management.Automation.ProviderInfo
   PSIsContainer : False
   Data          : System.Data.DataRow
   RowNumber     : 0
   ```

4. Återanvänd `Get-Item` för att hämta data för objekten på rad 0.

   ```powershell
   (Get-Item mydb:\customers\0).data
   ```

   Följande utdata visas.

   ```output
   CustomerID   : 1234
   CompanyName  : Fabrikam
   ContactName  : Eric Gruber
   ContactTitle : President
   Address      : 4567 Main Street
   City         : Buffalo
   Region       : NY
   PostalCode   : 98052
   Country      : USA
   Phone        : (425) 555-0100
   Fax          : (425) 555-0101
   ```

5. Använd nu `New-Item` cmdlet för att lägga till en rad i en befintlig tabell. Parametern `Path` anger den fullständiga sökvägen till raden och måste ange ett rad nummer som är större än det befintliga antalet rader i tabellen. Parametern `Type` anger "rad" för att ange den typ av objekt som ska läggas till.
   Slutligen anger parametern `Value` en kommaavgränsad lista med kolumn värden för raden.

   ```powershell
   New-Item -Path mydb:\Customers\3 -ItemType "row" -Value "3,CustomerFirstName,CustomerLastName,CustomerEmailAddress,CustomerTitle,CustomerCompany,CustomerPhone, CustomerAddress,CustomerCity,CustomerState,CustomerZip,CustomerCountry"
   ```

6. Kontrol lera att den nya objekt åtgärden är korrekt på följande sätt.

   ```none
   PS mydb:\> cd Customers
   PS mydb:\Customers> (Get-Item 3).data
   ```

   Följande utdata visas.

   ```output
   ID        : 3
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
   ```

## <a name="see-also"></a>Se även

[Skapa Windows PowerShell-leverantörer](./how-to-create-a-windows-powershell-provider.md)

[Designa din Windows PowerShell-Provider](./designing-your-windows-powershell-provider.md)

[Implementera ett objekts Windows PowerShell-Provider](./creating-a-windows-powershell-item-provider.md)

[Implementera en Windows PowerShell-Provider för navigering](./creating-a-windows-powershell-navigation-provider.md)

[Registrera cmdlets, providers och värd program](/previous-versions/ms714644(v=vs.85))

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Windows PowerShell Programmer ' s guide](./windows-powershell-programmer-s-guide.md)
