---
description: Beskriver hur du skapar och använder en PowerShell-profil.
Locale: en-US
ms.date: 11/30/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_profiles?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Profiles
ms.openlocfilehash: 3fe32a83ad1a63d64d293559c79f1465828d0a0a
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/12/2021
ms.locfileid: "103194995"
---
# <a name="about-profiles"></a><span data-ttu-id="f2763-103">Om profiler</span><span class="sxs-lookup"><span data-stu-id="f2763-103">About Profiles</span></span>

## <a name="short-description"></a><span data-ttu-id="f2763-104">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="f2763-104">Short Description</span></span>
<span data-ttu-id="f2763-105">Beskriver hur du skapar och använder en PowerShell-profil.</span><span class="sxs-lookup"><span data-stu-id="f2763-105">Describes how to create and use a PowerShell profile.</span></span>

## <a name="long-description"></a><span data-ttu-id="f2763-106">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="f2763-106">Long Description</span></span>

<span data-ttu-id="f2763-107">Du kan skapa en PowerShell-profil för att anpassa din miljö och lägga till sessionsbaserade element till varje PowerShell-session som du startar.</span><span class="sxs-lookup"><span data-stu-id="f2763-107">You can create a PowerShell profile to customize your environment and to add session-specific elements to every PowerShell session that you start.</span></span>

<span data-ttu-id="f2763-108">En PowerShell-profil är ett skript som körs när PowerShell startar.</span><span class="sxs-lookup"><span data-stu-id="f2763-108">A PowerShell profile is a script that runs when PowerShell starts.</span></span> <span data-ttu-id="f2763-109">Du kan använda profilen som ett inloggnings skript för att anpassa miljön.</span><span class="sxs-lookup"><span data-stu-id="f2763-109">You can use the profile as a logon script to customize the environment.</span></span> <span data-ttu-id="f2763-110">Du kan lägga till kommandon, alias, funktioner, variabler, snapin-moduler, moduler och PowerShell-enheter.</span><span class="sxs-lookup"><span data-stu-id="f2763-110">You can add commands, aliases, functions, variables, snap-ins, modules, and PowerShell drives.</span></span> <span data-ttu-id="f2763-111">Du kan också lägga till andra sessionsbaserade element i din profil så att de är tillgängliga i varje session utan att behöva importera eller återskapa dem.</span><span class="sxs-lookup"><span data-stu-id="f2763-111">You can also add other session-specific elements to your profile so they are available in every session without having to import or re-create them.</span></span>

<span data-ttu-id="f2763-112">PowerShell stöder flera profiler för användare och värd program.</span><span class="sxs-lookup"><span data-stu-id="f2763-112">PowerShell supports several profiles for users and host programs.</span></span> <span data-ttu-id="f2763-113">Det skapar dock inte profilerna åt dig.</span><span class="sxs-lookup"><span data-stu-id="f2763-113">However, it does not create the profiles for you.</span></span> <span data-ttu-id="f2763-114">I det här avsnittet beskrivs profilerna och hur du skapar och underhåller profiler på din dator.</span><span class="sxs-lookup"><span data-stu-id="f2763-114">This topic describes the profiles, and it describes how to create and maintain profiles on your computer.</span></span>

<span data-ttu-id="f2763-115">Den förklarar hur du använder parametern **noprofil** i PowerShell-konsolen (PowerShell.exe) för att starta PowerShell utan några profiler.</span><span class="sxs-lookup"><span data-stu-id="f2763-115">It explains how to use the **NoProfile** parameter of the PowerShell console (PowerShell.exe) to start PowerShell without any profiles.</span></span> <span data-ttu-id="f2763-116">Och det förklarar resultatet av körnings principen för PowerShell på profiler.</span><span class="sxs-lookup"><span data-stu-id="f2763-116">And, it explains the effect of the PowerShell execution policy on profiles.</span></span>

## <a name="the-profile-files"></a><span data-ttu-id="f2763-117">Profilmappar</span><span class="sxs-lookup"><span data-stu-id="f2763-117">The Profile Files</span></span>

<span data-ttu-id="f2763-118">PowerShell stöder flera profilmappar.</span><span class="sxs-lookup"><span data-stu-id="f2763-118">PowerShell supports several profile files.</span></span> <span data-ttu-id="f2763-119">Dessutom har PowerShell-värdprogram stöd för egna värdbaserade profiler.</span><span class="sxs-lookup"><span data-stu-id="f2763-119">Also, PowerShell host programs can support their own host-specific profiles.</span></span>

