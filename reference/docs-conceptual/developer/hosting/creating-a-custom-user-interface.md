---
title: Skapa ett anpassat användar gränssnitt | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d7286443-eed4-43d5-b809-50cdcdcba088
caps.latest.revision: 4
ms.openlocfilehash: 23518c625fe1138e1bd2bcc895274cb21d7daf8a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "84514843"
---
# <a name="creating-a-custom-user-interface"></a>Skapa ett anpassat användargränssnitt

Windows PowerShell tillhandahåller abstrakta klasser och gränssnitt som gör att du kan skapa ett anpassat interaktivt gränssnitt som är värd för Windows PowerShell-motorn. Om du vill skapa ett anpassat användar gränssnitt måste du implementera klassen [system. Management. Automation. Host. PSHost](/dotnet/api/System.Management.Automation.Host.PSHost) . Alternativt kan du även implementera [system. Management. Automation. Host. Pshostrawuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostRawUserInterface)och [system. Management. Automation. Host. Pshostuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface) -klasser och [system. Management. Automation. Host. Ihostsupportsinteractivesession](/dotnet/api/System.Management.Automation.Host.IHostSupportsInteractiveSession) och [system. Management. Automation. Host. Ihostuisupportsmultiplechoiceselection](/dotnet/api/System.Management.Automation.Host.IHostUISupportsMultipleChoiceSelection) -gränssnitt.
