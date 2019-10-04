---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: Bygg anpassade resurser för Desired Configuration för Windows PowerShell
ms.openlocfilehash: f0f35e8d0083d302f142f2215c9f28fee411eb07
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71941175"
---
# <a name="build-custom-windows-powershell-desired-state-configuration-resources"></a><span data-ttu-id="61841-103">Bygg anpassade resurser för Desired Configuration för Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="61841-103">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>

> <span data-ttu-id="61841-104">Gäller för: Windows PowerShell 4,0, Windows PowerShell 5,0</span><span class="sxs-lookup"><span data-stu-id="61841-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="61841-105">Windows PowerShell Desired State Configuration (DSC) har inbyggda resurser som du kan använda för att konfigurera din miljö.</span><span class="sxs-lookup"><span data-stu-id="61841-105">Windows PowerShell Desired State Configuration (DSC) has built-in resources that you can use to configure your environment.</span></span> <span data-ttu-id="61841-106">Det här avsnittet innehåller en översikt över hur du utvecklar resurser och länkar till ämnen med detaljerad information och exempel.</span><span class="sxs-lookup"><span data-stu-id="61841-106">This topic provides an overview of developing resources and links to topics with specific information and examples.</span></span>

## <a name="dsc-resource-components"></a><span data-ttu-id="61841-107">DSC-resurs komponenter</span><span class="sxs-lookup"><span data-stu-id="61841-107">DSC resource components</span></span>

<span data-ttu-id="61841-108">En DSC-resurs är en Windows PowerShell-modul.</span><span class="sxs-lookup"><span data-stu-id="61841-108">A DSC resource is a Windows PowerShell module.</span></span> <span data-ttu-id="61841-109">Modulen innehåller både schemat (definitionen av de konfigurerbara egenskaperna) och implementeringen (koden som gör det faktiska arbetet som anges i en konfiguration) för resursen.</span><span class="sxs-lookup"><span data-stu-id="61841-109">The module contains both the schema (the definition of the configurable properties) and the implementation (the code that does the actual work specified by a configuration) for the resource.</span></span> <span data-ttu-id="61841-110">Ett DSC-resurs schema kan definieras i en MOF-fil och implementeringen utförs av en-skript-modul.</span><span class="sxs-lookup"><span data-stu-id="61841-110">A DSC resource schema can be defined in a MOF file, and the implementation is performed by a script module.</span></span> <span data-ttu-id="61841-111">Från och med stöd för PowerShell-klasser i version 5 kan schemat och implementeringen båda definieras i en-klass.</span><span class="sxs-lookup"><span data-stu-id="61841-111">Beginning with the support of PowerShell classes in version 5, the schema and implementation can both be defined in a class.</span></span> <span data-ttu-id="61841-112">I följande avsnitt beskrivs mer information om hur du skapar DSC-resurser.</span><span class="sxs-lookup"><span data-stu-id="61841-112">The following topics describe in more detail how to create DSC resources.</span></span>

* [<span data-ttu-id="61841-113">Skriva en anpassad DSC-resurs med MOF</span><span class="sxs-lookup"><span data-stu-id="61841-113">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md)
* [<span data-ttu-id="61841-114">Implementera en DSC-resurs iC#</span><span class="sxs-lookup"><span data-stu-id="61841-114">Implementing a DSC resource in C#</span></span>](authoringResourceMofCS.md)
* [<span data-ttu-id="61841-115">Skriva en anpassad DSC-resurs med PowerShell-klasser</span><span class="sxs-lookup"><span data-stu-id="61841-115">Writing a custom DSC resource with PowerShell classes</span></span>](authoringResourceClass.md)
* <span data-ttu-id="61841-116">[Composite resurser: Använda en DSC-konfiguration som en resurs @ no__t-0</span><span class="sxs-lookup"><span data-stu-id="61841-116">[Composite resources: Using a DSC configuration as a resource](authoringResourceComposite.md)</span></span>
* [<span data-ttu-id="61841-117">Använda Resource designer-verktyget</span><span class="sxs-lookup"><span data-stu-id="61841-117">Using the Resource Designer tool</span></span>](authoringResourceMofDesigner.md)
