---
title: Lägg till support för autentiseringsuppgifter in PowerShell-funktioner
description: Hur du lägger till parametrar för autentiseringsuppgifter i dina PowerShell-skript,-funktioner och-cmdletar.
ms.date: 10/29/2020
ms.custom: contributor-JoshDuffney
ms.openlocfilehash: 3e4a3f41ccbca1cf97f2e96fd60f22d89be7bc5a
ms.sourcegitcommit: 39c2a697228276d5dae39e540995fa479c2b5f39
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/05/2020
ms.locfileid: "93354634"
---
# <a name="add-credential-support-to-powershell-functions"></a><span data-ttu-id="d1714-103">Lägg till support för autentiseringsuppgifter in PowerShell-funktioner</span><span class="sxs-lookup"><span data-stu-id="d1714-103">Add Credential support to PowerShell functions</span></span>

> [!NOTE]
> <span data-ttu-id="d1714-104">Den [ursprungliga versionen][] av den här artikeln visas på bloggen som skrivits av [@joshduffney][] .</span><span class="sxs-lookup"><span data-stu-id="d1714-104">The [original version][] of this article appeared on the blog written by [@joshduffney][].</span></span> <span data-ttu-id="d1714-105">Den här artikeln har redigerats för inkludering på den här webbplatsen.</span><span class="sxs-lookup"><span data-stu-id="d1714-105">This article has been edited for inclusion on this site.</span></span> <span data-ttu-id="d1714-106">PowerShell-teamet tack Josh för att dela det här innehållet med oss.</span><span class="sxs-lookup"><span data-stu-id="d1714-106">The PowerShell team thanks Josh for sharing this content with us.</span></span> <span data-ttu-id="d1714-107">Ta en titt på hans blogg på [duffney.io][].</span><span class="sxs-lookup"><span data-stu-id="d1714-107">Please check out his blog at [duffney.io][].</span></span>

<span data-ttu-id="d1714-108">Den här artikeln visar hur du lägger till parametrar för autentiseringsuppgifter till PowerShell-funktioner och varför du vill.</span><span class="sxs-lookup"><span data-stu-id="d1714-108">This article shows you how to add credential parameters to PowerShell functions and why you'd want to.</span></span> <span data-ttu-id="d1714-109">En parameter för autentiseringsuppgifter är att du ska kunna köra funktionen eller cmdleten som en annan användare.</span><span class="sxs-lookup"><span data-stu-id="d1714-109">A credential parameter is to allow you to run the function or cmdlet as a different user.</span></span> <span data-ttu-id="d1714-110">Den vanligaste användningen är att köra funktionen eller cmdleten som ett upphöjd användar konto.</span><span class="sxs-lookup"><span data-stu-id="d1714-110">The most common use is to run the function or cmdlet as an elevated user account.</span></span>

<span data-ttu-id="d1714-111">Till exempel har cmdleten `New-ADUser` en **Credential** -parameter, som du kan ange autentiseringsuppgifter för domän administratörer för att skapa ett konto i en domän.</span><span class="sxs-lookup"><span data-stu-id="d1714-111">For example, the cmdlet `New-ADUser` has a **Credential** parameter, which you could provide domain admin credentials to create an account in a domain.</span></span> <span data-ttu-id="d1714-112">Under förutsättning att det normala kontot som kör PowerShell-sessionen inte redan har den åtkomsten.</span><span class="sxs-lookup"><span data-stu-id="d1714-112">Assuming your normal account running the PowerShell session doesn't have that access already.</span></span>

## <a name="creating-credential-object"></a><span data-ttu-id="d1714-113">Skapar Credential-objekt</span><span class="sxs-lookup"><span data-stu-id="d1714-113">Creating credential object</span></span>

