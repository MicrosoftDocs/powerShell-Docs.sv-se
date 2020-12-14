---
description: Från och med PowerShell 6 definieras standardvyerna för objekt i PowerShell-källkod.  Du kan skapa egna `Format.ps1xml` filer om du vill ändra visningen av objekt eller definiera standard visning för nya objekt typer som du skapar i PowerShell.
Locale: en-US
ms.date: 11/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_format.ps1xml?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Format.ps1XML
ms.openlocfilehash: 56bac204e33c39aa6192da9e6a899f00b0a4a743
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709258"
---
# <a name="about-formatps1xml"></a><span data-ttu-id="da9a2-104">Om Format.ps1XML</span><span class="sxs-lookup"><span data-stu-id="da9a2-104">About Format.ps1xml</span></span>

## <a name="short-description"></a><span data-ttu-id="da9a2-105">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="da9a2-105">Short description</span></span>

<span data-ttu-id="da9a2-106">Från och med PowerShell 6 definieras standardvyerna för objekt i PowerShell-källkod.</span><span class="sxs-lookup"><span data-stu-id="da9a2-106">Beginning in PowerShell 6, the default views for objects are defined in PowerShell source code.</span></span>

<span data-ttu-id="da9a2-107">Du kan skapa egna `Format.ps1xml` filer om du vill ändra visningen av objekt eller definiera standard visning för nya objekt typer som du skapar i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="da9a2-107">You can create your own `Format.ps1xml` files to change the display of objects or to define default displays for new object types that you create in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="da9a2-108">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="da9a2-108">Long description</span></span>

<span data-ttu-id="da9a2-109">Från och med PowerShell 6 definieras standardvyerna i PowerShell-källkod.</span><span class="sxs-lookup"><span data-stu-id="da9a2-109">Beginning in PowerShell 6, the default views are defined in PowerShell source code.</span></span> <span data-ttu-id="da9a2-110">`Format.ps1xml`Filerna från powershell 5,1 och tidigare versioner finns inte i PowerShell 6 och senare versioner.</span><span class="sxs-lookup"><span data-stu-id="da9a2-110">The `Format.ps1xml` files from PowerShell 5.1 and earlier versions don't exist in PowerShell 6 and later versions.</span></span>

<span data-ttu-id="da9a2-111">PowerShell-källkoden definierar standard visningen av objekt i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="da9a2-111">The PowerShell source code defines the default display of objects in the PowerShell console.</span></span> <span data-ttu-id="da9a2-112">Du kan skapa egna `Format.ps1xml` filer om du vill ändra visningen av objekt eller definiera standard visning för nya objekt typer som du skapar i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="da9a2-112">You can create your own `Format.ps1xml` files to change the display of objects or to define default displays for new object types that you create in PowerShell.</span></span>

<span data-ttu-id="da9a2-113">När PowerShell visar ett objekt används data i strukturerade formateringsattribut för att fastställa standard visningen av objektet.</span><span class="sxs-lookup"><span data-stu-id="da9a2-113">When PowerShell displays an object, it uses the data in structured formatting files to determine the default display of the object.</span></span> <span data-ttu-id="da9a2-114">Data i formateringsattribut bestämmer om objektet återges i en tabell eller i en lista och avgör vilka egenskaper som visas som standard.</span><span class="sxs-lookup"><span data-stu-id="da9a2-114">The data in the formatting files determines whether the object is rendered in a table or in a list, and it determines which properties are displayed by default.</span></span>

<span data-ttu-id="da9a2-115">Formateringen påverkar endast visningen.</span><span class="sxs-lookup"><span data-stu-id="da9a2-115">The formatting affects the display only.</span></span> <span data-ttu-id="da9a2-116">Det påverkar inte vilka objekt egenskaper som har passerat pipelinen eller hur de skickas.</span><span class="sxs-lookup"><span data-stu-id="da9a2-116">It doesn't affect which object properties are passed down the pipeline or how they're passed.</span></span> <span data-ttu-id="da9a2-117">`Format.ps1xml` Det går inte att använda filer för att anpassa utdataformatet för hash-tabeller.</span><span class="sxs-lookup"><span data-stu-id="da9a2-117">`Format.ps1xml` files can't be used to customize the output format for hash tables.</span></span>

<span data-ttu-id="da9a2-118">En `.ps1xml` format fil kan definiera fyra olika vyer för varje objekt:</span><span class="sxs-lookup"><span data-stu-id="da9a2-118">A `.ps1xml` formatting file can define four different views of each object:</span></span>

- <span data-ttu-id="da9a2-119">Tabeller</span><span class="sxs-lookup"><span data-stu-id="da9a2-119">Table</span></span>
- <span data-ttu-id="da9a2-120">Lista</span><span class="sxs-lookup"><span data-stu-id="da9a2-120">List</span></span>
- <span data-ttu-id="da9a2-121">Täcka</span><span class="sxs-lookup"><span data-stu-id="da9a2-121">Wide</span></span>
- <span data-ttu-id="da9a2-122">Anpassad</span><span class="sxs-lookup"><span data-stu-id="da9a2-122">Custom</span></span>

