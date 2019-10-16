---
title: Definiera standard metoder för objekt | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53fe744a-485f-4c21-9623-1cb546372211
caps.latest.revision: 9
ms.openlocfilehash: 346a194c6b4c81aa61a6331cdb62ae380a17bb1e
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72356408"
---
# <a name="defining-default-methods-for-objects"></a><span data-ttu-id="8b6e0-102">Definiera standardmetoder för objekt</span><span class="sxs-lookup"><span data-stu-id="8b6e0-102">Defining Default Methods for Objects</span></span>

<span data-ttu-id="8b6e0-103">När du utökar .NET Framework objekt kan du lägga till kod metoder och skript metoder i objekten.</span><span class="sxs-lookup"><span data-stu-id="8b6e0-103">When you extend .NET Framework objects, you can add code methods and script methods to the objects.</span></span>
<span data-ttu-id="8b6e0-104">Den XML som används för att definiera dessa metoder beskrivs i följande avsnitt.</span><span class="sxs-lookup"><span data-stu-id="8b6e0-104">The XML that is used to define these methods is described in the following sections.</span></span>

> [!NOTE]
> <span data-ttu-id="8b6e0-105">Exemplen i följande avsnitt är från `Types.ps1xml`-typ filen i installations katalogen för Windows PowerShell (`$PSHOME`).</span><span class="sxs-lookup"><span data-stu-id="8b6e0-105">The examples in the following sections are from the `Types.ps1xml` types file in the Windows PowerShell installation directory (`$PSHOME`).</span></span> <span data-ttu-id="8b6e0-106">Mer information finns i [About types. ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml).</span><span class="sxs-lookup"><span data-stu-id="8b6e0-106">For more information, see [About Types.ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml).</span></span>

## <a name="code-methods"></a><span data-ttu-id="8b6e0-107">Kod metoder</span><span class="sxs-lookup"><span data-stu-id="8b6e0-107">Code methods</span></span>

<span data-ttu-id="8b6e0-108">En kod metod refererar till en statisk metod för ett .NET Framework-objekt.</span><span class="sxs-lookup"><span data-stu-id="8b6e0-108">A code method references a static method of a .NET Framework object.</span></span>

<span data-ttu-id="8b6e0-109">I följande exempel läggs metoden **toString** till i typen [system. xml. XmlNode](/dotnet/api/System.Xml.XmlNode) .</span><span class="sxs-lookup"><span data-stu-id="8b6e0-109">In the following example, the **ToString** method is added to the [System.Xml.XmlNode](/dotnet/api/System.Xml.XmlNode) type.</span></span> <span data-ttu-id="8b6e0-110">[PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) -elementet definierar den utökade metoden som en Code-metod.</span><span class="sxs-lookup"><span data-stu-id="8b6e0-110">The [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) element defines the extended method as a code method.</span></span> <span data-ttu-id="8b6e0-111">Elementet [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) anger namnet på den utökade metoden.</span><span class="sxs-lookup"><span data-stu-id="8b6e0-111">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) element specifies the name of the extended method.</span></span> <span data-ttu-id="8b6e0-112">Och [CodeReference](/dotnet/api/system.management.automation.pscodemethod.codereference?view=pscore-6.2.0#System_Management_Automation_PSCodeMethod_CodeReference) -elementet anger den statiska metoden.</span><span class="sxs-lookup"><span data-stu-id="8b6e0-112">And, the [CodeReference](/dotnet/api/system.management.automation.pscodemethod.codereference?view=pscore-6.2.0#System_Management_Automation_PSCodeMethod_CodeReference) element specifies the static method.</span></span> <span data-ttu-id="8b6e0-113">Du kan också lägga till elementet [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) i medlemmarna i [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) -elementet.</span><span class="sxs-lookup"><span data-stu-id="8b6e0-113">You can also add the [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) element to the members of the [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) element.</span></span>

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

## <a name="script-methods"></a><span data-ttu-id="8b6e0-114">Skript metoder</span><span class="sxs-lookup"><span data-stu-id="8b6e0-114">Script methods</span></span>

<span data-ttu-id="8b6e0-115">En skript metod definierar en metod vars värde är utdata från ett skript.</span><span class="sxs-lookup"><span data-stu-id="8b6e0-115">A script method defines a method whose value is the output of a script.</span></span> <span data-ttu-id="8b6e0-116">I följande exempel läggs **ConvertToDateTime** -metoden till i typen [system. Management. ManagementObject](/dotnet/api/System.Management.ManagementObject) .</span><span class="sxs-lookup"><span data-stu-id="8b6e0-116">In the following example, the **ConvertToDateTime** method is added to the [System.Management.ManagementObject](/dotnet/api/System.Management.ManagementObject) type.</span></span> <span data-ttu-id="8b6e0-117">[PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) -elementet definierar den utökade metoden som en skript metod.</span><span class="sxs-lookup"><span data-stu-id="8b6e0-117">The [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) element defines the extended method as a script method.</span></span> <span data-ttu-id="8b6e0-118">Elementet [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) anger namnet på den utökade metoden.</span><span class="sxs-lookup"><span data-stu-id="8b6e0-118">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) element specifies the name of the extended method.</span></span> <span data-ttu-id="8b6e0-119">Och [skript](/dotnet/api/system.management.automation.psscriptmethod.script?view=pscore-6.2.0#System_Management_Automation_PSScriptMethod_Script) elementet anger det skript som genererar metod svärdet.</span><span class="sxs-lookup"><span data-stu-id="8b6e0-119">And, the [Script](/dotnet/api/system.management.automation.psscriptmethod.script?view=pscore-6.2.0#System_Management_Automation_PSScriptMethod_Script) element specifies the script that generates the method value.</span></span> <span data-ttu-id="8b6e0-120">Du kan också lägga till elementet [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) i medlemmarna i [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) -elementet.</span><span class="sxs-lookup"><span data-stu-id="8b6e0-120">You can also add the [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) element to the members of the [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) element.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="8b6e0-121">Se även</span><span class="sxs-lookup"><span data-stu-id="8b6e0-121">See also</span></span>

[<span data-ttu-id="8b6e0-122">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="8b6e0-122">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
