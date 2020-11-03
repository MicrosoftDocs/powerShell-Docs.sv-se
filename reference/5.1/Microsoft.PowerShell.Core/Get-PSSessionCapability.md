---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-pssessioncapability?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSSessionCapability
ms.openlocfilehash: d76baaef31c27184bc355b6f0fc79ca67b986157
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263601"
---
# <span data-ttu-id="b304a-103">Get-PSSessionCapability</span><span class="sxs-lookup"><span data-stu-id="b304a-103">Get-PSSessionCapability</span></span>

## <span data-ttu-id="b304a-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="b304a-104">SYNOPSIS</span></span>
<span data-ttu-id="b304a-105">Hämtar funktionerna för en speciell användare i en begränsad sessions konfiguration.</span><span class="sxs-lookup"><span data-stu-id="b304a-105">Gets the capabilities of a specific user on a constrained session configuration.</span></span>

## <span data-ttu-id="b304a-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b304a-106">SYNTAX</span></span>

```
Get-PSSessionCapability [-ConfigurationName] <String> [-Username] <String> [-Full] [<CommonParameters>]
```

## <span data-ttu-id="b304a-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="b304a-107">DESCRIPTION</span></span>
<span data-ttu-id="b304a-108">Cmdlet: en **Get-PSSessionCapability** hämtar funktionerna för en speciell användare i en begränsad sessions konfiguration.</span><span class="sxs-lookup"><span data-stu-id="b304a-108">The **Get-PSSessionCapability** cmdlet gets the capabilities of a specific user on a constrained session configuration.</span></span>
<span data-ttu-id="b304a-109">Använd denna cmdlet för att granska anpassade sessionsinställningar för användare.</span><span class="sxs-lookup"><span data-stu-id="b304a-109">Use this cmdlet to audit customized session configurations for users.</span></span>

<span data-ttu-id="b304a-110">Från och med Windows PowerShell 5,0 kan du använda egenskapen **RoleDefinitions** i en session konfigurations fil (. PSSC).</span><span class="sxs-lookup"><span data-stu-id="b304a-110">Starting in Windows PowerShell 5.0, you can use the **RoleDefinitions** property in a session configuration (.pssc) file.</span></span>
<span data-ttu-id="b304a-111">Med den här egenskapen kan du ge användarna olika funktioner på en begränsad slut punkt baserat på grupp medlemskap.</span><span class="sxs-lookup"><span data-stu-id="b304a-111">Using this property lets you grant users different capabilities on a single constrained endpoint based on group membership.</span></span>
<span data-ttu-id="b304a-112">Cmdleten **Get-PSSessionCapability** minskar komplexiteten när du granskar de här slut punkterna genom att låta dig bestämma de exakta funktioner som beviljas en användare.</span><span class="sxs-lookup"><span data-stu-id="b304a-112">The **Get-PSSessionCapability** cmdlet reduces complexity when auditing these endpoints by letting you determine the exact capabilities granted to a user.</span></span>

<span data-ttu-id="b304a-113">Som standard returnerar cmdleten **Get-PSSessionCapability** en lista med kommandon som den angivna användaren kan köra i den angivna slut punkten.</span><span class="sxs-lookup"><span data-stu-id="b304a-113">By default, the **Get-PSSessionCapability** cmdlet returns a list of commands the specified user can run in the specified endpoint.</span></span>
<span data-ttu-id="b304a-114">Detta motsvarar användaren som kör **Get-Command** i den angivna slut punkten.</span><span class="sxs-lookup"><span data-stu-id="b304a-114">This is equivalent to the user running **Get-Command** in the specified endpoint.</span></span>
<span data-ttu-id="b304a-115">Vid körning med *fullständig* parameter returnerar denna cmdlet ett **InitialSessionState** -objekt.</span><span class="sxs-lookup"><span data-stu-id="b304a-115">When run with the *Full* parameter, this cmdlet returns an **InitialSessionState** object.</span></span>
<span data-ttu-id="b304a-116">Det här objektet innehåller information om Windows PowerShell-körnings utrymme som den angivna användaren skulle interagera med för den angivna slut punkten.</span><span class="sxs-lookup"><span data-stu-id="b304a-116">This object contains details about the Windows PowerShell runspace the specified user would interact with for the specified endpoint.</span></span>
<span data-ttu-id="b304a-117">Den innehåller information som språk läge, körnings princip och miljövariabler.</span><span class="sxs-lookup"><span data-stu-id="b304a-117">It includes information such as Language Mode, Execution Policy, and Environmental Variables.</span></span>

