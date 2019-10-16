---
title: Icke-avslutande fel | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 468dabd6-bfeb-448d-8e09-0996db516edd
caps.latest.revision: 8
ms.openlocfilehash: 5f804756e0e3e867832f15f50967fd6987f160a5
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359271"
---
# <a name="non-terminating-errors"></a><span data-ttu-id="c48ee-102">Fel som inte avbryter körningen</span><span class="sxs-lookup"><span data-stu-id="c48ee-102">Non-Terminating Errors</span></span>

<span data-ttu-id="c48ee-103">I det här avsnittet beskrivs den metod som används för att rapportera icke-avslutande fel.</span><span class="sxs-lookup"><span data-stu-id="c48ee-103">This topic discusses the method used to report non-terminating errors.</span></span> <span data-ttu-id="c48ee-104">Den beskriver också hur du anropar-metoden från cmdleten.</span><span class="sxs-lookup"><span data-stu-id="c48ee-104">It also discusses how to call the method from within the cmdlet.</span></span>

<span data-ttu-id="c48ee-105">När ett icke-avslutande fel inträffar ska cmdleten rapportera felet genom att anropa metoden [system. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) .</span><span class="sxs-lookup"><span data-stu-id="c48ee-105">When a non-terminating error occurs, the cmdlet should report this error by calling the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method.</span></span> <span data-ttu-id="c48ee-106">När cmdleten rapporterar ett icke-avslutande fel, kan cmdleten fortsätta att arbeta med det här inobjektet och på ytterligare inkommande pipelines-objekt.</span><span class="sxs-lookup"><span data-stu-id="c48ee-106">When the cmdlet reports a non-terminating error, the cmdlet can continue to operate on this input object and on further incoming pipeline objects.</span></span> <span data-ttu-id="c48ee-107">Om cmdleten anropar metoden [system. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) , kan cmdleten skriva en felpost som beskriver det villkor som orsakade det icke-avslutande fel meddelandet.</span><span class="sxs-lookup"><span data-stu-id="c48ee-107">If the cmdlet calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method, the cmdlet can write an error record that describes the condition that caused the non-terminating error.</span></span> <span data-ttu-id="c48ee-108">Mer information om fel poster finns i [fel poster för Windows PowerShell](./windows-powershell-error-records.md).</span><span class="sxs-lookup"><span data-stu-id="c48ee-108">For more information about error records, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

<span data-ttu-id="c48ee-109">-Cmdletar kan anropa [system. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) vid behov från sina metoder för bearbetning av indata.</span><span class="sxs-lookup"><span data-stu-id="c48ee-109">Cmdlets can call [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) as necessary from within their input processing methods.</span></span> <span data-ttu-id="c48ee-110">Cmdlets kan dock anropa [system. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) endast från den tråd som anropade [system. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [system. Management. Automation. cmdlet. ProcessRecord ](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)eller data bearbetnings metoden [system. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) .</span><span class="sxs-lookup"><span data-stu-id="c48ee-110">However, cmdlets can call [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) only from the thread that called the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), or [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) input processing method.</span></span> <span data-ttu-id="c48ee-111">Anropa inte [system. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) från en annan tråd.</span><span class="sxs-lookup"><span data-stu-id="c48ee-111">Do not call [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) from another thread.</span></span> <span data-ttu-id="c48ee-112">Kommunicera i stället fel i huvud tråden.</span><span class="sxs-lookup"><span data-stu-id="c48ee-112">Instead, communicate errors back to the main thread.</span></span>

## <a name="see-also"></a><span data-ttu-id="c48ee-113">Se även</span><span class="sxs-lookup"><span data-stu-id="c48ee-113">See Also</span></span>

[<span data-ttu-id="c48ee-114">System. Management. Automation. cmdlet. WriteError</span><span class="sxs-lookup"><span data-stu-id="c48ee-114">System.Management.Automation.Cmdlet.WriteError</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[<span data-ttu-id="c48ee-115">System. Management. Automation. cmdlet. BeginProcessing</span><span class="sxs-lookup"><span data-stu-id="c48ee-115">System.Management.Automation.Cmdlet.BeginProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[<span data-ttu-id="c48ee-116">System. Management. Automation. cmdlet. ProcessRecord</span><span class="sxs-lookup"><span data-stu-id="c48ee-116">System.Management.Automation.Cmdlet.ProcessRecord</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="c48ee-117">System. Management. Automation. cmdlet. EndProcessing</span><span class="sxs-lookup"><span data-stu-id="c48ee-117">System.Management.Automation.Cmdlet.EndProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[<span data-ttu-id="c48ee-118">Windows PowerShell-felposter</span><span class="sxs-lookup"><span data-stu-id="c48ee-118">Windows PowerShell Error Records</span></span>](./windows-powershell-error-records.md)

[<span data-ttu-id="c48ee-119">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="c48ee-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
