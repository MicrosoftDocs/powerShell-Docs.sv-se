---
description: PowerShell loggar interna åtgärder från motorn, providers och cmdlets.
keywords: powershell
Locale: en-US
ms.date: 03/30/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_logging_windows?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Logging-Windows
ms.openlocfilehash: e4f6134d4e9e7445233dea223e0a381e45bfb8e2
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270656"
---
# <a name="about-logging-windows"></a><span data-ttu-id="ec9c5-104">Om loggning av Windows</span><span class="sxs-lookup"><span data-stu-id="ec9c5-104">About Logging Windows</span></span>

## <a name="short-description"></a><span data-ttu-id="ec9c5-105">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="ec9c5-105">Short description</span></span>

<span data-ttu-id="ec9c5-106">PowerShell loggar interna åtgärder från motorn, providers och cmdlets.</span><span class="sxs-lookup"><span data-stu-id="ec9c5-106">PowerShell logs internal operations from the engine, providers, and cmdlets.</span></span>

## <a name="long-description"></a><span data-ttu-id="ec9c5-107">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="ec9c5-107">Long description</span></span>

<span data-ttu-id="ec9c5-108">PowerShell loggar information om PowerShell-åtgärder, till exempel starta och stoppa motorn och providers och köra PowerShell-kommandon.</span><span class="sxs-lookup"><span data-stu-id="ec9c5-108">PowerShell logs details about PowerShell operations, such as starting and stopping the engine and providers, and executing PowerShell commands.</span></span>

> [!NOTE]
> <span data-ttu-id="ec9c5-109">Windows PowerShell-versionerna 3,0, 4,0, 5,0 och 5,1 innehåller **EventLog** -cmdletar för Windows-händelseloggarna.</span><span class="sxs-lookup"><span data-stu-id="ec9c5-109">Windows PowerShell versions 3.0, 4.0, 5.0, and 5.1 include **EventLog** cmdlets for the Windows event logs.</span></span> <span data-ttu-id="ec9c5-110">I dessa versioner för att visa listan över cmdletar för **händelse loggen** skriver du: `Get-Command -Noun EventLog` .</span><span class="sxs-lookup"><span data-stu-id="ec9c5-110">In those versions, to display the list of **EventLog** cmdlets type: `Get-Command -Noun EventLog`.</span></span> <span data-ttu-id="ec9c5-111">Mer information finns i cmdlet-dokumentationen och about_EventLogs för din version av Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ec9c5-111">For more information, see the cmdlet documentation and about_EventLogs for your version of Windows PowerShell.</span></span>

## <a name="viewing-the-powershell-event-log-entries-on-windows"></a><span data-ttu-id="ec9c5-112">Visa poster i PowerShell-händelseloggen i Windows</span><span class="sxs-lookup"><span data-stu-id="ec9c5-112">Viewing the PowerShell event log entries on Windows</span></span>

<span data-ttu-id="ec9c5-113">PowerShell-loggar kan visas med hjälp av Windows Loggboken.</span><span class="sxs-lookup"><span data-stu-id="ec9c5-113">PowerShell logs can be viewed using the Windows Event Viewer.</span></span> <span data-ttu-id="ec9c5-114">Händelse loggen finns i gruppen program-och tjänst loggar och har namnet `PowerShellCore` .</span><span class="sxs-lookup"><span data-stu-id="ec9c5-114">The event log is located in the Application and Services Logs group and is named `PowerShellCore`.</span></span> <span data-ttu-id="ec9c5-115">Den tillhör ande ETW-providern `GUID` är `{f90714a8-5509-434a-bf6d-b1624c8a19a2}` .</span><span class="sxs-lookup"><span data-stu-id="ec9c5-115">The associated ETW provider `GUID` is `{f90714a8-5509-434a-bf6d-b1624c8a19a2}`.</span></span>

<span data-ttu-id="ec9c5-116">När skript block loggning är aktiverat loggar PowerShell följande händelser i `PowerShellCore/Operational` loggen:</span><span class="sxs-lookup"><span data-stu-id="ec9c5-116">When Script Block Logging is enabled, PowerShell logs the following events to the `PowerShellCore/Operational` log:</span></span>

