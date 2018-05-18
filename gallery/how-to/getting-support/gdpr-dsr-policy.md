---
ms.date: 03/27/2018
contributor: JKeithB
keywords: galleriet, powershell, psgallery BNPR
title: PowerShell-galleriet BNPR kompatibilitet
ms.openlocfilehash: dca1a82952c284980a84caafa13b2807e47e25a0
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/16/2018
---
# <a name="powershell-gallery-gdpr-compliance"></a><span data-ttu-id="8d0ab-103">PowerShell-galleriet BNPR kompatibilitet</span><span class="sxs-lookup"><span data-stu-id="8d0ab-103">PowerShell Gallery GDPR compliance</span></span>

## <a name="overview"></a><span data-ttu-id="8d0ab-104">Översikt</span><span class="sxs-lookup"><span data-stu-id="8d0ab-104">Overview</span></span>

<span data-ttu-id="8d0ab-105">I kan 2018 träder Europeiska sekretesslagstiftning, den allmänna Data Protection förordning (BNPR), i kraft.</span><span class="sxs-lookup"><span data-stu-id="8d0ab-105">In May 2018, a European privacy law, the General Data Protection Regulation (GDPR), takes effect.</span></span>
<span data-ttu-id="8d0ab-106">BNPR inför nya regler på företag, myndigheter, icke-vinst och andra organisationer att erbjudande varor och tjänster till personer i Europeiska unionen (EU), eller att samla in och analysera data som är knutna till Europa boende.</span><span class="sxs-lookup"><span data-stu-id="8d0ab-106">The GDPR imposes new rules on companies, government agencies, non-profits, and other organizations that offer goods and services to people in the European Union (EU), or that collect and analyze data tied to EU residents.</span></span>
<span data-ttu-id="8d0ab-107">BNPR gäller oavsett där du befinner dig.</span><span class="sxs-lookup"><span data-stu-id="8d0ab-107">The GDPR applies no matter where you are located.</span></span>

> [!NOTE]
> <span data-ttu-id="8d0ab-108">Den här artikeln innehåller anvisningar att ta bort personliga data från PowerShell-galleriet och kan användas för att stödja din skyldigheter enligt BNPR.</span><span class="sxs-lookup"><span data-stu-id="8d0ab-108">This article provides steps for how to delete personal data from the PowerShell Gallery and can be used to support your obligations under the GDPR.</span></span> <span data-ttu-id="8d0ab-109">Om du letar efter allmän information om BNPR finns i [BNPR avsnitt av tjänsten förtroende portal](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted).</span><span class="sxs-lookup"><span data-stu-id="8d0ab-109">If you’re looking for general info about GDPR, see the [GDPR section of the Service Trust portal](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted).</span></span>

## <a name="personally-identifiable-data"></a><span data-ttu-id="8d0ab-110">Personligt identifierbar information</span><span class="sxs-lookup"><span data-stu-id="8d0ab-110">Personally identifiable data</span></span>

<span data-ttu-id="8d0ab-111">Följande information som kan utföras av användare som kan innehålla personlig information lagras i PowerShell-galleriet:</span><span class="sxs-lookup"><span data-stu-id="8d0ab-111">The PowerShell Gallery stores the following information that may be provided by users, which may contain personal information:</span></span>

* <span data-ttu-id="8d0ab-112">PowerShell-galleriet konto</span><span class="sxs-lookup"><span data-stu-id="8d0ab-112">PowerShell Gallery account</span></span>
* <span data-ttu-id="8d0ab-113">Objekt som publicerats i PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="8d0ab-113">Items published to the PowerShell Gallery</span></span>
* <span data-ttu-id="8d0ab-114">E-postkommunikation med PowerShell-galleriet-teamet</span><span class="sxs-lookup"><span data-stu-id="8d0ab-114">Email correspondence with the PowerShell Gallery team</span></span>

