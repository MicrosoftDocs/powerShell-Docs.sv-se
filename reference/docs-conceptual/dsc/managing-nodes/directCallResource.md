---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: Anropa DSC-resursmetoder direkt
ms.openlocfilehash: cf237f638593706e5959e2bcc0d851b0e55baf0e
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71942253"
---
# <a name="calling-dsc-resource-methods-directly"></a><span data-ttu-id="8f667-103">Anropa DSC-resursmetoder direkt</span><span class="sxs-lookup"><span data-stu-id="8f667-103">Calling DSC resource methods directly</span></span>

><span data-ttu-id="8f667-104">Gäller för: Windows PowerShell 5,0</span><span class="sxs-lookup"><span data-stu-id="8f667-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="8f667-105">Du kan använda cmdleten [Invoke-dscresource Keyword Supports](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource) för att direkt anropa funktioner eller metoder för en DSC-resurs (funktionen **Get-TargetResource**, **set-TargetResource**och **test-TargetResource** i en MOF-baserad resurs, eller **Get**-, **set**-och **test** metoder för en klass-baserad resurs).</span><span class="sxs-lookup"><span data-stu-id="8f667-105">You can use the [Invoke-DscResource](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource) cmdlet to directly call the functions or methods of a DSC resource (The **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource** functions of a MOF-based resource, or the **Get**, **Set**, and **Test** methods of a class-based resource).</span></span>
<span data-ttu-id="8f667-106">Detta kan användas av tredje part som vill använda DSC-resurser eller som ett användbart verktyg när du utvecklar resurser.</span><span class="sxs-lookup"><span data-stu-id="8f667-106">This can be used by third-parties that want to use DSC resources, or as a helpful tool while developing resources.</span></span>

<span data-ttu-id="8f667-107">Denna cmdlet används vanligt vis i kombination med en metaconfiguration-egenskap `refreshMode = 'Disabled'`, men den kan användas oavsett vad **refreshMode** har angetts till.</span><span class="sxs-lookup"><span data-stu-id="8f667-107">This cmdlet is typically used in combination with a metaconfiguration property `refreshMode = 'Disabled'`, but it can be used no matter what **refreshMode** is set to.</span></span>

<span data-ttu-id="8f667-108">När du anropar cmdleten **Invoke-dscresource Keyword Supports** anger du vilken metod eller funktion som ska anropas med hjälp av **metod** parametern.</span><span class="sxs-lookup"><span data-stu-id="8f667-108">When calling the **Invoke-DscResource** cmdlet, you specify which method or function to call by using the **Method** parameter.</span></span> <span data-ttu-id="8f667-109">Du anger egenskaperna för resursen genom att skicka en hash-egenskap som värde för **egenskaps** parametern.</span><span class="sxs-lookup"><span data-stu-id="8f667-109">You specify the properties of the resource by passing a hashtable as the value of the **Property** parameter.</span></span>

<span data-ttu-id="8f667-110">Följande är exempel på anrop av resurs metoder direkt:</span><span class="sxs-lookup"><span data-stu-id="8f667-110">The following are examples of directly calling resource methods:</span></span>

## <a name="ensure-a-file-is-present"></a><span data-ttu-id="8f667-111">Se till att det finns en fil</span><span class="sxs-lookup"><span data-stu-id="8f667-111">Ensure a file is present</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Set -Property @{
                            DestinationPath = "$env:SystemDrive\\DirectAccess.txt";
                            Contents = 'This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="test-that-a-file-is-present"></a><span data-ttu-id="8f667-112">Testa att en fil finns</span><span class="sxs-lookup"><span data-stu-id="8f667-112">Test that a file is present</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Test -Property @{
                            DestinationPath="$env:SystemDrive\\DirectAccess.txt";
                            Contents='This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="get-the-contents-of-file"></a><span data-ttu-id="8f667-113">Hämta innehållet i filen</span><span class="sxs-lookup"><span data-stu-id="8f667-113">Get the contents of file</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Get -Property @{
                            DestinationPath="$env:SystemDrive\\DirectAccess.txt";
                            Contents='This file is create by Invoke-DscResource'} -Verbose
$result.ItemValue | fl
```

><span data-ttu-id="8f667-114">**Obs:** Det finns inte stöd för direkt anrop av sammansatta resurs metoder.</span><span class="sxs-lookup"><span data-stu-id="8f667-114">**Note:** Directly calling composite resource methods is not supported.</span></span> <span data-ttu-id="8f667-115">Anropa i stället metoderna för de underliggande resurserna som utgör den sammansatta resursen.</span><span class="sxs-lookup"><span data-stu-id="8f667-115">Instead, call the methods of the underlying resources that make up the composite resource.</span></span>

## <a name="see-also"></a><span data-ttu-id="8f667-116">Se även</span><span class="sxs-lookup"><span data-stu-id="8f667-116">See Also</span></span>
- [<span data-ttu-id="8f667-117">Skriva en anpassad DSC-resurs med MOF</span><span class="sxs-lookup"><span data-stu-id="8f667-117">Writing a custom DSC resource with MOF</span></span>](../resources/authoringResourceMOF.md)
- [<span data-ttu-id="8f667-118">Skriva en anpassad DSC-resurs med PowerShell-klasser</span><span class="sxs-lookup"><span data-stu-id="8f667-118">Writing a custom DSC resource with PowerShell classes</span></span>](../resources/authoringResourceClass.md)
- [<span data-ttu-id="8f667-119">Felsök DSC-resurser</span><span class="sxs-lookup"><span data-stu-id="8f667-119">Debugging DSC resources</span></span>](../troubleshooting/debugResource.md)