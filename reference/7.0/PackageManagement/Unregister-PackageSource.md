---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 05/24/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/unregister-packagesource?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unregister-PackageSource
ms.openlocfilehash: 06a4649d0d2f0912807219f25e60d85ba22564b0
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93262226"
---
# <span data-ttu-id="a800c-103">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="a800c-103">Unregister-PackageSource</span></span>

## <span data-ttu-id="a800c-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="a800c-104">SYNOPSIS</span></span>
<span data-ttu-id="a800c-105">Tar bort en registrerad paket källa.</span><span class="sxs-lookup"><span data-stu-id="a800c-105">Removes a registered package source.</span></span>

## <span data-ttu-id="a800c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a800c-106">SYNTAX</span></span>

### <span data-ttu-id="a800c-107">SourceBySearch</span><span class="sxs-lookup"><span data-stu-id="a800c-107">SourceBySearch</span></span>

```
Unregister-PackageSource [[-Source] <String>] [-Location <String>] [-Credential <PSCredential>]
 [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-ProviderName <String>] [<CommonParameters>]
```

### <span data-ttu-id="a800c-108">SourceByInputObject</span><span class="sxs-lookup"><span data-stu-id="a800c-108">SourceByInputObject</span></span>

```
Unregister-PackageSource -InputObject <PackageSource[]> [-Credential <PSCredential>] [-Force]
 [-ForceBootstrap] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="a800c-109">NuGet: SourceByInputObject</span><span class="sxs-lookup"><span data-stu-id="a800c-109">NuGet:SourceByInputObject</span></span>

```
Unregister-PackageSource [-Credential <PSCredential>] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-ConfigFile <String>] [-SkipValidate] [<CommonParameters>]
```

### <span data-ttu-id="a800c-110">NuGet: SourceBySearch</span><span class="sxs-lookup"><span data-stu-id="a800c-110">NuGet:SourceBySearch</span></span>

```
Unregister-PackageSource [-Credential <PSCredential>] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-ConfigFile <String>] [-SkipValidate] [<CommonParameters>]
```

### <span data-ttu-id="a800c-111">PowerShellGet: SourceByInputObject</span><span class="sxs-lookup"><span data-stu-id="a800c-111">PowerShellGet:SourceByInputObject</span></span>

```
Unregister-PackageSource [-Credential <PSCredential>] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [<CommonParameters>]
```

### <span data-ttu-id="a800c-112">PowerShellGet: SourceBySearch</span><span class="sxs-lookup"><span data-stu-id="a800c-112">PowerShellGet:SourceBySearch</span></span>

```
Unregister-PackageSource [-Credential <PSCredential>] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [<CommonParameters>]
```

## <span data-ttu-id="a800c-113">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="a800c-113">DESCRIPTION</span></span>

<span data-ttu-id="a800c-114">`Unregister-PackageSource`Cmdleten tar bort en registrerad paket källa.</span><span class="sxs-lookup"><span data-stu-id="a800c-114">The `Unregister-PackageSource` cmdlet removes a registered package source.</span></span> <span data-ttu-id="a800c-115">Paket källor hanteras alltid av en paket leverantör.</span><span class="sxs-lookup"><span data-stu-id="a800c-115">Package sources are always managed by a package provider.</span></span> <span data-ttu-id="a800c-116">Använd cmdleten för att hitta paket källor `Get-PackageSource` .</span><span class="sxs-lookup"><span data-stu-id="a800c-116">To find package sources, use the `Get-PackageSource` cmdlet.</span></span>

## <span data-ttu-id="a800c-117">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="a800c-117">EXAMPLES</span></span>

### <span data-ttu-id="a800c-118">Exempel 1: avregistrera en paket källa för NuGet-providern</span><span class="sxs-lookup"><span data-stu-id="a800c-118">Example 1: Unregister a package source for the Nuget provider</span></span>

<span data-ttu-id="a800c-119">`Unregister-PackageSource`Cmdleten avregistrerar en paket källa från den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="a800c-119">The `Unregister-PackageSource` cmdlet unregisters a package source from the local computer.</span></span> <span data-ttu-id="a800c-120">Parametrarna **plats** och **Provider** kan användas för att ytterligare ange vilken källa som ska tas bort.</span><span class="sxs-lookup"><span data-stu-id="a800c-120">The **Location** and **Provider** parameters can be used to further specify the source to remove.</span></span>

```
PS> Unregister-PackageSource -Source MyNuGet
```

<span data-ttu-id="a800c-121">`Unregister-PackageSource`Cmdleten använder parametern **Source** för att ange vilken källa som ska tas bort.</span><span class="sxs-lookup"><span data-stu-id="a800c-121">The `Unregister-PackageSource` cmdlet uses the **Source** parameter to specify which source to remove.</span></span>

### <span data-ttu-id="a800c-122">Exempel 2: Använd ett PackageSource-objekt för att avregistrera ett paket</span><span class="sxs-lookup"><span data-stu-id="a800c-122">Example 2: Use a PackageSource object to unregister a package</span></span>

<span data-ttu-id="a800c-123">I det här exemplet används `Get-PackageSource` och `Unregister-PackageSource` för att avregistrera en paket källa.</span><span class="sxs-lookup"><span data-stu-id="a800c-123">This example uses the `Get-PackageSource` and `Unregister-PackageSource` to unregister a package source.</span></span> <span data-ttu-id="a800c-124">**PackageSource** -objektet lagras i en variabel.</span><span class="sxs-lookup"><span data-stu-id="a800c-124">The **PackageSource** object is stored in a variable.</span></span>

```
PS> $pkgsource = Get-PackageSource -Name MyNuGet
PS> Unregister-PackageSource -InputObject $pkgsource
```

<span data-ttu-id="a800c-125">`$pkgsource`Variabeln lagrar de **PackageSource** som skapats av `Get-PackageSource` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a800c-125">The `$pkgsource` variable stores the **PackageSource** created by the `Get-PackageSource` cmdlet.</span></span>
<span data-ttu-id="a800c-126">`Unregister-PackageSource` använder `$pkgsource` som-indatamängden för parametern **InputObject** .</span><span class="sxs-lookup"><span data-stu-id="a800c-126">`Unregister-PackageSource` uses the `$pkgsource` as input to the **InputObject** parameter.</span></span>

<span data-ttu-id="a800c-127">Alternativt `Unregister-PackageSource` kan cmdleten ange ett värde för parametern **InputObject** :</span><span class="sxs-lookup"><span data-stu-id="a800c-127">As an alternative, the `Unregister-PackageSource` cmdlet can specify a value for the **InputObject** parameter:</span></span>

`Unregister-PackageSource -InputObject ( Get-PackageSource -Name MyNuGet )`

## <span data-ttu-id="a800c-128">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="a800c-128">PARAMETERS</span></span>

### <span data-ttu-id="a800c-129">– ConfigFile</span><span class="sxs-lookup"><span data-stu-id="a800c-129">-ConfigFile</span></span>

<span data-ttu-id="a800c-130">Anger en konfigurations fil.</span><span class="sxs-lookup"><span data-stu-id="a800c-130">Specifies a configuration file.</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet:SourceByInputObject, NuGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a800c-131">-Credential</span><span class="sxs-lookup"><span data-stu-id="a800c-131">-Credential</span></span>

<span data-ttu-id="a800c-132">Anger ett användar konto som har behörighet att komma åt datorn och köra kommandon.</span><span class="sxs-lookup"><span data-stu-id="a800c-132">Specifies a user account that has permission to access the computer and run commands.</span></span> <span data-ttu-id="a800c-133">Ange ett användar namn, till exempel **user01** , **Domain01\User01** , eller ange ett **PSCredential** -objekt som genereras av `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a800c-133">Type a user name, such as **User01** , **Domain01\User01** , or enter a **PSCredential** object, generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="a800c-134">Om du anger ett användar namn uppmanas du att ange ett lösen ord.</span><span class="sxs-lookup"><span data-stu-id="a800c-134">If you type a user name, you're prompted for a password.</span></span>

