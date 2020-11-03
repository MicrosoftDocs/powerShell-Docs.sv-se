---
description: PowerShell loggar interna åtgärder från motorn, providers och cmdlets.
keywords: powershell
Locale: en-US
ms.date: 12/14/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_logging?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Logging
ms.openlocfilehash: 5d061b38b5b0fa45cf0a86c2f5b7e0efcb8d1f7b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93271551"
---
# <a name="about-logging"></a><span data-ttu-id="071fd-104">Om loggning</span><span class="sxs-lookup"><span data-stu-id="071fd-104">About Logging</span></span>

## <a name="short-description"></a><span data-ttu-id="071fd-105">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="071fd-105">Short description</span></span>

<span data-ttu-id="071fd-106">PowerShell loggar interna åtgärder från motorn, providers och cmdlets.</span><span class="sxs-lookup"><span data-stu-id="071fd-106">PowerShell logs internal operations from the engine, providers, and cmdlets.</span></span>

## <a name="long-description"></a><span data-ttu-id="071fd-107">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="071fd-107">Long description</span></span>

<span data-ttu-id="071fd-108">PowerShell loggar information om PowerShell-åtgärder, till exempel starta och stoppa motorn och providers och köra PowerShell-kommandon.</span><span class="sxs-lookup"><span data-stu-id="071fd-108">PowerShell logs details about PowerShell operations, such as starting and stopping the engine and providers, and executing PowerShell commands.</span></span>

> [!NOTE]
> <span data-ttu-id="071fd-109">Windows PowerShell-versionerna 3,0, 4,0, 5,0 och 5,1 innehåller **EventLog** -cmdletar för Windows-händelseloggarna.</span><span class="sxs-lookup"><span data-stu-id="071fd-109">Windows PowerShell versions 3.0, 4.0, 5.0, and 5.1 include **EventLog** cmdlets for the Windows event logs.</span></span> <span data-ttu-id="071fd-110">I dessa versioner för att visa listan över cmdletar för **händelse loggen** skriver du: `Get-Command -Noun EventLog` .</span><span class="sxs-lookup"><span data-stu-id="071fd-110">In those versions, to display the list of **EventLog** cmdlets type: `Get-Command -Noun EventLog`.</span></span> <span data-ttu-id="071fd-111">Mer information finns i cmdlet-dokumentationen och about_EventLogs för din version av Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="071fd-111">For more information, see the cmdlet documentation and about_EventLogs for your version of Windows PowerShell.</span></span>

## <a name="viewing-the-powershell-event-log-entries-on-windows"></a><span data-ttu-id="071fd-112">Visa poster i PowerShell-händelseloggen i Windows</span><span class="sxs-lookup"><span data-stu-id="071fd-112">Viewing the PowerShell event log entries on Windows</span></span>

<span data-ttu-id="071fd-113">PowerShell-loggar kan visas med hjälp av Windows Loggboken.</span><span class="sxs-lookup"><span data-stu-id="071fd-113">PowerShell logs can be viewed using the Windows Event Viewer.</span></span> <span data-ttu-id="071fd-114">Händelse loggen finns i gruppen program-och tjänst loggar och har namnet `Microsoft-Windows-PowerShell` .</span><span class="sxs-lookup"><span data-stu-id="071fd-114">The event log is located in the Application and Services Logs group and is named `Microsoft-Windows-PowerShell`.</span></span> <span data-ttu-id="071fd-115">Den tillhör ande ETW-providern `GUID` är `{A0C1853B-5C40-4B15-8766-3CF1C58F985A}` .</span><span class="sxs-lookup"><span data-stu-id="071fd-115">The associated ETW provider `GUID` is `{A0C1853B-5C40-4B15-8766-3CF1C58F985A}`.</span></span>

<span data-ttu-id="071fd-116">När skript block loggning är aktiverat loggar PowerShell följande händelser i `Microsoft-Windows-PowerShell/Operational` loggen:</span><span class="sxs-lookup"><span data-stu-id="071fd-116">When Script Block Logging is enabled, PowerShell logs the following events to the `Microsoft-Windows-PowerShell/Operational` log:</span></span>

