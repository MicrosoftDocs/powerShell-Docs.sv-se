---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: Anropa DSC-resursmetoder direkt
ms.openlocfilehash: cf237f638593706e5959e2bcc0d851b0e55baf0e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685678"
---
# <a name="calling-dsc-resource-methods-directly"></a><span data-ttu-id="7d7c1-103">Anropa DSC-resursmetoder direkt</span><span class="sxs-lookup"><span data-stu-id="7d7c1-103">Calling DSC resource methods directly</span></span>

><span data-ttu-id="7d7c1-104">Gäller för: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="7d7c1-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="7d7c1-105">Du kan använda den [Invoke-DscResource](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource) cmdlet för att direkt anropar funktioner eller metoder för en DSC-resurs (den **Get-TargetResource**, **Set-TargetResource**, och  **Test-TargetResource** funktioner i en MOF-baserad resurs eller **hämta**, **ange**, och **Test** metoder för en MOF-baserade resurs).</span><span class="sxs-lookup"><span data-stu-id="7d7c1-105">You can use the [Invoke-DscResource](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource) cmdlet to directly call the functions or methods of a DSC resource (The **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource** functions of a MOF-based resource, or the **Get**, **Set**, and **Test** methods of a class-based resource).</span></span>
<span data-ttu-id="7d7c1-106">Detta kan användas med tredje part som vill använda DSC-resurser, eller som ett bra verktyg när du utvecklar resurser.</span><span class="sxs-lookup"><span data-stu-id="7d7c1-106">This can be used by third-parties that want to use DSC resources, or as a helpful tool while developing resources.</span></span>

<span data-ttu-id="7d7c1-107">Denna cmdlet används vanligtvis i kombination med en egenskap för metaconfiguration `refreshMode = 'Disabled'`, men du kan använda oavsett vad **refreshMode** är inställd på.</span><span class="sxs-lookup"><span data-stu-id="7d7c1-107">This cmdlet is typically used in combination with a metaconfiguration property `refreshMode = 'Disabled'`, but it can be used no matter what **refreshMode** is set to.</span></span>

<span data-ttu-id="7d7c1-108">När du anropar den **Invoke-DscResource** kan du ange vilken metod eller funktion som ska anropas med hjälp av den **metoden** parametern.</span><span class="sxs-lookup"><span data-stu-id="7d7c1-108">When calling the **Invoke-DscResource** cmdlet, you specify which method or function to call by using the **Method** parameter.</span></span> <span data-ttu-id="7d7c1-109">Du anger egenskaperna för resursen genom att skicka en hash-tabell som värde för den **egenskapen** parametern.</span><span class="sxs-lookup"><span data-stu-id="7d7c1-109">You specify the properties of the resource by passing a hashtable as the value of the **Property** parameter.</span></span>

<span data-ttu-id="7d7c1-110">Här följer några exempel på att anropa-resursmetoder direkt:</span><span class="sxs-lookup"><span data-stu-id="7d7c1-110">The following are examples of directly calling resource methods:</span></span>

## <a name="ensure-a-file-is-present"></a><span data-ttu-id="7d7c1-111">Se till att det finns en fil</span><span class="sxs-lookup"><span data-stu-id="7d7c1-111">Ensure a file is present</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Set -Property @{
                            DestinationPath = "$env:SystemDrive\\DirectAccess.txt";
                            Contents = 'This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="test-that-a-file-is-present"></a><span data-ttu-id="7d7c1-112">Testa att det finns en fil</span><span class="sxs-lookup"><span data-stu-id="7d7c1-112">Test that a file is present</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Test -Property @{
                            DestinationPath="$env:SystemDrive\\DirectAccess.txt";
                            Contents='This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="get-the-contents-of-file"></a><span data-ttu-id="7d7c1-113">Hämta innehållet i filen</span><span class="sxs-lookup"><span data-stu-id="7d7c1-113">Get the contents of file</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Get -Property @{
                            DestinationPath="$env:SystemDrive\\DirectAccess.txt";
                            Contents='This file is create by Invoke-DscResource'} -Verbose
$result.ItemValue | fl
```

><span data-ttu-id="7d7c1-114">**Obs:** Anropa direkt sammansatta resursmetoder stöds inte.</span><span class="sxs-lookup"><span data-stu-id="7d7c1-114">**Note:** Directly calling composite resource methods is not supported.</span></span> <span data-ttu-id="7d7c1-115">I stället anropa de underliggande resurserna som utgör den sammansatta resursen.</span><span class="sxs-lookup"><span data-stu-id="7d7c1-115">Instead, call the methods of the underlying resources that make up the composite resource.</span></span>

## <a name="see-also"></a><span data-ttu-id="7d7c1-116">Se även</span><span class="sxs-lookup"><span data-stu-id="7d7c1-116">See Also</span></span>
- [<span data-ttu-id="7d7c1-117">Skriva en anpassad DSC-resurs med MOF</span><span class="sxs-lookup"><span data-stu-id="7d7c1-117">Writing a custom DSC resource with MOF</span></span>](../resources/authoringResourceMOF.md)
- [<span data-ttu-id="7d7c1-118">Skriva en anpassad DSC-resurs med PowerShell-klasser</span><span class="sxs-lookup"><span data-stu-id="7d7c1-118">Writing a custom DSC resource with PowerShell classes</span></span>](../resources/authoringResourceClass.md)
- [<span data-ttu-id="7d7c1-119">Felsök DSC-resurser</span><span class="sxs-lookup"><span data-stu-id="7d7c1-119">Debugging DSC resources</span></span>](../troubleshooting/debugResource.md)