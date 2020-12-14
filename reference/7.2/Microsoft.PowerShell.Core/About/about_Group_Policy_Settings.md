---
description: Beskriver grupprincip inställningarna för PowerShell
Locale: en-US
ms.date: 03/25/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_group_policy_settings?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Group_Policy_Settings
ms.openlocfilehash: 5ca13d22c69213dd8bae57a0dd08587c9c2b1541
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708519"
---
# <a name="about-group-policy-settings"></a><span data-ttu-id="4a4e7-103">Om grupprincip inställningar</span><span class="sxs-lookup"><span data-stu-id="4a4e7-103">About Group Policy Settings</span></span>

## <a name="short-description"></a><span data-ttu-id="4a4e7-104">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="4a4e7-104">Short description</span></span>
<span data-ttu-id="4a4e7-105">Beskriver grupprincip inställningarna för PowerShell</span><span class="sxs-lookup"><span data-stu-id="4a4e7-105">Describes the Group Policy settings for PowerShell</span></span>

## <a name="long-description"></a><span data-ttu-id="4a4e7-106">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="4a4e7-106">Long description</span></span>

<span data-ttu-id="4a4e7-107">PowerShell innehåller grupprincip inställningar som hjälper dig att definiera konsekventa konfigurations värden för Windows-datorer i en företags miljö.</span><span class="sxs-lookup"><span data-stu-id="4a4e7-107">PowerShell includes Group Policy settings to help you define consistent configuration values for Windows computers in an enterprise environment.</span></span>

<span data-ttu-id="4a4e7-108">Inställningarna för PowerShell-grupprincip finns i följande grupprincip sökvägar:</span><span class="sxs-lookup"><span data-stu-id="4a4e7-108">The PowerShell Group Policy settings are in the following Group Policy paths:</span></span>

```
Computer Configuration\
  Administrative Templates\
    PowerShell Core

User Configuration\
  Administrative Templates\
    PowerShell Core
```

<span data-ttu-id="4a4e7-109">Grup princip inställningar i användar konfigurations Sök vägen har företräde framför grupprincip inställningar i datorns konfigurations Sök väg.</span><span class="sxs-lookup"><span data-stu-id="4a4e7-109">Group policy settings in the User Configuration path take precedence over Group Policy settings in the Computer Configuration path.</span></span>

<span data-ttu-id="4a4e7-110">PowerShell 7 innehåller grupprincip mallar och ett installations skript i `$PSHOME` .</span><span class="sxs-lookup"><span data-stu-id="4a4e7-110">PowerShell 7 includes Group Policy templates and an installation script in `$PSHOME`.</span></span>

<span data-ttu-id="4a4e7-111">Grupprincip verktyg använder administrativa mallfiler ( `.admx` , `.adml` ) för att fylla i princip inställningar i användar gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="4a4e7-111">Group Policy tools use administrative template files (`.admx`, `.adml`) to populate policy settings in the user interface.</span></span> <span data-ttu-id="4a4e7-112">Detta gör det möjligt för administratörer att hantera registerbaserade princip inställningar.</span><span class="sxs-lookup"><span data-stu-id="4a4e7-112">This allows administrators to manage registry-based policy settings.</span></span> <span data-ttu-id="4a4e7-113">`InstallPSCorePolicyDefinitions.ps1`Skriptet installerar **PowerShell Core administrativa mallar** på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="4a4e7-113">The `InstallPSCorePolicyDefinitions.ps1` script installs **PowerShell Core Administrative Templates** on the local machine.</span></span>

```powershell
Get-ChildItem -Path $PSHOME -Filter *Core*Policy*
```

```Output
    Directory: C:\Program Files\PowerShell\7

Mode       LastWriteTime         Length Name
----       -------------         ------ ----
-a---      2/27/2020 12:38 AM     15861 InstallPSCorePolicyDefinitions.ps1
-a---      2/27/2020 12:28 AM      9675 PowerShellCoreExecutionPolicy.adml
-a---      2/27/2020 12:28 AM      6201 PowerShellCoreExecutionPolicy.admx
```

<span data-ttu-id="4a4e7-114">När du har installerat mallarna kan du redigera inställningarna i grupprincip-redigeraren ( `gpedit.msc` ).</span><span class="sxs-lookup"><span data-stu-id="4a4e7-114">After installing the templates, you can edit these settings in the Group Policy editor (`gpedit.msc`).</span></span>

