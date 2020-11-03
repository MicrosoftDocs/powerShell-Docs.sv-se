---
description: '`Format.ps1xml`Filerna i PowerShell definierar standard visningen av objekt i PowerShell-konsolen. Du kan skapa egna `Format.ps1xml` filer om du vill ändra visningen av objekt eller definiera standard visning för nya objekt typer som du skapar i PowerShell.'
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_format.ps1xml?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Format.ps1XML
ms.openlocfilehash: be88007d23ab98b9c2f707b77f9c43578ba9887b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93271593"
---
# <a name="about-formatps1xml"></a><span data-ttu-id="4d303-105">Om Format.ps1XML</span><span class="sxs-lookup"><span data-stu-id="4d303-105">About Format.ps1xml</span></span>

## <a name="short-description"></a><span data-ttu-id="4d303-106">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="4d303-106">Short description</span></span>

<span data-ttu-id="4d303-107">`Format.ps1xml`Filerna i PowerShell definierar standard visningen av objekt i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="4d303-107">The `Format.ps1xml` files in PowerShell define the default display of objects in the PowerShell console.</span></span> <span data-ttu-id="4d303-108">Du kan skapa egna `Format.ps1xml` filer om du vill ändra visningen av objekt eller definiera standard visning för nya objekt typer som du skapar i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4d303-108">You can create your own `Format.ps1xml` files to change the display of objects or to define default displays for new object types that you create in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="4d303-109">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="4d303-109">Long description</span></span>

<span data-ttu-id="4d303-110">`Format.ps1xml`Filerna i PowerShell definierar standard visningen av objekt i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4d303-110">The `Format.ps1xml` files in PowerShell define the default display of objects in PowerShell.</span></span> <span data-ttu-id="4d303-111">Du kan skapa egna `Format.ps1xml` filer om du vill ändra visningen av objekt eller definiera standard visning för nya objekt typer som du skapar i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4d303-111">You can create your own `Format.ps1xml` files to change the display of objects or to define default displays for new object types that you create in PowerShell.</span></span>

<span data-ttu-id="4d303-112">När PowerShell visar ett objekt används data i strukturerade formateringsattribut för att fastställa standard visningen av objektet.</span><span class="sxs-lookup"><span data-stu-id="4d303-112">When PowerShell displays an object, it uses the data in structured formatting files to determine the default display of the object.</span></span> <span data-ttu-id="4d303-113">Data i formateringsattribut bestämmer om objektet återges i en tabell eller i en lista och avgör vilka egenskaper som visas som standard.</span><span class="sxs-lookup"><span data-stu-id="4d303-113">The data in the formatting files determines whether the object is rendered in a table or in a list, and it determines which properties are displayed by default.</span></span>

<span data-ttu-id="4d303-114">Formateringen påverkar endast visningen.</span><span class="sxs-lookup"><span data-stu-id="4d303-114">The formatting affects the display only.</span></span> <span data-ttu-id="4d303-115">Det påverkar inte vilka objekt egenskaper som har passerat pipelinen eller hur de skickas.</span><span class="sxs-lookup"><span data-stu-id="4d303-115">It doesn't affect which object properties are passed down the pipeline or how they're passed.</span></span> <span data-ttu-id="4d303-116">`Format.ps1xml` Det går inte att använda filer för att anpassa utdataformatet för hash-tabeller.</span><span class="sxs-lookup"><span data-stu-id="4d303-116">`Format.ps1xml` files can't be used to customize the output format for hash tables.</span></span>

<span data-ttu-id="4d303-117">PowerShell innehåller sju filer.</span><span class="sxs-lookup"><span data-stu-id="4d303-117">PowerShell includes seven formatting files.</span></span> <span data-ttu-id="4d303-118">De här filerna finns i installations katalogen ( `$PSHOME` ).</span><span class="sxs-lookup"><span data-stu-id="4d303-118">These files are located in the installation directory (`$PSHOME`).</span></span> <span data-ttu-id="4d303-119">Varje fil definierar visningen av en grupp Microsoft .NET Ramverks objekt:</span><span class="sxs-lookup"><span data-stu-id="4d303-119">Each file defines the display of a group of Microsoft .NET Framework objects:</span></span>

1. `Certificate.Format.ps1xml`

   <span data-ttu-id="4d303-120">Objekt i certifikat arkivet, till exempel X. 509-certifikat och certifikat arkiv.</span><span class="sxs-lookup"><span data-stu-id="4d303-120">Objects in the Certificate store, such as X.509 certificates and certificate stores.</span></span>

1. `DotNetTypes.Format.ps1xml`

   <span data-ttu-id="4d303-121">Andra .NET Framework typer, till exempel CultureInfo, FileVersionInfo och EventLogEntry-objekt.</span><span class="sxs-lookup"><span data-stu-id="4d303-121">Other .NET Framework types, such as CultureInfo, FileVersionInfo, and EventLogEntry objects.</span></span>

1. `FileSystem.Format.ps1xml`

   <span data-ttu-id="4d303-122">Fil system objekt, till exempel filer och kataloger.</span><span class="sxs-lookup"><span data-stu-id="4d303-122">File system objects, such as files and directories.</span></span>

1. `Help.Format.ps1xml`

   <span data-ttu-id="4d303-123">Hjälp vyer, till exempel detaljerade och fullständiga vyer, parametrar och exempel.</span><span class="sxs-lookup"><span data-stu-id="4d303-123">Help views, such as detailed and full views, parameters, and examples.</span></span>

1. `PowerShellCore.Format.ps1xml`

   <span data-ttu-id="4d303-124">Objekt som har genererats av PowerShell Core-cmdletar, till exempel `Get-Member` och `Get-History` .</span><span class="sxs-lookup"><span data-stu-id="4d303-124">Objects generated by PowerShell core cmdlets, such as `Get-Member` and `Get-History`.</span></span>