<span data-ttu-id="f2763-120">PowerShell-konsolen stöder till exempel följande grundläggande profilmappar.</span><span class="sxs-lookup"><span data-stu-id="f2763-120">For example, the PowerShell console supports the following basic profile files.</span></span> <span data-ttu-id="f2763-121">Profilerna anges i prioritetsordning.</span><span class="sxs-lookup"><span data-stu-id="f2763-121">The profiles are listed in precedence order.</span></span> <span data-ttu-id="f2763-122">Den första profilen har högst prioritet.</span><span class="sxs-lookup"><span data-stu-id="f2763-122">The first profile has the highest precedence.</span></span>

|<span data-ttu-id="f2763-123">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="f2763-123">Description</span></span>               | <span data-ttu-id="f2763-124">Sökväg</span><span class="sxs-lookup"><span data-stu-id="f2763-124">Path</span></span>                                          |
|--------------------------|-----------------------------------------------|
|<span data-ttu-id="f2763-125">Alla användare, alla värdar</span><span class="sxs-lookup"><span data-stu-id="f2763-125">All Users, All Hosts</span></span>      |<span data-ttu-id="f2763-126">$PSHOME \\Profile.ps1</span><span class="sxs-lookup"><span data-stu-id="f2763-126">$PSHOME\\Profile.ps1</span></span>                           |
|<span data-ttu-id="f2763-127">Alla användare, aktuell värd</span><span class="sxs-lookup"><span data-stu-id="f2763-127">All Users, Current Host</span></span>   |<span data-ttu-id="f2763-128">$PSHOME \\Microsoft.PowerShell_profile.ps1</span><span class="sxs-lookup"><span data-stu-id="f2763-128">$PSHOME\\Microsoft.PowerShell_profile.ps1</span></span>      |
|<span data-ttu-id="f2763-129">Aktuell användare, alla värdar</span><span class="sxs-lookup"><span data-stu-id="f2763-129">Current User, All Hosts</span></span>   |<span data-ttu-id="f2763-130">$Home \\ [My] Documents \\ PowerShell \\Profile.ps1</span><span class="sxs-lookup"><span data-stu-id="f2763-130">$Home\\[My ]Documents\\PowerShell\\Profile.ps1</span></span> |
|<span data-ttu-id="f2763-131">Aktuell användare, aktuell värd</span><span class="sxs-lookup"><span data-stu-id="f2763-131">Current user, Current Host</span></span>|<span data-ttu-id="f2763-132">$Home \\ [My] Documents \\ PowerShell</span><span class="sxs-lookup"><span data-stu-id="f2763-132">$Home\\[My ]Documents\\PowerShell</span></span>\\<br><span data-ttu-id="f2763-133">Microsoft.PowerShell_profile.ps1</span><span class="sxs-lookup"><span data-stu-id="f2763-133">Microsoft.PowerShell_profile.ps1</span></span> |

<span data-ttu-id="f2763-134">Profil Sök vägarna innehåller följande variabler:</span><span class="sxs-lookup"><span data-stu-id="f2763-134">The profile paths include the following variables:</span></span>

- <span data-ttu-id="f2763-135">`$PSHOME`Variabeln som lagrar installations katalogen för PowerShell</span><span class="sxs-lookup"><span data-stu-id="f2763-135">The `$PSHOME` variable, which stores the installation directory for PowerShell</span></span>
- <span data-ttu-id="f2763-136">`$Home`Variabeln som lagrar den aktuella användarens arbets katalog</span><span class="sxs-lookup"><span data-stu-id="f2763-136">The `$Home` variable, which stores the current user's home directory</span></span>

<span data-ttu-id="f2763-137">Dessutom kan andra program som är värdar för PowerShell stödja sina egna profiler.</span><span class="sxs-lookup"><span data-stu-id="f2763-137">In addition, other programs that host PowerShell can support their own profiles.</span></span> <span data-ttu-id="f2763-138">Visual Studio Code stöder till exempel följande tjänstspecifika profiler.</span><span class="sxs-lookup"><span data-stu-id="f2763-138">For example, Visual Studio Code supports the following host-specific profiles.</span></span>

