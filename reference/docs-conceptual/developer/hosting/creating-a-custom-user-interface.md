---
title: Skapa ett anpassat användar gränssnitt | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: ebbaba4231b54d42cdcdef07a3ff665bd207d696
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87779785"
---
# <a name="creating-a-custom-user-interface"></a>Skapa ett anpassat användargränssnitt

Windows PowerShell tillhandahåller abstrakta klasser och gränssnitt som gör att du kan skapa ett anpassat interaktivt gränssnitt som är värd för Windows PowerShell-motorn. Om du vill skapa ett anpassat användar gränssnitt måste du implementera klassen [system. Management. Automation. Host. PSHost](/dotnet/api/System.Management.Automation.Host.PSHost) . Alternativt kan du även implementera [system. Management. Automation. Host. Pshostrawuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostRawUserInterface)och [system. Management. Automation. Host. Pshostuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface) -klasser och [system. Management. Automation. Host. Ihostsupportsinteractivesession](/dotnet/api/System.Management.Automation.Host.IHostSupportsInteractiveSession) och [system. Management. Automation. Host. Ihostuisupportsmultiplechoiceselection](/dotnet/api/System.Management.Automation.Host.IHostUISupportsMultipleChoiceSelection) -gränssnitt.