1. `PowerShellTrace.Format.ps1xml`

   <span data-ttu-id="4d303-125">Spåra objekt, till exempel de som genereras av `Trace-Command` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="4d303-125">Trace objects, such as those generated by the `Trace-Command` cmdlet.</span></span>

1. `Registry.Format.ps1xml`

   <span data-ttu-id="4d303-126">Register objekt, till exempel nycklar och poster.</span><span class="sxs-lookup"><span data-stu-id="4d303-126">Registry objects, such as keys and entries.</span></span>

<span data-ttu-id="4d303-127">En format fil kan definiera fyra olika vyer för varje objekt:</span><span class="sxs-lookup"><span data-stu-id="4d303-127">A formatting file can define four different views of each object:</span></span>

- <span data-ttu-id="4d303-128">Tabeller</span><span class="sxs-lookup"><span data-stu-id="4d303-128">Table</span></span>
- <span data-ttu-id="4d303-129">Lista</span><span class="sxs-lookup"><span data-stu-id="4d303-129">List</span></span>
- <span data-ttu-id="4d303-130">Täcka</span><span class="sxs-lookup"><span data-stu-id="4d303-130">Wide</span></span>
- <span data-ttu-id="4d303-131">Anpassat</span><span class="sxs-lookup"><span data-stu-id="4d303-131">Custom</span></span>

<span data-ttu-id="4d303-132">När till exempel utdata från ett `Get-ChildItem` kommando är skickas till ett `Format-List` kommando, `Format-List` använder vyn i `FileSystem.Format.ps1xml` filen för att avgöra hur fil-och mappobjekt ska visas som en lista.</span><span class="sxs-lookup"><span data-stu-id="4d303-132">For example, when the output of a `Get-ChildItem` command is piped to a `Format-List` command, `Format-List` uses the view in the `FileSystem.Format.ps1xml` file to determine how to display the file and folder objects as a list.</span></span>

<span data-ttu-id="4d303-133">När en format fil innehåller mer än en vy av ett objekt, tillämpar PowerShell den första vyn som hittas.</span><span class="sxs-lookup"><span data-stu-id="4d303-133">When a formatting file includes more than one view of an object, PowerShell applies the first view that it finds.</span></span>

<span data-ttu-id="4d303-134">I en `Format.ps1xml` -fil definieras en vy av en uppsättning XML-taggar som beskriver namnet på vyn, vilken typ av objekt som kan användas, kolumn rubriker och de egenskaper som visas i bröd texten i vyn.</span><span class="sxs-lookup"><span data-stu-id="4d303-134">In a `Format.ps1xml` file, a view is defined by a set of XML tags that describe the name of the view, the type of object to which it can be applied, the column headers, and the properties that are displayed in the body of the view.</span></span> <span data-ttu-id="4d303-135">Formatet i `Format.ps1xml` filer tillämpas precis innan data visas för användaren.</span><span class="sxs-lookup"><span data-stu-id="4d303-135">The format in `Format.ps1xml` files is applied just before the data is presented to the user.</span></span>

## <a name="creating-new-formatps1xml-files"></a><span data-ttu-id="4d303-136">Skapa nya Format.ps1XML-filer</span><span class="sxs-lookup"><span data-stu-id="4d303-136">Creating new Format.ps1xml files</span></span>

<span data-ttu-id="4d303-137">De `.ps1xml` filer som installeras med PowerShell signeras digitalt för att förhindra manipulering eftersom formateringen kan innehålla skript block.</span><span class="sxs-lookup"><span data-stu-id="4d303-137">The `.ps1xml` files that are installed with PowerShell are digitally signed to prevent tampering because the formatting can include script blocks.</span></span> <span data-ttu-id="4d303-138">Om du vill ändra visnings formatet för en befintlig objekt vy, eller lägga till vyer för nya objekt, skapar du dina egna `Format.ps1xml` filer och lägger sedan till dem i PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="4d303-138">To change the display format of an existing object view, or to add views for new objects, create your own `Format.ps1xml` files, and then add them to your PowerShell session.</span></span>

<span data-ttu-id="4d303-139">Kopiera en befintlig fil om du vill skapa en ny fil `Format.ps1xml` .</span><span class="sxs-lookup"><span data-stu-id="4d303-139">To create a new file, copy an existing `Format.ps1xml` file.</span></span> <span data-ttu-id="4d303-140">Den nya filen kan ha vilket namn som helst, men den måste ha ett `.ps1xml` fil namns tillägg.</span><span class="sxs-lookup"><span data-stu-id="4d303-140">The new file can have any name, but it must have a `.ps1xml` file name extension.</span></span> <span data-ttu-id="4d303-141">Du kan placera den nya filen i valfri katalog som är tillgänglig för PowerShell, men det är praktiskt att placera filerna i installations katalogen för PowerShell ( `$PSHOME` ) eller i en under katalog i installations katalogen.</span><span class="sxs-lookup"><span data-stu-id="4d303-141">You can place the new file in any directory that is accessible to PowerShell, but it's useful to place the files in the PowerShell installation directory (`$PSHOME`) or in a subdirectory of the installation directory.</span></span>

<span data-ttu-id="4d303-142">Om du vill ändra formateringen för en aktuell vy letar du upp vyn i format filen och använder sedan taggarna för att ändra vyn.</span><span class="sxs-lookup"><span data-stu-id="4d303-142">To change the formatting of a current view, locate the view in the formatting file, and then use the tags to change the view.</span></span> <span data-ttu-id="4d303-143">Skapa en vy för en ny objekt typ genom att skapa en ny vy eller använda en befintlig vy som en modell.</span><span class="sxs-lookup"><span data-stu-id="4d303-143">To create a view for a new object type, create a new view, or use an existing view as a model.</span></span> <span data-ttu-id="4d303-144">Taggarna beskrivs i nästa avsnitt.</span><span class="sxs-lookup"><span data-stu-id="4d303-144">The tags are described in the next section.</span></span> <span data-ttu-id="4d303-145">Du kan sedan ta bort alla andra vyer i filen så att ändringarna är uppenbara för alla som granskar filen.</span><span class="sxs-lookup"><span data-stu-id="4d303-145">You can then delete all the other views in the file so that the changes are obvious to anyone examining the file.</span></span>

