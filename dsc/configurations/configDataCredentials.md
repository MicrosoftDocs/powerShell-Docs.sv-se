---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: Alternativ för autentiseringsuppgifter i konfigurationsdata
ms.openlocfilehash: 2a326e45bbbad7bd2362b66b88bf61b98df7b02e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080160"
---
# <a name="credentials-options-in-configuration-data"></a><span data-ttu-id="0447c-103">Alternativ för autentiseringsuppgifter i konfigurationsdata</span><span class="sxs-lookup"><span data-stu-id="0447c-103">Credentials Options in Configuration Data</span></span>

><span data-ttu-id="0447c-104">Gäller för: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="0447c-104">Applies To: Windows PowerShell 5.0</span></span>

## <a name="plain-text-passwords-and-domain-users"></a><span data-ttu-id="0447c-105">Oformaterad textlösenord och domänanvändare</span><span class="sxs-lookup"><span data-stu-id="0447c-105">Plain Text Passwords and Domain Users</span></span>

<span data-ttu-id="0447c-106">DSC-konfigurationer som innehåller en autentiseringsuppgift utan kryptering genererar ett felmeddelande om lösenord i klartext.</span><span class="sxs-lookup"><span data-stu-id="0447c-106">DSC configurations containing a credential without encryption will generate an error message about plain text passwords.</span></span>
<span data-ttu-id="0447c-107">Dessutom genererar DSC en varning när du använder autentiseringsuppgifter för domänen.</span><span class="sxs-lookup"><span data-stu-id="0447c-107">Also, DSC will generate a warning when using domain credentials.</span></span>
<span data-ttu-id="0447c-108">Använda DSC-konfiguration data nyckelord för att ignorera dessa fel och varningar:</span><span class="sxs-lookup"><span data-stu-id="0447c-108">To suppress these error and warning messages use the DSC configuration data keywords:</span></span>

- <span data-ttu-id="0447c-109">**PsDscAllowPlainTextPassword**</span><span class="sxs-lookup"><span data-stu-id="0447c-109">**PsDscAllowPlainTextPassword**</span></span>
- <span data-ttu-id="0447c-110">**PsDscAllowDomainUser**</span><span class="sxs-lookup"><span data-stu-id="0447c-110">**PsDscAllowDomainUser**</span></span>

