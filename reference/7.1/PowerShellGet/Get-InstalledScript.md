---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/get-installedscript?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-InstalledScript
ms.openlocfilehash: 6b99eb73fb126b67b97fc360b2f0474710b4cc52
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266336"
---
# <span data-ttu-id="6fa08-103">Get-InstalledScript</span><span class="sxs-lookup"><span data-stu-id="6fa08-103">Get-InstalledScript</span></span>

## <span data-ttu-id="6fa08-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="6fa08-104">SYNOPSIS</span></span>
<span data-ttu-id="6fa08-105">Hämtar ett installerat skript.</span><span class="sxs-lookup"><span data-stu-id="6fa08-105">Gets an installed script.</span></span>

## <span data-ttu-id="6fa08-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6fa08-106">SYNTAX</span></span>

```
Get-InstalledScript [[-Name] <String[]>] [-MinimumVersion <String>] [-RequiredVersion <String>]
 [-MaximumVersion <String>] [-AllowPrerelease] [<CommonParameters>]
```

## <span data-ttu-id="6fa08-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="6fa08-107">DESCRIPTION</span></span>

<span data-ttu-id="6fa08-108">**Get-InstalledScript** -cmdlet: en hämtar installerade skript för CurrentUser-och allusers-scope.</span><span class="sxs-lookup"><span data-stu-id="6fa08-108">The **Get-InstalledScript** cmdlet gets installed scripts for CurrentUser and AllUsers scopes.</span></span>

## <span data-ttu-id="6fa08-109">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="6fa08-109">EXAMPLES</span></span>

### <span data-ttu-id="6fa08-110">Exempel 1: Hämta alla installerade skript</span><span class="sxs-lookup"><span data-stu-id="6fa08-110">Example 1: Get all installed scripts</span></span>

```
PS C:\> Get-InstalledScript
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Required-Script1                    Script     local1               Description for the Required-Script1 script
2.5        Required-Script2                    Script     local1               Description for the Required-Script2 script
2.5        Required-Script3                    Script     local1               Description for the Required-Script3 script
2.0        Script-WithDependencies1            Script     local1               Description for the Script-WithDependencies1 script
```

<span data-ttu-id="6fa08-111">Det här kommandot hämtar alla installerade skript.</span><span class="sxs-lookup"><span data-stu-id="6fa08-111">This command gets all installed scripts.</span></span>

### <span data-ttu-id="6fa08-112">Exempel 2: Hämta installerade skript efter namn</span><span class="sxs-lookup"><span data-stu-id="6fa08-112">Example 2: Get installed scripts by name</span></span>

```
PS C:\> Get-InstalledScript -Name "Required-Scri*"
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Required-Script1                    Script     local1               Description for the Required-Script1 script
2.5        Required-Script2                    Script     local1               Description for the Required-Script2 script
2.5        Required-Script3                    Script     local1               Description for the Required-Script3 script
```

<span data-ttu-id="6fa08-113">Det här kommandot hämtar skript där namnet börjar med required-Scri.</span><span class="sxs-lookup"><span data-stu-id="6fa08-113">This command gets scripts where the name begins with Required-Scri.</span></span>

## <span data-ttu-id="6fa08-114">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="6fa08-114">PARAMETERS</span></span>

### <span data-ttu-id="6fa08-115">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="6fa08-115">-AllowPrerelease</span></span>

<span data-ttu-id="6fa08-116">Innehåller i de resultat skript som marker ATS som en för hands version.</span><span class="sxs-lookup"><span data-stu-id="6fa08-116">Includes in the results scripts marked as a prerelease.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6fa08-117">– MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="6fa08-117">-MaximumVersion</span></span>

<span data-ttu-id="6fa08-118">Anger den maximala eller senaste versionen av ett skript som ska hämtas.</span><span class="sxs-lookup"><span data-stu-id="6fa08-118">Specifies the maximum, or latest, version of a script to get.</span></span>
<span data-ttu-id="6fa08-119">Parametrarna *MaximumVersion* och *RequiredVersion* kan inte anges samtidigt. Du kan inte använda båda parametrarna i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="6fa08-119">The *MaximumVersion* and *RequiredVersion* parameters are mutually exclusive; you cannot use both parameters in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6fa08-120">– MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="6fa08-120">-MinimumVersion</span></span>

<span data-ttu-id="6fa08-121">Anger den lägsta versionen av ett skript som ska hämtas.</span><span class="sxs-lookup"><span data-stu-id="6fa08-121">Specifies the minimum version of a script to get.</span></span>
<span data-ttu-id="6fa08-122">Parametrarna *MinimumVersion* och *RequiredVersion* kan inte anges samtidigt. Du kan inte använda båda parametrarna i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="6fa08-122">The *MinimumVersion* and *RequiredVersion* parameters are mutually exclusive; you cannot use both parameters in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6fa08-123">-Name</span><span class="sxs-lookup"><span data-stu-id="6fa08-123">-Name</span></span>

<span data-ttu-id="6fa08-124">Anger en matris med namn på skript som ska hämtas.</span><span class="sxs-lookup"><span data-stu-id="6fa08-124">Specifies an array of names of scripts to get.</span></span>
<span data-ttu-id="6fa08-125">Jokertecken accepteras.</span><span class="sxs-lookup"><span data-stu-id="6fa08-125">Wildcards are accepted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="6fa08-126">– RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="6fa08-126">-RequiredVersion</span></span>

<span data-ttu-id="6fa08-127">Anger den exakta versionen av ett skript som ska hämtas.</span><span class="sxs-lookup"><span data-stu-id="6fa08-127">Specifies the exact version of a script to get.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6fa08-128">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6fa08-128">CommonParameters</span></span>

<span data-ttu-id="6fa08-129">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="6fa08-129">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6fa08-130">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="6fa08-130">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6fa08-131">INDATA</span><span class="sxs-lookup"><span data-stu-id="6fa08-131">INPUTS</span></span>

### <span data-ttu-id="6fa08-132">System.String[]</span><span class="sxs-lookup"><span data-stu-id="6fa08-132">System.String[]</span></span>

### <span data-ttu-id="6fa08-133">System. String</span><span class="sxs-lookup"><span data-stu-id="6fa08-133">System.String</span></span>

## <span data-ttu-id="6fa08-134">UTDATA</span><span class="sxs-lookup"><span data-stu-id="6fa08-134">OUTPUTS</span></span>

### <span data-ttu-id="6fa08-135">System. Object</span><span class="sxs-lookup"><span data-stu-id="6fa08-135">System.Object</span></span>

## <span data-ttu-id="6fa08-136">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="6fa08-136">NOTES</span></span>

## <span data-ttu-id="6fa08-137">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="6fa08-137">RELATED LINKS</span></span>

[<span data-ttu-id="6fa08-138">Installera – skript</span><span class="sxs-lookup"><span data-stu-id="6fa08-138">Install-Script</span></span>](Install-Script.md)

[<span data-ttu-id="6fa08-139">Avinstallera – skript</span><span class="sxs-lookup"><span data-stu-id="6fa08-139">Uninstall-Script</span></span>](Uninstall-Script.md)

