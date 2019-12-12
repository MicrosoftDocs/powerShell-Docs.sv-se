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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72352222"
---
# <a name="creating-a-management-odata-web-service"></a>Skapa en Management OData-webbtjänst

Hantering av ODATA IIS-tillägg är en infrastruktur för att skapa en slut punkt för ASP.NET-webbtjänst som visar dina hanterings data, via Windows PowerShell-cmdletar och-skript, som OData web service-enheter. Det sker genom bearbetning av OData-begäranden och konverterar dem till ett Windows PowerShell-anrop. Produkt team kan bygga ovanpå den här infrastrukturen för att skapa slut punkter som exponerar specifika uppsättningar av hanterings data.

Hämta och installera [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) -exemplet. Följ anvisningarna för att distribuera webb tjänsten. I den här webb tjänsten exponeras tjänster och processer genom åtgärder för att skapa, läsa, uppdatera och ta bort (CRUD). CRUD-begäranden som görs till webb tjänsten anropar Windows PowerShell-kommandon som utför de begärda åtgärderna. En mappning mellan CRUD-åtgärderna och de underliggande Windows PowerShell-kommandona implementeras av två schemafiler, schema. MOF och schema. xml. Filen schema. MOF använder MOF-standarden ( [Distributed Management Task Force](https://www.dmtf.org/) ). Filen schema. XML använder ett XML-schema som beskrivs i [resurs mappnings schema](./resource-mapping-schema.md).

> [!IMPORTANT]
> Innan du aktiverar hantering av ODATA IIS-tillägg i Windows Server 2008 R2 SP1 måste följande funktioner vara aktiverade.
>
> 1.  IIS-WebServerRole
> 2.  IIS-WebServer
> 3.  IIS-HttpTracing
> 4.  IIS-ManagementOData

## <a name="steps-for-creating-a-management-odata-web-service"></a>Steg för att skapa en webb tjänst för hantering av OData

I följande avsnitt beskrivs hur du skapar och distribuerar en hantering av OData-webbtjänsten.

- [Lägga till resurser till en hantering av OData-webbtjänsten](./adding-resources-to-a-management-odata-web-service.md)

- [Implementera anpassad auktorisering för en hantering av OData-webbtjänsten](./implementing-custom-authorization-for-a-management-odata-web-service.md)

- [Implementera SessionConfiguration för en hantering av OData-webbtjänst](./implementing-sessionconfiguration-for-a-management-odata-web-service.md)

- [Redigera MOF-schemafilen för en hantering av OData-webbtjänsten](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

- [Redigera XML-schemafilen för en hantering av OData-webbtjänsten](./authoring-the-xml-schema-file-for-a-management-odata-web-service.md)

- [Redigera Web. config-filen för en hantering av OData-webbtjänsten](./authoring-the-web-config-file-for-a-management-odata-web-service.md)

- [Distribuera en hantering av OData-webbtjänst](./deploying-a-management-odata-web-service.md)

- [Associera OData-enheter för hantering](./associating-management-odata-entities.md)

## <a name="see-also"></a>Se även

[Hantering av ODATA IIS-tillägg schema filer](./management-odata-iis-extension-schema-files.md)
