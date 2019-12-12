---
title: Rikt linjer för cmdlet-utveckling | Microsoft Docs
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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359436"
---
# <a name="cmdlet-development-guidelines"></a><span data-ttu-id="df5a3-102">Riktlinjer för cmdlet-utveckling</span><span class="sxs-lookup"><span data-stu-id="df5a3-102">Cmdlet Development Guidelines</span></span>

<span data-ttu-id="df5a3-103">Ämnena i det här avsnittet innehåller utvecklings rikt linjer som du kan använda för att skapa välformulerade cmdletar.</span><span class="sxs-lookup"><span data-stu-id="df5a3-103">The topics in this section provide development guidelines that you can use to produce well-formed cmdlets.</span></span> <span data-ttu-id="df5a3-104">Genom att använda de vanliga funktionerna i Windows PowerShell-körningsmiljön och genom att följa dessa rikt linjer kan du utveckla robusta cmdlets med minimal ansträngning och ge användaren en konsekvent upplevelse.</span><span class="sxs-lookup"><span data-stu-id="df5a3-104">By leveraging the common functionality provided by the Windows PowerShell runtime and by following these guidelines, you can develop robust cmdlets with minimal effort and provide the user with a consistent experience.</span></span> <span data-ttu-id="df5a3-105">Dessutom kommer du att minska test belastningen eftersom vanliga funktioner inte kräver omtestering.</span><span class="sxs-lookup"><span data-stu-id="df5a3-105">Additionally, you will reduce the test burden because common functionality does not require retesting.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="df5a3-106">I detta avsnitt</span><span class="sxs-lookup"><span data-stu-id="df5a3-106">In This Section</span></span>

- [<span data-ttu-id="df5a3-107">Nödvändiga utvecklings rikt linjer</span><span class="sxs-lookup"><span data-stu-id="df5a3-107">Required Development Guidelines</span></span>](./required-development-guidelines.md)

- [<span data-ttu-id="df5a3-108">Rekommendationer för starkt uppmuntrande utveckling</span><span class="sxs-lookup"><span data-stu-id="df5a3-108">Strongly Encouraged Development Guidelines</span></span>](./strongly-encouraged-development-guidelines.md)

- [<span data-ttu-id="df5a3-109">Rikt linjer för utveckling av råd</span><span class="sxs-lookup"><span data-stu-id="df5a3-109">Advisory Development Guidelines</span></span>](./advisory-development-guidelines.md)

## <a name="see-also"></a><span data-ttu-id="df5a3-110">Se även</span><span class="sxs-lookup"><span data-stu-id="df5a3-110">See Also</span></span>

[<span data-ttu-id="df5a3-111">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="df5a3-111">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="df5a3-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="df5a3-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
