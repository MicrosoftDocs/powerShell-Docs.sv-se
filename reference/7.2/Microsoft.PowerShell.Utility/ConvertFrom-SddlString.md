---
external help file: Microsoft.PowerShell.Utility-help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-sddlstring?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-SddlString
ms.openlocfilehash: 5c8e963486c0d4f5f3e7d643cb65c752720f37d1
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709853"
---
# <span data-ttu-id="099c6-102">ConvertFrom-SddlString</span><span class="sxs-lookup"><span data-stu-id="099c6-102">ConvertFrom-SddlString</span></span>

## <span data-ttu-id="099c6-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="099c6-103">SYNOPSIS</span></span>
<span data-ttu-id="099c6-104">Konverterar en SDDL-sträng till ett anpassat objekt.</span><span class="sxs-lookup"><span data-stu-id="099c6-104">Converts a SDDL string to a custom object.</span></span>

## <span data-ttu-id="099c6-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="099c6-105">SYNTAX</span></span>

### <span data-ttu-id="099c6-106">Alla</span><span class="sxs-lookup"><span data-stu-id="099c6-106">All</span></span>

```
ConvertFrom-SddlString [-Sddl] <String> [-Type <AccessRightTypeNames>] [<CommonParameters>]
```

## <span data-ttu-id="099c6-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="099c6-107">DESCRIPTION</span></span>

<span data-ttu-id="099c6-108">`ConvertFrom-SddlString`Cmdleten konverterar en språk sträng för en säkerhets beskrivnings definition till ett anpassat **PSCustomObject** -objekt med följande egenskaper: Owner, Group, DiscretionaryAcl, SystemAcl och RawDescriptor.</span><span class="sxs-lookup"><span data-stu-id="099c6-108">The `ConvertFrom-SddlString` cmdlet converts a Security Descriptor Definition Language string to a custom **PSCustomObject** object with the following properties: Owner, Group, DiscretionaryAcl, SystemAcl and RawDescriptor.</span></span>

<span data-ttu-id="099c6-109">Egenskaperna Owner, Group, DiscretionaryAcl och SystemAcl innehåller en läsbar text representation av de åtkomst rättigheter som anges i en SDDL-sträng.</span><span class="sxs-lookup"><span data-stu-id="099c6-109">Owner, Group, DiscretionaryAcl and SystemAcl properties contain a readable text representation of the access rights specified in a SDDL string.</span></span>

<span data-ttu-id="099c6-110">Denna cmdlet introducerades i PowerShell 5,0.</span><span class="sxs-lookup"><span data-stu-id="099c6-110">This cmdlet was introduced in PowerShell 5.0.</span></span>

## <span data-ttu-id="099c6-111">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="099c6-111">EXAMPLES</span></span>

### <span data-ttu-id="099c6-112">Exempel 1: konvertera SDDL för Access-behörigheter till en PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="099c6-112">Example 1: Convert file system access rights SDDL to a PSCustomObject</span></span>

```powershell
$acl = Get-Acl -Path C:\Windows
ConvertFrom-SddlString -Sddl $acl.Sddl
```

<span data-ttu-id="099c6-113">Det första kommandot använder `Get-Acl` cmdleten för att hämta säkerhets beskrivningen för mappen C:\Windows och sparar den i variabeln.</span><span class="sxs-lookup"><span data-stu-id="099c6-113">The first command uses the `Get-Acl` cmdlet to get the security descriptor for the C:\Windows folder and saves it in the variable.</span></span>

<span data-ttu-id="099c6-114">Det andra kommandot använder `ConvertFrom-SddlString` cmdleten för att hämta text representationen av SDDL-strängen, som finns i SDDL-egenskapen för objektet som representerar säkerhets beskrivningen.</span><span class="sxs-lookup"><span data-stu-id="099c6-114">The second command uses the `ConvertFrom-SddlString` cmdlet to get the text representation of the SDDL string, contained in the Sddl property of the object representing the security descriptor.</span></span>

### <span data-ttu-id="099c6-115">Exempel 2: konvertera SDDL för register åtkomst behörigheter till en PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="099c6-115">Example 2: Convert registry access rights SDDL to a PSCustomObject</span></span>

```powershell
$acl = Get-Acl HKLM:\SOFTWARE\Microsoft\
ConvertFrom-SddlString -Sddl $acl.Sddl -Type RegistryRights
```

