---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: galleriet, powershell, cmdlet, psgallery
title: psgalleryint_status
ms.openlocfilehash: 0b2f1ebcb365fcd24438a028a9c8181449266a8b
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
<a name="powershell-gallery-status"></a><span data-ttu-id="0d1a9-103">PowerShell-galleriet Status</span><span class="sxs-lookup"><span data-stu-id="0d1a9-103">PowerShell Gallery Status</span></span>
=========================

## <a name="03272017---resolved-unable-to-see-individual-module-and-script-pages"></a><span data-ttu-id="0d1a9-104">2017-03/27 - löst: Det gick inte att visa enskilda sidor för modulen och skript</span><span class="sxs-lookup"><span data-stu-id="0d1a9-104">03/27/2017 - RESOLVED: Unable to see individual module and script pages</span></span>

<span data-ttu-id="0d1a9-105">__Sammanfattning av påverkan__: Dirigera länkar till modulen och skript på enskilda sidor https://www.powershellgallery.com bröts.</span><span class="sxs-lookup"><span data-stu-id="0d1a9-105">__Summary of Impact__: Direct links to individual module and script pages on https://www.powershellgallery.com were broken.</span></span> <span data-ttu-id="0d1a9-106">Detta har rapporterats i alla regioner.</span><span class="sxs-lookup"><span data-stu-id="0d1a9-106">This was being reported across all the regions.</span></span> <span data-ttu-id="0d1a9-107">Det inte att påverka PowerShellGet cmdlets ie., installera modulen installationsskriptet, Update-Module-skript för att uppdatera, publicera-modulen, publicera-skript fortsätter att fungera.</span><span class="sxs-lookup"><span data-stu-id="0d1a9-107">This did not impact any of the PowerShellGet cmdlets ie., Install-Module, Install-Script, Update-Module, Update-Script, Publish-Module, Publish-Script continued to work.</span></span>

<span data-ttu-id="0d1a9-108">__Rotorsak__: Engineers identifieras orsaken som ett problem med att samla in sociala medier knappar som Facebook till sidan.</span><span class="sxs-lookup"><span data-stu-id="0d1a9-108">__Root Cause__: Engineers identified the cause as an issue bringing up social media buttons like Facebook onto the page.</span></span>  

<span data-ttu-id="0d1a9-109">__Lösning__: Engineers problemet genom att inaktivera Facebook antalsinformation.</span><span class="sxs-lookup"><span data-stu-id="0d1a9-109">__Resolution__: Engineers fixed the problem by disabling the Facebook count information.</span></span>

<span data-ttu-id="0d1a9-110">__Nästa steg__: vi öppnas ett internt spårning problem för att åtgärda vår användning av Facebook-API.</span><span class="sxs-lookup"><span data-stu-id="0d1a9-110">__Next Steps__: We opened an internal tracking issue to fix our usage of Facebook API.</span></span>

## <a name="12152016---unable-to-send-emails-via-powershellgallery-website"></a><span data-ttu-id="0d1a9-111">2016/12/15 - det går inte att skicka e-post via PowerShellGallery webbplats</span><span class="sxs-lookup"><span data-stu-id="0d1a9-111">12/15/2016 - Unable to send emails via PowerShellGallery website</span></span>

<span data-ttu-id="0d1a9-112">__Sammanfattning av påverkan__: mellan 2016/12/13 och 2016/12/15 alla meddelanden som skickas via kontakta ägare, hantera ägare, kontakta Support eller rapportera missbruk har inte tagits emot av PowerShell-galleriet administratörer.</span><span class="sxs-lookup"><span data-stu-id="0d1a9-112">__Summary of Impact__: Between 12/13/2016 and 12/15/2016, any messages sent via Contact Owners, Manage Owners, Contact Support, or Report Abuse were not received by the PowerShell Gallery Administrators.</span></span>  
<span data-ttu-id="0d1a9-113">__Rotorsak__: Engineers identifieras orsaken som autentiseringsproblem med SMTP-servern.</span><span class="sxs-lookup"><span data-stu-id="0d1a9-113">__Root Cause__: Engineers identified the cause as an authentication issue with the SMTP server.</span></span>  
<span data-ttu-id="0d1a9-114">__Lösning__: Engineers kunde lösa problemet för autentisering och återställa anslutningen till SMTP-servern.</span><span class="sxs-lookup"><span data-stu-id="0d1a9-114">__Resolution__: Engineers were able to resolve the authentication issue and restore connection to the SMTP server.</span></span>  
<span data-ttu-id="0d1a9-115">__Nästa steg__: Om du använde kontakta ägare, hantera ägare, kontakta Support eller rapportera missbruk länkar för att skicka e-post till cgadmin@microsoft.com under denna tid och vi har inte svarat, försök igen.</span><span class="sxs-lookup"><span data-stu-id="0d1a9-115">__Next Steps__: If you used the Contact Owners, Manage Owners, Contact Support, or Report Abuse links to send mail to cgadmin@microsoft.com during this time and we have not responded, please try again.</span></span> <span data-ttu-id="0d1a9-116">Vi ber om ursäkt för besväret.</span><span class="sxs-lookup"><span data-stu-id="0d1a9-116">We apologize for the inconvenience.</span></span>   


## <a name="8102016---resolved-unable-to-send-emails-to-cgadminmicrosoftcom"></a><span data-ttu-id="0d1a9-117">8/10/2016 - löst: Det gick inte att skicka e-postmeddelandencgadmin@microsoft.com</span><span class="sxs-lookup"><span data-stu-id="0d1a9-117">8/10/2016 - Resolved: Unable to send emails to cgadmin@microsoft.com</span></span>
<span data-ttu-id="0d1a9-118">__Sammanfattning av påverkan__: mellan 2016-8-5 och 2016-8-10 kunder kunde inte skicka e-postmeddelanden cgadmin@microsoft.com, eller använda funktionen Kontakta oss.</span><span class="sxs-lookup"><span data-stu-id="0d1a9-118">__Summary of Impact__: Between 8/5/2016 and 8/10/2016, customers were unable to send emails to cgadmin@microsoft.com, or use the Contact Us feature.</span></span>  
<span data-ttu-id="0d1a9-119">__Rotorsak__: Engineers identifieras orsaken som en konfigurationsändring av e-postkonto.</span><span class="sxs-lookup"><span data-stu-id="0d1a9-119">__Root Cause__: Engineers identified the cause as a configuration change of the email account.</span></span>  
<span data-ttu-id="0d1a9-120">__Lösning__: Engineers arbetat för att lösa problemet konfiguration.</span><span class="sxs-lookup"><span data-stu-id="0d1a9-120">__Resolution__: Engineers worked to resolve the configuration issue.</span></span>  
<span data-ttu-id="0d1a9-121">__Nästa steg__: Om du har använt länken Kontakta oss eller skickas e-post till cgadmin@microsoft.com under denna tid och vi har inte svarat, försök igen.</span><span class="sxs-lookup"><span data-stu-id="0d1a9-121">__Next Steps__: If you used the Contact Us link or sent mail to cgadmin@microsoft.com during this time and we have not responded, please try again.</span></span> <span data-ttu-id="0d1a9-122">Tack för ditt tålamod.</span><span class="sxs-lookup"><span data-stu-id="0d1a9-122">Thank you for your patience.</span></span>


