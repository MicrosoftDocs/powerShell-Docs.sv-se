---
title: Parametrar för | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e199bba3-90d3-41ca-9d78-cb502e58508d
caps.latest.revision: 6
ms.openlocfilehash: bdf88de0258af75c01739f30a71fb4914cac3a9a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849030"
---
# <a name="security-parameters"></a><span data-ttu-id="ff306-102">Säkerhetsparametrar</span><span class="sxs-lookup"><span data-stu-id="ff306-102">Security Parameters</span></span>

<span data-ttu-id="ff306-103">I följande tabell visas de rekommenderade namn och funktioner för parametrar som används för att ange säkerhetsinformation för en åtgärd, till exempel parametrar som anger certifikatinformationen för nyckeln och behörigheten.</span><span class="sxs-lookup"><span data-stu-id="ff306-103">The following table lists the recommended names and functionality for parameters used to provide security information for an operation, such as parameters that specify certificate key and privilege information.</span></span>

<span data-ttu-id="ff306-104">ACL-datatyp: Sträng</span><span class="sxs-lookup"><span data-stu-id="ff306-104">ACL Data type: String</span></span>

<span data-ttu-id="ff306-105">Implementera den här parametern om du vill ange åtkomstnivå för kontroll av skydd för en katalog eller för en identifierare URI (Uniform Resource).</span><span class="sxs-lookup"><span data-stu-id="ff306-105">Implement this parameter to specify the access control level of protection for a catalog or for a Uniform Resource Identifier (URI).</span></span>

<span data-ttu-id="ff306-106">Certifikatfil datatyp: Sträng</span><span class="sxs-lookup"><span data-stu-id="ff306-106">CertFile Data type: String</span></span>

<span data-ttu-id="ff306-107">Implementera den här parametern så att användaren kan ange namnet på en fil som innehåller något av följande:</span><span class="sxs-lookup"><span data-stu-id="ff306-107">Implement this parameter so that the user can specify the name of a file that contains one of the following:</span></span>

- <span data-ttu-id="ff306-108">En Base64- eller DER Distinguished Encoding Rules ()-kodad x.509-certifikat</span><span class="sxs-lookup"><span data-stu-id="ff306-108">A Base64 or Distinguished Encoding Rules (DER) encoded x.509 certificate</span></span>

- <span data-ttu-id="ff306-109">En offentlig Key Cryptography Standards (PKCS) #12-fil som innehåller minst ett certifikat och nyckel</span><span class="sxs-lookup"><span data-stu-id="ff306-109">A Public Key Cryptography Standards (PKCS) #12 file that contains at least one certificate and key</span></span>

<span data-ttu-id="ff306-110">CertIssuerName datatyp: Sträng</span><span class="sxs-lookup"><span data-stu-id="ff306-110">CertIssuerName Data type: String</span></span>

<span data-ttu-id="ff306-111">Implementera den här parametern så att användaren kan ange ett namn för utfärdaren av ett certifikat eller så att användaren kan ange en delsträng.</span><span class="sxs-lookup"><span data-stu-id="ff306-111">Implement this parameter so that the user can specify the name of the issuer of a certificate or so that the user can specify a substring.</span></span>

<span data-ttu-id="ff306-112">CertRequestFile datatyp: Sträng</span><span class="sxs-lookup"><span data-stu-id="ff306-112">CertRequestFile Data type: String</span></span>

<span data-ttu-id="ff306-113">Implementera den här parametern om du vill ange namnet på en fil som innehåller en Base64- eller DER-kodad PKCS #10-certifikatbegäran.</span><span class="sxs-lookup"><span data-stu-id="ff306-113">Implement this parameter to specify the name of a file that contains a Base64 or DER-encoded PKCS #10 certificate request.</span></span>

<span data-ttu-id="ff306-114">CertSerialNumber datatyp: Sträng</span><span class="sxs-lookup"><span data-stu-id="ff306-114">CertSerialNumber Data type: String</span></span>

