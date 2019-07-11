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
ms.openlocfilehash: af554cde5e888f2a008028010332caa473151622
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67733973"
---
# <a name="defining-default-methods-for-objects"></a><span data-ttu-id="5520d-102">Definiera standardmetoder för objekt</span><span class="sxs-lookup"><span data-stu-id="5520d-102">Defining Default Methods for Objects</span></span>

<span data-ttu-id="5520d-103">När du utökar .NET Framework-objekt kan du lägga till kod metoder och skript metoder till objekt.</span><span class="sxs-lookup"><span data-stu-id="5520d-103">When you extend .NET Framework objects, you can add code methods and script methods to the objects.</span></span> <span data-ttu-id="5520d-104">XML-filen som används för att definiera dessa metoder beskrivs i följande avsnitt.</span><span class="sxs-lookup"><span data-stu-id="5520d-104">The XML that is used to define these methods is described in the following sections.</span></span>

> [!NOTE]
> <span data-ttu-id="5520d-105">Exemplen i följande avsnitt kommer från filen Types.ps1xml typer i installationskatalogen för Windows PowerShell (`$pshome`).</span><span class="sxs-lookup"><span data-stu-id="5520d-105">The examples in the following sections are from the Types.ps1xml types file in the Windows PowerShell installation directory (`$pshome`).</span></span>

## <a name="code-methods"></a><span data-ttu-id="5520d-106">Kod metoder</span><span class="sxs-lookup"><span data-stu-id="5520d-106">Code Methods</span></span>

<span data-ttu-id="5520d-107">En metod som koden refererar till en statisk metod för ett .NET Framework-objekt.</span><span class="sxs-lookup"><span data-stu-id="5520d-107">A code method references a static method of a .NET Framework object.</span></span>

<span data-ttu-id="5520d-108">I följande exempel visas den **ConvertLargeIntegerToInt64** metod har lagts till i den [System.Xml.Xmlnode? Displayproperty = Fullname](/dotnet/api/System.Xml.XmlNode) typen.</span><span class="sxs-lookup"><span data-stu-id="5520d-108">In the following example, the **ConvertLargeIntegerToInt64** method is added to the [System.Xml.Xmlnode?Displayproperty=Fullname](/dotnet/api/System.Xml.XmlNode) type.</span></span> <span data-ttu-id="5520d-109">Den [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) elementet definierar metoden utökade som en metod för kod.</span><span class="sxs-lookup"><span data-stu-id="5520d-109">The [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) element defines the extended method as a code method.</span></span> <span data-ttu-id="5520d-110">Den [namn](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) elementet anger namnet på den utökade metoden.</span><span class="sxs-lookup"><span data-stu-id="5520d-110">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) element specifies the name of the extended method.</span></span> <span data-ttu-id="5520d-111">Och [CodeReference](/dotnet/api/system.management.automation.pscodemethod.codereference?view=pscore-6.2.0#System_Management_Automation_PSCodeMethod_CodeReference) elementet anger metoden som statisk.</span><span class="sxs-lookup"><span data-stu-id="5520d-111">And, the [CodeReference](/dotnet/api/system.management.automation.pscodemethod.codereference?view=pscore-6.2.0#System_Management_Automation_PSCodeMethod_CodeReference) element specifies the static method.</span></span> <span data-ttu-id="5520d-112">(Du kan också lägga till den [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) element till medlemmarna i den [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) element.)</span><span class="sxs-lookup"><span data-stu-id="5520d-112">(You can also add the [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) element to the members of the [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) element.)</span></span>

```xml
<Type>
  <Name>System.Xml.XmlNode</Name>
  <Members>
    <CodeMethod>
      <Name>ToString</Name>
      <CodeReference>
        <TypeName>Microsoft.PowerShell.ToStringCodemethods</TypeName>
        <MethodName>XmlNode</MethodName>
      </CodeReference>
    </CodeMethod>
  </Members>
</Type>
```

## <a name="script-methods"></a><span data-ttu-id="5520d-113">Skript-metoder</span><span class="sxs-lookup"><span data-stu-id="5520d-113">Script Methods</span></span>

<span data-ttu-id="5520d-114">En metod för skriptet definierar en metod som vars värde är utdata från ett skript.</span><span class="sxs-lookup"><span data-stu-id="5520d-114">A script method defines a method whose value is the output of a script.</span></span> <span data-ttu-id="5520d-115">I följande exempel visas den **ConvertToDateTime** metod har lagts till i den [System.Management.Managementobject? Displayproperty = Fullname](/dotnet/api/System.Management.ManagementObject) typen.</span><span class="sxs-lookup"><span data-stu-id="5520d-115">In the following example, the **ConvertToDateTime** method is added to the [System.Management.Managementobject?Displayproperty=Fullname](/dotnet/api/System.Management.ManagementObject) type.</span></span> <span data-ttu-id="5520d-116">Den [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) elementet definierar metoden utökade som en metod för skriptet.</span><span class="sxs-lookup"><span data-stu-id="5520d-116">The [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) element defines the extended method as a script method.</span></span> <span data-ttu-id="5520d-117">Den [namn](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) elementet anger namnet på den utökade metoden.</span><span class="sxs-lookup"><span data-stu-id="5520d-117">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) element specifies the name of the extended method.</span></span> <span data-ttu-id="5520d-118">Och [skriptet](/dotnet/api/system.management.automation.psscriptmethod.script?view=pscore-6.2.0#System_Management_Automation_PSScriptMethod_Script) elementet anger det skript som genererar metoden värdet.</span><span class="sxs-lookup"><span data-stu-id="5520d-118">And, the [Script](/dotnet/api/system.management.automation.psscriptmethod.script?view=pscore-6.2.0#System_Management_Automation_PSScriptMethod_Script) element specifies the script that generates the method value.</span></span> <span data-ttu-id="5520d-119">(Du kan också lägga till den [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) element till medlemmarna i den [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) element.)</span><span class="sxs-lookup"><span data-stu-id="5520d-119">(You can also add the [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) element to the members of the [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) element.)</span></span>

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

## <a name="see-also"></a><span data-ttu-id="5520d-120">Se även</span><span class="sxs-lookup"><span data-stu-id="5520d-120">See Also</span></span>

[<span data-ttu-id="5520d-121">Skriva en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5520d-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