|<span data-ttu-id="ec9c5-117">Fält</span><span class="sxs-lookup"><span data-stu-id="ec9c5-117">Field</span></span>| <span data-ttu-id="ec9c5-118">Värde</span><span class="sxs-lookup"><span data-stu-id="ec9c5-118">Value</span></span>|
|-|-|
|<span data-ttu-id="ec9c5-119">EventId</span><span class="sxs-lookup"><span data-stu-id="ec9c5-119">EventId</span></span>|`4104` / `0x1008`|
|<span data-ttu-id="ec9c5-120">Kanal</span><span class="sxs-lookup"><span data-stu-id="ec9c5-120">Channel</span></span>|`Operational`|
|<span data-ttu-id="ec9c5-121">Nivå</span><span class="sxs-lookup"><span data-stu-id="ec9c5-121">Level</span></span>|`Verbose`|
|<span data-ttu-id="ec9c5-122">Opcode</span><span class="sxs-lookup"><span data-stu-id="ec9c5-122">Opcode</span></span>|`Create`|
|<span data-ttu-id="ec9c5-123">Uppgift</span><span class="sxs-lookup"><span data-stu-id="ec9c5-123">Task</span></span>|`CommandStart`|
|<span data-ttu-id="ec9c5-124">Följt</span><span class="sxs-lookup"><span data-stu-id="ec9c5-124">Keyword</span></span>|`Runspace`|

### <a name="registering-the-powershell-event-provider-on-windows"></a><span data-ttu-id="ec9c5-125">Registrera PowerShell-Händelseprovidern i Windows</span><span class="sxs-lookup"><span data-stu-id="ec9c5-125">Registering the PowerShell event provider on Windows</span></span>

<span data-ttu-id="ec9c5-126">Till skillnad från Linux eller macOS kräver Windows att Händelseprovidern registreras innan händelser kan skrivas till händelse loggen.</span><span class="sxs-lookup"><span data-stu-id="ec9c5-126">Unlike Linux or macOS, Windows requires the event provider to be registered before events can be written to the event log.</span></span> <span data-ttu-id="ec9c5-127">Aktivera PowerShell-Händelseprovidern genom att köra följande kommando från en upphöjd PowerShell-kommandotolk.</span><span class="sxs-lookup"><span data-stu-id="ec9c5-127">To enable the PowerShell event provider, run the following command from an elevated PowerShell prompt.</span></span>

```powershell
$PSHOME\RegisterManifest.ps1
```

### <a name="unregistering-the-powershell-event-provider-on-windows"></a><span data-ttu-id="ec9c5-128">Avregistrerar PowerShell-Händelseprovidern i Windows</span><span class="sxs-lookup"><span data-stu-id="ec9c5-128">Unregistering the PowerShell event provider on Windows</span></span>

<span data-ttu-id="ec9c5-129">När du registrerar händelse leverantören placeras ett lås i det binära biblioteket som används för att avkoda händelser.</span><span class="sxs-lookup"><span data-stu-id="ec9c5-129">Registering the event provider places a lock in the binary library used to decode events.</span></span> <span data-ttu-id="ec9c5-130">För att kunna uppdatera det här biblioteket måste providern avregistreras för att låsa upp det här låset.</span><span class="sxs-lookup"><span data-stu-id="ec9c5-130">To update this library, the provider must be unregistered to release this lock.</span></span>

<span data-ttu-id="ec9c5-131">Om du vill avregistrera PowerShell-providern kör du följande kommando från en upphöjd PowerShell-kommandotolk.</span><span class="sxs-lookup"><span data-stu-id="ec9c5-131">To unregister the PowerShell provider, run the following command from an elevated PowerShell prompt.</span></span>

```powershell
$PSHOME\RegisterManifest.ps1 -Unregister
```

<span data-ttu-id="ec9c5-132">När du har uppdaterat PowerShell kör `$PSHOME\RegisterManifest.ps1` du för att registrera den uppdaterade Händelseprovidern.</span><span class="sxs-lookup"><span data-stu-id="ec9c5-132">After updating PowerShell, run `$PSHOME\RegisterManifest.ps1` to register the updated event provider.</span></span>

## <a name="enabling-script-block-logging"></a><span data-ttu-id="ec9c5-133">Aktivera skript Blocks loggning</span><span class="sxs-lookup"><span data-stu-id="ec9c5-133">Enabling Script Block Logging</span></span>

<span data-ttu-id="ec9c5-134">När du aktiverar skript Blocks loggning registrerar PowerShell innehållet i alla skript block som den bearbetar.</span><span class="sxs-lookup"><span data-stu-id="ec9c5-134">When you enable Script Block Logging, PowerShell records the content of all script blocks that it processes.</span></span> <span data-ttu-id="ec9c5-135">När en ny PowerShell-session har Aktiver ATS loggar den här informationen.</span><span class="sxs-lookup"><span data-stu-id="ec9c5-135">Once enabled, any new PowerShell session logs this information.</span></span>

