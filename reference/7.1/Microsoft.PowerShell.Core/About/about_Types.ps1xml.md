---
description: Förklarar hur du använder `Types.ps1xml` filer för att utöka de typer av objekt som används i PowerShell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 04/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_types.ps1xml?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Types.ps1XML
ms.openlocfilehash: 66c319a6f1e84fb2d7aeea60433a2ddea9fb4616
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93271274"
---
# <a name="about-typesps1xml"></a>Om Types.ps1XML

## <a name="short-description"></a>Kort beskrivning
Förklarar hur du använder `Types.ps1xml` filer för att utöka de typer av objekt som används i PowerShell.

## <a name="long-description"></a>Lång beskrivning

Utökade typ data definierar ytterligare egenskaper och metoder ("medlemmar") för objekt typer i PowerShell. Det finns två metoder för att lägga till utökade typ data till en PowerShell-session.

- `Types.ps1xml` fil: en XML-fil som definierar utökade typ data.
- `Update-TypeData`: En cmdlet som laddar `Types.ps1xml` om filer och definierar utökade data för typer i den aktuella sessionen.

I det här avsnittet beskrivs `Types.ps1xml` filer. Mer information om hur du använder `Update-TypeData` cmdleten för att lägga till dynamiska utökade typ data till den aktuella sessionen finns i [Update-TypeData](xref:Microsoft.PowerShell.Utility.Update-TypeData).

## <a name="about-extended-type-data"></a>Om utökade typ data

Utökade typ data definierar ytterligare egenskaper och metoder ("medlemmar") för objekt typer i PowerShell. Du kan utöka vilken typ som helst som stöds av PowerShell och använda de egenskaper och metoder som har lagts till på samma sätt som du använder de egenskaper som definierats för objekt typerna.

Exempelvis lägger PowerShell till en **datetime** -egenskap till alla `System.DateTime` objekt, till exempel de som `Get-Date` cmdleten returnerar.

```powershell
(Get-Date).DateTime
```

```Output
Sunday, January 29, 2012 9:43:57 AM
```

Du hittar inte egenskapen **datetime** i beskrivningen av [system. DateTime](/dotnet/api/system.datetime) -strukturen eftersom PowerShell lägger till egenskapen och den är endast synlig i PowerShell.

PowerShell definierar internt en standard uppsättning av utökade typer. Den här typen av information läses in i varje PowerShell-session vid start. **Datetime** -egenskapen ingår i den här standard uppsättningen. Före PowerShell 6 sparade typ definitionerna `Types.ps1xml` i filen i installations katalogen för PowerShell ( `$PSHOME` ).

## <a name="adding-extended-type-data-to-powershell"></a>Lägga till utökade typ data till PowerShell

Det finns tre källor av utökade typ data i PowerShell-sessioner.

- Den definieras av PowerShell och läses in automatiskt i varje PowerShell-session. Från och med PowerShell 6, kompileras den här informationen till PowerShell och levereras inte längre i en `Types.ps1xml` fil.

- `Types.ps1xml`Filerna som moduler exporterar läses in när modulen importeras till den aktuella sessionen.

- Utökade typ data som definieras med hjälp av `Update-TypeData` cmdleten läggs bara till i den aktuella sessionen. Den sparas inte i en fil.

I sessionen tillämpas utökade typ data från de tre källorna på objekt på samma sätt och är tillgängliga för alla objekt av de angivna typerna.

## <a name="the-typedata-cmdlets"></a>TypeData-cmdletar

Följande cmdletar ingår i **Microsoft. PowerShell. Utility** -modulen i PowerShell 3,0 och senare.

- `Get-TypeData`: Hämtar utökade typ data i den aktuella sessionen.
- `Update-TypeData`: Filer läses in på nytt `Types.ps1xml` . Lägger till utökade typ data till den aktuella sessionen.
- `Remove-TypeData`: Tar bort utökade typ data från den aktuella sessionen.

Mer information om dessa cmdlets finns i hjälp avsnittet för varje cmdlet.

## <a name="built-in-typesps1xml-files"></a>Inbyggda Types.ps1XML-filer

`Types.ps1xml`Filerna i `$PSHOME` katalogen läggs automatiskt till i varje session.

