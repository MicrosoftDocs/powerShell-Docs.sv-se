---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: GetMetaConfiguration-metoden för MSFT_DSCLocalConfigurationManager-klassen
ms.openlocfilehash: e14237ef68b95d68e2f14071aa1fa6ba0717f39f
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892849"
---
# <a name="getmetaconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="26d42-103">GetMetaConfiguration-metoden för MSFT_DSCLocalConfigurationManager-klassen</span><span class="sxs-lookup"><span data-stu-id="26d42-103">GetMetaConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="26d42-104">Hämtar de lokala inställningarna för Configuration Manager som används för att styra agenten konfiguration.</span><span class="sxs-lookup"><span data-stu-id="26d42-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="26d42-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="26d42-105">Syntax</span></span>

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

## <a name="parameters"></a><span data-ttu-id="26d42-106">Parametrar</span><span class="sxs-lookup"><span data-stu-id="26d42-106">Parameters</span></span>

<span data-ttu-id="26d42-107">*MetaConfiguration* \[ut\] på return innehåller en inbäddad förekomst av den **MSFT_DSCMetaConfiguration** klass som definierar inställningarna.</span><span class="sxs-lookup"><span data-stu-id="26d42-107">*MetaConfiguration* \[out\] On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="26d42-108">Returvärde</span><span class="sxs-lookup"><span data-stu-id="26d42-108">Return value</span></span>

<span data-ttu-id="26d42-109">Returnerar noll om åtgärden lyckades; Annars returnerar en felkod.</span><span class="sxs-lookup"><span data-stu-id="26d42-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="26d42-110">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="26d42-110">Remarks</span></span>

<span data-ttu-id="26d42-111">Det här är en statisk metod.</span><span class="sxs-lookup"><span data-stu-id="26d42-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="26d42-112">Krav</span><span class="sxs-lookup"><span data-stu-id="26d42-112">Requirements</span></span>

<span data-ttu-id="26d42-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="26d42-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="26d42-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="26d42-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="26d42-115">Se även</span><span class="sxs-lookup"><span data-stu-id="26d42-115">See also</span></span>

[<span data-ttu-id="26d42-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="26d42-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)