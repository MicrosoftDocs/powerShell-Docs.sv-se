---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: galleriet, powershell, cmdlet, psgallery
title: psgallery_status
ms.openlocfilehash: af6111d3c511273571bd978c6d0e7447726c2917
ms.sourcegitcommit: f069ff0689006fece768f178c10e3e3eeaee09f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2017
---
<a name="powershell-gallery-status"></a><span data-ttu-id="34bb2-103">PowerShell-galleriet Status</span><span class="sxs-lookup"><span data-stu-id="34bb2-103">PowerShell Gallery Status</span></span>
=========================
## <a name="10102017---powershell-gallery-unavailable-for-2-hours-101017"></a><span data-ttu-id="34bb2-104">10/10/2017 - PowerShell-galleriet är inte tillgänglig i 2 timmar 10/10/17</span><span class="sxs-lookup"><span data-stu-id="34bb2-104">10/10/2017 - PowerShell Gallery unavailable for 2 hours 10/10/17</span></span>

<span data-ttu-id="34bb2-105">__Sammanfattning av påverkan__: I PowerShell-galleriet orsakade en period av mycket hög latens, vilket resulterar i återkommande anslutningsproblem, från cirka 17: 00 (PDT) 10/10/17.</span><span class="sxs-lookup"><span data-stu-id="34bb2-105">__Summary of Impact__: The PowerShell Gallery experienced a period of very high latency, resulting in intermittent connection issues, beginning approximately 5pm (PDT) 10/10/17.</span></span> <span data-ttu-id="34bb2-106">När du har löst problemet har platsen kopplats från i 2 timmar från cirka 10 pm (PDT).</span><span class="sxs-lookup"><span data-stu-id="34bb2-106">While resolving the issue, the site was taken offline for 2 hours starting approximately 10pm (PDT).</span></span> <span data-ttu-id="34bb2-107">Platsen återställdes strax innan midnatt 10/10/2017.</span><span class="sxs-lookup"><span data-stu-id="34bb2-107">The site was restored shortly before midnight 10/10/2017.</span></span> 
 
<span data-ttu-id="34bb2-108">__Rotorsak__: håller fortfarande på att undersökas orsaken till hög fördröjning.</span><span class="sxs-lookup"><span data-stu-id="34bb2-108">__Root Cause__: The root cause of the high latency is still being investigated.</span></span>

<span data-ttu-id="34bb2-109">__Lösning__: webbtjänsterna var tvungen att vara offline och återställas för att lösa problem som primär.</span><span class="sxs-lookup"><span data-stu-id="34bb2-109">__Resolution__: The web services had to be taken offline and restored in order to address the primary issue.</span></span> 

<span data-ttu-id="34bb2-110">__Nästa steg__: grundorsaken till det ursprungliga problemet undersöks.</span><span class="sxs-lookup"><span data-stu-id="34bb2-110">__Next Steps__: The root cause for the original issue is being investigated.</span></span>

## <a name="06012017---deploy-to-azure-automation-currently-unavailable"></a><span data-ttu-id="34bb2-111">2017-06/01 – distribuera till Azure Automation för närvarande inte tillgänglig</span><span class="sxs-lookup"><span data-stu-id="34bb2-111">06/01/2017 - Deploy to Azure Automation Currently Unavailable</span></span>

<span data-ttu-id="34bb2-112">__Sammanfattning av påverkan__: distribuera objekt med beroenden till Azure Automation från PowerShell-galleriet är inte tillgänglig.</span><span class="sxs-lookup"><span data-stu-id="34bb2-112">__Summary of Impact__: Deploying items with dependencies to Azure Automation from the PowerShell Gallery is currently unavailable.</span></span>  <span data-ttu-id="34bb2-113">Importerar objekt från PowerShell-galleriet från i Azure Automation fortfarande är tillgänglig.</span><span class="sxs-lookup"><span data-stu-id="34bb2-113">Importing items from the PowerShell Gallery from inside Azure Automation is still available.</span></span>  
 
