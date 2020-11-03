---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/12/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-xml?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Xml
ms.openlocfilehash: c8d4f0607c28160ec40f9b36e03afdb7ba8b0c16
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93262754"
---
# <span data-ttu-id="b87ef-103">ConvertTo-Xml</span><span class="sxs-lookup"><span data-stu-id="b87ef-103">ConvertTo-Xml</span></span>

## <span data-ttu-id="b87ef-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="b87ef-104">SYNOPSIS</span></span>
<span data-ttu-id="b87ef-105">Skapar en XML-baserad representation av ett objekt.</span><span class="sxs-lookup"><span data-stu-id="b87ef-105">Creates an XML-based representation of an object.</span></span>

## <span data-ttu-id="b87ef-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b87ef-106">SYNTAX</span></span>

```
ConvertTo-Xml [-Depth <Int32>] [-InputObject] <PSObject> [-NoTypeInformation] [-As <String>]
 [<CommonParameters>]
```

## <span data-ttu-id="b87ef-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="b87ef-107">DESCRIPTION</span></span>

<span data-ttu-id="b87ef-108">`ConvertTo-Xml`Cmdleten skapar en [XML-baserad](/dotnet/api/system.xml.xmldocument) representation av ett eller flera .net-objekt.</span><span class="sxs-lookup"><span data-stu-id="b87ef-108">The `ConvertTo-Xml` cmdlet creates an [XML-based](/dotnet/api/system.xml.xmldocument) representation of one or more more .NET objects.</span></span> <span data-ttu-id="b87ef-109">Om du vill använda denna cmdlet, rör ett eller flera objekt till cmdleten eller Använd parametern **InputObject** för att ange objektet.</span><span class="sxs-lookup"><span data-stu-id="b87ef-109">To use this cmdlet, pipe one or more objects to the cmdlet, or use the **InputObject** parameter to specify the object.</span></span>

<span data-ttu-id="b87ef-110">När du lägger till flera objekt i `ConvertTo-Xml` eller använder parametern **InputObject** för att skicka flera objekt, `ConvertTo-Xml` returnerar ett enskilt XML-dokument i minnet som innehåller representationer av alla objekt.</span><span class="sxs-lookup"><span data-stu-id="b87ef-110">When you pipe multiple objects to `ConvertTo-Xml` or use the **InputObject** parameter to submit multiple objects, `ConvertTo-Xml` returns a single, in-memory XML document that includes representations of all of the objects.</span></span>

