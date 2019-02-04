---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.topic: conceptual
title: exempelmall för ett känt problem eller begränsning writeup
ms.openlocfilehash: ed7ae3de392c8902917e5b98fd4fc9d5138ccaed
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688681"
---
>Obs: Ange en föreslagna beskrivande rubrik och en kort beskrivning

## <a name="example-erroneous-executionpolicy-errors"></a>Exempel: Felaktiga ExecutionPolicy-fel ##
Använda PowerShell-moduler och DSC-resurser kan resultera i fel som rapporterats om ExecutionPolicy på Windows 7.

### <a name="resolution"></a>Lösning

Att lösa, ange den **ExecutionPolicy** till **RemoteSigned** genom att köra följande kommando i en upphöjd PowerShell-session (Kör som administratör):

```powershell
Set-ExecutionPolicy RemoteSigned
```
