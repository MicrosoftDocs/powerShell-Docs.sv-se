---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: GetMetaConfiguration-metoden
ms.openlocfilehash: bd280cb8ebd7b0522e4e01cbd24bd9bdcfddf4c2
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "71941567"
---
# <a name="getmetaconfiguration-method"></a><span data-ttu-id="bcbbb-103">GetMetaConfiguration-metoden</span><span class="sxs-lookup"><span data-stu-id="bcbbb-103">GetMetaConfiguration method</span></span>

<span data-ttu-id="bcbbb-104">Hämtar de lokala Configuration Manager inställningar som används för att kontrol lera konfigurations agenten.</span><span class="sxs-lookup"><span data-stu-id="bcbbb-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="bcbbb-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="bcbbb-105">Syntax</span></span>

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

## <a name="parameters"></a><span data-ttu-id="bcbbb-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="bcbbb-106">Parameters</span></span>

<span data-ttu-id="bcbbb-107">*MetaConfiguration* \[ut\] vid retur, innehåller en inbäddad instans av klassen **MSFT_DSCMetaConfiguration** som definierar inställningarna.</span><span class="sxs-lookup"><span data-stu-id="bcbbb-107">*MetaConfiguration* \[out\] On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="bcbbb-108">Returvärde</span><span class="sxs-lookup"><span data-stu-id="bcbbb-108">Return value</span></span>

<span data-ttu-id="bcbbb-109">Returnerar noll vid lyckad; annars returneras en felkod.</span><span class="sxs-lookup"><span data-stu-id="bcbbb-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="bcbbb-110">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="bcbbb-110">Remarks</span></span>

<span data-ttu-id="bcbbb-111">Detta är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="bcbbb-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="bcbbb-112">Krav</span><span class="sxs-lookup"><span data-stu-id="bcbbb-112">Requirements</span></span>

<span data-ttu-id="bcbbb-113">**MOF:** DscCore. MOF</span><span class="sxs-lookup"><span data-stu-id="bcbbb-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="bcbbb-114">**Namnrymd**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="bcbbb-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="bcbbb-115">Se även</span><span class="sxs-lookup"><span data-stu-id="bcbbb-115">See also</span></span>

[<span data-ttu-id="bcbbb-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="bcbbb-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
