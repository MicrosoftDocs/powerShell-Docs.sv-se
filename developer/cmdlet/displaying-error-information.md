---
title: Visa felinformation | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76fcc0c1-9795-45d3-a564-40f822b657b5
caps.latest.revision: 8
ms.openlocfilehash: 4bc8666ee9053eb368402c8644558f4fe2dcc9ee
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068291"
---
# <a name="displaying-error-information"></a>Visa felinformation

Det här avsnittet beskrivs hur där användare kan visa information om felet.

När din cmdlet påträffar ett fel, kommer, presentation av felinformationen som standard likna följande utdata om felet.

```powershell
$ stop-service lanmanworkstation
You do not have sufficient permissions to stop the service Workstation.
```

Användare kan dock visa fel efter kategori genom att ange den `$ErrorView` variabeln `"CategoryView"`. Kategorivyn visas viss information från en Felpost snarare än en fri text beskrivning av felet. Den här vyn kan vara användbart om du har en lång lista med fel att skanna. Vyn kategori visas föregående felmeddelande på följande sätt.

```powershell
$ $ErrorView = "CategoryView"
$ stop-service lanmanworkstation
CloseError: (System.ServiceProcess.ServiceController:ServiceController) [stop-service], ServiceCommandException
```

Läs mer om felkategorier [Windows PowerShell-felposter](./windows-powershell-error-records.md).

## <a name="see-also"></a>Se även

[Windows PowerShell-felposter](./windows-powershell-error-records.md)

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