<span data-ttu-id="8d0ab-115">De flesta användare skapar ett konto med PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="8d0ab-115">Most users do not create a PowerShell Gallery account.</span></span>
<span data-ttu-id="8d0ab-116">Ett konto behövs inte om du ska publicera ett objekt eller funktionen ”kontakta ägare” i PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="8d0ab-116">An account is not required unless you are going to publish an item or use the "Contact Owner" feature in the PowerShell Gallery.</span></span>
<span data-ttu-id="8d0ab-117">Förutom e-postkommunikation initieras av användaren, lagrar inte personligt identifierbar information för användare som inte har skapat ett konto i PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="8d0ab-117">Other than email correspondence initiated by the user, the PowerShell Gallery does not store personally identifiable data for users who have not created an account.</span></span>

<span data-ttu-id="8d0ab-118">Användare som skapar ett PowerShell-galleriet konto kan publicera objekt till PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="8d0ab-118">Users who create a PowerShell Gallery account can publish items to the PowerShell Gallery.</span></span>
<span data-ttu-id="8d0ab-119">Dessa objekt förväntas vara PowerShell-koden, men kan innehålla andra information, inklusive personlig information.</span><span class="sxs-lookup"><span data-stu-id="8d0ab-119">Those items are expected to be PowerShell code, but may contain other information including personal information.</span></span>
<span data-ttu-id="8d0ab-120">Informationen nedan visar hur du kan få alla objekt du har publicerat PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="8d0ab-120">The information below will show how you can get all the items you have published to the PowerShell Gallery.</span></span>

## <a name="dsr-export-of-powershell-gallery-data"></a><span data-ttu-id="8d0ab-121">DSR Export av Data för PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="8d0ab-121">DSR Export of PowerShell Gallery Data</span></span>

<span data-ttu-id="8d0ab-122">I följande avsnitt beskrivs hur PowerShell-galleriet stöder ämne begäranden (DSR), som förklarar hur du exporterar information som lagras i PowerShell-galleriet och hur du begär borttagning av den här informationen.</span><span class="sxs-lookup"><span data-stu-id="8d0ab-122">The following sections describe how the PowerShell Gallery supports data subject requests (DSR), by explaining how to export information stored in the PowerShell Gallery, and how to request deletion of this information.</span></span>

### <a name="email"></a><span data-ttu-id="8d0ab-123">E-post</span><span class="sxs-lookup"><span data-stu-id="8d0ab-123">Email</span></span>

<span data-ttu-id="8d0ab-124">E-postkommunikation kan vara något av följande:</span><span class="sxs-lookup"><span data-stu-id="8d0ab-124">Email correspondence may include any of the following:</span></span>

* <span data-ttu-id="8d0ab-125">E-post som skickas till ägare av PowerShell-galleriet artiklar om koden analysen skannar upptäckte ett problem med ett objekt som de har publicerats i PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="8d0ab-125">Email sent to the owners of PowerShell Gallery items if the code analysis scans detected an issue with any item they have published to the PowerShell Gallery</span></span>
* <span data-ttu-id="8d0ab-126">E-post som skickas av alla till PowerShell-galleriet teamet med hjälp av e-postadress på sidan ”Kontakta oss” (cgadmin@microsoft.com)</span><span class="sxs-lookup"><span data-stu-id="8d0ab-126">Email sent by anyone to the PowerShell Gallery team using the email address in the "Contact Us" page (cgadmin@microsoft.com)</span></span>
* <span data-ttu-id="8d0ab-127">Registrerad användare som använder funktionen ”kontakta ägare” i PowerShell-galleriet för att skicka e-post till ägaren av ett objekt i PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="8d0ab-127">Registered users who use the "Contact Owner" feature in the PowerShell Gallery to send email to the owner of an item in the PowerShell Gallery</span></span>

<span data-ttu-id="8d0ab-128">E-postmeddelanden som skickas av eller i PowerShell-galleriet har en bevarandeprincip 90 dagar för att stödja säkerhetsrisker undersökningar bör skadlig kod identifieras på PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="8d0ab-128">Emails sent by or to the PowerShell Gallery have a retention policy of 90 days to support possible security investigations should malicious code be discovered on the PowerShell Gallery.</span></span>
<span data-ttu-id="8d0ab-129">E-postmeddelanden tas bort av Grupprincip efter 90 dagar.</span><span class="sxs-lookup"><span data-stu-id="8d0ab-129">Emails are deleted by policy after 90 days.</span></span>

