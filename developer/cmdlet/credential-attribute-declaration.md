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
# <a name="credential-attribute-declaration"></a><span data-ttu-id="66d22-102">Deklaration av attributet Credential</span><span class="sxs-lookup"><span data-stu-id="66d22-102">Credential Attribute Declaration</span></span>

<span data-ttu-id="66d22-103">Attributet autentiseringsuppgifter är ett valfritt attribut som kan användas med autentiseringsuppgifter parametrar av typen [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) så att en sträng kan också skickas som ett argument för parametern.</span><span class="sxs-lookup"><span data-stu-id="66d22-103">The Credential attribute is an optional attribute that can be used with credential parameters of type [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) so that a string can also be passed as an argument to the parameter.</span></span> <span data-ttu-id="66d22-104">När det här attributet har lagts till en parameterdeklaration, Windows PowerShell konverterar sträng mata in en [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) objekt.</span><span class="sxs-lookup"><span data-stu-id="66d22-104">When this attribute is added to a parameter declaration, Windows PowerShell converts the string input into a [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) object.</span></span> <span data-ttu-id="66d22-105">Till exempel den [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) cmdlet använder det här attributet har Windows PowerShell som genererar den [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) objekt som returneras av cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="66d22-105">For example, the [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) cmdlet uses this attribute to have Windows PowerShell generate the [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) object that is returned by the cmdlet.</span></span>

## <a name="syntax"></a><span data-ttu-id="66d22-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="66d22-106">Syntax</span></span>

```csharp
[Credential]
```

## <a name="remarks"></a><span data-ttu-id="66d22-107">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="66d22-107">Remarks</span></span>

- <span data-ttu-id="66d22-108">Vanligtvis det här attributet används av parametrar av typen [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) så att en sträng kan också skickas som ett argument för parametern.</span><span class="sxs-lookup"><span data-stu-id="66d22-108">Typically this attribute is used by parameters of type [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) so that a string can also be passed as an argument to the parameter.</span></span> <span data-ttu-id="66d22-109">När en [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) objektet skickas till parametern, Windows PowerShell gör ingenting.</span><span class="sxs-lookup"><span data-stu-id="66d22-109">When a [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) object is passed to the parameter, Windows PowerShell does nothing.</span></span>

- <span data-ttu-id="66d22-110">När du skapar den [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) objekt, Windows PowerShell använder aktuella värden för att visa rätt anvisningarna för användaren.</span><span class="sxs-lookup"><span data-stu-id="66d22-110">When creating the [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) object, Windows PowerShell uses the current Host to display the appropriate prompts to the user.</span></span> <span data-ttu-id="66d22-111">Till exempel standard värd visar en uppmaning om ett användarnamn och lösenord när det här attributet används.</span><span class="sxs-lookup"><span data-stu-id="66d22-111">For example, the default Host displays a prompt for a user name and password when this attribute is used.</span></span> <span data-ttu-id="66d22-112">Om en anpassad värd används som definierar en annan kommandotolk sedan denna uppmaning visas.</span><span class="sxs-lookup"><span data-stu-id="66d22-112">However, if a custom host is being used that defines a different prompt then that prompt would be displayed.</span></span>

- <span data-ttu-id="66d22-113">Det här attributet används med parametern-attribut.</span><span class="sxs-lookup"><span data-stu-id="66d22-113">This attribute is used with the Parameter attribute.</span></span> <span data-ttu-id="66d22-114">Läs mer om attributet [parameterdeklaration för attributet](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="66d22-114">For more information about that attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

- <span data-ttu-id="66d22-115">Autentiseringsuppgifter attributet definieras av den [System.Management.Automation.Credentialattribute](/dotnet/api/System.Management.Automation.CredentialAttribute) klass.</span><span class="sxs-lookup"><span data-stu-id="66d22-115">The credential attribute is defined by the [System.Management.Automation.Credentialattribute](/dotnet/api/System.Management.Automation.CredentialAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="66d22-116">Se även</span><span class="sxs-lookup"><span data-stu-id="66d22-116">See Also</span></span>

[<span data-ttu-id="66d22-117">Parameteralias</span><span class="sxs-lookup"><span data-stu-id="66d22-117">Parameter Aliases</span></span>](./parameter-aliases.md)

[<span data-ttu-id="66d22-118">Attributet parameterdeklaration</span><span class="sxs-lookup"><span data-stu-id="66d22-118">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

[<span data-ttu-id="66d22-119">Skriva en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="66d22-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