<span data-ttu-id="34bb2-114">__Rotorsaken__: objekt som är beroende av andra och tidigare har distribuerats till Azure Automation kommer inte att distribueras till Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="34bb2-114">__Root Cause__: Items that have dependencies on others, and have been previously deployed to Azure Automation, will not be deployed to Azure Automation.</span></span> <span data-ttu-id="34bb2-115">Ingenjörer har hittat ett problem med hur ARM-mallar har genererats för artiklar med beroenden för distribution till Azure Automation-funktioner.</span><span class="sxs-lookup"><span data-stu-id="34bb2-115">Engineers have identified an issue with how ARM templates are generated for items with dependencies for the Deploy to Azure Automation functionality.</span></span>

<span data-ttu-id="34bb2-116">__Lösning__: tekniker som arbetar för att lösa problemet.</span><span class="sxs-lookup"><span data-stu-id="34bb2-116">__Resolution__: Engineers are working to resolve issue.</span></span>  <span data-ttu-id="34bb2-117">Den aktuella lösningen för användare är att importera objektet från PowerShell-galleriet från i Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="34bb2-117">The current workaround for users is to import the item from the PowerShell Gallery from inside Azure Automation.</span></span> 

<span data-ttu-id="34bb2-118">__Nästa steg__: Engineers släpper korrigering inom kort.</span><span class="sxs-lookup"><span data-stu-id="34bb2-118">__Next Steps__: Engineers will release the fix shortly.</span></span>  <span data-ttu-id="34bb2-119">Under tiden Använd rekommenderade lösningen.</span><span class="sxs-lookup"><span data-stu-id="34bb2-119">In the meantime, please use the recommended workaround.</span></span> 


## <a name="04112017---users-unable-to-log-in-with-azure-active-directory-aad-accounts"></a><span data-ttu-id="34bb2-120">11/04/2017 - användare kan inte logga in med Azure Active Directory (AAD)-konton</span><span class="sxs-lookup"><span data-stu-id="34bb2-120">04/11/2017 - Users unable to log in with Azure Active Directory (AAD) accounts</span></span>

<span data-ttu-id="34bb2-121">__Sammanfattning av påverkan__: vissa användare kunde inte logga in i PowerShell-galleriet med hjälp av Azure AD-konton.</span><span class="sxs-lookup"><span data-stu-id="34bb2-121">__Summary of Impact__: Some users were unable to log in to the PowerShell Gallery using Azure AD Accounts.</span></span> 
 
<span data-ttu-id="34bb2-122">__Rotorsaken__: en ändring av inställning uppfylldes under en uppdatering säkrare interagerar med AAD.</span><span class="sxs-lookup"><span data-stu-id="34bb2-122">__Root Cause__: During an update to interact more securely with AAD, a setting change was missed.</span></span> <span data-ttu-id="34bb2-123">Tester för att verifiera ändringen innehöll inte vissa typer av AAD-konton så fortsatte i distributionen.</span><span class="sxs-lookup"><span data-stu-id="34bb2-123">The testing done to validate the change did not include certain types of AAD accounts, so the deployment proceeded.</span></span>

<span data-ttu-id="34bb2-124">__Lösning__: Engineers identifieras inställningen som saknas och åtgärda problemet.</span><span class="sxs-lookup"><span data-stu-id="34bb2-124">__Resolution__: Engineers identified the missing setting and corrected the problem.</span></span> 

<span data-ttu-id="34bb2-125">__Nästa steg__: vi ska ändra våra tester för att inkludera en bredare uppsättning AAD kontotyper.</span><span class="sxs-lookup"><span data-stu-id="34bb2-125">__Next Steps__: We will be modifying our testing to include a broader set of AAD account types.</span></span>

## <a name="03272017---resolved-unable-to-see-individual-module-and-script-pages"></a><span data-ttu-id="34bb2-126">2017-03/27 - löst: Det gick inte att visa enskilda sidor för modulen och skript</span><span class="sxs-lookup"><span data-stu-id="34bb2-126">03/27/2017 - RESOLVED: Unable to see individual module and script pages</span></span>

