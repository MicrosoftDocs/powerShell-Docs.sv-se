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
# <a name="creating-a-custom-user-interface"></a><span data-ttu-id="655c5-102">Skapa ett anpassat användargränssnitt</span><span class="sxs-lookup"><span data-stu-id="655c5-102">Creating a custom user interface</span></span>

<span data-ttu-id="655c5-103">Windows PowerShell tillhandahåller abstrakta klasser och gränssnitt som gör att du kan skapa ett anpassat interaktivt gränssnitt som är värd för Windows PowerShell-motorn.</span><span class="sxs-lookup"><span data-stu-id="655c5-103">Windows PowerShell provides abstract classes and interfaces that allow you to create a custom interactive UI that hosts the Windows PowerShell engine.</span></span> <span data-ttu-id="655c5-104">Om du vill skapa ett anpassat användar gränssnitt måste du implementera klassen [system. Management. Automation. Host. PSHost](/dotnet/api/System.Management.Automation.Host.PSHost) .</span><span class="sxs-lookup"><span data-stu-id="655c5-104">To create a custom UI, you must implement the [System.Management.Automation.Host.PSHost](/dotnet/api/System.Management.Automation.Host.PSHost) class.</span></span> <span data-ttu-id="655c5-105">Alternativt kan du även implementera [system. Management. Automation. Host. Pshostrawuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostRawUserInterface)och [system. Management. Automation. Host. Pshostuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface) -klasser och [system. Management. Automation. Host. Ihostsupportsinteractivesession](/dotnet/api/System.Management.Automation.Host.IHostSupportsInteractiveSession) och [system. Management. Automation. Host. Ihostuisupportsmultiplechoiceselection](/dotnet/api/System.Management.Automation.Host.IHostUISupportsMultipleChoiceSelection) -gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="655c5-105">Optionally, you can also implement the [System.Management.Automation.Host.Pshostrawuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostRawUserInterface)and [System.Management.Automation.Host.Pshostuserinterface](/dotnet/api/System.Management.Automation.Host.PSHostUserInterface) classes, and the [System.Management.Automation.Host.Ihostsupportsinteractivesession](/dotnet/api/System.Management.Automation.Host.IHostSupportsInteractiveSession) and [System.Management.Automation.Host.Ihostuisupportsmultiplechoiceselection](/dotnet/api/System.Management.Automation.Host.IHostUISupportsMultipleChoiceSelection) interfaces.</span></span>
