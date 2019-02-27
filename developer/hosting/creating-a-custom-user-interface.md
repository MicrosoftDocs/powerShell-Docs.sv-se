---
title: Skapa ett anpassat användargränssnitt | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d7286443-eed4-43d5-b809-50cdcdcba088
caps.latest.revision: 4
ms.openlocfilehash: 23518c625fe1138e1bd2bcc895274cb21d7daf8a
ms.sourcegitcommit: c581c4c8036edf55147e7bce4b00c860da6c5a8b
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/25/2019
ms.locfileid: "56852215"
---
# <a name="creating-a-custom-user-interface"></a>Skapa ett anpassat användargränssnitt

Windows PowerShell innehåller abstrakta klasser och gränssnitt som gör att du kan skapa ett anpassat interaktivt gränssnitt som är värd för Windows PowerShell-motorn. Om du vill skapa ett anpassat gränssnitt, måste du implementera den [System.Management.Automation.Host.PSHost](/dotnet/api/System.Management.Automation.Host.PSHost) klass. Du kan också du kan också implementera den [System.Management.Automation.Host.Pshostrawuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostRawUserInterface)och [System.Management.Automation.Host.Pshostuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface) klasser och [System.Management.Automation.Host.Ihostsupportsinteractivesession](/dotnet/api/System.Management.Automation.Host.IHostSupportsInteractiveSession) och [System.Management.Automation.Host.Ihostuisupportsmultiplechoiceselection](/dotnet/api/System.Management.Automation.Host.IHostUISupportsMultipleChoiceSelection) gränssnitt.
