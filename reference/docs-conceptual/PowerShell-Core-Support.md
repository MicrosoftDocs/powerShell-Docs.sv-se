---
title: Supportlängd för PowerShell Core
description: Policyer som reglerar stöd för PowerShell Core
ms.date: 08/06/2018
ms.openlocfilehash: 2e0ca1b9c133e6f316a40aff13365d0489059165
ms.sourcegitcommit: 01ac77cd0b00e4e5e964504563a9212e8002e5e0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2018
ms.locfileid: "39587167"
---
# <a name="powershell-core-support-lifecycle"></a><span data-ttu-id="06cd3-103">Supportlängd för PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="06cd3-103">PowerShell Core Support Lifecycle</span></span>

<span data-ttu-id="06cd3-104">PowerShell Core är en specifik uppsättning verktyg och komponenter som har levererats, installeras och konfigureras separat från Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="06cd3-104">PowerShell Core is a distinct set of tools and components that is shipped, installed, and configured separately from Windows PowerShell.</span></span>
<span data-ttu-id="06cd3-105">PowerShell Core är därför inte ingår i Licensavtal för Windows 7/8.1/10 eller Windows Server.</span><span class="sxs-lookup"><span data-stu-id="06cd3-105">Therefore, PowerShell Core is not included in the Windows 7/8.1/10 or Windows Server licensing agreements.</span></span>

<span data-ttu-id="06cd3-106">PowerShell Core stöds dock under traditionella Microsoft support-avtal, inklusive [Premier][], [Microsoft Enterprise-avtal][enterprise-agreement], och [Microsoft Software Assurance][assurance].</span><span class="sxs-lookup"><span data-stu-id="06cd3-106">However, PowerShell Core is supported under traditional Microsoft support agreements, including [Premier][], [Microsoft Enterprise Agreements][enterprise-agreement], and [Microsoft Software Assurance][assurance].</span></span>
<span data-ttu-id="06cd3-107">Du kan också betala för [assisterad support för][] för PowerShell Core genom att skicka in en begäran om ditt problem.</span><span class="sxs-lookup"><span data-stu-id="06cd3-107">You can also pay for [assisted support][] for PowerShell Core by filing a support request for your problem.</span></span>

<span data-ttu-id="06cd3-108">Vi erbjuder också [Community-support][] på GitHub där du kan lagra ett problem, buggar eller funktionsförfrågan.</span><span class="sxs-lookup"><span data-stu-id="06cd3-108">We also offer [community support][] on GitHub where you can file an issue, bug, or feature request.</span></span>
<span data-ttu-id="06cd3-109">Alternativt kan du hitta hjälp från andra medlemmar i communityn på allmänna [Microsoft Community][] eller Microsoft [PowerShell-Tech-Community][].</span><span class="sxs-lookup"><span data-stu-id="06cd3-109">Alternatively, you may find help from other members of the community on the general [Microsoft Community][] or the Microsoft [PowerShell Tech Community][].</span></span>
<span data-ttu-id="06cd3-110">Vi erbjuder ingen garanti det att problemet ska åtgärdas eller löst i tid.</span><span class="sxs-lookup"><span data-stu-id="06cd3-110">We offer no guarantee there that your issue will be addressed or resolved in a timely manner.</span></span>
<span data-ttu-id="06cd3-111">Om du har ett problem som kräver omedelbar åtgärd, bör du använda den traditionella avgiftsbelagda supportalternativ.</span><span class="sxs-lookup"><span data-stu-id="06cd3-111">If you have a problem that requires immediate attention, you should use the traditional, paid support options.</span></span>

## <a name="lifecycle-of-powershell-core"></a><span data-ttu-id="06cd3-112">Livscykeln för PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="06cd3-112">Lifecycle of PowerShell Core</span></span>

