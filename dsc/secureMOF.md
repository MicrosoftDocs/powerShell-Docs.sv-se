---
ms.date: 2017-10-31
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: Skydda MOF-filen
ms.openlocfilehash: fdb8fa17e9b5e92b56e0a62bf850529c241eee41
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/17/2018
---
# <a name="securing-the-mof-file"></a><span data-ttu-id="b296a-103">Skydda MOF-filen</span><span class="sxs-lookup"><span data-stu-id="b296a-103">Securing the MOF File</span></span>

><span data-ttu-id="b296a-104">Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="b296a-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="b296a-105">DSC hanterar konfigurationen av servernoder genom att använda informationen i en MOF-fil där den lokala Configuration Manager (MGM) implementerar tillståndet önskade resultatet.</span><span class="sxs-lookup"><span data-stu-id="b296a-105">DSC manages the configuration of server nodes by applying information stored in a MOF file, where the Local Configuration Manager (LCM) implements the desired end state.</span></span>
<span data-ttu-id="b296a-106">Eftersom den här filen innehåller information om konfigurationen, är det viktigt att skydda den.</span><span class="sxs-lookup"><span data-stu-id="b296a-106">Because this file contains the details of the configuration, it’s important to keep it secure.</span></span>
<span data-ttu-id="b296a-107">Det här avsnittet beskriver hur du målnoden har krypterade filen.</span><span class="sxs-lookup"><span data-stu-id="b296a-107">This topic describes how to ensure the target node has encrypted the file.</span></span>

<span data-ttu-id="b296a-108">Från och med PowerShell version 5.0, hela MOF-filen är krypterad som standard när den används på en nod med hjälp av den **Start DSCConfiguration** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b296a-108">Beginning with PowerShell version 5.0, the entire MOF file is encrypted by default when it is applied to the node using the **Start-DSCConfiguration** cmdlet.</span></span>
<span data-ttu-id="b296a-109">Processen som beskrivs i den här artikeln krävs bara när du implementerar en lösning med pull-tjänsten-protokollet om certifikat inte som hanteras så konfigurationer som hämtas av målnoden kan dekryptera och läsa av systemet innan de tillämpas (till exempel pull tjänsten finns i Windows Server).</span><span class="sxs-lookup"><span data-stu-id="b296a-109">The process described in this article is required only when implementing a solution using the pull service protocol if certificates are not managed, to ensure configurations downloaded by the target node can be decrypted and read by the system before they are applied (for example, the pull service available in Windows Server).</span></span>
<span data-ttu-id="b296a-110">Noder registrerad [Azure Automation DSC](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview) automatiskt har certifikat installerat och hanteras av tjänsten med inga administrativa kostnader krävs.</span><span class="sxs-lookup"><span data-stu-id="b296a-110">Nodes registered to [Azure Automation DSC](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview) will automatically have certificates installed and managed by the service with no administrative overhead required.</span></span>

><span data-ttu-id="b296a-111">**Obs:** det här avsnittet beskrivs certifikat som används för kryptering.</span><span class="sxs-lookup"><span data-stu-id="b296a-111">**Note:** This topic discusses certificates used for encryption.</span></span>
><span data-ttu-id="b296a-112">Ett självsignerat certifikat är tillräcklig för kryptering, eftersom den privata nyckeln sparas alltid hemlighet och kryptering innebär inte förtroende för dokumentet.</span><span class="sxs-lookup"><span data-stu-id="b296a-112">For encryption, a self-signed certificate is sufficient, because the private key is always kept secret and encryption does not imply trust of the document.</span></span>
><span data-ttu-id="b296a-113">Självsignerade certifikat bör *inte* ska användas för autentisering.</span><span class="sxs-lookup"><span data-stu-id="b296a-113">Self-signed certificates should *not* be used for authentication purposes.</span></span>
><span data-ttu-id="b296a-114">Du bör använda ett certifikat från en betrodd certifikatutfärdare (CA) för andra syften för autentisering.</span><span class="sxs-lookup"><span data-stu-id="b296a-114">You should use a certificate from a trusted Certification Authority (CA) for any authentication purposes.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b296a-115">Förutsättningar</span><span class="sxs-lookup"><span data-stu-id="b296a-115">Prerequisites</span></span>

<span data-ttu-id="b296a-116">För att kryptera har de autentiseringsuppgifter som används för att skydda en DSC-konfiguration, kontrollera att du har följande:</span><span class="sxs-lookup"><span data-stu-id="b296a-116">To successfully encrypt the credentials used to secure a DSC configuration, make sure you have the following:</span></span>

