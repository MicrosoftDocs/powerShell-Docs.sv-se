---
title: Ändra installations Sök vägen för PSModulePath | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dc5ce5a2-50e9-4c88-abf1-ac148a8a6b7b
caps.latest.revision: 15
ms.openlocfilehash: 639d3a28dd2af09fcc498caedc5fe74c1493445d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72352887"
---
# <a name="modifying-the-psmodulepath-installation-path"></a><span data-ttu-id="fe9f5-102">Ändra installationssökvägen för PSModulePath</span><span class="sxs-lookup"><span data-stu-id="fe9f5-102">Modifying the PSModulePath Installation Path</span></span>

<span data-ttu-id="fe9f5-103">Miljövariabeln `PSModulePath` lagrar Sök vägarna till platserna för de moduler som är installerade på disk.</span><span class="sxs-lookup"><span data-stu-id="fe9f5-103">The `PSModulePath` environment variable stores the paths to the locations of the modules that are installed on disk.</span></span> <span data-ttu-id="fe9f5-104">Windows PowerShell använder den här variabeln för att hitta moduler när användaren inte anger den fullständiga sökvägen till en modul.</span><span class="sxs-lookup"><span data-stu-id="fe9f5-104">Windows PowerShell uses this variable to locate modules when the user does not specify the full path to a module.</span></span> <span data-ttu-id="fe9f5-105">Sök vägarna i den här variabeln genomsöks i den ordning som de visas.</span><span class="sxs-lookup"><span data-stu-id="fe9f5-105">The paths in this variable are searched in the order in which they appear.</span></span>

<span data-ttu-id="fe9f5-106">När Windows PowerShell startar skapas `PSModulePath` som en system miljö variabel med följande standardvärde: `$home\Documents\WindowsPowerShell\Modules; $pshome\Modules`.</span><span class="sxs-lookup"><span data-stu-id="fe9f5-106">When Windows PowerShell starts, `PSModulePath` is created as a system environment variable with the following default value: `$home\Documents\WindowsPowerShell\Modules; $pshome\Modules`.</span></span>

## <a name="to-view-the-psmodulepath-variable"></a><span data-ttu-id="fe9f5-107">Så här visar du variabeln PSModulePath</span><span class="sxs-lookup"><span data-stu-id="fe9f5-107">To view the PSModulePath variable</span></span>

<span data-ttu-id="fe9f5-108">Om du vill visa Sök vägarna som anges i variabeln `PSModulePath` skriver du följande kommando:</span><span class="sxs-lookup"><span data-stu-id="fe9f5-108">To view the paths that are specified in the `PSModulePath` variable, type the following command:</span></span>

`$env:PSModulePath`

## <a name="to-add-locations-to-the-psmodulepath-variable"></a><span data-ttu-id="fe9f5-109">Lägga till platser i PSModulePath-variabeln</span><span class="sxs-lookup"><span data-stu-id="fe9f5-109">To add locations to the PSModulePath variable</span></span>

<span data-ttu-id="fe9f5-110">Använd någon av följande metoder för att lägga till sökvägar till den här variabeln:</span><span class="sxs-lookup"><span data-stu-id="fe9f5-110">To add paths to this variable, use one of the following methods:</span></span>

- <span data-ttu-id="fe9f5-111">Om du vill lägga till ett tillfälligt värde som bara är tillgängligt för den aktuella sessionen kör du följande kommando på kommando raden:</span><span class="sxs-lookup"><span data-stu-id="fe9f5-111">To add a temporary value that is available only for the current session, run the following command at the command line:</span></span>

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

- <span data-ttu-id="fe9f5-112">Lägg till ett beständigt värde som är tillgängligt när en session öppnas genom att lägga till följande kommando i en Windows PowerShell-profil:</span><span class="sxs-lookup"><span data-stu-id="fe9f5-112">To add a persistent value that is available whenever a session is opened, add the following command to a Windows PowerShell profile:</span></span>

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

  <span data-ttu-id="fe9f5-113">Mer information om profiler finns i [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles) i Microsoft TechNet-biblioteket.</span><span class="sxs-lookup"><span data-stu-id="fe9f5-113">For more information about profiles, see [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles) in the Microsoft TechNet library.</span></span>

- <span data-ttu-id="fe9f5-114">Om du vill lägga till en beständig variabel i registret skapar du en ny användar miljö variabel som kallas `PSModulePath` med hjälp av miljövariabler-redigeraren i dialog rutan **system egenskaper** .</span><span class="sxs-lookup"><span data-stu-id="fe9f5-114">To add a persistent variable to the registry, create a new user environment variable called `PSModulePath` using the Environment Variables Editor in the **System Properties** dialog box.</span></span>

- <span data-ttu-id="fe9f5-115">Om du vill lägga till en beständig variabel med hjälp av ett skript, använder du metoden **SetEnvironmentVariable** i miljö klassen.</span><span class="sxs-lookup"><span data-stu-id="fe9f5-115">To add a persistent variable by using a script, use the **SetEnvironmentVariable** method on the Environment class.</span></span> <span data-ttu-id="fe9f5-116">Följande skript lägger till exempel till "C:\Program Files\Fabrikam\Module sökväg till värdet för PSModulePath-miljövariabeln för datorn.</span><span class="sxs-lookup"><span data-stu-id="fe9f5-116">For example, the following script adds the "C:\Program Files\Fabrikam\Module path to the value of the PSModulePath environment variable for the computer.</span></span> <span data-ttu-id="fe9f5-117">Om du vill lägga till sökvägen till PSModulePath-miljövariabeln anger du målet till "användare".</span><span class="sxs-lookup"><span data-stu-id="fe9f5-117">To add the path to the user PSModulePath environment variable, set the target to "User".</span></span>

  ```powershell
  $CurrentValue = [Environment]::GetEnvironmentVariable("PSModulePath", "Machine")
  [Environment]::SetEnvironmentVariable("PSModulePath", $CurrentValue + ";C:\Program Files\Fabrikam\Modules", "Machine")

  ```

## <a name="to-remove-locations-from-the-psmodulepath"></a><span data-ttu-id="fe9f5-118">Ta bort platser från PSModulePath</span><span class="sxs-lookup"><span data-stu-id="fe9f5-118">To remove locations from the PSModulePath</span></span>

<span data-ttu-id="fe9f5-119">Du kan ta bort sökvägar från variabeln med liknande metoder: `$env:PSModulePath = $env:PSModulePath -replace ";c:\\ModulePath"` tar till exempel bort **c:\ModulePath** -sökvägen från den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="fe9f5-119">You can remove paths from the variable using similar methods: for example, `$env:PSModulePath = $env:PSModulePath -replace ";c:\\ModulePath"` will remove the **c:\ModulePath** path from the current session.</span></span>

## <a name="see-also"></a><span data-ttu-id="fe9f5-120">Se även</span><span class="sxs-lookup"><span data-stu-id="fe9f5-120">See Also</span></span>

[<span data-ttu-id="fe9f5-121">Skriva en Windows PowerShell-modul</span><span class="sxs-lookup"><span data-stu-id="fe9f5-121">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)
