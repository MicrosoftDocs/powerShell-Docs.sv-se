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
# <a name="creating-a-management-odata-web-service"></a>Skapa en Management OData-webbtjänst

Management ODATA IIS Extension är en infrastruktur för att skapa en ASP.NET web service slutpunkt som visar dina hanteringsdata som nås via Windows PowerShell-cmdlets och skript som OData Web service-entiteter. Detta sker som som bearbetar begäranden från OData och konvertera dem till ett Windows PowerShell-anrop. Produktgrupper kan byggas ovanpå den här infrastrukturen för att skapa slutpunkter som visar specifika uppsättningar av data Manager.

Ladda ned och installera den [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) exemplet. Följ anvisningarna för att distribuera webbtjänsten. Den här webbtjänsten exponerar tjänster och processer via operations skapa, läsa, uppdatera och ta bort (CRUD). CRUD-begäranden som görs till webbtjänsten anropar Windows PowerShell-kommandon som utför de begärda åtgärderna. En mappning mellan CRUD-åtgärder och de underliggande Windows PowerShell-kommandona har implementerats av två schemafiler, schema.mof och schema.xml. Filen schema.mof använder den [Distributed Management Task Force](https://www.dmtf.org/) (DMTF) hanterade objekt (MOF) standard. Filen schema.xml använder ett XML-schema som beskrivs i [Resource mappning schemat](./resource-mapping-schema.md).

> [!IMPORTANT]
> Följande funktioner måste aktiveras innan du aktiverar Management ODATA IIS-tillägg på Windows Server 2008 R2 SP1.
>
> 1.  IIS-WebServerRole
> 2.  IIS-WebServer
> 3.  IIS-HttpTracing
> 4.  IIS-ManagementOData

## <a name="steps-for-creating-a-management-odata-web-service"></a>Anvisningar för att skapa en Management OData-webbtjänst

I följande avsnitt beskrivs hur du skapar och distribuerar en Management OData-webbtjänst.

- [Att lägga till resurser till en Management OData-webbtjänst](./adding-resources-to-a-management-odata-web-service.md)

- [Implementera anpassad auktorisering för en Management OData-webbtjänst](./implementing-custom-authorization-for-a-management-odata-web-service.md)

- [Implementera SessionConfiguration för en Management OData-webbtjänst](./implementing-sessionconfiguration-for-a-management-odata-web-service.md)

- [Redigera MOF-filen för schemat för en Management OData-webbtjänst](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

- [Redigera filen XML-schemat för en Management OData-webbtjänst](./authoring-the-xml-schema-file-for-a-management-odata-web-service.md)

- [Redigera filen Web.config för en Management OData-webbtjänst](./authoring-the-web-config-file-for-a-management-odata-web-service.md)

- [Distribuera en Management OData-webbtjänst](./deploying-a-management-odata-web-service.md)

- [Associera Management OData-entiteter](./associating-management-odata-entities.md)

## <a name="see-also"></a>Se även

[Management ODATA IIS-tillägget schemafiler](./management-odata-iis-extension-schema-files.md)
