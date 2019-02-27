---
title: Skapa en Windows PowerShell-providern för navigering | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- navigation providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], navigation provider
ms.assetid: 8bd3224d-ca6f-4640-9464-cb4d9f4e13b1
caps.latest.revision: 5
ms.openlocfilehash: 066aa188d5d7dfde5af424a3bb8f15ff51c1e936
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847483"
---
# <a name="creating-a-windows-powershell-navigation-provider"></a>Skapa en Windows PowerShell-navigeringsprovider

Det här avsnittet beskriver hur du skapar en provider för Windows PowerShell navigering som kan navigera till datalagret. Den här typen av providern har stöd för rekursiv kommandon, kapslade behållare och relativa sökvägar.

> [!NOTE]
> Du kan ladda ned den C# källfilen (AccessDBSampleProvider05.cs) för den här providern med hjälp av Microsoft Windows Software Development Kit för Windows Vista och .NET Framework 3.0 Runtime-komponenter. Hämta anvisningar finns i [hur du installerar Windows PowerShell och ladda ned Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).
> Du kan ladda ned den C# källfilen (AccessDBSampleProvider05.cs) för den här providern med hjälp av Microsoft Windows Software Development Kit för Windows Vista och .NET Framework 3.0 Runtime-komponenter. Hämta anvisningar finns i [hur du installerar Windows PowerShell och ladda ned Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Hämtade källfilerna är tillgängliga i den  **\<PowerShell-exempel >** directory.
>
> Läs mer om andra Windows PowerShell-providern implementeringar [designa din Windows PowerShell-providern](./designing-your-windows-powershell-provider.md).

Providern som beskrivs här kan Användarhanteraren en Access-databas som en enhet så att användaren kan navigera till datatabeller i databasen. När du skapar en egen provider för navigering, kan du implementera metoder som kan göra enhet kvalificerade sökvägar som krävs för navigering, normalisera relativa sökvägar, flytta objekt i datalagret, samt metoder som hämta underordnade namnen, hämta den överordnade sökvägen för ett objekt och testa är en behållare för att identifiera om ett objekt.

> [!CAUTION]
> Tänk på att den här designen förutsätter en databas som har ett fält med namn-ID och att fältet är LongInteger.

I följande lista innehåller avsnitt i det här avsnittet. Om du är bekant med att skriva en Windows PowerShell-providern för navigering, kan du läsa informationen i den ordning som det visas. Men om du är bekant med att skriva en Windows PowerShell-providern för navigering, gå direkt till den information du behöver.

