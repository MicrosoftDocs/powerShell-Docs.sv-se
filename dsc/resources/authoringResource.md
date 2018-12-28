---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: Skapa anpassade Windows PowerShell Desired State Configuration-resurser
ms.openlocfilehash: 882b6efed4564d2354183d7472b301e1e1758335
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404739"
---
# <a name="build-custom-windows-powershell-desired-state-configuration-resources"></a><span data-ttu-id="f7b3a-103">Skapa anpassade Windows PowerShell Desired State Configuration-resurser</span><span class="sxs-lookup"><span data-stu-id="f7b3a-103">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>

> <span data-ttu-id="f7b3a-104">Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="f7b3a-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="f7b3a-105">Windows PowerShell Desired State Configuration (DSC) har inbyggda resurser som du kan använda för att konfigurera din miljö.</span><span class="sxs-lookup"><span data-stu-id="f7b3a-105">Windows PowerShell Desired State Configuration (DSC) has built-in resources that you can use to configure your environment.</span></span> <span data-ttu-id="f7b3a-106">Det här avsnittet innehåller en översikt över utveckling av resurserna och länkarna till avsnitt med specifik information och exempel.</span><span class="sxs-lookup"><span data-stu-id="f7b3a-106">This topic provides an overview of developing resources and links to topics with specific information and examples.</span></span>

## <a name="dsc-resource-components"></a><span data-ttu-id="f7b3a-107">Komponenter för DSC-resurs</span><span class="sxs-lookup"><span data-stu-id="f7b3a-107">DSC resource components</span></span>

<span data-ttu-id="f7b3a-108">En DSC-resurs är en Windows PowerShell-modul.</span><span class="sxs-lookup"><span data-stu-id="f7b3a-108">A DSC resource is a Windows PowerShell module.</span></span> <span data-ttu-id="f7b3a-109">Modulen innehåller både schemat (definition av konfigurerbara egenskaper) och implementeringen (den kod som utför det faktiska arbetet som anges av en konfiguration) för resursen.</span><span class="sxs-lookup"><span data-stu-id="f7b3a-109">The module contains both the schema (the definition of the configurable properties) and the implementation (the code that does the actual work specified by a configuration) for the resource.</span></span> <span data-ttu-id="f7b3a-110">Ett schema för DSC-resurs kan definieras i en MOF-fil och implementeringen utförs av en skriptmodul.</span><span class="sxs-lookup"><span data-stu-id="f7b3a-110">A DSC resource schema can be defined in a MOF file, and the implementation is performed by a script module.</span></span> <span data-ttu-id="f7b3a-111">Från och med hjälp av PowerShell-klasser i version 5, kan schemat och implementering vara definierade i en klass.</span><span class="sxs-lookup"><span data-stu-id="f7b3a-111">Beginning with the support of PowerShell classes in version 5, the schema and implementation can both be defined in a class.</span></span> <span data-ttu-id="f7b3a-112">I följande avsnitt beskrivs i detalj hur du skapar DSC-resurser.</span><span class="sxs-lookup"><span data-stu-id="f7b3a-112">The following topics describe in more detail how to create DSC resources.</span></span>

* [<span data-ttu-id="f7b3a-113">Skriva en anpassad DSC-resurs med MOF</span><span class="sxs-lookup"><span data-stu-id="f7b3a-113">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md)
* [<span data-ttu-id="f7b3a-114">Implementera en DSC-resurs iC#</span><span class="sxs-lookup"><span data-stu-id="f7b3a-114">Implementing a DSC resource in C#</span></span>](authoringResourceMofCS.md)
* [<span data-ttu-id="f7b3a-115">Skriva en anpassad DSC-resurs med PowerShell-klasser</span><span class="sxs-lookup"><span data-stu-id="f7b3a-115">Writing a custom DSC resource with PowerShell classes</span></span>](authoringResourceClass.md)
* [<span data-ttu-id="f7b3a-116">Sammansatta resurser: Använda en DSC-konfiguration som en resurs</span><span class="sxs-lookup"><span data-stu-id="f7b3a-116">Composite resources: Using a DSC configuration as a resource</span></span>](authoringResourceComposite.md)
* [<span data-ttu-id="f7b3a-117">Med hjälp av verktyget Resource Designer</span><span class="sxs-lookup"><span data-stu-id="f7b3a-117">Using the Resource Designer tool</span></span>](../authoringResourceMofDesigner.md)
