---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.topic: conceptual
title: exempelmall för ett känt problem eller begränsning writeup
ms.openlocfilehash: 8c1004e16f78913174af2e519e451f6fd9f30ff7
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794507"
---
 >Obs: Ange en föreslagna beskrivande rubrik och en kort beskrivning

## <a name="example-erroneous-executionpolicy-errors"></a>Exempel: Felaktiga ExecutionPolicy-fel
Använda PowerShell-moduler och DSC-resurser kan resultera i fel som rapporterats om ExecutionPolicy på Windows 7.

### <a name="resolution"></a>Lösning

Att lösa, ange den **ExecutionPolicy** till **RemoteSigned** genom att köra följande kommando i en upphöjd PowerShell-session (Kör som administratör):

```powershell
Set-ExecutionPolicy RemoteSigned
```
