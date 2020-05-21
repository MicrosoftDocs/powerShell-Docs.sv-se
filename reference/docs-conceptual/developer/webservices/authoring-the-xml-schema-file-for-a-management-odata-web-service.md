---
title: Redigera XML-schemafilen för en hantering av OData-webbtjänsten | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e83c9d9-6d06-4247-94d9-e3bfd4013b11
caps.latest.revision: 4
ms.openlocfilehash: 7ccdeeb2833b79cabc7c77d1a400e0c9132b2dcd
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83561472"
---
# <a name="authoring-the-xml-schema-file-for-a-management-odata-web-service"></a><span data-ttu-id="9aac7-102">Redigera XML-schemafilen för en Management OData-webbtjänst</span><span class="sxs-lookup"><span data-stu-id="9aac7-102">Authoring the XML schema file for a Management OData web service</span></span>

<span data-ttu-id="9aac7-103">När du har definierat vilka resurser som ska exponeras för din webb tjänst (se [Redigera MOF-schemafilen för en hantering av OData-webbtjänsten](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)) mappar du dessa resurser till de underliggande Windows PowerShell-cmdletar som implementerar de åtgärder som stöds för varje resurs genom att skapa en XML-fil som följer [resurs mappnings schemat](./resource-mapping-schema.md).</span><span class="sxs-lookup"><span data-stu-id="9aac7-103">After you define the resources your web service will expose (see [Authoring the MOF schema file for a Management OData web service](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)), you map those resources to the underlying Windows PowerShell cmdlets that implement the supported operations for each resource by creating an XML file that conforms to the [Resource Mapping Schema](./resource-mapping-schema.md).</span></span> <span data-ttu-id="9aac7-104">XML-filen anger också de URL: er som används av klienten för att få åtkomst till resurserna.</span><span class="sxs-lookup"><span data-stu-id="9aac7-104">The XML file also specifies the URLs that are used by the client to access the resources.</span></span>

## <a name="mappng-resources-to-urls"></a><span data-ttu-id="9aac7-105">Mappng resurser till URL: er</span><span class="sxs-lookup"><span data-stu-id="9aac7-105">Mappng resources to URLs</span></span>

<span data-ttu-id="9aac7-106">Den första delen av XML-filen mappar de resurser som definierats i MOF-schemafilen till de URL: er som används för att komma åt dem.</span><span class="sxs-lookup"><span data-stu-id="9aac7-106">The first part of the XML file maps the resources defined in the MOF schema file to the URLs that are used to access them.</span></span> <span data-ttu-id="9aac7-107">I följande exempel visas mappningen.</span><span class="sxs-lookup"><span data-stu-id="9aac7-107">The following example shows that mapping.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<ResourceMetadata xmlns="https://schemas.microsoft.com/powershell-web-services/2010/09">
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

## <a name="mapping-cmdlets-to-crud-operations"></a><span data-ttu-id="9aac7-108">Mappa cmdletar till CRUD-åtgärder</span><span class="sxs-lookup"><span data-stu-id="9aac7-108">Mapping cmdlets to CRUD operations</span></span>

<span data-ttu-id="9aac7-109">Sedan anger du de cmdlet: ar som motsvarar de åtgärder för CRUD (skapa, läsa, uppdatera och ta bort) som resurserna stöder.</span><span class="sxs-lookup"><span data-stu-id="9aac7-109">You then specify the cmdlets that correspond to the CRUD (create, read, update, and delete) operations that the resources support.</span></span> <span data-ttu-id="9aac7-110">I hanterings schema för OData- [resurs mappar](./resource-mapping-schema.md)mappas CRUD-åtgärderna enligt följande.</span><span class="sxs-lookup"><span data-stu-id="9aac7-110">In the Management OData [Resource Mapping Schema](./resource-mapping-schema.md), the CRUD operations are mapped as follows.</span></span>

|<span data-ttu-id="9aac7-111">CRUD-kommando</span><span class="sxs-lookup"><span data-stu-id="9aac7-111">CRUD command</span></span>|<span data-ttu-id="9aac7-112">XML-element</span><span class="sxs-lookup"><span data-stu-id="9aac7-112">XML element</span></span>|
|------------------|-----------------|
|<span data-ttu-id="9aac7-113">Skapa</span><span class="sxs-lookup"><span data-stu-id="9aac7-113">Create</span></span>|<span data-ttu-id="9aac7-114">Skapa</span><span class="sxs-lookup"><span data-stu-id="9aac7-114">Create</span></span>|
|<span data-ttu-id="9aac7-115">Läsa</span><span class="sxs-lookup"><span data-stu-id="9aac7-115">Read</span></span>|<span data-ttu-id="9aac7-116">Söka i data</span><span class="sxs-lookup"><span data-stu-id="9aac7-116">Query</span></span>|
|<span data-ttu-id="9aac7-117">Uppdatera</span><span class="sxs-lookup"><span data-stu-id="9aac7-117">Update</span></span>|<span data-ttu-id="9aac7-118">Uppdatera</span><span class="sxs-lookup"><span data-stu-id="9aac7-118">Update</span></span>|
|<span data-ttu-id="9aac7-119">Ta bort</span><span class="sxs-lookup"><span data-stu-id="9aac7-119">Delete</span></span>|<span data-ttu-id="9aac7-120">Ta bort</span><span class="sxs-lookup"><span data-stu-id="9aac7-120">Delete</span></span>|

<span data-ttu-id="9aac7-121">I följande exempel visas mappningarna för åtgärderna skapa, läsa och uppdatera på `Service` resursen.</span><span class="sxs-lookup"><span data-stu-id="9aac7-121">The following example shows the mappings for the Create, Read, and Update operations on the `Service` resource.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="9aac7-122">Se även</span><span class="sxs-lookup"><span data-stu-id="9aac7-122">See Also</span></span>

[<span data-ttu-id="9aac7-123">Redigera MOF-schemafilen för en Management OData-webbtjänst</span><span class="sxs-lookup"><span data-stu-id="9aac7-123">Authoring the MOF schema file for a Management OData web service</span></span>](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

[<span data-ttu-id="9aac7-124">Schema för resursmappning</span><span class="sxs-lookup"><span data-stu-id="9aac7-124">Resource Mapping Schema</span></span>](./resource-mapping-schema.md)

[<span data-ttu-id="9aac7-125">Skapa en Management OData-webbtjänst</span><span class="sxs-lookup"><span data-stu-id="9aac7-125">Creating a Management OData Web Service</span></span>](./creating-a-management-odata-web-service.md)
