---
ms.date: 08/11/2020
keywords: DSC, PowerShell, konfiguration, installation
title: Anropa DSC-resursmetoder direkt
description: Invoke-DscResource cmdlet kan användas för att anropa funktioner eller metoder för en DSC-resurs. Detta kan användas av tredje part som vill använda DSC-resurser eller som ett användbart verktyg när du utvecklar resurser.
ms.openlocfilehash: 5ccf0f589b60cef4ec197d1e0a583af9ed60d5e7
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92651005"
---
# <a name="calling-dsc-resource-methods-directly"></a><span data-ttu-id="8a996-105">Anropa DSC-resursmetoder direkt</span><span class="sxs-lookup"><span data-stu-id="8a996-105">Calling DSC resource methods directly</span></span>

> <span data-ttu-id="8a996-106">Gäller för: Windows PowerShell 5,0</span><span class="sxs-lookup"><span data-stu-id="8a996-106">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="8a996-107">Du kan använda cmdleten [Invoke-dscresource Keyword Supports](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource) för att direkt anropa funktioner eller metoder för en DSC-resurs ( `Get-TargetResource` , `Set-TargetResource` , och `Test-TargetResource` funktioner i en MOF-baserad resurs, eller metoderna **Get** , **set** och **test** för en klass-baserad resurs).</span><span class="sxs-lookup"><span data-stu-id="8a996-107">You can use the [Invoke-DscResource](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource) cmdlet to directly call the functions or methods of a DSC resource (The `Get-TargetResource`, `Set-TargetResource`, and `Test-TargetResource` functions of a MOF-based resource, or the **Get** , **Set** , and **Test** methods of a class-based resource).</span></span> <span data-ttu-id="8a996-108">Detta kan användas av tredje part som vill använda DSC-resurser eller som ett användbart verktyg när du utvecklar resurser.</span><span class="sxs-lookup"><span data-stu-id="8a996-108">This can be used by third-parties that want to use DSC resources, or as a helpful tool while developing resources.</span></span>

> [!NOTE]
> <span data-ttu-id="8a996-109">I PowerShell 7.0 + `Invoke-DscResource` har inte längre stöd för att anropa WMI DSC-resurser.</span><span class="sxs-lookup"><span data-stu-id="8a996-109">In PowerShell 7.0+, `Invoke-DscResource` no longer supports invoking WMI DSC resources.</span></span> <span data-ttu-id="8a996-110">Detta inkluderar **fil** -och **logg** resurser i **PSDesiredStateConfiguration** .</span><span class="sxs-lookup"><span data-stu-id="8a996-110">This includes the **File** and **Log** resources in **PSDesiredStateConfiguration** .</span></span>

<span data-ttu-id="8a996-111">Denna cmdlet används vanligt vis i kombination med en metaconfiguration `refreshMode = 'Disabled'` -egenskap, men den kan användas oavsett vad **refreshMode** är inställt på.</span><span class="sxs-lookup"><span data-stu-id="8a996-111">This cmdlet is typically used in combination with a metaconfiguration property `refreshMode = 'Disabled'`, but it can be used no matter what **refreshMode** is set to.</span></span>

<span data-ttu-id="8a996-112">När du anropar `Invoke-DscResource` cmdleten anger du vilken metod eller funktion som ska anropas med hjälp av **metod** parametern.</span><span class="sxs-lookup"><span data-stu-id="8a996-112">When calling the `Invoke-DscResource` cmdlet, you specify which method or function to call by using the **Method** parameter.</span></span> <span data-ttu-id="8a996-113">Du anger egenskaperna för resursen genom att skicka en hash-egenskap som värde för **egenskaps** parametern.</span><span class="sxs-lookup"><span data-stu-id="8a996-113">You specify the properties of the resource by passing a hashtable as the value of the **Property** parameter.</span></span>

<span data-ttu-id="8a996-114">Följande är exempel på anrop av resurs metoder direkt:</span><span class="sxs-lookup"><span data-stu-id="8a996-114">The following are examples of directly calling resource methods:</span></span>

## <a name="ensure-a-file-is-present"></a><span data-ttu-id="8a996-115">Se till att det finns en fil</span><span class="sxs-lookup"><span data-stu-id="8a996-115">Ensure a file is present</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Set -Property @{
              DestinationPath = "$env:SystemDrive\\DirectAccess.txt";
              Contents = 'This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="test-that-a-file-is-present"></a><span data-ttu-id="8a996-116">Testa att en fil finns</span><span class="sxs-lookup"><span data-stu-id="8a996-116">Test that a file is present</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Test -Property @{
              DestinationPath="$env:SystemDrive\\DirectAccess.txt";
              Contents='This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="get-the-contents-of-file"></a><span data-ttu-id="8a996-117">Hämta innehållet i filen</span><span class="sxs-lookup"><span data-stu-id="8a996-117">Get the contents of file</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Get -Property @{
              DestinationPath="$env:SystemDrive\\DirectAccess.txt";
              Contents='This file is create by Invoke-DscResource'} -Verbose
$result.ItemValue | fl
```

> [!NOTE]
> <span data-ttu-id="8a996-118">Det finns inte stöd för direkt anrop av sammansatta resurs metoder.</span><span class="sxs-lookup"><span data-stu-id="8a996-118">Directly calling composite resource methods is not supported.</span></span> <span data-ttu-id="8a996-119">Anropa i stället metoderna för de underliggande resurserna som utgör den sammansatta resursen.</span><span class="sxs-lookup"><span data-stu-id="8a996-119">Instead, call the methods of the underlying resources that make up the composite resource.</span></span>

## <a name="see-also"></a><span data-ttu-id="8a996-120">Se även</span><span class="sxs-lookup"><span data-stu-id="8a996-120">See Also</span></span>

- [<span data-ttu-id="8a996-121">Skriva en anpassad DSC-resurs med MOF</span><span class="sxs-lookup"><span data-stu-id="8a996-121">Writing a custom DSC resource with MOF</span></span>](../resources/authoringResourceMOF.md)
- [<span data-ttu-id="8a996-122">Skriva en anpassad DSC-resurs med PowerShell-klasser</span><span class="sxs-lookup"><span data-stu-id="8a996-122">Writing a custom DSC resource with PowerShell classes</span></span>](../resources/authoringResourceClass.md)
- [<span data-ttu-id="8a996-123">Felsök DSC-resurser</span><span class="sxs-lookup"><span data-stu-id="8a996-123">Debugging DSC resources</span></span>](../troubleshooting/debugResource.md)
