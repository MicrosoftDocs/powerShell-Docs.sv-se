---
description: Från och med PowerShell 6 definieras standardvyerna för objekt i PowerShell-källkod.  Du kan skapa egna `Format.ps1xml` filer om du vill ändra visningen av objekt eller definiera standard visning för nya objekt typer som du skapar i PowerShell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_format.ps1xml?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Format.ps1XML
ms.openlocfilehash: ea7a5262be912750b2a4ff6ce72060b31ccdfb8a
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93271257"
---
# <a name="about-formatps1xml"></a><span data-ttu-id="9de33-105">Om Format.ps1XML</span><span class="sxs-lookup"><span data-stu-id="9de33-105">About Format.ps1xml</span></span>

## <a name="short-description"></a><span data-ttu-id="9de33-106">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="9de33-106">Short description</span></span>

<span data-ttu-id="9de33-107">Från och med PowerShell 6 definieras standardvyerna för objekt i PowerShell-källkod.</span><span class="sxs-lookup"><span data-stu-id="9de33-107">Beginning in PowerShell 6, the default views for objects are defined in PowerShell source code.</span></span>

<span data-ttu-id="9de33-108">Du kan skapa egna `Format.ps1xml` filer om du vill ändra visningen av objekt eller definiera standard visning för nya objekt typer som du skapar i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9de33-108">You can create your own `Format.ps1xml` files to change the display of objects or to define default displays for new object types that you create in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="9de33-109">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="9de33-109">Long description</span></span>

<span data-ttu-id="9de33-110">Från och med PowerShell 6 definieras standardvyerna i PowerShell-källkod.</span><span class="sxs-lookup"><span data-stu-id="9de33-110">Beginning in PowerShell 6, the default views are defined in PowerShell source code.</span></span> <span data-ttu-id="9de33-111">`Format.ps1xml`Filerna från powershell 5,1 och tidigare versioner finns inte i PowerShell 6 och senare versioner.</span><span class="sxs-lookup"><span data-stu-id="9de33-111">The `Format.ps1xml` files from PowerShell 5.1 and earlier versions don't exist in PowerShell 6 and later versions.</span></span>

<span data-ttu-id="9de33-112">PowerShell-källkoden definierar standard visningen av objekt i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="9de33-112">The PowerShell source code defines the default display of objects in the PowerShell console.</span></span> <span data-ttu-id="9de33-113">Du kan skapa egna `Format.ps1xml` filer om du vill ändra visningen av objekt eller definiera standard visning för nya objekt typer som du skapar i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9de33-113">You can create your own `Format.ps1xml` files to change the display of objects or to define default displays for new object types that you create in PowerShell.</span></span>

<span data-ttu-id="9de33-114">När PowerShell visar ett objekt används data i strukturerade formateringsattribut för att fastställa standard visningen av objektet.</span><span class="sxs-lookup"><span data-stu-id="9de33-114">When PowerShell displays an object, it uses the data in structured formatting files to determine the default display of the object.</span></span> <span data-ttu-id="9de33-115">Data i formateringsattribut bestämmer om objektet återges i en tabell eller i en lista och avgör vilka egenskaper som visas som standard.</span><span class="sxs-lookup"><span data-stu-id="9de33-115">The data in the formatting files determines whether the object is rendered in a table or in a list, and it determines which properties are displayed by default.</span></span>

<span data-ttu-id="9de33-116">Formateringen påverkar endast visningen.</span><span class="sxs-lookup"><span data-stu-id="9de33-116">The formatting affects the display only.</span></span> <span data-ttu-id="9de33-117">Det påverkar inte vilka objekt egenskaper som har passerat pipelinen eller hur de skickas.</span><span class="sxs-lookup"><span data-stu-id="9de33-117">It doesn't affect which object properties are passed down the pipeline or how they're passed.</span></span> <span data-ttu-id="9de33-118">`Format.ps1xml` Det går inte att använda filer för att anpassa utdataformatet för hash-tabeller.</span><span class="sxs-lookup"><span data-stu-id="9de33-118">`Format.ps1xml` files can't be used to customize the output format for hash tables.</span></span>

<span data-ttu-id="9de33-119">En `.ps1xml` format fil kan definiera fyra olika vyer för varje objekt:</span><span class="sxs-lookup"><span data-stu-id="9de33-119">A `.ps1xml` formatting file can define four different views of each object:</span></span>

- <span data-ttu-id="9de33-120">Tabeller</span><span class="sxs-lookup"><span data-stu-id="9de33-120">Table</span></span>
- <span data-ttu-id="9de33-121">Lista</span><span class="sxs-lookup"><span data-stu-id="9de33-121">List</span></span>
- <span data-ttu-id="9de33-122">Täcka</span><span class="sxs-lookup"><span data-stu-id="9de33-122">Wide</span></span>
- <span data-ttu-id="9de33-123">Anpassat</span><span class="sxs-lookup"><span data-stu-id="9de33-123">Custom</span></span>

<span data-ttu-id="9de33-124">Till exempel, när utdata från ett `Get-ChildItem` kommando är skickas till ett `Format-List` kommando, `Format-List` använder listvyn som definierats i käll koden för att avgöra hur fil-och mappobjekt ska visas som en lista.</span><span class="sxs-lookup"><span data-stu-id="9de33-124">For example, when the output of a `Get-ChildItem` command is piped to a `Format-List` command, `Format-List` uses the list view defined in the source code to determine how to display the file and folder objects as a list.</span></span>