|<span data-ttu-id="f2763-139">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="f2763-139">Description</span></span>               | <span data-ttu-id="f2763-140">Sökväg</span><span class="sxs-lookup"><span data-stu-id="f2763-140">Path</span></span>                                     |
|--------------------------|------------------------------------------|
|<span data-ttu-id="f2763-141">Alla användare, aktuell värd</span><span class="sxs-lookup"><span data-stu-id="f2763-141">All users, Current Host</span></span>   |<span data-ttu-id="f2763-142">$PSHOME \\Microsoft.VSCode_profile.ps1</span><span class="sxs-lookup"><span data-stu-id="f2763-142">$PSHOME\\Microsoft.VSCode_profile.ps1</span></span>|
|<span data-ttu-id="f2763-143">Aktuell användare, aktuell värd</span><span class="sxs-lookup"><span data-stu-id="f2763-143">Current user, Current Host</span></span>|<span data-ttu-id="f2763-144">$Home \\ [My] Documents \\ PowerShell</span><span class="sxs-lookup"><span data-stu-id="f2763-144">$Home\\[My ]Documents\\PowerShell</span></span>\\<br><span data-ttu-id="f2763-145">Microsoft.VSCode_profile.ps1</span><span class="sxs-lookup"><span data-stu-id="f2763-145">Microsoft.VSCode_profile.ps1</span></span>|

<span data-ttu-id="f2763-146">I PowerShell-hjälpen är profilen "CurrentUser, aktuell värd" profilen som oftast kallas för "din PowerShell-profil".</span><span class="sxs-lookup"><span data-stu-id="f2763-146">In PowerShell Help, the "CurrentUser, Current Host" profile is the profile most often referred to as "your PowerShell profile".</span></span>

## <a name="the-profile-variable"></a><span data-ttu-id="f2763-147">Variabeln $PROFILE</span><span class="sxs-lookup"><span data-stu-id="f2763-147">The $PROFILE variable</span></span>

<span data-ttu-id="f2763-148">Den `$PROFILE` automatiska variabeln lagrar Sök vägarna till de PowerShell-profiler som är tillgängliga i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="f2763-148">The `$PROFILE` automatic variable stores the paths to the PowerShell profiles that are available in the current session.</span></span>

<span data-ttu-id="f2763-149">Om du vill visa en profil Sök väg visar du värdet för `$PROFILE` variabeln.</span><span class="sxs-lookup"><span data-stu-id="f2763-149">To view a profile path, display the value of the `$PROFILE` variable.</span></span> <span data-ttu-id="f2763-150">Du kan också använda `$PROFILE` variabeln i ett kommando för att representera en sökväg.</span><span class="sxs-lookup"><span data-stu-id="f2763-150">You can also use the `$PROFILE` variable in a command to represent a path.</span></span>

<span data-ttu-id="f2763-151">`$PROFILE`Variabeln lagrar sökvägen till profilen "aktuell användare, aktuell värd".</span><span class="sxs-lookup"><span data-stu-id="f2763-151">The `$PROFILE` variable stores the path to the "Current User, Current Host" profile.</span></span> <span data-ttu-id="f2763-152">De andra profilerna sparas i antecknings egenskaperna för `$PROFILE` variabeln.</span><span class="sxs-lookup"><span data-stu-id="f2763-152">The other profiles are saved in note properties of the `$PROFILE` variable.</span></span>

<span data-ttu-id="f2763-153">`$PROFILE`Variabeln har till exempel följande värden i Windows PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="f2763-153">For example, the `$PROFILE` variable has the following values in the Windows PowerShell console.</span></span>

|<span data-ttu-id="f2763-154">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="f2763-154">Description</span></span>                |<span data-ttu-id="f2763-155">Name</span><span class="sxs-lookup"><span data-stu-id="f2763-155">Name</span></span>                              |
|---------------------------|----------------------------------|
|<span data-ttu-id="f2763-156">Aktuell användare, aktuell värd</span><span class="sxs-lookup"><span data-stu-id="f2763-156">Current User, Current Host</span></span> |`$PROFILE`                        |
|<span data-ttu-id="f2763-157">Aktuell användare, aktuell värd</span><span class="sxs-lookup"><span data-stu-id="f2763-157">Current User, Current Host</span></span> |`$PROFILE.CurrentUserCurrentHost` |
|<span data-ttu-id="f2763-158">Aktuell användare, alla värdar</span><span class="sxs-lookup"><span data-stu-id="f2763-158">Current User, All Hosts</span></span>    |`$PROFILE.CurrentUserAllHosts`    |
|<span data-ttu-id="f2763-159">Alla användare, aktuell värd</span><span class="sxs-lookup"><span data-stu-id="f2763-159">All Users, Current Host</span></span>    |`$PROFILE.AllUsersCurrentHost`    |
|<span data-ttu-id="f2763-160">Alla användare, alla värdar</span><span class="sxs-lookup"><span data-stu-id="f2763-160">All Users, All Hosts</span></span>       |`$PROFILE.AllUsersAllHosts`       |

