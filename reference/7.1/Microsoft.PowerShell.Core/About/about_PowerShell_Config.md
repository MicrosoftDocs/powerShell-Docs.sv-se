---
description: Konfigurationsfiler för PowerShell Core, och ersätter register konfiguration.
keywords: powershell
Locale: en-US
ms.date: 11/02/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_powershell_config?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PowerShell_Config
ms.openlocfilehash: fd4467845cf2b895401a55cbb7abd88b7b72af76
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93271035"
---
# <a name="about-powershell-config"></a><span data-ttu-id="f9cb5-104">Om PowerShell-konfiguration</span><span class="sxs-lookup"><span data-stu-id="f9cb5-104">About PowerShell Config</span></span>

## <a name="short-description"></a><span data-ttu-id="f9cb5-105">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="f9cb5-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="f9cb5-106">Konfigurationsfiler för PowerShell Core, och ersätter register konfiguration.</span><span class="sxs-lookup"><span data-stu-id="f9cb5-106">Configuration files for PowerShell Core, replacing Registry configuration.</span></span>

## <a name="long-description"></a><span data-ttu-id="f9cb5-107">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="f9cb5-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="f9cb5-108">`powershell.config.json`Filen innehåller konfigurations inställningar för PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="f9cb5-108">The `powershell.config.json` file contains configuration settings for PowerShell Core.</span></span> <span data-ttu-id="f9cb5-109">PowerShell läser in den här konfigurationen vid start.</span><span class="sxs-lookup"><span data-stu-id="f9cb5-109">PowerShell loads this configuration at startup.</span></span> <span data-ttu-id="f9cb5-110">Inställningarna kan också ändras vid körning.</span><span class="sxs-lookup"><span data-stu-id="f9cb5-110">The settings can also be modified at runtime.</span></span> <span data-ttu-id="f9cb5-111">Tidigare lagrades dessa inställningar i Windows-registret för PowerShell, men ingår nu i en fil för att aktivera konfiguration på macOS och Linux.</span><span class="sxs-lookup"><span data-stu-id="f9cb5-111">Previously, these settings were stored in the Windows Registry for PowerShell, but are now contained in a file to enable configuration on macOS and Linux.</span></span>

> [!WARNING]
> <span data-ttu-id="f9cb5-112">Om `powershell.config.json` filen innehåller ogiltig JSON PowerShell kan inte starta en interaktiv session.</span><span class="sxs-lookup"><span data-stu-id="f9cb5-112">If the `powershell.config.json` file contains invalid JSON PowerShell cannot start an interactive session.</span></span>
> <span data-ttu-id="f9cb5-113">Om detta inträffar måste du åtgärda konfigurations filen.</span><span class="sxs-lookup"><span data-stu-id="f9cb5-113">If this occurs, you must fix the configuration file.</span></span>

> [!NOTE]
> <span data-ttu-id="f9cb5-114">Okända nycklar eller ogiltiga värden i konfigurations filen ignoreras tyst.</span><span class="sxs-lookup"><span data-stu-id="f9cb5-114">Unrecognized keys or invalid values in the configuration file will be silently ignored.</span></span>

### <a name="allusers-shared-configuration"></a><span data-ttu-id="f9cb5-115">AllUsers (delad) konfiguration</span><span class="sxs-lookup"><span data-stu-id="f9cb5-115">AllUsers (shared) configuration</span></span>

<span data-ttu-id="f9cb5-116">En `powershell.config.json` fil i `$PSHOME` katalogen definierar konfigurationen för alla PowerShell-sessioner som körs från den PowerShell Core-installationen.</span><span class="sxs-lookup"><span data-stu-id="f9cb5-116">A `powershell.config.json` file in the `$PSHOME` directory defines the configuration for all PowerShell Core sessions running from that PowerShell Core installation.</span></span>

> [!NOTE]
> <span data-ttu-id="f9cb5-117">`$PSHOME`Platsen definieras som samma katalog som den System.Management.Automation.dll sammansättningen körs på.</span><span class="sxs-lookup"><span data-stu-id="f9cb5-117">The `$PSHOME` location is defined as the same directory as the executing System.Management.Automation.dll assembly.</span></span> <span data-ttu-id="f9cb5-118">Detta gäller även för värdbaserade PowerShell SDK-instanser.</span><span class="sxs-lookup"><span data-stu-id="f9cb5-118">This applies to hosted PowerShell SDK instances as well.</span></span>

### <a name="currentuser-per-user-configurations"></a><span data-ttu-id="f9cb5-119">CurrentUser-konfigurationer (per användare)</span><span class="sxs-lookup"><span data-stu-id="f9cb5-119">CurrentUser (per-user) configurations</span></span>

