---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-pssessioncapability?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSSessionCapability
ms.openlocfilehash: e81302a442294a7eeab81c6e8e1c6b7fd0cfb5fe
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710506"
---
# <span data-ttu-id="899cc-102">Get-PSSessionCapability</span><span class="sxs-lookup"><span data-stu-id="899cc-102">Get-PSSessionCapability</span></span>

## <span data-ttu-id="899cc-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="899cc-103">SYNOPSIS</span></span>
<span data-ttu-id="899cc-104">Hämtar funktionerna för en speciell användare i en begränsad sessions konfiguration.</span><span class="sxs-lookup"><span data-stu-id="899cc-104">Gets the capabilities of a specific user on a constrained session configuration.</span></span>

## <span data-ttu-id="899cc-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="899cc-105">SYNTAX</span></span>

```
Get-PSSessionCapability [-ConfigurationName] <String> [-Username] <String> [-Full] [<CommonParameters>]
```

## <span data-ttu-id="899cc-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="899cc-106">DESCRIPTION</span></span>

<span data-ttu-id="899cc-107">Cmdlet: en **Get-PSSessionCapability** hämtar funktionerna för en speciell användare i en begränsad sessions konfiguration.</span><span class="sxs-lookup"><span data-stu-id="899cc-107">The **Get-PSSessionCapability** cmdlet gets the capabilities of a specific user on a constrained session configuration.</span></span>
<span data-ttu-id="899cc-108">Använd denna cmdlet för att granska anpassade sessionsinställningar för användare.</span><span class="sxs-lookup"><span data-stu-id="899cc-108">Use this cmdlet to audit customized session configurations for users.</span></span>

<span data-ttu-id="899cc-109">Från och med Windows PowerShell 5,0 kan du använda egenskapen **RoleDefinitions** i en session konfigurations fil (. PSSC).</span><span class="sxs-lookup"><span data-stu-id="899cc-109">Starting in Windows PowerShell 5.0, you can use the **RoleDefinitions** property in a session configuration (.pssc) file.</span></span>
<span data-ttu-id="899cc-110">Med den här egenskapen kan du ge användarna olika funktioner på en begränsad slut punkt baserat på grupp medlemskap.</span><span class="sxs-lookup"><span data-stu-id="899cc-110">Using this property lets you grant users different capabilities on a single constrained endpoint based on group membership.</span></span>
<span data-ttu-id="899cc-111">Cmdleten **Get-PSSessionCapability** minskar komplexiteten när du granskar de här slut punkterna genom att låta dig bestämma de exakta funktioner som beviljas en användare.</span><span class="sxs-lookup"><span data-stu-id="899cc-111">The **Get-PSSessionCapability** cmdlet reduces complexity when auditing these endpoints by letting you determine the exact capabilities granted to a user.</span></span>

<span data-ttu-id="899cc-112">Som standard returnerar cmdleten **Get-PSSessionCapability** en lista med kommandon som den angivna användaren kan köra i den angivna slut punkten.</span><span class="sxs-lookup"><span data-stu-id="899cc-112">By default, the **Get-PSSessionCapability** cmdlet returns a list of commands the specified user can run in the specified endpoint.</span></span>
<span data-ttu-id="899cc-113">Detta motsvarar användaren som kör **Get-Command** i den angivna slut punkten.</span><span class="sxs-lookup"><span data-stu-id="899cc-113">This is equivalent to the user running **Get-Command** in the specified endpoint.</span></span>
<span data-ttu-id="899cc-114">Vid körning med *fullständig* parameter returnerar denna cmdlet ett **InitialSessionState** -objekt.</span><span class="sxs-lookup"><span data-stu-id="899cc-114">When run with the *Full* parameter, this cmdlet returns an **InitialSessionState** object.</span></span>
<span data-ttu-id="899cc-115">Det här objektet innehåller information om PowerShell-körnings utrymme som den angivna användaren skulle interagera med för den angivna slut punkten.</span><span class="sxs-lookup"><span data-stu-id="899cc-115">This object contains details about the PowerShell runspace the specified user would interact with for the specified endpoint.</span></span>
<span data-ttu-id="899cc-116">Den innehåller information som språk läge, körnings princip och miljövariabler.</span><span class="sxs-lookup"><span data-stu-id="899cc-116">It includes information such as Language Mode, Execution Policy, and Environmental Variables.</span></span>