`Types.ps1xml`Filen i PowerShell-installationsmappen ( `$PSHOME` ) är en XML-baserad textfil som låter dig lägga till egenskaper och metoder till de objekt som används i PowerShell. PowerShell har inbyggda `Types.ps1xml` filer som lägger till flera element i .net-typerna, men du kan skapa ytterligare `Types.ps1xml` filer för att utöka typerna ytterligare.

Som standard har till exempel mat ris objekt ( `System.Array` ) en **length** -egenskap som visar antalet objekt i matrisen. Men eftersom namn **längden** inte tydligt beskriver egenskapen, lägger PowerShell till en alias egenskap med namnet **Count** som visar samma värde. Följande XML lägger till egenskapen **Count** till `System.Array` typen.

```xml
<Type>
  <Name>System.Array</Name>
  <Members>
    <AliasProperty>
      <Name>Count</Name>
      <ReferencedMemberName>
        Length
      </ReferencedMemberName>
    </AliasProperty>
  </Members>
</Type>
```

Om du vill hämta den nya **AliasProperty** använder du ett `Get-Member` kommando på valfri matris, som du ser i följande exempel.

```powershell
Get-Member -InputObject (1,2,3,4)
```

Kommandot returnerar följande resultat.

```Output
Name       MemberType    Definition
----       ----------    ----------
Count      AliasProperty Count = Length
Address    Method        System.Object& Address(Int32)
Clone      Method        System.Object Clone()
CopyTo     Method        System.Void CopyTo(Array array, Int32 index):
Equals     Method        System.Boolean Equals(Object obj)
Get        Method        System.Object Get(Int32)
# ...
```

Det innebär att du kan använda antingen **Count** -egenskapen eller **length** -egenskapen för matriser i PowerShell. Ett exempel:

```powershell
(1, 2, 3, 4).count
4
```

```powershell
(1, 2, 3, 4).length
4
```

## <a name="creating-new-typesps1xml-files"></a>Skapa nya Types.ps1XML-filer

De `.ps1xml` filer som installeras med PowerShell signeras digitalt för att förhindra manipulering eftersom formateringen kan innehålla skript block. Om du vill lägga till en egenskap eller metod till en .NET-typ skapar du därför dina egna `Types.ps1xml` filer och lägger sedan till dem i PowerShell-sessionen.

Börja med att kopiera en befintlig fil för att skapa en ny fil `Types.ps1xml` . Den nya filen kan ha vilket namn som helst, men den måste ha ett `.ps1xml` fil namns tillägg. Du kan placera den nya filen i valfri katalog som är tillgänglig för PowerShell, men det är användbart att placera filerna i installations katalogen för PowerShell ( `$PSHOME` ) eller i en under katalog i installations katalogen.

När du har sparat den nya filen använder du `Update-TypeData` cmdleten för att lägga till den nya filen i PowerShell-sessionen. Om du vill att dina typer ska prioriteras över de inbyggda typer som har definierats använder du parametern **PrependData** för `Update-TypeData` cmdleten. `Update-TypeData` påverkar endast den aktuella sessionen. Om du vill göra ändringen i alla framtida sessioner exporterar du konsolen eller lägger till `Update-TypeData` kommandot i din PowerShell-profil.

## <a name="typesps1xml-and-add-member"></a>Types.ps1XML och Add-Member

`Types.ps1xml`Filerna lägger till egenskaper och metoder till alla instanser av objekten av den angivna .net-typen i den berörda PowerShell-sessionen. Men om du bara behöver lägga till egenskaper eller metoder till en instans av ett objekt, använder du `Add-Member` cmdleten.

Mer information finns i avsnittet om att [lägga till medlemmar](xref:Microsoft.PowerShell.Utility.Add-Member).

## <a name="example-adding-an-age-member-to-fileinfo-objects"></a>Exempel: lägga till en ålders medlem i FileInfo-objekt

Det här exemplet visar hur du lägger till en **ålders** egenskap i **system. io. fileinfo** -objekt. En fils ålder är skillnaden mellan tidpunkten för skapandet och den aktuella tiden i dagar.

Eftersom **ålders** egenskapen beräknas med hjälp av ett-skript block, hittar du en `<ScriptProperty>` tagg som ska användas som modell för den nya **ålders** egenskapen.

Spara följande XML-kod i filen `$PSHOME\MyTypes.ps1xml` .

