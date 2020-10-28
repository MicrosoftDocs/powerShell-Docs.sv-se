---
ms.date: 09/10/2018
title: Hantera API-nycklar
description: PowerShell-galleriet använder API-nycklar för att autentisera åtkomst till galleriet för innehålls utgivare.
ms.openlocfilehash: 4b70ac7d56fc1d63719c2acf93da3dd4ac22abed
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92661124"
---
# <a name="managing-api-keys"></a><span data-ttu-id="012a9-103">Hantera API-nycklar</span><span class="sxs-lookup"><span data-stu-id="012a9-103">Managing API keys</span></span>

<span data-ttu-id="012a9-104">PowerShell-galleriet har stöd för att skapa flera API-nycklar som stöder ett antal publicerings krav.</span><span class="sxs-lookup"><span data-stu-id="012a9-104">The PowerShell Gallery supports creating multiple API keys to support a range of publishing requirements.</span></span> <span data-ttu-id="012a9-105">En API-nyckel kan gälla för ett eller flera paket, ger vissa behörigheter och har ett förfallo datum.</span><span class="sxs-lookup"><span data-stu-id="012a9-105">An API key can apply to one or more packages, grants specific privileges, and has an expiration date.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="012a9-106">Användare som har publicerat till PowerShell-galleriet innan införandet av API-nycklar för omfattningar kommer att ha en "fullständig åtkomst-API-nyckel".</span><span class="sxs-lookup"><span data-stu-id="012a9-106">Users who published to the PowerShell Gallery prior to the introduction of scoped API keys will have a "Full access API key".</span></span> <span data-ttu-id="012a9-107">De fullständiga åtkomst nycklarna har inte de säkerhets förbättringar som är inbyggda i omfånget API-nycklar.</span><span class="sxs-lookup"><span data-stu-id="012a9-107">The full access keys do not have the security improvements built into scoped API keys.</span></span> <span data-ttu-id="012a9-108">De fullständiga åtkomst nycklarna upphör aldrig att gälla och gäller allt som ägs av användaren.</span><span class="sxs-lookup"><span data-stu-id="012a9-108">The full access keys never expires and apply to everything owned by the user.</span></span> <span data-ttu-id="012a9-109">Om du tar bort den här nyckeln kan den inte återskapas.</span><span class="sxs-lookup"><span data-stu-id="012a9-109">If you delete this key, it cannot be recreated.</span></span>

<span data-ttu-id="012a9-110">Följande bild visar de alternativ som är tillgängliga när du skapar en omfångs-API-nyckel.</span><span class="sxs-lookup"><span data-stu-id="012a9-110">The following image shows the options available when creating a scoped API key.</span></span>

![Skapar API-nycklar](media/creating-APIkeys/PSGallery_KeyScoped.png)

<span data-ttu-id="012a9-112">I det här exemplet har vi skapat en API-nyckel med namnet **AzureRMDataFactory** .</span><span class="sxs-lookup"><span data-stu-id="012a9-112">In this example, we created an API key named **AzureRMDataFactory** .</span></span> <span data-ttu-id="012a9-113">Detta nyckel värde kan användas för att skicka paket med namn som börjar med "AzureRM. DataFactory" och som är giltiga i 365 dagar.</span><span class="sxs-lookup"><span data-stu-id="012a9-113">This key value can be used to push packages with names that begin with 'AzureRM.DataFactory' and is valid for 365 days.</span></span> <span data-ttu-id="012a9-114">Detta är ett typiskt scenario när olika team inom samma organisation arbetar med olika paket.</span><span class="sxs-lookup"><span data-stu-id="012a9-114">This is a typical scenario when different teams within the same organization work on different packages.</span></span> <span data-ttu-id="012a9-115">Medlemmarna i teamet har en nyckel som ger dem behörighet för det aktuella paketet som de arbetar med.</span><span class="sxs-lookup"><span data-stu-id="012a9-115">The members of the team have a key that grants them privileges for the specific package they work on.</span></span>
<span data-ttu-id="012a9-116">Värdet för förfallo datum förhindrar att inaktuella eller bortglömt nycklar används.</span><span class="sxs-lookup"><span data-stu-id="012a9-116">The expiration value prevents the use of stale or forgotten keys.</span></span>

## <a name="using-glob-patterns"></a><span data-ttu-id="012a9-117">Använda BLOB mönster</span><span class="sxs-lookup"><span data-stu-id="012a9-117">Using glob patterns</span></span>

