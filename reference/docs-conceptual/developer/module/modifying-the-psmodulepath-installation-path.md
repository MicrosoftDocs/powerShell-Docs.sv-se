---
title: Ändra installations Sök vägen för PSModulePath | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 795f2bd52aeceddd3c0ca092d0c0cf2ef44bcf23
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784851"
---
# <a name="modifying-the-psmodulepath-installation-path"></a><span data-ttu-id="bc01e-102">Ändra installationssökvägen för PSModulePath</span><span class="sxs-lookup"><span data-stu-id="bc01e-102">Modifying the PSModulePath Installation Path</span></span>

<span data-ttu-id="bc01e-103">`PSModulePath`Miljövariabeln lagrar Sök vägarna till platserna för de moduler som är installerade på disk.</span><span class="sxs-lookup"><span data-stu-id="bc01e-103">The `PSModulePath` environment variable stores the paths to the locations of the modules that are installed on disk.</span></span> <span data-ttu-id="bc01e-104">PowerShell använder den här variabeln för att hitta moduler när användaren inte anger den fullständiga sökvägen till en modul.</span><span class="sxs-lookup"><span data-stu-id="bc01e-104">PowerShell uses this variable to locate modules when the user does not specify the full path to a module.</span></span> <span data-ttu-id="bc01e-105">Sök vägarna i den här variabeln genomsöks i den ordning som de visas.</span><span class="sxs-lookup"><span data-stu-id="bc01e-105">The paths in this variable are searched in the order in which they appear.</span></span>

<span data-ttu-id="bc01e-106">När PowerShell startar `PSModulePath` skapas som en system miljö variabel med följande standardvärde: `$HOME\Documents\PowerShell\Modules; $PSHOME\Modules` i Windows och `$HOME/.local/share/powershell/Modules: usr/local/share/powershell/Modules` på Linux eller Mac, och `$HOME\Documents\WindowsPowerShell\Modules; $PSHOME\Modules` för Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bc01e-106">When PowerShell starts, `PSModulePath` is created as a system environment variable with the following default value: `$HOME\Documents\PowerShell\Modules; $PSHOME\Modules` on Windows and `$HOME/.local/share/powershell/Modules: usr/local/share/powershell/Modules` on Linux or Mac, and `$HOME\Documents\WindowsPowerShell\Modules; $PSHOME\Modules` for Windows PowerShell.</span></span>

> [!NOTE]
> <span data-ttu-id="bc01e-107">Den användarspecifika **CurrentUser** -platsen är `WindowsPowerShell\Modules` mappen som finns på **dokument** platsen i din användar profil.</span><span class="sxs-lookup"><span data-stu-id="bc01e-107">The user-specific **CurrentUser** location is the `WindowsPowerShell\Modules` folder located in the **Documents** location in your user profile.</span></span> <span data-ttu-id="bc01e-108">Den angivna sökvägen till platsen varierar efter Windows-version och om du använder mappomdirigering.</span><span class="sxs-lookup"><span data-stu-id="bc01e-108">The specific path of that location varies by version of Windows and whether or not you are using folder redirection.</span></span> <span data-ttu-id="bc01e-109">Som standard är den platsen i Windows 10 `$HOME\Documents\WindowsPowerShell\Modules` .</span><span class="sxs-lookup"><span data-stu-id="bc01e-109">By default, on Windows 10, that location is `$HOME\Documents\WindowsPowerShell\Modules`.</span></span>

## <a name="to-view-the-psmodulepath-variable"></a><span data-ttu-id="bc01e-110">Så här visar du variabeln PSModulePath</span><span class="sxs-lookup"><span data-stu-id="bc01e-110">To view the PSModulePath variable</span></span>

<span data-ttu-id="bc01e-111">Om du vill visa Sök vägarna som anges i `PSModulePath` variabeln, skriver du följande kommando:</span><span class="sxs-lookup"><span data-stu-id="bc01e-111">To view the paths that are specified in the `PSModulePath` variable, type the following command:</span></span>

`$env:PSModulePath`

## <a name="to-add-locations-to-the-psmodulepath-variable"></a><span data-ttu-id="bc01e-112">Lägga till platser i PSModulePath-variabeln</span><span class="sxs-lookup"><span data-stu-id="bc01e-112">To add locations to the PSModulePath variable</span></span>

<span data-ttu-id="bc01e-113">Använd någon av följande metoder för att lägga till sökvägar till den här variabeln:</span><span class="sxs-lookup"><span data-stu-id="bc01e-113">To add paths to this variable, use one of the following methods:</span></span>

