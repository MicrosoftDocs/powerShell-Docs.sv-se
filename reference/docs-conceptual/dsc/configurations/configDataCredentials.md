---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: Alternativ för autentiseringsuppgifter i konfigurations data
ms.openlocfilehash: aac27f1ff4b4287b53745fa3b946fb3de84771c2
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "75870565"
---
# <a name="credentials-options-in-configuration-data"></a><span data-ttu-id="ca034-103">Alternativ för autentiseringsuppgifter i konfigurations data</span><span class="sxs-lookup"><span data-stu-id="ca034-103">Credentials Options in Configuration Data</span></span>

> <span data-ttu-id="ca034-104">Gäller för: Windows PowerShell 5,0</span><span class="sxs-lookup"><span data-stu-id="ca034-104">Applies To: Windows PowerShell 5.0</span></span>

## <a name="plain-text-passwords-and-domain-users"></a><span data-ttu-id="ca034-105">Lösen ord för oformaterad text och domän användare</span><span class="sxs-lookup"><span data-stu-id="ca034-105">Plain Text Passwords and Domain Users</span></span>

<span data-ttu-id="ca034-106">DSC-konfigurationer som innehåller en autentiseringsuppgift utan kryptering genererar ett fel meddelande om lösen ord med oformaterad text.</span><span class="sxs-lookup"><span data-stu-id="ca034-106">DSC configurations containing a credential without encryption will generate an error message about plain text passwords.</span></span> <span data-ttu-id="ca034-107">DSC kommer också att generera en varning när du använder domänautentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="ca034-107">Also, DSC will generate a warning when using domain credentials.</span></span> <span data-ttu-id="ca034-108">För att ignorera dessa fel och varnings meddelanden använder du nyckelorden DSC-konfigurations data:</span><span class="sxs-lookup"><span data-stu-id="ca034-108">To suppress these error and warning messages use the DSC configuration data keywords:</span></span>

- <span data-ttu-id="ca034-109">**PsDscAllowPlainTextPassword**</span><span class="sxs-lookup"><span data-stu-id="ca034-109">**PsDscAllowPlainTextPassword**</span></span>
- <span data-ttu-id="ca034-110">**PsDscAllowDomainUser**</span><span class="sxs-lookup"><span data-stu-id="ca034-110">**PsDscAllowDomainUser**</span></span>

