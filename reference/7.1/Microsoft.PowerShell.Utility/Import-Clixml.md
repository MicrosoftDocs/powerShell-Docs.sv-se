---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/15/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-clixml?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-Clixml
ms.openlocfilehash: d33b74101301ec5806f456ddd9cc73bd8b6bb3e1
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264320"
---
# <span data-ttu-id="641ef-103">Import-Clixml</span><span class="sxs-lookup"><span data-stu-id="641ef-103">Import-Clixml</span></span>

## <span data-ttu-id="641ef-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="641ef-104">SYNOPSIS</span></span>
<span data-ttu-id="641ef-105">Importerar en CLIXML-fil och skapar motsvarande objekt i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="641ef-105">Imports a CLIXML file and creates corresponding objects in PowerShell.</span></span>

## <span data-ttu-id="641ef-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="641ef-106">SYNTAX</span></span>

### <span data-ttu-id="641ef-107">ByPath (standard)</span><span class="sxs-lookup"><span data-stu-id="641ef-107">ByPath (Default)</span></span>

```
Import-Clixml [-Path] <String[]> [-IncludeTotalCount] [-Skip <UInt64>] [-First <UInt64>]
 [<CommonParameters>]
```

### <span data-ttu-id="641ef-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="641ef-108">ByLiteralPath</span></span>

```
Import-Clixml -LiteralPath <String[]> [-IncludeTotalCount] [-Skip <UInt64>] [-First <UInt64>]
 [<CommonParameters>]
```

## <span data-ttu-id="641ef-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="641ef-109">DESCRIPTION</span></span>

<span data-ttu-id="641ef-110">`Import-Clixml`Cmdleten importerar en XML-fil med Common Language Infrastructure (CLI) till data som representerar Microsoft .net Ramverks objekt och skapar PowerShell-objekt.</span><span class="sxs-lookup"><span data-stu-id="641ef-110">The `Import-Clixml` cmdlet imports a Common Language Infrastructure (CLI) XML file with data that represents Microsoft .NET Framework objects and creates the PowerShell objects.</span></span> <span data-ttu-id="641ef-111">Mer information om CLI finns i [språk oberoende](/dotnet/standard/language-independence).</span><span class="sxs-lookup"><span data-stu-id="641ef-111">For more information about CLI, see [Language independence](/dotnet/standard/language-independence).</span></span>

<span data-ttu-id="641ef-112">En värdefull användning av `Import-Clixml` Windows-datorer är att importera autentiseringsuppgifter och säkra strängar som har exporter ATS som säker XML med `Export-Clixml` .</span><span class="sxs-lookup"><span data-stu-id="641ef-112">A valuable use of `Import-Clixml` on Windows computers is to import credentials and secure strings that were exported as secure XML using `Export-Clixml`.</span></span> <span data-ttu-id="641ef-113">Ett exempel finns i exempel 2.</span><span class="sxs-lookup"><span data-stu-id="641ef-113">For an example, see Example 2.</span></span>

<span data-ttu-id="641ef-114">`Import-Clixml` använder byte-order-markering (BOM) för att identifiera filens kodnings format.</span><span class="sxs-lookup"><span data-stu-id="641ef-114">`Import-Clixml` uses the byte-order-mark (BOM) to detect the encoding format of the file.</span></span> <span data-ttu-id="641ef-115">Om filen saknar struktur antas kodningen vara UTF8.</span><span class="sxs-lookup"><span data-stu-id="641ef-115">If the file has no BOM, it assumes the encoding is UTF8.</span></span>

## <span data-ttu-id="641ef-116">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="641ef-116">EXAMPLES</span></span>

### <span data-ttu-id="641ef-117">Exempel 1: importera en serialiserad fil och återskapa ett objekt</span><span class="sxs-lookup"><span data-stu-id="641ef-117">Example 1: Import a serialized file and recreate an object</span></span>

