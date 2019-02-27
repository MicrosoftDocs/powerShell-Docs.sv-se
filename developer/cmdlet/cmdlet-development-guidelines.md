---
title: Riktlinjer för utveckling av cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- development guidelines [PowerShell Programmer's Guide]
- cmdlets [PowerShell Programmer's Guide], development guidelines
ms.assetid: c30cc3c0-e958-4a8f-b81f-1e38de772f13
caps.latest.revision: 14
ms.openlocfilehash: 89c7682e87fa6f389349fc44275be0d2ffc83957
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847938"
---
# <a name="cmdlet-development-guidelines"></a><span data-ttu-id="c120a-102">Riktlinjer för cmdlet-utveckling</span><span class="sxs-lookup"><span data-stu-id="c120a-102">Cmdlet Development Guidelines</span></span>

<span data-ttu-id="c120a-103">I det här avsnittet innehåller riktlinjer för utveckling som du kan använda för att skapa rätt cmdlets.</span><span class="sxs-lookup"><span data-stu-id="c120a-103">The topics in this section provide development guidelines that you can use to produce well-formed cmdlets.</span></span> <span data-ttu-id="c120a-104">Du kan utveckla robust cmdlets med minimal ansträngning och ge användaren en konsekvent upplevelse genom att utnyttja den gemensamma funktioner som tillhandahålls av Windows PowerShell-körningen och genom att följa dessa riktlinjer.</span><span class="sxs-lookup"><span data-stu-id="c120a-104">By leveraging the common functionality provided by the Windows PowerShell runtime and by following these guidelines, you can develop robust cmdlets with minimal effort and provide the user with a consistent experience.</span></span> <span data-ttu-id="c120a-105">Dessutom minskas belastningen test eftersom gemensamma funktioner inte kräver testning.</span><span class="sxs-lookup"><span data-stu-id="c120a-105">Additionally, you will reduce the test burden because common functionality does not require retesting.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="c120a-106">I detta avsnitt</span><span class="sxs-lookup"><span data-stu-id="c120a-106">In This Section</span></span>

- [<span data-ttu-id="c120a-107">Riktlinjer för nödvändiga utveckling</span><span class="sxs-lookup"><span data-stu-id="c120a-107">Required Development Guidelines</span></span>](./required-development-guidelines.md)

- [<span data-ttu-id="c120a-108">Vi rekommenderar utveckling riktlinjer</span><span class="sxs-lookup"><span data-stu-id="c120a-108">Strongly Encouraged Development Guidelines</span></span>](./strongly-encouraged-development-guidelines.md)

- [<span data-ttu-id="c120a-109">Riktlinjer för rådgivande utveckling</span><span class="sxs-lookup"><span data-stu-id="c120a-109">Advisory Development Guidelines</span></span>](./advisory-development-guidelines.md)

## <a name="see-also"></a><span data-ttu-id="c120a-110">Se även</span><span class="sxs-lookup"><span data-stu-id="c120a-110">See Also</span></span>

[<span data-ttu-id="c120a-111">Skriva en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c120a-111">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="c120a-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="c120a-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