<span data-ttu-id="f2763-161">Eftersom värdena i `$PROFILE` variabeln ändras för varje användare och i varje värd program, se till att du visar värdena för modellvariabler i varje PowerShell-värdprogram som du använder.</span><span class="sxs-lookup"><span data-stu-id="f2763-161">Because the values of the `$PROFILE` variable change for each user and in each host application, ensure that you display the values of the profile variables in each PowerShell host application that you use.</span></span>

<span data-ttu-id="f2763-162">Om du vill se de aktuella värdena för `$PROFILE` variabeln skriver du:</span><span class="sxs-lookup"><span data-stu-id="f2763-162">To see the current values of the `$PROFILE` variable, type:</span></span>

```powershell
$PROFILE | Get-Member -Type NoteProperty
```

<span data-ttu-id="f2763-163">Du kan använda `$PROFILE` variabeln i många kommandon.</span><span class="sxs-lookup"><span data-stu-id="f2763-163">You can use the `$PROFILE` variable in many commands.</span></span> <span data-ttu-id="f2763-164">Följande kommando öppnar exempelvis profilen "aktuell användare, aktuell värd" i anteckningar:</span><span class="sxs-lookup"><span data-stu-id="f2763-164">For example, the following command opens the "Current User, Current Host" profile in Notepad:</span></span>

```powershell
notepad $PROFILE
```

<span data-ttu-id="f2763-165">Följande kommando avgör om profilen "alla användare, alla värdar" har skapats på den lokala datorn:</span><span class="sxs-lookup"><span data-stu-id="f2763-165">The following command determines whether an "All Users, All Hosts" profile has been created on the local computer:</span></span>

```powershell
Test-Path -Path $PROFILE.AllUsersAllHosts
```

## <a name="how-to-create-a-profile"></a><span data-ttu-id="f2763-166">Så här skapar du en profil</span><span class="sxs-lookup"><span data-stu-id="f2763-166">How to create a profile</span></span>

<span data-ttu-id="f2763-167">Om du vill skapa en PowerShell-profil använder du följande kommando format:</span><span class="sxs-lookup"><span data-stu-id="f2763-167">To create a PowerShell profile, use the following command format:</span></span>

```powershell
if (!(Test-Path -Path <profile-name>)) {
  New-Item -ItemType File -Path <profile-name> -Force
}
```

<span data-ttu-id="f2763-168">Om du till exempel vill skapa en profil för den aktuella användaren i det aktuella PowerShell-värd programmet, använder du följande kommando:</span><span class="sxs-lookup"><span data-stu-id="f2763-168">For example, to create a profile for the current user in the current PowerShell host application, use the following command:</span></span>

```powershell
if (!(Test-Path -Path $PROFILE)) {
  New-Item -ItemType File -Path $PROFILE -Force
}
```

<span data-ttu-id="f2763-169">I det här kommandot `If` förhindrar instruktionen att du skriver över en befintlig profil.</span><span class="sxs-lookup"><span data-stu-id="f2763-169">In this command, the `If` statement prevents you from overwriting an existing profile.</span></span> <span data-ttu-id="f2763-170">Ersätt värdet för \<profile-path\> plats hållaren med sökvägen till den profil fil som du vill skapa.</span><span class="sxs-lookup"><span data-stu-id="f2763-170">Replace the value of the \<profile-path\> placeholder with the path to the profile file that you want to create.</span></span>

> [!NOTE]
> <span data-ttu-id="f2763-171">Om du vill skapa profiler för alla användare i Windows Vista och senare versioner av Windows startar du PowerShell med alternativet **Kör som administratör** .</span><span class="sxs-lookup"><span data-stu-id="f2763-171">To create "All Users" profiles in Windows Vista and later versions of Windows, start PowerShell with the **Run as administrator** option.</span></span>