<span data-ttu-id="ff306-115">Implementera den här parametern om du vill ange serienumret som har utfärdats av certifikatutfärdaren.</span><span class="sxs-lookup"><span data-stu-id="ff306-115">Implement this parameter to specify the serial number that was issued by the certification authority.</span></span>

<span data-ttu-id="ff306-116">CertStoreLocation datatyp: Sträng</span><span class="sxs-lookup"><span data-stu-id="ff306-116">CertStoreLocation Data type: String</span></span>

<span data-ttu-id="ff306-117">Implementera den här parametern så att användaren kan ange platsen för arkivet.</span><span class="sxs-lookup"><span data-stu-id="ff306-117">Implement this parameter so that the user can specify the location of the certificate store.</span></span> <span data-ttu-id="ff306-118">Platsen är vanligtvis en sökväg till filen.</span><span class="sxs-lookup"><span data-stu-id="ff306-118">The location is typically a file path.</span></span>

<span data-ttu-id="ff306-119">CertSubjectName datatyp: Sträng</span><span class="sxs-lookup"><span data-stu-id="ff306-119">CertSubjectName Data type: String</span></span>

<span data-ttu-id="ff306-120">Implementera den här parametern så att användaren kan ange utfärdaren av ett certifikat eller så att användaren kan ange en delsträng.</span><span class="sxs-lookup"><span data-stu-id="ff306-120">Implement this parameter so that the user can specify the issuer of a certificate or so that the user can specify a substring.</span></span>

<span data-ttu-id="ff306-121">CertUsage datatyp: Sträng</span><span class="sxs-lookup"><span data-stu-id="ff306-121">CertUsage Data type: String</span></span>

<span data-ttu-id="ff306-122">Implementera den här parametern om du vill ange nyckelanvändningen eller avancerad nyckelanvändning.</span><span class="sxs-lookup"><span data-stu-id="ff306-122">Implement this parameter to specify the key usage or the enhanced key usage.</span></span> <span data-ttu-id="ff306-123">Nyckeln kan representeras som en aning maskera, en aning objektidentifierare (OID) eller en sträng.</span><span class="sxs-lookup"><span data-stu-id="ff306-123">The key can be represented as a bit mask, a bit, an object identifier (OID), or a string.</span></span>

<span data-ttu-id="ff306-124">Autentiseringsuppgifterna skriver du: [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential)</span><span class="sxs-lookup"><span data-stu-id="ff306-124">Credential Data type: [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential)</span></span>

<span data-ttu-id="ff306-125">Implementera den här parametern så att cmdleten ska automatiskt frågar användaren om ett användarnamn eller lösenord.</span><span class="sxs-lookup"><span data-stu-id="ff306-125">Implement this parameter so that the cmdlet will automatically prompt the user for a user name or password.</span></span> <span data-ttu-id="ff306-126">Ett meddelande för både visas om en fullständig autentiseringsuppgift anges direkt.</span><span class="sxs-lookup"><span data-stu-id="ff306-126">A prompt for both is displayed if a full credential is not supplied directly.</span></span>

<span data-ttu-id="ff306-127">Kryptografiprovider datatyp: Sträng</span><span class="sxs-lookup"><span data-stu-id="ff306-127">CSPName Data type: String</span></span>

<span data-ttu-id="ff306-128">Implementera den här parametern så att användaren kan ange namnet på certifikatet service provider (CSP).</span><span class="sxs-lookup"><span data-stu-id="ff306-128">Implement this parameter so that the user can specify the name of the certificate service provider (CSP).</span></span>

<span data-ttu-id="ff306-129">CSPType datatyp: Heltal</span><span class="sxs-lookup"><span data-stu-id="ff306-129">CSPType Data type: Integer</span></span>

<span data-ttu-id="ff306-130">Implementera den här parametern så att användaren kan ange vilken typ av CSP.</span><span class="sxs-lookup"><span data-stu-id="ff306-130">Implement this parameter so that the user can specify the type of CSP.</span></span>