<span data-ttu-id="f9cb5-120">Du kan också konfigurera PowerShell per användare genom att placera filen i konfigurations katalogen för användar området.</span><span class="sxs-lookup"><span data-stu-id="f9cb5-120">You can also configure PowerShell on a per-user basis by placing the file in the user-scope configuration directory.</span></span> <span data-ttu-id="f9cb5-121">Du hittar användar konfigurations katalogen på olika plattformar med kommandot `Split-Path $PROFILE.CurrentUserCurrentHost` .</span><span class="sxs-lookup"><span data-stu-id="f9cb5-121">The user configuration directory can be found across platforms with the command `Split-Path $PROFILE.CurrentUserCurrentHost`.</span></span>

## <a name="general-configuration-settings"></a><span data-ttu-id="f9cb5-122">Allmänna konfigurationsinställningar</span><span class="sxs-lookup"><span data-stu-id="f9cb5-122">General configuration settings</span></span>

### <a name="executionpolicy"></a><span data-ttu-id="f9cb5-123">ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="f9cb5-123">ExecutionPolicy</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f9cb5-124">Den här konfigurationen gäller endast för Windows-plattformar.</span><span class="sxs-lookup"><span data-stu-id="f9cb5-124">This configuration only applies on Windows platforms.</span></span>

<span data-ttu-id="f9cb5-125">Konfigurerar körnings principen för PowerShell-sessioner och avgör vilka skript som kan köras.</span><span class="sxs-lookup"><span data-stu-id="f9cb5-125">Configures the execution policy for PowerShell sessions, determining what scripts can be run.</span></span> <span data-ttu-id="f9cb5-126">Som standard använder PowerShell den befintliga körnings principen.</span><span class="sxs-lookup"><span data-stu-id="f9cb5-126">By default, PowerShell uses the existing execution policy.</span></span>

<span data-ttu-id="f9cb5-127">För AllUsers-konfigurationer ställer detta in principen för **LocalMachine** -körning.</span><span class="sxs-lookup"><span data-stu-id="f9cb5-127">For AllUsers configurations, this sets the **LocalMachine** execution policy.</span></span>
<span data-ttu-id="f9cb5-128">För CurrentUser-konfigurationer ställer detta in principen för **CurrentUser** -körning.</span><span class="sxs-lookup"><span data-stu-id="f9cb5-128">For CurrentUser configurations, this sets the **CurrentUser** execution policy.</span></span>

> [!NOTE]
> <span data-ttu-id="f9cb5-129">[`Set-ExecutionPolicy`](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)Cmdleten ändrar den här inställningen i konfigurations filen för allusers när den anropas med `-Scope LocalMachine` , och ändrar den här inställningen i CurrentUser-konfigurationsfilen när den anropas med `-Scope CurrentUser` .</span><span class="sxs-lookup"><span data-stu-id="f9cb5-129">The [`Set-ExecutionPolicy`](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy) cmdlet modifies this setting in the AllUsers configuration file when invoked with `-Scope LocalMachine`, and modifies this setting in the CurrentUser configuration file when invoked with `-Scope CurrentUser`.</span></span>

```Schema
"<shell-id>:ExecutionPolicy": "<execution-policy>"
```

<span data-ttu-id="f9cb5-130">Där:</span><span class="sxs-lookup"><span data-stu-id="f9cb5-130">Where:</span></span>

- <span data-ttu-id="f9cb5-131">`<shell-id>` refererar till ID: t för den aktuella PowerShell-värden.</span><span class="sxs-lookup"><span data-stu-id="f9cb5-131">`<shell-id>` refers to the ID of the current PowerShell host.</span></span>
  <span data-ttu-id="f9cb5-132">För normal PowerShell-kärna är detta `Microsoft.PowerShell` .</span><span class="sxs-lookup"><span data-stu-id="f9cb5-132">For normal PowerShell Core, this is `Microsoft.PowerShell`.</span></span>
  <span data-ttu-id="f9cb5-133">I en PowerShell-session kan du identifiera den med `$ShellId` .</span><span class="sxs-lookup"><span data-stu-id="f9cb5-133">In any PowerShell session, you can discover it with `$ShellId`.</span></span>
- <span data-ttu-id="f9cb5-134">`<execution-policy>` refererar till ett giltigt körnings princip namn.</span><span class="sxs-lookup"><span data-stu-id="f9cb5-134">`<execution-policy>` refers to a valid execution policy name.</span></span>

<span data-ttu-id="f9cb5-135">I följande exempel anges körnings principen för PowerShell till `RemoteSigned` .</span><span class="sxs-lookup"><span data-stu-id="f9cb5-135">The following example sets the execution policy of PowerShell to `RemoteSigned`.</span></span>

```json
{
  "Microsoft.PowerShell.ExecutionPolicy": "RemoteSigned"
}
```

