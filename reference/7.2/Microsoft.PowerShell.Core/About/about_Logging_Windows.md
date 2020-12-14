---
description: PowerShell loggar interna åtgärder från motorn, providers och cmdlets till händelse loggen i Windows.
Locale: en-US
ms.date: 03/30/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_logging_windows?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Logging-Windows
ms.openlocfilehash: d6ae50b50911417da8dd306cad69e3fc7129fedc
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708475"
---
# <a name="about-logging-windows"></a><span data-ttu-id="5e55b-103">Om loggning av Windows</span><span class="sxs-lookup"><span data-stu-id="5e55b-103">About Logging Windows</span></span>

## <a name="short-description"></a><span data-ttu-id="5e55b-104">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="5e55b-104">Short description</span></span>
<span data-ttu-id="5e55b-105">PowerShell loggar interna åtgärder från motorn, providers och cmdlets till händelse loggen i Windows.</span><span class="sxs-lookup"><span data-stu-id="5e55b-105">PowerShell logs internal operations from the engine, providers, and cmdlets to the Windows event log.</span></span>

## <a name="long-description"></a><span data-ttu-id="5e55b-106">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="5e55b-106">Long description</span></span>

<span data-ttu-id="5e55b-107">PowerShell loggar information om PowerShell-åtgärder, till exempel starta och stoppa motorn och providers och köra PowerShell-kommandon.</span><span class="sxs-lookup"><span data-stu-id="5e55b-107">PowerShell logs details about PowerShell operations, such as starting and stopping the engine and providers, and executing PowerShell commands.</span></span>

> [!NOTE]
> <span data-ttu-id="5e55b-108">Windows PowerShell-versionerna 3,0, 4,0, 5,0 och 5,1 innehåller **EventLog** -cmdletar för Windows-händelseloggarna.</span><span class="sxs-lookup"><span data-stu-id="5e55b-108">Windows PowerShell versions 3.0, 4.0, 5.0, and 5.1 include **EventLog** cmdlets for the Windows event logs.</span></span> <span data-ttu-id="5e55b-109">I dessa versioner för att visa listan över cmdletar för **händelse loggen** skriver du: `Get-Command -Noun EventLog` .</span><span class="sxs-lookup"><span data-stu-id="5e55b-109">In those versions, to display the list of **EventLog** cmdlets type: `Get-Command -Noun EventLog`.</span></span> <span data-ttu-id="5e55b-110">Mer information finns i cmdlet-dokumentationen och about_EventLogs för din version av Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5e55b-110">For more information, see the cmdlet documentation and about_EventLogs for your version of Windows PowerShell.</span></span>

## <a name="viewing-the-powershell-event-log-entries-on-windows"></a><span data-ttu-id="5e55b-111">Visa poster i PowerShell-händelseloggen i Windows</span><span class="sxs-lookup"><span data-stu-id="5e55b-111">Viewing the PowerShell event log entries on Windows</span></span>

<span data-ttu-id="5e55b-112">PowerShell-loggar kan visas med hjälp av Windows Loggboken.</span><span class="sxs-lookup"><span data-stu-id="5e55b-112">PowerShell logs can be viewed using the Windows Event Viewer.</span></span> <span data-ttu-id="5e55b-113">Händelse loggen finns i gruppen program-och tjänst loggar och har namnet `PowerShellCore` .</span><span class="sxs-lookup"><span data-stu-id="5e55b-113">The event log is located in the Application and Services Logs group and is named `PowerShellCore`.</span></span> <span data-ttu-id="5e55b-114">Den tillhör ande ETW-providern `GUID` är `{f90714a8-5509-434a-bf6d-b1624c8a19a2}` .</span><span class="sxs-lookup"><span data-stu-id="5e55b-114">The associated ETW provider `GUID` is `{f90714a8-5509-434a-bf6d-b1624c8a19a2}`.</span></span>

<span data-ttu-id="5e55b-115">När skript block loggning är aktiverat loggar PowerShell följande händelser i `PowerShellCore/Operational` loggen:</span><span class="sxs-lookup"><span data-stu-id="5e55b-115">When Script Block Logging is enabled, PowerShell logs the following events to the `PowerShellCore/Operational` log:</span></span>

