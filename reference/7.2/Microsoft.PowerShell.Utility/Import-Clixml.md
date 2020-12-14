---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/15/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-clixml?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-Clixml
ms.openlocfilehash: 3658ea5eded0fed95a1c9a1ea6e7d84a557e1e36
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710806"
---
# <span data-ttu-id="23584-102">Import-Clixml</span><span class="sxs-lookup"><span data-stu-id="23584-102">Import-Clixml</span></span>

## <span data-ttu-id="23584-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="23584-103">SYNOPSIS</span></span>
<span data-ttu-id="23584-104">Importerar en CLIXML-fil och skapar motsvarande objekt i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="23584-104">Imports a CLIXML file and creates corresponding objects in PowerShell.</span></span>

## <span data-ttu-id="23584-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="23584-105">SYNTAX</span></span>

### <span data-ttu-id="23584-106">ByPath (standard)</span><span class="sxs-lookup"><span data-stu-id="23584-106">ByPath (Default)</span></span>

```
Import-Clixml [-Path] <String[]> [-IncludeTotalCount] [-Skip <UInt64>] [-First <UInt64>]
 [<CommonParameters>]
```

### <span data-ttu-id="23584-107">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="23584-107">ByLiteralPath</span></span>

```
Import-Clixml -LiteralPath <String[]> [-IncludeTotalCount] [-Skip <UInt64>] [-First <UInt64>]
 [<CommonParameters>]
```

## <span data-ttu-id="23584-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="23584-108">DESCRIPTION</span></span>

<span data-ttu-id="23584-109">`Import-Clixml`Cmdleten importerar en XML-fil med Common Language Infrastructure (CLI) till data som representerar Microsoft .net Ramverks objekt och skapar PowerShell-objekt.</span><span class="sxs-lookup"><span data-stu-id="23584-109">The `Import-Clixml` cmdlet imports a Common Language Infrastructure (CLI) XML file with data that represents Microsoft .NET Framework objects and creates the PowerShell objects.</span></span> <span data-ttu-id="23584-110">Mer information om CLI finns i [språk oberoende](/dotnet/standard/language-independence).</span><span class="sxs-lookup"><span data-stu-id="23584-110">For more information about CLI, see [Language independence](/dotnet/standard/language-independence).</span></span>

<span data-ttu-id="23584-111">En värdefull användning av `Import-Clixml` Windows-datorer är att importera autentiseringsuppgifter och säkra strängar som har exporter ATS som säker XML med `Export-Clixml` .</span><span class="sxs-lookup"><span data-stu-id="23584-111">A valuable use of `Import-Clixml` on Windows computers is to import credentials and secure strings that were exported as secure XML using `Export-Clixml`.</span></span> <span data-ttu-id="23584-112">Ett exempel finns i exempel 2.</span><span class="sxs-lookup"><span data-stu-id="23584-112">For an example, see Example 2.</span></span>

<span data-ttu-id="23584-113">`Import-Clixml` använder byte-order-markering (BOM) för att identifiera filens kodnings format.</span><span class="sxs-lookup"><span data-stu-id="23584-113">`Import-Clixml` uses the byte-order-mark (BOM) to detect the encoding format of the file.</span></span> <span data-ttu-id="23584-114">Om filen saknar struktur antas kodningen vara UTF8.</span><span class="sxs-lookup"><span data-stu-id="23584-114">If the file has no BOM, it assumes the encoding is UTF8.</span></span>

## <span data-ttu-id="23584-115">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="23584-115">EXAMPLES</span></span>

### <span data-ttu-id="23584-116">Exempel 1: importera en serialiserad fil och återskapa ett objekt</span><span class="sxs-lookup"><span data-stu-id="23584-116">Example 1: Import a serialized file and recreate an object</span></span>

