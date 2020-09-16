---
title: Cmdlet-attribut | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- attributes [PowerShell SDK]
- attributes [PowerShell SDK], described
ms.openlocfilehash: f22c2882fbe5b2f51ca5ea218b921192b0a7d41f
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784528"
---
# <a name="cmdlet-attributes"></a><span data-ttu-id="cafcf-102">Cmdlet-attribut</span><span class="sxs-lookup"><span data-stu-id="cafcf-102">Cmdlet Attributes</span></span>

<span data-ttu-id="cafcf-103">Windows PowerShell definierar flera attribut som du kan använda för att lägga till vanliga funktioner i dina cmdletar utan att implementera den funktionen i din egen kod.</span><span class="sxs-lookup"><span data-stu-id="cafcf-103">Windows PowerShell defines several attributes that you can use to add common functionality to your cmdlets without implementing that functionality within your own code.</span></span> <span data-ttu-id="cafcf-104">Detta inkluderar det cmdlet-attribut som identifierar en Microsoft .NET Framework-klass som en cmdlet-klass, attributet OutputType som anger de .NET Framework typer som returneras av cmdleten, attributet parameter som identifierar offentliga egenskaper som cmdlet-parametrar med mera.</span><span class="sxs-lookup"><span data-stu-id="cafcf-104">This includes the Cmdlet attribute that identifies a Microsoft .NET Framework class as a cmdlet class, the OutputType attribute that specifies the .NET Framework types returned by the cmdlet, the Parameter attribute that identifies public properties as cmdlet parameters, and more.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="cafcf-105">I det här avsnittet</span><span class="sxs-lookup"><span data-stu-id="cafcf-105">In This Section</span></span>

<span data-ttu-id="cafcf-106">[Attribut i cmdlet-kod](./attributes-in-cmdlet-code.md) Beskriver fördelen med att använda attribut i cmdlet-kod.</span><span class="sxs-lookup"><span data-stu-id="cafcf-106">[Attributes in Cmdlet Code](./attributes-in-cmdlet-code.md) Describes the benefit of using attributes in cmdlet code.</span></span>

<span data-ttu-id="cafcf-107">[Attributtyper](./attribute-types.md) Beskriver de olika attribut som kan dekorera en cmdlet-klass.</span><span class="sxs-lookup"><span data-stu-id="cafcf-107">[Attribute Types](./attribute-types.md) Describes the different attributes that can decorate a cmdlet class.</span></span>

<span data-ttu-id="cafcf-108">[Deklaration av alias-attribut](./alias-attribute-declaration.md) Beskriver hur du definierar alias för ett cmdlet-parameter namn.</span><span class="sxs-lookup"><span data-stu-id="cafcf-108">[Alias Attribute Declaration](./alias-attribute-declaration.md) Describes how to define aliases for a cmdlet parameter name.</span></span>

<span data-ttu-id="cafcf-109">[Deklaration av cmdlet-attribut](./cmdlet-attribute-declaration.md) Beskriver hur du definierar en .NET Framework-klass som en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="cafcf-109">[Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md) Describes how to define a .NET Framework class as a cmdlet.</span></span>

<span data-ttu-id="cafcf-110">[Deklaration för attribut för autentiseringsuppgift](./credential-attribute-declaration.md) Beskriver hur du lägger till stöd för att konvertera inmatade strängar till ett [system. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) -objekt.</span><span class="sxs-lookup"><span data-stu-id="cafcf-110">[Credential Attribute Declaration](./credential-attribute-declaration.md) Describes how to add support for converting string input into a [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object.</span></span>

<span data-ttu-id="cafcf-111">[Deklaration av OutputType-attribut](./outputtype-attribute-declaration.md) Beskriver hur du anger de .NET Framework typer som returneras av cmdleten.</span><span class="sxs-lookup"><span data-stu-id="cafcf-111">[OutputType attribute Declaration](./outputtype-attribute-declaration.md) Describes how to specify the .NET Framework types returned by the cmdlet.</span></span>

<span data-ttu-id="cafcf-112">[Deklaration av parameter attribut](./parameter-attribute-declaration.md) Beskriver hur du definierar parametrarna för en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="cafcf-112">[Parameter Attribute Declaration](./parameter-attribute-declaration.md) Describes how to define the parameters of a cmdlet.</span></span>

<span data-ttu-id="cafcf-113">[ValidateCount-Attribute-deklaration](./validatecount-attribute-declaration.md) Beskriver hur du definierar hur många argument som tillåts för en parameter.</span><span class="sxs-lookup"><span data-stu-id="cafcf-113">[ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md) Describes how to define how many arguments are allowed for a parameter.</span></span>

<span data-ttu-id="cafcf-114">[ValidateLength-Attribute-deklaration](./validatelength-attribute-declaration.md) Beskriver hur du definierar längden (i tecken) för ett parameter argument.</span><span class="sxs-lookup"><span data-stu-id="cafcf-114">[ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md) Describes how to define the length (in characters) of a parameter argument.</span></span>

<span data-ttu-id="cafcf-115">[ValidatePattern-Attribute-deklaration](./validatepattern-attribute-declaration.md) Beskriver hur du definierar giltiga mönster för ett parameter argument.</span><span class="sxs-lookup"><span data-stu-id="cafcf-115">[ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md) Describes how to define the valid patterns for a parameter argument.</span></span>

<span data-ttu-id="cafcf-116">[ValidateRange-Attribute-deklaration](./validaterange-attribute-declaration.md) Beskriver hur du definierar ett giltigt intervall för ett parameter argument.</span><span class="sxs-lookup"><span data-stu-id="cafcf-116">[ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md) Describes how to define the valid range for a parameter argument.</span></span>

<span data-ttu-id="cafcf-117">[ValidateSet-Attribute-deklaration](./validateset-attribute-declaration.md) Beskriver hur du definierar möjliga värden för ett parameter argument.</span><span class="sxs-lookup"><span data-stu-id="cafcf-117">[ValidateSet Attribute Declaration](./validateset-attribute-declaration.md) Describes how to define the possible values for a parameter argument.</span></span>

## <a name="reference"></a><span data-ttu-id="cafcf-118">Referens</span><span class="sxs-lookup"><span data-stu-id="cafcf-118">Reference</span></span>

[<span data-ttu-id="cafcf-119">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="cafcf-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