<span data-ttu-id="8d0ab-130">Du kan begära kopior av alla e-postmeddelanden skickas till eller från din e-postadress och PowerShell-galleriet inom de senaste 90 dagarna.</span><span class="sxs-lookup"><span data-stu-id="8d0ab-130">You may request copies of all emails sent to or from your email address and the PowerShell Gallery within the previous 90 days.</span></span>
<span data-ttu-id="8d0ab-131">Om du vill begära det här postkommunikation, skicka ett e-postmeddelande till cgadmin@microsoft.com, med rubriken: ”DSR begäran för e-postmeddelanden som är relaterade till det här kontot”.</span><span class="sxs-lookup"><span data-stu-id="8d0ab-131">To request this correspondence, send an email to cgadmin@microsoft.com, with the title: "DSR Request for emails relating to this account".</span></span>
<span data-ttu-id="8d0ab-132">Ange vilken information som du begär i själva meddelandet (till exempel: skicka alla e-postmeddelanden skickas till eller tas emot från den här e-postadress.) Alla e-post som berör din e-postadress inom 90 dagar efter begäran skickas inom 7 arbetsdagar.</span><span class="sxs-lookup"><span data-stu-id="8d0ab-132">In the body of the message, state what information you are requesting (for example: Please send all emails sent to or received from this email address.) All emails involving your email address within 90 days of the request will be sent within 7 business days.</span></span>

### <a name="powershell-gallery-account-information"></a><span data-ttu-id="8d0ab-133">PowerShell-galleriet kontoinformation</span><span class="sxs-lookup"><span data-stu-id="8d0ab-133">PowerShell Gallery Account Information</span></span>

<span data-ttu-id="8d0ab-134">Om du har skapat ett PowerShell-galleriet konto kan hittar du alla personlig information som har lagrats i PowerShell-galleriet genom att utföra följande steg:</span><span class="sxs-lookup"><span data-stu-id="8d0ab-134">If you have created a PowerShell Gallery account, you can find all personal information that has been stored in PowerShell Gallery by taking the following steps:</span></span>

1. <span data-ttu-id="8d0ab-135">Logga in på PowerShell-galleriet och sedan klicka på ditt användarnamn</span><span class="sxs-lookup"><span data-stu-id="8d0ab-135">Sign in to the PowerShell Gallery, then click on your username</span></span>
2. <span data-ttu-id="8d0ab-136">Nästa sida som visas är sidan konto, som visar e-postadressen används för kontot PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="8d0ab-136">The next page displayed is the Account page, which shows the email address used for the PowerShell Gallery account</span></span>

<span data-ttu-id="8d0ab-137">Om du har skapat mer än ett konto i PowerShell-galleriet, måste du upprepa dessa steg för varje konto.</span><span class="sxs-lookup"><span data-stu-id="8d0ab-137">If you have created more than one account in the PowerShell Gallery, you will need to repeat these steps for each account.</span></span>

### <a name="items-in-the-powershell-gallery"></a><span data-ttu-id="8d0ab-138">Objekt i PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="8d0ab-138">Items in the PowerShell Gallery</span></span>

<span data-ttu-id="8d0ab-139">Vi har publicerat skriptet ”GetPSGalleryItemsForAuthor” i PowerShell-galleriet för att underlätta exporterar objekt som har publicerats i PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="8d0ab-139">To facilitate exporting items published to the PowerShell Gallery, we have published the script "GetPSGalleryItemsForAuthor" to the PowerShell Gallery.</span></span>
<span data-ttu-id="8d0ab-140">Det här skriptet exporterar en kopia av alla versioner av varje objekt som tas i PowerShell-galleriet baserat på författare informationen som lagras i objektet.</span><span class="sxs-lookup"><span data-stu-id="8d0ab-140">This script exports a copy of every version of every item put into the PowerShell Gallery based on the author information stored in the item.</span></span>

