---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/select-xml?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Select-Xml
ms.openlocfilehash: 7e3d02dedb9f7809a8f8e1c657987fef8ec38fa9
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94387999"
---
# Select-Xml

## SAMMANFATTNING
Söker efter text i en XML-sträng eller ett dokument.

## SYNTAX

### XML (standard)

```
Select-Xml [-Xml] <XmlNode[]> [-XPath] <String> [-Namespace <Hashtable>] [<CommonParameters>]
```

### Sökväg

```
Select-Xml [-Path] <String[]> [-XPath] <String> [-Namespace <Hashtable>] [<CommonParameters>]
```

### LiteralPath

```
Select-Xml -LiteralPath <String[]> [-XPath] <String> [-Namespace <Hashtable>] [<CommonParameters>]
```

### Innehåll

```
Select-Xml -Content <String[]> [-XPath] <String> [-Namespace <Hashtable>] [<CommonParameters>]
```

## BESKRIVNING

Med **Select-XML-** cmdleten kan du använda XPath-frågor för att söka efter text i XML-strängar och dokument.
Ange en XPath-fråga och Använd *innehållet* , *sökvägen* eller *XML* -parametern för att ange XML-koden som ska genomsökas.

## EXEMPEL

### Exempel 1: Välj AliasProperty-noder

```
PS C:\> $Path = "$Pshome\Types.ps1xml"
PS C:\> $XPath = "/Types/Type/Members/AliasProperty"
PS C:\> Select-Xml -Path $Path -XPath $Xpath | Select-Object -ExpandProperty Node
Name                 ReferencedMemberName
----                 --------------------
Count                Length
Name                 Key
Name                 ServiceName
RequiredServices     ServicesDependedOn
ProcessName          Name
Handles              Handlecount
VM                   VirtualSize
WS                   WorkingSetSize
Name                 ProcessName
Handles              Handlecount
VM                   VirtualMemorySize
WS                   WorkingSet
PM                   PagedMemorySize
NPM                  NonpagedSystemMemorySize
Name                 __Class
Namespace            ModuleName
```

I det här exemplet hämtas egenskaperna för alias i Types.ps1XML.
(Mer information om den här filen finns i about_Types.ps1XML.)

Det första kommandot sparar sökvägen till Types.ps1XML-filen i $Path variabeln.

Det andra kommandot sparar XML-sökvägen till AliasProperty-noden i variabeln $XPath.

Det tredje kommandot använder **Select-XML** -cmdleten för att hämta de AliasProperty-noder som identifieras av XPath-instruktionen från Types.ps1XML-filen.
Kommandot använder en pipeline-operator för att skicka AliasProperty-noderna till Select-Object-cmdleten.
Parametern *ExpandProperty* utökar objektet **Node** och returnerar dess namn och ReferencedMemberName egenskaper.

Resultatet visar namnet och ReferencedMemberName för varje aliasresurspost i Types.ps1XML-filen.
Det finns till exempel en **Count** -egenskap som är ett alias för egenskapen **length** .

### Exempel 2: mata in ett XML-dokument

```
PS C:\> [xml]$Types = Get-Content $Pshome\Types.ps1xml
PS C:\> Select-Xml -Xml $Types -XPath "//MethodName"
```

Det här exemplet visar hur du använder *XML-* parametern för att tillhandahålla ett XML-dokument till **Select-XML-** cmdleten.

Det första kommandot använder cmdleten Get-Content för att hämta innehållet i Types.ps1XML-filen och spara den i $Types variabeln.
\[XML-koden \] kastar variabeln som ett XML-objekt.

Det andra kommandot använder **Select-XML** -cmdlet: en för att hämta methodName-noderna i Types.ps1XML-filen.
Kommandot använder *XML-* parametern för att ange XML-innehållet i variabeln $types och *XPath* -parametern för att ange sökvägen till methodName-noden.

### Exempel 3: Sök efter PowerShell-hjälpfiler