<span data-ttu-id="9de33-125">När en format fil innehåller mer än en vy av ett objekt, tillämpar PowerShell den första vyn som hittas.</span><span class="sxs-lookup"><span data-stu-id="9de33-125">When a formatting file includes more than one view of an object, PowerShell applies the first view that it finds.</span></span>

<span data-ttu-id="9de33-126">I en anpassad `Format.ps1xml` fil definieras en vy av en uppsättning XML-taggar som beskriver namnet på vyn, vilken typ av objekt som kan användas, kolumn rubriker och de egenskaper som visas i bröd texten i vyn.</span><span class="sxs-lookup"><span data-stu-id="9de33-126">In a custom `Format.ps1xml` file, a view is defined by a set of XML tags that describe the name of the view, the type of object to which it can be applied, the column headers, and the properties that are displayed in the body of the view.</span></span> <span data-ttu-id="9de33-127">Formatet i `Format.ps1xml` filer tillämpas precis innan data visas för användaren.</span><span class="sxs-lookup"><span data-stu-id="9de33-127">The format in `Format.ps1xml` files is applied just before the data is presented to the user.</span></span>

## <a name="creating-new-formatps1xml-files"></a><span data-ttu-id="9de33-128">Skapa nya Format.ps1XML-filer</span><span class="sxs-lookup"><span data-stu-id="9de33-128">Creating new Format.ps1xml files</span></span>

<span data-ttu-id="9de33-129">Om du vill ändra visnings formatet för en befintlig objekt vy, eller lägga till vyer för nya objekt, skapar du dina egna `Format.ps1xml` filer och lägger sedan till dem i PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="9de33-129">To change the display format of an existing object view, or to add views for new objects, create your own `Format.ps1xml` files, and then add them to your PowerShell session.</span></span>

<span data-ttu-id="9de33-130">Om du vill skapa en `Format.ps1xml` fil för att definiera en anpassad vy använder du cmdletarna [Get-FormatData](xref:Microsoft.PowerShell.Utility.Get-FormatData) och [export-FormatData](xref:Microsoft.PowerShell.Utility.Export-FormatData) .</span><span class="sxs-lookup"><span data-stu-id="9de33-130">To create a `Format.ps1xml` file to define a custom view, use the [Get-FormatData](xref:Microsoft.PowerShell.Utility.Get-FormatData) and [Export-FormatData](xref:Microsoft.PowerShell.Utility.Export-FormatData) cmdlets.</span></span> <span data-ttu-id="9de33-131">Använd en text redigerare för att redigera filen.</span><span class="sxs-lookup"><span data-stu-id="9de33-131">Use a text editor to edit the file.</span></span> <span data-ttu-id="9de33-132">Filen kan sparas till alla kataloger som PowerShell har åtkomst till, till exempel en under katalog till `$HOME` .</span><span class="sxs-lookup"><span data-stu-id="9de33-132">The file can be saved to any directory that PowerShell can access, such as a subdirectory of `$HOME`.</span></span>

<span data-ttu-id="9de33-133">Om du vill ändra formateringen för en aktuell vy letar du upp vyn i format filen och använder sedan taggarna för att ändra vyn.</span><span class="sxs-lookup"><span data-stu-id="9de33-133">To change the formatting of a current view, locate the view in the formatting file, and then use the tags to change the view.</span></span> <span data-ttu-id="9de33-134">Skapa en vy för en ny objekt typ genom att skapa en ny vy eller använda en befintlig vy som en modell.</span><span class="sxs-lookup"><span data-stu-id="9de33-134">To create a view for a new object type, create a new view, or use an existing view as a model.</span></span> <span data-ttu-id="9de33-135">Taggarna beskrivs i nästa avsnitt.</span><span class="sxs-lookup"><span data-stu-id="9de33-135">The tags are described in the next section.</span></span> <span data-ttu-id="9de33-136">Du kan sedan ta bort alla andra vyer i filen så att ändringarna är uppenbara för alla som granskar filen.</span><span class="sxs-lookup"><span data-stu-id="9de33-136">You can then delete all the other views in the file so that the changes are obvious to anyone examining the file.</span></span>

<span data-ttu-id="9de33-137">När du har sparat ändringarna använder du [Update-FormatData](xref:Microsoft.PowerShell.Utility.Update-FormatData) för att lägga till den nya filen i PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="9de33-137">After you save the changes, use the [Update-FormatData](xref:Microsoft.PowerShell.Utility.Update-FormatData) to add the new file to your PowerShell session.</span></span> <span data-ttu-id="9de33-138">Om du vill att vyn ska prioriteras över en vy som definierats i de inbyggda filerna använder du parametern **PrependPath** .</span><span class="sxs-lookup"><span data-stu-id="9de33-138">If you want your view to take precedence over a view defined in the built-in files, use the **PrependPath** parameter.</span></span> <span data-ttu-id="9de33-139">`Update-FormatData` påverkar endast den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="9de33-139">`Update-FormatData` affects only the current session.</span></span> <span data-ttu-id="9de33-140">Om du vill göra ändringen i alla framtida sessioner lägger du till `Update-FormatData` kommandot i din PowerShell-profil.</span><span class="sxs-lookup"><span data-stu-id="9de33-140">To make the change to all future sessions, add the `Update-FormatData` command to your PowerShell profile.</span></span>

