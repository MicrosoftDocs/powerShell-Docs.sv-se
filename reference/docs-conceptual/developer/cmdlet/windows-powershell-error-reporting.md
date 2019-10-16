---
title: Fel rapportering för Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 61b7773a-c346-4835-a928-7212dc4c85bc
caps.latest.revision: 7
ms.openlocfilehash: 259de341fd2fcce2b0c4629f806b4348cba1ff2c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355414"
---
# <a name="windows-powershell-error-reporting"></a><span data-ttu-id="7d6ef-102">Windows PowerShell-felrapportering</span><span class="sxs-lookup"><span data-stu-id="7d6ef-102">Windows PowerShell Error Reporting</span></span>

<span data-ttu-id="7d6ef-103">Ämnena i det här avsnittet beskriver hur cmdlets rapporterar fel.</span><span class="sxs-lookup"><span data-stu-id="7d6ef-103">The topics in this section discuss how cmdlets report errors.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="7d6ef-104">I detta avsnitt</span><span class="sxs-lookup"><span data-stu-id="7d6ef-104">In This Section</span></span>

<span data-ttu-id="7d6ef-105">[Fel rapporterings begrepp](./error-reporting-concepts.md) Beskriver de två mekanismer som cmdletar kan använda för att rapportera fel.</span><span class="sxs-lookup"><span data-stu-id="7d6ef-105">[Error Reporting Concepts](./error-reporting-concepts.md) Describes the two mechanisms that cmdlets can use to report errors.</span></span>

<span data-ttu-id="7d6ef-106">[Fel avslutas](./terminating-errors.md) Beskriver den metod som används för att rapportera avslutande fel, där den metoden kan anropas från cmdleten och undantag som kan returneras av Windows PowerShell-körningsmiljön när metoden anropas.</span><span class="sxs-lookup"><span data-stu-id="7d6ef-106">[Terminating Errors](./terminating-errors.md) Describes the method used to report terminating errors, where that method can be called from within the cmdlet, and exceptions that can be returned by the Windows PowerShell runtime when the method is called.</span></span>

<span data-ttu-id="7d6ef-107">[Icke-avslutande fel](./non-terminating-errors.md) Beskriver den metod som används för att rapportera icke-avslutande fel och där metoden kan anropas inifrån cmdleten.</span><span class="sxs-lookup"><span data-stu-id="7d6ef-107">[Non-Terminating Errors](./non-terminating-errors.md) Describes the method used to report non-terminating errors and where that method can be called from within the cmdlet.</span></span>

<span data-ttu-id="7d6ef-108">[Visa fel information per kategori](./displaying-error-information.md) Beskriver hur användarna kan visa fel.</span><span class="sxs-lookup"><span data-stu-id="7d6ef-108">[Displaying Error Information by Category](./displaying-error-information.md) Discusses the ways that users can display error.</span></span>

<span data-ttu-id="7d6ef-109">[Windows PowerShell-felposter](./windows-powershell-error-records.md) Beskriver komponenterna i en felpost.</span><span class="sxs-lookup"><span data-stu-id="7d6ef-109">[Windows PowerShell Error Records](./windows-powershell-error-records.md) Describes the components of an error record.</span></span>

<span data-ttu-id="7d6ef-110">[Tolka ErrorRecord-objekt](./interpreting-errorrecord-objects.md) Beskriver hur ErrorRecord-objekt tolkas.</span><span class="sxs-lookup"><span data-stu-id="7d6ef-110">[Interpreting ErrorRecord Objects](./interpreting-errorrecord-objects.md) Discusses how ErrorRecord objects are interpreted.</span></span>

## <a name="see-also"></a><span data-ttu-id="7d6ef-111">Se även</span><span class="sxs-lookup"><span data-stu-id="7d6ef-111">See Also</span></span>

[<span data-ttu-id="7d6ef-112">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="7d6ef-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