```
PS C:\> $Namespace = @{command = "http://schemas.microsoft.com/maml/dev/command/2004/10"; maml = "http://schemas.microsoft.com/maml/2004/10"; dev = "http://schemas.microsoft.com/maml/dev/2004/10"}

The second command saves the path to the help files in the $Path variable.If there are no help files in this path on your computer, use the Update-Help cmdlet to download the help files. For more information about Updatable Help, see about_Updatable_Help (https://go.microsoft.com/fwlink/?LinkId=235801).
PS C:\> $Path = "$Pshome\en-us\*dll-Help.xml"

The third command uses the **Select-Xml** cmdlet to search the XML for cmdlet names by finding Command:Name element anywhere in the files. It saves the results in the $Xml variable.**Select-Xml** returns a **SelectXmlInfo** object that has a Node property, which is a **System.Xml.XmlElement** object. The Node property has an InnerXML property, which contains the actual XML that is retrieved.
PS C:\> $Xml = Select-Xml -Path $Path -Namespace $Namespace -XPath "//command:name"

The fourth command sends the XML in the $Xml variable to the Format-Table cmdlet. The **Format-Table** command uses a calculated property to get the Node.InnerXML property of each object in the $Xml variable, trim the white space before and after the text, and display it in the table, along with the path to the source file.
PS C:\> $Xml | Format-Table @{Label="Name"; Expression= {($_.node.innerxml).trim()}}, Path -AutoSize

Name                    Path
----                    ----
Export-Counter          C:\Windows\system32\WindowsPowerShell\v1.0\en-us\Microsoft.PowerShell.Commands.Diagnostics.dll-Help.xml
Get-Counter             C:\Windows\system32\WindowsPowerShell\v1.0\en-us\Microsoft.PowerShell.Commands.Diagnostics.dll-Help.xml
Get-WinEvent            C:\Windows\system32\WindowsPowerShell\v1.0\en-us\Microsoft.PowerShell.Commands.Diagnostics.dll-Help.xml
Import-Counter          C:\Windows\system32\WindowsPowerShell\v1.0\en-us\Microsoft.PowerShell.Commands.Diagnostics.dll-Help.xml
Add-Computer            C:\Windows\system32\WindowsPowerShell\v1.0\en-us\Microsoft.PowerShell.Commands.Management.dll-Help.xml
Add-Content             C:\Windows\system32\WindowsPowerShell\v1.0\en-us\Microsoft.PowerShell.Commands.Management.dll-Help.xml
Checkpoint-Computer     C:\Windows\system32\WindowsPowerShell\v1.0\en-us\Microsoft.PowerShell.Commands.Management.dll-Help.xml
...
```

Det här exemplet visar hur du använder **Select-XML** -cmdleten för att söka i Hjälp filerna för PowerShell-baserad cmdlet-baserad cmdlet.
I det här exemplet ska vi söka efter det cmdlet-namn som fungerar som en rubrik för varje hjälpfil och sökvägen till hjälp filen.

Det första kommandot skapar en hash-tabell som representerar det XML-namnområde som används för hjälpfilerna och sparar det i $Namespace-variabeln.

### Exempel 4: olika sätt att mata in XML

```
PS C:\> $Xml = @"
<?xml version="1.0" encoding="utf-8"?>
<Book>
  <projects>
    <project name="Book1" date="2009-01-20">
      <editions>
        <edition language="English">En.Book1.com</edition>
        <edition language="German">Ge.Book1.Com</edition>
        <edition language="French">Fr.Book1.com</edition>
        <edition language="Polish">Pl.Book1.com</edition>
      </editions>
    </project>
  </projects>
</Book>
"@

The second command uses the *Content* parameter of **Select-Xml** to specify the XML in the $Xml variable.
PS C:\> Select-Xml -Content $Xml -XPath "//edition" | foreach {$_.node.InnerXML}

En.Book1.com
Ge.Book1.Com
Fr.Book1.com
Pl.Book1.com

The third command is equivalent to the second. It uses a pipeline operator (|) to send the XML in the $Xml variable to the **Select-Xml** cmdlet.
PS C:\> $Xml | Select-Xml -XPath "//edition" | foreach {$_.node.InnerXML}

En.Book1.com
Ge.Book1.Com
Fr.Book1.com
Pl.Book1.com
```