<span data-ttu-id="a800c-135">När parametern **Credential** inte anges används det aktuella användar kontot.</span><span class="sxs-lookup"><span data-stu-id="a800c-135">When the **Credential** parameter isn't specified, the current user account is used.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a800c-136">-Force</span><span class="sxs-lookup"><span data-stu-id="a800c-136">-Force</span></span>

<span data-ttu-id="a800c-137">Tvingar kommandot att köras utan att fråga användaren om bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="a800c-137">Forces the command to run without asking for user confirmation.</span></span> <span data-ttu-id="a800c-138">Åsidosätter begränsningar som förhindrar att `Unregister-PackageSource` de lyckas, med undantag för säkerhet.</span><span class="sxs-lookup"><span data-stu-id="a800c-138">Overrides restrictions that prevent `Unregister-PackageSource` from succeeding, with the exception of security.</span></span>

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

### <span data-ttu-id="a800c-139">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="a800c-139">-ForceBootstrap</span></span>

<span data-ttu-id="a800c-140">Anger att `Unregister-PackageSource` **PackageManagement** automatiskt ska avinstallera paket leverantören för den angivna paket källan.</span><span class="sxs-lookup"><span data-stu-id="a800c-140">Indicates that `Unregister-PackageSource` forces **PackageManagement** to automatically uninstall the package provider for the specified package source.</span></span>

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

