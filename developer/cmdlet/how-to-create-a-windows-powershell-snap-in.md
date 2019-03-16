---
title: Så här skapar du en Windows PowerShell snapin-modulen | Microsoft Docs
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
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055945"
---
# <a name="how-to-create-a-windows-powershell-snap-in"></a><span data-ttu-id="809ca-102">Skapa en Windows PowerShell-snapin-modul</span><span class="sxs-lookup"><span data-stu-id="809ca-102">How to Create a Windows PowerShell Snap-in</span></span>

<span data-ttu-id="809ca-103">Är en mekanism för att registrera uppsättningar med cmdlets och en annan Windows PowerShell-providern med shell, vilket utökar funktionaliteten i gränssnittet för en Windows PowerShell-snapin-modul.</span><span class="sxs-lookup"><span data-stu-id="809ca-103">A Windows PowerShell snap-in provides a mechanism for registering sets of cmdlets and another Windows PowerShell provider with the shell, thus extending the functionality of the shell.</span></span> <span data-ttu-id="809ca-104">En Windows PowerShell-snapin-modul kan registrera alla cmdletar och providers i en enda sammansättning, eller den kan registrera en viss lista med cmdlets och providers.</span><span class="sxs-lookup"><span data-stu-id="809ca-104">A Windows PowerShell snap-in can register all the cmdlets and providers in a single assembly, or it can register a specific list of cmdlets and providers.</span></span>

<span data-ttu-id="809ca-105">Snapin-modulen sammansättningar ska installeras i en skyddad katalog, precis som de skulle vara med andra operativsystem.</span><span class="sxs-lookup"><span data-stu-id="809ca-105">Snap-in assemblies should be installed in a protected directory, just as they would be with other operating systems.</span></span> <span data-ttu-id="809ca-106">I annat fall kan angripare ersätta en sammansättning med osäkra kod.</span><span class="sxs-lookup"><span data-stu-id="809ca-106">Otherwise, malicious users can replace an assembly with unsafe code.</span></span>

## <a name="windows-powershell-snap-in-classes"></a><span data-ttu-id="809ca-107">Windows-snapin-modulen för PowerShell-klasser</span><span class="sxs-lookup"><span data-stu-id="809ca-107">Windows PowerShell Snap-in Classes</span></span>

<span data-ttu-id="809ca-108">Alla Windows PowerShell snapin-modulen klasser som härleds från den [System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) eller [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) klasser.</span><span class="sxs-lookup"><span data-stu-id="809ca-108">All Windows PowerShell snap-in classes derive from the [System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) or [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) classes.</span></span>

## <a name="examples"></a><span data-ttu-id="809ca-109">Exempel</span><span class="sxs-lookup"><span data-stu-id="809ca-109">Examples</span></span>

<span data-ttu-id="809ca-110">[Skriva ett Windows PowerShell snapin-modulen](./writing-a-windows-powershell-snap-in.md): Det här exemplet visar hur du skapar en snapin-modul som används för att registrera alla cmdletar och providers i en sammansättning.</span><span class="sxs-lookup"><span data-stu-id="809ca-110">[Writing a Windows PowerShell Snap-in](./writing-a-windows-powershell-snap-in.md): This example shows how to create a snap-in that is used to register all the cmdlets and providers in an assembly.</span></span>

<span data-ttu-id="809ca-111">[Skriva en anpassad Windows PowerShell snapin-modul](./writing-a-custom-windows-powershell-snap-in.md): Det här exemplet visar hur du skapar en anpassad snapin-modul som används för att registrera en specifik uppsättning cmdlets och providers som kanske eller kanske inte finns i en enda sammansättning.</span><span class="sxs-lookup"><span data-stu-id="809ca-111">[Writing a Custom Windows PowerShell Snap-in](./writing-a-custom-windows-powershell-snap-in.md): This example shows how to create a custom snap-in that is used to register a specific set of cmdlets and providers that might or might not exist in a single assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="809ca-112">Se även</span><span class="sxs-lookup"><span data-stu-id="809ca-112">See Also</span></span>

[<span data-ttu-id="809ca-113">System.Management.Automation.PSSnapIn</span><span class="sxs-lookup"><span data-stu-id="809ca-113">System.Management.Automation.PSSnapIn</span></span>](/dotnet/api/System.Management.Automation.PSSnapIn)

[<span data-ttu-id="809ca-114">System.Management.Automation.Custompssnapin</span><span class="sxs-lookup"><span data-stu-id="809ca-114">System.Management.Automation.Custompssnapin</span></span>](/dotnet/api/System.Management.Automation.CustomPSSnapIn)

[<span data-ttu-id="809ca-115">Registrera cmdlet: ar</span><span class="sxs-lookup"><span data-stu-id="809ca-115">Registering Cmdlets</span></span>](./registering-cmdlets.md)

[<span data-ttu-id="809ca-116">Windows PowerShell Shell SDK</span><span class="sxs-lookup"><span data-stu-id="809ca-116">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
