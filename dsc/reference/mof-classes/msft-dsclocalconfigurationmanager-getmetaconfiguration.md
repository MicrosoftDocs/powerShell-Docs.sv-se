---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: GetMetaConfiguration-metoden
ms.openlocfilehash: bd280cb8ebd7b0522e4e01cbd24bd9bdcfddf4c2
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734441"
---
# <a name="getmetaconfiguration-method"></a><span data-ttu-id="8a330-103">GetMetaConfiguration-metoden</span><span class="sxs-lookup"><span data-stu-id="8a330-103">GetMetaConfiguration method</span></span>

<span data-ttu-id="8a330-104">Hämtar de lokala inställningarna för Configuration Manager som används för att styra agenten konfiguration.</span><span class="sxs-lookup"><span data-stu-id="8a330-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="8a330-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="8a330-105">Syntax</span></span>

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

## <a name="parameters"></a><span data-ttu-id="8a330-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="8a330-106">Parameters</span></span>

<span data-ttu-id="8a330-107">*MetaConfiguration* \[ut\] på return innehåller en inbäddad förekomst av den **MSFT_DSCMetaConfiguration** klass som definierar inställningarna.</span><span class="sxs-lookup"><span data-stu-id="8a330-107">*MetaConfiguration* \[out\] On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="8a330-108">Returvärde</span><span class="sxs-lookup"><span data-stu-id="8a330-108">Return value</span></span>

<span data-ttu-id="8a330-109">Returnerar noll om åtgärden lyckades; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="8a330-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="8a330-110">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="8a330-110">Remarks</span></span>

<span data-ttu-id="8a330-111">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="8a330-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="8a330-112">Krav</span><span class="sxs-lookup"><span data-stu-id="8a330-112">Requirements</span></span>

<span data-ttu-id="8a330-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="8a330-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="8a330-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="8a330-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="8a330-115">Se även</span><span class="sxs-lookup"><span data-stu-id="8a330-115">See also</span></span>

[<span data-ttu-id="8a330-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="8a330-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