```xml
<?xml version="1.0" encoding="utf-8" ?>
<Types>
  <Type>
    <Name>System.IO.FileInfo</Name>
    <Members>
      <ScriptProperty>
        <Name>Age</Name>
        <GetScriptBlock>
          ((Get-Date) - ($this.CreationTime)).Days
        </GetScriptBlock>
      </ScriptProperty>
    </Members>
  </Type>
</Types>
```

Kör `Update-TypeData` för att lägga till den nya `Types.ps1xml` filen i den aktuella sessionen. Kommandot använder parametern **PrependData** för att placera den nya filen i prioritetsordning högre än de ursprungliga definitionerna.

Mer information om `Update-TypeData` finns i [Update-TypeData](xref:Microsoft.PowerShell.Utility.Update-TypeData).

```powershell
Update-Typedata -PrependPath $PSHOME\MyTypes.ps1xml
```

Testa ändringen genom att köra ett `Get-ChildItem` kommando för att hämta PowerShell.exe-filen i `$PSHOME` katalogen och sedan skicka filen till `Format-List` cmdleten för att visa alla egenskaper för filen. På grund av ändringen visas **ålders** egenskapen i listan.

```powershell
Get-ChildItem $PSHOME\pwsh.exe | Select-Object Age
```

```Output
142
```

## <a name="the-xml-in-typesps1xml-files"></a>XML i Types.ps1XML-filer

