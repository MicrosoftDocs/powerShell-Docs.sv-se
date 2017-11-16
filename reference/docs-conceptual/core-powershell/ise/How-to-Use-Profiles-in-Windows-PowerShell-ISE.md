---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: "Hur du använder profiler i Windows PowerShell ISE"
ms.assetid: 0219626a-6da5-4acc-b630-d058e8b29cc6
ms.openlocfilehash: f959aeb91eecc8056c91c56162ea9bff53537be9
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/08/2017
---
# <a name="how-to-use-profiles-in-windows-powershell-ise"></a><span data-ttu-id="83fba-103">Hur du använder profiler i Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="83fba-103">How to Use Profiles in Windows PowerShell ISE</span></span>
<span data-ttu-id="83fba-104">Det här avsnittet beskriver hur du använder profiler i Windows PowerShell® Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="83fba-104">This topic explains how to use Profiles in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="83fba-105">Vi rekommenderar att innan du utför uppgifterna i det här avsnittet bör du granska [about_Profiles [v4]](https://technet.microsoft.com/library/e1d9e30a-70cc-4f36-949f-fc7cd96b4054(v=wps.630)), eller i konsolfönstret, typ, `Get-Help about_Profiles` och tryck på **RETUR**.</span><span class="sxs-lookup"><span data-stu-id="83fba-105">We recommend that before performing the tasks in this section, you review [about_Profiles [v4]](https://technet.microsoft.com/library/e1d9e30a-70cc-4f36-949f-fc7cd96b4054(v=wps.630)), or in the Console Pane, type, `Get-Help about_Profiles` and press **ENTER**.</span></span>

<span data-ttu-id="83fba-106">En profil är ett Windows PowerShell ISE-skript som körs automatiskt när du startar en ny session.</span><span class="sxs-lookup"><span data-stu-id="83fba-106">A profile is a Windows PowerShell ISE script that runs automatically when you start a new session.</span></span>  <span data-ttu-id="83fba-107">Du kan skapa en eller flera Windows PowerShell-profiler för Windows PowerShell ISE och använda dem för att lägga till Konfigurera i Windows PowerShell eller Windows PowerShell ISE-miljön förberedde som du kan använda med variabler, alias, funktioner, och färger och teckensnitt inställningar som finns tillgängliga.</span><span class="sxs-lookup"><span data-stu-id="83fba-107">You can create one or more Windows PowerShell profiles for Windows PowerShell ISE and use them to add the configure the Windows PowerShell or Windows PowerShell ISE environment, preparing it for your use, with variables, aliases, functions, and color and font preferences that you want available.</span></span> <span data-ttu-id="83fba-108">En profil påverkar alla Windows PowerShell ISE-session som du startar.</span><span class="sxs-lookup"><span data-stu-id="83fba-108">A profile affects every Windows PowerShell ISE session that you start.</span></span>

> [!NOTE]
> <span data-ttu-id="83fba-109">Windows PowerShell-körningsprincipen avgör om du kan köra skript och läsa in en profil.</span><span class="sxs-lookup"><span data-stu-id="83fba-109">The Windows PowerShell execution policy determines whether you can run scripts and load a profile.</span></span> <span data-ttu-id="83fba-110">Standardprincipen för körning ”begränsade” förhindrar alla skript från att köras, inklusive profiler.</span><span class="sxs-lookup"><span data-stu-id="83fba-110">The default execution policy, “Restricted,” prevents all scripts from running, including profiles.</span></span> <span data-ttu-id="83fba-111">Om du använder principen ”begränsad” profilen kan inte läsas in.</span><span class="sxs-lookup"><span data-stu-id="83fba-111">If you use the “Restricted” policy, the profile cannot load.</span></span> <span data-ttu-id="83fba-112">Läs mer om körningsprincipen [about_Execution_Policies [v4]](https://technet.microsoft.com/library/347708dc-1515-4d74-978b-8334603472e6(v=wps.630)).</span><span class="sxs-lookup"><span data-stu-id="83fba-112">For more information about execution policy, see [about_Execution_Policies [v4]](https://technet.microsoft.com/library/347708dc-1515-4d74-978b-8334603472e6(v=wps.630)).</span></span>

## <a name="selecting-a-profile-to-use-in-the-windows-powershell-ise"></a><span data-ttu-id="83fba-113">Att välja en profil som används i Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="83fba-113">Selecting a profile to use in the Windows PowerShell ISE</span></span>
<span data-ttu-id="83fba-114">Windows PowerShell ISE stöder profiler för den aktuella användaren och alla användare.</span><span class="sxs-lookup"><span data-stu-id="83fba-114">Windows PowerShell ISE supports profiles for the current user and all users.</span></span> <span data-ttu-id="83fba-115">Det stöder också Windows PowerShell-profiler som gäller för alla värdar.</span><span class="sxs-lookup"><span data-stu-id="83fba-115">It also supports the Windows PowerShell profiles that apply to all hosts.</span></span>

<span data-ttu-id="83fba-116">Den profil som du använder bestäms av hur du använder Windows PowerShell och Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="83fba-116">The profile that you use is determined by how you use Windows PowerShell and Windows PowerShell ISE.</span></span>

- <span data-ttu-id="83fba-117">Om du använder endast Windows PowerShell ISE för att köra Windows PowerShell, sparar du alla objekt i något av ISE-specifika profiler, till exempel CurrentUserCurrentHost profilen för Windows PowerShell ISE eller AllUsersCurrentHost profilen för Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="83fba-117">If you use only Windows PowerShell ISE to run Windows PowerShell, then save all your items in one of the ISE-specific profiles, such as the CurrentUserCurrentHost profile for Windows PowerShell ISE or the AllUsersCurrentHost profile for Windows PowerShell ISE.</span></span>

- <span data-ttu-id="83fba-118">Om du använder flera värden program för att köra Windows PowerShell, spara dina funktioner, alias, variabler och kommandon i en profil som påverkar alla värden program, till exempel CurrentUserAllHosts eller profilen för AllUsersAllHosts och spara ISE-specifika funktioner, t.ex. färger och teckensnitt anpassning i CurrentUserCurrentHost profilen för Windows PowerShell ISE profil eller AllUsersCurrentHost-profil för Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="83fba-118">If you use multiple host programs to run Windows PowerShell, save your functions, aliases, variables, and commands in a profile that affects all host programs, such as the CurrentUserAllHosts or the AllUsersAllHosts profile, and save ISE-specific features, like color and font customization in the CurrentUserCurrentHost profile for Windows PowerShell ISE profile or the AllUsersCurrentHost profile for Windows PowerShell ISE.</span></span>

<span data-ttu-id="83fba-119">Följande är profiler som skapas och används i Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="83fba-119">The following are profiles that can be created and used in Windows PowerShell ISE.</span></span> <span data-ttu-id="83fba-120">Varje profil sparas till sin egen angiven sökväg.</span><span class="sxs-lookup"><span data-stu-id="83fba-120">Each profile is saved to its own specific path.</span></span>

| <span data-ttu-id="83fba-121">Profiltyp</span><span class="sxs-lookup"><span data-stu-id="83fba-121">Profile Type</span></span> | <span data-ttu-id="83fba-122">Profilsökvägen</span><span class="sxs-lookup"><span data-stu-id="83fba-122">Profile Path</span></span> |
| --- | --- |
| <span data-ttu-id="83fba-123">**Aktuell användare, PowerShell ISE**</span><span class="sxs-lookup"><span data-stu-id="83fba-123">**Current user, PowerShell ISE**</span></span>| <span data-ttu-id="83fba-124">`$PROFILE.CurrentUserCurrentHost`, eller`$PROFILE`</span><span class="sxs-lookup"><span data-stu-id="83fba-124">`$PROFILE.CurrentUserCurrentHost`, or `$PROFILE`</span></span> |
| <span data-ttu-id="83fba-125">**Alla användare, PowerShell ISE**</span><span class="sxs-lookup"><span data-stu-id="83fba-125">**All users, PowerShell ISE**</span></span>| `$PROFILE.AllUsersCurrentHost` |
| <span data-ttu-id="83fba-126">**Aktuell användare, alla värdar**</span><span class="sxs-lookup"><span data-stu-id="83fba-126">**Current user, All hosts**</span></span>| `$PROFILE.CurrentUserAllHosts` |
| <span data-ttu-id="83fba-127">**Alla användare, alla värdar**</span><span class="sxs-lookup"><span data-stu-id="83fba-127">**All users, All hosts**</span></span> | `$PROFILE.AllUsersAllHosts` |

## <a name="to-create-a-new-profile"></a><span data-ttu-id="83fba-128">Skapa en ny profil</span><span class="sxs-lookup"><span data-stu-id="83fba-128">To create a new profile</span></span>
<span data-ttu-id="83fba-129">Skapa en ny ”aktuell användare, Windows PowerShell ISE” profil, köra det här kommandot:</span><span class="sxs-lookup"><span data-stu-id="83fba-129">To create a new “Current user, Windows PowerShell ISE” profile, run this command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE )) 
{ New-Item -Type File -Path $PROFILE -Force }
```

<span data-ttu-id="83fba-130">Att skapa en ny ”alla användare, Windows PowerShell ISE” profil, köra det här kommandot:</span><span class="sxs-lookup"><span data-stu-id="83fba-130">To create a new “All users, Windows PowerShell ISE” profile, run this command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE.AllUsersCurrentHost)) 
{ New-Item -Type File -Path $PROFILE.AllUsersCurrentHost -Force }
```

