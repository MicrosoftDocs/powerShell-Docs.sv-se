---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: "Anropar metoder för DSC-resursen direkt"
ms.openlocfilehash: 3e83984fbf31dfcfec76fa15cdd9b83d92501aa0
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/17/2018
---
# <a name="calling-dsc-resource-methods-directly"></a><span data-ttu-id="0841e-103">Anropar metoder för DSC-resursen direkt</span><span class="sxs-lookup"><span data-stu-id="0841e-103">Calling DSC resource methods directly</span></span>

><span data-ttu-id="0841e-104">Gäller för: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="0841e-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="0841e-105">Du kan använda den [Invoke-DscResource](https://technet.microsoft.com/en-us/library/mt517869.aspx) för att anropa direkt funktioner eller metoder för en DSC-resurs (den **Get-TargetResource**, **Set TargetResource**, och  **Test-TargetResource** funktioner för en MOF-baserade resurs eller **hämta**, **ange**, och **Test** metoder för en klass-baserade resurs).</span><span class="sxs-lookup"><span data-stu-id="0841e-105">You can use the [Invoke-DscResource](https://technet.microsoft.com/en-us/library/mt517869.aspx) cmdlet to directly call the functions or methods of a DSC resource (The **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource** functions of a MOF-based resource, or the **Get**, **Set**, and **Test** methods of a class-based resource).</span></span> <span data-ttu-id="0841e-106">Detta kan användas med tredje part som vill använda DSC-resurser, eller som ett bra verktyg när du arbetar med resurser.</span><span class="sxs-lookup"><span data-stu-id="0841e-106">This can be used by third-parties that want to use DSC resources, or as a helpful tool while developing resources.</span></span> 

<span data-ttu-id="0841e-107">Den här cmdleten används vanligtvis i kombination med en egenskap för metakonfigurationen `refreshMode = 'Disabled'`, men du kan använda oavsett vad **refreshMode** är inställd på.</span><span class="sxs-lookup"><span data-stu-id="0841e-107">This cmdlet is typically used in combination with a metaconfiguration property `refreshMode = 'Disabled'`, but it can be used no matter what **refreshMode** is set to.</span></span>

<span data-ttu-id="0841e-108">När du anropar den **Invoke-DscResource** kan du ange vilken metod eller en funktion som ska anropas med hjälp av den **metoden** parameter.</span><span class="sxs-lookup"><span data-stu-id="0841e-108">When calling the **Invoke-DscResource** cmdlet, you specify which method or function to call by using the **Method** parameter.</span></span> <span data-ttu-id="0841e-109">Du kan ange egenskaper för resursen genom att skicka en hash-tabell som värde för den **egenskapen** parameter.</span><span class="sxs-lookup"><span data-stu-id="0841e-109">You specify the properties of the resource by passing a hashtable as the value of the **Property** parameter.</span></span>

<span data-ttu-id="0841e-110">Följande är exempel på direkt anropar resurs metoder:</span><span class="sxs-lookup"><span data-stu-id="0841e-110">The following are examples of directly calling resource methods:</span></span>

## <a name="ensure-a-file-is-present"></a><span data-ttu-id="0841e-111">Se till att det finns en fil</span><span class="sxs-lookup"><span data-stu-id="0841e-111">Ensure a file is present</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Set -Property @{
                            DestinationPath = "$env:SystemDrive\\DirectAccess.txt";
                            Contents = 'This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="test-that-a-file-is-present"></a><span data-ttu-id="0841e-112">Testa att det finns en fil</span><span class="sxs-lookup"><span data-stu-id="0841e-112">Test that a file is present</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Test -Property @{
                            DestinationPath="$env:SystemDrive\\DirectAccess.txt";
                            Contents='This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## <a name="get-the-contents-of-file"></a><span data-ttu-id="0841e-113">Hämta innehållet i filen</span><span class="sxs-lookup"><span data-stu-id="0841e-113">Get the contents of file</span></span>

```powershell
$result = Invoke-DscResource -Name File -Method Get -Property @{
                            DestinationPath="$env:SystemDrive\\DirectAccess.txt";
                            Contents='This file is create by Invoke-DscResource'} -Verbose
$result.ItemValue | fl
```

><span data-ttu-id="0841e-114">**Obs:** direkt anropar sammansatta resurs metoder inte stöds.</span><span class="sxs-lookup"><span data-stu-id="0841e-114">**Note:** Directly calling composite resource methods is not supported.</span></span> <span data-ttu-id="0841e-115">I stället anropa de underliggande resurserna som utgör sammansatta resursen.</span><span class="sxs-lookup"><span data-stu-id="0841e-115">Instead, call the methods of the underlying resources that make up the composite resource.</span></span>

## <a name="see-also"></a><span data-ttu-id="0841e-116">Se även</span><span class="sxs-lookup"><span data-stu-id="0841e-116">See Also</span></span>
- [<span data-ttu-id="0841e-117">Skriva en anpassad DSC-resurs med MOF</span><span class="sxs-lookup"><span data-stu-id="0841e-117">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md) 
- [<span data-ttu-id="0841e-118">Skriva en anpassad DSC-resurs med PowerShell-klasser</span><span class="sxs-lookup"><span data-stu-id="0841e-118">Writing a custom DSC resource with PowerShell classes</span></span>](authoringResourceClass.md)
- [<span data-ttu-id="0841e-119">Felsök DSC-resurser</span><span class="sxs-lookup"><span data-stu-id="0841e-119">Debugging DSC resources</span></span>](debugResource.md)