<span data-ttu-id="ff306-131">Gruppera Data skriver du: Sträng</span><span class="sxs-lookup"><span data-stu-id="ff306-131">Group Data type: String</span></span>

<span data-ttu-id="ff306-132">Implementera den här parametern så att användaren kan ange en samling av säkerhetsobjekt för åtkomst.</span><span class="sxs-lookup"><span data-stu-id="ff306-132">Implement this parameter so that the user can specify a collection of principals for access.</span></span> <span data-ttu-id="ff306-133">Mer information finns i beskrivningen av den `Principal` parametern.</span><span class="sxs-lookup"><span data-stu-id="ff306-133">For more information, see the description of the `Principal` parameter.</span></span>

<span data-ttu-id="ff306-134">KeyAlgorithm datatyp: Sträng</span><span class="sxs-lookup"><span data-stu-id="ff306-134">KeyAlgorithm Data type: String</span></span>

<span data-ttu-id="ff306-135">Implementera den här parametern så att användaren kan ange nyckelgenerering-algoritm som ska användas för säkerhet.</span><span class="sxs-lookup"><span data-stu-id="ff306-135">Implement this parameter so that the user can specify the key generation algorithm to use for security.</span></span>

<span data-ttu-id="ff306-136">Nyckelbehållare datatyp: Sträng</span><span class="sxs-lookup"><span data-stu-id="ff306-136">KeyContainerName Data type: String</span></span>

<span data-ttu-id="ff306-137">Implementera den här parametern så att användaren kan ange namnet på nyckelbehållaren.</span><span class="sxs-lookup"><span data-stu-id="ff306-137">Implement this parameter so that the user can specify the name of the key container.</span></span>

<span data-ttu-id="ff306-138">Nyckellängd datatyp: Heltal</span><span class="sxs-lookup"><span data-stu-id="ff306-138">KeyLength Data type: Integer</span></span>

<span data-ttu-id="ff306-139">Implementera den här parametern så att användaren kan ange längden på nyckeln i bitar.</span><span class="sxs-lookup"><span data-stu-id="ff306-139">Implement this parameter so that the user can specify the length of the key in bits.</span></span>

<span data-ttu-id="ff306-140">Åtgärden datatyp: Sträng</span><span class="sxs-lookup"><span data-stu-id="ff306-140">Operation Data type: String</span></span>

<span data-ttu-id="ff306-141">Implementera den här parametern så att användaren kan ange en åtgärd som kan utföras på ett skyddat objekt.</span><span class="sxs-lookup"><span data-stu-id="ff306-141">Implement this parameter so that the user can specify an action that can be performed on a protected object.</span></span>

<span data-ttu-id="ff306-142">Huvudnamn datatyp: Sträng</span><span class="sxs-lookup"><span data-stu-id="ff306-142">Principal Data type: String</span></span>

<span data-ttu-id="ff306-143">Implementera den här parametern så att användaren kan ange en unik identifierbar entitet för åtkomst.</span><span class="sxs-lookup"><span data-stu-id="ff306-143">Implement this parameter so that the user can specify a unique identifiable entity for access.</span></span>

<span data-ttu-id="ff306-144">Behörighet datatyp: Sträng</span><span class="sxs-lookup"><span data-stu-id="ff306-144">Privilege Data type: String</span></span>

<span data-ttu-id="ff306-145">Implementera den här parametern så att användaren kan ange höger en cmdlet måste utföra en åtgärd för en viss enhet.</span><span class="sxs-lookup"><span data-stu-id="ff306-145">Implement this parameter so that the user can specify the right a cmdlet needs to perform an operation for a particular entity.</span></span>

<span data-ttu-id="ff306-146">Privilegier datatyp: Matris med privilegier</span><span class="sxs-lookup"><span data-stu-id="ff306-146">Privileges Data type: Array of privileges</span></span>

