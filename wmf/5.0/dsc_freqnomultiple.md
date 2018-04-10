---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, inställning
ms.openlocfilehash: e1faf71436c8ba0ae02a166ce06d03de9f66f094
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="frequencies-for-refreshmode-and-configurationmode-dont-need-to-be-multiples-of-each-other"></a><span data-ttu-id="e1a34-102">Frekvensen för RefreshMode och ConfigurationMode behöver inte vara en multipel av varandra</span><span class="sxs-lookup"><span data-stu-id="e1a34-102">Frequencies for RefreshMode and ConfigurationMode don't need to be multiples of each other</span></span>

<span data-ttu-id="e1a34-103">I den tidigare versionen av DSC MGM skulle behandla `RefreshFrequencyMins` och `ConfigurationModeFrequencyMins` som multiplar av varandra.</span><span class="sxs-lookup"><span data-stu-id="e1a34-103">In the previous version of DSC, the LCM would treat `RefreshFrequencyMins` and `ConfigurationModeFrequencyMins` as multiples of each other.</span></span> <span data-ttu-id="e1a34-104">WMF 5.0 RTM bearbetas dessa egenskaper oberoende av varandra.</span><span class="sxs-lookup"><span data-stu-id="e1a34-104">In WMF 5.0 RTM, these properties are processed independent of each other.</span></span>

<span data-ttu-id="e1a34-105">Mer information finns i [konfigurera den lokala Configuration Manager](https://msdn.microsoft.com/powershell/dsc/metaconfig).</span><span class="sxs-lookup"><span data-stu-id="e1a34-105">For more information, see [Configuring the Local Configuration Manager](https://msdn.microsoft.com/powershell/dsc/metaconfig).</span></span>