<span data-ttu-id="f9cb5-136">I Windows kan du hitta motsvarande register nycklar `\SOFTWARE\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell` under `HKEY_LOCAL_MACHINE` och i `HKEY_CURRENT_USER` .</span><span class="sxs-lookup"><span data-stu-id="f9cb5-136">In Windows, the equivalent registry keys can be found in `\SOFTWARE\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell` under `HKEY_LOCAL_MACHINE` and `HKEY_CURRENT_USER`.</span></span>

### <a name="psmodulepath"></a><span data-ttu-id="f9cb5-137">PSModulePath</span><span class="sxs-lookup"><span data-stu-id="f9cb5-137">PSModulePath</span></span>

<span data-ttu-id="f9cb5-138">Åsidosätter en PSModulePath-komponent för den här PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="f9cb5-138">Overrides a PSModulePath component for this PowerShell session.</span></span> <span data-ttu-id="f9cb5-139">Om konfigurationen gäller för den aktuella användaren anger du sökvägen till CurrentUser-modulen.</span><span class="sxs-lookup"><span data-stu-id="f9cb5-139">If the configuration is for the current user, sets the CurrentUser module path.</span></span> <span data-ttu-id="f9cb5-140">Om konfigurationen är för alla användare anger sökvägen till AllUser-modulen.</span><span class="sxs-lookup"><span data-stu-id="f9cb5-140">If the configuration is for all users, sets the AllUser module path.</span></span>

> [!WARNING]
> <span data-ttu-id="f9cb5-141">Om du konfigurerar en sökväg för en AllUsers-eller CurrentUser-modul så ändras inte den omfångs installations platsen för PowerShellGet-moduler som [install-module](/powershell/module/powershellget/install-module).</span><span class="sxs-lookup"><span data-stu-id="f9cb5-141">Configuring an AllUsers or CurrentUser module path here will not change the scoped installation location for PowerShellGet modules like [Install-Module](/powershell/module/powershellget/install-module).</span></span>
> <span data-ttu-id="f9cb5-142">Dessa cmdletar använder alltid *standard* Sök vägarna.</span><span class="sxs-lookup"><span data-stu-id="f9cb5-142">These cmdlets always use the *default* module paths.</span></span>