<span data-ttu-id="b87ef-111">Den här cmdleten liknar [export-CliXml](./Export-Clixml.md) , förutom att `Export-Clixml` lagrar XML-koden i en [XML-fil med Common Language Infrastructure (CLI)](https://www.ecma-international.org/publications/standards/Ecma-335.htm) som kan importeras om som objekt med [import-CliXml](./Import-Clixml.md).</span><span class="sxs-lookup"><span data-stu-id="b87ef-111">This cmdlet is similar to [Export-Clixml](./Export-Clixml.md) except that `Export-Clixml` stores the resulting XML in a [Common Language Infrastructure(CLI) XML](https://www.ecma-international.org/publications/standards/Ecma-335.htm) file that can be reimported as objects with [Import-Clixml](./Import-Clixml.md).</span></span> <span data-ttu-id="b87ef-112">`ConvertTo-Xml` Returnerar en minnes intern representation av ett XML-dokument, så du kan fortsätta att bearbeta det i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b87ef-112">`ConvertTo-Xml` returns an in-memory representation of an XML document, so you can continue to process it in PowerShell.</span></span> <span data-ttu-id="b87ef-113">`ConvertTo-Xml` har inget alternativ för att konvertera objekt till CLI XML.</span><span class="sxs-lookup"><span data-stu-id="b87ef-113">`ConvertTo-Xml` does not have an option to convert objects to CLI XML.</span></span>

## <span data-ttu-id="b87ef-114">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="b87ef-114">EXAMPLES</span></span>

### <span data-ttu-id="b87ef-115">Exempel 1: konvertera ett datum till XML</span><span class="sxs-lookup"><span data-stu-id="b87ef-115">Example 1: Convert a date to XML</span></span>

```
PS C:\> Get-Date | ConvertTo-Xml
```

<span data-ttu-id="b87ef-116">Det här kommandot konverterar det aktuella datumet (ett **datetime** -objekt) till XML.</span><span class="sxs-lookup"><span data-stu-id="b87ef-116">This command converts the current date (a **DateTime** object) to XML.</span></span>

### <span data-ttu-id="b87ef-117">Exempel 2: konvertera processer till XML</span><span class="sxs-lookup"><span data-stu-id="b87ef-117">Example 2: Convert processes to XML</span></span>

```
PS C:\> ConvertTo-Xml -As "Document" -InputObject (Get-Process) -Depth 3
```

<span data-ttu-id="b87ef-118">Detta kommando konverterar de process objekt som representerar alla processer på datorn till ett XML-dokument.</span><span class="sxs-lookup"><span data-stu-id="b87ef-118">This command converts the process objects that represent all of the processes on the computer into an XML document.</span></span> <span data-ttu-id="b87ef-119">Objekten expanderas till ett djup på tre nivåer.</span><span class="sxs-lookup"><span data-stu-id="b87ef-119">The objects are expanded to a depth of three levels.</span></span>

## <span data-ttu-id="b87ef-120">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="b87ef-120">PARAMETERS</span></span>

### <span data-ttu-id="b87ef-121">– Som</span><span class="sxs-lookup"><span data-stu-id="b87ef-121">-As</span></span>

<span data-ttu-id="b87ef-122">Anger utdataformatet.</span><span class="sxs-lookup"><span data-stu-id="b87ef-122">Determines the output format.</span></span>
<span data-ttu-id="b87ef-123">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="b87ef-123">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="b87ef-124">Sträng.</span><span class="sxs-lookup"><span data-stu-id="b87ef-124">String.</span></span>
<span data-ttu-id="b87ef-125">Returnerar en enskild sträng.</span><span class="sxs-lookup"><span data-stu-id="b87ef-125">Returns a single string.</span></span>
- <span data-ttu-id="b87ef-126">Skicka.</span><span class="sxs-lookup"><span data-stu-id="b87ef-126">Stream.</span></span>
<span data-ttu-id="b87ef-127">Returnerar en sträng mat ris.</span><span class="sxs-lookup"><span data-stu-id="b87ef-127">Returns an array of strings.</span></span>
- <span data-ttu-id="b87ef-128">Handling.</span><span class="sxs-lookup"><span data-stu-id="b87ef-128">Document.</span></span>
<span data-ttu-id="b87ef-129">Returnerar ett **XMLDocument** -objekt.</span><span class="sxs-lookup"><span data-stu-id="b87ef-129">Returns an **XmlDocument** object.</span></span>

<span data-ttu-id="b87ef-130">Standardvärdet är Document.</span><span class="sxs-lookup"><span data-stu-id="b87ef-130">The default value is Document.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Stream, String, Document

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b87ef-131">-Djup</span><span class="sxs-lookup"><span data-stu-id="b87ef-131">-Depth</span></span>

<span data-ttu-id="b87ef-132">Anger hur många nivåer med objekt som ingår i XML-representationen.</span><span class="sxs-lookup"><span data-stu-id="b87ef-132">Specifies how many levels of contained objects are included in the XML representation.</span></span> <span data-ttu-id="b87ef-133">Standardvärdet är 1.</span><span class="sxs-lookup"><span data-stu-id="b87ef-133">The default value is 1.</span></span>

<span data-ttu-id="b87ef-134">Om objektets egenskaper till exempel även innehåller objekt, så att du kan spara en XML-representation av egenskaperna för de objekt som finns i listan, måste du ange ett djup på 2.</span><span class="sxs-lookup"><span data-stu-id="b87ef-134">For example, if the object's properties also contain objects, to save an XML representation of the properties of the contained objects, you must specify a depth of 2.</span></span>

<span data-ttu-id="b87ef-135">Standardvärdet kan åsidosättas av objekt typen i Types.ps1XML-filer.</span><span class="sxs-lookup"><span data-stu-id="b87ef-135">The default value can be overridden for the object type in the Types.ps1xml files.</span></span> <span data-ttu-id="b87ef-136">Mer information finns i about_Types.ps1XML.</span><span class="sxs-lookup"><span data-stu-id="b87ef-136">For more information, see about_Types.ps1xml.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b87ef-137">– InputObject</span><span class="sxs-lookup"><span data-stu-id="b87ef-137">-InputObject</span></span>

<span data-ttu-id="b87ef-138">Anger det objekt som ska konverteras.</span><span class="sxs-lookup"><span data-stu-id="b87ef-138">Specifies the object to be converted.</span></span> <span data-ttu-id="b87ef-139">Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten.</span><span class="sxs-lookup"><span data-stu-id="b87ef-139">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span> <span data-ttu-id="b87ef-140">Du kan också skicka pipe-objekt till **ConvertTo-XML**.</span><span class="sxs-lookup"><span data-stu-id="b87ef-140">You can also pipe objects to **ConvertTo-XML**.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="b87ef-141">-NoTypeInformation</span><span class="sxs-lookup"><span data-stu-id="b87ef-141">-NoTypeInformation</span></span>

<span data-ttu-id="b87ef-142">Utesluter Typattributet från objekt-noderna.</span><span class="sxs-lookup"><span data-stu-id="b87ef-142">Omits the Type attribute from the object nodes.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b87ef-143">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b87ef-143">CommonParameters</span></span>

<span data-ttu-id="b87ef-144">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b87ef-144">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b87ef-145">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="b87ef-145">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b87ef-146">INDATA</span><span class="sxs-lookup"><span data-stu-id="b87ef-146">INPUTS</span></span>

### <span data-ttu-id="b87ef-147">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="b87ef-147">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="b87ef-148">Du kan skicka ett objekt till **ConvertTo-XML**.</span><span class="sxs-lookup"><span data-stu-id="b87ef-148">You can pipe any object to **ConvertTo-XML**.</span></span>

## <span data-ttu-id="b87ef-149">UTDATA</span><span class="sxs-lookup"><span data-stu-id="b87ef-149">OUTPUTS</span></span>

### <span data-ttu-id="b87ef-150">System. String eller System.Xml.Xmldokument</span><span class="sxs-lookup"><span data-stu-id="b87ef-150">System.String or System.Xml.XmlDocument</span></span>

<span data-ttu-id="b87ef-151">Värdet för parametern *as* bestämmer vilken typ av objekt som **ConvertTo-XML** returnerar.</span><span class="sxs-lookup"><span data-stu-id="b87ef-151">The value of the *As* parameter determines the type of object that **ConvertTo-XML** returns.</span></span>

## <span data-ttu-id="b87ef-152">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="b87ef-152">NOTES</span></span>

## <span data-ttu-id="b87ef-153">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="b87ef-153">RELATED LINKS</span></span>

[<span data-ttu-id="b87ef-154">ConvertTo-Csv</span><span class="sxs-lookup"><span data-stu-id="b87ef-154">ConvertTo-Csv</span></span>](ConvertTo-Csv.md)

[<span data-ttu-id="b87ef-155">ConvertTo-Html</span><span class="sxs-lookup"><span data-stu-id="b87ef-155">ConvertTo-Html</span></span>](ConvertTo-Html.md)

[<span data-ttu-id="b87ef-156">Exportera – CliXml</span><span class="sxs-lookup"><span data-stu-id="b87ef-156">Export-Clixml</span></span>](Export-Clixml.md)

[<span data-ttu-id="b87ef-157">Hämta datum</span><span class="sxs-lookup"><span data-stu-id="b87ef-157">Get-Date</span></span>](Get-Date.md)

[<span data-ttu-id="b87ef-158">Importera – CliXml</span><span class="sxs-lookup"><span data-stu-id="b87ef-158">Import-Clixml</span></span>](Import-Clixml.md)