<span data-ttu-id="06cd3-113">PowerShell Core inför den [Microsoft moderna livscykelpolicy][modern].</span><span class="sxs-lookup"><span data-stu-id="06cd3-113">PowerShell Core is adopting the [Microsoft Modern Lifecycle Policy][modern].</span></span>
<span data-ttu-id="06cd3-114">Den här supportlängd är avsedd att hålla kunder uppdaterade med de senaste versionerna.</span><span class="sxs-lookup"><span data-stu-id="06cd3-114">This support lifecycle is intended to keep customers up-to-date with the latest versions.</span></span>

<span data-ttu-id="06cd3-115">Den version 6.x-grenen av PowerShell Core kommer att uppdateras ungefär en gång var sjätte månad (t.ex. 6.0, 6.1, 6.2, osv.)</span><span class="sxs-lookup"><span data-stu-id="06cd3-115">The version 6.x branch of PowerShell Core will be updated approximately once every six months (e.g. 6.0, 6.1, 6.2, etc.)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="06cd3-116">Du måste uppdatera inom sex månader efter varje ny delversion viktig för att fortsätta att få support.</span><span class="sxs-lookup"><span data-stu-id="06cd3-116">You must update within six months after each new minor version release to continue receiving support.</span></span>

<span data-ttu-id="06cd3-117">Till exempel om PowerShell Core 6.1 släpps den 1 juli 2018 börjar är du förväntat att uppdatera till PowerShell Core 6.1 med den 1 januari 2019 att underhålla support.</span><span class="sxs-lookup"><span data-stu-id="06cd3-117">For example, if PowerShell Core 6.1 is released on July 1st, 2018, you would be expected to update to PowerShell Core 6.1 by January 1st, 2019 to maintain support.</span></span>

![PowerShell Core gren livscykel][lifecycle-chart]

<span data-ttu-id="06cd3-119">Moderna livscykelpolicy kräver också att Microsoft ge kunderna 12 månader meddelande innan avslutade stöd för en produkt (d.v.s. PowerShell Core).</span><span class="sxs-lookup"><span data-stu-id="06cd3-119">The Modern Lifecycle Policy also requires that Microsoft give customers 12 months notice before discontinuing support for a product (i.e. PowerShell Core).</span></span>

<span data-ttu-id="06cd3-120">Så småningom vi förväntar oss PowerShell Core antar att ”långsiktig Service” metod där vi kräver bara underhåll och säkerhet som uppdaterar vara i stöd på en viss gren/version av 6.x.</span><span class="sxs-lookup"><span data-stu-id="06cd3-120">Eventually, we expect PowerShell Core will adopt the "long-term servicing" approach where we would require only servicing and security updates to stay in support on a specific branch/version of 6.x.</span></span>

## <a name="supported-platforms"></a><span data-ttu-id="06cd3-121">Plattformar som stöds</span><span class="sxs-lookup"><span data-stu-id="06cd3-121">Supported platforms</span></span>

<span data-ttu-id="06cd3-122">Se följande tabell för att se vilken plattform som versionen av PowerShell Core som du använder stöds officiellt.</span><span class="sxs-lookup"><span data-stu-id="06cd3-122">Please see the following table to see what platform the version of PowerShell Core you are using is officially supported.</span></span>

<span data-ttu-id="06cd3-123">Paket för vissa plattformar också har bidragit med vår community, men de officiellt stöds inte.</span><span class="sxs-lookup"><span data-stu-id="06cd3-123">Our community has also contributed packages for some platforms, but they are not officially supported.</span></span>
<span data-ttu-id="06cd3-124">Dessa paket är märkta `Community` i tabellen.</span><span class="sxs-lookup"><span data-stu-id="06cd3-124">These packages are marked as `Community` in the table.</span></span>

<span data-ttu-id="06cd3-125">Plattformar som anges som `Experimental` inte stöds officiellt, men är tillgängliga för experimentering och feedback.</span><span class="sxs-lookup"><span data-stu-id="06cd3-125">Platforms listed as `Experimental` are not officially supported, but are available for experimentation and feedback.</span></span>