<span data-ttu-id="4d303-146">När du har sparat ändringarna använder du `Update-FormatData` cmdleten för att lägga till den nya filen i PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="4d303-146">After you save the changes, use the `Update-FormatData` cmdlet to add the new file to your PowerShell session.</span></span> <span data-ttu-id="4d303-147">Om du vill att vyn ska prioriteras över en vy som definierats i de inbyggda filerna använder du parametern **PrependPath** .</span><span class="sxs-lookup"><span data-stu-id="4d303-147">If you want your view to take precedence over a view defined in the built-in files, use the **PrependPath** parameter.</span></span>
<span data-ttu-id="4d303-148">`Update-FormatData` påverkar endast den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="4d303-148">`Update-FormatData` affects only the current session.</span></span> <span data-ttu-id="4d303-149">Om du vill göra ändringen i alla framtida sessioner lägger du till `Update-FormatData` kommandot i din PowerShell-profil.</span><span class="sxs-lookup"><span data-stu-id="4d303-149">To make the change to all future sessions, add the `Update-FormatData` command to your PowerShell profile.</span></span>

### <a name="example-adding-calendar-data-to-culture-objects"></a><span data-ttu-id="4d303-150">Exempel: lägga till kalender data till kultur objekt</span><span class="sxs-lookup"><span data-stu-id="4d303-150">Example: Adding calendar data to culture objects</span></span>

<span data-ttu-id="4d303-151">Det här exemplet visar hur du ändrar formateringen för kultur objekt **system. globalisering. CultureInfo** som genereras av `Get-Culture` cmdleten i den aktuella PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="4d303-151">This example shows how to change the formatting of the culture objects **System.Globalization.CultureInfo** generated by the `Get-Culture` cmdlet in the current PowerShell session.</span></span> <span data-ttu-id="4d303-152">Kommandona i exemplet lägger till **kalender** egenskapen i standardvyn visning av kultur objekt.</span><span class="sxs-lookup"><span data-stu-id="4d303-152">The commands in the example add the **Calendar** property to the default table view display of culture objects.</span></span>

<span data-ttu-id="4d303-153">Det första steget är att hitta `Format.ps1xml` filen som innehåller den aktuella vyn av kultur objekt.</span><span class="sxs-lookup"><span data-stu-id="4d303-153">The first step is to find the `Format.ps1xml` file that contains the current view of the culture objects.</span></span> <span data-ttu-id="4d303-154">Följande `Select-String` kommando hittar filen:</span><span class="sxs-lookup"><span data-stu-id="4d303-154">The following `Select-String` command finds the file:</span></span>

```powershell
$Parms = @{
  Path = "$PSHOME\*Format.ps1xml"
  Pattern = "System.Globalization.CultureInfo"
}

Select-String @Parms
```

```Output
C:\Windows\System32\WindowsPowerShell\v1.0\DotNetTypes.format.ps1xml:113:
     <Name>System.Globalization.CultureInfo</Name>
C:\Windows\System32\WindowsPowerShell\v1.0\DotNetTypes.format.ps1xml:115:
<TypeName>System.Globalization.CultureInfo</TypeName>
```

<span data-ttu-id="4d303-155">Det här kommandot visar att definitionen finns i `DotNetTypes.Format.ps1xml` filen.</span><span class="sxs-lookup"><span data-stu-id="4d303-155">This command reveals that the definition is in the `DotNetTypes.Format.ps1xml` file.</span></span>

<span data-ttu-id="4d303-156">Nästa kommando kopierar fil innehållet till en ny fil `MyDotNetTypes.Format.ps1xml` .</span><span class="sxs-lookup"><span data-stu-id="4d303-156">The next command copies the file contents to a new file, `MyDotNetTypes.Format.ps1xml`.</span></span>

```powershell
Copy-Item $PSHome\DotNetTypes.format.ps1xml MyDotNetTypes.Format.ps1xml
```

<span data-ttu-id="4d303-157">Öppna `MyDotNetTypes.Format.ps1xml` filen i valfri XML-eller text redigerare, t. ex. Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="4d303-157">Open the `MyDotNetTypes.Format.ps1xml` file in any XML or text editor, such as Visual Studio Code.</span></span> <span data-ttu-id="4d303-158">Hitta objekt avsnittet **system. globalisering. CultureInfo** .</span><span class="sxs-lookup"><span data-stu-id="4d303-158">Find the **System.Globalization.CultureInfo** object section.</span></span> <span data-ttu-id="4d303-159">Följande XML definierar vyerna för **CultureInfo** -objektet.</span><span class="sxs-lookup"><span data-stu-id="4d303-159">The following XML defines the views of the **CultureInfo** object.</span></span> <span data-ttu-id="4d303-160">Objektet har endast en **TableControl** -vy.</span><span class="sxs-lookup"><span data-stu-id="4d303-160">The object has only a **TableControl** view.</span></span>

```xml
<View>
  <Name>System.Globalization.CultureInfo</Name>
  <ViewSelectedBy>
    <TypeName>Deserialized.System.Globalization.CultureInfo</TypeName>
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
```

<span data-ttu-id="4d303-161">Ta bort resten av filen, förutom öppnings `<?xml>` -, `<Configuration>` ,-och- `<ViewDefinitions>` taggarna och stängnings- `<ViewDefinitions>` och `<Configuration>` taggarna.</span><span class="sxs-lookup"><span data-stu-id="4d303-161">Delete the remainder of the file, except for the opening `<?xml>`, `<Configuration>`, and `<ViewDefinitions>` tags and the closing `<ViewDefinitions>` and `<Configuration>` tags.</span></span> <span data-ttu-id="4d303-162">Om det finns en digital signatur tar du bort den från den anpassade `Format.ps1xml` filen.</span><span class="sxs-lookup"><span data-stu-id="4d303-162">If there is a digital signature, delete it from your custom `Format.ps1xml`file.</span></span>