<span data-ttu-id="34bb2-127">__Sammanfattning av påverkan__: Dirigera länkar till modulen och skript på enskilda sidor https://www.powershellgallery.com bröts.</span><span class="sxs-lookup"><span data-stu-id="34bb2-127">__Summary of Impact__: Direct links to individual module and script pages on https://www.powershellgallery.com were broken.</span></span> <span data-ttu-id="34bb2-128">Detta har rapporterats i alla regioner.</span><span class="sxs-lookup"><span data-stu-id="34bb2-128">This was being reported across all the regions.</span></span> <span data-ttu-id="34bb2-129">Det inte att påverka PowerShellGet cmdlets ie., installera modulen installationsskriptet, Update-Module-skript för att uppdatera, publicera-modulen, publicera-Scirpt fortsätter att fungera.</span><span class="sxs-lookup"><span data-stu-id="34bb2-129">This did not impact any of the PowerShellGet cmdlets ie., Install-Module, Install-Script, Update-Module, Update-Script, Publish-Module, Publish-Scirpt continued to work.</span></span>

<span data-ttu-id="34bb2-130">__Rotorsak__: Engineers identifieras orsaken som ett problem med att samla in sociala medier knappar som Facebook till sidan.</span><span class="sxs-lookup"><span data-stu-id="34bb2-130">__Root Cause__: Engineers identified the cause as an issue bringing up social media buttons like Facebook onto the page.</span></span>  

<span data-ttu-id="34bb2-131">__Lösning__: Engineers problemet genom att inaktivera Facebook antalsinformation.</span><span class="sxs-lookup"><span data-stu-id="34bb2-131">__Resolution__: Engineers fixed the problem by disabling the Facebook count information.</span></span>

<span data-ttu-id="34bb2-132">__Nästa steg__: vi öppnas ett internt spårning problem för att åtgärda vår användning av Facebook-API.</span><span class="sxs-lookup"><span data-stu-id="34bb2-132">__Next Steps__: We opened an internal tracking issue to fix our usage of Facebook API.</span></span>

## <a name="12152016---unable-to-send-emails-via-powershellgallery-website"></a><span data-ttu-id="34bb2-133">2016/12/15 - det går inte att skicka e-post via PowerShellGallery webbplats</span><span class="sxs-lookup"><span data-stu-id="34bb2-133">12/15/2016 - Unable to send emails via PowerShellGallery website</span></span>

<span data-ttu-id="34bb2-134">__Sammanfattning av påverkan__: mellan 2016/12/13 och 2016/12/15 alla meddelanden som skickas via kontakta ägare, hantera ägare, kontakta Support eller rapportera missbruk har inte tagits emot av PowerShell-galleriet administratörer.</span><span class="sxs-lookup"><span data-stu-id="34bb2-134">__Summary of Impact__: Between 12/13/2016 and 12/15/2016, any messages sent via Contact Owners, Manage Owners, Contact Support, or Report Abuse were not received by the PowerShell Gallery Administrators.</span></span>  
<span data-ttu-id="34bb2-135">__Rotorsak__: Engineers identifieras orsaken som autentiseringsproblem med SMTP-servern.</span><span class="sxs-lookup"><span data-stu-id="34bb2-135">__Root Cause__: Engineers identified the cause as an authentication issue with the SMTP server.</span></span>  
<span data-ttu-id="34bb2-136">__Lösning__: Engineers kunde lösa problemet för autentisering och återställa anslutningen till SMTP-servern.</span><span class="sxs-lookup"><span data-stu-id="34bb2-136">__Resolution__: Engineers were able to resolve the authentication issue and restore connection to the SMTP server.</span></span>  
<span data-ttu-id="34bb2-137">__Nästa steg__: Om du använde kontakta ägare, hantera ägare, kontakta Support eller rapportera missbruk länkar för att skicka e-post till cgadmin@microsoft.com under denna tid och vi har inte svarat, försök igen.</span><span class="sxs-lookup"><span data-stu-id="34bb2-137">__Next Steps__: If you used the Contact Owners, Manage Owners, Contact Support, or Report Abuse links to send mail to cgadmin@microsoft.com during this time and we have not responded, please try again.</span></span> <span data-ttu-id="34bb2-138">Vi ber om ursäkt för besväret.</span><span class="sxs-lookup"><span data-stu-id="34bb2-138">We apologize for the inconvenience.</span></span>  