<span data-ttu-id="da9a2-123">Till exempel, när utdata från ett `Get-ChildItem` kommando är skickas till ett `Format-List` kommando, `Format-List` använder listvyn som definierats i käll koden för att avgöra hur fil-och mappobjekt ska visas som en lista.</span><span class="sxs-lookup"><span data-stu-id="da9a2-123">For example, when the output of a `Get-ChildItem` command is piped to a `Format-List` command, `Format-List` uses the list view defined in the source code to determine how to display the file and folder objects as a list.</span></span>

<span data-ttu-id="da9a2-124">När en format fil innehåller mer än en vy av ett objekt, tillämpar PowerShell den första vyn som hittas.</span><span class="sxs-lookup"><span data-stu-id="da9a2-124">When a formatting file includes more than one view of an object, PowerShell applies the first view that it finds.</span></span>

<span data-ttu-id="da9a2-125">I en anpassad `Format.ps1xml` fil definieras en vy av en uppsättning XML-taggar som beskriver namnet på vyn, vilken typ av objekt som kan användas, kolumn rubriker och de egenskaper som visas i bröd texten i vyn.</span><span class="sxs-lookup"><span data-stu-id="da9a2-125">In a custom `Format.ps1xml` file, a view is defined by a set of XML tags that describe the name of the view, the type of object to which it can be applied, the column headers, and the properties that are displayed in the body of the view.</span></span> <span data-ttu-id="da9a2-126">Formatet i `Format.ps1xml` filer tillämpas precis innan data visas för användaren.</span><span class="sxs-lookup"><span data-stu-id="da9a2-126">The format in `Format.ps1xml` files is applied just before the data is presented to the user.</span></span>

## <a name="creating-new-formatps1xml-files"></a><span data-ttu-id="da9a2-127">Skapa nya Format.ps1XML-filer</span><span class="sxs-lookup"><span data-stu-id="da9a2-127">Creating new Format.ps1xml files</span></span>

<span data-ttu-id="da9a2-128">Om du vill ändra visnings formatet för en befintlig objekt vy, eller lägga till vyer för nya objekt, skapar du dina egna `Format.ps1xml` filer och lägger sedan till dem i PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="da9a2-128">To change the display format of an existing object view, or to add views for new objects, create your own `Format.ps1xml` files, and then add them to your PowerShell session.</span></span>

<span data-ttu-id="da9a2-129">Om du vill skapa en `Format.ps1xml` fil för att definiera en anpassad vy använder du cmdletarna [Get-FormatData](xref:Microsoft.PowerShell.Utility.Get-FormatData) och [export-FormatData](xref:Microsoft.PowerShell.Utility.Export-FormatData) .</span><span class="sxs-lookup"><span data-stu-id="da9a2-129">To create a `Format.ps1xml` file to define a custom view, use the [Get-FormatData](xref:Microsoft.PowerShell.Utility.Get-FormatData) and [Export-FormatData](xref:Microsoft.PowerShell.Utility.Export-FormatData) cmdlets.</span></span> <span data-ttu-id="da9a2-130">Använd en text redigerare för att redigera filen.</span><span class="sxs-lookup"><span data-stu-id="da9a2-130">Use a text editor to edit the file.</span></span> <span data-ttu-id="da9a2-131">Filen kan sparas till alla kataloger som PowerShell har åtkomst till, till exempel en under katalog till `$HOME` .</span><span class="sxs-lookup"><span data-stu-id="da9a2-131">The file can be saved to any directory that PowerShell can access, such as a subdirectory of `$HOME`.</span></span>

<span data-ttu-id="da9a2-132">Om du vill ändra formateringen för en aktuell vy letar du upp vyn i format filen och använder sedan taggarna för att ändra vyn.</span><span class="sxs-lookup"><span data-stu-id="da9a2-132">To change the formatting of a current view, locate the view in the formatting file, and then use the tags to change the view.</span></span> <span data-ttu-id="da9a2-133">Skapa en vy för en ny objekt typ genom att skapa en ny vy eller använda en befintlig vy som en modell.</span><span class="sxs-lookup"><span data-stu-id="da9a2-133">To create a view for a new object type, create a new view, or use an existing view as a model.</span></span> <span data-ttu-id="da9a2-134">Taggarna beskrivs i nästa avsnitt.</span><span class="sxs-lookup"><span data-stu-id="da9a2-134">The tags are described in the next section.</span></span> <span data-ttu-id="da9a2-135">Du kan sedan ta bort alla andra vyer i filen så att ändringarna är uppenbara för alla som granskar filen.</span><span class="sxs-lookup"><span data-stu-id="da9a2-135">You can then delete all the other views in the file so that the changes are obvious to anyone examining the file.</span></span>

