---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 1153738fdf6f926d5d819bbf91450408dcb17f71
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057816"
---
# <a name="generate-powershell-cmdlets-based-on-odata-endpoint"></a>Skapa PowerShell-cmdletar baserade på OData-slutpunkt

## <a name="generate-windows-powershell-cmdlets-based-on-an-odata-endpoint"></a>Skapa Windows PowerShell-cmdletar baserade på en OData-slutpunkt

**Export-ODataEndpointProxy** är en cmdlet som genererar en uppsättning Windows PowerShell-cmdletar baserade på funktioner som exponeras av en viss OData-slutpunkten.

I följande exempel visas hur du använder den här nya cmdleten:

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

Det finns fortfarande delar av viktiga användningsområden i utveckling för den här funktionen, inklusive, men inte begränsat till:
-   Associationer
-   Skicka dataströmmar

## <a name="generate-windows-powershell-cmdlets-based-on-an-odata-endpoint-with-odatautils"></a>Skapa Windows PowerShell-cmdletar baserade på en OData-slutpunkt med ODataUtils

Modulen ODataUtils kan generation av Windows PowerShell-cmdletar från REST-slutpunkter som har stöd för OData. Följande inkrementella förbättringar är i Microsoft.PowerShell.ODataUtils Windows PowerShell-modulen.
-   Kanal för ytterligare information från serversidan slutpunkten till klienten.
-   Stöd för klientsidan växling
-   Serversidan filtrering med hjälp av väljer parametern -
-   Stöd för web-begärandehuvuden

Proxy-cmdletar som genereras av cmdlet: en Export-ODataEndPointProxy innehåller ytterligare information (inte nämns i $metadata används under genereringen av klientsidan proxy) från servern på klientsidan OData-slutpunkten på informationsström (en ny Windows PowerShell 5.0-funktionen). Här är ett exempel på hur du hämtar den informationen.

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

Du kan hämta poster från serversidan i batchar med hjälp av klientsidan sidindelning support. Detta är användbart när du måste hämta en stor mängd data från servern via nätverket.

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

Genererade proxy-cmdletarna har stöd för – Välj parametern som du kan använda som ett filter för att ta emot endast postegenskaperna som klienten behöver. Detta minskar mängden data som överförs över nätverket, eftersom den filtrering utförs på serversidan.

```powershell
# In the below example only the Name property of the
# Product record is retrieved from the server side.
Get-Product -Top 2 -AllowUnsecureConnection -AllowAdditionalData -Select Name
```

Cmdleten Export-ODataEndpointProxy och proxy-cmdletar som genereras av det, är nu stöd för parametern rubriker (ange värden som en hashtabell), som du kan använda på channel eventuell ytterligare information som förväntas av serversidan OData-slutpunkten. I följande exempel kanaler du en prenumerationsnyckel via rubriker för tjänster som väntar en prenumerationsnyckel för autentisering.

```powershell
# As an example, in the below command 'XXXX' is the authentication used by the
# Export-ODataEndpointProxy cmdlet to interact with the server-side
# OData endpoint accessed through $endPointUri.

Export-ODataEndpointProxy -Uri $endPointUri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -Headers @{'subscription-key'='XXXX'}
```