|  <span data-ttu-id="5e55b-116">Fält</span><span class="sxs-lookup"><span data-stu-id="5e55b-116">Field</span></span>  |       <span data-ttu-id="5e55b-117">Värde</span><span class="sxs-lookup"><span data-stu-id="5e55b-117">Value</span></span>       |
| ------- | ----------------- |
| <span data-ttu-id="5e55b-118">EventId</span><span class="sxs-lookup"><span data-stu-id="5e55b-118">EventId</span></span> | `4104` / `0x1008` |
| <span data-ttu-id="5e55b-119">Kanal</span><span class="sxs-lookup"><span data-stu-id="5e55b-119">Channel</span></span> | `Operational`     |
| <span data-ttu-id="5e55b-120">Nivå</span><span class="sxs-lookup"><span data-stu-id="5e55b-120">Level</span></span>   | `Verbose`         |
| <span data-ttu-id="5e55b-121">Opcode</span><span class="sxs-lookup"><span data-stu-id="5e55b-121">Opcode</span></span>  | `Create`          |
| <span data-ttu-id="5e55b-122">Uppgift</span><span class="sxs-lookup"><span data-stu-id="5e55b-122">Task</span></span>    | `CommandStart`    |
| <span data-ttu-id="5e55b-123">Följt</span><span class="sxs-lookup"><span data-stu-id="5e55b-123">Keyword</span></span> | `Runspace`        |

### <a name="registering-the-powershell-event-provider-on-windows"></a><span data-ttu-id="5e55b-124">Registrera PowerShell-Händelseprovidern i Windows</span><span class="sxs-lookup"><span data-stu-id="5e55b-124">Registering the PowerShell event provider on Windows</span></span>

<span data-ttu-id="5e55b-125">Till skillnad från Linux eller macOS kräver Windows att Händelseprovidern registreras innan händelser kan skrivas till händelse loggen.</span><span class="sxs-lookup"><span data-stu-id="5e55b-125">Unlike Linux or macOS, Windows requires the event provider to be registered before events can be written to the event log.</span></span> <span data-ttu-id="5e55b-126">Aktivera PowerShell-Händelseprovidern genom att köra följande kommando från en upphöjd PowerShell-kommandotolk.</span><span class="sxs-lookup"><span data-stu-id="5e55b-126">To enable the PowerShell event provider, run the following command from an elevated PowerShell prompt.</span></span>

```powershell
$PSHOME\RegisterManifest.ps1
```

### <a name="unregistering-the-powershell-event-provider-on-windows"></a><span data-ttu-id="5e55b-127">Avregistrerar PowerShell-Händelseprovidern i Windows</span><span class="sxs-lookup"><span data-stu-id="5e55b-127">Unregistering the PowerShell event provider on Windows</span></span>

<span data-ttu-id="5e55b-128">När du registrerar händelse leverantören placeras ett lås i det binära biblioteket som används för att avkoda händelser.</span><span class="sxs-lookup"><span data-stu-id="5e55b-128">Registering the event provider places a lock in the binary library used to decode events.</span></span> <span data-ttu-id="5e55b-129">För att kunna uppdatera det här biblioteket måste providern avregistreras för att låsa upp det här låset.</span><span class="sxs-lookup"><span data-stu-id="5e55b-129">To update this library, the provider must be unregistered to release this lock.</span></span>

<span data-ttu-id="5e55b-130">Om du vill avregistrera PowerShell-providern kör du följande kommando från en upphöjd PowerShell-kommandotolk.</span><span class="sxs-lookup"><span data-stu-id="5e55b-130">To unregister the PowerShell provider, run the following command from an elevated PowerShell prompt.</span></span>

```powershell
$PSHOME\RegisterManifest.ps1 -Unregister
```

<span data-ttu-id="5e55b-131">När du har uppdaterat PowerShell kör `$PSHOME\RegisterManifest.ps1` du för att registrera den uppdaterade Händelseprovidern.</span><span class="sxs-lookup"><span data-stu-id="5e55b-131">After updating PowerShell, run `$PSHOME\RegisterManifest.ps1` to register the updated event provider.</span></span>

## <a name="enabling-script-block-logging"></a><span data-ttu-id="5e55b-132">Aktivera skript Blocks loggning</span><span class="sxs-lookup"><span data-stu-id="5e55b-132">Enabling Script Block Logging</span></span>

