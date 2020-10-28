---
ms.date: 09/13/2016
ms.topic: reference
title: Attribut i cmdlet-kod
description: Attribut i cmdlet-kod
ms.openlocfilehash: 296bb8bcb06ef660e97dc792d1ecf596cc7c2930
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92653646"
---
# <a name="attributes-in-cmdlet-code"></a><span data-ttu-id="e0618-103">Attribut i cmdlet-kod</span><span class="sxs-lookup"><span data-stu-id="e0618-103">Attributes in Cmdlet Code</span></span>

<span data-ttu-id="e0618-104">För att kunna använda de vanliga funktionerna i Windows PowerShell, dekoreras de klasser och offentliga egenskaper som definierats i cmdlet-koden med attribut.</span><span class="sxs-lookup"><span data-stu-id="e0618-104">To use the common functionality provided by Windows PowerShell, the classes and public properties defined in the cmdlet code are decorated with attributes.</span></span> <span data-ttu-id="e0618-105">Följande klass definition använder exempelvis cmdlet-attributet för att identifiera den Microsoft .NET Ramverks klass där **Get-proc-** cmdleten implementeras.</span><span class="sxs-lookup"><span data-stu-id="e0618-105">For example, the following class definition uses the Cmdlet attribute to identify the Microsoft .NET Framework class in which the **Get-Proc** cmdlet is implemented.</span></span> <span data-ttu-id="e0618-106">(Denna cmdlet används som ett exempel i det här dokumentet och liknar den `Get-Process` cmdlet som tillhandahålls av Windows PowerShell.)</span><span class="sxs-lookup"><span data-stu-id="e0618-106">(This cmdlet is used as an example in this document, and is similar to the `Get-Process` cmdlet provided by Windows PowerShell.)</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

<span data-ttu-id="e0618-107">Attributen betraktas som metadata eftersom deras implementering är separat från implementeringen av cmdlet-koden.</span><span class="sxs-lookup"><span data-stu-id="e0618-107">These attributes are considered metadata because their implementation is separate from the implementation of the cmdlet code.</span></span> <span data-ttu-id="e0618-108">När Windows PowerShell-körningsmiljön kör cmdleten känner den igen attributen och utför sedan lämplig åtgärd för varje attribut.</span><span class="sxs-lookup"><span data-stu-id="e0618-108">When the Windows PowerShell runtime runs the cmdlet, it recognizes the attributes and then performs the appropriate action for each attribute.</span></span>

<span data-ttu-id="e0618-109">Även om du kanske vill implementera din egen version av funktionerna som tillhandahålls av dessa attribut, använder en bra cmdlet-design dessa vanliga funktioner.</span><span class="sxs-lookup"><span data-stu-id="e0618-109">Although you might want to implement your own version of the functionality provided by these attributes, a good cmdlet design uses these common functionalities.</span></span>

<span data-ttu-id="e0618-110">Mer information om de olika attribut som kan deklareras i dina cmdlets finns i [attributtyper](./attribute-types.md).</span><span class="sxs-lookup"><span data-stu-id="e0618-110">For more information about the different attributes that can be declared in your cmdlets, see [Attribute Types](./attribute-types.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e0618-111">Se även</span><span class="sxs-lookup"><span data-stu-id="e0618-111">See Also</span></span>

[<span data-ttu-id="e0618-112">Attributtyper</span><span class="sxs-lookup"><span data-stu-id="e0618-112">Attribute Types</span></span>](./attribute-types.md)

[<span data-ttu-id="e0618-113">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="e0618-113">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
