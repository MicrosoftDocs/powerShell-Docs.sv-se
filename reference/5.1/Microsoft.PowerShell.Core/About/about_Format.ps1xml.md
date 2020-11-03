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
# <a name="about-formatps1xml"></a>Om Format.ps1XML

## <a name="short-description"></a>Kort beskrivning

`Format.ps1xml`Filerna i PowerShell definierar standard visningen av objekt i PowerShell-konsolen. Du kan skapa egna `Format.ps1xml` filer om du vill ändra visningen av objekt eller definiera standard visning för nya objekt typer som du skapar i PowerShell.

## <a name="long-description"></a>Lång beskrivning

`Format.ps1xml`Filerna i PowerShell definierar standard visningen av objekt i PowerShell. Du kan skapa egna `Format.ps1xml` filer om du vill ändra visningen av objekt eller definiera standard visning för nya objekt typer som du skapar i PowerShell.

När PowerShell visar ett objekt används data i strukturerade formateringsattribut för att fastställa standard visningen av objektet. Data i formateringsattribut bestämmer om objektet återges i en tabell eller i en lista och avgör vilka egenskaper som visas som standard.

Formateringen påverkar endast visningen. Det påverkar inte vilka objekt egenskaper som har passerat pipelinen eller hur de skickas. `Format.ps1xml` Det går inte att använda filer för att anpassa utdataformatet för hash-tabeller.

PowerShell innehåller sju filer. De här filerna finns i installations katalogen ( `$PSHOME` ). Varje fil definierar visningen av en grupp Microsoft .NET Ramverks objekt:

1. `Certificate.Format.ps1xml`

   Objekt i certifikat arkivet, till exempel X. 509-certifikat och certifikat arkiv.

1. `DotNetTypes.Format.ps1xml`

   Andra .NET Framework typer, till exempel CultureInfo, FileVersionInfo och EventLogEntry-objekt.

1. `FileSystem.Format.ps1xml`

   Fil system objekt, till exempel filer och kataloger.

1. `Help.Format.ps1xml`

   Hjälp vyer, till exempel detaljerade och fullständiga vyer, parametrar och exempel.

1. `PowerShellCore.Format.ps1xml`

   Objekt som har genererats av PowerShell Core-cmdletar, till exempel `Get-Member` och `Get-History` .

1. `PowerShellTrace.Format.ps1xml`

   Spåra objekt, till exempel de som genereras av `Trace-Command` cmdleten.

1. `Registry.Format.ps1xml`

   Register objekt, till exempel nycklar och poster.

En format fil kan definiera fyra olika vyer för varje objekt:

- Tabeller
- Lista
- Täcka
- Anpassat

När till exempel utdata från ett `Get-ChildItem` kommando är skickas till ett `Format-List` kommando, `Format-List` använder vyn i `FileSystem.Format.ps1xml` filen för att avgöra hur fil-och mappobjekt ska visas som en lista.

När en format fil innehåller mer än en vy av ett objekt, tillämpar PowerShell den första vyn som hittas.

I en `Format.ps1xml` -fil definieras en vy av en uppsättning XML-taggar som beskriver namnet på vyn, vilken typ av objekt som kan användas, kolumn rubriker och de egenskaper som visas i bröd texten i vyn. Formatet i `Format.ps1xml` filer tillämpas precis innan data visas för användaren.

## <a name="creating-new-formatps1xml-files"></a>Skapa nya Format.ps1XML-filer

De `.ps1xml` filer som installeras med PowerShell signeras digitalt för att förhindra manipulering eftersom formateringen kan innehålla skript block. Om du vill ändra visnings formatet för en befintlig objekt vy, eller lägga till vyer för nya objekt, skapar du dina egna `Format.ps1xml` filer och lägger sedan till dem i PowerShell-sessionen.

Kopiera en befintlig fil om du vill skapa en ny fil `Format.ps1xml` . Den nya filen kan ha vilket namn som helst, men den måste ha ett `.ps1xml` fil namns tillägg. Du kan placera den nya filen i valfri katalog som är tillgänglig för PowerShell, men det är praktiskt att placera filerna i installations katalogen för PowerShell ( `$PSHOME` ) eller i en under katalog i installations katalogen.

