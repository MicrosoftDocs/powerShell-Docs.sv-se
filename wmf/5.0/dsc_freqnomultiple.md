---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: a3ac215396206fba62bce303733429d60722ee6b
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218390"
---
# <a name="frequencies-for-refreshmode-and-configurationmode-dont-need-to-be-multiples-of-each-other"></a><span data-ttu-id="31dcf-102">Frekvensen för RefreshMode och ConfigurationMode behöver inte vara en multipel av varandra</span><span class="sxs-lookup"><span data-stu-id="31dcf-102">Frequencies for RefreshMode and ConfigurationMode don't need to be multiples of each other</span></span>

<span data-ttu-id="31dcf-103">I den tidigare versionen av DSC MGM skulle behandla `RefreshFrequencyMins` och `ConfigurationModeFrequencyMins` som multiplar av varandra.</span><span class="sxs-lookup"><span data-stu-id="31dcf-103">In the previous version of DSC, the LCM would treat `RefreshFrequencyMins` and `ConfigurationModeFrequencyMins` as multiples of each other.</span></span> <span data-ttu-id="31dcf-104">WMF 5.0 RTM bearbetas dessa egenskaper oberoende av varandra.</span><span class="sxs-lookup"><span data-stu-id="31dcf-104">In WMF 5.0 RTM, these properties are processed independent of each other.</span></span>

<span data-ttu-id="31dcf-105">Mer information finns i [konfigurera den lokala Configuration Manager](https://msdn.microsoft.com/powershell/dsc/metaconfig).</span><span class="sxs-lookup"><span data-stu-id="31dcf-105">For more information, see [Configuring the Local Configuration Manager](https://msdn.microsoft.com/powershell/dsc/metaconfig).</span></span>
