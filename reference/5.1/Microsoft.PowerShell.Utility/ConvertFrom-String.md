---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-string?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-String
ms.openlocfilehash: 665a0ca8332c4052b59362c7947e408ba811c5f2
ms.sourcegitcommit: c4906f4c9fa4ef1a16dcd6dd00ff960d19446d71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/01/2020
ms.locfileid: "93269384"
---
# <span data-ttu-id="b2b80-103">ConvertFrom-String</span><span class="sxs-lookup"><span data-stu-id="b2b80-103">ConvertFrom-String</span></span>

## <span data-ttu-id="b2b80-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="b2b80-104">SYNOPSIS</span></span>
<span data-ttu-id="b2b80-105">Extraherar och tolkar strukturerade egenskaper från sträng innehåll.</span><span class="sxs-lookup"><span data-stu-id="b2b80-105">Extracts and parses structured properties from string content.</span></span>

## <span data-ttu-id="b2b80-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b2b80-106">SYNTAX</span></span>

### <span data-ttu-id="b2b80-107">ByDelimiter (standard)</span><span class="sxs-lookup"><span data-stu-id="b2b80-107">ByDelimiter (Default)</span></span>

```
ConvertFrom-String [-Delimiter <String>] [-PropertyNames <String[]>] [-InputObject] <String>
 [<CommonParameters>]
```

### <span data-ttu-id="b2b80-108">TemplateParsing</span><span class="sxs-lookup"><span data-stu-id="b2b80-108">TemplateParsing</span></span>

```
ConvertFrom-String [-TemplateFile <String[]>] [-TemplateContent <String[]>] [-IncludeExtent] [-UpdateTemplate]
 [-InputObject] <String> [<CommonParameters>]
```

## <span data-ttu-id="b2b80-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="b2b80-109">DESCRIPTION</span></span>

<span data-ttu-id="b2b80-110">**ConvertFrom-String-** cmdleten extraherar och tolkar strukturerade egenskaper från sträng innehåll.</span><span class="sxs-lookup"><span data-stu-id="b2b80-110">The **ConvertFrom-String** cmdlet extracts and parses structured properties from string content.</span></span>
<span data-ttu-id="b2b80-111">Denna cmdlet genererar ett objekt genom att parsa text från en vanlig text ström.</span><span class="sxs-lookup"><span data-stu-id="b2b80-111">This cmdlet generates an object by parsing text from a traditional text stream.</span></span>
<span data-ttu-id="b2b80-112">För varje sträng i pipelinen delar cmdleten indatamängden med antingen en avgränsare eller ett pars uttryck, och tilldelar sedan egenskaps namnen till var och en av de resulterande delade elementen.</span><span class="sxs-lookup"><span data-stu-id="b2b80-112">For each string in the pipeline, the cmdlet splits the input by either a delimiter or a parse expression, and then assigns property names to each of the resulting split elements.</span></span>
<span data-ttu-id="b2b80-113">Du kan ange dessa egenskaps namn. Om du inte gör det genereras de automatiskt åt dig.</span><span class="sxs-lookup"><span data-stu-id="b2b80-113">You can provide these property names; if you do not, they are automatically generated for you.</span></span>

<span data-ttu-id="b2b80-114">Cmdletens standard parameter uppsättning, **ByDelimiter** , delar upp exakt den reguljära uttrycks avgränsaren.</span><span class="sxs-lookup"><span data-stu-id="b2b80-114">The cmdlet's default parameter set, **ByDelimiter** , splits exactly on the regular expression delimiter.</span></span>
<span data-ttu-id="b2b80-115">Den utför inte offert matchning eller avgränsare undantags tecken som `Import-Csv` cmdleten gör.</span><span class="sxs-lookup"><span data-stu-id="b2b80-115">It does not perform quote matching or delimiter escaping as the `Import-Csv` cmdlet does.</span></span>

