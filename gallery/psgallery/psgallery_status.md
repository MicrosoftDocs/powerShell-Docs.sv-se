---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: galleriet, powershell, cmdlet, psgallery
title: psgallery_status
ms.openlocfilehash: 08d09ce83b5133598152186e12fc8ced90c36a88
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
<a name="powershell-gallery-status"></a>PowerShell-galleriet Status
=========================
## <a name="10102017---powershell-gallery-unavailable-for-2-hours-101017"></a>10/10/2017 - PowerShell-galleriet är inte tillgänglig i 2 timmar 10/10/17

__Sammanfattning av påverkan__: I PowerShell-galleriet orsakade en period av mycket hög latens, vilket resulterar i återkommande anslutningsproblem, från cirka 17: 00 (PDT) 10/10/17. När du har löst problemet har platsen kopplats från i 2 timmar från cirka 10 pm (PDT). Platsen återställdes strax innan midnatt 10/10/2017.

__Rotorsak__: håller fortfarande på att undersökas orsaken till hög fördröjning.

__Lösning__: webbtjänsterna var tvungen att vara offline och återställas för att lösa problem som primär.

__Nästa steg__: grundorsaken till det ursprungliga problemet undersöks.

## <a name="06012017---deploy-to-azure-automation-currently-unavailable"></a>2017-06/01 – distribuera till Azure Automation för närvarande inte tillgänglig

__Sammanfattning av påverkan__: distribuera objekt med beroenden till Azure Automation från PowerShell-galleriet är inte tillgänglig.  Importerar objekt från PowerShell-galleriet från i Azure Automation fortfarande är tillgänglig.

__Rotorsaken__: objekt som är beroende av andra och tidigare har distribuerats till Azure Automation kommer inte att distribueras till Azure Automation. Ingenjörer har hittat ett problem med hur ARM-mallar har genererats för artiklar med beroenden för distribution till Azure Automation-funktioner.

__Lösning__: tekniker som arbetar för att lösa problemet.  Den aktuella lösningen för användare är att importera objektet från PowerShell-galleriet från i Azure Automation.

__Nästa steg__: Engineers släpper korrigering inom kort.  Under tiden Använd rekommenderade lösningen.


## <a name="04112017---users-unable-to-log-in-with-azure-active-directory-aad-accounts"></a>11/04/2017 - användare kan inte logga in med Azure Active Directory (AAD)-konton

__Sammanfattning av påverkan__: vissa användare kunde inte logga in i PowerShell-galleriet med hjälp av Azure AD-konton.

__Rotorsaken__: en ändring av inställning uppfylldes under en uppdatering säkrare interagerar med AAD.
Tester för att verifiera ändringen innehöll inte vissa typer av AAD-konton så fortsatte i distributionen.

__Lösning__: Engineers identifieras inställningen som saknas och åtgärda problemet.

__Nästa steg__: vi ska ändra våra tester för att inkludera en bredare uppsättning AAD kontotyper.

## <a name="03272017---resolved-unable-to-see-individual-module-and-script-pages"></a>2017-03/27 - löst: Det gick inte att visa enskilda sidor för modulen och skript

__Sammanfattning av påverkan__: Dirigera länkar till enskilda sidor för modulen och skript på https://www.powershellgallery.com bröts. Detta har rapporterats i alla regioner. Det inte att påverka PowerShellGet cmdlets ie., installera modulen installationsskriptet, Update-Module-skript för att uppdatera, publicera-modulen, publicera-Scirpt fortsätter att fungera.

__Rotorsak__: Engineers identifieras orsaken som ett problem med att samla in sociala medier knappar som Facebook till sidan.

__Lösning__: Engineers problemet genom att inaktivera Facebook antalsinformation.

__Nästa steg__: vi öppnas ett internt spårning problem för att åtgärda vår användning av Facebook-API.

## <a name="12152016---unable-to-send-emails-via-powershellgallery-website"></a>2016/12/15 - det går inte att skicka e-post via PowerShellGallery webbplats

__Sammanfattning av påverkan__: mellan 2016/12/13 och 2016/12/15 alla meddelanden som skickas via kontakta ägare, hantera ägare, kontakta Support eller rapportera missbruk har inte tagits emot av PowerShell-galleriet administratörer.
__Rotorsak__: Engineers identifieras orsaken som autentiseringsproblem med SMTP-servern.
__Lösning__: Engineers kunde lösa problemet för autentisering och återställa anslutningen till SMTP-servern.
__Nästa steg__: Om du använde kontakta ägare, hantera ägare, kontakta Support eller rapportera missbruk länkar för att skicka e-post till cgadmin@microsoft.com under denna tid och vi har inte svarat, försök igen. Vi ber om ursäkt för besväret.



## <a name="8102016---resolved-unable-to-send-emails-to-cgadminmicrosoftcom"></a>8/10/2016 - löst: Det gick inte att skicka e-postmeddelanden cgadmin@microsoft.com

__Sammanfattning av påverkan__: mellan 2016-8-5 och 2016-8-10 kunder kunde inte skicka e-postmeddelanden cgadmin@microsoft.com, eller använda funktionen Kontakta oss.
__Rotorsak__: Engineers identifieras orsaken som en konfigurationsändring av e-postkonto.
__Lösning__: Engineers arbetat för att lösa problemet konfiguration.
__Nästa steg__: Om du har använt länken Kontakta oss eller skickas e-post till cgadmin@microsoft.com under denna tid och vi har inte svarat, försök igen. Tack för ditt tålamod.



## <a name="7132016---download-items-failed"></a>7/13/2016 - hämta objekt misslyckades

__Sammanfattning av påverkan__: mellan 2016-7-11 och 2016/7/13 en delmängd av kunder stötte på problem som hämtar objekt från PowerShell-galleriet. Problemet förmodligen är manifesterad i följande felmeddelande returnerades från Install-modulen /-installationsskriptet och spara-modul eller spara-skript:

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

__Preliminär grundorsaken__: Engineers hittat ett problem med Azure innehåll leverera innehållsleveransnätverk (CDN), som har distribuerats till PowerShell-galleriet på 2016-7-11.
__Minskning__: Engineers inaktiverad Azure CDN i PowerShell-galleriet.
__Nästa steg__: Utforska underliggande rotorsaken och utveckla en lösning för att förhindra framtida förekomster.


## <a name="5192016---download-items-failed"></a>5/19/2016 - hämta objekt misslyckades
__Sammanfattning av påverkan__: mellan 2016-17-5 och 5/19/2016 en delmängd av kunder stötte på problem som hämtar objekt från PowerShell-galleriet. Problemet förmodligen är manifesterad i följande felmeddelande returnerades från Install-modulen /-installationsskriptet och spara-modul eller spara-skript:

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

__Preliminär grundorsaken__: Engineers identifierat ett avbrott i den underliggande providern i Azure Content leverera innehållsleveransnätverk (CDN), som har distribuerats till PowerShell-galleriet på 2016-5-17.
__Minskning__: Engineers inaktiverad Azure CDN i PowerShell-galleriet.
__Nästa steg__: Utforska underliggande rotorsaken och utveckla en lösning för att förhindra framtida förekomster.