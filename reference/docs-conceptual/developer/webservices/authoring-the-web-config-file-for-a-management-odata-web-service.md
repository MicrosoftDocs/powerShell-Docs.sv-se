---
title: Redigera Web. config-filen för en hantering av OData-webbtjänsten | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d569f5d5-9746-40c0-be5e-f218bc4560f7
caps.latest.revision: 4
ms.openlocfilehash: eee515252cf03c05d15368ee6e2a1cb62dc82647
ms.sourcegitcommit: 30ccbbb32915b551c4cd4c91ef1df96b5b7514c4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/01/2020
ms.locfileid: "80500791"
---
# <a name="authoring-the-webconfig-file-for-a-management-odata-web-service"></a><span data-ttu-id="511d3-102">Redigera Web.config-filen för en Management OData-webbtjänst</span><span class="sxs-lookup"><span data-stu-id="511d3-102">Authoring the Web.config file for a Management OData web service</span></span>

<span data-ttu-id="511d3-103">Innan du kan distribuera din webb tjänst för hantering av OData måste du konfigurera filen Web. config så att den pekar på XML-schemafiler och de dll: er som implementerar [Microsoft. Management. OData. Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization) och [system. Management. Automation. Remoting. Pssessionconfiguration](/dotnet/api/System.Management.Automation.Remoting.PSSessionConfiguration) -gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="511d3-103">Before you can deploy your Management OData web service, you must configure the web.config file to point to the XML schema files and the DLLs that implement the [Microsoft.Management.Odata.Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization) and [System.Management.Automation.Remoting.Pssessionconfiguration](/dotnet/api/System.Management.Automation.Remoting.PSSessionConfiguration) interfaces.</span></span>

## <a name="sample-config-file"></a><span data-ttu-id="511d3-104">Exempel på konfigurations fil</span><span class="sxs-lookup"><span data-stu-id="511d3-104">Sample config file</span></span>

<span data-ttu-id="511d3-105">Följande är ett exempel på hur Web. config-filen för din webb tjänst ser ut.</span><span class="sxs-lookup"><span data-stu-id="511d3-105">The following is an example of what the web.config file for your web service looks like.</span></span>

```xml
<?xml version="1.0" encoding="UTF-8"?>
<configuration>
   <configSections>
      <section name="managementOdata" type="Microsoft.Management.Odata.Core.DSConfiguration, Microsoft.Management.OData, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL" />
   </configSections>
   <managementOdata schemaFileName="Schema.mof" resourceMappingFileName="Schema.xml">
      <customAuthorization type="Microsoft.Samples.Management.OData.RoleBasedPlugins.CustomAuthorization" assembly=".\Microsoft.Samples.Management.OData.RoleBasedPlugins.dll" />
      <powershell>
         <sessionConfiguration type="Microsoft.Samples.Management.OData.RoleBasedPlugins.SessionConfiguration" assembly=".\Microsoft.Samples.Management.OData.RoleBasedPlugins.dll" />
      </powershell>
      <commandInvocation enabled="true" />
      <wcfDataServicesConfig>
      </wcfDataServicesConfig>
   </managementOdata>
   <system.serviceModel>
      <behaviors>
         <serviceBehaviors>
            <behavior>
                  <serviceAuthorization serviceAuthorizationManagerType="Microsoft.Management.Odata.Core.CustomAuthorizationManager, Microsoft.Management.OData, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" />
            </behavior>
         </serviceBehaviors>
      </behaviors>
      <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />
   </system.serviceModel>
   <system.webServer>
      <security>
         <authentication>
            <anonymousAuthentication enabled="false" />
            <basicAuthentication enabled="true" />
            <windowsAuthentication enabled="false" />
         </authentication>
      </security>
  </system.webServer>
</configuration>

```

## <a name="see-also"></a><span data-ttu-id="511d3-106">Se även</span><span class="sxs-lookup"><span data-stu-id="511d3-106">See Also</span></span>

[<span data-ttu-id="511d3-107">Implementera anpassad auktorisering för en hantering av OData-webbtjänsten</span><span class="sxs-lookup"><span data-stu-id="511d3-107">Implementing Custom Authorization for a Management OData web service</span></span>](./implementing-custom-authorization-for-a-management-odata-web-service.md)

[<span data-ttu-id="511d3-108">Implementera SessionConfiguration för en hantering av OData-webbtjänst</span><span class="sxs-lookup"><span data-stu-id="511d3-108">Implementing SessionConfiguration for a Management OData web service</span></span>](./implementing-sessionconfiguration-for-a-management-odata-web-service.md)

[<span data-ttu-id="511d3-109">Redigera MOF-schemafilen för en hantering av OData-webbtjänsten</span><span class="sxs-lookup"><span data-stu-id="511d3-109">Authoring the MOF schema file for a Management OData web service</span></span>](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

[<span data-ttu-id="511d3-110">Redigera XML-schemafilen för en hantering av OData-webbtjänsten</span><span class="sxs-lookup"><span data-stu-id="511d3-110">Authoring the XML schema file for a Management OData web service</span></span>](./authoring-the-xml-schema-file-for-a-management-odata-web-service.md)

[<span data-ttu-id="511d3-111">Skapa en hantering av OData-webbtjänst</span><span class="sxs-lookup"><span data-stu-id="511d3-111">Creating a Management OData Web Service</span></span>](./creating-a-management-odata-web-service.md)