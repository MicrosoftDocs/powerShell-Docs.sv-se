---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Använd profiler Windows PowerShell ISE
ms.openlocfilehash: 28354f39aaaa577cec69c1b3f62cfe16ef091218
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030600"
---
# <a name="how-to-use-profiles-in-windows-powershell-ise"></a><span data-ttu-id="f3bdb-103">Använd profiler Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="f3bdb-103">How to Use Profiles in Windows PowerShell ISE</span></span>

<span data-ttu-id="f3bdb-104">Det här avsnittet förklarar hur du använder profiler i Windows PowerShell® Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="f3bdb-104">This topic explains how to use Profiles in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="f3bdb-105">Vi rekommenderar att innan du utför uppgifterna i det här avsnittet måste du granska [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles), eller i konsolfönstret, typ, `Get-Help about_Profiles` och tryck på **RETUR**.</span><span class="sxs-lookup"><span data-stu-id="f3bdb-105">We recommend that before performing the tasks in this section, you review [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles), or in the Console Pane, type, `Get-Help about_Profiles` and press **ENTER**.</span></span>

<span data-ttu-id="f3bdb-106">En profil är ett Windows PowerShell ISE-skript som körs automatiskt när du startar en ny session.</span><span class="sxs-lookup"><span data-stu-id="f3bdb-106">A profile is a Windows PowerShell ISE script that runs automatically when you start a new session.</span></span>  <span data-ttu-id="f3bdb-107">Du kan skapa en eller flera Windows PowerShell-profiler för Windows PowerShell ISE och använda dem för att lägga till Konfigurera Windows PowerShell eller Windows PowerShell ISE-miljön, förbereder den för din användning, med variabler, alias, funktioner, och färg och teckensnitt inställningar som du efterfrågar tillgängliga.</span><span class="sxs-lookup"><span data-stu-id="f3bdb-107">You can create one or more Windows PowerShell profiles for Windows PowerShell ISE and use them to add the configure the Windows PowerShell or Windows PowerShell ISE environment, preparing it for your use, with variables, aliases, functions, and color and font preferences that you want available.</span></span> <span data-ttu-id="f3bdb-108">En profil påverkar alla Windows PowerShell ISE-session som du startar.</span><span class="sxs-lookup"><span data-stu-id="f3bdb-108">A profile affects every Windows PowerShell ISE session that you start.</span></span>