## <a name="how-to-edit-a-profile"></a><span data-ttu-id="f2763-172">Så här redigerar du en profil</span><span class="sxs-lookup"><span data-stu-id="f2763-172">How to edit a profile</span></span>

<span data-ttu-id="f2763-173">Du kan öppna en PowerShell-profil i en text redigerare, till exempel Anteckningar.</span><span class="sxs-lookup"><span data-stu-id="f2763-173">You can open any PowerShell profile in a text editor, such as Notepad.</span></span>

<span data-ttu-id="f2763-174">Om du vill öppna profilen för den aktuella användaren i det aktuella programmet för PowerShell-värd i anteckningar, skriver du:</span><span class="sxs-lookup"><span data-stu-id="f2763-174">To open the profile of the current user in the current PowerShell host application in Notepad, type:</span></span>

```powershell
notepad $PROFILE
```

<span data-ttu-id="f2763-175">Ange profil namnet om du vill öppna andra profiler.</span><span class="sxs-lookup"><span data-stu-id="f2763-175">To open other profiles, specify the profile name.</span></span> <span data-ttu-id="f2763-176">Om du till exempel vill öppna profilen för alla användare av alla värd program skriver du:</span><span class="sxs-lookup"><span data-stu-id="f2763-176">For example, to open the profile for all the users of all the host applications, type:</span></span>

```powershell
notepad $PROFILE.AllUsersAllHosts
```

<span data-ttu-id="f2763-177">Om du vill tillämpa ändringarna sparar du profil filen och startar sedan om PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f2763-177">To apply the changes, save the profile file, and then restart PowerShell.</span></span>

## <a name="how-to-choose-a-profile"></a><span data-ttu-id="f2763-178">Så här väljer du en profil</span><span class="sxs-lookup"><span data-stu-id="f2763-178">How to choose a profile</span></span>

<span data-ttu-id="f2763-179">Om du använder flera värd program ska du placera de objekt som du använder i alla värd program i din `$PROFILE.CurrentUserAllHosts` profil.</span><span class="sxs-lookup"><span data-stu-id="f2763-179">If you use multiple host applications, put the items that you use in all the host applications into your `$PROFILE.CurrentUserAllHosts` profile.</span></span> <span data-ttu-id="f2763-180">Placera objekt som är specifika för ett värd program, till exempel ett kommando som anger bakgrunds färgen för ett värd program, i en profil som är specifik för värd programmet.</span><span class="sxs-lookup"><span data-stu-id="f2763-180">Put items that are specific to a host application, such as a command that sets the background color for a host application, in a profile that is specific to that host application.</span></span>

<span data-ttu-id="f2763-181">Om du är administratör som anpassar PowerShell för många användare följer du dessa rikt linjer:</span><span class="sxs-lookup"><span data-stu-id="f2763-181">If you are an administrator who is customizing PowerShell for many users, follow these guidelines:</span></span>

- <span data-ttu-id="f2763-182">Lagra gemensamma objekt i `$PROFILE.AllUsersAllHosts` profilen</span><span class="sxs-lookup"><span data-stu-id="f2763-182">Store the common items in the `$PROFILE.AllUsersAllHosts` profile</span></span>
- <span data-ttu-id="f2763-183">Lagra objekt som är specifika för ett värd program i `$PROFILE.AllUsersCurrentHost` profiler som är specifika för värd programmet</span><span class="sxs-lookup"><span data-stu-id="f2763-183">Store items that are specific to a host application in `$PROFILE.AllUsersCurrentHost` profiles that are specific to the host application</span></span>
- <span data-ttu-id="f2763-184">Lagra objekt för särskilda användare i användarspecifika profiler</span><span class="sxs-lookup"><span data-stu-id="f2763-184">Store items for particular users in the user-specific profiles</span></span>

<span data-ttu-id="f2763-185">Se till att kontrol lera om det finns någon speciell implementering av PowerShell-profiler i värd program dokumentationen.</span><span class="sxs-lookup"><span data-stu-id="f2763-185">Be sure to check the host application documentation for any special implementation of PowerShell profiles.</span></span>

## <a name="how-to-use-a-profile"></a><span data-ttu-id="f2763-186">Använda en profil</span><span class="sxs-lookup"><span data-stu-id="f2763-186">How to use a profile</span></span>

