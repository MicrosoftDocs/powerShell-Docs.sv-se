---
ms.date: 03/27/2018
title: PowerShell-galleriet GDPR-kompatibilitet
description: Den här artikeln förklarar hur du tar bort personliga data från PowerShell-galleriet och kan användas för att stödja dina skyldigheter enligt GDPR.
ms.openlocfilehash: bd2537f48367a9b6ee3a9d70380b1f32d0a1a651
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92661140"
---
# <a name="powershell-gallery-gdpr-compliance"></a><span data-ttu-id="a8bb1-103">PowerShell-galleriet GDPR-kompatibilitet</span><span class="sxs-lookup"><span data-stu-id="a8bb1-103">PowerShell Gallery GDPR compliance</span></span>

## <a name="overview"></a><span data-ttu-id="a8bb1-104">Översikt</span><span class="sxs-lookup"><span data-stu-id="a8bb1-104">Overview</span></span>

<span data-ttu-id="a8bb1-105">I maj 2018 trädde en europeisk sekretess lagstiftning, allmän dataskyddsförordning (GDPR).</span><span class="sxs-lookup"><span data-stu-id="a8bb1-105">In May 2018, a European privacy law, the General Data Protection Regulation (GDPR), took effect.</span></span> <span data-ttu-id="a8bb1-106">GDPR ålägger nya regler för företag, myndigheter, ideella organisationer och andra organisationer som tillhandahåller varor och tjänster till personer i EU, eller som samlar in och analyserar data som är kopplade till EU-invånare.</span><span class="sxs-lookup"><span data-stu-id="a8bb1-106">The GDPR imposes new rules on companies, government agencies, non-profits, and other organizations that offer goods and services to people in the European Union (EU), or that collect and analyze data tied to EU residents.</span></span> <span data-ttu-id="a8bb1-107">GDPR gäller oavsett var organisationen har sin verksamhet.</span><span class="sxs-lookup"><span data-stu-id="a8bb1-107">The GDPR applies no matter where you are located.</span></span>

> [!NOTE]
> <span data-ttu-id="a8bb1-108">Den här artikeln innehåller anvisningar för hur du tar bort personliga data från PowerShell-galleriet och kan användas för att stödja dina skyldigheter enligt GDPR.</span><span class="sxs-lookup"><span data-stu-id="a8bb1-108">This article provides steps for how to delete personal data from the PowerShell Gallery and can be used to support your obligations under the GDPR.</span></span> <span data-ttu-id="a8bb1-109">Om du letar efter allmän information om GDPR finns den i [GDPR-avsnittet i Service Trust-portalen](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted).</span><span class="sxs-lookup"><span data-stu-id="a8bb1-109">If you're looking for general info about GDPR, see the [GDPR section of the Service Trust portal](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted).</span></span>

## <a name="personally-identifiable-data"></a><span data-ttu-id="a8bb1-110">Personligt identifierbara data</span><span class="sxs-lookup"><span data-stu-id="a8bb1-110">Personally identifiable data</span></span>

<span data-ttu-id="a8bb1-111">PowerShell-galleriet lagrar följande information som kan tillhandahållas av användare, som kan innehålla personlig information:</span><span class="sxs-lookup"><span data-stu-id="a8bb1-111">The PowerShell Gallery stores the following information that may be provided by users, which may contain personal information:</span></span>

- <span data-ttu-id="a8bb1-112">PowerShell-galleriet konto</span><span class="sxs-lookup"><span data-stu-id="a8bb1-112">PowerShell Gallery account</span></span>
- <span data-ttu-id="a8bb1-113">Paket som publicerats till PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="a8bb1-113">Packages published to the PowerShell Gallery</span></span>
- <span data-ttu-id="a8bb1-114">E-postkorrespondens med PowerShell-galleriet-teamet</span><span class="sxs-lookup"><span data-stu-id="a8bb1-114">Email correspondence with the PowerShell Gallery team</span></span>

