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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067662"
---
# <a name="non-terminating-errors"></a><span data-ttu-id="fb215-102">Fel som inte avbryter körningen</span><span class="sxs-lookup"><span data-stu-id="fb215-102">Non-Terminating Errors</span></span>

<span data-ttu-id="fb215-103">Det här avsnittet beskrivs den metod som används för att rapportera icke-avslutande fel.</span><span class="sxs-lookup"><span data-stu-id="fb215-103">This topic discusses the method used to report non-terminating errors.</span></span> <span data-ttu-id="fb215-104">Den behandlar också hur du anropar metoden från cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="fb215-104">It also discusses how to call the method from within the cmdlet.</span></span>

<span data-ttu-id="fb215-105">När ett icke-avslutande fel inträffar, cmdleten ska rapportera det här felet genom att anropa den [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) metod.</span><span class="sxs-lookup"><span data-stu-id="fb215-105">When a non-terminating error occurs, the cmdlet should report this error by calling the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method.</span></span> <span data-ttu-id="fb215-106">När cmdleten visar ett icke-avslutande fel, cmdleten fortsätter att fungera på den här indataobjektet och ytterligare inkommande pipeline-objekt.</span><span class="sxs-lookup"><span data-stu-id="fb215-106">When the cmdlet reports a non-terminating error, the cmdlet can continue to operate on this input object and on further incoming pipeline objects.</span></span> <span data-ttu-id="fb215-107">Om cmdleten anropar den [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) metoden cmdlet: en kan skriva en Felpost som beskriver den situation som orsakade icke avslutande fel.</span><span class="sxs-lookup"><span data-stu-id="fb215-107">If the cmdlet calls the [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method, the cmdlet can write an error record that describes the condition that caused the non-terminating error.</span></span> <span data-ttu-id="fb215-108">Mer information om felposter finns i [Windows PowerShell-felposter](./windows-powershell-error-records.md).</span><span class="sxs-lookup"><span data-stu-id="fb215-108">For more information about error records, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

<span data-ttu-id="fb215-109">Cmdlet: ar kan anropa [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) vid behov från inom sin syn metoderna.</span><span class="sxs-lookup"><span data-stu-id="fb215-109">Cmdlets can call [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) as necessary from within their input processing methods.</span></span> <span data-ttu-id="fb215-110">Dock cmdlets kan anropa [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) endast från den tråd som kallas den [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), eller [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) indatametod för bearbetning.</span><span class="sxs-lookup"><span data-stu-id="fb215-110">However, cmdlets can call [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) only from the thread that called the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), or [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) input processing method.</span></span> <span data-ttu-id="fb215-111">Anropa inte [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) från en annan tråd.</span><span class="sxs-lookup"><span data-stu-id="fb215-111">Do not call [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) from another thread.</span></span> <span data-ttu-id="fb215-112">I stället kommunicera fel tillbaka till huvudtråden.</span><span class="sxs-lookup"><span data-stu-id="fb215-112">Instead, communicate errors back to the main thread.</span></span>

## <a name="see-also"></a><span data-ttu-id="fb215-113">Se även</span><span class="sxs-lookup"><span data-stu-id="fb215-113">See Also</span></span>

[<span data-ttu-id="fb215-114">System.Management.Automation.Cmdlet.WriteError</span><span class="sxs-lookup"><span data-stu-id="fb215-114">System.Management.Automation.Cmdlet.WriteError</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[<span data-ttu-id="fb215-115">System.Management.Automation.Cmdlet.BeginProcessing</span><span class="sxs-lookup"><span data-stu-id="fb215-115">System.Management.Automation.Cmdlet.BeginProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[<span data-ttu-id="fb215-116">System.Management.Automation.Cmdlet.ProcessRecord</span><span class="sxs-lookup"><span data-stu-id="fb215-116">System.Management.Automation.Cmdlet.ProcessRecord</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="fb215-117">System.Management.Automation.Cmdlet.EndProcessing</span><span class="sxs-lookup"><span data-stu-id="fb215-117">System.Management.Automation.Cmdlet.EndProcessing</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[<span data-ttu-id="fb215-118">Windows PowerShell-felposter</span><span class="sxs-lookup"><span data-stu-id="fb215-118">Windows PowerShell Error Records</span></span>](./windows-powershell-error-records.md)

[<span data-ttu-id="fb215-119">Skriva en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="fb215-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