Om du vill ändra formateringen för en aktuell vy letar du upp vyn i format filen och använder sedan taggarna för att ändra vyn. Skapa en vy för en ny objekt typ genom att skapa en ny vy eller använda en befintlig vy som en modell. Taggarna beskrivs i nästa avsnitt. Du kan sedan ta bort alla andra vyer i filen så att ändringarna är uppenbara för alla som granskar filen.

När du har sparat ändringarna använder du `Update-FormatData` cmdleten för att lägga till den nya filen i PowerShell-sessionen. Om du vill att vyn ska prioriteras över en vy som definierats i de inbyggda filerna använder du parametern **PrependPath** .
`Update-FormatData` påverkar endast den aktuella sessionen. Om du vill göra ändringen i alla framtida sessioner lägger du till `Update-FormatData` kommandot i din PowerShell-profil.

### <a name="example-adding-calendar-data-to-culture-objects"></a>Exempel: lägga till kalender data till kultur objekt

Det här exemplet visar hur du ändrar formateringen för kultur objekt **system. globalisering. CultureInfo** som genereras av `Get-Culture` cmdleten i den aktuella PowerShell-sessionen. Kommandona i exemplet lägger till **kalender** egenskapen i standardvyn visning av kultur objekt.

Det första steget är att hitta `Format.ps1xml` filen som innehåller den aktuella vyn av kultur objekt. Följande `Select-String` kommando hittar filen:

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

Det här kommandot visar att definitionen finns i `DotNetTypes.Format.ps1xml` filen.

Nästa kommando kopierar fil innehållet till en ny fil `MyDotNetTypes.Format.ps1xml` .

```powershell
Copy-Item $PSHome\DotNetTypes.format.ps1xml MyDotNetTypes.Format.ps1xml
```

Öppna `MyDotNetTypes.Format.ps1xml` filen i valfri XML-eller text redigerare, t. ex. Visual Studio Code. Hitta objekt avsnittet **system. globalisering. CultureInfo** . Följande XML definierar vyerna för **CultureInfo** -objektet. Objektet har endast en **TableControl** -vy.

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

Ta bort resten av filen, förutom öppnings `<?xml>` -, `<Configuration>` ,-och- `<ViewDefinitions>` taggarna och stängnings- `<ViewDefinitions>` och `<Configuration>` taggarna. Om det finns en digital signatur tar du bort den från den anpassade `Format.ps1xml` filen.

`MyDotNetTypes.Format.ps1xml`Filen bör nu se ut som i följande exempel:

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

Skapa en ny kolumn för **kalender** egenskapen genom att lägga till en ny uppsättning `<TableColumnHeader>` taggar. Värdet för egenskapen **Calendar** kan vara Long, så ange ett värde på 45 tecken som `<Width>` .

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

Lägg till ett nytt kolumn objekt för **kalender** i tabell rader med `<TableColumnItem>` `<PropertyName` taggarna och:

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

Spara och stäng filen. Använd `Update-FormatData` för att lägga till den nya format filen i den aktuella PowerShell-sessionen.

I det här exemplet används parametern **PrependPath** för att placera den nya filen i en högre prioritets ordning än den ursprungliga filen. Mer information finns i [Update-FormatData](xref:Microsoft.PowerShell.Utility.Update-FormatData).

```powershell
Update-FormatData -PrependPath $PSHOME\MyDotNetTypes.Format.ps1xml
```

Testa ändringen genom att skriva `Get-Culture` och granska utdata som innehåller **kalender** egenskapen.

```powershell
Get-Culture
```

```Output
LCID Name  Calendar                               DisplayName
---- ----  --------                               -----------
1033 en-US System.Globalization.GregorianCalendar English (United States)
```

## <a name="the-xml-in-formatps1xml-files"></a>XML i Format.ps1XML-filer

