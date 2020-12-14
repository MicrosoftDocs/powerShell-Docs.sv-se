---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
Locale: en-US
Module Name: PackageManagement
ms.date: 05/24/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/unregister-packagesource?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unregister-PackageSource
ms.openlocfilehash: 6ef89e9143fe8883bc98723d10775bf739fe72f9
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708988"
---
# <span data-ttu-id="d6ebd-102">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="d6ebd-102">Unregister-PackageSource</span></span>

## <span data-ttu-id="d6ebd-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="d6ebd-103">SYNOPSIS</span></span>
<span data-ttu-id="d6ebd-104">Tar bort en registrerad paket källa.</span><span class="sxs-lookup"><span data-stu-id="d6ebd-104">Removes a registered package source.</span></span>

## <span data-ttu-id="d6ebd-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d6ebd-105">SYNTAX</span></span>

### <span data-ttu-id="d6ebd-106">SourceBySearch</span><span class="sxs-lookup"><span data-stu-id="d6ebd-106">SourceBySearch</span></span>

```
Unregister-PackageSource [[-Source] <String>] [-Location <String>] [-Credential <PSCredential>]
 [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-ProviderName <String>] [<CommonParameters>]
```

### <span data-ttu-id="d6ebd-107">SourceByInputObject</span><span class="sxs-lookup"><span data-stu-id="d6ebd-107">SourceByInputObject</span></span>

