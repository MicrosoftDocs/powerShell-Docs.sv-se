---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: Alternativ för autentiseringsuppgifter i konfigurationsdata
ms.openlocfilehash: 890dbd01ae37ca5834070961ffd693aa811dbaa2
ms.sourcegitcommit: 56b9be8503a5a1342c0b85b36f5ba6f57c281b63
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/21/2018
ms.locfileid: "43133831"
---
# <a name="credentials-options-in-configuration-data"></a><span data-ttu-id="e4882-103">Alternativ för autentiseringsuppgifter i konfigurationsdata</span><span class="sxs-lookup"><span data-stu-id="e4882-103">Credentials Options in Configuration Data</span></span>
><span data-ttu-id="e4882-104">Gäller för: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="e4882-104">Applies To: Windows PowerShell 5.0</span></span>

## <a name="plain-text-passwords-and-domain-users"></a><span data-ttu-id="e4882-105">Oformaterad textlösenord och domänanvändare</span><span class="sxs-lookup"><span data-stu-id="e4882-105">Plain Text Passwords and Domain Users</span></span>

<span data-ttu-id="e4882-106">DSC-konfigurationer som innehåller en autentiseringsuppgift utan kryptering genererar ett felmeddelande om lösenord i klartext.</span><span class="sxs-lookup"><span data-stu-id="e4882-106">DSC configurations containing a credential without encryption will generate an error message about plain text passwords.</span></span>
<span data-ttu-id="e4882-107">Dessutom genererar DSC en varning när du använder autentiseringsuppgifter för domänen.</span><span class="sxs-lookup"><span data-stu-id="e4882-107">Also, DSC will generate a warning when using domain credentials.</span></span>
<span data-ttu-id="e4882-108">Använda DSC-konfiguration data nyckelord för att ignorera dessa fel och varningar:</span><span class="sxs-lookup"><span data-stu-id="e4882-108">To suppress these error and warning messages use the DSC configuration data keywords:</span></span>
* <span data-ttu-id="e4882-109">**PsDscAllowPlainTextPassword**</span><span class="sxs-lookup"><span data-stu-id="e4882-109">**PsDscAllowPlainTextPassword**</span></span>
* <span data-ttu-id="e4882-110">**PsDscAllowDomainUser**</span><span class="sxs-lookup"><span data-stu-id="e4882-110">**PsDscAllowDomainUser**</span></span>