<span data-ttu-id="da9a2-136">När du har sparat ändringarna använder du [Update-FormatData](xref:Microsoft.PowerShell.Utility.Update-FormatData) för att lägga till den nya filen i PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="da9a2-136">After you save the changes, use the [Update-FormatData](xref:Microsoft.PowerShell.Utility.Update-FormatData) to add the new file to your PowerShell session.</span></span> <span data-ttu-id="da9a2-137">Om du vill att vyn ska prioriteras över en vy som definierats i de inbyggda filerna använder du parametern **PrependPath** .</span><span class="sxs-lookup"><span data-stu-id="da9a2-137">If you want your view to take precedence over a view defined in the built-in files, use the **PrependPath** parameter.</span></span> <span data-ttu-id="da9a2-138">`Update-FormatData` påverkar endast den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="da9a2-138">`Update-FormatData` affects only the current session.</span></span> <span data-ttu-id="da9a2-139">Om du vill göra ändringen i alla framtida sessioner lägger du till `Update-FormatData` kommandot i din PowerShell-profil.</span><span class="sxs-lookup"><span data-stu-id="da9a2-139">To make the change to all future sessions, add the `Update-FormatData` command to your PowerShell profile.</span></span>

### <a name="example-add-calendar-data-to-culture-objects"></a><span data-ttu-id="da9a2-140">Exempel: Lägg till kalender data till kultur objekt</span><span class="sxs-lookup"><span data-stu-id="da9a2-140">Example: Add calendar data to culture objects</span></span>

<span data-ttu-id="da9a2-141">Det här exemplet visar hur du ändrar formateringen för kultur objekt **system. globalisering. CultureInfo** som genereras av `Get-Culture` cmdleten i den aktuella PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="da9a2-141">This example shows how to change the formatting of the culture objects **System.Globalization.CultureInfo** generated by the `Get-Culture` cmdlet in the current PowerShell session.</span></span> <span data-ttu-id="da9a2-142">Kommandona i exemplet lägger till **kalender** egenskapen i standardvyn visning av kultur objekt.</span><span class="sxs-lookup"><span data-stu-id="da9a2-142">The commands in the example add the **Calendar** property to the default table view display of culture objects.</span></span>

<span data-ttu-id="da9a2-143">Börja med att hämta format data från käll kods filen och skapa en `Format.ps1xml` fil som innehåller den aktuella vyn av kultur objekt.</span><span class="sxs-lookup"><span data-stu-id="da9a2-143">To begin, get the format data from the source code file and create a `Format.ps1xml` file that contains the current view of the culture objects.</span></span>

```powershell
Get-FormatData -TypeName System.Globalization.CultureInfo |
  Export-FormatData -Path $HOME\Format\CultureInfo.Format.ps1xml
```

<span data-ttu-id="da9a2-144">Öppna `CultureInfo.Format.ps1xml` filen i valfri XML-eller text redigerare, t. ex. Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="da9a2-144">Open the `CultureInfo.Format.ps1xml` file in any XML or text editor, such as Visual Studio Code.</span></span> <span data-ttu-id="da9a2-145">Följande XML definierar vyerna för **CultureInfo** -objektet.</span><span class="sxs-lookup"><span data-stu-id="da9a2-145">The following XML defines the views of the **CultureInfo** object.</span></span>

<span data-ttu-id="da9a2-146">`CultureInfo.Format.ps1xml`Filen bör se ut som i följande exempel:</span><span class="sxs-lookup"><span data-stu-id="da9a2-146">The `CultureInfo.Format.ps1xml` file should look like the following sample:</span></span>

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

<span data-ttu-id="da9a2-147">Skapa en ny kolumn för **kalender** egenskapen genom att lägga till en ny uppsättning `<TableColumnHeader>` taggar.</span><span class="sxs-lookup"><span data-stu-id="da9a2-147">Create a new column for the **Calendar** property by adding a new set of `<TableColumnHeader>` tags.</span></span> <span data-ttu-id="da9a2-148">Värdet för egenskapen **Calendar** kan vara Long, så ange ett värde på 45 tecken som `<Width>` .</span><span class="sxs-lookup"><span data-stu-id="da9a2-148">The value of the **Calendar** property can be long, so specify a value of 45 characters as the `<Width>`.</span></span>

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

<span data-ttu-id="da9a2-149">Lägg till ett nytt kolumn objekt för **kalender** i tabell rader med `<TableColumnItem>` `<PropertyName` taggarna och:</span><span class="sxs-lookup"><span data-stu-id="da9a2-149">Add a new column item for **Calendar** in the table rows using the `<TableColumnItem>` and `<PropertyName` tags:</span></span>

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

<span data-ttu-id="da9a2-150">Spara och stäng filen.</span><span class="sxs-lookup"><span data-stu-id="da9a2-150">Save and close the file.</span></span> <span data-ttu-id="da9a2-151">Använd `Update-FormatData` för att lägga till den nya format filen i den aktuella PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="da9a2-151">Use `Update-FormatData` to add the new format file to the current PowerShell session.</span></span>

