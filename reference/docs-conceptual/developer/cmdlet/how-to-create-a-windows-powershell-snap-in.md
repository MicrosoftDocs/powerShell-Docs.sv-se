---
title: Så här skapar du en Windows PowerShell-snapin-modul | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- snap-ins [PowerShell SDK], examples
ms.assetid: 71bd9b2c-5f2e-4aa8-b5fe-08c956540d37
caps.latest.revision: 10
ms.openlocfilehash: 43199544dc02ccae4b61053c30d6ed36576adfcf
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355526"
---
# <a name="how-to-create-a-windows-powershell-snap-in"></a><span data-ttu-id="93e70-102">Skapa en Windows PowerShell-snapin-modul</span><span class="sxs-lookup"><span data-stu-id="93e70-102">How to Create a Windows PowerShell Snap-in</span></span>

<span data-ttu-id="93e70-103">En Windows PowerShell-snapin-modul innehåller en mekanism för registrering av uppsättningar av cmdlets och en annan Windows PowerShell-Provider med gränssnittet, vilket utökar funktionerna i gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="93e70-103">A Windows PowerShell snap-in provides a mechanism for registering sets of cmdlets and another Windows PowerShell provider with the shell, thus extending the functionality of the shell.</span></span> <span data-ttu-id="93e70-104">En snapin-modul för Windows PowerShell kan registrera alla cmdlets och providers i en enda sammansättning, eller så kan den registrera en viss lista med cmdlets och providers.</span><span class="sxs-lookup"><span data-stu-id="93e70-104">A Windows PowerShell snap-in can register all the cmdlets and providers in a single assembly, or it can register a specific list of cmdlets and providers.</span></span>

<span data-ttu-id="93e70-105">Snapin-sammansättningar bör installeras i en skyddad katalog, precis som de skulle vara med andra operativ system.</span><span class="sxs-lookup"><span data-stu-id="93e70-105">Snap-in assemblies should be installed in a protected directory, just as they would be with other operating systems.</span></span> <span data-ttu-id="93e70-106">Annars kan obehöriga användare ersätta en sammansättning med osäker kod.</span><span class="sxs-lookup"><span data-stu-id="93e70-106">Otherwise, malicious users can replace an assembly with unsafe code.</span></span>

## <a name="windows-powershell-snap-in-classes"></a><span data-ttu-id="93e70-107">Windows PowerShell snap-in-klasser</span><span class="sxs-lookup"><span data-stu-id="93e70-107">Windows PowerShell Snap-in Classes</span></span>

<span data-ttu-id="93e70-108">Alla Windows PowerShell snap-in-klasser härleds från klassen [system. Management. Automation. PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) eller [system. Management. Automation. Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) .</span><span class="sxs-lookup"><span data-stu-id="93e70-108">All Windows PowerShell snap-in classes derive from the [System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) or [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) classes.</span></span>

## <a name="examples"></a><span data-ttu-id="93e70-109">Exempel</span><span class="sxs-lookup"><span data-stu-id="93e70-109">Examples</span></span>

<span data-ttu-id="93e70-110">[Skriva en Windows PowerShell-snapin-modul](./writing-a-windows-powershell-snap-in.md): det här exemplet visar hur du skapar en snapin-modul som används för att registrera alla cmdlets och providers i en sammansättning.</span><span class="sxs-lookup"><span data-stu-id="93e70-110">[Writing a Windows PowerShell Snap-in](./writing-a-windows-powershell-snap-in.md): This example shows how to create a snap-in that is used to register all the cmdlets and providers in an assembly.</span></span>

<span data-ttu-id="93e70-111">[Skriva en anpassad Windows PowerShell-snapin-modul](./writing-a-custom-windows-powershell-snap-in.md): det här exemplet visar hur du skapar en anpassad snapin-modul som används för att registrera en viss uppsättning cmdlets och providrar som kan vara eller inte finns i en enda sammansättning.</span><span class="sxs-lookup"><span data-stu-id="93e70-111">[Writing a Custom Windows PowerShell Snap-in](./writing-a-custom-windows-powershell-snap-in.md): This example shows how to create a custom snap-in that is used to register a specific set of cmdlets and providers that might or might not exist in a single assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="93e70-112">Se även</span><span class="sxs-lookup"><span data-stu-id="93e70-112">See Also</span></span>

[<span data-ttu-id="93e70-113">System. Management. Automation. PSSnapIn</span><span class="sxs-lookup"><span data-stu-id="93e70-113">System.Management.Automation.PSSnapIn</span></span>](/dotnet/api/System.Management.Automation.PSSnapIn)

[<span data-ttu-id="93e70-114">System. Management. Automation. Custompssnapin</span><span class="sxs-lookup"><span data-stu-id="93e70-114">System.Management.Automation.Custompssnapin</span></span>](/dotnet/api/System.Management.Automation.CustomPSSnapIn)

[<span data-ttu-id="93e70-115">Registrerar cmdletar</span><span class="sxs-lookup"><span data-stu-id="93e70-115">Registering Cmdlets</span></span>](./registering-cmdlets.md)

[<span data-ttu-id="93e70-116">Windows PowerShell Shell SDK</span><span class="sxs-lookup"><span data-stu-id="93e70-116">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
