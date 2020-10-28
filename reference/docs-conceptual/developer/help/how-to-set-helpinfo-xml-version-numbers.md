---
ms.date: 09/12/2016
ms.topic: reference
title: Konfigurera versionsnummer för HelpInfo-XML-filer
description: Konfigurera versionsnummer för HelpInfo-XML-filer
ms.openlocfilehash: 9ef1940ca05d8aa9b04770013287490b71c8065a
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92658842"
---
# <a name="how-to-set-helpinfo-xml-version-numbers"></a><span data-ttu-id="b5cb8-103">Konfigurera versionsnummer för HelpInfo-XML-filer</span><span class="sxs-lookup"><span data-stu-id="b5cb8-103">How to Set HelpInfo XML Version Numbers</span></span>

<span data-ttu-id="b5cb8-104">I det här avsnittet beskrivs hur du ställer in och ökar versions numren i en uppdaterings bar hjälp informations fil, som kallas för en "HelpInfo XML-fil".</span><span class="sxs-lookup"><span data-stu-id="b5cb8-104">This topic explains how to set and increase the version numbers in an Updatable Help Information file, commonly known as a "HelpInfo XML file."</span></span>

## <a name="how-to-set-helpinfo-xml-version-numbers"></a><span data-ttu-id="b5cb8-105">Konfigurera versionsnummer för HelpInfo-XML-filer</span><span class="sxs-lookup"><span data-stu-id="b5cb8-105">How to Set HelpInfo XML Version Numbers</span></span>

<span data-ttu-id="b5cb8-106">Versions numren i en HelpInfo XML-fil är viktiga för att det ska gå att uppdatera hjälpen.</span><span class="sxs-lookup"><span data-stu-id="b5cb8-106">The version numbers in a HelpInfo XML file are critical to the operation of Updatable Help.</span></span> <span data-ttu-id="b5cb8-107">Cmdletarna [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) och [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) laddar bara ned nya hjälpfiler när versions numret för en GRÄNSSNITTS kultur i XML-HelpInfo är större än versions numret för denna gränssnitts kultur i den lokala HelpInfo-XML-filen, eller så finns det ingen lokal HelpInfo XML-fil.</span><span class="sxs-lookup"><span data-stu-id="b5cb8-107">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets download new help files only when the version number for a UI culture in the remote HelpInfo XML file is greater than the version number for that UI culture in the local HelpInfo XML, or there is no local HelpInfo XML file.</span></span>

<span data-ttu-id="b5cb8-108">XML-filen HelpInfo använder det versions nummer på 4 delar som definieras i klassen **system. version** i Microsoft .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b5cb8-108">The HelpInfo XML file uses the 4-part version number that is defined in the **System.Version** class of the Microsoft .NET Framework.</span></span> <span data-ttu-id="b5cb8-109">Formatet är `N1.N2.N3.N4`.</span><span class="sxs-lookup"><span data-stu-id="b5cb8-109">The format is `N1.N2.N3.N4`.</span></span> <span data-ttu-id="b5cb8-110">Module-författare kan använda alla versions scheman som tillåts av klassen **system. version** .</span><span class="sxs-lookup"><span data-stu-id="b5cb8-110">Module authors can use any version numbering scheme that is permitted by the **System.Version** class.</span></span> <span data-ttu-id="b5cb8-111">Uppdaterings bara hjälp kräver bara att versions numret för en användar gränssnitts kultur ökar när en ny version av CAB-filen för den användar gränssnitts kulturen överförs till den plats som anges av **HelpContentURI** -elementet i XML-filen för HelpInfo.</span><span class="sxs-lookup"><span data-stu-id="b5cb8-111">Updatable Help requires only that the version number for a UI culture increase when a new version of the CAB file for that UI culture is uploaded to the location that is specified by the **HelpContentURI** element in the HelpInfo XML file.</span></span>

<span data-ttu-id="b5cb8-112">I följande exempel visas elementen i XML-filen HelpInfo för den tyska (de-DE) användar gränssnitts kulturen när versionen är 2.15.0.10.</span><span class="sxs-lookup"><span data-stu-id="b5cb8-112">The following example shows the elements of the HelpInfo XML file for the German (de-DE) UI culture when the version is 2.15.0.10.</span></span>

```xml
<UICulture>
  <UICultureName>de-DE</UICultureName>
  <UICultureVersion>2.15.0.10</UICultureVersion>
</UICulture>
```

<span data-ttu-id="b5cb8-113">Versions numret för en kultur i användar gränssnittet återspeglar versionen av CAB-filen för användar gränssnitts kulturen.</span><span class="sxs-lookup"><span data-stu-id="b5cb8-113">The version number for a UI culture reflects the version of the CAB file for that UI culture.</span></span> <span data-ttu-id="b5cb8-114">Versions numret gäller hela CAB-filen.</span><span class="sxs-lookup"><span data-stu-id="b5cb8-114">The version number applies to the entire CAB file.</span></span> <span data-ttu-id="b5cb8-115">Du kan inte ange olika versions nummer för olika filer i CAB-filen.</span><span class="sxs-lookup"><span data-stu-id="b5cb8-115">You cannot set different version numbers for different files in the CAB file.</span></span> <span data-ttu-id="b5cb8-116">Versions numret för varje GRÄNSSNITTs kultur utvärderas oberoende och behöver inte vara relaterat till versions numren för andra användar gränssnitts kulturer som modulen stöder.</span><span class="sxs-lookup"><span data-stu-id="b5cb8-116">The version number for each UI culture is evaluated independently and need not be related to the version numbers for other UI cultures that the module supports.</span></span>
