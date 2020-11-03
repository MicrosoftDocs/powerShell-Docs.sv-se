---
description: Beskriver hur du skapar och använder en PowerShell-profil.
keywords: powershell,cmdlet
ms.date: 11/30/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_profiles?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Profiles
ms.openlocfilehash: d0457cf485528f675840161383aa24d0f63781fb
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270548"
---
# <a name="about-profiles"></a><span data-ttu-id="fdf27-104">Om profiler</span><span class="sxs-lookup"><span data-stu-id="fdf27-104">About Profiles</span></span>

## <a name="short-description"></a><span data-ttu-id="fdf27-105">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="fdf27-105">Short Description</span></span>
<span data-ttu-id="fdf27-106">Beskriver hur du skapar och använder en PowerShell-profil.</span><span class="sxs-lookup"><span data-stu-id="fdf27-106">Describes how to create and use a PowerShell profile.</span></span>

## <a name="long-description"></a><span data-ttu-id="fdf27-107">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="fdf27-107">Long Description</span></span>

<span data-ttu-id="fdf27-108">Du kan skapa en PowerShell-profil för att anpassa din miljö och lägga till sessionsbaserade element till varje PowerShell-session som du startar.</span><span class="sxs-lookup"><span data-stu-id="fdf27-108">You can create a PowerShell profile to customize your environment and to add session-specific elements to every PowerShell session that you start.</span></span>

<span data-ttu-id="fdf27-109">En PowerShell-profil är ett skript som körs när PowerShell startar.</span><span class="sxs-lookup"><span data-stu-id="fdf27-109">A PowerShell profile is a script that runs when PowerShell starts.</span></span> <span data-ttu-id="fdf27-110">Du kan använda profilen som ett inloggnings skript för att anpassa miljön.</span><span class="sxs-lookup"><span data-stu-id="fdf27-110">You can use the profile as a logon script to customize the environment.</span></span> <span data-ttu-id="fdf27-111">Du kan lägga till kommandon, alias, funktioner, variabler, snapin-moduler, moduler och PowerShell-enheter.</span><span class="sxs-lookup"><span data-stu-id="fdf27-111">You can add commands, aliases, functions, variables, snap-ins, modules, and PowerShell drives.</span></span> <span data-ttu-id="fdf27-112">Du kan också lägga till andra sessionsbaserade element i din profil så att de är tillgängliga i varje session utan att behöva importera eller återskapa dem.</span><span class="sxs-lookup"><span data-stu-id="fdf27-112">You can also add other session-specific elements to your profile so they are available in every session without having to import or re-create them.</span></span>

<span data-ttu-id="fdf27-113">PowerShell stöder flera profiler för användare och värd program.</span><span class="sxs-lookup"><span data-stu-id="fdf27-113">PowerShell supports several profiles for users and host programs.</span></span> <span data-ttu-id="fdf27-114">Det skapar dock inte profilerna åt dig.</span><span class="sxs-lookup"><span data-stu-id="fdf27-114">However, it does not create the profiles for you.</span></span> <span data-ttu-id="fdf27-115">I det här avsnittet beskrivs profilerna och hur du skapar och underhåller profiler på din dator.</span><span class="sxs-lookup"><span data-stu-id="fdf27-115">This topic describes the profiles, and it describes how to create and maintain profiles on your computer.</span></span>

<span data-ttu-id="fdf27-116">Den förklarar hur du använder parametern **noprofil** i PowerShell-konsolen (PowerShell.exe) för att starta PowerShell utan några profiler.</span><span class="sxs-lookup"><span data-stu-id="fdf27-116">It explains how to use the **NoProfile** parameter of the PowerShell console (PowerShell.exe) to start PowerShell without any profiles.</span></span> <span data-ttu-id="fdf27-117">Och det förklarar resultatet av körnings principen för PowerShell på profiler.</span><span class="sxs-lookup"><span data-stu-id="fdf27-117">And, it explains the effect of the PowerShell execution policy on profiles.</span></span>

## <a name="the-profile-files"></a><span data-ttu-id="fdf27-118">Profilmappar</span><span class="sxs-lookup"><span data-stu-id="fdf27-118">The Profile Files</span></span>

<span data-ttu-id="fdf27-119">PowerShell stöder flera profilmappar.</span><span class="sxs-lookup"><span data-stu-id="fdf27-119">PowerShell supports several profile files.</span></span> <span data-ttu-id="fdf27-120">Dessutom har PowerShell-värdprogram stöd för egna värdbaserade profiler.</span><span class="sxs-lookup"><span data-stu-id="fdf27-120">Also, PowerShell host programs can support their own host-specific profiles.</span></span>