<span data-ttu-id="4d303-163">`MyDotNetTypes.Format.ps1xml`Filen bör nu se ut som i följande exempel:</span><span class="sxs-lookup"><span data-stu-id="4d303-163">The `MyDotNetTypes.Format.ps1xml` file should now look like the following sample:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<Configuration>
<ViewDefinitions>
<View>
  <Name>System.Globalization.CultureInfo</Name>
  <ViewSelectedBy>
    <TypeName>Deserialized.System.Globalization.CultureInfo</TypeName>
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
      <TableColumnHeader/>
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

<span data-ttu-id="4d303-164">Skapa en ny kolumn för **kalender** egenskapen genom att lägga till en ny uppsättning `<TableColumnHeader>` taggar.</span><span class="sxs-lookup"><span data-stu-id="4d303-164">Create a new column for the **Calendar** property by adding a new set of `<TableColumnHeader>` tags.</span></span> <span data-ttu-id="4d303-165">Värdet för egenskapen **Calendar** kan vara Long, så ange ett värde på 45 tecken som `<Width>` .</span><span class="sxs-lookup"><span data-stu-id="4d303-165">The value of the **Calendar** property can be long, so specify a value of 45 characters as the `<Width>`.</span></span>

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

<span data-ttu-id="4d303-166">Lägg till ett nytt kolumn objekt för **kalender** i tabell rader med `<TableColumnItem>` `<PropertyName` taggarna och:</span><span class="sxs-lookup"><span data-stu-id="4d303-166">Add a new column item for **Calendar** in the table rows using the `<TableColumnItem>` and `<PropertyName` tags:</span></span>

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

<span data-ttu-id="4d303-167">Spara och stäng filen.</span><span class="sxs-lookup"><span data-stu-id="4d303-167">Save and close the file.</span></span> <span data-ttu-id="4d303-168">Använd `Update-FormatData` för att lägga till den nya format filen i den aktuella PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="4d303-168">Use `Update-FormatData` to add the new format file to the current PowerShell session.</span></span>

<span data-ttu-id="4d303-169">I det här exemplet används parametern **PrependPath** för att placera den nya filen i en högre prioritets ordning än den ursprungliga filen.</span><span class="sxs-lookup"><span data-stu-id="4d303-169">This example uses the **PrependPath** parameter to place the new file in a higher precedence order than the original file.</span></span> <span data-ttu-id="4d303-170">Mer information finns i [Update-FormatData](xref:Microsoft.PowerShell.Utility.Update-FormatData).</span><span class="sxs-lookup"><span data-stu-id="4d303-170">For more information, see [Update-FormatData](xref:Microsoft.PowerShell.Utility.Update-FormatData).</span></span>

```powershell
Update-FormatData -PrependPath $PSHOME\MyDotNetTypes.Format.ps1xml
```

<span data-ttu-id="4d303-171">Testa ändringen genom att skriva `Get-Culture` och granska utdata som innehåller **kalender** egenskapen.</span><span class="sxs-lookup"><span data-stu-id="4d303-171">To test the change, type `Get-Culture` and review the output that includes the **Calendar** property.</span></span>

```powershell
Get-Culture
```

```Output
LCID Name  Calendar                               DisplayName
---- ----  --------                               -----------
1033 en-US System.Globalization.GregorianCalendar English (United States)
```

## <a name="the-xml-in-formatps1xml-files"></a><span data-ttu-id="4d303-172">XML i Format.ps1XML-filer</span><span class="sxs-lookup"><span data-stu-id="4d303-172">The XML in Format.ps1xml files</span></span>

