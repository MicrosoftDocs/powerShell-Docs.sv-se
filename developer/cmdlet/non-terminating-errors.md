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
ms.openlocfilehash: 9d5c9b16fc5daf3d2f753eeeeedb0db925551a67
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845257"
---
# <a name="non-terminating-errors"></a><span data-ttu-id="6c9e4-102">Fel som inte avbryter körningen</span><span class="sxs-lookup"><span data-stu-id="6c9e4-102">Non-Terminating Errors</span></span>

<span data-ttu-id="6c9e4-103">Det här avsnittet beskrivs den metod som används för att rapportera icke-avslutande fel.</span><span class="sxs-lookup"><span data-stu-id="6c9e4-103">This topic discusses the method used to report non-terminating errors.</span></span> <span data-ttu-id="6c9e4-104">Den behandlar också hur du anropar metoden från cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="6c9e4-104">It also discusses how to call the method from within the cmdlet.</span></span>

<span data-ttu-id="6c9e4-105">När ett icke-avslutande fel inträffar, cmdleten ska rapportera det här felet genom att anropa den [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) metod.</span><span class="sxs-lookup"><span data-stu-id="6c9e4-105">When a non-terminating error occurs, the cmdlet should report this error by calling the [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method.</span></span> <span data-ttu-id="6c9e4-106">När cmdleten visar ett icke-avslutande fel, cmdleten fortsätter att fungera på den här indataobjektet och ytterligare inkommande pipeline-objekt.</span><span class="sxs-lookup"><span data-stu-id="6c9e4-106">When the cmdlet reports a non-terminating error, the cmdlet can continue to operate on this input object and on further incoming pipeline objects.</span></span> <span data-ttu-id="6c9e4-107">Om cmdleten anropar den [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) metoden cmdlet: en kan skriva en Felpost som beskriver den situation som orsakade icke avslutande fel.</span><span class="sxs-lookup"><span data-stu-id="6c9e4-107">If the cmdlet calls the [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method, the cmdlet can write an error record that describes the condition that caused the non-terminating error.</span></span> <span data-ttu-id="6c9e4-108">Mer information om felposter finns i [Windows PowerShell-felposter](./windows-powershell-error-records.md).</span><span class="sxs-lookup"><span data-stu-id="6c9e4-108">For more information about error records, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

<span data-ttu-id="6c9e4-109">Cmdlet: ar kan anropa [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) vid behov från inom sin syn metoderna.</span><span class="sxs-lookup"><span data-stu-id="6c9e4-109">Cmdlets can call [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) as necessary from within their input processing methods.</span></span> <span data-ttu-id="6c9e4-110">Dock cmdlets kan anropa [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) endast från den tråd som kallas den [System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [ System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), eller [System.Management.Automation.Cmdlet.Endprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) indatametod för bearbetning.</span><span class="sxs-lookup"><span data-stu-id="6c9e4-110">However, cmdlets can call [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) only from the thread that called the [System.Management.Automation.Cmdlet.Beginprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), or [System.Management.Automation.Cmdlet.Endprocessing\*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) input processing method.</span></span> <span data-ttu-id="6c9e4-111">Anropa inte [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) från en annan tråd.</span><span class="sxs-lookup"><span data-stu-id="6c9e4-111">Do not call [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) from another thread.</span></span> <span data-ttu-id="6c9e4-112">I stället kommunicera fel tillbaka till huvudtråden.</span><span class="sxs-lookup"><span data-stu-id="6c9e4-112">Instead, communicate errors back to the main thread.</span></span>

## <a name="see-also"></a><span data-ttu-id="6c9e4-113">Se även</span><span class="sxs-lookup"><span data-stu-id="6c9e4-113">See Also</span></span>

[<span data-ttu-id="6c9e4-114">System.Management.Automation.Cmdlet.Writeerror\*</span><span class="sxs-lookup"><span data-stu-id="6c9e4-114">System.Management.Automation.Cmdlet.Writeerror\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[<span data-ttu-id="6c9e4-115">System.Management.Automation.Cmdlet.Beginprocessing\*</span><span class="sxs-lookup"><span data-stu-id="6c9e4-115">System.Management.Automation.Cmdlet.Beginprocessing\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[<span data-ttu-id="6c9e4-116">System.Management.Automation.Cmdlet.Processrecord\*</span><span class="sxs-lookup"><span data-stu-id="6c9e4-116">System.Management.Automation.Cmdlet.Processrecord\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[<span data-ttu-id="6c9e4-117">System.Management.Automation.Cmdlet.Endprocessing\*</span><span class="sxs-lookup"><span data-stu-id="6c9e4-117">System.Management.Automation.Cmdlet.Endprocessing\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[<span data-ttu-id="6c9e4-118">Windows PowerShell-felposter</span><span class="sxs-lookup"><span data-stu-id="6c9e4-118">Windows PowerShell Error Records</span></span>](./windows-powershell-error-records.md)

[<span data-ttu-id="6c9e4-119">Skriva en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="6c9e4-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
