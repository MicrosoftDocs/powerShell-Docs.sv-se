---
ms.date: 07/06/2020
keywords: DSC, PowerShell, konfiguration, installation
title: Skydda MOF-filen
description: Den här artikeln beskriver hur du ser till att målnoden har krypterat MOF-filen.
ms.openlocfilehash: e8b495a5c3c18dca5cde29cbbcf7d3f3cdab8f48
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92662795"
---
# <a name="securing-the-mof-file"></a><span data-ttu-id="57743-104">Skydda MOF-filen</span><span class="sxs-lookup"><span data-stu-id="57743-104">Securing the MOF File</span></span>

> <span data-ttu-id="57743-105">Gäller för: Windows PowerShell 4,0, Windows PowerShell 5,0</span><span class="sxs-lookup"><span data-stu-id="57743-105">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="57743-106">DSC hanterar konfigurationen av serverklusternoder genom att använda information som lagras i en MOF-fil, där den lokala Configuration Manager (LCM) implementerar det önskade slut läget.</span><span class="sxs-lookup"><span data-stu-id="57743-106">DSC manages the configuration of server nodes by applying information stored in a MOF file, where the Local Configuration Manager (LCM) implements the desired end state.</span></span> <span data-ttu-id="57743-107">Eftersom den här filen innehåller information om konfigurationen är det viktigt att skydda den.</span><span class="sxs-lookup"><span data-stu-id="57743-107">Because this file contains the details of the configuration, it's important to keep it secure.</span></span> <span data-ttu-id="57743-108">Den här artikeln beskriver hur du ser till att målnoden har krypterat filen.</span><span class="sxs-lookup"><span data-stu-id="57743-108">This article describes how to ensure the target node has encrypted the file.</span></span>

<span data-ttu-id="57743-109">Från och med PowerShell version 5,0 krypteras hela MOF-filen som standard när den tillämpas på noden med hjälp av `Start-DSCConfiguration` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="57743-109">Beginning with PowerShell version 5.0, the entire MOF file is encrypted by default when it is applied to the node using the `Start-DSCConfiguration` cmdlet.</span></span> <span data-ttu-id="57743-110">Processen som beskrivs i den här artikeln krävs bara när du implementerar en lösning med protokollet för pull-protokollet om certifikat inte hanteras, för att se till att konfigurationer som hämtas av målnoden kan dekrypteras och läsas av systemet innan de tillämpas (till exempel den pull-tjänst som är tillgänglig i Windows Server).</span><span class="sxs-lookup"><span data-stu-id="57743-110">The process described in this article is required only when implementing a solution using the pull service protocol if certificates are not managed, to ensure configurations downloaded by the target node can be decrypted and read by the system before they are applied (for example, the pull service available in Windows Server).</span></span> <span data-ttu-id="57743-111">Noder som är registrerade för [Azure Automation DSC](/azure/automation/automation-dsc-overview) har automatiskt certifikat som installeras och hanteras av tjänsten utan att det krävs någon administrativ omkostnader.</span><span class="sxs-lookup"><span data-stu-id="57743-111">Nodes registered to [Azure Automation DSC](/azure/automation/automation-dsc-overview) will automatically have certificates installed and managed by the service with no administrative overhead required.</span></span>

> [!NOTE]
> <span data-ttu-id="57743-112">I det här avsnittet beskrivs certifikat som används för kryptering.</span><span class="sxs-lookup"><span data-stu-id="57743-112">This topic discusses certificates used for encryption.</span></span> <span data-ttu-id="57743-113">För kryptering räcker ett självsignerat certifikat, eftersom den privata nyckeln alltid hålls hemlig och kryptering innebär inte att dokumentet är tillförlitligt.</span><span class="sxs-lookup"><span data-stu-id="57743-113">For encryption, a self-signed certificate is sufficient, because the private key is always kept secret and encryption does not imply trust of the document.</span></span> <span data-ttu-id="57743-114">Självsignerade certifikat bör _inte_ användas för autentisering.</span><span class="sxs-lookup"><span data-stu-id="57743-114">Self-signed certificates should _not_ be used for authentication purposes.</span></span> <span data-ttu-id="57743-115">Du bör använda ett certifikat från en betrodd certifikat utfärdare (CA) i alla autentiserings syfte.</span><span class="sxs-lookup"><span data-stu-id="57743-115">You should use a certificate from a trusted Certification Authority (CA) for any authentication purposes.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="57743-116">Förutsättningar</span><span class="sxs-lookup"><span data-stu-id="57743-116">Prerequisites</span></span>

<span data-ttu-id="57743-117">Kontrol lera att du har följande för att kunna kryptera de autentiseringsuppgifter som används för att skydda en DSC-konfiguration:</span><span class="sxs-lookup"><span data-stu-id="57743-117">To successfully encrypt the credentials used to secure a DSC configuration, make sure you have the following:</span></span>

