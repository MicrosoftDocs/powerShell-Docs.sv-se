---
title: Anropar Cmdlets och skript i en Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e7040a5c-4a47-42df-a2ea-96b134a4ed9b
caps.latest.revision: 10
ms.openlocfilehash: f20708ff41d9a6de90090997a875ba5371eccd74
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058886"
---
# <a name="invoking-cmdlets-and-scripts-within-a-cmdlet"></a><span data-ttu-id="b9462-102">Anropa cmdlets och skript inuti en cmdlet</span><span class="sxs-lookup"><span data-stu-id="b9462-102">Invoking Cmdlets and Scripts Within a Cmdlet</span></span>

<span data-ttu-id="b9462-103">En cmdlet kan anropa andra cmdlet: ar och skript från i indata metoden-cmdlet: ens bearbetades.</span><span class="sxs-lookup"><span data-stu-id="b9462-103">A cmdlet can invoke other cmdlets and scripts from within the input processing method of the cmdlet.</span></span> <span data-ttu-id="b9462-104">På så sätt kan du lägga till funktioner för befintliga cmdlets och skript till din cmdlet utan att behöva skriva om koden.</span><span class="sxs-lookup"><span data-stu-id="b9462-104">This allows you to add the functionality of existing cmdlets and scripts to your cmdlet without having to rewrite the code.</span></span>

## <a name="the-invoke-method"></a><span data-ttu-id="b9462-105">Den anropa metod</span><span class="sxs-lookup"><span data-stu-id="b9462-105">The Invoke Method</span></span>

<span data-ttu-id="b9462-106">Alla cmdletar kan anropa en befintlig cmdlet genom att anropa den [System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) metod inifrån indata som bearbetar metod, till exempel [ System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), det vill säga åsidosätts av cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="b9462-106">All cmdlets can invoke an existing cmdlet by calling the [System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) method from within an input processing method, such as [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), that is overridden by the cmdlet.</span></span> <span data-ttu-id="b9462-107">Men du kan anropa dessa cmdlets som härleds direkt från den [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) klass.</span><span class="sxs-lookup"><span data-stu-id="b9462-107">However, you can invoke only those cmdlets that derive directly from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class.</span></span> <span data-ttu-id="b9462-108">Du kan inte anropa en cmdlet som härleds från den [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) klass.</span><span class="sxs-lookup"><span data-stu-id="b9462-108">You cannot invoke a cmdlet that derives from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) class.</span></span>

<span data-ttu-id="b9462-109">Den [System.Management.Automation.Cmdlet.Invoke\*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) metoden har följande varianter.</span><span class="sxs-lookup"><span data-stu-id="b9462-109">The [System.Management.Automation.Cmdlet.Invoke\*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) method has the following variants.</span></span>

<span data-ttu-id="b9462-110">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) denna variant anropar cmdlet-objektet och returnerar en samling objekt av typen ”T”.</span><span class="sxs-lookup"><span data-stu-id="b9462-110">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) This variant invokes the cmdlet object and returns a collection of "T" type objects.</span></span>

<span data-ttu-id="b9462-111">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) denna variant anropar cmdlet-objektet och returnerar en starkt typifierad emumerator.</span><span class="sxs-lookup"><span data-stu-id="b9462-111">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) This variant invokes the cmdlet object and returns a strongly typed emumerator.</span></span> <span data-ttu-id="b9462-112">Den här variant gör att användaren kan använda objekten i samlingen för att utföra anpassade åtgärder.</span><span class="sxs-lookup"><span data-stu-id="b9462-112">This variant allows the user to use the objects in the collection to perform custom operations.</span></span>

## <a name="examples"></a><span data-ttu-id="b9462-113">Exempel</span><span class="sxs-lookup"><span data-stu-id="b9462-113">Examples</span></span>

|<span data-ttu-id="b9462-114">Exempel</span><span class="sxs-lookup"><span data-stu-id="b9462-114">Example</span></span>|<span data-ttu-id="b9462-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b9462-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b9462-116">Anropar cmdletar i en Cmdlet</span><span class="sxs-lookup"><span data-stu-id="b9462-116">Invoking Cmdlets Within a Cmdlet</span></span>](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md)|<span data-ttu-id="b9462-117">Det här exemplet visar hur du anropar en cmdlet från inom en annan cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b9462-117">This example shows how to invoke a cmdlet from within another cmdlet.</span></span>|
|[<span data-ttu-id="b9462-118">Aktivera skript i en Cmdlet</span><span class="sxs-lookup"><span data-stu-id="b9462-118">Invoking Scripts Within a Cmdlet</span></span>](./how-to-invoke-scripts-within-a-cmdlet.md)|<span data-ttu-id="b9462-119">Det här exemplet visar hur du anropar ett skript som har angetts till cmdleten från en annan cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b9462-119">This example shows how to invoke a script that is supplied to the cmdlet from within another cmdlet.</span></span>|

## <a name="see-also"></a><span data-ttu-id="b9462-120">Se även</span><span class="sxs-lookup"><span data-stu-id="b9462-120">See Also</span></span>

[<span data-ttu-id="b9462-121">Skriva en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="b9462-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
