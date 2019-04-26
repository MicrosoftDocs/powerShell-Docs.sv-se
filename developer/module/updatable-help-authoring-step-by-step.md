---
title: 'Redigering av uppdateringsbar hjälp: Stegvisa | Microsoft Docs'
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10098160-c6b4-4339-b8ff-2c4f8cc0699b
caps.latest.revision: 13
ms.openlocfilehash: fbc77cc0fafce93d239da1c459d4b761b21ef3cb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082132"
---
# <a name="updatable-help-authoring-step-by-step"></a><span data-ttu-id="fab94-102">Redigering av uppdateringsbar hjälp: Steg för steg</span><span class="sxs-lookup"><span data-stu-id="fab94-102">Updatable Help Authoring: Step-by-Step</span></span>

<span data-ttu-id="fab94-103">Detta dokument innehåller stegen redigering uppdateringsbar hjälp.</span><span class="sxs-lookup"><span data-stu-id="fab94-103">This documents lists the steps in the process of authoring Updatable Help.</span></span>

## <a name="authoring-updatable-help-step-by-step"></a><span data-ttu-id="fab94-104">Redigera uppdateringsbar hjälp: Steg för steg</span><span class="sxs-lookup"><span data-stu-id="fab94-104">Authoring Updatable Help: Step-by-Step</span></span>

