---
external help file: Microsoft.PowerShell.ODataUtils-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.ODataUtils
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.odatautils/export-odataendpointproxy?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-ODataEndpointProxy
ms.openlocfilehash: 846aca6974190863a073773fe5148f0c57d77dc3
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388203"
---
# <span data-ttu-id="52ff1-103">Export-ODataEndpointProxy</span><span class="sxs-lookup"><span data-stu-id="52ff1-103">Export-ODataEndpointProxy</span></span>

## <span data-ttu-id="52ff1-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="52ff1-104">SYNOPSIS</span></span>
<span data-ttu-id="52ff1-105">Genererar en modul som innehåller cmdlets för att hantera en OData-slutpunkt.</span><span class="sxs-lookup"><span data-stu-id="52ff1-105">Generates a module that contains cmdlets to manage an OData endpoint.</span></span>

## <span data-ttu-id="52ff1-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="52ff1-106">SYNTAX</span></span>

```
Export-ODataEndpointProxy [-Uri] <String> [-OutputModule] <String> [[-MetadataUri] <String>]
 [[-Credential] <PSCredential>] [[-CreateRequestMethod] <String>] [[-UpdateRequestMethod] <String>]
 [[-CmdletAdapter] <String>] [[-ResourceNameMapping] <Hashtable>] [-Force] [[-CustomData] <Hashtable>]
 [-AllowClobber] [-AllowUnsecureConnection] [[-Headers] <Hashtable>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="52ff1-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="52ff1-107">DESCRIPTION</span></span>

<span data-ttu-id="52ff1-108">`Export-ODataEndpointProxy`Cmdlet: en använder metadata för en OData-slutpunkt för att skapa en modul som innehåller cmdletar som du kan använda för att hantera OData-slutpunkten.</span><span class="sxs-lookup"><span data-stu-id="52ff1-108">The `Export-ODataEndpointProxy` cmdlet uses the metadata of an OData endpoint to generate a module that contains cmdlets you can use to manage that OData endpoint.</span></span> <span data-ttu-id="52ff1-109">Modulen baseras på CDXLM.</span><span class="sxs-lookup"><span data-stu-id="52ff1-109">The module is based on CDXML.</span></span> <span data-ttu-id="52ff1-110">När den här cmdleten genererar modulen sparar den modulen till sökvägen och fil namnet som anges av parametern **OutputModule** .</span><span class="sxs-lookup"><span data-stu-id="52ff1-110">After this cmdlet generates the module, it saves that module to the path and file name specified by the **OutputModule** parameter.</span></span>

<span data-ttu-id="52ff1-111">`Export-ODataEndpointProxy` genererar cmdlets för åtgärder för att skapa, läsa, uppdatera och ta bort (CRUD), icke-CRUD åtgärder och associerings manipulering.</span><span class="sxs-lookup"><span data-stu-id="52ff1-111">`Export-ODataEndpointProxy` generates cmdlets for create, read, update, and delete (CRUD) operations, non-CRUD actions, and association manipulation.</span></span>

<span data-ttu-id="52ff1-112">`Export-ODataEndpointProxy` genererar en CDXLM-fil per slut punkts resurs.</span><span class="sxs-lookup"><span data-stu-id="52ff1-112">`Export-ODataEndpointProxy` generates one CDXML file per endpoint resource.</span></span> <span data-ttu-id="52ff1-113">Du kan redigera dessa CDXLM-filer när modulen har genererats.</span><span class="sxs-lookup"><span data-stu-id="52ff1-113">You can edit these CDXML files after the module is generated.</span></span> <span data-ttu-id="52ff1-114">Om du till exempel vill ändra Substantiv-eller verbfras för cmdletarna så att de överensstämmer med rikt linjerna för Windows PowerShell-cmdlet, kan du ändra filen.</span><span class="sxs-lookup"><span data-stu-id="52ff1-114">For example, if you want to change the noun or verb names of the cmdlets to align with Windows PowerShell cmdlet naming guidelines, you can modify the file.</span></span>

<span data-ttu-id="52ff1-115">Varje cmdlet i en genererad modul måste innehålla en **ConnectionURI** -parameter för att kunna ansluta till den slut punkt som modulen hanterar.</span><span class="sxs-lookup"><span data-stu-id="52ff1-115">Every cmdlet in a generated module must include a **ConnectionURI** parameter in order to connect to the endpoint that the module manages.</span></span>

## <span data-ttu-id="52ff1-116">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="52ff1-116">EXAMPLES</span></span>

### <span data-ttu-id="52ff1-117">Exempel 1: generera en modul för att hantera en webb tjänst slut punkt för åter försäljning</span><span class="sxs-lookup"><span data-stu-id="52ff1-117">Example 1: Generate a module to manage a retail web service endpoint</span></span>

```powershell
PS C:\> Export-ODataEndpointProxy -Uri 'http://services.odata.org/v3/(S(snyobsk1hhutkb2yulwldgf1))/odata/odata.svc' -MetadataUri 'http://services.odata.org/v3/(S(snyobsk1hhutkb2yulwldgf1))/odata/odata.svc/$metadata' -AllowUnsecureConnection -OutputModule 'C:\Users\user\GeneratedScript.psm1' -ResourceNameMapping @{Products = 'Merchandise'}
```

<span data-ttu-id="52ff1-118">Det här kommandot genererar en modul för att hantera en tjänst slut punkt för detalj handeln.</span><span class="sxs-lookup"><span data-stu-id="52ff1-118">This command generates a module to manage a retail service endpoint.</span></span> <span data-ttu-id="52ff1-119">Kommandot anger URI för slut punkten och URI: n för slut punktens metadata.</span><span class="sxs-lookup"><span data-stu-id="52ff1-119">The command specifies the URI of the endpoint and the URI of the endpoint metadata.</span></span> <span data-ttu-id="52ff1-120">Kommandot tillhandahåller också en sökväg för utdata och ett namn på en skript-modul som värde för parametern **OutputModule** .</span><span class="sxs-lookup"><span data-stu-id="52ff1-120">The command also provides an output path and script module name as the value of the **OutputModule** parameter.</span></span> <span data-ttu-id="52ff1-121">För värdet för parametern **ResourceNameMapping** tillhandahåller kommandot en hash-tabellen som mappar resurs samlings namnet till önskat Substantiv för cmdlet-uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="52ff1-121">For the value of the **ResourceNameMapping** parameter, the command provides a hashtable that maps the resource collection name to the desired noun for the cmdlet set.</span></span> <span data-ttu-id="52ff1-122">I det här exemplet är produkter resurs samlingens namn och **varorna** är substantiv.</span><span class="sxs-lookup"><span data-stu-id="52ff1-122">In this example, Products is the resource collection name and **Merchandise** is the noun.</span></span> <span data-ttu-id="52ff1-123">Om du vill tillåta anslutningar till icke-SSL-platser, HTTP, i stället för HTTPS, lägger du till parametern **AllowUnsecureConnection** .</span><span class="sxs-lookup"><span data-stu-id="52ff1-123">To allow connections to non-SSL sites, HTTP, as opposed to HTTPS, add the **AllowUnsecureConnection** parameter.</span></span>

## <span data-ttu-id="52ff1-124">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="52ff1-124">PARAMETERS</span></span>

### <span data-ttu-id="52ff1-125">-AllowClobber</span><span class="sxs-lookup"><span data-stu-id="52ff1-125">-AllowClobber</span></span>

<span data-ttu-id="52ff1-126">Anger att denna cmdlet ersätter en befintlig modul.</span><span class="sxs-lookup"><span data-stu-id="52ff1-126">Indicates that this cmdlet replaces an existing module.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: 10
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="52ff1-127">-AllowUnsecureConnection</span><span class="sxs-lookup"><span data-stu-id="52ff1-127">-AllowUnsecureConnection</span></span>

<span data-ttu-id="52ff1-128">Anger att den här modulen kan ansluta till URI: er som inte är SSL-säkrade.</span><span class="sxs-lookup"><span data-stu-id="52ff1-128">Indicates that this module can connect to URIs that are not SSL-secured.</span></span> <span data-ttu-id="52ff1-129">Modulen kan hantera HTTP-platser förutom HTTPS-platser.</span><span class="sxs-lookup"><span data-stu-id="52ff1-129">The module can manage HTTP sites in addition to HTTPS sites.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: 11
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="52ff1-130">-CmdletAdapter</span><span class="sxs-lookup"><span data-stu-id="52ff1-130">-CmdletAdapter</span></span>

<span data-ttu-id="52ff1-131">Anger cmdlet-nätverkskortet.</span><span class="sxs-lookup"><span data-stu-id="52ff1-131">Specifies the cmdlet adapter.</span></span> <span data-ttu-id="52ff1-132">De acceptabla värdena för den här parametern är: ODataAdapter och NetworkControllerAdapter.</span><span class="sxs-lookup"><span data-stu-id="52ff1-132">The acceptable values for this parameter are: ODataAdapter and NetworkControllerAdapter.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: ODataAdapter, NetworkControllerAdapter, ODataV4Adapter

Required: False
Position: 6
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="52ff1-133">-CreateRequestMethod</span><span class="sxs-lookup"><span data-stu-id="52ff1-133">-CreateRequestMethod</span></span>

<span data-ttu-id="52ff1-134">Anger metod för begäran.</span><span class="sxs-lookup"><span data-stu-id="52ff1-134">Specifies the request method.</span></span> <span data-ttu-id="52ff1-135">De acceptabla värdena för den här parametern är: placering, POST och korrigering.</span><span class="sxs-lookup"><span data-stu-id="52ff1-135">The acceptable values for this parameter are: PUT, POST, and PATCH.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Put, Post, Patch

Required: False
Position: 4
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="52ff1-136">-Credential</span><span class="sxs-lookup"><span data-stu-id="52ff1-136">-Credential</span></span>

<span data-ttu-id="52ff1-137">Anger ett användar konto som har åtkomst till OData-slutpunkten.</span><span class="sxs-lookup"><span data-stu-id="52ff1-137">Specifies a user account that has access to the OData endpoint.</span></span> <span data-ttu-id="52ff1-138">Standardvärdet är den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="52ff1-138">The default value is the current user.</span></span> <span data-ttu-id="52ff1-139">Om en fjärrdator kör Windows Vista eller en senare version av Windows-operativsystemet, uppmanas du att ange autentiseringsuppgifter för cmdleten.</span><span class="sxs-lookup"><span data-stu-id="52ff1-139">If a remote computer runs Windows Vista or a later release of the Windows operating system, the cmdlet prompts you for credentials.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: 3
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="52ff1-140">– CustomData</span><span class="sxs-lookup"><span data-stu-id="52ff1-140">-CustomData</span></span>

<span data-ttu-id="52ff1-141">Anger en hash-tabell med anpassade data.</span><span class="sxs-lookup"><span data-stu-id="52ff1-141">Specifies a hash table of custom data.</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: 9
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="52ff1-142">-Force</span><span class="sxs-lookup"><span data-stu-id="52ff1-142">-Force</span></span>

<span data-ttu-id="52ff1-143">Anger att denna cmdlet skriver över en befintlig genererad modul med samma namn i en befintlig `Modules` mapp.</span><span class="sxs-lookup"><span data-stu-id="52ff1-143">Indicates that this cmdlet overwrites an existing generated module of the same name in an existing `Modules` folder.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: 8
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="52ff1-144">– Sidhuvud</span><span class="sxs-lookup"><span data-stu-id="52ff1-144">-Headers</span></span>

<span data-ttu-id="52ff1-145">Anger webb begärans rubriker.</span><span class="sxs-lookup"><span data-stu-id="52ff1-145">Specifies the headers of the web request.</span></span> <span data-ttu-id="52ff1-146">Ange en hash-tabell eller-ord lista.</span><span class="sxs-lookup"><span data-stu-id="52ff1-146">Enter a hash table or dictionary.</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: 12
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="52ff1-147">-MetadataUri</span><span class="sxs-lookup"><span data-stu-id="52ff1-147">-MetadataUri</span></span>

<span data-ttu-id="52ff1-148">Anger URI för slut punktens metadata.</span><span class="sxs-lookup"><span data-stu-id="52ff1-148">Specifies the URI of the metadata of the endpoint.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="52ff1-149">-OutputModule</span><span class="sxs-lookup"><span data-stu-id="52ff1-149">-OutputModule</span></span>

<span data-ttu-id="52ff1-150">Anger den sökväg och det Modulnamn som denna cmdlet ska spara den genererade modulen med proxy-kommandon i.</span><span class="sxs-lookup"><span data-stu-id="52ff1-150">Specifies the path and module name to which this cmdlet saves the generated module of proxy commands.</span></span>

<span data-ttu-id="52ff1-151">Denna cmdlet kopierar en binär modul, ett modul manifest och en format fil, om det är tillämpligt, till den angivna mappen.</span><span class="sxs-lookup"><span data-stu-id="52ff1-151">This cmdlet copies a binary module, module manifest, and formatting file, if applicable, to the specified folder.</span></span> <span data-ttu-id="52ff1-152">Om du bara anger namnet på modulen `Export-ODataEndpointProxy` sparar modulen i `$home\Documents\WindowsPowerShell\Modules` mappen.</span><span class="sxs-lookup"><span data-stu-id="52ff1-152">If you specify only the name of the module, `Export-ODataEndpointProxy` saves the module in the `$home\Documents\WindowsPowerShell\Modules` folder.</span></span> <span data-ttu-id="52ff1-153">Om du anger en sökväg skapar cmdleten mappen modul i den sökvägen.</span><span class="sxs-lookup"><span data-stu-id="52ff1-153">If you specify a path, the cmdlet creates the module folder in that path.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="52ff1-154">-ResourceNameMapping</span><span class="sxs-lookup"><span data-stu-id="52ff1-154">-ResourceNameMapping</span></span>

<span data-ttu-id="52ff1-155">Anger en hash-tabellen som innehåller mappningar som gör att du kan anpassa de genererade cmdletarna.</span><span class="sxs-lookup"><span data-stu-id="52ff1-155">Specifies a hashtable that contains mappings that let you customize the generated cmdlets.</span></span> <span data-ttu-id="52ff1-156">I den här hash-tabellen är resurs samlingens namn nyckeln.</span><span class="sxs-lookup"><span data-stu-id="52ff1-156">In this hashtable, the resource collection name is the key.</span></span> <span data-ttu-id="52ff1-157">Önskad cmdlet Substantiv är värdet.</span><span class="sxs-lookup"><span data-stu-id="52ff1-157">The desired cmdlet noun is the value.</span></span>

<span data-ttu-id="52ff1-158">I tabellen hash är produkter till exempel `@{Products = 'Merchandise'}` resurs **Products** samlings namnet som fungerar som nyckel.</span><span class="sxs-lookup"><span data-stu-id="52ff1-158">For example, in the hash table `@{Products = 'Merchandise'}`, **Products** is the resource collection name that serves as the key.</span></span> <span data-ttu-id="52ff1-159">**Produkter** är den resulterande cmdleten substantiv.</span><span class="sxs-lookup"><span data-stu-id="52ff1-159">**Merchandise** is the resulting cmdlet noun.</span></span> <span data-ttu-id="52ff1-160">De genererade cmdlet-namnen kanske inte överensstämmer med namngivnings rikt linjerna för Windows PowerShell-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="52ff1-160">The generated cmdlet names might not align to Windows PowerShell cmdlet naming guidelines.</span></span> <span data-ttu-id="52ff1-161">Du kan ändra resursens CDXLM-fil om du vill ändra cmdlet-namnen när denna cmdlet skapar modulen.</span><span class="sxs-lookup"><span data-stu-id="52ff1-161">You can modify the resource CDXML file to change the cmdlet names after this cmdlet creates the module.</span></span> <span data-ttu-id="52ff1-162">Mer information finns i [rikt linjer för starkt uppmuntrande utveckling](/powershell/scripting/developer/cmdlet/strongly-encouraged-development-guidelines).</span><span class="sxs-lookup"><span data-stu-id="52ff1-162">For more information, see [Strongly Encouraged Development Guidelines](/powershell/scripting/developer/cmdlet/strongly-encouraged-development-guidelines).</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: 7
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="52ff1-163">-UpdateRequestMethod</span><span class="sxs-lookup"><span data-stu-id="52ff1-163">-UpdateRequestMethod</span></span>

<span data-ttu-id="52ff1-164">Anger metoden för att uppdatera begäran.</span><span class="sxs-lookup"><span data-stu-id="52ff1-164">Specifies the update request method.</span></span> <span data-ttu-id="52ff1-165">De acceptabla värdena för den här parametern är: placering, POST och korrigering.</span><span class="sxs-lookup"><span data-stu-id="52ff1-165">The acceptable values for this parameter are: PUT, POST, and PATCH.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Put, Post, Patch

Required: False
Position: 5
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="52ff1-166">-URI</span><span class="sxs-lookup"><span data-stu-id="52ff1-166">-Uri</span></span>

<span data-ttu-id="52ff1-167">Anger slut punktens URI.</span><span class="sxs-lookup"><span data-stu-id="52ff1-167">Specifies the URI of the endpoint.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="52ff1-168">-Confirm</span><span class="sxs-lookup"><span data-stu-id="52ff1-168">-Confirm</span></span>

<span data-ttu-id="52ff1-169">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="52ff1-169">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="52ff1-170">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="52ff1-170">-WhatIf</span></span>

<span data-ttu-id="52ff1-171">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="52ff1-171">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="52ff1-172">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="52ff1-172">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="52ff1-173">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="52ff1-173">CommonParameters</span></span>

<span data-ttu-id="52ff1-174">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="52ff1-174">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="52ff1-175">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="52ff1-175">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="52ff1-176">INDATA</span><span class="sxs-lookup"><span data-stu-id="52ff1-176">INPUTS</span></span>

## <span data-ttu-id="52ff1-177">UTDATA</span><span class="sxs-lookup"><span data-stu-id="52ff1-177">OUTPUTS</span></span>

## <span data-ttu-id="52ff1-178">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="52ff1-178">NOTES</span></span>

## <span data-ttu-id="52ff1-179">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="52ff1-179">RELATED LINKS</span></span>

<span data-ttu-id="52ff1-180">[OData-bibliotek](/previous-versions/dotnet/wcf-data-services/hh525392(v=vs.103))</span><span class="sxs-lookup"><span data-stu-id="52ff1-180">[OData Library](/previous-versions/dotnet/wcf-data-services/hh525392(v=vs.103))</span></span>

[<span data-ttu-id="52ff1-181">Vad är OData-protokollet?</span><span class="sxs-lookup"><span data-stu-id="52ff1-181">What is the OData Protocol?</span></span>](https://www.odata.org/)

[<span data-ttu-id="52ff1-182">Invoke-RestMethod</span><span class="sxs-lookup"><span data-stu-id="52ff1-182">Invoke-RestMethod</span></span>](../Microsoft.PowerShell.Utility/Invoke-RestMethod.md)