<span data-ttu-id="012a9-118">Om du arbetar med flera paket kan du använda globbing mönster för att matcha flera paket som en grupp.</span><span class="sxs-lookup"><span data-stu-id="012a9-118">If you work on multiple packages, you can use globbing patterns to match multiple packages as a group.</span></span> <span data-ttu-id="012a9-119">API-nyckelns behörigheter gäller för alla nya paket som matchar BLOB-mönstret.</span><span class="sxs-lookup"><span data-stu-id="012a9-119">API key permissions apply to all new packages matching the glob pattern.</span></span> <span data-ttu-id="012a9-120">Exemplet ovan använder till exempel ett BLOB- **Pattern** -värde för ' AzureRM. DataFactory \* '.</span><span class="sxs-lookup"><span data-stu-id="012a9-120">For example, the previous example uses a **Glob Pattern** value of 'AzureRM.DataFactory\*'.</span></span> <span data-ttu-id="012a9-121">Du kan skicka ett paket med namnet "AzureRm. DataFactoryV2. NetCore" med hjälp av den här nyckeln eftersom paketet matchar BLOB-mönstret.</span><span class="sxs-lookup"><span data-stu-id="012a9-121">You can push a package named 'AzureRm.DataFactoryV2.Netcore' using this key since the package matches the glob pattern.</span></span>

## <a name="create-api-keys-securely"></a><span data-ttu-id="012a9-122">Skapa API-nycklar på ett säkert sätt</span><span class="sxs-lookup"><span data-stu-id="012a9-122">Create API keys securely</span></span>

<span data-ttu-id="012a9-123">För säkerhet visas ett nytt nyckel värde aldrig på skärmen och är bara tillgängligt med kopierings knappen, som du ser nedan.</span><span class="sxs-lookup"><span data-stu-id="012a9-123">For security, a newly created key value is never shown on the screen and is only available with the Copy button, as shown below.</span></span>

![Hämtar nytt API-nyckel värde](media/creating-APIkeys/PSGallery_CopyCreatedKey.png)

> [!IMPORTANT]
> <span data-ttu-id="012a9-125">Du kan bara kopiera API-nyckelvärdet direkt efter att du har skapat eller uppdaterat det.</span><span class="sxs-lookup"><span data-stu-id="012a9-125">You can only copy the API key value immediately after creating or refreshing it.</span></span> <span data-ttu-id="012a9-126">Den kommer inte att visas och kommer inte att vara tillgänglig igen när sidan har uppdaterats.</span><span class="sxs-lookup"><span data-stu-id="012a9-126">It will not be displayed, and will not be accessible again after the page is refreshed.</span></span> <span data-ttu-id="012a9-127">Om du förlorar nyckelvärdet måste du använda återskapa och kopiera nyckeln när den har återskapats.</span><span class="sxs-lookup"><span data-stu-id="012a9-127">If you lose the key value, you must use Regenerate, and copy the key after it is regenerated.</span></span>

## <a name="key-permissions-and-expiration"></a><span data-ttu-id="012a9-128">Nyckel behörigheter och förfallo datum</span><span class="sxs-lookup"><span data-stu-id="012a9-128">Key permissions and expiration</span></span>

<span data-ttu-id="012a9-129">Begränsade API-nycklar kan tilldela någon av följande behörigheter:</span><span class="sxs-lookup"><span data-stu-id="012a9-129">Scoped API keys can assign any of the following permissions:</span></span>

- <span data-ttu-id="012a9-130">Skicka nya paket</span><span class="sxs-lookup"><span data-stu-id="012a9-130">Push new packages</span></span>
- <span data-ttu-id="012a9-131">Skicka nya eller uppdatera paket</span><span class="sxs-lookup"><span data-stu-id="012a9-131">Push new or update packages</span></span>
- <span data-ttu-id="012a9-132">Lista paket</span><span class="sxs-lookup"><span data-stu-id="012a9-132">Unlist packages</span></span>

<span data-ttu-id="012a9-133">Varje ny nyckel har ett förfallo datum.</span><span class="sxs-lookup"><span data-stu-id="012a9-133">Every new key has an expiration.</span></span> <span data-ttu-id="012a9-134">Värdet för förfallo datum mäts i dagar.</span><span class="sxs-lookup"><span data-stu-id="012a9-134">The expiration value is measured in days.</span></span> <span data-ttu-id="012a9-135">De möjliga värdena för förfallo datum är:</span><span class="sxs-lookup"><span data-stu-id="012a9-135">The possible values for expiration are:</span></span>

- <span data-ttu-id="012a9-136">1 dag</span><span class="sxs-lookup"><span data-stu-id="012a9-136">1 day</span></span>
- <span data-ttu-id="012a9-137">90 dagar</span><span class="sxs-lookup"><span data-stu-id="012a9-137">90 days</span></span>
- <span data-ttu-id="012a9-138">180 dagar</span><span class="sxs-lookup"><span data-stu-id="012a9-138">180 days</span></span>
- <span data-ttu-id="012a9-139">270 dagar</span><span class="sxs-lookup"><span data-stu-id="012a9-139">270 days</span></span>
- <span data-ttu-id="012a9-140">365 dagar (standard)</span><span class="sxs-lookup"><span data-stu-id="012a9-140">365 days (default)</span></span>

