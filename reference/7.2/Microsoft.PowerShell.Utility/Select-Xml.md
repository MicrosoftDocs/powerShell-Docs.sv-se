---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/select-xml?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Select-Xml
ms.openlocfilehash: 7686ade747345b7c770772067007b8abf13aac3d
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708347"
---
# <span data-ttu-id="b6bba-102">Select-Xml</span><span class="sxs-lookup"><span data-stu-id="b6bba-102">Select-Xml</span></span>

## <span data-ttu-id="b6bba-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="b6bba-103">SYNOPSIS</span></span>
<span data-ttu-id="b6bba-104">Söker efter text i en XML-sträng eller ett dokument.</span><span class="sxs-lookup"><span data-stu-id="b6bba-104">Finds text in an XML string or document.</span></span>

## <span data-ttu-id="b6bba-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b6bba-105">SYNTAX</span></span>

### <span data-ttu-id="b6bba-106">XML (standard)</span><span class="sxs-lookup"><span data-stu-id="b6bba-106">Xml (Default)</span></span>

```
Select-Xml [-Xml] <XmlNode[]> [-XPath] <String> [-Namespace <Hashtable>] [<CommonParameters>]
```

### <span data-ttu-id="b6bba-107">Sökväg</span><span class="sxs-lookup"><span data-stu-id="b6bba-107">Path</span></span>

```
Select-Xml [-Path] <String[]> [-XPath] <String> [-Namespace <Hashtable>] [<CommonParameters>]
```

### <span data-ttu-id="b6bba-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="b6bba-108">LiteralPath</span></span>

```
Select-Xml -LiteralPath <String[]> [-XPath] <String> [-Namespace <Hashtable>] [<CommonParameters>]
```

### <span data-ttu-id="b6bba-109">Innehåll</span><span class="sxs-lookup"><span data-stu-id="b6bba-109">Content</span></span>

```
Select-Xml -Content <String[]> [-XPath] <String> [-Namespace <Hashtable>] [<CommonParameters>]
```

## <span data-ttu-id="b6bba-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="b6bba-110">DESCRIPTION</span></span>

<span data-ttu-id="b6bba-111">Med **Select-XML-** cmdleten kan du använda XPath-frågor för att söka efter text i XML-strängar och dokument.</span><span class="sxs-lookup"><span data-stu-id="b6bba-111">The **Select-Xml** cmdlet lets you use XPath queries to search for text in XML strings and documents.</span></span>
<span data-ttu-id="b6bba-112">Ange en XPath-fråga och Använd *innehållet*, *sökvägen* eller *XML* -parametern för att ange XML-koden som ska genomsökas.</span><span class="sxs-lookup"><span data-stu-id="b6bba-112">Enter an XPath query, and use the *Content*, *Path*, or *Xml* parameter to specify the XML to be searched.</span></span>

## <span data-ttu-id="b6bba-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="b6bba-113">EXAMPLES</span></span>

### <span data-ttu-id="b6bba-114">Exempel 1: Välj AliasProperty-noder</span><span class="sxs-lookup"><span data-stu-id="b6bba-114">Example 1: Select AliasProperty nodes</span></span>

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

<span data-ttu-id="b6bba-115">I det här exemplet hämtas egenskaperna för alias i Types.ps1XML.</span><span class="sxs-lookup"><span data-stu-id="b6bba-115">This example gets the alias properties in the Types.ps1xml.</span></span>
<span data-ttu-id="b6bba-116">(Mer information om den här filen finns i about_Types.ps1XML.)</span><span class="sxs-lookup"><span data-stu-id="b6bba-116">(For information about this file, see about_Types.ps1xml.)</span></span>

<span data-ttu-id="b6bba-117">Det första kommandot sparar sökvägen till Types.ps1XML-filen i $Path variabeln.</span><span class="sxs-lookup"><span data-stu-id="b6bba-117">The first command saves the path to the Types.ps1xml file in the $Path variable.</span></span>

<span data-ttu-id="b6bba-118">Det andra kommandot sparar XML-sökvägen till AliasProperty-noden i variabeln $XPath.</span><span class="sxs-lookup"><span data-stu-id="b6bba-118">The second command saves the XML path to the AliasProperty node in the $XPath variable.</span></span>

