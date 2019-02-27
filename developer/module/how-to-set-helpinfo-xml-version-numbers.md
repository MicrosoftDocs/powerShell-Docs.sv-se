---
title: Hur du ställer in HelpInfo XML-versionsnumren | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93a00463-af58-41c8-b088-450909fa1d05
caps.latest.revision: 6
ms.openlocfilehash: 4929a5b1c9f73bb12b6df975e03fc529db3565ef
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851935"
---
# <a name="how-to-set-helpinfo-xml-version-numbers"></a><span data-ttu-id="9e9d3-102">Konfigurera versionsnummer för HelpInfo-XML-filer</span><span class="sxs-lookup"><span data-stu-id="9e9d3-102">How to Set HelpInfo XML Version Numbers</span></span>

<span data-ttu-id="9e9d3-103">Det här avsnittet beskriver hur du ställer och öka versionsnumren i en uppdateringsbar hjälp Information-fil som kallas en ”HelpInfo XML-fil”.</span><span class="sxs-lookup"><span data-stu-id="9e9d3-103">This topic explains how to set and increase the version numbers in an Updatable Help Information file, commonly known as a "HelpInfo XML file."</span></span>

## <a name="how-to-set-helpinfo-xml-version-numbers"></a><span data-ttu-id="9e9d3-104">Konfigurera versionsnummer för HelpInfo-XML-filer</span><span class="sxs-lookup"><span data-stu-id="9e9d3-104">How to Set HelpInfo XML Version Numbers</span></span>

<span data-ttu-id="9e9d3-105">Versionsnummer i en HelpInfo XML-fil är viktiga för driften av uppdateringsbar hjälp.</span><span class="sxs-lookup"><span data-stu-id="9e9d3-105">The version numbers in a HelpInfo XML file are critical to the operation of Updatable Help.</span></span> <span data-ttu-id="9e9d3-106">Den [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) och [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) hämtar nya hjälpfiler endast när det lägre versionsnumret för en UI-kultur i den fjärranslutna HelpInfo XML-filen är större än versionsnumret för den kulturen för Användargränssnittet i den lokala HelpInfo XML, eller om det finns ingen lokal HelpInfo XML-fil.</span><span class="sxs-lookup"><span data-stu-id="9e9d3-106">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlets download new help files only when the version number for a UI culture in the remote HelpInfo XML file is greater than the version number for that UI culture in the local HelpInfo XML, or there is no local HelpInfo XML file.</span></span>
<span data-ttu-id="9e9d3-107">Versionsnummer i en HelpInfo XML-fil är viktiga för driften av uppdateringsbar hjälp.</span><span class="sxs-lookup"><span data-stu-id="9e9d3-107">The version numbers in a HelpInfo XML file are critical to the operation of Updatable Help.</span></span> <span data-ttu-id="9e9d3-108">Den [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) och [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) hämtar nya hjälpfiler endast när det lägre versionsnumret för en UI-kultur i den fjärranslutna HelpInfo XML-filen är större än versionsnumret för den kulturen för Användargränssnittet i den lokala HelpInfo XML, eller om det finns ingen lokal HelpInfo XML-fil.</span><span class="sxs-lookup"><span data-stu-id="9e9d3-108">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlets download new help files only when the version number for a UI culture in the remote HelpInfo XML file is greater than the version number for that UI culture in the local HelpInfo XML, or there is no local HelpInfo XML file.</span></span>

<span data-ttu-id="9e9d3-109">HelpInfo XML-filen använder 4 delar versionsnumret som definieras i den **System.Version** klass av Microsoft .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9e9d3-109">The HelpInfo XML file uses the 4-part version number that is defined in the **System.Version** class of the Microsoft .NET Framework.</span></span> <span data-ttu-id="9e9d3-110">Formatet är `N1.N2.N3.N4`.</span><span class="sxs-lookup"><span data-stu-id="9e9d3-110">The format is `N1.N2.N3.N4`.</span></span> <span data-ttu-id="9e9d3-111">Modulskapare kan använda valfri versionsnumrering schema är tillåten enligt den **System.Version** klass.</span><span class="sxs-lookup"><span data-stu-id="9e9d3-111">Module authors can use any version numbering scheme that is permitted by the **System.Version** class.</span></span> <span data-ttu-id="9e9d3-112">Uppdateringsbar hjälp kräver bara att versionsnumret för en UI kultur ökning när en ny version av CAB-filen för den kulturen överförs till den plats som anges av den **HelpContentURI** element i HelpInfo XML-filen.</span><span class="sxs-lookup"><span data-stu-id="9e9d3-112">Updatable Help requires only that the version number for a UI culture increase when a new version of the CAB file for that UI culture is uploaded to the location that is specified by the **HelpContentURI** element in the HelpInfo XML file.</span></span>

<span data-ttu-id="9e9d3-113">I följande exempel visar elementen i HelpInfo XML-filen för tyska (de-DE) UI kultur när version är 2.15.0.10.</span><span class="sxs-lookup"><span data-stu-id="9e9d3-113">The following example shows the elements of the HelpInfo XML file for the German (de-DE) UI culture when the version is 2.15.0.10.</span></span>

```xml

<UICulture>
  <UICultureName>de-DE</UICultureName>
  <UICultureVersion>2.15.0.10</UICultureVersion>
</UICulture>
```

<span data-ttu-id="9e9d3-114">Versionen av CAB-filen för den kulturen för Användargränssnittet visar versionsnumret för en UI-kultur.</span><span class="sxs-lookup"><span data-stu-id="9e9d3-114">The version number for a UI culture reflects the version of the CAB file for that UI culture.</span></span> <span data-ttu-id="9e9d3-115">Versionsnumret som gäller för hela CAB-filen.</span><span class="sxs-lookup"><span data-stu-id="9e9d3-115">The version number applies to the entire CAB file.</span></span> <span data-ttu-id="9e9d3-116">Du kan inte ange olika versionsnummer används för olika filer i CAB-filen.</span><span class="sxs-lookup"><span data-stu-id="9e9d3-116">You cannot set different version numbers for different files in the CAB file.</span></span> <span data-ttu-id="9e9d3-117">Versionsnumret för varje UI-kultur utvärderas oberoende av varandra och behöver inte vara relaterade till versionsnummer för andra UI-kulturer som har stöd för modulen.</span><span class="sxs-lookup"><span data-stu-id="9e9d3-117">The version number for each UI culture is evaluated independently and need not be related to the version numbers for other UI cultures that the module supports.</span></span>