## <a name="8102016---resolved-unable-to-send-emails-to-cgadminmicrosoftcom"></a><span data-ttu-id="34bb2-139">8/10/2016 - löst: Det gick inte att skicka e-postmeddelandencgadmin@microsoft.com</span><span class="sxs-lookup"><span data-stu-id="34bb2-139">8/10/2016 - Resolved: Unable to send emails to cgadmin@microsoft.com</span></span>

<span data-ttu-id="34bb2-140">__Sammanfattning av påverkan__: mellan 2016-8-5 och 2016-8-10 kunder kunde inte skicka e-postmeddelanden cgadmin@microsoft.com, eller använda funktionen Kontakta oss.</span><span class="sxs-lookup"><span data-stu-id="34bb2-140">__Summary of Impact__: Between 8/5/2016 and 8/10/2016, customers were unable to send emails to cgadmin@microsoft.com, or use the Contact Us feature.</span></span>  
<span data-ttu-id="34bb2-141">__Rotorsak__: Engineers identifieras orsaken som en konfigurationsändring av e-postkonto.</span><span class="sxs-lookup"><span data-stu-id="34bb2-141">__Root Cause__: Engineers identified the cause as a configuration change of the email account.</span></span>  
<span data-ttu-id="34bb2-142">__Lösning__: Engineers arbetat för att lösa problemet konfiguration.</span><span class="sxs-lookup"><span data-stu-id="34bb2-142">__Resolution__: Engineers worked to resolve the configuration issue.</span></span>  
<span data-ttu-id="34bb2-143">__Nästa steg__: Om du har använt länken Kontakta oss eller skickas e-post till cgadmin@microsoft.com under denna tid och vi har inte svarat, försök igen.</span><span class="sxs-lookup"><span data-stu-id="34bb2-143">__Next Steps__: If you used the Contact Us link or sent mail to cgadmin@microsoft.com during this time and we have not responded, please try again.</span></span> <span data-ttu-id="34bb2-144">Tack för ditt tålamod.</span><span class="sxs-lookup"><span data-stu-id="34bb2-144">Thank you for your patience.</span></span>



## <a name="7132016---download-items-failed"></a><span data-ttu-id="34bb2-145">7/13/2016 - hämta objekt misslyckades</span><span class="sxs-lookup"><span data-stu-id="34bb2-145">7/13/2016 - Download Items Failed</span></span>

<span data-ttu-id="34bb2-146">__Sammanfattning av påverkan__: mellan 2016-7-11 och 2016/7/13 en delmängd av kunder stötte på problem som hämtar objekt från PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="34bb2-146">__Summary of Impact__: Between 7/11/2016 and 7/13/2016, a subset of customers experienced issues downloading items from the PowerShell Gallery.</span></span> <span data-ttu-id="34bb2-147">Problemet förmodligen är manifesterad i följande felmeddelande returnerades från Install-modulen /-installationsskriptet och spara-modul eller spara-skript:</span><span class="sxs-lookup"><span data-stu-id="34bb2-147">The issue likely manifested itself in the following error message returned from Install-Module/Install-Script and Save-Module/Save-Script:</span></span>

```powershell
PS C:\> Install-Module xStorage 
PackageManagement\Install-Package : Package 'xStorage' failed to be installed because: 
End of Central Directory record could not be found. At C:\Program 
Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PSModule.psm1:1375 char:21 + ... 
$null = PackageManagement\Install-Package @PSBoundParameters + 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ + CategoryInfo : InvalidResult: 
(xStorage:String) [Install-Package], Exception + FullyQualifiedErrorId : Package '{0}' 
failed to be installed because: {1},Microsoft.PowerShell.PackageManagement.Cmdlets.InstallPackage 
```