<span data-ttu-id="fab94-105">Uppdateringsbar hjälp är avsedd för slutanvändare, men den också ger betydande fördelar modulskapare och hjälp-skrivare, inklusive möjligheten att lägga till innehåll, åtgärda fel, leverera i flera Användargränssnittet kulturer och svara på användarkommentarer och begäranden, lång tid efter den modulen har levererats.</span><span class="sxs-lookup"><span data-stu-id="fab94-105">Updatable Help is designed for end-users, but it also provides significant benefits to module authors and help writers, including the ability to add content, fix errors, deliver in multiple UI cultures, and respond to user comments and requests, long after the module has shipped.</span></span> <span data-ttu-id="fab94-106">Det här avsnittet beskriver hur du paketerar och hjälp med att ladda upp filer så att användarna kan ladda ned och installera dem med hjälp av den [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) och [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdletar.</span><span class="sxs-lookup"><span data-stu-id="fab94-106">This topic explains how you package and upload help files so that users can download and install them by using the [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets.</span></span>

<span data-ttu-id="fab94-107">Följande steg ger en översikt av processen för att stödja uppdateringsbar hjälp.</span><span class="sxs-lookup"><span data-stu-id="fab94-107">The following steps provide an overview of the process of supporting Updatable Help.</span></span>

### <a name="step-1-find-an-internet-site-for-your-help-files"></a><span data-ttu-id="fab94-108">Steg 1: Hitta en webbplats för din hjälpfiler</span><span class="sxs-lookup"><span data-stu-id="fab94-108">Step 1: Find an Internet site for your help files</span></span>

<span data-ttu-id="fab94-109">Det första steget i att skapa uppdateringsbar hjälp är att hitta en plats på Internet för din modul hjälpfiler.</span><span class="sxs-lookup"><span data-stu-id="fab94-109">The first step in creating updatable help is to find an Internet location for your module's help files.</span></span> <span data-ttu-id="fab94-110">Du kan faktiskt använda två olika platser.</span><span class="sxs-lookup"><span data-stu-id="fab94-110">Actually, you can use two different locations.</span></span> <span data-ttu-id="fab94-111">Du kan behålla din modul hjälpfilen information (HelpInfo XML - beskrivs nedan) på en plats på Internet och help CAB innehållsfilerna på en annan Internetplats.</span><span class="sxs-lookup"><span data-stu-id="fab94-111">You can keep your module's help information file (HelpInfo XML - described below) at one Internet location and the help content CAB files at another Internet location.</span></span> <span data-ttu-id="fab94-112">Alla hjälp innehåll CAB-filer för en modul måste vara på samma plats.</span><span class="sxs-lookup"><span data-stu-id="fab94-112">All help content CAB files for a module must be in the same location.</span></span> <span data-ttu-id="fab94-113">Du kan placera hjälp innehåll CAB-filer för olika moduler på samma plats.</span><span class="sxs-lookup"><span data-stu-id="fab94-113">You can place help content CAB files for different modules in the same location.</span></span>

### <a name="step-2-add-a-helpinfouri-key-to-your-module-manifest"></a><span data-ttu-id="fab94-114">Steg 2: Lägg till en HelpInfoURI nyckel till din modulmanifestet</span><span class="sxs-lookup"><span data-stu-id="fab94-114">Step 2: Add a HelpInfoURI key to your module manifest</span></span>

<span data-ttu-id="fab94-115">Lägg till en **HelpInfoURI** avgörande för att din modulmanifestet.</span><span class="sxs-lookup"><span data-stu-id="fab94-115">Add a **HelpInfoURI** key to your module manifest.</span></span> <span data-ttu-id="fab94-116">Värdet för nyckeln är den identifierare URI (Uniform Resource) för platsen för filen HelpInfo XML information för din modul.</span><span class="sxs-lookup"><span data-stu-id="fab94-116">The value of the key is the Uniform Resource Identifier (URI) of the location of the HelpInfo XML information file for your module.</span></span> <span data-ttu-id="fab94-117">Av säkerhetsskäl måste adressen börja med ”http” eller ”https”.</span><span class="sxs-lookup"><span data-stu-id="fab94-117">For security, the address must begin with "http" or "https".</span></span> <span data-ttu-id="fab94-118">URI: N ska ange en plats på Internet, men får inte innehålla HelpInfo XML-filnamn.</span><span class="sxs-lookup"><span data-stu-id="fab94-118">The URI should specify an Internet location, but must not include the HelpInfo XML file name.</span></span>

<span data-ttu-id="fab94-119">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="fab94-119">For example:</span></span>

```powershell

@{
RootModule = TestModule.psm1
ModuleVersion = '2.0'
HelpInfoURI = 'http://go.microsoft.com/fwlink/?LinkID=0123'
}
```

### <a name="step-3-create-a-helpinfo-xml-file"></a><span data-ttu-id="fab94-120">Steg 3: Skapa en HelpInfo XML-fil</span><span class="sxs-lookup"><span data-stu-id="fab94-120">Step 3: Create a HelpInfo XML file</span></span>

<span data-ttu-id="fab94-121">Den information HelpInfo XML-filen innehåller URI för Internet-platsen för din hjälpfiler och versionsnumren för de senaste hjälpfilerna för i varje UI-kultur som stöds.</span><span class="sxs-lookup"><span data-stu-id="fab94-121">The HelpInfo XML information file contains the URI of the Internet location of your help files and the version numbers of the newest help files for your module in each supported UI culture.</span></span> <span data-ttu-id="fab94-122">Alla Windows PowerShell-modulen har en HelpInfo XML-fil.</span><span class="sxs-lookup"><span data-stu-id="fab94-122">Every Windows PowerShell module has one HelpInfo XML file.</span></span> <span data-ttu-id="fab94-123">När du uppdaterar din hjälpfiler du redigera eller ersätta HelpInfo XML-filen. du inte lägga till en annan.</span><span class="sxs-lookup"><span data-stu-id="fab94-123">When you update your help files, you edit or replace the HelpInfo XML file; you do not add another one.</span></span> <span data-ttu-id="fab94-124">Mer information finns i [så här skapar du en XML-fil med HelpInfo](./how-to-create-a-helpinfo-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="fab94-124">For more information, see [How to Create a HelpInfo XML File](./how-to-create-a-helpinfo-xml-file.md).</span></span>

### <a name="step-4-sign-your-help-files"></a><span data-ttu-id="fab94-125">Steg 4: Registrera din hjälpfiler</span><span class="sxs-lookup"><span data-stu-id="fab94-125">Step 4: Sign your help files</span></span>

<span data-ttu-id="fab94-126">Digitala signaturer krävs inte, men de är en rekommendation för bästa praxis när du delar filer.</span><span class="sxs-lookup"><span data-stu-id="fab94-126">Digital signatures are not required, but they are a best-practice recommendation whenever you are sharing files.</span></span>

### <a name="step-5-create-cab-files"></a><span data-ttu-id="fab94-127">Steg 5: Skapa CAB-filer</span><span class="sxs-lookup"><span data-stu-id="fab94-127">Step 5: Create CAB files</span></span>

<span data-ttu-id="fab94-128">Använd ett verktyg som skapar CAB-filer, till exempel MakeCab.exe att skapa en. CAB-filen som innehåller hjälpfilerna som för.</span><span class="sxs-lookup"><span data-stu-id="fab94-128">Use a tool that creates cabinet (.cab) files, such as MakeCab.exe, to create a .CAB file that contains the help files for your module.</span></span> <span data-ttu-id="fab94-129">Skapa en separat CAB-fil för hjälpfilerna i varje UI-kultur som stöds.</span><span class="sxs-lookup"><span data-stu-id="fab94-129">Create a separate CAB file for the help files in each supported UI culture.</span></span> <span data-ttu-id="fab94-130">Mer information finns i [hur du förbereder uppdateringsbar hjälp CAB-filer](./how-to-prepare-updatable-help-cab-files.md).</span><span class="sxs-lookup"><span data-stu-id="fab94-130">For more information, see [How to Prepare Updatable Help CAB Files](./how-to-prepare-updatable-help-cab-files.md).</span></span>

### <a name="step-6-upload-your-files"></a><span data-ttu-id="fab94-131">Steg 6: Ladda upp dina filer</span><span class="sxs-lookup"><span data-stu-id="fab94-131">Step 6: Upload your files</span></span>

<span data-ttu-id="fab94-132">Om du vill publicera nya eller uppdaterade hjälpfiler överföra CAB-filer till den Internet-plats som anges av den **HelpContentUri** element i HelpInfo XML-filen.</span><span class="sxs-lookup"><span data-stu-id="fab94-132">To publish new or updated help files, upload the CAB files to the Internet location that is specified by the **HelpContentUri** element in the HelpInfo XML file.</span></span> <span data-ttu-id="fab94-133">Ladda sedan upp HelpInfo XML-filen till den Internet-plats som anges av värdet för den **HelpInfoUri** nyckeln i modulmanifestet.</span><span class="sxs-lookup"><span data-stu-id="fab94-133">Then, upload the HelpInfo XML file to the Internet location that is specified by the value of the **HelpInfoUri** key in the module manifest.</span></span>