<span data-ttu-id="641ef-118">I det här exemplet används `Export-Clixml` cmdleten för att spara en serialiserad kopia av den process information som returnerades av `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="641ef-118">This example uses the `Export-Clixml` cmdlet to save a serialized copy of the process information returned by `Get-Process`.</span></span> <span data-ttu-id="641ef-119">`Import-Clixml` hämtar den serialiserade filens innehåll och återskapar ett objekt som lagras i `$Processes` variabeln.</span><span class="sxs-lookup"><span data-stu-id="641ef-119">`Import-Clixml` retrieves the serialized file's contents and recreates an object that is stored in the `$Processes` variable.</span></span>

```powershell
Get-Process | Export-Clixml -Path .\pi.xml
$Processes = Import-Clixml -Path .\pi.xml
```

### <span data-ttu-id="641ef-120">Exempel 2: importera ett säkert objekt för autentiseringsuppgifter</span><span class="sxs-lookup"><span data-stu-id="641ef-120">Example 2: Import a secure credential object</span></span>

<span data-ttu-id="641ef-121">I det här exemplet har du fått en autentiseringsuppgift som du har lagrat i `$Credential` variabeln genom `Get-Credential` att köra cmdleten, så du kan köra `Export-Clixml` cmdleten för att spara autentiseringsuppgifterna på disken.</span><span class="sxs-lookup"><span data-stu-id="641ef-121">In this example, given a credential that you've stored in the `$Credential` variable by running the `Get-Credential` cmdlet, you can run the `Export-Clixml` cmdlet to save the credential to disk.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="641ef-122">`Export-Clixml` exporterar endast krypterade autentiseringsuppgifter i Windows.</span><span class="sxs-lookup"><span data-stu-id="641ef-122">`Export-Clixml` only exports encrypted credentials on Windows.</span></span> <span data-ttu-id="641ef-123">På andra operativ system än Windows, till exempel macOS och Linux, exporteras autentiseringsuppgifterna som oformaterad text.</span><span class="sxs-lookup"><span data-stu-id="641ef-123">On non-Windows operating systems such as macOS and Linux, credentials are exported in plain text.</span></span>

```powershell
$Credxmlpath = Join-Path (Split-Path $Profile) TestScript.ps1.credential
$Credential | Export-Clixml $Credxmlpath
$Credxmlpath = Join-Path (Split-Path $Profile) TestScript.ps1.credential
$Credential = Import-Clixml $Credxmlpath
```

<span data-ttu-id="641ef-124">`Export-Clixml`Cmdleten krypterar Credential-objekt med hjälp av Windows [Data Protection-API](/previous-versions/windows/apps/hh464970(v=win.10)).</span><span class="sxs-lookup"><span data-stu-id="641ef-124">The `Export-Clixml` cmdlet encrypts credential objects by using the Windows [Data Protection API](/previous-versions/windows/apps/hh464970(v=win.10)).</span></span>
<span data-ttu-id="641ef-125">Krypteringen säkerställer att endast ditt användar konto kan dekryptera innehållet i Credential-objektet.</span><span class="sxs-lookup"><span data-stu-id="641ef-125">The encryption ensures that only your user account can decrypt the contents of the credential object.</span></span> <span data-ttu-id="641ef-126">Den exporterade `CLIXML` filen kan inte användas på en annan dator eller av en annan användare.</span><span class="sxs-lookup"><span data-stu-id="641ef-126">The exported `CLIXML` file can't be used on a different computer or by a different user.</span></span>

<span data-ttu-id="641ef-127">I exemplet representeras filen där autentiseringsuppgiften lagras av `TestScript.ps1.credential` .</span><span class="sxs-lookup"><span data-stu-id="641ef-127">In the example, the file in which the credential is stored is represented by `TestScript.ps1.credential`.</span></span> <span data-ttu-id="641ef-128">Ersätt **TestScript** med namnet på skriptet som du läser in autentiseringsuppgiften med.</span><span class="sxs-lookup"><span data-stu-id="641ef-128">Replace **TestScript** with the name of the script with which you're loading the credential.</span></span>

<span data-ttu-id="641ef-129">Du skickar Credential-objektet ned till pipelinen till `Export-Clixml` och sparar det på den sökväg, `$Credxmlpath` som du angav i det första kommandot.</span><span class="sxs-lookup"><span data-stu-id="641ef-129">You send the credential object down the pipeline to `Export-Clixml`, and save it to the path, `$Credxmlpath`, that you specified in the first command.</span></span>

<span data-ttu-id="641ef-130">Kör de sista två kommandona om du vill importera autentiseringsuppgiften automatiskt till ditt skript.</span><span class="sxs-lookup"><span data-stu-id="641ef-130">To import the credential automatically into your script, run the final two commands.</span></span> <span data-ttu-id="641ef-131">Kör `Import-Clixml` för att importera det skyddade objektet Credential till skriptet.</span><span class="sxs-lookup"><span data-stu-id="641ef-131">Run `Import-Clixml` to import the secured credential object into your script.</span></span> <span data-ttu-id="641ef-132">Den här importen eliminerar risken att exponera lösen ord i klartext i skriptet.</span><span class="sxs-lookup"><span data-stu-id="641ef-132">This import eliminates the risk of exposing plain-text passwords in your script.</span></span>

## <span data-ttu-id="641ef-133">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="641ef-133">PARAMETERS</span></span>

### <span data-ttu-id="641ef-134">– Första</span><span class="sxs-lookup"><span data-stu-id="641ef-134">-First</span></span>

<span data-ttu-id="641ef-135">Hämtar endast det angivna antalet objekt.</span><span class="sxs-lookup"><span data-stu-id="641ef-135">Gets only the specified number of objects.</span></span> <span data-ttu-id="641ef-136">Ange antalet objekt som ska hämtas.</span><span class="sxs-lookup"><span data-stu-id="641ef-136">Enter the number of objects to get.</span></span>

```yaml
Type: System.UInt64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="641ef-137">-IncludeTotalCount</span><span class="sxs-lookup"><span data-stu-id="641ef-137">-IncludeTotalCount</span></span>