|                                                   | <span data-ttu-id="06cd3-126">6.0</span><span class="sxs-lookup"><span data-stu-id="06cd3-126">6.0</span></span>         | <span data-ttu-id="06cd3-127">6.1</span><span class="sxs-lookup"><span data-stu-id="06cd3-127">6.1</span></span>         |
|---------------------------------------------------|:-----------:|:-----------:|
| <span data-ttu-id="06cd3-128">Windows 7, 8.1 och 10</span><span class="sxs-lookup"><span data-stu-id="06cd3-128">Windows 7, 8.1, and 10</span></span>                            | <span data-ttu-id="06cd3-129">Stöds</span><span class="sxs-lookup"><span data-stu-id="06cd3-129">Supported</span></span>   | <span data-ttu-id="06cd3-130">Stöds</span><span class="sxs-lookup"><span data-stu-id="06cd3-130">Supported</span></span>   |
| <span data-ttu-id="06cd3-131">Windows Server 2008 R2, 2012 R2, 2016</span><span class="sxs-lookup"><span data-stu-id="06cd3-131">Windows Server 2008 R2, 2012 R2, 2016</span></span>             | <span data-ttu-id="06cd3-132">Stöds</span><span class="sxs-lookup"><span data-stu-id="06cd3-132">Supported</span></span>   | <span data-ttu-id="06cd3-133">Stöds</span><span class="sxs-lookup"><span data-stu-id="06cd3-133">Supported</span></span>   |
| <span data-ttu-id="06cd3-134">[Windows Server Halvårskanal][semi-annual]</span><span class="sxs-lookup"><span data-stu-id="06cd3-134">[Windows Server Semi-Annual Channel][semi-annual]</span></span> | <span data-ttu-id="06cd3-135">Stöds</span><span class="sxs-lookup"><span data-stu-id="06cd3-135">Supported</span></span>   | <span data-ttu-id="06cd3-136">Stöds</span><span class="sxs-lookup"><span data-stu-id="06cd3-136">Supported</span></span>   |
| <span data-ttu-id="06cd3-137">Ubuntu 14.04 och 16.04</span><span class="sxs-lookup"><span data-stu-id="06cd3-137">Ubuntu 14.04 and, 16.04</span></span>                           | <span data-ttu-id="06cd3-138">Stöds</span><span class="sxs-lookup"><span data-stu-id="06cd3-138">Supported</span></span>   | <span data-ttu-id="06cd3-139">Stöds</span><span class="sxs-lookup"><span data-stu-id="06cd3-139">Supported</span></span>   |
| <span data-ttu-id="06cd3-140">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="06cd3-140">Ubuntu 18.04</span></span>                                      |             | <span data-ttu-id="06cd3-141">Stöds</span><span class="sxs-lookup"><span data-stu-id="06cd3-141">Supported</span></span>   |
| <span data-ttu-id="06cd3-142">Ubuntu 18.10 (via Fäst paket)</span><span class="sxs-lookup"><span data-stu-id="06cd3-142">Ubuntu 18.10 (via Snap Package)</span></span>                   |             | <span data-ttu-id="06cd3-143">Community</span><span class="sxs-lookup"><span data-stu-id="06cd3-143">Community</span></span>   |
| <span data-ttu-id="06cd3-144">Debian 8.7 + och 9</span><span class="sxs-lookup"><span data-stu-id="06cd3-144">Debian 8.7+, and 9</span></span>                                | <span data-ttu-id="06cd3-145">Stöds</span><span class="sxs-lookup"><span data-stu-id="06cd3-145">Supported</span></span>   | <span data-ttu-id="06cd3-146">Stöds</span><span class="sxs-lookup"><span data-stu-id="06cd3-146">Supported</span></span>   |
| <span data-ttu-id="06cd3-147">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="06cd3-147">CentOS 7</span></span>                                          | <span data-ttu-id="06cd3-148">Stöds</span><span class="sxs-lookup"><span data-stu-id="06cd3-148">Supported</span></span>   | <span data-ttu-id="06cd3-149">Stöds</span><span class="sxs-lookup"><span data-stu-id="06cd3-149">Supported</span></span>   |
| <span data-ttu-id="06cd3-150">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="06cd3-150">Red Hat Enterprise Linux 7</span></span>                        | <span data-ttu-id="06cd3-151">Stöds</span><span class="sxs-lookup"><span data-stu-id="06cd3-151">Supported</span></span>   | <span data-ttu-id="06cd3-152">Stöds</span><span class="sxs-lookup"><span data-stu-id="06cd3-152">Supported</span></span>   |
| <span data-ttu-id="06cd3-153">OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="06cd3-153">OpenSUSE 42.3</span></span>                                     | <span data-ttu-id="06cd3-154">Stöds</span><span class="sxs-lookup"><span data-stu-id="06cd3-154">Supported</span></span>   | <span data-ttu-id="06cd3-155">Stöds</span><span class="sxs-lookup"><span data-stu-id="06cd3-155">Supported</span></span>   |
| <span data-ttu-id="06cd3-156">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="06cd3-156">Fedora 27</span></span>                                         | <span data-ttu-id="06cd3-157">Stöds</span><span class="sxs-lookup"><span data-stu-id="06cd3-157">Supported</span></span>   | <span data-ttu-id="06cd3-158">Stöds</span><span class="sxs-lookup"><span data-stu-id="06cd3-158">Supported</span></span>   |
| <span data-ttu-id="06cd3-159">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="06cd3-159">Fedora 28</span></span>                                         |             | <span data-ttu-id="06cd3-160">Stöds</span><span class="sxs-lookup"><span data-stu-id="06cd3-160">Supported</span></span>   |
| <span data-ttu-id="06cd3-161">macOS 10.12 +</span><span class="sxs-lookup"><span data-stu-id="06cd3-161">macOS 10.12+</span></span>                                      | <span data-ttu-id="06cd3-162">Stöds</span><span class="sxs-lookup"><span data-stu-id="06cd3-162">Supported</span></span>   | <span data-ttu-id="06cd3-163">Stöds</span><span class="sxs-lookup"><span data-stu-id="06cd3-163">Supported</span></span>   |
| <span data-ttu-id="06cd3-164">Arch</span><span class="sxs-lookup"><span data-stu-id="06cd3-164">Arch</span></span>                                              | <span data-ttu-id="06cd3-165">Community</span><span class="sxs-lookup"><span data-stu-id="06cd3-165">Community</span></span>   | <span data-ttu-id="06cd3-166">Community</span><span class="sxs-lookup"><span data-stu-id="06cd3-166">Community</span></span>   |
| <span data-ttu-id="06cd3-167">Raspbian</span><span class="sxs-lookup"><span data-stu-id="06cd3-167">Raspbian</span></span>                                          | <span data-ttu-id="06cd3-168">Experimentella</span><span class="sxs-lookup"><span data-stu-id="06cd3-168">Experimental</span></span>| <span data-ttu-id="06cd3-169">Community</span><span class="sxs-lookup"><span data-stu-id="06cd3-169">Community</span></span>   |
| <span data-ttu-id="06cd3-170">Kali</span><span class="sxs-lookup"><span data-stu-id="06cd3-170">Kali</span></span>                                              | <span data-ttu-id="06cd3-171">Community</span><span class="sxs-lookup"><span data-stu-id="06cd3-171">Community</span></span>   | <span data-ttu-id="06cd3-172">Community</span><span class="sxs-lookup"><span data-stu-id="06cd3-172">Community</span></span>   |
| <span data-ttu-id="06cd3-173">AppImage (fungerar på flera Linux-plattformar)</span><span class="sxs-lookup"><span data-stu-id="06cd3-173">AppImage  (works on multiple Linux platforms)</span></span>     | <span data-ttu-id="06cd3-174">Community</span><span class="sxs-lookup"><span data-stu-id="06cd3-174">Community</span></span>   | <span data-ttu-id="06cd3-175">Community</span><span class="sxs-lookup"><span data-stu-id="06cd3-175">Community</span></span>   |
| [<span data-ttu-id="06cd3-176">Fäst paket</span><span class="sxs-lookup"><span data-stu-id="06cd3-176">Snap Package</span></span>](https://snapcraft.io/powershell)   | <span data-ttu-id="06cd3-177">Se kommentar</span><span class="sxs-lookup"><span data-stu-id="06cd3-177">See note</span></span>    | <span data-ttu-id="06cd3-178">Se kommentar</span><span class="sxs-lookup"><span data-stu-id="06cd3-178">See note</span></span>    |

> [!NOTE]
> <span data-ttu-id="06cd3-179">Fäst paket kommer att experimentella under en period.</span><span class="sxs-lookup"><span data-stu-id="06cd3-179">Snap packages will be experimental for a period.</span></span>  <span data-ttu-id="06cd3-180">När du har är vi övertygade om att snapin inte innehåller några nya supportfrågor, support följer du kör paketet på distributionsplatsen.</span><span class="sxs-lookup"><span data-stu-id="06cd3-180">After, we are confident that Snap does not introduce new support issues, the support will follow the distribution you are running the package on.</span></span>

## <a name="platform-which-are-out-of-support"></a><span data-ttu-id="06cd3-181">Plattformen som inte längre stöds</span><span class="sxs-lookup"><span data-stu-id="06cd3-181">Platform which are out of support</span></span>

<span data-ttu-id="06cd3-182">När en plattformsversion når slutet på sin livscykel som definieras av plattform ägaren, PowerShell Core också att upphöra att ge stöd för den plattform-versionen.</span><span class="sxs-lookup"><span data-stu-id="06cd3-182">When a platform version reaches end-of-life as defined by the platform owner, PowerShell Core will also cease to provide support for that platform version.</span></span> <span data-ttu-id="06cd3-183">Tidigare uppdateringar paket förblir tillgängliga för kunder som behöver åtkomst utan formella support och kommer inte längre att förses uppdateringar av något slag.</span><span class="sxs-lookup"><span data-stu-id="06cd3-183">Previously released packages will remain available for customers needing access but formal support and updates of any kind will no longer be provided.</span></span>

<span data-ttu-id="06cd3-184">Därför stöd för följande versioner av ägare för distribution och stöds inte.</span><span class="sxs-lookup"><span data-stu-id="06cd3-184">Therefore, support for the following versions was ended by the distribution owners and are not supported.</span></span>

| <span data-ttu-id="06cd3-185">Operativsystem</span><span class="sxs-lookup"><span data-stu-id="06cd3-185">OS</span></span>       | <span data-ttu-id="06cd3-186">Version</span><span class="sxs-lookup"><span data-stu-id="06cd3-186">Version</span></span> | <span data-ttu-id="06cd3-187">Livscykelns slut</span><span class="sxs-lookup"><span data-stu-id="06cd3-187">End of Life</span></span>                                                                                 |
|----------|---------|---------------------------------------------------------------------------------------------|
| <span data-ttu-id="06cd3-188">Fedora</span><span class="sxs-lookup"><span data-stu-id="06cd3-188">Fedora</span></span>   | <span data-ttu-id="06cd3-189">24</span><span class="sxs-lookup"><span data-stu-id="06cd3-189">24</span></span>      | [<span data-ttu-id="06cd3-190">Augusti 2017</span><span class="sxs-lookup"><span data-stu-id="06cd3-190">August 2017</span></span>](https://fedoramagazine.org/fedora-24-eol/)                                    |
| <span data-ttu-id="06cd3-191">Fedora</span><span class="sxs-lookup"><span data-stu-id="06cd3-191">Fedora</span></span>   | <span data-ttu-id="06cd3-192">25</span><span class="sxs-lookup"><span data-stu-id="06cd3-192">25</span></span>      | [<span data-ttu-id="06cd3-193">December 2017</span><span class="sxs-lookup"><span data-stu-id="06cd3-193">December 2017</span></span>](https://fedoramagazine.org/fedora-25-end-life/)                             |
| <span data-ttu-id="06cd3-194">Fedora</span><span class="sxs-lookup"><span data-stu-id="06cd3-194">Fedora</span></span>   | <span data-ttu-id="06cd3-195">26</span><span class="sxs-lookup"><span data-stu-id="06cd3-195">26</span></span>      | [<span data-ttu-id="06cd3-196">Maj 2018</span><span class="sxs-lookup"><span data-stu-id="06cd3-196">May 2018</span></span>](https://fedoramagazine.org/fedora-26-end-life/)                                  |
| <span data-ttu-id="06cd3-197">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="06cd3-197">openSUSE</span></span> | <span data-ttu-id="06cd3-198">42.1</span><span class="sxs-lookup"><span data-stu-id="06cd3-198">42.1</span></span>    | [<span data-ttu-id="06cd3-199">Maj 2017</span><span class="sxs-lookup"><span data-stu-id="06cd3-199">May 2017</span></span>](https://lists.opensuse.org/opensuse-security-announce/2017-05/msg00053.html)     |
| <span data-ttu-id="06cd3-200">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="06cd3-200">openSUSE</span></span> | <span data-ttu-id="06cd3-201">42.2</span><span class="sxs-lookup"><span data-stu-id="06cd3-201">42.2</span></span>    | [<span data-ttu-id="06cd3-202">Januari 2018</span><span class="sxs-lookup"><span data-stu-id="06cd3-202">January 2018</span></span>](https://lists.opensuse.org/opensuse-security-announce/2017-11/msg00066.html) |
| <span data-ttu-id="06cd3-203">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="06cd3-203">Ubuntu</span></span>   | <span data-ttu-id="06cd3-204">16,10</span><span class="sxs-lookup"><span data-stu-id="06cd3-204">16.10</span></span>   | [<span data-ttu-id="06cd3-205">Juli 2017</span><span class="sxs-lookup"><span data-stu-id="06cd3-205">July 2017</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2017-July/000223.html)        |
| <span data-ttu-id="06cd3-206">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="06cd3-206">Ubuntu</span></span>   | <span data-ttu-id="06cd3-207">nr 17.04 från</span><span class="sxs-lookup"><span data-stu-id="06cd3-207">17.04</span></span>   | [<span data-ttu-id="06cd3-208">Januari 2018</span><span class="sxs-lookup"><span data-stu-id="06cd3-208">January 2018</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2018-January.txt)          |
| <span data-ttu-id="06cd3-209">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="06cd3-209">Ubuntu</span></span>   | <span data-ttu-id="06cd3-210">17.10</span><span class="sxs-lookup"><span data-stu-id="06cd3-210">17.10</span></span>   | [<span data-ttu-id="06cd3-211">Juli 2018</span><span class="sxs-lookup"><span data-stu-id="06cd3-211">July 2018</span></span>](https://lists.ubuntu.com/archives/ubuntu-announce/2018-July/000232.html)        |

## <a name="notes-on-licensing"></a><span data-ttu-id="06cd3-212">Anmärkningar om licensiering</span><span class="sxs-lookup"><span data-stu-id="06cd3-212">Notes on licensing</span></span>

<span data-ttu-id="06cd3-213">PowerShell Core är tillgängliga under den [MIT-licens][].</span><span class="sxs-lookup"><span data-stu-id="06cd3-213">PowerShell Core is released under the [MIT license][].</span></span>
<span data-ttu-id="06cd3-214">Under denna licens, och det inte finns i en betald support-avtal, användare är begränsade till [Community-support][].</span><span class="sxs-lookup"><span data-stu-id="06cd3-214">Under this license, and in the absence of a paid support agreement, users are limited to [community support][].</span></span>
<span data-ttu-id="06cd3-215">Med community-support kan Microsoft inte garantera svarstider eller korrigeringar.</span><span class="sxs-lookup"><span data-stu-id="06cd3-215">With community support, Microsoft makes no guarantees of responsiveness or fixes.</span></span>

## <a name="windows-powershell-module"></a><span data-ttu-id="06cd3-216">Windows PowerShell-modulen</span><span class="sxs-lookup"><span data-stu-id="06cd3-216">Windows PowerShell Module</span></span>

<span data-ttu-id="06cd3-217">Stöd för PowerShell Core förlängs inte till andra produkt-moduler om du inte uttryckligen PowerShell Core stöd för dessa moduler.</span><span class="sxs-lookup"><span data-stu-id="06cd3-217">Support for PowerShell Core does not extend to other product modules unless those modules explicitly support PowerShell Core.</span></span>
<span data-ttu-id="06cd3-218">Till exempel med hjälp av den `ActiveDirectory` -modulen som levereras som en del av Windows Server är ett scenario som inte stöds.</span><span class="sxs-lookup"><span data-stu-id="06cd3-218">For example, using the `ActiveDirectory` module that ships as part of Windows Server is an unsupported scenario.</span></span>

<span data-ttu-id="06cd3-219">Moduler som inte uttryckligen har stöd för PowerShell Core kan dock vara kompatibla i vissa fall.</span><span class="sxs-lookup"><span data-stu-id="06cd3-219">However, modules that do not explicitly support PowerShell Core may be compatible in some cases.</span></span>
<span data-ttu-id="06cd3-220">Genom att installera den [ `WindowsPSModulePath` ][] modulen, kan du lägga till Windows PowerShell `PSModulePath` till PowerShell Core `PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="06cd3-220">By installing the [`WindowsPSModulePath`][] module, you can append the Windows PowerShell `PSModulePath` to your PowerShell Core `PSModulePath`.</span></span>

<span data-ttu-id="06cd3-221">Installera först den `WindowsPSModulePath` modul från PowerShell-galleriet:</span><span class="sxs-lookup"><span data-stu-id="06cd3-221">First, install the `WindowsPSModulePath` module from the PowerShell Gallery:</span></span>

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin
Install-Module WindowsPSModulePath -Force
```

<span data-ttu-id="06cd3-222">När du har installerat den här modulen, kör den `Add-WindowsPSModulePath` cmdlet för att lägga till Windows PowerShell `PSModulePath` till PowerShell Core:</span><span class="sxs-lookup"><span data-stu-id="06cd3-222">After installing this module, run the `Add-WindowsPSModulePath` cmdlet to add the Windows PowerShell `PSModulePath` to PowerShell Core:</span></span>

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

[Premier]: https://www.microsoft.com/en-us/microsoftservices/support.aspx
[enterprise-agreement]: https://www.microsoft.com/en-us/licensing/licensing-programs/enterprise.aspx
[assurance]: https://www.microsoft.com/en-us/licensing/licensing-programs/software-assurance-default.aspx
[Community-support]: https://github.com/powershell/powershell/issues
[community support]: https://github.com/powershell/powershell/issues
[Microsoft Community]: https://answers.microsoft.com/
[PowerShell-Tech-Community]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[PowerShell Tech Community]: https://techcommunity.microsoft.com/t5/PowerShell/ct-p/WindowsPowerShell
[assisterad support för]: https://support.microsoft.com/assistedsupportproducts
[assisted support]: https://support.microsoft.com/assistedsupportproducts
[modern]: https://support.microsoft.com/help/30881/modern-lifecycle-policy
[lifecycle-chart]: ./images/modern-lifecycle.png
[semi-annual]: https://docs.microsoft.com/windows-server/get-started/semi-annual-channel-overview
[MIT-licens]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
[MIT license]: https://github.com/PowerShell/PowerShell/blob/master/LICENSE.txt
['WindowsPSModulePath']: https://www.powershellgallery.com/packages/WindowsPSModulePath/
[`WindowsPSModulePath`]: https://www.powershellgallery.com/packages/WindowsPSModulePath/