<span data-ttu-id="4a4e7-115">Principerna är följande:</span><span class="sxs-lookup"><span data-stu-id="4a4e7-115">The policies are as follows:</span></span>

- <span data-ttu-id="4a4e7-116">Konfiguration av konsolsession: anger en konfigurations slut punkt där PowerShell körs.</span><span class="sxs-lookup"><span data-stu-id="4a4e7-116">Console session configuration: Sets a configuration endpoint in which PowerShell is run.</span></span>
- <span data-ttu-id="4a4e7-117">Aktivera modul loggning: anger **LogPipelineExecutionDetails** -egenskapen för moduler.</span><span class="sxs-lookup"><span data-stu-id="4a4e7-117">Turn on Module Logging: Sets the **LogPipelineExecutionDetails** property of modules.</span></span>
- <span data-ttu-id="4a4e7-118">Aktivera loggning av PowerShell-skript block: aktiverar detaljerad loggning av alla PowerShell-skript.</span><span class="sxs-lookup"><span data-stu-id="4a4e7-118">Turn on PowerShell Script Block Logging: Enables detailed logging of all PowerShell scripts.</span></span>
- <span data-ttu-id="4a4e7-119">Aktivera skript körning: ställer in PowerShell-körnings principen.</span><span class="sxs-lookup"><span data-stu-id="4a4e7-119">Turn on Script Execution: Sets the PowerShell execution policy.</span></span>
- <span data-ttu-id="4a4e7-120">Aktivera PowerShell-avskrift: aktiverar insamling av indata och utdata från PowerShell-kommandon i textbaserade avskrifter.</span><span class="sxs-lookup"><span data-stu-id="4a4e7-120">Turn on PowerShell Transcription: enables capturing of input and output of PowerShell commands into text-based transcripts.</span></span>
- <span data-ttu-id="4a4e7-121">Ange standard käll Sök väg för `Update-Help` : Anger källan för uppdaterbar hjälp till en katalog, inte Internet.</span><span class="sxs-lookup"><span data-stu-id="4a4e7-121">Set the default source path for `Update-Help`: Sets the source for Updatable Help to a directory, not the Internet.</span></span>

<span data-ttu-id="4a4e7-122">Varje PowerShell-grupprincip inställning har ett alternativ ("Använd Windows PowerShell princip inställnings fält") för att använda värdet från en liknande Windows PowerShell grupprincip-inställning som finns i följande grupprincip sökvägar:</span><span class="sxs-lookup"><span data-stu-id="4a4e7-122">Each PowerShell Group Policy setting has an option ('Use Windows PowerShell Policy setting' field) to use the value from a similar Windows PowerShell Group Policy setting that is located in the following Group Policy paths:</span></span>

```
Computer Configuration\
  Administrative Templates\
    Windows Components\
      Windows PowerShell

User Configuration\
  Administrative Templates\
    Windows Components\
      Windows PowerShell
```

> [!NOTE]
> <span data-ttu-id="4a4e7-123">Dessa **PowerShell-administrativa mallar** innehåller inte inställningar för Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4a4e7-123">These **PowerShell Core Administrative Templates** do not include settings for Windows PowerShell.</span></span> <span data-ttu-id="4a4e7-124">Mer information om hur du hämtar andra mallar och konfigurerar grup principer finns i [så här skapar och hanterar du den centrala butiken för grupprincip administrativa mallar i Windows][gpstore].</span><span class="sxs-lookup"><span data-stu-id="4a4e7-124">For more information about acquiring other templates and configuring Group policy, see [How to create and manage the Central Store for Group Policy Administrative Templates in Windows][gpstore].</span></span>

## <a name="console-session-configuration"></a><span data-ttu-id="4a4e7-125">Konfiguration av konsolsession</span><span class="sxs-lookup"><span data-stu-id="4a4e7-125">Console session configuration</span></span>

<span data-ttu-id="4a4e7-126">**Konfigurations** princip inställningen för konsolsessionen anger en konfigurations slut punkt där PowerShell körs.</span><span class="sxs-lookup"><span data-stu-id="4a4e7-126">The **Console session configuration** policy setting specifies a configuration endpoint in which PowerShell is run.</span></span> <span data-ttu-id="4a4e7-127">Detta kan vara vilken slut punkt som helst som är registrerad på den lokala datorn, inklusive standard slut punkter för PowerShell-fjärrkommunikation eller en anpassad slut punkt med vissa användar roll funktioner.</span><span class="sxs-lookup"><span data-stu-id="4a4e7-127">This can be any endpoint registered on the local machine including the default PowerShell remoting endpoints or a custom endpoint having specific user role capabilities.</span></span>

