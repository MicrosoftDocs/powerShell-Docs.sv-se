---
title: Skriva ett Windows PowerShell-arbetsflöde | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2551ceed-836f-4275-9fc0-ea68446d6a35
caps.latest.revision: 7
ms.openlocfilehash: 0f8a9938a1685e9abc2f1dbfb18c3b2b9008d9be
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83564934"
---
# <a name="writing-a-windows-powershell-workflow"></a><span data-ttu-id="f8a10-102">Skriva ett Windows PowerShell-arbetsflöde</span><span class="sxs-lookup"><span data-stu-id="f8a10-102">Writing a Windows PowerShell Workflow</span></span>

<span data-ttu-id="f8a10-103">Du kan skapa ett XAML-arbetsflöde genom att lägga till aktiviteter som exponeras av Windows PowerShell-sammansättningar i arbetsflödesdesignern i Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f8a10-103">You can create a XAML workflow by adding activities exposed by Windows PowerShell assemblies to the Workflow designer in Visual Studio.</span></span> <span data-ttu-id="f8a10-104">Följande Windows PowerShell-sammansättningar exponerar arbets flöde – aktiverade aktiviteter.</span><span class="sxs-lookup"><span data-stu-id="f8a10-104">The following Windows PowerShell assemblies expose workflow-enabled activities.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f8a10-105">Ett XAML-arbetsflöde måste paketeras som en modul om du vill ge hjälp för arbets flödet.</span><span class="sxs-lookup"><span data-stu-id="f8a10-105">A XAML workflow must be packaged as a module if you want to provide help for the workflow.</span></span> <span data-ttu-id="f8a10-106">Information om moduler finns i [skriva en Windows PowerShell-modul](../module/writing-a-windows-powershell-module.md).</span><span class="sxs-lookup"><span data-stu-id="f8a10-106">For information about modules, see [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).</span></span>

- [<span data-ttu-id="f8a10-107">Microsoft. PowerShell.-aktiviteter</span><span class="sxs-lookup"><span data-stu-id="f8a10-107">Microsoft.Powershell.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Activities)

- [<span data-ttu-id="f8a10-108">Microsoft. PowerShell. Core. Activities</span><span class="sxs-lookup"><span data-stu-id="f8a10-108">Microsoft.Powershell.Core.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Core.Activities)

- [<span data-ttu-id="f8a10-109">Microsoft. PowerShell. Diagnostics.-aktiviteter</span><span class="sxs-lookup"><span data-stu-id="f8a10-109">Microsoft.Powershell.Diagnostics.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Diagnostics.Activities)

- [<span data-ttu-id="f8a10-110">Microsoft. PowerShell. Management. Activities</span><span class="sxs-lookup"><span data-stu-id="f8a10-110">Microsoft.Powershell.Management.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Management.Activities)

- [<span data-ttu-id="f8a10-111">Microsoft. PowerShell. Security. Activities</span><span class="sxs-lookup"><span data-stu-id="f8a10-111">Microsoft.Powershell.Security.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Security.Activities)

- [<span data-ttu-id="f8a10-112">Microsoft. PowerShell. Utility.-aktiviteter</span><span class="sxs-lookup"><span data-stu-id="f8a10-112">Microsoft.Powershell.Utility.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Utility.Activities)

  <span data-ttu-id="f8a10-113">I följande avsnitt beskrivs hur du skapar ett arbets flöde med hjälp av Windows PowerShell-aktiviteter.</span><span class="sxs-lookup"><span data-stu-id="f8a10-113">The following topics describe how to create a Workflow by using Windows PowerShell activities.</span></span>

- [<span data-ttu-id="f8a10-114">Lägga till Windows PowerShell-aktiviteter till Visual Studio Toolbox</span><span class="sxs-lookup"><span data-stu-id="f8a10-114">Adding Windows PowerShell Activities to the Visual Studio Toolbox</span></span>](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md)

- [<span data-ttu-id="f8a10-115">Skapa ett arbetsflöde med Windows PowerShell-aktiviteter</span><span class="sxs-lookup"><span data-stu-id="f8a10-115">Creating a Workflow with Windows PowerShell Activities</span></span>](./creating-a-workflow-with-windows-powershell-activities.md)

- [<span data-ttu-id="f8a10-116">Skapa ett arbetsflöde med hjälp av ett Windows PowerShell-skript</span><span class="sxs-lookup"><span data-stu-id="f8a10-116">Creating a Workflow by Using a Windows PowerShell Script</span></span>](./creating-a-workflow-by-using-a-windows-powershell-script.md)

- [<span data-ttu-id="f8a10-117">Importera och anropa ett Windows PowerShell-arbetsflöde</span><span class="sxs-lookup"><span data-stu-id="f8a10-117">Importing and Invoking a Windows PowerShell Workflow</span></span>](./importing-and-invoking-a-windows-powershell-workflow.md)

- [<span data-ttu-id="f8a10-118">Skapa en arbetsflödesaktivitet från en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="f8a10-118">Creating a Workflow Activity from a Windows PowerShell Cmdlet</span></span>](./creating-a-workflow-activity-from-a-windows-powershell-cmdlet.md)