<span data-ttu-id="fdf27-121">PowerShell-konsolen stöder till exempel följande grundläggande profilmappar.</span><span class="sxs-lookup"><span data-stu-id="fdf27-121">For example, the PowerShell console supports the following basic profile files.</span></span> <span data-ttu-id="fdf27-122">Profilerna anges i prioritetsordning.</span><span class="sxs-lookup"><span data-stu-id="fdf27-122">The profiles are listed in precedence order.</span></span> <span data-ttu-id="fdf27-123">Den första profilen har högst prioritet.</span><span class="sxs-lookup"><span data-stu-id="fdf27-123">The first profile has the highest precedence.</span></span>

|<span data-ttu-id="fdf27-124">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="fdf27-124">Description</span></span>               | <span data-ttu-id="fdf27-125">Sökväg</span><span class="sxs-lookup"><span data-stu-id="fdf27-125">Path</span></span>                                          |
|--------------------------|-----------------------------------------------|
|<span data-ttu-id="fdf27-126">Alla användare, alla värdar</span><span class="sxs-lookup"><span data-stu-id="fdf27-126">All Users, All Hosts</span></span>      |<span data-ttu-id="fdf27-127">$PSHOME \\Profile.ps1</span><span class="sxs-lookup"><span data-stu-id="fdf27-127">$PSHOME\\Profile.ps1</span></span>                           |
|<span data-ttu-id="fdf27-128">Alla användare, aktuell värd</span><span class="sxs-lookup"><span data-stu-id="fdf27-128">All Users, Current Host</span></span>   |<span data-ttu-id="fdf27-129">$PSHOME \\Microsoft.PowerShell_profile.ps1</span><span class="sxs-lookup"><span data-stu-id="fdf27-129">$PSHOME\\Microsoft.PowerShell_profile.ps1</span></span>      |
|<span data-ttu-id="fdf27-130">Aktuell användare, alla värdar</span><span class="sxs-lookup"><span data-stu-id="fdf27-130">Current User, All Hosts</span></span>   |<span data-ttu-id="fdf27-131">$Home \\ [My] Documents \\ PowerShell \\Profile.ps1</span><span class="sxs-lookup"><span data-stu-id="fdf27-131">$Home\\[My ]Documents\\PowerShell\\Profile.ps1</span></span> |
|<span data-ttu-id="fdf27-132">Aktuell användare, aktuell värd</span><span class="sxs-lookup"><span data-stu-id="fdf27-132">Current user, Current Host</span></span>|<span data-ttu-id="fdf27-133">$Home \\ [My] Documents \\ PowerShell</span><span class="sxs-lookup"><span data-stu-id="fdf27-133">$Home\\[My ]Documents\\PowerShell</span></span>\\<br><span data-ttu-id="fdf27-134">Microsoft.PowerShell_profile.ps1</span><span class="sxs-lookup"><span data-stu-id="fdf27-134">Microsoft.PowerShell_profile.ps1</span></span> |

<span data-ttu-id="fdf27-135">Profil Sök vägarna innehåller följande variabler:</span><span class="sxs-lookup"><span data-stu-id="fdf27-135">The profile paths include the following variables:</span></span>

- <span data-ttu-id="fdf27-136">`$PSHOME`Variabeln som lagrar installations katalogen för PowerShell</span><span class="sxs-lookup"><span data-stu-id="fdf27-136">The `$PSHOME` variable, which stores the installation directory for PowerShell</span></span>
- <span data-ttu-id="fdf27-137">`$Home`Variabeln som lagrar den aktuella användarens arbets katalog</span><span class="sxs-lookup"><span data-stu-id="fdf27-137">The `$Home` variable, which stores the current user's home directory</span></span>

<span data-ttu-id="fdf27-138">Dessutom kan andra program som är värdar för PowerShell stödja sina egna profiler.</span><span class="sxs-lookup"><span data-stu-id="fdf27-138">In addition, other programs that host PowerShell can support their own profiles.</span></span> <span data-ttu-id="fdf27-139">Visual Studio Code stöder till exempel följande tjänstspecifika profiler.</span><span class="sxs-lookup"><span data-stu-id="fdf27-139">For example, Visual Studio Code supports the following host-specific profiles.</span></span>