## <a name="turn-on-module-logging"></a><span data-ttu-id="4a4e7-128">Aktivera modul loggning</span><span class="sxs-lookup"><span data-stu-id="4a4e7-128">Turn on module logging</span></span>

<span data-ttu-id="4a4e7-129">Princip inställningen Aktivera loggning av **modul** aktiverar loggning för valda PowerShell-moduler.</span><span class="sxs-lookup"><span data-stu-id="4a4e7-129">The **Turn on Module Logging** policy setting turns on logging for selected PowerShell modules.</span></span> <span data-ttu-id="4a4e7-130">Inställningen gäller alla sessioner på alla berörda datorer.</span><span class="sxs-lookup"><span data-stu-id="4a4e7-130">The setting is effective in all sessions on all affected computers.</span></span>

<span data-ttu-id="4a4e7-131">Om du aktiverar den här policy inställningen och anger en eller flera moduler, registreras pipeline-körningar för de angivna modulerna i Windows PowerShell-loggen i Loggboken.</span><span class="sxs-lookup"><span data-stu-id="4a4e7-131">If you enable this policy setting and specify one or more modules, pipeline execution events for the specified modules are recorded in the Windows PowerShell log in Event Viewer.</span></span>

<span data-ttu-id="4a4e7-132">Om du inaktiverar den här inställningen inaktive ras loggning av körnings händelser för alla PowerShell-moduler.</span><span class="sxs-lookup"><span data-stu-id="4a4e7-132">If you disable this policy setting, logging of execution events is disabled for all PowerShell modules.</span></span>

<span data-ttu-id="4a4e7-133">Om den här inställningen inte konfigureras bestämmer egenskapen **LogPipelineExecutionDetails** för varje modul om körnings händelserna i en modul loggas.</span><span class="sxs-lookup"><span data-stu-id="4a4e7-133">If this policy setting is not configured, the **LogPipelineExecutionDetails** property of each module determines whether the execution events of a module are logged.</span></span> <span data-ttu-id="4a4e7-134">Som standard har egenskapen **LogPipelineExecutionDetails** för alla moduler angetts till false.</span><span class="sxs-lookup"><span data-stu-id="4a4e7-134">By default, the **LogPipelineExecutionDetails** property of all modules is set to False.</span></span>

<span data-ttu-id="4a4e7-135">Använd följande kommando format om du vill aktivera en moduls loggning för en modul.</span><span class="sxs-lookup"><span data-stu-id="4a4e7-135">To turn on module logging for a module, use the following command format.</span></span> <span data-ttu-id="4a4e7-136">Modulen måste importeras till sessionen och inställningen är endast effektiv i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="4a4e7-136">The module must be imported into the session and the setting is effective only in the current session.</span></span>

```powershell
Import-Module <Module-Name>
(Get-Module <Module-Name>).LogPipelineExecutionDetails = $true
```

<span data-ttu-id="4a4e7-137">Om du vill aktivera module-loggning för alla sessioner på en viss dator lägger du till föregående kommandon i PowerShell-profilen "alla användare" ( `$Profile.AllUsersAllHosts` ).</span><span class="sxs-lookup"><span data-stu-id="4a4e7-137">To turn on module logging for all sessions on a particular computer, add the previous commands to the 'All Users' PowerShell profile (`$Profile.AllUsersAllHosts`).</span></span>

<span data-ttu-id="4a4e7-138">Mer information om module-loggning finns [about_Modules](about_Modules.md).</span><span class="sxs-lookup"><span data-stu-id="4a4e7-138">For more information about module logging, see [about_Modules](about_Modules.md).</span></span>

## <a name="turn-on-powershell-script-block-logging"></a><span data-ttu-id="4a4e7-139">Aktivera loggning av PowerShell-skriptkommando</span><span class="sxs-lookup"><span data-stu-id="4a4e7-139">Turn on PowerShell script block logging</span></span>

