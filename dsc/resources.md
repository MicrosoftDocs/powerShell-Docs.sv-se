---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: DSC-resurser
ms.openlocfilehash: 27e16c39699bb96b2829744b5700f75f59f8802f
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
---
# <a name="dsc-resources"></a>DSC-resurser

>Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0

Önskade tillstånd Configuration (DSC) resurser innehåller byggblock för DSC-konfigurationen. En resurs Exponerar egenskaper som kan vara konfigurerade (schema) och innehåller funktioner för PowerShell-skript som den lokala Configuration Manager (MGM) anrop till ”gör den det”.

En resurs kan modellen något som generiska som en fil eller så specifik som en inställning för IIS-servern.  Grupper av som resurser kombineras till en DSC-modul som ordnar alla filer som krävs i en struktur som har en bärbar och som innehåller metadata för att identifiera hur resurserna som är avsedd att användas i.

I följande avsnitt beskrivs DSC-resurser:

- [Inbyggda DSC-resurser](builtInResource.md)
- [Skapa anpassade DSC-resurser](authoringResource.md)
- [Inbyggda DSC-resurser för Linux](lnxBuiltInResources.md)