<span data-ttu-id="099c6-116">Det första kommandot använder `Get-Acl` cmdleten för att hämta säkerhets beskrivningen för HKLM: \ SOFTWARE\Microsoft\-nyckeln och sparar den i variabeln.</span><span class="sxs-lookup"><span data-stu-id="099c6-116">The first command uses the `Get-Acl` cmdlet to get the security descriptor for the HKLM:\SOFTWARE\Microsoft\ key and saves it in the variable.</span></span>

<span data-ttu-id="099c6-117">Det andra kommandot använder `ConvertFrom-SddlString` cmdleten för att hämta text representationen av SDDL-strängen, som finns i SDDL-egenskapen för objektet som representerar säkerhets beskrivningen.</span><span class="sxs-lookup"><span data-stu-id="099c6-117">The second command uses the `ConvertFrom-SddlString` cmdlet to get the text representation of the SDDL string, contained in the Sddl property of the object representing the security descriptor.</span></span>

<span data-ttu-id="099c6-118">`-Type`Parametern används för att ange att SDDL-strängen representerar en säkerhets beskrivning för registret.</span><span class="sxs-lookup"><span data-stu-id="099c6-118">It uses the `-Type` parameter to specify that SDDL string represents a registry security descriptor.</span></span>

### <span data-ttu-id="099c6-119">Exempel 3: konvertera SDDL-behörighet för register åtkomst till en PSCustomObject med hjälp av ConvertFrom-SddlString med och utan `-Type` parametern</span><span class="sxs-lookup"><span data-stu-id="099c6-119">Example 3: Convert registry access rights SDDL to a PSCustomObject by using ConvertFrom-SddlString with and without the `-Type` parameter</span></span>

```powershell
$acl = Get-Acl -Path HKLM:\SOFTWARE\Microsoft\

ConvertFrom-SddlString -Sddl $acl.Sddl | Foreach-Object {$_.DiscretionaryAcl[0]}

BUILTIN\Administrators: AccessAllowed (ChangePermissions, CreateDirectories, Delete, ExecuteKey, FullControl, GenericExecute, GenericWrite, ListDirectory, ReadExtendedAttributes, ReadPermissions, TakeOwnership, Traverse, WriteData, WriteExtendedAttributes, WriteKey)

ConvertFrom-SddlString -Sddl $acl.Sddl -Type RegistryRights | Foreach-Object {$_.DiscretionaryAcl[0]}

BUILTIN\Administrators: AccessAllowed (ChangePermissions, CreateLink, CreateSubKey, Delete, EnumerateSubKeys, ExecuteKey, FullControl, GenericExecute, GenericWrite, Notify, QueryValues, ReadPermissions, SetValue, TakeOwnership, WriteKey)
```

<span data-ttu-id="099c6-120">Det första kommandot använder `Get-Acl` cmdleten för att hämta säkerhets beskrivningen för HKLM: \ SOFTWARE\Microsoft\-nyckeln och sparar den i variabeln.</span><span class="sxs-lookup"><span data-stu-id="099c6-120">The first command uses the `Get-Acl` cmdlet to get the security descriptor for the HKLM:\SOFTWARE\Microsoft\ key and saves it in the variable.</span></span>

<span data-ttu-id="099c6-121">Det andra kommandot använder `ConvertFrom-SddlString` cmdleten för att hämta text representationen av SDDL-strängen, som finns i SDDL-egenskapen för objektet som representerar säkerhets beskrivningen.</span><span class="sxs-lookup"><span data-stu-id="099c6-121">The second command uses the `ConvertFrom-SddlString` cmdlet to get the text representation of the SDDL string, contained in the Sddl property of the object representing the security descriptor.</span></span>

<span data-ttu-id="099c6-122">Den använder inte `-Type` parametern, så åtkomst rättigheterna som visas gäller för fil system.</span><span class="sxs-lookup"><span data-stu-id="099c6-122">It doesn't use the `-Type` parameter, so the access rights shown are for file system.</span></span>

<span data-ttu-id="099c6-123">Det tredje kommandot använder `ConvertFrom-SddlString` cmdleten med `-Type` parametern, så åtkomst rättigheterna som returneras är för registret.</span><span class="sxs-lookup"><span data-stu-id="099c6-123">The third command uses the `ConvertFrom-SddlString` cmdlet with the `-Type` parameter, so the access rights returned are for registry.</span></span>