|<span data-ttu-id="071fd-117">Fält</span><span class="sxs-lookup"><span data-stu-id="071fd-117">Field</span></span>| <span data-ttu-id="071fd-118">Värde</span><span class="sxs-lookup"><span data-stu-id="071fd-118">Value</span></span>|
|-|-|
|<span data-ttu-id="071fd-119">EventId</span><span class="sxs-lookup"><span data-stu-id="071fd-119">EventId</span></span>|`4104` / `0x1008`|
|<span data-ttu-id="071fd-120">Kanal</span><span class="sxs-lookup"><span data-stu-id="071fd-120">Channel</span></span>|`Operational`|
|<span data-ttu-id="071fd-121">Nivå</span><span class="sxs-lookup"><span data-stu-id="071fd-121">Level</span></span>|`Verbose`|
|<span data-ttu-id="071fd-122">Opcode</span><span class="sxs-lookup"><span data-stu-id="071fd-122">Opcode</span></span>|`Create`|
|<span data-ttu-id="071fd-123">Uppgift</span><span class="sxs-lookup"><span data-stu-id="071fd-123">Task</span></span>|`CommandStart`|
|<span data-ttu-id="071fd-124">Följt</span><span class="sxs-lookup"><span data-stu-id="071fd-124">Keyword</span></span>|`Runspace`|

## <a name="enabling-script-block-logging"></a><span data-ttu-id="071fd-125">Aktivera skript Blocks loggning</span><span class="sxs-lookup"><span data-stu-id="071fd-125">Enabling Script Block Logging</span></span>

<span data-ttu-id="071fd-126">När du aktiverar skript Blocks loggning registrerar PowerShell innehållet i alla skript block som den bearbetar.</span><span class="sxs-lookup"><span data-stu-id="071fd-126">When you enable Script Block Logging, PowerShell records the content of all script blocks that it processes.</span></span> <span data-ttu-id="071fd-127">När en ny PowerShell-session har Aktiver ATS loggar den här informationen.</span><span class="sxs-lookup"><span data-stu-id="071fd-127">Once enabled, any new PowerShell session logs this information.</span></span>

> [!NOTE]
> <span data-ttu-id="071fd-128">Vi rekommenderar att du aktiverar skyddad händelse loggning, enligt beskrivningen nedan, när du använder skript Blocks loggning för något annat än diagnostiskt syfte.</span><span class="sxs-lookup"><span data-stu-id="071fd-128">It's recommended to enable Protected Event Logging, as described below, when using Script Block Logging for anything other than diagnostics purposes.</span></span>

<span data-ttu-id="071fd-129">Loggning av skript block kan aktive ras via grupprincip eller en register inställning.</span><span class="sxs-lookup"><span data-stu-id="071fd-129">Script Block Logging can be enabled via Group Policy or a registry setting.</span></span>

### <a name="using-group-policy"></a><span data-ttu-id="071fd-130">Använda grupprincip</span><span class="sxs-lookup"><span data-stu-id="071fd-130">Using Group Policy</span></span>

<span data-ttu-id="071fd-131">Aktivera automatisk avskrift genom att aktivera `Turn on PowerShell Script Block
Logging` funktionen i Grupprincip via `Administrative Templates -> Windows
Components -> Windows PowerShell` .</span><span class="sxs-lookup"><span data-stu-id="071fd-131">To enable automatic transcription, enable the `Turn on PowerShell Script Block
Logging` feature in Group Policy through `Administrative Templates -> Windows
Components -> Windows PowerShell`.</span></span>

### <a name="using-the-registry"></a><span data-ttu-id="071fd-132">Använda registret</span><span class="sxs-lookup"><span data-stu-id="071fd-132">Using the Registry</span></span>

<span data-ttu-id="071fd-133">Kör följande funktion:</span><span class="sxs-lookup"><span data-stu-id="071fd-133">Run the following function:</span></span>

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

## <a name="protected-event-logging"></a><span data-ttu-id="071fd-134">Skyddad händelse loggning</span><span class="sxs-lookup"><span data-stu-id="071fd-134">Protected Event Logging</span></span>

<span data-ttu-id="071fd-135">Att öka loggnings nivån på ett system ökar risken för att loggat innehåll kan innehålla känsliga data.</span><span class="sxs-lookup"><span data-stu-id="071fd-135">Increasing the level of logging on a system increases the possibility that logged content may contain sensitive data.</span></span> <span data-ttu-id="071fd-136">Med skript loggning aktive rad kan exempelvis autentiseringsuppgifter eller andra känsliga data som används av ett skript skrivas till händelse loggen.</span><span class="sxs-lookup"><span data-stu-id="071fd-136">For example, with script logging enabled, credentials or other sensitive data used by a script can be written to the event log.</span></span> <span data-ttu-id="071fd-137">När en dator som har loggat känsliga data komprometteras, kan loggarna tillhandahålla en angripare med information som behövs för att utöka sin räckvidd.</span><span class="sxs-lookup"><span data-stu-id="071fd-137">When a machine that has logged sensitive data is compromised, the logs can provide an attacker with information needed to extend their reach.</span></span>