I det här exemplet visas två olika sätt att skicka XML till **Select-XML-** cmdleten.

Det första kommandot sparar en här-sträng som innehåller XML i variabeln $Xml.
(Mer information om här – strängar finns i about_Quoting_Rules.)

### Exempel 5: Använd standard namn området xmlns

```
PS C:\> $SnippetNamespace = @{snip = "http://schemas.microsoft.com/PowerShell/Snippets"}

The second command uses the **Select-Xml** cmdlet to get the content of the Title element of each snippet. It uses the *Path* parameter to specify the Snippets directory and the *Namespace* parameter to specify the namespace in the $SnippetNamespace variable. The value of the *XPath* parameter is the "snip" namespace key, a colon (:), and the name of the Title element.The command uses a pipeline operator (|) to send each **Node** property that **Select-Xml** returns to the ForEach-Object cmdlet, which gets the title in the value of the **InnerXml** property of the node.
PS C:\> Select-Xml -Path $Home\Documents\WindowsPowerShell\Snippets -Namespace $SnippetNamespace -XPath "//snip:Title" | foreach {$_.Node.Innerxml}
```

Det här exemplet visar hur du använder **Select-XML** -cmdleten med XML-dokument som använder standardvärdet för xmlns-namnrymd.
Exemplet hämtar titlarna på Windows PowerShell ISE kodfragment-filer som skapats av användare.
Information om kodfragment finns i New-IseSnippet.

Det första kommandot skapar en hash-tabell för det standard namn område som XML-filerna använder och tilldelar dem till $SnippetNamespace variabeln.
Värdet för hash-tabellen är XMLNS-schemats URI i XML-kodfragmentet.
Hash-tabellens nyckel namn, skärm klipp, är godtyckligt.
Du kan använda ett namn som inte är reserverat, men du kan inte använda xmlns.

## PARAMETRAR

### – Innehåll

Anger en sträng som innehåller den XML som ska genomsökas.
Du kan också skicka en sträng till **Select-XML**.

```yaml
Type: System.String[]
Parameter Sets: Content
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -LiteralPath

Anger sökvägar och fil namn för de XML-filer som ska genomsökas.
Till skillnad från *sökväg* används värdet för parametern *LiteralPath* exakt som det har angetts.
Inga tecken tolkas som jokertecken.
Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.
Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### – Namnrymd

Anger en hash-tabell för de namn områden som används i XML-filen.
Använd formatet @ { \<namespaceName\>  =  \<namespaceValue\> }.

När XML använder standard namn området, som börjar med xmlns, använder du en godtycklig nyckel för namn områdets namn.
Du kan inte använda xmlns.
I XPath-instruktionen prefixerar du varje nodnamn med namn områdets namn och ett kolon, till exempel//namespaceName: Node.

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

Anger sökväg och fil namn för de XML-filer som ska genomsökas.
Jokertecken är tillåtna.

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -XML

Anger en eller flera XML-noder.

Ett XML-dokument kommer att bearbetas som en samling av XML-noder.
Om du rör ett XML-dokument för att **välja-XML** genomsöks varje dokument-nod separat när den kommer till pipelinen.

```yaml
Type: System.Xml.XmlNode[]
Parameter Sets: Xml
Aliases: Node

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### – XPath

Anger en XPath-Sök fråga.
Frågespråket är Skift läges känsligt.
Den här parametern är obligatorisk.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. String eller System.Xml.Xmlnod

Du kan skicka en sökväg eller XML-nod till denna cmdlet.

## UTDATA

### Microsoft. PowerShell. commands. SelectXmlInfo

## ANTECKNINGAR

XPath är ett standard språk som är utformat för att identifiera delar av ett XML-dokument. Mer information om XPath-språket finns i [XPath-referens](/dotnet/standard/data/xml/select-nodes-using-xpath-navigation) och urvals filter avsnittet i [händelse urvalet](/previous-versions//aa385231(v=vs.85)).

## RELATERADE LÄNKAR

[ConvertTo-Xml](ConvertTo-Xml.md)