- [Definiera en PS navigering providerklass](#Define-the-Windows-PowerShell-provider)

- [Definiera grundfunktionen](#Defining-Base-Functionality)

- [Skapa en PS-sökväg](#Creating-a-Windows-PowerShell-Path)

- [Hämtning av den överordnade sökvägen](#Retrieving-the-Parent-Path)

- [Hämtar namnet på underordnade sökväg](#Retrieve-the-Child-Path-Name)

- [Avgör om ett objekt är en behållare](#Determining-if-an-Item-is-a-Container)

- [Flyttar ett objekt](#Moving-an-Item)

- [Koppla dynamiska parametrar till den `Move-Item` Cmdlet](#Attaching-Dynamic-Parameters-to-the-Move-Item-Cmdlet)

- [Normaliserar en relativ sökväg](#Normalizing-a-Relative-Path)

- [Kodexempel](#Code-Sample)

- [Definiera objekttyper och formatering](#Defining-Object-Types-and-Formatting)

- [Att skapa Windows PowerShell-providern](#Building-the-Windows-PowerShell-provider)

- [Testa Windows PowerShell-providern](#Testing-the-Windows-PowerShell-provider)

## <a name="define-the-windows-powershell-provider"></a>Definiera Windows PowerShell-providern

En Windows PowerShell-providern för navigering måste skapa en .NET-klass som härleds från den [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) basklassen. Här är klassdefinitionen för navigering-providern som beskrivs i det här avsnittet.

[!code-csharp[AccessDBProviderSample05.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample05/AccessDBProviderSample05.cs#L31-L32 "AccessDBProviderSample05.cs")]

Observera att i den här providern den [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribut innehåller två parametrar. Den första parametern anger ett användarvänligt namn för providern som används av Windows PowerShell. Den andra parametern anger de specifika funktioner i Windows PowerShell som providern visar Windows PowerShell-runtime under bearbetning av kommandot. Det finns inga specifika Windows PowerShell-funktioner som har lagts till för den här providern.

## <a name="defining-base-functionality"></a>Definiera grundfunktionen

Mer information finns i [Design Your PS-Provider](./designing-your-windows-powershell-provider.md), [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) basklass härleds från flera klasser som angetts annan provider CRL-funktionalitet. En provider för Windows PowerShell navigering, därför måste definiera alla funktioner som tillhandahålls av dessa klasser.

Om du vill implementera funktioner för att lägga till sessionen-specifika initieringsinformation och för att frisläppa resurser som används av providern, se [skapar en grundläggande PS-Provider](./creating-a-basic-windows-powershell-provider.md). De flesta leverantörer (inklusive providern som beskrivs här) kan dock använda standardimplementering av den här funktionen tillhandahålls av Windows PowerShell.

För att få åtkomst till datalagret via en Windows PowerShell-enhet, måste du implementera-metoderna i den [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) basklassen. Läs mer om hur du implementerar dessa metoder, [skapar en Windows PowerShell Drive Provider](./creating-a-windows-powershell-drive-provider.md).

Om du vill manipulera objekten i ett datalager, till exempel komma, inställningen och rensar objekt providern måste implementera de metoder som tillhandahålls av den [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) basklassen. Läs mer om hur du implementerar dessa metoder, [skapa en Windows PowerShell-Provider för objektet](./creating-a-windows-powershell-item-provider.md).

För att komma till de underordnade objekten eller namnen i datalagret, samt metoder som kan skapa, kopiera, byta namn på och ta bort objekt, måste du implementera de metoder som tillhandahålls av den [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)basklassen. Läs mer om hur du implementerar dessa metoder, [skapar en Windows PowerShell-providern för behållaren](./creating-a-windows-powershell-container-provider.md).

## <a name="creating-a-windows-powershell-path"></a>Skapa en Windows PowerShell-sökväg

Windows PowerShell-providern för navigering använda en provider-internt Windows PowerShell-sökväg för att navigera objekten i datalagret. Skapa en provider-internt sökväg providern måste implementera de [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) till stöder anropar från kombinera-Path-cmdlet. Den här metoden kombinerar en över- och underordnade sökväg till en provider-internt sökväg, med hjälp av en provider-specifik sökvägsavdelare mellan överordnade och underordnade sökvägar.

Standardimplementering tar sökvägar med ”/” eller ”\\” som avgränsare för sökvägen normaliserar avgränsare för sökvägen till ”\\” kombinerar sögvägar överordnade och underordnade med avgränsare mellan dem och returnerar en sträng som innehåller den kombinerade sökvägar.

Den här providern för navigering implementerar inte den här metoden. Följande kod är dock standardimplementering av den [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) metod.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermakepath](Msh_samplestestcmdlets#testprovidermakepath)]  -->

#### <a name="things-to-remember-about-implementing-makepath"></a>Kom ihåg följande om hur du implementerar MakePath

Följande villkor kan tillkomma för din implementering av [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath):

- Implementeringen av den [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) metoden bör inte verifiera sökvägen som en juridiska fullständiga sökväg i providernamnområde. Tänk på att varje parameter kan bara representera en del av en sökväg och de kombinerade delarna kan inte generera en fullständig sökväg. Till exempel den [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) metod för filsystem-providern få ”windows\system32” i den `parent` parametern och ”abc.dll” i `child` parametern. Metoden kopplar ihop dessa värden med den ”\\” avgränsare och returnerar ”windows\system32\abc.dll” som inte är en fullständigt kvalificerad sökväg i filsystemet.

  > [!IMPORTANT]
  > Sögvägar som angetts i anropet till [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) kan innehålla tecken tillåts inte i providernamnområde. De här tecknen används mest sannolikt för jokertecken expansion och implementeringen av den här metoden bör inte ta bort dem.

## <a name="retrieving-the-parent-path"></a>Hämtning av den överordnade sökvägen

Windows PowerShell navigering providers implementerar den [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) metod för att hämta den överordnade delen av den angivna fullständigt eller partiellt provider-specifik sökväg. Metoden tar bort den underordnade delen av sökvägen och returnerar överordnat sökvägen del. Den `root` parametern anger den fullständiga sökvägen till roten för en enhet. Den här parametern kan vara null eller tomt om en monterad enhet inte används för åtgärd för hämtning. Om en rotcertifikatutfärdare anges returnera metoden en sökväg till en behållare i samma träd som roten.

Exemplet navigering providern åsidosätter inte den här metoden, men använder standardimplementering. Den accepterar sökvägar som använder både ”/” och ”\\” som avgränsare för sökvägen. Den första normaliserar sökvägen till endast ha ”\\” skiljetecken, delar sedan upp den överordnade sökvägen ut på sist ”\\” och returnerar den överordnade sökvägen.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetparentpath](Msh_samplestestcmdlets#testprovidergetparentpath)]  -->

#### <a name="to-remember-about-implementing-getparentpath"></a>Du bör tänka på att implementera GetParentPath

Implementeringen av den [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) metoden bör dela upp sökvägen lexically på sökvägsavdelare för leverantörens namnområde. Till exempel filsystem-providern använder den här metoden för att söka efter senaste ”\\” och returnerar allt till vänster om avgränsaren.

## <a name="retrieve-the-child-path-name"></a>Hämta namnet på underordnade sökväg

Din navigering providern implementerar den [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) metod för att hämta namnet (lövelement) på underordnat objektets finns på den angivna fullständiga eller ofullständig provider-specifik sökväg.

Exemplet navigering providern åsidosätts inte den här metoden. Standardimplementering visas nedan. Den accepterar sökvägar som använder både ”/” och ”\\” som avgränsare för sökvägen. Den första normaliserar sökvägen till endast ha ”\\” skiljetecken, delar sedan upp den överordnade sökvägen ut på sist ”\\” och returnerar namnet på underordnat del av filsökväg.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchildname](Msh_samplestestcmdlets#testprovidergetchildname)]  -->

#### <a name="things-to-remember-about-implementing-getchildname"></a>Kom ihåg följande om hur du implementerar GetChildName

Implementeringen av den [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) metoden bör dela upp sökvägen lexically på avgränsare för sökvägen. Om den angivna sökvägen innehåller ingen avgränsarna, ska metoden returnera den sökväg som ska ändras.

> [!IMPORTANT]
> Den sökväg som angavs i anropet till den här metoden kan innehålla tecken som är ogiltiga i providernamnområde. Följande tecken är mest sannolika används för jokertecken expansion eller matchning med reguljära uttryck och implementeringen av den här metoden bör inte ta bort dem.

## <a name="determining-if-an-item-is-a-container"></a>Avgör om ett objekt är en behållare

Navigering providern kan implementera den [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) metod för att avgöra om den angivna sökvägen indikerar en behållare. Den returnerar true om sökvägen representerar en behållare och false i annat. Användaren behöver den här metoden för att kunna använda den `Test-Path` cmdlet: en för den angivna sökvägen.

Följande kod visar den [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) implementering i vårt exempel navigering providern. Metoden kontrollerar att den angivna sökvägen är korrekt och om tabellen finns och returnerar true om sökvägen anger en behållare.

[!code-csharp[AccessDBProviderSample05.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample05/AccessDBProviderSample05.cs#L847-L872 "AccessDBProviderSample05.cs")]

#### <a name="things-to-remember-about-implementing-isitemcontainer"></a>Kom ihåg följande om hur du implementerar IsItemContainer

Navigering leverantören .NET-klass kan deklarera provider-funktionerna i ExpandWildcards, Filter, inkludera eller exkludera, från den [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) uppräkning. I det här fallet implementeringen av [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) måste se till att sökvägen skickas uppfyller kraven. Gör detta genom metoden ska komma åt egenskapen lämplig, till exempel, [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) egenskapen.

## <a name="moving-an-item"></a>Flyttar ett objekt

Stöd i `Move-Item` cmdlet, navigering leverantören implementerar den [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) metod. Den här metoden flyttar objektet som specificeras av den `path` parametern till behållaren på den sökväg som anges i den `destination` parametern.

Exemplet navigering providern inte åsidosätter den [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) metod. Följande är standardimplementering.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermoveitem](Msh_samplestestcmdlets#testprovidermoveitem)]  -->

#### <a name="things-to-remember-about-implementing-moveitem"></a>Kom ihåg följande om hur du implementerar MoveItem

Navigering leverantören .NET-klass kan deklarera provider-funktionerna i ExpandWildcards, Filter, inkludera eller exkludera, från den [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) uppräkning. I det här fallet implementeringen av [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) måste se till att sökvägen skickas uppfyller kraven. Gör detta genom metoden ska komma åt egenskapen lämplig, till exempel, **CmdletProvider.Exclude** egenskapen.

Som standard åsidosättningar av den här metoden bör inte flytta objekt över befintliga objekt om de [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) är inställd på `true`. Till exempel filsystem providern kopierar inte c:\temp\abc.txt över en befintlig c:\bar.txt-fil, såvida inte den [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) är inställd på `true`. Om sökvägen som angetts i den `destination` parametern finns och är en behållare i [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) egenskapen är inte obligatoriskt. I det här fallet [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) ska flytta det objektet som anges av den `path` parametern till behållaren som anges av den `destination` parametern som en underordnad.

Implementeringen av den [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) metoden ska anropa [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) och kontrollera dess returvärdet innan du gör några ändringar i datalagret. Den här metoden används för att bekräfta körning av en åtgärd när en ändring görs i systemtillståndet, till exempel ta bort filer. [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) skickar namnet på resursen som ska ändras till användaren, med hänsyn till alla inställningar för kommandoraden eller variabler i Windows PowerShell-körningsmiljön bestämma vad som ska visas för användaren.

Efter anropet till [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) returnerar `true`, [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) metoden ska anropa den [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) metod. Den här metoden skickar ett meddelande till användaren att godkänna feedback att säga om åtgärden bör behållas. Leverantören bör anropa [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) som ytterligare en kontroll efter ändringar av potentiellt skadliga system.

## <a name="attaching-dynamic-parameters-to-the-move-item-cmdlet"></a>Bifoga dynamiska parametrar till cmdleten Move-objekt

Ibland den `Move-Item` cmdlet kräver ytterligare parametrar som tillhandahålls dynamiskt vid körning. För att ge dessa dynamiska parametrar, navigering-leverantören måste implementera de [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) metod för att hämta de obligatoriska parametervärdena från objektet på den angivna sökvägen och returnera ett objekt med egenskaper och fält med parsning attribut liknar en cmdlet-klass eller en [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) objekt.

Den här providern för navigering implementerar inte den här metoden. Följande kod är dock standardimplementering av [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters).

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidermoveitemdynamicparameters](Msh_samplestestcmdlets#testprovidermoveitemdynamicparameters)]  -->

## <a name="normalizing-a-relative-path"></a>Normaliserar en relativ sökväg

Din navigering providern implementerar den [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) metod för att normalisera den fullständiga sökvägen som anges i den `path` parameter är i förhållande till sökvägen som angetts av den `basePath` parametern. Metoden returnerar en strängrepresentation av normaliserade sökvägen. Den skriver ett fel om de `path` parametern anger en sökväg som inte finns.

Exemplet navigering providern åsidosätts inte den här metoden. Följande är standardimplementering.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernormalizepath](Msh_samplestestcmdlets#testprovidernormalizepath)]  -->

#### <a name="things-to-remember-about-implementing-normalizerelativepath"></a>Kom ihåg följande om hur du implementerar NormalizeRelativePath

Implementeringen av [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) ska tolka den `path` parametern, men det behöver inte använda helt och hållet syntaktiska parsning. Du bör utforma den här metoden för att använda sökvägen för att leta upp sökvägsinformation i datalagret och skapa en väg som matchar gemener och versaler och standardiserade sökvägssyntaxen.

## <a name="code-sample"></a>Kodexempel

Komplett exempel finns i [AccessDbProviderSample05 kodexempel](./accessdbprovidersample05-code-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definiera objekttyper och formatering

Det är möjligt för en provider för att lägga till medlemmar i befintliga objekt eller definiera nya objekt. Mer information finns i[utöka objekttyper och formatering](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).
Det är möjligt för en provider för att lägga till medlemmar i befintliga objekt eller definiera nya objekt. Mer information finns i[utöka objekttyper och formatering](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-windows-powershell-provider"></a>Att skapa Windows PowerShell-providern

Mer information finns i [hur du registrera Cmdlets och Providers värdprogram](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).
Mer information finns i [hur du registrera Cmdlets och Providers värdprogram](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-windows-powershell-provider"></a>Testa Windows PowerShell-providern

När din Windows PowerShell-provider har registrerats med Windows PowerShell kan testa du den genom att köra cmdletarna stöds på kommandoraden, inklusive cmdlet: ar som gjorts tillgängliga av härledning. Det här exemplet kommer att testa exemplet navigering providern.

1. Kör ditt nya gränssnitt och använder den `Set-Location` cmdlet för att ange sökvägen till indikerar Access-databas.

   ```powershell
   Set-Location mydb:
   ```

2. Kör nu den `Get-Childitem` cmdlet för att hämta en lista över de databasen, som är tillgängliga databastabeller. Denna cmdlet hämtar också antalet rader för varje tabell.

   ```powershell
   Get-ChildItem | Format-Table rowcount,name -AutoSize
   ```

   ```output
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

3. Använd den `Set-Location` cmdleten igen för att ange platsen för tabellen Anställda data.

   ```powershell
   Set-Location Employees
   ```

4. Nu använder vi den `Get-Location` cmdlet för att hämta sökvägen till tabellen Anställda.

   ```powershell
   Get-Location
   ```

   ```output
   Path
   ----
   mydb:\Employees
   ```

5. Nu använda den `Get-Childitem` cmdlet skickas till den `Format-Table` cmdlet. Den här uppsättningen cmdlet: ar hämtar objekt för tabellen Anställda data som är tabellraderna. Formateras som angetts av den `Format-Table` cmdlet.

   ```powershell
   Get-ChildItem | Format-Table rownumber,psiscontainer,data -AutoSize
   ```

   ```output
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

6. Nu kan du köra den `Get-Item` cmdlet för att hämta objekt för rad 0 i tabellen Anställda data.

   ```powershell
   Get-Item 0
   ```

   ```output
   PSPath        : AccessDB::C:\PS\Northwind.mdb\Employees\0
   PSParentPath  : AccessDB::C:\PS\Northwind.mdb\Employees
   PSChildName   : 0
   PSDrive       : mydb
   PSProvider    : System.Management.Automation.ProviderInfo
   PSIsContainer : False
   Data           : System.Data.DataRow
   RowNumber      : 0
   ```

7. Använd den `Get-Item` cmdleten igen för att hämta medarbetardata för objekten i rad 0.

   ```powershell
   (Get-Item 0).data
   ```

   ```output
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

[Skapa Windows PowerShell-providers](./how-to-create-a-windows-powershell-provider.md)

[Utforma din Windows PowerShell-providern](./designing-your-windows-powershell-provider.md)

[Utöka objekttyper och formatering](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Utöka objekttyper och formatering](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Implementera en behållare Windows PowerShell-providern](./creating-a-windows-powershell-container-provider.md)

[Hur du registrerar Cmdlets, Providers och vara värd för program](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Hur du registrerar Cmdlets, Providers och vara värd för program](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Programmeringsguide för Windows PowerShell](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)