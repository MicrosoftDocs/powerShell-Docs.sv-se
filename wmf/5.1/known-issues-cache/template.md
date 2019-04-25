---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.topic: conceptual
title: exempelmall för ett känt problem eller begränsning writeup
ms.openlocfilehash: 8c1004e16f78913174af2e519e451f6fd9f30ff7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62055555"
---
 >Obs: Ange en föreslagna beskrivande rubrik och en kort beskrivning

## <a name="example-erroneous-executionpolicy-errors"></a>Exempel: Felaktiga ExecutionPolicy-fel
Använda PowerShell-moduler och DSC-resurser kan resultera i fel som rapporterats om ExecutionPolicy på Windows 7.

### <a name="resolution"></a>Lösning

Att lösa, ange den **ExecutionPolicy** till **RemoteSigned** genom att köra följande kommando i en upphöjd PowerShell-session (Kör som administratör):

```powershell
Set-ExecutionPolicy RemoteSigned
```
