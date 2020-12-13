---
ms.date: 09/13/2016
ms.topic: reference
title: Cmdlet-attribut
description: Cmdlet-attribut
ms.openlocfilehash: 6a106f33cb34c6c33b88a981815543bc9af4e4ba
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92653516"
---
# <a name="cmdlet-attributes"></a><span data-ttu-id="83c47-103">Cmdlet-attribut</span><span class="sxs-lookup"><span data-stu-id="83c47-103">Cmdlet Attributes</span></span>

<span data-ttu-id="83c47-104">Windows PowerShell definierar flera attribut som du kan använda för att lägga till vanliga funktioner i dina cmdletar utan att implementera den funktionen i din egen kod.</span><span class="sxs-lookup"><span data-stu-id="83c47-104">Windows PowerShell defines several attributes that you can use to add common functionality to your cmdlets without implementing that functionality within your own code.</span></span> <span data-ttu-id="83c47-105">Detta inkluderar det cmdlet-attribut som identifierar en Microsoft .NET Framework-klass som en cmdlet-klass, attributet OutputType som anger de .NET Framework typer som returneras av cmdleten, attributet parameter som identifierar offentliga egenskaper som cmdlet-parametrar med mera.</span><span class="sxs-lookup"><span data-stu-id="83c47-105">This includes the Cmdlet attribute that identifies a Microsoft .NET Framework class as a cmdlet class, the OutputType attribute that specifies the .NET Framework types returned by the cmdlet, the Parameter attribute that identifies public properties as cmdlet parameters, and more.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="83c47-106">I det här avsnittet</span><span class="sxs-lookup"><span data-stu-id="83c47-106">In This Section</span></span>

<span data-ttu-id="83c47-107">[Attribut i cmdlet-kod](./attributes-in-cmdlet-code.md) Beskriver fördelen med att använda attribut i cmdlet-kod.</span><span class="sxs-lookup"><span data-stu-id="83c47-107">[Attributes in Cmdlet Code](./attributes-in-cmdlet-code.md) Describes the benefit of using attributes in cmdlet code.</span></span>

<span data-ttu-id="83c47-108">[Attributtyper](./attribute-types.md) Beskriver de olika attribut som kan dekorera en cmdlet-klass.</span><span class="sxs-lookup"><span data-stu-id="83c47-108">[Attribute Types](./attribute-types.md) Describes the different attributes that can decorate a cmdlet class.</span></span>

<span data-ttu-id="83c47-109">[Deklaration av alias-attribut](./alias-attribute-declaration.md) Beskriver hur du definierar alias för ett cmdlet-parameter namn.</span><span class="sxs-lookup"><span data-stu-id="83c47-109">[Alias Attribute Declaration](./alias-attribute-declaration.md) Describes how to define aliases for a cmdlet parameter name.</span></span>

<span data-ttu-id="83c47-110">[Deklaration av cmdlet-attribut](./cmdlet-attribute-declaration.md) Beskriver hur du definierar en .NET Framework-klass som en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="83c47-110">[Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md) Describes how to define a .NET Framework class as a cmdlet.</span></span>

<span data-ttu-id="83c47-111">[Deklaration för attribut för autentiseringsuppgift](./credential-attribute-declaration.md) Beskriver hur du lägger till stöd för att konvertera inmatade strängar till ett [system. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) -objekt.</span><span class="sxs-lookup"><span data-stu-id="83c47-111">[Credential Attribute Declaration](./credential-attribute-declaration.md) Describes how to add support for converting string input into a [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object.</span></span>

<span data-ttu-id="83c47-112">[Deklaration av OutputType-attribut](./outputtype-attribute-declaration.md) Beskriver hur du anger de .NET Framework typer som returneras av cmdleten.</span><span class="sxs-lookup"><span data-stu-id="83c47-112">[OutputType attribute Declaration](./outputtype-attribute-declaration.md) Describes how to specify the .NET Framework types returned by the cmdlet.</span></span>

<span data-ttu-id="83c47-113">[Deklaration av parameter attribut](./parameter-attribute-declaration.md) Beskriver hur du definierar parametrarna för en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="83c47-113">[Parameter Attribute Declaration](./parameter-attribute-declaration.md) Describes how to define the parameters of a cmdlet.</span></span>

<span data-ttu-id="83c47-114">[ValidateCount-Attribute-deklaration](./validatecount-attribute-declaration.md) Beskriver hur du definierar hur många argument som tillåts för en parameter.</span><span class="sxs-lookup"><span data-stu-id="83c47-114">[ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md) Describes how to define how many arguments are allowed for a parameter.</span></span>

<span data-ttu-id="83c47-115">[ValidateLength-Attribute-deklaration](./validatelength-attribute-declaration.md) Beskriver hur du definierar längden (i tecken) för ett parameter argument.</span><span class="sxs-lookup"><span data-stu-id="83c47-115">[ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md) Describes how to define the length (in characters) of a parameter argument.</span></span>

<span data-ttu-id="83c47-116">[ValidatePattern-Attribute-deklaration](./validatepattern-attribute-declaration.md) Beskriver hur du definierar giltiga mönster för ett parameter argument.</span><span class="sxs-lookup"><span data-stu-id="83c47-116">[ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md) Describes how to define the valid patterns for a parameter argument.</span></span>

<span data-ttu-id="83c47-117">[ValidateRange-Attribute-deklaration](./validaterange-attribute-declaration.md) Beskriver hur du definierar ett giltigt intervall för ett parameter argument.</span><span class="sxs-lookup"><span data-stu-id="83c47-117">[ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md) Describes how to define the valid range for a parameter argument.</span></span>

<span data-ttu-id="83c47-118">[ValidateSet-Attribute-deklaration](./validateset-attribute-declaration.md) Beskriver hur du definierar möjliga värden för ett parameter argument.</span><span class="sxs-lookup"><span data-stu-id="83c47-118">[ValidateSet Attribute Declaration](./validateset-attribute-declaration.md) Describes how to define the possible values for a parameter argument.</span></span>

## <a name="reference"></a><span data-ttu-id="83c47-119">Referens</span><span class="sxs-lookup"><span data-stu-id="83c47-119">Reference</span></span>

[<span data-ttu-id="83c47-120">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="83c47-120">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
