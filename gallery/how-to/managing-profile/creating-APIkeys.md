---
ms.date: 09/10/2018
contributor: JKeithB
keywords: galleriet, powershell, cmdlet, psgallery
title: Hantera API-nycklar
ms.openlocfilehash: 954eb27c25babdb8efe50c13caf5f2d287c6b3e3
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/25/2018
ms.locfileid: "50002521"
---
# <a name="managing-api-keys"></a><span data-ttu-id="d6be6-103">Hantera API-nycklar</span><span class="sxs-lookup"><span data-stu-id="d6be6-103">Managing API keys</span></span>

<span data-ttu-id="d6be6-104">PowerShell-galleriet kan du skapa flera API-nycklar för att stödja flera olika publicera krav.</span><span class="sxs-lookup"><span data-stu-id="d6be6-104">The PowerShell Gallery supports creating multiple API keys to support a range of publishing requirements.</span></span> <span data-ttu-id="d6be6-105">En API-nyckel kan tillämpa på ett eller flera paket, ger specifika rättigheter och har ett utgångsdatum.</span><span class="sxs-lookup"><span data-stu-id="d6be6-105">An API key can apply to one or more packages, grants specific privileges, and has an expiration date.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d6be6-106">Användare som publicerats i PowerShell-galleriet innan introduktionen av begränsade API-nycklar har en ”fullständig åtkomst API key”.</span><span class="sxs-lookup"><span data-stu-id="d6be6-106">Users who published to the PowerShell Gallery prior to the introduction of scoped API keys will have a "Full access API key".</span></span> <span data-ttu-id="d6be6-107">Nycklar för fullständig åtkomst har inte säkerhetsförbättringar som är inbyggda i begränsade API-nycklar.</span><span class="sxs-lookup"><span data-stu-id="d6be6-107">The full access keys do not have the security improvements built into scoped API keys.</span></span> <span data-ttu-id="d6be6-108">Fullständig åtkomstnycklarna aldrig upphör att gälla och gäller för allt som ägs av användaren.</span><span class="sxs-lookup"><span data-stu-id="d6be6-108">The full access keys never expires and apply to everything owned by the user.</span></span> <span data-ttu-id="d6be6-109">Om du tar bort den här nyckeln kan inte återskapas.</span><span class="sxs-lookup"><span data-stu-id="d6be6-109">If you delete this key, it cannot be recreated.</span></span>

<span data-ttu-id="d6be6-110">Följande bild visar de tillgängliga alternativen när du skapar en begränsade API-nyckel.</span><span class="sxs-lookup"><span data-stu-id="d6be6-110">The following image shows the options available when creating a scoped API key.</span></span>

![Skapa API-nycklar](../../Images/PSGallery_KeyScoped.png)

<span data-ttu-id="d6be6-112">I det här exemplet skapade vi en API-nyckel med namnet **AzureRMDataFactory**.</span><span class="sxs-lookup"><span data-stu-id="d6be6-112">In this example, we created an API key named **AzureRMDataFactory**.</span></span> <span data-ttu-id="d6be6-113">Värdet för nyckeln kan användas för att skicka paket med namn som börjar med ”AzureRM.DataFactory” och är giltig i 365 dagar.</span><span class="sxs-lookup"><span data-stu-id="d6be6-113">This key value can be used to push packages with names that begin with 'AzureRM.DataFactory' and is valid for 365 days.</span></span> <span data-ttu-id="d6be6-114">Det här är ett vanligt scenario när olika team inom samma organisation arbetar med olika paket.</span><span class="sxs-lookup"><span data-stu-id="d6be6-114">This is a typical scenario when different teams within the same organization work on different packages.</span></span> <span data-ttu-id="d6be6-115">Medlemmar i teamet har en nyckel som ger behörighet för det specifika paket som de arbetar på.</span><span class="sxs-lookup"><span data-stu-id="d6be6-115">The members of the team have a key that grants them privileges for the specific package they work on.</span></span>
<span data-ttu-id="d6be6-116">Värdet för förfallotid förhindrar användning av inaktuella eller glömda nycklar.</span><span class="sxs-lookup"><span data-stu-id="d6be6-116">The expiration value prevents the use of stale or forgotten keys.</span></span>

## <a name="using-glob-patterns"></a><span data-ttu-id="d6be6-117">Med hjälp av BLOB-mönster</span><span class="sxs-lookup"><span data-stu-id="d6be6-117">Using glob patterns</span></span>

