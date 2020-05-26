---
ms.date: 01/02/2020
keywords: powershell,cmdlet
title: Använd profiler Windows PowerShell ISE
ms.openlocfilehash: da7dc2f234ad0c2968fbb213e9e57da875f456e4
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/23/2020
ms.locfileid: "83810290"
---
# <a name="how-to-use-profiles-in-windows-powershell-ise"></a><span data-ttu-id="ecb55-103">Använd profiler Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="ecb55-103">How to Use Profiles in Windows PowerShell ISE</span></span>

<span data-ttu-id="ecb55-104">I det här avsnittet beskrivs hur du använder profiler i Windows PowerShell® Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="ecb55-104">This topic explains how to use Profiles in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="ecb55-105">Innan du utför uppgifterna i det här avsnittet rekommenderar vi att du granskar [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles)eller i konsol fönstret, skriver `Get-Help about_Profiles` och trycker på <kbd>RETUR</kbd>.</span><span class="sxs-lookup"><span data-stu-id="ecb55-105">We recommend that before performing the tasks in this section, you review [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles), or in the Console Pane, type, `Get-Help about_Profiles` and press <kbd>ENTER</kbd>.</span></span>

<span data-ttu-id="ecb55-106">En profil är ett Windows PowerShell ISE-skript som körs automatiskt när du startar en ny session.</span><span class="sxs-lookup"><span data-stu-id="ecb55-106">A profile is a Windows PowerShell ISE script that runs automatically when you start a new session.</span></span>
<span data-ttu-id="ecb55-107">Du kan skapa en eller flera Windows PowerShell-profiler för Windows PowerShell ISE och använda dem för att lägga till konfigurera Windows PowerShell-eller Windows PowerShell ISE-miljön, förbereda den för användning med variabler, alias, funktioner och färg och teckensnitts inställningar som du vill ha tillgängliga.</span><span class="sxs-lookup"><span data-stu-id="ecb55-107">You can create one or more Windows PowerShell profiles for Windows PowerShell ISE and use them to add the configure the Windows PowerShell or Windows PowerShell ISE environment, preparing it for your use, with variables, aliases, functions, and color and font preferences that you want available.</span></span> <span data-ttu-id="ecb55-108">En profil påverkar varje Windows PowerShell ISE session som du startar.</span><span class="sxs-lookup"><span data-stu-id="ecb55-108">A profile affects every Windows PowerShell ISE session that you start.</span></span>

