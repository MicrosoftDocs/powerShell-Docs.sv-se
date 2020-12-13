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
# <a name="credential-attribute-declaration"></a><span data-ttu-id="7e1f4-103">Deklaration av attributet Credential</span><span class="sxs-lookup"><span data-stu-id="7e1f4-103">Credential Attribute Declaration</span></span>

<span data-ttu-id="7e1f4-104">Attributet Credential är ett valfritt attribut som kan användas med Credential-parametrar av typen [system. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) så att en sträng även kan skickas som ett argument till parametern.</span><span class="sxs-lookup"><span data-stu-id="7e1f4-104">The Credential attribute is an optional attribute that can be used with credential parameters of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) so that a string can also be passed as an argument to the parameter.</span></span> <span data-ttu-id="7e1f4-105">När det här attributet läggs till i en parameter deklaration, konverterar Windows PowerShell sträng ingången till ett [system. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) -objekt.</span><span class="sxs-lookup"><span data-stu-id="7e1f4-105">When this attribute is added to a parameter declaration, Windows PowerShell converts the string input into a [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object.</span></span> <span data-ttu-id="7e1f4-106">Till exempel använder cmdleten [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) det här attributet för att Windows PowerShell ska generera objektet [system. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) som returneras av cmdleten.</span><span class="sxs-lookup"><span data-stu-id="7e1f4-106">For example, the [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) cmdlet uses this attribute to have Windows PowerShell generate the [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object that is returned by the cmdlet.</span></span>

## <a name="syntax"></a><span data-ttu-id="7e1f4-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="7e1f4-107">Syntax</span></span>

```csharp
[Credential]
```

## <a name="remarks"></a><span data-ttu-id="7e1f4-108">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="7e1f4-108">Remarks</span></span>

- <span data-ttu-id="7e1f4-109">Normalt används det här attributet av parametrar av typen [system. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) så att en sträng även kan skickas som ett argument till parametern.</span><span class="sxs-lookup"><span data-stu-id="7e1f4-109">Typically this attribute is used by parameters of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) so that a string can also be passed as an argument to the parameter.</span></span> <span data-ttu-id="7e1f4-110">När ett [system. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) -objekt skickas till parametern gör Windows PowerShell ingenting.</span><span class="sxs-lookup"><span data-stu-id="7e1f4-110">When a [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object is passed to the parameter, Windows PowerShell does nothing.</span></span>

- <span data-ttu-id="7e1f4-111">När du skapar objektet [system. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) använder Windows PowerShell den aktuella värden för att visa lämpliga prompter för användaren.</span><span class="sxs-lookup"><span data-stu-id="7e1f4-111">When creating the [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object, Windows PowerShell uses the current Host to display the appropriate prompts to the user.</span></span> <span data-ttu-id="7e1f4-112">Standardvärdet visar till exempel en prompt för ett användar namn och lösen ord när det här attributet används.</span><span class="sxs-lookup"><span data-stu-id="7e1f4-112">For example, the default Host displays a prompt for a user name and password when this attribute is used.</span></span> <span data-ttu-id="7e1f4-113">Men om en anpassad värd används som definierar en annan prompt, visas den här prompten.</span><span class="sxs-lookup"><span data-stu-id="7e1f4-113">However, if a custom host is being used that defines a different prompt then that prompt would be displayed.</span></span>

- <span data-ttu-id="7e1f4-114">Det här attributet används med attributet parameter.</span><span class="sxs-lookup"><span data-stu-id="7e1f4-114">This attribute is used with the Parameter attribute.</span></span> <span data-ttu-id="7e1f4-115">Mer information om attributet finns i deklaration av [parameter attribut](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="7e1f4-115">For more information about that attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

- <span data-ttu-id="7e1f4-116">Attributet Credential definieras av klassen [system. Management. Automation. Credentialattribute](/dotnet/api/System.Management.Automation.CredentialAttribute) .</span><span class="sxs-lookup"><span data-stu-id="7e1f4-116">The credential attribute is defined by the [System.Management.Automation.Credentialattribute](/dotnet/api/System.Management.Automation.CredentialAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="7e1f4-117">Se även</span><span class="sxs-lookup"><span data-stu-id="7e1f4-117">See Also</span></span>

[<span data-ttu-id="7e1f4-118">Parameteralias</span><span class="sxs-lookup"><span data-stu-id="7e1f4-118">Parameter Aliases</span></span>](./parameter-aliases.md)

[<span data-ttu-id="7e1f4-119">Deklaration av attributet Parameter</span><span class="sxs-lookup"><span data-stu-id="7e1f4-119">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

[<span data-ttu-id="7e1f4-120">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="7e1f4-120">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