<span data-ttu-id="5e55b-133">När du aktiverar skript Blocks loggning registrerar PowerShell innehållet i alla skript block som den bearbetar.</span><span class="sxs-lookup"><span data-stu-id="5e55b-133">When you enable Script Block Logging, PowerShell records the content of all script blocks that it processes.</span></span> <span data-ttu-id="5e55b-134">När en ny PowerShell-session har Aktiver ATS loggar den här informationen.</span><span class="sxs-lookup"><span data-stu-id="5e55b-134">Once enabled, any new PowerShell session logs this information.</span></span>

> [!NOTE]
> <span data-ttu-id="5e55b-135">Vi rekommenderar att du aktiverar skyddad händelse loggning, enligt beskrivningen nedan, när du använder skript Blocks loggning för något annat än diagnostiskt syfte.</span><span class="sxs-lookup"><span data-stu-id="5e55b-135">It's recommended to enable Protected Event Logging, as described below, when using Script Block Logging for anything other than diagnostics purposes.</span></span>

<span data-ttu-id="5e55b-136">Loggning av skript block kan aktive ras via grupprincip eller en register inställning.</span><span class="sxs-lookup"><span data-stu-id="5e55b-136">Script Block Logging can be enabled via Group Policy or a registry setting.</span></span>

### <a name="using-group-policy"></a><span data-ttu-id="5e55b-137">Använda grupprincip</span><span class="sxs-lookup"><span data-stu-id="5e55b-137">Using Group Policy</span></span>

<span data-ttu-id="5e55b-138">Aktivera automatisk avskrift genom att aktivera `Turn on PowerShell Script Block
Logging` funktionen i Grupprincip via `Administrative Templates -> Windows
Components -> Windows PowerShell` .</span><span class="sxs-lookup"><span data-stu-id="5e55b-138">To enable automatic transcription, enable the `Turn on PowerShell Script Block
Logging` feature in Group Policy through `Administrative Templates -> Windows
Components -> Windows PowerShell`.</span></span>

### <a name="using-the-registry"></a><span data-ttu-id="5e55b-139">Använda registret</span><span class="sxs-lookup"><span data-stu-id="5e55b-139">Using the Registry</span></span>

<span data-ttu-id="5e55b-140">Kör följande funktion:</span><span class="sxs-lookup"><span data-stu-id="5e55b-140">Run the following function:</span></span>

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

## <a name="protected-event-logging"></a><span data-ttu-id="5e55b-141">Skyddad händelse loggning</span><span class="sxs-lookup"><span data-stu-id="5e55b-141">Protected Event Logging</span></span>

<span data-ttu-id="5e55b-142">Att öka loggnings nivån på ett system ökar risken för att loggat innehåll kan innehålla känsliga data.</span><span class="sxs-lookup"><span data-stu-id="5e55b-142">Increasing the level of logging on a system increases the possibility that logged content may contain sensitive data.</span></span> <span data-ttu-id="5e55b-143">Med skript loggning aktive rad kan exempelvis autentiseringsuppgifter eller andra känsliga data som används av ett skript skrivas till händelse loggen.</span><span class="sxs-lookup"><span data-stu-id="5e55b-143">For example, with script logging enabled, credentials or other sensitive data used by a script can be written to the event log.</span></span> <span data-ttu-id="5e55b-144">När en dator som har loggat känsliga data komprometteras, kan loggarna tillhandahålla en angripare med information som behövs för att utöka sin räckvidd.</span><span class="sxs-lookup"><span data-stu-id="5e55b-144">When a machine that has logged sensitive data is compromised, the logs can provide an attacker with information needed to extend their reach.</span></span>

<span data-ttu-id="5e55b-145">För att skydda den här informationen introducerar Windows 10 skyddad händelse loggning.</span><span class="sxs-lookup"><span data-stu-id="5e55b-145">To protect this information, Windows 10 introduces Protected Event Logging.</span></span>
<span data-ttu-id="5e55b-146">Med skyddad händelse loggning kan deltagande program Kryptera känsliga data som skrivs till händelse loggen.</span><span class="sxs-lookup"><span data-stu-id="5e55b-146">Protected Event Logging lets participating applications encrypt sensitive data written to the event log.</span></span> <span data-ttu-id="5e55b-147">Senare kan du dekryptera och bearbeta dessa loggar på en säkrare och centraliserad logg insamlare.</span><span class="sxs-lookup"><span data-stu-id="5e55b-147">Later, you can decrypt and process these logs on a more secure and centralized log collector.</span></span>