<span data-ttu-id="b6bba-119">Det tredje kommandot använder **Select-XML** -cmdleten för att hämta de AliasProperty-noder som identifieras av XPath-instruktionen från Types.ps1XML-filen.</span><span class="sxs-lookup"><span data-stu-id="b6bba-119">The third command uses the **Select-Xml** cmdlet to get the AliasProperty nodes that are identified by the XPath statement from the Types.ps1xml file.</span></span>
<span data-ttu-id="b6bba-120">Kommandot använder en pipeline-operator för att skicka AliasProperty-noderna till Select-Object-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="b6bba-120">The command uses a pipeline operator to send the AliasProperty nodes to the Select-Object cmdlet.</span></span>
<span data-ttu-id="b6bba-121">Parametern *ExpandProperty* utökar objektet **Node** och returnerar dess namn och ReferencedMemberName egenskaper.</span><span class="sxs-lookup"><span data-stu-id="b6bba-121">The *ExpandProperty* parameter expands the **Node** object and returns its Name and ReferencedMemberName properties.</span></span>

<span data-ttu-id="b6bba-122">Resultatet visar namnet och ReferencedMemberName för varje aliasresurspost i Types.ps1XML-filen.</span><span class="sxs-lookup"><span data-stu-id="b6bba-122">The result shows the Name and ReferencedMemberName of each alias property in the Types.ps1xml file.</span></span>
<span data-ttu-id="b6bba-123">Det finns till exempel en **Count** -egenskap som är ett alias för egenskapen **length** .</span><span class="sxs-lookup"><span data-stu-id="b6bba-123">For example, there is a **Count** property that is an alias of the **Length** property.</span></span>

### <span data-ttu-id="b6bba-124">Exempel 2: mata in ett XML-dokument</span><span class="sxs-lookup"><span data-stu-id="b6bba-124">Example 2: Input an XML document</span></span>

```
PS C:\> [xml]$Types = Get-Content $Pshome\Types.ps1xml
PS C:\> Select-Xml -Xml $Types -XPath "//MethodName"
```

<span data-ttu-id="b6bba-125">Det här exemplet visar hur du använder *XML-* parametern för att tillhandahålla ett XML-dokument till **Select-XML-** cmdleten.</span><span class="sxs-lookup"><span data-stu-id="b6bba-125">This example shows how to use the *XML* parameter to provide an XML document to the **Select-Xml** cmdlet.</span></span>

<span data-ttu-id="b6bba-126">Det första kommandot använder cmdleten Get-Content för att hämta innehållet i Types.ps1XML-filen och spara den i $Types variabeln.</span><span class="sxs-lookup"><span data-stu-id="b6bba-126">The first command uses the Get-Content cmdlet to get the content of the Types.ps1xml file and save it in the $Types variable.</span></span>
<span data-ttu-id="b6bba-127">\[XML-koden \] kastar variabeln som ett XML-objekt.</span><span class="sxs-lookup"><span data-stu-id="b6bba-127">The \[xml\] casts the variable as an XML object.</span></span>

<span data-ttu-id="b6bba-128">Det andra kommandot använder **Select-XML** -cmdlet: en för att hämta methodName-noderna i Types.ps1XML-filen.</span><span class="sxs-lookup"><span data-stu-id="b6bba-128">The second command uses the **Select-Xml** cmdlet to get the MethodName nodes in the Types.ps1xml file.</span></span>
<span data-ttu-id="b6bba-129">Kommandot använder *XML-* parametern för att ange XML-innehållet i variabeln $types och *XPath* -parametern för att ange sökvägen till methodName-noden.</span><span class="sxs-lookup"><span data-stu-id="b6bba-129">The command uses the *Xml* parameter to specify the XML content in the $Types variable and the *XPath* parameter to specify the path to the MethodName node.</span></span>

### <span data-ttu-id="b6bba-130">Exempel 3: Sök efter PowerShell-hjälpfiler</span><span class="sxs-lookup"><span data-stu-id="b6bba-130">Example 3: Search PowerShell Help files</span></span>

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