<span data-ttu-id="23584-117">I det här exemplet används `Export-Clixml` cmdleten för att spara en serialiserad kopia av den process information som returnerades av `Get-Process` .</span><span class="sxs-lookup"><span data-stu-id="23584-117">This example uses the `Export-Clixml` cmdlet to save a serialized copy of the process information returned by `Get-Process`.</span></span> <span data-ttu-id="23584-118">`Import-Clixml` hämtar den serialiserade filens innehåll och återskapar ett objekt som lagras i `$Processes` variabeln.</span><span class="sxs-lookup"><span data-stu-id="23584-118">`Import-Clixml` retrieves the serialized file's contents and recreates an object that is stored in the `$Processes` variable.</span></span>

```powershell
Get-Process | Export-Clixml -Path .\pi.xml
$Processes = Import-Clixml -Path .\pi.xml
```

### <span data-ttu-id="23584-119">Exempel 2: importera ett säkert objekt för autentiseringsuppgifter</span><span class="sxs-lookup"><span data-stu-id="23584-119">Example 2: Import a secure credential object</span></span>

<span data-ttu-id="23584-120">I det här exemplet har du fått en autentiseringsuppgift som du har lagrat i `$Credential` variabeln genom `Get-Credential` att köra cmdleten, så du kan köra `Export-Clixml` cmdleten för att spara autentiseringsuppgifterna på disken.</span><span class="sxs-lookup"><span data-stu-id="23584-120">In this example, given a credential that you've stored in the `$Credential` variable by running the `Get-Credential` cmdlet, you can run the `Export-Clixml` cmdlet to save the credential to disk.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="23584-121">`Export-Clixml` exporterar endast krypterade autentiseringsuppgifter i Windows.</span><span class="sxs-lookup"><span data-stu-id="23584-121">`Export-Clixml` only exports encrypted credentials on Windows.</span></span> <span data-ttu-id="23584-122">På andra operativ system än Windows, till exempel macOS och Linux, exporteras autentiseringsuppgifterna som oformaterad text.</span><span class="sxs-lookup"><span data-stu-id="23584-122">On non-Windows operating systems such as macOS and Linux, credentials are exported in plain text.</span></span>

```powershell
$Credxmlpath = Join-Path (Split-Path $Profile) TestScript.ps1.credential
$Credential | Export-Clixml $Credxmlpath
$Credxmlpath = Join-Path (Split-Path $Profile) TestScript.ps1.credential
$Credential = Import-Clixml $Credxmlpath
```

<span data-ttu-id="23584-123">`Export-Clixml`Cmdleten krypterar Credential-objekt med hjälp av Windows [Data Protection-API](/previous-versions/windows/apps/hh464970(v=win.10)).</span><span class="sxs-lookup"><span data-stu-id="23584-123">The `Export-Clixml` cmdlet encrypts credential objects by using the Windows [Data Protection API](/previous-versions/windows/apps/hh464970(v=win.10)).</span></span>
<span data-ttu-id="23584-124">Krypteringen säkerställer att endast ditt användar konto kan dekryptera innehållet i Credential-objektet.</span><span class="sxs-lookup"><span data-stu-id="23584-124">The encryption ensures that only your user account can decrypt the contents of the credential object.</span></span> <span data-ttu-id="23584-125">Den exporterade `CLIXML` filen kan inte användas på en annan dator eller av en annan användare.</span><span class="sxs-lookup"><span data-stu-id="23584-125">The exported `CLIXML` file can't be used on a different computer or by a different user.</span></span>

<span data-ttu-id="23584-126">I exemplet representeras filen där autentiseringsuppgiften lagras av `TestScript.ps1.credential` .</span><span class="sxs-lookup"><span data-stu-id="23584-126">In the example, the file in which the credential is stored is represented by `TestScript.ps1.credential`.</span></span> <span data-ttu-id="23584-127">Ersätt **TestScript** med namnet på skriptet som du läser in autentiseringsuppgiften med.</span><span class="sxs-lookup"><span data-stu-id="23584-127">Replace **TestScript** with the name of the script with which you're loading the credential.</span></span>

<span data-ttu-id="23584-128">Du skickar Credential-objektet ned till pipelinen till `Export-Clixml` och sparar det på den sökväg, `$Credxmlpath` som du angav i det första kommandot.</span><span class="sxs-lookup"><span data-stu-id="23584-128">You send the credential object down the pipeline to `Export-Clixml`, and save it to the path, `$Credxmlpath`, that you specified in the first command.</span></span>

