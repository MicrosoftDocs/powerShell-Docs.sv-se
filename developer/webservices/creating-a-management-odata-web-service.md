---
title: Skapa en Management OData-webbtjänst | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 06b1b050-0bf7-48f5-ba05-43f489d597c0
caps.latest.revision: 10
ms.openlocfilehash: 476fce9fc087b870bad93a9204a820c5a84df99e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847252"
---
# <a name="creating-a-management-odata-web-service"></a><span data-ttu-id="358ff-102">Skapa en Management OData-webbtjänst</span><span class="sxs-lookup"><span data-stu-id="358ff-102">Creating a Management OData Web Service</span></span>

<span data-ttu-id="358ff-103">Management ODATA IIS Extension är en infrastruktur för att skapa en ASP.NET web service slutpunkt som visar dina hanteringsdata som nås via Windows PowerShell-cmdlets och skript som OData Web service-entiteter.</span><span class="sxs-lookup"><span data-stu-id="358ff-103">Management ODATA IIS Extension is an infrastructure for creating an ASP.NET web service end point that exposes your management data, accessed through Windows PowerShell cmdlets and scripts, as OData Web service entities.</span></span> <span data-ttu-id="358ff-104">Detta sker som som bearbetar begäranden från OData och konvertera dem till ett Windows PowerShell-anrop.</span><span class="sxs-lookup"><span data-stu-id="358ff-104">It does that by processing OData requests and converting them into a Windows PowerShell invocation.</span></span> <span data-ttu-id="358ff-105">Produktgrupper kan byggas ovanpå den här infrastrukturen för att skapa slutpunkter som visar specifika uppsättningar av data Manager.</span><span class="sxs-lookup"><span data-stu-id="358ff-105">Product teams can build on top of this infrastructure to create endpoints that expose specific sets of management data.</span></span>

