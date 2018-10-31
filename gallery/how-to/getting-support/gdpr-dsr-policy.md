---
ms.date: 03/27/2018
contributor: JKeithB
keywords: galleriet, powershell, psgallery, GDPR
title: PowerShell-galleriet GDPR-kompatibilitet
ms.openlocfilehash: fb1191d8a1cd12d5994e41238c384eb504d0c261
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/25/2018
ms.locfileid: "50002658"
---
# <a name="powershell-gallery-gdpr-compliance"></a><span data-ttu-id="bb8a1-103">PowerShell-galleriet GDPR-kompatibilitet</span><span class="sxs-lookup"><span data-stu-id="bb8a1-103">PowerShell Gallery GDPR compliance</span></span>

## <a name="overview"></a><span data-ttu-id="bb8a1-104">Översikt</span><span class="sxs-lookup"><span data-stu-id="bb8a1-104">Overview</span></span>

<span data-ttu-id="bb8a1-105">En europeisk lag är den allmänna Dataskyddsförordningen GDPR (Data Protection), tog gälla i maj 2018.</span><span class="sxs-lookup"><span data-stu-id="bb8a1-105">In May 2018, a European privacy law, the General Data Protection Regulation (GDPR), took effect.</span></span>
<span data-ttu-id="bb8a1-106">Dataskyddsförordningen inför nya regler på företag, myndigheter, ideella och andra organisationer att erbjudandet varor och tjänster till personer i Europeiska unionen (EU) eller att samla in och analysera data som EU invånare.</span><span class="sxs-lookup"><span data-stu-id="bb8a1-106">The GDPR imposes new rules on companies, government agencies, non-profits, and other organizations that offer goods and services to people in the European Union (EU), or that collect and analyze data tied to EU residents.</span></span>
<span data-ttu-id="bb8a1-107">Dataskyddsförordningen gäller oavsett var du befinner dig.</span><span class="sxs-lookup"><span data-stu-id="bb8a1-107">The GDPR applies no matter where you are located.</span></span>

> [!NOTE]
> <span data-ttu-id="bb8a1-108">Den här artikeln innehåller anvisningar att ta bort personliga data från PowerShell-galleriet och kan användas för att stödja dina skyldigheter enligt GDPR.</span><span class="sxs-lookup"><span data-stu-id="bb8a1-108">This article provides steps for how to delete personal data from the PowerShell Gallery and can be used to support your obligations under the GDPR.</span></span> <span data-ttu-id="bb8a1-109">Om du letar efter allmän information om GDPR finns i den [GDPR-delen av den Service Trust portalen](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted).</span><span class="sxs-lookup"><span data-stu-id="bb8a1-109">If you’re looking for general info about GDPR, see the [GDPR section of the Service Trust portal](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted).</span></span>

## <a name="personally-identifiable-data"></a><span data-ttu-id="bb8a1-110">Personligt identifierbar information</span><span class="sxs-lookup"><span data-stu-id="bb8a1-110">Personally identifiable data</span></span>

<span data-ttu-id="bb8a1-111">PowerShell-galleriet lagrar följande information som tillhandahålls av användare, som kan innehålla personlig information:</span><span class="sxs-lookup"><span data-stu-id="bb8a1-111">The PowerShell Gallery stores the following information that may be provided by users, which may contain personal information:</span></span>

- <span data-ttu-id="bb8a1-112">PowerShell-galleriet konto</span><span class="sxs-lookup"><span data-stu-id="bb8a1-112">PowerShell Gallery account</span></span>
- <span data-ttu-id="bb8a1-113">Paket som publicerats i PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="bb8a1-113">Packages published to the PowerShell Gallery</span></span>
- <span data-ttu-id="bb8a1-114">E-postkommunikation med PowerShell-galleriet-teamet</span><span class="sxs-lookup"><span data-stu-id="bb8a1-114">Email correspondence with the PowerShell Gallery team</span></span>