<span data-ttu-id="071fd-138">För att skydda den här informationen introducerar Windows 10 skyddad händelse loggning.</span><span class="sxs-lookup"><span data-stu-id="071fd-138">To protect this information, Windows 10 introduces Protected Event Logging.</span></span>
<span data-ttu-id="071fd-139">Med skyddad händelse loggning kan deltagande program Kryptera känsliga data som skrivs till händelse loggen.</span><span class="sxs-lookup"><span data-stu-id="071fd-139">Protected Event Logging lets participating applications encrypt sensitive data written to the event log.</span></span> <span data-ttu-id="071fd-140">Senare kan du dekryptera och bearbeta dessa loggar på en säkrare och centraliserad logg insamlare.</span><span class="sxs-lookup"><span data-stu-id="071fd-140">Later, you can decrypt and process these logs on a more secure and centralized log collector.</span></span>

<span data-ttu-id="071fd-141">Innehållet i händelse loggen skyddas med hjälp av standard-CMS (Cryptographic Message Syntax) i IETF.</span><span class="sxs-lookup"><span data-stu-id="071fd-141">Event log content is protected using the IETF Cryptographic Message Syntax (CMS) standard.</span></span> <span data-ttu-id="071fd-142">CMS använder kryptering med offentlig nyckel.</span><span class="sxs-lookup"><span data-stu-id="071fd-142">CMS uses public key cryptography.</span></span> <span data-ttu-id="071fd-143">Nycklar som används för att kryptera innehåll och dekryptera innehåll hålls åtskilda.</span><span class="sxs-lookup"><span data-stu-id="071fd-143">The keys used to encrypt content and decrypt content are kept separate.</span></span>

<span data-ttu-id="071fd-144">Den offentliga nyckeln kan delas mycket och är inte känslig för data.</span><span class="sxs-lookup"><span data-stu-id="071fd-144">The public key can be shared widely and isn't sensitive data.</span></span> <span data-ttu-id="071fd-145">Allt innehåll som krypteras med den här offentliga nyckeln kan bara dekrypteras av den privata nyckeln.</span><span class="sxs-lookup"><span data-stu-id="071fd-145">Any content encrypted with this public key can only be decrypted by the private key.</span></span> <span data-ttu-id="071fd-146">Mer information om kryptering med offentliga nycklar finns i [Wikipedia-offentlig nyckel kryptering](https://en.wikipedia.org/wiki/Public-key_cryptography).</span><span class="sxs-lookup"><span data-stu-id="071fd-146">For more information about Public Key Cryptography, see [Wikipedia - Public Key Cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography).</span></span>

<span data-ttu-id="071fd-147">Om du vill aktivera en princip för en skyddad händelse loggning distribuerar du en offentlig nyckel till alla datorer som har händelse logg data som ska skyddas.</span><span class="sxs-lookup"><span data-stu-id="071fd-147">To enable a Protected Event Logging policy, deploy a public key to all machines that have event log data to protect.</span></span> <span data-ttu-id="071fd-148">Motsvarande privata nyckel används för att efter bearbetning av händelse loggarna på en säkrare plats, till exempel en central händelse logg insamlare eller [Siem][] Aggregator.</span><span class="sxs-lookup"><span data-stu-id="071fd-148">The corresponding private key is used to post-process the event logs at a more secure location such as a central event log collector, or [SIEM][] aggregator.</span></span> <span data-ttu-id="071fd-149">Du kan konfigurera SIEM i Azure.</span><span class="sxs-lookup"><span data-stu-id="071fd-149">You can set up SIEM in Azure.</span></span> <span data-ttu-id="071fd-150">Mer information finns i [allmän Siem-integrering](/cloud-app-security/siem).</span><span class="sxs-lookup"><span data-stu-id="071fd-150">For more information, see [Generic SIEM integration](/cloud-app-security/siem).</span></span>

### <a name="enabling-protected-event-logging-via-group-policy"></a><span data-ttu-id="071fd-151">Aktivera skyddad händelse loggning via grupprincip</span><span class="sxs-lookup"><span data-stu-id="071fd-151">Enabling Protected Event Logging via Group Policy</span></span>