<span data-ttu-id="4a4e7-140">Princip inställningen **Aktivera PowerShell-skript block loggning** aktiverar loggning av alla PowerShell-skriptfiler till händelse loggen Microsoft-Windows-PowerShell/Operational.</span><span class="sxs-lookup"><span data-stu-id="4a4e7-140">The **Turn on PowerShell Script Block Logging** policy setting enables logging of all PowerShell script input to the Microsoft-Windows-PowerShell/Operational event log.</span></span> <span data-ttu-id="4a4e7-141">Om du aktiverar den här policy inställningen loggar PowerShell Core bearbetningen av kommandon, skript block, funktioner och skript – oavsett om de anropas interaktivt eller via Automation.</span><span class="sxs-lookup"><span data-stu-id="4a4e7-141">If you enable this policy setting, PowerShell Core will log the processing of commands, script blocks, functions, and scripts - whether invoked interactively, or through automation.</span></span>

<span data-ttu-id="4a4e7-142">Om du inaktiverar den här principinställningen inaktiveras loggning av PowerShell-skriptindata.</span><span class="sxs-lookup"><span data-stu-id="4a4e7-142">If you disable this policy setting, logging of PowerShell script input is disabled.</span></span> <span data-ttu-id="4a4e7-143">Om du aktiverar loggning av indata av skriptblock loggar PowerShell även händelser om anrop av ett kommando, skriptblock, funktion eller skript startar eller stoppar.</span><span class="sxs-lookup"><span data-stu-id="4a4e7-143">If you enable the Script Block Invocation Logging, PowerShell additionally logs events when invocation of a command, script block, function, or script starts or stops.</span></span> <span data-ttu-id="4a4e7-144">Om du aktiverar loggning av anrop genereras ett stort antal händelseloggar.</span><span class="sxs-lookup"><span data-stu-id="4a4e7-144">Enabling Invocation Logging generates a high volume of event logs.</span></span>

## <a name="turn-on-script-execution"></a><span data-ttu-id="4a4e7-145">Aktivera skript körning</span><span class="sxs-lookup"><span data-stu-id="4a4e7-145">Turn on script execution</span></span>

<span data-ttu-id="4a4e7-146">Inställningen **Aktivera princip för skript körning** anger körnings principen för datorer och användare, vilket avgör vilka skript som tillåts köra.</span><span class="sxs-lookup"><span data-stu-id="4a4e7-146">The **Turn on Script Execution** policy setting sets the execution policy for computers and users, which determines which scripts are permitted to run.</span></span>

<span data-ttu-id="4a4e7-147">Om du aktiverar princip inställningen kan du välja bland följande princip inställningar.</span><span class="sxs-lookup"><span data-stu-id="4a4e7-147">If you enable the policy setting, you can select from among the following policy settings.</span></span>

- <span data-ttu-id="4a4e7-148">**Tillåt endast signerade skript** tillåter att skript endast körs om de är signerade av en betrodd utgivare.</span><span class="sxs-lookup"><span data-stu-id="4a4e7-148">**Allow only signed scripts** allows scripts to execute only if they are signed by a trusted publisher.</span></span> <span data-ttu-id="4a4e7-149">Den här inställningen motsvarar körnings principen för AllSigned.</span><span class="sxs-lookup"><span data-stu-id="4a4e7-149">This policy setting is equivalent to the AllSigned execution policy.</span></span>

- <span data-ttu-id="4a4e7-150">**Tillåt lokala skript och fjärrsignerade skript** tillåter att alla lokala skript körs.</span><span class="sxs-lookup"><span data-stu-id="4a4e7-150">**Allow local scripts and remote signed scripts** allows all local scripts to run.</span></span> <span data-ttu-id="4a4e7-151">Skript som kommer från Internet måste signeras av en betrodd utgivare.</span><span class="sxs-lookup"><span data-stu-id="4a4e7-151">Scripts that originate from the Internet must be signed by a trusted publisher.</span></span> <span data-ttu-id="4a4e7-152">Den här inställningen motsvarar körnings principen för RemoteSigned.</span><span class="sxs-lookup"><span data-stu-id="4a4e7-152">This policy setting is equivalent to the RemoteSigned execution policy.</span></span>

- <span data-ttu-id="4a4e7-153">**Tillåt alla skript** att köra alla skript.</span><span class="sxs-lookup"><span data-stu-id="4a4e7-153">**Allow all scripts** allows all scripts to run.</span></span> <span data-ttu-id="4a4e7-154">Den här princip inställningen motsvarar principen för obegränsad körning.</span><span class="sxs-lookup"><span data-stu-id="4a4e7-154">This policy setting is equivalent to the Unrestricted execution policy.</span></span>