<span data-ttu-id="a8bb1-115">De flesta användare skapar inget PowerShell-galleriet-konto.</span><span class="sxs-lookup"><span data-stu-id="a8bb1-115">Most users do not create a PowerShell Gallery account.</span></span> <span data-ttu-id="a8bb1-116">Det krävs inget konto om du inte ska publicera ett paket eller använda funktionen "kontakta ägare" i PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="a8bb1-116">An account is not required unless you are going to publish a package or use the "Contact Owner" feature in the PowerShell Gallery.</span></span> <span data-ttu-id="a8bb1-117">Förutom e-postkorrespondens som initierats av användaren, lagrar PowerShell-galleriet inte personligt identifierbar information för användare som inte har skapat något konto.</span><span class="sxs-lookup"><span data-stu-id="a8bb1-117">Other than email correspondence initiated by the user, the PowerShell Gallery does not store personally identifiable data for users who have not created an account.</span></span>

<span data-ttu-id="a8bb1-118">Användare som skapar ett PowerShell-galleriet konto kan publicera paket till PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="a8bb1-118">Users who create a PowerShell Gallery account can publish packages to the PowerShell Gallery.</span></span> <span data-ttu-id="a8bb1-119">Dessa paket förväntas vara PowerShell-kod, men kan innehålla annan information, inklusive personlig information.</span><span class="sxs-lookup"><span data-stu-id="a8bb1-119">Those packages are expected to be PowerShell code, but may contain other information including personal information.</span></span> <span data-ttu-id="a8bb1-120">Informationen nedan visar hur du kan hämta alla paket som du har publicerat i PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="a8bb1-120">The information below will show how you can get all the packages you have published to the PowerShell Gallery.</span></span>

## <a name="dsr-export-of-powershell-gallery-data"></a><span data-ttu-id="a8bb1-121">DSR-export av PowerShell-galleriet data</span><span class="sxs-lookup"><span data-stu-id="a8bb1-121">DSR Export of PowerShell Gallery Data</span></span>

<span data-ttu-id="a8bb1-122">I följande avsnitt beskrivs hur PowerShell-galleriet stöder DSR (data subject requests) genom att förklara hur du exporterar information som lagras i PowerShell-galleriet och hur du begär borttagning av den här informationen.</span><span class="sxs-lookup"><span data-stu-id="a8bb1-122">The following sections describe how the PowerShell Gallery supports data subject requests (DSR), by explaining how to export information stored in the PowerShell Gallery, and how to request deletion of this information.</span></span>

### <a name="email"></a><span data-ttu-id="a8bb1-123">E-post</span><span class="sxs-lookup"><span data-stu-id="a8bb1-123">Email</span></span>

<span data-ttu-id="a8bb1-124">E-postkorrespondens kan vara något av följande:</span><span class="sxs-lookup"><span data-stu-id="a8bb1-124">Email correspondence may include any of the following:</span></span>

- <span data-ttu-id="a8bb1-125">E-post som skickas till ägare av PowerShell-galleriet-paket om kod analysen upptäcker ett problem med ett paket som de har publicerat till PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="a8bb1-125">Email sent to the owners of PowerShell Gallery packages if the code analysis scans detected an issue with any package they have published to the PowerShell Gallery</span></span>
- <span data-ttu-id="a8bb1-126">E-post som skickas av någon till PowerShell-galleriets teamet med hjälp av e-postadressen på sidan kontakta oss [cgadmin@microsoft.com](mailto:cgadmin@microsoft.com)</span><span class="sxs-lookup"><span data-stu-id="a8bb1-126">Email sent by anyone to the PowerShell Gallery team using the email address in the "Contact Us" page [cgadmin@microsoft.com](mailto:cgadmin@microsoft.com)</span></span>
- <span data-ttu-id="a8bb1-127">Registrerade användare som använder funktionen "kontakta ägare" i PowerShell-galleriet för att skicka e-post till ägaren av ett paket i PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="a8bb1-127">Registered users who use the "Contact Owner" feature in the PowerShell Gallery to send email to the owner of a package in the PowerShell Gallery</span></span>

<span data-ttu-id="a8bb1-128">E-postmeddelanden som skickas av eller till PowerShell-galleriet har en bevarande princip på 90 dagar för att stödja möjliga säkerhets undersökningar bör skadlig kod identifieras på PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="a8bb1-128">Emails sent by or to the PowerShell Gallery have a retention policy of 90 days to support possible security investigations should malicious code be discovered on the PowerShell Gallery.</span></span> <span data-ttu-id="a8bb1-129">E-postmeddelanden tas bort av en princip efter 90 dagar.</span><span class="sxs-lookup"><span data-stu-id="a8bb1-129">Emails are deleted by policy after 90 days.</span></span>