## <span data-ttu-id="099c6-124">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="099c6-124">PARAMETERS</span></span>

### <span data-ttu-id="099c6-125">-SDDL</span><span class="sxs-lookup"><span data-stu-id="099c6-125">-Sddl</span></span>

<span data-ttu-id="099c6-126">Anger den sträng som representerar säkerhets beskrivningen i SDDL-syntax.</span><span class="sxs-lookup"><span data-stu-id="099c6-126">Specifies the string representing the security descriptor in SDDL syntax.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="099c6-127">-Typ</span><span class="sxs-lookup"><span data-stu-id="099c6-127">-Type</span></span>

<span data-ttu-id="099c6-128">Anger vilken typ av rättigheter som SDDL-sträng representerar.</span><span class="sxs-lookup"><span data-stu-id="099c6-128">Specifies the type of rights that SDDL string represents.</span></span>

<span data-ttu-id="099c6-129">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="099c6-129">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="099c6-130">FileSystemRights</span><span class="sxs-lookup"><span data-stu-id="099c6-130">FileSystemRights</span></span>
- <span data-ttu-id="099c6-131">RegistryRights</span><span class="sxs-lookup"><span data-stu-id="099c6-131">RegistryRights</span></span>
- <span data-ttu-id="099c6-132">ActiveDirectoryRights</span><span class="sxs-lookup"><span data-stu-id="099c6-132">ActiveDirectoryRights</span></span>
- <span data-ttu-id="099c6-133">MutexRights</span><span class="sxs-lookup"><span data-stu-id="099c6-133">MutexRights</span></span>
- <span data-ttu-id="099c6-134">SemaphoreRights</span><span class="sxs-lookup"><span data-stu-id="099c6-134">SemaphoreRights</span></span>
- <span data-ttu-id="099c6-135">CryptoKeyRights</span><span class="sxs-lookup"><span data-stu-id="099c6-135">CryptoKeyRights</span></span>
- <span data-ttu-id="099c6-136">EventWaitHandleRights</span><span class="sxs-lookup"><span data-stu-id="099c6-136">EventWaitHandleRights</span></span>

<span data-ttu-id="099c6-137">Som standard använder cmdlet fil system rättigheter.</span><span class="sxs-lookup"><span data-stu-id="099c6-137">By default cmdlet uses file system rights.</span></span>

<span data-ttu-id="099c6-138">CryptoKeyRights och ActiveDirectoryRights stöds inte i PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="099c6-138">CryptoKeyRights and ActiveDirectoryRights are not supported in PowerShell Core.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ConvertFromSddlStringCommand+AccessRightTypeNames
Parameter Sets: (All)
Aliases:
Accepted values: FileSystemRights, RegistryRights, ActiveDirectoryRights, MutexRights, SemaphoreRights, CryptoKeyRights, EventWaitHandleRights

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="099c6-139">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="099c6-139">CommonParameters</span></span>

<span data-ttu-id="099c6-140">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="099c6-140">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="099c6-141">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="099c6-141">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="099c6-142">INDATA</span><span class="sxs-lookup"><span data-stu-id="099c6-142">INPUTS</span></span>

### <span data-ttu-id="099c6-143">System. String</span><span class="sxs-lookup"><span data-stu-id="099c6-143">System.String</span></span>

<span data-ttu-id="099c6-144">Du kan skicka vidare en SDDL-sträng till `ConvertFrom-SddlString` .</span><span class="sxs-lookup"><span data-stu-id="099c6-144">You can pipe a SDDL string to `ConvertFrom-SddlString`.</span></span>

## <span data-ttu-id="099c6-145">UTDATA</span><span class="sxs-lookup"><span data-stu-id="099c6-145">OUTPUTS</span></span>

## <span data-ttu-id="099c6-146">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="099c6-146">NOTES</span></span>

<span data-ttu-id="099c6-147">Den här cmdleten är endast tillgänglig på Windows-plattformar.</span><span class="sxs-lookup"><span data-stu-id="099c6-147">This cmdlet is only available on Windows platforms.</span></span>

## <span data-ttu-id="099c6-148">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="099c6-148">RELATED LINKS</span></span>

[<span data-ttu-id="099c6-149">Språk för säkerhets beskrivnings definition</span><span class="sxs-lookup"><span data-stu-id="099c6-149">Security Descriptor Definition Language</span></span>](/windows/win32/secauthz/security-descriptor-definition-language)