> [!NOTE]
> <span data-ttu-id="e4882-111">Lagra/överföring av okrypterade lösenord i klartext är inte säker.</span><span class="sxs-lookup"><span data-stu-id="e4882-111">Storing/transmitting plaintext passwords unencrypted is generally not secure.</span></span> <span data-ttu-id="e4882-112">Du rekommenderas att skydda autentiseringsuppgifter med hjälp av de metoder som beskrivs senare i det här avsnittet.</span><span class="sxs-lookup"><span data-stu-id="e4882-112">Securing credentials by using the techniques covered later in this topic is recommended.</span></span>
> <span data-ttu-id="e4882-113">Tjänsten Azure Automation DSC kan du centralt hantera autentiseringsuppgifter för att kompileras i konfigurationer och lagras på ett säkert sätt.</span><span class="sxs-lookup"><span data-stu-id="e4882-113">The Azure Automation DSC service allows you to centrally manage credentials to be compiled in configurations and stored securely.</span></span>
> <span data-ttu-id="e4882-114">Läs om: [kompilering av DSC-konfigurationer / Inloggningstillgångar](/azure/automation/automation-dsc-compile#credential-assets)</span><span class="sxs-lookup"><span data-stu-id="e4882-114">For information, see: [Compiling DSC Configurations / Credential Assets](/azure/automation/automation-dsc-compile#credential-assets)</span></span>

<span data-ttu-id="e4882-115">Följande är ett exempel på Skicka autentiseringsuppgifter med oformaterad text:</span><span class="sxs-lookup"><span data-stu-id="e4882-115">The following is an example of passing plain text credentials:</span></span>

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
        $password = $Node.LocalPassword | ConvertTo-SecureString -asPlainText -Force
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
            Credential = $promptedCreds
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

## <a name="handling-credentials-in-dsc"></a><span data-ttu-id="e4882-116">Hantering av autentiseringsuppgifter i DSC</span><span class="sxs-lookup"><span data-stu-id="e4882-116">Handling Credentials in DSC</span></span>

<span data-ttu-id="e4882-117">DSC-konfiguration resurser kör som- `Local System` som standard.</span><span class="sxs-lookup"><span data-stu-id="e4882-117">DSC configuration resources run as `Local System` by default.</span></span>
<span data-ttu-id="e4882-118">Men vissa resurser måste autentiseringsuppgifter, till exempel när den `Package` resurs ska installera programvara under ett visst användarkonto.</span><span class="sxs-lookup"><span data-stu-id="e4882-118">However, some resources need a credential, for example when the `Package` resource needs to install software under a specific user account.</span></span>

<span data-ttu-id="e4882-119">Resurser som tidigare använde ett hårdkodat `Credential` egenskapsnamn ska hantera detta.</span><span class="sxs-lookup"><span data-stu-id="e4882-119">Earlier resources used a hard-coded `Credential` property name to handle this.</span></span>
<span data-ttu-id="e4882-120">WMF 5.0 har lagts till en automatisk `PsDscRunAsCredential` egenskap för alla resurser.</span><span class="sxs-lookup"><span data-stu-id="e4882-120">WMF 5.0 added an automatic `PsDscRunAsCredential` property for all resources.</span></span>
<span data-ttu-id="e4882-121">Information om hur du använder `PsDscRunAsCredential`, se [kör DSC med autentiseringsuppgifterna för användaren](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="e4882-121">For information about using `PsDscRunAsCredential`, see [Running DSC with user credentials](runAsUser.md).</span></span>
<span data-ttu-id="e4882-122">Nyare resurser och anpassade resurser kan använda den här automatiska egenskapen istället för att skapa sina egna egenskapen för autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="e4882-122">Newer resources and custom resources can use this automatic property instead of creating their own property for credentials.</span></span>

> [!NOTE]
> <span data-ttu-id="e4882-123">Design av vissa resurser är använder olika autentiseringsuppgifter för en särskild anledning och de har sina egna autentiseringsegenskaper.</span><span class="sxs-lookup"><span data-stu-id="e4882-123">The design of some resources are to use multiple credentials for a specific reason, and they will have their own credential properties.</span></span>

<span data-ttu-id="e4882-124">För att hitta tillgängliga autentiseringsuppgifterna egenskaperna för en resurs använder antingen `Get-DscResource -Name ResourceName -Syntax` eller Intellisense i ISE (`CTRL+SPACE`).</span><span class="sxs-lookup"><span data-stu-id="e4882-124">To find the available credential properties on a resource use either `Get-DscResource -Name ResourceName -Syntax` or the Intellisense in the ISE (`CTRL+SPACE`).</span></span>

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

<span data-ttu-id="e4882-125">Det här exemplet används en [grupp](https://msdn.microsoft.com/powershell/dsc/groupresource) resurs från den `PSDesiredStateConfiguration` inbyggda modulen för DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="e4882-125">This example uses a [Group](https://msdn.microsoft.com/powershell/dsc/groupresource) resource from the `PSDesiredStateConfiguration` built-in DSC resource module.</span></span>
<span data-ttu-id="e4882-126">Det kan skapa lokala grupper och lägga till eller ta bort medlemmar.</span><span class="sxs-lookup"><span data-stu-id="e4882-126">It can create local groups and add or remove members.</span></span>
<span data-ttu-id="e4882-127">Den accepterar både den `Credential` egenskap och automatiskt `PsDscRunAsCredential` egenskapen.</span><span class="sxs-lookup"><span data-stu-id="e4882-127">It accepts both the `Credential` property and the automatic `PsDscRunAsCredential` property.</span></span>
<span data-ttu-id="e4882-128">Resursen endast använder dock den `Credential` egenskapen.</span><span class="sxs-lookup"><span data-stu-id="e4882-128">However, the resource only uses the `Credential` property.</span></span>

<span data-ttu-id="e4882-129">Mer information om den `PsDscRunAsCredential` egenskap, finns i [kör DSC med autentiseringsuppgifterna för användaren](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="e4882-129">For more information about the `PsDscRunAsCredential` property, see [Running DSC with user credentials](runAsUser.md).</span></span>

## <a name="example-the-group-resource-credential-property"></a><span data-ttu-id="e4882-130">Exempel: Gruppresurs Credential-egenskapen</span><span class="sxs-lookup"><span data-stu-id="e4882-130">Example: The Group resource Credential property</span></span>

<span data-ttu-id="e4882-131">DSC körs under `Local System`, så att den redan har behörighet att ändra lokala användare och grupper.</span><span class="sxs-lookup"><span data-stu-id="e4882-131">DSC runs under `Local System`, so it already has permissions to change local users and groups.</span></span>
<span data-ttu-id="e4882-132">Om medlemmen har lagts till är ett lokalt konto, krävs inga autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="e4882-132">If the member added is a local account, then no credential is necessary.</span></span>
<span data-ttu-id="e4882-133">Om den `Group` resurs lägger till ett nytt konto i den lokala gruppen och sedan en autentiseringsuppgift är nödvändigt.</span><span class="sxs-lookup"><span data-stu-id="e4882-133">If the `Group` resource adds a domain account to the local group, then a credential is necessary.</span></span>

<span data-ttu-id="e4882-134">Anonyma frågor till Active Directory är inte tillåtna.</span><span class="sxs-lookup"><span data-stu-id="e4882-134">Anonymous queries to Active Directory are not allowed.</span></span>
<span data-ttu-id="e4882-135">Den `Credential` egenskapen för den `Group` resurs är det domänkonto som används för att fråga Active Directory.</span><span class="sxs-lookup"><span data-stu-id="e4882-135">The `Credential` property of the `Group` resource is the domain account used to query Active Directory.</span></span>
<span data-ttu-id="e4882-136">För de flesta ändamål detta kan bero på ett generiskt användarkonto att som standard kan användare *läsa* de flesta objekt i Active Directory.</span><span class="sxs-lookup"><span data-stu-id="e4882-136">For most purposes this could be a generic user account, because by default users can *read* most of the objects in Active Directory.</span></span>

## <a name="example-configuration"></a><span data-ttu-id="e4882-137">Exempel på konfiguration</span><span class="sxs-lookup"><span data-stu-id="e4882-137">Example Configuration</span></span>

<span data-ttu-id="e4882-138">Följande exempelkod använder DSC för att fylla i en lokal grupp med en domänanvändare:</span><span class="sxs-lookup"><span data-stu-id="e4882-138">The following example code uses DSC to populate a local group with a domain user:</span></span>

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

<span data-ttu-id="e4882-139">Den här koden genererar ett fel och ett varningsmeddelande:</span><span class="sxs-lookup"><span data-stu-id="e4882-139">This code generates both an error and warning message:</span></span>

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

<span data-ttu-id="e4882-140">Det här exemplet har två problem:</span><span class="sxs-lookup"><span data-stu-id="e4882-140">This example has two issues:</span></span>
1. <span data-ttu-id="e4882-141">Felmeddelandet förklarar att lösenord i klartext inte rekommenderas</span><span class="sxs-lookup"><span data-stu-id="e4882-141">An error explains that plain text passwords are not recommended</span></span>
2. <span data-ttu-id="e4882-142">En varning om att du inte använder en domänautentiseringsuppgift</span><span class="sxs-lookup"><span data-stu-id="e4882-142">A warning advises against using a domain credential</span></span>

## <a name="psdscallowplaintextpassword"></a><span data-ttu-id="e4882-143">PsDscAllowPlainTextPassword</span><span class="sxs-lookup"><span data-stu-id="e4882-143">PsDscAllowPlainTextPassword</span></span>

<span data-ttu-id="e4882-144">Det första felmeddelandet har en URL med dokumentation.</span><span class="sxs-lookup"><span data-stu-id="e4882-144">The first error message has a URL with documentation.</span></span>
<span data-ttu-id="e4882-145">Den här länken förklarar hur du krypterar lösenord med hjälp av en [ConfigurationData](https://msdn.microsoft.com/powershell/dsc/configdata) struktur och ett certifikat.</span><span class="sxs-lookup"><span data-stu-id="e4882-145">This link explains how to encrypt passwords using a [ConfigurationData](https://msdn.microsoft.com/powershell/dsc/configdata) structure and a certificate.</span></span>
<span data-ttu-id="e4882-146">Mer information om certifikat och DSC [Läs det här inlägget](http://aka.ms/certs4dsc).</span><span class="sxs-lookup"><span data-stu-id="e4882-146">For more information on certificates and DSC [read this post](http://aka.ms/certs4dsc).</span></span>

<span data-ttu-id="e4882-147">Om du vill framtvinga ett lösenord i oformaterad text, resursen kräver den `PsDscAllowPlainTextPassword` nyckelord i konfigurationsdata avsnittet på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="e4882-147">To force a plain text password, the resource requires the `PsDscAllowPlainTextPassword` keyword in the configuration data section as follows:</span></span>

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
> <span data-ttu-id="e4882-148">`NodeName` Det går inte att vara lika med asterisk, en viss nod-namn är obligatoriskt.</span><span class="sxs-lookup"><span data-stu-id="e4882-148">`NodeName` cannot equal asterisk, a specific node name is mandatory.</span></span>

<span data-ttu-id="e4882-149">**Microsoft avråder för att undvika lösenord på grund av en stor säkerhetsrisk.**</span><span class="sxs-lookup"><span data-stu-id="e4882-149">**Microsoft advises to avoid plain text passwords due to the significant security risk.**</span></span>

## <a name="domain-credentials"></a><span data-ttu-id="e4882-150">Autentiseringsuppgifter för domänen</span><span class="sxs-lookup"><span data-stu-id="e4882-150">Domain Credentials</span></span>

<span data-ttu-id="e4882-151">Som exempel konfigurationsskript igen (med eller utan kryptering), fortfarande att genererar varning som använder en domän-konto för en autentiseringsuppgift inte rekommenderas.</span><span class="sxs-lookup"><span data-stu-id="e4882-151">Running the example configuration script again (with or without encryption), still generates the warning that using a domain account for a credential is not recommended.</span></span>
<span data-ttu-id="e4882-152">Med ett lokalt konto eliminerar potentiell exponering av autentiseringsuppgifter för domänen som kan användas på andra servrar.</span><span class="sxs-lookup"><span data-stu-id="e4882-152">Using a local account eliminates potential exposure of domain credentials that could be used on other servers.</span></span>

<span data-ttu-id="e4882-153">**När du använder autentiseringsuppgifter med DSC-resurser, föredrar du ett lokalt konto under ett domänkonto när det är möjligt.**</span><span class="sxs-lookup"><span data-stu-id="e4882-153">**When using credentials with DSC resources, prefer a local account over a domain account when possible.**</span></span>

<span data-ttu-id="e4882-154">Om det finns en ”\' eller ' @' i den `Username` egenskapen för autentiseringsuppgifter och sedan DSC behandlar det som ett domänkonto.</span><span class="sxs-lookup"><span data-stu-id="e4882-154">If there is a '\' or '@' in the `Username` property of the credential, then DSC will treat it as a domain account.</span></span>
<span data-ttu-id="e4882-155">Det finns ett undantag för ”localhost”, ”127.0.0.1” och ”:: 1” i domändelen i användarnamnet.</span><span class="sxs-lookup"><span data-stu-id="e4882-155">There is an exception for "localhost", "127.0.0.1", and "::1" in the domain portion of the user name.</span></span>

## <a name="psdscallowdomainuser"></a><span data-ttu-id="e4882-156">PSDscAllowDomainUser</span><span class="sxs-lookup"><span data-stu-id="e4882-156">PSDscAllowDomainUser</span></span>

<span data-ttu-id="e4882-157">I DSC `Group` resursexempel ovan, frågar ett Active Directory-domän *kräver* ett domänkonto.</span><span class="sxs-lookup"><span data-stu-id="e4882-157">In the DSC `Group` resource example above, querying an Active Directory domain *requires* a domain account.</span></span>
<span data-ttu-id="e4882-158">I det här fallet lägger du till den `PSDscAllowDomainUser` egenskap enligt den `ConfigurationData` blockera på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="e4882-158">In this case add the `PSDscAllowDomainUser` property to the `ConfigurationData` block as follows:</span></span>

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

<span data-ttu-id="e4882-159">Nu genererar konfigurationsskriptet MOF-filen med några fel eller varningar.</span><span class="sxs-lookup"><span data-stu-id="e4882-159">Now the configuration script will generate the MOF file with no errors or warnings.</span></span>
