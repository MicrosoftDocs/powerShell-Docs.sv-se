---
title: StopProc självstudien | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a142aeb6-9c11-44a0-b34f-1f9470fa347b
caps.latest.revision: 5
ms.openlocfilehash: 27c8e2c7525aba38e69e50b2b7fd3b18b8e54989
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794407"
---
# <a name="stopproc-tutorial"></a>Självstudie om StopProc

Det här avsnittet innehåller en självstudie för att skapa cmdlet Stop-processen, som liknar den [Stop-Process](/powershell/module/Microsoft.PowerShell.Management/Stop-Process) cmdlet som tillhandahålls av Windows PowerShell. Den här självstudien innehåller delar av kod som illustrerar hur cmdletar implementeras och en förklaring av koden.

## <a name="topics-in-this-tutorial"></a>Avsnitt i den här självstudien

Ämnena i den här självstudien är avsedda att läsas sekventiellt, med varje avsnitt som bygger på vad som beskrevs i föregående avsnitt.

[Skapa en Cmdlet som ändrar systemet](./creating-a-cmdlet-that-modifies-the-system.md) i det här avsnittet beskriver hur du skapar en cmdlet som stöder system ändringar, som att stoppa en process som körs på datorn.

[Att lägga till meddelanden för användare i din Cmdlet](./adding-user-messages-to-your-cmdlet.md) det här avsnittet beskrivs hur du lägger till möjligheten att skriva meddelanden för användare, felsökningsmeddelanden, varningsmeddelanden och statusinformation i cmdlet:.

[Att lägga till alias och jokertecken Expansion och bidra till att Cmdlet-parametrarna](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md) i det här avsnittet beskriver hur du skapar en cmdlet som stöder parameteralias, hjälp och jokertecken expansion.

[Att lägga till parametern anger cmdletar](./adding-parameter-sets-to-a-cmdlet.md) det här avsnittet beskrivs hur du lägger till parametern anger att en cmdlet. Parameteruppsättningar kan cmdleten ska fungera på olika sätt beroende på vilka parametrar som anges av användaren.

## <a name="see-also"></a>Se även

[Skapa en Cmdlet som ändrar systemet](./creating-a-cmdlet-that-modifies-the-system.md)

[Meddelanden för att lägga till användare i cmdlet:](./adding-user-messages-to-your-cmdlet.md)

[Att lägga till alias och jokertecken Expansion och bidra till att Cmdlet-parametrarna](./adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters.md)

[Att lägga till parametern anger till cmdlet: ar](./adding-parameter-sets-to-a-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
