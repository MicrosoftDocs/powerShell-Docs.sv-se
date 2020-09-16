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
# <a name="credential-attribute-declaration"></a><span data-ttu-id="a76b6-102">Deklaration av attributet Credential</span><span class="sxs-lookup"><span data-stu-id="a76b6-102">Credential Attribute Declaration</span></span>

<span data-ttu-id="a76b6-103">Attributet Credential är ett valfritt attribut som kan användas med Credential-parametrar av typen [system. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) så att en sträng även kan skickas som ett argument till parametern.</span><span class="sxs-lookup"><span data-stu-id="a76b6-103">The Credential attribute is an optional attribute that can be used with credential parameters of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) so that a string can also be passed as an argument to the parameter.</span></span> <span data-ttu-id="a76b6-104">När det här attributet läggs till i en parameter deklaration, konverterar Windows PowerShell sträng ingången till ett [system. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) -objekt.</span><span class="sxs-lookup"><span data-stu-id="a76b6-104">When this attribute is added to a parameter declaration, Windows PowerShell converts the string input into a [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object.</span></span> <span data-ttu-id="a76b6-105">Till exempel använder cmdleten [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) det här attributet för att Windows PowerShell ska generera objektet [system. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) som returneras av cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a76b6-105">For example, the [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) cmdlet uses this attribute to have Windows PowerShell generate the [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object that is returned by the cmdlet.</span></span>

## <a name="syntax"></a><span data-ttu-id="a76b6-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="a76b6-106">Syntax</span></span>

```csharp
[Credential]
```

## <a name="remarks"></a><span data-ttu-id="a76b6-107">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="a76b6-107">Remarks</span></span>

- <span data-ttu-id="a76b6-108">Normalt används det här attributet av parametrar av typen [system. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) så att en sträng även kan skickas som ett argument till parametern.</span><span class="sxs-lookup"><span data-stu-id="a76b6-108">Typically this attribute is used by parameters of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) so that a string can also be passed as an argument to the parameter.</span></span> <span data-ttu-id="a76b6-109">När ett [system. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) -objekt skickas till parametern gör Windows PowerShell ingenting.</span><span class="sxs-lookup"><span data-stu-id="a76b6-109">When a [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object is passed to the parameter, Windows PowerShell does nothing.</span></span>

- <span data-ttu-id="a76b6-110">När du skapar objektet [system. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) använder Windows PowerShell den aktuella värden för att visa lämpliga prompter för användaren.</span><span class="sxs-lookup"><span data-stu-id="a76b6-110">When creating the [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object, Windows PowerShell uses the current Host to display the appropriate prompts to the user.</span></span> <span data-ttu-id="a76b6-111">Standardvärdet visar till exempel en prompt för ett användar namn och lösen ord när det här attributet används.</span><span class="sxs-lookup"><span data-stu-id="a76b6-111">For example, the default Host displays a prompt for a user name and password when this attribute is used.</span></span> <span data-ttu-id="a76b6-112">Men om en anpassad värd används som definierar en annan prompt, visas den här prompten.</span><span class="sxs-lookup"><span data-stu-id="a76b6-112">However, if a custom host is being used that defines a different prompt then that prompt would be displayed.</span></span>

- <span data-ttu-id="a76b6-113">Det här attributet används med attributet parameter.</span><span class="sxs-lookup"><span data-stu-id="a76b6-113">This attribute is used with the Parameter attribute.</span></span> <span data-ttu-id="a76b6-114">Mer information om attributet finns i deklaration av [parameter attribut](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="a76b6-114">For more information about that attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

- <span data-ttu-id="a76b6-115">Attributet Credential definieras av klassen [system. Management. Automation. Credentialattribute](/dotnet/api/System.Management.Automation.CredentialAttribute) .</span><span class="sxs-lookup"><span data-stu-id="a76b6-115">The credential attribute is defined by the [System.Management.Automation.Credentialattribute](/dotnet/api/System.Management.Automation.CredentialAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="a76b6-116">Se även</span><span class="sxs-lookup"><span data-stu-id="a76b6-116">See Also</span></span>

[<span data-ttu-id="a76b6-117">Parameteralias</span><span class="sxs-lookup"><span data-stu-id="a76b6-117">Parameter Aliases</span></span>](./parameter-aliases.md)

[<span data-ttu-id="a76b6-118">Deklaration av attributet Parameter</span><span class="sxs-lookup"><span data-stu-id="a76b6-118">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

[<span data-ttu-id="a76b6-119">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="a76b6-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