<span data-ttu-id="4a4e7-155">Om du inaktiverar den här inställningen tillåts inga skript att köras.</span><span class="sxs-lookup"><span data-stu-id="4a4e7-155">If you disable this policy setting, no scripts are allowed to run.</span></span> <span data-ttu-id="4a4e7-156">Den här princip inställningen motsvarar principen för begränsad körning.</span><span class="sxs-lookup"><span data-stu-id="4a4e7-156">This policy setting is equivalent to the Restricted execution policy.</span></span>

<span data-ttu-id="4a4e7-157">Om du inaktiverar eller inte konfigurerar den här princip inställningen avgör den körnings princip som har angetts för datorn eller användaren av `Set-ExecutionPolicy` cmdleten om skript tillåts köra.</span><span class="sxs-lookup"><span data-stu-id="4a4e7-157">If you disable or do not configure this policy setting, the execution policy that is set for the computer or user by the `Set-ExecutionPolicy` cmdlet determines whether scripts are permitted to run.</span></span> <span data-ttu-id="4a4e7-158">Standardvärdet är begränsat.</span><span class="sxs-lookup"><span data-stu-id="4a4e7-158">The default value is Restricted.</span></span>

<span data-ttu-id="4a4e7-159">Mer information finns i [about_Execution_Policies](about_Execution_Policies.md).</span><span class="sxs-lookup"><span data-stu-id="4a4e7-159">For more information, see [about_Execution_Policies](about_Execution_Policies.md).</span></span>

## <a name="turn-on-powershell-transcription"></a><span data-ttu-id="4a4e7-160">Aktivera PowerShell-avskrift</span><span class="sxs-lookup"><span data-stu-id="4a4e7-160">Turn on powershell transcription</span></span>

<span data-ttu-id="4a4e7-161">Med princip inställningen **Aktivera PowerShell-avskrift** kan du samla in indata och utdata för PowerShell Core-kommandon i textbaserade avskrifter.</span><span class="sxs-lookup"><span data-stu-id="4a4e7-161">The **Turn on PowerShell Transcription** policy setting lets you capture the input and output of PowerShell Core commands into text-based transcripts.</span></span> <span data-ttu-id="4a4e7-162">Om du aktiverar den här inställningen aktive ras avskrifts loggning för PowerShell Core och andra program som utnyttjar PowerShell Core-motorn av PowerShell-kärnan.</span><span class="sxs-lookup"><span data-stu-id="4a4e7-162">If you enable this policy setting, PowerShell Core will enable transcription logging for PowerShell Core and any other applications that leverage the PowerShell Core engine.</span></span> <span data-ttu-id="4a4e7-163">Som standard registrerar PowerShell Core avskrifts-utdata till varje användares Mina dokument katalog, med ett fil namn som innehåller PowerShell_transcript, tillsammans med dator namnet och start tiden.</span><span class="sxs-lookup"><span data-stu-id="4a4e7-163">By default, PowerShell Core will record transcript output to each users' My Documents directory, with a file name that includes 'PowerShell_transcript', along with the computer name and time started.</span></span>
<span data-ttu-id="4a4e7-164">Att aktivera den här principen motsvarar att anropa Start-Transcript-cmdlet: en på varje PowerShell Core-session.</span><span class="sxs-lookup"><span data-stu-id="4a4e7-164">Enabling this policy is equivalent to calling the Start-Transcript cmdlet on each PowerShell Core session.</span></span>

<span data-ttu-id="4a4e7-165">Om du inaktiverar den här inställningen inaktive ras avskrifts loggningen av PowerShell-baserade program som standard, även om avskriften fortfarande kan aktive ras via Start-Transcript-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="4a4e7-165">If you disable this policy setting, transcription logging of PowerShell-based applications is disabled by default, although transcripting can still be enabled through the Start-Transcript cmdlet.</span></span>

<span data-ttu-id="4a4e7-166">Om du använder OutputDirectory-inställningen för att aktivera avskrifts loggning till en delad plats måste du begränsa åtkomsten till katalogen för att hindra användare från att Visa avskrifterna för andra användare eller datorer.</span><span class="sxs-lookup"><span data-stu-id="4a4e7-166">If you use the OutputDirectory setting to enable transcription logging to a shared location, be sure to limit access to that directory to prevent users from viewing the transcripts of other users or computers.</span></span>