<span data-ttu-id="83fba-131">Om du vill skapa en ny profil ”aktuell användare, alla värd”, kör du kommandot:</span><span class="sxs-lookup"><span data-stu-id="83fba-131">To create a new “Current user, All Hosts” profile, run this command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE.CurrentUserAllHosts)) 
{ New-Item -Type File -Path $PROFILE.CurrentUserAllHosts -Force }
```

<span data-ttu-id="83fba-132">Om du vill skapa en ny profil för ”alla användare alla värd”, skriver du:</span><span class="sxs-lookup"><span data-stu-id="83fba-132">To create a new “All users, All Hosts” profile, type:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE.AllUsersAllHosts)) 
{ New-Item -Type File -Path $PROFILE.AllUsersAllHosts -Force }
```

## <a name="to-edit-a-profile"></a><span data-ttu-id="83fba-133">Så här redigerar du en profil</span><span class="sxs-lookup"><span data-stu-id="83fba-133">To edit a profile</span></span>

1. <span data-ttu-id="83fba-134">Om du vill öppna profilen kör du kommandot psedit med variabeln som anger den profil som du vill redigera.</span><span class="sxs-lookup"><span data-stu-id="83fba-134">To open the profile, run the command psedit with the variable that specifies the profile you want to edit.</span></span> <span data-ttu-id="83fba-135">Till exempel för att öppna den ”aktuella användaren, Windows PowerShell ISE” profil, skriver du:`psEdit $PROFILE`</span><span class="sxs-lookup"><span data-stu-id="83fba-135">For example, to open the “Current user, Windows PowerShell ISE” profile, type: `psEdit $PROFILE`</span></span>