<span data-ttu-id="a8bb1-130">Du kan begära kopior av alla e-postmeddelanden som skickas till eller från din e-postadress och PowerShell-galleriet inom de föregående 90 dagarna.</span><span class="sxs-lookup"><span data-stu-id="a8bb1-130">You may request copies of all emails sent to or from your email address and the PowerShell Gallery within the previous 90 days.</span></span> <span data-ttu-id="a8bb1-131">Skicka ett e-postmeddelande till [cgadmin@microsoft.com](mailto:cgadmin@microsoft.com) , med rubriken: "DSR-begäran om e-post som är relaterad till det här kontot", för att begära denna korrespondens.</span><span class="sxs-lookup"><span data-stu-id="a8bb1-131">To request this correspondence, send an email to [cgadmin@microsoft.com](mailto:cgadmin@microsoft.com), with the title: "DSR Request for emails relating to this account".</span></span> <span data-ttu-id="a8bb1-132">Ange vilken information du begär i meddelandets brödtext (till exempel: skicka alla e-postmeddelanden som skickas till eller tas emot från den här e-postadressen.) Alla e-postmeddelanden som involverar din e-postadress inom 90 dagar från det att begäran skickas inom 7 arbets dagar.</span><span class="sxs-lookup"><span data-stu-id="a8bb1-132">In the body of the message, state what information you are requesting (for example: Please send all emails sent to or received from this email address.) All emails involving your email address within 90 days of the request will be sent within 7 business days.</span></span>

### <a name="powershell-gallery-account-information"></a><span data-ttu-id="a8bb1-133">PowerShell-galleriet konto information</span><span class="sxs-lookup"><span data-stu-id="a8bb1-133">PowerShell Gallery Account Information</span></span>

<span data-ttu-id="a8bb1-134">Om du har skapat ett PowerShell-galleriet konto kan du hitta all personlig information som har lagrats i PowerShell-galleriet genom att utföra följande steg:</span><span class="sxs-lookup"><span data-stu-id="a8bb1-134">If you have created a PowerShell Gallery account, you can find all personal information that has been stored in PowerShell Gallery by taking the following steps:</span></span>

1. <span data-ttu-id="a8bb1-135">Logga in på PowerShell-galleriet och klicka sedan på ditt användar namn</span><span class="sxs-lookup"><span data-stu-id="a8bb1-135">Sign in to the PowerShell Gallery, then click on your username</span></span>
2. <span data-ttu-id="a8bb1-136">Nästa sida som visas är konto sidan som visar den e-postadress som används för det PowerShell-galleriet kontot</span><span class="sxs-lookup"><span data-stu-id="a8bb1-136">The next page displayed is the Account page, which shows the email address used for the PowerShell Gallery account</span></span>

<span data-ttu-id="a8bb1-137">Om du har skapat fler än ett konto i PowerShell-galleriet måste du upprepa de här stegen för varje konto.</span><span class="sxs-lookup"><span data-stu-id="a8bb1-137">If you have created more than one account in the PowerShell Gallery, you will need to repeat these steps for each account.</span></span>

### <a name="packages-in-the-powershell-gallery"></a><span data-ttu-id="a8bb1-138">Paket i PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="a8bb1-138">Packages in the PowerShell Gallery</span></span>

<span data-ttu-id="a8bb1-139">För att under lätta exporten av paket som publiceras till PowerShell-galleriet har vi publicerat skriptet "GetPSGalleryItemsForAuthor" till PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="a8bb1-139">To facilitate exporting packages published to the PowerShell Gallery, we have published the script "GetPSGalleryItemsForAuthor" to the PowerShell Gallery.</span></span> <span data-ttu-id="a8bb1-140">Det här skriptet exporterar en kopia av varje version av varje paket som försätts i PowerShell-galleriet baserat på den författar information som lagras i paketet.</span><span class="sxs-lookup"><span data-stu-id="a8bb1-140">This script exports a copy of every version of every package put into the PowerShell Gallery based on the author information stored in the package.</span></span>