<span data-ttu-id="b6bba-131">Det här exemplet visar hur du använder **Select-XML** -cmdleten för att söka i Hjälp filerna för PowerShell-baserad cmdlet-baserad cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b6bba-131">This example shows how to use the **Select-Xml** cmdlet to search the PowerShell XML-based cmdlet help files.</span></span>
<span data-ttu-id="b6bba-132">I det här exemplet ska vi söka efter det cmdlet-namn som fungerar som en rubrik för varje hjälpfil och sökvägen till hjälp filen.</span><span class="sxs-lookup"><span data-stu-id="b6bba-132">In this example, we'll search for the cmdlet name that serves as a title for each help file and the path to the help file.</span></span>

<span data-ttu-id="b6bba-133">Det första kommandot skapar en hash-tabell som representerar det XML-namnområde som används för hjälpfilerna och sparar det i $Namespace-variabeln.</span><span class="sxs-lookup"><span data-stu-id="b6bba-133">The first command creates a hash table that represents the XML namespace that is used for the help files and saves it in the $Namespace variable.</span></span>

### <span data-ttu-id="b6bba-134">Exempel 4: olika sätt att mata in XML</span><span class="sxs-lookup"><span data-stu-id="b6bba-134">Example 4: Different ways to input XML</span></span>

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

<span data-ttu-id="b6bba-135">I det här exemplet visas två olika sätt att skicka XML till **Select-XML-** cmdleten.</span><span class="sxs-lookup"><span data-stu-id="b6bba-135">This example shows two different ways to send XML to the **Select-Xml** cmdlet.</span></span>

<span data-ttu-id="b6bba-136">Det första kommandot sparar en här-sträng som innehåller XML i variabeln $Xml.</span><span class="sxs-lookup"><span data-stu-id="b6bba-136">The first command saves a here-string that contains XML in the $Xml variable.</span></span>
<span data-ttu-id="b6bba-137">(Mer information om här – strängar finns i about_Quoting_Rules.)</span><span class="sxs-lookup"><span data-stu-id="b6bba-137">(For more information about here-strings, see about_Quoting_Rules.)</span></span>

### <span data-ttu-id="b6bba-138">Exempel 5: Använd standard namn området xmlns</span><span class="sxs-lookup"><span data-stu-id="b6bba-138">Example 5: Use the default xmlns namespace</span></span>

```
PS C:\> $SnippetNamespace = @{snip = "http://schemas.microsoft.com/PowerShell/Snippets"}

The second command uses the **Select-Xml** cmdlet to get the content of the Title element of each snippet. It uses the *Path* parameter to specify the Snippets directory and the *Namespace* parameter to specify the namespace in the $SnippetNamespace variable. The value of the *XPath* parameter is the "snip" namespace key, a colon (:), and the name of the Title element.The command uses a pipeline operator (|) to send each **Node** property that **Select-Xml** returns to the ForEach-Object cmdlet, which gets the title in the value of the **InnerXml** property of the node.
PS C:\> Select-Xml -Path $Home\Documents\WindowsPowerShell\Snippets -Namespace $SnippetNamespace -XPath "//snip:Title" | foreach {$_.Node.Innerxml}
```

<span data-ttu-id="b6bba-139">Det här exemplet visar hur du använder **Select-XML** -cmdleten med XML-dokument som använder standardvärdet för xmlns-namnrymd.</span><span class="sxs-lookup"><span data-stu-id="b6bba-139">This example shows how to use the **Select-Xml** cmdlet with XML documents that use the default xmlns namespace.</span></span>
<span data-ttu-id="b6bba-140">Exemplet hämtar titlarna på Windows PowerShell ISE kodfragment-filer som skapats av användare.</span><span class="sxs-lookup"><span data-stu-id="b6bba-140">The example gets the titles of Windows PowerShell ISE user-created snippet files.</span></span>
<span data-ttu-id="b6bba-141">Information om kodfragment finns i New-IseSnippet.</span><span class="sxs-lookup"><span data-stu-id="b6bba-141">For information about snippets, see New-IseSnippet.</span></span>

