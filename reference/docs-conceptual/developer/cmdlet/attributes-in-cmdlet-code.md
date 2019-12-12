---
title: Attribut i cmdlet-kod | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aea8d293-c45b-41eb-8385-548f7c9b280b
caps.latest.revision: 10
ms.openlocfilehash: 14505c4f7cc8490418ca463e3b81902f29d4f90b
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359464"
---
# <a name="attributes-in-cmdlet-code"></a><span data-ttu-id="77423-102">Attribut i cmdlet-kod</span><span class="sxs-lookup"><span data-stu-id="77423-102">Attributes in Cmdlet Code</span></span>

<span data-ttu-id="77423-103">För att kunna använda de vanliga funktionerna i Windows PowerShell, dekoreras de klasser och offentliga egenskaper som definierats i cmdlet-koden med attribut.</span><span class="sxs-lookup"><span data-stu-id="77423-103">To use the common functionality provided by Windows PowerShell, the classes and public properties defined in the cmdlet code are decorated with attributes.</span></span> <span data-ttu-id="77423-104">Följande klass definition använder exempelvis cmdlet-attributet för att identifiera den Microsoft .NET Ramverks klass där **Get-proc-** cmdleten implementeras.</span><span class="sxs-lookup"><span data-stu-id="77423-104">For example, the following class definition uses the Cmdlet attribute to identify the Microsoft .NET Framework class in which the **Get-Proc** cmdlet is implemented.</span></span> <span data-ttu-id="77423-105">(Denna cmdlet används som ett exempel i det här dokumentet och liknar `Get-Process`-cmdleten som tillhandahålls av Windows PowerShell.)</span><span class="sxs-lookup"><span data-stu-id="77423-105">(This cmdlet is used as an example in this document, and is similar to the `Get-Process` cmdlet provided by Windows PowerShell.)</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

<span data-ttu-id="77423-106">Attributen betraktas som metadata eftersom deras implementering är separat från implementeringen av cmdlet-koden.</span><span class="sxs-lookup"><span data-stu-id="77423-106">These attributes are considered metadata because their implementation is separate from the implementation of the cmdlet code.</span></span> <span data-ttu-id="77423-107">När Windows PowerShell-körningsmiljön kör cmdleten känner den igen attributen och utför sedan lämplig åtgärd för varje attribut.</span><span class="sxs-lookup"><span data-stu-id="77423-107">When the Windows PowerShell runtime runs the cmdlet, it recognizes the attributes and then performs the appropriate action for each attribute.</span></span>

<span data-ttu-id="77423-108">Även om du kanske vill implementera din egen version av funktionerna som tillhandahålls av dessa attribut, använder en bra cmdlet-design dessa vanliga funktioner.</span><span class="sxs-lookup"><span data-stu-id="77423-108">Although you might want to implement your own version of the functionality provided by these attributes, a good cmdlet design uses these common functionalities.</span></span>

<span data-ttu-id="77423-109">Mer information om de olika attribut som kan deklareras i dina cmdlets finns i [attributtyper](./attribute-types.md).</span><span class="sxs-lookup"><span data-stu-id="77423-109">For more information about the different attributes that can be declared in your cmdlets, see [Attribute Types](./attribute-types.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="77423-110">Se även</span><span class="sxs-lookup"><span data-stu-id="77423-110">See Also</span></span>

[<span data-ttu-id="77423-111">Attributtyper</span><span class="sxs-lookup"><span data-stu-id="77423-111">Attribute Types</span></span>](./attribute-types.md)

[<span data-ttu-id="77423-112">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="77423-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