<span data-ttu-id="f2763-187">Många av de objekt som du skapar i PowerShell och de flesta kommandon som du kör påverkar bara den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="f2763-187">Many of the items that you create in PowerShell and most commands that you run affect only the current session.</span></span> <span data-ttu-id="f2763-188">När du slutar sessionen tas objekten bort.</span><span class="sxs-lookup"><span data-stu-id="f2763-188">When you end the session, the items are deleted.</span></span>

<span data-ttu-id="f2763-189">De sessionsbaserade kommandona och objekten innehåller variabler, inställningar för variabler, alias, funktioner, kommandon (förutom för [set-ExecutionPolicy](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)) och PowerShell-moduler som du lägger till i sessionen.</span><span class="sxs-lookup"><span data-stu-id="f2763-189">The session-specific commands and items include variables, preference variables, aliases, functions, commands (except for [Set-ExecutionPolicy](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)), and PowerShell modules that you add to the session.</span></span>

<span data-ttu-id="f2763-190">Om du vill spara objekten och göra dem tillgängliga i alla framtida sessioner, lägger du till dem i en PowerShell-profil.</span><span class="sxs-lookup"><span data-stu-id="f2763-190">To save these items and make them available in all future sessions, add them to a PowerShell profile.</span></span>

<span data-ttu-id="f2763-191">Ett annat vanligt användnings sätt för profiler är att spara ofta använda funktioner, alias och variabler.</span><span class="sxs-lookup"><span data-stu-id="f2763-191">Another common use for profiles is to save frequently-used functions, aliases, and variables.</span></span> <span data-ttu-id="f2763-192">När du sparar objekten i en profil kan du använda dem i en lämplig session utan att skapa om dem.</span><span class="sxs-lookup"><span data-stu-id="f2763-192">When you save the items in a profile, you can use them in any applicable session without recreating them.</span></span>

## <a name="how-to-start-a-profile"></a><span data-ttu-id="f2763-193">Så här startar du en profil</span><span class="sxs-lookup"><span data-stu-id="f2763-193">How to start a profile</span></span>

<span data-ttu-id="f2763-194">När du öppnar profil filen är den tom.</span><span class="sxs-lookup"><span data-stu-id="f2763-194">When you open the profile file, it is blank.</span></span> <span data-ttu-id="f2763-195">Du kan dock fylla det med variabler, alias och kommandon som du använder ofta.</span><span class="sxs-lookup"><span data-stu-id="f2763-195">However, you can fill it with the variables, aliases, and commands that you use frequently.</span></span>

<span data-ttu-id="f2763-196">Här är några förslag på hur du kan komma igång.</span><span class="sxs-lookup"><span data-stu-id="f2763-196">Here are a few suggestions to get you started.</span></span>

### <a name="add-commands-that-make-it-easy-to-open-your-profile"></a><span data-ttu-id="f2763-197">Lägg till kommandon som gör det enkelt att öppna din profil</span><span class="sxs-lookup"><span data-stu-id="f2763-197">Add commands that make it easy to open your profile</span></span>

<span data-ttu-id="f2763-198">Detta är särskilt användbart om du använder en annan profil än profilen "aktuell användare, aktuell värd".</span><span class="sxs-lookup"><span data-stu-id="f2763-198">This is especially useful if you use a profile other than the "Current User, Current Host" profile.</span></span> <span data-ttu-id="f2763-199">Lägg till exempel till följande kommando:</span><span class="sxs-lookup"><span data-stu-id="f2763-199">For example, add the following command:</span></span>

```powershell
function Pro {notepad $PROFILE.CurrentUserAllHosts}
```

### <a name="add-a-function-that-lists-the-aliases-for-any-cmdlet"></a><span data-ttu-id="f2763-200">Lägg till en funktion som visar alias för alla cmdletar</span><span class="sxs-lookup"><span data-stu-id="f2763-200">Add a function that lists the aliases for any cmdlet</span></span>

```powershell
function Get-CmdletAlias ($cmdletname) {
  Get-Alias |
    Where-Object -FilterScript {$_.Definition -like "$cmdletname"} |
      Format-Table -Property Definition, Name -AutoSize
}
```

### <a name="customize-your-console"></a><span data-ttu-id="f2763-201">Anpassa konsolen</span><span class="sxs-lookup"><span data-stu-id="f2763-201">Customize your console</span></span>

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

