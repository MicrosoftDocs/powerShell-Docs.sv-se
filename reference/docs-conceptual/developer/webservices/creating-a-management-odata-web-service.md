---
title: Skapa en hantering av OData-webbtjänsten | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 06b1b050-0bf7-48f5-ba05-43f489d597c0
caps.latest.revision: 10
ms.openlocfilehash: 476fce9fc087b870bad93a9204a820c5a84df99e
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72352222"
---
# <a name="creating-a-management-odata-web-service"></a><span data-ttu-id="ae9d2-102">Skapa en Management OData-webbtjänst</span><span class="sxs-lookup"><span data-stu-id="ae9d2-102">Creating a Management OData Web Service</span></span>

<span data-ttu-id="ae9d2-103">Hantering av ODATA IIS-tillägg är en infrastruktur för att skapa en slut punkt för ASP.NET-webbtjänst som visar dina hanterings data, via Windows PowerShell-cmdletar och-skript, som OData web service-enheter.</span><span class="sxs-lookup"><span data-stu-id="ae9d2-103">Management ODATA IIS Extension is an infrastructure for creating an ASP.NET web service end point that exposes your management data, accessed through Windows PowerShell cmdlets and scripts, as OData Web service entities.</span></span> <span data-ttu-id="ae9d2-104">Det sker genom bearbetning av OData-begäranden och konverterar dem till ett Windows PowerShell-anrop.</span><span class="sxs-lookup"><span data-stu-id="ae9d2-104">It does that by processing OData requests and converting them into a Windows PowerShell invocation.</span></span> <span data-ttu-id="ae9d2-105">Produkt team kan bygga ovanpå den här infrastrukturen för att skapa slut punkter som exponerar specifika uppsättningar av hanterings data.</span><span class="sxs-lookup"><span data-stu-id="ae9d2-105">Product teams can build on top of this infrastructure to create endpoints that expose specific sets of management data.</span></span>