<span data-ttu-id="5e55b-148">Innehållet i händelse loggen skyddas med hjälp av standard-CMS (Cryptographic Message Syntax) i IETF.</span><span class="sxs-lookup"><span data-stu-id="5e55b-148">Event log content is protected using the IETF Cryptographic Message Syntax (CMS) standard.</span></span> <span data-ttu-id="5e55b-149">CMS använder kryptering med offentlig nyckel.</span><span class="sxs-lookup"><span data-stu-id="5e55b-149">CMS uses public key cryptography.</span></span> <span data-ttu-id="5e55b-150">Nycklar som används för att kryptera innehåll och dekryptera innehåll hålls åtskilda.</span><span class="sxs-lookup"><span data-stu-id="5e55b-150">The keys used to encrypt content and decrypt content are kept separate.</span></span>

<span data-ttu-id="5e55b-151">Den offentliga nyckeln kan delas mycket och är inte känslig för data.</span><span class="sxs-lookup"><span data-stu-id="5e55b-151">The public key can be shared widely and isn't sensitive data.</span></span> <span data-ttu-id="5e55b-152">Allt innehåll som krypteras med den här offentliga nyckeln kan bara dekrypteras av den privata nyckeln.</span><span class="sxs-lookup"><span data-stu-id="5e55b-152">Any content encrypted with this public key can only be decrypted by the private key.</span></span> <span data-ttu-id="5e55b-153">Mer information om kryptering med offentliga nycklar finns i [Wikipedia-offentlig nyckel kryptering](https://en.wikipedia.org/wiki/Public-key_cryptography).</span><span class="sxs-lookup"><span data-stu-id="5e55b-153">For more information about Public Key Cryptography, see [Wikipedia - Public Key Cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography).</span></span>

<span data-ttu-id="5e55b-154">Om du vill aktivera en princip för en skyddad händelse loggning distribuerar du en offentlig nyckel till alla datorer som har händelse logg data som ska skyddas.</span><span class="sxs-lookup"><span data-stu-id="5e55b-154">To enable a Protected Event Logging policy, deploy a public key to all machines that have event log data to protect.</span></span> <span data-ttu-id="5e55b-155">Motsvarande privata nyckel används för att efter bearbetning av händelse loggarna på en säkrare plats, till exempel en central händelse logg insamlare eller [Siem][] Aggregator.</span><span class="sxs-lookup"><span data-stu-id="5e55b-155">The corresponding private key is used to post-process the event logs at a more secure location such as a central event log collector, or [SIEM][] aggregator.</span></span> <span data-ttu-id="5e55b-156">Du kan konfigurera SIEM i Azure.</span><span class="sxs-lookup"><span data-stu-id="5e55b-156">You can set up SIEM in Azure.</span></span> <span data-ttu-id="5e55b-157">Mer information finns i [allmän Siem-integrering](/cloud-app-security/siem).</span><span class="sxs-lookup"><span data-stu-id="5e55b-157">For more information, see [Generic SIEM integration](/cloud-app-security/siem).</span></span>

### <a name="enabling-protected-event-logging-via-group-policy"></a><span data-ttu-id="5e55b-158">Aktivera skyddad händelse loggning via grupprincip</span><span class="sxs-lookup"><span data-stu-id="5e55b-158">Enabling Protected Event Logging via Group Policy</span></span>

<span data-ttu-id="5e55b-159">Aktivera skyddad händelse loggning genom att aktivera `Enable Protected Event Logging` funktionen i Grupprincip via `Administrative Templates -> Windows Components
-> Event Logging` .</span><span class="sxs-lookup"><span data-stu-id="5e55b-159">To enable Protected Event Logging, enable the `Enable Protected Event Logging` feature in Group Policy through `Administrative Templates -> Windows Components
-> Event Logging`.</span></span> <span data-ttu-id="5e55b-160">Den här inställningen kräver ett krypterings certifikat, som du kan ange i ett av flera formulär:</span><span class="sxs-lookup"><span data-stu-id="5e55b-160">This setting requires an encryption certificate, which you can provide in one of several forms:</span></span>