> [!NOTE]
> <span data-ttu-id="0447c-111">Lagra/överföring av okrypterade lösenord i klartext är inte säker.</span><span class="sxs-lookup"><span data-stu-id="0447c-111">Storing/transmitting plaintext passwords unencrypted is generally not secure.</span></span> <span data-ttu-id="0447c-112">Du rekommenderas att skydda autentiseringsuppgifter med hjälp av de metoder som beskrivs senare i det här avsnittet.</span><span class="sxs-lookup"><span data-stu-id="0447c-112">Securing credentials by using the techniques covered later in this topic is recommended.</span></span>
> <span data-ttu-id="0447c-113">Tjänsten Azure Automation DSC kan du centralt hantera autentiseringsuppgifter för att kompileras i konfigurationer och lagras på ett säkert sätt.</span><span class="sxs-lookup"><span data-stu-id="0447c-113">The Azure Automation DSC service allows you to centrally manage credentials to be compiled in configurations and stored securely.</span></span>
> <span data-ttu-id="0447c-114">Läs om: [Kompilera DSC-konfigurationer / Autentiseringstillgångar](/azure/automation/automation-dsc-compile#credential-assets)</span><span class="sxs-lookup"><span data-stu-id="0447c-114">For information, see: [Compiling DSC Configurations / Credential Assets](/azure/automation/automation-dsc-compile#credential-assets)</span></span>

## <a name="handling-credentials-in-dsc"></a><span data-ttu-id="0447c-115">Hantering av autentiseringsuppgifter i DSC</span><span class="sxs-lookup"><span data-stu-id="0447c-115">Handling Credentials in DSC</span></span>

<span data-ttu-id="0447c-116">DSC-konfiguration resurser kör som- `Local System` som standard.</span><span class="sxs-lookup"><span data-stu-id="0447c-116">DSC configuration resources run as `Local System` by default.</span></span>
<span data-ttu-id="0447c-117">Men vissa resurser måste autentiseringsuppgifter, till exempel när den `Package` resurs ska installera programvara under ett visst användarkonto.</span><span class="sxs-lookup"><span data-stu-id="0447c-117">However, some resources need a credential, for example when the `Package` resource needs to install software under a specific user account.</span></span>

<span data-ttu-id="0447c-118">Resurser som tidigare använde ett hårdkodat `Credential` egenskapsnamn ska hantera detta.</span><span class="sxs-lookup"><span data-stu-id="0447c-118">Earlier resources used a hard-coded `Credential` property name to handle this.</span></span>
<span data-ttu-id="0447c-119">WMF 5.0 har lagts till en automatisk `PsDscRunAsCredential` egenskap för alla resurser.</span><span class="sxs-lookup"><span data-stu-id="0447c-119">WMF 5.0 added an automatic `PsDscRunAsCredential` property for all resources.</span></span>
<span data-ttu-id="0447c-120">Information om hur du använder `PsDscRunAsCredential`, se [kör DSC med autentiseringsuppgifterna för användaren](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="0447c-120">For information about using `PsDscRunAsCredential`, see [Running DSC with user credentials](runAsUser.md).</span></span>
<span data-ttu-id="0447c-121">Nyare resurser och anpassade resurser kan använda den här automatiska egenskapen istället för att skapa sina egna egenskapen för autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="0447c-121">Newer resources and custom resources can use this automatic property instead of creating their own property for credentials.</span></span>

> [!NOTE]
> <span data-ttu-id="0447c-122">Design av vissa resurser är använder olika autentiseringsuppgifter för en särskild anledning och de har sina egna autentiseringsegenskaper.</span><span class="sxs-lookup"><span data-stu-id="0447c-122">The design of some resources are to use multiple credentials for a specific reason, and they will have their own credential properties.</span></span>

<span data-ttu-id="0447c-123">För att hitta tillgängliga autentiseringsuppgifterna egenskaperna för en resurs använder antingen `Get-DscResource -Name ResourceName -Syntax` eller Intellisense i ISE (`CTRL+SPACE`).</span><span class="sxs-lookup"><span data-stu-id="0447c-123">To find the available credential properties on a resource use either `Get-DscResource -Name ResourceName -Syntax` or the Intellisense in the ISE (`CTRL+SPACE`).</span></span>

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

<span data-ttu-id="0447c-124">Det här exemplet används en [grupp](../resources/resources.md) resurs från den `PSDesiredStateConfiguration` inbyggda modulen för DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="0447c-124">This example uses a [Group](../resources/resources.md) resource from the `PSDesiredStateConfiguration` built-in DSC resource module.</span></span>
<span data-ttu-id="0447c-125">Det kan skapa lokala grupper och lägga till eller ta bort medlemmar.</span><span class="sxs-lookup"><span data-stu-id="0447c-125">It can create local groups and add or remove members.</span></span>
<span data-ttu-id="0447c-126">Den accepterar både den `Credential` egenskap och automatiskt `PsDscRunAsCredential` egenskapen.</span><span class="sxs-lookup"><span data-stu-id="0447c-126">It accepts both the `Credential` property and the automatic `PsDscRunAsCredential` property.</span></span>
<span data-ttu-id="0447c-127">Resursen endast använder dock den `Credential` egenskapen.</span><span class="sxs-lookup"><span data-stu-id="0447c-127">However, the resource only uses the `Credential` property.</span></span>

<span data-ttu-id="0447c-128">Mer information om den `PsDscRunAsCredential` egenskap, finns i [kör DSC med autentiseringsuppgifterna för användaren](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="0447c-128">For more information about the `PsDscRunAsCredential` property, see [Running DSC with user credentials](runAsUser.md).</span></span>

## <a name="example-the-group-resource-credential-property"></a><span data-ttu-id="0447c-129">Exempel: Gruppresurs Credential-egenskapen</span><span class="sxs-lookup"><span data-stu-id="0447c-129">Example: The Group resource Credential property</span></span>

<span data-ttu-id="0447c-130">DSC körs under `Local System`, så att den redan har behörighet att ändra lokala användare och grupper.</span><span class="sxs-lookup"><span data-stu-id="0447c-130">DSC runs under `Local System`, so it already has permissions to change local users and groups.</span></span>
<span data-ttu-id="0447c-131">Om medlemmen har lagts till är ett lokalt konto, krävs inga autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="0447c-131">If the member added is a local account, then no credential is necessary.</span></span>
<span data-ttu-id="0447c-132">Om den `Group` resurs lägger till ett nytt konto i den lokala gruppen och sedan en autentiseringsuppgift är nödvändigt.</span><span class="sxs-lookup"><span data-stu-id="0447c-132">If the `Group` resource adds a domain account to the local group, then a credential is necessary.</span></span>

<span data-ttu-id="0447c-133">Anonyma frågor till Active Directory är inte tillåtna.</span><span class="sxs-lookup"><span data-stu-id="0447c-133">Anonymous queries to Active Directory are not allowed.</span></span>
<span data-ttu-id="0447c-134">Den `Credential` egenskapen för den `Group` resurs är det domänkonto som används för att fråga Active Directory.</span><span class="sxs-lookup"><span data-stu-id="0447c-134">The `Credential` property of the `Group` resource is the domain account used to query Active Directory.</span></span>
<span data-ttu-id="0447c-135">För de flesta ändamål detta kan bero på ett generiskt användarkonto att som standard kan användare *läsa* de flesta objekt i Active Directory.</span><span class="sxs-lookup"><span data-stu-id="0447c-135">For most purposes this could be a generic user account, because by default users can *read* most of the objects in Active Directory.</span></span>

## <a name="example-configuration"></a><span data-ttu-id="0447c-136">Exempel på konfiguration</span><span class="sxs-lookup"><span data-stu-id="0447c-136">Example Configuration</span></span>

<span data-ttu-id="0447c-137">Följande exempelkod använder DSC för att fylla i en lokal grupp med en domänanvändare:</span><span class="sxs-lookup"><span data-stu-id="0447c-137">The following example code uses DSC to populate a local group with a domain user:</span></span>

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

<span data-ttu-id="0447c-138">Den här koden genererar ett fel och ett varningsmeddelande:</span><span class="sxs-lookup"><span data-stu-id="0447c-138">This code generates both an error and warning message:</span></span>

```
ConvertTo-MOFInstance : System.InvalidOperationException error processing property 'Credential' OF
TYPE 'Group': Converting and storing encrypted passwords as plain text is not recommended.
For more information on securing credentials in MOF file, please refer to MSDN blog:
https://go.microsoft.com/fwlink/?LinkId=393729

At line:11 char:9
+   Group
At line:341 char:16
+     $aliasId = ConvertTo-MOFInstance $keywordName $canonicalizedValue
+                ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Write-Error], InvalidOperationException
    + FullyQualifiedErrorId : FailToProcessProperty,ConvertTo-MOFInstance
WARNING: It is not recommended to use domain credential for node 'localhost'. In order to suppress
the warning, you can add a property named 'PSDscAllowDomainUser' with a value of $true to your DSC
configuration data for node 'localhost'.

Compilation errors occurred while processing configuration
'DomainCredentialExample'. Please review the errors reported in error stream and modify your
configuration code appropriately.
At C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\PSDesiredStateConfiguration.psm1:3917 char:5
+     throw $ErrorRecord
+     ~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (DomainCredentialExample:String) [], InvalidOperationException
    + FullyQualifiedErrorId : FailToProcessConfiguration
```

<span data-ttu-id="0447c-139">Det här exemplet har två problem:</span><span class="sxs-lookup"><span data-stu-id="0447c-139">This example has two issues:</span></span>

1. <span data-ttu-id="0447c-140">Felmeddelandet förklarar att lösenord i klartext inte rekommenderas</span><span class="sxs-lookup"><span data-stu-id="0447c-140">An error explains that plain text passwords are not recommended</span></span>
2. <span data-ttu-id="0447c-141">En varning om att du inte använder en domänautentiseringsuppgift</span><span class="sxs-lookup"><span data-stu-id="0447c-141">A warning advises against using a domain credential</span></span>

<span data-ttu-id="0447c-142">Flaggorna **PSDSCAllowPlainTextPassword** och **PSDSCAllowDomainUser** Ignorera fel- och varningsstatusmeddelanden som informerar användaren om risken i fråga.</span><span class="sxs-lookup"><span data-stu-id="0447c-142">The flags **PSDSCAllowPlainTextPassword** and **PSDSCAllowDomainUser** suppress the error and warning informing the user of the risk involved.</span></span>

## <a name="psdscallowplaintextpassword"></a><span data-ttu-id="0447c-143">PSDSCAllowPlainTextPassword</span><span class="sxs-lookup"><span data-stu-id="0447c-143">PSDSCAllowPlainTextPassword</span></span>

<span data-ttu-id="0447c-144">Det första felmeddelandet har en URL med dokumentation.</span><span class="sxs-lookup"><span data-stu-id="0447c-144">The first error message has a URL with documentation.</span></span>
<span data-ttu-id="0447c-145">Den här länken förklarar hur du krypterar lösenord med hjälp av en [ConfigurationData](./configData.md) struktur och ett certifikat.</span><span class="sxs-lookup"><span data-stu-id="0447c-145">This link explains how to encrypt passwords using a [ConfigurationData](./configData.md) structure and a certificate.</span></span>
<span data-ttu-id="0447c-146">Mer information om certifikat och DSC [Läs det här inlägget](http://aka.ms/certs4dsc).</span><span class="sxs-lookup"><span data-stu-id="0447c-146">For more information on certificates and DSC [read this post](http://aka.ms/certs4dsc).</span></span>

<span data-ttu-id="0447c-147">Om du vill framtvinga ett lösenord i oformaterad text, resursen kräver den `PsDscAllowPlainTextPassword` nyckelord i konfigurationsdata avsnittet på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="0447c-147">To force a plain text password, the resource requires the `PsDscAllowPlainTextPassword` keyword in the configuration data section as follows:</span></span>

```powershell
$password = "ThisIsAPlaintextPassword" | ConvertTo-SecureString -asPlainText -Force
$username = "contoso\Administrator"
[PSCredential] $credential = New-Object System.Management.Automation.PSCredential($username,$password)

Configuration DomainCredentialExample
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    node localhost
    {
        Group DomainUserToLocalGroup
        {
            GroupName        = 'ApplicationAdmins'
            MembersToInclude = 'contoso\alice'
            Credential       = $credential
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

DomainCredentialExample -ConfigurationData $cd
```

### <a name="localhostmof"></a><span data-ttu-id="0447c-148">localhost.mof</span><span class="sxs-lookup"><span data-stu-id="0447c-148">localhost.mof</span></span>

<span data-ttu-id="0447c-149">Den **PSDSCAllowPlainTextPassword** flaggan kräver att användaren bekräftar risken för att lagra lösenord i oformaterad text i en MOF-fil.</span><span class="sxs-lookup"><span data-stu-id="0447c-149">The **PSDSCAllowPlainTextPassword** flag requires that the user acknowledge the risk of storing plain text passwords in a MOF file.</span></span> <span data-ttu-id="0447c-150">I den genererade MOF-filen, även om en **PSCredential** objekt som innehåller en **SecureString** har använts, lösenorden visas fortfarande som oformaterad text.</span><span class="sxs-lookup"><span data-stu-id="0447c-150">In the generated MOF file, even though a **PSCredential** object containing a **SecureString** was used, the passwords still appear as plain text.</span></span> <span data-ttu-id="0447c-151">Det här är den enda gången som autentiseringsuppgifterna är tillgängliga.</span><span class="sxs-lookup"><span data-stu-id="0447c-151">This is the only time the credentials are exposed.</span></span> <span data-ttu-id="0447c-152">Få åtkomst till MOF-filen på så sätt får alla komma åt administratörskontot.</span><span class="sxs-lookup"><span data-stu-id="0447c-152">Gaining access to this MOF file gives anyone access to the Administrator account.</span></span>

```
/*
@TargetNode='localhost'
@GeneratedBy=Administrator
@GenerationDate=01/31/2019 06:43:13
@GenerationHost=Server01
*/

instance of MSFT_Credential as $MSFT_Credential1ref
{
Password = "ThisIsAPlaintextPassword";
 UserName = "Administrator";

};

instance of MSFT_GroupResource as $MSFT_GroupResource1ref
{
ResourceID = "[Group]DomainUserToLocalGroup";
 MembersToInclude = {
    "contoso\\alice"
};
 Credential = $MSFT_Credential1ref;
 SourceInfo = "::11::9::Group";
 GroupName = "ApplicationAdmins";
 ModuleName = "PSDesiredStateConfiguration";

ModuleVersion = "1.0";

 ConfigurationName = "DomainCredentialExample";

};
```

### <a name="credentials-in-transit-and-at-rest"></a><span data-ttu-id="0447c-153">Autentiseringsuppgifter vid överföring och i vila</span><span class="sxs-lookup"><span data-stu-id="0447c-153">Credentials in transit and at rest</span></span>

- <span data-ttu-id="0447c-154">Den **PSDscAllowPlainTextPassword** -flagga gör kompileringen av MOF-filer som innehåller lösenord i klartext.</span><span class="sxs-lookup"><span data-stu-id="0447c-154">The **PSDscAllowPlainTextPassword** flag allows the compilation of MOF files that contain passwords in clear text.</span></span>
  <span data-ttu-id="0447c-155">Vidta åtgärder vid lagring MOF-filer som innehåller lösenord i klartext.</span><span class="sxs-lookup"><span data-stu-id="0447c-155">Take precautions when storing MOF files containing clear text passwords.</span></span>
- <span data-ttu-id="0447c-156">När MOF-filen levereras till en nod i **Push** läge, WinRM krypterar kommunikation för att skydda lösenord i klartext, såvida inte du åsidosätta standardinställningen med den **AllowUnencrypted** parametern.</span><span class="sxs-lookup"><span data-stu-id="0447c-156">When the MOF file is delivered to a Node in **Push** mode, WinRM encrypts the communication to protect the clear text password unless you override the default with the **AllowUnencrypted** parameter.</span></span>
  - <span data-ttu-id="0447c-157">Kryptera MOF med ett certifikat skyddar MOF-filen i viloläge innan den har kopplats till en nod.</span><span class="sxs-lookup"><span data-stu-id="0447c-157">Encrypting the MOF with a certificate protects the MOF file at rest before it has been applied to a node.</span></span>
- <span data-ttu-id="0447c-158">I **Pull** läge, som du kan konfigurera Windows-hämtningsservern för att använda HTTPS för att kryptera trafik med hjälp av det protokoll som anges i Internet Information Server.</span><span class="sxs-lookup"><span data-stu-id="0447c-158">In **Pull** mode, you can configure Windows pull server to use HTTPS to encrypt traffic using the protocol specified in Internet Information Server.</span></span> <span data-ttu-id="0447c-159">Mer information finns i artiklarna [konfigurera en DSC-hämtningsklient](../pull-server/pullclient.md) och [skydda MOF-filer med certifikat](../pull-server/secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="0447c-159">For more information, see the articles [Setting up a DSC pull client](../pull-server/pullclient.md) and [Securing MOF files with Certificates](../pull-server/secureMOF.md).</span></span>
  - <span data-ttu-id="0447c-160">I den [Azure Automation-Tillståndskonfiguration](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview) service, Pull-trafik krypteras alltid.</span><span class="sxs-lookup"><span data-stu-id="0447c-160">In the [Azure Automation State Configuration](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview) service, Pull traffic is always encrypted.</span></span>
- <span data-ttu-id="0447c-161">På noden och MOF-filer krypteras på plats från och med PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="0447c-161">On the Node, MOF files are encrypted at rest Beginning in PowerShell 5.0.</span></span>
  - <span data-ttu-id="0447c-162">Filer är krypterade i vila i PowerShell 4.0 MOF om de är krypterade med ett certifikat när de skickas eller hämtas till noden.</span><span class="sxs-lookup"><span data-stu-id="0447c-162">In PowerShell 4.0 MOF files are unencrypted at rest unless they are encrypted with a certificate when they pushed or pulled to the Node.</span></span>

<span data-ttu-id="0447c-163">**Microsoft avråder för att undvika lösenord på grund av en stor säkerhetsrisk.**</span><span class="sxs-lookup"><span data-stu-id="0447c-163">**Microsoft advises to avoid plain text passwords due to the significant security risk.**</span></span>

## <a name="domain-credentials"></a><span data-ttu-id="0447c-164">Domain Credentials</span><span class="sxs-lookup"><span data-stu-id="0447c-164">Domain Credentials</span></span>

<span data-ttu-id="0447c-165">Som exempel konfigurationsskript igen (med eller utan kryptering), fortfarande att genererar varning som använder en domän-konto för en autentiseringsuppgift inte rekommenderas.</span><span class="sxs-lookup"><span data-stu-id="0447c-165">Running the example configuration script again (with or without encryption), still generates the warning that using a domain account for a credential is not recommended.</span></span>
<span data-ttu-id="0447c-166">Med ett lokalt konto eliminerar potentiell exponering av autentiseringsuppgifter för domänen som kan användas på andra servrar.</span><span class="sxs-lookup"><span data-stu-id="0447c-166">Using a local account eliminates potential exposure of domain credentials that could be used on other servers.</span></span>

<span data-ttu-id="0447c-167">**När du använder autentiseringsuppgifter med DSC-resurser, föredrar du ett lokalt konto under ett domänkonto när det är möjligt.**</span><span class="sxs-lookup"><span data-stu-id="0447c-167">**When using credentials with DSC resources, prefer a local account over a domain account when possible.**</span></span>

<span data-ttu-id="0447c-168">Om det finns en ”\\” eller ”\@” i den `Username` egenskapen för autentiseringsuppgifter och sedan DSC behandlar det som ett domänkonto.</span><span class="sxs-lookup"><span data-stu-id="0447c-168">If there is a '\\' or '\@' in the `Username` property of the credential, then DSC will treat it as a domain account.</span></span>
<span data-ttu-id="0447c-169">Det finns ett undantag för ”localhost”, ”127.0.0.1” och ”:: 1” i domändelen i användarnamnet.</span><span class="sxs-lookup"><span data-stu-id="0447c-169">There is an exception for "localhost", "127.0.0.1", and "::1" in the domain portion of the user name.</span></span>

## <a name="psdscallowdomainuser"></a><span data-ttu-id="0447c-170">PSDscAllowDomainUser</span><span class="sxs-lookup"><span data-stu-id="0447c-170">PSDscAllowDomainUser</span></span>

<span data-ttu-id="0447c-171">I DSC `Group` resursexempel ovan, frågar ett Active Directory-domän *kräver* ett domänkonto.</span><span class="sxs-lookup"><span data-stu-id="0447c-171">In the DSC `Group` resource example above, querying an Active Directory domain *requires* a domain account.</span></span>
<span data-ttu-id="0447c-172">I det här fallet lägger du till den `PSDscAllowDomainUser` egenskap enligt den `ConfigurationData` blockera på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="0447c-172">In this case add the `PSDscAllowDomainUser` property to the `ConfigurationData` block as follows:</span></span>

```powershell
$password = "ThisIsAPlaintextPassword" | ConvertTo-SecureString -asPlainText -Force
$username = "contoso\Administrator"
[PSCredential] $credential = New-Object System.Management.Automation.PSCredential($username,$password)

Configuration DomainCredentialExample
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    node localhost
    {
        Group DomainUserToLocalGroup
        {
            GroupName        = 'ApplicationAdmins'
            MembersToInclude = 'contoso\alice'
            Credential       = $credential
        }
    }
}

$cd = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            PSDscAllowDomainUser = $true
            PSDscAllowPlainTextPassword = $true
        }
    )
}

DomainCredentialExample -ConfigurationData $cd
```

<span data-ttu-id="0447c-173">Nu genererar konfigurationsskriptet MOF-filen med några fel eller varningar.</span><span class="sxs-lookup"><span data-stu-id="0447c-173">Now the configuration script will generate the MOF file with no errors or warnings.</span></span>
