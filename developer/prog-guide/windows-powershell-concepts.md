---
title: Windows PowerShell-koncept | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3dd5608e-50b6-4c6a-aee3-dde0e86032bc
caps.latest.revision: 7
ms.openlocfilehash: c4b13518ad6452a39ca49e897e1d3e353818d332
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850143"
---
# <a name="windows-powershell-concepts"></a><span data-ttu-id="ff732-102">Begrepp relaterade till Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ff732-102">Windows PowerShell Concepts</span></span>

<span data-ttu-id="ff732-103">Det här avsnittet innehåller begreppsrelaterad information som hjälper dig förstå Windows PowerShell med hänsyn till utvecklare.</span><span class="sxs-lookup"><span data-stu-id="ff732-103">This section contains conceptual information that will help you understand Windows PowerShell from the viewpoint of a developer.</span></span>

|<span data-ttu-id="ff732-104">Ämnesnamn</span><span class="sxs-lookup"><span data-stu-id="ff732-104">Topic Name</span></span>|<span data-ttu-id="ff732-105">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="ff732-105">Description</span></span>|
|----------------|-----------------|
|[<span data-ttu-id="ff732-106">Windows PowerShell-Providers</span><span class="sxs-lookup"><span data-stu-id="ff732-106">Windows PowerShell Providers</span></span>](http://msdn.microsoft.com/en-us/a65c5c75-1131-4ade-90d3-a613dbe620e9)|<span data-ttu-id="ff732-107">En diskussion om Windows PowerShell-providers som används för att komma åt data lagras.</span><span class="sxs-lookup"><span data-stu-id="ff732-107">A discussion about Windows PowerShell providers that are used to access data stores.</span></span>|
|[<span data-ttu-id="ff732-108">Windows PowerShell snapin-moduler</span><span class="sxs-lookup"><span data-stu-id="ff732-108">Windows PowerShell Snap-ins</span></span>](http://msdn.microsoft.com/en-us/20e081a9-522c-48bf-9f21-faaf8cca2e82)|<span data-ttu-id="ff732-109">En mekanism för att registrera cmdlets och providers.</span><span class="sxs-lookup"><span data-stu-id="ff732-109">A mechanism for registering cmdlets and providers.</span></span> <span data-ttu-id="ff732-110">(Se även [skriva en Windows PowerShell-modul](../module/writing-a-windows-powershell-module.md).)</span><span class="sxs-lookup"><span data-stu-id="ff732-110">(See also, [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).)</span></span>|
|[<span data-ttu-id="ff732-111">Windows PowerShell-Runtime</span><span class="sxs-lookup"><span data-stu-id="ff732-111">Windows PowerShell Runtime</span></span>](http://msdn.microsoft.com/en-us/949f06e8-0224-4cd3-bbad-a0cebbb5dec8)|<span data-ttu-id="ff732-112">Den aktuella instansen av Windows PowerShell-körningsutrymmet.</span><span class="sxs-lookup"><span data-stu-id="ff732-112">The current instance of the Windows PowerShell runspace.</span></span>|
|[<span data-ttu-id="ff732-113">Windows PowerShell-Körningsutrymmen</span><span class="sxs-lookup"><span data-stu-id="ff732-113">Windows PowerShell Runspaces</span></span>](http://msdn.microsoft.com/en-us/a1582cfe-f06d-4aff-adc6-71f49a860ce9)|<span data-ttu-id="ff732-114">Av driftmiljöerna där kommandon bearbetas.</span><span class="sxs-lookup"><span data-stu-id="ff732-114">The operating environments where commands are processed.</span></span>|
|[<span data-ttu-id="ff732-115">Windows PowerShell-namnområden</span><span class="sxs-lookup"><span data-stu-id="ff732-115">Windows PowerShell Namespaces</span></span>](http://msdn.microsoft.com/en-us/04bd2841-e90c-47d2-8a1f-3aeb3df35176)|<span data-ttu-id="ff732-116">Översikt över Windows PowerShell-API-namnområdena.</span><span class="sxs-lookup"><span data-stu-id="ff732-116">Overview of Windows PowerShell API namespaces.</span></span>|
|[<span data-ttu-id="ff732-117">Windows PowerShell-hjälpen</span><span class="sxs-lookup"><span data-stu-id="ff732-117">Windows PowerShell Help</span></span>](http://msdn.microsoft.com/en-us/097b7c1c-a056-4b36-9c86-65b2ee702fc7)|<span data-ttu-id="ff732-118">En diskussion om hur du skriver cmdlet hjälp.</span><span class="sxs-lookup"><span data-stu-id="ff732-118">A discussion about writing cmdlet Help.</span></span>|
|[<span data-ttu-id="ff732-119">Uppmanar dig att bekräfta</span><span class="sxs-lookup"><span data-stu-id="ff732-119">Requesting Confirmation</span></span>](../cmdlet/requesting-confirmation-from-cmdlets.md)|<span data-ttu-id="ff732-120">En diskussion om hur cmdlets och providers begäran feedback till användaren innan en åtgärd vidtas.</span><span class="sxs-lookup"><span data-stu-id="ff732-120">A discussion about how cmdlets and providers request feedback from the user before an action is taken.</span></span>|
|[<span data-ttu-id="ff732-121">Koncept för Windows PowerShell-objekt</span><span class="sxs-lookup"><span data-stu-id="ff732-121">Windows PowerShell Object Concepts</span></span>](http://msdn.microsoft.com/en-us/a1449178-b6fd-4ca8-a5e1-d747c2c54181)|<span data-ttu-id="ff732-122">Hur hanterar Windows PowerShell objekt.</span><span class="sxs-lookup"><span data-stu-id="ff732-122">How Windows PowerShell handles objects.</span></span>|
|[<span data-ttu-id="ff732-123">Windows PowerShell utökade typsystemet (ETS)</span><span class="sxs-lookup"><span data-stu-id="ff732-123">Windows PowerShell Extended Type System (ETS)</span></span>](http://msdn.microsoft.com/en-us/12700631-be23-4e6b-9bf0-81ea0d166353)|<span data-ttu-id="ff732-124">Utöka programmässigt objekt.</span><span class="sxs-lookup"><span data-stu-id="ff732-124">Programmatically extending objects.</span></span>|

## <a name="see-also"></a><span data-ttu-id="ff732-125">Se även</span><span class="sxs-lookup"><span data-stu-id="ff732-125">See Also</span></span>

[<span data-ttu-id="ff732-126">Programmeringsguide för Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ff732-126">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)