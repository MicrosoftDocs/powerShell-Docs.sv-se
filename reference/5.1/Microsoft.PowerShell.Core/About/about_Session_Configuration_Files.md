---
description: Beskriver konfigurationsfiler för sessioner, som används i en sessionsnyckel (kallas även "slut punkt") för att definiera miljön för sessioner som använder sessionen.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_session_configuration_files?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Session_Configuration_Files
ms.openlocfilehash: 198a0aeb667c3c947bc7e202bc3c0d9832195b91
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93271419"
---
# <a name="about-session-configuration-files"></a><span data-ttu-id="a49f2-104">Om konfigurationsfiler för sessioner</span><span class="sxs-lookup"><span data-stu-id="a49f2-104">About Session Configuration Files</span></span>

## <a name="short-description"></a><span data-ttu-id="a49f2-105">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="a49f2-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="a49f2-106">Beskriver konfigurationsfiler för sessioner, som används i en sessionsnyckel (kallas även "slut punkt") för att definiera miljön för sessioner som använder sessionen.</span><span class="sxs-lookup"><span data-stu-id="a49f2-106">Describes session configuration files, which are used in a session configuration (also known as an "endpoint") to define the environment of sessions that use the session configuration.</span></span>

## <a name="long-description"></a><span data-ttu-id="a49f2-107">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="a49f2-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="a49f2-108">En "sessions konfigurations fil" är en textfil med fil namns tillägget. PSSC som innehåller en hash-tabell med konfigurations egenskaper och värden för sessioner.</span><span class="sxs-lookup"><span data-stu-id="a49f2-108">A "session configuration file" is a text file with a .pssc file name extension that contains a hash table of session configuration properties and values.</span></span> <span data-ttu-id="a49f2-109">Du kan använda en konfigurations fil för sessionen för att ange egenskaperna för en sessions konfiguration.</span><span class="sxs-lookup"><span data-stu-id="a49f2-109">You can use a session configuration file to set the properties of a session configuration.</span></span> <span data-ttu-id="a49f2-110">Detta definierar miljön för alla Windows PowerShell-sessioner som använder den konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="a49f2-110">Doing so defines the environment of any Windows PowerShell sessions that use that session configuration.</span></span>

<span data-ttu-id="a49f2-111">Konfigurationsfiler för sessioner gör det enkelt att skapa anpassade sessioner utan att använda komplexa C#-sammansättningar eller skript.</span><span class="sxs-lookup"><span data-stu-id="a49f2-111">Session configuration files make it easy to create custom session configurations without using complex C# assemblies or scripts.</span></span>

