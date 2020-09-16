---
title: Attribut i cmdlet-kod | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 1f92e329d304754d5596cef0c95dc597aca3a538
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774923"
---
# <a name="attributes-in-cmdlet-code"></a><span data-ttu-id="21283-102">Attribut i cmdlet-kod</span><span class="sxs-lookup"><span data-stu-id="21283-102">Attributes in Cmdlet Code</span></span>

<span data-ttu-id="21283-103">För att kunna använda de vanliga funktionerna i Windows PowerShell, dekoreras de klasser och offentliga egenskaper som definierats i cmdlet-koden med attribut.</span><span class="sxs-lookup"><span data-stu-id="21283-103">To use the common functionality provided by Windows PowerShell, the classes and public properties defined in the cmdlet code are decorated with attributes.</span></span> <span data-ttu-id="21283-104">Följande klass definition använder exempelvis cmdlet-attributet för att identifiera den Microsoft .NET Ramverks klass där **Get-proc-** cmdleten implementeras.</span><span class="sxs-lookup"><span data-stu-id="21283-104">For example, the following class definition uses the Cmdlet attribute to identify the Microsoft .NET Framework class in which the **Get-Proc** cmdlet is implemented.</span></span> <span data-ttu-id="21283-105">(Denna cmdlet används som ett exempel i det här dokumentet och liknar den `Get-Process` cmdlet som tillhandahålls av Windows PowerShell.)</span><span class="sxs-lookup"><span data-stu-id="21283-105">(This cmdlet is used as an example in this document, and is similar to the `Get-Process` cmdlet provided by Windows PowerShell.)</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
public class GetProcCommand : Cmdlet
```

<span data-ttu-id="21283-106">Attributen betraktas som metadata eftersom deras implementering är separat från implementeringen av cmdlet-koden.</span><span class="sxs-lookup"><span data-stu-id="21283-106">These attributes are considered metadata because their implementation is separate from the implementation of the cmdlet code.</span></span> <span data-ttu-id="21283-107">När Windows PowerShell-körningsmiljön kör cmdleten känner den igen attributen och utför sedan lämplig åtgärd för varje attribut.</span><span class="sxs-lookup"><span data-stu-id="21283-107">When the Windows PowerShell runtime runs the cmdlet, it recognizes the attributes and then performs the appropriate action for each attribute.</span></span>

<span data-ttu-id="21283-108">Även om du kanske vill implementera din egen version av funktionerna som tillhandahålls av dessa attribut, använder en bra cmdlet-design dessa vanliga funktioner.</span><span class="sxs-lookup"><span data-stu-id="21283-108">Although you might want to implement your own version of the functionality provided by these attributes, a good cmdlet design uses these common functionalities.</span></span>

<span data-ttu-id="21283-109">Mer information om de olika attribut som kan deklareras i dina cmdlets finns i [attributtyper](./attribute-types.md).</span><span class="sxs-lookup"><span data-stu-id="21283-109">For more information about the different attributes that can be declared in your cmdlets, see [Attribute Types](./attribute-types.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="21283-110">Se även</span><span class="sxs-lookup"><span data-stu-id="21283-110">See Also</span></span>

[<span data-ttu-id="21283-111">Attributtyper</span><span class="sxs-lookup"><span data-stu-id="21283-111">Attribute Types</span></span>](./attribute-types.md)

[<span data-ttu-id="21283-112">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="21283-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