> [!NOTE]
> <span data-ttu-id="ec9c5-136">Vi rekommenderar att du aktiverar skyddad händelse loggning, enligt beskrivningen nedan, när du använder skript Blocks loggning för något annat än diagnostiskt syfte.</span><span class="sxs-lookup"><span data-stu-id="ec9c5-136">It's recommended to enable Protected Event Logging, as described below, when using Script Block Logging for anything other than diagnostics purposes.</span></span>

<span data-ttu-id="ec9c5-137">Loggning av skript block kan aktive ras via grupprincip eller en register inställning.</span><span class="sxs-lookup"><span data-stu-id="ec9c5-137">Script Block Logging can be enabled via Group Policy or a registry setting.</span></span>

### <a name="using-group-policy"></a><span data-ttu-id="ec9c5-138">Använda grupprincip</span><span class="sxs-lookup"><span data-stu-id="ec9c5-138">Using Group Policy</span></span>

<span data-ttu-id="ec9c5-139">Aktivera automatisk avskrift genom att aktivera `Turn on PowerShell Script Block
Logging` funktionen i Grupprincip via `Administrative Templates -> Windows
Components -> Windows PowerShell` .</span><span class="sxs-lookup"><span data-stu-id="ec9c5-139">To enable automatic transcription, enable the `Turn on PowerShell Script Block
Logging` feature in Group Policy through `Administrative Templates -> Windows
Components -> Windows PowerShell`.</span></span>

### <a name="using-the-registry"></a><span data-ttu-id="ec9c5-140">Använda registret</span><span class="sxs-lookup"><span data-stu-id="ec9c5-140">Using the Registry</span></span>

<span data-ttu-id="ec9c5-141">Kör följande funktion:</span><span class="sxs-lookup"><span data-stu-id="ec9c5-141">Run the following function:</span></span>

```powershell
function Enable-PSScriptBlockLogging
{
    $basePath = 'HKLM:\Software\Policies\Microsoft\Windows' +
      '\PowerShell\ScriptBlockLogging'

    if(-not (Test-Path $basePath))
    {
        $null = New-Item $basePath -Force
    }

    Set-ItemProperty $basePath -Name EnableScriptBlockLogging -Value "1"
}
```

## <a name="protected-event-logging"></a><span data-ttu-id="ec9c5-142">Skyddad händelse loggning</span><span class="sxs-lookup"><span data-stu-id="ec9c5-142">Protected Event Logging</span></span>

<span data-ttu-id="ec9c5-143">Att öka loggnings nivån på ett system ökar risken för att loggat innehåll kan innehålla känsliga data.</span><span class="sxs-lookup"><span data-stu-id="ec9c5-143">Increasing the level of logging on a system increases the possibility that logged content may contain sensitive data.</span></span> <span data-ttu-id="ec9c5-144">Med skript loggning aktive rad kan exempelvis autentiseringsuppgifter eller andra känsliga data som används av ett skript skrivas till händelse loggen.</span><span class="sxs-lookup"><span data-stu-id="ec9c5-144">For example, with script logging enabled, credentials or other sensitive data used by a script can be written to the event log.</span></span> <span data-ttu-id="ec9c5-145">När en dator som har loggat känsliga data komprometteras, kan loggarna tillhandahålla en angripare med information som behövs för att utöka sin räckvidd.</span><span class="sxs-lookup"><span data-stu-id="ec9c5-145">When a machine that has logged sensitive data is compromised, the logs can provide an attacker with information needed to extend their reach.</span></span>

<span data-ttu-id="ec9c5-146">För att skydda den här informationen introducerar Windows 10 skyddad händelse loggning.</span><span class="sxs-lookup"><span data-stu-id="ec9c5-146">To protect this information, Windows 10 introduces Protected Event Logging.</span></span>
<span data-ttu-id="ec9c5-147">Med skyddad händelse loggning kan deltagande program Kryptera känsliga data som skrivs till händelse loggen.</span><span class="sxs-lookup"><span data-stu-id="ec9c5-147">Protected Event Logging lets participating applications encrypt sensitive data written to the event log.</span></span> <span data-ttu-id="ec9c5-148">Senare kan du dekryptera och bearbeta dessa loggar på en säkrare och centraliserad logg insamlare.</span><span class="sxs-lookup"><span data-stu-id="ec9c5-148">Later, you can decrypt and process these logs on a more secure and centralized log collector.</span></span>