<span data-ttu-id="bb8a1-115">De flesta användare skapa inte ett konto med PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="bb8a1-115">Most users do not create a PowerShell Gallery account.</span></span>
<span data-ttu-id="bb8a1-116">Ett konto krävs inte om du ska publicera ett paket eller funktionen ”kontakta ägare” i PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="bb8a1-116">An account is not required unless you are going to publish a package or use the "Contact Owner" feature in the PowerShell Gallery.</span></span>
<span data-ttu-id="bb8a1-117">Förutom e-postkommunikation initieras av användaren, lagrar inte PowerShell-galleriet personligt identifierbar information för användare som inte har skapat ett konto.</span><span class="sxs-lookup"><span data-stu-id="bb8a1-117">Other than email correspondence initiated by the user, the PowerShell Gallery does not store personally identifiable data for users who have not created an account.</span></span>

<span data-ttu-id="bb8a1-118">Användare som skapar ett konto med PowerShell-galleriet kan publicera paket PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="bb8a1-118">Users who create a PowerShell Gallery account can publish packages to the PowerShell Gallery.</span></span>
<span data-ttu-id="bb8a1-119">Dessa paket förväntas vara PowerShell-kod, men kan innehålla andra information inklusive personlig information.</span><span class="sxs-lookup"><span data-stu-id="bb8a1-119">Those packages are expected to be PowerShell code, but may contain other information including personal information.</span></span>
<span data-ttu-id="bb8a1-120">Informationen nedan visar hur du kan hämta alla paket du har publicerat PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="bb8a1-120">The information below will show how you can get all the packages you have published to the PowerShell Gallery.</span></span>

## <a name="dsr-export-of-powershell-gallery-data"></a><span data-ttu-id="bb8a1-121">DSR-Export av Data för PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="bb8a1-121">DSR Export of PowerShell Gallery Data</span></span>

<span data-ttu-id="bb8a1-122">I följande avsnitt beskrivs hur PowerShell-galleriet stöder DSR-begäranden (DSR) genom att förklara hur du exporterar information som lagras i PowerShell-galleriet och hur du begär borttagning av den här informationen.</span><span class="sxs-lookup"><span data-stu-id="bb8a1-122">The following sections describe how the PowerShell Gallery supports data subject requests (DSR), by explaining how to export information stored in the PowerShell Gallery, and how to request deletion of this information.</span></span>

### <a name="email"></a><span data-ttu-id="bb8a1-123">E-post</span><span class="sxs-lookup"><span data-stu-id="bb8a1-123">Email</span></span>

<span data-ttu-id="bb8a1-124">E-postkommunikation kan vara något av följande:</span><span class="sxs-lookup"><span data-stu-id="bb8a1-124">Email correspondence may include any of the following:</span></span>

- <span data-ttu-id="bb8a1-125">E-postmeddelande skickas till innehavare av PowerShell-galleriet paket om kod analysen söker igenom har upptäckt ett problem med alla paket som de har publicerats i PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="bb8a1-125">Email sent to the owners of PowerShell Gallery packages if the code analysis scans detected an issue with any package they have published to the PowerShell Gallery</span></span>
- <span data-ttu-id="bb8a1-126">E-post som skickas av vem som helst till PowerShell-galleriet teamet med den e-postadressen på sidan ”Kontakta oss” [cgadmin@microsoft.com](mailto:cgadmin@microsoft.com)</span><span class="sxs-lookup"><span data-stu-id="bb8a1-126">Email sent by anyone to the PowerShell Gallery team using the email address in the "Contact Us" page [cgadmin@microsoft.com](mailto:cgadmin@microsoft.com)</span></span>
- <span data-ttu-id="bb8a1-127">Registrerad användare som använder funktionen ”kontakta ägare” i PowerShell-galleriet för att skicka e-postmeddelande till ägaren av ett paket i PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="bb8a1-127">Registered users who use the "Contact Owner" feature in the PowerShell Gallery to send email to the owner of a package in the PowerShell Gallery</span></span>

<span data-ttu-id="bb8a1-128">E-postmeddelanden som skickas av eller PowerShell-galleriet har en bevarandeprincip 90 dagar för att stödja säkerhetsrisker undersökningar bör skadlig kod identifieras på PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="bb8a1-128">Emails sent by or to the PowerShell Gallery have a retention policy of 90 days to support possible security investigations should malicious code be discovered on the PowerShell Gallery.</span></span>
<span data-ttu-id="bb8a1-129">E-postmeddelanden tas bort av Grupprincip efter 90 dagar.</span><span class="sxs-lookup"><span data-stu-id="bb8a1-129">Emails are deleted by policy after 90 days.</span></span>