<span data-ttu-id="d6be6-118">Om du arbetar med flera paket kan använda du globbing mönster så att de matchar flera paket som en grupp.</span><span class="sxs-lookup"><span data-stu-id="d6be6-118">If you work on multiple packages, you can use globbing patterns to match multiple packages as a group.</span></span> <span data-ttu-id="d6be6-119">API-nyckel behörigheter gäller för alla nya paket som matchar mönstret BLOB.</span><span class="sxs-lookup"><span data-stu-id="d6be6-119">API key permissions apply to all new packages matching the glob pattern.</span></span> <span data-ttu-id="d6be6-120">Till exempel det föregående exemplet används en **BLOB mönstret** värdet för ”AzureRM.DataFactory\*”.</span><span class="sxs-lookup"><span data-stu-id="d6be6-120">For example, the previous example uses a **Glob Pattern** value of 'AzureRM.DataFactory\*'.</span></span> <span data-ttu-id="d6be6-121">Du kan skicka ett paket med namnet ”AzureRm.DataFactoryV2.Netcore” med hjälp av den här nyckeln eftersom paketet matchar mönstret BLOB.</span><span class="sxs-lookup"><span data-stu-id="d6be6-121">You can push a package named 'AzureRm.DataFactoryV2.Netcore' using this key since the package matches the glob pattern.</span></span>

## <a name="create-api-keys-securely"></a><span data-ttu-id="d6be6-122">Skapa API-nycklar på ett säkert sätt</span><span class="sxs-lookup"><span data-stu-id="d6be6-122">Create API keys securely</span></span>

<span data-ttu-id="d6be6-123">För säkerhet, ett nyligen skapade nyckelvärde visas aldrig på skärmen och är endast tillgänglig med knappen Kopiera enligt nedan.</span><span class="sxs-lookup"><span data-stu-id="d6be6-123">For security, a newly created key value is never shown on the screen and is only available with the Copy button, as shown below.</span></span>

![Hämta nya API-nyckelvärdet](../../Images/PSGallery_CopyCreatedKey.png)

> [!IMPORTANT]
> <span data-ttu-id="d6be6-125">Du kan bara kopiera API-nyckelvärdet omedelbart efter att skapa eller uppdatera den.</span><span class="sxs-lookup"><span data-stu-id="d6be6-125">You can only copy the API key value immediately after creating or refreshing it.</span></span> <span data-ttu-id="d6be6-126">Den visas inte och kommer inte att komma åt igen när sidan uppdateras.</span><span class="sxs-lookup"><span data-stu-id="d6be6-126">It will not be displayed, and will not be accessible again after the page is refreshed.</span></span> <span data-ttu-id="d6be6-127">Om du förlorar nyckelvärdet kan du använda återskapa och kopiera nyckeln när den har återskapats.</span><span class="sxs-lookup"><span data-stu-id="d6be6-127">If you lose the key value, you must use Regenerate, and copy the key after it is regenerated.</span></span>

## <a name="key-permissions-and-expiration"></a><span data-ttu-id="d6be6-128">Nyckelns behörigheter och upphör att gälla</span><span class="sxs-lookup"><span data-stu-id="d6be6-128">Key permissions and expiration</span></span>

<span data-ttu-id="d6be6-129">Begränsade API-nycklar kan tilldela någon av följande behörigheter:</span><span class="sxs-lookup"><span data-stu-id="d6be6-129">Scoped API keys can assign any of the following permissions:</span></span>

- <span data-ttu-id="d6be6-130">Skicka nya paket</span><span class="sxs-lookup"><span data-stu-id="d6be6-130">Push new packages</span></span>
- <span data-ttu-id="d6be6-131">Skicka ny eller uppdatera paket</span><span class="sxs-lookup"><span data-stu-id="d6be6-131">Push new or update packages</span></span>
- <span data-ttu-id="d6be6-132">Ta bort paket</span><span class="sxs-lookup"><span data-stu-id="d6be6-132">Unlist packages</span></span>

<span data-ttu-id="d6be6-133">Alla nya nycklar har en giltighetstid.</span><span class="sxs-lookup"><span data-stu-id="d6be6-133">Every new key has an expiration.</span></span> <span data-ttu-id="d6be6-134">Värdet för förfallotid mäts i dagar.</span><span class="sxs-lookup"><span data-stu-id="d6be6-134">The expiration value is measured in days.</span></span> <span data-ttu-id="d6be6-135">De möjliga värdena för förfallodatum är:</span><span class="sxs-lookup"><span data-stu-id="d6be6-135">The possible values for expiration are:</span></span>

- <span data-ttu-id="d6be6-136">1 dag</span><span class="sxs-lookup"><span data-stu-id="d6be6-136">1 day</span></span>
- <span data-ttu-id="d6be6-137">90 dagar</span><span class="sxs-lookup"><span data-stu-id="d6be6-137">90 days</span></span>
- <span data-ttu-id="d6be6-138">180 dagar</span><span class="sxs-lookup"><span data-stu-id="d6be6-138">180 days</span></span>
- <span data-ttu-id="d6be6-139">270 dagar</span><span class="sxs-lookup"><span data-stu-id="d6be6-139">270 days</span></span>
- <span data-ttu-id="d6be6-140">365 dagar (standard)</span><span class="sxs-lookup"><span data-stu-id="d6be6-140">365 days (default)</span></span>

