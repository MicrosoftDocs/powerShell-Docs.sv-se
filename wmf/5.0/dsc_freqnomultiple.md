---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, powershell, inställning"
ms.openlocfilehash: 30055cff87159df98029e25409782e0fe2f0bae4
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="frequencies-for-refreshmode-and-configurationmode-dont-need-to-be-multiples-of-each-other"></a>Frekvensen för RefreshMode och ConfigurationMode behöver inte vara en multipel av varandra

I den tidigare versionen av DSC MGM skulle behandla `RefreshFrequencyMins` och `ConfigurationModeFrequencyMins` som multiplar av varandra. WMF 5.0 RTM bearbetas dessa egenskaper oberoende av varandra. 

Mer information finns i [konfigurera den lokala Configuration Manager](https://msdn.microsoft.com/powershell/dsc/metaconfig).