|<span data-ttu-id="fdf27-140">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="fdf27-140">Description</span></span>               | <span data-ttu-id="fdf27-141">Sökväg</span><span class="sxs-lookup"><span data-stu-id="fdf27-141">Path</span></span>                                     |
|--------------------------|------------------------------------------|
|<span data-ttu-id="fdf27-142">Alla användare, aktuell värd</span><span class="sxs-lookup"><span data-stu-id="fdf27-142">All users, Current Host</span></span>   |<span data-ttu-id="fdf27-143">$PSHOME \\Microsoft.VSCode_profile.ps1</span><span class="sxs-lookup"><span data-stu-id="fdf27-143">$PSHOME\\Microsoft.VSCode_profile.ps1</span></span>|
|<span data-ttu-id="fdf27-144">Aktuell användare, aktuell värd</span><span class="sxs-lookup"><span data-stu-id="fdf27-144">Current user, Current Host</span></span>|<span data-ttu-id="fdf27-145">$Home \\ [My] Documents \\ PowerShell</span><span class="sxs-lookup"><span data-stu-id="fdf27-145">$Home\\[My ]Documents\\PowerShell</span></span>\\<br><span data-ttu-id="fdf27-146">Microsoft.VSCode_profile.ps1</span><span class="sxs-lookup"><span data-stu-id="fdf27-146">Microsoft.VSCode_profile.ps1</span></span>|

<span data-ttu-id="fdf27-147">I PowerShell-hjälpen är profilen "CurrentUser, aktuell värd" profilen som oftast kallas för "din PowerShell-profil".</span><span class="sxs-lookup"><span data-stu-id="fdf27-147">In PowerShell Help, the "CurrentUser, Current Host" profile is the profile most often referred to as "your PowerShell profile".</span></span>

## <a name="the-profile-variable"></a><span data-ttu-id="fdf27-148">Variabeln $PROFILE</span><span class="sxs-lookup"><span data-stu-id="fdf27-148">The $PROFILE variable</span></span>

<span data-ttu-id="fdf27-149">Den `$PROFILE` automatiska variabeln lagrar Sök vägarna till de PowerShell-profiler som är tillgängliga i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="fdf27-149">The `$PROFILE` automatic variable stores the paths to the PowerShell profiles that are available in the current session.</span></span>

<span data-ttu-id="fdf27-150">Om du vill visa en profil Sök väg visar du värdet för `$PROFILE` variabeln.</span><span class="sxs-lookup"><span data-stu-id="fdf27-150">To view a profile path, display the value of the `$PROFILE` variable.</span></span> <span data-ttu-id="fdf27-151">Du kan också använda `$PROFILE` variabeln i ett kommando för att representera en sökväg.</span><span class="sxs-lookup"><span data-stu-id="fdf27-151">You can also use the `$PROFILE` variable in a command to represent a path.</span></span>

<span data-ttu-id="fdf27-152">`$PROFILE`Variabeln lagrar sökvägen till profilen "aktuell användare, aktuell värd".</span><span class="sxs-lookup"><span data-stu-id="fdf27-152">The `$PROFILE` variable stores the path to the "Current User, Current Host" profile.</span></span> <span data-ttu-id="fdf27-153">De andra profilerna sparas i antecknings egenskaperna för `$PROFILE` variabeln.</span><span class="sxs-lookup"><span data-stu-id="fdf27-153">The other profiles are saved in note properties of the `$PROFILE` variable.</span></span>

<span data-ttu-id="fdf27-154">`$PROFILE`Variabeln har till exempel följande värden i Windows PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="fdf27-154">For example, the `$PROFILE` variable has the following values in the Windows PowerShell console.</span></span>

|<span data-ttu-id="fdf27-155">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="fdf27-155">Description</span></span>                |<span data-ttu-id="fdf27-156">Name</span><span class="sxs-lookup"><span data-stu-id="fdf27-156">Name</span></span>                              |
|---------------------------|----------------------------------|
|<span data-ttu-id="fdf27-157">Aktuell användare, aktuell värd</span><span class="sxs-lookup"><span data-stu-id="fdf27-157">Current User, Current Host</span></span> |`$PROFILE`                        |
|<span data-ttu-id="fdf27-158">Aktuell användare, aktuell värd</span><span class="sxs-lookup"><span data-stu-id="fdf27-158">Current User, Current Host</span></span> |`$PROFILE.CurrentUserCurrentHost` |
|<span data-ttu-id="fdf27-159">Aktuell användare, alla värdar</span><span class="sxs-lookup"><span data-stu-id="fdf27-159">Current User, All Hosts</span></span>    |`$PROFILE.CurrentUserAllHosts`    |
|<span data-ttu-id="fdf27-160">Alla användare, aktuell värd</span><span class="sxs-lookup"><span data-stu-id="fdf27-160">All Users, Current Host</span></span>    |`$PROFILE.AllUsersCurrentHost`    |
|<span data-ttu-id="fdf27-161">Alla användare, alla värdar</span><span class="sxs-lookup"><span data-stu-id="fdf27-161">All Users, All Hosts</span></span>       |`$PROFILE.AllUsersAllHosts`       |

