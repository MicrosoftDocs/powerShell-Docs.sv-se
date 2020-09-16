---
title: Deklaration för attribut för autentiseringsuppgift | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: a6deca52fa6c9e46138ae92401f58ac5dbd15852
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784375"
---
# <a name="credential-attribute-declaration"></a>Deklaration av attributet Credential

Attributet Credential är ett valfritt attribut som kan användas med Credential-parametrar av typen [system. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) så att en sträng även kan skickas som ett argument till parametern. När det här attributet läggs till i en parameter deklaration, konverterar Windows PowerShell sträng ingången till ett [system. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) -objekt. Till exempel använder cmdleten [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) det här attributet för att Windows PowerShell ska generera objektet [system. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) som returneras av cmdleten.

## <a name="syntax"></a>Syntax

```csharp
[Credential]
```

## <a name="remarks"></a>Kommentarer

- Normalt används det här attributet av parametrar av typen [system. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) så att en sträng även kan skickas som ett argument till parametern. När ett [system. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) -objekt skickas till parametern gör Windows PowerShell ingenting.

- När du skapar objektet [system. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) använder Windows PowerShell den aktuella värden för att visa lämpliga prompter för användaren. Standardvärdet visar till exempel en prompt för ett användar namn och lösen ord när det här attributet används. Men om en anpassad värd används som definierar en annan prompt, visas den här prompten.

- Det här attributet används med attributet parameter. Mer information om attributet finns i deklaration av [parameter attribut](./parameter-attribute-declaration.md).

- Attributet Credential definieras av klassen [system. Management. Automation. Credentialattribute](/dotnet/api/System.Management.Automation.CredentialAttribute) .

## <a name="see-also"></a>Se även

[Parameteralias](./parameter-aliases.md)

[Deklaration av attributet Parameter](./parameter-attribute-declaration.md)

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)
