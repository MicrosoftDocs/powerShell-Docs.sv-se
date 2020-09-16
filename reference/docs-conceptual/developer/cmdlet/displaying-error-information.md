---
title: Visar fel information | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e542110e9c35a74c5d4c112b0a831f7f8ad9242e
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774583"
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