* <span data-ttu-id="b296a-117">**Vissa sätt för att utfärda och distribuera certifikat**.</span><span class="sxs-lookup"><span data-stu-id="b296a-117">**Some means of issuing and distributing certificates**.</span></span> <span data-ttu-id="b296a-118">Det här avsnittet och dess exempel förutsätter att du använder Active Directory-certifikatutfärdare.</span><span class="sxs-lookup"><span data-stu-id="b296a-118">This topic and its examples assume you are using Active Directory Certification Authority.</span></span> <span data-ttu-id="b296a-119">Mer bakgrundsinformation om Active Directory Certificate Services finns i avsnittet [Active Directory Certificate Services översikt](https://technet.microsoft.com/library/hh831740.aspx) och [Active Directory-certifikattjänster i Windows Server 2008](https://technet.microsoft.com/windowsserver/dd448615.aspx).</span><span class="sxs-lookup"><span data-stu-id="b296a-119">For more background information on Active Directory Certificate Services, see [Active Directory Certificate Services Overview](https://technet.microsoft.com/library/hh831740.aspx) and [Active Directory Certificate Services in Windows Server 2008](https://technet.microsoft.com/windowsserver/dd448615.aspx).</span></span>
* <span data-ttu-id="b296a-120">**Administrativ åtkomst till målnoden eller noder**.</span><span class="sxs-lookup"><span data-stu-id="b296a-120">**Administrative access to the target node or nodes**.</span></span>
* <span data-ttu-id="b296a-121">**Varje målnoden har kryptering-kompatibla certifikat sparade personliga arkivet**.</span><span class="sxs-lookup"><span data-stu-id="b296a-121">**Each target node has an encryption-capable certificate saved its Personal Store**.</span></span> <span data-ttu-id="b296a-122">Sökvägen till arkivet är i Windows PowerShell-Cert: \LocalMachine\My.</span><span class="sxs-lookup"><span data-stu-id="b296a-122">In Windows PowerShell, the path to the store is Cert:\LocalMachine\My.</span></span> <span data-ttu-id="b296a-123">Exemplen i det här avsnittet använder mallen ”autentisering av arbetsstation”, som du kan hitta (tillsammans med andra certifikatmallar) på [Standardcertifikatmallar](https://technet.microsoft.com/library/cc740061(v=WS.10).aspx).</span><span class="sxs-lookup"><span data-stu-id="b296a-123">The examples in this topic use the “workstation authentication” template, which you can find (along with other certificate templates) at [Default Certificate Templates](https://technet.microsoft.com/library/cc740061(v=WS.10).aspx).</span></span>
* <span data-ttu-id="b296a-124">Om du ska köra den här konfigurationen på en annan dator än målnoden **exportera den offentliga nyckeln för certifikatet**, och sedan importera den till den dator som du vill köra konfigurationen från.</span><span class="sxs-lookup"><span data-stu-id="b296a-124">If you will be running this configuration on a computer other than the target node, **export the public key of the certificate**, and then import it to the computer you will run the configuration from.</span></span> <span data-ttu-id="b296a-125">Kontrollera att du exporterar endast den **offentliga** nyckeln; skydda den privata nyckeln.</span><span class="sxs-lookup"><span data-stu-id="b296a-125">Make sure that you export only the **public** key; keep the private key secure.</span></span>

## <a name="overall-process"></a><span data-ttu-id="b296a-126">Övergripande processen</span><span class="sxs-lookup"><span data-stu-id="b296a-126">Overall process</span></span>

 1. <span data-ttu-id="b296a-127">Konfigurera certifikat, nycklar och tumavtryck, se till att varje målnoden har kopior av certifikat och konfiguration av datorn har den offentliga nyckeln och tumavtrycket.</span><span class="sxs-lookup"><span data-stu-id="b296a-127">Set up the certificates, keys, and thumbprints, making sure that each target node has copies of the certificate and the configuration computer has the public key and thumbprint.</span></span>
 2. <span data-ttu-id="b296a-128">Skapa ett configuration datablock som innehåller sökvägen och tumavtrycket för den offentliga nyckeln.</span><span class="sxs-lookup"><span data-stu-id="b296a-128">Create a configuration data block that contains the path and thumbprint of the public key.</span></span>
 3. <span data-ttu-id="b296a-129">Skapa ett konfigurationsskript som definierar konfigurationen för målnoden och ställer in dekryptering på målnoder av drar till sig den lokala Configuration manager för att dekryptera konfigurationsdata med hjälp av certifikatet och dess tumavtryck.</span><span class="sxs-lookup"><span data-stu-id="b296a-129">Create a configuration script that defines your desired configuration for the target node and sets up decryption on the target nodes by commanding the Local Configuration manager to decrypt the configuration data using the certificate and its thumbprint.</span></span>
 4. <span data-ttu-id="b296a-130">Kör sedan konfigurationen, vilket anger Local Configuration Manager-inställningar och starta DSC-konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="b296a-130">Run the configuration, which will set the Local Configuration Manager settings and start the DSC configuration.</span></span>

![Diagram1](images/CredentialEncryptionDiagram1.png)

## <a name="certificate-requirements"></a><span data-ttu-id="b296a-132">Certifikatkrav</span><span class="sxs-lookup"><span data-stu-id="b296a-132">Certificate Requirements</span></span>

<span data-ttu-id="b296a-133">Certifikatets offentliga nyckel för att du tillämpar kryptering av autentiseringsuppgifter måste vara tillgängligt på den _målnoden_ som **betrodda** för datorn som används för att skapa DSC-konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="b296a-133">To enact credential encryption, a public key certificate must be available on the _Target Node_ that is **trusted** by the computer being used to author the DSC configuration.</span></span>
<span data-ttu-id="b296a-134">Den här offentliga nyckelcertifikat har särskilda krav för att användas för kryptering av DSC-autentiseringsuppgifter:</span><span class="sxs-lookup"><span data-stu-id="b296a-134">This public key certificate has specific requirements for it to be used for DSC credential encryption:</span></span>
 1. <span data-ttu-id="b296a-135">**Nyckelanvändning**:</span><span class="sxs-lookup"><span data-stu-id="b296a-135">**Key Usage**:</span></span>
   - <span data-ttu-id="b296a-136">Måste innehålla: 'KeyEncipherment' och 'DataEncipherment'.</span><span class="sxs-lookup"><span data-stu-id="b296a-136">Must contain: 'KeyEncipherment' and 'DataEncipherment'.</span></span>
   - <span data-ttu-id="b296a-137">Ska _inte_ innehålla: ”Digital signatur”.</span><span class="sxs-lookup"><span data-stu-id="b296a-137">Should _not_ contain: 'Digital Signature'.</span></span>
 2. <span data-ttu-id="b296a-138">**Utökad nyckelanvändning**:</span><span class="sxs-lookup"><span data-stu-id="b296a-138">**Enhanced Key Usage**:</span></span>
   - <span data-ttu-id="b296a-139">Måste innehålla: dokumentkryptering (1.3.6.1.4.1.311.80.1).</span><span class="sxs-lookup"><span data-stu-id="b296a-139">Must contain: Document Encryption (1.3.6.1.4.1.311.80.1).</span></span>
   - <span data-ttu-id="b296a-140">Ska _inte_ innehålla: klientautentisering (1.3.6.1.5.5.7.3.2) och serverautentisering (1.3.6.1.5.5.7.3.1).</span><span class="sxs-lookup"><span data-stu-id="b296a-140">Should _not_ contain: Client Authentication (1.3.6.1.5.5.7.3.2) and Server Authentication (1.3.6.1.5.5.7.3.1).</span></span>
 3. <span data-ttu-id="b296a-141">Den privata nyckeln för certifikatet är tillgängligt på den \* mål Node_.</span><span class="sxs-lookup"><span data-stu-id="b296a-141">The Private Key for the certificate is available on the \*Target Node_.</span></span>
 4. <span data-ttu-id="b296a-142">Den **Provider** för certifikatet måste vara ”Microsoft RSA SChannel kryptografiprovider”.</span><span class="sxs-lookup"><span data-stu-id="b296a-142">The **Provider** for the certificate must be "Microsoft RSA SChannel Cryptographic Provider".</span></span>
 
><span data-ttu-id="b296a-143">**Rekommenderad praxis:** men du kan använda ett certifikat med som innehåller en nyckelanvändning i ”Digital signatur” eller något av Nyckelanvändning för klientautentisering, detta aktiverar krypteringsnyckeln ska vara enklare felanvända och sårbar för angrepp.</span><span class="sxs-lookup"><span data-stu-id="b296a-143">**Recommended Best Practice:** Although you can use a certificate with containing a Key Usage of 'Digital Signature' or one of the Authentication EKU's, this will enable the encryption key to be more easily misused and vulnerable to attack.</span></span> <span data-ttu-id="b296a-144">Det är därför bäst att använda ett certifikat som skapats specifikt för att skydda DSC-autentiseringsuppgifter som utesluter dessa nyckelanvändning och EKU.</span><span class="sxs-lookup"><span data-stu-id="b296a-144">So it is best practice to use a certificate created specifically for the purpose of securing DSC credentials that omits these Key Usage and EKUs.</span></span>
  
<span data-ttu-id="b296a-145">Alla befintliga certifikat på den _målnoden_ som uppfyller dessa villkor kan användas för att säkra DSC-referenser.</span><span class="sxs-lookup"><span data-stu-id="b296a-145">Any existing certificate on the _Target Node_ that meets these criteria can be used to secure DSC credentials.</span></span>

## <a name="certificate-creation"></a><span data-ttu-id="b296a-146">Skapande av certifikat</span><span class="sxs-lookup"><span data-stu-id="b296a-146">Certificate creation</span></span>

<span data-ttu-id="b296a-147">Det finns två metoder som du kan använda för att skapa och använda nödvändiga krypteringscertifikat (privat-offentligt nyckelpar).</span><span class="sxs-lookup"><span data-stu-id="b296a-147">There are two approaches you can take to create and use the required Encryption Certificate (public-private key pair).</span></span>

1. <span data-ttu-id="b296a-148">Skapa den på den **målnoden** och exportera den offentliga nyckeln till den **redigering nod**</span><span class="sxs-lookup"><span data-stu-id="b296a-148">Create it on the **Target Node** and export just the public key to the **Authoring Node**</span></span>
2. <span data-ttu-id="b296a-149">Skapa den på den **redigering nod** och exportera hela nyckelparet till den **målnod**</span><span class="sxs-lookup"><span data-stu-id="b296a-149">Create it on the **Authoring Node** and export the entire key pair to the **Target Node**</span></span>

<span data-ttu-id="b296a-150">Metod 1 rekommenderas eftersom den privata nyckeln används för att dekryptera autentiseringsuppgifterna i MOF finns kvar på målnoden vid alla tidpunkter.</span><span class="sxs-lookup"><span data-stu-id="b296a-150">Method 1 is recommended because the private key used to decrypt credentials in the MOF stays on the Target Node at all times.</span></span>


### <a name="creating-the-certificate-on-the-target-node"></a><span data-ttu-id="b296a-151">Skapa certifikatet på målnoden</span><span class="sxs-lookup"><span data-stu-id="b296a-151">Creating the Certificate on the Target Node</span></span>

<span data-ttu-id="b296a-152">Den privata nyckeln måste hållas hemliga eftersom används för att dekryptera MOF på den **målnoden** det enklaste sättet att göra det är att skapa certifikat för privata nyckel på den **målnoden**, och kopierar den  **Certifikatets offentliga nyckel** på datorn som används för att skapa DSC-konfigurationen till en MOF-fil.</span><span class="sxs-lookup"><span data-stu-id="b296a-152">The private key must be kept secret, because is used to decrypt the MOF on the **Target Node** The easiest way to do that is to create the private key certificate on the **Target Node**, and copy the **public key certificate** to the computer being used to author the DSC configuration into a MOF file.</span></span>
<span data-ttu-id="b296a-153">I följande exempel:</span><span class="sxs-lookup"><span data-stu-id="b296a-153">The following example:</span></span>
 1. <span data-ttu-id="b296a-154">skapar ett certifikat på den **målnod**</span><span class="sxs-lookup"><span data-stu-id="b296a-154">creates a certificate on the **Target node**</span></span>
 2. <span data-ttu-id="b296a-155">exporterar det offentliga nyckelcertifikatet på den **målnoden**.</span><span class="sxs-lookup"><span data-stu-id="b296a-155">exports the public key certificate on the **Target node**.</span></span>
 3. <span data-ttu-id="b296a-156">importerar det offentliga nyckelcertifikatet till den **min** certifikatarkivet på den **redigering nod**.</span><span class="sxs-lookup"><span data-stu-id="b296a-156">imports the public key certificate into the **my** certificate store on the **Authoring node**.</span></span>

#### <a name="on-the-target-node-create-and-export-the-certificate"></a><span data-ttu-id="b296a-157">På målnoden: skapa och exportera certifikatet</span><span class="sxs-lookup"><span data-stu-id="b296a-157">On the Target Node: create and export the certificate</span></span>
><span data-ttu-id="b296a-158">Målnoden: Windows Server 2016 och Windows 10</span><span class="sxs-lookup"><span data-stu-id="b296a-158">Target Node: Windows Server 2016 and Windows 10</span></span>

```powershell
# note: These steps need to be performed in an Administrator PowerShell session
$cert = New-SelfSignedCertificate -Type DocumentEncryptionCertLegacyCsp -DnsName 'DscEncryptionCert' -HashAlgorithm SHA256
# export the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
```
<span data-ttu-id="b296a-159">En gång exporterade den ```DscPublicKey.cer``` måste kopieras till den **redigering nod**.</span><span class="sxs-lookup"><span data-stu-id="b296a-159">Once exported, the ```DscPublicKey.cer``` would need to be copied to the **Authoring Node**.</span></span>

><span data-ttu-id="b296a-160">Målnoden: Windows Server 2012 R2/Windows 8.1 och tidigare</span><span class="sxs-lookup"><span data-stu-id="b296a-160">Target Node: Windows Server 2012 R2/Windows 8.1 and earlier</span></span>

<span data-ttu-id="b296a-161">Eftersom cmdlet New-SelfSignedCertificate på Windows-operativsystem före Windows 10 och Windows Server 2016 inte stöder den **typen** parameter, en alternativ metod för att skapa det här certifikatet måste finnas på dessa operativsystem.</span><span class="sxs-lookup"><span data-stu-id="b296a-161">Because the New-SelfSignedCertificate cmdlet on Windows Operating Systems prior to Windows 10 and Windows Server 2016 do not support the **Type** parameter, an alternate method of creating this certificate is required on these operating systems.</span></span>
<span data-ttu-id="b296a-162">I det här fallet kan du använda ```makecert.exe``` eller ```certutil.exe``` att skapa certifikatet.</span><span class="sxs-lookup"><span data-stu-id="b296a-162">In this case you can use ```makecert.exe``` or ```certutil.exe``` to create the certificate.</span></span>

<span data-ttu-id="b296a-163">En alternativ metod är att [hämta ny SelfSignedCertificateEx.ps1 skriptet från Microsoft Script Center](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) och använda den för att skapa certifikatet i stället:</span><span class="sxs-lookup"><span data-stu-id="b296a-163">An alternate method is to [download the New-SelfSignedCertificateEx.ps1 script from Microsoft Script Center](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) and use it to create the certificate instead:</span></span>
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
$Cert = Get-ChildItem -Path cert:\LocalMachine\My `
    | Where-Object {
        ($_.FriendlyName -eq 'DSC Credential Encryption certificate') `
        -and ($_.Subject -eq "CN=${ENV:ComputerName}")
    } | Select-Object -First 1
# export the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
```
<span data-ttu-id="b296a-164">En gång exporterade den ```DscPublicKey.cer``` måste kopieras till den **redigering nod**.</span><span class="sxs-lookup"><span data-stu-id="b296a-164">Once exported, the ```DscPublicKey.cer``` would need to be copied to the **Authoring Node**.</span></span>

#### <a name="on-the-authoring-node-import-the-certs-public-key"></a><span data-ttu-id="b296a-165">På noden redigering: importera på certifikatets offentliga nyckel</span><span class="sxs-lookup"><span data-stu-id="b296a-165">On the Authoring Node: import the cert’s public key</span></span>
```powershell
# Import to the my store
Import-Certificate -FilePath "$env:temp\DscPublicKey.cer" -CertStoreLocation Cert:\LocalMachine\My
```

### <a name="creating-the-certificate-on-the-authoring-node"></a><span data-ttu-id="b296a-166">Skapa certifikatet på noden redigering</span><span class="sxs-lookup"><span data-stu-id="b296a-166">Creating the Certificate on the Authoring Node</span></span>
<span data-ttu-id="b296a-167">Alternativt kan krypteringscertifikat kan skapas på den **redigering nod**, exporterade med den **privat nyckel** som en PFX-fil och sedan importeras på den **målnoden**.</span><span class="sxs-lookup"><span data-stu-id="b296a-167">Alternately, the encryption certificate can be created on the **Authoring Node**, exported with the **private key** as a PFX file and then imported on the **Target Node**.</span></span>
<span data-ttu-id="b296a-168">Detta är den aktuella metoden för att implementera kryptering av DSC-autentiseringsuppgifter på _Nano Server_.</span><span class="sxs-lookup"><span data-stu-id="b296a-168">This is the current method for implementing DSC credential encryption on _Nano Server_.</span></span>
<span data-ttu-id="b296a-169">Även om den PFX-filen är skyddad med ett lösenord bör den hållas säkra under överföringen.</span><span class="sxs-lookup"><span data-stu-id="b296a-169">Although the PFX is secured with a password it should be kept secure during transit.</span></span>
<span data-ttu-id="b296a-170">I följande exempel:</span><span class="sxs-lookup"><span data-stu-id="b296a-170">The following example:</span></span>
 1. <span data-ttu-id="b296a-171">skapar ett certifikat på den **redigering nod**.</span><span class="sxs-lookup"><span data-stu-id="b296a-171">creates a certificate on the **Authoring node**.</span></span>
 2. <span data-ttu-id="b296a-172">exporterar certifikatet inklusive den privata nyckeln på den **redigering nod**.</span><span class="sxs-lookup"><span data-stu-id="b296a-172">exports the certificate including the private key on the **Authoring node**.</span></span>
 3. <span data-ttu-id="b296a-173">tar bort den privata nyckeln från den **redigering nod**, men behåller det offentliga nyckelcertifikatet i den **min** lagras.</span><span class="sxs-lookup"><span data-stu-id="b296a-173">removes the private key from the **Authoring node**, but keeps the public key certificate in the **my** store.</span></span>
 4. <span data-ttu-id="b296a-174">importerar privata nyckel certifikatet till rotarkivet certifikat på den **målnoden**.</span><span class="sxs-lookup"><span data-stu-id="b296a-174">imports the private key certificate into the root certificate store on the **Target node**.</span></span>
   - <span data-ttu-id="b296a-175">den måste läggas till rotarkivet så att det ska vara betrott av den **målnoden**.</span><span class="sxs-lookup"><span data-stu-id="b296a-175">it must be added to the root store so that it will be trusted by the **Target node**.</span></span>

#### <a name="on-the-authoring-node-create-and-export-the-certificate"></a><span data-ttu-id="b296a-176">På noden redigering: skapa och exportera certifikatet</span><span class="sxs-lookup"><span data-stu-id="b296a-176">On the Authoring Node: create and export the certificate</span></span>
><span data-ttu-id="b296a-177">Målnoden: Windows Server 2016 och Windows 10</span><span class="sxs-lookup"><span data-stu-id="b296a-177">Target Node: Windows Server 2016 and Windows 10</span></span>

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
<span data-ttu-id="b296a-178">En gång exporterade den ```DscPrivateKey.pfx``` måste kopieras till den **målnoden**.</span><span class="sxs-lookup"><span data-stu-id="b296a-178">Once exported, the ```DscPrivateKey.pfx``` would need to be copied to the **Target Node**.</span></span>

><span data-ttu-id="b296a-179">Målnoden: Windows Server 2012 R2/Windows 8.1 och tidigare</span><span class="sxs-lookup"><span data-stu-id="b296a-179">Target Node: Windows Server 2012 R2/Windows 8.1 and earlier</span></span>

<span data-ttu-id="b296a-180">Eftersom cmdlet New-SelfSignedCertificate på Windows-operativsystem före Windows 10 och Windows Server 2016 inte stöder den **typen** parameter, en alternativ metod för att skapa det här certifikatet måste finnas på dessa operativsystem.</span><span class="sxs-lookup"><span data-stu-id="b296a-180">Because the New-SelfSignedCertificate cmdlet on Windows Operating Systems prior to Windows 10 and Windows Server 2016 do not support the **Type** parameter, an alternate method of creating this certificate is required on these operating systems.</span></span>
<span data-ttu-id="b296a-181">I det här fallet kan du använda ```makecert.exe``` eller ```certutil.exe``` att skapa certifikatet.</span><span class="sxs-lookup"><span data-stu-id="b296a-181">In this case you can use ```makecert.exe``` or ```certutil.exe``` to create the certificate.</span></span>

<span data-ttu-id="b296a-182">En alternativ metod är att [hämta ny SelfSignedCertificateEx.ps1 skriptet från Microsoft Script Center](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) och använda den för att skapa certifikatet i stället:</span><span class="sxs-lookup"><span data-stu-id="b296a-182">An alternate method is to [download the New-SelfSignedCertificateEx.ps1 script from Microsoft Script Center](https://gallery.technet.microsoft.com/scriptcenter/Self-signed-certificate-5920a7c6) and use it to create the certificate instead:</span></span>
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
$Cert = Get-ChildItem -Path cert:\LocalMachine\My `
    | Where-Object {
        ($_.FriendlyName -eq 'DSC Credential Encryption certificate') `
        -and ($_.Subject -eq "CN=${ENV:ComputerName}")
    } | Select-Object -First 1
# export the public key certificate
$mypwd = ConvertTo-SecureString -String "YOUR_PFX_PASSWD" -Force -AsPlainText
$cert | Export-PfxCertificate -FilePath "$env:temp\DscPrivateKey.pfx" -Password $mypwd -Force
# remove the private key certificate from the node but keep the public key certificate
$cert | Export-Certificate -FilePath "$env:temp\DscPublicKey.cer" -Force
$cert | Remove-Item -Force
Import-Certificate -FilePath "$env:temp\DscPublicKey.cer" -CertStoreLocation Cert:\LocalMachine\My
```

#### <a name="on-the-target-node-import-the-certs-private-key-as-a-trusted-root"></a><span data-ttu-id="b296a-183">På målnoden: importera den certifikatets privata nyckel som en betrodd rot</span><span class="sxs-lookup"><span data-stu-id="b296a-183">On the Target Node: import the cert’s private key as a trusted root</span></span>
```powershell
# Import to the root store so that it is trusted
$mypwd = ConvertTo-SecureString -String "YOUR_PFX_PASSWD" -Force -AsPlainText
Import-PfxCertificate -FilePath "$env:temp\DscPrivateKey.pfx" -CertStoreLocation Cert:\LocalMachine\My -Password $mypwd > $null
```

## <a name="configuration-data"></a><span data-ttu-id="b296a-184">Konfigurationsdata</span><span class="sxs-lookup"><span data-stu-id="b296a-184">Configuration data</span></span>

<span data-ttu-id="b296a-185">Datablock konfigurationen definierar vilka målnoder ska fungera på om eller inte för att kryptera autentiseringsuppgifterna för kryptering och annan information.</span><span class="sxs-lookup"><span data-stu-id="b296a-185">The configuration data block defines which target nodes to operate on, whether or not to encrypt the credentials, the means of encryption, and other information.</span></span> <span data-ttu-id="b296a-186">Mer information om konfiguration datablock finns [avgränsa konfiguration och miljödata](configData.md).</span><span class="sxs-lookup"><span data-stu-id="b296a-186">For more information on the configuration data block, see [Separating Configuration and Environment Data](configData.md).</span></span>

<span data-ttu-id="b296a-187">Element som kan konfigureras för varje nod som är relaterade till autentiseringsuppgifter kryptering är:</span><span class="sxs-lookup"><span data-stu-id="b296a-187">The elements that can be configured for each node that are related to credential encryption are:</span></span>
* <span data-ttu-id="b296a-188">**Nodnamn** -namnet på målnoden kryptering av autentiseringsuppgifter konfigureras för.</span><span class="sxs-lookup"><span data-stu-id="b296a-188">**NodeName** - the name of the target node that the credential encryption is being configured for.</span></span>
* <span data-ttu-id="b296a-189">**PsDscAllowPlainTextPassword** – oavsett om okrypterad autentiseringsuppgifter kan skickas till den här noden.</span><span class="sxs-lookup"><span data-stu-id="b296a-189">**PsDscAllowPlainTextPassword** - whether unencrypted credentials will be allowed to be passed to this node.</span></span> <span data-ttu-id="b296a-190">Detta är **bör inte**.</span><span class="sxs-lookup"><span data-stu-id="b296a-190">This is **not recommended**.</span></span>
* <span data-ttu-id="b296a-191">**Tumavtryck för** -tumavtrycket för certifikatet som används för att dekryptera autentiseringsuppgifterna i DSC-konfigurationen på den _målnoden_.</span><span class="sxs-lookup"><span data-stu-id="b296a-191">**Thumbprint** - the thumbprint of the certificate that will be used to decrypt the credentials in the DSC Configuration on the _Target Node_.</span></span> <span data-ttu-id="b296a-192">**Det här certifikatet måste finnas i lokala datorns certifikatarkiv på målnoden.**</span><span class="sxs-lookup"><span data-stu-id="b296a-192">**This certificate must exist in the Local Machine certificate store on the Target Node.**</span></span>
* <span data-ttu-id="b296a-193">**CertificateFile** - certifikatfilen (som innehåller den offentliga nyckeln) som ska användas för att kryptera autentiseringsuppgifterna för den _målnoden_.</span><span class="sxs-lookup"><span data-stu-id="b296a-193">**CertificateFile** - the certificate file (containing the public key only) that should be used to encrypt the credentials for the _Target Node_.</span></span> <span data-ttu-id="b296a-194">Det här måste vara antingen en DER-kodad binärfil X.509 eller Base64-kodat X.509-format-certifikatfil.</span><span class="sxs-lookup"><span data-stu-id="b296a-194">This must be either a DER encoded binary X.509 or Base-64 encoded X.509 format certificate file.</span></span>

<span data-ttu-id="b296a-195">Det här exemplet illustrerar en konfiguration datablock som anger en målnoden för att fungera på namngiven targetNode, sökvägen till filen certifikat med offentlig nyckel (som kallas targetNode.cer) och tumavtrycket för den offentliga nyckeln.</span><span class="sxs-lookup"><span data-stu-id="b296a-195">This example shows a configuration data block that specifies a target node to act on named targetNode, the path to the public key certificate file (named targetNode.cer), and the thumbprint for the public key.</span></span>

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
            }; 
        );    
    }