<span data-ttu-id="4d303-173">Du hittar fullständig schema definition i [formatet. xsd](https://github.com/PowerShell/PowerShell/blob/master/src/Schemas/Format.xsd) i PowerShell-källkoden på GitHub.</span><span class="sxs-lookup"><span data-stu-id="4d303-173">The full schema definition can be found in [Format.xsd](https://github.com/PowerShell/PowerShell/blob/master/src/Schemas/Format.xsd) in the PowerShell source code repository on GitHub.</span></span>

<span data-ttu-id="4d303-174">Avsnittet **ViewDefinitions** i varje `Format.ps1xml` fil innehåller de `<View>` taggar som definierar varje vy.</span><span class="sxs-lookup"><span data-stu-id="4d303-174">The **ViewDefinitions** section of each `Format.ps1xml` file contains the `<View>` tags that define each view.</span></span> <span data-ttu-id="4d303-175">En typisk `<View>` tagg innehåller följande Taggar:</span><span class="sxs-lookup"><span data-stu-id="4d303-175">A typical `<View>` tag includes the following tags:</span></span>

- <span data-ttu-id="4d303-176">`<Name>` identifierar namnet på vyn.</span><span class="sxs-lookup"><span data-stu-id="4d303-176">`<Name>` identifies the name of the view.</span></span>
- <span data-ttu-id="4d303-177">`<ViewSelectedBy>` anger objekt typen eller typerna som vyn gäller för.</span><span class="sxs-lookup"><span data-stu-id="4d303-177">`<ViewSelectedBy>` specifies the object type or types to which the view applies.</span></span>
- <span data-ttu-id="4d303-178">`<GroupBy>` anger hur objekt i vyn ska kombineras i grupper.</span><span class="sxs-lookup"><span data-stu-id="4d303-178">`<GroupBy>` specifies how items in the view will be combined in groups.</span></span>
- <span data-ttu-id="4d303-179">`<TableControl>`, `<ListControl>` , `<WideControl>` och `<CustomControl>` innehåller taggarna som anger hur varje objekt ska visas.</span><span class="sxs-lookup"><span data-stu-id="4d303-179">`<TableControl>`, `<ListControl>`, `<WideControl>`, and `<CustomControl>` contain the tags that specify how each item will be displayed.</span></span>

### <a name="viewselectedby-tag"></a><span data-ttu-id="4d303-180">ViewSelectedBy-tagg</span><span class="sxs-lookup"><span data-stu-id="4d303-180">ViewSelectedBy tag</span></span>

<span data-ttu-id="4d303-181">`<ViewSelectedBy>`Taggen kan innehålla en `<TypeName>` tagg för varje objekt typ som vyn gäller för.</span><span class="sxs-lookup"><span data-stu-id="4d303-181">The `<ViewSelectedBy>` tag can contain a `<TypeName>` tag for each object type to which the view applies.</span></span> <span data-ttu-id="4d303-182">Eller så kan den innehålla en `<SelectionSetName>` tagg som refererar till en urvals uppsättning som definieras någon annan stans genom att använda en- `<SelectionSet>` tagg.</span><span class="sxs-lookup"><span data-stu-id="4d303-182">Or, it can contain a `<SelectionSetName>` tag that references a selection set that is defined elsewhere by using a `<SelectionSet>` tag.</span></span>

### <a name="groupby-tag"></a><span data-ttu-id="4d303-183">GroupBy-tagg</span><span class="sxs-lookup"><span data-stu-id="4d303-183">GroupBy tag</span></span>

<span data-ttu-id="4d303-184">`<GroupBy>`Taggen innehåller en `<PropertyName>` tagg som anger den objekt egenskap enligt vilken objekten ska grupperas.</span><span class="sxs-lookup"><span data-stu-id="4d303-184">The `<GroupBy>` tag contains a `<PropertyName>` tag that specifies the object property by which items are to be grouped.</span></span> <span data-ttu-id="4d303-185">Den innehåller också antingen en `<Label>` tagg som anger en sträng som ska användas som en etikett för varje grupp eller en `<CustomControlName>` tagg som refererar till en anpassad kontroll som definierats någon annan stans med en `<Control>` tagg.</span><span class="sxs-lookup"><span data-stu-id="4d303-185">It also contains either a `<Label>` tag that specifies a string to be used as a label for each group or a `<CustomControlName>` tag that references a custom control defined elsewhere using a `<Control>` tag.</span></span> <span data-ttu-id="4d303-186">`<Control>`Taggen innehåller en `<Name>` tagg och en `<CustomControl>` tagg.</span><span class="sxs-lookup"><span data-stu-id="4d303-186">The `<Control>` tag contains a `<Name>` tag and a `<CustomControl>` tag.</span></span>

### <a name="tablecontroltag"></a><span data-ttu-id="4d303-187">TableControlTag</span><span class="sxs-lookup"><span data-stu-id="4d303-187">TableControlTag</span></span>

<span data-ttu-id="4d303-188">`<TableControl>`Taggen innehåller vanligt vis `<TableHeaders>` och `<TableRowEntries>` taggar som definierar formateringen för tabellens huvuden och rader.</span><span class="sxs-lookup"><span data-stu-id="4d303-188">The `<TableControl>` tag typically contains `<TableHeaders>` and `<TableRowEntries>` tags that define the formatting for the table's heads and rows.</span></span> <span data-ttu-id="4d303-189">`<TableHeaders>`Taggen innehåller vanligt vis `<TableColumnHeader>` taggar som innehåller `<Label>` `<Width>` taggar, och `<Alignment>` .</span><span class="sxs-lookup"><span data-stu-id="4d303-189">The `<TableHeaders>` tag typically contains `<TableColumnHeader>` tags that contain `<Label>`, `<Width>`, and `<Alignment>` tags.</span></span> <span data-ttu-id="4d303-190">`<TableRowEntries>`Taggen innehåller `<TableRowEntry>` taggar för varje rad i tabellen.</span><span class="sxs-lookup"><span data-stu-id="4d303-190">The `<TableRowEntries>` tag contains `<TableRowEntry>` tags for each row in the table.</span></span> <span data-ttu-id="4d303-191">`<TableRowEntry>`Taggen innehåller en `<TableColumnItems>` tagg som innehåller en `<TableColumnItem>` tagg för varje kolumn på raden.</span><span class="sxs-lookup"><span data-stu-id="4d303-191">The `<TableRowEntry>` tag contains a `<TableColumnItems>` tag that contains a `<TableColumnItem>` tag for each column in the row.</span></span> <span data-ttu-id="4d303-192">Normalt `<TableColumnItem>` innehåller taggen en `<PropertyName>` tagg som identifierar objekt egenskapen som ska visas på den definierade platsen, eller en `<ScriptBlock>` tagg som innehåller skript kod som beräknar ett resultat som ska visas på platsen.</span><span class="sxs-lookup"><span data-stu-id="4d303-192">Typically, the `<TableColumnItem>` tag contains either a `<PropertyName>` tag that identifies the object property to be displayed in the defined location, or a `<ScriptBlock>` tag that contains script code that calculates a result that is to be displayed in the location.</span></span>

> [!NOTE]
> <span data-ttu-id="4d303-193">Skript block kan också användas på andra platser på platser där beräknade resultat kan vara användbara.</span><span class="sxs-lookup"><span data-stu-id="4d303-193">Script blocks can also be used elsewhere in locations where calculated results can be useful.</span></span>

<span data-ttu-id="4d303-194">`<TableColumnItem>`Taggen kan också innehålla en `<FormatString>` tagg som anger hur egenskapen eller de beräknade resultaten ska visas.</span><span class="sxs-lookup"><span data-stu-id="4d303-194">The `<TableColumnItem>` tag can also contain a `<FormatString>` tag that specifies how the property or the calculated results will be displayed.</span></span>

### <a name="listcontrol-tag"></a><span data-ttu-id="4d303-195">ListControl-tagg</span><span class="sxs-lookup"><span data-stu-id="4d303-195">ListControl tag</span></span>

<span data-ttu-id="4d303-196">`<ListControl>`Taggen innehåller vanligt vis en `<ListEntries>` tagg.</span><span class="sxs-lookup"><span data-stu-id="4d303-196">The `<ListControl>` tag typically contains a `<ListEntries>` tag.</span></span> <span data-ttu-id="4d303-197">`<ListEntries>`Taggen innehåller en `<ListEntry>` tagg.</span><span class="sxs-lookup"><span data-stu-id="4d303-197">The `<ListEntries>` tag contains a `<ListEntry>` tag.</span></span> <span data-ttu-id="4d303-198">`<ListEntry>`Taggen innehåller en `<ListItems>` tagg.</span><span class="sxs-lookup"><span data-stu-id="4d303-198">The `<ListEntry>` tag contains a `<ListItems>` tag.</span></span> <span data-ttu-id="4d303-199">`<ListItems>`Taggen innehåller `<ListItem>` taggar som innehåller `<PropertyName>` taggar.</span><span class="sxs-lookup"><span data-stu-id="4d303-199">The `<ListItems>` tag contains `<ListItem>` tags, which contain `<PropertyName>` tags.</span></span> <span data-ttu-id="4d303-200">`<PropertyName>`Taggarna anger vilken objekt egenskap som ska visas på den angivna platsen i listan.</span><span class="sxs-lookup"><span data-stu-id="4d303-200">The `<PropertyName>` tags specify the object property to be displayed at the specified location in the list.</span></span> <span data-ttu-id="4d303-201">Om visnings valet definieras med en urvals uppsättning `<ListControl>` `<ListEntry>` kan taggarna och också innehålla en `<EntrySelectedBy>` tagg som innehåller en eller flera `<TypeName>` taggar.</span><span class="sxs-lookup"><span data-stu-id="4d303-201">If the view selection is defined using a selection set, the `<ListControl>` and `<ListEntry>` tags can also contain an `<EntrySelectedBy>` tag that contains one or more `<TypeName>` tags.</span></span> <span data-ttu-id="4d303-202">`<TypeName>`Taggarna anger vilken objekt typ `<ListControl>` taggen är avsedd att visa.</span><span class="sxs-lookup"><span data-stu-id="4d303-202">These `<TypeName>` tags specify the object type that the `<ListControl>` tag is intended to display.</span></span>

### <a name="widecontrol-tag"></a><span data-ttu-id="4d303-203">WideControl-tagg</span><span class="sxs-lookup"><span data-stu-id="4d303-203">WideControl tag</span></span>

<span data-ttu-id="4d303-204">`<WideControl>`Taggen innehåller vanligt vis en `<WideEntries>` tagg.</span><span class="sxs-lookup"><span data-stu-id="4d303-204">The `<WideControl>` tag typically contains a `<WideEntries>` tag.</span></span> <span data-ttu-id="4d303-205">`<WideEntries>`Taggen innehåller en eller flera `<WideEntry>` taggar.</span><span class="sxs-lookup"><span data-stu-id="4d303-205">The `<WideEntries>` tag contains one or more `<WideEntry>` tags.</span></span> <span data-ttu-id="4d303-206">En- `<WideEntry>` tagg innehåller vanligt vis en `<PropertyName>` tagg som anger den egenskap som ska visas på den angivna platsen i vyn.</span><span class="sxs-lookup"><span data-stu-id="4d303-206">A `<WideEntry>` tag typically contains a `<PropertyName>` tag that specifies the property to be displayed at the specified location in the view.</span></span> <span data-ttu-id="4d303-207">`<PropertyName>`Taggen kan innehålla en `<FormatString>` tagg som anger hur egenskapen ska visas.</span><span class="sxs-lookup"><span data-stu-id="4d303-207">The `<PropertyName>` tag can contain a `<FormatString>` tag that specifies how the property is to be displayed.</span></span>

### <a name="customcontrol-tag"></a><span data-ttu-id="4d303-208">CustomControl-tagg</span><span class="sxs-lookup"><span data-stu-id="4d303-208">CustomControl tag</span></span>

<span data-ttu-id="4d303-209">Med `<CustomControl>` taggen kan du definiera ett format genom att använda ett-skript block.</span><span class="sxs-lookup"><span data-stu-id="4d303-209">The `<CustomControl>` tag lets you use a script block to define a format.</span></span> <span data-ttu-id="4d303-210">En- `<CustomControl>` tagg innehåller vanligt vis en `<CustomEntries>` tagg som innehåller flera `<CustomEntry>` taggar.</span><span class="sxs-lookup"><span data-stu-id="4d303-210">A `<CustomControl>` tag typically contains a `<CustomEntries>` tag that contains multiple `<CustomEntry>` tags.</span></span> <span data-ttu-id="4d303-211">Varje- `<CustomEntry>` tagg innehåller en `<CustomItem>` tagg som kan innehålla en rad olika taggar som anger innehåll och formatering för den angivna platsen i vyn, inklusive `<Text>` , `<Indentation>` , `<ExpressionBinding>` och `<NewLine>` taggar.</span><span class="sxs-lookup"><span data-stu-id="4d303-211">Each `<CustomEntry>` tag contains a `<CustomItem>` tag that can contain a variety of tags that specify contents and formatting of the specified location in the view, including `<Text>`, `<Indentation>`, `<ExpressionBinding>`, and `<NewLine>` tags.</span></span>

## <a name="default-displays-in-typesps1xml"></a><span data-ttu-id="4d303-212">Standard visas i Types.ps1XML</span><span class="sxs-lookup"><span data-stu-id="4d303-212">Default displays in Types.ps1xml</span></span>

<span data-ttu-id="4d303-213">Standard visningen av vissa grundläggande objekt typer definieras i `Types.ps1xml` filen i `$PSHOME` katalogen.</span><span class="sxs-lookup"><span data-stu-id="4d303-213">The default displays of some basic object types are defined in the `Types.ps1xml` file in the `$PSHOME` directory.</span></span> <span data-ttu-id="4d303-214">Noderna heter **PsStandardMembers** och undernoderna använder någon av följande Taggar:</span><span class="sxs-lookup"><span data-stu-id="4d303-214">The nodes are named **PsStandardMembers** , and the subnodes use one of the following tags:</span></span>

- `<DefaultDisplayProperty>`
- `<DefaultDisplayPropertySet>`
- `<DefaultKeyPropertySet>`

<span data-ttu-id="4d303-215">Mer information finns i [about_Types.ps1XML](about_Types.ps1xml.md).</span><span class="sxs-lookup"><span data-stu-id="4d303-215">For more information, see [about_Types.ps1xml](about_Types.ps1xml.md).</span></span>

## <a name="tracing-formatps1xml-file-use"></a><span data-ttu-id="4d303-216">Använda spårning Format.ps1XML-fil</span><span class="sxs-lookup"><span data-stu-id="4d303-216">Tracing Format.ps1xml file use</span></span>

<span data-ttu-id="4d303-217">Om du vill identifiera fel vid inläsning eller tillämpning av `Format.ps1xml` filer använder du `Trace-Command` cmdleten med någon av följande format komponenter som värde för parametern **Name** :</span><span class="sxs-lookup"><span data-stu-id="4d303-217">To detect errors in the loading or application of `Format.ps1xml` files, use the `Trace-Command` cmdlet with any of the following format components as the value of the **Name** parameter:</span></span>

- <span data-ttu-id="4d303-218">FormatFileLoading</span><span class="sxs-lookup"><span data-stu-id="4d303-218">FormatFileLoading</span></span>
- <span data-ttu-id="4d303-219">FormatViewBinding</span><span class="sxs-lookup"><span data-stu-id="4d303-219">FormatViewBinding</span></span>

<span data-ttu-id="4d303-220">Mer information finns i [trace-Command](xref:Microsoft.PowerShell.Utility.Trace-Command) och [Get-TraceSource](xref:Microsoft.PowerShell.Utility.Get-TraceSource).</span><span class="sxs-lookup"><span data-stu-id="4d303-220">For more information, see [Trace-Command](xref:Microsoft.PowerShell.Utility.Trace-Command) and [Get-TraceSource](xref:Microsoft.PowerShell.Utility.Get-TraceSource).</span></span>

## <a name="signing-a-formatps1xml-file"></a><span data-ttu-id="4d303-221">Signera en Format.ps1XML-fil</span><span class="sxs-lookup"><span data-stu-id="4d303-221">Signing a Format.ps1xml file</span></span>

<span data-ttu-id="4d303-222">Du skyddar användare av `Format.ps1xml` filen genom att signera filen med en digital signatur.</span><span class="sxs-lookup"><span data-stu-id="4d303-222">To protect the users of your `Format.ps1xml` file, sign the file using a digital signature.</span></span> <span data-ttu-id="4d303-223">Mer information finns i [about_Signing](about_Signing.md).</span><span class="sxs-lookup"><span data-stu-id="4d303-223">For more information, see [about_Signing](about_Signing.md).</span></span>

## <a name="sample-xml-for-a-format-table-custom-view"></a><span data-ttu-id="4d303-224">Exempel-XML för en Format-Table anpassad vy</span><span class="sxs-lookup"><span data-stu-id="4d303-224">Sample XML for a Format-Table custom view</span></span>

<span data-ttu-id="4d303-225">I följande exempel skapas en `Format-Table` anpassad vy för objekten **system. io. DirectoryInfo** och **system. io. fileinfo** som skapats av `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="4d303-225">The following sample creates a `Format-Table` custom view for the **System.IO.DirectoryInfo** and **System.IO.FileInfo** objects created by `Get-ChildItem`.</span></span> <span data-ttu-id="4d303-226">Den anpassade vyn heter **mygciview** och lägger till **CreationTime** -kolumnen i tabellen.</span><span class="sxs-lookup"><span data-stu-id="4d303-226">The custom view is named **mygciview** and adds the **CreationTime** column to the table.</span></span>

<span data-ttu-id="4d303-227">Den anpassade vyn skapas från en redige rad version av `FileSystem.Format.ps1xml` filen som lagras i `$PSHOME` på PowerShell 5,1.</span><span class="sxs-lookup"><span data-stu-id="4d303-227">The custom view is created from an edited version of the `FileSystem.Format.ps1xml` file that's stored in `$PSHOME` on PowerShell 5.1.</span></span>

<span data-ttu-id="4d303-228">När din anpassade `.ps1xml` fil har sparats använder `Update-FormatData` du för att inkludera vyn i en PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="4d303-228">After your custom `.ps1xml` file is saved, use `Update-FormatData` to include the view in a PowerShell session.</span></span> <span data-ttu-id="4d303-229">I det här exemplet måste den anpassade vyn använda tabell formatet, annars `Format-Table` Miss lyckas.</span><span class="sxs-lookup"><span data-stu-id="4d303-229">For this example, the custom view must use the table format, otherwise, `Format-Table` fails.</span></span>

<span data-ttu-id="4d303-230">Använd `Format-Table` med parametern **View** för att ange den anpassade vyns namn och formatera tabellens utdata.</span><span class="sxs-lookup"><span data-stu-id="4d303-230">Use `Format-Table` with the **View** parameter to specify the custom view's name and format the table's output.</span></span> <span data-ttu-id="4d303-231">Ett exempel på hur kommandot körs finns i [Format-Table](xref:Microsoft.PowerShell.Utility.Format-Table).</span><span class="sxs-lookup"><span data-stu-id="4d303-231">For an example of how the command is run, see [Format-Table](xref:Microsoft.PowerShell.Utility.Format-Table).</span></span>

```powershell
$Parms = @{
  Path = "$PSHOME\*Format.ps1xml"
  Pattern = "System.IO.DirectoryInfo"
}
Select-String @Parms
Copy-Item $PSHome\FileSystem.format.ps1xml .\MyFileSystem.Format.ps1xml
Update-FormatData -PrependPath $PSHOME\Format\MyFileSystem.Format.ps1xml
```

> [!NOTE]
> <span data-ttu-id="4d303-232">För att anpassa XML-exemplet inom gränserna för linje bredd var det nödvändigt att komprimera vissa indrag och använda rad brytningar i koden.</span><span class="sxs-lookup"><span data-stu-id="4d303-232">To fit the XML sample within line width limitations, it was necessary to compress some indentation and use line breaks within the code.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<Configuration>
    <SelectionSets>
        <SelectionSet>
            <Name>FileSystemTypes</Name>
            <Types>
                <TypeName>System.IO.DirectoryInfo</TypeName>
                <TypeName>System.IO.FileInfo</TypeName>
            </Types>
        </SelectionSet>
    </SelectionSets>
<Controls>
<Control>
<Name>FileSystemTypes-GroupingFormat</Name>
<CustomControl>
 <CustomEntries>
  <CustomEntry>
    <CustomItem>
    <Frame>
    <LeftIndent>4</LeftIndent>
    <CustomItem>
    <Text AssemblyName="System.Management.Automation"
    BaseName="FileSystemProviderStrings"
    ResourceId="DirectoryDisplayGrouping"/>
    <ExpressionBinding>
     <ScriptBlock>
      $_.PSParentPath.Replace("Microsoft.PowerShell.Core\FileSystem::", "")
     </ScriptBlock>
    </ExpressionBinding>
    <NewLine/>
    </CustomItem>
    </Frame>
    </CustomItem>
    </CustomEntry>
 </CustomEntries>
</CustomControl>
</Control>
</Controls>
<ViewDefinitions>
    <View>
    <Name>mygciview</Name>
    <ViewSelectedBy>
        <SelectionSetName>FileSystemTypes</SelectionSetName>
    </ViewSelectedBy>
    <GroupBy>
      <PropertyName>PSParentPath</PropertyName>
      <CustomControlName>FileSystemTypes-GroupingFormat</CustomControlName>
    </GroupBy>
        <TableControl>
            <TableHeaders>
                <TableColumnHeader>
                    <Label>Mode</Label>
                    <Width>7</Width>
                    <Alignment>left</Alignment>
                </TableColumnHeader>
                <TableColumnHeader>
                    <Label>LastWriteTime</Label>
                    <Width>25</Width>
                    <Alignment>right</Alignment>
                </TableColumnHeader>
                <TableColumnHeader>
                    <Label>CreationTime</Label>
                    <Width>25</Width>
                    <Alignment>right</Alignment>
                </TableColumnHeader>
                <TableColumnHeader>
                    <Label>Length</Label>
                    <Width>14</Width>
                    <Alignment>right</Alignment>
                </TableColumnHeader>
                <TableColumnHeader/>
            </TableHeaders>
            <TableRowEntries>
                <TableRowEntry>
                    <Wrap/>
                    <TableColumnItems>
                        <TableColumnItem>
                            <PropertyName>Mode</PropertyName>
                        </TableColumnItem>
                        <TableColumnItem>
                            <ScriptBlock>
                                [String]::Format("{0,10}  {1,8}",
                                    $_.LastWriteTime.ToString("d"),
                                    $_.LastWriteTime.ToString("t"))
                            </ScriptBlock>
                        </TableColumnItem>
                        <TableColumnItem>
                            <ScriptBlock>
                                [String]::Format("{0,10}  {1,8}",
                                    $_.CreationTime.ToString("d"),
                                    $_.LastWriteTime.ToString("t"))
                            </ScriptBlock>
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

## <a name="see-also"></a><span data-ttu-id="4d303-233">Se även</span><span class="sxs-lookup"><span data-stu-id="4d303-233">See also</span></span>

[<span data-ttu-id="4d303-234">Exportera – FormatData</span><span class="sxs-lookup"><span data-stu-id="4d303-234">Export-FormatData</span></span>](xref:Microsoft.PowerShell.Utility.Export-FormatData)

[<span data-ttu-id="4d303-235">Get-FormatData</span><span class="sxs-lookup"><span data-stu-id="4d303-235">Get-FormatData</span></span>](xref:Microsoft.PowerShell.Utility.Get-FormatData)

[<span data-ttu-id="4d303-236">Get-TraceSource</span><span class="sxs-lookup"><span data-stu-id="4d303-236">Get-TraceSource</span></span>](xref:Microsoft.PowerShell.Utility.Get-TraceSource)

[<span data-ttu-id="4d303-237">XML-referens för formatschema</span><span class="sxs-lookup"><span data-stu-id="4d303-237">Format Schema XML Reference</span></span>](/powershell/scripting/developer/format/format-schema-xml-reference)

[<span data-ttu-id="4d303-238">Spåra-kommando</span><span class="sxs-lookup"><span data-stu-id="4d303-238">Trace-Command</span></span>](xref:Microsoft.PowerShell.Utility.Trace-Command)

[<span data-ttu-id="4d303-239">Uppdatera – FormatData</span><span class="sxs-lookup"><span data-stu-id="4d303-239">Update-FormatData</span></span>](xref:Microsoft.PowerShell.Utility.Update-FormatData)

[<span data-ttu-id="4d303-240">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="4d303-240">Writing a PowerShell Formatting File</span></span>](/powershell/scripting/developer/format/writing-a-powershell-formatting-file)
