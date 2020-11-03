---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 02/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/get-localuser?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-LocalUser
ms.openlocfilehash: 34210145bcddc8d9420552d637a6cd6e5f8e61cc
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263505"
---
# <span data-ttu-id="f2ae0-103">Get-LocalUser</span><span class="sxs-lookup"><span data-stu-id="f2ae0-103">Get-LocalUser</span></span>

## <span data-ttu-id="f2ae0-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="f2ae0-104">SYNOPSIS</span></span>
<span data-ttu-id="f2ae0-105">Hämtar lokala användar konton.</span><span class="sxs-lookup"><span data-stu-id="f2ae0-105">Gets local user accounts.</span></span>

## <span data-ttu-id="f2ae0-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f2ae0-106">SYNTAX</span></span>

### <span data-ttu-id="f2ae0-107">Standard (standard)</span><span class="sxs-lookup"><span data-stu-id="f2ae0-107">Default (Default)</span></span>

```
Get-LocalUser [[-Name] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="f2ae0-108">SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="f2ae0-108">SecurityIdentifier</span></span>

```
Get-LocalUser [[-SID] <SecurityIdentifier[]>] [<CommonParameters>]
```

## <span data-ttu-id="f2ae0-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="f2ae0-109">DESCRIPTION</span></span>

<span data-ttu-id="f2ae0-110">`Get-LocalUser`Cmdlet: en hämtar lokala användar konton.</span><span class="sxs-lookup"><span data-stu-id="f2ae0-110">The `Get-LocalUser` cmdlet gets local user accounts.</span></span> <span data-ttu-id="f2ae0-111">Denna cmdlet hämtar inbyggda standard användar konton, lokala användar konton som du har skapat och lokala konton som du har anslutit till Microsoft-konton.</span><span class="sxs-lookup"><span data-stu-id="f2ae0-111">This cmdlet gets default built-in user accounts, local user accounts that you created, and local accounts that you connected to Microsoft accounts.</span></span>

> [!NOTE]
> <span data-ttu-id="f2ae0-112">Modulen Microsoft. PowerShell. LocalAccounts är inte tillgänglig i 32-bitars PowerShell på ett 64-bitars system.</span><span class="sxs-lookup"><span data-stu-id="f2ae0-112">The Microsoft.PowerShell.LocalAccounts module is not available in 32-bit PowerShell on a 64-bit system.</span></span>

## <span data-ttu-id="f2ae0-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="f2ae0-113">EXAMPLES</span></span>

### <span data-ttu-id="f2ae0-114">Exempel 1: Hämta ett konto med hjälp av dess namn</span><span class="sxs-lookup"><span data-stu-id="f2ae0-114">Example 1: Get an account by using its name</span></span>

<span data-ttu-id="f2ae0-115">I det här exemplet får du ett användar konto med namnet AdminContoso02.</span><span class="sxs-lookup"><span data-stu-id="f2ae0-115">This example gets a user account named AdminContoso02.</span></span>

```powershell
Get-LocalUser -Name "AdminContoso02"
```

```Output
Name             Enabled Description
----             ------- -----------
AdminContoso02   True    Description of this account.
```

### <span data-ttu-id="f2ae0-116">Exempel 2: Hämta ett konto som är anslutet till en Microsoft-konto</span><span class="sxs-lookup"><span data-stu-id="f2ae0-116">Example 2: Get an account that is connected to a Microsoft account</span></span>

<span data-ttu-id="f2ae0-117">I det här exemplet får du ett användar konto som är anslutet till en Microsoft-konto.</span><span class="sxs-lookup"><span data-stu-id="f2ae0-117">This example gets a user account that is connected to a Microsoft account.</span></span> <span data-ttu-id="f2ae0-118">I det här exemplet används ett placeholder-värde för användar namnet för ett konto på Outlook.com.</span><span class="sxs-lookup"><span data-stu-id="f2ae0-118">This example uses a placeholder value for the username of an account at Outlook.com.</span></span>

```powershell
Get-LocalUser -Name "MicrosoftAccount\username@Outlook.com"
```

```Output
Name                                    Enabled  Description
----                                    -------  -----------
MicrosoftAccount\username@outlook.com  True     Description of this account.
```

### <span data-ttu-id="f2ae0-119">Exempel 3: Hämta ett konto som är anslutet till en Microsoft-konto</span><span class="sxs-lookup"><span data-stu-id="f2ae0-119">Example 3: Get an account that is connected to a Microsoft account</span></span>

<span data-ttu-id="f2ae0-120">Det här exemplet hämtar ett lokalt användar konto som har angivet SID.</span><span class="sxs-lookup"><span data-stu-id="f2ae0-120">This example gets a local user account that has the specified SID.</span></span>

```powershell
Get-LocalUser -SID S-1-5-21-9526073513-1762370368-3942940353-500
```

```Output
Name          Enabled Description
----          ------- -----------
Administrator True    Built-in account for administering the computer/domain
```

## <span data-ttu-id="f2ae0-121">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="f2ae0-121">PARAMETERS</span></span>

### <span data-ttu-id="f2ae0-122">-Name</span><span class="sxs-lookup"><span data-stu-id="f2ae0-122">-Name</span></span>

<span data-ttu-id="f2ae0-123">Anger en matris med namn på de användar konton som denna cmdlet hämtar.</span><span class="sxs-lookup"><span data-stu-id="f2ae0-123">Specifies an array of names of user accounts that this cmdlet gets.</span></span> <span data-ttu-id="f2ae0-124">Du kan använda jokertecknet.</span><span class="sxs-lookup"><span data-stu-id="f2ae0-124">You can use the wildcard character.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="f2ae0-125">-SID</span><span class="sxs-lookup"><span data-stu-id="f2ae0-125">-SID</span></span>

<span data-ttu-id="f2ae0-126">Anger en matris med säkerhets-ID: n (sid) för de användar konton som denna cmdlet hämtar.</span><span class="sxs-lookup"><span data-stu-id="f2ae0-126">Specifies an array of security IDs (SIDs) of user accounts that this cmdlet gets.</span></span>

```yaml
Type: System.Security.Principal.SecurityIdentifier[]
Parameter Sets: SecurityIdentifier
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="f2ae0-127">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f2ae0-127">CommonParameters</span></span>