```
Unregister-PackageSource -InputObject <PackageSource[]> [-Credential <PSCredential>] [-Force]
 [-ForceBootstrap] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="d6ebd-108">NuGet: SourceByInputObject</span><span class="sxs-lookup"><span data-stu-id="d6ebd-108">NuGet:SourceByInputObject</span></span>

```
Unregister-PackageSource [-Credential <PSCredential>] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-ConfigFile <String>] [-SkipValidate] [<CommonParameters>]
```

### <span data-ttu-id="d6ebd-109">NuGet: SourceBySearch</span><span class="sxs-lookup"><span data-stu-id="d6ebd-109">NuGet:SourceBySearch</span></span>

```
Unregister-PackageSource [-Credential <PSCredential>] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-ConfigFile <String>] [-SkipValidate] [<CommonParameters>]
```

### <span data-ttu-id="d6ebd-110">PowerShellGet: SourceByInputObject</span><span class="sxs-lookup"><span data-stu-id="d6ebd-110">PowerShellGet:SourceByInputObject</span></span>

```
Unregister-PackageSource [-Credential <PSCredential>] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [<CommonParameters>]
```

### <span data-ttu-id="d6ebd-111">PowerShellGet: SourceBySearch</span><span class="sxs-lookup"><span data-stu-id="d6ebd-111">PowerShellGet:SourceBySearch</span></span>

```
Unregister-PackageSource [-Credential <PSCredential>] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [<CommonParameters>]
```

## <span data-ttu-id="d6ebd-112">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="d6ebd-112">DESCRIPTION</span></span>

<span data-ttu-id="d6ebd-113">`Unregister-PackageSource`Cmdleten tar bort en registrerad paket källa.</span><span class="sxs-lookup"><span data-stu-id="d6ebd-113">The `Unregister-PackageSource` cmdlet removes a registered package source.</span></span> <span data-ttu-id="d6ebd-114">Paket källor hanteras alltid av en paket leverantör.</span><span class="sxs-lookup"><span data-stu-id="d6ebd-114">Package sources are always managed by a package provider.</span></span> <span data-ttu-id="d6ebd-115">Använd cmdleten för att hitta paket källor `Get-PackageSource` .</span><span class="sxs-lookup"><span data-stu-id="d6ebd-115">To find package sources, use the `Get-PackageSource` cmdlet.</span></span>

## <span data-ttu-id="d6ebd-116">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="d6ebd-116">EXAMPLES</span></span>

### <span data-ttu-id="d6ebd-117">Exempel 1: avregistrera en paket källa för NuGet-providern</span><span class="sxs-lookup"><span data-stu-id="d6ebd-117">Example 1: Unregister a package source for the Nuget provider</span></span>

<span data-ttu-id="d6ebd-118">`Unregister-PackageSource`Cmdleten avregistrerar en paket källa från den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="d6ebd-118">The `Unregister-PackageSource` cmdlet unregisters a package source from the local computer.</span></span> <span data-ttu-id="d6ebd-119">Parametrarna **plats** och **Provider** kan användas för att ytterligare ange vilken källa som ska tas bort.</span><span class="sxs-lookup"><span data-stu-id="d6ebd-119">The **Location** and **Provider** parameters can be used to further specify the source to remove.</span></span>

```
PS> Unregister-PackageSource -Source MyNuGet
```

<span data-ttu-id="d6ebd-120">`Unregister-PackageSource`Cmdleten använder parametern **Source** för att ange vilken källa som ska tas bort.</span><span class="sxs-lookup"><span data-stu-id="d6ebd-120">The `Unregister-PackageSource` cmdlet uses the **Source** parameter to specify which source to remove.</span></span>

### <span data-ttu-id="d6ebd-121">Exempel 2: Använd ett PackageSource-objekt för att avregistrera ett paket</span><span class="sxs-lookup"><span data-stu-id="d6ebd-121">Example 2: Use a PackageSource object to unregister a package</span></span>

<span data-ttu-id="d6ebd-122">I det här exemplet används `Get-PackageSource` och `Unregister-PackageSource` för att avregistrera en paket källa.</span><span class="sxs-lookup"><span data-stu-id="d6ebd-122">This example uses the `Get-PackageSource` and `Unregister-PackageSource` to unregister a package source.</span></span> <span data-ttu-id="d6ebd-123">**PackageSource** -objektet lagras i en variabel.</span><span class="sxs-lookup"><span data-stu-id="d6ebd-123">The **PackageSource** object is stored in a variable.</span></span>

```
PS> $pkgsource = Get-PackageSource -Name MyNuGet
PS> Unregister-PackageSource -InputObject $pkgsource
```

<span data-ttu-id="d6ebd-124">`$pkgsource`Variabeln lagrar de **PackageSource** som skapats av `Get-PackageSource` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="d6ebd-124">The `$pkgsource` variable stores the **PackageSource** created by the `Get-PackageSource` cmdlet.</span></span>
<span data-ttu-id="d6ebd-125">`Unregister-PackageSource` använder `$pkgsource` som-indatamängden för parametern **InputObject** .</span><span class="sxs-lookup"><span data-stu-id="d6ebd-125">`Unregister-PackageSource` uses the `$pkgsource` as input to the **InputObject** parameter.</span></span>

<span data-ttu-id="d6ebd-126">Alternativt `Unregister-PackageSource` kan cmdleten ange ett värde för parametern **InputObject** :</span><span class="sxs-lookup"><span data-stu-id="d6ebd-126">As an alternative, the `Unregister-PackageSource` cmdlet can specify a value for the **InputObject** parameter:</span></span>

`Unregister-PackageSource -InputObject ( Get-PackageSource -Name MyNuGet )`

## <span data-ttu-id="d6ebd-127">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="d6ebd-127">PARAMETERS</span></span>

### <span data-ttu-id="d6ebd-128">– ConfigFile</span><span class="sxs-lookup"><span data-stu-id="d6ebd-128">-ConfigFile</span></span>

<span data-ttu-id="d6ebd-129">Anger en konfigurations fil.</span><span class="sxs-lookup"><span data-stu-id="d6ebd-129">Specifies a configuration file.</span></span>

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

### <span data-ttu-id="d6ebd-130">-Credential</span><span class="sxs-lookup"><span data-stu-id="d6ebd-130">-Credential</span></span>

<span data-ttu-id="d6ebd-131">Anger ett användar konto som har behörighet att komma åt datorn och köra kommandon.</span><span class="sxs-lookup"><span data-stu-id="d6ebd-131">Specifies a user account that has permission to access the computer and run commands.</span></span> <span data-ttu-id="d6ebd-132">Ange ett användar namn, till exempel **user01**, **Domain01\User01**, eller ange ett **PSCredential** -objekt som genereras av `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="d6ebd-132">Type a user name, such as **User01**, **Domain01\User01**, or enter a **PSCredential** object, generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="d6ebd-133">Om du anger ett användar namn uppmanas du att ange ett lösen ord.</span><span class="sxs-lookup"><span data-stu-id="d6ebd-133">If you type a user name, you're prompted for a password.</span></span>

<span data-ttu-id="d6ebd-134">När parametern **Credential** inte anges används det aktuella användar kontot.</span><span class="sxs-lookup"><span data-stu-id="d6ebd-134">When the **Credential** parameter isn't specified, the current user account is used.</span></span>

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