Du hittar fullständig schema definition i [types. xsd](https://github.com/PowerShell/PowerShell/blob/master/src/Schemas/Types.xsd) i PowerShell-källkoden på GitHub.

`<Types>`Taggen innesluter alla typer som har definierats i filen. Det får bara finnas en `<Types>` tagg.

Varje .NET-typ som anges i filen ska representeras av en `<Type>` tagg.

Taggarna Type måste innehålla följande Taggar:

`<Name>`: Anger namnet på den berörda .NET-typen.

`<Members>`: Taggar för de nya egenskaper och metoder som har definierats för .NET-typen.

Någon av följande medlems taggar kan finnas inuti `<Members>` taggen.

`<AliasProperty>`: Definierar ett nytt namn för en befintlig egenskap.

`<AliasProperty>`Taggen måste ha en `<Name>` tagg som anger namnet på den nya egenskapen och en `<ReferencedMemberName>` tagg som anger den befintliga egenskapen.

Till exempel är **Count** -egenskapen alias ett alias för egenskapen **length** för Array-objekt.

```xml
<Type>
  <Name>System.Array</Name>
  <Members>
    <AliasProperty>
      <Name>Count</Name>
      <ReferencedMemberName>Length</ReferencedMemberName>
    </AliasProperty>
  </Members>
</Type>
```

`<CodeMethod>`: Refererar till en statisk metod för en .NET-klass.

`<CodeMethod>`Taggen måste ha en `<Name>` tagg som anger namnet på den nya metoden och en `<GetCodeReference>` tagg som anger koden där metoden definieras.

Till exempel är egenskapen **mode** för `System.IO.DirectoryInfo` objekt en kod egenskap som definierats i PowerShell-fil leverantören.

```xml
<Type>
  <Name>System.IO.DirectoryInfo</Name>
  <Members>
    <CodeProperty>
      <Name>Mode</Name>
      <GetCodeReference>
        <TypeName>
          Microsoft.PowerShell.Commands.FileSystemProvider
        </TypeName>
        <MethodName>Mode</MethodName>
      </GetCodeReference>
    </CodeProperty>
  </Members>
</Type>
```

`<CodeProperty>`: Refererar till en statisk metod för en .NET-klass.

`<CodeProperty>`Taggen måste ha en `<Name>` tagg som anger namnet på den nya egenskapen och en `<GetCodeReference>` tagg som anger koden där egenskapen definieras.

Till exempel är egenskapen **mode** för `System.IO.DirectoryInfo` objekt en kod egenskap som definierats i PowerShell-fil leverantören.

```xml
<Type>
  <Name>System.IO.DirectoryInfo</Name>
  <Members>
    <CodeProperty>
      <Name>Mode</Name>
      <GetCodeReference>
        <TypeName>
          Microsoft.PowerShell.Commands.FileSystemProvider
        </TypeName>
        <MethodName>Mode</MethodName>
      </GetCodeReference>
    </CodeProperty>
  </Members>
</Type>
```

`<MemberSet>`: Definierar en samling medlemmar (egenskaper och metoder).

`<MemberSet>`Taggarna visas i de primära `<Members>` taggarna. Taggarna måste omge en `<Name>` tagg som omger namnet på medlems uppsättningen och en sekundär `<Members>` tagg som omger medlemmar (egenskaper och metoder) i uppsättningen. Alla Taggar som skapar en egenskap (till exempel `<NoteProperty>` eller `<ScriptProperty>` ) eller en metod (till exempel `<Method>` eller `<ScriptMethod>` ) kan vara medlemmar i uppsättningen.

I `Types.ps1xml` filer `<MemberSet>` används taggen för att definiera standardvyerna för .net-objekt i PowerShell. I det här fallet är namnet på medlems uppsättningen (värdet i `<Name>` taggarna) alltid **PsStandardMembers** och namnen på egenskaperna (värdet för `<Name>` taggen) är något av följande:

- `DefaultDisplayProperty`: En enskild egenskap för ett objekt.

- `DefaultDisplayPropertySet`: En eller flera egenskaper för ett objekt.

- `DefaultKeyPropertySet`: En eller flera nyckel egenskaper för ett objekt. En nyckel egenskap identifierar instanser av egenskaps värden, t. ex. ID-antal objekt i en tidigare session.

Följande XML definierar till exempel standard visning av tjänster ( `System.ServiceProcess.ServiceController` objekt) som returneras av `Get-Service` cmdleten. Den definierar en medlems uppsättning med namnet **PsStandardMembers** som består av en standard egenskap som har angetts med egenskaperna **status** , **Name** och **DisplayName** .

```xml
<Type>
  <Name>System.ServiceProcess.ServiceController</Name>
  <Members>
    <MemberSet>
      <Name>PSStandardMembers</Name>
      <Members>
        <PropertySet>
          <Name>DefaultDisplayPropertySet</Name>
          <ReferencedProperties>
            <Name>Status</Name>
            <Name>Name</Name>
            <Name>DisplayName</Name>
          </ReferencedProperties>
        </PropertySet>
      </Members>
    </MemberSet>
  </Members>
</Type>
```

`<Method>`: Refererar till en ursprunglig metod för det underliggande objektet.

`<Methods>`: En samling av objektets metoder.

`<NoteProperty>`: Definierar en egenskap med ett statiskt värde.

`<NoteProperty>`Taggen måste ha en `<Name>` tagg som anger namnet på den nya egenskapen och en `<Value>` tagg som anger egenskapens värde.

Till exempel skapar följande XML en **status** egenskap för **system. io. DirectoryInfo** -objekt. Värdet för egenskapen **status** är alltid **klart**.

```xml
<Type>
  <Name>System.IO.DirectoryInfo</Name>
  <Members>
    <NoteProperty>
      <Name>Status</Name>
      <Value>Success</Value>
    </NoteProperty>
  </Members>
</Type>
```

`<ParameterizedProperty>`: Egenskaper som tar argument och returnerar ett värde.

`<Properties>`: En samling av objektets egenskaper.

`<Property>`: En egenskap för bas objekt.

`<PropertySet>`: Definierar en samling egenskaper för objektet.

`<PropertySet>`Taggen måste ha en `<Name>` tagg som anger namnet på egenskaps uppsättningen och en `<ReferencedProperty>` tagg som anger egenskaperna. Namnen på egenskaperna är omslutna i `<Name>` taggen.

I `Types.ps1xml` `<PropertySet>` används taggar för att definiera uppsättningar av egenskaper för standard visningen av ett objekt. Du kan identifiera standardvärden som visas genom värdet **PsStandardMembers** i `<Name>` taggen för en `<MemberSet>` tagg.

Till exempel skapar följande XML en **status** egenskap för `System.IO.DirectoryInfo` objektet. Värdet för egenskapen **status** är alltid **klart**.

```xml
<Type>
  <Name>System.ServiceProcess.ServiceController</Name>
  <Members>
    <MemberSet>
      <Name>PSStandardMembers</Name>
      <Members>
        <PropertySet>
          <Name>DefaultDisplayPropertySet</Name>
          <ReferencedProperties>
            <Name>Status</Name>
            <Name>Name</Name>
            <Name>DisplayName</Name>
          </ReferencedProperties>
        </PropertySet>
      </Members>
    </MemberSet>
  </Members>
</Type>
```

`<ScriptMethod>`: Definierar en metod vars värde är utdata från ett skript.

`<ScriptMethod>`Taggen måste ha en `<Name>` tagg som anger namnet på den nya metoden och en `<Script>` tagg som innesluter det skript block som returnerar metod resultatet.

Till exempel `ConvertToDateTime` `ConvertFromDateTime` är metoderna och för hanterings objekt ( `System.System.Management.ManagementObject` ) skript metoder som använder `ToDateTime` `ToDmtfDateTime` klassen och statiska metoder för `System.Management.ManagementDateTimeConverter` klassen.

```xml
<Type>
 <Name>System.Management.ManagementObject</Name>
 <Members>
 <ScriptMethod>
   <Name>ConvertToDateTime</Name>
   <Script>
   [System.Management.ManagementDateTimeConverter]::ToDateTime($args[0])
   </Script>
 </ScriptMethod>
 <ScriptMethod>
   <Name>ConvertFromDateTime</Name>
   <Script>
   [System.Management.ManagementDateTimeConverter]::ToDmtfDateTime($args[0])
   </Script>
 </ScriptMethod>
 </Members>
</Type>
```

`<ScriptProperty>`: Definierar en egenskap vars värde är utdata från ett skript.

`<ScriptProperty>`Taggen måste ha en `<Name>` tagg som anger namnet på den nya egenskapen och en `<GetScriptBlock>` tagg som innesluter det skript block som returnerar egenskap svärdet.

Till exempel är egenskapen **VersionInfo** för objektet **system. io. fileinfo** en skript egenskap som resulterar i att du använder egenskapen **FullName** för den **GetVersionInfo** statiska metoden **system. Diagnostics. FileVersionInfo** .

```xml
<Type>
  <Name>System.IO.FileInfo</Name>
  <Members>
    <ScriptProperty>
      <Name>VersionInfo</Name>
      <GetScriptBlock>
      [System.Diagnostics.FileVersionInfo]::GetVersionInfo($this.FullName)
      </GetScriptBlock>
    </ScriptProperty>
  </Members>
</Type>
```

Mer information finns i [Windows PowerShell Software Development Kit (SDK)](/powershell/scripting/developer/windows-powershell).

## <a name="update-typedata"></a>Update-TypeData

Kör cmdleten om du vill läsa in dina `Types.ps1xml` filer i en PowerShell-session `Update-TypeData` . Om du vill att typerna i filen ska prioriteras över typer i den inbyggda `Types.ps1xml` filen lägger du till parametern **PrependData** i `Update-TypeData` . `Update-TypeData` påverkar endast den aktuella sessionen. Om du vill göra ändringen i alla framtida sessioner exporterar du sessionen eller lägger till `Update-TypeData` kommandot i din PowerShell-profil.

Undantag som inträffar i egenskaper, eller genom att lägga till egenskaper till ett `Update-TypeData` kommando, rapportera inte fel till `StdErr` . Detta är att utelämna undantag som skulle uppstå i många vanliga typer vid formatering och utmatning. Om du får .NET-egenskaper kan du undvika att utelämna undantag genom att använda metoden syntax i stället, som du ser i följande exempel:

```powershell
"hello".get_Length()
```

Observera att metoden syntax bara kan användas med .NET-egenskaper. Egenskaper som läggs till genom att köra `Update-TypeData` cmdleten kan inte använda Method-syntax.

## <a name="signing-a-typesps1xml-file"></a>Signera en Types.ps1XML-fil

För att skydda användare av `Types.ps1xml` filen kan du signera filen med en digital signatur. Mer information finns i [about_Signing](about_Signing.md).

## <a name="see-also"></a>Se även

[about_Signing](about_Signing.md)

[Kopiera objekt](xref:Microsoft.PowerShell.Management.Copy-Item)

[Kopiera – ItemProperty](xref:Microsoft.PowerShell.Management.Copy-ItemProperty)

[Hämta medlem](xref:Microsoft.PowerShell.Utility.Get-Member)

[Get-TypeData](xref:Microsoft.PowerShell.Utility.Get-TypeData)

[Remove-TypeData](xref:Microsoft.PowerShell.Utility.Remove-TypeData)

[Uppdatera – TypeData](xref:Microsoft.PowerShell.Utility.Update-TypeData)

