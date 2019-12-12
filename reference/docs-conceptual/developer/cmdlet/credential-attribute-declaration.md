---
title: Deklaration för attribut för autentiseringsuppgift | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 96a5dcad-faed-44d8-8c80-321f10499710
caps.latest.revision: 6
ms.openlocfilehash: 49a62ccb09f06f77862d4737199e58293e7fbe0a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359418"
---
# <a name="credential-attribute-declaration"></a>Deklaration av attributet Credential

Attributet Credential är ett valfritt attribut som kan användas med Credential-parametrar av typen [system. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) så att en sträng även kan skickas som ett argument till parametern. När det här attributet läggs till i en parameter deklaration, konverterar Windows PowerShell sträng ingången till ett [system. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) -objekt. Till exempel använder cmdleten [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) det här attributet för att Windows PowerShell ska generera objektet [system. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) som returneras av cmdleten.

## <a name="syntax"></a>Syntax

```csharp
[Credential]
```

## <a name="remarks"></a>Anmärkningar

- Normalt används det här attributet av parametrar av typen [system. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) så att en sträng även kan skickas som ett argument till parametern. När ett [system. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) -objekt skickas till parametern gör Windows PowerShell ingenting.

- När du skapar objektet [system. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) använder Windows PowerShell den aktuella värden för att visa lämpliga prompter för användaren. Standardvärdet visar till exempel en prompt för ett användar namn och lösen ord när det här attributet används. Men om en anpassad värd används som definierar en annan prompt, visas den här prompten.

- Det här attributet används med attributet parameter. Mer information om attributet finns i deklaration av [parameter attribut](./parameter-attribute-declaration.md).

- Attributet Credential definieras av klassen [system. Management. Automation. Credentialattribute](/dotnet/api/System.Management.Automation.CredentialAttribute) .

## <a name="see-also"></a>Se även

[Parameter-alias](./parameter-aliases.md)

[Deklaration av parameter attribut](./parameter-attribute-declaration.md)

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)
