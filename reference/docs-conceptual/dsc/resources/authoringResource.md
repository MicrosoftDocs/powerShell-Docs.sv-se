---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: Bygg anpassade resurser för Desired Configuration för Windows PowerShell
ms.openlocfilehash: f0f35e8d0083d302f142f2215c9f28fee411eb07
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71941175"
---
# <a name="build-custom-windows-powershell-desired-state-configuration-resources"></a><span data-ttu-id="ad22d-103">Bygg anpassade resurser för Desired Configuration för Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ad22d-103">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>

> <span data-ttu-id="ad22d-104">Gäller för: Windows PowerShell 4,0, Windows PowerShell 5,0</span><span class="sxs-lookup"><span data-stu-id="ad22d-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="ad22d-105">Windows PowerShell Desired State Configuration (DSC) har inbyggda resurser som du kan använda för att konfigurera din miljö.</span><span class="sxs-lookup"><span data-stu-id="ad22d-105">Windows PowerShell Desired State Configuration (DSC) has built-in resources that you can use to configure your environment.</span></span> <span data-ttu-id="ad22d-106">Det här avsnittet innehåller en översikt över hur du utvecklar resurser och länkar till ämnen med detaljerad information och exempel.</span><span class="sxs-lookup"><span data-stu-id="ad22d-106">This topic provides an overview of developing resources and links to topics with specific information and examples.</span></span>

## <a name="dsc-resource-components"></a><span data-ttu-id="ad22d-107">DSC-resurs komponenter</span><span class="sxs-lookup"><span data-stu-id="ad22d-107">DSC resource components</span></span>

<span data-ttu-id="ad22d-108">En DSC-resurs är en Windows PowerShell-modul.</span><span class="sxs-lookup"><span data-stu-id="ad22d-108">A DSC resource is a Windows PowerShell module.</span></span> <span data-ttu-id="ad22d-109">Modulen innehåller både schemat (definitionen av de konfigurerbara egenskaperna) och implementeringen (koden som gör det faktiska arbetet som anges i en konfiguration) för resursen.</span><span class="sxs-lookup"><span data-stu-id="ad22d-109">The module contains both the schema (the definition of the configurable properties) and the implementation (the code that does the actual work specified by a configuration) for the resource.</span></span> <span data-ttu-id="ad22d-110">Ett DSC-resurs schema kan definieras i en MOF-fil och implementeringen utförs av en-skript-modul.</span><span class="sxs-lookup"><span data-stu-id="ad22d-110">A DSC resource schema can be defined in a MOF file, and the implementation is performed by a script module.</span></span> <span data-ttu-id="ad22d-111">Från och med stöd för PowerShell-klasser i version 5 kan schemat och implementeringen båda definieras i en-klass.</span><span class="sxs-lookup"><span data-stu-id="ad22d-111">Beginning with the support of PowerShell classes in version 5, the schema and implementation can both be defined in a class.</span></span> <span data-ttu-id="ad22d-112">I följande avsnitt beskrivs mer information om hur du skapar DSC-resurser.</span><span class="sxs-lookup"><span data-stu-id="ad22d-112">The following topics describe in more detail how to create DSC resources.</span></span>

* [<span data-ttu-id="ad22d-113">Skriva en anpassad DSC-resurs med MOF</span><span class="sxs-lookup"><span data-stu-id="ad22d-113">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md)
* [<span data-ttu-id="ad22d-114">Implementera en DSC-resurs iC#</span><span class="sxs-lookup"><span data-stu-id="ad22d-114">Implementing a DSC resource in C#</span></span>](authoringResourceMofCS.md)
* [<span data-ttu-id="ad22d-115">Skriva en anpassad DSC-resurs med PowerShell-klasser</span><span class="sxs-lookup"><span data-stu-id="ad22d-115">Writing a custom DSC resource with PowerShell classes</span></span>](authoringResourceClass.md)
* [<span data-ttu-id="ad22d-116">Sammansatta resurser: använda en DSC-konfiguration som en resurs</span><span class="sxs-lookup"><span data-stu-id="ad22d-116">Composite resources: Using a DSC configuration as a resource</span></span>](authoringResourceComposite.md)
* [<span data-ttu-id="ad22d-117">Använda Resource designer-verktyget</span><span class="sxs-lookup"><span data-stu-id="ad22d-117">Using the Resource Designer tool</span></span>](authoringResourceMofDesigner.md)