## <a name="set-the-default-source-path-for-update-help"></a><span data-ttu-id="4a4e7-167">Ange standard käll Sök väg för Update-Help</span><span class="sxs-lookup"><span data-stu-id="4a4e7-167">Set the default source path for Update-Help</span></span>

<span data-ttu-id="4a4e7-168">**Ange standard käll Sök väg för uppdatering – hjälp** princip inställningen anger ett standardvärde för cmdlet: en **SourcePath** -parameter `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="4a4e7-168">The **Set the Default Source Path for Update-Help** policy setting sets a default value for the **SourcePath** parameter of the `Update-Help` cmdlet.</span></span>
<span data-ttu-id="4a4e7-169">Den här inställningen förhindrar att användare använder `Update-Help` cmdleten för att hämta hjälpfiler från Internet.</span><span class="sxs-lookup"><span data-stu-id="4a4e7-169">This setting prevents users from using the `Update-Help` cmdlet to download help files from the Internet.</span></span>

> [!NOTE]
> <span data-ttu-id="4a4e7-170">Den här grupprincip inställningen visas under **dator konfiguration** och **användar konfiguration**.</span><span class="sxs-lookup"><span data-stu-id="4a4e7-170">This Group Policy setting appears under **Computer Configuration** and **User Configuration**.</span></span> <span data-ttu-id="4a4e7-171">Men endast grupprincip-inställningen under **dator konfiguration** är effektiv.</span><span class="sxs-lookup"><span data-stu-id="4a4e7-171">However, only the Group Policy setting under **Computer Configuration** is effective.</span></span> <span data-ttu-id="4a4e7-172">Inställningen grupprincip under **användar konfigurationen** ignoreras.</span><span class="sxs-lookup"><span data-stu-id="4a4e7-172">The Group Policy setting under **User Configuration** is ignored.</span></span>

<span data-ttu-id="4a4e7-173">`Update-Help`Cmdlet: en laddar ned och installerar de senaste hjälpfilerna för PowerShell-moduler och installerar dem på datorn.</span><span class="sxs-lookup"><span data-stu-id="4a4e7-173">The `Update-Help` cmdlet downloads and installs the newest help files for PowerShell modules and installs them on the computer.</span></span> <span data-ttu-id="4a4e7-174">Som standard `Update-Help` hämtar nya hjälpfiler från en Internet plats som anges av modulen.</span><span class="sxs-lookup"><span data-stu-id="4a4e7-174">By default, `Update-Help` downloads new help files from an Internet location specified by the module.</span></span>

<span data-ttu-id="4a4e7-175">Du kan dock använda `Save-Help` cmdleten för att ladda ned de senaste hjälpfilerna till en fil system plats, till exempel en nätverks resurs, och sedan använda `Update-Help` cmdleten för att hämta hjälpfilerna från fil system platsen och installera dem på datorn.</span><span class="sxs-lookup"><span data-stu-id="4a4e7-175">However, you can use the `Save-Help` cmdlet to download the newest help files to a file system location, such as a network share, and then use the `Update-Help` cmdlet to get the help files from the file system location and install them on the computer.</span></span> <span data-ttu-id="4a4e7-176">Parametern **SourcePath** för `Update-Help` cmdleten anger fil system platsen.</span><span class="sxs-lookup"><span data-stu-id="4a4e7-176">The **SourcePath** parameter of the `Update-Help` cmdlet specifies the file system location.</span></span>

<span data-ttu-id="4a4e7-177">Genom att ange ett standardvärde för parametern **SourcePath** lägger den här grupprincip inställningen implicit till parametern **SourcePath** i alla `Update-Help` kommandon.</span><span class="sxs-lookup"><span data-stu-id="4a4e7-177">By providing a default value for the **SourcePath** parameter, this Group Policy setting implicitly adds the **SourcePath** parameter to all `Update-Help` commands.</span></span> <span data-ttu-id="4a4e7-178">Användare kan åsidosätta den specifika fil system platsen som anges som standardvärde genom att ange en annan plats för fil systemet.</span><span class="sxs-lookup"><span data-stu-id="4a4e7-178">Users can override the particular file system location specified as the default value by entering a different file system location.</span></span>
<span data-ttu-id="4a4e7-179">Men de kan inte ta bort **SourcePath** -parametern från `Update-Help` kommandot.</span><span class="sxs-lookup"><span data-stu-id="4a4e7-179">But they cannot remove the **SourcePath** parameter from the `Update-Help` command.</span></span>

<span data-ttu-id="4a4e7-180">Om du aktiverar den här inställningen kan du ange ett standardvärde för parametern **SourcePath** .</span><span class="sxs-lookup"><span data-stu-id="4a4e7-180">If you enable this policy setting, you can specify a default value for the **SourcePath** parameter.</span></span> <span data-ttu-id="4a4e7-181">Ange en fil system plats.</span><span class="sxs-lookup"><span data-stu-id="4a4e7-181">Enter a file system location.</span></span>

<span data-ttu-id="4a4e7-182">Om den här inställningen är inaktive rad eller inte konfigurerad, finns det inget standardvärde för cmdlet-parameterns **SourcePath** -parameter `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="4a4e7-182">If this policy setting is disabled or not configured, there is no default value for the **SourcePath** parameter of the `Update-Help` cmdlet.</span></span> <span data-ttu-id="4a4e7-183">Användare kan hämta hjälpen från Internet eller från alla fil system platser.</span><span class="sxs-lookup"><span data-stu-id="4a4e7-183">Users can download help from the Internet or from any file system location.</span></span>

