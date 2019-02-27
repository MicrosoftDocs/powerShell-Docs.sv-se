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
ms.openlocfilehash: fa0f0371856d8723af7ec17a4306de209a481a18
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850598"
---
# <a name="defining-default-methods-for-objects"></a><span data-ttu-id="4d65a-102">Definiera standardmetoder för objekt</span><span class="sxs-lookup"><span data-stu-id="4d65a-102">Defining Default Methods for Objects</span></span>

<span data-ttu-id="4d65a-103">När du utökar .NET Framework-objekt kan du lägga till kod metoder och skript metoder till objekt.</span><span class="sxs-lookup"><span data-stu-id="4d65a-103">When you extend .NET Framework objects, you can add code methods and script methods to the objects.</span></span> <span data-ttu-id="4d65a-104">XML-filen som används för att definiera dessa metoder beskrivs i följande avsnitt.</span><span class="sxs-lookup"><span data-stu-id="4d65a-104">The XML that is used to define these methods is described in the following sections.</span></span>

> [!NOTE]
> <span data-ttu-id="4d65a-105">Exemplen i följande avsnitt kommer från filen Types.ps1xml typer i installationskatalogen för Windows PowerShell (`$pshome`).</span><span class="sxs-lookup"><span data-stu-id="4d65a-105">The examples in the following sections are from the Types.ps1xml types file in the Windows PowerShell installation directory (`$pshome`).</span></span>

## <a name="code-methods"></a><span data-ttu-id="4d65a-106">Kod metoder</span><span class="sxs-lookup"><span data-stu-id="4d65a-106">Code Methods</span></span>

<span data-ttu-id="4d65a-107">En metod som koden refererar till en statisk metod för ett .NET Framework-objekt.</span><span class="sxs-lookup"><span data-stu-id="4d65a-107">A code method references a static method of a .NET Framework object.</span></span>

<span data-ttu-id="4d65a-108">I följande exempel visas den **ConvertLargeIntegerToInt64** metod har lagts till i den [System.Xml.Xmlnode? Displayproperty = Fullname](/dotnet/api/System.Xml.XmlNode) typen.</span><span class="sxs-lookup"><span data-stu-id="4d65a-108">In the following example, the **ConvertLargeIntegerToInt64** method is added to the [System.Xml.Xmlnode?Displayproperty=Fullname](/dotnet/api/System.Xml.XmlNode) type.</span></span> <span data-ttu-id="4d65a-109">Den [CodeMethod](http://msdn.microsoft.com/en-us/1ea9b031-bbcf-4e35-b497-bf30fa0b1b05) elementet definierar metoden utökade som en metod för kod.</span><span class="sxs-lookup"><span data-stu-id="4d65a-109">The [CodeMethod](http://msdn.microsoft.com/en-us/1ea9b031-bbcf-4e35-b497-bf30fa0b1b05) element defines the extended method as a code method.</span></span> <span data-ttu-id="4d65a-110">Den [namn](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) elementet anger namnet på den utökade metoden.</span><span class="sxs-lookup"><span data-stu-id="4d65a-110">The [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the name of the extended method.</span></span> <span data-ttu-id="4d65a-111">Och [CodeReference](http://msdn.microsoft.com/en-us/70017b85-18d2-4f55-8357-92f309d5618b) elementet anger metoden som statisk.</span><span class="sxs-lookup"><span data-stu-id="4d65a-111">And, the [CodeReference](http://msdn.microsoft.com/en-us/70017b85-18d2-4f55-8357-92f309d5618b) element specifies the static method.</span></span> <span data-ttu-id="4d65a-112">(Du kan också lägga till den [CodeMethod](http://msdn.microsoft.com/en-us/1ea9b031-bbcf-4e35-b497-bf30fa0b1b05) element till medlemmarna i den [MemberSet](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span><span class="sxs-lookup"><span data-stu-id="4d65a-112">(You can also add the [CodeMethod](http://msdn.microsoft.com/en-us/1ea9b031-bbcf-4e35-b497-bf30fa0b1b05) element to the members of the [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span></span>

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

## <a name="script-methods"></a><span data-ttu-id="4d65a-113">Skript-metoder</span><span class="sxs-lookup"><span data-stu-id="4d65a-113">Script Methods</span></span>

<span data-ttu-id="4d65a-114">En metod för skriptet definierar en metod som vars värde är utdata från ett skript.</span><span class="sxs-lookup"><span data-stu-id="4d65a-114">A script method defines a method whose value is the output of a script.</span></span> <span data-ttu-id="4d65a-115">I följande exempel visas den **ConvertToDateTime** metod har lagts till i den [System.Management.Managementobject? Displayproperty = Fullname](/dotnet/api/System.Management.ManagementObject) typen.</span><span class="sxs-lookup"><span data-stu-id="4d65a-115">In the following example, the **ConvertToDateTime** method is added to the [System.Management.Managementobject?Displayproperty=Fullname](/dotnet/api/System.Management.ManagementObject) type.</span></span> <span data-ttu-id="4d65a-116">Den [ScriptMethod](http://msdn.microsoft.com/en-us/59f8160f-bc95-42f0-92e2-b16a616bc65c) elementet definierar metoden utökade som en metod för skriptet.</span><span class="sxs-lookup"><span data-stu-id="4d65a-116">The [ScriptMethod](http://msdn.microsoft.com/en-us/59f8160f-bc95-42f0-92e2-b16a616bc65c) element defines the extended method as a script method.</span></span> <span data-ttu-id="4d65a-117">Den [namn](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) elementet anger namnet på den utökade metoden.</span><span class="sxs-lookup"><span data-stu-id="4d65a-117">The [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the name of the extended method.</span></span> <span data-ttu-id="4d65a-118">Och [skriptet](http://msdn.microsoft.com/en-us/1937ad1b-bb2b-4512-9864-01fc0767d46f) elementet anger det skript som genererar metoden värdet.</span><span class="sxs-lookup"><span data-stu-id="4d65a-118">And, the [Script](http://msdn.microsoft.com/en-us/1937ad1b-bb2b-4512-9864-01fc0767d46f) element specifies the script that generates the method value.</span></span> <span data-ttu-id="4d65a-119">(Du kan också lägga till den [ScriptMethod](http://msdn.microsoft.com/en-us/59f8160f-bc95-42f0-92e2-b16a616bc65c) element till medlemmarna i den [MemberSet](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span><span class="sxs-lookup"><span data-stu-id="4d65a-119">(You can also add the [ScriptMethod](http://msdn.microsoft.com/en-us/59f8160f-bc95-42f0-92e2-b16a616bc65c) element to the members of the [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span></span>

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

## <a name="see-also"></a><span data-ttu-id="4d65a-120">Se även</span><span class="sxs-lookup"><span data-stu-id="4d65a-120">See Also</span></span>

[<span data-ttu-id="4d65a-121">Skriva en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="4d65a-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)