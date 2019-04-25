---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 23a5c8832f7c2888880a1ee846d75feaa95ebe47
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058411"
---
# <a name="frequencies-for-refreshmode-and-configurationmode-dont-need-to-be-multiples-of-each-other"></a><span data-ttu-id="7accf-102">Frekvenserna för RefreshMode och ConfigurationMode behöver inte vara multiplar av varandra</span><span class="sxs-lookup"><span data-stu-id="7accf-102">Frequencies for RefreshMode and ConfigurationMode don't need to be multiples of each other</span></span>

<span data-ttu-id="7accf-103">I den tidigare versionen av DSC LCM skulle behandla `RefreshFrequencyMins` och `ConfigurationModeFrequencyMins` som multiplar av varandra.</span><span class="sxs-lookup"><span data-stu-id="7accf-103">In the previous version of DSC, the LCM would treat `RefreshFrequencyMins` and `ConfigurationModeFrequencyMins` as multiples of each other.</span></span> <span data-ttu-id="7accf-104">I WMF 5.0 RTM bearbetas de här egenskaperna oberoende av varandra.</span><span class="sxs-lookup"><span data-stu-id="7accf-104">In WMF 5.0 RTM, these properties are processed independent of each other.</span></span>

<span data-ttu-id="7accf-105">Mer information finns i [konfigurerar den lokala Konfigurationshanteraren](https://msdn.microsoft.com/powershell/dsc/metaconfig).</span><span class="sxs-lookup"><span data-stu-id="7accf-105">For more information, see [Configuring the Local Configuration Manager](https://msdn.microsoft.com/powershell/dsc/metaconfig).</span></span>
