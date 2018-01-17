---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: "Alternativ för autentiseringsuppgifter i konfigurationsdata"
ms.openlocfilehash: 15cdb29127d9774c58e1d6518bbba56273e7defd
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/17/2018
---
# <a name="credentials-options-in-configuration-data"></a><span data-ttu-id="1bca4-103">Alternativ för autentiseringsuppgifter i konfigurationsdata</span><span class="sxs-lookup"><span data-stu-id="1bca4-103">Credentials Options in Configuration Data</span></span>
><span data-ttu-id="1bca4-104">Gäller för: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="1bca4-104">Applies To: Windows PowerShell 5.0</span></span>

## <a name="plain-text-passwords-and-domain-users"></a><span data-ttu-id="1bca4-105">Lösenord i klartext och domänanvändare</span><span class="sxs-lookup"><span data-stu-id="1bca4-105">Plain Text Passwords and Domain Users</span></span>

<span data-ttu-id="1bca4-106">DSC-konfigurationer som innehåller en autentiseringsuppgift utan kryptering genererar ett felmeddelande om lösenord i klartext.</span><span class="sxs-lookup"><span data-stu-id="1bca4-106">DSC configurations containing a credential without encryption will generate an error message about plain text passwords.</span></span>
<span data-ttu-id="1bca4-107">Dessutom genererar DSC en varning när du använder autentiseringsuppgifter för domänen.</span><span class="sxs-lookup"><span data-stu-id="1bca4-107">Also, DSC will generate a warning when using domain credentials.</span></span>
<span data-ttu-id="1bca4-108">Använd nyckelorden DSC-konfiguration data för att ignorera dessa fel och varningar:</span><span class="sxs-lookup"><span data-stu-id="1bca4-108">To suppress these error and warning messages use the DSC configuration data keywords:</span></span>
* <span data-ttu-id="1bca4-109">**PsDscAllowPlainTextPassword**</span><span class="sxs-lookup"><span data-stu-id="1bca4-109">**PsDscAllowPlainTextPassword**</span></span>
* <span data-ttu-id="1bca4-110">**PsDscAllowDomainUser**</span><span class="sxs-lookup"><span data-stu-id="1bca4-110">**PsDscAllowDomainUser**</span></span>

