---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/get-installedscript?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-InstalledScript
ms.openlocfilehash: fe5fc0feb34fda87dab987f33140992a346017a1
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710740"
---
# <span data-ttu-id="fc57c-102">Get-InstalledScript</span><span class="sxs-lookup"><span data-stu-id="fc57c-102">Get-InstalledScript</span></span>

## <span data-ttu-id="fc57c-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="fc57c-103">SYNOPSIS</span></span>
<span data-ttu-id="fc57c-104">Hämtar ett installerat skript.</span><span class="sxs-lookup"><span data-stu-id="fc57c-104">Gets an installed script.</span></span>

## <span data-ttu-id="fc57c-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="fc57c-105">SYNTAX</span></span>

```
Get-InstalledScript [[-Name] <String[]>] [-MinimumVersion <String>] [-RequiredVersion <String>]
 [-MaximumVersion <String>] [-AllowPrerelease] [<CommonParameters>]
```

## <span data-ttu-id="fc57c-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="fc57c-106">DESCRIPTION</span></span>

<span data-ttu-id="fc57c-107">**Get-InstalledScript** -cmdlet: en hämtar installerade skript för CurrentUser-och allusers-scope.</span><span class="sxs-lookup"><span data-stu-id="fc57c-107">The **Get-InstalledScript** cmdlet gets installed scripts for CurrentUser and AllUsers scopes.</span></span>

## <span data-ttu-id="fc57c-108">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="fc57c-108">EXAMPLES</span></span>

### <span data-ttu-id="fc57c-109">Exempel 1: Hämta alla installerade skript</span><span class="sxs-lookup"><span data-stu-id="fc57c-109">Example 1: Get all installed scripts</span></span>

```
PS C:\> Get-InstalledScript
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Required-Script1                    Script     local1               Description for the Required-Script1 script
2.5        Required-Script2                    Script     local1               Description for the Required-Script2 script
2.5        Required-Script3                    Script     local1               Description for the Required-Script3 script
2.0        Script-WithDependencies1            Script     local1               Description for the Script-WithDependencies1 script
```

<span data-ttu-id="fc57c-110">Det här kommandot hämtar alla installerade skript.</span><span class="sxs-lookup"><span data-stu-id="fc57c-110">This command gets all installed scripts.</span></span>

### <span data-ttu-id="fc57c-111">Exempel 2: Hämta installerade skript efter namn</span><span class="sxs-lookup"><span data-stu-id="fc57c-111">Example 2: Get installed scripts by name</span></span>

```
PS C:\> Get-InstalledScript -Name "Required-Scri*"
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Required-Script1                    Script     local1               Description for the Required-Script1 script
2.5        Required-Script2                    Script     local1               Description for the Required-Script2 script
2.5        Required-Script3                    Script     local1               Description for the Required-Script3 script
```

<span data-ttu-id="fc57c-112">Det här kommandot hämtar skript där namnet börjar med required-Scri.</span><span class="sxs-lookup"><span data-stu-id="fc57c-112">This command gets scripts where the name begins with Required-Scri.</span></span>

## <span data-ttu-id="fc57c-113">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="fc57c-113">PARAMETERS</span></span>

### <span data-ttu-id="fc57c-114">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="fc57c-114">-AllowPrerelease</span></span>

<span data-ttu-id="fc57c-115">Innehåller i de resultat skript som marker ATS som en för hands version.</span><span class="sxs-lookup"><span data-stu-id="fc57c-115">Includes in the results scripts marked as a prerelease.</span></span>

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

### <span data-ttu-id="fc57c-116">– MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="fc57c-116">-MaximumVersion</span></span>

<span data-ttu-id="fc57c-117">Anger den maximala eller senaste versionen av ett skript som ska hämtas.</span><span class="sxs-lookup"><span data-stu-id="fc57c-117">Specifies the maximum, or latest, version of a script to get.</span></span>
<span data-ttu-id="fc57c-118">Parametrarna *MaximumVersion* och *RequiredVersion* kan inte anges samtidigt. Du kan inte använda båda parametrarna i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="fc57c-118">The *MaximumVersion* and *RequiredVersion* parameters are mutually exclusive; you cannot use both parameters in the same command.</span></span>

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

### <span data-ttu-id="fc57c-119">– MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="fc57c-119">-MinimumVersion</span></span>

<span data-ttu-id="fc57c-120">Anger den lägsta versionen av ett skript som ska hämtas.</span><span class="sxs-lookup"><span data-stu-id="fc57c-120">Specifies the minimum version of a script to get.</span></span>
<span data-ttu-id="fc57c-121">Parametrarna *MinimumVersion* och *RequiredVersion* kan inte anges samtidigt. Du kan inte använda båda parametrarna i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="fc57c-121">The *MinimumVersion* and *RequiredVersion* parameters are mutually exclusive; you cannot use both parameters in the same command.</span></span>

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

### <span data-ttu-id="fc57c-122">-Name</span><span class="sxs-lookup"><span data-stu-id="fc57c-122">-Name</span></span>

<span data-ttu-id="fc57c-123">Anger en matris med namn på skript som ska hämtas.</span><span class="sxs-lookup"><span data-stu-id="fc57c-123">Specifies an array of names of scripts to get.</span></span>
<span data-ttu-id="fc57c-124">Jokertecken accepteras.</span><span class="sxs-lookup"><span data-stu-id="fc57c-124">Wildcards are accepted.</span></span>

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

### <span data-ttu-id="fc57c-125">– RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="fc57c-125">-RequiredVersion</span></span>

<span data-ttu-id="fc57c-126">Anger den exakta versionen av ett skript som ska hämtas.</span><span class="sxs-lookup"><span data-stu-id="fc57c-126">Specifies the exact version of a script to get.</span></span>

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

### <span data-ttu-id="fc57c-127">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="fc57c-127">CommonParameters</span></span>

<span data-ttu-id="fc57c-128">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="fc57c-128">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="fc57c-129">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="fc57c-129">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="fc57c-130">INDATA</span><span class="sxs-lookup"><span data-stu-id="fc57c-130">INPUTS</span></span>

### <span data-ttu-id="fc57c-131">System.String[]</span><span class="sxs-lookup"><span data-stu-id="fc57c-131">System.String[]</span></span>

### <span data-ttu-id="fc57c-132">System. String</span><span class="sxs-lookup"><span data-stu-id="fc57c-132">System.String</span></span>

## <span data-ttu-id="fc57c-133">UTDATA</span><span class="sxs-lookup"><span data-stu-id="fc57c-133">OUTPUTS</span></span>

### <span data-ttu-id="fc57c-134">System. Object</span><span class="sxs-lookup"><span data-stu-id="fc57c-134">System.Object</span></span>

## <span data-ttu-id="fc57c-135">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="fc57c-135">NOTES</span></span>

## <span data-ttu-id="fc57c-136">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="fc57c-136">RELATED LINKS</span></span>

[<span data-ttu-id="fc57c-137">Installera – skript</span><span class="sxs-lookup"><span data-stu-id="fc57c-137">Install-Script</span></span>](Install-Script.md)

[<span data-ttu-id="fc57c-138">Avinstallera – skript</span><span class="sxs-lookup"><span data-stu-id="fc57c-138">Uninstall-Script</span></span>](Uninstall-Script.md)

