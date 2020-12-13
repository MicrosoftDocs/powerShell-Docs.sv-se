---
ms.date: 09/13/2016
ms.topic: reference
title: Visa felinformation
description: Visa felinformation
ms.openlocfilehash: 37a3adb91d0e616a5c7f27bcab866f8da139f969
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92653062"
---
# <a name="displaying-error-information"></a>Visa felinformation

I det här avsnittet beskrivs hur användare kan visa fel information.

När cmdleten påträffar ett fel, ser presentationen av fel informationen som standard ut ungefär så här:

```powershell
$ stop-service lanmanworkstation
You do not have sufficient permissions to stop the service Workstation.
```

Användare kan dock visa fel efter kategori genom `$ErrorView` att ange variabeln till `"CategoryView"` . I vyn kategori visas viss information från fel posten i stället för en kostnads fri text Beskrivning av felet. Den här vyn kan vara användbar om du har en lång lista med fel som ska genomsökas. Föregående fel meddelande visas i kategorivyn enligt följande.

```powershell
$ $ErrorView = "CategoryView"
$ stop-service lanmanworkstation
CloseError: (System.ServiceProcess.ServiceController:ServiceController) [stop-service], ServiceCommandException
```

Mer information om fel kategorier finns i [fel poster för Windows PowerShell](./windows-powershell-error-records.md).

## <a name="see-also"></a>Se även

[Windows PowerShell-felposter](./windows-powershell-error-records.md)

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)