### <a name="example-add-calendar-data-to-culture-objects"></a><span data-ttu-id="9de33-141">Exempel: Lägg till kalender data till kultur objekt</span><span class="sxs-lookup"><span data-stu-id="9de33-141">Example: Add calendar data to culture objects</span></span>

<span data-ttu-id="9de33-142">Det här exemplet visar hur du ändrar formateringen för kultur objekt **system. globalisering. CultureInfo** som genereras av `Get-Culture` cmdleten i den aktuella PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="9de33-142">This example shows how to change the formatting of the culture objects **System.Globalization.CultureInfo** generated by the `Get-Culture` cmdlet in the current PowerShell session.</span></span> <span data-ttu-id="9de33-143">Kommandona i exemplet lägger till **kalender** egenskapen i standardvyn visning av kultur objekt.</span><span class="sxs-lookup"><span data-stu-id="9de33-143">The commands in the example add the **Calendar** property to the default table view display of culture objects.</span></span>

<span data-ttu-id="9de33-144">Börja med att hämta format data från käll kods filen och skapa en `Format.ps1xml` fil som innehåller den aktuella vyn av kultur objekt.</span><span class="sxs-lookup"><span data-stu-id="9de33-144">To begin, get the format data from the source code file and create a `Format.ps1xml` file that contains the current view of the culture objects.</span></span>

```powershell
Get-FormatData -TypeName System.Globalization.CultureInfo |
  Export-FormatData -Path $HOME\Format\CultureInfo.Format.ps1xml
```

<span data-ttu-id="9de33-145">Öppna `CultureInfo.Format.ps1xml` filen i valfri XML-eller text redigerare, t. ex. Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="9de33-145">Open the `CultureInfo.Format.ps1xml` file in any XML or text editor, such as Visual Studio Code.</span></span> <span data-ttu-id="9de33-146">Följande XML definierar vyerna för **CultureInfo** -objektet.</span><span class="sxs-lookup"><span data-stu-id="9de33-146">The following XML defines the views of the **CultureInfo** object.</span></span>

<span data-ttu-id="9de33-147">`CultureInfo.Format.ps1xml`Filen bör se ut som i följande exempel:</span><span class="sxs-lookup"><span data-stu-id="9de33-147">The `CultureInfo.Format.ps1xml` file should look like the following sample:</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<Configuration>
  <ViewDefinitions>
    <View>
      <Name>System.Globalization.CultureInfo</Name>
      <ViewSelectedBy>
        <TypeName>System.Globalization.CultureInfo</TypeName>
      </ViewSelectedBy>
      <TableControl>
        <TableHeaders>
          <TableColumnHeader>
            <Width>16</Width>
          </TableColumnHeader>
          <TableColumnHeader>
            <Width>16</Width>
          </TableColumnHeader>
          <TableColumnHeader />
        </TableHeaders>
        <TableRowEntries>
          <TableRowEntry>
            <TableColumnItems>
              <TableColumnItem>
                <PropertyName>LCID</PropertyName>
              </TableColumnItem>
              <TableColumnItem>
                <PropertyName>Name</PropertyName>
              </TableColumnItem>
              <TableColumnItem>
                <PropertyName>DisplayName</PropertyName>
              </TableColumnItem>
            </TableColumnItems>
          </TableRowEntry>
        </TableRowEntries>
      </TableControl>
    </View>
  </ViewDefinitions>
</Configuration>
```

<span data-ttu-id="9de33-148">Skapa en ny kolumn för **kalender** egenskapen genom att lägga till en ny uppsättning `<TableColumnHeader>` taggar.</span><span class="sxs-lookup"><span data-stu-id="9de33-148">Create a new column for the **Calendar** property by adding a new set of `<TableColumnHeader>` tags.</span></span> <span data-ttu-id="9de33-149">Värdet för egenskapen **Calendar** kan vara Long, så ange ett värde på 45 tecken som `<Width>` .</span><span class="sxs-lookup"><span data-stu-id="9de33-149">The value of the **Calendar** property can be long, so specify a value of 45 characters as the `<Width>`.</span></span>

```xml
<TableHeaders>
  <TableColumnHeader>
    <Width>16</Width>
  </TableColumnHeader>
  <TableColumnHeader>
    <Width>16</Width>
  </TableColumnHeader>
  <TableColumnHeader>
    <Width>45</Width>
  </TableColumnHeader>
  <TableColumnHeader/>
</TableHeaders>
```

<span data-ttu-id="9de33-150">Lägg till ett nytt kolumn objekt för **kalender** i tabell rader med `<TableColumnItem>` `<PropertyName` taggarna och:</span><span class="sxs-lookup"><span data-stu-id="9de33-150">Add a new column item for **Calendar** in the table rows using the `<TableColumnItem>` and `<PropertyName` tags:</span></span>

```xml
<TableRowEntries>
  <TableRowEntry>
    <TableColumnItems>
      <TableColumnItem>
        <PropertyName>LCID</PropertyName>
      </TableColumnItem>
      <TableColumnItem>
        <PropertyName>Name</PropertyName>
      </TableColumnItem>
      <TableColumnItem>
        <PropertyName>Calendar</PropertyName>
      </TableColumnItem>
      <TableColumnItem>
        <PropertyName>DisplayName</PropertyName>
      </TableColumnItem>
    </TableColumnItems>
  </TableRowEntry>