<span data-ttu-id="b2b80-116">Cmdletens alternativa parameter uppsättning, **TemplateParsing** , genererar element från grupper som har samlats in med ett reguljärt uttryck.</span><span class="sxs-lookup"><span data-stu-id="b2b80-116">The cmdlet's alternate parameter set, **TemplateParsing** , generates elements from the groups that are captured by a regular expression.</span></span> <span data-ttu-id="b2b80-117">Mer information om reguljära uttryck finns [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md).</span><span class="sxs-lookup"><span data-stu-id="b2b80-117">For more information on regular expressions, see [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md).</span></span>

<span data-ttu-id="b2b80-118">Denna cmdlet har stöd för två lägen: grundläggande avgränsad parsning och automatiskt genererad, exempel beroende parsning.</span><span class="sxs-lookup"><span data-stu-id="b2b80-118">This cmdlet supports two modes: basic delimited parsing, and automatically-generated, example-driven parsing.</span></span>

<span data-ttu-id="b2b80-119">Delimited parsing, som standard, delar in indatamängden med blank steg och tilldelar de resulterande grupperna egenskaps namn.</span><span class="sxs-lookup"><span data-stu-id="b2b80-119">Delimited parsing, by default, splits the input at white space, and assigns property names to the resulting groups.</span></span>

<span data-ttu-id="b2b80-120">Du kan anpassa avgränsaren genom att skicka `ConvertFrom-String` resultatet till en av `Format-*` cmdletarna, eller så kan du använda **avgränsnings** parametern.</span><span class="sxs-lookup"><span data-stu-id="b2b80-120">You can customize the delimiter by piping the `ConvertFrom-String` results into one of the `Format-*` cmdlets, or you can use the **Delimiter** parameter.</span></span>

