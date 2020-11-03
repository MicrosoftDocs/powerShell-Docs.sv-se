---
external help file: Microsoft.PowerShell.Utility-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-sddlstring?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-SddlString
ms.openlocfilehash: 8552bec8029210553a8d4e51dcecb88948eb353e
ms.sourcegitcommit: c4906f4c9fa4ef1a16dcd6dd00ff960d19446d71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/01/2020
ms.locfileid: "93269379"
---
# <span data-ttu-id="92a7d-103">ConvertFrom-SddlString</span><span class="sxs-lookup"><span data-stu-id="92a7d-103">ConvertFrom-SddlString</span></span>

## <span data-ttu-id="92a7d-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="92a7d-104">SYNOPSIS</span></span>
<span data-ttu-id="92a7d-105">Konverterar en SDDL-sträng till ett anpassat objekt.</span><span class="sxs-lookup"><span data-stu-id="92a7d-105">Converts a SDDL string to a custom object.</span></span>

## <span data-ttu-id="92a7d-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="92a7d-106">SYNTAX</span></span>

### <span data-ttu-id="92a7d-107">Alla</span><span class="sxs-lookup"><span data-stu-id="92a7d-107">All</span></span>

```
ConvertFrom-SddlString [-Sddl] <String> [-Type <AccessRightTypeNames>] [<CommonParameters>]
```

## <span data-ttu-id="92a7d-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="92a7d-108">DESCRIPTION</span></span>

<span data-ttu-id="92a7d-109">`ConvertFrom-SddlString`Cmdleten konverterar en språk sträng för en säkerhets beskrivnings definition till ett anpassat **PSCustomObject** -objekt med följande egenskaper: Owner, Group, DiscretionaryAcl, SystemAcl och RawDescriptor.</span><span class="sxs-lookup"><span data-stu-id="92a7d-109">The `ConvertFrom-SddlString` cmdlet converts a Security Descriptor Definition Language string to a custom **PSCustomObject** object with the following properties: Owner, Group, DiscretionaryAcl, SystemAcl and RawDescriptor.</span></span>

<span data-ttu-id="92a7d-110">Egenskaperna Owner, Group, DiscretionaryAcl och SystemAcl innehåller en läsbar text representation av de åtkomst rättigheter som anges i en SDDL-sträng.</span><span class="sxs-lookup"><span data-stu-id="92a7d-110">Owner, Group, DiscretionaryAcl and SystemAcl properties contain a readable text representation of the access rights specified in a SDDL string.</span></span>

<span data-ttu-id="92a7d-111">Denna cmdlet introducerades i PowerShell 5,0.</span><span class="sxs-lookup"><span data-stu-id="92a7d-111">This cmdlet was introduced in PowerShell 5.0.</span></span>

## <span data-ttu-id="92a7d-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="92a7d-112">EXAMPLES</span></span>

### <span data-ttu-id="92a7d-113">Exempel 1: konvertera SDDL för Access-behörigheter till en PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="92a7d-113">Example 1: Convert file system access rights SDDL to a PSCustomObject</span></span>

```powershell
$acl = Get-Acl -Path C:\Windows
ConvertFrom-SddlString -Sddl $acl.Sddl
```

<span data-ttu-id="92a7d-114">Det första kommandot använder `Get-Acl` cmdleten för att hämta säkerhets beskrivningen för mappen C:\Windows och sparar den i variabeln.</span><span class="sxs-lookup"><span data-stu-id="92a7d-114">The first command uses the `Get-Acl` cmdlet to get the security descriptor for the C:\Windows folder and saves it in the variable.</span></span>

<span data-ttu-id="92a7d-115">Det andra kommandot använder `ConvertFrom-SddlString` cmdleten för att hämta text representationen av SDDL-strängen, som finns i SDDL-egenskapen för objektet som representerar säkerhets beskrivningen.</span><span class="sxs-lookup"><span data-stu-id="92a7d-115">The second command uses the `ConvertFrom-SddlString` cmdlet to get the text representation of the SDDL string, contained in the Sddl property of the object representing the security descriptor.</span></span>

### <span data-ttu-id="92a7d-116">Exempel 2: konvertera SDDL för register åtkomst behörigheter till en PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="92a7d-116">Example 2: Convert registry access rights SDDL to a PSCustomObject</span></span>

