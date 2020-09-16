---
ms.date: 08/11/2020
keywords: DSC, PowerShell, konfiguration, installation
title: Anropa DSC-resursmetoder direkt
ms.openlocfilehash: 029a278c938e414820e172b85fac3cb3ad4b4afa
ms.sourcegitcommit: f05f18154913d346012527c23020d48d87ccac74
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/13/2020
ms.locfileid: "88162502"
---
# <a name="calling-dsc-resource-methods-directly"></a><span data-ttu-id="3129a-103">Anropa DSC-resursmetoder direkt</span><span class="sxs-lookup"><span data-stu-id="3129a-103">Calling DSC resource methods directly</span></span>

><span data-ttu-id="3129a-104">Gäller för: Windows PowerShell 5,0</span><span class="sxs-lookup"><span data-stu-id="3129a-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="3129a-105">Du kan använda cmdleten [Invoke-dscresource Keyword Supports](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource) för att direkt anropa funktioner eller metoder för en DSC-resurs ( `Get-TargetResource` , `Set-TargetResource` , och `Test-TargetResource` funktioner i en MOF-baserad resurs, eller metoderna **Get**, **set**och **test** för en klass-baserad resurs).</span><span class="sxs-lookup"><span data-stu-id="3129a-105">You can use the [Invoke-DscResource](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource) cmdlet to directly call the functions or methods of a DSC resource (The `Get-TargetResource`, `Set-TargetResource`, and `Test-TargetResource` functions of a MOF-based resource, or the **Get**, **Set**, and **Test** methods of a class-based resource).</span></span> <span data-ttu-id="3129a-106">Detta kan användas av tredje part som vill använda DSC-resurser eller som ett användbart verktyg när du utvecklar resurser.</span><span class="sxs-lookup"><span data-stu-id="3129a-106">This can be used by third-parties that want to use DSC resources, or as a helpful tool while developing resources.</span></span>

> [!NOTE]
> <span data-ttu-id="3129a-107">I PowerShell 7.0 + `Invoke-DscResource` har inte längre stöd för att anropa WMI DSC-resurser.</span><span class="sxs-lookup"><span data-stu-id="3129a-107">In PowerShell 7.0+, `Invoke-DscResource` no longer supports invoking WMI DSC resources.</span></span> <span data-ttu-id="3129a-108">Detta inkluderar **fil** -och **logg** resurser i **PSDesiredStateConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="3129a-108">This includes the **File** and **Log** resources in **PSDesiredStateConfiguration**.</span></span>

<span data-ttu-id="3129a-109">Denna cmdlet används vanligt vis i kombination med en metaconfiguration `refreshMode = 'Disabled'` -egenskap, men den kan användas oavsett vad **refreshMode** är inställt på.</span><span class="sxs-lookup"><span data-stu-id="3129a-109">This cmdlet is typically used in combination with a metaconfiguration property `refreshMode = 'Disabled'`, but it can be used no matter what **refreshMode** is set to.</span></span>

<span data-ttu-id="3129a-110">När du anropar `Invoke-DscResource` cmdleten anger du vilken metod eller funktion som ska anropas med hjälp av **metod** parametern.</span><span class="sxs-lookup"><span data-stu-id="3129a-110">When calling the `Invoke-DscResource` cmdlet, you specify which method or function to call by using the **Method** parameter.</span></span> <span data-ttu-id="3129a-111">Du anger egenskaperna för resursen genom att skicka en hash-egenskap som värde för **egenskaps** parametern.</span><span class="sxs-lookup"><span data-stu-id="3129a-111">You specify the properties of the resource by passing a hashtable as the value of the **Property** parameter.</span></span>

<span data-ttu-id="3129a-112">Följande är exempel på anrop av resurs metoder direkt:</span><span class="sxs-lookup"><span data-stu-id="3129a-112">The following are examples of directly calling resource methods:</span></span>

## <a name="ensure-a-file-is-present"></a><span data-ttu-id="3129a-113">Se till att det finns en fil</span><span class="sxs-lookup"><span data-stu-id="3129a-113">Ensure a file is present</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Set -Property @{
              DestinationPath = "$env:SystemDrive\\DirectAccess.txt";
              Contents = 'This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="test-that-a-file-is-present"></a><span data-ttu-id="3129a-114">Testa att en fil finns</span><span class="sxs-lookup"><span data-stu-id="3129a-114">Test that a file is present</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Test -Property @{
              DestinationPath="$env:SystemDrive\\DirectAccess.txt";
              Contents='This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="get-the-contents-of-file"></a><span data-ttu-id="3129a-115">Hämta innehållet i filen</span><span class="sxs-lookup"><span data-stu-id="3129a-115">Get the contents of file</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Get -Property @{
              DestinationPath="$env:SystemDrive\\DirectAccess.txt";
              Contents='This file is create by Invoke-DscResource'} -Verbose
$result.ItemValue | fl
```

>[!NOTE]
> <span data-ttu-id="3129a-116">Det finns inte stöd för direkt anrop av sammansatta resurs metoder.</span><span class="sxs-lookup"><span data-stu-id="3129a-116">Directly calling composite resource methods is not supported.</span></span> <span data-ttu-id="3129a-117">Anropa i stället metoderna för de underliggande resurserna som utgör den sammansatta resursen.</span><span class="sxs-lookup"><span data-stu-id="3129a-117">Instead, call the methods of the underlying resources that make up the composite resource.</span></span>

## <a name="see-also"></a><span data-ttu-id="3129a-118">Se även</span><span class="sxs-lookup"><span data-stu-id="3129a-118">See Also</span></span>

- [<span data-ttu-id="3129a-119">Skriva en anpassad DSC-resurs med MOF</span><span class="sxs-lookup"><span data-stu-id="3129a-119">Writing a custom DSC resource with MOF</span></span>](../resources/authoringResourceMOF.md)
- [<span data-ttu-id="3129a-120">Skriva en anpassad DSC-resurs med PowerShell-klasser</span><span class="sxs-lookup"><span data-stu-id="3129a-120">Writing a custom DSC resource with PowerShell classes</span></span>](../resources/authoringResourceClass.md)
- [<span data-ttu-id="3129a-121">Felsök DSC-resurser</span><span class="sxs-lookup"><span data-stu-id="3129a-121">Debugging DSC resources</span></span>](../troubleshooting/debugResource.md)