> [!NOTE]
> <span data-ttu-id="ecb55-109">Windows PowerShell-körnings principen avgör om du kan köra skript och läsa in en profil.</span><span class="sxs-lookup"><span data-stu-id="ecb55-109">The Windows PowerShell execution policy determines whether you can run scripts and load a profile.</span></span>
> <span data-ttu-id="ecb55-110">Standard körnings principen "begränsad" förhindrar att alla skript körs, inklusive profiler.</span><span class="sxs-lookup"><span data-stu-id="ecb55-110">The default execution policy, “Restricted,” prevents all scripts from running, including profiles.</span></span>
> <span data-ttu-id="ecb55-111">Om du använder principen "begränsad" går det inte att läsa in profilen.</span><span class="sxs-lookup"><span data-stu-id="ecb55-111">If you use the “Restricted” policy, the profile cannot load.</span></span> <span data-ttu-id="ecb55-112">Mer information om körnings principer finns [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span><span class="sxs-lookup"><span data-stu-id="ecb55-112">For more information about execution policy, see [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span></span>

## <a name="selecting-a-profile-to-use-in-the-windows-powershell-ise"></a><span data-ttu-id="ecb55-113">Välja en profil som ska användas i Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="ecb55-113">Selecting a profile to use in the Windows PowerShell ISE</span></span>

<span data-ttu-id="ecb55-114">Windows PowerShell ISE stöder profiler för den aktuella användaren och alla användare.</span><span class="sxs-lookup"><span data-stu-id="ecb55-114">Windows PowerShell ISE supports profiles for the current user and all users.</span></span> <span data-ttu-id="ecb55-115">Det stöder också de Windows PowerShell-profiler som gäller för alla värdar.</span><span class="sxs-lookup"><span data-stu-id="ecb55-115">It also supports the Windows PowerShell profiles that apply to all hosts.</span></span>

<span data-ttu-id="ecb55-116">Den profil som du använder bestäms av hur du använder Windows PowerShell och Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="ecb55-116">The profile that you use is determined by how you use Windows PowerShell and Windows PowerShell ISE.</span></span>

- <span data-ttu-id="ecb55-117">Om du bara använder Windows PowerShell ISE för att köra Windows PowerShell sparar du alla objekt i någon av de ISE-/regionsspecifika profilerna, till exempel **CurrentUserCurrentHost** -profilen för Windows PowerShell ISE eller **AllUsersCurrentHost** -profilen för Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="ecb55-117">If you use only Windows PowerShell ISE to run Windows PowerShell, then save all your items in one of the ISE-specific profiles, such as the **CurrentUserCurrentHost** profile for Windows PowerShell ISE or the **AllUsersCurrentHost** profile for Windows PowerShell ISE.</span></span>

- <span data-ttu-id="ecb55-118">Om du använder flera värd program för att köra Windows PowerShell sparar du funktioner, alias, variabler och kommandon i en profil som påverkar alla värd program, till exempel CurrentUserAllHosts eller **AllUsersAllHosts** -profilen, och sparar ISE-/regionsspecifika funktioner, till exempel färg-och teckensnitts anpassning i **CurrentUserCurrentHost** -profilen för Windows PowerShell ISE profil eller **AllUsersCurrentHost** -profilen för Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="ecb55-118">If you use multiple host programs to run Windows PowerShell, save your functions, aliases, variables, and commands in a profile that affects all host programs, such as the CurrentUserAllHosts or the **AllUsersAllHosts** profile, and save ISE-specific features, like color and font customization in the **CurrentUserCurrentHost** profile for Windows PowerShell ISE profile or the **AllUsersCurrentHost** profile for Windows PowerShell ISE.</span></span>

<span data-ttu-id="ecb55-119">Följande är profiler som kan skapas och användas i Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="ecb55-119">The following are profiles that can be created and used in Windows PowerShell ISE.</span></span> <span data-ttu-id="ecb55-120">Varje profil sparas på en egen angiven sökväg.</span><span class="sxs-lookup"><span data-stu-id="ecb55-120">Each profile is saved to its own specific path.</span></span>

|           <span data-ttu-id="ecb55-121">Profil typ</span><span class="sxs-lookup"><span data-stu-id="ecb55-121">Profile Type</span></span>           |                   <span data-ttu-id="ecb55-122">Sökväg till profil</span><span class="sxs-lookup"><span data-stu-id="ecb55-122">Profile Path</span></span>                   |
| -------------------------------- | ------------------------------------------------ |
| <span data-ttu-id="ecb55-123">**Aktuell användare, PowerShell ISE**</span><span class="sxs-lookup"><span data-stu-id="ecb55-123">**Current user, PowerShell ISE**</span></span> | <span data-ttu-id="ecb55-124">`$PROFILE.CurrentUserCurrentHost` eller `$PROFILE`</span><span class="sxs-lookup"><span data-stu-id="ecb55-124">`$PROFILE.CurrentUserCurrentHost`, or `$PROFILE`</span></span> |
| <span data-ttu-id="ecb55-125">**Alla användare, PowerShell ISE**</span><span class="sxs-lookup"><span data-stu-id="ecb55-125">**All users, PowerShell ISE**</span></span>    | `$PROFILE.AllUsersCurrentHost`                   |
| <span data-ttu-id="ecb55-126">**Aktuell användare, alla värdar**</span><span class="sxs-lookup"><span data-stu-id="ecb55-126">**Current user, All hosts**</span></span>      | `$PROFILE.CurrentUserAllHosts`                   |
| <span data-ttu-id="ecb55-127">**Alla användare, alla värdar**</span><span class="sxs-lookup"><span data-stu-id="ecb55-127">**All users, All hosts**</span></span>         | `$PROFILE.AllUsersAllHosts`                      |

## <a name="to-create-a-new-profile"></a><span data-ttu-id="ecb55-128">Så här skapar du en ny profil</span><span class="sxs-lookup"><span data-stu-id="ecb55-128">To create a new profile</span></span>

<span data-ttu-id="ecb55-129">Kör följande kommando för att skapa en ny profil för "aktuell användare, Windows PowerShell ISE":</span><span class="sxs-lookup"><span data-stu-id="ecb55-129">To create a new “Current user, Windows PowerShell ISE” profile, run this command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE ))
{ New-Item -Type File -Path $PROFILE -Force }
```

<span data-ttu-id="ecb55-130">Kör det här kommandot om du vill skapa en ny "alla användare, Windows PowerShell ISE"-profil:</span><span class="sxs-lookup"><span data-stu-id="ecb55-130">To create a new “All users, Windows PowerShell ISE” profile, run this command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE.AllUsersCurrentHost))
{ New-Item -Type File -Path $PROFILE.AllUsersCurrentHost -Force }
```

