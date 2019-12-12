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
ms.openlocfilehash: 5957ea4c15cd3778bd09b67c4b97de0ef0cfdd2a
ms.sourcegitcommit: 0e4c69d8b5cf71431592fe41da816dec9b70f1f9
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/09/2019
ms.locfileid: "74953848"
---
# <a name="modifying-the-psmodulepath-installation-path"></a><span data-ttu-id="abc1b-102">Ändra installationssökvägen för PSModulePath</span><span class="sxs-lookup"><span data-stu-id="abc1b-102">Modifying the PSModulePath Installation Path</span></span>

<span data-ttu-id="abc1b-103">I miljövariabeln `PSModulePath` lagras Sök vägarna till platserna för de moduler som är installerade på disk.</span><span class="sxs-lookup"><span data-stu-id="abc1b-103">The `PSModulePath` environment variable stores the paths to the locations of the modules that are installed on disk.</span></span> <span data-ttu-id="abc1b-104">PowerShell använder den här variabeln för att hitta moduler när användaren inte anger den fullständiga sökvägen till en modul.</span><span class="sxs-lookup"><span data-stu-id="abc1b-104">PowerShell uses this variable to locate modules when the user does not specify the full path to a module.</span></span> <span data-ttu-id="abc1b-105">Sök vägarna i den här variabeln genomsöks i den ordning som de visas.</span><span class="sxs-lookup"><span data-stu-id="abc1b-105">The paths in this variable are searched in the order in which they appear.</span></span>

<span data-ttu-id="abc1b-106">När PowerShell startar skapas `PSModulePath` som en system miljö variabel med följande standardvärde: `$HOME\Documents\PowerShell\Modules; $PSHOME\Modules` eller `$HOME\Documents\WindowsPowerShell\Modules; $PSHOME\Modules` för Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="abc1b-106">When PowerShell starts, `PSModulePath` is created as a system environment variable with the following default value: `$HOME\Documents\PowerShell\Modules; $PSHOME\Modules` or `$HOME\Documents\WindowsPowerShell\Modules; $PSHOME\Modules` for Windows PowerShell.</span></span>

## <a name="to-view-the-psmodulepath-variable"></a><span data-ttu-id="abc1b-107">Så här visar du variabeln PSModulePath</span><span class="sxs-lookup"><span data-stu-id="abc1b-107">To view the PSModulePath variable</span></span>

<span data-ttu-id="abc1b-108">Om du vill visa de sökvägar som anges i variabeln `PSModulePath` anger du följande kommando:</span><span class="sxs-lookup"><span data-stu-id="abc1b-108">To view the paths that are specified in the `PSModulePath` variable, type the following command:</span></span>

`$env:PSModulePath`

## <a name="to-add-locations-to-the-psmodulepath-variable"></a><span data-ttu-id="abc1b-109">Lägga till platser i PSModulePath-variabeln</span><span class="sxs-lookup"><span data-stu-id="abc1b-109">To add locations to the PSModulePath variable</span></span>

<span data-ttu-id="abc1b-110">Använd någon av följande metoder för att lägga till sökvägar till den här variabeln:</span><span class="sxs-lookup"><span data-stu-id="abc1b-110">To add paths to this variable, use one of the following methods:</span></span>

- <span data-ttu-id="abc1b-111">Om du vill lägga till ett tillfälligt värde som bara är tillgängligt för den aktuella sessionen kör du följande kommando på kommando raden:</span><span class="sxs-lookup"><span data-stu-id="abc1b-111">To add a temporary value that is available only for the current session, run the following command at the command line:</span></span>

  `$env:PSModulePath = $env:PSModulePath + "$([System.IO.Path]::PathSeparator)$MyModulePath"`

- <span data-ttu-id="abc1b-112">Om du vill lägga till ett permanent värde som är tillgängligt när en session öppnas, lägger du till kommandot ovan i en PowerShell-profil fil (`$PROFILE`) ></span><span class="sxs-lookup"><span data-stu-id="abc1b-112">To add a persistent value that is available whenever a session is opened, add the above command to a PowerShell profile file (`$PROFILE`)></span></span>

  <span data-ttu-id="abc1b-113">Mer information om profiler finns [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles).</span><span class="sxs-lookup"><span data-stu-id="abc1b-113">For more information about profiles, see [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles).</span></span>

- <span data-ttu-id="abc1b-114">Om du vill lägga till en beständig variabel i registret skapar du en ny användar miljö variabel som kallas `PSModulePath` med hjälp av miljövariabler-redigeraren i dialog rutan **system egenskaper** .</span><span class="sxs-lookup"><span data-stu-id="abc1b-114">To add a persistent variable to the registry, create a new user environment variable called `PSModulePath` using the Environment Variables Editor in the **System Properties** dialog box.</span></span>

- <span data-ttu-id="abc1b-115">Om du vill lägga till en beständig variabel med hjälp av ett skript, använder du .net-metoden [SetEnvironmentVariable](https://docs.microsoft.com/dotnet/api/system.environment.setenvironmentvariable) i klassen [system. Environment](https://docs.microsoft.com/dotnet/api/system.environment) .</span><span class="sxs-lookup"><span data-stu-id="abc1b-115">To add a persistent variable by using a script, use the .Net method [SetEnvironmentVariable](https://docs.microsoft.com/dotnet/api/system.environment.setenvironmentvariable) on the [System.Environment](https://docs.microsoft.com/dotnet/api/system.environment) class.</span></span> <span data-ttu-id="abc1b-116">Följande skript lägger till exempel till `C:\Program Files\Fabrikam\Module` sökvägen till värdet i `PSModulePath` miljövariabeln för datorn.</span><span class="sxs-lookup"><span data-stu-id="abc1b-116">For example, the following script adds the `C:\Program Files\Fabrikam\Module` path to the value of the `PSModulePath` environment variable for the computer.</span></span> <span data-ttu-id="abc1b-117">Om du vill lägga till sökvägen till användar `PSModulePath`-miljövariabeln anger du målet till "användare".</span><span class="sxs-lookup"><span data-stu-id="abc1b-117">To add the path to the user `PSModulePath` environment variable, set the target to "User".</span></span>

  ```powershell
  $CurrentValue = [Environment]::GetEnvironmentVariable("PSModulePath", "Machine")
  [Environment]::SetEnvironmentVariable("PSModulePath", $CurrentValue + [System.IO.Path]::PathSeparator + "C:\Program Files\Fabrikam\Modules", "Machine")

  ```

## <a name="to-remove-locations-from-the-psmodulepath"></a><span data-ttu-id="abc1b-118">Ta bort platser från PSModulePath</span><span class="sxs-lookup"><span data-stu-id="abc1b-118">To remove locations from the PSModulePath</span></span>

<span data-ttu-id="abc1b-119">Du kan ta bort sökvägar från variabeln med liknande metoder: `$env:PSModulePath = $env:PSModulePath -replace "$([System.IO.Path]::PathSeparator)c:\\ModulePath"` tar till exempel bort **c:\ModulePath** -sökvägen från den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="abc1b-119">You can remove paths from the variable using similar methods: for example, `$env:PSModulePath = $env:PSModulePath -replace "$([System.IO.Path]::PathSeparator)c:\\ModulePath"` will remove the **c:\ModulePath** path from the current session.</span></span>

## <a name="see-also"></a><span data-ttu-id="abc1b-120">Se även</span><span class="sxs-lookup"><span data-stu-id="abc1b-120">See Also</span></span>

[<span data-ttu-id="abc1b-121">Skriva en Windows PowerShell-modul</span><span class="sxs-lookup"><span data-stu-id="abc1b-121">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)
