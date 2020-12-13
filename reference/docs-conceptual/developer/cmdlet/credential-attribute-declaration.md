---
ms.date: 09/13/2016
ms.topic: reference
title: Deklaration av attributet Credential
description: Deklaration av attributet Credential
ms.openlocfilehash: fb826d9a46cadc021fe0c667091bbc7a9251aaa8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92648604"
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