<span data-ttu-id="23584-129">Kör de sista två kommandona om du vill importera autentiseringsuppgiften automatiskt till ditt skript.</span><span class="sxs-lookup"><span data-stu-id="23584-129">To import the credential automatically into your script, run the final two commands.</span></span> <span data-ttu-id="23584-130">Kör `Import-Clixml` för att importera det skyddade objektet Credential till skriptet.</span><span class="sxs-lookup"><span data-stu-id="23584-130">Run `Import-Clixml` to import the secured credential object into your script.</span></span> <span data-ttu-id="23584-131">Den här importen eliminerar risken att exponera lösen ord i klartext i skriptet.</span><span class="sxs-lookup"><span data-stu-id="23584-131">This import eliminates the risk of exposing plain-text passwords in your script.</span></span>

## <span data-ttu-id="23584-132">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="23584-132">PARAMETERS</span></span>

### <span data-ttu-id="23584-133">– Första</span><span class="sxs-lookup"><span data-stu-id="23584-133">-First</span></span>

<span data-ttu-id="23584-134">Hämtar endast det angivna antalet objekt.</span><span class="sxs-lookup"><span data-stu-id="23584-134">Gets only the specified number of objects.</span></span> <span data-ttu-id="23584-135">Ange antalet objekt som ska hämtas.</span><span class="sxs-lookup"><span data-stu-id="23584-135">Enter the number of objects to get.</span></span>

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

### <span data-ttu-id="23584-136">-IncludeTotalCount</span><span class="sxs-lookup"><span data-stu-id="23584-136">-IncludeTotalCount</span></span>

<span data-ttu-id="23584-137">Rapporterar det totala antalet objekt i data uppsättningen följt av de valda objekten.</span><span class="sxs-lookup"><span data-stu-id="23584-137">Reports the total number of objects in the data set followed by the selected objects.</span></span> <span data-ttu-id="23584-138">Om cmdleten inte kan avgöra det totala antalet, visar den det **okända totala antalet**.</span><span class="sxs-lookup"><span data-stu-id="23584-138">If the cmdlet can't determine the total count, it displays **Unknown total count**.</span></span> <span data-ttu-id="23584-139">Heltalet har en **precisions** egenskap som anger tillförlitligheten för det totala Count-värdet.</span><span class="sxs-lookup"><span data-stu-id="23584-139">The integer has an **Accuracy** property that indicates the reliability of the total count value.</span></span> <span data-ttu-id="23584-140">Värdet för **precisions** intervall från `0.0` till `1.0` `0.0` anger att cmdleten inte kunde räkna objekten, `1.0` innebär att antalet är exakt och ett värde mellan `0.0` och `1.0` indikerar en allt mer tillförlitlig uppskattning.</span><span class="sxs-lookup"><span data-stu-id="23584-140">The value of **Accuracy** ranges from `0.0` to `1.0` where `0.0` means that the cmdlet couldn't count the objects, `1.0` means that the count is exact, and a value between `0.0` and `1.0` indicates an increasingly reliable estimate.</span></span>

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

### <span data-ttu-id="23584-141">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="23584-141">-LiteralPath</span></span>

<span data-ttu-id="23584-142">Anger sökvägen till XML-filerna.</span><span class="sxs-lookup"><span data-stu-id="23584-142">Specifies the path to the XML files.</span></span> <span data-ttu-id="23584-143">Till skillnad från **sökväg** används värdet för parametern **LiteralPath** exakt som det skrivs.</span><span class="sxs-lookup"><span data-stu-id="23584-143">Unlike **Path**, the value of the **LiteralPath** parameter is used exactly as it's typed.</span></span> <span data-ttu-id="23584-144">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="23584-144">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="23584-145">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="23584-145">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="23584-146">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="23584-146">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="23584-147">-Path</span><span class="sxs-lookup"><span data-stu-id="23584-147">-Path</span></span>