2. <span data-ttu-id="83fba-136">Lägg till vissa objekt i din profil.</span><span class="sxs-lookup"><span data-stu-id="83fba-136">Add some items to your profile.</span></span> <span data-ttu-id="83fba-137">Följande är några exempel för att komma igång:</span><span class="sxs-lookup"><span data-stu-id="83fba-137">The following are a few examples to get you started:</span></span>

    -   <span data-ttu-id="83fba-138">Ändra bakgrundsfärgen som används i konsolfönstret till blått i filen profiltypen: `$psISE.Options.OutputPaneBackground = 'blue'` .</span><span class="sxs-lookup"><span data-stu-id="83fba-138">To change the default background color of the Console Pane to blue, in the profile file type: `$psISE.Options.OutputPaneBackground = 'blue'` .</span></span> <span data-ttu-id="83fba-139">Läs mer om variabeln $psISE [modell för Windows PowerShell ISE objektreferens](The-ISE-Object-Model-Hierarchy.md).</span><span class="sxs-lookup"><span data-stu-id="83fba-139">For more information about the $psISE variable, see [Windows PowerShell ISE Object Model Reference](The-ISE-Object-Model-Hierarchy.md).</span></span>

    -   <span data-ttu-id="83fba-140">Ändra storlek till 20 i filtypen profil:`$psISE.Options.FontSize =20`</span><span class="sxs-lookup"><span data-stu-id="83fba-140">To change font size to 20, in the profile file type: `$psISE.Options.FontSize =20`</span></span>

3. <span data-ttu-id="83fba-141">Spara profilfilen på den **filen** -menyn klickar du på **spara**.</span><span class="sxs-lookup"><span data-stu-id="83fba-141">To save your profile file, on the **File** menu, click **Save**.</span></span> <span data-ttu-id="83fba-142">Nästa gång du öppnar Windows PowerShell ISE tillämpas anpassningarna.</span><span class="sxs-lookup"><span data-stu-id="83fba-142">Next time you open the Windows PowerShell ISE, your customizations are applied.</span></span>

## <a name="see-also"></a><span data-ttu-id="83fba-143">Se även</span><span class="sxs-lookup"><span data-stu-id="83fba-143">See Also</span></span>
- <span data-ttu-id="83fba-144">[about_Profiles [v4]](https://technet.microsoft.com/library/e1d9e30a-70cc-4f36-949f-fc7cd96b4054(v=wps.630))</span><span class="sxs-lookup"><span data-stu-id="83fba-144">[about_Profiles [v4]](https://technet.microsoft.com/library/e1d9e30a-70cc-4f36-949f-fc7cd96b4054(v=wps.630))</span></span>
- [<span data-ttu-id="83fba-145">Med hjälp av Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="83fba-145">Using the Windows PowerShell ISE</span></span>](Using-the-Windows-PowerShell-ISE.md)