<span data-ttu-id="4a4e7-184">Mer information finns i [about_Updatable_Help](about_Updatable_Help.md).</span><span class="sxs-lookup"><span data-stu-id="4a4e7-184">For more information, see [about_Updatable_Help](about_Updatable_Help.md).</span></span>

## <a name="keywords"></a><span data-ttu-id="4a4e7-185">Nyckelord</span><span class="sxs-lookup"><span data-stu-id="4a4e7-185">Keywords</span></span>

<span data-ttu-id="4a4e7-186">about_Group_Policies about_GroupPolicy</span><span class="sxs-lookup"><span data-stu-id="4a4e7-186">about_Group_Policies about_GroupPolicy</span></span>

## <a name="see-also"></a><span data-ttu-id="4a4e7-187">Se även</span><span class="sxs-lookup"><span data-stu-id="4a4e7-187">See also</span></span>

[<span data-ttu-id="4a4e7-188">Princip för PowerShell-kärnan RFC</span><span class="sxs-lookup"><span data-stu-id="4a4e7-188">PowerShell Core Policy RFC</span></span>](https://github.com/PowerShell/PowerShell-RFC/blob/master/4-Experimental-Accepted/RFC0041-Policy.md)

[<span data-ttu-id="4a4e7-189">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="4a4e7-189">about_Execution_Policies</span></span>](about_Execution_Policies.md)

[<span data-ttu-id="4a4e7-190">about_Modules</span><span class="sxs-lookup"><span data-stu-id="4a4e7-190">about_Modules</span></span>](about_Modules.md)

[<span data-ttu-id="4a4e7-191">about_Updatable_Help</span><span class="sxs-lookup"><span data-stu-id="4a4e7-191">about_Updatable_Help</span></span>](about_Updatable_Help.md)

[<span data-ttu-id="4a4e7-192">Get-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="4a4e7-192">Get-ExecutionPolicy</span></span>](xref:Microsoft.PowerShell.Security.Get-ExecutionPolicy)

[<span data-ttu-id="4a4e7-193">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="4a4e7-193">Set-ExecutionPolicy</span></span>](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)

[<span data-ttu-id="4a4e7-194">Hämta modul</span><span class="sxs-lookup"><span data-stu-id="4a4e7-194">Get-Module</span></span>](xref:Microsoft.PowerShell.Core.Get-Module)

[<span data-ttu-id="4a4e7-195">Uppdatera – hjälp</span><span class="sxs-lookup"><span data-stu-id="4a4e7-195">Update-Help</span></span>](xref:Microsoft.PowerShell.Core.Update-Help)

[<span data-ttu-id="4a4e7-196">Spara – hjälp</span><span class="sxs-lookup"><span data-stu-id="4a4e7-196">Save-Help</span></span>](xref:Microsoft.PowerShell.Core.Save-Help)

<!-- link references -->
[gpstore]: https://support.microsoft.com/help/3087759

