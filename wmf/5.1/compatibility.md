---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: WMF, powershell, inställning
title: WMF 5.1 operativsystemskompatibilitet
ms.openlocfilehash: f4d7d1403c1f397bf6720485d7a7302543c2010f
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794977"
---
# <a name="wmf-51-operating-system-compatibility"></a>WMF 5.1 operativsystemskompatibilitet

> [!NOTE]
> Den här informationen är preliminär och kan komma att ändras.

| Operativsystemversion | [WMF 5.1](https://aka.ms/wmf51download) | [WMF 5.0](https://aka.ms/wmf5download) | [WMF 4.0](https://aka.ms/wmf4download) |  [WMF 3.0](https://aka.ms/wmf3download) | [WMF 2.0](https://aka.ms/wmf2download) |
| ------------------------ | ----------- | ----------- | ----------- | ------------ |  ------------- |
| Windows Server 2016 | Levereras i-box * |  |  |  |  |
| Windows 10 | Levereras i-box * | Levereras i-box *  | | | |
| Windows Server 2012 R2| Ja | Ja | Levereras i box |  |  |
| Windows 8.1 | Ja | Ja |  Levereras i box |  |  |
| Windows Server 2012 | Ja | Ja | Ja |  Levereras i box | |
| Windows 8 |  |  |  | Levereras i box | |
| Windows Server 2008 R2 SP1 | Ja | Ja | Ja |  Ja| Levereras i box |
| Windows 7 SP1  | Ja | Ja | Ja | Ja | Levereras i box |
| Windows Server 2008 SP2 | | | | Ja | Ja |
| Windows Vista | | | | | Ja |
| Windows Server 2003| | | |  | Ja |
| Windows XP | | | |  | Ja |

Om ”levereras i-box *”: Funktionerna i WMF 5.0 ingick i den ursprungliga Windows 10 RTM-versionen.
Funktionerna i WMF 5.1 infördes i Windows Server 2016 och Windows 10 Anniversary Edition.
WMF 5.1 kan inte användas för dessa versioner av operativsystemet som uppdateringarna tillhandahålls via Windows Update.

En sak att tänka på är att WMF inte levereras i Windows.
WMF är ett uppgraderingspaket som tillhandahåller en uppsättning Windows-funktioner för tidigare Windows-versioner.
Detta kan göra en viktig skillnad när du söker hjälp för någon av dessa funktioner, som versionen för dessa komponenter inte kommer att matcha vad levereras i det ursprungliga operativsystemet.
