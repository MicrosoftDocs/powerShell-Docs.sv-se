---
title: Autentiseringsuppgifter för attributet deklarationen | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 96a5dcad-faed-44d8-8c80-321f10499710
caps.latest.revision: 6
ms.openlocfilehash: 1513d340cdadc5cb7622e791cc3c163ff39dfe1d
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795410"
---
# <a name="credential-attribute-declaration"></a>Deklaration av attributet Credential

Attributet autentiseringsuppgifter är ett valfritt attribut som kan användas med autentiseringsuppgifter parametrar av typen [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) så att en sträng kan också skickas som ett argument för parametern. När det här attributet har lagts till en parameterdeklaration, Windows PowerShell konverterar sträng mata in en [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) objekt. Till exempel den [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) cmdlet använder det här attributet har Windows PowerShell som genererar den [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) objekt som returneras av cmdlet: en.

## <a name="syntax"></a>Syntax

```csharp
[Credential]
```

## <a name="remarks"></a>Anmärkningar

- Vanligtvis det här attributet används av parametrar av typen [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) så att en sträng kan också skickas som ett argument för parametern. När en [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) objektet skickas till parametern, Windows PowerShell gör ingenting.

- När du skapar den [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) objekt, Windows PowerShell använder aktuella värden för att visa rätt anvisningarna för användaren. Till exempel standard värd visar en uppmaning om ett användarnamn och lösenord när det här attributet används. Om en anpassad värd används som definierar en annan kommandotolk sedan denna uppmaning visas.

- Det här attributet används med parametern-attribut. Läs mer om attributet [parameterdeklaration för attributet](./parameter-attribute-declaration.md).

- Autentiseringsuppgifter attributet definieras av den [System.Management.Automation.Credentialattribute](/dotnet/api/System.Management.Automation.CredentialAttribute) klass.

## <a name="see-also"></a>Se även

[Parameteralias](./parameter-aliases.md)

[Attributet parameterdeklaration](./parameter-attribute-declaration.md)

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