> [!NOTE]
> <span data-ttu-id="ca034-111">Det är vanligt vis inte säkert att lagra/överföra okrypterade lösen ord okrypterade.</span><span class="sxs-lookup"><span data-stu-id="ca034-111">Storing/transmitting plaintext passwords unencrypted is generally not secure.</span></span> <span data-ttu-id="ca034-112">Att skydda autentiseringsuppgifter genom att använda de metoder som beskrivs senare i det här avsnittet rekommenderas.</span><span class="sxs-lookup"><span data-stu-id="ca034-112">Securing credentials by using the techniques covered later in this topic is recommended.</span></span> <span data-ttu-id="ca034-113">Med tjänsten Azure Automation DSC kan du centralt hantera autentiseringsuppgifter som ska kompileras i konfigurationer och lagras på ett säkert sätt.</span><span class="sxs-lookup"><span data-stu-id="ca034-113">The Azure Automation DSC service allows you to centrally manage credentials to be compiled in configurations and stored securely.</span></span> <span data-ttu-id="ca034-114">Mer information finns i: [kompilera DSC-konfigurationer/Credential-tillgångar](/azure/automation/automation-dsc-compile#credential-assets)</span><span class="sxs-lookup"><span data-stu-id="ca034-114">For information, see: [Compiling DSC Configurations / Credential Assets](/azure/automation/automation-dsc-compile#credential-assets)</span></span>

## <a name="handling-credentials-in-dsc"></a><span data-ttu-id="ca034-115">Hantera autentiseringsuppgifter i DSC</span><span class="sxs-lookup"><span data-stu-id="ca034-115">Handling Credentials in DSC</span></span>

<span data-ttu-id="ca034-116">DSC-konfigurations resurser `Local System` körs som standard.</span><span class="sxs-lookup"><span data-stu-id="ca034-116">DSC configuration resources run as `Local System` by default.</span></span> <span data-ttu-id="ca034-117">Vissa resurser behöver dock en autentiseringsuppgift, till exempel när `Package` resursen måste installera program vara under ett visst användar konto.</span><span class="sxs-lookup"><span data-stu-id="ca034-117">However, some resources need a credential, for example when the `Package` resource needs to install software under a specific user account.</span></span>

<span data-ttu-id="ca034-118">Tidigare resurser använde ett hårdkodat `Credential` egenskaps namn för att hantera detta.</span><span class="sxs-lookup"><span data-stu-id="ca034-118">Earlier resources used a hard-coded `Credential` property name to handle this.</span></span> <span data-ttu-id="ca034-119">WMF 5,0 har lagt till `PsDscRunAsCredential` en automatisk egenskap för alla resurser.</span><span class="sxs-lookup"><span data-stu-id="ca034-119">WMF 5.0 added an automatic `PsDscRunAsCredential` property for all resources.</span></span> <span data-ttu-id="ca034-120">Information om hur du `PsDscRunAsCredential`använder finns i [köra DSC med användarautentiseringsuppgifter](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="ca034-120">For information about using `PsDscRunAsCredential`, see [Running DSC with user credentials](runAsUser.md).</span></span> <span data-ttu-id="ca034-121">Nya resurser och anpassade resurser kan använda denna automatiska egenskap i stället för att skapa egna egenskaper för autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="ca034-121">Newer resources and custom resources can use this automatic property instead of creating their own property for credentials.</span></span>

> [!NOTE]
> <span data-ttu-id="ca034-122">Designen av vissa resurser är att använda flera autentiseringsuppgifter av en viss anledning och de har sina egna egenskaper för autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="ca034-122">The design of some resources are to use multiple credentials for a specific reason, and they will have their own credential properties.</span></span>

<span data-ttu-id="ca034-123">Om du vill hitta tillgängliga egenskaper för autentiseringsuppgifter på en resurs `Get-DscResource -Name ResourceName -Syntax` använder du antingen eller IntelliSense: en`CTRL+SPACE`i Ise ().</span><span class="sxs-lookup"><span data-stu-id="ca034-123">To find the available credential properties on a resource use either `Get-DscResource -Name ResourceName -Syntax` or the Intellisense in the ISE (`CTRL+SPACE`).</span></span>

```powershell
Get-DscResource -Name Group -Syntax
```

```Output
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

<span data-ttu-id="ca034-124">I det här exemplet används en [grupp](../resources/resources.md) resurs `PSDesiredStateConfiguration` från den inbyggda DSC-modulen.</span><span class="sxs-lookup"><span data-stu-id="ca034-124">This example uses a [Group](../resources/resources.md) resource from the `PSDesiredStateConfiguration` built-in DSC resource module.</span></span> <span data-ttu-id="ca034-125">Den kan skapa lokala grupper och lägga till eller ta bort medlemmar.</span><span class="sxs-lookup"><span data-stu-id="ca034-125">It can create local groups and add or remove members.</span></span> <span data-ttu-id="ca034-126">Både `Credential` egenskapen och den automatiska `PsDscRunAsCredential` egenskapen accepteras.</span><span class="sxs-lookup"><span data-stu-id="ca034-126">It accepts both the `Credential` property and the automatic `PsDscRunAsCredential` property.</span></span> <span data-ttu-id="ca034-127">Resursen använder dock endast- `Credential` egenskapen.</span><span class="sxs-lookup"><span data-stu-id="ca034-127">However, the resource only uses the `Credential` property.</span></span>

<span data-ttu-id="ca034-128">Mer information om `PsDscRunAsCredential` egenskapen finns i [köra DSC med](runAsUser.md)användarautentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="ca034-128">For more information about the `PsDscRunAsCredential` property, see [Running DSC with user credentials](runAsUser.md).</span></span>

## <a name="example-the-group-resource-credential-property"></a><span data-ttu-id="ca034-129">Exempel: egenskapen autentiseringsuppgifter för grupp resurs</span><span class="sxs-lookup"><span data-stu-id="ca034-129">Example: The Group resource Credential property</span></span>

<span data-ttu-id="ca034-130">DSC körs under `Local System`, så den har redan behörighet att ändra lokala användare och grupper.</span><span class="sxs-lookup"><span data-stu-id="ca034-130">DSC runs under `Local System`, so it already has permissions to change local users and groups.</span></span> <span data-ttu-id="ca034-131">Om medlemmen som har lagts till är ett lokalt konto krävs ingen autentiseringsuppgift.</span><span class="sxs-lookup"><span data-stu-id="ca034-131">If the member added is a local account, then no credential is necessary.</span></span> <span data-ttu-id="ca034-132">Om `Group` resursen lägger till ett domän konto i den lokala gruppen är en autentiseringsuppgift nödvändig.</span><span class="sxs-lookup"><span data-stu-id="ca034-132">If the `Group` resource adds a domain account to the local group, then a credential is necessary.</span></span>

<span data-ttu-id="ca034-133">Anonyma frågor till Active Directory är inte tillåtna.</span><span class="sxs-lookup"><span data-stu-id="ca034-133">Anonymous queries to Active Directory are not allowed.</span></span> <span data-ttu-id="ca034-134">`Group` Resursens `Credential` egenskap är det domän konto som används för att fråga Active Directory.</span><span class="sxs-lookup"><span data-stu-id="ca034-134">The `Credential` property of the `Group` resource is the domain account used to query Active Directory.</span></span> <span data-ttu-id="ca034-135">Detta kan vara ett allmänt användar konto, eftersom användare som standard kan *läsa* de flesta objekt i Active Directory.</span><span class="sxs-lookup"><span data-stu-id="ca034-135">For most purposes this could be a generic user account, because by default users can *read* most of the objects in Active Directory.</span></span>

## <a name="example-configuration"></a><span data-ttu-id="ca034-136">Exempel på konfiguration</span><span class="sxs-lookup"><span data-stu-id="ca034-136">Example Configuration</span></span>

<span data-ttu-id="ca034-137">I följande exempel kod används DSC för att fylla i en lokal grupp med en domän användare:</span><span class="sxs-lookup"><span data-stu-id="ca034-137">The following example code uses DSC to populate a local group with a domain user:</span></span>

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

<span data-ttu-id="ca034-138">Den här koden genererar både ett fel och ett varnings meddelande:</span><span class="sxs-lookup"><span data-stu-id="ca034-138">This code generates both an error and warning message:</span></span>

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

<span data-ttu-id="ca034-139">Det här exemplet har två problem:</span><span class="sxs-lookup"><span data-stu-id="ca034-139">This example has two issues:</span></span>

1. <span data-ttu-id="ca034-140">Ett fel förklarar att lösen ord för oformaterad text inte rekommenderas</span><span class="sxs-lookup"><span data-stu-id="ca034-140">An error explains that plain text passwords are not recommended</span></span>
2. <span data-ttu-id="ca034-141">En varning om att använda en domän behörighet</span><span class="sxs-lookup"><span data-stu-id="ca034-141">A warning advises against using a domain credential</span></span>

<span data-ttu-id="ca034-142">Flaggorna **PSDSCAllowPlainTextPassword** och **PSDSCAllowDomainUser** undertrycker felet och varningen som informerar användaren om risken.</span><span class="sxs-lookup"><span data-stu-id="ca034-142">The flags **PSDSCAllowPlainTextPassword** and **PSDSCAllowDomainUser** suppress the error and warning informing the user of the risk involved.</span></span>

## <a name="psdscallowplaintextpassword"></a><span data-ttu-id="ca034-143">PSDSCAllowPlainTextPassword</span><span class="sxs-lookup"><span data-stu-id="ca034-143">PSDSCAllowPlainTextPassword</span></span>

<span data-ttu-id="ca034-144">Det första fel meddelandet har en URL med dokumentation.</span><span class="sxs-lookup"><span data-stu-id="ca034-144">The first error message has a URL with documentation.</span></span> <span data-ttu-id="ca034-145">Den här länken förklarar hur du krypterar lösen ord med hjälp av en [ConfigurationData](./configData.md) -struktur och ett certifikat.</span><span class="sxs-lookup"><span data-stu-id="ca034-145">This link explains how to encrypt passwords using a [ConfigurationData](./configData.md) structure and a certificate.</span></span> <span data-ttu-id="ca034-146">Mer information om certifikat och DSC [finns i det här inlägget](https://aka.ms/certs4dsc).</span><span class="sxs-lookup"><span data-stu-id="ca034-146">For more information on certificates and DSC [read this post](https://aka.ms/certs4dsc).</span></span>

<span data-ttu-id="ca034-147">För att framtvinga ett lösen ord för oformaterad text kräver resursen `PsDscAllowPlainTextPassword` nyckelordet i avsnittet konfigurations data på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="ca034-147">To force a plain text password, the resource requires the `PsDscAllowPlainTextPassword` keyword in the configuration data section as follows:</span></span>

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

### <a name="localhostmof"></a><span data-ttu-id="ca034-148">localhost. MOF</span><span class="sxs-lookup"><span data-stu-id="ca034-148">localhost.mof</span></span>

<span data-ttu-id="ca034-149">**PSDSCAllowPlainTextPassword** -flaggan kräver att användaren bekräftar risken för att lösen ord för oformaterad text ska lagras i en MOF-fil.</span><span class="sxs-lookup"><span data-stu-id="ca034-149">The **PSDSCAllowPlainTextPassword** flag requires that the user acknowledge the risk of storing plain text passwords in a MOF file.</span></span> <span data-ttu-id="ca034-150">I den genererade MOF-filen, även om ett **PSCredential** -objekt som innehåller en **SecureString** användes, visas lösen orden fortfarande som oformaterad text.</span><span class="sxs-lookup"><span data-stu-id="ca034-150">In the generated MOF file, even though a **PSCredential** object containing a **SecureString** was used, the passwords still appear as plain text.</span></span> <span data-ttu-id="ca034-151">Detta är den enda tidpunkt då autentiseringsuppgifterna exponeras.</span><span class="sxs-lookup"><span data-stu-id="ca034-151">This is the only time the credentials are exposed.</span></span> <span data-ttu-id="ca034-152">Om du får åtkomst till den här MOF-filen får vem som helst åtkomst till administratörs kontot.</span><span class="sxs-lookup"><span data-stu-id="ca034-152">Gaining access to this MOF file gives anyone access to the Administrator account.</span></span>

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

### <a name="credentials-in-transit-and-at-rest"></a><span data-ttu-id="ca034-153">Autentiseringsuppgifter vid överföring och i vila</span><span class="sxs-lookup"><span data-stu-id="ca034-153">Credentials in transit and at rest</span></span>

- <span data-ttu-id="ca034-154">Flaggan **PSDscAllowPlainTextPassword** tillåter KOMPILERING av MOF-filer som innehåller lösen ord i klartext.</span><span class="sxs-lookup"><span data-stu-id="ca034-154">The **PSDscAllowPlainTextPassword** flag allows the compilation of MOF files that contain passwords in clear text.</span></span> <span data-ttu-id="ca034-155">Vidta försiktighets åtgärder när du lagrar MOF-filer som innehåller lösen ord för klartext.</span><span class="sxs-lookup"><span data-stu-id="ca034-155">Take precautions when storing MOF files containing clear text passwords.</span></span>
- <span data-ttu-id="ca034-156">När MOF-filen levereras till en nod i **push** -läge krypterar WinRM kommunikationen för att skydda lösen ordet för klartext om du inte åsidosätter standardvärdet med parametern **AllowUnencrypted** .</span><span class="sxs-lookup"><span data-stu-id="ca034-156">When the MOF file is delivered to a Node in **Push** mode, WinRM encrypts the communication to protect the clear text password unless you override the default with the **AllowUnencrypted** parameter.</span></span>
  - <span data-ttu-id="ca034-157">Kryptering av MOF med ett certifikat skyddar MOF-filen i vila innan den tillämpas på en nod.</span><span class="sxs-lookup"><span data-stu-id="ca034-157">Encrypting the MOF with a certificate protects the MOF file at rest before it has been applied to a node.</span></span>
- <span data-ttu-id="ca034-158">I **pull** -läge kan du konfigurera Windows pull server för att använda HTTPS för att kryptera trafik med protokollet som anges i Internet Information Server.</span><span class="sxs-lookup"><span data-stu-id="ca034-158">In **Pull** mode, you can configure Windows pull server to use HTTPS to encrypt traffic using the protocol specified in Internet Information Server.</span></span> <span data-ttu-id="ca034-159">Mer information finns i artikeln om att konfigurera [en DSC-pull-klient](../pull-server/pullclient.md) och [skydda MOF-filer med certifikat](../pull-server/secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="ca034-159">For more information, see the articles [Setting up a DSC pull client](../pull-server/pullclient.md) and [Securing MOF files with Certificates](../pull-server/secureMOF.md).</span></span>
  - <span data-ttu-id="ca034-160">Pull-trafik är alltid krypterad i [Azure Automation tillstånds konfigurations](/azure/automation/automation-dsc-overview) tjänsten.</span><span class="sxs-lookup"><span data-stu-id="ca034-160">In the [Azure Automation State Configuration](/azure/automation/automation-dsc-overview) service, Pull traffic is always encrypted.</span></span>
- <span data-ttu-id="ca034-161">På noden krypteras MOF-filer i vila från och med PowerShell 5,0.</span><span class="sxs-lookup"><span data-stu-id="ca034-161">On the Node, MOF files are encrypted at rest Beginning in PowerShell 5.0.</span></span>
  - <span data-ttu-id="ca034-162">I PowerShell 4,0 MOF-filer okrypterade i rest om de inte krypteras med ett certifikat när de skickas eller hämtas till noden.</span><span class="sxs-lookup"><span data-stu-id="ca034-162">In PowerShell 4.0 MOF files are unencrypted at rest unless they are encrypted with a certificate when they pushed or pulled to the Node.</span></span>

<span data-ttu-id="ca034-163">**Microsoft rekommenderar att lösen ord för oformaterad text undviks på grund av en betydande säkerhets risk.**</span><span class="sxs-lookup"><span data-stu-id="ca034-163">**Microsoft advises to avoid plain text passwords due to the significant security risk.**</span></span>

## <a name="domain-credentials"></a><span data-ttu-id="ca034-164">Domänautentiseringsuppgifter</span><span class="sxs-lookup"><span data-stu-id="ca034-164">Domain Credentials</span></span>

<span data-ttu-id="ca034-165">Om du kör exempel konfigurations skriptet igen (med eller utan kryptering), genererar fortfarande varningen att ett domän konto för en autentiseringsuppgift inte rekommenderas.</span><span class="sxs-lookup"><span data-stu-id="ca034-165">Running the example configuration script again (with or without encryption), still generates the warning that using a domain account for a credential is not recommended.</span></span> <span data-ttu-id="ca034-166">Genom att använda ett lokalt konto elimineras potentiell exponering för domänautentiseringsuppgifter som kan användas på andra servrar.</span><span class="sxs-lookup"><span data-stu-id="ca034-166">Using a local account eliminates potential exposure of domain credentials that could be used on other servers.</span></span>

<span data-ttu-id="ca034-167">**När du använder autentiseringsuppgifter med DSC-resurser föredrar du ett lokalt konto över ett domän konto när det är möjligt.**</span><span class="sxs-lookup"><span data-stu-id="ca034-167">**When using credentials with DSC resources, prefer a local account over a domain account when possible.**</span></span>

<span data-ttu-id="ca034-168">Om det finns en\\eller\@i `Username` egenskapen för autentiseringsuppgiften, kommer DSC att behandla det som ett domän konto.</span><span class="sxs-lookup"><span data-stu-id="ca034-168">If there is a '\\' or '\@' in the `Username` property of the credential, then DSC will treat it as a domain account.</span></span> <span data-ttu-id="ca034-169">Det finns ett undantag för "localhost", "127.0.0.1" och ":: 1" i domän delen av användar namnet.</span><span class="sxs-lookup"><span data-stu-id="ca034-169">There is an exception for "localhost", "127.0.0.1", and "::1" in the domain portion of the user name.</span></span>

## <a name="psdscallowdomainuser"></a><span data-ttu-id="ca034-170">PSDscAllowDomainUser</span><span class="sxs-lookup"><span data-stu-id="ca034-170">PSDscAllowDomainUser</span></span>

<span data-ttu-id="ca034-171">I DSC `Group` -resursens exempel ovan *kräver* en förfrågan till en Active Directory domän ett domän konto.</span><span class="sxs-lookup"><span data-stu-id="ca034-171">In the DSC `Group` resource example above, querying an Active Directory domain *requires* a domain account.</span></span> <span data-ttu-id="ca034-172">I det här fallet lägger `PSDscAllowDomainUser` du till egenskapen `ConfigurationData` i blocket enligt följande:</span><span class="sxs-lookup"><span data-stu-id="ca034-172">In this case add the `PSDscAllowDomainUser` property to the `ConfigurationData` block as follows:</span></span>

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

<span data-ttu-id="ca034-173">Nu kommer konfigurations skriptet att generera MOF-filen utan fel eller varningar.</span><span class="sxs-lookup"><span data-stu-id="ca034-173">Now the configuration script will generate the MOF file with no errors or warnings.</span></span>