> [!NOTE]
> <span data-ttu-id="1bca4-111">Lagra/överföring av okrypterade lösenord i klartext är inte säker.</span><span class="sxs-lookup"><span data-stu-id="1bca4-111">Storing/transmitting plaintext passwords unencrypted is generally not secure.</span></span> <span data-ttu-id="1bca4-112">Du rekommenderas att säkra autentiseringsuppgifter genom att använda de tekniker som beskrivs senare i det här avsnittet.</span><span class="sxs-lookup"><span data-stu-id="1bca4-112">Securing credentials by using the techniques covered later in this topic is recommended.</span></span>
> <span data-ttu-id="1bca4-113">Tjänsten Azure Automation DSC kan du centralt hantera autentiseringsuppgifter som ska kompileras i konfigurationer och lagras på ett säkert sätt.</span><span class="sxs-lookup"><span data-stu-id="1bca4-113">The Azure Automation DSC service allows you to centrally manage credentials to be compiled in configurations and stored securely.</span></span>
> <span data-ttu-id="1bca4-114">Mer information finns i: [kompilering av DSC-konfigurationer / Inloggningstillgångar](/azure/automation/automation-dsc-compile#credential-assets)</span><span class="sxs-lookup"><span data-stu-id="1bca4-114">For information, see: [Compiling DSC Configurations / Credential Assets](/azure/automation/automation-dsc-compile#credential-assets)</span></span>

<span data-ttu-id="1bca4-115">Följande är ett exempel på att skicka autentiseringsuppgifter med oformaterad text:</span><span class="sxs-lookup"><span data-stu-id="1bca4-115">The following is an example of passing plain text credentials:</span></span>

```powershell
#Prompt user for their credentials
#credentials will be unencrypted in the MOF
$promptedCreds = get-credential -Message "Please enter your credentials to generate a DSC MOF:"

# Store passwords in plaintext, in the document itself
# will also be stored in plaintext in the mof
$password = "ThisIsAPlaintextPassword" | ConvertTo-SecureString -asPlainText -Force
$username = "User1"
[PSCredential] $credential = New-Object System.Management.Automation.PSCredential($username,$password)

# DSC requires explicit confirmation before storing passwords insecurely
$ConfigurationData = @{
    AllNodes = @(
        @{
            # The "*" means "all nodes named in ConfigData" so we don't have to repeat ourselves
            NodeName="*"
            PSDscAllowPlainTextPassword = $true
        },
        #however, each node still needs to be explicitly defined for "*" to have meaning
        @{
            NodeName = "TestMachine1"
        },
        #we can also use a property to define node-specific passwords, although this is no more secure
        @{
            NodeName = "TestMachine2";
            UserName = "User2"
            LocalPassword = "ThisIsYetAnotherPlaintextPassword"
        }
        )
}
configuration unencryptedPasswordDemo
{
    Node "TestMachine1"
    {
        # We use the plaintext password to generate a new account
        User User1
        {
            UserName = $username
            Password = $credential
            Description = "local account"
            Ensure = "Present"
            Disabled = $false
            PasswordNeverExpires = $true
            PasswordChangeRequired = $false
        }
        # We use the prompted password to add this account to the local admins group
        Group addToAdmin
        {
            # Ensure the user exists before we add the user to a group
            DependsOn = "[User]User1"
            Credential = $promptedCreds
            GroupName = "Administrators"
            Ensure = "Present"
            MembersToInclude = "User1"
        }
    }

    Node "TestMachine2"
    {
        # Now we'll use a node-specific password to this machine
        $password = $Node.LocalPass | ConvertTo-SecureString -asPlainText -Force
        $username = $node.UserName
        [PSCredential] $nodeCred = New-Object System.Management.Automation.PSCredential($username,$password)

        User User2
        {
            UserName = $username
            Password = $nodeCred
            Description = "local account"
            Ensure = "Present"
            Disabled = $false
            PasswordNeverExpires = $true
            PasswordChangeRequired = $false
        }

        Group addToAdmin
        {
            Credential = $domain
            GroupName = "Administrators"
            DependsOn = "[User]User2"
            Ensure = "Present"
            MembersToInclude = "User2"
        }
    }

}
# We declared the ConfigurationData in a local variable, but we need to pass it in to our configuration function
# We need to invoke the configuration function we created to generate a MOF
unencryptedPasswordDemo -ConfigurationData $ConfigurationData
# We need to pass the MOF to the machines we named.
#-wait: doesn't use jobs so we get blocked at the prompt until the configuration is done
#-verbose: so we can see what's going on and catch any errors
#-force: for testing purposes, I run start-dscconfiguration frequently + want to make sure i'm
#        not blocked by previous configurations that are still running
Start-DscConfiguration ./unencryptedPasswordDemo -verbose -wait -force
```

## <a name="handling-credentials-in-dsc"></a><span data-ttu-id="1bca4-116">Hantering av autentiseringsuppgifter i DSC</span><span class="sxs-lookup"><span data-stu-id="1bca4-116">Handling Credentials in DSC</span></span>

<span data-ttu-id="1bca4-117">Kör som-resurser för DSC-konfigurationen `Local System` som standard.</span><span class="sxs-lookup"><span data-stu-id="1bca4-117">DSC configuration resources run as `Local System` by default.</span></span>
<span data-ttu-id="1bca4-118">Men vissa resurser behöver autentiseringsuppgifter, till exempel när den `Package` resurs ska installera programvara under ett visst användarkonto.</span><span class="sxs-lookup"><span data-stu-id="1bca4-118">However, some resources need a credential, for example when the `Package` resource needs to install software under a specific user account.</span></span>

<span data-ttu-id="1bca4-119">Tidigare resurser används en hårdkodad `Credential` egenskapsnamn för att hantera detta.</span><span class="sxs-lookup"><span data-stu-id="1bca4-119">Earlier resources used a hard-coded `Credential` property name to handle this.</span></span>
<span data-ttu-id="1bca4-120">WMF 5.0 lagt till en automatisk `PsDscRunAsCredential` egenskap för alla resurser.</span><span class="sxs-lookup"><span data-stu-id="1bca4-120">WMF 5.0 added an automatic `PsDscRunAsCredential` property for all resources.</span></span>
<span data-ttu-id="1bca4-121">Information om hur du använder `PsDscRunAsCredential`, se [kör DSC med autentiseringsuppgifterna för användaren](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="1bca4-121">For information about using `PsDscRunAsCredential`, see [Running DSC with user credentials](runAsUser.md).</span></span>
<span data-ttu-id="1bca4-122">Nyare resurser och anpassade resurser kan använda automatiska egenskapen i stället för att skapa egna egenskapen för autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="1bca4-122">Newer resources and custom resources can use this automatic property instead of creating their own property for credentials.</span></span>

> [!NOTE]
> <span data-ttu-id="1bca4-123">Designen för vissa resurser som använder olika autentiseringsuppgifter för en specifik orsak och de har sina egna autentiseringsuppgifter egenskaper.</span><span class="sxs-lookup"><span data-stu-id="1bca4-123">The design of some resources are to use multiple credentials for a specific reason, and they will have their own credential properties.</span></span>

<span data-ttu-id="1bca4-124">För att hitta tillgängliga autentiseringsuppgifter egenskaperna för en resurs använder antingen `Get-DscResource -Name ResourceName -Syntax` eller Intellisense i ISE (`CTRL+SPACE`).</span><span class="sxs-lookup"><span data-stu-id="1bca4-124">To find the available credential properties on a resource use either `Get-DscResource -Name ResourceName -Syntax` or the Intellisense in the ISE (`CTRL+SPACE`).</span></span>

```powershell
PS C:\> Get-DscResource -Name Group -Syntax
Group [String] #ResourceName
{
    GroupName = [string]
    [Credential = [PSCredential]]
    [DependsOn = [string[]]]
    [Description = [string]]
    [Ensure = [string]{ Absent | Present }]
    [Members = [string[]]]
    [MembersToExclude = [string[]]]
    [MembersToInclude = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
}
```

<span data-ttu-id="1bca4-125">Det här exemplet används en [grupp](https://msdn.microsoft.com/en-us/powershell/dsc/groupresource) resurs från den `PSDesiredStateConfiguration` inbyggda DSC-Resursmodul.</span><span class="sxs-lookup"><span data-stu-id="1bca4-125">This example uses a [Group](https://msdn.microsoft.com/en-us/powershell/dsc/groupresource) resource from the `PSDesiredStateConfiguration` built-in DSC resource module.</span></span>
<span data-ttu-id="1bca4-126">Det kan skapa lokala grupper och lägga till eller ta bort medlemmar.</span><span class="sxs-lookup"><span data-stu-id="1bca4-126">It can create local groups and add or remove members.</span></span>
<span data-ttu-id="1bca4-127">Accepteras både den `Credential` egenskap och automatiskt `PsDscRunAsCredential` egenskapen.</span><span class="sxs-lookup"><span data-stu-id="1bca4-127">It accepts both the `Credential` property and the automatic `PsDscRunAsCredential` property.</span></span>
<span data-ttu-id="1bca4-128">Resursen som endast använder dock den `Credential` egenskapen.</span><span class="sxs-lookup"><span data-stu-id="1bca4-128">However, the resource only uses the `Credential` property.</span></span>

<span data-ttu-id="1bca4-129">Mer information om den `PsDscRunAsCredential` egenskap, se [kör DSC med autentiseringsuppgifterna för användaren](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="1bca4-129">For more information about the `PsDscRunAsCredential` property, see [Running DSC with user credentials](runAsUser.md).</span></span>

## <a name="example-the-group-resource-credential-property"></a><span data-ttu-id="1bca4-130">Exempel: Gruppresurser Credential-egenskapen</span><span class="sxs-lookup"><span data-stu-id="1bca4-130">Example: The Group resource Credential property</span></span>

<span data-ttu-id="1bca4-131">DSC körs under `Local System`, så den redan har behörighet att ändra lokala användare och grupper.</span><span class="sxs-lookup"><span data-stu-id="1bca4-131">DSC runs under `Local System`, so it already has permissions to change local users and groups.</span></span>
<span data-ttu-id="1bca4-132">Om den medlem som lagts till är ett lokalt konto, krävs inga autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="1bca4-132">If the member added is a local account, then no credential is necessary.</span></span>
<span data-ttu-id="1bca4-133">Om den `Group` resurs lägger till ett domänkonto till den lokala gruppen och sedan autentiseringsuppgifter krävs.</span><span class="sxs-lookup"><span data-stu-id="1bca4-133">If the `Group` resource adds a domain account to the local group, then a credential is necessary.</span></span>

<span data-ttu-id="1bca4-134">Anonyma frågor till Active Directory är inte tillåtna.</span><span class="sxs-lookup"><span data-stu-id="1bca4-134">Anonymous queries to Active Directory are not allowed.</span></span>
<span data-ttu-id="1bca4-135">Den `Credential` -egenskapen för den `Group` resursen är domänkontot som används för att fråga Active Directory.</span><span class="sxs-lookup"><span data-stu-id="1bca4-135">The `Credential` property of the `Group` resource is the domain account used to query Active Directory.</span></span>
<span data-ttu-id="1bca4-136">För de flesta ändamål det kan bero ett allmänt användarkonto som standard användarna kan *läsa* de flesta objekt i Active Directory.</span><span class="sxs-lookup"><span data-stu-id="1bca4-136">For most purposes this could be a generic user account, because by default users can *read* most of the objects in Active Directory.</span></span>

## <a name="example-configuration"></a><span data-ttu-id="1bca4-137">Exempel på konfiguration</span><span class="sxs-lookup"><span data-stu-id="1bca4-137">Example Configuration</span></span>

<span data-ttu-id="1bca4-138">Följande exempelkod använder DSC för att fylla i en lokal grupp med domän:</span><span class="sxs-lookup"><span data-stu-id="1bca4-138">The following example code uses DSC to populate a local group with a domain user:</span></span>

```powershell
Configuration DomainCredentialExample
{
    param
    (
        [PSCredential] $DomainCredential
    )
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    node localhost
    {
        Group DomainUserToLocalGroup
        {
            GroupName        = 'ApplicationAdmins'
            MembersToInclude = 'contoso\alice'
            Credential       = $DomainCredential
        }
    }
}

$cred = Get-Credential -UserName contoso\genericuser -Message "Password please"
DomainCredentialExample -DomainCredential $cred
```

<span data-ttu-id="1bca4-139">Den här koden genereras ett fel och ett varningsmeddelande:</span><span class="sxs-lookup"><span data-stu-id="1bca4-139">This code generates both an error and warning message:</span></span>

```
ConvertTo-MOFInstance : System.InvalidOperationException error processing
property 'Credential' OF TYPE 'Group': Converting and storing encrypted
passwords as plain text is not recommended. For more information on securing
credentials in MOF file, please refer to MSDN blog:
http://go.microsoft.com/fwlink/?LinkId=393729

At line:11 char:9
+   Group
At line:297 char:16
+     $aliasId = ConvertTo-MOFInstance $keywordName $canonicalizedValue
+                ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Write-Error], InvalidOperationException
    + FullyQualifiedErrorId : FailToProcessProperty,ConvertTo-MOFInstance

WARNING: It is not recommended to use domain credential for node 'localhost'.
In order to suppress the warning, you can add a property named
'PSDscAllowDomainUser' with a value of $true to your DSC configuration data
for node 'localhost'.
```

<span data-ttu-id="1bca4-140">Det här exemplet har två problem:</span><span class="sxs-lookup"><span data-stu-id="1bca4-140">This example has two issues:</span></span>
1. <span data-ttu-id="1bca4-141">Ett fel som förklarar att lösenord i klartext inte rekommenderas</span><span class="sxs-lookup"><span data-stu-id="1bca4-141">An error explains that plain text passwords are not recommended</span></span>
2. <span data-ttu-id="1bca4-142">En varning om att du inte använder en domän-autentiseringsuppgift</span><span class="sxs-lookup"><span data-stu-id="1bca4-142">A warning advises against using a domain credential</span></span>

## <a name="psdscallowplaintextpassword"></a><span data-ttu-id="1bca4-143">PsDscAllowPlainTextPassword</span><span class="sxs-lookup"><span data-stu-id="1bca4-143">PsDscAllowPlainTextPassword</span></span>

<span data-ttu-id="1bca4-144">Det första felmeddelandet har en URL till dokumentation.</span><span class="sxs-lookup"><span data-stu-id="1bca4-144">The first error message has a URL with documentation.</span></span>
<span data-ttu-id="1bca4-145">Den här länken förklarar hur du krypterar lösenord med en [ConfigurationData](https://msdn.microsoft.com/en-us/powershell/dsc/configdata) struktur och ett certifikat.</span><span class="sxs-lookup"><span data-stu-id="1bca4-145">This link explains how to encrypt passwords using a [ConfigurationData](https://msdn.microsoft.com/en-us/powershell/dsc/configdata) structure and a certificate.</span></span>
<span data-ttu-id="1bca4-146">Mer information om certifikat och DSC [läsa inlägget](http://aka.ms/certs4dsc).</span><span class="sxs-lookup"><span data-stu-id="1bca4-146">For more information on certificates and DSC [read this post](http://aka.ms/certs4dsc).</span></span>

<span data-ttu-id="1bca4-147">Om du vill framtvinga ett lösenord i oformaterad text resursen kräver den `PsDscAllowPlainTextPassword` nyckelord i konfigurationsdata avsnittet på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="1bca4-147">To force a plain text password, the resource requires the `PsDscAllowPlainTextPassword` keyword in the configuration data section as follows:</span></span>

```powershell
Configuration DomainCredentialExample
{
    param
    (
        [PSCredential] $DomainCredential
    )
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    node localhost
    {
        Group DomainUserToLocalGroup
        {
            GroupName        = 'ApplicationAdmins'
            MembersToInclude = 'contoso\alice'
            Credential       = $DomainCredential
        }
    }
}

$cd = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            PSDscAllowPlainTextPassword = $true
        }
    )
}

$cred = Get-Credential -UserName contoso\genericuser -Message "Password please"
DomainCredentialExample -DomainCredential $cred -ConfigurationData $cd
```

> [!NOTE]
> <span data-ttu-id="1bca4-148">`NodeName`Det går inte att vara lika med asterisk, en specifik nod-namn är obligatoriskt.</span><span class="sxs-lookup"><span data-stu-id="1bca4-148">`NodeName` cannot equal asterisk, a specific node name is mandatory.</span></span>

<span data-ttu-id="1bca4-149">**Microsoft avråder för att undvika lösenord på grund av en stor säkerhetsrisk.**</span><span class="sxs-lookup"><span data-stu-id="1bca4-149">**Microsoft advises to avoid plain text passwords due to the significant security risk.**</span></span>

<span data-ttu-id="1bca4-150">Ett undantag är när du använder tjänsten Azure Automation DSC, eftersom data lagras alltid krypterad (under överföring i vila i tjänsten och i vila på noden).</span><span class="sxs-lookup"><span data-stu-id="1bca4-150">An exception would be when using the Azure Automation DSC service, only because the data is always stored encrypted (in transit, at rest in the service, and at rest on the node).</span></span>

## <a name="domain-credentials"></a><span data-ttu-id="1bca4-151">Domain Credentials</span><span class="sxs-lookup"><span data-stu-id="1bca4-151">Domain Credentials</span></span>

<span data-ttu-id="1bca4-152">Kör exempel konfigurationsskript igen (med eller utan kryptering) fortfarande genererar den varning som använder en domän-konto för en autentiseringsuppgift inte rekommenderas.</span><span class="sxs-lookup"><span data-stu-id="1bca4-152">Running the example configuration script again (with or without encryption), still generates the warning that using a domain account for a credential is not recommended.</span></span>
<span data-ttu-id="1bca4-153">Med ett lokalt konto eliminerar eventuell exponering av autentiseringsuppgifter för domänen som kan användas på andra servrar.</span><span class="sxs-lookup"><span data-stu-id="1bca4-153">Using a local account eliminates potential exposure of domain credentials that could be used on other servers.</span></span>

<span data-ttu-id="1bca4-154">**När du använder autentiseringsuppgifter med DSC-resurser, föredrar du ett lokalt konto under ett domänkonto när det är möjligt.**</span><span class="sxs-lookup"><span data-stu-id="1bca4-154">**When using credentials with DSC resources, prefer a local account over a domain account when possible.**</span></span>

<span data-ttu-id="1bca4-155">Om det finns en '\' eller ”@” i den `Username` egenskapen för autentiseringsuppgifter och sedan DSC ska behandla det som ett domänkonto.</span><span class="sxs-lookup"><span data-stu-id="1bca4-155">If there is a '\' or '@' in the `Username` property of the credential, then DSC will treat it as a domain account.</span></span>
<span data-ttu-id="1bca4-156">Det finns ett undantag för ”localhost”, ”127.0.0.1” och ”:: 1” i den som domändel av användarnamnet.</span><span class="sxs-lookup"><span data-stu-id="1bca4-156">There is an exception for "localhost", "127.0.0.1", and "::1" in the domain portion of the user name.</span></span>

## <a name="psdscallowdomainuser"></a><span data-ttu-id="1bca4-157">PSDscAllowDomainUser</span><span class="sxs-lookup"><span data-stu-id="1bca4-157">PSDscAllowDomainUser</span></span>

<span data-ttu-id="1bca4-158">I DSC `Group` resurs-exemplet ovan, frågar Active Directory-domänen *kräver* ett domänkonto.</span><span class="sxs-lookup"><span data-stu-id="1bca4-158">In the DSC `Group` resource example above, querying an Active Directory domain *requires* a domain account.</span></span>
<span data-ttu-id="1bca4-159">I det här fallet lägger du till den `PSDscAllowDomainUser` egenskapen till den `ConfigurationData` blockera på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="1bca4-159">In this case add the `PSDscAllowDomainUser` property to the `ConfigurationData` block as follows:</span></span>

```powershell
$cd = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            PSDscAllowDomainUser = $true
            # PSDscAllowPlainTextPassword = $true
            CertificateFile = "C:\PublicKeys\server1.cer"
        }
    )
}
```

<span data-ttu-id="1bca4-160">Nu skapar skriptet configuration MOF-filen med några fel eller varningar.</span><span class="sxs-lookup"><span data-stu-id="1bca4-160">Now the configuration script will generate the MOF file with no errors or warnings.</span></span>