<span data-ttu-id="ec9c5-149">Innehållet i händelse loggen skyddas med hjälp av standard-CMS (Cryptographic Message Syntax) i IETF.</span><span class="sxs-lookup"><span data-stu-id="ec9c5-149">Event log content is protected using the IETF Cryptographic Message Syntax (CMS) standard.</span></span> <span data-ttu-id="ec9c5-150">CMS använder kryptering med offentlig nyckel.</span><span class="sxs-lookup"><span data-stu-id="ec9c5-150">CMS uses public key cryptography.</span></span> <span data-ttu-id="ec9c5-151">Nycklar som används för att kryptera innehåll och dekryptera innehåll hålls åtskilda.</span><span class="sxs-lookup"><span data-stu-id="ec9c5-151">The keys used to encrypt content and decrypt content are kept separate.</span></span>

<span data-ttu-id="ec9c5-152">Den offentliga nyckeln kan delas mycket och är inte känslig för data.</span><span class="sxs-lookup"><span data-stu-id="ec9c5-152">The public key can be shared widely and isn't sensitive data.</span></span> <span data-ttu-id="ec9c5-153">Allt innehåll som krypteras med den här offentliga nyckeln kan bara dekrypteras av den privata nyckeln.</span><span class="sxs-lookup"><span data-stu-id="ec9c5-153">Any content encrypted with this public key can only be decrypted by the private key.</span></span> <span data-ttu-id="ec9c5-154">Mer information om kryptering med offentliga nycklar finns i [Wikipedia-offentlig nyckel kryptering](https://en.wikipedia.org/wiki/Public-key_cryptography).</span><span class="sxs-lookup"><span data-stu-id="ec9c5-154">For more information about Public Key Cryptography, see [Wikipedia - Public Key Cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography).</span></span>

<span data-ttu-id="ec9c5-155">Om du vill aktivera en princip för en skyddad händelse loggning distribuerar du en offentlig nyckel till alla datorer som har händelse logg data som ska skyddas.</span><span class="sxs-lookup"><span data-stu-id="ec9c5-155">To enable a Protected Event Logging policy, deploy a public key to all machines that have event log data to protect.</span></span> <span data-ttu-id="ec9c5-156">Motsvarande privata nyckel används för att efter bearbetning av händelse loggarna på en säkrare plats, till exempel en central händelse logg insamlare eller [Siem][] Aggregator.</span><span class="sxs-lookup"><span data-stu-id="ec9c5-156">The corresponding private key is used to post-process the event logs at a more secure location such as a central event log collector, or [SIEM][] aggregator.</span></span> <span data-ttu-id="ec9c5-157">Du kan konfigurera SIEM i Azure.</span><span class="sxs-lookup"><span data-stu-id="ec9c5-157">You can set up SIEM in Azure.</span></span> <span data-ttu-id="ec9c5-158">Mer information finns i [allmän Siem-integrering](/cloud-app-security/siem).</span><span class="sxs-lookup"><span data-stu-id="ec9c5-158">For more information, see [Generic SIEM integration](/cloud-app-security/siem).</span></span>

### <a name="enabling-protected-event-logging-via-group-policy"></a><span data-ttu-id="ec9c5-159">Aktivera skyddad händelse loggning via grupprincip</span><span class="sxs-lookup"><span data-stu-id="ec9c5-159">Enabling Protected Event Logging via Group Policy</span></span>

<span data-ttu-id="ec9c5-160">Aktivera skyddad händelse loggning genom att aktivera `Enable Protected Event Logging` funktionen i Grupprincip via `Administrative Templates -> Windows Components
-> Event Logging` .</span><span class="sxs-lookup"><span data-stu-id="ec9c5-160">To enable Protected Event Logging, enable the `Enable Protected Event Logging` feature in Group Policy through `Administrative Templates -> Windows Components
-> Event Logging`.</span></span> <span data-ttu-id="ec9c5-161">Den här inställningen kräver ett krypterings certifikat, som du kan ange i ett av flera formulär:</span><span class="sxs-lookup"><span data-stu-id="ec9c5-161">This setting requires an encryption certificate, which you can provide in one of several forms:</span></span>

