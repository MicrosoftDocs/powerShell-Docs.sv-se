---
title: Redigera filen XML-schemat för en Management OData-webbtjänst | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e83c9d9-6d06-4247-94d9-e3bfd4013b11
caps.latest.revision: 4
ms.openlocfilehash: a806d012097d107b6cc35710b9a93f2b27dd1ace
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080738"
---
# <a name="authoring-the-xml-schema-file-for-a-management-odata-web-service"></a><span data-ttu-id="45066-102">Redigera XML-schemafilen för en Management OData-webbtjänst</span><span class="sxs-lookup"><span data-stu-id="45066-102">Authoring the XML schema file for a Management OData web service</span></span>

<span data-ttu-id="45066-103">När du har definierat resurser webbtjänsten utsätter (se [redigering MOF-filen för schemat för en Management OData-webbtjänst](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)), du mappa dessa resurser till den underliggande Windows PowerShell-cmdlets som implementerar stöds åtgärder för varje resurs genom att skapa en XML-fil som överensstämmer med den [Resource mappning schemat](./resource-mapping-schema.md).</span><span class="sxs-lookup"><span data-stu-id="45066-103">After you define the resources your web service will expose (see [Authoring the MOF schema file for a Management OData web service](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)), you map those resources to the underlying Windows PowerShell cmdlets that implement the supported operations for each resource by creating an XML file that conforms to the [Resource Mapping Schema](./resource-mapping-schema.md).</span></span> <span data-ttu-id="45066-104">XML-filen anger också de webbadresser som används av klienten för att få åtkomst till resurserna.</span><span class="sxs-lookup"><span data-stu-id="45066-104">The XML file also specifies the URLs that are used by the client to access the resources.</span></span>

## <a name="mappng-resources-to-urls"></a><span data-ttu-id="45066-105">Mappng resurser till URL: er</span><span class="sxs-lookup"><span data-stu-id="45066-105">Mappng resources to URLs</span></span>

<span data-ttu-id="45066-106">Den första delen av XML-filen mappar de resurser som definierats i MOF-filen till URL: er som används för att komma åt dem för schemat.</span><span class="sxs-lookup"><span data-stu-id="45066-106">The first part of the XML file maps the resources defined in the MOF schema file to the URLs that are used to access them.</span></span> <span data-ttu-id="45066-107">I följande exempel visas mappningen.</span><span class="sxs-lookup"><span data-stu-id="45066-107">The following example shows that mapping.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<ResourceMetadata xmlns="http://schemas.microsoft.com/powershell-web-services/2010/09">
    <SchemaNamespace>PswsTest</SchemaNamespace>
    <ContainerName>PSWSEntityContainer</ContainerName>
    <Resources>
        <Resource>
            <RelativeUrl>Service</RelativeUrl>
            <Class>PswsTest_Service</Class>
        </Resource>
        <Resource>
            <RelativeUrl>Process</RelativeUrl>
            <Class>PswsTest_Process</Class>
        </Resource>
    </Resources>
