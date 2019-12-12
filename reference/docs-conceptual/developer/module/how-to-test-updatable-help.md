---
title: Testa uppdaterbar hjälp | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e064048-2b94-4365-bdb7-f1ee7c0a7fd7
caps.latest.revision: 6
ms.openlocfilehash: cecc6c26ccaece06462ddd74b53534137fcf3037
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72357430"
---
# <a name="how-to-test-updatable-help"></a>Testa uppdateringsbar hjälp

I det här avsnittet beskrivs metoder för att testa uppdaterings bara hjälp för en modul.

## <a name="using-verbose-to-detect-errors"></a>Använda utförlig för att identifiera fel

När du har laddat upp XML-HelpInfo och CAB-filerna för modulen testar du filerna genom att köra ett [Update-Help-](/powershell/module/Microsoft.PowerShell.Core/Update-Help) kommando med **utförlig** parameter. Den **utförliga** parametern dirigerar `Update-Help` för att rapportera de viktiga stegen i sina åtgärder, från att läsa nyckeln **HelpInfoUri** i modulen manifest för att validera fil typerna i den uppackade CAB-filen och placera filerna i den språkspecifika modulen.

När alla utförliga meddelanden har åtgärd ATS kör du ett `Update-Help`-kommando med **fel söknings** parametern. Den här parametern ska identifiera eventuella återstående problem med de uppdateringsfiler som kan uppdateras.