### <span data-ttu-id="a800c-141">– InputObject</span><span class="sxs-lookup"><span data-stu-id="a800c-141">-InputObject</span></span>

<span data-ttu-id="a800c-142">Accepterar pipeline-inflöde som anger **PackageSource** -objektet från `Get-PackageSource` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a800c-142">Accepts pipeline input that specifies the **PackageSource** object from the `Get-PackageSource` cmdlet.</span></span> <span data-ttu-id="a800c-143">**InputObject** accepterar **PackageSource** -objektet som ett `Get-PackageSource` värde eller en variabel som innehåller objektet.</span><span class="sxs-lookup"><span data-stu-id="a800c-143">**InputObject** accepts the **PackageSource** object as a `Get-PackageSource` value or a variable that contains the object.</span></span>

```yaml
Type: Microsoft.PackageManagement.Packaging.PackageSource[]
Parameter Sets: SourceByInputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="a800c-144">– Plats</span><span class="sxs-lookup"><span data-stu-id="a800c-144">-Location</span></span>

<span data-ttu-id="a800c-145">Anger den plats som paket källan pekar på.</span><span class="sxs-lookup"><span data-stu-id="a800c-145">Specifies the location to which a package source points.</span></span> <span data-ttu-id="a800c-146">Värdet för den här parametern kan vara en URI, en fil Sök väg eller något annat mål format som stöds av paket leverantören.</span><span class="sxs-lookup"><span data-stu-id="a800c-146">The value of this parameter can be a URI, a file path, or any other destination format that is supported by the package provider.</span></span>

```yaml
Type: System.String
Parameter Sets: SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a800c-147">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="a800c-147">-PackageManagementProvider</span></span>

<span data-ttu-id="a800c-148">Anger **PackageManagement** -providern.</span><span class="sxs-lookup"><span data-stu-id="a800c-148">Specifies the **PackageManagement** provider.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:SourceByInputObject, PowerShellGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a800c-149">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="a800c-149">-ProviderName</span></span>

<span data-ttu-id="a800c-150">Anger namnet på providern.</span><span class="sxs-lookup"><span data-stu-id="a800c-150">Specifies the provider name.</span></span>

```yaml
Type: System.String
Parameter Sets: SourceBySearch
Aliases: Provider
Accepted values: Bootstrap, NuGet, PowerShellGet

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a800c-151">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="a800c-151">-PublishLocation</span></span>

<span data-ttu-id="a800c-152">Anger publicerings platsen.</span><span class="sxs-lookup"><span data-stu-id="a800c-152">Specifies the publish location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:SourceByInputObject, PowerShellGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a800c-153">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="a800c-153">-ScriptPublishLocation</span></span>

<span data-ttu-id="a800c-154">Anger skriptets publicerings plats.</span><span class="sxs-lookup"><span data-stu-id="a800c-154">Specifies the script publish location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:SourceByInputObject, PowerShellGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a800c-155">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="a800c-155">-ScriptSourceLocation</span></span>

<span data-ttu-id="a800c-156">Anger sökvägen till skript källan.</span><span class="sxs-lookup"><span data-stu-id="a800c-156">Specifies the script source location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:SourceByInputObject, PowerShellGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a800c-157">-SkipValidate</span><span class="sxs-lookup"><span data-stu-id="a800c-157">-SkipValidate</span></span>

<span data-ttu-id="a800c-158">Växel som hoppar över verifiering av autentiseringsuppgifterna för en paket källa.</span><span class="sxs-lookup"><span data-stu-id="a800c-158">Switch that skips validating the credentials of a package source.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:SourceByInputObject, NuGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a800c-159">-Source</span><span class="sxs-lookup"><span data-stu-id="a800c-159">-Source</span></span>

<span data-ttu-id="a800c-160">Anger det egna namnet på paket källan.</span><span class="sxs-lookup"><span data-stu-id="a800c-160">Specifies the friendly name of the package source.</span></span>

```yaml
Type: System.String
Parameter Sets: SourceBySearch
Aliases: Name

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a800c-161">-Confirm</span><span class="sxs-lookup"><span data-stu-id="a800c-161">-Confirm</span></span>

