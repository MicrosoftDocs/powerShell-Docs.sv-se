---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: DSC-resurser
ms.openlocfilehash: 0994616673b5e447c69c09154bfdb9b9126a88c8
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-resources"></a>DSC-resurser

>Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0

Önskade tillstånd Configuration (DSC) resurser innehåller byggblock för DSC-konfigurationen. En resurs Exponerar egenskaper som kan vara konfigurerade (schema) och innehåller funktioner för PowerShell-skript som den lokala Configuration Manager (MGM) anrop till ”gör den det”.

En resurs kan modellen något som generiska som en fil eller så specifik som en inställning för IIS-servern.  Grupper av som resurser kombineras till en DSC-modul som ordnar alla filer som krävs i en struktur som har en bärbar och som innehåller metadata för att identifiera hur resurserna som är avsedd att användas i.  

I följande avsnitt beskrivs DSC-resurser:

- [Inbyggda DSC-resurser](builtInResource.md)
- [Skapa anpassade DSC-resurser](authoringResource.md)
- [Inbyggda DSC-resurser för Linux](lnxBuiltInResources.md)