<span data-ttu-id="641ef-138">Rapporterar det totala antalet objekt i data uppsättningen följt av de valda objekten.</span><span class="sxs-lookup"><span data-stu-id="641ef-138">Reports the total number of objects in the data set followed by the selected objects.</span></span> <span data-ttu-id="641ef-139">Om cmdleten inte kan avgöra det totala antalet, visar den det **okända totala antalet**.</span><span class="sxs-lookup"><span data-stu-id="641ef-139">If the cmdlet can't determine the total count, it displays **Unknown total count**.</span></span> <span data-ttu-id="641ef-140">Heltalet har en **precisions** egenskap som anger tillförlitligheten för det totala Count-värdet.</span><span class="sxs-lookup"><span data-stu-id="641ef-140">The integer has an **Accuracy** property that indicates the reliability of the total count value.</span></span> <span data-ttu-id="641ef-141">Värdet för **precisions** intervall från `0.0` till `1.0` `0.0` anger att cmdleten inte kunde räkna objekten, `1.0` innebär att antalet är exakt och ett värde mellan `0.0` och `1.0` indikerar en allt mer tillförlitlig uppskattning.</span><span class="sxs-lookup"><span data-stu-id="641ef-141">The value of **Accuracy** ranges from `0.0` to `1.0` where `0.0` means that the cmdlet couldn't count the objects, `1.0` means that the count is exact, and a value between `0.0` and `1.0` indicates an increasingly reliable estimate.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="641ef-142">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="641ef-142">-LiteralPath</span></span>

<span data-ttu-id="641ef-143">Anger sökvägen till XML-filerna.</span><span class="sxs-lookup"><span data-stu-id="641ef-143">Specifies the path to the XML files.</span></span> <span data-ttu-id="641ef-144">Till skillnad från **sökväg** används värdet för parametern **LiteralPath** exakt som det skrivs.</span><span class="sxs-lookup"><span data-stu-id="641ef-144">Unlike **Path** , the value of the **LiteralPath** parameter is used exactly as it's typed.</span></span> <span data-ttu-id="641ef-145">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="641ef-145">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="641ef-146">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="641ef-146">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="641ef-147">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="641ef-147">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="641ef-148">-Path</span><span class="sxs-lookup"><span data-stu-id="641ef-148">-Path</span></span>