```

## <a name="mapping-cmdlets-to-crud-operations"></a><span data-ttu-id="45066-108">Mappning av cmdlet: ar till CRUD-åtgärder</span><span class="sxs-lookup"><span data-stu-id="45066-108">Mapping cmdlets to CRUD operations</span></span>

<span data-ttu-id="45066-109">Sedan kan du ange de cmdletar som motsvarar CRUD (skapa, läsa, uppdatera och ta bort) åtgärder som har stöd för resurserna.</span><span class="sxs-lookup"><span data-stu-id="45066-109">You then specify the cmdlets that correspond to the CRUD (create, read, update, and delete) operations that the resources support.</span></span> <span data-ttu-id="45066-110">I Management OData [Resource mappning schemat](./resource-mapping-schema.md), mappas CRUD-åtgärder på följande sätt.</span><span class="sxs-lookup"><span data-stu-id="45066-110">In the Management OData [Resource Mapping Schema](./resource-mapping-schema.md), the CRUD operations are mapped as follows.</span></span>

|<span data-ttu-id="45066-111">CRUD-kommando</span><span class="sxs-lookup"><span data-stu-id="45066-111">CRUD command</span></span>|<span data-ttu-id="45066-112">XML-element</span><span class="sxs-lookup"><span data-stu-id="45066-112">XML element</span></span>|
|------------------|-----------------|
|<span data-ttu-id="45066-113">Create</span><span class="sxs-lookup"><span data-stu-id="45066-113">Create</span></span>|<span data-ttu-id="45066-114">Create</span><span class="sxs-lookup"><span data-stu-id="45066-114">Create</span></span>|
|<span data-ttu-id="45066-115">Läsa</span><span class="sxs-lookup"><span data-stu-id="45066-115">Read</span></span>|<span data-ttu-id="45066-116">Söka i data</span><span class="sxs-lookup"><span data-stu-id="45066-116">Query</span></span>|
|<span data-ttu-id="45066-117">Uppdatera</span><span class="sxs-lookup"><span data-stu-id="45066-117">Update</span></span>|<span data-ttu-id="45066-118">Uppdatera</span><span class="sxs-lookup"><span data-stu-id="45066-118">Update</span></span>|
|<span data-ttu-id="45066-119">Ta bort</span><span class="sxs-lookup"><span data-stu-id="45066-119">Delete</span></span>|<span data-ttu-id="45066-120">Ta bort</span><span class="sxs-lookup"><span data-stu-id="45066-120">Delete</span></span>|

<span data-ttu-id="45066-121">I följande exempel visas mappningarna för åtgärderna Skapa, läsa och uppdatera på den `Service` resurs.</span><span class="sxs-lookup"><span data-stu-id="45066-121">The following example shows the mappings for the Create, Read, and Update operations on the `Service` resource.</span></span>

```xml
<ClassImplementations>
        <Class>
            <Name>PswsTest_Service</Name>
            <CmdletImplementation>
                <Query>
                    <Cmdlet>Get-Service</Cmdlet>
                        <FieldParameterMap>
                            <Field>
                                <FieldName>ServiceName</FieldName>
                                <ParameterName>Name</ParameterName>
                            </Field>
                        </FieldParameterMap>
                        <ParameterSets>
                            <ParameterSet>
                                <Name>Default</Name>
                                <Parameter><Name>Name</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>ComputerName</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>Include</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>Exclude</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>ErrorVariable</Name></Parameter>
                                <Parameter><Name>WarningVariable</Name></Parameter>
                                <Parameter><Name>OutVariable</Name></Parameter>
                                <Parameter><Name>OutBuffer</Name></Parameter>
                            </ParameterSet>
                            <ParameterSet>
                                <Name>DisplayName</Name>
                                <Parameter><Name>DisplayName</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>ComputerName</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>Include</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>Exclude</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>ErrorVariable</Name></Parameter>
                                <Parameter><Name>WarningVariable</Name></Parameter>
                                <Parameter><Name>OutVariable</Name></Parameter>
                                <Parameter><Name>OutBuffer</Name></Parameter>
                            </ParameterSet>
                            <ParameterSet>
                                <Name>InputObject</Name>
                                <Parameter><Name>ComputerName</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>Include</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>Exclude</Name><Type>System.String[]</Type></Parameter>
                                <Parameter><Name>ErrorVariable</Name></Parameter>
                                <Parameter><Name>WarningVariable</Name></Parameter>
                                <Parameter><Name>OutVariable</Name></Parameter>
                                <Parameter><Name>OutBuffer</Name></Parameter>
                        </ParameterSet>
                    </ParameterSets>
                </Query>
                <Update>
                    <Cmdlet>Set-Service</Cmdlet>
                    <FieldParameterMap>
                        <Field>
                            <FieldName>ServiceName</FieldName>
                            <ParameterName>Name</ParameterName>
                        </Field>
                    </FieldParameterMap>
                    <ParameterSets>
                        <ParameterSet>
                            <Name>Name</Name>
                            <Parameter><Name>ComputerName</Name><Type>System.String[]</Type></Parameter>
                            <Parameter><Name>Name</Name></Parameter>
                            <Parameter><Name>DisplayName</Name></Parameter>
                            <Parameter><Name>Description</Name></Parameter>
                            <Parameter><Name>Status</Name></Parameter>
                            <Parameter><Name>ErrorVariable</Name></Parameter>
                            <Parameter><Name>WarningVariable</Name></Parameter>
                            <Parameter><Name>OutVariable</Name></Parameter>
                            <Parameter><Name>OutBuffer</Name></Parameter>
                        </ParameterSet>
                        <ParameterSet>
                            <Name>InputObject</Name>
                            <Parameter><Name>ComputerName</Name><Type>System.String[]</Type></Parameter>
                            <Parameter><Name>DisplayName</Name></Parameter>
                            <Parameter><Name>Description</Name></Parameter>
                        </ParameterSet>
                    </ParameterSets>
                </Update>
                <Create>
                    <Cmdlet>New-Service</Cmdlet>
                    <FieldParameterMap>
                        <Field>
                            <FieldName>ServiceName</FieldName>
                            <ParameterName>Name</ParameterName>
                        </Field>
                    </FieldParameterMap>
                    <ParameterSets>
                        <ParameterSet>
                            <Name>__AllParameterSets</Name>
                            <Parameter><Name>BinaryPathName</Name></Parameter>
                            <Parameter><Name>Name</Name></Parameter>
                            <Parameter><Name>DisplayName</Name></Parameter>
                            <Parameter><Name>Description</Name></Parameter>
                            <Parameter><Name>DependsOn</Name></Parameter>
                            <Parameter><Name>ErrorVariable</Name></Parameter>
                            <Parameter><Name>WarningVariable</Name></Parameter>
                            <Parameter><Name>OutVariable</Name></Parameter>
                            <Parameter><Name>OutBuffer</Name></Parameter>
                        </ParameterSet>
                    </ParameterSets>
                </Create>
            </CmdletImplementation>
        </Class>
```

## <a name="see-also"></a><span data-ttu-id="45066-122">Se även</span><span class="sxs-lookup"><span data-stu-id="45066-122">See Also</span></span>

[<span data-ttu-id="45066-123">Redigera MOF-filen för schemat för en Management OData-webbtjänst</span><span class="sxs-lookup"><span data-stu-id="45066-123">Authoring the MOF schema file for a Management OData web service</span></span>](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

[<span data-ttu-id="45066-124">Resursen mappningsschemat</span><span class="sxs-lookup"><span data-stu-id="45066-124">Resource Mapping Schema</span></span>](./resource-mapping-schema.md)

[<span data-ttu-id="45066-125">Skapa en Management OData-webbtjänst</span><span class="sxs-lookup"><span data-stu-id="45066-125">Creating a Management OData Web Service</span></span>](./creating-a-management-odata-web-service.md)