> [!NOTE]
> <span data-ttu-id="f3bdb-109">Windows PowerShell-körningsprincipen avgör om du kan köra skript och läsa in en profil.</span><span class="sxs-lookup"><span data-stu-id="f3bdb-109">The Windows PowerShell execution policy determines whether you can run scripts and load a profile.</span></span> <span data-ttu-id="f3bdb-110">Standardprincipen för körning ”begränsad”, förhindrar alla skript från att köras, inklusive profiler.</span><span class="sxs-lookup"><span data-stu-id="f3bdb-110">The default execution policy, “Restricted,” prevents all scripts from running, including profiles.</span></span> <span data-ttu-id="f3bdb-111">Om du använder principen ”begränsad” profilen kan inte läsas in.</span><span class="sxs-lookup"><span data-stu-id="f3bdb-111">If you use the “Restricted” policy, the profile cannot load.</span></span> <span data-ttu-id="f3bdb-112">Läs mer om körningsprincipen [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span><span class="sxs-lookup"><span data-stu-id="f3bdb-112">For more information about execution policy, see [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).</span></span>

## <a name="selecting-a-profile-to-use-in-the-windows-powershell-ise"></a><span data-ttu-id="f3bdb-113">Att välja en profil som används i Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="f3bdb-113">Selecting a profile to use in the Windows PowerShell ISE</span></span>

<span data-ttu-id="f3bdb-114">Windows PowerShell ISE stöder profiler för den aktuella användaren och alla användare.</span><span class="sxs-lookup"><span data-stu-id="f3bdb-114">Windows PowerShell ISE supports profiles for the current user and all users.</span></span> <span data-ttu-id="f3bdb-115">Det stöder även de Windows PowerShell-profiler som gäller för alla värdar.</span><span class="sxs-lookup"><span data-stu-id="f3bdb-115">It also supports the Windows PowerShell profiles that apply to all hosts.</span></span>

<span data-ttu-id="f3bdb-116">Den profil som du använder bestäms av hur du använder Windows PowerShell och Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="f3bdb-116">The profile that you use is determined by how you use Windows PowerShell and Windows PowerShell ISE.</span></span>

- <span data-ttu-id="f3bdb-117">Om du använder bara Windows PowerShell ISE för att köra Windows PowerShell, sparar du alla objekt i ett av ISE-specifika profiler, till exempel CurrentUserCurrentHost profilen för Windows PowerShell ISE eller AllUsersCurrentHost profilen för Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="f3bdb-117">If you use only Windows PowerShell ISE to run Windows PowerShell, then save all your items in one of the ISE-specific profiles, such as the CurrentUserCurrentHost profile for Windows PowerShell ISE or the AllUsersCurrentHost profile for Windows PowerShell ISE.</span></span>

- <span data-ttu-id="f3bdb-118">Om du använder flera värden program för att köra Windows PowerShell, spara dina funktioner, alias, variabler och kommandon i en profil som påverkar alla värden program, till exempel CurrentUserAllHosts eller profilen för AllUsersAllHosts och spara ISE-specifika funktioner, t.ex. färger och teckensnitt anpassning i CurrentUserCurrentHost profilen för Windows PowerShell ISE-profil eller AllUsersCurrentHost-profil för Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="f3bdb-118">If you use multiple host programs to run Windows PowerShell, save your functions, aliases, variables, and commands in a profile that affects all host programs, such as the CurrentUserAllHosts or the AllUsersAllHosts profile, and save ISE-specific features, like color and font customization in the CurrentUserCurrentHost profile for Windows PowerShell ISE profile or the AllUsersCurrentHost profile for Windows PowerShell ISE.</span></span>

<span data-ttu-id="f3bdb-119">Här följer profiler som skapas och används i Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="f3bdb-119">The following are profiles that can be created and used in Windows PowerShell ISE.</span></span> <span data-ttu-id="f3bdb-120">Varje profil sparas till sin egen angiven sökväg.</span><span class="sxs-lookup"><span data-stu-id="f3bdb-120">Each profile is saved to its own specific path.</span></span>

| <span data-ttu-id="f3bdb-121">Profiltyp</span><span class="sxs-lookup"><span data-stu-id="f3bdb-121">Profile Type</span></span> | <span data-ttu-id="f3bdb-122">Profilsökvägen</span><span class="sxs-lookup"><span data-stu-id="f3bdb-122">Profile Path</span></span> |
| --- | --- |
| <span data-ttu-id="f3bdb-123">**Aktuell användare, PowerShell ISE**</span><span class="sxs-lookup"><span data-stu-id="f3bdb-123">**Current user, PowerShell ISE**</span></span>| <span data-ttu-id="f3bdb-124">`$PROFILE.CurrentUserCurrentHost`, eller `$PROFILE`</span><span class="sxs-lookup"><span data-stu-id="f3bdb-124">`$PROFILE.CurrentUserCurrentHost`, or `$PROFILE`</span></span> |
| <span data-ttu-id="f3bdb-125">**Alla användare, PowerShell ISE**</span><span class="sxs-lookup"><span data-stu-id="f3bdb-125">**All users, PowerShell ISE**</span></span>| `$PROFILE.AllUsersCurrentHost` |
| <span data-ttu-id="f3bdb-126">**Aktuell användare, alla värdar**</span><span class="sxs-lookup"><span data-stu-id="f3bdb-126">**Current user, All hosts**</span></span>| `$PROFILE.CurrentUserAllHosts` |
| <span data-ttu-id="f3bdb-127">**Alla användare, alla värdar**</span><span class="sxs-lookup"><span data-stu-id="f3bdb-127">**All users, All hosts**</span></span> | `$PROFILE.AllUsersAllHosts` |

## <a name="to-create-a-new-profile"></a><span data-ttu-id="f3bdb-128">Skapa en ny profil</span><span class="sxs-lookup"><span data-stu-id="f3bdb-128">To create a new profile</span></span>

<span data-ttu-id="f3bdb-129">Skapa en ny ”aktuella användare, Windows PowerShell ISE” profil, kör du följande kommando:</span><span class="sxs-lookup"><span data-stu-id="f3bdb-129">To create a new “Current user, Windows PowerShell ISE” profile, run this command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE ))
{ New-Item -Type File -Path $PROFILE -Force }
```

<span data-ttu-id="f3bdb-130">Att skapa en ny ”alla användare, Windows PowerShell ISE” profil, kör du följande kommando:</span><span class="sxs-lookup"><span data-stu-id="f3bdb-130">To create a new “All users, Windows PowerShell ISE” profile, run this command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE.AllUsersCurrentHost))
{ New-Item -Type File -Path $PROFILE.AllUsersCurrentHost -Force }
```