<span data-ttu-id="b2b80-121">Cmdleten stöder också automatiskt genererad, exempel-driven parsning baserat på [FlashExtract, forskning som fungerar av Microsoft Research](https://www.microsoft.com/research/publication/flashextract-framework-data-extraction-examples/).</span><span class="sxs-lookup"><span data-stu-id="b2b80-121">The cmdlet also supports automatically-generated, example-driven parsing based on the [FlashExtract, research work by Microsoft Research](https://www.microsoft.com/research/publication/flashextract-framework-data-extraction-examples/).</span></span>

## <span data-ttu-id="b2b80-122">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="b2b80-122">EXAMPLES</span></span>

### <span data-ttu-id="b2b80-123">Exempel 1: generera ett objekt med standard egenskaps namn</span><span class="sxs-lookup"><span data-stu-id="b2b80-123">Example 1: Generate an object with default property names</span></span>

```powershell
"Hello World" | ConvertFrom-String
```

```Output
P1    P2
--    --
Hello World
```

<span data-ttu-id="b2b80-124">Det här kommandot genererar ett objekt med standard egenskaps namn, **P1** och **P2**.</span><span class="sxs-lookup"><span data-stu-id="b2b80-124">This command generates an object with default property names, **P1** and **P2**.</span></span>

### <span data-ttu-id="b2b80-125">Exempel 1A: bekanta dig med det genererade objektet</span><span class="sxs-lookup"><span data-stu-id="b2b80-125">Example 1A: Get to know the generated object</span></span>

<span data-ttu-id="b2b80-126">Det här kommandot genererar ett objekt med egenskaperna **P1** , **P2** ; båda egenskaperna är av **sträng** typ, som standard.</span><span class="sxs-lookup"><span data-stu-id="b2b80-126">This command generates one object with properties **P1** , **P2** ; both properties are of **String** type, by default.</span></span>

```powershell
"Hello World" | ConvertFrom-String | Get-Member
```

```Output

   TypeName: System.Management.Automation.PSCustomObject

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       bool Equals(System.Object obj)
GetHashCode Method       int GetHashCode()
GetType     Method       type GetType()
ToString    Method       string ToString()
P1          NoteProperty string P1=Hello
P2          NoteProperty string P2=World
```

### <span data-ttu-id="b2b80-127">Exempel 2: generera ett objekt med standard egenskaps namn med hjälp av en avgränsare</span><span class="sxs-lookup"><span data-stu-id="b2b80-127">Example 2: Generate an object with default property names using a delimiter</span></span>

<span data-ttu-id="b2b80-128">Det här kommandot genererar ett objekt med en domän och ett användar namn som använder omvänt snedstreck ( `\` ) som avgränsare.</span><span class="sxs-lookup"><span data-stu-id="b2b80-128">This command generates an object with a domain and username using the backslash (`\`) as the delimiter.</span></span> <span data-ttu-id="b2b80-129">Det omvända snedstrecket måste föregås av ett annat omvänt snedstreck när du använder reguljära uttryck.</span><span class="sxs-lookup"><span data-stu-id="b2b80-129">The backslash character must be escaped with another backslash when using regular expressions.</span></span>

```powershell
"Contoso\Administrator" | ConvertFrom-String -Delimiter "\\"
```

```Output
P1      P2
--      --
Contoso Administrator
```

### <span data-ttu-id="b2b80-130">Exempel 3: generera ett objekt som innehåller två namngivna egenskaper</span><span class="sxs-lookup"><span data-stu-id="b2b80-130">Example 3: Generate an object that contains two named properties</span></span>

<span data-ttu-id="b2b80-131">I följande exempel skapas objekt från fil poster i Windows-värdar.</span><span class="sxs-lookup"><span data-stu-id="b2b80-131">The following example creates objects from Windows hosts file entries.</span></span>

```powershell
$content = Get-Content C:\Windows\System32\drivers\etc\hosts
$content = $content -match "^[^#]"
$content | ConvertFrom-String -PropertyNames IP, Server
```

```Output
IP             Server
--             ------
192.168.7.10   W2012R2
192.168.7.20   W2016
192.168.7.101  WIN8
192.168.7.102  WIN10
```

<span data-ttu-id="b2b80-132">`Get-Content`Cmdlet: en lagrar innehållet i en Windows Hosts-fil i `$content` .</span><span class="sxs-lookup"><span data-stu-id="b2b80-132">The `Get-Content` cmdlet stores the content of a Windows hosts file in `$content`.</span></span> <span data-ttu-id="b2b80-133">Det andra kommandot tar bort alla kommentarer i början av värd filen med ett reguljärt uttryck som matchar alla rader som inte börjar med ( `#` ).</span><span class="sxs-lookup"><span data-stu-id="b2b80-133">The second command removes any comments at the beginning of the hosts file using a regular expression that matches any line that does not start with (`#`).</span></span> <span data-ttu-id="b2b80-134">Det sista kommandot konverterar den återstående texten till objekt med **Server** **-och IP-** egenskaper.</span><span class="sxs-lookup"><span data-stu-id="b2b80-134">The last command converts the remaining text into objects with **Server** and **IP** properties.</span></span>

### <span data-ttu-id="b2b80-135">Exempel 4: Använd ett uttryck som värde för parametern TemplateContent och spara resultatet i en variabel.</span><span class="sxs-lookup"><span data-stu-id="b2b80-135">Example 4: Use an expression as the value of the TemplateContent parameter, save the results in a variable.</span></span>

<span data-ttu-id="b2b80-136">Det här kommandot använder ett uttryck som värde för parametern **TemplateContent** .</span><span class="sxs-lookup"><span data-stu-id="b2b80-136">This command uses an expression as the value of the **TemplateContent** parameter.</span></span>
<span data-ttu-id="b2b80-137">Uttrycket sparas i en variabel för enkelhetens skull.</span><span class="sxs-lookup"><span data-stu-id="b2b80-137">The expression is saved in a variable for simplicity.</span></span>
<span data-ttu-id="b2b80-138">Windows PowerShell förstår nu att strängen som används i pipelinen `ConvertFrom-String` har tre egenskaper:</span><span class="sxs-lookup"><span data-stu-id="b2b80-138">Windows PowerShell understands now that the string that is used on the pipeline to `ConvertFrom-String` has three properties:</span></span>

- <span data-ttu-id="b2b80-139">**Namn**</span><span class="sxs-lookup"><span data-stu-id="b2b80-139">**Name**</span></span>
- <span data-ttu-id="b2b80-140">**nummer**</span><span class="sxs-lookup"><span data-stu-id="b2b80-140">**phone**</span></span>
- <span data-ttu-id="b2b80-141">**tids**</span><span class="sxs-lookup"><span data-stu-id="b2b80-141">**age**</span></span>

```powershell
$template = @'
{Name*:Phoebe Cat}, {phone:425-123-6789}, {age:6}
{Name*:Lucky Shot}, {phone:(206) 987-4321}, {age:12}
'@

$testText = @'
Phoebe Cat, 425-123-6789, 6
Lucky Shot, (206) 987-4321, 12
Elephant Wise, 425-888-7766, 87
Wild Shrimp, (111)  222-3333, 1
'@

$PersonalData = $testText | ConvertFrom-String -TemplateContent $template
Write-output ("Pet items found: " + ($PersonalData.Count))
$PersonalData
```

```Output
Pet items found: 4

Name          phone           age
----          -----           ---
Phoebe Cat    425-123-6789    6
Lucky Shot    (206) 987-4321  12
Elephant Wise 425-888-7766    87
Wild Shrimp   (111)  222-3333 1
```

<span data-ttu-id="b2b80-142">Varje rad i indatatypen utvärderas av exempel matchningarna.</span><span class="sxs-lookup"><span data-stu-id="b2b80-142">Each line in the input is evaluated by the sample matches.</span></span> <span data-ttu-id="b2b80-143">Om raden matchar exemplen som anges i mönstret extraheras värdena och skickas till den utgående variabeln.</span><span class="sxs-lookup"><span data-stu-id="b2b80-143">If the line matches the examples given in the pattern, values are extracted and passed to the output variable.</span></span>

<span data-ttu-id="b2b80-144">Exempel data, har `$template` två olika telefon format:</span><span class="sxs-lookup"><span data-stu-id="b2b80-144">The sample data, `$template`, provides two different phone formats:</span></span>

- `425-123-6789`
- `(206) 987-4321`

<span data-ttu-id="b2b80-145">Exempel data innehåller också två olika ålders format:</span><span class="sxs-lookup"><span data-stu-id="b2b80-145">The sample data also provides two different age formats:</span></span>

- `6`
- `12`

<span data-ttu-id="b2b80-146">Detta innebär att telefoner som `(206) 987 4321` inte kommer att identifieras, eftersom det inte finns några exempel data som matchar mönstret eftersom det inte finns några bindestreck.</span><span class="sxs-lookup"><span data-stu-id="b2b80-146">This implies that phones like `(206) 987 4321` will not be recognized, because there's no sample data that matches that pattern because there are no hyphens.</span></span>

### <span data-ttu-id="b2b80-147">Exempel 5: ange data typer för de genererade egenskaperna</span><span class="sxs-lookup"><span data-stu-id="b2b80-147">Example 5: Specifying data types to the generated properties</span></span>

<span data-ttu-id="b2b80-148">Detta är samma exempel som exempel 4 ovan.</span><span class="sxs-lookup"><span data-stu-id="b2b80-148">This is the same example as Example 4, above.</span></span>
<span data-ttu-id="b2b80-149">Skillnaden är att mönster strängen innehåller en datatyp för varje önskad egenskap.</span><span class="sxs-lookup"><span data-stu-id="b2b80-149">The difference is that the pattern string includes a data type for each desired property.</span></span>

```powershell
$template = @'
{[string]Name*:Phoebe Cat}, {[string]phone:425-123-6789}, {[int]age:6}
{[string]Name*:Lucky Shot}, {[string]phone:(206) 987-4321}, {[int]age:12}
'@

$testText = @'
Phoebe Cat, 425-123-6789, 6
Lucky Shot, (206) 987-4321, 12
Elephant Wise, 425-888-7766, 87
Wild Shrimp, (111)  222-3333, 1
'@

$PersonalData = $testText | ConvertFrom-String -TemplateContent $template
Write-output ("Pet items found: " + ($PersonalData.Count))
$PersonalData
```

```Output
Pet items found: 4

Name          phone           age
----          -----           ---
Phoebe Cat    425-123-6789      6
Lucky Shot    (206) 987-4321   12
Elephant Wise 425-888-7766     87
Wild Shrimp   (111)  222-3333   1
```

```powershell
$PersonalData | Get-Member
```

```Output
   TypeName: System.Management.Automation.PSCustomObject

Name        MemberType   Definition
----        ----------   ----------
Equals      Method       bool Equals(System.Object obj)
GetHashCode Method       int GetHashCode()
GetType     Method       type GetType()
ToString    Method       string ToString()
age         NoteProperty int age=6
Name        NoteProperty string Name=Phoebe Cat
phone       NoteProperty string phone=425-123-6789
```

<span data-ttu-id="b2b80-150">`Get-Member`Cmdleten används för att visa att **ålders** egenskapen är ett heltal.</span><span class="sxs-lookup"><span data-stu-id="b2b80-150">The `Get-Member` cmdlet is used to show that the **age** property is an integer.</span></span>

## <span data-ttu-id="b2b80-151">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="b2b80-151">PARAMETERS</span></span>

### <span data-ttu-id="b2b80-152">-Avgränsare</span><span class="sxs-lookup"><span data-stu-id="b2b80-152">-Delimiter</span></span>

<span data-ttu-id="b2b80-153">Anger ett reguljärt uttryck som identifierar avgränsningen mellan element.</span><span class="sxs-lookup"><span data-stu-id="b2b80-153">Specifies a regular expression that identifies the boundary between elements.</span></span>
<span data-ttu-id="b2b80-154">Element som skapas av Split blir egenskaper i det resulterande objektet.</span><span class="sxs-lookup"><span data-stu-id="b2b80-154">Elements that are created by the split become properties in the resulting object.</span></span>
<span data-ttu-id="b2b80-155">Avgränsaren används slutligen i ett anrop till metoden **Split** för typen `[System.Text.RegularExpressions.RegularExpression]` .</span><span class="sxs-lookup"><span data-stu-id="b2b80-155">The delimiter is ultimately used in a call to the **Split** method of the type `[System.Text.RegularExpressions.RegularExpression]`.</span></span>

```yaml
Type: System.String
Parameter Sets: ByDelimiter
Aliases: DEL

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b2b80-156">-IncludeExtent</span><span class="sxs-lookup"><span data-stu-id="b2b80-156">-IncludeExtent</span></span>

<span data-ttu-id="b2b80-157">Anger att denna cmdlet innehåller en text egenskap för omfattning som tas bort som standard.</span><span class="sxs-lookup"><span data-stu-id="b2b80-157">Indicates that this cmdlet includes an extent text property that is removed by default.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TemplateParsing
Aliases: IE

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b2b80-158">– InputObject</span><span class="sxs-lookup"><span data-stu-id="b2b80-158">-InputObject</span></span>

<span data-ttu-id="b2b80-159">Anger strängar som tagits emot från pipelinen eller en variabel som innehåller ett String-objekt.</span><span class="sxs-lookup"><span data-stu-id="b2b80-159">Specifies strings received from the pipeline, or a variable that contains a string object.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="b2b80-160">-PropertyNames</span><span class="sxs-lookup"><span data-stu-id="b2b80-160">-PropertyNames</span></span>

<span data-ttu-id="b2b80-161">Anger en matris med egenskaps namn som ska tilldelas ett delat värde i det resulterande objektet.</span><span class="sxs-lookup"><span data-stu-id="b2b80-161">Specifies an array of property names to which to assign split values in the resulting object.</span></span>
<span data-ttu-id="b2b80-162">Alla text rader som du delar eller tolkar genererar element som representerar egenskaps värden.</span><span class="sxs-lookup"><span data-stu-id="b2b80-162">Every line of text that you split or parse generates elements that represent property values.</span></span>
<span data-ttu-id="b2b80-163">Om elementet är resultatet av en infångnings grupp och den infångnings gruppen har namnet (till exempel `(?<name>)` eller `(?'name')` ), tilldelas namnet på den infångnings gruppen till egenskapen.</span><span class="sxs-lookup"><span data-stu-id="b2b80-163">If the element is the result of a capture group, and that capture group is named (for example, `(?<name>)` or `(?'name')` ), then the name of that capture group is assigned to the property.</span></span>

<span data-ttu-id="b2b80-164">Om du anger något element i matrisen **PropertyName** , tilldelas dessa namn egenskaper som ännu inte har namngetts.</span><span class="sxs-lookup"><span data-stu-id="b2b80-164">If you provide any elements in the **PropertyName** array, those names are assigned to properties that have not yet been named.</span></span>

<span data-ttu-id="b2b80-165">Om du anger fler egenskaps namn än det finns fält, ignorerar PowerShell de extra egenskaps namnen.</span><span class="sxs-lookup"><span data-stu-id="b2b80-165">If you provide more property names than there are fields, PowerShell ignores the extra property names.</span></span> <span data-ttu-id="b2b80-166">Om du inte anger tillräckligt många egenskaps namn för att namnge alla fält tilldelar PowerShell automatiskt numeriska egenskaps namn till alla egenskaper som inte heter: **P1** , **P2** osv.</span><span class="sxs-lookup"><span data-stu-id="b2b80-166">If you do not specify enough property names to name all fields, PowerShell automatically assigns numerical property names to any properties that are not named: **P1** , **P2** , etc.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByDelimiter
Aliases: PN

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b2b80-167">-TemplateContent</span><span class="sxs-lookup"><span data-stu-id="b2b80-167">-TemplateContent</span></span>

<span data-ttu-id="b2b80-168">Anger ett uttryck eller ett uttryck som har sparats som en variabel som beskriver de egenskaper som denna cmdlet tilldelar strängar till.</span><span class="sxs-lookup"><span data-stu-id="b2b80-168">Specifies an expression, or an expression saved as a variable, that describes the properties to which this cmdlet assigns strings.</span></span> <span data-ttu-id="b2b80-169">Syntaxen för en mall fält specifikation är följande: `{[optional-typecast]<name>:<example-value>}` .</span><span class="sxs-lookup"><span data-stu-id="b2b80-169">The syntax of a template field specification is the following: `{[optional-typecast]<name>:<example-value>}`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: TemplateParsing
Aliases: TC

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b2b80-170">-TemplateFile</span><span class="sxs-lookup"><span data-stu-id="b2b80-170">-TemplateFile</span></span>

<span data-ttu-id="b2b80-171">Anger en fil, som en matris, som innehåller en mall för den önskade parsningen av strängen.</span><span class="sxs-lookup"><span data-stu-id="b2b80-171">Specifies a file, as an array, that contains a template for the desired parsing of the string.</span></span>
<span data-ttu-id="b2b80-172">I mallfilen anges egenskaper och deras värden inom hakparenteser, som du ser nedan.</span><span class="sxs-lookup"><span data-stu-id="b2b80-172">In the template file, properties and their values are enclosed in brackets, as shown below.</span></span>
<span data-ttu-id="b2b80-173">Om en egenskap, till exempel egenskapen **namn** och tillhör ande andra egenskaper, visas flera gånger kan du lägga till en asterisk ( `*` ) för att indikera att detta resulterar i flera poster.</span><span class="sxs-lookup"><span data-stu-id="b2b80-173">If a property, such as the **Name** property and its associated other properties, appears multiple times, you can add an asterisk (`*`) to indicate that this results in multiple records.</span></span> <span data-ttu-id="b2b80-174">Detta förhindrar att flera egenskaper extraheras till en enda post.</span><span class="sxs-lookup"><span data-stu-id="b2b80-174">This avoids extracting multiple properties into a single record.</span></span>

```
{Name*:David Chew}
{City:Redmond}, {State:WA}
{Name*:Evan Narvaez}    {Name*:Antonio Moreno}
{City:Issaquah}, {State:WA}
```

```yaml
Type: System.String[]
Parameter Sets: TemplateParsing
Aliases: TF

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b2b80-175">-UpdateTemplate</span><span class="sxs-lookup"><span data-stu-id="b2b80-175">-UpdateTemplate</span></span>

<span data-ttu-id="b2b80-176">Anger att denna cmdlet sparar resultatet av en Learning-algoritm i en kommentar i mallfilen.</span><span class="sxs-lookup"><span data-stu-id="b2b80-176">Indicates that this cmdlet saves the results of a learning algorithm into a comment in the template file.</span></span>
<span data-ttu-id="b2b80-177">Detta gör att algoritm inlärnings processen går snabbare.</span><span class="sxs-lookup"><span data-stu-id="b2b80-177">This makes the algorithm learning process faster.</span></span>
<span data-ttu-id="b2b80-178">Om du vill använda den här parametern måste du även ange en mallfil med parametern **TemplateFile** .</span><span class="sxs-lookup"><span data-stu-id="b2b80-178">To use this parameter, you must also specify a template file with the **TemplateFile** parameter.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: TemplateParsing
Aliases: UT

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b2b80-179">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b2b80-179">CommonParameters</span></span>

<span data-ttu-id="b2b80-180">Denna cmdlet stöder de gemensamma parametrarna:,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` , och `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="b2b80-180">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="b2b80-181">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="b2b80-181">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="b2b80-182">INDATA</span><span class="sxs-lookup"><span data-stu-id="b2b80-182">INPUTS</span></span>

### <span data-ttu-id="b2b80-183">System. String</span><span class="sxs-lookup"><span data-stu-id="b2b80-183">System.String</span></span>

## <span data-ttu-id="b2b80-184">UTDATA</span><span class="sxs-lookup"><span data-stu-id="b2b80-184">OUTPUTS</span></span>

## <span data-ttu-id="b2b80-185">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="b2b80-185">NOTES</span></span>

## <span data-ttu-id="b2b80-186">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="b2b80-186">RELATED LINKS</span></span>

[<span data-ttu-id="b2b80-187">ConvertFrom-sträng: exempel-baserad text tolkning</span><span class="sxs-lookup"><span data-stu-id="b2b80-187">ConvertFrom-String: Example-based text parsing</span></span>](https://devblogs.microsoft.com/powershell/convertfrom-string-example-based-text-parsing/)

[<span data-ttu-id="b2b80-188">ConvertFrom-StringData</span><span class="sxs-lookup"><span data-stu-id="b2b80-188">ConvertFrom-StringData</span></span>](ConvertFrom-StringData.md)

[<span data-ttu-id="b2b80-189">ConvertFrom-CSV</span><span class="sxs-lookup"><span data-stu-id="b2b80-189">ConvertFrom-Csv</span></span>](ConvertFrom-Csv.md)

[<span data-ttu-id="b2b80-190">ConvertTo-Xml</span><span class="sxs-lookup"><span data-stu-id="b2b80-190">ConvertTo-Xml</span></span>](ConvertTo-Xml.md)