- <span data-ttu-id="ec9c5-162">Innehållet i ett Base-64-kodat X. 509-certifikat (till exempel som erbjuds av `Export` alternativet i certifikat hanteraren).</span><span class="sxs-lookup"><span data-stu-id="ec9c5-162">The content of a base-64 encoded X.509 certificate (for example, as offered by the `Export` option in Certificate Manager).</span></span>
- <span data-ttu-id="ec9c5-163">Tumavtrycket för ett certifikat som finns i den lokala datorns certifikat arkiv (kan distribueras av PKI-infrastrukturen).</span><span class="sxs-lookup"><span data-stu-id="ec9c5-163">The thumbprint of a certificate that can be found in the Local Machine certificate store (can be deployed by PKI infrastructure).</span></span>
- <span data-ttu-id="ec9c5-164">Den fullständiga sökvägen till ett certifikat (kan vara lokal eller en fjär resurs).</span><span class="sxs-lookup"><span data-stu-id="ec9c5-164">The full path to a certificate (can be local, or a remote share).</span></span>
- <span data-ttu-id="ec9c5-165">Sökvägen till en katalog som innehåller ett certifikat eller certifikat (kan vara lokalt eller en fjär resurs).</span><span class="sxs-lookup"><span data-stu-id="ec9c5-165">The path to a directory containing a certificate or certificates (can be local, or a remote share).</span></span>
- <span data-ttu-id="ec9c5-166">Ämnes namnet för ett certifikat som kan hittas i den lokala datorns certifikat arkiv (kan distribueras av PKI-infrastrukturen).</span><span class="sxs-lookup"><span data-stu-id="ec9c5-166">The subject name of a certificate that can be found in the Local Machine certificate store (can be deployed by PKI infrastructure).</span></span>

<span data-ttu-id="ec9c5-167">Det resulterande certifikatet måste ha `Document Encryption` som en förbättrad nyckel användning ( `1.3.6.1.4.1.311.80.1` ) och antingen `Data Encipherment` eller `Key
Encipherment` nyckel användningen aktiverade.</span><span class="sxs-lookup"><span data-stu-id="ec9c5-167">The resulting certificate must have `Document Encryption` as an enhanced key usage (`1.3.6.1.4.1.311.80.1`), and either `Data Encipherment` or `Key
Encipherment` key usages enabled.</span></span>

> [!WARNING]
> <span data-ttu-id="ec9c5-168">Den privata nyckeln bör inte distribueras till datorns loggnings händelser.</span><span class="sxs-lookup"><span data-stu-id="ec9c5-168">The private key shouldn't be deployed to the machines logging events.</span></span> <span data-ttu-id="ec9c5-169">Den bör behållas på en säker plats där du dekrypterar meddelandena.</span><span class="sxs-lookup"><span data-stu-id="ec9c5-169">It should be kept in a secure location where you decrypt the messages.</span></span>

### <a name="decrypting-protected-event-logging-messages"></a><span data-ttu-id="ec9c5-170">Dekryptera meddelanden om skyddade händelser</span><span class="sxs-lookup"><span data-stu-id="ec9c5-170">Decrypting Protected Event Logging messages</span></span>

<span data-ttu-id="ec9c5-171">Följande skript kommer att hämta och dekryptera, förutsatt att du har den privata nyckeln:</span><span class="sxs-lookup"><span data-stu-id="ec9c5-171">The following script will retrieve and decrypt, assuming that you have the private key:</span></span>

```powershell
Get-WinEvent Microsoft-Windows-PowerShell/Operational |
  Where-Object Id -eq 4104 | Unprotect-CmsMessage
```

## <a name="see-also"></a><span data-ttu-id="ec9c5-172">Se även</span><span class="sxs-lookup"><span data-stu-id="ec9c5-172">See also</span></span>

[<span data-ttu-id="ec9c5-173">about_Logging_Non-Windows</span><span class="sxs-lookup"><span data-stu-id="ec9c5-173">about_Logging_Non-Windows</span></span>](about_Logging_Non-Windows.md)

[<span data-ttu-id="ec9c5-174">PowerShell det blå teamet</span><span class="sxs-lookup"><span data-stu-id="ec9c5-174">PowerShell the Blue Team</span></span>](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)

[<span data-ttu-id="ec9c5-175">Allmän SIEM-integration</span><span class="sxs-lookup"><span data-stu-id="ec9c5-175">Generic SIEM integration</span></span>](/cloud-app-security/siem)

<!-- link references -->
[SIEM]: https://wikipedia.org/wiki/Security_information_and_event_management