<span data-ttu-id="34bb2-148">__Preliminär grundorsaken__: Engineers hittat ett problem med Azure innehåll leverera innehållsleveransnätverk (CDN), som har distribuerats till PowerShell-galleriet på 2016-7-11.</span><span class="sxs-lookup"><span data-stu-id="34bb2-148">__Preliminary root cause__: Engineers identified an issue with Azure Content Deliver Network (CDN), which was deployed to the PowerShell Gallery on 7/11/2016.</span></span>  
<span data-ttu-id="34bb2-149">__Minskning__: Engineers inaktiverad Azure CDN i PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="34bb2-149">__Mitigation__: Engineers disabled Azure CDN in the PowerShell Gallery.</span></span>  
<span data-ttu-id="34bb2-150">__Nästa steg__: Utforska underliggande rotorsaken och utveckla en lösning för att förhindra framtida förekomster.</span><span class="sxs-lookup"><span data-stu-id="34bb2-150">__Next Steps__: Investigate the underlying root cause and developing a solution to prevent future occurrences.</span></span>


## <a name="5192016---download-items-failed"></a><span data-ttu-id="34bb2-151">5/19/2016 - hämta objekt misslyckades</span><span class="sxs-lookup"><span data-stu-id="34bb2-151">5/19/2016 - Download Items Failed</span></span>
<span data-ttu-id="34bb2-152">__Sammanfattning av påverkan__: mellan 2016-17-5 och 5/19/2016 en delmängd av kunder stötte på problem som hämtar objekt från PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="34bb2-152">__Summary of Impact__: Between 5/17/2016 and 5/19/2016, a subset of customers experienced issues downloading items from the PowerShell Gallery.</span></span> <span data-ttu-id="34bb2-153">Problemet förmodligen är manifesterad i följande felmeddelande returnerades från Install-modulen /-installationsskriptet och spara-modul eller spara-skript:</span><span class="sxs-lookup"><span data-stu-id="34bb2-153">The issue likely manifested itself in the following error message returned from Install-Module/Install-Script and Save-Module/Save-Script:</span></span>

```powershell
VERBOSE: Hash for package 'AzureRM.OperationalInsights' does not match hash provided from the server.
VERBOSE: InstallPackageLocal' - name='AzureRM.OperationalInsights', version='1.0.8',
destination='C:\Users\jbritt\AppData\Local\Temp\2\1741355729'
WARNING: Package 'AzureRM.OperationalInsights' failed to be installed because: 
End of Central Directory record could not be found. 
WARNING: Dependent Package 'AzureRM.OperationalInsights' failed to install. 
WARNING: Package 'AzureRM' failed to install. 
VERBOSE: Module 'AzureRM.Network' was saved successfully. 
VERBOSE: Saving the dependency module 'AzureRM.NotificationHubs' with version '1.0.8' for the 
module 'AzureRM'. 
VERBOSE: Module 'AzureRM.NotificationHubs' was saved successfully. 
PackageManagement\Save-Package : Unable to save the module 'AzureRM'. At C:\Program 
Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PSModule.psm1:1187 char:21 + 
$null = PackageManagement\Save-Package @PSBoundParameters + 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ + 
CategoryInfo : InvalidOperation: (Microsoft.Power...ets.SavePackage:SavePackage) 
[Save-Package], Exception + FullyQualifiedErrorId : ProviderFailToDownloadFile,
Microsoft.PowerShell.PackageManagement.Cmdlets.SavePackage 
```

<span data-ttu-id="34bb2-154">__Preliminär grundorsaken__: Engineers identifierat ett avbrott i den underliggande providern i Azure Content leverera innehållsleveransnätverk (CDN), som har distribuerats till PowerShell-galleriet på 2016-5-17.</span><span class="sxs-lookup"><span data-stu-id="34bb2-154">__Preliminary root cause__: Engineers identified an outage in the underlying provider of Azure Content Deliver Network (CDN), which was deployed to the PowerShell Gallery on 5/17/2016.</span></span>  
<span data-ttu-id="34bb2-155">__Minskning__: Engineers inaktiverad Azure CDN i PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="34bb2-155">__Mitigation__: Engineers disabled Azure CDN in the PowerShell Gallery.</span></span>  
<span data-ttu-id="34bb2-156">__Nästa steg__: Utforska underliggande rotorsaken och utveckla en lösning för att förhindra framtida förekomster.</span><span class="sxs-lookup"><span data-stu-id="34bb2-156">__Next Steps__: Investigate the underlying root cause and developing a solution to prevent future occurrences.</span></span>