<span data-ttu-id="f9cb5-143">Om inget värde anges används standardvärdet för respektive modul Sök vägs komponent.</span><span class="sxs-lookup"><span data-stu-id="f9cb5-143">If no value is set, the default value for the respective module path component will be used.</span></span> <span data-ttu-id="f9cb5-144">Se [about_Modules](./about_Modules.md#module-and-dsc-resource-locations-and-psmodulepath) för mer information om dessa standardvärden.</span><span class="sxs-lookup"><span data-stu-id="f9cb5-144">See [about_Modules](./about_Modules.md#module-and-dsc-resource-locations-and-psmodulepath) for more details on these defaults.</span></span>

<span data-ttu-id="f9cb5-145">Den här inställningen gör att miljövariabler kan användas genom att bädda in dem mellan `%` tecken, t `"%HOME%\Documents\PowerShell\Modules"` . ex. på samma sätt som cmd tillåter.</span><span class="sxs-lookup"><span data-stu-id="f9cb5-145">This setting allows environment variables to be used by embedding them between `%` characters, like `"%HOME%\Documents\PowerShell\Modules"`, in the same way as CMD allows.</span></span> <span data-ttu-id="f9cb5-146">Den här syntaxen gäller även för Linux och macOS.</span><span class="sxs-lookup"><span data-stu-id="f9cb5-146">This syntax also applies on Linux and macOS.</span></span> <span data-ttu-id="f9cb5-147">Se nedan för exempel.</span><span class="sxs-lookup"><span data-stu-id="f9cb5-147">See below for examples.</span></span>

```Schema
"PSModulePath": "<ps-module-path>"
```

<span data-ttu-id="f9cb5-148">Där:</span><span class="sxs-lookup"><span data-stu-id="f9cb5-148">Where:</span></span>

- <span data-ttu-id="f9cb5-149">`<ps-module-path>` är den absoluta sökvägen till en modul-katalog.</span><span class="sxs-lookup"><span data-stu-id="f9cb5-149">`<ps-module-path>` is the absolute path to a module directory.</span></span> <span data-ttu-id="f9cb5-150">För alla användarkonfigurationer är detta den AllUsers delade modul katalogen.</span><span class="sxs-lookup"><span data-stu-id="f9cb5-150">For all user configurations, this is the AllUsers shared module directory.</span></span> <span data-ttu-id="f9cb5-151">För aktuella användarkonfigurationer är detta CurrentUser-modulens katalog.</span><span class="sxs-lookup"><span data-stu-id="f9cb5-151">For current user configurations, this is CurrentUser module directory.</span></span>

<span data-ttu-id="f9cb5-152">I det här exemplet visas en PSModulePath-konfiguration för en Windows-miljö:</span><span class="sxs-lookup"><span data-stu-id="f9cb5-152">This example shows a PSModulePath configuration for a Windows environment:</span></span>

```json
{
  "PSModulePath": "C:\\Program Files\\PowerShell\\6\\Modules"
}
```

<span data-ttu-id="f9cb5-153">I det här exemplet visas en PSModulePath-konfiguration för en macOS-eller Linux-miljö:</span><span class="sxs-lookup"><span data-stu-id="f9cb5-153">This example shows a PSModulePath configuration for a macOS or Linux environment:</span></span>

```json
{
  "PSModulePath": "/opt/powershell/6/Modules"
}
```

<span data-ttu-id="f9cb5-154">I det här exemplet visas hur du bäddar in en miljö variabel i en PSModulePath-konfiguration.</span><span class="sxs-lookup"><span data-stu-id="f9cb5-154">This example shows embedding an environment variable in a PSModulePath configuration.</span></span> <span data-ttu-id="f9cb5-155">Observera att om du använder `HOME` miljövariabeln och `/` katalog avgränsaren fungerar detta på Windows, MacOS och Linux.</span><span class="sxs-lookup"><span data-stu-id="f9cb5-155">Note that using the `HOME` environment variable and the `/` directory separator, this will work on Windows, macOS and Linux.</span></span>

```json
{
  "PSModulePath": "%HOME%/Documents/PowerShell/Modules"
}
```

<span data-ttu-id="f9cb5-156">I det här exemplet visas hur du bäddar in en miljö variabel i en PSModulePath-konfiguration som bara fungerar på macOS och Linux:</span><span class="sxs-lookup"><span data-stu-id="f9cb5-156">This example shows embedding an environment variable in a PSModulePath configuration that will only work on macOS and Linux:</span></span>

```json
{
  "PSModulePath": "%XDG_CONFIG_HOME%/powershell/Modules"
}
```

> [!NOTE]
> <span data-ttu-id="f9cb5-157">PowerShell-variabler kan inte bäddas in i PSModulePath-konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="f9cb5-157">PowerShell variables cannot be embedded in PSModulePath configurations.</span></span>
> <span data-ttu-id="f9cb5-158">PSModulePath-konfigurationer på Linux och macOS är Skift läges känsliga.</span><span class="sxs-lookup"><span data-stu-id="f9cb5-158">PSModulePath configurations on Linux and macOS are case-sensitive.</span></span> <span data-ttu-id="f9cb5-159">En PSModulePath-konfiguration måste använda giltiga katalog avgränsare för plattformen.</span><span class="sxs-lookup"><span data-stu-id="f9cb5-159">A PSModulePath configuration must use valid directory separators for the platform.</span></span> <span data-ttu-id="f9cb5-160">På macOS och Linux innebär det här `/` .</span><span class="sxs-lookup"><span data-stu-id="f9cb5-160">On macOS and Linux, this means `/`.</span></span> <span data-ttu-id="f9cb5-161">I Windows fungerar både `/` och `\` .</span><span class="sxs-lookup"><span data-stu-id="f9cb5-161">On Windows, both `/` and `\` will work.</span></span>

### <a name="experimentalfeatures"></a><span data-ttu-id="f9cb5-162">ExperimentalFeatures</span><span class="sxs-lookup"><span data-stu-id="f9cb5-162">ExperimentalFeatures</span></span>

<span data-ttu-id="f9cb5-163">Namnen på de experimentella funktioner som ska aktive ras i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f9cb5-163">The names of the experimental features to enable in PowerShell.</span></span>
<span data-ttu-id="f9cb5-164">Som standard är inga experimentella funktioner aktiverade.</span><span class="sxs-lookup"><span data-stu-id="f9cb5-164">By default, no experimental features are enabled.</span></span>
<span data-ttu-id="f9cb5-165">Standardvärdet är en tom matris.</span><span class="sxs-lookup"><span data-stu-id="f9cb5-165">The default value is an empty array.</span></span>

```Schema
"ExperimentalFeatures": ["<experimental-feature-name>", ...]
```

<span data-ttu-id="f9cb5-166">Där:</span><span class="sxs-lookup"><span data-stu-id="f9cb5-166">Where:</span></span>

- <span data-ttu-id="f9cb5-167">`<experimental-feature-name>` är namnet på en experimentell funktion som ska aktive ras.</span><span class="sxs-lookup"><span data-stu-id="f9cb5-167">`<experimental-feature-name>` is the name of an experimental feature to enable.</span></span>

<span data-ttu-id="f9cb5-168">I följande exempel aktive ras **PSImplicitRemoting** -och **PSUseAbbreviationExpansion** -experimentella funktioner när PowerShell startas.</span><span class="sxs-lookup"><span data-stu-id="f9cb5-168">The following example enables the **PSImplicitRemoting** and **PSUseAbbreviationExpansion** experimental features when PowerShell starts up.</span></span>

```json
{
  "ExperimentalFeatures": [
    "PSImplicitRemotingBatching",
    "PSUseAbbreviationExpansion"
  ]
}
```

<span data-ttu-id="f9cb5-169">Mer information om experimentella funktioner finns i [POWERSHELL RFC 29][RFC0029].</span><span class="sxs-lookup"><span data-stu-id="f9cb5-169">For more information on experimental features, see [PowerShell RFC 29][RFC0029].</span></span>

## <a name="non-windows-logging-configuration"></a><span data-ttu-id="f9cb5-170">Konfiguration för icke-Windows-loggning</span><span class="sxs-lookup"><span data-stu-id="f9cb5-170">Non-Windows logging configuration</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f9cb5-171">Konfigurations alternativen i det här avsnittet gäller endast macOS och Linux.</span><span class="sxs-lookup"><span data-stu-id="f9cb5-171">The configuration options in this section only apply to macOS and Linux.</span></span>
> <span data-ttu-id="f9cb5-172">Loggning för Windows hanteras av Windows-Loggboken.</span><span class="sxs-lookup"><span data-stu-id="f9cb5-172">Logging for Windows is managed by the Windows Event Viewer.</span></span>

<span data-ttu-id="f9cb5-173">PowerShell-loggning på macOS och Linux kan konfigureras i PowerShell-konfigurationsfilen.</span><span class="sxs-lookup"><span data-stu-id="f9cb5-173">PowerShell's logging on macOS and Linux can be configured in the PowerShell configuration file.</span></span> <span data-ttu-id="f9cb5-174">En fullständig beskrivning av PowerShell-loggning för icke-Windows-system finns i [om loggning](./about_Logging_Non-Windows.md).</span><span class="sxs-lookup"><span data-stu-id="f9cb5-174">For a full description of PowerShell logging for non-Windows systems, see [About Logging](./about_Logging_Non-Windows.md).</span></span>

### <a name="logidentity"></a><span data-ttu-id="f9cb5-175">LogIdentity</span><span class="sxs-lookup"><span data-stu-id="f9cb5-175">LogIdentity</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f9cb5-176">Den här inställningen kan endast användas i macOS och Linux.</span><span class="sxs-lookup"><span data-stu-id="f9cb5-176">This setting can only be used in macOS and Linux.</span></span>

<span data-ttu-id="f9cb5-177">Anger det identitets namn som används för att skriva till system loggen.</span><span class="sxs-lookup"><span data-stu-id="f9cb5-177">Sets the identity name used to write to the system log.</span></span> <span data-ttu-id="f9cb5-178">Standardvärdet är "PowerShell".</span><span class="sxs-lookup"><span data-stu-id="f9cb5-178">The default value is "powershell".</span></span>

```Schema
"LogIdentity": "<log-identity>"
```

<span data-ttu-id="f9cb5-179">Där:</span><span class="sxs-lookup"><span data-stu-id="f9cb5-179">Where:</span></span>

- <span data-ttu-id="f9cb5-180">`<log-identity>` är sträng identiteten som PowerShell ska använda för att skriva till syslog.</span><span class="sxs-lookup"><span data-stu-id="f9cb5-180">`<log-identity>` is the string identity that PowerShell should use for writing to syslog.</span></span>

> [!NOTE]
> <span data-ttu-id="f9cb5-181">Du kanske vill ha olika **LogIdentity** -värden för varje instans av PowerShell som du har installerat.</span><span class="sxs-lookup"><span data-stu-id="f9cb5-181">You may want to have different **LogIdentity** values for each different instance of PowerShell you have installed.</span></span>

<span data-ttu-id="f9cb5-182">I det här exemplet konfigurerar vi **LogIdentity** för en för hands version av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f9cb5-182">In this example, we are configuring the **LogIdentity** for a preview release of PowerShell.</span></span>

```json
{
  "LogIdentity": "powershell-preview"
}
```

### <a name="loglevel"></a><span data-ttu-id="f9cb5-183">Loggnivå</span><span class="sxs-lookup"><span data-stu-id="f9cb5-183">LogLevel</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f9cb5-184">Den här inställningen kan endast användas i macOS och Linux.</span><span class="sxs-lookup"><span data-stu-id="f9cb5-184">This setting can only be used in macOS and Linux.</span></span>

<span data-ttu-id="f9cb5-185">Anger den lägsta allvarlighets grad som PowerShell ska logga.</span><span class="sxs-lookup"><span data-stu-id="f9cb5-185">Specifies the minimum severity level at which PowerShell should log.</span></span>

```Schema
"LogLevel": "<log-level>|default"
```

<span data-ttu-id="f9cb5-186">Där:</span><span class="sxs-lookup"><span data-stu-id="f9cb5-186">Where:</span></span>

- <span data-ttu-id="f9cb5-187">`<log-level>` är en av:</span><span class="sxs-lookup"><span data-stu-id="f9cb5-187">`<log-level>` is one of:</span></span>
  - <span data-ttu-id="f9cb5-188">Always</span><span class="sxs-lookup"><span data-stu-id="f9cb5-188">Always</span></span>
  - <span data-ttu-id="f9cb5-189">Kritiskt</span><span class="sxs-lookup"><span data-stu-id="f9cb5-189">Critical</span></span>
  - <span data-ttu-id="f9cb5-190">Fel</span><span class="sxs-lookup"><span data-stu-id="f9cb5-190">Error</span></span>
  - <span data-ttu-id="f9cb5-191">Varning</span><span class="sxs-lookup"><span data-stu-id="f9cb5-191">Warning</span></span>
  - <span data-ttu-id="f9cb5-192">Information</span><span class="sxs-lookup"><span data-stu-id="f9cb5-192">Informational</span></span>
  - <span data-ttu-id="f9cb5-193">Verbose</span><span class="sxs-lookup"><span data-stu-id="f9cb5-193">Verbose</span></span>
  - <span data-ttu-id="f9cb5-194">Felsökning</span><span class="sxs-lookup"><span data-stu-id="f9cb5-194">Debug</span></span>

> [!NOTE]
> <span data-ttu-id="f9cb5-195">Om du anger en loggnings nivå aktive ras alla logg nivåer ovanför.</span><span class="sxs-lookup"><span data-stu-id="f9cb5-195">Setting a the log level enables all log levels above it.</span></span>

<span data-ttu-id="f9cb5-196">Om du ställer in den här inställningen som **standard** tolkas det som standardvärdet.</span><span class="sxs-lookup"><span data-stu-id="f9cb5-196">Setting this setting to **default** will be interpreted as the default value.</span></span>
<span data-ttu-id="f9cb5-197">Standardvärdet är **information**.</span><span class="sxs-lookup"><span data-stu-id="f9cb5-197">The default value is **Informational**.</span></span>

<span data-ttu-id="f9cb5-198">I följande exempel anges värdet till **verbose**.</span><span class="sxs-lookup"><span data-stu-id="f9cb5-198">The following example sets the value to **Verbose**.</span></span>

```json
{
  "LogLevel": "Verbose"
}
```

### <a name="logchannels"></a><span data-ttu-id="f9cb5-199">LogChannels</span><span class="sxs-lookup"><span data-stu-id="f9cb5-199">LogChannels</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f9cb5-200">Den här inställningen kan endast användas i macOS och Linux.</span><span class="sxs-lookup"><span data-stu-id="f9cb5-200">This setting can only be used in macOS and Linux.</span></span>

<span data-ttu-id="f9cb5-201">Bestämmer vilka loggnings kanaler som är aktiverade.</span><span class="sxs-lookup"><span data-stu-id="f9cb5-201">Determines which logging channels are enabled.</span></span>

```Schema
"LogChannels": "<log-channel>,..."
```

<span data-ttu-id="f9cb5-202">Där:</span><span class="sxs-lookup"><span data-stu-id="f9cb5-202">Where:</span></span>

- <span data-ttu-id="f9cb5-203">`<log-channel>` är en av:</span><span class="sxs-lookup"><span data-stu-id="f9cb5-203">`<log-channel>` is one of:</span></span>
  - <span data-ttu-id="f9cb5-204">Drift – loggar grundläggande information om PowerShell-aktiviteter</span><span class="sxs-lookup"><span data-stu-id="f9cb5-204">Operational - logs basic information about PowerShell activities</span></span>
  - <span data-ttu-id="f9cb5-205">Analytiskt loggar mer detaljerad diagnostikinformation</span><span class="sxs-lookup"><span data-stu-id="f9cb5-205">Analytic - logs more detailed diagnostic information</span></span>

<span data-ttu-id="f9cb5-206">Standardvärdet är **drift**.</span><span class="sxs-lookup"><span data-stu-id="f9cb5-206">The default value is **Operational**.</span></span> <span data-ttu-id="f9cb5-207">Om du vill aktivera båda kanalerna inkluderar du båda värdena som en kommaavgränsad sträng.</span><span class="sxs-lookup"><span data-stu-id="f9cb5-207">To enable both channels, include both values as a single comma-separated string.</span></span> <span data-ttu-id="f9cb5-208">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="f9cb5-208">For example:</span></span>

```json
{
  "LogChannels": "Operational,Analytic"
}
```

### <a name="logkeywords"></a><span data-ttu-id="f9cb5-209">LogKeywords</span><span class="sxs-lookup"><span data-stu-id="f9cb5-209">LogKeywords</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f9cb5-210">Den här inställningen kan endast användas i macOS och Linux.</span><span class="sxs-lookup"><span data-stu-id="f9cb5-210">This setting can only be used in macOS and Linux.</span></span>

<span data-ttu-id="f9cb5-211">Anger vilka delar av PowerShell som loggas.</span><span class="sxs-lookup"><span data-stu-id="f9cb5-211">Determines which parts of PowerShell are logged.</span></span> <span data-ttu-id="f9cb5-212">Som standard är alla logg nyckelord aktiverade.</span><span class="sxs-lookup"><span data-stu-id="f9cb5-212">By default, all log keywords are enabled.</span></span> <span data-ttu-id="f9cb5-213">Om du vill aktivera flera nyckelord anger du värdena i en enda kommaavgränsad sträng.</span><span class="sxs-lookup"><span data-stu-id="f9cb5-213">To enable multiple keywords, list the values in a single comma-separated string.</span></span>

```Schema
"LogKeywords": "<log-keyword>,..."
```

<span data-ttu-id="f9cb5-214">Där:</span><span class="sxs-lookup"><span data-stu-id="f9cb5-214">Where:</span></span>

- <span data-ttu-id="f9cb5-215">`<log-keyword>` är en av:</span><span class="sxs-lookup"><span data-stu-id="f9cb5-215">`<log-keyword>` is one of:</span></span>
  - <span data-ttu-id="f9cb5-216">Hantering av körnings utrymme-körnings utrymme</span><span class="sxs-lookup"><span data-stu-id="f9cb5-216">Runspace - runspace management</span></span>
  - <span data-ttu-id="f9cb5-217">Pipeline – pipeline-åtgärder</span><span class="sxs-lookup"><span data-stu-id="f9cb5-217">Pipeline - pipeline operations</span></span>
  - <span data-ttu-id="f9cb5-218">Protokoll hantering av protokoll, till exempel PSRP</span><span class="sxs-lookup"><span data-stu-id="f9cb5-218">Protocol - communication protocol handling, such as PSRP</span></span>
  - <span data-ttu-id="f9cb5-219">Stöd för transport transport skikt, till exempel SSH</span><span class="sxs-lookup"><span data-stu-id="f9cb5-219">Transport - transport layer support, such as SSH</span></span>
  - <span data-ttu-id="f9cb5-220">Värd-PowerShell-värd funktioner, till exempel konsol interaktion</span><span class="sxs-lookup"><span data-stu-id="f9cb5-220">Host - PowerShell host functionality, for example console interaction</span></span>
  - <span data-ttu-id="f9cb5-221">Cmdlets – PowerShell Built-cmdlet: ar</span><span class="sxs-lookup"><span data-stu-id="f9cb5-221">Cmdlets -PowerShell builtin cmdlets</span></span>
  - <span data-ttu-id="f9cb5-222">Serialiserare – serialiserings logik</span><span class="sxs-lookup"><span data-stu-id="f9cb5-222">Serializer - serialization logic</span></span>
  - <span data-ttu-id="f9cb5-223">Session – PowerShell-sessionstillstånd</span><span class="sxs-lookup"><span data-stu-id="f9cb5-223">Session - PowerShell session state</span></span>
  - <span data-ttu-id="f9cb5-224">ManagedPlugin – WSMan-plugin</span><span class="sxs-lookup"><span data-stu-id="f9cb5-224">ManagedPlugin - WSMan plugin</span></span>

> [!NOTE]
> <span data-ttu-id="f9cb5-225">Det rekommenderas vanligt vis att lämna det här värdet unset om du inte försöker diagnostisera ett visst beteende i en känd del av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f9cb5-225">It is generally advised to leave this value unset unless you are trying to diagnose a specific behavior in a known part of PowerShell.</span></span>
> <span data-ttu-id="f9cb5-226">Om du ändrar det här värdet minskar bara mängden information som loggas.</span><span class="sxs-lookup"><span data-stu-id="f9cb5-226">Changing this value only decreases the amount of information logged.</span></span>

<span data-ttu-id="f9cb5-227">Det här exemplet begränsar loggningen till körnings utrymme-åtgärder, pipeline-logik och cmdlet-användning.</span><span class="sxs-lookup"><span data-stu-id="f9cb5-227">This example limits the logging to runspace operations, pipeline logic, and cmdlet use.</span></span> <span data-ttu-id="f9cb5-228">All annan loggning kommer att utelämnas.</span><span class="sxs-lookup"><span data-stu-id="f9cb5-228">All other logging will be omitted.</span></span>

```json
"LogKeywords": "Runspace,Pipeline,Cmdlets"
```

<!--

## Group policy configuration

### ScriptExecution

### ScriptBlockLogging

### ProtectedEventLogging

### Transcription

### UpdateableHelp

### ConsoleSessionConfiguration

-->

## <a name="more-example-configurations"></a><span data-ttu-id="f9cb5-229">Fler exempel konfigurationer</span><span class="sxs-lookup"><span data-stu-id="f9cb5-229">More example configurations</span></span>

### <a name="example-windows-configuration"></a><span data-ttu-id="f9cb5-230">Exempel på Windows-konfiguration</span><span class="sxs-lookup"><span data-stu-id="f9cb5-230">Example Windows configuration</span></span>

<span data-ttu-id="f9cb5-231">Den här konfigurationen har flera inställningar som uttryckligen anges:</span><span class="sxs-lookup"><span data-stu-id="f9cb5-231">This configuration has more settings explicitly set:</span></span>

- <span data-ttu-id="f9cb5-232">Körnings principen för den här PowerShell-installationen är `AllSigned`</span><span class="sxs-lookup"><span data-stu-id="f9cb5-232">Execution policy for this PowerShell installation is `AllSigned`</span></span>
- <span data-ttu-id="f9cb5-233">Sökvägen till CurrentUser-modulen har angetts till en modul-katalog på en delad enhet</span><span class="sxs-lookup"><span data-stu-id="f9cb5-233">The CurrentUser module path is set to a module directory on a shared drive</span></span>
- <span data-ttu-id="f9cb5-234">`PSImplicitRemotingBatching`Experimentell funktion är aktive rad</span><span class="sxs-lookup"><span data-stu-id="f9cb5-234">The `PSImplicitRemotingBatching` experimental feature is enabled</span></span>

> [!NOTE]
> <span data-ttu-id="f9cb5-235">`ExecutionPolicy`Inställningarna och `PSModulePath` fungerar bara på en Windows-plattform eftersom modulens sökväg använder `\` och `;` avgränsnings tecken och körnings principen inte `Unrestricted` (den enda principen som tillåts på UNIX-liknande plattformar).</span><span class="sxs-lookup"><span data-stu-id="f9cb5-235">The `ExecutionPolicy` and `PSModulePath` settings here would only work on a Windows platform, since the module path uses `\` and `;` separator characters and the execution policy is not `Unrestricted` (the only policy allowed on UNIX-like platforms).</span></span>

```json
{
  "Microsoft.PowerShell.ExecutionPolicy": "AllSigned",
  "PSModulePath": "Z:\\Marisol's Shared Drive\\Modules",
  "ExperimentalFeatures": ["PSImplicitRemotingBatching"],
}
```

### <a name="example-non-windows-configuration"></a><span data-ttu-id="f9cb5-236">Exempel på konfiguration som inte är Windows</span><span class="sxs-lookup"><span data-stu-id="f9cb5-236">Example non-Windows configuration</span></span>

<span data-ttu-id="f9cb5-237">Den här konfigurationen anger ett antal alternativ som bara fungerar i macOS eller Linux:</span><span class="sxs-lookup"><span data-stu-id="f9cb5-237">This configuration sets a number of options that only work in macOS or Linux:</span></span>

- <span data-ttu-id="f9cb5-238">Sökvägen till CurrentUser-modulen har angetts till en anpassad modul-katalog i `$HOME`</span><span class="sxs-lookup"><span data-stu-id="f9cb5-238">The CurrentUser module path is set to a custom module directory in `$HOME`</span></span>
- <span data-ttu-id="f9cb5-239">Funktionen **PSImplicitRemotingBatching** experimentell är aktive rad</span><span class="sxs-lookup"><span data-stu-id="f9cb5-239">The **PSImplicitRemotingBatching** experimental feature is enabled</span></span>
- <span data-ttu-id="f9cb5-240">Loggnings nivån för PowerShell är inställd på **verbose** , för mer loggning</span><span class="sxs-lookup"><span data-stu-id="f9cb5-240">The PowerShell logging level is set to **Verbose** , for more logging</span></span>
- <span data-ttu-id="f9cb5-241">Den här PowerShell-installationen skriver till loggarna med hjälp av **Home-PowerShell-** identiteten.</span><span class="sxs-lookup"><span data-stu-id="f9cb5-241">This PowerShell installation writes to the logs using the **home-powershell** identity.</span></span>

```json
{
  "PSModulePath": "%HOME%/.powershell/Modules",
  "ExperimentalFeatures": ["PSImplicitRemotingBatching"],
  "LogLevel": "Verbose",
  "LogIdentity": "home-powershell"
}
```

## <a name="see-also"></a><span data-ttu-id="f9cb5-242">Se även</span><span class="sxs-lookup"><span data-stu-id="f9cb5-242">See also</span></span>

[<span data-ttu-id="f9cb5-243">Om körnings principer</span><span class="sxs-lookup"><span data-stu-id="f9cb5-243">About Execution Policies</span></span>](./about_Execution_Policies.md)

[<span data-ttu-id="f9cb5-244">Om automatiska variabler</span><span class="sxs-lookup"><span data-stu-id="f9cb5-244">About Automatic Variables</span></span>](./about_Automatic_Variables.md)

[RFC0029]: https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0029-Support-Experimental-Features.md

