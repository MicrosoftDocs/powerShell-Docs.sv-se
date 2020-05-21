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
ms.openlocfilehash: f903c99300a34c0dfbed598738e96142588d69d9
ms.sourcegitcommit: 17d798a041851382b406ed789097843faf37692d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/20/2020
ms.locfileid: "83691484"
---
# <a name="creating-a-management-odata-web-service"></a>Skapa en Management OData-webbtjänst

Hantering av ODATA IIS-tillägg är en infrastruktur för att skapa en slut punkt för ASP.NET-webbtjänst som visar dina hanterings data, via Windows PowerShell-cmdletar och-skript, som OData web service-enheter. Det sker genom bearbetning av OData-begäranden och konverterar dem till ett Windows PowerShell-anrop. Produkt team kan bygga ovanpå den här infrastrukturen för att skapa slut punkter som exponerar specifika uppsättningar av hanterings data.

Hämta och installera [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) -exemplet. Följ anvisningarna för att distribuera webb tjänsten. I den här webb tjänsten exponeras tjänster och processer genom åtgärder för att skapa, läsa, uppdatera och ta bort (CRUD). CRUD-begäranden som görs till webb tjänsten anropar Windows PowerShell-kommandon som utför de begärda åtgärderna. En mappning mellan CRUD-åtgärderna och de underliggande Windows PowerShell-kommandona implementeras av två schemafiler, schema. MOF och schema. xml. Filen schema. MOF använder MOF-standarden ( [Distributed Management Task Force](https://www.dmtf.org/) ). Filen schema. XML använder ett XML-schema som beskrivs i [resurs mappnings schema](./resource-mapping-schema.md).

> [!IMPORTANT]
> Innan du aktiverar hantering av ODATA IIS-tillägg i Windows Server 2008 R2 SP1 måste följande funktioner vara aktiverade.
>
> 1. IIS-WebServerRole
> 2. IIS-WebServer
> 3. IIS-HttpTracing
> 4. IIS-ManagementOData

## <a name="steps-for-creating-a-management-odata-web-service"></a>Steg för att skapa en webb tjänst för hantering av OData

I följande avsnitt beskrivs hur du skapar och distribuerar en hantering av OData-webbtjänsten.

- [Lägga till resurser till en Management OData-webbtjänst](./adding-resources-to-a-management-odata-web-service.md)

- [Implementera anpassad auktorisering för en Management OData-webbtjänst](./implementing-custom-authorization-for-a-management-odata-web-service.md)

- [Implementera SessionConfiguration för en Management OData-webbtjänst](./implementing-sessionconfiguration-for-a-management-odata-web-service.md)

- [Redigera MOF-schemafilen för en Management OData-webbtjänst](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

- [Redigera XML-schemafilen för en Management OData-webbtjänst](./authoring-the-xml-schema-file-for-a-management-odata-web-service.md)

- [Redigera Web.config-filen för en Management OData-webbtjänst](./authoring-the-web-config-file-for-a-management-odata-web-service.md)

- [Distribuera en Management OData-webbtjänst](./deploying-a-management-odata-web-service.md)

- [Associera Management OData-entiteter](./associating-management-odata-entities.md)

## <a name="see-also"></a>Se även

[Hantering av ODATA IIS-tillägg schema filer](./management-odata-iis-extension-schema-files.md)
