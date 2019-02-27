---
title: Så här uppdaterar du hjälpfiler | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 495869a6-080e-4401-9ddc-16edd2f86857
caps.latest.revision: 6
ms.openlocfilehash: 2c1fbd70aab1f65f33ea206b7ab1e2bd3dfd8c7a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846482"
---
# <a name="how-to-update-help-files"></a>Uppdatera hjälpfiler

Det här avsnittet förklarar hur du uppdaterar hjälpfilerna för en modul som har stöd för uppdateringsbar hjälp.

## <a name="updating-help-files"></a>Uppdaterar hjälpfiler

Det finns många skäl att uppdatera hjälpfiler, till exempel hur du korrigerar fel, förstå ett koncept, besvara vanliga frågor, att lägga till nya filer eller att lägga till nya och bättre exempel.

Så här uppdaterar en hjälpfilen:

1. Ändra filerna.

2. Omvandla filerna till andra UI-kulturer.

3. Samla in alla hjälpfiler (nya, ändrade och oförändrade) för modulen i varje UI-kultur.

4. Validera filerna mot XML-schema.

5. Återskapa CAB-filer för varje UI-kultur.

6. Öka versionsnumren för CAB-filen för varje UI-kultur i HelpInfo XML-fil.

7. Ladda upp nya CAB-filer till den plats som anges av värdet för den **HelpContentUri** element i HelpInfo XML-filen. Ersätt de äldre CAB-filerna med de nya CAB-filerna.

8. Överföra den uppdaterade HelpInfo XML-filen till den plats som anges av den **HelpInfoUri** nyckeln i modulmanifestet. Ersätt den äldre HelpInfo XML-filen med den nya filen.