<span data-ttu-id="b6bba-142">Det första kommandot skapar en hash-tabell för det standard namn område som XML-filerna använder och tilldelar dem till $SnippetNamespace variabeln.</span><span class="sxs-lookup"><span data-stu-id="b6bba-142">The first command creates a hash table for the default namespace that snippet XML files use and assigns it to the $SnippetNamespace variable.</span></span>
<span data-ttu-id="b6bba-143">Värdet för hash-tabellen är XMLNS-schemats URI i XML-kodfragmentet.</span><span class="sxs-lookup"><span data-stu-id="b6bba-143">The hash table value is the XMLNS schema URI in the snippet XML.</span></span>
<span data-ttu-id="b6bba-144">Hash-tabellens nyckel namn, skärm klipp, är godtyckligt.</span><span class="sxs-lookup"><span data-stu-id="b6bba-144">The hash table key name, snip, is arbitrary.</span></span>
<span data-ttu-id="b6bba-145">Du kan använda ett namn som inte är reserverat, men du kan inte använda xmlns.</span><span class="sxs-lookup"><span data-stu-id="b6bba-145">You can use any name that is not reserved, but you cannot use xmlns.</span></span>

## <span data-ttu-id="b6bba-146">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="b6bba-146">PARAMETERS</span></span>

### <span data-ttu-id="b6bba-147">– Innehåll</span><span class="sxs-lookup"><span data-stu-id="b6bba-147">-Content</span></span>

<span data-ttu-id="b6bba-148">Anger en sträng som innehåller den XML som ska genomsökas.</span><span class="sxs-lookup"><span data-stu-id="b6bba-148">Specifies a string that contains the XML to search.</span></span>
<span data-ttu-id="b6bba-149">Du kan också skicka en sträng till **Select-XML**.</span><span class="sxs-lookup"><span data-stu-id="b6bba-149">You can also pipe strings to **Select-Xml**.</span></span>

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

### <span data-ttu-id="b6bba-150">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="b6bba-150">-LiteralPath</span></span>

<span data-ttu-id="b6bba-151">Anger sökvägar och fil namn för de XML-filer som ska genomsökas.</span><span class="sxs-lookup"><span data-stu-id="b6bba-151">Specifies the paths and file names of the XML files to search.</span></span>
<span data-ttu-id="b6bba-152">Till skillnad från *sökväg* används värdet för parametern *LiteralPath* exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="b6bba-152">Unlike *Path*, the value of the *LiteralPath* parameter is used exactly as it is typed.</span></span>
<span data-ttu-id="b6bba-153">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="b6bba-153">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="b6bba-154">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="b6bba-154">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="b6bba-155">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="b6bba-155">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b6bba-156">– Namnrymd</span><span class="sxs-lookup"><span data-stu-id="b6bba-156">-Namespace</span></span>

<span data-ttu-id="b6bba-157">Anger en hash-tabell för de namn områden som används i XML-filen.</span><span class="sxs-lookup"><span data-stu-id="b6bba-157">Specifies a hash table of the namespaces used in the XML.</span></span>
<span data-ttu-id="b6bba-158">Använd formatet @ { \<namespaceName\>  =  \<namespaceValue\> }.</span><span class="sxs-lookup"><span data-stu-id="b6bba-158">Use the format @{\<namespaceName\> = \<namespaceValue\>}.</span></span>

<span data-ttu-id="b6bba-159">När XML använder standard namn området, som börjar med xmlns, använder du en godtycklig nyckel för namn områdets namn.</span><span class="sxs-lookup"><span data-stu-id="b6bba-159">When the XML uses the default namespace, which begins with xmlns, use an arbitrary key for the namespace name.</span></span>
<span data-ttu-id="b6bba-160">Du kan inte använda xmlns.</span><span class="sxs-lookup"><span data-stu-id="b6bba-160">You cannot use xmlns.</span></span>
<span data-ttu-id="b6bba-161">I XPath-instruktionen prefixerar du varje nodnamn med namn områdets namn och ett kolon, till exempel//namespaceName: Node.</span><span class="sxs-lookup"><span data-stu-id="b6bba-161">In the XPath statement, prefix each node name with the namespace name and a colon, such as //namespaceName:Node.</span></span>

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

### <span data-ttu-id="b6bba-162">-Path</span><span class="sxs-lookup"><span data-stu-id="b6bba-162">-Path</span></span>