### <a name="add-a-customized-powershell-prompt"></a><span data-ttu-id="f2763-202">Lägg till en anpassad PowerShell-prompt</span><span class="sxs-lookup"><span data-stu-id="f2763-202">Add a customized PowerShell prompt</span></span>

```powershell
function Prompt
{
$env:COMPUTERNAME + "\" + (Get-Location) + "> "
}
```

<span data-ttu-id="f2763-203">Mer information om PowerShell-prompten finns [about_Prompts](about_Prompts.md).</span><span class="sxs-lookup"><span data-stu-id="f2763-203">For more information about the PowerShell prompt, see [about_Prompts](about_Prompts.md).</span></span>

## <a name="the-noprofile-parameter"></a><span data-ttu-id="f2763-204">Parametern noprofile</span><span class="sxs-lookup"><span data-stu-id="f2763-204">The NoProfile parameter</span></span>

<span data-ttu-id="f2763-205">Om du vill starta PowerShell utan profiler använder du parametern **noprofile** i **PowerShell.exe**, programmet som startar PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f2763-205">To start PowerShell without profiles, use the **NoProfile** parameter of **PowerShell.exe**, the program that starts PowerShell.</span></span>

<span data-ttu-id="f2763-206">Börja genom att öppna ett program som kan starta PowerShell, till exempel Cmd.exe eller PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f2763-206">To begin, open a program that can start PowerShell, such as Cmd.exe or PowerShell itself.</span></span> <span data-ttu-id="f2763-207">Du kan också använda dialog rutan Kör i Windows.</span><span class="sxs-lookup"><span data-stu-id="f2763-207">You can also use the Run dialog box in Windows.</span></span>

<span data-ttu-id="f2763-208">Ange:</span><span class="sxs-lookup"><span data-stu-id="f2763-208">Type:</span></span>

```
PowerShell -NoProfile
```

<span data-ttu-id="f2763-209">Om du vill ha en fullständig lista över parametrarna för PowerShell.exe skriver du:</span><span class="sxs-lookup"><span data-stu-id="f2763-209">For a complete list of the parameters of PowerShell.exe, type:</span></span>

```
PowerShell -?
```

## <a name="profiles-and-execution-policy"></a><span data-ttu-id="f2763-210">Profiler och körnings princip</span><span class="sxs-lookup"><span data-stu-id="f2763-210">Profiles and Execution Policy</span></span>

<span data-ttu-id="f2763-211">Körnings principen för PowerShell bestämmer delvis om du kan köra skript och läsa in konfigurationsfiler, inklusive profilerna.</span><span class="sxs-lookup"><span data-stu-id="f2763-211">The PowerShell execution policy determines, in part, whether you can run scripts and load configuration files, including the profiles.</span></span> <span data-ttu-id="f2763-212">Principen för **begränsade** körningar är standardinställningen.</span><span class="sxs-lookup"><span data-stu-id="f2763-212">The **Restricted** execution policy is the default.</span></span> <span data-ttu-id="f2763-213">Det förhindrar att alla skript körs, inklusive profilerna.</span><span class="sxs-lookup"><span data-stu-id="f2763-213">It prevents all scripts from running, including the profiles.</span></span> <span data-ttu-id="f2763-214">Om du använder principen "begränsad" körs inte profilen och dess innehåll tillämpas inte.</span><span class="sxs-lookup"><span data-stu-id="f2763-214">If you use the "Restricted" policy, the profile does not run, and its contents are not applied.</span></span>

<span data-ttu-id="f2763-215">Ett `Set-ExecutionPolicy` kommando anger och ändrar din körnings princip.</span><span class="sxs-lookup"><span data-stu-id="f2763-215">A `Set-ExecutionPolicy` command sets and changes your execution policy.</span></span> <span data-ttu-id="f2763-216">Det är ett av de få kommandon som gäller för alla PowerShell-sessioner eftersom värdet sparas i registret.</span><span class="sxs-lookup"><span data-stu-id="f2763-216">It is one of the few commands that applies in all PowerShell sessions because the value is saved in the registry.</span></span> <span data-ttu-id="f2763-217">Du behöver inte ange det när du öppnar-konsolen och du behöver inte lagra ett `Set-ExecutionPolicy` kommando i din profil.</span><span class="sxs-lookup"><span data-stu-id="f2763-217">You do not have to set it when you open the console, and you do not have to store a `Set-ExecutionPolicy` command in your profile.</span></span>