</TableRowEntries>
```

<span data-ttu-id="9de33-151">Spara och stäng filen.</span><span class="sxs-lookup"><span data-stu-id="9de33-151">Save and close the file.</span></span> <span data-ttu-id="9de33-152">Använd `Update-FormatData` för att lägga till den nya format filen i den aktuella PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="9de33-152">Use `Update-FormatData` to add the new format file to the current PowerShell session.</span></span>

<span data-ttu-id="9de33-153">I det här exemplet används parametern **PrependPath** för att placera den nya filen i en högre prioritets ordning än den ursprungliga filen.</span><span class="sxs-lookup"><span data-stu-id="9de33-153">This example uses the **PrependPath** parameter to place the new file in a higher precedence order than the original file.</span></span> <span data-ttu-id="9de33-154">Mer information finns i [Update-FormatData](xref:Microsoft.PowerShell.Utility.Update-FormatData).</span><span class="sxs-lookup"><span data-stu-id="9de33-154">For more information, see [Update-FormatData](xref:Microsoft.PowerShell.Utility.Update-FormatData).</span></span>

```powershell
Update-FormatData -PrependPath $HOME\Format\CultureInfo.Format.ps1xml
```

<span data-ttu-id="9de33-155">Testa ändringen genom att skriva `Get-Culture` och granska utdata som innehåller **kalender** egenskapen.</span><span class="sxs-lookup"><span data-stu-id="9de33-155">To test the change, type `Get-Culture` and review the output that includes the **Calendar** property.</span></span>

```powershell
Get-Culture
```

```Output
LCID  Name   Calendar                                DisplayName
----  ----   --------                                -----------
1033  en-US  System.Globalization.GregorianCalendar  English (United States)
```

## <a name="the-xml-in-formatps1xml-files"></a><span data-ttu-id="9de33-156">XML i Format.ps1XML-filer</span><span class="sxs-lookup"><span data-stu-id="9de33-156">The XML in Format.ps1xml files</span></span>

<span data-ttu-id="9de33-157">Du hittar fullständig schema definition i [formatet. xsd](https://github.com/PowerShell/PowerShell/blob/master/src/Schemas/Format.xsd) i PowerShell-källkoden på GitHub.</span><span class="sxs-lookup"><span data-stu-id="9de33-157">The full schema definition can be found in [Format.xsd](https://github.com/PowerShell/PowerShell/blob/master/src/Schemas/Format.xsd) in the PowerShell source code repository on GitHub.</span></span>

<span data-ttu-id="9de33-158">Avsnittet **ViewDefinitions** i varje `Format.ps1xml` fil innehåller de `<View>` taggar som definierar varje vy.</span><span class="sxs-lookup"><span data-stu-id="9de33-158">The **ViewDefinitions** section of each `Format.ps1xml` file contains the `<View>` tags that define each view.</span></span> <span data-ttu-id="9de33-159">En typisk `<View>` tagg innehåller följande Taggar:</span><span class="sxs-lookup"><span data-stu-id="9de33-159">A typical `<View>` tag includes the following tags:</span></span>

- <span data-ttu-id="9de33-160">`<Name>` identifierar namnet på vyn.</span><span class="sxs-lookup"><span data-stu-id="9de33-160">`<Name>` identifies the name of the view.</span></span>
- <span data-ttu-id="9de33-161">`<ViewSelectedBy>` anger objekt typen eller typerna som vyn gäller för.</span><span class="sxs-lookup"><span data-stu-id="9de33-161">`<ViewSelectedBy>` specifies the object type or types to which the view applies.</span></span>
- <span data-ttu-id="9de33-162">`<GroupBy>` anger hur objekt i vyn ska kombineras i grupper.</span><span class="sxs-lookup"><span data-stu-id="9de33-162">`<GroupBy>` specifies how items in the view will be combined in groups.</span></span>
- <span data-ttu-id="9de33-163">`<TableControl>`, `<ListControl>` , `<WideControl>` och `<CustomControl>` innehåller taggarna som anger hur varje objekt ska visas.</span><span class="sxs-lookup"><span data-stu-id="9de33-163">`<TableControl>`, `<ListControl>`, `<WideControl>`, and `<CustomControl>` contain the tags that specify how each item will be displayed.</span></span>

### <a name="viewselectedby-tag"></a><span data-ttu-id="9de33-164">ViewSelectedBy-tagg</span><span class="sxs-lookup"><span data-stu-id="9de33-164">ViewSelectedBy tag</span></span>

<span data-ttu-id="9de33-165">`<ViewSelectedBy>`Taggen kan innehålla en `<TypeName>` tagg för varje objekt typ som vyn gäller för.</span><span class="sxs-lookup"><span data-stu-id="9de33-165">The `<ViewSelectedBy>` tag can contain a `<TypeName>` tag for each object type to which the view applies.</span></span> <span data-ttu-id="9de33-166">Eller så kan den innehålla en `<SelectionSetName>` tagg som refererar till en urvals uppsättning som definieras någon annan stans genom att använda en- `<SelectionSet>` tagg.</span><span class="sxs-lookup"><span data-stu-id="9de33-166">Or, it can contain a `<SelectionSetName>` tag that references a selection set that is defined elsewhere by using a `<SelectionSet>` tag.</span></span>

### <a name="groupby-tag"></a><span data-ttu-id="9de33-167">GroupBy-tagg</span><span class="sxs-lookup"><span data-stu-id="9de33-167">GroupBy tag</span></span>

<span data-ttu-id="9de33-168">`<GroupBy>`Taggen innehåller en `<PropertyName>` tagg som anger den objekt egenskap enligt vilken objekten ska grupperas.</span><span class="sxs-lookup"><span data-stu-id="9de33-168">The `<GroupBy>` tag contains a `<PropertyName>` tag that specifies the object property by which items are to be grouped.</span></span> <span data-ttu-id="9de33-169">Den innehåller också antingen en `<Label>` tagg som anger en sträng som ska användas som en etikett för varje grupp eller en `<CustomControlName>` tagg som refererar till en anpassad kontroll som definierats någon annan stans med en `<Control>` tagg.</span><span class="sxs-lookup"><span data-stu-id="9de33-169">It also contains either a `<Label>` tag that specifies a string to be used as a label for each group or a `<CustomControlName>` tag that references a custom control defined elsewhere using a `<Control>` tag.</span></span> <span data-ttu-id="9de33-170">`<Control>`Taggen innehåller en `<Name>` tagg och en `<CustomControl>` tagg.</span><span class="sxs-lookup"><span data-stu-id="9de33-170">The `<Control>` tag contains a `<Name>` tag and a `<CustomControl>` tag.</span></span>

### <a name="tablecontroltag"></a><span data-ttu-id="9de33-171">TableControlTag</span><span class="sxs-lookup"><span data-stu-id="9de33-171">TableControlTag</span></span>

<span data-ttu-id="9de33-172">`<TableControl>`Taggen innehåller vanligt vis `<TableHeaders>` och `<TableRowEntries>` taggar som definierar formateringen för tabellens huvuden och rader.</span><span class="sxs-lookup"><span data-stu-id="9de33-172">The `<TableControl>` tag typically contains `<TableHeaders>` and `<TableRowEntries>` tags that define the formatting for the table's heads and rows.</span></span> <span data-ttu-id="9de33-173">`<TableHeaders>`Taggen innehåller vanligt vis `<TableColumnHeader>` taggar som innehåller `<Label>` `<Width>` taggar, och `<Alignment>` .</span><span class="sxs-lookup"><span data-stu-id="9de33-173">The `<TableHeaders>` tag typically contains `<TableColumnHeader>` tags that contain `<Label>`, `<Width>`, and `<Alignment>` tags.</span></span> <span data-ttu-id="9de33-174">`<TableRowEntries>`Taggen innehåller `<TableRowEntry>` taggar för varje rad i tabellen.</span><span class="sxs-lookup"><span data-stu-id="9de33-174">The `<TableRowEntries>` tag contains `<TableRowEntry>` tags for each row in the table.</span></span> <span data-ttu-id="9de33-175">`<TableRowEntry>`Taggen innehåller en `<TableColumnItems>` tagg som innehåller en `<TableColumnItem>` tagg för varje kolumn på raden.</span><span class="sxs-lookup"><span data-stu-id="9de33-175">The `<TableRowEntry>` tag contains a `<TableColumnItems>` tag that contains a `<TableColumnItem>` tag for each column in the row.</span></span> <span data-ttu-id="9de33-176">Normalt `<TableColumnItem>` innehåller taggen en `<PropertyName>` tagg som identifierar objekt egenskapen som ska visas på den definierade platsen, eller en `<ScriptBlock>` tagg som innehåller skript kod som beräknar ett resultat som ska visas på platsen.</span><span class="sxs-lookup"><span data-stu-id="9de33-176">Typically, the `<TableColumnItem>` tag contains either a `<PropertyName>` tag that identifies the object property to be displayed in the defined location, or a `<ScriptBlock>` tag that contains script code that calculates a result that is to be displayed in the location.</span></span>

> [!NOTE]
> <span data-ttu-id="9de33-177">Skript block kan också användas på andra platser på platser där beräknade resultat kan vara användbara.</span><span class="sxs-lookup"><span data-stu-id="9de33-177">Script blocks can also be used elsewhere in locations where calculated results can be useful.</span></span>

<span data-ttu-id="9de33-178">`<TableColumnItem>`Taggen kan också innehålla en `<FormatString>` tagg som anger hur egenskapen eller de beräknade resultaten ska visas.</span><span class="sxs-lookup"><span data-stu-id="9de33-178">The `<TableColumnItem>` tag can also contain a `<FormatString>` tag that specifies how the property or the calculated results will be displayed.</span></span>

### <a name="listcontrol-tag"></a><span data-ttu-id="9de33-179">ListControl-tagg</span><span class="sxs-lookup"><span data-stu-id="9de33-179">ListControl tag</span></span>

<span data-ttu-id="9de33-180">`<ListControl>`Taggen innehåller vanligt vis en `<ListEntries>` tagg.</span><span class="sxs-lookup"><span data-stu-id="9de33-180">The `<ListControl>` tag typically contains a `<ListEntries>` tag.</span></span> <span data-ttu-id="9de33-181">`<ListEntries>`Taggen innehåller en `<ListEntry>` tagg.</span><span class="sxs-lookup"><span data-stu-id="9de33-181">The `<ListEntries>` tag contains a `<ListEntry>` tag.</span></span> <span data-ttu-id="9de33-182">`<ListEntry>`Taggen innehåller en `<ListItems>` tagg.</span><span class="sxs-lookup"><span data-stu-id="9de33-182">The `<ListEntry>` tag contains a `<ListItems>` tag.</span></span> <span data-ttu-id="9de33-183">`<ListItems>`Taggen innehåller `<ListItem>` taggar som innehåller `<PropertyName>` taggar.</span><span class="sxs-lookup"><span data-stu-id="9de33-183">The `<ListItems>` tag contains `<ListItem>` tags, which contain `<PropertyName>` tags.</span></span> <span data-ttu-id="9de33-184">`<PropertyName>`Taggarna anger vilken objekt egenskap som ska visas på den angivna platsen i listan.</span><span class="sxs-lookup"><span data-stu-id="9de33-184">The `<PropertyName>` tags specify the object property to be displayed at the specified location in the list.</span></span> <span data-ttu-id="9de33-185">Om visnings valet definieras med en urvals uppsättning `<ListControl>` `<ListEntry>` kan taggarna och också innehålla en `<EntrySelectedBy>` tagg som innehåller en eller flera `<TypeName>` taggar.</span><span class="sxs-lookup"><span data-stu-id="9de33-185">If the view selection is defined using a selection set, the `<ListControl>` and `<ListEntry>` tags can also contain an `<EntrySelectedBy>` tag that contains one or more `<TypeName>` tags.</span></span> <span data-ttu-id="9de33-186">`<TypeName>`Taggarna anger vilken objekt typ `<ListControl>` taggen är avsedd att visa.</span><span class="sxs-lookup"><span data-stu-id="9de33-186">These `<TypeName>` tags specify the object type that the `<ListControl>` tag is intended to display.</span></span>

### <a name="widecontrol-tag"></a><span data-ttu-id="9de33-187">WideControl-tagg</span><span class="sxs-lookup"><span data-stu-id="9de33-187">WideControl tag</span></span>

<span data-ttu-id="9de33-188">`<WideControl>`Taggen innehåller vanligt vis en `<WideEntries>` tagg.</span><span class="sxs-lookup"><span data-stu-id="9de33-188">The `<WideControl>` tag typically contains a `<WideEntries>` tag.</span></span> <span data-ttu-id="9de33-189">`<WideEntries>`Taggen innehåller en eller flera `<WideEntry>` taggar.</span><span class="sxs-lookup"><span data-stu-id="9de33-189">The `<WideEntries>` tag contains one or more `<WideEntry>` tags.</span></span> <span data-ttu-id="9de33-190">En- `<WideEntry>` tagg innehåller vanligt vis en `<PropertyName>` tagg som anger den egenskap som ska visas på den angivna platsen i vyn.</span><span class="sxs-lookup"><span data-stu-id="9de33-190">A `<WideEntry>` tag typically contains a `<PropertyName>` tag that specifies the property to be displayed at the specified location in the view.</span></span> <span data-ttu-id="9de33-191">`<PropertyName>`Taggen kan innehålla en `<FormatString>` tagg som anger hur egenskapen ska visas.</span><span class="sxs-lookup"><span data-stu-id="9de33-191">The `<PropertyName>` tag can contain a `<FormatString>` tag that specifies how the property is to be displayed.</span></span>

### <a name="customcontrol-tag"></a><span data-ttu-id="9de33-192">CustomControl-tagg</span><span class="sxs-lookup"><span data-stu-id="9de33-192">CustomControl tag</span></span>

<span data-ttu-id="9de33-193">Med `<CustomControl>` taggen kan du definiera ett format genom att använda ett-skript block.</span><span class="sxs-lookup"><span data-stu-id="9de33-193">The `<CustomControl>` tag lets you use a script block to define a format.</span></span> <span data-ttu-id="9de33-194">En- `<CustomControl>` tagg innehåller vanligt vis en `<CustomEntries>` tagg som innehåller flera `<CustomEntry>` taggar.</span><span class="sxs-lookup"><span data-stu-id="9de33-194">A `<CustomControl>` tag typically contains a `<CustomEntries>` tag that contains multiple `<CustomEntry>` tags.</span></span> <span data-ttu-id="9de33-195">Varje- `<CustomEntry>` tagg innehåller en `<CustomItem>` tagg som kan innehålla en rad olika taggar som anger innehåll och formatering för den angivna platsen i vyn, inklusive `<Text>` , `<Indentation>` , `<ExpressionBinding>` och `<NewLine>` taggar.</span><span class="sxs-lookup"><span data-stu-id="9de33-195">Each `<CustomEntry>` tag contains a `<CustomItem>` tag that can contain a variety of tags that specify contents and formatting of the specified location in the view, including `<Text>`, `<Indentation>`, `<ExpressionBinding>`, and `<NewLine>` tags.</span></span>

## <a name="tracing-formatps1xml-file-use"></a><span data-ttu-id="9de33-196">Använda spårning Format.ps1XML-fil</span><span class="sxs-lookup"><span data-stu-id="9de33-196">Tracing Format.ps1xml file use</span></span>

<span data-ttu-id="9de33-197">Om du vill identifiera fel vid inläsning eller tillämpning av `Format.ps1xml` filer använder du `Trace-Command` cmdleten med någon av följande format komponenter som värde för parametern **Name** :</span><span class="sxs-lookup"><span data-stu-id="9de33-197">To detect errors in the loading or application of `Format.ps1xml` files, use the `Trace-Command` cmdlet with any of the following format components as the value of the **Name** parameter:</span></span>

- <span data-ttu-id="9de33-198">FormatFileLoading</span><span class="sxs-lookup"><span data-stu-id="9de33-198">FormatFileLoading</span></span>
- <span data-ttu-id="9de33-199">FormatViewBinding</span><span class="sxs-lookup"><span data-stu-id="9de33-199">FormatViewBinding</span></span>

<span data-ttu-id="9de33-200">Mer information finns i [trace-Command](xref:Microsoft.PowerShell.Utility.Trace-Command) och [Get-TraceSource](xref:Microsoft.PowerShell.Utility.Get-TraceSource).</span><span class="sxs-lookup"><span data-stu-id="9de33-200">For more information, see [Trace-Command](xref:Microsoft.PowerShell.Utility.Trace-Command) and [Get-TraceSource](xref:Microsoft.PowerShell.Utility.Get-TraceSource).</span></span>

## <a name="signing-a-formatps1xml-file"></a><span data-ttu-id="9de33-201">Signera en Format.ps1XML-fil</span><span class="sxs-lookup"><span data-stu-id="9de33-201">Signing a Format.ps1xml file</span></span>

<span data-ttu-id="9de33-202">Du skyddar användare av `Format.ps1xml` filen genom att signera filen med en digital signatur.</span><span class="sxs-lookup"><span data-stu-id="9de33-202">To protect the users of your `Format.ps1xml` file, sign the file using a digital signature.</span></span> <span data-ttu-id="9de33-203">Mer information finns i [about_Signing](about_Signing.md).</span><span class="sxs-lookup"><span data-stu-id="9de33-203">For more information, see [about_Signing](about_Signing.md).</span></span>

## <a name="sample-xml-for-a-format-table-custom-view"></a><span data-ttu-id="9de33-204">Exempel-XML för en Format-Table anpassad vy</span><span class="sxs-lookup"><span data-stu-id="9de33-204">Sample XML for a Format-Table custom view</span></span>

<span data-ttu-id="9de33-205">Följande XML-exempel skapar en `Format-Table` anpassad vy för objekten **system. io. DirectoryInfo** och **system. io. fileinfo** som skapats av `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="9de33-205">The following XML sample creates a `Format-Table` custom view for the **System.IO.DirectoryInfo** and **System.IO.FileInfo** objects created by `Get-ChildItem`.</span></span> <span data-ttu-id="9de33-206">Den anpassade vyn heter **mygciview** och lägger till **CreationTime** -kolumnen i tabellen.</span><span class="sxs-lookup"><span data-stu-id="9de33-206">The custom view is named **mygciview** and adds the **CreationTime** column to the table.</span></span>