```powershell
$acl = Get-Acl HKLM:\SOFTWARE\Microsoft\
ConvertFrom-SddlString -Sddl $acl.Sddl -Type RegistryRights
```

<span data-ttu-id="92a7d-117">Det första kommandot använder `Get-Acl` cmdleten för att hämta säkerhets beskrivningen för HKLM: \ SOFTWARE\Microsoft\-nyckeln och sparar den i variabeln.</span><span class="sxs-lookup"><span data-stu-id="92a7d-117">The first command uses the `Get-Acl` cmdlet to get the security descriptor for the HKLM:\SOFTWARE\Microsoft\ key and saves it in the variable.</span></span>

<span data-ttu-id="92a7d-118">Det andra kommandot använder `ConvertFrom-SddlString` cmdleten för att hämta text representationen av SDDL-strängen, som finns i SDDL-egenskapen för objektet som representerar säkerhets beskrivningen.</span><span class="sxs-lookup"><span data-stu-id="92a7d-118">The second command uses the `ConvertFrom-SddlString` cmdlet to get the text representation of the SDDL string, contained in the Sddl property of the object representing the security descriptor.</span></span>

<span data-ttu-id="92a7d-119">`-Type`Parametern används för att ange att SDDL-strängen representerar en säkerhets beskrivning för registret.</span><span class="sxs-lookup"><span data-stu-id="92a7d-119">It uses the `-Type` parameter to specify that SDDL string represents a registry security descriptor.</span></span>

### <span data-ttu-id="92a7d-120">Exempel 3: konvertera SDDL-behörighet för register åtkomst till en PSCustomObject med hjälp av ConvertFrom-SddlString med och utan `-Type` parametern</span><span class="sxs-lookup"><span data-stu-id="92a7d-120">Example 3: Convert registry access rights SDDL to a PSCustomObject by using ConvertFrom-SddlString with and without the `-Type` parameter</span></span>

```powershell
$acl = Get-Acl -Path HKLM:\SOFTWARE\Microsoft\

ConvertFrom-SddlString -Sddl $acl.Sddl | Foreach-Object {$_.DiscretionaryAcl[0]}

BUILTIN\Administrators: AccessAllowed (ChangePermissions, CreateDirectories, Delete, ExecuteKey, FullControl, GenericExecute, GenericWrite, ListDirectory, ReadExtendedAttributes, ReadPermissions, TakeOwnership, Traverse, WriteData, WriteExtendedAttributes, WriteKey)

ConvertFrom-SddlString -Sddl $acl.Sddl -Type RegistryRights | Foreach-Object {$_.DiscretionaryAcl[0]}

BUILTIN\Administrators: AccessAllowed (ChangePermissions, CreateLink, CreateSubKey, Delete, EnumerateSubKeys, ExecuteKey, FullControl, GenericExecute, GenericWrite, Notify, QueryValues, ReadPermissions, SetValue, TakeOwnership, WriteKey)
```

<span data-ttu-id="92a7d-121">Det första kommandot använder `Get-Acl` cmdleten för att hämta säkerhets beskrivningen för HKLM: \ SOFTWARE\Microsoft\-nyckeln och sparar den i variabeln.</span><span class="sxs-lookup"><span data-stu-id="92a7d-121">The first command uses the `Get-Acl` cmdlet to get the security descriptor for the HKLM:\SOFTWARE\Microsoft\ key and saves it in the variable.</span></span>

<span data-ttu-id="92a7d-122">Det andra kommandot använder `ConvertFrom-SddlString` cmdleten för att hämta text representationen av SDDL-strängen, som finns i SDDL-egenskapen för objektet som representerar säkerhets beskrivningen.</span><span class="sxs-lookup"><span data-stu-id="92a7d-122">The second command uses the `ConvertFrom-SddlString` cmdlet to get the text representation of the SDDL string, contained in the Sddl property of the object representing the security descriptor.</span></span>

<span data-ttu-id="92a7d-123">Den använder inte `-Type` parametern, så åtkomst rättigheterna som visas gäller för fil system.</span><span class="sxs-lookup"><span data-stu-id="92a7d-123">It doesn't use the `-Type` parameter, so the access rights shown are for file system.</span></span>