<span data-ttu-id="bb8a1-130">Du kan begära kopior av alla e-postmeddelanden skickas till eller från din e-postadress och PowerShell-galleriet inom de senaste 90 dagarna.</span><span class="sxs-lookup"><span data-stu-id="bb8a1-130">You may request copies of all emails sent to or from your email address and the PowerShell Gallery within the previous 90 days.</span></span>
<span data-ttu-id="bb8a1-131">Om du vill begära det här postkommunikation, skicka ett e- [ cgadmin@microsoft.com ](mailto:cgadmin@microsoft.com), med rubriken: ”DSR-begäran för e-postmeddelanden som är relaterade till det här kontot”.</span><span class="sxs-lookup"><span data-stu-id="bb8a1-131">To request this correspondence, send an email to [cgadmin@microsoft.com](mailto:cgadmin@microsoft.com), with the title: "DSR Request for emails relating to this account".</span></span>
<span data-ttu-id="bb8a1-132">Ange vilken information som du begär i meddelandets brödtext (till exempel: skicka alla e-postmeddelanden skickas till eller tas emot från den här e-postadress.) Alla e-postmeddelanden som rör din e-postadress inom 90 dagar från förfrågan skickas inom 7 affärsdagar.</span><span class="sxs-lookup"><span data-stu-id="bb8a1-132">In the body of the message, state what information you are requesting (for example: Please send all emails sent to or received from this email address.) All emails involving your email address within 90 days of the request will be sent within 7 business days.</span></span>

### <a name="powershell-gallery-account-information"></a><span data-ttu-id="bb8a1-133">Information om PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="bb8a1-133">PowerShell Gallery Account Information</span></span>

<span data-ttu-id="bb8a1-134">Om du har skapat ett konto med PowerShell-galleriet hittar du all personlig information som har lagrats i PowerShell-galleriet genom att utföra följande steg:</span><span class="sxs-lookup"><span data-stu-id="bb8a1-134">If you have created a PowerShell Gallery account, you can find all personal information that has been stored in PowerShell Gallery by taking the following steps:</span></span>

1. <span data-ttu-id="bb8a1-135">Logga in på PowerShell-galleriet och sedan klicka på ditt användarnamn</span><span class="sxs-lookup"><span data-stu-id="bb8a1-135">Sign in to the PowerShell Gallery, then click on your username</span></span>
2. <span data-ttu-id="bb8a1-136">Nästa sida som visas är sidan som visar e-postadressen används för PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="bb8a1-136">The next page displayed is the Account page, which shows the email address used for the PowerShell Gallery account</span></span>

<span data-ttu-id="bb8a1-137">Om du har skapat fler än ett konto i PowerShell-galleriet, måste du upprepa dessa steg för varje konto.</span><span class="sxs-lookup"><span data-stu-id="bb8a1-137">If you have created more than one account in the PowerShell Gallery, you will need to repeat these steps for each account.</span></span>

### <a name="packages-in-the-powershell-gallery"></a><span data-ttu-id="bb8a1-138">Paket i PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="bb8a1-138">Packages in the PowerShell Gallery</span></span>

<span data-ttu-id="bb8a1-139">För att underlätta exporterar paket som publicerats i PowerShell-galleriet, har vi publicerat skriptet ”GetPSGalleryItemsForAuthor” PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="bb8a1-139">To facilitate exporting packages published to the PowerShell Gallery, we have published the script "GetPSGalleryItemsForAuthor" to the PowerShell Gallery.</span></span>
<span data-ttu-id="bb8a1-140">Det här skriptet exporterar en kopia av varje version av varje paket placerar i PowerShell-galleriet baserat på informationen för författare som lagras i paketet.</span><span class="sxs-lookup"><span data-stu-id="bb8a1-140">This script exports a copy of every version of every package put into the PowerShell Gallery based on the author information stored in the package.</span></span>