### <span data-ttu-id="d6ebd-135">-Force</span><span class="sxs-lookup"><span data-stu-id="d6ebd-135">-Force</span></span>

<span data-ttu-id="d6ebd-136">Tvingar kommandot att köras utan att fråga användaren om bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="d6ebd-136">Forces the command to run without asking for user confirmation.</span></span> <span data-ttu-id="d6ebd-137">Åsidosätter begränsningar som förhindrar att `Unregister-PackageSource` de lyckas, med undantag för säkerhet.</span><span class="sxs-lookup"><span data-stu-id="d6ebd-137">Overrides restrictions that prevent `Unregister-PackageSource` from succeeding, with the exception of security.</span></span>

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

### <span data-ttu-id="d6ebd-138">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="d6ebd-138">-ForceBootstrap</span></span>

<span data-ttu-id="d6ebd-139">Anger att `Unregister-PackageSource` **PackageManagement** automatiskt ska avinstallera paket leverantören för den angivna paket källan.</span><span class="sxs-lookup"><span data-stu-id="d6ebd-139">Indicates that `Unregister-PackageSource` forces **PackageManagement** to automatically uninstall the package provider for the specified package source.</span></span>

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

### <span data-ttu-id="d6ebd-140">– InputObject</span><span class="sxs-lookup"><span data-stu-id="d6ebd-140">-InputObject</span></span>

<span data-ttu-id="d6ebd-141">Accepterar pipeline-inflöde som anger **PackageSource** -objektet från `Get-PackageSource` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="d6ebd-141">Accepts pipeline input that specifies the **PackageSource** object from the `Get-PackageSource` cmdlet.</span></span> <span data-ttu-id="d6ebd-142">**InputObject** accepterar **PackageSource** -objektet som ett `Get-PackageSource` värde eller en variabel som innehåller objektet.</span><span class="sxs-lookup"><span data-stu-id="d6ebd-142">**InputObject** accepts the **PackageSource** object as a `Get-PackageSource` value or a variable that contains the object.</span></span>

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

### <span data-ttu-id="d6ebd-143">– Plats</span><span class="sxs-lookup"><span data-stu-id="d6ebd-143">-Location</span></span>

<span data-ttu-id="d6ebd-144">Anger den plats som paket källan pekar på.</span><span class="sxs-lookup"><span data-stu-id="d6ebd-144">Specifies the location to which a package source points.</span></span> <span data-ttu-id="d6ebd-145">Värdet för den här parametern kan vara en URI, en fil Sök väg eller något annat mål format som stöds av paket leverantören.</span><span class="sxs-lookup"><span data-stu-id="d6ebd-145">The value of this parameter can be a URI, a file path, or any other destination format that is supported by the package provider.</span></span>

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

### <span data-ttu-id="d6ebd-146">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="d6ebd-146">-PackageManagementProvider</span></span>

<span data-ttu-id="d6ebd-147">Anger **PackageManagement** -providern.</span><span class="sxs-lookup"><span data-stu-id="d6ebd-147">Specifies the **PackageManagement** provider.</span></span>

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

### <span data-ttu-id="d6ebd-148">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="d6ebd-148">-ProviderName</span></span>

<span data-ttu-id="d6ebd-149">Anger namnet på providern.</span><span class="sxs-lookup"><span data-stu-id="d6ebd-149">Specifies the provider name.</span></span>

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

### <span data-ttu-id="d6ebd-150">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="d6ebd-150">-PublishLocation</span></span>

<span data-ttu-id="d6ebd-151">Anger publicerings platsen.</span><span class="sxs-lookup"><span data-stu-id="d6ebd-151">Specifies the publish location.</span></span>

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

### <span data-ttu-id="d6ebd-152">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="d6ebd-152">-ScriptPublishLocation</span></span>

<span data-ttu-id="d6ebd-153">Anger skriptets publicerings plats.</span><span class="sxs-lookup"><span data-stu-id="d6ebd-153">Specifies the script publish location.</span></span>

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

### <span data-ttu-id="d6ebd-154">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="d6ebd-154">-ScriptSourceLocation</span></span>

<span data-ttu-id="d6ebd-155">Anger sökvägen till skript källan.</span><span class="sxs-lookup"><span data-stu-id="d6ebd-155">Specifies the script source location.</span></span>

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