<span data-ttu-id="641ef-149">Anger sökvägen till XML-filerna.</span><span class="sxs-lookup"><span data-stu-id="641ef-149">Specifies the path to the XML files.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="641ef-150">-Hoppa över</span><span class="sxs-lookup"><span data-stu-id="641ef-150">-Skip</span></span>

<span data-ttu-id="641ef-151">Ignorerar det angivna antalet objekt och hämtar kvarvarande objekt.</span><span class="sxs-lookup"><span data-stu-id="641ef-151">Ignores the specified number of objects and then gets the remaining objects.</span></span> <span data-ttu-id="641ef-152">Ange antalet objekt som ska hoppas över.</span><span class="sxs-lookup"><span data-stu-id="641ef-152">Enter the number of objects to skip.</span></span>

```yaml
Type: System.UInt64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="641ef-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="641ef-153">CommonParameters</span></span>

<span data-ttu-id="641ef-154">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="641ef-154">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="641ef-155">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="641ef-155">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="641ef-156">INDATA</span><span class="sxs-lookup"><span data-stu-id="641ef-156">INPUTS</span></span>

### <span data-ttu-id="641ef-157">System. String</span><span class="sxs-lookup"><span data-stu-id="641ef-157">System.String</span></span>

<span data-ttu-id="641ef-158">Du kan pipelina en sträng som innehåller en sökväg till `Import-Clixml` .</span><span class="sxs-lookup"><span data-stu-id="641ef-158">You can pipeline a string that contains a path to `Import-Clixml`.</span></span>

## <span data-ttu-id="641ef-159">UTDATA</span><span class="sxs-lookup"><span data-stu-id="641ef-159">OUTPUTS</span></span>

### <span data-ttu-id="641ef-160">PSObject</span><span class="sxs-lookup"><span data-stu-id="641ef-160">PSObject</span></span>

<span data-ttu-id="641ef-161">`Import-Clixml` returnerar objekt som har deserialiserats från de lagrade XML-filerna.</span><span class="sxs-lookup"><span data-stu-id="641ef-161">`Import-Clixml` returns objects that were deserialized from the stored XML files.</span></span>

## <span data-ttu-id="641ef-162">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="641ef-162">NOTES</span></span>

<span data-ttu-id="641ef-163">Använd kommatecken för att avgränsa värdena när du anger flera värden för en parameter.</span><span class="sxs-lookup"><span data-stu-id="641ef-163">When specifying multiple values for a parameter, use commas to separate the values.</span></span> <span data-ttu-id="641ef-164">Till exempel `<parameter-name> <value1>, <value2>`.</span><span class="sxs-lookup"><span data-stu-id="641ef-164">For example, `<parameter-name> <value1>, <value2>`.</span></span>

## <span data-ttu-id="641ef-165">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="641ef-165">RELATED LINKS</span></span>

[<span data-ttu-id="641ef-166">Exportera – CliXml</span><span class="sxs-lookup"><span data-stu-id="641ef-166">Export-Clixml</span></span>](Export-Clixml.md)

[<span data-ttu-id="641ef-167">Introduktion till XML-serialisering</span><span class="sxs-lookup"><span data-stu-id="641ef-167">Introducing XML Serialization</span></span>](/dotnet/standard/serialization/introducing-xml-serialization)

[<span data-ttu-id="641ef-168">Anslut till sökväg</span><span class="sxs-lookup"><span data-stu-id="641ef-168">Join-Path</span></span>](../Microsoft.PowerShell.Management/Join-Path.md)

[<span data-ttu-id="641ef-169">Lagra autentiseringsuppgifter på ett säkert sätt på disken</span><span class="sxs-lookup"><span data-stu-id="641ef-169">Securely Store Credentials on Disk</span></span>](https://powershellcookbook.com/recipe/PukO/securely-store-credentials-on-disk)

[<span data-ttu-id="641ef-170">Använd PowerShell för att skicka autentiseringsuppgifter till äldre system</span><span class="sxs-lookup"><span data-stu-id="641ef-170">Use PowerShell to Pass Credentials to Legacy Systems</span></span>](https://devblogs.microsoft.com/scripting/use-powershell-to-pass-credentials-to-legacy-systems/)

