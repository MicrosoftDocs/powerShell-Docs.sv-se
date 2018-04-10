---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, inställning
ms.openlocfilehash: a8947844df0da167961c64e1e09d5075960c95de
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="generate-powershell-cmdlets-based-on-odata-endpoint"></a><span data-ttu-id="e6267-102">Skapa PowerShell-cmdletar baserade på OData-slutpunkt</span><span class="sxs-lookup"><span data-stu-id="e6267-102">Generate PowerShell Cmdlets based on OData Endpoint</span></span>
<a name="generate-windows-powershell-cmdlets-based-on-an-odata-endpoint"></a><span data-ttu-id="e6267-103">Generera en Windows PowerShell-cmdlets som är baserat på en OData-slutpunkt</span><span class="sxs-lookup"><span data-stu-id="e6267-103">Generate Windows PowerShell cmdlets based on an OData endpoint</span></span>
--------------------------------------------------------------

<span data-ttu-id="e6267-104">**Export-ODataEndpointProxy** är en cmdlet som genererar en uppsättning Windows PowerShell-cmdlets baserat på de funktioner som exponeras av en viss OData-slutpunkt.</span><span class="sxs-lookup"><span data-stu-id="e6267-104">**Export-ODataEndpointProxy** is a cmdlet that generates a set of Windows PowerShell cmdlets based on the functionality exposed by a given OData endpoint.</span></span>

<span data-ttu-id="e6267-105">I följande exempel visas hur du använder den här nya cmdlet:</span><span class="sxs-lookup"><span data-stu-id="e6267-105">The following example shows how to use this new cmdlet:</span></span>

<span data-ttu-id="e6267-106">\# Grundläggande användningsfall för Export ODataEndpointProxy</span><span class="sxs-lookup"><span data-stu-id="e6267-106">\# Basic use case of Export-ODataEndpointProxy</span></span>

```powershell
Export-ODataEndpointProxy -Uri 'http://services.odata.org/v3/(S(snyobsk1hhutkb2yulwldgf1))/odata/odata.svc' -OutputModule C:\Users\user\Generated.psd1

ipmo 'C:\Users\user\Generated.psd1'
# Cmdlets are created based on the following heuristics
# New-<EntityType> -<Key> [-<Other Attributes>]
#
# Get-<EntityType> [-<Key> -Top –Skip –Filter -OrderBy]
# # If there is a complex key, the keys will actually be -<Key1> -<Key2>…
# # Note this rule applies to any other instances of the key
#
# Set-<EntityType> -<Key> [-<Other Attributes>]
#
# Remove-<EntityType> -<Key>
#
# Invoke-<EntityType><Action> [-<Key> -<Other Parameters>]
#
#
# Cmdlets from associations (Note: Get and Remove get additional parameter sets)
# Get-<EntityType> -<AssociatedEntity>
# New-<EntityType> -<AssociatedEntity> -<Key>
# Remove-<EntityType> -<AssociatedEntity> -<Key>
#
#
# Note: Every cmdlet has the –ConnectionURI parameter for explicitly setting the URI of the endpoint. This normally uses the same address that you gave the Export-ODataEndpointProxy cmdlet, but can be overridden in this fashion for the sake of similar endpoints.
#
```

<span data-ttu-id="e6267-107">Det finns fortfarande delar av viktiga användningsområden under utveckling för den här funktionen, inklusive men inte begränsat till:</span><span class="sxs-lookup"><span data-stu-id="e6267-107">There are still parts of key use cases in development for this functionality, including, but not limited to:</span></span>
-   <span data-ttu-id="e6267-108">Kopplingar</span><span class="sxs-lookup"><span data-stu-id="e6267-108">Associations</span></span>
-   <span data-ttu-id="e6267-109">Skicka strömmar</span><span class="sxs-lookup"><span data-stu-id="e6267-109">Passing streams</span></span>

<a name="generate-windows-powershell-cmdlets-based-on-an-odata-endpoint-with-odatautils"></a><span data-ttu-id="e6267-110">Generera baserat på en OData-slutpunkt med ODataUtils Windows PowerShell-cmdlets</span><span class="sxs-lookup"><span data-stu-id="e6267-110">Generate Windows PowerShell cmdlets based on an OData endpoint with ODataUtils</span></span>
------------------------------------------------------------------------------
<span data-ttu-id="e6267-111">Modulen ODataUtils kan generering av Windows PowerShell-cmdlets från REST-slutpunkter som stöder OData.</span><span class="sxs-lookup"><span data-stu-id="e6267-111">The ODataUtils module allows generation of Windows PowerShell cmdlets from REST endpoints that support OData.</span></span> <span data-ttu-id="e6267-112">Följande inkrementell förbättringar finns i Microsoft.PowerShell.ODataUtils Windows PowerShell-modulen.</span><span class="sxs-lookup"><span data-stu-id="e6267-112">The following incremental enhancements are in the Microsoft.PowerShell.ODataUtils Windows PowerShell module.</span></span>
-   <span data-ttu-id="e6267-113">Kanal ytterligare information från serversidan slutpunkten till klienten.</span><span class="sxs-lookup"><span data-stu-id="e6267-113">Channel additional information from server-side endpoint to client side.</span></span>
-   <span data-ttu-id="e6267-114">Stöd för klientsidan sidindelning</span><span class="sxs-lookup"><span data-stu-id="e6267-114">Client-side paging support</span></span>
-   <span data-ttu-id="e6267-115">Filtrering av servern med hjälp av väljer parametern -</span><span class="sxs-lookup"><span data-stu-id="e6267-115">Server-side filtering by using the -Select parameter</span></span>
-   <span data-ttu-id="e6267-116">Stöd för web-huvuden för begäran</span><span class="sxs-lookup"><span data-stu-id="e6267-116">Support for web request headers</span></span>

