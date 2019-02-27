---
title: Felrapportering begrepp | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- non-terminating errors [PowerShell SDK]
- errors [PowerShell SDK], described
- terminating errors [PowerShell SDK]
- errors [PowerShell SDK]
ms.assetid: 0dce97c0-bd9a-4691-8ca3-e8d5dea902c5
caps.latest.revision: 11
ms.openlocfilehash: aac6b7b6ac8a0fad15194b6d3f92c434524fabdb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846167"
---
# <a name="error-reporting-concepts"></a><span data-ttu-id="1fe4c-102">Begrepp relaterade till felrapportering</span><span class="sxs-lookup"><span data-stu-id="1fe4c-102">Error Reporting Concepts</span></span>

<span data-ttu-id="1fe4c-103">Windows PowerShell innehåller två mekanismer för rapporterat fel: en mekanism för *avslutande fel* och en annan mekanism för *icke-avslutande fel*.</span><span class="sxs-lookup"><span data-stu-id="1fe4c-103">Windows PowerShell provides two mechanisms for reporting errors: one mechanism for *terminating errors* and another mechanism for *non-terminating errors*.</span></span> <span data-ttu-id="1fe4c-104">Det är viktigt för din cmdlet för att rapportera fel korrekt så att värdprogrammet som kör dina cmdlets kan reagera på lämpligt sätt.</span><span class="sxs-lookup"><span data-stu-id="1fe4c-104">It is important for your cmdlet to report errors correctly so that the host application that is running your cmdlets can react in an appropriate manner.</span></span>

<span data-ttu-id="1fe4c-105">Cmdlet: ska anropa den [System.Management.Automation.Cmdlet.Throwterminatingerror\*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) metoden när ett fel som inte eller bör inte tillåta att cmdleten ska fortsätta att bearbeta dess inkommande objekt.</span><span class="sxs-lookup"><span data-stu-id="1fe4c-105">Your cmdlet should call the [System.Management.Automation.Cmdlet.Throwterminatingerror\*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) method when an error occurs that does not or should not allow the cmdlet to continue to process its input objects.</span></span> <span data-ttu-id="1fe4c-106">Cmdlet: ska anropa den [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) metod för att rapportera icke-avslutande fel när cmdlet: en kan fortsätta att bearbeta inkommande objekt.</span><span class="sxs-lookup"><span data-stu-id="1fe4c-106">Your cmdlet should call the [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method to report non-terminating errors when the cmdlet can continue processing the input objects.</span></span> <span data-ttu-id="1fe4c-107">Båda metoderna ger en Felpost värdprogrammet kan använda för att undersöka orsaken till felet.</span><span class="sxs-lookup"><span data-stu-id="1fe4c-107">Both methods provide an error record that the host application can use to investigate the cause of the error.</span></span>

<span data-ttu-id="1fe4c-108">Använd följande riktlinjer för att fastställa om ett fel är avslutande eller icke-avslutande fel.</span><span class="sxs-lookup"><span data-stu-id="1fe4c-108">Use the following guidelines to determine whether an error is a terminating or non-terminating error.</span></span>

- <span data-ttu-id="1fe4c-109">Ett fel är ett avslutande fel om det förhindrar att cmdlet: fortsätter att bearbeta det aktuella objektet eller bearbetar eventuella ytterligare indata objekt, oavsett deras innehåll.</span><span class="sxs-lookup"><span data-stu-id="1fe4c-109">An error is a terminating error if it prevents your cmdlet from continuing to process the current object or from successfully processing any further input objects, regardless of their content.</span></span>

- <span data-ttu-id="1fe4c-110">Ett fel är ett avslutande fel om du inte vill cmdlet: fortsätta att bearbeta det aktuella objektet eller eventuella ytterligare indata objekt, oavsett deras innehåll.</span><span class="sxs-lookup"><span data-stu-id="1fe4c-110">An error is a terminating error if you do not want your cmdlet to continue processing the current object or any further input objects, regardless of their content.</span></span>

- <span data-ttu-id="1fe4c-111">Ett fel är ett avslutande fel om det inträffar i en cmdlet som inte acceptera eller returneras ett objekt eller om det förekommer i en cmdlet som godkänner eller returnerar endast ett objekt.</span><span class="sxs-lookup"><span data-stu-id="1fe4c-111">An error is a terminating error if it occurs in a cmdlet that does not accept or return an object or if it occurs in a cmdlet that accepts or returns only one object.</span></span>

- <span data-ttu-id="1fe4c-112">Ett fel är ett icke-avslutande fel om cmdlet: vill du fortsätta att bearbeta det aktuella objektet och alla objekt som är ytterligare indata.</span><span class="sxs-lookup"><span data-stu-id="1fe4c-112">An error is a non-terminating error if you want your cmdlet to continue processing the current object and any further input objects.</span></span>

- <span data-ttu-id="1fe4c-113">Ett fel är ett icke-avslutande fel om den är kopplad till en specifik indataobjektet eller en delmängd av indata-objekt.</span><span class="sxs-lookup"><span data-stu-id="1fe4c-113">An error is a non-terminating error if it is related to a specific input object or subset of input objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="1fe4c-114">Se även</span><span class="sxs-lookup"><span data-stu-id="1fe4c-114">See Also</span></span>

[<span data-ttu-id="1fe4c-115">System.Management.Automation.Cmdlet.Throwterminatingerror\*</span><span class="sxs-lookup"><span data-stu-id="1fe4c-115">System.Management.Automation.Cmdlet.Throwterminatingerror\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[<span data-ttu-id="1fe4c-116">System.Management.Automation.Cmdlet.Writeerror\*</span><span class="sxs-lookup"><span data-stu-id="1fe4c-116">System.Management.Automation.Cmdlet.Writeerror\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[<span data-ttu-id="1fe4c-117">Windows PowerShell-felposter</span><span class="sxs-lookup"><span data-stu-id="1fe4c-117">Windows PowerShell Error Records</span></span>](./windows-powershell-error-records.md)

[<span data-ttu-id="1fe4c-118">Skriva en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="1fe4c-118">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