<span data-ttu-id="ff306-147">Implementera den här parametern så att användaren kan ange de rättigheter som en cmdlet behöver för att utföra åtgärden för en viss post.</span><span class="sxs-lookup"><span data-stu-id="ff306-147">Implement this parameter so that the user can specify the rights that a cmdlet needs to perform its operation for a particular entry.</span></span>

<span data-ttu-id="ff306-148">Datatypen för rollen: Sträng</span><span class="sxs-lookup"><span data-stu-id="ff306-148">Role Data type: String</span></span>

<span data-ttu-id="ff306-149">Implementera den här parametern så att användaren kan ange en uppsättning åtgärder som kan utföras av en annan entitet.</span><span class="sxs-lookup"><span data-stu-id="ff306-149">Implement this parameter so that the user can specify a set of operations that can be performed by an entity.</span></span>

<span data-ttu-id="ff306-150">SaveCred datatyp: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="ff306-150">SaveCred Data type: SwitchParameter</span></span>

<span data-ttu-id="ff306-151">Implementera den här parametern så att autentiseringsuppgifter som tidigare sparades av användaren kommer att användas när parametern anges.</span><span class="sxs-lookup"><span data-stu-id="ff306-151">Implement this parameter so that credentials that were previously saved by the user will be used when the parameter is specified.</span></span>

<span data-ttu-id="ff306-152">Scope-datatyp: Sträng</span><span class="sxs-lookup"><span data-stu-id="ff306-152">Scope Data type: String</span></span>

<span data-ttu-id="ff306-153">Implementera den här parametern så att användaren kan ange gruppen för skyddade objekt för cmdleten.</span><span class="sxs-lookup"><span data-stu-id="ff306-153">Implement this parameter so that the user can specify the group of protected objects for the cmdlet.</span></span>

<span data-ttu-id="ff306-154">Typ av SID Data: Sträng</span><span class="sxs-lookup"><span data-stu-id="ff306-154">SID Data type: String</span></span>

<span data-ttu-id="ff306-155">Implementera den här parametern så att användaren kan ange en unik identifierare som representerar ett huvudnamn.</span><span class="sxs-lookup"><span data-stu-id="ff306-155">Implement this parameter so that the user can specify a unique identifier that represents a principal.</span></span>

<span data-ttu-id="ff306-156">Betrodda datatyp: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="ff306-156">Trusted Data type: SwitchParameter</span></span>

<span data-ttu-id="ff306-157">Implementera den här parametern så att förtroendenivåer stöds när parametern anges.</span><span class="sxs-lookup"><span data-stu-id="ff306-157">Implement this parameter so that trust levels are supported when the parameter is specified.</span></span>

<span data-ttu-id="ff306-158">TrustLevel datatyp: Nyckelord</span><span class="sxs-lookup"><span data-stu-id="ff306-158">TrustLevel Data type: Keyword</span></span>

<span data-ttu-id="ff306-159">Implementera den här parametern så att användaren kan ange förtroendenivå som stöds.</span><span class="sxs-lookup"><span data-stu-id="ff306-159">Implement this parameter so that the user can specify the trust level that is supported.</span></span> <span data-ttu-id="ff306-160">Möjliga värden omfattar till exempel internet och intranätet fulltrust.</span><span class="sxs-lookup"><span data-stu-id="ff306-160">For example, possible values include internet, intranet, and fulltrust.</span></span>

## <a name="see-also"></a><span data-ttu-id="ff306-161">Se även</span><span class="sxs-lookup"><span data-stu-id="ff306-161">See Also</span></span>

[<span data-ttu-id="ff306-162">Cmdlet-parametrarna</span><span class="sxs-lookup"><span data-stu-id="ff306-162">Cmdlet Parameters</span></span>](./cmdlet-parameters.md)

[<span data-ttu-id="ff306-163">Skriva en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="ff306-163">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="ff306-164">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="ff306-164">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
