---
title: Lägga till anteckningar till en Cmdlet-hjälpavsnittet | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2bea35e5-b680-4f86-b928-176890aac99d
caps.latest.revision: 5
ms.openlocfilehash: 4e9ca9a3bbcbc900d079b9275bc47d21de9e2996
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083424"
---
# <a name="how-to-add-notes-to-a-cmdlet-help-topic"></a>Lägga till anteckningar i ett cmdlet-hjälpavsnitt

Det här avsnittet beskrivs hur du lägger till avsnittet anteckningar till en Windows PowerShell® cmdlet-hjälpavsnittet. Avsnittet med anteckningar används för att förklara information som inte passar enkelt i andra strukturerade avsnitt, till exempel en mer detaljerad förklaring av en parameter. Det här innehållet kan omfatta kommentarer om hur cmdlet: en fungerar med en viss leverantör, några unika, men viktiga, användningsområden för cmdlet eller sätt att undvika möjlig felvillkor.

Det finns ingen gräns för hur många anteckningar som du kan lägga till avsnittet Anteckningar. Observera att varje lägger du till ett par \<maml:alert > etiketter till den \<maml:alertset > noden. Innehållet i varje anteckning har lagts till i en uppsättning \<maml:para > taggar. Använd tomt \<maml:para >-taggar för avstånd.

I följande XML-visas en \<maml:alertset > noden med två anteckningar. Observera att varje anteckning har en valfri \<maml:title > taggen (rubriker som kan användas för att gruppera en uppsättning \<maml:alert > taggar), och att varje anteckning har en tom rad efter innehållet för avstånd.

```xml
<maml:alertSet>
  <maml:title>title for Note 1</maml:title>
  <maml:alert>
    <maml:para> Note 1</maml:para>
    <maml:para></maml:para>
  </maml:alert>
  <maml:title>title for Note 2</maml:title>
  <maml:alert>
    <maml:para> Note 1</maml:para>
    <maml:para></maml:para>
  </maml:alert>
</maml:alertSet>
```