<span data-ttu-id="a800c-162">Du uppmanas att bekräfta innan körs `Unregister-PackageSource` .</span><span class="sxs-lookup"><span data-stu-id="a800c-162">Prompts you for confirmation before `Unregister-PackageSource` is run.</span></span>

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

### <span data-ttu-id="a800c-163">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="a800c-163">-WhatIf</span></span>

<span data-ttu-id="a800c-164">Visar vad som händer om `Unregister-PackageSource` cmdleten körs.</span><span class="sxs-lookup"><span data-stu-id="a800c-164">Shows what would happen if `Unregister-PackageSource` cmdlet is run.</span></span> <span data-ttu-id="a800c-165">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="a800c-165">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="a800c-166">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a800c-166">CommonParameters</span></span>

<span data-ttu-id="a800c-167">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a800c-167">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a800c-168">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="a800c-168">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a800c-169">INDATA</span><span class="sxs-lookup"><span data-stu-id="a800c-169">INPUTS</span></span>

### <span data-ttu-id="a800c-170">`Unregister-PackageSource` accepterar **PackageSource** -objekt från pipelinen som inmatade.</span><span class="sxs-lookup"><span data-stu-id="a800c-170">`Unregister-PackageSource` accepts **PackageSource** objects from the pipeline as input.</span></span>

## <span data-ttu-id="a800c-171">UTDATA</span><span class="sxs-lookup"><span data-stu-id="a800c-171">OUTPUTS</span></span>

### <span data-ttu-id="a800c-172">`Unregister-PackageSource` genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="a800c-172">`Unregister-PackageSource` doesn't generate any output.</span></span>

## <span data-ttu-id="a800c-173">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="a800c-173">NOTES</span></span>

<span data-ttu-id="a800c-174">Att inkludera en paket leverantör i ett kommando kan göra dynamiska parametrar tillgängliga för en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a800c-174">Including a package provider in a command can make dynamic parameters available to a cmdlet.</span></span> <span data-ttu-id="a800c-175">Dynamiska parametrar är speciella för en paket leverantör.</span><span class="sxs-lookup"><span data-stu-id="a800c-175">Dynamic parameters are specific to a package provider.</span></span> <span data-ttu-id="a800c-176">`Get-Help`Cmdleten listar en cmdlets parameter uppsättningar och inkluderar providerns parameter uppsättning.</span><span class="sxs-lookup"><span data-stu-id="a800c-176">The `Get-Help` cmdlet lists a cmdlet's parameter sets and includes the provider's parameter set.</span></span>

## <span data-ttu-id="a800c-177">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="a800c-177">RELATED LINKS</span></span>

[<span data-ttu-id="a800c-178">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="a800c-178">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="a800c-179">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="a800c-179">Get-Credential</span></span>](../Microsoft.PowerShell.Security/Get-Credential.md)

[<span data-ttu-id="a800c-180">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="a800c-180">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="a800c-181">Registrera – PackageSource</span><span class="sxs-lookup"><span data-stu-id="a800c-181">Register-PackageSource</span></span>](Register-PackageSource.md)

[<span data-ttu-id="a800c-182">Set-PackageSource</span><span class="sxs-lookup"><span data-stu-id="a800c-182">Set-PackageSource</span></span>](Set-PackageSource.md)