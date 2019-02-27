---
title: Ändra installationssökvägen PSModulePath | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dc5ce5a2-50e9-4c88-abf1-ac148a8a6b7b
caps.latest.revision: 15
ms.openlocfilehash: 639d3a28dd2af09fcc498caedc5fe74c1493445d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846510"
---
# <a name="modifying-the-psmodulepath-installation-path"></a><span data-ttu-id="dd84e-102">Ändra installationssökvägen för PSModulePath</span><span class="sxs-lookup"><span data-stu-id="dd84e-102">Modifying the PSModulePath Installation Path</span></span>

<span data-ttu-id="dd84e-103">Den `PSModulePath` miljövariabeln lagrar sökvägar till platser där modulerna som är installerade på disken.</span><span class="sxs-lookup"><span data-stu-id="dd84e-103">The `PSModulePath` environment variable stores the paths to the locations of the modules that are installed on disk.</span></span> <span data-ttu-id="dd84e-104">Windows PowerShell använder den här variabeln för att hitta moduler när användaren inte anger den fullständiga sökvägen till en modul.</span><span class="sxs-lookup"><span data-stu-id="dd84e-104">Windows PowerShell uses this variable to locate modules when the user does not specify the full path to a module.</span></span> <span data-ttu-id="dd84e-105">Sökvägarna i den här variabeln genomsöks i den ordning som de visas.</span><span class="sxs-lookup"><span data-stu-id="dd84e-105">The paths in this variable are searched in the order in which they appear.</span></span>

<span data-ttu-id="dd84e-106">När Windows PowerShell startar `PSModulePath` skapas som en systemmiljövariabel med följande standardvärdet: `$home\Documents\WindowsPowerShell\Modules; $pshome\Modules`.</span><span class="sxs-lookup"><span data-stu-id="dd84e-106">When Windows PowerShell starts, `PSModulePath` is created as a system environment variable with the following default value: `$home\Documents\WindowsPowerShell\Modules; $pshome\Modules`.</span></span>

## <a name="to-view-the-psmodulepath-variable"></a><span data-ttu-id="dd84e-107">Visa PSModulePath variabeln</span><span class="sxs-lookup"><span data-stu-id="dd84e-107">To view the PSModulePath variable</span></span>

<span data-ttu-id="dd84e-108">Visa sökvägarna som anges i den `PSModulePath` variabel, skriver du följande kommando:</span><span class="sxs-lookup"><span data-stu-id="dd84e-108">To view the paths that are specified in the `PSModulePath` variable, type the following command:</span></span>

`$env:PSModulePath`

## <a name="to-add-locations-to-the-psmodulepath-variable"></a><span data-ttu-id="dd84e-109">Att lägga till platser i variabeln PSModulePath</span><span class="sxs-lookup"><span data-stu-id="dd84e-109">To add locations to the PSModulePath variable</span></span>

<span data-ttu-id="dd84e-110">Använd någon av följande metoder för att lägga till sökvägar till den här variabeln:</span><span class="sxs-lookup"><span data-stu-id="dd84e-110">To add paths to this variable, use one of the following methods:</span></span>

- <span data-ttu-id="dd84e-111">Om du vill lägga till ett tillfälligt värde som är tillgänglig endast för den aktuella sessionen, kör du följande kommando på kommandoraden:</span><span class="sxs-lookup"><span data-stu-id="dd84e-111">To add a temporary value that is available only for the current session, run the following command at the command line:</span></span>

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

- <span data-ttu-id="dd84e-112">Lägg till följande kommando i en Windows PowerShell-profil för att lägga till ett beständigt värde som är tillgängliga när en session öppnas:</span><span class="sxs-lookup"><span data-stu-id="dd84e-112">To add a persistent value that is available whenever a session is opened, add the following command to a Windows PowerShell profile:</span></span>

  `$env:PSModulePath = $env:PSModulePath + ";c:\ModulePath"`

  <span data-ttu-id="dd84e-113">Mer information om profiler finns i [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles) i Microsoft TechNet-biblioteket.</span><span class="sxs-lookup"><span data-stu-id="dd84e-113">For more information about profiles, see [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles) in the Microsoft TechNet library.</span></span>

- <span data-ttu-id="dd84e-114">Lägg till en beständig variabel i registret genom att skapa en ny användare-miljövariabel som heter `PSModulePath` med hjälp av redigeraren miljö variabler i den **Systemegenskaper** dialogrutan.</span><span class="sxs-lookup"><span data-stu-id="dd84e-114">To add a persistent variable to the registry, create a new user environment variable called `PSModulePath` using the Environment Variables Editor in the **System Properties** dialog box.</span></span>

- <span data-ttu-id="dd84e-115">Lägg till en beständig variabel med ett skript genom att använda den **SetEnvironmentVariable** -metoden i klassen miljö.</span><span class="sxs-lookup"><span data-stu-id="dd84e-115">To add a persistent variable by using a script, use the **SetEnvironmentVariable** method on the Environment class.</span></span> <span data-ttu-id="dd84e-116">Till exempel följande skriptet lägger till ”c:\Program\Microsoft Files\Fabrikam\Module sökväg till värdet för miljövariabeln PSModulePath för datorn.</span><span class="sxs-lookup"><span data-stu-id="dd84e-116">For example, the following script adds the "C:\Program Files\Fabrikam\Module path to the value of the PSModulePath environment variable for the computer.</span></span> <span data-ttu-id="dd84e-117">Lägg till sökvägen till miljövariabeln användaren PSModulePath, ange målet ”användare”.</span><span class="sxs-lookup"><span data-stu-id="dd84e-117">To add the path to the user PSModulePath environment variable, set the target to "User".</span></span>

  ```powershell
  $CurrentValue = [Environment]::GetEnvironmentVariable("PSModulePath", "Machine")
  [Environment]::SetEnvironmentVariable("PSModulePath", $CurrentValue + ";C:\Program Files\Fabrikam\Modules", "Machine")

  ```

## <a name="to-remove-locations-from-the-psmodulepath"></a><span data-ttu-id="dd84e-118">Ta bort platser från PSModulePath</span><span class="sxs-lookup"><span data-stu-id="dd84e-118">To remove locations from the PSModulePath</span></span>

<span data-ttu-id="dd84e-119">Du kan ta bort sökvägar från variabeln med liknande metoder: till exempel `$env:PSModulePath = $env:PSModulePath -replace ";c:\\ModulePath"` tar bort den **c:\ModulePath** sökväg från den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="dd84e-119">You can remove paths from the variable using similar methods: for example, `$env:PSModulePath = $env:PSModulePath -replace ";c:\\ModulePath"` will remove the **c:\ModulePath** path from the current session.</span></span>

## <a name="see-also"></a><span data-ttu-id="dd84e-120">Se även</span><span class="sxs-lookup"><span data-stu-id="dd84e-120">See Also</span></span>

[<span data-ttu-id="dd84e-121">Skriva ett Windows PowerShell-modul</span><span class="sxs-lookup"><span data-stu-id="dd84e-121">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)
