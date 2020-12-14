---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/12/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-xml?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Xml
ms.openlocfilehash: e461c07360b3d9eaf7d9a3c8875d34cd1fc841e8
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710189"
---
# <span data-ttu-id="bc38a-102">ConvertTo-Xml</span><span class="sxs-lookup"><span data-stu-id="bc38a-102">ConvertTo-Xml</span></span>

## <span data-ttu-id="bc38a-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="bc38a-103">SYNOPSIS</span></span>
<span data-ttu-id="bc38a-104">Skapar en XML-baserad representation av ett objekt.</span><span class="sxs-lookup"><span data-stu-id="bc38a-104">Creates an XML-based representation of an object.</span></span>

## <span data-ttu-id="bc38a-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="bc38a-105">SYNTAX</span></span>

```
ConvertTo-Xml [-Depth <Int32>] [-InputObject] <PSObject> [-NoTypeInformation] [-As <String>]
 [<CommonParameters>]
```

## <span data-ttu-id="bc38a-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="bc38a-106">DESCRIPTION</span></span>

<span data-ttu-id="bc38a-107">`ConvertTo-Xml`Cmdleten skapar en [XML-baserad](/dotnet/api/system.xml.xmldocument) representation av ett eller flera .net-objekt.</span><span class="sxs-lookup"><span data-stu-id="bc38a-107">The `ConvertTo-Xml` cmdlet creates an [XML-based](/dotnet/api/system.xml.xmldocument) representation of one or more more .NET objects.</span></span> <span data-ttu-id="bc38a-108">Om du vill använda denna cmdlet, rör ett eller flera objekt till cmdleten eller Använd parametern **InputObject** för att ange objektet.</span><span class="sxs-lookup"><span data-stu-id="bc38a-108">To use this cmdlet, pipe one or more objects to the cmdlet, or use the **InputObject** parameter to specify the object.</span></span>

<span data-ttu-id="bc38a-109">När du lägger till flera objekt i `ConvertTo-Xml` eller använder parametern **InputObject** för att skicka flera objekt, `ConvertTo-Xml` returnerar ett enskilt XML-dokument i minnet som innehåller representationer av alla objekt.</span><span class="sxs-lookup"><span data-stu-id="bc38a-109">When you pipe multiple objects to `ConvertTo-Xml` or use the **InputObject** parameter to submit multiple objects, `ConvertTo-Xml` returns a single, in-memory XML document that includes representations of all of the objects.</span></span>