## <a name="profiles-and-remote-sessions"></a><span data-ttu-id="f2763-218">Profiler och fjärrsessioner</span><span class="sxs-lookup"><span data-stu-id="f2763-218">Profiles and remote sessions</span></span>

<span data-ttu-id="f2763-219">PowerShell-profiler körs inte automatiskt i fjärrsessioner, så kommandon som profiler lägger till finns inte i fjärrsessionen.</span><span class="sxs-lookup"><span data-stu-id="f2763-219">PowerShell profiles are not run automatically in remote sessions, so the commands that the profiles add are not present in the remote session.</span></span> <span data-ttu-id="f2763-220">Dessutom `$PROFILE` är den automatiska variabeln inte ifylld i fjärrsessioner.</span><span class="sxs-lookup"><span data-stu-id="f2763-220">In addition, the `$PROFILE` automatic variable is not populated in remote sessions.</span></span>

<span data-ttu-id="f2763-221">Om du vill köra en profil i en session använder du cmdleten [Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command) .</span><span class="sxs-lookup"><span data-stu-id="f2763-221">To run a profile in a session, use the [Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command) cmdlet.</span></span>

<span data-ttu-id="f2763-222">Följande kommando kör till exempel "aktuell användare, aktuell värd"-profil från den lokala datorn i sessionen i `$s` .</span><span class="sxs-lookup"><span data-stu-id="f2763-222">For example, the following command runs the "Current user, Current Host" profile from the local computer in the session in `$s`.</span></span>

```powershell
Invoke-Command -Session $s -FilePath $PROFILE
```

<span data-ttu-id="f2763-223">Följande kommando kör profilen "aktuell användare, aktuell värd" från fjärrdatorn i sessionen i `$s` .</span><span class="sxs-lookup"><span data-stu-id="f2763-223">The following command runs the "Current user, Current Host" profile from the remote computer in the session in `$s`.</span></span> <span data-ttu-id="f2763-224">Eftersom `$PROFILE` variabeln inte är ifylld använder kommandot den explicita sökvägen till profilen.</span><span class="sxs-lookup"><span data-stu-id="f2763-224">Because the `$PROFILE` variable is not populated, the command uses the explicit path to the profile.</span></span> <span data-ttu-id="f2763-225">Vi använder en punkt källa-operator så att profilen körs i det aktuella omfånget på fjärrdatorn och inte i det egna omfånget.</span><span class="sxs-lookup"><span data-stu-id="f2763-225">We use dot sourcing operator so that the profile executes in the current scope on the remote computer and not in its own scope.</span></span>

```powershell
Invoke-Command -Session $s -ScriptBlock {
  . "$HOME\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1"
}
```

<span data-ttu-id="f2763-226">När du har kört det här kommandot är de kommandon som profilen lägger till i sessionen tillgängliga i `$s` .</span><span class="sxs-lookup"><span data-stu-id="f2763-226">After running this command, the commands that the profile adds to the session are available in `$s`.</span></span>

## <a name="see-also"></a><span data-ttu-id="f2763-227">Se även</span><span class="sxs-lookup"><span data-stu-id="f2763-227">See Also</span></span>

[<span data-ttu-id="f2763-228">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="f2763-228">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)

[<span data-ttu-id="f2763-229">about_Functions</span><span class="sxs-lookup"><span data-stu-id="f2763-229">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="f2763-230">about_Prompts</span><span class="sxs-lookup"><span data-stu-id="f2763-230">about_Prompts</span></span>](about_Prompts.md)

[<span data-ttu-id="f2763-231">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="f2763-231">about_Execution_Policies</span></span>](about_Execution_Policies.md)

[<span data-ttu-id="f2763-232">about_Signing</span><span class="sxs-lookup"><span data-stu-id="f2763-232">about_Signing</span></span>](about_Signing.md)

[<span data-ttu-id="f2763-233">about_Remote</span><span class="sxs-lookup"><span data-stu-id="f2763-233">about_Remote</span></span>](about_Remote.md)

[<span data-ttu-id="f2763-234">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="f2763-234">about_Scopes</span></span>](about_Scopes.md)

[<span data-ttu-id="f2763-235">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="f2763-235">Set-ExecutionPolicy</span></span>](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)