<span data-ttu-id="012a9-141">De här inställningarna kan inte ändras när nyckeln har skapats.</span><span class="sxs-lookup"><span data-stu-id="012a9-141">These settings cannot be changed once the key is created.</span></span> <span data-ttu-id="012a9-142">Du kan inte skapa en ny nyckel som aldrig upphör att gälla.</span><span class="sxs-lookup"><span data-stu-id="012a9-142">You cannot create a new key that never expires.</span></span>

## <a name="editing-and-deleting-existing-api-keys"></a><span data-ttu-id="012a9-143">Redigera och ta bort befintliga API-nycklar</span><span class="sxs-lookup"><span data-stu-id="012a9-143">Editing and deleting existing API keys</span></span>

<span data-ttu-id="012a9-144">Du kan ändra vissa inställningar för en befintlig nyckel.</span><span class="sxs-lookup"><span data-stu-id="012a9-144">You can change some settings of an existing key.</span></span> <span data-ttu-id="012a9-145">Som tidigare nämnts kan du inte ändra säkerhets omfattningen för en befintlig API-nyckel eller ändra förfallo datumet.</span><span class="sxs-lookup"><span data-stu-id="012a9-145">As previously noted, you cannot modify the security scope for an existing API key or change the expiration.</span></span> <span data-ttu-id="012a9-146">De ändrings bara alternativen visas på följande skärm bild:</span><span class="sxs-lookup"><span data-stu-id="012a9-146">The changeable options are shown in the following screenshot:</span></span>

![Redigerar ditt API-nyckel värde](media/creating-APIkeys/PSGallery_EditAPIKey.png)

<span data-ttu-id="012a9-148">Om du vill ändra de paket som styrs av en nyckel kan du välja enskilda paket i listan eller ändra BLOB-mönstret.</span><span class="sxs-lookup"><span data-stu-id="012a9-148">To change the packages controlled by a key, you can choose individual packages from the list or change the glob pattern.</span></span>

<span data-ttu-id="012a9-149">Om du klickar på **Återskapa** skapas ett nytt nyckel värde.</span><span class="sxs-lookup"><span data-stu-id="012a9-149">Clicking **Regenerate** creates a new key value.</span></span> <span data-ttu-id="012a9-150">Precis som när du skapade nyckeln första gången måste du **Kopiera** nyckelvärdet direkt efter att det har uppdaterats.</span><span class="sxs-lookup"><span data-stu-id="012a9-150">Just like when you initially created the key, you must **Copy** the key value immediately after updating it.</span></span> <span data-ttu-id="012a9-151">**Kopierings** alternativet är inte tillgängligt när du lämnar den här sidan.</span><span class="sxs-lookup"><span data-stu-id="012a9-151">The **Copy** option is not available once you leave this page.</span></span>

<span data-ttu-id="012a9-152">Om du klickar på **ta bort** visas ett bekräftelse meddelande.</span><span class="sxs-lookup"><span data-stu-id="012a9-152">Clicking **Delete** displays a confirmation message.</span></span> <span data-ttu-id="012a9-153">När en nyckel har tagits bort går den inte att använda.</span><span class="sxs-lookup"><span data-stu-id="012a9-153">Once a key is deleted, it will be unusable.</span></span>

## <a name="key-expiration"></a><span data-ttu-id="012a9-154">Nyckel förfallo datum</span><span class="sxs-lookup"><span data-stu-id="012a9-154">Key expiration</span></span>

<span data-ttu-id="012a9-155">Tio dagar innan förfallo tiden skickar PowerShell-galleriet en varning via e-post till konto innehavaren av API-nyckeln.</span><span class="sxs-lookup"><span data-stu-id="012a9-155">Ten days before the expiration, the PowerShell Gallery sends a warning email the account holder of the API key.</span></span> <span data-ttu-id="012a9-156">Efter förfallo datum är nyckeln oanvändbar.</span><span class="sxs-lookup"><span data-stu-id="012a9-156">After expiration, the key is unusable.</span></span> <span data-ttu-id="012a9-157">Ett varnings meddelande visas längst upp på sidan API-nyckel hantering som visar vilka nycklar som inte längre är giltiga.</span><span class="sxs-lookup"><span data-stu-id="012a9-157">A warning message is displayed at the top of the API key management page showing which keys are no longer valid.</span></span> <span data-ttu-id="012a9-158">Du kan generera ett nytt nyckel värde.</span><span class="sxs-lookup"><span data-stu-id="012a9-158">You can generate a new key value.</span></span>