<span data-ttu-id="e6267-117">Proxy-cmdlets som genereras av cmdleten Export-ODataEndPointProxy innehåller ytterligare information (inte anges i $metadata används under genereringen av klientsidan proxy) från servern sida OData-slutpunkt på strömmen Information (en ny Windows PowerShell 5.0-funktionen).</span><span class="sxs-lookup"><span data-stu-id="e6267-117">The proxy cmdlets generated by the Export-ODataEndPointProxy cmdlet provide additional information (not mentioned in the $metadata used during the client-side proxy generation) from the server side OData endpoint on the Information stream (a new Windows PowerShell 5.0 feature).</span></span> <span data-ttu-id="e6267-118">Här är ett exempel på hur du hämtar den informationen.</span><span class="sxs-lookup"><span data-stu-id="e6267-118">Here is an example of how to get that information.</span></span>
```powershell
Import-Module Microsoft.PowerShell.ODataUtils -Force
$generatedProxyModuleDir = Join-Path -Path $env:SystemDrive -ChildPath 'ODataDemoProxy'
$uri = "http://services.odata.org/V3/(S(fhleiief23wrm5a5nhf542q5))/OData/OData.svc/"
Export-ODataEndpointProxy -Uri $uri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -AllowClobber
Import-Module $generatedProxyModuleDir -Force

# In the below command, we are retrieving top 1 product.
# By specifying -IncludeTotalResponseCount parameter,
# we are getting the total count of all the Product records
# available on the server side. This information
# is surfaced on the client side through the Information stream.
$product = Get-Product -Top 1 -AllowUnsecureConnection -AllowAdditionalData -IncludeTotalResponseCount -InformationVariable infoStream
# The Information stream contains the additional
# information sent from the server side.
$additionalInfo = $infoStream.GetEnumerator() | % MessageData
# 'Odata.Count' indicates the total product records
# available on the server side Odata endpoint.
$additionalInfo['odata.count']
```

<span data-ttu-id="e6267-119">Du kan hämta posterna från serversidan i grupper genom att använda stöd för sidindelning av klientsidan.</span><span class="sxs-lookup"><span data-stu-id="e6267-119">You can get the records from the server side in batches by using client-side paging support.</span></span> <span data-ttu-id="e6267-120">Detta är användbart när du måste hämta stora mängder data från servern via nätverket.</span><span class="sxs-lookup"><span data-stu-id="e6267-120">This is useful when you must get a large amount of data from the server over the network.</span></span>
```powershell
$skipCount = 0
$batchSize = 3
# Client-Side Paging Support: The records from the server side
# are retrieved in batches of $batchSize
while($skipCount -le $additionalInfo['odata.count'])
{
Get-Product -AllowUnsecureConnection -AllowAdditionalData -Top $batchSize -Skip $skipCount
$skipCount += $batchSize
}
```

<span data-ttu-id="e6267-121">Stöd för de genererade cmdlet: ar väljer parametern – som du kan använda som ett filter för att ta emot bara de post egenskaper som klienten behöver.</span><span class="sxs-lookup"><span data-stu-id="e6267-121">The generated proxy cmdlets support the –Select parameter which you can use as a filter to receive only the record properties that the client needs.</span></span> <span data-ttu-id="e6267-122">Detta minskar mängden data som överförs över nätverket, eftersom filtreringen sker på serversidan.</span><span class="sxs-lookup"><span data-stu-id="e6267-122">This reduces the amount of data that is transferred over the network, because the filtering occurs on the server side.</span></span>
```powershell
# In the below example only the Name property of the
# Product record is retrieved from the server side.
Get-Product -Top 2 -AllowUnsecureConnection -AllowAdditionalData -Select Name
```

<span data-ttu-id="e6267-123">Cmdleten Export-ODataEndpointProxy och proxy-cmdlets som genererats av det, stöder nu parametern huvuden (ange värden som en hash-tabell), som kan användas för att kanalen ytterligare information som förväntas av serversidan OData-slutpunkt.</span><span class="sxs-lookup"><span data-stu-id="e6267-123">The Export-ODataEndpointProxy cmdlet, and the proxy cmdlets generated by it, now support the Headers parameter (supply values as a hash table), which you can use to channel any additional information that is expected by the server-side OData endpoint.</span></span> <span data-ttu-id="e6267-124">I följande exempel kanaler du en prenumeration nyckel via huvuden för tjänster som väntar på en prenumeration nyckel för autentisering.</span><span class="sxs-lookup"><span data-stu-id="e6267-124">In the following example, you can channel a Subscription key through Headers for services that are expecting a Subscription key for authentication.</span></span>
```powershell
# As an example, in the below command 'XXXX' is the authentication used by the
# Export-ODataEndpointProxy cmdlet to interact with the server-side
# OData endpoint accessed through $endPointUri.

Export-ODataEndpointProxy -Uri $endPointUri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -Headers @{'subscription-key'='XXXX'}
```