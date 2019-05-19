---
title: Skapa en Windows PowerShell-providern för behållare | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- providers [PowerShell Programmer's Guide], container provider
- container providers [PowerShell Programmer's Guide]
ms.assetid: a7926647-0d18-45b2-967e-b31f92004bc4
caps.latest.revision: 5
ms.openlocfilehash: 9e7da13ff559e802d52df475f2a555baeeeef983
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855183"
---
# <a name="creating-a-windows-powershell-container-provider"></a>Skapa en Windows PowerShell-containerprovider

Det här avsnittet beskriver hur du skapar en Windows PowerShell-providern som fungerar på flera lager datalager. Den översta nivån i arkivet innehåller rot-objekt för den här typen av datalager och varje efterföljande nivå kallas för en nod i underordnade objekt. Genom att tillåta användare att arbeta på dessa underordnade noder, kan en användare interagera hierarkiskt via datalagret.

Leverantörer som fungerar på flera nivåer datalager kallas providers för Windows PowerShell-behållare. Men tänk på att en Windows PowerShell-providern för behållare kan användas endast när det är en behållare (inga kapslade behållare) med objekt i den. Om det finns kapslade behållare, måste du implementera en Windows PowerShell-providern för navigering. Mer information om hur du implementerar Windows PowerShell navigering-providern finns i [skapar en Windows PowerShell-providern för navigering](./creating-a-windows-powershell-navigation-provider.md).

> [!NOTE]
> Du kan ladda ned den C# källfilen (AccessDBSampleProvider04.cs) för den här providern med hjälp av Microsoft Windows Software Development Kit för Windows Vista och .NET Framework 3.0 Runtime-komponenter. Hämta anvisningar finns i [hur du installerar Windows PowerShell och ladda ned Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Hämtade källfilerna är tillgängliga i den  **\<PowerShell-exempel >** directory.
>
> Läs mer om andra Windows PowerShell-providern implementeringar [designa din Windows PowerShell-providern](./designing-your-windows-powershell-provider.md).

Windows PowerShell-container-providern som beskrivs här definierar databasen som den enda behållaren med tabeller och rader för den databas som har definierats som objekt i behållaren.

> [!CAUTION]
> Tänk på att den här designen förutsätter en databas som har ett fält med namn-ID och att fältet är LongInteger.

## <a name="defining-a-windows-powershell-container-provider-class"></a>Definiera en providerklass för Windows PowerShell-behållare

En Windows PowerShell-providern för behållaren måste definiera en .NET-klass som härleds från den [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) basklassen. Här är klassdefinitionen för Windows PowerShell-container-providern som beskrivs i det här avsnittet.

```csharp
   [CmdletProvider("AccessDB", ProviderCapabilities.None)]
   public class AccessDBProvider : ContainerCmdletProvider
```

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L34-L35 "AccessDBProviderSample04.cs")]