- <span data-ttu-id="5e55b-161">Innehållet i ett Base-64-kodat X. 509-certifikat (till exempel som erbjuds av `Export` alternativet i certifikat hanteraren).</span><span class="sxs-lookup"><span data-stu-id="5e55b-161">The content of a base-64 encoded X.509 certificate (for example, as offered by the `Export` option in Certificate Manager).</span></span>
- <span data-ttu-id="5e55b-162">Tumavtrycket för ett certifikat som finns i den lokala datorns certifikat arkiv (kan distribueras av PKI-infrastrukturen).</span><span class="sxs-lookup"><span data-stu-id="5e55b-162">The thumbprint of a certificate that can be found in the Local Machine certificate store (can be deployed by PKI infrastructure).</span></span>
- <span data-ttu-id="5e55b-163">Den fullständiga sökvägen till ett certifikat (kan vara lokal eller en fjär resurs).</span><span class="sxs-lookup"><span data-stu-id="5e55b-163">The full path to a certificate (can be local, or a remote share).</span></span>
- <span data-ttu-id="5e55b-164">Sökvägen till en katalog som innehåller ett certifikat eller certifikat (kan vara lokalt eller en fjär resurs).</span><span class="sxs-lookup"><span data-stu-id="5e55b-164">The path to a directory containing a certificate or certificates (can be local, or a remote share).</span></span>
- <span data-ttu-id="5e55b-165">Ämnes namnet för ett certifikat som kan hittas i den lokala datorns certifikat arkiv (kan distribueras av PKI-infrastrukturen).</span><span class="sxs-lookup"><span data-stu-id="5e55b-165">The subject name of a certificate that can be found in the Local Machine certificate store (can be deployed by PKI infrastructure).</span></span>

<span data-ttu-id="5e55b-166">Det resulterande certifikatet måste ha `Document Encryption` som en förbättrad nyckel användning ( `1.3.6.1.4.1.311.80.1` ) och antingen `Data Encipherment` eller `Key
Encipherment` nyckel användningen aktiverade.</span><span class="sxs-lookup"><span data-stu-id="5e55b-166">The resulting certificate must have `Document Encryption` as an enhanced key usage (`1.3.6.1.4.1.311.80.1`), and either `Data Encipherment` or `Key
Encipherment` key usages enabled.</span></span>

> [!WARNING]
> <span data-ttu-id="5e55b-167">Den privata nyckeln bör inte distribueras till datorns loggnings händelser.</span><span class="sxs-lookup"><span data-stu-id="5e55b-167">The private key shouldn't be deployed to the machines logging events.</span></span> <span data-ttu-id="5e55b-168">Den bör behållas på en säker plats där du dekrypterar meddelandena.</span><span class="sxs-lookup"><span data-stu-id="5e55b-168">It should be kept in a secure location where you decrypt the messages.</span></span>

### <a name="decrypting-protected-event-logging-messages"></a><span data-ttu-id="5e55b-169">Dekryptera meddelanden om skyddade händelser</span><span class="sxs-lookup"><span data-stu-id="5e55b-169">Decrypting Protected Event Logging messages</span></span>

<span data-ttu-id="5e55b-170">Följande skript kommer att hämta och dekryptera, förutsatt att du har den privata nyckeln:</span><span class="sxs-lookup"><span data-stu-id="5e55b-170">The following script will retrieve and decrypt, assuming that you have the private key:</span></span>

```powershell
Get-WinEvent Microsoft-Windows-PowerShell/Operational |
  Where-Object Id -eq 4104 | Unprotect-CmsMessage
```

## <a name="see-also"></a><span data-ttu-id="5e55b-171">Se även</span><span class="sxs-lookup"><span data-stu-id="5e55b-171">See also</span></span>

[<span data-ttu-id="5e55b-172">about_Logging_Non-Windows</span><span class="sxs-lookup"><span data-stu-id="5e55b-172">about_Logging_Non-Windows</span></span>](about_Logging_Non-Windows.md)

[<span data-ttu-id="5e55b-173">PowerShell det blå teamet</span><span class="sxs-lookup"><span data-stu-id="5e55b-173">PowerShell the Blue Team</span></span>](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)

[<span data-ttu-id="5e55b-174">Allmän SIEM-integration</span><span class="sxs-lookup"><span data-stu-id="5e55b-174">Generic SIEM integration</span></span>](/cloud-app-security/siem)

<!-- link references -->
[SIEM]: https://wikipedia.org/wiki/Security_information_and_event_management