```


## <a name="configuration-script"></a><span data-ttu-id="b296a-196">Konfigurationsskript</span><span class="sxs-lookup"><span data-stu-id="b296a-196">Configuration script</span></span>

<span data-ttu-id="b296a-197">I konfigurationsskript själva använder den `PsCredential` parametern för att se till att autentiseringsuppgifterna lagras för på kortast möjliga tid.</span><span class="sxs-lookup"><span data-stu-id="b296a-197">In the configuration script itself, use the `PsCredential` parameter to ensure that credentials are stored for the shortest possible time.</span></span> <span data-ttu-id="b296a-198">När du kör det angivna exemplet DSC efterfrågar autentiseringsuppgifter och kryptera MOF-filen med hjälp av CertificateFile som är kopplad till målnoden i datablock konfiguration.</span><span class="sxs-lookup"><span data-stu-id="b296a-198">When you run the supplied example, DSC will prompt you for credentials and then encrypt the MOF file using the CertificateFile that is associated with the target node in the configuration data block.</span></span> <span data-ttu-id="b296a-199">Det här kodexemplet kopierar en fil från en resurs som skyddas till en användare.</span><span class="sxs-lookup"><span data-stu-id="b296a-199">This code example copies a file from a share that is secured to a user.</span></span>

```
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

