---
title: Windows PowerShell-felrapportering | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 61b7773a-c346-4835-a928-7212dc4c85bc
caps.latest.revision: 7
ms.openlocfilehash: 259de341fd2fcce2b0c4629f806b4348cba1ff2c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067101"
---
# <a name="windows-powershell-error-reporting"></a><span data-ttu-id="7cab4-102">Windows PowerShell-felrapportering</span><span class="sxs-lookup"><span data-stu-id="7cab4-102">Windows PowerShell Error Reporting</span></span>

<span data-ttu-id="7cab4-103">Ämnena i det här avsnittet beskrivs hur cmdletar rapporterar fel.</span><span class="sxs-lookup"><span data-stu-id="7cab4-103">The topics in this section discuss how cmdlets report errors.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="7cab4-104">I detta avsnitt</span><span class="sxs-lookup"><span data-stu-id="7cab4-104">In This Section</span></span>

<span data-ttu-id="7cab4-105">[Fel Reporting begrepp](./error-reporting-concepts.md) beskriver de två mekanismer som cmdlet: ar kan använda för att rapportera fel.</span><span class="sxs-lookup"><span data-stu-id="7cab4-105">[Error Reporting Concepts](./error-reporting-concepts.md) Describes the two mechanisms that cmdlets can use to report errors.</span></span>

<span data-ttu-id="7cab4-106">[Avslutande fel](./terminating-errors.md) beskriver den metod som används för att rapportera avslutande fel, där den metoden kan anropas från cmdlet: en, och undantag som kan returneras av Windows PowerShell-körningen när metoden anropas.</span><span class="sxs-lookup"><span data-stu-id="7cab4-106">[Terminating Errors](./terminating-errors.md) Describes the method used to report terminating errors, where that method can be called from within the cmdlet, and exceptions that can be returned by the Windows PowerShell runtime when the method is called.</span></span>

<span data-ttu-id="7cab4-107">[Icke-avslutande fel](./non-terminating-errors.md) beskriver den metod som används för att rapportera icke-avslutande fel och där den metoden kan anropas från i cmdleten.</span><span class="sxs-lookup"><span data-stu-id="7cab4-107">[Non-Terminating Errors](./non-terminating-errors.md) Describes the method used to report non-terminating errors and where that method can be called from within the cmdlet.</span></span>

<span data-ttu-id="7cab4-108">[Visa Information om fel efter kategori](./displaying-error-information.md) beskrivs de metoder för att användare kan visa fel.</span><span class="sxs-lookup"><span data-stu-id="7cab4-108">[Displaying Error Information by Category](./displaying-error-information.md) Discusses the ways that users can display error.</span></span>

<span data-ttu-id="7cab4-109">[Windows PowerShell-felposter](./windows-powershell-error-records.md) beskriver komponenterna i en Felpost.</span><span class="sxs-lookup"><span data-stu-id="7cab4-109">[Windows PowerShell Error Records](./windows-powershell-error-records.md) Describes the components of an error record.</span></span>

<span data-ttu-id="7cab4-110">[Tolka ErrorRecord objekt](./interpreting-errorrecord-objects.md) diskuterar hur ErrorRecord objekt ska tolkas.</span><span class="sxs-lookup"><span data-stu-id="7cab4-110">[Interpreting ErrorRecord Objects](./interpreting-errorrecord-objects.md) Discusses how ErrorRecord objects are interpreted.</span></span>

## <a name="see-also"></a><span data-ttu-id="7cab4-111">Se även</span><span class="sxs-lookup"><span data-stu-id="7cab4-111">See Also</span></span>

[<span data-ttu-id="7cab4-112">Skriva en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="7cab4-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