> [!NOTE]
> <span data-ttu-id="bb8a1-141">Författaren lagras i Paketmanifestet när du publicerar ditt paket.</span><span class="sxs-lookup"><span data-stu-id="bb8a1-141">The Author is stored in the package manifest when you publish your package.</span></span>
> <span data-ttu-id="bb8a1-142">Det finns ingen garanti att författaren är samma identitet som det konto som används i PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="bb8a1-142">There is no guarantee that the Author is the same identity as the account you use in the PowerShell Gallery.</span></span>
> <span data-ttu-id="bb8a1-143">Om du använder ett annat värde i fältet Författare, måste du ange detta värde när du använder det här skriptet.</span><span class="sxs-lookup"><span data-stu-id="bb8a1-143">If you use some other value in the Author field, you will need to supply that value when using this script.</span></span>

<span data-ttu-id="bb8a1-144">Du kan ladda ned skriptet med hjälp av följande PowerShell-kommando:</span><span class="sxs-lookup"><span data-stu-id="bb8a1-144">You may download the script by using the following PowerShell command:</span></span>

```powershell
Save-Script Get-repository psgallery
```

<span data-ttu-id="bb8a1-145">Du kan sedan köra skriptet direkt, genom att köra följande PowerShell-kommandon:</span><span class="sxs-lookup"><span data-stu-id="bb8a1-145">You can then run the script directly, by running the following PowerShell commands:</span></span>

```powershell
# cd <local folder location>
.\GetPSGalleryItemsForAuthor.ps1
```

<span data-ttu-id="bb8a1-146">Du uppmanas att ange författaren och en mapp på datorn där du vill att de paket som ska sparas.</span><span class="sxs-lookup"><span data-stu-id="bb8a1-146">You will be prompted to supply the Author and a folder on your system where you want the packages to be saved.</span></span>

## <a name="deleting-personal-data-from-the-powershell-gallery"></a><span data-ttu-id="bb8a1-147">Ta bort personliga Data från PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="bb8a1-147">Deleting Personal Data From The PowerShell Gallery</span></span>

<span data-ttu-id="bb8a1-148">Om du vill ta bort ditt konto med PowerShell-galleriet eller alla paket som du äger i PowerShell-galleriet, skicka e-postmeddelande till cgadmin@microsoft.com med rubriken: ”GDPR-begäran för artiklar som är relaterade till det här kontot”.</span><span class="sxs-lookup"><span data-stu-id="bb8a1-148">To delete your PowerShell Gallery account or any package you own in the PowerShell Gallery, send email to cgadmin@microsoft.com with the title: "GDPR Request for items relating to this account".</span></span>
<span data-ttu-id="bb8a1-149">Ange vilken information som du vill ta bort i brödtexten i meddelandet.</span><span class="sxs-lookup"><span data-stu-id="bb8a1-149">In the body of the message state what information you want deleted.</span></span> <span data-ttu-id="bb8a1-150">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="bb8a1-150">For example:</span></span>

- <span data-ttu-id="bb8a1-151">Ta bort version x.y.z för min paketet ”namn”</span><span class="sxs-lookup"><span data-stu-id="bb8a1-151">Please delete version x.y.z of my package "package name"</span></span>
- <span data-ttu-id="bb8a1-152">Ta bort alla versioner av Mina paket ”namn”</span><span class="sxs-lookup"><span data-stu-id="bb8a1-152">Please delete all versions of my package "package name"</span></span>
- <span data-ttu-id="bb8a1-153">Ta bort mitt konto för PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="bb8a1-153">Please delete my PowerShell Gallery account</span></span>

<span data-ttu-id="bb8a1-154">PowerShell-galleriet administratörer kommer att svara inom 7 affärsdagar.</span><span class="sxs-lookup"><span data-stu-id="bb8a1-154">The PowerShell Gallery administrators will reply within 7 business days.</span></span>
<span data-ttu-id="bb8a1-155">De paket som angetts tas bort inom 30 dagar efter att begäran har skickats.</span><span class="sxs-lookup"><span data-stu-id="bb8a1-155">The packages specified will be deleted within 30 days after the request is sent.</span></span>