## <a name="setting-up-decryption"></a><span data-ttu-id="b296a-200">Konfigurera dekryptering</span><span class="sxs-lookup"><span data-stu-id="b296a-200">Setting up decryption</span></span>

<span data-ttu-id="b296a-201">Innan du [ `Start-DscConfiguration` ](https://technet.microsoft.com/en-us/library/dn521623.aspx) kan fungera, måste du ange Local Configuration Manager på varje målnoden vilket certifikat som ska använda för att dekryptera autentiseringsuppgifterna resursnamnet CertificateID för att verifiera certifikatets tumavtryck.</span><span class="sxs-lookup"><span data-stu-id="b296a-201">Before [`Start-DscConfiguration`](https://technet.microsoft.com/en-us/library/dn521623.aspx) can work, you have to tell the Local Configuration Manager on each target node which certificate to use to decrypt the credentials, using the CertificateID resource to verify the certificate’s thumbprint.</span></span> <span data-ttu-id="b296a-202">Den här funktionen exempel hittar lokala intyg (du kan behöva anpassa den så att den ska hitta exakt certifikatet som du vill använda):</span><span class="sxs-lookup"><span data-stu-id="b296a-202">This example function will find the appropriate local certificate (you might have to customize it so it will find the exact certificate you want to use):</span></span>

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

<span data-ttu-id="b296a-203">Skriptet konfiguration kan uppdateras för att använda värdet med det certifikat som identifieras av dess tumavtryck:</span><span class="sxs-lookup"><span data-stu-id="b296a-203">With the certificate identified by its thumbprint, the configuration script can be updated to use the value:</span></span>

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

## <a name="running-the-configuration"></a><span data-ttu-id="b296a-204">Kör konfigurationen</span><span class="sxs-lookup"><span data-stu-id="b296a-204">Running the configuration</span></span>

<span data-ttu-id="b296a-205">Du kan nu köra konfiguration, som kommer att skapa två filer:</span><span class="sxs-lookup"><span data-stu-id="b296a-205">At this point, you can run the configuration, which will output two files:</span></span>

 * <span data-ttu-id="b296a-206">A \*. meta.mof-fil som konfigurerar den lokala Configuration Manager för att dekryptera autentiseringsuppgifterna med det certifikat som lagras på lokala datorns Arkiv och identifieras av dess tumavtryck.</span><span class="sxs-lookup"><span data-stu-id="b296a-206">A \*.meta.mof file that configures the Local Configuration Manager to decrypt the credentials using the certificate that is stored on the local machine store and identified by its thumbprint.</span></span> <span data-ttu-id="b296a-207">[`Set-DscLocalConfigurationManager`](https://technet.microsoft.com/en-us/library/dn521621.aspx)gäller de \*. meta.mof fil.</span><span class="sxs-lookup"><span data-stu-id="b296a-207">[`Set-DscLocalConfigurationManager`](https://technet.microsoft.com/en-us/library/dn521621.aspx) applies the \*.meta.mof file.</span></span>
 * <span data-ttu-id="b296a-208">En MOF-fil som faktiskt gäller konfigurationen av.</span><span class="sxs-lookup"><span data-stu-id="b296a-208">A MOF file that actually applies the configuration.</span></span> <span data-ttu-id="b296a-209">Start-DscConfiguration gäller konfigurationen av.</span><span class="sxs-lookup"><span data-stu-id="b296a-209">Start-DscConfiguration applies the configuration.</span></span>

<span data-ttu-id="b296a-210">Dessa kommandon kan utföra dessa steg:</span><span class="sxs-lookup"><span data-stu-id="b296a-210">These commands will accomplish those steps:</span></span>

```powershell
Write-Host "Generate DSC Configuration..."
CredentialEncryptionExample -ConfigurationData $ConfigData -OutputPath .\CredentialEncryptionExample

Write-Host "Setting up LCM to decrypt credentials..."
Set-DscLocalConfigurationManager .\CredentialEncryptionExample -Verbose 
 
Write-Host "Starting Configuration..."
Start-DscConfiguration .\CredentialEncryptionExample -wait -Verbose
```

<span data-ttu-id="b296a-211">Det här exemplet skulle skicka DSC-konfigurationen till målnoden.</span><span class="sxs-lookup"><span data-stu-id="b296a-211">This example would push the DSC configuration to the target node.</span></span>
<span data-ttu-id="b296a-212">DSC-konfigurationen kan också användas med en DSC Pull-Server om det inte finns.</span><span class="sxs-lookup"><span data-stu-id="b296a-212">The DSC configuration can also be applied using a DSC Pull Server if one is available.</span></span>

<span data-ttu-id="b296a-213">Se [installera en klient för DSC-pull](pullClient.md) för mer information om hur du använder DSC-konfigurationer som använder en DSC Pull-Server.</span><span class="sxs-lookup"><span data-stu-id="b296a-213">See [Setting up a DSC pull client](pullClient.md) for more information on applying DSC configurations using a DSC Pull Server.</span></span>

## <a name="credential-encryption-module-example"></a><span data-ttu-id="b296a-214">Autentiseringsuppgifter kryptering modulen exempel</span><span class="sxs-lookup"><span data-stu-id="b296a-214">Credential Encryption Module Example</span></span>

<span data-ttu-id="b296a-215">Här är ett fullständigt exempel som omfattar alla de här stegen plus en helper-cmdlet som exporterar och kopierar de offentliga nycklarna:</span><span class="sxs-lookup"><span data-stu-id="b296a-215">Here is a full example that incorporates all of these steps, plus a helper cmdlet that exports and copies the public keys:</span></span>

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