Observera att i det här klassdefinitionen, den [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribut innehåller två parametrar. Den första parametern anger ett användarvänligt namn för providern som används av Windows PowerShell. Den andra parametern anger de specifika funktioner i Windows PowerShell som providern visar Windows PowerShell-runtime under bearbetning av kommandot. Det finns inga specifika Windows PowerShell-funktioner som har lagts till för den här providern.

## <a name="defining-base-functionality"></a>Definiera grundfunktionen

Mer information finns i [designa din Windows PowerShell-providern](./designing-your-windows-powershell-provider.md), [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) klassen härleds från flera klasser som angetts annan provider-funktionalitet. En provider för Windows PowerShell-behållare, måste därför definiera alla funktioner som tillhandahålls av dessa klasser.

Om du vill implementera funktioner för att lägga till sessionen-specifika initieringsinformation och för att frisläppa resurser som används av providern, se [skapar en grundläggande Windows PowerShell-providern](./creating-a-basic-windows-powershell-provider.md). De flesta leverantörer (inklusive providern som beskrivs här) kan dock använda standardimplementering av den här funktionen som tillhandahålls av Windows PowerShell.

För att få åtkomst till datalagret för providern måste implementera-metoderna i den [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) basklassen. Läs mer om hur du implementerar dessa metoder, [skapar en Windows PowerShell Drive Provider](./creating-a-windows-powershell-drive-provider.md).

Om du vill manipulera objekten i ett datalager, till exempel komma, inställningen och rensar objekt providern måste implementera de metoder som tillhandahålls av den [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) basklassen. Läs mer om hur du implementerar dessa metoder, [skapa en Windows PowerShell-Provider för objektet](./creating-a-windows-powershell-item-provider.md).

## <a name="retrieving-child-items"></a>Hämtning av underordnade objekt

Om du vill hämta ett underordnat objekt av Windows PowerShell-providern för behållaren måste åsidosätta de [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) metod för att stödja anrop från den `Get-ChildItem` cmdlet. Den här metoden hämtar underordnade objekt från datalagret och skriver dem till pipelinen som objekt. Om den `recurse` parametern för cmdlet har angetts, metoden hämtar alla underordnade oavsett vilken nivå som de är på. Om den `recurse` parametern inte anges, metoden hämtar bara en enda nivå med underordnade.

Här är implementeringen av den [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) metod för den här providern. Observera att den här metoden hämtar de underordnade objekten i alla databastabeller när sökvägen anger Access-databas och hämtar de underordnade objekten från raderna i tabellen om sökvägen indikerar en datatabell.

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

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L311-L362 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-getchilditems"></a>Kom ihåg följande om hur du implementerar GetChildItems

Följande villkor kan tillkomma för din implementering av [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems):

- När du definierar providerklassen, en Windows PowerShell-providern för behållare kan deklarera provider-funktionerna i ExpandWildcards, Filter, inkludera eller exkludera, från den [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) uppräkning. I dessa fall är implementeringen av den [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) metod måste se till att sökvägen skickas till metoden uppfyller kraven för den angivna funktioner. Gör detta genom metoden ska komma åt egenskapen lämplig, till exempel, [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) och [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) egenskaper.

- Implementeringen av den här metoden bör beakta någon form av åtkomst till objekt som kan göra objektet som är synliga för användaren. Till exempel om en användare har skrivbehörighet till en fil via filsystemet provider (som tillhandahålls av Windows PowerShell), men inte läsbehörighet kan filen fortfarande finns och [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) returnerar `true`. Implementeringen kan kräva kontroll av en överordnad artikel för att se om underordnat kan ingå.

- När du skriver flera objekt i [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) metod kan ta lite tid. Du kan utforma din provider för att skriva artiklar som använder den [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) metoden en i taget. Med den här tekniken kommer att presentera objekten till användare i en ström.

- Implementeringen av [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) ansvarar för att förhindra oändlig rekursion när Cirkulära länkar och liknande. Ett lämpligt avslutande undantag måste undantagsfel för att återspegla dessa villkor.

## <a name="attaching-dynamic-parameters-to-the-get-childitem-cmdlet"></a>Bifoga dynamiska parametrar till cmdleten Get-ChildItem

Ibland den `Get-ChildItem` cmdlet: en som anropar [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) kräver ytterligare parametrar som anges dynamiskt vid körning. För att ge dessa dynamiska parametrar, Windows PowerShell container-providern måste implementera de [System.Management.Automation.Provider.Containercmdletprovider.Getchilditemsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) metod. Den här metoden hämtar dynamiska parametrar för objektet på den angivna sökvägen och returnerar ett objekt med egenskaper och fält med parsning attribut som liknar en cmdlet-klass eller en [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objekt. Windows PowerShell-runtime använder det returnerade objektet för att lägga till parametrar till den `Get-ChildItem` cmdlet.

Den här behållaren Windows PowerShell-providern implementerar inte den här metoden. Följande kod är dock standardimplementering av den här metoden.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchilditemsdynamicparameters](Msh_samplestestcmdlets#testprovidergetchilditemsdynamicparameters)]  -->

## <a name="retrieving-child-item-names"></a>Hämtning av underordnade objektnamn

Om du vill hämta namnen på underordnade objekt av Windows PowerShell-providern för behållaren måste åsidosätta de [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) metod för att stödja anrop från `Get-ChildItem`cmdlet när dess `Name` parameter har angetts. Den här metoden hämtar namnen på de underordnade objekten för de angivna sökvägen eller underordnad objektnamn för alla behållare om den `returnAllContainers` parametern för cmdlet har angetts. Ett underordnade namn är den lägsta delen av en sökväg. Namnet på underordnade för sökvägen c:\windows\system32\abc.dll är till exempel ”abc.dll”. Namnet på underordnade för directory c:\windows\system32 är ”system32”.

Här är implementeringen av den [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) metod för den här providern. Observera att metoden hämtar tabellnamn om den angivna sökvägen visar Access-databas (enhet) och radnummer om sökvägen visar en tabell.

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

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L369-L411 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-getchildnames"></a>Kom ihåg följande om hur du implementerar GetChildNames

Följande villkor kan tillkomma för din implementering av [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems):

- När du definierar providerklassen, en Windows PowerShell-providern för behållare kan deklarera provider-funktionerna i ExpandWildcards, Filter, inkludera eller exkludera, från den [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) uppräkning. I dessa fall är implementeringen av den [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) metod måste se till att sökvägen skickas till metoden uppfyller kraven för den angivna funktioner. Gör detta genom metoden ska komma åt egenskapen lämplig, till exempel, [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) och [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) egenskaper.

  > [!NOTE]
  > Ett undantag till den här regeln inträffar när den `returnAllContainers` parametern för cmdlet har angetts. I det här fallet metoden bör hämta alla underordnade namn för en behållare, även om det inte matchar värdena för den [System.Management.Automation.Provider.Cmdletprovider.Filter*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Filter), [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include), eller [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) egenskaper.

- Som standard åsidosättningar av den här metoden ska inte att hämta namnen på objekten som vanligtvis är dolda från användaren, såvida inte den [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) egenskapen har angetts. Om den angivna sökvägen indikerar en behållare i [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) egenskapen är inte obligatoriskt.

- Implementeringen av [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) ansvarar för att förhindra oändlig rekursion när Cirkulära länkar och liknande. Ett lämpligt avslutande undantag måste undantagsfel för att återspegla dessa villkor.

## <a name="attaching-dynamic-parameters-to-the-get-childitem-cmdlet-name"></a>Bifoga dynamiska parametrar till cmdleten Get-ChildItem (namn)

Ibland den `Get-ChildItem` cmdlet (med den `Name` parametern) kräver ytterligare parametrar som anges dynamiskt vid körning. För att ge dessa dynamiska parametrar, Windows PowerShell container-providern måste implementera de [System.Management.Automation.Provider.Containercmdletprovider.Getchildnamesdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) metod. Den här metoden hämtar de dynamiska parametrarna för objektet på den angivna sökvägen och returnerar ett objekt med egenskaper och fält med parsning attribut som liknar en cmdlet-klass eller en [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objekt. Windows PowerShell-runtime använder det returnerade objektet för att lägga till parametrar till den `Get-ChildItem` cmdlet.

Den här providern implementerar inte den här metoden. Följande kod är dock standardimplementering av den här metoden.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchildnamesdynamicparameters](Msh_samplestestcmdlets#testprovidergetchildnamesdynamicparameters)]  -->

## <a name="renaming-items"></a>Byta namn på objekt

Om du vill byta namn på ett objekt, en Windows PowerShell-providern för behållaren måste åsidosätta de [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) metod för att stödja anrop från den `Rename-Item` cmdlet. Den här metoden ändrar namnet på objektet på den angivna sökvägen till det nya namnet som angetts. Det nya namnet måste alltid vara i förhållande till den överordnade artikeln (behållare).

Den här providern inte åsidosätter den [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) metod. Följande är dock standardimplementering.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderrenameitem](Msh_samplestestcmdlets#testproviderrenameitem)]  -->

#### <a name="things-to-remember-about-implementing-renameitem"></a>Kom ihåg följande om hur du implementerar RenameItem

Följande villkor kan tillkomma för din implementering av [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem):

- När du definierar providerklassen, en Windows PowerShell-providern för behållare kan deklarera provider-funktionerna i ExpandWildcards, Filter, inkludera eller exkludera, från den [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) uppräkning. I dessa fall är implementeringen av den [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) metod måste se till att sökvägen skickas till metoden uppfyller kraven för den angivna funktioner. Gör detta genom metoden ska komma åt egenskapen lämplig, till exempel, [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) och [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) egenskaper.

- Den [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) metoden är avsedd för ändring av namnet på ett objekt bara och inte för flyttåtgärder. Implementeringen av metoden ska skriva ett fel om de `newName` parametern innehåller avgränsarna eller på annat sätt kan orsaka objektet du vill ändra den överordnade platsen.

- Som standard åsidosättningar av den här metoden bör inte byta namn på objekt, såvida inte den [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) egenskapen har angetts. Om den angivna sökvägen indikerar en behållare i [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) egenskapen är inte obligatoriskt.

- Implementeringen av den [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) metoden ska anropa [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) och kontrollera dess returvärdet innan du gör några ändringar i datalagret. Den här metoden används för att bekräfta körning av en åtgärd när en ändring görs i systemtillståndet, till exempel byta namn på filer. [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) skickar namnet på resursen som ska ändras till användaren, med hänsyn till alla inställningar för kommandoraden eller variabler i Windows PowerShell-körningsmiljön bestämma vad som ska visas.

  Efter anropet till [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) returnerar `true`, [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) metoden ska anropa den [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) metod. Den här metoden skickar ett meddelande ett bekräftelsemeddelande visas för användaren så att ytterligare feedback att säga om åtgärden bör behållas. En provider ska anropa [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) som ytterligare en kontroll efter ändringar av potentiellt skadliga system.

## <a name="attaching-dynamic-parameters-to-the-rename-item-cmdlet"></a>Bifoga dynamiska parametrar till Cmdlet Rename-objekt

Ibland den `Rename-Item` cmdlet kräver ytterligare parametrar som anges dynamiskt vid körning. För att ge dessa dynamiska parametrar, Windows PowerShell behållare leverantören måste implementera de [System.Management.Automation.Provider.Containercmdletprovider.Renameitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) metod. Den här metoden hämtar parametrarna för objektet på den angivna sökvägen och returnerar ett objekt med egenskaper och fält med parsning attribut som liknar en cmdlet-klass eller en [System.Management.Automation.Runtimedefinedparameterdictionary ](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objekt. Windows PowerShell-runtime använder det returnerade objektet för att lägga till parametrar till den `Rename-Item` cmdlet.

Den här behållaren providern implementerar inte den här metoden. Följande kod är dock standardimplementering av den här metoden.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderrenameitemdynamicparameters](Msh_samplestestcmdlets#testproviderrenameitemdynamicparameters)]  -->

## <a name="creating-new-items"></a>Skapa nya objekt

Om du vill skapa nya objekt, en behållare leverantören måste implementera de [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) metod för att stödja anrop från den `New-Item` cmdlet. Den här metoden skapar ett dataobjekt som finns på den angivna sökvägen. Den `type` parametern för cmdlet: en innehåller typen provider-definierade för det nya objektet. Till exempel filsystem-providern använder en `type` parametern med värdet ”fil” eller ”directory”. Den `newItemValue` parametern för cmdlet: en anger ett värde för provider-specifik för det nya objektet.

Här är implementeringen av den [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) metod för den här providern.

```csharp
protected override void NewItem( string path, string type,
                                 object newItemValue )
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

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L939-L955 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-newitem"></a>Kom ihåg följande om hur du implementerar NewItem

Följande villkor kan tillkomma för din implementering av [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem):

- Den [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) metoden bör utföra en skiftlägeskänslig jämförelse av den sträng som har skickats i de `type` parametern. Det bör också tillåta för minst tvetydig matchningar. För typer ”fil” och ”directory”, till exempel krävs bara den första bokstaven att undvika. Om den `type` parametern anger en typ som leverantören inte kan skapa den [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) metoden ska skriva en ArgumentException med ett meddelande som anger vilka kan providern skapa.

- För den `newItemValue` parametern, implementering av den [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) metoden rekommenderas att acceptera strängar minst. Det bör också godkänna typ av objekt som hämtas av den [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) metod för samma sökväg. Den [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) metod kan använda den [System.Management.Automation.Languageprimitives.Convertto*](/dotnet/api/System.Management.Automation.LanguagePrimitives.ConvertTo) metod för att konvertera programdistributionstyperna som ska den önskade typen.

- Implementeringen av den [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) metoden ska anropa [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) och kontrollera dess returvärdet innan du gör några ändringar i datalagret. Efter anropet till [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) returnerar true, den [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) metoden ska anropa den [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) metod som ytterligare en kontroll efter ändringar av potentiellt skadliga system.

## <a name="attaching-dynamic-parameters-to-the-new-item-cmdlet"></a>Koppla dynamiska parametrar till nytt objekt-Cmdlet

Ibland den `New-Item` cmdlet kräver ytterligare parametrar som anges dynamiskt vid körning. För att ge dessa dynamiska parametrar, container-leverantören måste implementera de [System.Management.Automation.Provider.Containercmdletprovider.Newitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) metod. Den här metoden hämtar parametrarna för objektet på den angivna sökvägen och returnerar ett objekt med egenskaper och fält med parsning attribut som liknar en cmdlet-klass eller en [System.Management.Automation.Runtimedefinedparameterdictionary ](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objekt. Windows PowerShell-runtime använder det returnerade objektet för att lägga till parametrar till den `New-Item` cmdlet.

Den här providern implementerar inte den här metoden. Följande kod är dock standardimplementering av den här metoden.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernewitemdynamicparameters](Msh_samplestestcmdlets#testprovidernewitemdynamicparameters)]  -->

## <a name="removing-items"></a>Tar bort objekt

Om du vill ta bort objekt, Windows PowerShell-providern måste åsidosätta de [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) metod för att stödja anrop från den `Remove-Item` cmdlet. Den här metoden tar bort ett objekt från datalagret i den angivna sökvägen. Om den `recurse` -parametern för den `Remove-Item` cmdlet har angetts till `true`, metoden tar bort alla underordnade objekt oavsett. Om parametern är inställd `false`, metoden tar bort ett enskilt objekt i den angivna sökvägen.

Den här providern stöder inte objekt tas bort. Följande kod är dock standardimplementering av [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderremoveitem](Msh_samplestestcmdlets#testproviderremoveitem)]  -->

#### <a name="things-to-remember-about-implementing-removeitem"></a>Kom ihåg följande om hur du implementerar RemoveItem

Följande villkor kan tillkomma för din implementering av [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem):

- När du definierar providerklassen, en Windows PowerShell-providern för behållare kan deklarera provider-funktionerna i ExpandWildcards, Filter, inkludera eller exkludera, från den [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) uppräkning. I dessa fall är implementeringen av den [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) metod måste se till att sökvägen skickas till metoden uppfyller kraven för den angivna funktioner. Gör detta genom metoden ska komma åt egenskapen lämplig, till exempel, [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) och [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) egenskaper.

- Som standard åsidosättningar av den här metoden bör inte ta bort objekt om de [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) är inställd till true. Om den angivna sökvägen indikerar en behållare i [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) egenskapen är inte obligatoriskt.

- Implementeringen av [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) ansvarar för att förhindra oändlig rekursion när Cirkulära länkar och liknande. Ett lämpligt avslutande undantag måste undantagsfel för att återspegla dessa villkor.

- Implementeringen av den [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) metoden ska anropa [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) och kontrollera dess returvärdet innan du gör några ändringar i datalagret. Efter anropet till [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) returnerar `true`, [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) metoden ska anropa den [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) metod som ytterligare en kontroll efter ändringar av potentiellt skadliga system.

## <a name="attaching-dynamic-parameters-to-the-remove-item-cmdlet"></a>Bifoga dynamiska parametrar till cmdleten Remove-objekt

Ibland den `Remove-Item` cmdlet kräver ytterligare parametrar som anges dynamiskt vid körning. För att ge dessa dynamiska parametrar, container-leverantören måste implementera de [System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) metod för att hantera dessa parametrar. Den här metoden hämtar de dynamiska parametrarna för objektet på den angivna sökvägen och returnerar ett objekt med egenskaper och fält med parsning attribut som liknar en cmdlet-klass eller en [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objekt. Windows PowerShell-runtime använder det returnerade objektet för att lägga till parametrar till den `Remove-Item` cmdlet.

Den här behållaren providern implementerar inte den här metoden. Följande kod är dock standardimplementering av [System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderremoveitemdynamicparameters](Msh_samplestestcmdlets#testproviderremoveitemdynamicparameters)]  -->

## <a name="querying-for-child-items"></a>Fråga efter underordnade objekt

Om du vill kontrollera om du vill se om det finns underordnade objekt i den angivna sökvägen av Windows PowerShell-providern för behållaren måste åsidosätta de [System.Management.Automation.Provider.Containercmdletprovider.Haschilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) metod. Den här metoden returnerar `true` om objektet har barn, och `false` annars. För en null eller tom sökväg, metoden tar hänsyn till alla objekt i datalager vara underordnade och returnerar `true`.

Här är åsidosättning för den [System.Management.Automation.Provider.Containercmdletprovider.Haschilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) metod. Om det finns fler än två delar av filsökväg som skapats av hjälpmetoden ChunkPath, returnerar-metoden `false`, eftersom bara en databasbehållare och en tabellbehållare har definierats. Mer information om den här helper-metoden finns i metoden ChunkPath beskrivs i [skapar en Windows PowerShell-providern för objektet](./creating-a-windows-powershell-item-provider.md).

```csharp
protected override bool HasChildItems( string path )
{
    return false;
} // HasChildItems
```

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L1094-L1097 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-haschilditems"></a>Kom ihåg följande om hur du implementerar HasChildItems

Följande villkor kan tillkomma för din implementering av [System.Management.Automation.Provider.Containercmdletprovider.Haschilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems):

- Om container providern Exponerar en rotcertifikatutfärdare som innehåller intressanta monteringspunkter, implementering av den [System.Management.Automation.Provider.Containercmdletprovider.Haschilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) ska metoden returnera `true`när ett null-värde eller en tom sträng skickas för sökvägen.

## <a name="copying-items"></a>Kopiera objekt

Om du vill kopiera objekt container-leverantören måste implementera de [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) metod för att stödja anrop från den `Copy-Item` cmdlet. Den här metoden kopierar ett dataobjekt från den plats som anges av den `path` parametern för cmdlet: en till den plats som anges av den `copyPath` parametern. Om den `recurse` parameter har angetts, metoden kopierar alla underordnade behållare. Om parametern inte anges, kopierar metoden endast en enda nivå av objekt.

Den här providern implementerar inte den här metoden. Följande kod är dock standardimplementering av [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidercopyitem](Msh_samplestestcmdlets#testprovidercopyitem)]  -->

#### <a name="things-to-remember-about-implementing-copyitem"></a>Kom ihåg följande om hur du implementerar CopyItem

Följande villkor kan tillkomma för din implementering av [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem):

- När du definierar providerklassen, en Windows PowerShell-providern för behållare kan deklarera provider-funktionerna i ExpandWildcards, Filter, inkludera eller exkludera, från den [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) uppräkning. I dessa fall är implementeringen av den [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) metod måste se till att sökvägen skickas till metoden uppfyller kraven för den angivna funktioner. Gör detta genom metoden ska komma åt egenskapen lämplig, till exempel, [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) och [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) egenskaper.

- Som standard åsidosättningar av den här metoden bör inte kopiera objekt över befintliga objekt, såvida inte den [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) är inställd på `true`. Till exempel filsystem providern kopierar inte c:\temp\abc.txt över en befintlig c:\abc.txt-fil, såvida inte den [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) är inställd på `true`. Om sökvägen som angetts i den `copyPath` parametern finns och anger en behållare i [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) egenskapen är inte obligatoriskt. I det här fallet [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) bör kopiera objektet som anges av den `path` parametern till behållaren som anges av den `copyPath` parametern som en underordnad.

- Implementeringen av [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) ansvarar för att förhindra oändlig rekursion när Cirkulära länkar och liknande. Ett lämpligt avslutande undantag måste undantagsfel för att återspegla dessa villkor.

- Implementeringen av den [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) metoden ska anropa [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) och kontrollera dess returvärdet innan du gör några ändringar i datalagret. Efter anropet till [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) returnerar true, den [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) metoden ska anropa den [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) metod som ytterligare en kontroll efter ändringar av potentiellt skadliga system. Läs mer om att anropa metoderna [Byt namn på objekt](#renaming-items).

## <a name="attaching-dynamic-parameters-to-the-copy-item-cmdlet"></a>Bifoga dynamiska parametrar till Cmdlet Copy-Item

Ibland den `Copy-Item` cmdlet kräver ytterligare parametrar som anges dynamiskt vid körning. För att ge dessa dynamiska parametrar, Windows PowerShell container-providern måste implementera de [System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) metod för att hantera dessa parametrar. Den här metoden hämtar parametrarna för objektet på den angivna sökvägen och returnerar ett objekt med egenskaper och fält med parsning attribut som liknar en cmdlet-klass eller en [System.Management.Automation.Runtimedefinedparameterdictionary ](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objekt. Windows PowerShell-runtime använder det returnerade objektet för att lägga till parametrar till den `Copy-Item` cmdlet.

Den här providern implementerar inte den här metoden. Följande kod är dock standardimplementering av [System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidercopyitemdynamicparameters](Msh_samplestestcmdlets#testprovidercopyitemdynamicparameters)]  -->

## <a name="code-sample"></a>Kodexempel

Komplett exempel finns i [AccessDbProviderSample04 kodexempel](./accessdbprovidersample04-code-sample.md).

## <a name="building-the-windows-powershell-provider"></a>Att skapa Windows PowerShell-providern

Se [hur du registrerar Cmdlets, Providers och vara värd för program](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-windows-powershell-provider"></a>Testa Windows PowerShell-providern

När din Windows PowerShell-provider har registrerats med Windows PowerShell kan testa du den genom att köra cmdletarna stöds på kommandoraden. Tänk på att följande Exempelutdata använder en fiktiva Access-databas.

1. Kör den `Get-ChildItem` cmdlet för att hämta listan över underordnade objekt från en kundtabell i Access-databasen.

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

2. Kör den `Get-ChildItem` cmdleten igen för att hämta data i en tabell.

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

3. Nu använda den `Get-Item` cmdlet för att hämta elementen på rad 0 i tabellen.

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

4. Återanvända `Get-Item` att hämta data för objekten i rad 0.

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

5. Nu använda den `New-Item` cmdlet för att lägga till en rad i en befintlig tabell. Den `Path` parametern anger den fullständiga sökvägen till raden och måste ange ett radnummer som är större än det befintliga antalet rader i tabellen. Den `Type` parametern anger ”rad” för att ange den typ av objekt som ska läggas. Slutligen den `Value` parametern anger en kommaavgränsad lista med kolumnvärdena för raden.

   ```powershell
   New-Item -Path mydb:\Customers\3 -ItemType "row" -Value "3,CustomerFirstName,CustomerLastName,CustomerEmailAddress,CustomerTitle,CustomerCompany,CustomerPhone, CustomerAddress,CustomerCity,CustomerState,CustomerZip,CustomerCountry"
   ```

6. Kontrollera för nya objekt igen på följande sätt.

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

[Skapa Windows PowerShell-Providers](./how-to-create-a-windows-powershell-provider.md)

[Designa din Windows PowerShell-providern](./designing-your-windows-powershell-provider.md)

[Implementera en objekt Windows PowerShell-Provider](./creating-a-windows-powershell-item-provider.md)

[Implementera en navigering Windows PowerShell-providern](./creating-a-windows-powershell-navigation-provider.md)

[Hur du registrerar Cmdlets, Providers och vara värd för program](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Programmeringsguide för Windows PowerShell](./windows-powershell-programmer-s-guide.md)