<span data-ttu-id="23584-148">Anger sökvägen till XML-filerna.</span><span class="sxs-lookup"><span data-stu-id="23584-148">Specifies the path to the XML files.</span></span>

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

### <span data-ttu-id="23584-149">-Hoppa över</span><span class="sxs-lookup"><span data-stu-id="23584-149">-Skip</span></span>

<span data-ttu-id="23584-150">Ignorerar det angivna antalet objekt och hämtar kvarvarande objekt.</span><span class="sxs-lookup"><span data-stu-id="23584-150">Ignores the specified number of objects and then gets the remaining objects.</span></span> <span data-ttu-id="23584-151">Ange antalet objekt som ska hoppas över.</span><span class="sxs-lookup"><span data-stu-id="23584-151">Enter the number of objects to skip.</span></span>

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

### <span data-ttu-id="23584-152">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="23584-152">CommonParameters</span></span>

<span data-ttu-id="23584-153">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="23584-153">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="23584-154">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="23584-154">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="23584-155">INDATA</span><span class="sxs-lookup"><span data-stu-id="23584-155">INPUTS</span></span>

### <span data-ttu-id="23584-156">System. String</span><span class="sxs-lookup"><span data-stu-id="23584-156">System.String</span></span>

<span data-ttu-id="23584-157">Du kan pipelina en sträng som innehåller en sökväg till `Import-Clixml` .</span><span class="sxs-lookup"><span data-stu-id="23584-157">You can pipeline a string that contains a path to `Import-Clixml`.</span></span>

## <span data-ttu-id="23584-158">UTDATA</span><span class="sxs-lookup"><span data-stu-id="23584-158">OUTPUTS</span></span>

### <span data-ttu-id="23584-159">PSObject</span><span class="sxs-lookup"><span data-stu-id="23584-159">PSObject</span></span>

<span data-ttu-id="23584-160">`Import-Clixml` returnerar objekt som har deserialiserats från de lagrade XML-filerna.</span><span class="sxs-lookup"><span data-stu-id="23584-160">`Import-Clixml` returns objects that were deserialized from the stored XML files.</span></span>

## <span data-ttu-id="23584-161">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="23584-161">NOTES</span></span>

<span data-ttu-id="23584-162">Använd kommatecken för att avgränsa värdena när du anger flera värden för en parameter.</span><span class="sxs-lookup"><span data-stu-id="23584-162">When specifying multiple values for a parameter, use commas to separate the values.</span></span> <span data-ttu-id="23584-163">Ett exempel är `<parameter-name> <value1>, <value2>`.</span><span class="sxs-lookup"><span data-stu-id="23584-163">For example, `<parameter-name> <value1>, <value2>`.</span></span>

## <span data-ttu-id="23584-164">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="23584-164">RELATED LINKS</span></span>

[<span data-ttu-id="23584-165">Exportera – CliXml</span><span class="sxs-lookup"><span data-stu-id="23584-165">Export-Clixml</span></span>](Export-Clixml.md)

[<span data-ttu-id="23584-166">Introduktion till XML-serialisering</span><span class="sxs-lookup"><span data-stu-id="23584-166">Introducing XML Serialization</span></span>](/dotnet/standard/serialization/introducing-xml-serialization)

[<span data-ttu-id="23584-167">Anslut till sökväg</span><span class="sxs-lookup"><span data-stu-id="23584-167">Join-Path</span></span>](../Microsoft.PowerShell.Management/Join-Path.md)

[<span data-ttu-id="23584-168">Lagra autentiseringsuppgifter på ett säkert sätt på disken</span><span class="sxs-lookup"><span data-stu-id="23584-168">Securely Store Credentials on Disk</span></span>](https://powershellcookbook.com/recipe/PukO/securely-store-credentials-on-disk)

[<span data-ttu-id="23584-169">Använd PowerShell för att skicka autentiseringsuppgifter till äldre system</span><span class="sxs-lookup"><span data-stu-id="23584-169">Use PowerShell to Pass Credentials to Legacy Systems</span></span>](https://devblogs.microsoft.com/scripting/use-powershell-to-pass-credentials-to-legacy-systems/)