<span data-ttu-id="92a7d-124">Det tredje kommandot använder `ConvertFrom-SddlString` cmdleten med `-Type` parametern, så åtkomst rättigheterna som returneras är för registret.</span><span class="sxs-lookup"><span data-stu-id="92a7d-124">The third command uses the `ConvertFrom-SddlString` cmdlet with the `-Type` parameter, so the access rights returned are for registry.</span></span>

## <span data-ttu-id="92a7d-125">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="92a7d-125">PARAMETERS</span></span>

### <span data-ttu-id="92a7d-126">-SDDL</span><span class="sxs-lookup"><span data-stu-id="92a7d-126">-Sddl</span></span>

<span data-ttu-id="92a7d-127">Anger den sträng som representerar säkerhets beskrivningen i SDDL-syntax.</span><span class="sxs-lookup"><span data-stu-id="92a7d-127">Specifies the string representing the security descriptor in SDDL syntax.</span></span>

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

### <span data-ttu-id="92a7d-128">-Typ</span><span class="sxs-lookup"><span data-stu-id="92a7d-128">-Type</span></span>

<span data-ttu-id="92a7d-129">Anger vilken typ av rättigheter som SDDL-sträng representerar.</span><span class="sxs-lookup"><span data-stu-id="92a7d-129">Specifies the type of rights that SDDL string represents.</span></span>

<span data-ttu-id="92a7d-130">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="92a7d-130">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="92a7d-131">FileSystemRights</span><span class="sxs-lookup"><span data-stu-id="92a7d-131">FileSystemRights</span></span>
- <span data-ttu-id="92a7d-132">RegistryRights</span><span class="sxs-lookup"><span data-stu-id="92a7d-132">RegistryRights</span></span>
- <span data-ttu-id="92a7d-133">ActiveDirectoryRights</span><span class="sxs-lookup"><span data-stu-id="92a7d-133">ActiveDirectoryRights</span></span>
- <span data-ttu-id="92a7d-134">MutexRights</span><span class="sxs-lookup"><span data-stu-id="92a7d-134">MutexRights</span></span>
- <span data-ttu-id="92a7d-135">SemaphoreRights</span><span class="sxs-lookup"><span data-stu-id="92a7d-135">SemaphoreRights</span></span>
- <span data-ttu-id="92a7d-136">CryptoKeyRights</span><span class="sxs-lookup"><span data-stu-id="92a7d-136">CryptoKeyRights</span></span>
- <span data-ttu-id="92a7d-137">EventWaitHandleRights</span><span class="sxs-lookup"><span data-stu-id="92a7d-137">EventWaitHandleRights</span></span>

<span data-ttu-id="92a7d-138">Som standard använder cmdlet fil system rättigheter.</span><span class="sxs-lookup"><span data-stu-id="92a7d-138">By default cmdlet uses file system rights.</span></span>

<span data-ttu-id="92a7d-139">CryptoKeyRights och ActiveDirectoryRights stöds inte i PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="92a7d-139">CryptoKeyRights and ActiveDirectoryRights are not supported in PowerShell Core.</span></span>

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

### <span data-ttu-id="92a7d-140">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="92a7d-140">CommonParameters</span></span>

<span data-ttu-id="92a7d-141">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="92a7d-141">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="92a7d-142">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="92a7d-142">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="92a7d-143">INDATA</span><span class="sxs-lookup"><span data-stu-id="92a7d-143">INPUTS</span></span>

### <span data-ttu-id="92a7d-144">System. String</span><span class="sxs-lookup"><span data-stu-id="92a7d-144">System.String</span></span>

<span data-ttu-id="92a7d-145">Du kan skicka vidare en SDDL-sträng till `ConvertFrom-SddlString` .</span><span class="sxs-lookup"><span data-stu-id="92a7d-145">You can pipe a SDDL string to `ConvertFrom-SddlString`.</span></span>

## <span data-ttu-id="92a7d-146">UTDATA</span><span class="sxs-lookup"><span data-stu-id="92a7d-146">OUTPUTS</span></span>

## <span data-ttu-id="92a7d-147">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="92a7d-147">NOTES</span></span>

## <span data-ttu-id="92a7d-148">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="92a7d-148">RELATED LINKS</span></span>

[<span data-ttu-id="92a7d-149">Språk för säkerhets beskrivnings definition</span><span class="sxs-lookup"><span data-stu-id="92a7d-149">Security Descriptor Definition Language</span></span>](/windows/win32/secauthz/security-descriptor-definition-language)