<span data-ttu-id="da9a2-152">I det här exemplet används parametern **PrependPath** för att placera den nya filen i en högre prioritets ordning än den ursprungliga filen.</span><span class="sxs-lookup"><span data-stu-id="da9a2-152">This example uses the **PrependPath** parameter to place the new file in a higher precedence order than the original file.</span></span> <span data-ttu-id="da9a2-153">Mer information finns i [Update-FormatData](xref:Microsoft.PowerShell.Utility.Update-FormatData).</span><span class="sxs-lookup"><span data-stu-id="da9a2-153">For more information, see [Update-FormatData](xref:Microsoft.PowerShell.Utility.Update-FormatData).</span></span>

```powershell
Update-FormatData -PrependPath $HOME\Format\CultureInfo.Format.ps1xml
```

<span data-ttu-id="da9a2-154">Testa ändringen genom att skriva `Get-Culture` och granska utdata som innehåller **kalender** egenskapen.</span><span class="sxs-lookup"><span data-stu-id="da9a2-154">To test the change, type `Get-Culture` and review the output that includes the **Calendar** property.</span></span>

```powershell
Get-Culture
```

```Output
LCID  Name   Calendar                                DisplayName
----  ----   --------                                -----------
1033  en-US  System.Globalization.GregorianCalendar  English (United States)
```

## <a name="the-xml-in-formatps1xml-files"></a><span data-ttu-id="da9a2-155">XML i Format.ps1XML-filer</span><span class="sxs-lookup"><span data-stu-id="da9a2-155">The XML in Format.ps1xml files</span></span>