> [!NOTE]
> <span data-ttu-id="a8bb1-141">Författaren lagras i paket manifestet när du publicerar ditt paket.</span><span class="sxs-lookup"><span data-stu-id="a8bb1-141">The Author is stored in the package manifest when you publish your package.</span></span> <span data-ttu-id="a8bb1-142">Det finns ingen garanti för att författaren är samma identitet som det konto som du använder i PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="a8bb1-142">There is no guarantee that the Author is the same identity as the account you use in the PowerShell Gallery.</span></span> <span data-ttu-id="a8bb1-143">Om du använder något annat värde i fältet författare måste du ange det värdet när du använder det här skriptet.</span><span class="sxs-lookup"><span data-stu-id="a8bb1-143">If you use some other value in the Author field, you will need to supply that value when using this script.</span></span>

<span data-ttu-id="a8bb1-144">Du kan hämta skriptet med hjälp av följande PowerShell-kommando:</span><span class="sxs-lookup"><span data-stu-id="a8bb1-144">You may download the script by using the following PowerShell command:</span></span>

```powershell
Save-Script Get-repository psgallery
```

<span data-ttu-id="a8bb1-145">Du kan sedan köra skriptet direkt genom att köra följande PowerShell-kommandon:</span><span class="sxs-lookup"><span data-stu-id="a8bb1-145">You can then run the script directly, by running the following PowerShell commands:</span></span>

```powershell
# cd <local folder location>
.\GetPSGalleryItemsForAuthor.ps1
```

<span data-ttu-id="a8bb1-146">Du uppmanas att ange författaren och en mapp i systemet där du vill att paketen ska sparas.</span><span class="sxs-lookup"><span data-stu-id="a8bb1-146">You will be prompted to supply the Author and a folder on your system where you want the packages to be saved.</span></span>

## <a name="deleting-personal-data-from-the-powershell-gallery"></a><span data-ttu-id="a8bb1-147">Ta bort personliga data från PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="a8bb1-147">Deleting Personal Data From The PowerShell Gallery</span></span>

<span data-ttu-id="a8bb1-148">Om du vill ta bort ditt PowerShell-galleriet-konto eller paket som du äger i PowerShell-galleriet skickar du e-post till cgadmin@microsoft.com med rubriken: "GDPR-begäran om objekt som är relaterade till det här kontot".</span><span class="sxs-lookup"><span data-stu-id="a8bb1-148">To delete your PowerShell Gallery account or any package you own in the PowerShell Gallery, send email to cgadmin@microsoft.com with the title: "GDPR Request for items relating to this account".</span></span> <span data-ttu-id="a8bb1-149">I bröd texten i meddelande läget, vilken information som du vill ta bort.</span><span class="sxs-lookup"><span data-stu-id="a8bb1-149">In the body of the message state what information you want deleted.</span></span> <span data-ttu-id="a8bb1-150">Exempel:</span><span class="sxs-lookup"><span data-stu-id="a8bb1-150">For example:</span></span>

- <span data-ttu-id="a8bb1-151">Ta bort version x. y. z för mitt pakets paket namn.</span><span class="sxs-lookup"><span data-stu-id="a8bb1-151">Please delete version x.y.z of my package "package name"</span></span>
- <span data-ttu-id="a8bb1-152">Ta bort alla versioner av mitt pakets paket namn.</span><span class="sxs-lookup"><span data-stu-id="a8bb1-152">Please delete all versions of my package "package name"</span></span>
- <span data-ttu-id="a8bb1-153">Ta bort mitt PowerShell-galleriet-konto</span><span class="sxs-lookup"><span data-stu-id="a8bb1-153">Please delete my PowerShell Gallery account</span></span>

<span data-ttu-id="a8bb1-154">PowerShell-galleriet-administratörer kommer att svara inom 7 arbets dagar.</span><span class="sxs-lookup"><span data-stu-id="a8bb1-154">The PowerShell Gallery administrators will reply within 7 business days.</span></span>
<span data-ttu-id="a8bb1-155">De angivna paketen tas bort inom 30 dagar efter att begäran har skickats.</span><span class="sxs-lookup"><span data-stu-id="a8bb1-155">The packages specified will be deleted within 30 days after the request is sent.</span></span>