<span data-ttu-id="9de33-207">Skapa en anpassad vy genom att använda `Get-FormatData` `Export-FormatData` cmdletarna och för att generera en `.ps1xml` fil.</span><span class="sxs-lookup"><span data-stu-id="9de33-207">To create the custom view, use the `Get-FormatData` and `Export-FormatData` cmdlets to generate a `.ps1xml` file.</span></span> <span data-ttu-id="9de33-208">Redigera sedan `.ps1xml` filen och skapa koden för den anpassade vyn.</span><span class="sxs-lookup"><span data-stu-id="9de33-208">Then, edit your `.ps1xml` file to create the code for your custom view.</span></span> <span data-ttu-id="9de33-209">`.ps1xml`Filen kan lagras i valfri katalog som PowerShell kan komma åt.</span><span class="sxs-lookup"><span data-stu-id="9de33-209">The `.ps1xml` file can be stored in any directory that PowerShell can access.</span></span> <span data-ttu-id="9de33-210">Till exempel en under katalog till `$HOME` .</span><span class="sxs-lookup"><span data-stu-id="9de33-210">For example, a subdirectory of `$HOME`.</span></span>

<span data-ttu-id="9de33-211">När `.ps1xml` filen har skapats använder du `Update-FormatData` cmdleten för att inkludera vyn i den aktuella PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="9de33-211">After the `.ps1xml` file is created, use the `Update-FormatData` cmdlet to include the view in the current PowerShell session.</span></span> <span data-ttu-id="9de33-212">Eller Lägg till kommandot Update i din PowerShell-profil om du behöver vyn tillgänglig i alla PowerShell-sessioner.</span><span class="sxs-lookup"><span data-stu-id="9de33-212">Or, add the update command to your PowerShell profile if you need the view available in all PowerShell sessions.</span></span>