Du hittar fullständig schema definition i [formatet. xsd](https://github.com/PowerShell/PowerShell/blob/master/src/Schemas/Format.xsd) i PowerShell-källkoden på GitHub.

Avsnittet **ViewDefinitions** i varje `Format.ps1xml` fil innehåller de `<View>` taggar som definierar varje vy. En typisk `<View>` tagg innehåller följande Taggar:

- `<Name>` identifierar namnet på vyn.
- `<ViewSelectedBy>` anger objekt typen eller typerna som vyn gäller för.
- `<GroupBy>` anger hur objekt i vyn ska kombineras i grupper.
- `<TableControl>`, `<ListControl>` , `<WideControl>` och `<CustomControl>` innehåller taggarna som anger hur varje objekt ska visas.

### <a name="viewselectedby-tag"></a>ViewSelectedBy-tagg

`<ViewSelectedBy>`Taggen kan innehålla en `<TypeName>` tagg för varje objekt typ som vyn gäller för. Eller så kan den innehålla en `<SelectionSetName>` tagg som refererar till en urvals uppsättning som definieras någon annan stans genom att använda en- `<SelectionSet>` tagg.

### <a name="groupby-tag"></a>GroupBy-tagg

`<GroupBy>`Taggen innehåller en `<PropertyName>` tagg som anger den objekt egenskap enligt vilken objekten ska grupperas. Den innehåller också antingen en `<Label>` tagg som anger en sträng som ska användas som en etikett för varje grupp eller en `<CustomControlName>` tagg som refererar till en anpassad kontroll som definierats någon annan stans med en `<Control>` tagg. `<Control>`Taggen innehåller en `<Name>` tagg och en `<CustomControl>` tagg.

### <a name="tablecontroltag"></a>TableControlTag

`<TableControl>`Taggen innehåller vanligt vis `<TableHeaders>` och `<TableRowEntries>` taggar som definierar formateringen för tabellens huvuden och rader. `<TableHeaders>`Taggen innehåller vanligt vis `<TableColumnHeader>` taggar som innehåller `<Label>` `<Width>` taggar, och `<Alignment>` . `<TableRowEntries>`Taggen innehåller `<TableRowEntry>` taggar för varje rad i tabellen. `<TableRowEntry>`Taggen innehåller en `<TableColumnItems>` tagg som innehåller en `<TableColumnItem>` tagg för varje kolumn på raden. Normalt `<TableColumnItem>` innehåller taggen en `<PropertyName>` tagg som identifierar objekt egenskapen som ska visas på den definierade platsen, eller en `<ScriptBlock>` tagg som innehåller skript kod som beräknar ett resultat som ska visas på platsen.

> [!NOTE]
> Skript block kan också användas på andra platser på platser där beräknade resultat kan vara användbara.

`<TableColumnItem>`Taggen kan också innehålla en `<FormatString>` tagg som anger hur egenskapen eller de beräknade resultaten ska visas.

### <a name="listcontrol-tag"></a>ListControl-tagg

`<ListControl>`Taggen innehåller vanligt vis en `<ListEntries>` tagg. `<ListEntries>`Taggen innehåller en `<ListEntry>` tagg. `<ListEntry>`Taggen innehåller en `<ListItems>` tagg. `<ListItems>`Taggen innehåller `<ListItem>` taggar som innehåller `<PropertyName>` taggar. `<PropertyName>`Taggarna anger vilken objekt egenskap som ska visas på den angivna platsen i listan. Om visnings valet definieras med en urvals uppsättning `<ListControl>` `<ListEntry>` kan taggarna och också innehålla en `<EntrySelectedBy>` tagg som innehåller en eller flera `<TypeName>` taggar. `<TypeName>`Taggarna anger vilken objekt typ `<ListControl>` taggen är avsedd att visa.

### <a name="widecontrol-tag"></a>WideControl-tagg

`<WideControl>`Taggen innehåller vanligt vis en `<WideEntries>` tagg. `<WideEntries>`Taggen innehåller en eller flera `<WideEntry>` taggar. En- `<WideEntry>` tagg innehåller vanligt vis en `<PropertyName>` tagg som anger den egenskap som ska visas på den angivna platsen i vyn. `<PropertyName>`Taggen kan innehålla en `<FormatString>` tagg som anger hur egenskapen ska visas.

### <a name="customcontrol-tag"></a>CustomControl-tagg

Med `<CustomControl>` taggen kan du definiera ett format genom att använda ett-skript block. En- `<CustomControl>` tagg innehåller vanligt vis en `<CustomEntries>` tagg som innehåller flera `<CustomEntry>` taggar. Varje- `<CustomEntry>` tagg innehåller en `<CustomItem>` tagg som kan innehålla en rad olika taggar som anger innehåll och formatering för den angivna platsen i vyn, inklusive `<Text>` , `<Indentation>` , `<ExpressionBinding>` och `<NewLine>` taggar.

## <a name="default-displays-in-typesps1xml"></a>Standard visas i Types.ps1XML

Standard visningen av vissa grundläggande objekt typer definieras i `Types.ps1xml` filen i `$PSHOME` katalogen. Noderna heter **PsStandardMembers** och undernoderna använder någon av följande Taggar:

- `<DefaultDisplayProperty>`
- `<DefaultDisplayPropertySet>`
- `<DefaultKeyPropertySet>`

Mer information finns i [about_Types.ps1XML](about_Types.ps1xml.md).

## <a name="tracing-formatps1xml-file-use"></a>Använda spårning Format.ps1XML-fil

Om du vill identifiera fel vid inläsning eller tillämpning av `Format.ps1xml` filer använder du `Trace-Command` cmdleten med någon av följande format komponenter som värde för parametern **Name** :

- FormatFileLoading
- FormatViewBinding

Mer information finns i [trace-Command](xref:Microsoft.PowerShell.Utility.Trace-Command) och [Get-TraceSource](xref:Microsoft.PowerShell.Utility.Get-TraceSource).

## <a name="signing-a-formatps1xml-file"></a>Signera en Format.ps1XML-fil

Du skyddar användare av `Format.ps1xml` filen genom att signera filen med en digital signatur. Mer information finns i [about_Signing](about_Signing.md).

## <a name="sample-xml-for-a-format-table-custom-view"></a>Exempel-XML för en Format-Table anpassad vy

I följande exempel skapas en `Format-Table` anpassad vy för objekten **system. io. DirectoryInfo** och **system. io. fileinfo** som skapats av `Get-ChildItem` . Den anpassade vyn heter **mygciview** och lägger till **CreationTime** -kolumnen i tabellen.

Den anpassade vyn skapas från en redige rad version av `FileSystem.Format.ps1xml` filen som lagras i `$PSHOME` på PowerShell 5,1.

När din anpassade `.ps1xml` fil har sparats använder `Update-FormatData` du för att inkludera vyn i en PowerShell-session. I det här exemplet måste den anpassade vyn använda tabell formatet, annars `Format-Table` Miss lyckas.

Använd `Format-Table` med parametern **View** för att ange den anpassade vyns namn och formatera tabellens utdata. Ett exempel på hur kommandot körs finns i [Format-Table](xref:Microsoft.PowerShell.Utility.Format-Table).

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
> För att anpassa XML-exemplet inom gränserna för linje bredd var det nödvändigt att komprimera vissa indrag och använda rad brytningar i koden.

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

## <a name="see-also"></a>Se även

[Exportera – FormatData](xref:Microsoft.PowerShell.Utility.Export-FormatData)

[Get-FormatData](xref:Microsoft.PowerShell.Utility.Get-FormatData)

[Get-TraceSource](xref:Microsoft.PowerShell.Utility.Get-TraceSource)

[XML-referens för formatschema](/powershell/scripting/developer/format/format-schema-xml-reference)

[Spåra-kommando](xref:Microsoft.PowerShell.Utility.Trace-Command)

[Uppdatera – FormatData](xref:Microsoft.PowerShell.Utility.Update-FormatData)

[Skriva en PowerShell-formateringsfil](/powershell/scripting/developer/format/writing-a-powershell-formatting-file)