### <span data-ttu-id="d6ebd-156">-SkipValidate</span><span class="sxs-lookup"><span data-stu-id="d6ebd-156">-SkipValidate</span></span>

<span data-ttu-id="d6ebd-157">Växel som hoppar över verifiering av autentiseringsuppgifterna för en paket källa.</span><span class="sxs-lookup"><span data-stu-id="d6ebd-157">Switch that skips validating the credentials of a package source.</span></span>

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

### <span data-ttu-id="d6ebd-158">-Source</span><span class="sxs-lookup"><span data-stu-id="d6ebd-158">-Source</span></span>

<span data-ttu-id="d6ebd-159">Anger det egna namnet på paket källan.</span><span class="sxs-lookup"><span data-stu-id="d6ebd-159">Specifies the friendly name of the package source.</span></span>

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

### <span data-ttu-id="d6ebd-160">-Confirm</span><span class="sxs-lookup"><span data-stu-id="d6ebd-160">-Confirm</span></span>

<span data-ttu-id="d6ebd-161">Du uppmanas att bekräfta innan körs `Unregister-PackageSource` .</span><span class="sxs-lookup"><span data-stu-id="d6ebd-161">Prompts you for confirmation before `Unregister-PackageSource` is run.</span></span>

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

### <span data-ttu-id="d6ebd-162">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="d6ebd-162">-WhatIf</span></span>

<span data-ttu-id="d6ebd-163">Visar vad som händer om `Unregister-PackageSource` cmdleten körs.</span><span class="sxs-lookup"><span data-stu-id="d6ebd-163">Shows what would happen if `Unregister-PackageSource` cmdlet is run.</span></span> <span data-ttu-id="d6ebd-164">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="d6ebd-164">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="d6ebd-165">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d6ebd-165">CommonParameters</span></span>

<span data-ttu-id="d6ebd-166">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d6ebd-166">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d6ebd-167">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="d6ebd-167">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d6ebd-168">INDATA</span><span class="sxs-lookup"><span data-stu-id="d6ebd-168">INPUTS</span></span>

### <span data-ttu-id="d6ebd-169">`Unregister-PackageSource` accepterar **PackageSource** -objekt från pipelinen som inmatade.</span><span class="sxs-lookup"><span data-stu-id="d6ebd-169">`Unregister-PackageSource` accepts **PackageSource** objects from the pipeline as input.</span></span>

## <span data-ttu-id="d6ebd-170">UTDATA</span><span class="sxs-lookup"><span data-stu-id="d6ebd-170">OUTPUTS</span></span>

### <span data-ttu-id="d6ebd-171">`Unregister-PackageSource` genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="d6ebd-171">`Unregister-PackageSource` doesn't generate any output.</span></span>

## <span data-ttu-id="d6ebd-172">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="d6ebd-172">NOTES</span></span>

<span data-ttu-id="d6ebd-173">Att inkludera en paket leverantör i ett kommando kan göra dynamiska parametrar tillgängliga för en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d6ebd-173">Including a package provider in a command can make dynamic parameters available to a cmdlet.</span></span> <span data-ttu-id="d6ebd-174">Dynamiska parametrar är speciella för en paket leverantör.</span><span class="sxs-lookup"><span data-stu-id="d6ebd-174">Dynamic parameters are specific to a package provider.</span></span> <span data-ttu-id="d6ebd-175">`Get-Help`Cmdleten listar en cmdlets parameter uppsättningar och inkluderar providerns parameter uppsättning.</span><span class="sxs-lookup"><span data-stu-id="d6ebd-175">The `Get-Help` cmdlet lists a cmdlet's parameter sets and includes the provider's parameter set.</span></span>

## <span data-ttu-id="d6ebd-176">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="d6ebd-176">RELATED LINKS</span></span>

[<span data-ttu-id="d6ebd-177">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="d6ebd-177">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="d6ebd-178">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="d6ebd-178">Get-Credential</span></span>](../Microsoft.PowerShell.Security/Get-Credential.md)

[<span data-ttu-id="d6ebd-179">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="d6ebd-179">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="d6ebd-180">Registrera – PackageSource</span><span class="sxs-lookup"><span data-stu-id="d6ebd-180">Register-PackageSource</span></span>](Register-PackageSource.md)

[<span data-ttu-id="d6ebd-181">Set-PackageSource</span><span class="sxs-lookup"><span data-stu-id="d6ebd-181">Set-PackageSource</span></span>](Set-PackageSource.md)