<span data-ttu-id="9de33-213">I det här exemplet måste den anpassade vyn använda tabell formatet, annars `Format-Table` Miss lyckas.</span><span class="sxs-lookup"><span data-stu-id="9de33-213">For this example, the custom view must use the table format, otherwise, `Format-Table` fails.</span></span>

<span data-ttu-id="9de33-214">Använd `Format-Table` med parametern **View** för att ange den anpassade vyns namn, **mygciview** och formatera tabellens utdata med kolumnen **CreationTime** .</span><span class="sxs-lookup"><span data-stu-id="9de33-214">Use `Format-Table` with the **View** parameter to specify the custom view's name, **mygciview** , and format the table's output with the **CreationTime** column.</span></span> <span data-ttu-id="9de33-215">Ett exempel på hur kommandot körs finns i [Format-Table](xref:Microsoft.PowerShell.Utility.Format-Table).</span><span class="sxs-lookup"><span data-stu-id="9de33-215">For an example of how the command is run, see [Format-Table](xref:Microsoft.PowerShell.Utility.Format-Table).</span></span>

> [!NOTE]
> <span data-ttu-id="9de33-216">Även om du kan hämta XML-formatering från käll koden för att skapa en anpassad vy, kan det krävas mer utveckling för att få önskat resultat.</span><span class="sxs-lookup"><span data-stu-id="9de33-216">Although you can get the formatting XML from the source code to create a custom view, more development might be needed to get the desired result.</span></span>

