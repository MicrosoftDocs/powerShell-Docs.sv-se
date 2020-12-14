---
ms.date: 09/13/2016
ms.topic: reference
title: Skapa ett anpassat användargränssnitt
description: Skapa ett anpassat användargränssnitt
ms.openlocfilehash: 411165f868cd524c0cef0ba9cce3188c60a7dbdf
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645413"
---
# <a name="creating-a-custom-user-interface"></a>Skapa ett anpassat användargränssnitt

Windows PowerShell tillhandahåller abstrakta klasser och gränssnitt som gör att du kan skapa ett anpassat interaktivt gränssnitt som är värd för Windows PowerShell-motorn. Om du vill skapa ett anpassat användar gränssnitt måste du implementera klassen [system. Management. Automation. Host. PSHost](/dotnet/api/System.Management.Automation.Host.PSHost) . Alternativt kan du även implementera [system. Management. Automation. Host. Pshostrawuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostRawUserInterface)och [system. Management. Automation. Host. Pshostuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface) -klasser och [system. Management. Automation. Host. Ihostsupportsinteractivesession](/dotnet/api/System.Management.Automation.Host.IHostSupportsInteractiveSession) och [system. Management. Automation. Host. Ihostuisupportsmultiplechoiceselection](/dotnet/api/System.Management.Automation.Host.IHostUISupportsMultipleChoiceSelection) -gränssnitt.