<span data-ttu-id="ecb55-131">Om du vill skapa en ny "aktuell användare, alla värdar"-profil kör du följande kommando:</span><span class="sxs-lookup"><span data-stu-id="ecb55-131">To create a new “Current user, All Hosts” profile, run this command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE.CurrentUserAllHosts))
{ New-Item -Type File -Path $PROFILE.CurrentUserAllHosts -Force }
```

<span data-ttu-id="ecb55-132">Om du vill skapa en ny profil för alla användare, alla värdar skriver du:</span><span class="sxs-lookup"><span data-stu-id="ecb55-132">To create a new “All users, All Hosts” profile, type:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE.AllUsersAllHosts))
{ New-Item -Type File -Path $PROFILE.AllUsersAllHosts -Force }
```

## <a name="to-edit-a-profile"></a><span data-ttu-id="ecb55-133">Redigera en profil</span><span class="sxs-lookup"><span data-stu-id="ecb55-133">To edit a profile</span></span>

1. <span data-ttu-id="ecb55-134">Om du vill öppna profilen kör du kommandot `psEdit` med variabeln som anger den profil som du vill redigera.</span><span class="sxs-lookup"><span data-stu-id="ecb55-134">To open the profile, run the command `psEdit` with the variable that specifies the profile you want to edit.</span></span> <span data-ttu-id="ecb55-135">Om du till exempel vill öppna profilen "aktuell användare, Windows PowerShell ISE" skriver du:`psEdit $PROFILE`</span><span class="sxs-lookup"><span data-stu-id="ecb55-135">For example, to open the “Current user, Windows PowerShell ISE” profile, type: `psEdit $PROFILE`</span></span>

2. <span data-ttu-id="ecb55-136">Lägg till några objekt i din profil.</span><span class="sxs-lookup"><span data-stu-id="ecb55-136">Add some items to your profile.</span></span> <span data-ttu-id="ecb55-137">Nedan följer några exempel på hur du kan komma igång:</span><span class="sxs-lookup"><span data-stu-id="ecb55-137">The following are a few examples to get you started:</span></span>

   - <span data-ttu-id="ecb55-138">Ändra standard bakgrunds färgen för konsol fönstret till blått i profil fil typen: `$psISE.Options.OutputPaneBackground = 'blue'` .</span><span class="sxs-lookup"><span data-stu-id="ecb55-138">To change the default background color of the Console Pane to blue, in the profile file type: `$psISE.Options.OutputPaneBackground = 'blue'` .</span></span> <span data-ttu-id="ecb55-139">Mer information om `$psISE` variabeln finns i [Windows PowerShell ISE objekt modell referens](object-model/The-ISE-Object-Model-Hierarchy.md).</span><span class="sxs-lookup"><span data-stu-id="ecb55-139">For more information about the `$psISE` variable, see [Windows PowerShell ISE Object Model Reference](object-model/The-ISE-Object-Model-Hierarchy.md).</span></span>

   - <span data-ttu-id="ecb55-140">Om du vill ändra tecken storleken till 20, i profil fil typen:`$psISE.Options.FontSize =20`</span><span class="sxs-lookup"><span data-stu-id="ecb55-140">To change font size to 20, in the profile file type: `$psISE.Options.FontSize =20`</span></span>

3. <span data-ttu-id="ecb55-141">Spara profil filen genom att klicka på **Spara**på **Arkiv** -menyn.</span><span class="sxs-lookup"><span data-stu-id="ecb55-141">To save your profile file, on the **File** menu, click **Save**.</span></span> <span data-ttu-id="ecb55-142">Nästa gången du öppnar Windows PowerShell ISE tillämpas dina anpassningar.</span><span class="sxs-lookup"><span data-stu-id="ecb55-142">Next time you open the Windows PowerShell ISE, your customizations are applied.</span></span>

## <a name="see-also"></a><span data-ttu-id="ecb55-143">Se även</span><span class="sxs-lookup"><span data-stu-id="ecb55-143">See Also</span></span>

- [<span data-ttu-id="ecb55-144">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="ecb55-144">about_Profiles</span></span>](/powershell/module/microsoft.powershell.core/about/about_profiles)
- [<span data-ttu-id="ecb55-145">Vi presenterar Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="ecb55-145">Introducing the Windows PowerShell ISE</span></span>](Introducing-the-Windows-PowerShell-ISE.md)