> [!NOTE]
> <span data-ttu-id="8d0ab-141">Författaren lagras i manifestet objektet när du publicerar ditt objekt.</span><span class="sxs-lookup"><span data-stu-id="8d0ab-141">The Author is stored in the item manifest when you publish your item.</span></span>
> <span data-ttu-id="8d0ab-142">Det är inte säkert att författaren är samma identitet som det konto som används i PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="8d0ab-142">There is no guarantee that the Author is the same identity as the account you use in the PowerShell Gallery.</span></span>
> <span data-ttu-id="8d0ab-143">Om du använder ett annat värde i fältet Författare behöver du ange värdet när du använder det här skriptet.</span><span class="sxs-lookup"><span data-stu-id="8d0ab-143">If you use some other value in the Author field, you will need to supply that value when using this script.</span></span>

<span data-ttu-id="8d0ab-144">Du kan ladda ned skriptet med hjälp av följande PowerShell-kommando:</span><span class="sxs-lookup"><span data-stu-id="8d0ab-144">You may download the script by using the following PowerShell command:</span></span>

```powershell
Save-Script GetPSGalleryItemsForAuthor -path <local folder location> -repository psgallery
```

<span data-ttu-id="8d0ab-145">Sedan kan du köra skriptet direkt, genom att köra följande PowerShell-kommandon:</span><span class="sxs-lookup"><span data-stu-id="8d0ab-145">You can then run the script directly, by running the following PowerShell commands:</span></span>

```powershell
cd <local folder location >
.\GetPSGalleryItemsForAuthor.ps1
```

<span data-ttu-id="8d0ab-146">Du uppmanas att ange författaren och en mapp på datorn där du vill att de objekt som ska sparas.</span><span class="sxs-lookup"><span data-stu-id="8d0ab-146">You will be prompted to supply the Author and a folder on your system where you want the items to be saved.</span></span>

## <a name="deleting-personal-data-from-the-powershell-gallery"></a><span data-ttu-id="8d0ab-147">Ta bort personliga Data från PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="8d0ab-147">Deleting Personal Data From The PowerShell Gallery</span></span>

<span data-ttu-id="8d0ab-148">Ta bort ditt konto med PowerShell-galleriet eller ett objekt som du äger i PowerShell-galleriet genom att skicka e-post till cgadmin@microsoft.com med rubriken: ”BNPR begäran för objekt som är relaterade till det här kontot”.</span><span class="sxs-lookup"><span data-stu-id="8d0ab-148">To delete your PowerShell Gallery account or any item you own in the PowerShell Gallery, send email to cgadmin@microsoft.com with the title: "GDPR Request for items relating to this account".</span></span>
<span data-ttu-id="8d0ab-149">Ange vilken information som du vill ta bort i själva meddelandet.</span><span class="sxs-lookup"><span data-stu-id="8d0ab-149">In the body of the message state what information you want deleted.</span></span> <span data-ttu-id="8d0ab-150">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="8d0ab-150">For example:</span></span>

* <span data-ttu-id="8d0ab-151">Ta bort version x.y.z för Mina objekt ”namn”</span><span class="sxs-lookup"><span data-stu-id="8d0ab-151">Please delete version x.y.z of my item "item name"</span></span>
* <span data-ttu-id="8d0ab-152">Ta bort alla versioner av Mina objekt ”namn”</span><span class="sxs-lookup"><span data-stu-id="8d0ab-152">Please delete all versions of my item "item name"</span></span>
* <span data-ttu-id="8d0ab-153">Ta bort mitt konto PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="8d0ab-153">Please delete my PowerShell Gallery account</span></span>

<span data-ttu-id="8d0ab-154">PowerShell-galleriet administratörer svarar inom 7 arbetsdagar.</span><span class="sxs-lookup"><span data-stu-id="8d0ab-154">The PowerShell Gallery administrators will reply within 7 business days.</span></span>
<span data-ttu-id="8d0ab-155">De angivna objekt tas bort inom 30 dagar efter att begäran har skickats.</span><span class="sxs-lookup"><span data-stu-id="8d0ab-155">The items specified will be deleted within 30 days after the request is sent.</span></span>