- <span data-ttu-id="57743-118">**Några sätt att utfärda och distribuera certifikat** .</span><span class="sxs-lookup"><span data-stu-id="57743-118">**Some means of issuing and distributing certificates** .</span></span> <span data-ttu-id="57743-119">I det här avsnittet och dess exempel förutsätter vi att du använder Active Directory certifikat utfärdare.</span><span class="sxs-lookup"><span data-stu-id="57743-119">This topic and its examples assume you are using Active Directory Certification Authority.</span></span> <span data-ttu-id="57743-120">Mer bakgrunds information om Active Directory Certificate Services finns i [Översikt över Active Directory Certificate Services](https://technet.microsoft.com/library/hh831740.aspx) och [Active Directory Certificate Services i Windows Server 2008](https://technet.microsoft.com/windowsserver/dd448615.aspx).</span><span class="sxs-lookup"><span data-stu-id="57743-120">For more background information on Active Directory Certificate Services, see [Active Directory Certificate Services Overview](https://technet.microsoft.com/library/hh831740.aspx) and [Active Directory Certificate Services in Windows Server 2008](https://technet.microsoft.com/windowsserver/dd448615.aspx).</span></span>
- <span data-ttu-id="57743-121">**Administrativ åtkomst till målnoden eller noder** .</span><span class="sxs-lookup"><span data-stu-id="57743-121">**Administrative access to the target node or nodes** .</span></span>
- <span data-ttu-id="57743-122">**Varje målnod har ett krypterat certifikat som har sparats i det personliga arkivet** .</span><span class="sxs-lookup"><span data-stu-id="57743-122">**Each target node has an encryption-capable certificate saved its Personal Store** .</span></span> <span data-ttu-id="57743-123">I Windows PowerShell är sökvägen till arkivet certifikat: \ LocalMachine\My.</span><span class="sxs-lookup"><span data-stu-id="57743-123">In Windows PowerShell, the path to the store is Cert:\LocalMachine\My.</span></span> <span data-ttu-id="57743-124">I exemplen i det här avsnittet används mallen "arbetsstations autentisering", som du hittar (tillsammans med andra certifikatmallar) på [standardmallarna för certifikat](https://technet.microsoft.com/library/cc740061(v=WS.10).aspx).</span><span class="sxs-lookup"><span data-stu-id="57743-124">The examples in this topic use the "workstation authentication" template, which you can find (along with other certificate templates) at [Default Certificate Templates](https://technet.microsoft.com/library/cc740061(v=WS.10).aspx).</span></span>
- <span data-ttu-id="57743-125">Om du kommer att köra den här konfigurationen på en annan dator än målnoden, **Exportera den offentliga nyckeln för certifikatet** och sedan importera den till datorn som du ska köra konfigurationen från.</span><span class="sxs-lookup"><span data-stu-id="57743-125">If you will be running this configuration on a computer other than the target node, **export the public key of the certificate** , and then import it to the computer you will run the configuration from.</span></span> <span data-ttu-id="57743-126">Se till att du endast exporterar den **offentliga** nyckeln. skydda den privata nyckeln.</span><span class="sxs-lookup"><span data-stu-id="57743-126">Make sure that you export only the **public** key; keep the private key secure.</span></span>

> [!NOTE]
> <span data-ttu-id="57743-127">Skript resurser har begränsningar när det kommer att krypteras.</span><span class="sxs-lookup"><span data-stu-id="57743-127">Script Resources have limitations when it comes to encryption.</span></span> <span data-ttu-id="57743-128">Mer information finns i [skript resurs](../reference/resources/windows/scriptResource.md#known-limitations)</span><span class="sxs-lookup"><span data-stu-id="57743-128">For more information, see [Script Resource](../reference/resources/windows/scriptResource.md#known-limitations)</span></span>

## <a name="overall-process"></a><span data-ttu-id="57743-129">Övergripande process</span><span class="sxs-lookup"><span data-stu-id="57743-129">Overall process</span></span>

 1. <span data-ttu-id="57743-130">Konfigurera certifikat, nycklar och tumavtrycken och se till att varje målnod har kopior av certifikatet och att konfigurations datorn har den offentliga nyckeln och tumavtryck.</span><span class="sxs-lookup"><span data-stu-id="57743-130">Set up the certificates, keys, and thumbprints, making sure that each target node has copies of the certificate and the configuration computer has the public key and thumbprint.</span></span>
 1. <span data-ttu-id="57743-131">Skapa ett konfigurations data block som innehåller sökvägen och tumavtrycket för den offentliga nyckeln.</span><span class="sxs-lookup"><span data-stu-id="57743-131">Create a configuration data block that contains the path and thumbprint of the public key.</span></span>
 1. <span data-ttu-id="57743-132">Skapa ett konfigurations skript som definierar den önskade konfigurationen för målnoden och ställer in dekryptering på målnoden genom att använda den lokala Konfigurations hanteraren för att dekryptera konfigurations data med hjälp av certifikatet och dess tumavtryck.</span><span class="sxs-lookup"><span data-stu-id="57743-132">Create a configuration script that defines your desired configuration for the target node and sets up decryption on the target nodes by commanding the Local Configuration manager to decrypt the configuration data using the certificate and its thumbprint.</span></span>
 1. <span data-ttu-id="57743-133">Kör konfigurationen, som anger de lokala Configuration Manager inställningarna och startar DSC-konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="57743-133">Run the configuration, which will set the Local Configuration Manager settings and start the DSC configuration.</span></span>

![Process flöde för kryptering av autentiseringsuppgifter](media/secureMOF/CredentialEncryptionDiagram1.png)

## <a name="certificate-requirements"></a><span data-ttu-id="57743-135">Certifikatkrav</span><span class="sxs-lookup"><span data-stu-id="57743-135">Certificate Requirements</span></span>

<span data-ttu-id="57743-136">För att anta kryptering av autentiseringsuppgifter måste ett offentligt nyckel certifikat vara tillgängligt på den _målnod_ som är **betrodd** av den dator som används för att redigera DSC-konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="57743-136">To enact credential encryption, a public key certificate must be available on the _Target Node_ that is **trusted** by the computer being used to author the DSC configuration.</span></span> <span data-ttu-id="57743-137">Det här certifikatet för den offentliga nyckeln har särskilda krav för att det ska kunna användas för kryptering av DSC-autentiseringsuppgifter:</span><span class="sxs-lookup"><span data-stu-id="57743-137">This public key certificate has specific requirements for it to be used for DSC credential encryption:</span></span>

1. <span data-ttu-id="57743-138">**Nyckel användning** :</span><span class="sxs-lookup"><span data-stu-id="57743-138">**Key Usage** :</span></span>
   - <span data-ttu-id="57743-139">Måste innehålla: ' KeyEncipherment ' och ' DataEncipherment '.</span><span class="sxs-lookup"><span data-stu-id="57743-139">Must contain: 'KeyEncipherment' and 'DataEncipherment'.</span></span>
   - <span data-ttu-id="57743-140">Får _inte_ innehålla: digital signatur.</span><span class="sxs-lookup"><span data-stu-id="57743-140">Should _not_ contain: 'Digital Signature'.</span></span>
1. <span data-ttu-id="57743-141">**Förbättrad nyckel användning** :</span><span class="sxs-lookup"><span data-stu-id="57743-141">**Enhanced Key Usage** :</span></span>
   - <span data-ttu-id="57743-142">Måste innehålla: dokument kryptering (1.3.6.1.4.1.311.80.1).</span><span class="sxs-lookup"><span data-stu-id="57743-142">Must contain: Document Encryption (1.3.6.1.4.1.311.80.1).</span></span>
   - <span data-ttu-id="57743-143">Får _inte_ innehålla: klientautentisering (1.3.6.1.5.5.7.3.2) och serverautentisering (1.3.6.1.5.5.7.3.1).</span><span class="sxs-lookup"><span data-stu-id="57743-143">Should _not_ contain: Client Authentication (1.3.6.1.5.5.7.3.2) and Server Authentication (1.3.6.1.5.5.7.3.1).</span></span>
1. <span data-ttu-id="57743-144">Den privata nyckeln för certifikatet finns på \* Target Node_.</span><span class="sxs-lookup"><span data-stu-id="57743-144">The Private Key for the certificate is available on the \*Target Node_.</span></span>
1. <span data-ttu-id="57743-145">**Providern** för certifikatet måste vara "Microsoft RSA SChannel Cryptographic Provider".</span><span class="sxs-lookup"><span data-stu-id="57743-145">The **Provider** for the certificate must be "Microsoft RSA SChannel Cryptographic Provider".</span></span>

> [!IMPORTANT]
> <span data-ttu-id="57743-146">Även om du kan använda ett certifikat som innehåller en nyckel användning av "Digital Signature" eller en av EKU för autentisering, så gör detta att krypterings nyckeln blir enklare att använda och sårbar för angrepp.</span><span class="sxs-lookup"><span data-stu-id="57743-146">Although you can use a certificate containing a Key Usage of 'Digital Signature' or one of the Authentication EKU's, this will enable the encryption key to be more easily misused and vulnerable to attack.</span></span> <span data-ttu-id="57743-147">Vi rekommenderar att du använder ett certifikat som har skapats specifikt för att skydda DSC-autentiseringsuppgifter som utesluter denna nyckel användning och EKU.</span><span class="sxs-lookup"><span data-stu-id="57743-147">So it is best practice to use a certificate created specifically for the purpose of securing DSC credentials that omits these Key Usage and EKUs.</span></span>

<span data-ttu-id="57743-148">Alla befintliga certifikat på _målnoden_ som uppfyller dessa villkor kan användas för att skydda DSC-autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="57743-148">Any existing certificate on the _Target Node_ that meets these criteria can be used to secure DSC credentials.</span></span>

## <a name="certificate-creation"></a><span data-ttu-id="57743-149">Skapa certifikat</span><span class="sxs-lookup"><span data-stu-id="57743-149">Certificate creation</span></span>

<span data-ttu-id="57743-150">Det finns två sätt som du kan vidta för att skapa och använda det krypterings certifikat som krävs (offentligt-privat nyckel par).</span><span class="sxs-lookup"><span data-stu-id="57743-150">There are two approaches you can take to create and use the required Encryption Certificate (public-private key pair).</span></span>

1. <span data-ttu-id="57743-151">Skapa den på **målnoden** och exportera bara den offentliga nyckeln till **redigerings noden**</span><span class="sxs-lookup"><span data-stu-id="57743-151">Create it on the **Target Node** and export just the public key to the **Authoring Node**</span></span>
1. <span data-ttu-id="57743-152">Skapa den på **noden redigering** och exportera hela nyckel paret till **målnoden**</span><span class="sxs-lookup"><span data-stu-id="57743-152">Create it on the **Authoring Node** and export the entire key pair to the **Target Node**</span></span>

<span data-ttu-id="57743-153">Metod 1 rekommenderas eftersom den privata nyckel som används för att dekryptera autentiseringsuppgifter i MOF kvar på målnoden.</span><span class="sxs-lookup"><span data-stu-id="57743-153">Method 1 is recommended because the private key used to decrypt credentials in the MOF stays on the Target Node at all times.</span></span>

### <a name="creating-the-certificate-on-the-target-node"></a><span data-ttu-id="57743-154">Skapar certifikatet på målnoden</span><span class="sxs-lookup"><span data-stu-id="57743-154">Creating the Certificate on the Target Node</span></span>

<span data-ttu-id="57743-155">Den privata nyckeln måste hållas hemlig, eftersom används för att dekryptera MOF på **målnoden det enklaste** sättet att göra det är att skapa certifikatet för den privata nyckeln på **målnoden** och kopiera det **offentliga nyckel certifikatet** till den dator som används för att redigera DSC-konfigurationen i en MOF-fil.</span><span class="sxs-lookup"><span data-stu-id="57743-155">The private key must be kept secret, because is used to decrypt the MOF on the **Target Node** The easiest way to do that is to create the private key certificate on the **Target Node** , and copy the **public key certificate** to the computer being used to author the DSC configuration into a MOF file.</span></span> <span data-ttu-id="57743-156">Följande exempel:</span><span class="sxs-lookup"><span data-stu-id="57743-156">The following example:</span></span>

1. <span data-ttu-id="57743-157">skapar ett certifikat på **målnoden**</span><span class="sxs-lookup"><span data-stu-id="57743-157">creates a certificate on the **Target node**</span></span>
1. <span data-ttu-id="57743-158">exporterar certifikatet för den offentliga nyckeln på **målnoden** .</span><span class="sxs-lookup"><span data-stu-id="57743-158">exports the public key certificate on the **Target node** .</span></span>
1. <span data-ttu-id="57743-159">importerar certifikatet för den offentliga nyckeln till **mitt** certifikat Arkiv på **noden redigering** .</span><span class="sxs-lookup"><span data-stu-id="57743-159">imports the public key certificate into the **my** certificate store on the **Authoring node** .</span></span>

#### <a name="on-the-target-node-create-and-export-the-certificate"></a><span data-ttu-id="57743-160">På målnoden: skapa och exportera certifikatet</span><span class="sxs-lookup"><span data-stu-id="57743-160">On the Target Node: create and export the certificate</span></span>

> <span data-ttu-id="57743-161">Målnod: Windows Server 2016 och Windows 10</span><span class="sxs-lookup"><span data-stu-id="57743-161">Target Node: Windows Server 2016 and Windows 10</span></span>

```powershell
# note: These steps need to be performed in an Administrator PowerShell session
$cert = New-SelfSignedCertificate -Type DocumentEncryptionCertLegacyCsp -DnsName 'DscEncryptionCert' -HashAlgorithm SHA256
# export the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
```

<span data-ttu-id="57743-162">När du har exporterat `DscPublicKey.cer` måste du kopiera den till **redigerings-noden** .</span><span class="sxs-lookup"><span data-stu-id="57743-162">Once exported, the `DscPublicKey.cer` would need to be copied to the **Authoring Node** .</span></span>

> <span data-ttu-id="57743-163">Målnod: Windows Server 2012 R2/Windows 8,1 och tidigare</span><span class="sxs-lookup"><span data-stu-id="57743-163">Target Node: Windows Server 2012 R2/Windows 8.1 and earlier</span></span>

> [!WARNING]
> <span data-ttu-id="57743-164">Eftersom `New-SelfSignedCertificate` cmdleten på Windows-operativsystem före Windows 10 och Windows Server 2016 inte stöder **typ** parametern, krävs en alternativ metod för att skapa det här certifikatet på dessa operativ system.</span><span class="sxs-lookup"><span data-stu-id="57743-164">Because the `New-SelfSignedCertificate` cmdlet on Windows Operating Systems prior to Windows 10 and Windows Server 2016 do not support the **Type** parameter, an alternate method of creating this certificate is required on these operating systems.</span></span> <span data-ttu-id="57743-165">I det här fallet kan du använda `makecert.exe` eller `certutil.exe` för att skapa certifikatet.</span><span class="sxs-lookup"><span data-stu-id="57743-165">In this case you can use `makecert.exe` or `certutil.exe` to create the certificate.</span></span> <span data-ttu-id="57743-166">En alternativ metod är att ladda ned [New-SelfSignedCertificateEx.ps1](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) -skriptet från Microsoft Script Center och använda det för att skapa certifikatet i stället:</span><span class="sxs-lookup"><span data-stu-id="57743-166">An alternate method is to download the [New-SelfSignedCertificateEx.ps1](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) script from Microsoft Script Center and use it to create the certificate instead:</span></span>

```powershell
# note: These steps need to be performed in an Administrator PowerShell session
# and in the folder that contains New-SelfSignedCertificateEx.ps1
. .\New-SelfSignedCertificateEx.ps1
New-SelfsignedCertificateEx `
    -Subject "CN=${ENV:ComputerName}" `
    -EKU 'Document Encryption' `
    -KeyUsage 'KeyEncipherment, DataEncipherment' `
    -SAN ${ENV:ComputerName} `
    -FriendlyName 'DSC Credential Encryption certificate' `
    -Exportable `
    -StoreLocation 'LocalMachine' `
    -KeyLength 2048 `
    -ProviderName 'Microsoft Enhanced Cryptographic Provider v1.0' `
    -AlgorithmName 'RSA' `
    -SignatureAlgorithm 'SHA256'
# Locate the newly created certificate
$Cert = Get-ChildItem -Path cert:\LocalMachine\My | Where-Object {
        ($_.FriendlyName -eq 'DSC Credential Encryption certificate') -and ($_.Subject -eq "CN=${ENV:ComputerName}")
    } | Select-Object -First 1
# export the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
```

<span data-ttu-id="57743-167">När du har exporterat ```DscPublicKey.cer``` måste du kopiera den till **redigerings-noden** .</span><span class="sxs-lookup"><span data-stu-id="57743-167">Once exported, the ```DscPublicKey.cer``` would need to be copied to the **Authoring Node** .</span></span>

#### <a name="on-the-authoring-node-import-the-certs-public-key"></a><span data-ttu-id="57743-168">På noden redigering: importera certifikatets offentliga nyckel</span><span class="sxs-lookup"><span data-stu-id="57743-168">On the Authoring Node: import the cert's public key</span></span>

```powershell
# Import to the my store
Import-Certificate -FilePath "$env:temp\DscPublicKey.cer" -CertStoreLocation Cert:\LocalMachine\My
```

### <a name="creating-the-certificate-on-the-authoring-node"></a><span data-ttu-id="57743-169">Skapa certifikatet på noden redigering</span><span class="sxs-lookup"><span data-stu-id="57743-169">Creating the Certificate on the Authoring Node</span></span>

<span data-ttu-id="57743-170">Alternativt kan du skapa krypterings certifikatet på **noden redigering** , som exporteras med den **privata nyckeln** som en PFX-fil och sedan importeras på **målnoden** .</span><span class="sxs-lookup"><span data-stu-id="57743-170">Alternately, the encryption certificate can be created on the **Authoring Node** , exported with the **private key** as a PFX file and then imported on the **Target Node** .</span></span> <span data-ttu-id="57743-171">Det här är den aktuella metoden för att implementera kryptering av DSC-autentiseringsuppgifter på _Nano Server_ .</span><span class="sxs-lookup"><span data-stu-id="57743-171">This is the current method for implementing DSC credential encryption on _Nano Server_ .</span></span> <span data-ttu-id="57743-172">Även om PFX är skyddat med ett lösen ord bör det hållas säkert under överföringen.</span><span class="sxs-lookup"><span data-stu-id="57743-172">Although the PFX is secured with a password it should be kept secure during transit.</span></span> <span data-ttu-id="57743-173">Följande exempel:</span><span class="sxs-lookup"><span data-stu-id="57743-173">The following example:</span></span>

1. <span data-ttu-id="57743-174">skapar ett certifikat på **noden redigering** .</span><span class="sxs-lookup"><span data-stu-id="57743-174">creates a certificate on the **Authoring node** .</span></span>
1. <span data-ttu-id="57743-175">exporterar certifikatet inklusive den privata nyckeln på **noden redigering** .</span><span class="sxs-lookup"><span data-stu-id="57743-175">exports the certificate including the private key on the **Authoring node** .</span></span>
1. <span data-ttu-id="57743-176">tar bort den privata nyckeln från **redigerings noden** , men behåller certifikatet för den offentliga nyckeln i **My** Store.</span><span class="sxs-lookup"><span data-stu-id="57743-176">removes the private key from the **Authoring node** , but keeps the public key certificate in the **my** store.</span></span>
1. <span data-ttu-id="57743-177">importerar det privata nyckel certifikatet till certifikat arkivet My (personal) på **målnoden** .</span><span class="sxs-lookup"><span data-stu-id="57743-177">imports the private key certificate into the My(Personal) certificate store on the **Target node** .</span></span>
   - <span data-ttu-id="57743-178">den måste läggas till i rot arkivet så att den är betrodd av **målnoden** .</span><span class="sxs-lookup"><span data-stu-id="57743-178">it must be added to the root store so that it will be trusted by the **Target node** .</span></span>

#### <a name="on-the-authoring-node-create-and-export-the-certificate"></a><span data-ttu-id="57743-179">På noden redigering: skapa och exportera certifikatet</span><span class="sxs-lookup"><span data-stu-id="57743-179">On the Authoring Node: create and export the certificate</span></span>

> <span data-ttu-id="57743-180">Målnod: Windows Server 2016 och Windows 10</span><span class="sxs-lookup"><span data-stu-id="57743-180">Target Node: Windows Server 2016 and Windows 10</span></span>

```powershell
# note: These steps need to be performed in an Administrator PowerShell session
$cert = New-SelfSignedCertificate -Type DocumentEncryptionCertLegacyCsp -DnsName 'DscEncryptionCert' -HashAlgorithm SHA256
# export the private key certificate
$mypwd = ConvertTo-SecureString -String "YOUR_PFX_PASSWD" -Force -AsPlainText
$cert | Export-PfxCertificate -FilePath "$env:temp\DscPrivateKey.pfx" -Password $mypwd -Force
# remove the private key certificate from the node but keep the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
$cert | Remove-Item -Force
Import-Certificate -FilePath "$env:temp\DscPublicKey.cer" -CertStoreLocation Cert:\LocalMachine\My
```

<span data-ttu-id="57743-181">När du har exporterat `DscPrivateKey.pfx` måste du kopiera den till **målnoden** .</span><span class="sxs-lookup"><span data-stu-id="57743-181">Once exported, the `DscPrivateKey.pfx` would need to be copied to the **Target Node** .</span></span>

> <span data-ttu-id="57743-182">Målnod: Windows Server 2012 R2/Windows 8,1 och tidigare</span><span class="sxs-lookup"><span data-stu-id="57743-182">Target Node: Windows Server 2012 R2/Windows 8.1 and earlier</span></span>

> [!WARNING]
> <span data-ttu-id="57743-183">Eftersom `New-SelfSignedCertificate` cmdleten på Windows-operativsystem före Windows 10 och Windows Server 2016 inte stöder **typ** parametern, krävs en alternativ metod för att skapa det här certifikatet på dessa operativ system.</span><span class="sxs-lookup"><span data-stu-id="57743-183">Because the `New-SelfSignedCertificate` cmdlet on Windows Operating Systems prior to Windows 10 and Windows Server 2016 do not support the **Type** parameter, an alternate method of creating this certificate is required on these operating systems.</span></span> <span data-ttu-id="57743-184">I det här fallet kan du använda `makecert.exe` eller `certutil.exe` för att skapa certifikatet.</span><span class="sxs-lookup"><span data-stu-id="57743-184">In this case you can use `makecert.exe` or `certutil.exe` to create the certificate.</span></span> <span data-ttu-id="57743-185">En alternativ metod är att ladda ned [New-SelfSignedCertificateEx.ps1](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) -skriptet från Microsoft Script Center och använda det för att skapa certifikatet i stället:</span><span class="sxs-lookup"><span data-stu-id="57743-185">An alternate method is to download the [New-SelfSignedCertificateEx.ps1](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) script from Microsoft Script Center and use it to create the certificate instead:</span></span>

```powershell
# note: These steps need to be performed in an Administrator PowerShell session
# and in the folder that contains New-SelfSignedCertificateEx.ps1
. .\New-SelfSignedCertificateEx.ps1
New-SelfsignedCertificateEx `
    -Subject "CN=${ENV:ComputerName}" `
    -EKU 'Document Encryption' `
    -KeyUsage 'KeyEncipherment, DataEncipherment' `
    -SAN ${ENV:ComputerName} `
    -FriendlyName 'DSC Credential Encryption certificate' `
    -Exportable `
    -StoreLocation 'LocalMachine' `
    -KeyLength 2048 `
    -ProviderName 'Microsoft Enhanced Cryptographic Provider v1.0' `
    -AlgorithmName 'RSA' `
    -SignatureAlgorithm 'SHA256'
# Locate the newly created certificate
$Cert = Get-ChildItem -Path cert:\LocalMachine\My | Where-Object {
        ($_.FriendlyName -eq 'DSC Credential Encryption certificate') -and ($_.Subject -eq "CN=${ENV:ComputerName}")
    } | Select-Object -First 1
# export the public key certificate
$mypwd = ConvertTo-SecureString -String "YOUR_PFX_PASSWD" -Force -AsPlainText
$cert | Export-PfxCertificate -FilePath "$env:temp\DscPrivateKey.pfx" -Password $mypwd -Force
# remove the private key certificate from the node but keep the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
$cert | Remove-Item -Force
Import-Certificate -FilePath "$env:temp\DscPublicKey.cer" -CertStoreLocation Cert:\LocalMachine\My
```

#### <a name="on-the-target-node-import-the-certs-private-key-as-a-trusted-root"></a><span data-ttu-id="57743-186">På målnoden: importera certifikatets privata nyckel som en betrodd rot</span><span class="sxs-lookup"><span data-stu-id="57743-186">On the Target Node: import the cert's private key as a trusted root</span></span>

```powershell
# Import to the root store so that it is trusted
$mypwd = ConvertTo-SecureString -String "YOUR_PFX_PASSWD" -Force -AsPlainText
Import-PfxCertificate -FilePath "$env:temp\DscPrivateKey.pfx" -CertStoreLocation Cert:\LocalMachine\My -Password $mypwd > $null
```

## <a name="configuration-data"></a><span data-ttu-id="57743-187">Konfigurationsdata</span><span class="sxs-lookup"><span data-stu-id="57743-187">Configuration data</span></span>

<span data-ttu-id="57743-188">Konfigurations data blocket definierar vilka mål noder som ska användas, om du vill kryptera autentiseringsuppgifterna, krypterings metoder och annan information.</span><span class="sxs-lookup"><span data-stu-id="57743-188">The configuration data block defines which target nodes to operate on, whether or not to encrypt the credentials, the means of encryption, and other information.</span></span> <span data-ttu-id="57743-189">Mer information om konfigurations data blocket finns i [avgränsa konfigurations-och miljö data](../configurations/configData.md).</span><span class="sxs-lookup"><span data-stu-id="57743-189">For more information on the configuration data block, see [Separating Configuration and Environment Data](../configurations/configData.md).</span></span>

<span data-ttu-id="57743-190">De element som kan konfigureras för varje nod som är relaterade till kryptering av autentiseringsuppgifter är:</span><span class="sxs-lookup"><span data-stu-id="57743-190">The elements that can be configured for each node that are related to credential encryption are:</span></span>

- <span data-ttu-id="57743-191">**Nodnamn** -namnet på den målnod som kryptering av autentiseringsuppgifter konfigureras för.</span><span class="sxs-lookup"><span data-stu-id="57743-191">**NodeName** - the name of the target node that the credential encryption is being configured for.</span></span>
- <span data-ttu-id="57743-192">**PsDscAllowPlainTextPassword** – anger om okrypterade autentiseringsuppgifter ska kunna skickas till den här noden.</span><span class="sxs-lookup"><span data-stu-id="57743-192">**PsDscAllowPlainTextPassword** - whether unencrypted credentials will be allowed to be passed to this node.</span></span> <span data-ttu-id="57743-193">Detta **rekommenderas inte** .</span><span class="sxs-lookup"><span data-stu-id="57743-193">This is **not recommended** .</span></span>
- <span data-ttu-id="57743-194">**Tumavtryck** -tumavtrycket för det certifikat som ska användas för att dekryptera AUTENTISERINGSUPPGIFTERNA i DSC-konfigurationen på _målnoden_ .</span><span class="sxs-lookup"><span data-stu-id="57743-194">**Thumbprint** - the thumbprint of the certificate that will be used to decrypt the credentials in the DSC Configuration on the _Target Node_ .</span></span> <span data-ttu-id="57743-195">**Det här certifikatet måste finnas i den lokala datorns certifikat Arkiv på målnoden.**</span><span class="sxs-lookup"><span data-stu-id="57743-195">**This certificate must exist in the Local Machine certificate store on the Target Node.**</span></span>
- <span data-ttu-id="57743-196">**CertificateFile** – certifikat filen (som endast innehåller den offentliga nyckeln) som ska användas för att kryptera autentiseringsuppgifterna för _målnoden_ .</span><span class="sxs-lookup"><span data-stu-id="57743-196">**CertificateFile** - the certificate file (containing the public key only) that should be used to encrypt the credentials for the _Target Node_ .</span></span> <span data-ttu-id="57743-197">Måste vara antingen en DER-kodad binär X. 509-eller Base-64-kodad X. 509-format certifikat fil.</span><span class="sxs-lookup"><span data-stu-id="57743-197">This must be either a DER encoded binary X.509 or Base-64 encoded X.509 format certificate file.</span></span>

<span data-ttu-id="57743-198">Det här exemplet visar ett konfigurations data block som anger en målnod som agerar på namngivna targetNode, sökvägen till certifikat filen för offentlig nyckel (med namnet targetNode. cer) och tumavtrycket för den offentliga nyckeln.</span><span class="sxs-lookup"><span data-stu-id="57743-198">This example shows a configuration data block that specifies a target node to act on named targetNode, the path to the public key certificate file (named targetNode.cer), and the thumbprint for the public key.</span></span>

```powershell
$ConfigData= @{
    AllNodes = @(
            @{
                # The name of the node we are describing
                NodeName = "targetNode"

                # The path to the .cer file containing the
                # public key of the Encryption Certificate
                # used to encrypt credentials for this node
                CertificateFile = "C:\publicKeys\targetNode.cer"


                # The thumbprint of the Encryption Certificate
                # used to decrypt the credentials on target node
                Thumbprint = "AC23EA3A9E291A75757A556D0B71CBBF8C4F6FD8"
            }
        )
    }
```

## <a name="configuration-script"></a><span data-ttu-id="57743-199">Konfigurations skript</span><span class="sxs-lookup"><span data-stu-id="57743-199">Configuration script</span></span>

<span data-ttu-id="57743-200">I själva konfigurations skriptet använder du `PsCredential` parametern för att se till att autentiseringsuppgifterna lagras på kortast möjliga tid.</span><span class="sxs-lookup"><span data-stu-id="57743-200">In the configuration script itself, use the `PsCredential` parameter to ensure that credentials are stored for the shortest possible time.</span></span> <span data-ttu-id="57743-201">När du kör det angivna exemplet uppmanas du att ange autentiseringsuppgifter för DSC och sedan kryptera MOF-filen med hjälp av den CertificateFile som är kopplad till målnoden i konfigurations data blocket.</span><span class="sxs-lookup"><span data-stu-id="57743-201">When you run the supplied example, DSC will prompt you for credentials and then encrypt the MOF file using the CertificateFile that is associated with the target node in the configuration data block.</span></span> <span data-ttu-id="57743-202">I det här kod exemplet kopieras en fil från en resurs som är skyddad till en användare.</span><span class="sxs-lookup"><span data-stu-id="57743-202">This code example copies a file from a share that is secured to a user.</span></span>

```powershell
configuration CredentialEncryptionExample
{
    param(
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [PsCredential] $credential
    )

    Node $AllNodes.NodeName
    {
        File exampleFile
        {
            SourcePath = "\\Server\share\path\file.ext"
            DestinationPath = "C:\destinationPath"
            Credential = $credential
        }
    }
}
```

## <a name="setting-up-decryption"></a><span data-ttu-id="57743-203">Konfigurera dekryptering</span><span class="sxs-lookup"><span data-stu-id="57743-203">Setting up decryption</span></span>

<span data-ttu-id="57743-204">Innan [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) kan fungera måste du ange den lokala Configuration Manager på varje målnod som certifikatet ska använda för att dekryptera autentiseringsuppgifterna, med hjälp av CertificateID-resursen för att verifiera certifikatets tumavtryck.</span><span class="sxs-lookup"><span data-stu-id="57743-204">Before [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) can work, you have to tell the Local Configuration Manager on each target node which certificate to use to decrypt the credentials, using the CertificateID resource to verify the certificate's thumbprint.</span></span> <span data-ttu-id="57743-205">Den här exempel funktionen hittar lämpligt lokalt certifikat (du kanske måste anpassa det så att det hittar det exakta certifikat som du vill använda):</span><span class="sxs-lookup"><span data-stu-id="57743-205">This example function will find the appropriate local certificate (you might have to customize it so it will find the exact certificate you want to use):</span></span>

```powershell
# Get the certificate that works for encryption
function Get-LocalEncryptionCertificateThumbprint
{
    (dir Cert:\LocalMachine\my) | %{
        # Verify the certificate is for Encryption and valid
        if ($_.PrivateKey.KeyExchangeAlgorithm -and $_.Verify())
        {
            return $_.Thumbprint
        }
    }
}
```

<span data-ttu-id="57743-206">Med certifikatet som identifieras av sitt tumavtryck kan konfigurations skriptet uppdateras för att använda värdet:</span><span class="sxs-lookup"><span data-stu-id="57743-206">With the certificate identified by its thumbprint, the configuration script can be updated to use the value:</span></span>

```powershell
configuration CredentialEncryptionExample
{
    param(
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [PsCredential] $credential
    )

    Node $AllNodes.NodeName
    {
        File exampleFile
        {
            SourcePath = "\\Server\share\path\file.ext"
            DestinationPath = "C:\destinationPath"
            Credential = $credential
        }

        LocalConfigurationManager
        {
             CertificateId = $node.Thumbprint
        }
    }
}
```

## <a name="running-the-configuration"></a><span data-ttu-id="57743-207">Köra konfigurationen</span><span class="sxs-lookup"><span data-stu-id="57743-207">Running the configuration</span></span>

<span data-ttu-id="57743-208">I det här läget kan du köra konfigurationen, som kommer att skriva ut två filer:</span><span class="sxs-lookup"><span data-stu-id="57743-208">At this point, you can run the configuration, which will output two files:</span></span>

- <span data-ttu-id="57743-209">En `*.meta.mof ` fil som konfigurerar den lokala Configuration Manager för att dekryptera autentiseringsuppgifterna med hjälp av det certifikat som lagras i den lokala datorns Arkiv och som identifieras av dess tumavtryck.</span><span class="sxs-lookup"><span data-stu-id="57743-209">A `*.meta.mof `file that configures the Local Configuration Manager to decrypt the credentials using the certificate that is stored on the local machine store and identified by its thumbprint.</span></span>
  <span data-ttu-id="57743-210">[Set-DscLocalConfigurationManager](/powershell/module/psdesiredstateconfiguration/Set-DscLocalConfigurationManager) tillämpar `*.meta.mof ` filen.</span><span class="sxs-lookup"><span data-stu-id="57743-210">[Set-DscLocalConfigurationManager](/powershell/module/psdesiredstateconfiguration/Set-DscLocalConfigurationManager) applies the `*.meta.mof `file.</span></span>
- <span data-ttu-id="57743-211">En MOF-fil som faktiskt tillämpar konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="57743-211">A MOF file that actually applies the configuration.</span></span> <span data-ttu-id="57743-212">Start-DscConfiguration tillämpar konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="57743-212">Start-DscConfiguration applies the configuration.</span></span>

<span data-ttu-id="57743-213">Dessa kommandon utför dessa steg:</span><span class="sxs-lookup"><span data-stu-id="57743-213">These commands will accomplish those steps:</span></span>

```powershell
Write-Host "Generate DSC Configuration..."
CredentialEncryptionExample -ConfigurationData $ConfigData -OutputPath .\CredentialEncryptionExample

Write-Host "Setting up LCM to decrypt credentials..."
Set-DscLocalConfigurationManager .\CredentialEncryptionExample -Verbose

Write-Host "Starting Configuration..."
Start-DscConfiguration .\CredentialEncryptionExample -wait -Verbose
```

<span data-ttu-id="57743-214">I det här exemplet pushar DSC-konfigurationen till målnoden.</span><span class="sxs-lookup"><span data-stu-id="57743-214">This example would push the DSC configuration to the target node.</span></span> <span data-ttu-id="57743-215">DSC-konfigurationen kan också användas med en DSC-pull-server om en sådan finns tillgänglig.</span><span class="sxs-lookup"><span data-stu-id="57743-215">The DSC configuration can also be applied using a DSC Pull Server if one is available.</span></span>

<span data-ttu-id="57743-216">Mer information om hur du använder DSC-konfigurationer med en DSC-pull-server finns i [Konfigurera en DSC-pull-klient](pullClient.md) .</span><span class="sxs-lookup"><span data-stu-id="57743-216">See [Setting up a DSC pull client](pullClient.md) for more information on applying DSC configurations using a DSC Pull Server.</span></span>

## <a name="credential-encryption-module-example"></a><span data-ttu-id="57743-217">Modul för kryptering av autentiseringsuppgifter</span><span class="sxs-lookup"><span data-stu-id="57743-217">Credential Encryption Module Example</span></span>

<span data-ttu-id="57743-218">Här är ett fullständigt exempel som införlivar alla dessa steg, plus en hjälp-cmdlet som exporterar och kopierar offentliga nycklar:</span><span class="sxs-lookup"><span data-stu-id="57743-218">Here is a full example that incorporates all of these steps, plus a helper cmdlet that exports and copies the public keys:</span></span>

```powershell
# A simple example of using credentials
configuration CredentialEncryptionExample
{
    param(
        [Parameter(Mandatory=$true)]
        [ValidateNotNullorEmpty()]
        [PsCredential] $credential
    )

    Node $AllNodes.NodeName
    {
        File exampleFile
        {
            SourcePath = "\\server\share\file.txt"
            DestinationPath = "C:\Users\user"
            Credential = $credential
        }

        LocalConfigurationManager
        {
            CertificateId = $node.Thumbprint
        }
    }
}

# A Helper to invoke the configuration, with the correct public key
# To encrypt the configuration credentials
function Start-CredentialEncryptionExample
{
    [CmdletBinding()]
    param ($computerName)

    [string] $thumbprint = Get-EncryptionCertificate -computerName $computerName -Verbose
    Write-Verbose "using cert: $thumbprint"

    $certificatePath = join-path -Path "$env:SystemDrive\$script:publicKeyFolder" -childPath "$computername.EncryptionCertificate.cer"

    $ConfigData=    @{
        AllNodes = @(
                        @{
                            # The name of the node we are describing
                            NodeName = "$computerName"

                            # The path to the .cer file containing the
                            # public key of the Encryption Certificate
                            CertificateFile = "$certificatePath"

                            # The thumbprint of the Encryption Certificate
                            # used to decrypt the credentials
                            Thumbprint = $thumbprint
                        };
                    );
    }

    Write-Verbose "Generate DSC Configuration..."
    CredentialEncryptionExample -ConfigurationData $ConfigData -OutputPath .\CredentialEncryptionExample `
        -credential (Get-Credential -UserName "$env:USERDOMAIN\$env:USERNAME" -Message "Enter credentials for configuration")

    Write-Verbose "Setting up LCM to decrypt credentials..."
    Set-DscLocalConfigurationManager .\CredentialEncryptionExample -Verbose

    Write-Verbose "Starting Configuration..."
    Start-DscConfiguration .\CredentialEncryptionExample -wait -Verbose
}

#region HelperFunctions

# The folder name for the exported public keys
$script:publicKeyFolder = "publicKeys"

# Get the certificate that works for encryptions
function Get-EncryptionCertificate
{
    [CmdletBinding()]
    param ($computerName)

    $returnValue= Invoke-Command -ComputerName $computerName -ScriptBlock {
        $certificates = dir Cert:\LocalMachine\my

        $certificates | %{
                    # Verify the certificate is for Encryption and valid
            if ($_.PrivateKey.KeyExchangeAlgorithm -and $_.Verify())
            {
                # Create the folder to hold the exported public key
                $folder= Join-Path -Path $env:SystemDrive\ -ChildPath $using:publicKeyFolder
                if (! (Test-Path $folder))
                {
                    md $folder | Out-Null
                }

                # Export the public key to a well known location
                $certPath = Export-Certificate -Cert $_ -FilePath (Join-Path -path $folder -childPath "EncryptionCertificate.cer")

                # Return the thumbprint, and exported certificate path
                return @($_.Thumbprint,$certPath);
            }
        }
    }

    Write-Verbose "Identified and exported cert..."
    # Copy the exported certificate locally
    $destinationPath = join-path -Path "$env:SystemDrive\$script:publicKeyFolder" -childPath "$computername.EncryptionCertificate.cer"
    Copy-Item -Path (join-path -path \\$computername -childPath $returnValue[1].FullName.Replace(":","$"))  $destinationPath | Out-Null

    # Return the thumbprint
    return $returnValue[0]
}

Start-CredentialEncryptionExample
```