<span data-ttu-id="071fd-152">Aktivera skyddad händelse loggning genom att aktivera `Enable Protected Event Logging` funktionen i Grupprincip via `Administrative Templates -> Windows Components
-> Event Logging` .</span><span class="sxs-lookup"><span data-stu-id="071fd-152">To enable Protected Event Logging, enable the `Enable Protected Event Logging` feature in Group Policy through `Administrative Templates -> Windows Components
-> Event Logging`.</span></span> <span data-ttu-id="071fd-153">Den här inställningen kräver ett krypterings certifikat, som du kan ange i ett av flera formulär:</span><span class="sxs-lookup"><span data-stu-id="071fd-153">This setting requires an encryption certificate, which you can provide in one of several forms:</span></span>

- <span data-ttu-id="071fd-154">Innehållet i ett Base-64-kodat X. 509-certifikat (till exempel som erbjuds av `Export` alternativet i certifikat hanteraren).</span><span class="sxs-lookup"><span data-stu-id="071fd-154">The content of a base-64 encoded X.509 certificate (for example, as offered by the `Export` option in Certificate Manager).</span></span>
- <span data-ttu-id="071fd-155">Tumavtrycket för ett certifikat som finns i den lokala datorns certifikat arkiv (kan distribueras av PKI-infrastrukturen).</span><span class="sxs-lookup"><span data-stu-id="071fd-155">The thumbprint of a certificate that can be found in the Local Machine certificate store (can be deployed by PKI infrastructure).</span></span>
- <span data-ttu-id="071fd-156">Den fullständiga sökvägen till ett certifikat (kan vara lokal eller en fjär resurs).</span><span class="sxs-lookup"><span data-stu-id="071fd-156">The full path to a certificate (can be local, or a remote share).</span></span>
- <span data-ttu-id="071fd-157">Sökvägen till en katalog som innehåller ett certifikat eller certifikat (kan vara lokalt eller en fjär resurs).</span><span class="sxs-lookup"><span data-stu-id="071fd-157">The path to a directory containing a certificate or certificates (can be local, or a remote share).</span></span>
- <span data-ttu-id="071fd-158">Ämnes namnet för ett certifikat som kan hittas i den lokala datorns certifikat arkiv (kan distribueras av PKI-infrastrukturen).</span><span class="sxs-lookup"><span data-stu-id="071fd-158">The subject name of a certificate that can be found in the Local Machine certificate store (can be deployed by PKI infrastructure).</span></span>

<span data-ttu-id="071fd-159">Det resulterande certifikatet måste ha `Document Encryption` som en förbättrad nyckel användning ( `1.3.6.1.4.1.311.80.1` ) och antingen `Data Encipherment` eller `Key
Encipherment` nyckel användningen aktiverade.</span><span class="sxs-lookup"><span data-stu-id="071fd-159">The resulting certificate must have `Document Encryption` as an enhanced key usage (`1.3.6.1.4.1.311.80.1`), and either `Data Encipherment` or `Key
Encipherment` key usages enabled.</span></span>

> [!WARNING]
> <span data-ttu-id="071fd-160">Den privata nyckeln bör inte distribueras till datorns loggnings händelser.</span><span class="sxs-lookup"><span data-stu-id="071fd-160">The private key shouldn't be deployed to the machines logging events.</span></span> <span data-ttu-id="071fd-161">Den bör behållas på en säker plats där du dekrypterar meddelandena.</span><span class="sxs-lookup"><span data-stu-id="071fd-161">It should be kept in a secure location where you decrypt the messages.</span></span>

### <a name="decrypting-protected-event-logging-messages"></a><span data-ttu-id="071fd-162">Dekryptera meddelanden om skyddade händelser</span><span class="sxs-lookup"><span data-stu-id="071fd-162">Decrypting Protected Event Logging messages</span></span>

<span data-ttu-id="071fd-163">Följande skript kommer att hämta och dekryptera, förutsatt att du har den privata nyckeln:</span><span class="sxs-lookup"><span data-stu-id="071fd-163">The following script will retrieve and decrypt, assuming that you have the private key:</span></span>

```powershell
Get-WinEvent Microsoft-Windows-PowerShell/Operational |
  Where-Object Id -eq 4104 | Unprotect-CmsMessage
```

## <a name="see-also"></a><span data-ttu-id="071fd-164">Se även</span><span class="sxs-lookup"><span data-stu-id="071fd-164">See also</span></span>

[<span data-ttu-id="071fd-165">PowerShell det blå teamet</span><span class="sxs-lookup"><span data-stu-id="071fd-165">PowerShell the Blue Team</span></span>](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)

[<span data-ttu-id="071fd-166">Allmän SIEM-integration</span><span class="sxs-lookup"><span data-stu-id="071fd-166">Generic SIEM integration</span></span>](/cloud-app-security/siem)

<!-- link references -->
[SIEM]: https://wikipedia.org/wiki/Security_information_and_event_management