<span data-ttu-id="d1714-114">Objektet [PSCredential][] representerar en uppsättning säkerhets referenser, till exempel användar namn och lösen ord.</span><span class="sxs-lookup"><span data-stu-id="d1714-114">The [PSCredential][] object represents a set of security credentials such as a user name and password.</span></span> <span data-ttu-id="d1714-115">Objektet kan skickas som en parameter till en funktion som körs som användar konto i objektet Credential.</span><span class="sxs-lookup"><span data-stu-id="d1714-115">The object can be passed as a parameter to a function that runs as the user account in that credential object.</span></span> <span data-ttu-id="d1714-116">Det finns några sätt som du kan skapa ett Credential-objekt på.</span><span class="sxs-lookup"><span data-stu-id="d1714-116">There are a few ways that you can create a credential object.</span></span> <span data-ttu-id="d1714-117">Det första sättet att skapa ett Credential-objekt är att använda PowerShell-cmdleten `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="d1714-117">The first way to create a credential object is to use the PowerShell cmdlet `Get-Credential`.</span></span> <span data-ttu-id="d1714-118">När du kör utan parametrar uppmanas du att ange ett användar namn och lösen ord.</span><span class="sxs-lookup"><span data-stu-id="d1714-118">When you run without parameters, it prompts you for a username and password.</span></span> <span data-ttu-id="d1714-119">Du kan också anropa cmdleten med några valfria parametrar.</span><span class="sxs-lookup"><span data-stu-id="d1714-119">Or you can call the cmdlet with some optional parameters.</span></span>

<span data-ttu-id="d1714-120">Om du vill ange domän namn och användar namn i förväg kan du antingen använda parametrarna **Credential** eller **username** .</span><span class="sxs-lookup"><span data-stu-id="d1714-120">To specify the domain name and username ahead of time you can use either the **Credential** or **UserName** parameters.</span></span> <span data-ttu-id="d1714-121">När du använder **användar namns** parametern måste du också ange ett **meddelande** värde.</span><span class="sxs-lookup"><span data-stu-id="d1714-121">When you use the **UserName** parameter, you're also required to provide a **Message** value.</span></span> <span data-ttu-id="d1714-122">Koden nedan visar hur du använder cmdleten.</span><span class="sxs-lookup"><span data-stu-id="d1714-122">The code below demonstrates using the cmdlet.</span></span> <span data-ttu-id="d1714-123">Du kan också lagra Credential-objektet i en variabel så att du kan använda autentiseringsuppgiften flera gånger.</span><span class="sxs-lookup"><span data-stu-id="d1714-123">You can also store the credential object in a variable so that you can use the credential multiple times.</span></span> <span data-ttu-id="d1714-124">I exemplet nedan lagras Credential-objektet i variabeln `$Cred` .</span><span class="sxs-lookup"><span data-stu-id="d1714-124">In the example below, the credential object is stored in the variable `$Cred`.</span></span>

```powershell
$Cred = Get-Credential
$Cred = Get-Credential -Credential domain\user
$Cred = Get-Credential -UserName domain\user -Message 'Enter Password'
```

<span data-ttu-id="d1714-125">Ibland kan du inte använda den interaktiva metoden för att skapa Credential-objekt som visas i föregående exempel.</span><span class="sxs-lookup"><span data-stu-id="d1714-125">Sometimes, you can't use the interactive method of creating credential objects shown in the previous example.</span></span> <span data-ttu-id="d1714-126">De flesta automatiserings verktyg kräver en icke-interaktiv metod.</span><span class="sxs-lookup"><span data-stu-id="d1714-126">Most automation tools require a non-interactive method.</span></span> <span data-ttu-id="d1714-127">Om du vill skapa en autentiseringsuppgift utan användar interaktion skapar du en säker sträng som innehåller lösen ordet.</span><span class="sxs-lookup"><span data-stu-id="d1714-127">To create a credential without user interaction, create a secure string containing the password.</span></span> <span data-ttu-id="d1714-128">Skicka sedan den säkra strängen och användar namnet till- `System.Management.Automation.PSCredential()` metoden.</span><span class="sxs-lookup"><span data-stu-id="d1714-128">Then pass the secure string and user name to the `System.Management.Automation.PSCredential()` method.</span></span>

<span data-ttu-id="d1714-129">Använd följande kommando för att skapa en säker sträng som innehåller lösen ordet:</span><span class="sxs-lookup"><span data-stu-id="d1714-129">Use the following command to create a secure string containing the password:</span></span>

```powershell
ConvertTo-SecureString "MyPlainTextPassword" -AsPlainText -Force
```

<span data-ttu-id="d1714-130">Både egenskaperna för **klartext** och **Force** måste anges.</span><span class="sxs-lookup"><span data-stu-id="d1714-130">Both the **AsPlainText** and **Force** parameters are required.</span></span> <span data-ttu-id="d1714-131">Utan dessa parametrar får du en varning om att du inte ska skicka oformaterad text till en säker sträng.</span><span class="sxs-lookup"><span data-stu-id="d1714-131">Without those parameters, you receive a message warning that you shouldn't pass plain text into a secure string.</span></span> <span data-ttu-id="d1714-132">PowerShell returnerar denna varning eftersom lösen ordet för oformaterad text registreras i olika loggar.</span><span class="sxs-lookup"><span data-stu-id="d1714-132">PowerShell returns this warning because the plain text password gets recorded in various logs.</span></span> <span data-ttu-id="d1714-133">När du har skapat en säker sträng måste du skicka den till- `PSCredential()` metoden för att skapa Credential-objektet.</span><span class="sxs-lookup"><span data-stu-id="d1714-133">Once you have a secure string created, you need to pass it to the `PSCredential()` method to create the credential object.</span></span> <span data-ttu-id="d1714-134">I följande exempel innehåller variabeln `$password` den säkra strängen som `$Cred` innehåller objektet Credential.</span><span class="sxs-lookup"><span data-stu-id="d1714-134">In the following example, the variable `$password` contains the secure string `$Cred` contains the credential object.</span></span>

```powershell
$password = ConvertTo-SecureString "MyPlainTextPassword" -AsPlainText -Force
$Cred = New-Object System.Management.Automation.PSCredential ("username", $password)
```

<span data-ttu-id="d1714-135">Nu när du vet hur du skapar Credential-objekt kan du lägga till inloggnings parametrar till dina PowerShell-funktioner.</span><span class="sxs-lookup"><span data-stu-id="d1714-135">Now that you know how to create credential objects, you can add credential parameters to your PowerShell functions.</span></span>

## <a name="adding-a-credential-parameter"></a><span data-ttu-id="d1714-136">Lägger till en Credential-parameter</span><span class="sxs-lookup"><span data-stu-id="d1714-136">Adding a Credential Parameter</span></span>

<span data-ttu-id="d1714-137">Precis som med andra parametrar börjar du med att lägga till den i `param` blockeringen av din funktion.</span><span class="sxs-lookup"><span data-stu-id="d1714-137">Just like any other parameter, you start off by adding it in the `param` block of your function.</span></span>
<span data-ttu-id="d1714-138">Vi rekommenderar att du namnger parametern `$Credential` , eftersom det är det som befintliga PowerShell-cmdletar använder.</span><span class="sxs-lookup"><span data-stu-id="d1714-138">It's recommended that you name the parameter `$Credential` because that's what existing PowerShell cmdlets use.</span></span> <span data-ttu-id="d1714-139">Parameterns typ ska vara `[System.Management.Automation.PSCredential]` .</span><span class="sxs-lookup"><span data-stu-id="d1714-139">The type of the parameter should be `[System.Management.Automation.PSCredential]`.</span></span>

<span data-ttu-id="d1714-140">I följande exempel visas parameter block för en funktion som kallas `Get-Something` .</span><span class="sxs-lookup"><span data-stu-id="d1714-140">The following example shows the parameter block for a function called `Get-Something`.</span></span> <span data-ttu-id="d1714-141">Det har två parametrar: `$Name` och `$Credential` .</span><span class="sxs-lookup"><span data-stu-id="d1714-141">It has two parameters: `$Name` and `$Credential`.</span></span>

```powershell
function Get-Something {
    param(
        $Name,
        [System.Management.Automation.PSCredential]$Credential
    )
```

<span data-ttu-id="d1714-142">Koden i det här exemplet räcker för att ha en fungerande Credential-parameter, men det finns några saker som du kan lägga till för att göra den mer robust.</span><span class="sxs-lookup"><span data-stu-id="d1714-142">The code in this example is enough to have a working credential parameter, however there are a few things you can add to make it more robust.</span></span>

- <span data-ttu-id="d1714-143">Lägg till `[ValidateNotNull()]` attributet verifiering för att kontrol lera att värdet skickas till **autentiseringsuppgiften**.</span><span class="sxs-lookup"><span data-stu-id="d1714-143">Add the `[ValidateNotNull()]` validation attribute to check that the value being passed to **Credential**.</span></span> <span data-ttu-id="d1714-144">Om parametervärdet är null förhindrar det här attributet funktionen från att köras med ogiltiga autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="d1714-144">If the parameter value is null, this attribute prevents the function from executing with invalid credentials.</span></span>

- <span data-ttu-id="d1714-145">Lägg till `[System.Management.Automation.Credential()]` .</span><span class="sxs-lookup"><span data-stu-id="d1714-145">Add `[System.Management.Automation.Credential()]`.</span></span> <span data-ttu-id="d1714-146">På så sätt kan du skicka in ett användar namn som en sträng och ha en interaktiv prompt för lösen ordet.</span><span class="sxs-lookup"><span data-stu-id="d1714-146">This allows you to pass in a username as a string and have an interactive prompt for the password.</span></span>

- <span data-ttu-id="d1714-147">Ange ett standardvärde för `$Credential` parametern till `[System.Management.Automation.PSCredential]::Empty` .</span><span class="sxs-lookup"><span data-stu-id="d1714-147">Set a default value for the `$Credential` parameter to `[System.Management.Automation.PSCredential]::Empty`.</span></span> <span data-ttu-id="d1714-148">Funktionen du kanske skickar det här `$Credential` objektet till befintliga PowerShell-cmdletar.</span><span class="sxs-lookup"><span data-stu-id="d1714-148">Your function you might be passing this `$Credential` object to existing PowerShell cmdlets.</span></span> <span data-ttu-id="d1714-149">Om du anger ett null-värde för cmdleten som anropas inuti funktionen uppstår ett fel.</span><span class="sxs-lookup"><span data-stu-id="d1714-149">Providing a null value to the cmdlet called inside your function causes an error.</span></span> <span data-ttu-id="d1714-150">Om du anger ett tomt Credential-objekt undviker du det här felet.</span><span class="sxs-lookup"><span data-stu-id="d1714-150">Providing an empty credential object avoids this error.</span></span>

> [!TIP]
> <span data-ttu-id="d1714-151">Vissa cmdlets som accepterar en Credential-parameter stöder inte `[System.Management.Automation.PSCredential]::Empty` som de ska.</span><span class="sxs-lookup"><span data-stu-id="d1714-151">Some cmdlets that accept a credential parameter do not support `[System.Management.Automation.PSCredential]::Empty` as they should.</span></span> <span data-ttu-id="d1714-152">En lösning finns i avsnittet [hantera med äldre cmdlets](#dealing-with-legacy-cmdlets) .</span><span class="sxs-lookup"><span data-stu-id="d1714-152">See the [Dealing with Legacy Cmdlets](#dealing-with-legacy-cmdlets) section for a workaround.</span></span>

## <a name="using-credential-parameters"></a><span data-ttu-id="d1714-153">Använda Credential-parametrar</span><span class="sxs-lookup"><span data-stu-id="d1714-153">Using credential parameters</span></span>

<span data-ttu-id="d1714-154">Följande exempel visar hur du använder Credential-parametrar.</span><span class="sxs-lookup"><span data-stu-id="d1714-154">The following example demonstrates how to use credential parameters.</span></span> <span data-ttu-id="d1714-155">I det här exemplet visas en funktion `Set-RemoteRegistryValue` som kallas, som ligger utanför [pester-boken][].</span><span class="sxs-lookup"><span data-stu-id="d1714-155">This example shows a function called `Set-RemoteRegistryValue`, which is out of [The Pester Book][].</span></span> <span data-ttu-id="d1714-156">Den här funktionen definierar Credential-parametern med hjälp av metoderna som beskrivs i föregående avsnitt.</span><span class="sxs-lookup"><span data-stu-id="d1714-156">This function defines the credential parameter using the techniques describe in the previous section.</span></span> <span data-ttu-id="d1714-157">Funktionen anropar `Invoke-Command` med `$Credential` variabeln som skapats av funktionen.</span><span class="sxs-lookup"><span data-stu-id="d1714-157">The function calls `Invoke-Command` using the `$Credential` variable created by the function.</span></span> <span data-ttu-id="d1714-158">På så sätt kan du ändra den användare som kör `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="d1714-158">This allows you to change the user who's running `Invoke-Command`.</span></span> <span data-ttu-id="d1714-159">Eftersom standardvärdet för `$Credential` är en tom autentiseringsuppgift kan funktionen köras utan att ange autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="d1714-159">Because the default value of `$Credential` is an empty credential, the function can run without providing credentials.</span></span>

```powershell
function Set-RemoteRegistryValue {
    param(
        $ComputerName,
        $Path,
        $Name,
        $Value,
        [ValidateNotNull()]
        [System.Management.Automation.PSCredential]
        [System.Management.Automation.Credential()]
        $Credential = [System.Management.Automation.PSCredential]::Empty
    )
        $null = Invoke-Command -ComputerName $ComputerName -ScriptBlock {
            Set-ItemProperty -Path $using:Path -Name $using:Name -Value $using:Value
        } -Credential $Credential
}
```

<span data-ttu-id="d1714-160">I följande avsnitt visas olika metoder för att ange autentiseringsuppgifter för `Set-RemoteRegistryValue` .</span><span class="sxs-lookup"><span data-stu-id="d1714-160">The following sections show different methods of providing credentials to `Set-RemoteRegistryValue`.</span></span>

### <a name="prompting-for-credentials"></a><span data-ttu-id="d1714-161">Fråga efter autentiseringsuppgifter</span><span class="sxs-lookup"><span data-stu-id="d1714-161">Prompting for credentials</span></span>

<span data-ttu-id="d1714-162">`Get-Credential`Att använda inom parentes `()` vid körningen gör `Get-credential` att körs först.</span><span class="sxs-lookup"><span data-stu-id="d1714-162">Using `Get-Credential` in parentheses `()` at run time causes the `Get-credential` to run first.</span></span> <span data-ttu-id="d1714-163">Du uppmanas att ange ett användar namn och lösen ord.</span><span class="sxs-lookup"><span data-stu-id="d1714-163">You are prompted for a username and password.</span></span> <span data-ttu-id="d1714-164">Du kan använda parametrarna **Credential** eller **username** för `Get-credential` att fylla i användar namnet och domänen i förväg.</span><span class="sxs-lookup"><span data-stu-id="d1714-164">You could use the **Credential** or **UserName** parameters of `Get-credential` to pre-populate the username and domain.</span></span> <span data-ttu-id="d1714-165">I följande exempel används en teknik som kallas ihopbuntning för att skicka parametrar till `Set-RemoteRegistryValue` funktionen.</span><span class="sxs-lookup"><span data-stu-id="d1714-165">The following example uses a technique called splatting to pass parameters to the `Set-RemoteRegistryValue` function.</span></span> <span data-ttu-id="d1714-166">Mer information om ihopbuntning finns i artikeln [about_Splatting][] .</span><span class="sxs-lookup"><span data-stu-id="d1714-166">For more information about splatting, check out the [about_Splatting][] article.</span></span>

```powershell
$remoteKeyParams = @{
    ComputerName = $env:COMPUTERNAME
    Path = 'HKLM:\SOFTWARE\Microsoft\WebManagement\Server'
    Name = 'EnableRemoteManagement'
    Value = '1'
}

Set-RemoteRegistryValue @remoteKeyParams -Credential (Get-Credential)
```

![Få en autentiseringsuppgift vid körning](./media/add-credentials-to-powershell-functions/GetCredAtRunTime.gif)

<span data-ttu-id="d1714-168">Användningen `(Get-Credential)` verkar vara besvärlig.</span><span class="sxs-lookup"><span data-stu-id="d1714-168">Using `(Get-Credential)` seems cumbersome.</span></span> <span data-ttu-id="d1714-169">Normalt uppmanas du att ange lösen ordet när du använder parametern **Credential** med bara ett användar namn.</span><span class="sxs-lookup"><span data-stu-id="d1714-169">Normally, when you use the **Credential** parameter with only a username, the cmdlet automatically prompts for the password.</span></span> <span data-ttu-id="d1714-170">`[System.Management.Automation.Credential()]`Attributet aktiverar det här beteendet.</span><span class="sxs-lookup"><span data-stu-id="d1714-170">The `[System.Management.Automation.Credential()]` attribute enables this behavior.</span></span>

```powershell
$remoteKeyParams = @{
    ComputerName = $env:COMPUTERNAME
    Path = 'HKLM:\SOFTWARE\Microsoft\WebManagement\Server'
    Name = 'EnableRemoteManagement'
    Value = '1'
}

Set-RemoteRegistryValue @remoteKeyParams -Credential duffney
```

![Fråga efter autentiseringsuppgifter](./media/add-credentials-to-powershell-functions/GetCredsPrompt.gif)

> [!NOTE]
> <span data-ttu-id="d1714-172">Dessa exempel förutsätter att du har **webb server** funktionerna i Windows installerat för att ange registervärdet som visas.</span><span class="sxs-lookup"><span data-stu-id="d1714-172">To set the registry value shown, these examples assume you have the **Web Server** features of Windows installed.</span></span> <span data-ttu-id="d1714-173">Kör `Install-WindowsFeature Web-Server` och `Install-WindowsFeature web-mgmt-tools` om det behövs.</span><span class="sxs-lookup"><span data-stu-id="d1714-173">Run `Install-WindowsFeature Web-Server` and `Install-WindowsFeature web-mgmt-tools` if required.</span></span>

### <a name="provide-credentials-in-a-variable"></a><span data-ttu-id="d1714-174">Ange autentiseringsuppgifter i en variabel</span><span class="sxs-lookup"><span data-stu-id="d1714-174">Provide credentials in a variable</span></span>

<span data-ttu-id="d1714-175">Du kan också fylla i en Credential-variabel i förväg och skicka den till parametern **Credential** för `Set-RemoteRegistryValue` funktionen.</span><span class="sxs-lookup"><span data-stu-id="d1714-175">You can also populate a credential variable ahead of time and pass it to the **Credential** parameter of `Set-RemoteRegistryValue` function.</span></span> <span data-ttu-id="d1714-176">Använd den här metoden med verktyg för kontinuerlig integrering/kontinuerlig distribution (CI/CD) som Jenkins, TeamCity och Octopus Deploy.</span><span class="sxs-lookup"><span data-stu-id="d1714-176">Use this method with Continuous Integration / Continuous Deployment (CI/CD) tools such as Jenkins, TeamCity, and Octopus Deploy.</span></span> <span data-ttu-id="d1714-177">Ett exempel på hur du använder Jenkins finns i blogg inlägget om att ta reda på Hodges blogg inlägg [med Jenkins och PowerShell på Windows-del 2][].</span><span class="sxs-lookup"><span data-stu-id="d1714-177">For an example using Jenkins, check out Hodge's blog post [Automating with Jenkins and PowerShell on Windows - Part 2][].</span></span>

<span data-ttu-id="d1714-178">I det här exemplet används .NET-metoden för att skapa Credential-objektet och en säker sträng för att skicka lösen ordet.</span><span class="sxs-lookup"><span data-stu-id="d1714-178">This example uses the .NET method to create the credential object and a secure string to pass in the password.</span></span>

```powershell
$password = ConvertTo-SecureString "P@ssw0rd" -AsPlainText -Force
$Cred = New-Object System.Management.Automation.PSCredential ("duffney", $password)

$remoteKeyParams = @{
    ComputerName = $env:COMPUTERNAME
    Path = 'HKLM:\SOFTWARE\Microsoft\WebManagement\Server'
    Name = 'EnableRemoteManagement'
    Value = '1'
}

Set-RemoteRegistryValue @remoteKeyParams -Credential $Cred
```

<span data-ttu-id="d1714-179">I det här exemplet skapas en säker sträng med ett lösen ord för klartext.</span><span class="sxs-lookup"><span data-stu-id="d1714-179">For this example, the secure string is created using a clear text password.</span></span> <span data-ttu-id="d1714-180">Alla tidigare angivna CI/CD-skivor har en säker metod för att ange lösen ordet vid körning.</span><span class="sxs-lookup"><span data-stu-id="d1714-180">All of the previously mentioned CI/CD have a secure method of providing that password at run time.</span></span> <span data-ttu-id="d1714-181">När du använder dessa verktyg ersätter du lösen ordet för klartext med den variabel som definierats i CI/CD-verktyget som du använder.</span><span class="sxs-lookup"><span data-stu-id="d1714-181">When using those tools, replace the plain text password with the variable defined within the CI/CD tool you use.</span></span>

### <a name="run-without-credentials"></a><span data-ttu-id="d1714-182">Kör utan autentiseringsuppgifter</span><span class="sxs-lookup"><span data-stu-id="d1714-182">Run without credentials</span></span>

<span data-ttu-id="d1714-183">Eftersom `$Credential` standardvärdet är ett tomt Credential-objekt kan du köra kommandot utan autentiseringsuppgifter, som du ser i det här exemplet:</span><span class="sxs-lookup"><span data-stu-id="d1714-183">Since `$Credential` defaults to an empty credential object, you can run the command without credentials, as shown in this example:</span></span>

```powershell
$remoteKeyParams = @{
    ComputerName = $env:COMPUTERNAME
    Path = 'HKLM:\SOFTWARE\Microsoft\WebManagement\Server'
    Name = 'EnableRemoteManagement'
    Value = '1'
}

Set-RemoteRegistryValue @remoteKeyParams
```

## <a name="dealing-with-legacy-cmdlets"></a><span data-ttu-id="d1714-184">Hantera äldre cmdlets</span><span class="sxs-lookup"><span data-stu-id="d1714-184">Dealing with legacy cmdlets</span></span>

<span data-ttu-id="d1714-185">Alla cmdlets stöder inte Credential-objekt eller Tillåt tomma autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="d1714-185">Not all cmdlets support credential objects or allow empty credentials.</span></span> <span data-ttu-id="d1714-186">I stället vill cmdleten användar namn och lösen ord parametrar som strängar.</span><span class="sxs-lookup"><span data-stu-id="d1714-186">Instead, the cmdlet wants username and password parameters as strings.</span></span> <span data-ttu-id="d1714-187">Det finns några sätt att kringgå den här begränsningen.</span><span class="sxs-lookup"><span data-stu-id="d1714-187">There are a few ways to work around this limitation.</span></span>

### <a name="using-if-else-to-handle-empty-credentials"></a><span data-ttu-id="d1714-188">Använda if-else för att hantera tomma autentiseringsuppgifter</span><span class="sxs-lookup"><span data-stu-id="d1714-188">Using if-else to handle empty credentials</span></span>

<span data-ttu-id="d1714-189">I det här scenariot accepterar inte den cmdlet som du vill köra ett tomt Credential-objekt.</span><span class="sxs-lookup"><span data-stu-id="d1714-189">In this scenario, the cmdlet you want to run doesn't accept an empty credential object.</span></span> <span data-ttu-id="d1714-190">I det här exemplet läggs parametern **Credential** till `Invoke-Command` endast om den inte är tom.</span><span class="sxs-lookup"><span data-stu-id="d1714-190">This example adds the **Credential** parameter to `Invoke-Command` only if it's not empty.</span></span> <span data-ttu-id="d1714-191">Annars körs den `Invoke-Command` utan parametern **Credential** .</span><span class="sxs-lookup"><span data-stu-id="d1714-191">Otherwise, it runs the `Invoke-Command` without the **Credential** parameter.</span></span>

```powershell
function Set-RemoteRegistryValue {
    param(
        $ComputerName,
        $Path,
        $Name,
        $Value,
        [ValidateNotNull()]
        [System.Management.Automation.PSCredential]
        [System.Management.Automation.Credential()]
        $Credential = [System.Management.Automation.PSCredential]::Empty
    )

    if($Credential -ne [System.Management.Automation.PSCredential]::Empty) {
        Invoke-Command -ComputerName:$ComputerName -Credential:$Credential  {
            Set-ItemProperty -Path $using:Path -Name $using:Name -Value $using:Value
        }
    } else {
        Invoke-Command -ComputerName:$ComputerName {
            Set-ItemProperty -Path $using:Path -Name $using:Name -Value $using:Value
        }
    }
}
```

### <a name="using-splatting-to-handle-empty-credentials"></a><span data-ttu-id="d1714-192">Använda ihopbuntning för att hantera tomma autentiseringsuppgifter</span><span class="sxs-lookup"><span data-stu-id="d1714-192">Using splatting to handle empty credentials</span></span>

<span data-ttu-id="d1714-193">I det här exemplet används parametern ihopbuntning för att anropa den äldre cmdleten.</span><span class="sxs-lookup"><span data-stu-id="d1714-193">This example uses parameter splatting to call the legacy cmdlet.</span></span> <span data-ttu-id="d1714-194">`$Credential`Objektet läggs villkorligt till i hash-tabellen för ihopbuntning och gör att du inte behöver upprepa `Invoke-Command` skript blocket.</span><span class="sxs-lookup"><span data-stu-id="d1714-194">The `$Credential` object is conditionally added to the hash table for splatting and avoids the need to repeat the `Invoke-Command` script block.</span></span> <span data-ttu-id="d1714-195">Mer information om ihopbuntning inuti Functions finns i [ihopbuntning-parametrarna inuti avancerade funktioner][] blogg inlägg.</span><span class="sxs-lookup"><span data-stu-id="d1714-195">To learn more about splatting inside functions, see the [Splatting Parameters Inside Advanced Functions][] blog post.</span></span>

```powershell
function Set-RemoteRegistryValue {
    param(
        $ComputerName,
        $Path,
        $Name,
        $Value,
        [ValidateNotNull()]
        [System.Management.Automation.PSCredential]
        [System.Management.Automation.Credential()]
        $Credential = [System.Management.Automation.PSCredential]::Empty
    )

        $Splat = @{
            ComputerName = $ComputerName
        }

        if ($Credential -ne [System.Management.Automation.PSCredential]::Empty) {
            $Splat['Credential'] = $Credential
        }

        $null = Invoke-Command -ScriptBlock {
            Set-ItemProperty -Path $using:Path -Name $using:Name -Value $using:Value
        } @splat
}
```

### <a name="working-with-string-passwords"></a><span data-ttu-id="d1714-196">Arbeta med sträng lösen ord</span><span class="sxs-lookup"><span data-stu-id="d1714-196">Working with string passwords</span></span>

<span data-ttu-id="d1714-197">`Invoke-Sqlcmd`Cmdlet är ett exempel på en cmdlet som accepterar en sträng som ett lösen ord.</span><span class="sxs-lookup"><span data-stu-id="d1714-197">The `Invoke-Sqlcmd` cmdlet is an example of a cmdlet that accepts a string as a password.</span></span>
<span data-ttu-id="d1714-198">`Invoke-Sqlcmd` gör att du kan köra enkla SQL INSERT-, Update-och Delete-instruktioner.</span><span class="sxs-lookup"><span data-stu-id="d1714-198">`Invoke-Sqlcmd` allows you to run simple SQL insert, update, and delete statements.</span></span> <span data-ttu-id="d1714-199">`Invoke-Sqlcmd` kräver ett användar namn och lösen ord i klartext i stället för ett säkrare Credential-objekt.</span><span class="sxs-lookup"><span data-stu-id="d1714-199">`Invoke-Sqlcmd` requires a clear-text username and password rather than a more secure credential object.</span></span> <span data-ttu-id="d1714-200">Det här exemplet visar hur du extraherar användar namnet och lösen ordet från ett Credential-objekt.</span><span class="sxs-lookup"><span data-stu-id="d1714-200">This example shows how to extract the username and password from a credential object.</span></span>

<span data-ttu-id="d1714-201">`Get-AllSQLDatabases`Funktionen i det här exemplet anropar `Invoke-Sqlcmd` cmdleten för att fråga en SQL-Server för alla dess databaser.</span><span class="sxs-lookup"><span data-stu-id="d1714-201">The `Get-AllSQLDatabases` function in this example calls the `Invoke-Sqlcmd` cmdlet to query a SQL server for all its databases.</span></span> <span data-ttu-id="d1714-202">Funktionen definierar en **Credential** -parameter med samma attribut som användes i föregående exempel.</span><span class="sxs-lookup"><span data-stu-id="d1714-202">The function defines a **Credential** parameter with the same attribute used in the previous examples.</span></span> <span data-ttu-id="d1714-203">Eftersom användar namnet och lösen ordet finns i `$Credential` variabeln kan du extrahera dessa värden för användning med `Invoke-Sqlcmd` .</span><span class="sxs-lookup"><span data-stu-id="d1714-203">Since the username and password exist within the `$Credential` variable, you can extract those values for use with `Invoke-Sqlcmd`.</span></span>

<span data-ttu-id="d1714-204">Användar namnet är tillgängligt från egenskapen **username** för `$Credential` variabeln.</span><span class="sxs-lookup"><span data-stu-id="d1714-204">The user name is available from the **UserName** property of the `$Credential` variable.</span></span> <span data-ttu-id="d1714-205">För att få lösen ordet måste du använda- `GetNetworkCredential()` metoden för `$Credential` objektet.</span><span class="sxs-lookup"><span data-stu-id="d1714-205">To obtain the password, you have to use the `GetNetworkCredential()` method of the `$Credential` object.</span></span> <span data-ttu-id="d1714-206">Värdena extraheras till variabler som läggs till i en hash-tabell som används för ihopbuntning-parametrar till `Invoke-Sqlcmd` .</span><span class="sxs-lookup"><span data-stu-id="d1714-206">The values are extracted into variables that are added to a hash table used for splatting parameters to `Invoke-Sqlcmd`.</span></span>

```powershell
function Get-AllSQLDatabases {
    param(
        $SQLServer,
        [ValidateNotNull()]
        [System.Management.Automation.PSCredential]
        [System.Management.Automation.Credential()]
        $Credential = [System.Management.Automation.PSCredential]::Empty
    )

        $UserName = $Credential.UserName
        $Password = $Credential.GetNetworkCredential().Password

        $splat = @{
            UserName = $UserName
            Password = $Password
            ServerInstance = 'SQLServer'
            Query = "Select * from Sys.Databases"
        }

        Invoke-Sqlcmd @splat
}

$credSplat = @{
    TypeName = 'System.Management.Automation.PSCredential'
    ArgumentList = 'duffney',('P@ssw0rd' | ConvertTo-SecureString -AsPlainText -Force)
}
$Credential= New-Object @credSplat
ConvertTo-SecureString -AsPlainText -Force)

Get-AllSQLDatabases -SQLServer SQL01 -Credential $Credential
```

## <a name="continued-learning-credential-management"></a><span data-ttu-id="d1714-207">Hantering av fortsatt inlärning av autentiseringsuppgifter</span><span class="sxs-lookup"><span data-stu-id="d1714-207">Continued learning credential management</span></span>

<span data-ttu-id="d1714-208">Det kan vara svårt att skapa och lagra Credential-objekt på ett säkert sätt.</span><span class="sxs-lookup"><span data-stu-id="d1714-208">Creating and storing credential objects securely can be difficult.</span></span> <span data-ttu-id="d1714-209">Följande resurser kan hjälpa dig att underhålla PowerShell-autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="d1714-209">The following resources can help you maintain PowerShell credentials.</span></span>

- <span data-ttu-id="d1714-210">[BetterCredentials][]</span><span class="sxs-lookup"><span data-stu-id="d1714-210">[BetterCredentials][]</span></span>
- <span data-ttu-id="d1714-211">[Azure Key Vault][]</span><span class="sxs-lookup"><span data-stu-id="d1714-211">[Azure Key Vault][]</span></span>
- <span data-ttu-id="d1714-212">[Valv projekt][]</span><span class="sxs-lookup"><span data-stu-id="d1714-212">[Vault Project][]</span></span>
- <span data-ttu-id="d1714-213">[SecretManagement-modul][]</span><span class="sxs-lookup"><span data-stu-id="d1714-213">[SecretManagement module][]</span></span>

<!-- link references -->
[ursprunglig version]: https://duffney.io/addcredentialstopowershellfunctions/
[original version]: https://duffney.io/addcredentialstopowershellfunctions/
[@joshduffney]: https://twitter.com/joshduffney
[duffney.io]: https://duffney.io/posts/
[BetterCredentials]: https://www.powershellgallery.com/packages/BetterCredentials/
[Azure Key Vault]: https://azure.microsoft.com/services/key-vault/
[Valv projekt]: https://www.vaultproject.io/
[Vault Project]: https://www.vaultproject.io/
[Ihopbuntning-parametrar inuti avancerade funktioner]: https://duffney.io/Splatting-Parameters-Within-AdvancedFunctions
[Splatting Parameters Inside Advanced Functions]: https://duffney.io/Splatting-Parameters-Within-AdvancedFunctions
[Automatisera med Jenkins och PowerShell i Windows-del 2]: https://hodgkins.io/automating-with-jenkins-and-powershell-on-windows-part-2
[Automating with Jenkins and PowerShell on Windows - Part 2]: https://hodgkins.io/automating-with-jenkins-and-powershell-on-windows-part-2
[PSCredential]: /dotnet/api/system.management.automation.pscredential
[Pester-boken]: https://leanpub.com/the-pester-book
[The Pester Book]: https://leanpub.com/the-pester-book
[about_Splatting]: /powershell/module/microsoft.powershell.core/about/about_splatting
[SecretManagement-modul]: https://devblogs.microsoft.com/powershell/secretmanagement-and-secretstore-updates/
[SecretManagement module]: https://devblogs.microsoft.com/powershell/secretmanagement-and-secretstore-updates/