<span data-ttu-id="358ff-106">Ladda ned och installera den [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) exemplet.</span><span class="sxs-lookup"><span data-stu-id="358ff-106">Download and install the [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) sample.</span></span> <span data-ttu-id="358ff-107">Följ anvisningarna för att distribuera webbtjänsten.</span><span class="sxs-lookup"><span data-stu-id="358ff-107">Follow the instructions to deploy the web service.</span></span> <span data-ttu-id="358ff-108">Den här webbtjänsten exponerar tjänster och processer via operations skapa, läsa, uppdatera och ta bort (CRUD).</span><span class="sxs-lookup"><span data-stu-id="358ff-108">This web service exposes Services and Processes through Create, Read, Update, and Delete (CRUD) operations.</span></span> <span data-ttu-id="358ff-109">CRUD-begäranden som görs till webbtjänsten anropar Windows PowerShell-kommandon som utför de begärda åtgärderna.</span><span class="sxs-lookup"><span data-stu-id="358ff-109">CRUD requests made to the web service invoke  Windows PowerShell commands that perform the requested operations.</span></span> <span data-ttu-id="358ff-110">En mappning mellan CRUD-åtgärder och de underliggande Windows PowerShell-kommandona har implementerats av två schemafiler, schema.mof och schema.xml.</span><span class="sxs-lookup"><span data-stu-id="358ff-110">A mapping between the CRUD operations and the underlying Windows PowerShell commands is implemented by two schema files, schema.mof and schema.xml.</span></span> <span data-ttu-id="358ff-111">Filen schema.mof använder den [Distributed Management Task Force](https://www.dmtf.org/) (DMTF) hanterade objekt (MOF) standard.</span><span class="sxs-lookup"><span data-stu-id="358ff-111">The schema.mof file uses the [Distributed Management  Task Force](https://www.dmtf.org/) (DMTF) Managed Object (MOF) standard.</span></span> <span data-ttu-id="358ff-112">Filen schema.xml använder ett XML-schema som beskrivs i [Resource mappning schemat](./resource-mapping-schema.md).</span><span class="sxs-lookup"><span data-stu-id="358ff-112">The schema.xml file uses an XML schema that is described in [Resource Mapping Schema](./resource-mapping-schema.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="358ff-113">Följande funktioner måste aktiveras innan du aktiverar Management ODATA IIS-tillägg på Windows Server 2008 R2 SP1.</span><span class="sxs-lookup"><span data-stu-id="358ff-113">Before you enabling Management ODATA IIS Extension on Windows Server 2008 R2 SP1, the following features must be enabled.</span></span>
>
> 1.  <span data-ttu-id="358ff-114">IIS-WebServerRole</span><span class="sxs-lookup"><span data-stu-id="358ff-114">IIS-WebServerRole</span></span>
> 2.  <span data-ttu-id="358ff-115">IIS-WebServer</span><span class="sxs-lookup"><span data-stu-id="358ff-115">IIS-WebServer</span></span>
> 3.  <span data-ttu-id="358ff-116">IIS-HttpTracing</span><span class="sxs-lookup"><span data-stu-id="358ff-116">IIS-HttpTracing</span></span>
> 4.  <span data-ttu-id="358ff-117">IIS-ManagementOData</span><span class="sxs-lookup"><span data-stu-id="358ff-117">IIS-ManagementOData</span></span>

## <a name="steps-for-creating-a-management-odata-web-service"></a><span data-ttu-id="358ff-118">Anvisningar för att skapa en Management OData-webbtjänst</span><span class="sxs-lookup"><span data-stu-id="358ff-118">Steps for creating a Management OData web service</span></span>

<span data-ttu-id="358ff-119">I följande avsnitt beskrivs hur du skapar och distribuerar en Management OData-webbtjänst.</span><span class="sxs-lookup"><span data-stu-id="358ff-119">The following topics describe how to create and deploy a Management OData web service.</span></span>

- [<span data-ttu-id="358ff-120">Att lägga till resurser till en Management OData-webbtjänst</span><span class="sxs-lookup"><span data-stu-id="358ff-120">Adding Resources to a Management OData Web Service</span></span>](./adding-resources-to-a-management-odata-web-service.md)

- [<span data-ttu-id="358ff-121">Implementera anpassad auktorisering för en Management OData-webbtjänst</span><span class="sxs-lookup"><span data-stu-id="358ff-121">Implementing Custom Authorization for a Management OData web service</span></span>](./implementing-custom-authorization-for-a-management-odata-web-service.md)

- [<span data-ttu-id="358ff-122">Implementera SessionConfiguration för en Management OData-webbtjänst</span><span class="sxs-lookup"><span data-stu-id="358ff-122">Implementing SessionConfiguration for a Management OData web service</span></span>](./implementing-sessionconfiguration-for-a-management-odata-web-service.md)

- [<span data-ttu-id="358ff-123">Redigera MOF-filen för schemat för en Management OData-webbtjänst</span><span class="sxs-lookup"><span data-stu-id="358ff-123">Authoring the MOF schema file for a Management OData web service</span></span>](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

- [<span data-ttu-id="358ff-124">Redigera filen XML-schemat för en Management OData-webbtjänst</span><span class="sxs-lookup"><span data-stu-id="358ff-124">Authoring the XML schema file for a Management OData web service</span></span>](./authoring-the-xml-schema-file-for-a-management-odata-web-service.md)

- [<span data-ttu-id="358ff-125">Redigera filen Web.config för en Management OData-webbtjänst</span><span class="sxs-lookup"><span data-stu-id="358ff-125">Authoring the Web.config file for a Management OData web service</span></span>](./authoring-the-web-config-file-for-a-management-odata-web-service.md)

- [<span data-ttu-id="358ff-126">Distribuera en Management OData-webbtjänst</span><span class="sxs-lookup"><span data-stu-id="358ff-126">Deploying a Management OData web service</span></span>](./deploying-a-management-odata-web-service.md)

- [<span data-ttu-id="358ff-127">Associera Management OData-entiteter</span><span class="sxs-lookup"><span data-stu-id="358ff-127">Associating Management OData Entities</span></span>](./associating-management-odata-entities.md)

## <a name="see-also"></a><span data-ttu-id="358ff-128">Se även</span><span class="sxs-lookup"><span data-stu-id="358ff-128">See Also</span></span>

[<span data-ttu-id="358ff-129">Management ODATA IIS-tillägget schemafiler</span><span class="sxs-lookup"><span data-stu-id="358ff-129">Management ODATA IIS Extension Schema Files</span></span>](./management-odata-iis-extension-schema-files.md)