<span data-ttu-id="9de33-217">I följande `Get-FormatData` kommando finns ett alternativ för parametern **PowerShellVersion** för att se till att all lokal formateringsinformation returneras.</span><span class="sxs-lookup"><span data-stu-id="9de33-217">In the following `Get-FormatData` command, there's an alternative for the **PowerShellVersion** parameter to ensure that all local formatting information is returned.</span></span> <span data-ttu-id="9de33-218">Använd `-PowerShellVersion $PSVersionTable.PSVersion` snarare än en angiven PowerShell-version.</span><span class="sxs-lookup"><span data-stu-id="9de33-218">Use `-PowerShellVersion $PSVersionTable.PSVersion` rather than a specific PowerShell version.</span></span>

```powershell
Get-FormatData -PowerShellVersion 5.1 -TypeName System.IO.DirectoryInfo |
   Export-FormatData -Path ./Mygciview.Format.ps1xml
Update-FormatData -AppendPath ./Mygciview.Format.ps1xml
```

```xml
<?xml version="1.0" encoding="utf-8"?>
<Configuration>
  <ViewDefinitions>
    <View>
      <Name>mygciview</Name>
      <ViewSelectedBy>
        <TypeName>System.IO.DirectoryInfo</TypeName>
        <TypeName>System.IO.FileInfo</TypeName>
      </ViewSelectedBy>
      <GroupBy>
        <PropertyName>PSParentPath</PropertyName>
      </GroupBy>
      <TableControl>
        <TableHeaders>
          <TableColumnHeader>
            <Label>Mode</Label>
            <Width>7</Width>
            <Alignment>Left</Alignment>
          </TableColumnHeader>
          <TableColumnHeader>
            <Label>LastWriteTime</Label>
            <Width>26</Width>
            <Alignment>Right</Alignment>
          </TableColumnHeader>
          <TableColumnHeader>
            <Label>CreationTime</Label>
            <Width>26</Width>
            <Alignment>Right</Alignment>
          </TableColumnHeader>
          <TableColumnHeader>
            <Label>Length</Label>
            <Width>14</Width>
            <Alignment>Right</Alignment>
          </TableColumnHeader>
          <TableColumnHeader>
            <Label>Name</Label>
            <Alignment>Left</Alignment>
          </TableColumnHeader>
        </TableHeaders>
        <TableRowEntries>
          <TableRowEntry>
            <Wrap />
            <TableColumnItems>
              <TableColumnItem>
                <PropertyName>ModeWithoutHardLink</PropertyName>
              </TableColumnItem>
              <TableColumnItem>
                <PropertyName>LastWriteTime</PropertyName>
              </TableColumnItem>
              <TableColumnItem>
                <PropertyName>CreationTime</PropertyName>
              </TableColumnItem>
              <TableColumnItem>
                <PropertyName>Length</PropertyName>
              </TableColumnItem>
              <TableColumnItem>
                <PropertyName>Name</PropertyName>
              </TableColumnItem>
            </TableColumnItems>
          </TableRowEntry>
        </TableRowEntries>
      </TableControl>
    </View>
  </ViewDefinitions>
</Configuration>
```

