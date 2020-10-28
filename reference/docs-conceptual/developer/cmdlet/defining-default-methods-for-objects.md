---
ms.date: 09/13/2016
ms.topic: reference
title: Definiera standardmetoder för objekt
description: Definiera standardmetoder för objekt
ms.openlocfilehash: b3b61b552d0f5ef4a018c6f1dd495ac0c770cddc
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92653112"
---
# <a name="defining-default-methods-for-objects"></a><span data-ttu-id="6f77b-103">Definiera standardmetoder för objekt</span><span class="sxs-lookup"><span data-stu-id="6f77b-103">Defining Default Methods for Objects</span></span>

<span data-ttu-id="6f77b-104">När du utökar .NET Framework objekt kan du lägga till kod metoder och skript metoder i objekten.</span><span class="sxs-lookup"><span data-stu-id="6f77b-104">When you extend .NET Framework objects, you can add code methods and script methods to the objects.</span></span>
<span data-ttu-id="6f77b-105">Den XML som används för att definiera dessa metoder beskrivs i följande avsnitt.</span><span class="sxs-lookup"><span data-stu-id="6f77b-105">The XML that is used to define these methods is described in the following sections.</span></span>

> [!NOTE]
> <span data-ttu-id="6f77b-106">Exemplen i följande avsnitt är från `Types.ps1xml` typ filen i installations katalogen för Windows PowerShell ( `$PSHOME` ).</span><span class="sxs-lookup"><span data-stu-id="6f77b-106">The examples in the following sections are from the `Types.ps1xml` types file in the Windows PowerShell installation directory (`$PSHOME`).</span></span> <span data-ttu-id="6f77b-107">Mer information finns i [About Types.ps1XML](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml).</span><span class="sxs-lookup"><span data-stu-id="6f77b-107">For more information, see [About Types.ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml).</span></span>

## <a name="code-methods"></a><span data-ttu-id="6f77b-108">Kod metoder</span><span class="sxs-lookup"><span data-stu-id="6f77b-108">Code methods</span></span>

<span data-ttu-id="6f77b-109">En kod metod refererar till en statisk metod för ett .NET Framework-objekt.</span><span class="sxs-lookup"><span data-stu-id="6f77b-109">A code method references a static method of a .NET Framework object.</span></span>

<span data-ttu-id="6f77b-110">I följande exempel läggs metoden **toString** till i den [System.Xml.Xmlnodtypen](/dotnet/api/System.Xml.XmlNode) .</span><span class="sxs-lookup"><span data-stu-id="6f77b-110">In the following example, the **ToString** method is added to the [System.Xml.XmlNode](/dotnet/api/System.Xml.XmlNode) type.</span></span> <span data-ttu-id="6f77b-111">[PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) -elementet definierar den utökade metoden som en Code-metod.</span><span class="sxs-lookup"><span data-stu-id="6f77b-111">The [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) element defines the extended method as a code method.</span></span> <span data-ttu-id="6f77b-112">Elementet [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) anger namnet på den utökade metoden.</span><span class="sxs-lookup"><span data-stu-id="6f77b-112">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) element specifies the name of the extended method.</span></span> <span data-ttu-id="6f77b-113">Och [CodeReference](/dotnet/api/system.management.automation.pscodemethod.codereference?view=pscore-6.2.0#System_Management_Automation_PSCodeMethod_CodeReference) -elementet anger den statiska metoden.</span><span class="sxs-lookup"><span data-stu-id="6f77b-113">And, the [CodeReference](/dotnet/api/system.management.automation.pscodemethod.codereference?view=pscore-6.2.0#System_Management_Automation_PSCodeMethod_CodeReference) element specifies the static method.</span></span> <span data-ttu-id="6f77b-114">Du kan också lägga till elementet [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) i medlemmarna i [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) -elementet.</span><span class="sxs-lookup"><span data-stu-id="6f77b-114">You can also add the [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) element to the members of the [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) element.</span></span>

```xml
<Type>
  <Name>System.Xml.XmlNode</Name>
  <Members>
    <CodeMethod>
      <Name>ToString</Name>
      <CodeReference>
        <TypeName>Microsoft.PowerShell.ToStringCodeMethods</TypeName>
        <MethodName>XmlNode</MethodName>
      </CodeReference>
    </CodeMethod>
  </Members>
</Type>
```

## <a name="script-methods"></a><span data-ttu-id="6f77b-115">Skript metoder</span><span class="sxs-lookup"><span data-stu-id="6f77b-115">Script methods</span></span>

<span data-ttu-id="6f77b-116">En skript metod definierar en metod vars värde är utdata från ett skript.</span><span class="sxs-lookup"><span data-stu-id="6f77b-116">A script method defines a method whose value is the output of a script.</span></span> <span data-ttu-id="6f77b-117">I följande exempel läggs **ConvertToDateTime** -metoden till i typen [system. Management. ManagementObject](/dotnet/api/System.Management.ManagementObject) .</span><span class="sxs-lookup"><span data-stu-id="6f77b-117">In the following example, the **ConvertToDateTime** method is added to the [System.Management.ManagementObject](/dotnet/api/System.Management.ManagementObject) type.</span></span> <span data-ttu-id="6f77b-118">[PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) -elementet definierar den utökade metoden som en skript metod.</span><span class="sxs-lookup"><span data-stu-id="6f77b-118">The [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) element defines the extended method as a script method.</span></span> <span data-ttu-id="6f77b-119">Elementet [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) anger namnet på den utökade metoden.</span><span class="sxs-lookup"><span data-stu-id="6f77b-119">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) element specifies the name of the extended method.</span></span> <span data-ttu-id="6f77b-120">Och [skript](/dotnet/api/system.management.automation.psscriptmethod.script?view=pscore-6.2.0#System_Management_Automation_PSScriptMethod_Script) elementet anger det skript som genererar metod svärdet.</span><span class="sxs-lookup"><span data-stu-id="6f77b-120">And, the [Script](/dotnet/api/system.management.automation.psscriptmethod.script?view=pscore-6.2.0#System_Management_Automation_PSScriptMethod_Script) element specifies the script that generates the method value.</span></span> <span data-ttu-id="6f77b-121">Du kan också lägga till elementet [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) i medlemmarna i [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) -elementet.</span><span class="sxs-lookup"><span data-stu-id="6f77b-121">You can also add the [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) element to the members of the [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) element.</span></span>

```xml
<Type>
  <Name>System.Management.ManagementObject</Name>
  <Members>
    <ScriptMethod>
      <Name>ConvertToDateTime</Name>
      <Script>
        [System.Management.ManagementDateTimeConverter]::ToDateTime($args[0])
      </Script>
    </ScriptMethod>
  </Members>
</Type>
```

## <a name="see-also"></a><span data-ttu-id="6f77b-122">Se även</span><span class="sxs-lookup"><span data-stu-id="6f77b-122">See also</span></span>

[<span data-ttu-id="6f77b-123">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="6f77b-123">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