<span data-ttu-id="fdf27-162">Eftersom värdena i `$PROFILE` variabeln ändras för varje användare och i varje värd program, se till att du visar värdena för modellvariabler i varje PowerShell-värdprogram som du använder.</span><span class="sxs-lookup"><span data-stu-id="fdf27-162">Because the values of the `$PROFILE` variable change for each user and in each host application, ensure that you display the values of the profile variables in each PowerShell host application that you use.</span></span>

<span data-ttu-id="fdf27-163">Om du vill se de aktuella värdena för `$PROFILE` variabeln skriver du:</span><span class="sxs-lookup"><span data-stu-id="fdf27-163">To see the current values of the `$PROFILE` variable, type:</span></span>

```powershell
$PROFILE | Get-Member -Type NoteProperty
```

<span data-ttu-id="fdf27-164">Du kan använda `$PROFILE` variabeln i många kommandon.</span><span class="sxs-lookup"><span data-stu-id="fdf27-164">You can use the `$PROFILE` variable in many commands.</span></span> <span data-ttu-id="fdf27-165">Följande kommando öppnar exempelvis profilen "aktuell användare, aktuell värd" i anteckningar:</span><span class="sxs-lookup"><span data-stu-id="fdf27-165">For example, the following command opens the "Current User, Current Host" profile in Notepad:</span></span>

```powershell
notepad $PROFILE
```

<span data-ttu-id="fdf27-166">Följande kommando avgör om profilen "alla användare, alla värdar" har skapats på den lokala datorn:</span><span class="sxs-lookup"><span data-stu-id="fdf27-166">The following command determines whether an "All Users, All Hosts" profile has been created on the local computer:</span></span>

```powershell
Test-Path -Path $PROFILE.AllUsersAllHosts
```

## <a name="how-to-create-a-profile"></a><span data-ttu-id="fdf27-167">Så här skapar du en profil</span><span class="sxs-lookup"><span data-stu-id="fdf27-167">How to create a profile</span></span>

<span data-ttu-id="fdf27-168">Om du vill skapa en PowerShell-profil använder du följande kommando format:</span><span class="sxs-lookup"><span data-stu-id="fdf27-168">To create a PowerShell profile, use the following command format:</span></span>

```powershell
if (!(Test-Path -Path <profile-name>)) {
  New-Item -ItemType File -Path <profile-name> -Force
}
```