## <span data-ttu-id="899cc-117">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="899cc-117">EXAMPLES</span></span>

### <span data-ttu-id="899cc-118">Exempel 1: Hämta kommandon som är tillgängliga för en användare</span><span class="sxs-lookup"><span data-stu-id="899cc-118">Example 1: Get commands available for a user</span></span>

```powershell
Get-PSSessionCapability -ConfigurationName Endpoint1 -Username 'CONTOSO\User'
```

<span data-ttu-id="899cc-119">Det här exemplet returnerar de kommandon som är tillgängliga för användaren CONTOSO\User vid anslutning till Endpoint1-begränsade slut punkter på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="899cc-119">This example returns the commands available to the user CONTOSO\User when connecting to the Endpoint1 constrained endpoint on the local computer.</span></span>

### <span data-ttu-id="899cc-120">Exempel 2: Hämta information om en körnings utrymme för en användare</span><span class="sxs-lookup"><span data-stu-id="899cc-120">Example 2: Get details about a runspace for a user</span></span>

```powershell
Get-PSSessionCapability -ConfigurationName Endpoint1 -Username 'CONTOSO\User' -Full
```

<span data-ttu-id="899cc-121">Det här exemplet returnerar information om körnings utrymme som användaren CONTOSO\User skulle interagera med vid anslutning till Endpoint1-begränsad slut punkt.</span><span class="sxs-lookup"><span data-stu-id="899cc-121">This example returns details about the runspace the user CONTOSO\User would interact with when connecting to the Endpoint1 constrained endpoint.</span></span>

## <span data-ttu-id="899cc-122">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="899cc-122">PARAMETERS</span></span>

### <span data-ttu-id="899cc-123">– ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="899cc-123">-ConfigurationName</span></span>

<span data-ttu-id="899cc-124">Anger den begränsade sessionen som du inspekterar (slut punkt).</span><span class="sxs-lookup"><span data-stu-id="899cc-124">Specifies the constrained session configuration (endpoint) that you are inspecting.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="899cc-125">– Fullständig</span><span class="sxs-lookup"><span data-stu-id="899cc-125">-Full</span></span>

<span data-ttu-id="899cc-126">Anger att denna cmdlet returnerar hela det första sessionstillståndet för den angivna användaren vid den angivna begränsade slut punkten.</span><span class="sxs-lookup"><span data-stu-id="899cc-126">Indicates that this cmdlet returns the entire initial session state for the specified user at the specified constrained endpoint.</span></span>

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

### <span data-ttu-id="899cc-127">-Username</span><span class="sxs-lookup"><span data-stu-id="899cc-127">-Username</span></span>

<span data-ttu-id="899cc-128">Anger den användare vars funktioner du undersöker.</span><span class="sxs-lookup"><span data-stu-id="899cc-128">Specifies the user whose capabilities you are inspecting.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="899cc-129">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="899cc-129">CommonParameters</span></span>

<span data-ttu-id="899cc-130">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="899cc-130">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="899cc-131">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="899cc-131">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="899cc-132">INDATA</span><span class="sxs-lookup"><span data-stu-id="899cc-132">INPUTS</span></span>

## <span data-ttu-id="899cc-133">UTDATA</span><span class="sxs-lookup"><span data-stu-id="899cc-133">OUTPUTS</span></span>

### <span data-ttu-id="899cc-134">System. Management. Automation. AliasInfo</span><span class="sxs-lookup"><span data-stu-id="899cc-134">System.Management.Automation.AliasInfo</span></span>

### <span data-ttu-id="899cc-135">System. Management. Automation. FunctionInfo</span><span class="sxs-lookup"><span data-stu-id="899cc-135">System.Management.Automation.FunctionInfo</span></span>

### <span data-ttu-id="899cc-136">System.Management.Automation.Runspaces.InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="899cc-136">System.Management.Automation.Runspaces.InitialSessionState</span></span>

## <span data-ttu-id="899cc-137">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="899cc-137">NOTES</span></span>

## <span data-ttu-id="899cc-138">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="899cc-138">RELATED LINKS</span></span>

[<span data-ttu-id="899cc-139">New-PSRoleCapabilityFile</span><span class="sxs-lookup"><span data-stu-id="899cc-139">New-PSRoleCapabilityFile</span></span>](New-PSRoleCapabilityFile.md)