## <span data-ttu-id="b304a-118">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="b304a-118">EXAMPLES</span></span>

### <span data-ttu-id="b304a-119">Exempel 1: Hämta kommandon som är tillgängliga för en användare</span><span class="sxs-lookup"><span data-stu-id="b304a-119">Example 1: Get commands available for a user</span></span>

```
PS C:\> Get-PSSessionCapability -ConfigurationName Endpoint1 -Username 'CONTOSO\User'
```

<span data-ttu-id="b304a-120">Det här exemplet returnerar de kommandon som är tillgängliga för användaren CONTOSO\User vid anslutning till Endpoint1-begränsade slut punkter på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="b304a-120">This example returns the commands available to the user CONTOSO\User when connecting to the Endpoint1 constrained endpoint on the local computer.</span></span>

### <span data-ttu-id="b304a-121">Exempel 2: Hämta information om en körnings utrymme för en användare</span><span class="sxs-lookup"><span data-stu-id="b304a-121">Example 2: Get details about a runspace for a user</span></span>

```
PS C:\> Get-PSSessionCapability -ConfigurationName Endpoint1 -Username 'CONTOSO\User' -Full
```

<span data-ttu-id="b304a-122">Det här exemplet returnerar information om körnings utrymme som användaren CONTOSO\User skulle interagera med vid anslutning till Endpoint1-begränsad slut punkt.</span><span class="sxs-lookup"><span data-stu-id="b304a-122">This example returns details about the runspace the user CONTOSO\User would interact with when connecting to the Endpoint1 constrained endpoint.</span></span>

## <span data-ttu-id="b304a-123">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="b304a-123">PARAMETERS</span></span>

### <span data-ttu-id="b304a-124">– ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="b304a-124">-ConfigurationName</span></span>
<span data-ttu-id="b304a-125">Anger den begränsade sessionen som du inspekterar (slut punkt).</span><span class="sxs-lookup"><span data-stu-id="b304a-125">Specifies the constrained session configuration (endpoint) that you are inspecting.</span></span>

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

### <span data-ttu-id="b304a-126">– Fullständig</span><span class="sxs-lookup"><span data-stu-id="b304a-126">-Full</span></span>
<span data-ttu-id="b304a-127">Anger att denna cmdlet returnerar hela det första sessionstillståndet för den angivna användaren vid den angivna begränsade slut punkten.</span><span class="sxs-lookup"><span data-stu-id="b304a-127">Indicates that this cmdlet returns the entire initial session state for the specified user at the specified constrained endpoint.</span></span>

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

### <span data-ttu-id="b304a-128">-Username</span><span class="sxs-lookup"><span data-stu-id="b304a-128">-Username</span></span>
<span data-ttu-id="b304a-129">Anger den användare vars funktioner du undersöker.</span><span class="sxs-lookup"><span data-stu-id="b304a-129">Specifies the user whose capabilities you are inspecting.</span></span>

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

### <span data-ttu-id="b304a-130">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b304a-130">CommonParameters</span></span>
<span data-ttu-id="b304a-131">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b304a-131">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b304a-132">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="b304a-132">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b304a-133">INDATA</span><span class="sxs-lookup"><span data-stu-id="b304a-133">INPUTS</span></span>

## <span data-ttu-id="b304a-134">UTDATA</span><span class="sxs-lookup"><span data-stu-id="b304a-134">OUTPUTS</span></span>

### <span data-ttu-id="b304a-135">System. Management. Automation. AliasInfo</span><span class="sxs-lookup"><span data-stu-id="b304a-135">System.Management.Automation.AliasInfo</span></span>

### <span data-ttu-id="b304a-136">System. Management. Automation. FunctionInfo</span><span class="sxs-lookup"><span data-stu-id="b304a-136">System.Management.Automation.FunctionInfo</span></span>

### <span data-ttu-id="b304a-137">System.Management.Automation.Runspaces.InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="b304a-137">System.Management.Automation.Runspaces.InitialSessionState</span></span>

## <span data-ttu-id="b304a-138">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="b304a-138">NOTES</span></span>

## <span data-ttu-id="b304a-139">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="b304a-139">RELATED LINKS</span></span>

[<span data-ttu-id="b304a-140">New-PSRoleCapabilityFile</span><span class="sxs-lookup"><span data-stu-id="b304a-140">New-PSRoleCapabilityFile</span></span>](New-PSRoleCapabilityFile.md)