<span data-ttu-id="fdf27-169">Om du till exempel vill skapa en profil för den aktuella användaren i det aktuella PowerShell-värd programmet, använder du följande kommando:</span><span class="sxs-lookup"><span data-stu-id="fdf27-169">For example, to create a profile for the current user in the current PowerShell host application, use the following command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE)) {
  New-Item -ItemType File -Path $PROFILE -Force
}
```

<span data-ttu-id="fdf27-170">I det här kommandot `If` förhindrar instruktionen att du skriver över en befintlig profil.</span><span class="sxs-lookup"><span data-stu-id="fdf27-170">In this command, the `If` statement prevents you from overwriting an existing profile.</span></span> <span data-ttu-id="fdf27-171">Ersätt värdet för \<profile-path\> plats hållaren med sökvägen till den profil fil som du vill skapa.</span><span class="sxs-lookup"><span data-stu-id="fdf27-171">Replace the value of the \<profile-path\> placeholder with the path to the profile file that you want to create.</span></span>

> [!NOTE]
> <span data-ttu-id="fdf27-172">Om du vill skapa profiler för alla användare i Windows Vista och senare versioner av Windows startar du PowerShell med alternativet **Kör som administratör** .</span><span class="sxs-lookup"><span data-stu-id="fdf27-172">To create "All Users" profiles in Windows Vista and later versions of Windows, start PowerShell with the **Run as administrator** option.</span></span>

## <a name="how-to-edit-a-profile"></a><span data-ttu-id="fdf27-173">Så här redigerar du en profil</span><span class="sxs-lookup"><span data-stu-id="fdf27-173">How to edit a profile</span></span>

<span data-ttu-id="fdf27-174">Du kan öppna en PowerShell-profil i en text redigerare, till exempel Anteckningar.</span><span class="sxs-lookup"><span data-stu-id="fdf27-174">You can open any PowerShell profile in a text editor, such as Notepad.</span></span>

<span data-ttu-id="fdf27-175">Om du vill öppna profilen för den aktuella användaren i det aktuella programmet för PowerShell-värd i anteckningar, skriver du:</span><span class="sxs-lookup"><span data-stu-id="fdf27-175">To open the profile of the current user in the current PowerShell host application in Notepad, type:</span></span>

```powershell
notepad $PROFILE
```

<span data-ttu-id="fdf27-176">Ange profil namnet om du vill öppna andra profiler.</span><span class="sxs-lookup"><span data-stu-id="fdf27-176">To open other profiles, specify the profile name.</span></span> <span data-ttu-id="fdf27-177">Om du till exempel vill öppna profilen för alla användare av alla värd program skriver du:</span><span class="sxs-lookup"><span data-stu-id="fdf27-177">For example, to open the profile for all the users of all the host applications, type:</span></span>

```powershell
notepad $PROFILE.AllUsersAllHosts
```

<span data-ttu-id="fdf27-178">Om du vill tillämpa ändringarna sparar du profil filen och startar sedan om PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fdf27-178">To apply the changes, save the profile file, and then restart PowerShell.</span></span>

## <a name="how-to-choose-a-profile"></a><span data-ttu-id="fdf27-179">Så här väljer du en profil</span><span class="sxs-lookup"><span data-stu-id="fdf27-179">How to choose a profile</span></span>

<span data-ttu-id="fdf27-180">Om du använder flera värd program ska du placera de objekt som du använder i alla värd program i din `$PROFILE.CurrentUserAllHosts` profil.</span><span class="sxs-lookup"><span data-stu-id="fdf27-180">If you use multiple host applications, put the items that you use in all the host applications into your `$PROFILE.CurrentUserAllHosts` profile.</span></span> <span data-ttu-id="fdf27-181">Placera objekt som är specifika för ett värd program, till exempel ett kommando som anger bakgrunds färgen för ett värd program, i en profil som är specifik för värd programmet.</span><span class="sxs-lookup"><span data-stu-id="fdf27-181">Put items that are specific to a host application, such as a command that sets the background color for a host application, in a profile that is specific to that host application.</span></span>

<span data-ttu-id="fdf27-182">Om du är administratör som anpassar PowerShell för många användare följer du dessa rikt linjer:</span><span class="sxs-lookup"><span data-stu-id="fdf27-182">If you are an administrator who is customizing PowerShell for many users, follow these guidelines:</span></span>

- <span data-ttu-id="fdf27-183">Lagra gemensamma objekt i `$PROFILE.AllUsersAllHosts` profilen</span><span class="sxs-lookup"><span data-stu-id="fdf27-183">Store the common items in the `$PROFILE.AllUsersAllHosts` profile</span></span>
- <span data-ttu-id="fdf27-184">Lagra objekt som är specifika för ett värd program i `$PROFILE.AllUsersCurrentHost` profiler som är specifika för värd programmet</span><span class="sxs-lookup"><span data-stu-id="fdf27-184">Store items that are specific to a host application in `$PROFILE.AllUsersCurrentHost` profiles that are specific to the host application</span></span>
- <span data-ttu-id="fdf27-185">Lagra objekt för särskilda användare i användarspecifika profiler</span><span class="sxs-lookup"><span data-stu-id="fdf27-185">Store items for particular users in the user-specific profiles</span></span>

<span data-ttu-id="fdf27-186">Se till att kontrol lera om det finns någon speciell implementering av PowerShell-profiler i värd program dokumentationen.</span><span class="sxs-lookup"><span data-stu-id="fdf27-186">Be sure to check the host application documentation for any special implementation of PowerShell profiles.</span></span>

## <a name="how-to-use-a-profile"></a><span data-ttu-id="fdf27-187">Använda en profil</span><span class="sxs-lookup"><span data-stu-id="fdf27-187">How to use a profile</span></span>

<span data-ttu-id="fdf27-188">Många av de objekt som du skapar i PowerShell och de flesta kommandon som du kör påverkar bara den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="fdf27-188">Many of the items that you create in PowerShell and most commands that you run affect only the current session.</span></span> <span data-ttu-id="fdf27-189">När du slutar sessionen tas objekten bort.</span><span class="sxs-lookup"><span data-stu-id="fdf27-189">When you end the session, the items are deleted.</span></span>

<span data-ttu-id="fdf27-190">De sessionsbaserade kommandona och objekten innehåller variabler, inställningar för variabler, alias, funktioner, kommandon (förutom för [set-ExecutionPolicy](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)) och PowerShell-moduler som du lägger till i sessionen.</span><span class="sxs-lookup"><span data-stu-id="fdf27-190">The session-specific commands and items include variables, preference variables, aliases, functions, commands (except for [Set-ExecutionPolicy](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)), and PowerShell modules that you add to the session.</span></span>

<span data-ttu-id="fdf27-191">Om du vill spara objekten och göra dem tillgängliga i alla framtida sessioner, lägger du till dem i en PowerShell-profil.</span><span class="sxs-lookup"><span data-stu-id="fdf27-191">To save these items and make them available in all future sessions, add them to a PowerShell profile.</span></span>

<span data-ttu-id="fdf27-192">Ett annat vanligt användnings sätt för profiler är att spara ofta använda funktioner, alias och variabler.</span><span class="sxs-lookup"><span data-stu-id="fdf27-192">Another common use for profiles is to save frequently-used functions, aliases, and variables.</span></span> <span data-ttu-id="fdf27-193">När du sparar objekten i en profil kan du använda dem i en lämplig session utan att skapa om dem.</span><span class="sxs-lookup"><span data-stu-id="fdf27-193">When you save the items in a profile, you can use them in any applicable session without recreating them.</span></span>

## <a name="how-to-start-a-profile"></a><span data-ttu-id="fdf27-194">Så här startar du en profil</span><span class="sxs-lookup"><span data-stu-id="fdf27-194">How to start a profile</span></span>

<span data-ttu-id="fdf27-195">När du öppnar profil filen är den tom.</span><span class="sxs-lookup"><span data-stu-id="fdf27-195">When you open the profile file, it is blank.</span></span> <span data-ttu-id="fdf27-196">Du kan dock fylla det med variabler, alias och kommandon som du använder ofta.</span><span class="sxs-lookup"><span data-stu-id="fdf27-196">However, you can fill it with the variables, aliases, and commands that you use frequently.</span></span>

<span data-ttu-id="fdf27-197">Här är några förslag på hur du kan komma igång.</span><span class="sxs-lookup"><span data-stu-id="fdf27-197">Here are a few suggestions to get you started.</span></span>

### <a name="add-commands-that-make-it-easy-to-open-your-profile"></a><span data-ttu-id="fdf27-198">Lägg till kommandon som gör det enkelt att öppna din profil</span><span class="sxs-lookup"><span data-stu-id="fdf27-198">Add commands that make it easy to open your profile</span></span>

<span data-ttu-id="fdf27-199">Detta är särskilt användbart om du använder en annan profil än profilen "aktuell användare, aktuell värd".</span><span class="sxs-lookup"><span data-stu-id="fdf27-199">This is especially useful if you use a profile other than the "Current User, Current Host" profile.</span></span> <span data-ttu-id="fdf27-200">Lägg till exempel till följande kommando:</span><span class="sxs-lookup"><span data-stu-id="fdf27-200">For example, add the following command:</span></span>

```powershell
function Pro {notepad $PROFILE.CurrentUserAllHosts}
```

### <a name="add-a-function-that-lists-the-aliases-for-any-cmdlet"></a><span data-ttu-id="fdf27-201">Lägg till en funktion som visar alias för alla cmdletar</span><span class="sxs-lookup"><span data-stu-id="fdf27-201">Add a function that lists the aliases for any cmdlet</span></span>

```powershell
function Get-CmdletAlias ($cmdletname) {
  Get-Alias |
    Where-Object -FilterScript {$_.Definition -like "$cmdletname"} |
      Format-Table -Property Definition, Name -AutoSize
}
```

### <a name="customize-your-console"></a><span data-ttu-id="fdf27-202">Anpassa konsolen</span><span class="sxs-lookup"><span data-stu-id="fdf27-202">Customize your console</span></span>

```powershell
function Color-Console {
  $Host.ui.rawui.backgroundcolor = "white"
  $Host.ui.rawui.foregroundcolor = "black"
  $hosttime = (Get-ChildItem -Path $PSHOME\PowerShell.exe).CreationTime
  $hostversion="$($Host.Version.Major)`.$($Host.Version.Minor)"
  $Host.UI.RawUI.WindowTitle = "PowerShell $hostversion ($hosttime)"
  Clear-Host
}
Color-Console
```

### <a name="add-a-customized-powershell-prompt"></a><span data-ttu-id="fdf27-203">Lägg till en anpassad PowerShell-prompt</span><span class="sxs-lookup"><span data-stu-id="fdf27-203">Add a customized PowerShell prompt</span></span>

```powershell
function Prompt
{
$env:COMPUTERNAME + "\" + (Get-Location) + "> "
}
```

<span data-ttu-id="fdf27-204">Mer information om PowerShell-prompten finns [about_Prompts](about_Prompts.md).</span><span class="sxs-lookup"><span data-stu-id="fdf27-204">For more information about the PowerShell prompt, see [about_Prompts](about_Prompts.md).</span></span>

## <a name="the-noprofile-parameter"></a><span data-ttu-id="fdf27-205">Parametern noprofile</span><span class="sxs-lookup"><span data-stu-id="fdf27-205">The NoProfile parameter</span></span>

<span data-ttu-id="fdf27-206">Om du vill starta PowerShell utan profiler använder du parametern **noprofile** i **PowerShell.exe** , programmet som startar PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fdf27-206">To start PowerShell without profiles, use the **NoProfile** parameter of **PowerShell.exe** , the program that starts PowerShell.</span></span>

<span data-ttu-id="fdf27-207">Börja genom att öppna ett program som kan starta PowerShell, till exempel Cmd.exe eller PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fdf27-207">To begin, open a program that can start PowerShell, such as Cmd.exe or PowerShell itself.</span></span> <span data-ttu-id="fdf27-208">Du kan också använda dialog rutan Kör i Windows.</span><span class="sxs-lookup"><span data-stu-id="fdf27-208">You can also use the Run dialog box in Windows.</span></span>

<span data-ttu-id="fdf27-209">Ange:</span><span class="sxs-lookup"><span data-stu-id="fdf27-209">Type:</span></span>

```
PowerShell -NoProfile
```

<span data-ttu-id="fdf27-210">Om du vill ha en fullständig lista över parametrarna för PowerShell.exe skriver du:</span><span class="sxs-lookup"><span data-stu-id="fdf27-210">For a complete list of the parameters of PowerShell.exe, type:</span></span>

```
PowerShell -?
```

## <a name="profiles-and-execution-policy"></a><span data-ttu-id="fdf27-211">Profiler och körnings princip</span><span class="sxs-lookup"><span data-stu-id="fdf27-211">Profiles and Execution Policy</span></span>

<span data-ttu-id="fdf27-212">Körnings principen för PowerShell bestämmer delvis om du kan köra skript och läsa in konfigurationsfiler, inklusive profilerna.</span><span class="sxs-lookup"><span data-stu-id="fdf27-212">The PowerShell execution policy determines, in part, whether you can run scripts and load configuration files, including the profiles.</span></span> <span data-ttu-id="fdf27-213">Principen för **begränsade** körningar är standardinställningen.</span><span class="sxs-lookup"><span data-stu-id="fdf27-213">The **Restricted** execution policy is the default.</span></span> <span data-ttu-id="fdf27-214">Det förhindrar att alla skript körs, inklusive profilerna.</span><span class="sxs-lookup"><span data-stu-id="fdf27-214">It prevents all scripts from running, including the profiles.</span></span> <span data-ttu-id="fdf27-215">Om du använder principen "begränsad" körs inte profilen och dess innehåll tillämpas inte.</span><span class="sxs-lookup"><span data-stu-id="fdf27-215">If you use the "Restricted" policy, the profile does not run, and its contents are not applied.</span></span>

<span data-ttu-id="fdf27-216">Ett `Set-ExecutionPolicy` kommando anger och ändrar din körnings princip.</span><span class="sxs-lookup"><span data-stu-id="fdf27-216">A `Set-ExecutionPolicy` command sets and changes your execution policy.</span></span> <span data-ttu-id="fdf27-217">Det är ett av de få kommandon som gäller för alla PowerShell-sessioner eftersom värdet sparas i registret.</span><span class="sxs-lookup"><span data-stu-id="fdf27-217">It is one of the few commands that applies in all PowerShell sessions because the value is saved in the registry.</span></span> <span data-ttu-id="fdf27-218">Du behöver inte ange det när du öppnar-konsolen och du behöver inte lagra ett `Set-ExecutionPolicy` kommando i din profil.</span><span class="sxs-lookup"><span data-stu-id="fdf27-218">You do not have to set it when you open the console, and you do not have to store a `Set-ExecutionPolicy` command in your profile.</span></span>

## <a name="profiles-and-remote-sessions"></a><span data-ttu-id="fdf27-219">Profiler och fjärrsessioner</span><span class="sxs-lookup"><span data-stu-id="fdf27-219">Profiles and remote sessions</span></span>

<span data-ttu-id="fdf27-220">PowerShell-profiler körs inte automatiskt i fjärrsessioner, så kommandon som profiler lägger till finns inte i fjärrsessionen.</span><span class="sxs-lookup"><span data-stu-id="fdf27-220">PowerShell profiles are not run automatically in remote sessions, so the commands that the profiles add are not present in the remote session.</span></span> <span data-ttu-id="fdf27-221">Dessutom `$PROFILE` är den automatiska variabeln inte ifylld i fjärrsessioner.</span><span class="sxs-lookup"><span data-stu-id="fdf27-221">In addition, the `$PROFILE` automatic variable is not populated in remote sessions.</span></span>

<span data-ttu-id="fdf27-222">Om du vill köra en profil i en session använder du cmdleten [Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command) .</span><span class="sxs-lookup"><span data-stu-id="fdf27-222">To run a profile in a session, use the [Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command) cmdlet.</span></span>

<span data-ttu-id="fdf27-223">Följande kommando kör till exempel "aktuell användare, aktuell värd"-profil från den lokala datorn i sessionen i `$s` .</span><span class="sxs-lookup"><span data-stu-id="fdf27-223">For example, the following command runs the "Current user, Current Host" profile from the local computer in the session in `$s`.</span></span>

```powershell
Invoke-Command -Session $s -FilePath $PROFILE
```

<span data-ttu-id="fdf27-224">Följande kommando kör profilen "aktuell användare, aktuell värd" från fjärrdatorn i sessionen i `$s` .</span><span class="sxs-lookup"><span data-stu-id="fdf27-224">The following command runs the "Current user, Current Host" profile from the remote computer in the session in `$s`.</span></span> <span data-ttu-id="fdf27-225">Eftersom `$PROFILE` variabeln inte är ifylld använder kommandot den explicita sökvägen till profilen.</span><span class="sxs-lookup"><span data-stu-id="fdf27-225">Because the `$PROFILE` variable is not populated, the command uses the explicit path to the profile.</span></span> <span data-ttu-id="fdf27-226">Vi använder en punkt källa-operator så att profilen körs i det aktuella omfånget på fjärrdatorn och inte i det egna omfånget.</span><span class="sxs-lookup"><span data-stu-id="fdf27-226">We use dot sourcing operator so that the profile executes in the current scope on the remote computer and not in its own scope.</span></span>

```powershell
Invoke-Command -Session $s -ScriptBlock {
  . "$HOME\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1"
}
```

<span data-ttu-id="fdf27-227">När du har kört det här kommandot är de kommandon som profilen lägger till i sessionen tillgängliga i `$s` .</span><span class="sxs-lookup"><span data-stu-id="fdf27-227">After running this command, the commands that the profile adds to the session are available in `$s`.</span></span>

## <a name="see-also"></a><span data-ttu-id="fdf27-228">Se även</span><span class="sxs-lookup"><span data-stu-id="fdf27-228">See Also</span></span>

[<span data-ttu-id="fdf27-229">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="fdf27-229">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)

[<span data-ttu-id="fdf27-230">about_Functions</span><span class="sxs-lookup"><span data-stu-id="fdf27-230">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="fdf27-231">about_Prompts</span><span class="sxs-lookup"><span data-stu-id="fdf27-231">about_Prompts</span></span>](about_Prompts.md)

[<span data-ttu-id="fdf27-232">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="fdf27-232">about_Execution_Policies</span></span>](about_Execution_Policies.md)

[<span data-ttu-id="fdf27-233">about_Signing</span><span class="sxs-lookup"><span data-stu-id="fdf27-233">about_Signing</span></span>](about_Signing.md)

[<span data-ttu-id="fdf27-234">about_Remote</span><span class="sxs-lookup"><span data-stu-id="fdf27-234">about_Remote</span></span>](about_Remote.md)

[<span data-ttu-id="fdf27-235">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="fdf27-235">about_Scopes</span></span>](about_Scopes.md)

[<span data-ttu-id="fdf27-236">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="fdf27-236">Set-ExecutionPolicy</span></span>](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)