<span data-ttu-id="a49f2-112">En "sessionsinformation" eller "slut punkt" är en samling inställningar för lokala datorer som avgör vilka användare som kan skapa sessioner på datorn. vilka kommandon användare kan köra i dessa sessioner. och om sessionen ska köras som ett privilegierat virtuellt konto.</span><span class="sxs-lookup"><span data-stu-id="a49f2-112">A "session configuration" or "endpoint" is a collection of local computer settings that determine such things as which users can create sessions on the computer; which commands users can run in those sessions; and whether the session should run as a privileged virtual account.</span></span> <span data-ttu-id="a49f2-113">För ytterligare information om sessionskonfigurationer, se [about_Session_Configurations](about_Session_Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="a49f2-113">For more information about session configurations, see [about_Session_Configurations](about_Session_Configurations.md).</span></span>

<span data-ttu-id="a49f2-114">Nodkonfigurationer introducerades i Windows PowerShell 2,0 och konfigurationsfiler för sessionen introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="a49f2-114">Session configurations were introduced in Windows PowerShell 2.0, and session configuration files were introduced in Windows PowerShell 3.0.</span></span> <span data-ttu-id="a49f2-115">Du måste använda Windows PowerShell 3,0 för att inkludera en sessions konfigurations fil i en sessions konfiguration.</span><span class="sxs-lookup"><span data-stu-id="a49f2-115">You must use Windows PowerShell 3.0 to include a session configuration file in a session configuration.</span></span> <span data-ttu-id="a49f2-116">Användare av Windows PowerShell 2,0 (och senare) påverkas dock av inställningarna i konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="a49f2-116">However, users of Windows PowerShell 2.0 (and later) are affected by the settings in the session configuration.</span></span>

## <a name="creating-custom-sessions"></a><span data-ttu-id="a49f2-117">Skapa anpassade sessioner</span><span class="sxs-lookup"><span data-stu-id="a49f2-117">Creating Custom Sessions</span></span>

<span data-ttu-id="a49f2-118">Du kan anpassa många funktioner i en Windows PowerShell-session genom att ange sessionsinställningar i en sessions konfiguration.</span><span class="sxs-lookup"><span data-stu-id="a49f2-118">You can customize many features of a Windows PowerShell session by specifying session properties in a session configuration.</span></span> <span data-ttu-id="a49f2-119">Du kan anpassa en session genom att skriva ett C#-program som definierar en anpassad körnings utrymme, eller så kan du använda en konfigurations fil för sessionen för att definiera egenskaperna för sessioner som skapats med hjälp av konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="a49f2-119">You can customize a session by writing a C# program that defines a custom runspace, or you can use a session configuration file to define the properties of sessions created by using the session configuration.</span></span> <span data-ttu-id="a49f2-120">Som en allmän regel är det enklare att använda konfigurations filen för sessionen än att skriva ett C#-program.</span><span class="sxs-lookup"><span data-stu-id="a49f2-120">As a general rule, it is easier to use the session configuration file than to write a C# program.</span></span>

<span data-ttu-id="a49f2-121">Du kan använda en konfigurations fil för sessionen för att skapa objekt som till exempel fullt fungerande sessioner för mycket betrodda användare. låsta sessioner som tillåter minimal åtkomst; sessioner som har utformats för vissa och som endast innehåller de moduler som krävs för dessa uppgifter. sessioner där användare utan privilegier kan bara köra vissa kommandon som ett privilegierat konto.</span><span class="sxs-lookup"><span data-stu-id="a49f2-121">You can use a session configuration file to create items such as fully-functioning sessions for highly trusted users; locked-down sessions that allow minimal access; sessions designed for particular and that contain only the modules required for those tasks; and sessions where unprivileged users can only run specific commands as a privileged account.</span></span>

<span data-ttu-id="a49f2-122">Förutom det kan du hantera om användare av-sessionen kan använda Windows PowerShell-språkelement som skript block eller om de bara kan köra kommandon.</span><span class="sxs-lookup"><span data-stu-id="a49f2-122">In addition to that, you can manage whether users of the session can use Windows PowerShell language elements such as script blocks, or whether they can only run commands.</span></span> <span data-ttu-id="a49f2-123">Du kan hantera versionen av Windows PowerShell-användare som kan köras i sessionen. hantera vilka moduler som importeras till sessionen. och hantera vilka cmdlets, Functions och alias som session användare kan köra.</span><span class="sxs-lookup"><span data-stu-id="a49f2-123">You can manage the version of Windows PowerShell users can run in the session; manage which modules are imported into the session; and manage which cmdlets, functions, and aliases session users can run.</span></span> <span data-ttu-id="a49f2-124">När du använder fältet RoleDefinitions kan du ge användarna olika funktioner i sessionen baserat på grupp medlemskap.</span><span class="sxs-lookup"><span data-stu-id="a49f2-124">When using the RoleDefinitions field, you can give users different capabilities in the session based on group membership.</span></span>

<span data-ttu-id="a49f2-125">Mer information om RoleDefinitions och hur du definierar det här värdet finns i hjälp avsnittet för cmdleten New-PSRoleCapabilityFile.</span><span class="sxs-lookup"><span data-stu-id="a49f2-125">For more information about RoleDefinitions and how to define this Value, see the help topic for the New-PSRoleCapabilityFile Cmdlet.</span></span>

## <a name="creating-a-session-configuration-file"></a><span data-ttu-id="a49f2-126">Skapa en konfigurations fil för sessionen</span><span class="sxs-lookup"><span data-stu-id="a49f2-126">Creating a Session Configuration File</span></span>

<span data-ttu-id="a49f2-127">Det enklaste sättet att skapa en konfigurations fil för en session är genom att använda New-PSSessionConfigurationFile-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a49f2-127">The easiest way to create a session configuration file is by using the New-PSSessionConfigurationFile cmdlet.</span></span> <span data-ttu-id="a49f2-128">Denna cmdlet skapar en fil som använder rätt syntax och format, och som automatiskt verifierar många av konfigurations filens egenskaps värden.</span><span class="sxs-lookup"><span data-stu-id="a49f2-128">This cmdlet generates a file that uses the correct syntax and format, and that automatically verifies many of the configuration file property values.</span></span>

<span data-ttu-id="a49f2-129">Detaljerad beskrivning av de egenskaper som du kan ange i en sessions konfigurations fil finns i hjälp avsnittet för New-PSSessionConfigurationFile-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a49f2-129">For detailed descriptions of the properties that you can set in a session configuration file, see the help topic for the New-PSSessionConfigurationFile cmdlet.</span></span>

<span data-ttu-id="a49f2-130">Följande kommando skapar en konfigurations fil för sessionen som använder standardvärdena.</span><span class="sxs-lookup"><span data-stu-id="a49f2-130">The following command creates a session configuration file that uses the default values.</span></span> <span data-ttu-id="a49f2-131">Den resulterande konfigurations filen använder bara standardvärdena eftersom inga andra parametrar än Sök vägs parametern (som anger fil Sök vägen) ingår:</span><span class="sxs-lookup"><span data-stu-id="a49f2-131">The resulting configuration file uses only the default values because no parameters other than the Path parameter (which specifies the file path) are included:</span></span>

```powershell
New-PSSessionConfigurationFile -Path .\Defaults.pssc
```

<span data-ttu-id="a49f2-132">Om du vill visa den nya konfigurations filen i standard text redigeraren använder du följande kommando:</span><span class="sxs-lookup"><span data-stu-id="a49f2-132">To view the new configuration file in your default text editor, use the following command:</span></span>

```powershell
Invoke-Item -Path .\Defaults.pssc
```

<span data-ttu-id="a49f2-133">Om du vill skapa en sessions konfiguration för sessioner där användaren kan köra kommandon, men inte använda andra element i Windows PowerShell-språket, skriver du:</span><span class="sxs-lookup"><span data-stu-id="a49f2-133">To create a session configuration for sessions in which user can run commands, but not use other elements of the Windows PowerShell language, type:</span></span>

```powershell
New-PSSessionConfigurationFile -LanguageMode NoLanguage
-Path .\NoLanguage.pssc
```

<span data-ttu-id="a49f2-134">I föregående kommando ställer du in parametern LanguageMode till nolanguage förhindrar användare att göra sådana saker som att skriva eller köra skript eller använda variabler.</span><span class="sxs-lookup"><span data-stu-id="a49f2-134">In the preceding command, setting the LanguageMode parameter to NoLanguage prevents users from doing such things as writing or running scripts, or using variables.</span></span>

<span data-ttu-id="a49f2-135">Om du vill skapa en sessionsnyckel för sessioner där användare bara kan använda Get-cmdletar skriver du:</span><span class="sxs-lookup"><span data-stu-id="a49f2-135">To create a session configuration for sessions in which users can use only Get cmdlets, type:</span></span>

```powershell
New-PSSessionConfigurationFile -VisibleCmdlets Get-*
-Path .\GetSessions.pssc
```

<span data-ttu-id="a49f2-136">I föregående exempel ställer du in parametern VisibleCmdlets på Get-\* begränsar användare till cmdletar som har namn som börjar med strängvärdet "Get-".</span><span class="sxs-lookup"><span data-stu-id="a49f2-136">In the preceding example, setting the VisibleCmdlets parameter to Get-\* limits users to cmdlets that have names that start with the string value "Get-".</span></span>

<span data-ttu-id="a49f2-137">Om du vill skapa en sessionsnyckel för sessioner som körs under ett privilegierat virtuellt konto i stället för användarens autentiseringsuppgifter, skriver du:</span><span class="sxs-lookup"><span data-stu-id="a49f2-137">To create a session configuration for sessions that run under a privileged virtual account instead of the user's credentials, type:</span></span>

```powershell
New-PSSessionConfigurationFile -RunAsVirtualAccount
-Path .\VirtualAccount.pssc
```

<span data-ttu-id="a49f2-138">Om du vill skapa en sessionsnyckel för sessioner där de kommandon som är synliga för användaren anges i en roll funktions fil, skriver du:</span><span class="sxs-lookup"><span data-stu-id="a49f2-138">To create a session configuration for sessions in which the commands visible to the user are specified in a role capabilities file, type:</span></span>

```powershell
New-PSSessionConfigurationFile -RoleDefinitions
@{ 'CONTOSO\User' = @{ RoleCapabilities = 'Maintenance' }}
-Path .\Maintenance.pssc
```

### <a name="using-a-session-configuration-file"></a><span data-ttu-id="a49f2-139">Använda en konfigurations fil för sessionen</span><span class="sxs-lookup"><span data-stu-id="a49f2-139">Using a Session Configuration File</span></span>

<span data-ttu-id="a49f2-140">Du kan inkludera en konfigurations fil för sessionen när du skapar en konfiguration av sessionen eller lägga till en fil i konfigurationen vid ett senare tillfälle.</span><span class="sxs-lookup"><span data-stu-id="a49f2-140">You can include a session configuration file when you create a session configuration or add you can add a file to the session configuration at a later time.</span></span>

<span data-ttu-id="a49f2-141">Om du vill lägga till en sessions konfigurations fil när du skapar en-sessionsnyckel använder du parametern Path i Register-PSSessionConfiguration-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a49f2-141">To include a session configuration file when creating a session configuration, use the Path parameter of the Register-PSSessionConfiguration cmdlet.</span></span>

<span data-ttu-id="a49f2-142">Följande kommando använder till exempel filen nolanguage. PSSC när den skapar en konfiguration för nolanguage-sessionen.</span><span class="sxs-lookup"><span data-stu-id="a49f2-142">For example, the following command uses the NoLanguage.pssc file when it creates a NoLanguage session configuration.</span></span>

```powershell
Register-PSSessionConfiguration -Name NoLanguage
-Path .\NoLanguage.pssc
```

<span data-ttu-id="a49f2-143">När en ny nolanguage-session startar får användarna bara åtkomst till Windows PowerShell-kommandon.</span><span class="sxs-lookup"><span data-stu-id="a49f2-143">When a new NoLanguage session starts, users will only have access to Windows PowerShell commands.</span></span>

<span data-ttu-id="a49f2-144">Om du vill lägga till en sessions konfigurations fil i en befintlig sessionsnyckel använder du cmdleten Set-PSSessionConfiguration och parametern Path.</span><span class="sxs-lookup"><span data-stu-id="a49f2-144">To add a session configuration file to an existing session configuration, use the Set-PSSessionConfiguration cmdlet and the Path parameter.</span></span> <span data-ttu-id="a49f2-145">Detta påverkar alla nya sessioner som skapats med den angivna konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="a49f2-145">This affects any new sessions created with the specified session configuration.</span></span> <span data-ttu-id="a49f2-146">Observera att Set-PSSessionConfiguration-cmdlet ändrar själva sessionen och ändrar inte konfigurations filen för sessionen.</span><span class="sxs-lookup"><span data-stu-id="a49f2-146">Note that the Set-PSSessionConfiguration cmdlet changes the session itself and does not modify the session configuration file.</span></span>

<span data-ttu-id="a49f2-147">Följande kommando lägger till exempel till nolanguage. PSSC-filen i konfigurationen av LockedDown-sessionen.</span><span class="sxs-lookup"><span data-stu-id="a49f2-147">For example, the following command adds the NoLanguage.pssc file to the LockedDown session configuration.</span></span>

```powershell
Set-PSSessionConfiguration -Name LockedDown
-Path .\NoLanguage.pssc
```

<span data-ttu-id="a49f2-148">När användarna använder LockedDown för att skapa en session kommer de att kunna köra cmdlets, men de kommer inte att kunna skapa eller använda variabler, tilldela värden eller använda andra språk element i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a49f2-148">When users use the LockedDown session configuration to create a session, they will be able to run cmdlets but they will not be able to create or use variables, assign values, or use other Windows PowerShell language elements.</span></span>

<span data-ttu-id="a49f2-149">Följande kommando använder cmdleten New-PSSession för att skapa en session på datorn SRV01 som använder LockedDown och sparar en objekt referens till sessionen i $s variabeln.</span><span class="sxs-lookup"><span data-stu-id="a49f2-149">The following command uses the New-PSSession cmdlet to create a session on the computer Srv01 that uses the LockedDown session configuration, saving an object reference to the session in the $s variable.</span></span> <span data-ttu-id="a49f2-150">Åtkomst kontrol listan (åtkomst kontrol listan) för sessionen avgör vem som kan använda den för att skapa en session.</span><span class="sxs-lookup"><span data-stu-id="a49f2-150">The ACL (access control list) of the session configuration determines who can use it to create a session.</span></span>

```powershell
$s = New-PSSession -ComputerName Srv01
-ConfigurationName LockedDown
```

<span data-ttu-id="a49f2-151">Eftersom inga språk begränsningar har lagts till i LockedDown, kommer användare i LockedDown-sessioner endast att kunna köra Windows PowerShell-kommandon och-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="a49f2-151">Because the NoLanguage constraints were added to the LockedDown session configuration, users in LockedDown sessions will only be able to run Windows PowerShell commands and cmdlets.</span></span> <span data-ttu-id="a49f2-152">Följande två kommandon använder exempelvis cmdleten Invoke-Command för att köra kommandon i sessionen som refereras i $s-variabeln.</span><span class="sxs-lookup"><span data-stu-id="a49f2-152">For example, the following two commands use the Invoke-Command cmdlet to run commands in the session referenced in the $s variable.</span></span> <span data-ttu-id="a49f2-153">Det första kommandot, som kör Get-UICulture-cmdleten, och som inte använder några variabler, lyckas.</span><span class="sxs-lookup"><span data-stu-id="a49f2-153">The first command, which runs the Get-UICulture cmdlet and does not use any variables, succeeds.</span></span> <span data-ttu-id="a49f2-154">Det andra kommandot, som hämtar värdet för variabeln $PSUICulture, Miss lyckas.</span><span class="sxs-lookup"><span data-stu-id="a49f2-154">The second command, which gets the value of the $PSUICulture variable, fails.</span></span>

```
Invoke-Command -Session $s {Get-UICulture}
en-US

Invoke-Command -Session $s {$PSUICulture}
The syntax is not supported by this runspace. This might be
because it is in no-language mode.
+ CategoryInfo          : ParserError: ($PSUICulture:String) [],
ParseException
+ FullyQualifiedErrorId : ScriptsNotAllowed
```

## <a name="editing-a-session-configuration-file"></a><span data-ttu-id="a49f2-155">Redigera en konfigurations fil för sessionen</span><span class="sxs-lookup"><span data-stu-id="a49f2-155">Editing a Session Configuration File</span></span>

<span data-ttu-id="a49f2-156">Alla inställningar i en sessionsinformation förutom RunAsVirtualAccount och RunAsVirtualAccountGroups kan ändras genom att du redigerar den sessionens konfigurations fil som används av konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="a49f2-156">All settings in a session configuration except for RunAsVirtualAccount and RunAsVirtualAccountGroups can be modified by editing the session configuration file used by the session configuration.</span></span> <span data-ttu-id="a49f2-157">Börja med att hitta den aktiva kopian av sessionens konfigurations fil.</span><span class="sxs-lookup"><span data-stu-id="a49f2-157">To do this, begin by locating the active copy of the session configuration file.</span></span>

<span data-ttu-id="a49f2-158">När du använder en sessions konfigurations fil i en-session, skapar Windows PowerShell en aktiv kopia av sessionens konfigurations fil och lagrar den i \$ \\ katalogen pshome SessionConfig på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="a49f2-158">When you use a session configuration file in a session configuration, Windows PowerShell creates an active copy of the session configuration file and stores it in the \$pshome\\SessionConfig directory on the local computer.</span></span>

<span data-ttu-id="a49f2-159">Platsen för den aktiva kopian av en sessions konfigurations fil lagras i egenskapen ConfigFilePath för sessionens konfigurations objekt.</span><span class="sxs-lookup"><span data-stu-id="a49f2-159">The location of the active copy of a session configuration file is stored in the ConfigFilePath property of the session configuration object.</span></span>

<span data-ttu-id="a49f2-160">Följande kommando hämtar platsen för sessionens konfigurations fil för konfiguration av nolanguage-sessionen.</span><span class="sxs-lookup"><span data-stu-id="a49f2-160">The following command gets the location of the session configuration file for the NoLanguage session configuration.</span></span>

```powershell
(Get-PSSessionConfiguration -Name NoLanguage).ConfigFilePath
```

<span data-ttu-id="a49f2-161">Kommandot returnerar en fil Sök väg som liknar följande:</span><span class="sxs-lookup"><span data-stu-id="a49f2-161">That command returns a file path similar to the following:</span></span>

```
C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\
NoLanguage_0c115179-ff2a-4f66-a5eb-e56e5692ba22.pssc
```

<span data-ttu-id="a49f2-162">Du kan redigera. PSSC-filen i valfri text redigerare.</span><span class="sxs-lookup"><span data-stu-id="a49f2-162">You can edit the .pssc file in any text editor.</span></span> <span data-ttu-id="a49f2-163">När filen har sparats kommer den att användas av alla nya sessioner som använder-sessionen.</span><span class="sxs-lookup"><span data-stu-id="a49f2-163">After the file is saved it will be employed by any new sessions that use the session configuration.</span></span>

<span data-ttu-id="a49f2-164">Om du behöver ändra RunAsVirtualAccount-eller RunAsVirtualAccountGroups-inställningarna måste du avregistrera konfigurationen för sessionen och registrera en konfigurations fil för sessionen som innehåller de redigerade värdena.</span><span class="sxs-lookup"><span data-stu-id="a49f2-164">If you need to modify the RunAsVirtualAccount or the RunAsVirtualAccountGroups settings, you must un-register the session configuration and re-register a session configuration file that includes the edited values.</span></span>

## <a name="testing-a-session-configuration-file"></a><span data-ttu-id="a49f2-165">Testa en konfigurations fil för sessionen</span><span class="sxs-lookup"><span data-stu-id="a49f2-165">Testing a Session Configuration File</span></span>

<span data-ttu-id="a49f2-166">Använd Test-PSSessionConfigurationFile-cmdlet för att testa manuellt redigerade konfigurationsfiler för sessioner.</span><span class="sxs-lookup"><span data-stu-id="a49f2-166">Use the Test-PSSessionConfigurationFile cmdlet to test manually edited session configuration files.</span></span> <span data-ttu-id="a49f2-167">Det är viktigt: om filsyntaxen och värdena inte är giltiga kan användarna inte använda sessionen för att skapa en session.</span><span class="sxs-lookup"><span data-stu-id="a49f2-167">That's important: if the file syntax and values are not valid users will not be able to use the session configuration to create a session.</span></span>

<span data-ttu-id="a49f2-168">Följande kommando testar till exempel den aktiva sessionens konfigurations fil för konfigurationen av nolanguage-sessionen.</span><span class="sxs-lookup"><span data-stu-id="a49f2-168">For example, the following command tests the active session configuration file of the NoLanguage session configuration.</span></span>

```powershell
Test-PSSessionConfigurationFile -Path C:\WINDOWS\System32\
WindowsPowerShell\v1.0\SessionConfig\
NoLanguage_0c115179-ff2a-4f66-a5eb-e56e5692ba22.pssc
```

<span data-ttu-id="a49f2-169">Om syntaxen och värdena i konfigurations filen är giltiga Test-PSSessionConfigurationFile returnerar true.</span><span class="sxs-lookup"><span data-stu-id="a49f2-169">If the syntax and values in the configuration file are valid Test-PSSessionConfigurationFile returns True.</span></span> <span data-ttu-id="a49f2-170">Om syntaxen och värdena inte är giltiga returnerar cmdleten false.</span><span class="sxs-lookup"><span data-stu-id="a49f2-170">If the syntax and values are not valid then the cmdlet returns False.</span></span>

<span data-ttu-id="a49f2-171">Du kan använda Test-PSSessionConfigurationFile för att testa en konfigurations fil för sessionen, inklusive filer som New-PSSessionConfiguration-cmdlet skapar.</span><span class="sxs-lookup"><span data-stu-id="a49f2-171">You can use Test-PSSessionConfigurationFile to test any session configuration file, including files that the New-PSSessionConfiguration cmdlet creates.</span></span> <span data-ttu-id="a49f2-172">Mer information finns i hjälp avsnittet för Test-PSSessionConfigurationFile-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a49f2-172">For more information, see the help topic for the Test-PSSessionConfigurationFile cmdlet.</span></span>

## <a name="removing-a-session-configuration-file"></a><span data-ttu-id="a49f2-173">Tar bort en konfigurations fil för sessionen</span><span class="sxs-lookup"><span data-stu-id="a49f2-173">Removing a Session Configuration File</span></span>

<span data-ttu-id="a49f2-174">Du kan inte ta bort en sessions konfigurations fil från en sessions konfiguration.</span><span class="sxs-lookup"><span data-stu-id="a49f2-174">You cannot remove a session configuration file from a session configuration.</span></span>
<span data-ttu-id="a49f2-175">Du kan dock ersätta filen med en ny fil som använder standardinställningarna.</span><span class="sxs-lookup"><span data-stu-id="a49f2-175">However, you can replace the file with a new file that uses the default settings.</span></span> <span data-ttu-id="a49f2-176">Detta avbryter de inställningar som används av den ursprungliga konfigurations filen.</span><span class="sxs-lookup"><span data-stu-id="a49f2-176">This effectively cancels the settings used by the original configuration file.</span></span>

<span data-ttu-id="a49f2-177">Om du vill ersätta en sessions konfigurations fil skapar du en ny konfigurations fil för sessionen som använder standardinställningarna och använder sedan Set-PSSessionConfiguration-cmdlet: en för att ersätta den anpassade sessionens konfigurations fil med den nya filen.</span><span class="sxs-lookup"><span data-stu-id="a49f2-177">To replace a session configuration file, create a new session configuration file that uses the default settings, then use the Set-PSSessionConfiguration cmdlet to replace the custom session configuration file with the new file.</span></span>

<span data-ttu-id="a49f2-178">Följande kommandon skapar till exempel en standardsessions konfigurations fil och ersätter sedan den aktiva sessionens konfigurations fil i konfigurationen för konfiguration av nolanguage.</span><span class="sxs-lookup"><span data-stu-id="a49f2-178">For example, the following commands create a Default session configuration file and then replace the active session configuration file in the NoLanguage session configuration.</span></span>

```powershell
New-PSSessionConfigurationFile -Path .\Default.pssc
Set-PSSessionConfiguration -Name NoLanguage
-Path .\Default.pssc
```

<span data-ttu-id="a49f2-179">När de här kommandona är slutförda, ger konfigurationen av nolanguages-sessionen faktiskt stöd för fullständigt språk (standardinställningen) för alla sessioner som skapats med den konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="a49f2-179">When these commands finish, the NoLanguage session configuration will actually provide full language support (the default setting) for all sessions created with that session configuration.</span></span>

<span data-ttu-id="a49f2-180">Visa egenskaperna för en konfiguration av en session. de konfigurations objekt för sessionen som representerar sessionsinställningar med hjälp av konfigurationsfiler har ytterligare egenskaper som gör det enkelt att identifiera och analysera konfigurationen för sessionen.</span><span class="sxs-lookup"><span data-stu-id="a49f2-180">Viewing the Properties of a Session Configuration The session configuration objects that represent session configurations using session configuration files have additional properties that make it easy to discover and analyze the session configuration.</span></span> <span data-ttu-id="a49f2-181">(Observera att det typnamn som visas nedan innehåller en formaterad vydefinition.) Du kan visa egenskaperna genom att köra cmdleten Get-PSSessionConfiguration och skicka tillbaka data till Get-Member-cmdlet:</span><span class="sxs-lookup"><span data-stu-id="a49f2-181">(Note that the type name shown below includes a formatted view definition.) You can view the properties by running the Get-PSSessionConfiguration cmdlet and piping the returned data to the Get-Member cmdlet:</span></span>

```powershell
Get-PSSessionConfiguration NoLanguage | Get-Member
```

```output
TypeName: Microsoft.PowerShell.Commands.PSSessionConfigurationCommands
#PSSessionConfiguration

Name                          MemberType     Definition
----                          ----------     ----------
Equals                        Method         bool Equals(System.O...
GetHashCode                   Method         int GetHashCode()
GetType                       Method         type GetType()
ToString                      Method         string ToString()
Architecture                  NoteProperty   System.String Archit...
Author                        NoteProperty   System.String Author...
AutoRestart                   NoteProperty   System.String AutoRe...
Capability                    NoteProperty   System.Object[] Capa...
CompanyName                   NoteProperty   System.String Compan...
configfilepath                NoteProperty   System.String config...
Copyright                     NoteProperty   System.String Copyri...
Enabled                       NoteProperty   System.String Enable...
ExactMatch                    NoteProperty   System.String ExactM...
ExecutionPolicy               NoteProperty   System.String Execut...
Filename                      NoteProperty   System.String Filena...
GUID                          NoteProperty   System.String GUID=0...
ProcessIdleTimeoutSec         NoteProperty   System.String Proces...
IdleTimeoutms                 NoteProperty   System.String IdleTi...
lang                          NoteProperty   System.String lang=e...
LanguageMode                  NoteProperty   System.String Langua...
MaxConcurrentCommandsPerShell NoteProperty   System.String MaxCon...
MaxConcurrentUsers            NoteProperty   System.String MaxCon...
MaxIdleTimeoutms              NoteProperty   System.String MaxIdl...
MaxMemoryPerShellMB           NoteProperty   System.String MaxMem...
MaxProcessesPerShell          NoteProperty   System.String MaxPro...
MaxShells                     NoteProperty   System.String MaxShells
MaxShellsPerUser              NoteProperty   System.String MaxShe...
Name                          NoteProperty   System.String Name=N...
PSVersion                     NoteProperty   System.String PSVersion
ResourceUri                   NoteProperty   System.String Resour...
RunAsPassword                 NoteProperty   System.String RunAsP...
RunAsUser                     NoteProperty   System.String RunAsUser
SchemaVersion                 NoteProperty   System.String Schema...
SDKVersion                    NoteProperty   System.String SDKVer...
OutputBufferingMode           NoteProperty   System.String Output...
SessionType                   NoteProperty   System.String Sessio...
UseSharedProcess              NoteProperty   System.String UseSha...
SupportsOptions               NoteProperty   System.String Suppor...
xmlns                         NoteProperty   System.String xmlns=...
XmlRenderingType              NoteProperty   System.String XmlRen...
Permission                    ScriptProperty System.Object Permis...
```

<span data-ttu-id="a49f2-182">De här egenskaperna gör det enkelt att söka efter vissa konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="a49f2-182">These properties make it easy to search for specific session configurations.</span></span>
<span data-ttu-id="a49f2-183">Du kan till exempel använda egenskapen ExecutionPolicy för att hitta en sessionsnyckel som stöder sessioner med RemoteSigned-körnings principen.</span><span class="sxs-lookup"><span data-stu-id="a49f2-183">For example, you can use the ExecutionPolicy property to find a session configuration that supports sessions with the RemoteSigned execution policy.</span></span>
<span data-ttu-id="a49f2-184">Observera att eftersom egenskapen ExecutionPolicy bara finns på sessioner som använder konfigurationsfiler för sessioner, kanske kommandot inte returnerar alla kvalificerade konfigurationer av konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="a49f2-184">Note that, because the ExecutionPolicy property exists only on sessions that use session configuration files, the command might not return all qualifying session configurations.</span></span>

```powershell
Get-PSSessionConfiguration |
where {$_.ExecutionPolicy -eq "RemoteSigned"}
```

<span data-ttu-id="a49f2-185">Följande kommando hämtar sessionsinställningar där RunAsUser är Exchange-administratören.</span><span class="sxs-lookup"><span data-stu-id="a49f2-185">The following command gets session configurations in which the RunAsUser is the Exchange administrator.</span></span>

```powershell
 Get-PSSessionConfiguration |
where {$_.RunAsUser -eq "Exchange01\Admin01"}
```

<span data-ttu-id="a49f2-186">Om du vill visa information om roll definitionerna som är associerade med en konfiguration använder du cmdleten Get-PSSessionCapability.</span><span class="sxs-lookup"><span data-stu-id="a49f2-186">To view information about the role definitions associated with a configuration use the Get-PSSessionCapability cmdlet.</span></span> <span data-ttu-id="a49f2-187">Med den här cmdleten kan du bestämma vilka kommandon och miljö som är tillgängliga för vissa användare i vissa slut punkter.</span><span class="sxs-lookup"><span data-stu-id="a49f2-187">This cmdlet enables you to determine the commands and environment available to specific users in specific endpoints.</span></span>

## <a name="notes"></a><span data-ttu-id="a49f2-188">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="a49f2-188">NOTES</span></span>

<span data-ttu-id="a49f2-189">Sessionsbaserade stöder också en typ av session som kallas "Empty"-session.</span><span class="sxs-lookup"><span data-stu-id="a49f2-189">Session configurations also support a type of session known as an "empty" session.</span></span> <span data-ttu-id="a49f2-190">Med en tom sessionsfil kan du skapa anpassade sessioner med valda kommandon.</span><span class="sxs-lookup"><span data-stu-id="a49f2-190">An Empty session type enables you to create custom sessions with selected commands.</span></span> <span data-ttu-id="a49f2-191">Om du inte lägger till moduler, funktioner eller skript i en tom session, är sessionen begränsad till uttryck och kanske inte är en praktisk användning.</span><span class="sxs-lookup"><span data-stu-id="a49f2-191">If you do not add modules, functions, or scripts to an empty session, the session is limited to expressions and might not be of any practical use.</span></span> <span data-ttu-id="a49f2-192">Egenskapen SessionType anger om du arbetar med en tom session eller inte.</span><span class="sxs-lookup"><span data-stu-id="a49f2-192">The SessionType property tells you whether or not you are working with an empty session.</span></span>

## <a name="see-also"></a><span data-ttu-id="a49f2-193">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="a49f2-193">SEE ALSO</span></span>

[<span data-ttu-id="a49f2-194">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="a49f2-194">about_Session_Configurations</span></span>](about_Session_Configurations.md)

[<span data-ttu-id="a49f2-195">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="a49f2-195">New-PSSession</span></span>](xref:Microsoft.PowerShell.Core.New-PSSession)

[<span data-ttu-id="a49f2-196">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="a49f2-196">Disable-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Disable-PSSessionConfiguration)

[<span data-ttu-id="a49f2-197">Aktivera – PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="a49f2-197">Enable-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Enable-PSSessionConfiguration)

[<span data-ttu-id="a49f2-198">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="a49f2-198">Get-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Get-PSSessionConfiguration)

[<span data-ttu-id="a49f2-199">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="a49f2-199">New-PSSessionConfigurationFile</span></span>](xref:Microsoft.PowerShell.Core.New-PSSessionConfigurationFile)

[<span data-ttu-id="a49f2-200">Registrera – PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="a49f2-200">Register-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Register-PSSessionConfiguration)

[<span data-ttu-id="a49f2-201">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="a49f2-201">Set-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Set-PSSessionConfiguration)

[<span data-ttu-id="a49f2-202">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="a49f2-202">Test-PSSessionConfigurationFile</span></span>](xref:Microsoft.PowerShell.Core.Test-PSSessionConfigurationFile)

[<span data-ttu-id="a49f2-203">Avregistrera-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="a49f2-203">Unregister-PSSessionConfiguration</span></span>](xref:Microsoft.PowerShell.Core.Unregister-PSSessionConfiguration)

[<span data-ttu-id="a49f2-204">Get-PSSessionCapability</span><span class="sxs-lookup"><span data-stu-id="a49f2-204">Get-PSSessionCapability</span></span>](xref:Microsoft.PowerShell.Core.Get-PSSessionCapability)

[<span data-ttu-id="a49f2-205">New-PSRoleCapabilityFile</span><span class="sxs-lookup"><span data-stu-id="a49f2-205">New-PSRoleCapabilityFile</span></span>](xref:Microsoft.PowerShell.Core.New-PSRoleCapabilityFile)
