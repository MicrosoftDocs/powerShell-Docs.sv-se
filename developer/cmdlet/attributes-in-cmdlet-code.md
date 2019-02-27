---
title: I Cmdlet-koden | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aea8d293-c45b-41eb-8385-548f7c9b280b
caps.latest.revision: 10
ms.openlocfilehash: 14505c4f7cc8490418ca463e3b81902f29d4f90b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845264"
---
# <a name="attributes-in-cmdlet-code"></a><span data-ttu-id="34c55-102">Attribut i cmdlet-kod</span><span class="sxs-lookup"><span data-stu-id="34c55-102">Attributes in Cmdlet Code</span></span>

<span data-ttu-id="34c55-103">Om du vill använda de vanliga funktioner som Windows PowerShell dekorerad-klasser och offentliga egenskaperna som definierats i cmdlet-kod med attribut.</span><span class="sxs-lookup"><span data-stu-id="34c55-103">To use the common functionality provided by Windows PowerShell, the classes and public properties defined in the cmdlet code are decorated with attributes.</span></span> <span data-ttu-id="34c55-104">Till exempel följande klassdefinition använder Cmdlet-attribut för att identifiera Microsoft .NET Framework-klassen där den **Get-Proc** cmdlet har implementerats.</span><span class="sxs-lookup"><span data-stu-id="34c55-104">For example, the following class definition uses the Cmdlet attribute to identify the Microsoft .NET Framework class in which the **Get-Proc** cmdlet is implemented.</span></span> <span data-ttu-id="34c55-105">(Den här cmdleten används som exempel i det här dokumentet och liknar den `Get-Process` cmdlet som tillhandahålls av Windows PowerShell.)</span><span class="sxs-lookup"><span data-stu-id="34c55-105">(This cmdlet is used as an example in this document, and is similar to the `Get-Process` cmdlet provided by Windows PowerShell.)</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

<span data-ttu-id="34c55-106">Dessa attribut kallas metadata eftersom deras implementering skiljer sig från implementeringen av cmdlet-kod.</span><span class="sxs-lookup"><span data-stu-id="34c55-106">These attributes are considered metadata because their implementation is separate from the implementation of the cmdlet code.</span></span> <span data-ttu-id="34c55-107">När Windows PowerShell-körningen körs cmdleten identifierar attribut och utför sedan lämplig åtgärd för varje attribut.</span><span class="sxs-lookup"><span data-stu-id="34c55-107">When the Windows PowerShell runtime runs the cmdlet, it recognizes the attributes and then performs the appropriate action for each attribute.</span></span>

<span data-ttu-id="34c55-108">Även om du implementerar en egen version av funktionerna i dessa attribut, använder en bra cmdlet-design dessa vanliga funktioner.</span><span class="sxs-lookup"><span data-stu-id="34c55-108">Although you might want to implement your own version of the functionality provided by these attributes, a good cmdlet design uses these common functionalities.</span></span>

<span data-ttu-id="34c55-109">Mer information om de olika attribut kan deklareras i dina cmdlets finns i [attributtyper](./attribute-types.md).</span><span class="sxs-lookup"><span data-stu-id="34c55-109">For more information about the different attributes that can be declared in your cmdlets, see [Attribute Types](./attribute-types.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="34c55-110">Se även</span><span class="sxs-lookup"><span data-stu-id="34c55-110">See Also</span></span>

[<span data-ttu-id="34c55-111">Attributtyper</span><span class="sxs-lookup"><span data-stu-id="34c55-111">Attribute Types</span></span>](./attribute-types.md)

[<span data-ttu-id="34c55-112">Skriva en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="34c55-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