<span data-ttu-id="bc38a-110">Den här cmdleten liknar [export-CliXml](./Export-Clixml.md) , förutom att `Export-Clixml` lagrar XML-koden i en [XML-fil med Common Language Infrastructure (CLI)](https://www.ecma-international.org/publications/standards/Ecma-335.htm) som kan importeras om som objekt med [import-CliXml](./Import-Clixml.md).</span><span class="sxs-lookup"><span data-stu-id="bc38a-110">This cmdlet is similar to [Export-Clixml](./Export-Clixml.md) except that `Export-Clixml` stores the resulting XML in a [Common Language Infrastructure(CLI) XML](https://www.ecma-international.org/publications/standards/Ecma-335.htm) file that can be reimported as objects with [Import-Clixml](./Import-Clixml.md).</span></span> <span data-ttu-id="bc38a-111">`ConvertTo-Xml` Returnerar en minnes intern representation av ett XML-dokument, så du kan fortsätta att bearbeta det i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bc38a-111">`ConvertTo-Xml` returns an in-memory representation of an XML document, so you can continue to process it in PowerShell.</span></span> <span data-ttu-id="bc38a-112">`ConvertTo-Xml` har inget alternativ för att konvertera objekt till CLI XML.</span><span class="sxs-lookup"><span data-stu-id="bc38a-112">`ConvertTo-Xml` does not have an option to convert objects to CLI XML.</span></span>

## <span data-ttu-id="bc38a-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="bc38a-113">EXAMPLES</span></span>

### <span data-ttu-id="bc38a-114">Exempel 1: konvertera ett datum till XML</span><span class="sxs-lookup"><span data-stu-id="bc38a-114">Example 1: Convert a date to XML</span></span>

```
PS C:\> Get-Date | ConvertTo-Xml
```

<span data-ttu-id="bc38a-115">Det här kommandot konverterar det aktuella datumet (ett **datetime** -objekt) till XML.</span><span class="sxs-lookup"><span data-stu-id="bc38a-115">This command converts the current date (a **DateTime** object) to XML.</span></span>

### <span data-ttu-id="bc38a-116">Exempel 2: konvertera processer till XML</span><span class="sxs-lookup"><span data-stu-id="bc38a-116">Example 2: Convert processes to XML</span></span>

```
PS C:\> ConvertTo-Xml -As "Document" -InputObject (Get-Process) -Depth 3
```

<span data-ttu-id="bc38a-117">Detta kommando konverterar de process objekt som representerar alla processer på datorn till ett XML-dokument.</span><span class="sxs-lookup"><span data-stu-id="bc38a-117">This command converts the process objects that represent all of the processes on the computer into an XML document.</span></span> <span data-ttu-id="bc38a-118">Objekten expanderas till ett djup på tre nivåer.</span><span class="sxs-lookup"><span data-stu-id="bc38a-118">The objects are expanded to a depth of three levels.</span></span>

## <span data-ttu-id="bc38a-119">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="bc38a-119">PARAMETERS</span></span>

### <span data-ttu-id="bc38a-120">– Som</span><span class="sxs-lookup"><span data-stu-id="bc38a-120">-As</span></span>

<span data-ttu-id="bc38a-121">Anger utdataformatet.</span><span class="sxs-lookup"><span data-stu-id="bc38a-121">Determines the output format.</span></span>
<span data-ttu-id="bc38a-122">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="bc38a-122">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="bc38a-123">Sträng.</span><span class="sxs-lookup"><span data-stu-id="bc38a-123">String.</span></span>
<span data-ttu-id="bc38a-124">Returnerar en enskild sträng.</span><span class="sxs-lookup"><span data-stu-id="bc38a-124">Returns a single string.</span></span>
- <span data-ttu-id="bc38a-125">Skicka.</span><span class="sxs-lookup"><span data-stu-id="bc38a-125">Stream.</span></span>
<span data-ttu-id="bc38a-126">Returnerar en sträng mat ris.</span><span class="sxs-lookup"><span data-stu-id="bc38a-126">Returns an array of strings.</span></span>
- <span data-ttu-id="bc38a-127">Handling.</span><span class="sxs-lookup"><span data-stu-id="bc38a-127">Document.</span></span>
<span data-ttu-id="bc38a-128">Returnerar ett **XMLDocument** -objekt.</span><span class="sxs-lookup"><span data-stu-id="bc38a-128">Returns an **XmlDocument** object.</span></span>

<span data-ttu-id="bc38a-129">Standardvärdet är Document.</span><span class="sxs-lookup"><span data-stu-id="bc38a-129">The default value is Document.</span></span>

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

### <span data-ttu-id="bc38a-130">-Djup</span><span class="sxs-lookup"><span data-stu-id="bc38a-130">-Depth</span></span>

<span data-ttu-id="bc38a-131">Anger hur många nivåer med objekt som ingår i XML-representationen.</span><span class="sxs-lookup"><span data-stu-id="bc38a-131">Specifies how many levels of contained objects are included in the XML representation.</span></span> <span data-ttu-id="bc38a-132">Standardvärdet är 1.</span><span class="sxs-lookup"><span data-stu-id="bc38a-132">The default value is 1.</span></span>

<span data-ttu-id="bc38a-133">Om objektets egenskaper till exempel även innehåller objekt, så att du kan spara en XML-representation av egenskaperna för de objekt som finns i listan, måste du ange ett djup på 2.</span><span class="sxs-lookup"><span data-stu-id="bc38a-133">For example, if the object's properties also contain objects, to save an XML representation of the properties of the contained objects, you must specify a depth of 2.</span></span>

<span data-ttu-id="bc38a-134">Standardvärdet kan åsidosättas av objekt typen i Types.ps1XML-filer.</span><span class="sxs-lookup"><span data-stu-id="bc38a-134">The default value can be overridden for the object type in the Types.ps1xml files.</span></span> <span data-ttu-id="bc38a-135">Mer information finns i about_Types.ps1XML.</span><span class="sxs-lookup"><span data-stu-id="bc38a-135">For more information, see about_Types.ps1xml.</span></span>

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

### <span data-ttu-id="bc38a-136">– InputObject</span><span class="sxs-lookup"><span data-stu-id="bc38a-136">-InputObject</span></span>

<span data-ttu-id="bc38a-137">Anger det objekt som ska konverteras.</span><span class="sxs-lookup"><span data-stu-id="bc38a-137">Specifies the object to be converted.</span></span> <span data-ttu-id="bc38a-138">Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten.</span><span class="sxs-lookup"><span data-stu-id="bc38a-138">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span> <span data-ttu-id="bc38a-139">Du kan också skicka pipe-objekt till **ConvertTo-XML**.</span><span class="sxs-lookup"><span data-stu-id="bc38a-139">You can also pipe objects to **ConvertTo-XML**.</span></span>

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

### <span data-ttu-id="bc38a-140">-NoTypeInformation</span><span class="sxs-lookup"><span data-stu-id="bc38a-140">-NoTypeInformation</span></span>

<span data-ttu-id="bc38a-141">Utesluter Typattributet från objekt-noderna.</span><span class="sxs-lookup"><span data-stu-id="bc38a-141">Omits the Type attribute from the object nodes.</span></span>

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

### <span data-ttu-id="bc38a-142">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="bc38a-142">CommonParameters</span></span>

<span data-ttu-id="bc38a-143">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="bc38a-143">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="bc38a-144">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="bc38a-144">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="bc38a-145">INDATA</span><span class="sxs-lookup"><span data-stu-id="bc38a-145">INPUTS</span></span>

### <span data-ttu-id="bc38a-146">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="bc38a-146">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="bc38a-147">Du kan skicka ett objekt till **ConvertTo-XML**.</span><span class="sxs-lookup"><span data-stu-id="bc38a-147">You can pipe any object to **ConvertTo-XML**.</span></span>

## <span data-ttu-id="bc38a-148">UTDATA</span><span class="sxs-lookup"><span data-stu-id="bc38a-148">OUTPUTS</span></span>

### <span data-ttu-id="bc38a-149">System. String eller System.Xml.Xmldokument</span><span class="sxs-lookup"><span data-stu-id="bc38a-149">System.String or System.Xml.XmlDocument</span></span>

<span data-ttu-id="bc38a-150">Värdet för parametern *as* bestämmer vilken typ av objekt som **ConvertTo-XML** returnerar.</span><span class="sxs-lookup"><span data-stu-id="bc38a-150">The value of the *As* parameter determines the type of object that **ConvertTo-XML** returns.</span></span>

## <span data-ttu-id="bc38a-151">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="bc38a-151">NOTES</span></span>

## <span data-ttu-id="bc38a-152">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="bc38a-152">RELATED LINKS</span></span>

[<span data-ttu-id="bc38a-153">ConvertTo-Csv</span><span class="sxs-lookup"><span data-stu-id="bc38a-153">ConvertTo-Csv</span></span>](ConvertTo-Csv.md)

[<span data-ttu-id="bc38a-154">ConvertTo-Html</span><span class="sxs-lookup"><span data-stu-id="bc38a-154">ConvertTo-Html</span></span>](ConvertTo-Html.md)

[<span data-ttu-id="bc38a-155">Exportera – CliXml</span><span class="sxs-lookup"><span data-stu-id="bc38a-155">Export-Clixml</span></span>](Export-Clixml.md)

[<span data-ttu-id="bc38a-156">Hämta datum</span><span class="sxs-lookup"><span data-stu-id="bc38a-156">Get-Date</span></span>](Get-Date.md)

[<span data-ttu-id="bc38a-157">Importera – CliXml</span><span class="sxs-lookup"><span data-stu-id="bc38a-157">Import-Clixml</span></span>](Import-Clixml.md)