<span data-ttu-id="b6bba-163">Anger sökväg och fil namn för de XML-filer som ska genomsökas.</span><span class="sxs-lookup"><span data-stu-id="b6bba-163">Specifies the path and file names of the XML files to search.</span></span>
<span data-ttu-id="b6bba-164">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="b6bba-164">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="b6bba-165">-XML</span><span class="sxs-lookup"><span data-stu-id="b6bba-165">-Xml</span></span>

<span data-ttu-id="b6bba-166">Anger en eller flera XML-noder.</span><span class="sxs-lookup"><span data-stu-id="b6bba-166">Specifies one or more XML nodes.</span></span>

<span data-ttu-id="b6bba-167">Ett XML-dokument kommer att bearbetas som en samling av XML-noder.</span><span class="sxs-lookup"><span data-stu-id="b6bba-167">An XML document will be processed as a collection of XML nodes.</span></span>
<span data-ttu-id="b6bba-168">Om du rör ett XML-dokument för att **välja-XML** genomsöks varje dokument-nod separat när den kommer till pipelinen.</span><span class="sxs-lookup"><span data-stu-id="b6bba-168">If you pipe an XML document to **Select-Xml**, each document node will be searched separately as it comes through the pipeline.</span></span>

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

### <span data-ttu-id="b6bba-169">– XPath</span><span class="sxs-lookup"><span data-stu-id="b6bba-169">-XPath</span></span>

<span data-ttu-id="b6bba-170">Anger en XPath-Sök fråga.</span><span class="sxs-lookup"><span data-stu-id="b6bba-170">Specifies an XPath search query.</span></span>
<span data-ttu-id="b6bba-171">Frågespråket är Skift läges känsligt.</span><span class="sxs-lookup"><span data-stu-id="b6bba-171">The query language is case-sensitive.</span></span>
<span data-ttu-id="b6bba-172">Den här parametern är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="b6bba-172">This parameter is required.</span></span>

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

### <span data-ttu-id="b6bba-173">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b6bba-173">CommonParameters</span></span>

<span data-ttu-id="b6bba-174">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b6bba-174">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b6bba-175">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="b6bba-175">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b6bba-176">INDATA</span><span class="sxs-lookup"><span data-stu-id="b6bba-176">INPUTS</span></span>

### <span data-ttu-id="b6bba-177">System. String eller System.Xml.Xmlnod</span><span class="sxs-lookup"><span data-stu-id="b6bba-177">System.String or System.Xml.XmlNode</span></span>

<span data-ttu-id="b6bba-178">Du kan skicka en sökväg eller XML-nod till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b6bba-178">You can pipe a path or XML node to this cmdlet.</span></span>

## <span data-ttu-id="b6bba-179">UTDATA</span><span class="sxs-lookup"><span data-stu-id="b6bba-179">OUTPUTS</span></span>

### <span data-ttu-id="b6bba-180">Microsoft. PowerShell. commands. SelectXmlInfo</span><span class="sxs-lookup"><span data-stu-id="b6bba-180">Microsoft.PowerShell.Commands.SelectXmlInfo</span></span>

## <span data-ttu-id="b6bba-181">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="b6bba-181">NOTES</span></span>

<span data-ttu-id="b6bba-182">XPath är ett standard språk som är utformat för att identifiera delar av ett XML-dokument.</span><span class="sxs-lookup"><span data-stu-id="b6bba-182">XPath is a standard language that is designed to identify parts of an XML document.</span></span> <span data-ttu-id="b6bba-183">Mer information om XPath-språket finns i [XPath-referens](/dotnet/standard/data/xml/select-nodes-using-xpath-navigation) och urvals filter avsnittet i [händelse urvalet](/previous-versions//aa385231(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="b6bba-183">For more information about the XPath language, see [XPath Reference](/dotnet/standard/data/xml/select-nodes-using-xpath-navigation) and the Selection Filters section of [Event Selection](/previous-versions//aa385231(v=vs.85)).</span></span>

## <span data-ttu-id="b6bba-184">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="b6bba-184">RELATED LINKS</span></span>

[<span data-ttu-id="b6bba-185">ConvertTo-Xml</span><span class="sxs-lookup"><span data-stu-id="b6bba-185">ConvertTo-Xml</span></span>](ConvertTo-Xml.md)