<span data-ttu-id="f3bdb-131">Om du vill skapa en ny ”aktuella användaren, alla är värd för” profil, kör du följande kommando:</span><span class="sxs-lookup"><span data-stu-id="f3bdb-131">To create a new “Current user, All Hosts” profile, run this command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE.CurrentUserAllHosts))
{ New-Item -Type File -Path $PROFILE.CurrentUserAllHosts -Force }
```

<span data-ttu-id="f3bdb-132">Om du vill skapa en ny profil för ”alla användare, alla är värd för”, skriver du:</span><span class="sxs-lookup"><span data-stu-id="f3bdb-132">To create a new “All users, All Hosts” profile, type:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE.AllUsersAllHosts))
{ New-Item -Type File -Path $PROFILE.AllUsersAllHosts -Force }
```

## <a name="to-edit-a-profile"></a><span data-ttu-id="f3bdb-133">Så här redigerar du en profil</span><span class="sxs-lookup"><span data-stu-id="f3bdb-133">To edit a profile</span></span>

1. <span data-ttu-id="f3bdb-134">Öppna profilen genom att köra kommandot psedit med variabeln som anger den profil du vill redigera.</span><span class="sxs-lookup"><span data-stu-id="f3bdb-134">To open the profile, run the command psedit with the variable that specifies the profile you want to edit.</span></span> <span data-ttu-id="f3bdb-135">Till exempel för att öppna den ”aktuella användaren, Windows PowerShell ISE” profil, skriver du: `psEdit $PROFILE`</span><span class="sxs-lookup"><span data-stu-id="f3bdb-135">For example, to open the “Current user, Windows PowerShell ISE” profile, type: `psEdit $PROFILE`</span></span>

2. <span data-ttu-id="f3bdb-136">Lägg till vissa objekt i din profil.</span><span class="sxs-lookup"><span data-stu-id="f3bdb-136">Add some items to your profile.</span></span> <span data-ttu-id="f3bdb-137">Här följer några exempel för att komma igång:</span><span class="sxs-lookup"><span data-stu-id="f3bdb-137">The following are a few examples to get you started:</span></span>

   - <span data-ttu-id="f3bdb-138">Ändra bakgrundsfärgen som används av konsolfönstret till blått, i filen Profiltyp: `$psISE.Options.OutputPaneBackground = 'blue'` .</span><span class="sxs-lookup"><span data-stu-id="f3bdb-138">To change the default background color of the Console Pane to blue, in the profile file type: `$psISE.Options.OutputPaneBackground = 'blue'` .</span></span> <span data-ttu-id="f3bdb-139">Läs mer om variabeln $psISE [Windows PowerShell ISE-Objektmodellreferens](object-model/The-ISE-Object-Model-Hierarchy.md).</span><span class="sxs-lookup"><span data-stu-id="f3bdb-139">For more information about the $psISE variable, see [Windows PowerShell ISE Object Model Reference](object-model/The-ISE-Object-Model-Hierarchy.md).</span></span>

   - <span data-ttu-id="f3bdb-140">Ändra storlek till 20, i filen Profiltyp: `$psISE.Options.FontSize =20`</span><span class="sxs-lookup"><span data-stu-id="f3bdb-140">To change font size to 20, in the profile file type: `$psISE.Options.FontSize =20`</span></span>

3. <span data-ttu-id="f3bdb-141">Spara fil för Konfigurationsprofil på den **filen** -menyn klickar du på **spara**.</span><span class="sxs-lookup"><span data-stu-id="f3bdb-141">To save your profile file, on the **File** menu, click **Save**.</span></span> <span data-ttu-id="f3bdb-142">Nästa gång du öppnar Windows PowerShell ISE tillämpas anpassningarna.</span><span class="sxs-lookup"><span data-stu-id="f3bdb-142">Next time you open the Windows PowerShell ISE, your customizations are applied.</span></span>

## <a name="see-also"></a><span data-ttu-id="f3bdb-143">Se även</span><span class="sxs-lookup"><span data-stu-id="f3bdb-143">See Also</span></span>

- [<span data-ttu-id="f3bdb-144">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="f3bdb-144">about_Profiles</span></span>](/powershell/module/microsoft.powershell.core/about/about_profiles)
- [<span data-ttu-id="f3bdb-145">Introduktion till Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="f3bdb-145">Introducing the Windows PowerShell ISE</span></span>](Introducing-the-Windows-PowerShell-ISE.md)