<span data-ttu-id="d6be6-141">De här inställningarna kan inte ändras när nyckeln har skapats.</span><span class="sxs-lookup"><span data-stu-id="d6be6-141">These settings cannot be changed once the key is created.</span></span> <span data-ttu-id="d6be6-142">Du kan inte skapa en ny nyckel med upphör aldrig att gälla.</span><span class="sxs-lookup"><span data-stu-id="d6be6-142">You cannot create a new key that never expires.</span></span>

## <a name="editing-and-deleting-existing-api-keys"></a><span data-ttu-id="d6be6-143">Redigera och ta bort befintliga API-nycklar</span><span class="sxs-lookup"><span data-stu-id="d6be6-143">Editing and deleting existing API keys</span></span>

<span data-ttu-id="d6be6-144">Du kan ändra vissa inställningar för en befintlig nyckel.</span><span class="sxs-lookup"><span data-stu-id="d6be6-144">You can change some settings of an existing key.</span></span> <span data-ttu-id="d6be6-145">Som vi nämnde tidigare kan kan inte du ändra säkerhetsomfattningen för en befintlig API-nyckel eller ändra förfallodatum.</span><span class="sxs-lookup"><span data-stu-id="d6be6-145">As previously noted, you cannot modify the security scope for an existing API key or change the expiration.</span></span> <span data-ttu-id="d6be6-146">Ändringsbart alternativ visas på följande skärmbild:</span><span class="sxs-lookup"><span data-stu-id="d6be6-146">The changeable options are shown in the following screenshot:</span></span>

![Hämta nya API-nyckelvärdet](../../Images/PSGallery_EditAPIKey.png)

<span data-ttu-id="d6be6-148">Om du vill ändra de paket som styrs av en nyckel, kan du välja enskilda paket i listan eller ändra BLOB-mönster.</span><span class="sxs-lookup"><span data-stu-id="d6be6-148">To change the packages controlled by a key, you can choose individual packages from the list or change the glob pattern.</span></span>

<span data-ttu-id="d6be6-149">Klicka på **återskapa** skapar ett nytt nyckelvärde.</span><span class="sxs-lookup"><span data-stu-id="d6be6-149">Clicking **Regenerate** creates a new key value.</span></span> <span data-ttu-id="d6be6-150">Precis som när du först skapade nyckeln, måste du **kopia** nyckelvärdet omedelbart när du har uppdaterat den.</span><span class="sxs-lookup"><span data-stu-id="d6be6-150">Just like when you initially created the key, you must **Copy** the key value immediately after updating it.</span></span> <span data-ttu-id="d6be6-151">Den **kopia** alternativet är inte tillgängligt när du lämnar den här sidan.</span><span class="sxs-lookup"><span data-stu-id="d6be6-151">The **Copy** option is not available once you leave this page.</span></span>

<span data-ttu-id="d6be6-152">Klicka på **ta bort** visas en bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="d6be6-152">Clicking **Delete** displays a confirmation message.</span></span> <span data-ttu-id="d6be6-153">När en nyckel har tagits bort, blir det inte kan användas.</span><span class="sxs-lookup"><span data-stu-id="d6be6-153">Once a key is deleted, it will be unusable.</span></span>

## <a name="key-expiration"></a><span data-ttu-id="d6be6-154">Utgångsdatum för nyckel</span><span class="sxs-lookup"><span data-stu-id="d6be6-154">Key expiration</span></span>

<span data-ttu-id="d6be6-155">Tio dagar före förfallodatum, skickar PowerShell-galleriet ett e-postmeddelande med varning kontoinnehavaren av API-nyckeln.</span><span class="sxs-lookup"><span data-stu-id="d6be6-155">Ten days before the expiration, the PowerShell Gallery sends a warning email the account holder of the API key.</span></span> <span data-ttu-id="d6be6-156">Efter förfallodatumet kan nyckeln inte användas.</span><span class="sxs-lookup"><span data-stu-id="d6be6-156">After expiration, the key is unusable.</span></span> <span data-ttu-id="d6be6-157">Ett varningsmeddelande visas överst på sidan API nyckelhantering som visar vilka nycklar är inte längre giltig.</span><span class="sxs-lookup"><span data-stu-id="d6be6-157">A warning message is displayed at the top of the API key management page showing which keys are no longer valid.</span></span> <span data-ttu-id="d6be6-158">Du kan generera ett nytt nyckelvärde.</span><span class="sxs-lookup"><span data-stu-id="d6be6-158">You can generate a new key value.</span></span>
