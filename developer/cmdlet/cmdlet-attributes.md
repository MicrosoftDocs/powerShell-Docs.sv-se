---
title: Cmdlet-attribut | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes [PowerShell SDK]
- attributes [PowerShell SDK], described
ms.assetid: d3f4f652-d929-4c27-9358-9baa390a094c
caps.latest.revision: 14
ms.openlocfilehash: b06faf7204213b383b25685837941ad63dcb225b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845355"
---
# <a name="cmdlet-attributes"></a><span data-ttu-id="0d4aa-102">Cmdlet-attribut</span><span class="sxs-lookup"><span data-stu-id="0d4aa-102">Cmdlet Attributes</span></span>

<span data-ttu-id="0d4aa-103">Windows PowerShell definierar flera attribut som du kan använda för att lägga till vanliga funktioner i dina cmdlets utan att implementera den funktionen i din egen kod.</span><span class="sxs-lookup"><span data-stu-id="0d4aa-103">Windows PowerShell defines several attributes that you can use to add common functionality to your cmdlets without implementing that functionality within your own code.</span></span> <span data-ttu-id="0d4aa-104">Detta inkluderar Cmdlet-attributet som identifierar en Microsoft .NET Framework-klass som OutputType-attributet som anger vilka .NET Framework-typer som returneras av cmdlet: en, parameterattributet som identifierar offentliga egenskaper som cmdlet: en cmdlet-klass parametrar och mycket mer.</span><span class="sxs-lookup"><span data-stu-id="0d4aa-104">This includes the Cmdlet attribute that identifies a Microsoft .NET Framework class as a cmdlet class, the OutputType attribute that specifies the .NET Framework types returned by the cmdlet, the Parameter attribute that identifies public properties as cmdlet parameters, and more.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="0d4aa-105">I detta avsnitt</span><span class="sxs-lookup"><span data-stu-id="0d4aa-105">In This Section</span></span>

<span data-ttu-id="0d4aa-106">[I Cmdlet-koden](./attributes-in-cmdlet-code.md) beskriver fördelarna med att använda attribut i cmdlet-kod.</span><span class="sxs-lookup"><span data-stu-id="0d4aa-106">[Attributes in Cmdlet Code](./attributes-in-cmdlet-code.md) Describes the benefit of using attributes in cmdlet code.</span></span>

<span data-ttu-id="0d4aa-107">[Attributet typer](./attribute-types.md) beskrivs olika attribut som kan anpassa en cmdlet-klass.</span><span class="sxs-lookup"><span data-stu-id="0d4aa-107">[Attribute Types](./attribute-types.md) Describes the different attributes that can decorate a cmdlet class.</span></span>

<span data-ttu-id="0d4aa-108">[Alias attributet deklarationen](./alias-attribute-declaration.md) beskriver hur du definierar alias för en cmdlet-namn för parametern.</span><span class="sxs-lookup"><span data-stu-id="0d4aa-108">[Alias Attribute Declaration](./alias-attribute-declaration.md) Describes how to define aliases for a cmdlet parameter name.</span></span>

<span data-ttu-id="0d4aa-109">[Cmdlet: en deklaration av attribut](./cmdlet-attribute-declaration.md) beskriver hur du definierar en .NET Framework-klass som en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0d4aa-109">[Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md) Describes how to define a .NET Framework class as a cmdlet.</span></span>

<span data-ttu-id="0d4aa-110">[Autentiseringsuppgifter för attributet deklarationen](./credential-attribute-declaration.md) beskriver hur du lägger till stöd för att konvertera strängen mata in en [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) objekt.</span><span class="sxs-lookup"><span data-stu-id="0d4aa-110">[Credential Attribute Declaration](./credential-attribute-declaration.md) Describes how to add support for converting string input into a [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) object.</span></span>

<span data-ttu-id="0d4aa-111">[OutputType-attributet deklarationen](./outputtype-attribute-declaration.md) beskriver hur du anger .NET Framework-typer som returneras av cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="0d4aa-111">[OutputType attribute Declaration](./outputtype-attribute-declaration.md) Describes how to specify the .NET Framework types returned by the cmdlet.</span></span>

<span data-ttu-id="0d4aa-112">[Attributet parameterdeklaration](./parameter-attribute-declaration.md) beskriver hur du definierar parametrar för en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0d4aa-112">[Parameter Attribute Declaration](./parameter-attribute-declaration.md) Describes how to define the parameters of a cmdlet.</span></span>

<span data-ttu-id="0d4aa-113">[ValidateCount attributet deklarationen](./validatecount-attribute-declaration.md) beskriver hur du definierar hur många argument är tillåtna för en parameter.</span><span class="sxs-lookup"><span data-stu-id="0d4aa-113">[ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md) Describes how to define how many arguments are allowed for a parameter.</span></span>

<span data-ttu-id="0d4aa-114">[ValidateLength attributet deklarationen](./validatelength-attribute-declaration.md) beskriver hur du definierar längden (i antal tecken) för en Parameterargumentet.</span><span class="sxs-lookup"><span data-stu-id="0d4aa-114">[ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md) Describes how to define the length (in characters) of a parameter argument.</span></span>

<span data-ttu-id="0d4aa-115">[ValidatePattern attributet deklarationen](./validatepattern-attribute-declaration.md) beskriver hur du definierar de giltiga mönster för ett argument för parametern.</span><span class="sxs-lookup"><span data-stu-id="0d4aa-115">[ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md) Describes how to define the valid patterns for a parameter argument.</span></span>

<span data-ttu-id="0d4aa-116">[ValidateRange attributet deklarationen](./validaterange-attribute-declaration.md) beskriver hur du definierar det giltiga intervallet för ett argument för parametern.</span><span class="sxs-lookup"><span data-stu-id="0d4aa-116">[ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md) Describes how to define the valid range for a parameter argument.</span></span>

<span data-ttu-id="0d4aa-117">[ValidateSet attributet deklarationen](./validateset-attribute-declaration.md) beskriver hur du definierar de möjliga värdena för ett argument för parametern.</span><span class="sxs-lookup"><span data-stu-id="0d4aa-117">[ValidateSet Attribute Declaration](./validateset-attribute-declaration.md) Describes how to define the possible values for a parameter argument.</span></span>

## <a name="reference"></a><span data-ttu-id="0d4aa-118">Referens</span><span class="sxs-lookup"><span data-stu-id="0d4aa-118">Reference</span></span>

[<span data-ttu-id="0d4aa-119">Skriva en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="0d4aa-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