## <a name="see-also"></a><span data-ttu-id="9de33-219">Se även</span><span class="sxs-lookup"><span data-stu-id="9de33-219">See also</span></span>

[<span data-ttu-id="9de33-220">Exportera – FormatData</span><span class="sxs-lookup"><span data-stu-id="9de33-220">Export-FormatData</span></span>](xref:Microsoft.PowerShell.Utility.Export-FormatData)

[<span data-ttu-id="9de33-221">Get-FormatData</span><span class="sxs-lookup"><span data-stu-id="9de33-221">Get-FormatData</span></span>](xref:Microsoft.PowerShell.Utility.Get-FormatData)

[<span data-ttu-id="9de33-222">Get-TraceSource</span><span class="sxs-lookup"><span data-stu-id="9de33-222">Get-TraceSource</span></span>](xref:Microsoft.PowerShell.Utility.Get-TraceSource)

[<span data-ttu-id="9de33-223">XML-referens för formatschema</span><span class="sxs-lookup"><span data-stu-id="9de33-223">Format Schema XML Reference</span></span>](/powershell/scripting/developer/format/format-schema-xml-reference)

[<span data-ttu-id="9de33-224">Spåra-kommando</span><span class="sxs-lookup"><span data-stu-id="9de33-224">Trace-Command</span></span>](xref:Microsoft.PowerShell.Utility.Trace-Command)

[<span data-ttu-id="9de33-225">Uppdatera – FormatData</span><span class="sxs-lookup"><span data-stu-id="9de33-225">Update-FormatData</span></span>](xref:Microsoft.PowerShell.Utility.Update-FormatData)

[<span data-ttu-id="9de33-226">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="9de33-226">Writing a PowerShell Formatting File</span></span>](/powershell/scripting/developer/format/writing-a-powershell-formatting-file)
