---
ms.date: 09/13/2016
ms.topic: reference
title: Uppdaterings bar hjälp redigering-steg-för-steg
description: Uppdaterings bar hjälp redigering-steg-för-steg
ms.openlocfilehash: c4aecdb801cac16c9cb07853317835fd87e6a0a8
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92658813"
---
# <a name="updatable-help-authoring-step-by-step"></a><span data-ttu-id="1c021-103">Redigering av uppdateringsbar hjälp: Steg för steg</span><span class="sxs-lookup"><span data-stu-id="1c021-103">Updatable Help Authoring: Step-by-Step</span></span>

<span data-ttu-id="1c021-104">I de här dokumenten visas stegen i processen för att redigera uppdaterings bar hjälp.</span><span class="sxs-lookup"><span data-stu-id="1c021-104">This documents lists the steps in the process of authoring Updatable Help.</span></span>

## <a name="authoring-updatable-help-step-by-step"></a><span data-ttu-id="1c021-105">Redigering av uppdaterbar hjälp: steg för steg</span><span class="sxs-lookup"><span data-stu-id="1c021-105">Authoring Updatable Help: Step-by-Step</span></span>

<span data-ttu-id="1c021-106">Uppdaterings bara hjälp har utformats för slutanvändare, men det ger också betydande fördelar för att skapa och hjälpa skribenter, inklusive möjlighet att lägga till innehåll, åtgärda fel, leverera i flera användar gränssnitts kulturer och svara på användar kommentarer och förfrågningar, långt efter att modulen har levererats.</span><span class="sxs-lookup"><span data-stu-id="1c021-106">Updatable Help is designed for end-users, but it also provides significant benefits to module authors and help writers, including the ability to add content, fix errors, deliver in multiple UI cultures, and respond to user comments and requests, long after the module has shipped.</span></span> <span data-ttu-id="1c021-107">I det här avsnittet beskrivs hur du paketerar och laddar upp hjälpfiler så att användarna kan ladda ned och installera dem med hjälp av cmdletarna [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) och [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) .</span><span class="sxs-lookup"><span data-stu-id="1c021-107">This topic explains how you package and upload help files so that users can download and install them by using the [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets.</span></span>

<span data-ttu-id="1c021-108">Följande steg ger en översikt över processen för att stödja uppdaterings bar hjälp.</span><span class="sxs-lookup"><span data-stu-id="1c021-108">The following steps provide an overview of the process of supporting Updatable Help.</span></span>

### <a name="step-1-find-an-internet-site-for-your-help-files"></a><span data-ttu-id="1c021-109">Steg 1: hitta en Internet webbplats för dina hjälpfiler</span><span class="sxs-lookup"><span data-stu-id="1c021-109">Step 1: Find an internet site for your help files</span></span>

<span data-ttu-id="1c021-110">Det första steget i att skapa en uppdaterings bar hjälp är att hitta en Internet plats för modulens hjälpfiler.</span><span class="sxs-lookup"><span data-stu-id="1c021-110">The first step in creating updatable help is to find an internet location for your module's help files.</span></span> <span data-ttu-id="1c021-111">Du kan faktiskt använda två olika platser.</span><span class="sxs-lookup"><span data-stu-id="1c021-111">Actually, you can use two different locations.</span></span> <span data-ttu-id="1c021-112">Du kan behålla modulens hjälp informations fil (HelpInfo XML-beskrivs nedan) på en Internet plats och CAB-filerna för hjälp innehåll på en annan Internet plats.</span><span class="sxs-lookup"><span data-stu-id="1c021-112">You can keep your module's help information file (HelpInfo XML - described below) at one internet location and the help content CAB files at another internet location.</span></span> <span data-ttu-id="1c021-113">Alla CAB-filer för hjälp innehåll för en modul måste finnas på samma plats.</span><span class="sxs-lookup"><span data-stu-id="1c021-113">All help content CAB files for a module must be in the same location.</span></span> <span data-ttu-id="1c021-114">Du kan placera CAB-filer för hjälp innehåll för olika moduler på samma plats.</span><span class="sxs-lookup"><span data-stu-id="1c021-114">You can place help content CAB files for different modules in the same location.</span></span>

### <a name="step-2-add-a-helpinfouri-key-to-your-module-manifest"></a><span data-ttu-id="1c021-115">Steg 2: Lägg till en HelpInfoURI-nyckel till modulen manifest</span><span class="sxs-lookup"><span data-stu-id="1c021-115">Step 2: Add a HelpInfoURI key to your module manifest</span></span>

<span data-ttu-id="1c021-116">Lägg till en **HelpInfoURI** -nyckel till modulen manifest.</span><span class="sxs-lookup"><span data-stu-id="1c021-116">Add a **HelpInfoURI** key to your module manifest.</span></span> <span data-ttu-id="1c021-117">Nyckelns värde är Uniform Resource Identifier (URI) för platsen för XML-HelpInfo för modulen.</span><span class="sxs-lookup"><span data-stu-id="1c021-117">The value of the key is the Uniform Resource Identifier (URI) of the location of the HelpInfo XML information file for your module.</span></span> <span data-ttu-id="1c021-118">För säkerhet måste adressen börja med "http" eller "https".</span><span class="sxs-lookup"><span data-stu-id="1c021-118">For security, the address must begin with "http" or "https".</span></span> <span data-ttu-id="1c021-119">URI: n måste ange en Internet plats, men får inte innehålla HelpInfo XML-filnamn.</span><span class="sxs-lookup"><span data-stu-id="1c021-119">The URI should specify an internet location, but must not include the HelpInfo XML filename.</span></span>

<span data-ttu-id="1c021-120">Exempel:</span><span class="sxs-lookup"><span data-stu-id="1c021-120">For example:</span></span>

```powershell

@{
RootModule = TestModule.psm1
ModuleVersion = '2.0'
HelpInfoURI = 'https://go.microsoft.com/fwlink/?LinkID=0123'
}
```

### <a name="step-3-create-a-helpinfo-xml-file"></a><span data-ttu-id="1c021-121">Steg 3: skapa en HelpInfo XML-fil</span><span class="sxs-lookup"><span data-stu-id="1c021-121">Step 3: Create a HelpInfo XML file</span></span>

<span data-ttu-id="1c021-122">XML-HelpInfo innehåller URI: n för Internet platsen för dina hjälpfiler och versions numren för de senaste hjälpfilerna för modulen i varje GRÄNSSNITTs kultur som stöds.</span><span class="sxs-lookup"><span data-stu-id="1c021-122">The HelpInfo XML information file contains the URI of the internet location of your help files and the version numbers of the newest help files for your module in each supported UI culture.</span></span> <span data-ttu-id="1c021-123">Alla Windows PowerShell-moduler har en HelpInfo XML-fil.</span><span class="sxs-lookup"><span data-stu-id="1c021-123">Every Windows PowerShell module has one HelpInfo XML file.</span></span> <span data-ttu-id="1c021-124">När du uppdaterar dina hjälpfiler redigerar eller ersätter du HelpInfo XML-filen. du lägger inte till ett annat.</span><span class="sxs-lookup"><span data-stu-id="1c021-124">When you update your help files, you edit or replace the HelpInfo XML file; you do not add another one.</span></span> <span data-ttu-id="1c021-125">Mer information finns i [så här skapar du en HelpInfo XML-fil](./how-to-create-a-helpinfo-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="1c021-125">For more information, see [How to Create a HelpInfo XML File](./how-to-create-a-helpinfo-xml-file.md).</span></span>

### <a name="step-4-create-cab-files"></a><span data-ttu-id="1c021-126">Steg 4: skapa CAB-filer</span><span class="sxs-lookup"><span data-stu-id="1c021-126">Step 4: Create CAB files</span></span>

<span data-ttu-id="1c021-127">Använd ett verktyg som skapar CAB- `.cab` filer, till exempel `MakeCab.exe` , för att skapa en CAB-fil som innehåller hjälpfilerna för modulen.</span><span class="sxs-lookup"><span data-stu-id="1c021-127">Use a tool that creates cabinet (`.cab`) files, such as `MakeCab.exe`, to create a CAB file that contains the help files for your module.</span></span> <span data-ttu-id="1c021-128">Skapa en separat CAB-fil för hjälpfilerna i varje GRÄNSSNITTs kultur som stöds.</span><span class="sxs-lookup"><span data-stu-id="1c021-128">Create a separate CAB file for the help files in each supported UI culture.</span></span> <span data-ttu-id="1c021-129">Mer information finns i [så här förbereder du uppdaterings bara CAB-filer](./how-to-prepare-updatable-help-cab-files.md).</span><span class="sxs-lookup"><span data-stu-id="1c021-129">For more information, see [How to Prepare Updatable Help CAB Files](./how-to-prepare-updatable-help-cab-files.md).</span></span>

### <a name="step-5-upload-your-files"></a><span data-ttu-id="1c021-130">Steg 5: Ladda upp filer</span><span class="sxs-lookup"><span data-stu-id="1c021-130">Step 5: Upload your files</span></span>

<span data-ttu-id="1c021-131">Om du vill publicera nya eller uppdaterade hjälpfiler laddar du upp CAB-filerna till Internet platsen som anges av **HelpContentUri** -elementet i HelpInfo XML-filen.</span><span class="sxs-lookup"><span data-stu-id="1c021-131">To publish new or updated help files, upload the CAB files to the internet location that is specified by the **HelpContentUri** element in the HelpInfo XML file.</span></span> <span data-ttu-id="1c021-132">Ladda sedan upp XML-filen HelpInfo till den Internet plats som anges av värdet för **HelpInfoUri** -nyckeln i modulen manifest.</span><span class="sxs-lookup"><span data-stu-id="1c021-132">Then, upload the HelpInfo XML file to the internet location that is specified by the value of the **HelpInfoUri** key in the module manifest.</span></span>