<span data-ttu-id="da9a2-156">Du hittar fullständig schema definition i [formatet. xsd](https://github.com/PowerShell/PowerShell/blob/master/src/Schemas/Format.xsd) i PowerShell-källkoden på GitHub.</span><span class="sxs-lookup"><span data-stu-id="da9a2-156">The full schema definition can be found in [Format.xsd](https://github.com/PowerShell/PowerShell/blob/master/src/Schemas/Format.xsd) in the PowerShell source code repository on GitHub.</span></span>

<span data-ttu-id="da9a2-157">Avsnittet **ViewDefinitions** i varje `Format.ps1xml` fil innehåller de `<View>` taggar som definierar varje vy.</span><span class="sxs-lookup"><span data-stu-id="da9a2-157">The **ViewDefinitions** section of each `Format.ps1xml` file contains the `<View>` tags that define each view.</span></span> <span data-ttu-id="da9a2-158">En typisk `<View>` tagg innehåller följande Taggar:</span><span class="sxs-lookup"><span data-stu-id="da9a2-158">A typical `<View>` tag includes the following tags:</span></span>

- <span data-ttu-id="da9a2-159">`<Name>` identifierar namnet på vyn.</span><span class="sxs-lookup"><span data-stu-id="da9a2-159">`<Name>` identifies the name of the view.</span></span>
- <span data-ttu-id="da9a2-160">`<ViewSelectedBy>` anger objekt typen eller typerna som vyn gäller för.</span><span class="sxs-lookup"><span data-stu-id="da9a2-160">`<ViewSelectedBy>` specifies the object type or types to which the view applies.</span></span>
- <span data-ttu-id="da9a2-161">`<GroupBy>` anger hur objekt i vyn ska kombineras i grupper.</span><span class="sxs-lookup"><span data-stu-id="da9a2-161">`<GroupBy>` specifies how items in the view will be combined in groups.</span></span>
- <span data-ttu-id="da9a2-162">`<TableControl>`, `<ListControl>` , `<WideControl>` och `<CustomControl>` innehåller taggarna som anger hur varje objekt ska visas.</span><span class="sxs-lookup"><span data-stu-id="da9a2-162">`<TableControl>`, `<ListControl>`, `<WideControl>`, and `<CustomControl>` contain the tags that specify how each item will be displayed.</span></span>

### <a name="viewselectedby-tag"></a><span data-ttu-id="da9a2-163">ViewSelectedBy-tagg</span><span class="sxs-lookup"><span data-stu-id="da9a2-163">ViewSelectedBy tag</span></span>

<span data-ttu-id="da9a2-164">`<ViewSelectedBy>`Taggen kan innehålla en `<TypeName>` tagg för varje objekt typ som vyn gäller för.</span><span class="sxs-lookup"><span data-stu-id="da9a2-164">The `<ViewSelectedBy>` tag can contain a `<TypeName>` tag for each object type to which the view applies.</span></span> <span data-ttu-id="da9a2-165">Eller så kan den innehålla en `<SelectionSetName>` tagg som refererar till en urvals uppsättning som definieras någon annan stans genom att använda en- `<SelectionSet>` tagg.</span><span class="sxs-lookup"><span data-stu-id="da9a2-165">Or, it can contain a `<SelectionSetName>` tag that references a selection set that is defined elsewhere by using a `<SelectionSet>` tag.</span></span>

### <a name="groupby-tag"></a><span data-ttu-id="da9a2-166">GroupBy-tagg</span><span class="sxs-lookup"><span data-stu-id="da9a2-166">GroupBy tag</span></span>

<span data-ttu-id="da9a2-167">`<GroupBy>`Taggen innehåller en `<PropertyName>` tagg som anger den objekt egenskap enligt vilken objekten ska grupperas.</span><span class="sxs-lookup"><span data-stu-id="da9a2-167">The `<GroupBy>` tag contains a `<PropertyName>` tag that specifies the object property by which items are to be grouped.</span></span> <span data-ttu-id="da9a2-168">Den innehåller också antingen en `<Label>` tagg som anger en sträng som ska användas som en etikett för varje grupp eller en `<CustomControlName>` tagg som refererar till en anpassad kontroll som definierats någon annan stans med en `<Control>` tagg.</span><span class="sxs-lookup"><span data-stu-id="da9a2-168">It also contains either a `<Label>` tag that specifies a string to be used as a label for each group or a `<CustomControlName>` tag that references a custom control defined elsewhere using a `<Control>` tag.</span></span> <span data-ttu-id="da9a2-169">`<Control>`Taggen innehåller en `<Name>` tagg och en `<CustomControl>` tagg.</span><span class="sxs-lookup"><span data-stu-id="da9a2-169">The `<Control>` tag contains a `<Name>` tag and a `<CustomControl>` tag.</span></span>

### <a name="tablecontroltag"></a><span data-ttu-id="da9a2-170">TableControlTag</span><span class="sxs-lookup"><span data-stu-id="da9a2-170">TableControlTag</span></span>

<span data-ttu-id="da9a2-171">`<TableControl>`Taggen innehåller vanligt vis `<TableHeaders>` och `<TableRowEntries>` taggar som definierar formateringen för tabellens huvuden och rader.</span><span class="sxs-lookup"><span data-stu-id="da9a2-171">The `<TableControl>` tag typically contains `<TableHeaders>` and `<TableRowEntries>` tags that define the formatting for the table's heads and rows.</span></span> <span data-ttu-id="da9a2-172">`<TableHeaders>`Taggen innehåller vanligt vis `<TableColumnHeader>` taggar som innehåller `<Label>` `<Width>` taggar, och `<Alignment>` .</span><span class="sxs-lookup"><span data-stu-id="da9a2-172">The `<TableHeaders>` tag typically contains `<TableColumnHeader>` tags that contain `<Label>`, `<Width>`, and `<Alignment>` tags.</span></span> <span data-ttu-id="da9a2-173">`<TableRowEntries>`Taggen innehåller `<TableRowEntry>` taggar för varje rad i tabellen.</span><span class="sxs-lookup"><span data-stu-id="da9a2-173">The `<TableRowEntries>` tag contains `<TableRowEntry>` tags for each row in the table.</span></span> <span data-ttu-id="da9a2-174">`<TableRowEntry>`Taggen innehåller en `<TableColumnItems>` tagg som innehåller en `<TableColumnItem>` tagg för varje kolumn på raden.</span><span class="sxs-lookup"><span data-stu-id="da9a2-174">The `<TableRowEntry>` tag contains a `<TableColumnItems>` tag that contains a `<TableColumnItem>` tag for each column in the row.</span></span> <span data-ttu-id="da9a2-175">Normalt `<TableColumnItem>` innehåller taggen en `<PropertyName>` tagg som identifierar objekt egenskapen som ska visas på den definierade platsen, eller en `<ScriptBlock>` tagg som innehåller skript kod som beräknar ett resultat som ska visas på platsen.</span><span class="sxs-lookup"><span data-stu-id="da9a2-175">Typically, the `<TableColumnItem>` tag contains either a `<PropertyName>` tag that identifies the object property to be displayed in the defined location, or a `<ScriptBlock>` tag that contains script code that calculates a result that is to be displayed in the location.</span></span>

> [!NOTE]
> <span data-ttu-id="da9a2-176">Skript block kan också användas på andra platser på platser där beräknade resultat kan vara användbara.</span><span class="sxs-lookup"><span data-stu-id="da9a2-176">Script blocks can also be used elsewhere in locations where calculated results can be useful.</span></span>

<span data-ttu-id="da9a2-177">`<TableColumnItem>`Taggen kan också innehålla en `<FormatString>` tagg som anger hur egenskapen eller de beräknade resultaten ska visas.</span><span class="sxs-lookup"><span data-stu-id="da9a2-177">The `<TableColumnItem>` tag can also contain a `<FormatString>` tag that specifies how the property or the calculated results will be displayed.</span></span>

### <a name="listcontrol-tag"></a><span data-ttu-id="da9a2-178">ListControl-tagg</span><span class="sxs-lookup"><span data-stu-id="da9a2-178">ListControl tag</span></span>

<span data-ttu-id="da9a2-179">`<ListControl>`Taggen innehåller vanligt vis en `<ListEntries>` tagg.</span><span class="sxs-lookup"><span data-stu-id="da9a2-179">The `<ListControl>` tag typically contains a `<ListEntries>` tag.</span></span> <span data-ttu-id="da9a2-180">`<ListEntries>`Taggen innehåller en `<ListEntry>` tagg.</span><span class="sxs-lookup"><span data-stu-id="da9a2-180">The `<ListEntries>` tag contains a `<ListEntry>` tag.</span></span> <span data-ttu-id="da9a2-181">`<ListEntry>`Taggen innehåller en `<ListItems>` tagg.</span><span class="sxs-lookup"><span data-stu-id="da9a2-181">The `<ListEntry>` tag contains a `<ListItems>` tag.</span></span> <span data-ttu-id="da9a2-182">`<ListItems>`Taggen innehåller `<ListItem>` taggar som innehåller `<PropertyName>` taggar.</span><span class="sxs-lookup"><span data-stu-id="da9a2-182">The `<ListItems>` tag contains `<ListItem>` tags, which contain `<PropertyName>` tags.</span></span> <span data-ttu-id="da9a2-183">`<PropertyName>`Taggarna anger vilken objekt egenskap som ska visas på den angivna platsen i listan.</span><span class="sxs-lookup"><span data-stu-id="da9a2-183">The `<PropertyName>` tags specify the object property to be displayed at the specified location in the list.</span></span> <span data-ttu-id="da9a2-184">Om visnings valet definieras med en urvals uppsättning `<ListControl>` `<ListEntry>` kan taggarna och också innehålla en `<EntrySelectedBy>` tagg som innehåller en eller flera `<TypeName>` taggar.</span><span class="sxs-lookup"><span data-stu-id="da9a2-184">If the view selection is defined using a selection set, the `<ListControl>` and `<ListEntry>` tags can also contain an `<EntrySelectedBy>` tag that contains one or more `<TypeName>` tags.</span></span> <span data-ttu-id="da9a2-185">`<TypeName>`Taggarna anger vilken objekt typ `<ListControl>` taggen är avsedd att visa.</span><span class="sxs-lookup"><span data-stu-id="da9a2-185">These `<TypeName>` tags specify the object type that the `<ListControl>` tag is intended to display.</span></span>

### <a name="widecontrol-tag"></a><span data-ttu-id="da9a2-186">WideControl-tagg</span><span class="sxs-lookup"><span data-stu-id="da9a2-186">WideControl tag</span></span>

<span data-ttu-id="da9a2-187">`<WideControl>`Taggen innehåller vanligt vis en `<WideEntries>` tagg.</span><span class="sxs-lookup"><span data-stu-id="da9a2-187">The `<WideControl>` tag typically contains a `<WideEntries>` tag.</span></span> <span data-ttu-id="da9a2-188">`<WideEntries>`Taggen innehåller en eller flera `<WideEntry>` taggar.</span><span class="sxs-lookup"><span data-stu-id="da9a2-188">The `<WideEntries>` tag contains one or more `<WideEntry>` tags.</span></span> <span data-ttu-id="da9a2-189">En- `<WideEntry>` tagg innehåller vanligt vis en `<PropertyName>` tagg som anger den egenskap som ska visas på den angivna platsen i vyn.</span><span class="sxs-lookup"><span data-stu-id="da9a2-189">A `<WideEntry>` tag typically contains a `<PropertyName>` tag that specifies the property to be displayed at the specified location in the view.</span></span> <span data-ttu-id="da9a2-190">`<PropertyName>`Taggen kan innehålla en `<FormatString>` tagg som anger hur egenskapen ska visas.</span><span class="sxs-lookup"><span data-stu-id="da9a2-190">The `<PropertyName>` tag can contain a `<FormatString>` tag that specifies how the property is to be displayed.</span></span>

### <a name="customcontrol-tag"></a><span data-ttu-id="da9a2-191">CustomControl-tagg</span><span class="sxs-lookup"><span data-stu-id="da9a2-191">CustomControl tag</span></span>

<span data-ttu-id="da9a2-192">Med `<CustomControl>` taggen kan du definiera ett format genom att använda ett-skript block.</span><span class="sxs-lookup"><span data-stu-id="da9a2-192">The `<CustomControl>` tag lets you use a script block to define a format.</span></span> <span data-ttu-id="da9a2-193">En- `<CustomControl>` tagg innehåller vanligt vis en `<CustomEntries>` tagg som innehåller flera `<CustomEntry>` taggar.</span><span class="sxs-lookup"><span data-stu-id="da9a2-193">A `<CustomControl>` tag typically contains a `<CustomEntries>` tag that contains multiple `<CustomEntry>` tags.</span></span> <span data-ttu-id="da9a2-194">Varje- `<CustomEntry>` tagg innehåller en `<CustomItem>` tagg som kan innehålla en rad olika taggar som anger innehåll och formatering för den angivna platsen i vyn, inklusive `<Text>` , `<Indentation>` , `<ExpressionBinding>` och `<NewLine>` taggar.</span><span class="sxs-lookup"><span data-stu-id="da9a2-194">Each `<CustomEntry>` tag contains a `<CustomItem>` tag that can contain a variety of tags that specify contents and formatting of the specified location in the view, including `<Text>`, `<Indentation>`, `<ExpressionBinding>`, and `<NewLine>` tags.</span></span>

## <a name="tracing-formatps1xml-file-use"></a><span data-ttu-id="da9a2-195">Använda spårning Format.ps1XML-fil</span><span class="sxs-lookup"><span data-stu-id="da9a2-195">Tracing Format.ps1xml file use</span></span>

<span data-ttu-id="da9a2-196">Om du vill identifiera fel vid inläsning eller tillämpning av `Format.ps1xml` filer använder du `Trace-Command` cmdleten med någon av följande format komponenter som värde för parametern **Name** :</span><span class="sxs-lookup"><span data-stu-id="da9a2-196">To detect errors in the loading or application of `Format.ps1xml` files, use the `Trace-Command` cmdlet with any of the following format components as the value of the **Name** parameter:</span></span>

- <span data-ttu-id="da9a2-197">FormatFileLoading</span><span class="sxs-lookup"><span data-stu-id="da9a2-197">FormatFileLoading</span></span>
- <span data-ttu-id="da9a2-198">FormatViewBinding</span><span class="sxs-lookup"><span data-stu-id="da9a2-198">FormatViewBinding</span></span>

<span data-ttu-id="da9a2-199">Mer information finns i [trace-Command](xref:Microsoft.PowerShell.Utility.Trace-Command) och [Get-TraceSource](xref:Microsoft.PowerShell.Utility.Get-TraceSource).</span><span class="sxs-lookup"><span data-stu-id="da9a2-199">For more information, see [Trace-Command](xref:Microsoft.PowerShell.Utility.Trace-Command) and [Get-TraceSource](xref:Microsoft.PowerShell.Utility.Get-TraceSource).</span></span>

## <a name="signing-a-formatps1xml-file"></a><span data-ttu-id="da9a2-200">Signera en Format.ps1XML-fil</span><span class="sxs-lookup"><span data-stu-id="da9a2-200">Signing a Format.ps1xml file</span></span>

<span data-ttu-id="da9a2-201">Du skyddar användare av `Format.ps1xml` filen genom att signera filen med en digital signatur.</span><span class="sxs-lookup"><span data-stu-id="da9a2-201">To protect the users of your `Format.ps1xml` file, sign the file using a digital signature.</span></span> <span data-ttu-id="da9a2-202">Mer information finns i [about_Signing](about_Signing.md).</span><span class="sxs-lookup"><span data-stu-id="da9a2-202">For more information, see [about_Signing](about_Signing.md).</span></span>

## <a name="sample-xml-for-a-format-table-custom-view"></a><span data-ttu-id="da9a2-203">Exempel-XML för en Format-Table anpassad vy</span><span class="sxs-lookup"><span data-stu-id="da9a2-203">Sample XML for a Format-Table custom view</span></span>

<span data-ttu-id="da9a2-204">Följande XML-exempel skapar en `Format-Table` anpassad vy för objekten **system. io. DirectoryInfo** och **system. io. fileinfo** som skapats av `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="da9a2-204">The following XML sample creates a `Format-Table` custom view for the **System.IO.DirectoryInfo** and **System.IO.FileInfo** objects created by `Get-ChildItem`.</span></span> <span data-ttu-id="da9a2-205">Den anpassade vyn heter **mygciview** och lägger till **CreationTime** -kolumnen i tabellen.</span><span class="sxs-lookup"><span data-stu-id="da9a2-205">The custom view is named **mygciview** and adds the **CreationTime** column to the table.</span></span>

<span data-ttu-id="da9a2-206">Skapa en anpassad vy genom att använda `Get-FormatData` `Export-FormatData` cmdletarna och för att generera en `.ps1xml` fil.</span><span class="sxs-lookup"><span data-stu-id="da9a2-206">To create the custom view, use the `Get-FormatData` and `Export-FormatData` cmdlets to generate a `.ps1xml` file.</span></span> <span data-ttu-id="da9a2-207">Redigera sedan `.ps1xml` filen och skapa koden för den anpassade vyn.</span><span class="sxs-lookup"><span data-stu-id="da9a2-207">Then, edit your `.ps1xml` file to create the code for your custom view.</span></span> <span data-ttu-id="da9a2-208">`.ps1xml`Filen kan lagras i valfri katalog som PowerShell kan komma åt.</span><span class="sxs-lookup"><span data-stu-id="da9a2-208">The `.ps1xml` file can be stored in any directory that PowerShell can access.</span></span> <span data-ttu-id="da9a2-209">Till exempel en under katalog till `$HOME` .</span><span class="sxs-lookup"><span data-stu-id="da9a2-209">For example, a subdirectory of `$HOME`.</span></span>

<span data-ttu-id="da9a2-210">När `.ps1xml` filen har skapats använder du `Update-FormatData` cmdleten för att inkludera vyn i den aktuella PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="da9a2-210">After the `.ps1xml` file is created, use the `Update-FormatData` cmdlet to include the view in the current PowerShell session.</span></span> <span data-ttu-id="da9a2-211">Eller Lägg till kommandot Update i din PowerShell-profil om du behöver vyn tillgänglig i alla PowerShell-sessioner.</span><span class="sxs-lookup"><span data-stu-id="da9a2-211">Or, add the update command to your PowerShell profile if you need the view available in all PowerShell sessions.</span></span>

<span data-ttu-id="da9a2-212">I det här exemplet måste den anpassade vyn använda tabell formatet, annars `Format-Table` Miss lyckas.</span><span class="sxs-lookup"><span data-stu-id="da9a2-212">For this example, the custom view must use the table format, otherwise, `Format-Table` fails.</span></span>

<span data-ttu-id="da9a2-213">Använd `Format-Table` med parametern **View** för att ange den anpassade vyns namn, **mygciview** och formatera tabellens utdata med kolumnen **CreationTime** .</span><span class="sxs-lookup"><span data-stu-id="da9a2-213">Use `Format-Table` with the **View** parameter to specify the custom view's name, **mygciview**, and format the table's output with the **CreationTime** column.</span></span> <span data-ttu-id="da9a2-214">Ett exempel på hur kommandot körs finns i [Format-Table](xref:Microsoft.PowerShell.Utility.Format-Table).</span><span class="sxs-lookup"><span data-stu-id="da9a2-214">For an example of how the command is run, see [Format-Table](xref:Microsoft.PowerShell.Utility.Format-Table).</span></span>

> [!NOTE]
> <span data-ttu-id="da9a2-215">Även om du kan hämta XML-formatering från käll koden för att skapa en anpassad vy, kan det krävas mer utveckling för att få önskat resultat.</span><span class="sxs-lookup"><span data-stu-id="da9a2-215">Although you can get the formatting XML from the source code to create a custom view, more development might be needed to get the desired result.</span></span>

<span data-ttu-id="da9a2-216">I följande `Get-FormatData` kommando finns ett alternativ för parametern **PowerShellVersion** för att se till att all lokal formateringsinformation returneras.</span><span class="sxs-lookup"><span data-stu-id="da9a2-216">In the following `Get-FormatData` command, there's an alternative for the **PowerShellVersion** parameter to ensure that all local formatting information is returned.</span></span> <span data-ttu-id="da9a2-217">Använd `-PowerShellVersion $PSVersionTable.PSVersion` snarare än en angiven PowerShell-version.</span><span class="sxs-lookup"><span data-stu-id="da9a2-217">Use `-PowerShellVersion $PSVersionTable.PSVersion` rather than a specific PowerShell version.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="da9a2-218">Se även</span><span class="sxs-lookup"><span data-stu-id="da9a2-218">See also</span></span>

[<span data-ttu-id="da9a2-219">Exportera – FormatData</span><span class="sxs-lookup"><span data-stu-id="da9a2-219">Export-FormatData</span></span>](xref:Microsoft.PowerShell.Utility.Export-FormatData)

[<span data-ttu-id="da9a2-220">Get-FormatData</span><span class="sxs-lookup"><span data-stu-id="da9a2-220">Get-FormatData</span></span>](xref:Microsoft.PowerShell.Utility.Get-FormatData)

[<span data-ttu-id="da9a2-221">Get-TraceSource</span><span class="sxs-lookup"><span data-stu-id="da9a2-221">Get-TraceSource</span></span>](xref:Microsoft.PowerShell.Utility.Get-TraceSource)

[<span data-ttu-id="da9a2-222">XML-referens för formatschema</span><span class="sxs-lookup"><span data-stu-id="da9a2-222">Format Schema XML Reference</span></span>](/powershell/scripting/developer/format/format-schema-xml-reference)

[<span data-ttu-id="da9a2-223">Spåra-kommando</span><span class="sxs-lookup"><span data-stu-id="da9a2-223">Trace-Command</span></span>](xref:Microsoft.PowerShell.Utility.Trace-Command)

[<span data-ttu-id="da9a2-224">Uppdatera – FormatData</span><span class="sxs-lookup"><span data-stu-id="da9a2-224">Update-FormatData</span></span>](xref:Microsoft.PowerShell.Utility.Update-FormatData)

[<span data-ttu-id="da9a2-225">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="da9a2-225">Writing a PowerShell Formatting File</span></span>](/powershell/scripting/developer/format/writing-a-powershell-formatting-file)