- <span data-ttu-id="bc01e-114">Om du vill lägga till ett tillfälligt värde som bara är tillgängligt för den aktuella sessionen kör du följande kommando på kommando raden:</span><span class="sxs-lookup"><span data-stu-id="bc01e-114">To add a temporary value that is available only for the current session, run the following command at the command line:</span></span>

  `$env:PSModulePath = $env:PSModulePath + "$([System.IO.Path]::PathSeparator)$MyModulePath"`

- <span data-ttu-id="bc01e-115">Om du vill lägga till ett permanent värde som är tillgängligt när en session öppnas, lägger du till kommandot ovan i en PowerShell-profil fil ( `$PROFILE` ) ></span><span class="sxs-lookup"><span data-stu-id="bc01e-115">To add a persistent value that is available whenever a session is opened, add the above command to a PowerShell profile file (`$PROFILE`)></span></span>

  <span data-ttu-id="bc01e-116">Mer information om profiler finns [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles).</span><span class="sxs-lookup"><span data-stu-id="bc01e-116">For more information about profiles, see [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles).</span></span>

- <span data-ttu-id="bc01e-117">Om du vill lägga till en beständig variabel i registret skapar du en ny användar miljö variabel som kallas `PSModulePath` med hjälp av miljövariabler-redigeraren i dialog rutan **system egenskaper** .</span><span class="sxs-lookup"><span data-stu-id="bc01e-117">To add a persistent variable to the registry, create a new user environment variable called `PSModulePath` using the Environment Variables Editor in the **System Properties** dialog box.</span></span>

- <span data-ttu-id="bc01e-118">Om du vill lägga till en beständig variabel med hjälp av ett skript, använder du .net-metoden [SetEnvironmentVariable](/dotnet/api/system.environment.setenvironmentvariable) i klassen [system. Environment](/dotnet/api/system.environment) .</span><span class="sxs-lookup"><span data-stu-id="bc01e-118">To add a persistent variable by using a script, use the .Net method [SetEnvironmentVariable](/dotnet/api/system.environment.setenvironmentvariable) on the [System.Environment](/dotnet/api/system.environment) class.</span></span> <span data-ttu-id="bc01e-119">Följande skript lägger till exempel till `C:\Program Files\Fabrikam\Module` sökvägen till värdet för `PSModulePath` miljö variabeln för datorn.</span><span class="sxs-lookup"><span data-stu-id="bc01e-119">For example, the following script adds the `C:\Program Files\Fabrikam\Module` path to the value of the `PSModulePath` environment variable for the computer.</span></span> <span data-ttu-id="bc01e-120">Om du vill lägga till sökvägen till användar `PSModulePath` miljö variabeln anger du målet till "användare".</span><span class="sxs-lookup"><span data-stu-id="bc01e-120">To add the path to the user `PSModulePath` environment variable, set the target to "User".</span></span>

  ```powershell
  $CurrentValue = [Environment]::GetEnvironmentVariable("PSModulePath", "Machine")
  [Environment]::SetEnvironmentVariable("PSModulePath", $CurrentValue + [System.IO.Path]::PathSeparator + "C:\Program Files\Fabrikam\Modules", "Machine")

  ```

## <a name="to-remove-locations-from-the-psmodulepath"></a><span data-ttu-id="bc01e-121">Ta bort platser från PSModulePath</span><span class="sxs-lookup"><span data-stu-id="bc01e-121">To remove locations from the PSModulePath</span></span>

<span data-ttu-id="bc01e-122">Du kan ta bort sökvägar från variabeln med liknande metoder: om du till exempel tar `$env:PSModulePath = $env:PSModulePath -replace "$([System.IO.Path]::PathSeparator)c:\\ModulePath"` bort **c:\ModulePath** -sökvägen från den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="bc01e-122">You can remove paths from the variable using similar methods: for example, `$env:PSModulePath = $env:PSModulePath -replace "$([System.IO.Path]::PathSeparator)c:\\ModulePath"` will remove the **c:\ModulePath** path from the current session.</span></span>

## <a name="see-also"></a><span data-ttu-id="bc01e-123">Se även</span><span class="sxs-lookup"><span data-stu-id="bc01e-123">See Also</span></span>

[<span data-ttu-id="bc01e-124">Skriva en Windows PowerShell-modul</span><span class="sxs-lookup"><span data-stu-id="bc01e-124">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)

[<span data-ttu-id="bc01e-125">about_Modules</span><span class="sxs-lookup"><span data-stu-id="bc01e-125">about_Modules</span></span>](/powershell/module/microsoft.powershell.core/about/about_modules)
