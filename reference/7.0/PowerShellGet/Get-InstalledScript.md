---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/get-installedscript?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-InstalledScript
ms.openlocfilehash: a90ece844d5a271402537f17c601bf2e36b5ed8c
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93262298"
---
# <span data-ttu-id="d8e71-103">Get-InstalledScript</span><span class="sxs-lookup"><span data-stu-id="d8e71-103">Get-InstalledScript</span></span>

## <span data-ttu-id="d8e71-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="d8e71-104">SYNOPSIS</span></span>
<span data-ttu-id="d8e71-105">Hämtar ett installerat skript.</span><span class="sxs-lookup"><span data-stu-id="d8e71-105">Gets an installed script.</span></span>

## <span data-ttu-id="d8e71-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d8e71-106">SYNTAX</span></span>

```
Get-InstalledScript [[-Name] <String[]>] [-MinimumVersion <String>] [-RequiredVersion <String>]
 [-MaximumVersion <String>] [-AllowPrerelease] [<CommonParameters>]
```

## <span data-ttu-id="d8e71-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="d8e71-107">DESCRIPTION</span></span>

<span data-ttu-id="d8e71-108">**Get-InstalledScript** -cmdlet: en hämtar installerade skript för CurrentUser-och allusers-scope.</span><span class="sxs-lookup"><span data-stu-id="d8e71-108">The **Get-InstalledScript** cmdlet gets installed scripts for CurrentUser and AllUsers scopes.</span></span>

## <span data-ttu-id="d8e71-109">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="d8e71-109">EXAMPLES</span></span>

### <span data-ttu-id="d8e71-110">Exempel 1: Hämta alla installerade skript</span><span class="sxs-lookup"><span data-stu-id="d8e71-110">Example 1: Get all installed scripts</span></span>

```
PS C:\> Get-InstalledScript
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Required-Script1                    Script     local1               Description for the Required-Script1 script
2.5        Required-Script2                    Script     local1               Description for the Required-Script2 script
2.5        Required-Script3                    Script     local1               Description for the Required-Script3 script
2.0        Script-WithDependencies1            Script     local1               Description for the Script-WithDependencies1 script
```

<span data-ttu-id="d8e71-111">Det här kommandot hämtar alla installerade skript.</span><span class="sxs-lookup"><span data-stu-id="d8e71-111">This command gets all installed scripts.</span></span>

### <span data-ttu-id="d8e71-112">Exempel 2: Hämta installerade skript efter namn</span><span class="sxs-lookup"><span data-stu-id="d8e71-112">Example 2: Get installed scripts by name</span></span>

```
PS C:\> Get-InstalledScript -Name "Required-Scri*"
Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Required-Script1                    Script     local1               Description for the Required-Script1 script
2.5        Required-Script2                    Script     local1               Description for the Required-Script2 script
2.5        Required-Script3                    Script     local1               Description for the Required-Script3 script
```

<span data-ttu-id="d8e71-113">Det här kommandot hämtar skript där namnet börjar med required-Scri.</span><span class="sxs-lookup"><span data-stu-id="d8e71-113">This command gets scripts where the name begins with Required-Scri.</span></span>

## <span data-ttu-id="d8e71-114">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="d8e71-114">PARAMETERS</span></span>

### <span data-ttu-id="d8e71-115">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="d8e71-115">-AllowPrerelease</span></span>

<span data-ttu-id="d8e71-116">Innehåller i de resultat skript som marker ATS som en för hands version.</span><span class="sxs-lookup"><span data-stu-id="d8e71-116">Includes in the results scripts marked as a prerelease.</span></span>

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

### <span data-ttu-id="d8e71-117">– MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="d8e71-117">-MaximumVersion</span></span>

<span data-ttu-id="d8e71-118">Anger den maximala eller senaste versionen av ett skript som ska hämtas.</span><span class="sxs-lookup"><span data-stu-id="d8e71-118">Specifies the maximum, or latest, version of a script to get.</span></span>
<span data-ttu-id="d8e71-119">Parametrarna *MaximumVersion* och *RequiredVersion* kan inte anges samtidigt. Du kan inte använda båda parametrarna i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="d8e71-119">The *MaximumVersion* and *RequiredVersion* parameters are mutually exclusive; you cannot use both parameters in the same command.</span></span>

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

### <span data-ttu-id="d8e71-120">– MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="d8e71-120">-MinimumVersion</span></span>

<span data-ttu-id="d8e71-121">Anger den lägsta versionen av ett skript som ska hämtas.</span><span class="sxs-lookup"><span data-stu-id="d8e71-121">Specifies the minimum version of a script to get.</span></span>
<span data-ttu-id="d8e71-122">Parametrarna *MinimumVersion* och *RequiredVersion* kan inte anges samtidigt. Du kan inte använda båda parametrarna i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="d8e71-122">The *MinimumVersion* and *RequiredVersion* parameters are mutually exclusive; you cannot use both parameters in the same command.</span></span>

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

### <span data-ttu-id="d8e71-123">-Name</span><span class="sxs-lookup"><span data-stu-id="d8e71-123">-Name</span></span>

<span data-ttu-id="d8e71-124">Anger en matris med namn på skript som ska hämtas.</span><span class="sxs-lookup"><span data-stu-id="d8e71-124">Specifies an array of names of scripts to get.</span></span>
<span data-ttu-id="d8e71-125">Jokertecken accepteras.</span><span class="sxs-lookup"><span data-stu-id="d8e71-125">Wildcards are accepted.</span></span>

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

### <span data-ttu-id="d8e71-126">– RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="d8e71-126">-RequiredVersion</span></span>

<span data-ttu-id="d8e71-127">Anger den exakta versionen av ett skript som ska hämtas.</span><span class="sxs-lookup"><span data-stu-id="d8e71-127">Specifies the exact version of a script to get.</span></span>

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

### <span data-ttu-id="d8e71-128">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d8e71-128">CommonParameters</span></span>

<span data-ttu-id="d8e71-129">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d8e71-129">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d8e71-130">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="d8e71-130">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d8e71-131">INDATA</span><span class="sxs-lookup"><span data-stu-id="d8e71-131">INPUTS</span></span>

### <span data-ttu-id="d8e71-132">System.String[]</span><span class="sxs-lookup"><span data-stu-id="d8e71-132">System.String[]</span></span>

### <span data-ttu-id="d8e71-133">System. String</span><span class="sxs-lookup"><span data-stu-id="d8e71-133">System.String</span></span>

## <span data-ttu-id="d8e71-134">UTDATA</span><span class="sxs-lookup"><span data-stu-id="d8e71-134">OUTPUTS</span></span>

### <span data-ttu-id="d8e71-135">System. Object</span><span class="sxs-lookup"><span data-stu-id="d8e71-135">System.Object</span></span>

## <span data-ttu-id="d8e71-136">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="d8e71-136">NOTES</span></span>

## <span data-ttu-id="d8e71-137">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="d8e71-137">RELATED LINKS</span></span>

[<span data-ttu-id="d8e71-138">Installera – skript</span><span class="sxs-lookup"><span data-stu-id="d8e71-138">Install-Script</span></span>](Install-Script.md)

[<span data-ttu-id="d8e71-139">Avinstallera – skript</span><span class="sxs-lookup"><span data-stu-id="d8e71-139">Uninstall-Script</span></span>](Uninstall-Script.md)
