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
# <a name="frequencies-for-refreshmode-and-configurationmode-dont-need-to-be-multiples-of-each-other"></a>Frekvenserna för RefreshMode och ConfigurationMode behöver inte vara multiplar av varandra

I den tidigare versionen av DSC LCM skulle behandla `RefreshFrequencyMins` och `ConfigurationModeFrequencyMins` som multiplar av varandra. I WMF 5.0 RTM bearbetas de här egenskaperna oberoende av varandra.

Mer information finns i [konfigurerar den lokala Konfigurationshanteraren](https://msdn.microsoft.com/powershell/dsc/metaconfig).
