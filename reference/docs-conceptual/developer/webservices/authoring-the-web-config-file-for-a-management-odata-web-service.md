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
ms.openlocfilehash: f52953ee091f05df5f355719ecba788d3d5ee055
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72352271"
---
# <a name="authoring-the-webconfig-file-for-a-management-odata-web-service"></a>Redigera Web.config-filen för en Management OData-webbtjänst

Innan du kan distribuera din webb tjänst för hantering av OData måste du konfigurera filen Web. config så att den pekar på XML-schemafiler och de dll: er som implementerar [Microsoft. Management. OData. Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization) och [ System. Management. Automation. Remoting. Pssessionconfiguration](/dotnet/api/System.Management.Automation.Remoting.PSSessionConfiguration) -gränssnitt.

## <a name="sample-config-file"></a>Exempel på konfigurations fil

Följande är ett exempel på hur Web. config-filen för din webb tjänst ser ut.

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

## <a name="see-also"></a>Se även

[Implementera anpassad auktorisering för en hantering av OData-webbtjänsten](./implementing-custom-authorization-for-a-management-odata-web-service.md)

[Implementera SessionConfiguration för en hantering av OData-webbtjänst](./implementing-sessionconfiguration-for-a-management-odata-web-service.md)

[Redigera MOF-schemafilen för en hantering av OData-webbtjänsten](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

[Redigera XML-schemafilen för en hantering av OData-webbtjänsten](./authoring-the-xml-schema-file-for-a-management-odata-web-service.md)

[Skapa en hantering av OData-webbtjänst](./creating-a-management-odata-web-service.md)