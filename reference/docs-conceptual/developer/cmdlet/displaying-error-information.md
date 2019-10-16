---
title: Visar fel information | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76fcc0c1-9795-45d3-a564-40f822b657b5
caps.latest.revision: 8
ms.openlocfilehash: 4bc8666ee9053eb368402c8644558f4fe2dcc9ee
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359369"
---
# <a name="displaying-error-information"></a>Visa felinformation

I det här avsnittet beskrivs hur användare kan visa fel information.

När cmdleten påträffar ett fel, ser presentationen av fel informationen som standard ut ungefär så här:

```powershell
$ stop-service lanmanworkstation
You do not have sufficient permissions to stop the service Workstation.
```

Användare kan dock visa fel efter kategori genom att ange variabeln `$ErrorView` till `"CategoryView"`. I vyn kategori visas viss information från fel posten i stället för en kostnads fri text Beskrivning av felet. Den här vyn kan vara användbar om du har en lång lista med fel som ska genomsökas. Föregående fel meddelande visas i kategorivyn enligt följande.

```powershell
$ $ErrorView = "CategoryView"
$ stop-service lanmanworkstation
CloseError: (System.ServiceProcess.ServiceController:ServiceController) [stop-service], ServiceCommandException
```

Mer information om fel kategorier finns i [fel poster för Windows PowerShell](./windows-powershell-error-records.md).

## <a name="see-also"></a>Se även

[Windows PowerShell-felposter](./windows-powershell-error-records.md)

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)