<span data-ttu-id="f2ae0-128">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f2ae0-128">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f2ae0-129">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="f2ae0-129">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f2ae0-130">INDATA</span><span class="sxs-lookup"><span data-stu-id="f2ae0-130">INPUTS</span></span>

### <span data-ttu-id="f2ae0-131">System. String, system. Security. Principal. SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="f2ae0-131">System.String, System.Security.Principal.SecurityIdentifier</span></span>

<span data-ttu-id="f2ae0-132">Du kan skicka vidare en sträng eller SID till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f2ae0-132">You can pipe a string or SID to this cmdlet.</span></span>

## <span data-ttu-id="f2ae0-133">UTDATA</span><span class="sxs-lookup"><span data-stu-id="f2ae0-133">OUTPUTS</span></span>

### <span data-ttu-id="f2ae0-134">System. Management. Automation. SecurityAccountsManager. lokal användare []</span><span class="sxs-lookup"><span data-stu-id="f2ae0-134">System.Management.Automation.SecurityAccountsManager.LocalUser[]</span></span>

<span data-ttu-id="f2ae0-135">Den här cmdleten returnerar lokala användar konton.</span><span class="sxs-lookup"><span data-stu-id="f2ae0-135">This cmdlet returns local user accounts.</span></span>

## <span data-ttu-id="f2ae0-136">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="f2ae0-136">NOTES</span></span>

<span data-ttu-id="f2ae0-137">**PrincipalSource** -egenskapen för **lokal användare** -, **localgroup** -och **LocalPrincipal** -objekten beskriver objektets källa.</span><span class="sxs-lookup"><span data-stu-id="f2ae0-137">The **PrincipalSource** property on **LocalUser** , **LocalGroup** , and **LocalPrincipal** objects describes the source of the object.</span></span> <span data-ttu-id="f2ae0-138">De möjliga källorna är följande:</span><span class="sxs-lookup"><span data-stu-id="f2ae0-138">The possible sources are as follows:</span></span>

- <span data-ttu-id="f2ae0-139">Lokal</span><span class="sxs-lookup"><span data-stu-id="f2ae0-139">Local</span></span>
- <span data-ttu-id="f2ae0-140">Active Directory</span><span class="sxs-lookup"><span data-stu-id="f2ae0-140">Active Directory</span></span>
- <span data-ttu-id="f2ae0-141">Azure Active Directory grupp</span><span class="sxs-lookup"><span data-stu-id="f2ae0-141">Azure Active Directory group</span></span>
- <span data-ttu-id="f2ae0-142">Microsoft-konto</span><span class="sxs-lookup"><span data-stu-id="f2ae0-142">Microsoft Account</span></span>

<span data-ttu-id="f2ae0-143">**PrincipalSource** stöds endast av Windows 10, windows Server 2016 och senare versioner av operativ systemet Windows.</span><span class="sxs-lookup"><span data-stu-id="f2ae0-143">**PrincipalSource** is supported only by Windows 10, Windows Server 2016, and later versions of the Windows operating system.</span></span> <span data-ttu-id="f2ae0-144">För tidigare versioner är egenskapen tom.</span><span class="sxs-lookup"><span data-stu-id="f2ae0-144">For earlier versions, the property is blank.</span></span>

## <span data-ttu-id="f2ae0-145">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="f2ae0-145">RELATED LINKS</span></span>

[<span data-ttu-id="f2ae0-146">Disable-lokal användare</span><span class="sxs-lookup"><span data-stu-id="f2ae0-146">Disable-LocalUser</span></span>](Disable-LocalUser.md)

[<span data-ttu-id="f2ae0-147">Aktivera – lokal användare</span><span class="sxs-lookup"><span data-stu-id="f2ae0-147">Enable-LocalUser</span></span>](Enable-LocalUser.md)

[<span data-ttu-id="f2ae0-148">New-lokal användare</span><span class="sxs-lookup"><span data-stu-id="f2ae0-148">New-LocalUser</span></span>](New-LocalUser.md)

[<span data-ttu-id="f2ae0-149">Remove-lokal användare</span><span class="sxs-lookup"><span data-stu-id="f2ae0-149">Remove-LocalUser</span></span>](Remove-LocalUser.md)

[<span data-ttu-id="f2ae0-150">Byt namn – lokal användare</span><span class="sxs-lookup"><span data-stu-id="f2ae0-150">Rename-LocalUser</span></span>](Rename-LocalUser.md)

[<span data-ttu-id="f2ae0-151">Set-lokal användare</span><span class="sxs-lookup"><span data-stu-id="f2ae0-151">Set-LocalUser</span></span>](Set-LocalUser.md)
