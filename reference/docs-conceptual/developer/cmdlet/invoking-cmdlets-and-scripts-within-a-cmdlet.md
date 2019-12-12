---
title: Anropar cmdlets och skript inom en cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e7040a5c-4a47-42df-a2ea-96b134a4ed9b
caps.latest.revision: 10
ms.openlocfilehash: f20708ff41d9a6de90090997a875ba5371eccd74
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72355428"
---
# <a name="invoking-cmdlets-and-scripts-within-a-cmdlet"></a><span data-ttu-id="abf85-102">Anropa cmdlets och skript inuti en cmdlet</span><span class="sxs-lookup"><span data-stu-id="abf85-102">Invoking Cmdlets and Scripts Within a Cmdlet</span></span>

<span data-ttu-id="abf85-103">En cmdlet kan anropa andra cmdletar och skript inifrån den ingående bearbetnings metoden för cmdleten.</span><span class="sxs-lookup"><span data-stu-id="abf85-103">A cmdlet can invoke other cmdlets and scripts from within the input processing method of the cmdlet.</span></span> <span data-ttu-id="abf85-104">På så sätt kan du lägga till funktionerna i befintliga cmdlets och skript till din cmdlet utan att behöva skriva om koden.</span><span class="sxs-lookup"><span data-stu-id="abf85-104">This allows you to add the functionality of existing cmdlets and scripts to your cmdlet without having to rewrite the code.</span></span>

## <a name="the-invoke-method"></a><span data-ttu-id="abf85-105">Metoden Invoke</span><span class="sxs-lookup"><span data-stu-id="abf85-105">The Invoke Method</span></span>

<span data-ttu-id="abf85-106">Alla cmdletar kan anropa en befintlig cmdlet genom att anropa metoden [system. Management. Automation. cmdlet. Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) inifrån en bearbetnings metod för indata, till exempel [system. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), som åsidosätts av cmdleten.</span><span class="sxs-lookup"><span data-stu-id="abf85-106">All cmdlets can invoke an existing cmdlet by calling the [System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) method from within an input processing method, such as [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), that is overridden by the cmdlet.</span></span> <span data-ttu-id="abf85-107">Du kan dock bara anropa de cmdlet: ar som härleds direkt från klassen [system. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) .</span><span class="sxs-lookup"><span data-stu-id="abf85-107">However, you can invoke only those cmdlets that derive directly from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class.</span></span> <span data-ttu-id="abf85-108">Det går inte att anropa en cmdlet som härleds från klassen [system. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) .</span><span class="sxs-lookup"><span data-stu-id="abf85-108">You cannot invoke a cmdlet that derives from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) class.</span></span>

<span data-ttu-id="abf85-109">Metoden [system. Management. Automation. cmdlet. Invoke \*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) har följande varianter.</span><span class="sxs-lookup"><span data-stu-id="abf85-109">The [System.Management.Automation.Cmdlet.Invoke\*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) method has the following variants.</span></span>

<span data-ttu-id="abf85-110">[System. Management. Automation. cmdlet. Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) den här varianten anropar cmdlet-objektet och returnerar en mängd "T"-typ objekt.</span><span class="sxs-lookup"><span data-stu-id="abf85-110">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) This variant invokes the cmdlet object and returns a collection of "T" type objects.</span></span>

<span data-ttu-id="abf85-111">[System. Management. Automation. cmdlet. Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) den här varianten anropar cmdlet-objektet och returnerar en starkt skriven emumerator.</span><span class="sxs-lookup"><span data-stu-id="abf85-111">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) This variant invokes the cmdlet object and returns a strongly typed emumerator.</span></span> <span data-ttu-id="abf85-112">Med den här varianten kan användaren använda objekten i samlingen för att utföra anpassade åtgärder.</span><span class="sxs-lookup"><span data-stu-id="abf85-112">This variant allows the user to use the objects in the collection to perform custom operations.</span></span>

## <a name="examples"></a><span data-ttu-id="abf85-113">Exempel</span><span class="sxs-lookup"><span data-stu-id="abf85-113">Examples</span></span>

|<span data-ttu-id="abf85-114">Exempel</span><span class="sxs-lookup"><span data-stu-id="abf85-114">Example</span></span>|<span data-ttu-id="abf85-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="abf85-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="abf85-116">Anropa cmdlets i en cmdlet</span><span class="sxs-lookup"><span data-stu-id="abf85-116">Invoking Cmdlets Within a Cmdlet</span></span>](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md)|<span data-ttu-id="abf85-117">I det här exemplet visas hur du anropar en cmdlet från en annan cmdlet.</span><span class="sxs-lookup"><span data-stu-id="abf85-117">This example shows how to invoke a cmdlet from within another cmdlet.</span></span>|
|[<span data-ttu-id="abf85-118">Anropa skript i en cmdlet</span><span class="sxs-lookup"><span data-stu-id="abf85-118">Invoking Scripts Within a Cmdlet</span></span>](./how-to-invoke-scripts-within-a-cmdlet.md)|<span data-ttu-id="abf85-119">I det här exemplet visas hur du anropar ett skript som har angetts för cmdleten från en annan cmdlet.</span><span class="sxs-lookup"><span data-stu-id="abf85-119">This example shows how to invoke a script that is supplied to the cmdlet from within another cmdlet.</span></span>|

## <a name="see-also"></a><span data-ttu-id="abf85-120">Se även</span><span class="sxs-lookup"><span data-stu-id="abf85-120">See Also</span></span>

[<span data-ttu-id="abf85-121">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="abf85-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