<span data-ttu-id="ae9d2-106">Hämta och installera [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) -exemplet.</span><span class="sxs-lookup"><span data-stu-id="ae9d2-106">Download and install the [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) sample.</span></span> <span data-ttu-id="ae9d2-107">Följ anvisningarna för att distribuera webb tjänsten.</span><span class="sxs-lookup"><span data-stu-id="ae9d2-107">Follow the instructions to deploy the web service.</span></span> <span data-ttu-id="ae9d2-108">I den här webb tjänsten exponeras tjänster och processer genom åtgärder för att skapa, läsa, uppdatera och ta bort (CRUD).</span><span class="sxs-lookup"><span data-stu-id="ae9d2-108">This web service exposes Services and Processes through Create, Read, Update, and Delete (CRUD) operations.</span></span> <span data-ttu-id="ae9d2-109">CRUD-begäranden som görs till webb tjänsten anropar Windows PowerShell-kommandon som utför de begärda åtgärderna.</span><span class="sxs-lookup"><span data-stu-id="ae9d2-109">CRUD requests made to the web service invoke  Windows PowerShell commands that perform the requested operations.</span></span> <span data-ttu-id="ae9d2-110">En mappning mellan CRUD-åtgärderna och de underliggande Windows PowerShell-kommandona implementeras av två schemafiler, schema. MOF och schema. xml.</span><span class="sxs-lookup"><span data-stu-id="ae9d2-110">A mapping between the CRUD operations and the underlying Windows PowerShell commands is implemented by two schema files, schema.mof and schema.xml.</span></span> <span data-ttu-id="ae9d2-111">Filen schema. MOF använder MOF-standarden ( [Distributed Management Task Force](https://www.dmtf.org/) ).</span><span class="sxs-lookup"><span data-stu-id="ae9d2-111">The schema.mof file uses the [Distributed Management  Task Force](https://www.dmtf.org/) (DMTF) Managed Object (MOF) standard.</span></span> <span data-ttu-id="ae9d2-112">Filen schema. XML använder ett XML-schema som beskrivs i [resurs mappnings schema](./resource-mapping-schema.md).</span><span class="sxs-lookup"><span data-stu-id="ae9d2-112">The schema.xml file uses an XML schema that is described in [Resource Mapping Schema](./resource-mapping-schema.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ae9d2-113">Innan du aktiverar hantering av ODATA IIS-tillägg i Windows Server 2008 R2 SP1 måste följande funktioner vara aktiverade.</span><span class="sxs-lookup"><span data-stu-id="ae9d2-113">Before you enabling Management ODATA IIS Extension on Windows Server 2008 R2 SP1, the following features must be enabled.</span></span>
>
> 1.  <span data-ttu-id="ae9d2-114">IIS-WebServerRole</span><span class="sxs-lookup"><span data-stu-id="ae9d2-114">IIS-WebServerRole</span></span>
> 2.  <span data-ttu-id="ae9d2-115">IIS-WebServer</span><span class="sxs-lookup"><span data-stu-id="ae9d2-115">IIS-WebServer</span></span>
> 3.  <span data-ttu-id="ae9d2-116">IIS-HttpTracing</span><span class="sxs-lookup"><span data-stu-id="ae9d2-116">IIS-HttpTracing</span></span>
> 4.  <span data-ttu-id="ae9d2-117">IIS-ManagementOData</span><span class="sxs-lookup"><span data-stu-id="ae9d2-117">IIS-ManagementOData</span></span>

## <a name="steps-for-creating-a-management-odata-web-service"></a><span data-ttu-id="ae9d2-118">Steg för att skapa en webb tjänst för hantering av OData</span><span class="sxs-lookup"><span data-stu-id="ae9d2-118">Steps for creating a Management OData web service</span></span>

<span data-ttu-id="ae9d2-119">I följande avsnitt beskrivs hur du skapar och distribuerar en hantering av OData-webbtjänsten.</span><span class="sxs-lookup"><span data-stu-id="ae9d2-119">The following topics describe how to create and deploy a Management OData web service.</span></span>

- [<span data-ttu-id="ae9d2-120">Lägga till resurser till en hantering av OData-webbtjänsten</span><span class="sxs-lookup"><span data-stu-id="ae9d2-120">Adding Resources to a Management OData Web Service</span></span>](./adding-resources-to-a-management-odata-web-service.md)

- [<span data-ttu-id="ae9d2-121">Implementera anpassad auktorisering för en hantering av OData-webbtjänsten</span><span class="sxs-lookup"><span data-stu-id="ae9d2-121">Implementing Custom Authorization for a Management OData web service</span></span>](./implementing-custom-authorization-for-a-management-odata-web-service.md)

- [<span data-ttu-id="ae9d2-122">Implementera SessionConfiguration för en hantering av OData-webbtjänst</span><span class="sxs-lookup"><span data-stu-id="ae9d2-122">Implementing SessionConfiguration for a Management OData web service</span></span>](./implementing-sessionconfiguration-for-a-management-odata-web-service.md)

- [<span data-ttu-id="ae9d2-123">Redigera MOF-schemafilen för en hantering av OData-webbtjänsten</span><span class="sxs-lookup"><span data-stu-id="ae9d2-123">Authoring the MOF schema file for a Management OData web service</span></span>](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

- [<span data-ttu-id="ae9d2-124">Redigera XML-schemafilen för en hantering av OData-webbtjänsten</span><span class="sxs-lookup"><span data-stu-id="ae9d2-124">Authoring the XML schema file for a Management OData web service</span></span>](./authoring-the-xml-schema-file-for-a-management-odata-web-service.md)

- [<span data-ttu-id="ae9d2-125">Redigera Web. config-filen för en hantering av OData-webbtjänsten</span><span class="sxs-lookup"><span data-stu-id="ae9d2-125">Authoring the Web.config file for a Management OData web service</span></span>](./authoring-the-web-config-file-for-a-management-odata-web-service.md)

- [<span data-ttu-id="ae9d2-126">Distribuera en hantering av OData-webbtjänst</span><span class="sxs-lookup"><span data-stu-id="ae9d2-126">Deploying a Management OData web service</span></span>](./deploying-a-management-odata-web-service.md)

- [<span data-ttu-id="ae9d2-127">Associera OData-enheter för hantering</span><span class="sxs-lookup"><span data-stu-id="ae9d2-127">Associating Management OData Entities</span></span>](./associating-management-odata-entities.md)

## <a name="see-also"></a><span data-ttu-id="ae9d2-128">Se även</span><span class="sxs-lookup"><span data-stu-id="ae9d2-128">See Also</span></span>

[<span data-ttu-id="ae9d2-129">Hantering av ODATA IIS-tillägg schema filer</span><span class="sxs-lookup"><span data-stu-id="ae9d2-129">Management ODATA IIS Extension Schema Files</span></span>](./management-odata-iis-extension-schema-files.md)
