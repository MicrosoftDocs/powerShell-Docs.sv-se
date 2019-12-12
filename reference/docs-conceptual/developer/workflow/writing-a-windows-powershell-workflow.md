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
ms.openlocfilehash: 4f0be193fb5b5c753d040a48e5f49235ece11708
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72356632"
---
# <a name="writing-a-windows-powershell-workflow"></a><span data-ttu-id="f72e0-102">Skriva ett Windows PowerShell-arbetsflöde</span><span class="sxs-lookup"><span data-stu-id="f72e0-102">Writing a Windows PowerShell Workflow</span></span>

<span data-ttu-id="f72e0-103">Du kan skapa ett XAML-arbetsflöde genom att lägga till aktiviteter som exponeras av Windows PowerShell-sammansättningar i arbetsflödesdesignern i Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f72e0-103">You can create a XAML workflow by adding activities exposed by Windows PowerShell assemblies to the Workflow designer in Visual Studio.</span></span> <span data-ttu-id="f72e0-104">Följande Windows PowerShell-sammansättningar exponerar arbets flöde – aktiverade aktiviteter.</span><span class="sxs-lookup"><span data-stu-id="f72e0-104">The following Windows PowerShell assemblies expose workflow-enabled activities.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f72e0-105">Ett XAML-arbetsflöde måste paketeras som en modul om du vill ge hjälp för arbets flödet.</span><span class="sxs-lookup"><span data-stu-id="f72e0-105">A XAML workflow must be packaged as a module if you want to provide help for the workflow.</span></span> <span data-ttu-id="f72e0-106">Information om moduler finns i [skriva en Windows PowerShell-modul](../module/writing-a-windows-powershell-module.md).</span><span class="sxs-lookup"><span data-stu-id="f72e0-106">For information about modules, see [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).</span></span>

- [<span data-ttu-id="f72e0-107">Microsoft. PowerShell.-aktiviteter</span><span class="sxs-lookup"><span data-stu-id="f72e0-107">Microsoft.Powershell.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Activities)

- [<span data-ttu-id="f72e0-108">Microsoft. PowerShell. Core. Activities</span><span class="sxs-lookup"><span data-stu-id="f72e0-108">Microsoft.Powershell.Core.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Core.Activities)

- [<span data-ttu-id="f72e0-109">Microsoft. PowerShell. Diagnostics.-aktiviteter</span><span class="sxs-lookup"><span data-stu-id="f72e0-109">Microsoft.Powershell.Diagnostics.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Diagnostics.Activities)

- [<span data-ttu-id="f72e0-110">Microsoft. PowerShell. Management. Activities</span><span class="sxs-lookup"><span data-stu-id="f72e0-110">Microsoft.Powershell.Management.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Management.Activities)

- [<span data-ttu-id="f72e0-111">Microsoft. PowerShell. Security. Activities</span><span class="sxs-lookup"><span data-stu-id="f72e0-111">Microsoft.Powershell.Security.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Security.Activities)

- [<span data-ttu-id="f72e0-112">Microsoft. PowerShell. Utility.-aktiviteter</span><span class="sxs-lookup"><span data-stu-id="f72e0-112">Microsoft.Powershell.Utility.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Utility.Activities)

  <span data-ttu-id="f72e0-113">I följande avsnitt beskrivs hur du skapar ett arbets flöde med hjälp av Windows PowerShell-aktiviteter.</span><span class="sxs-lookup"><span data-stu-id="f72e0-113">The following topics describe how to create a Workflow by using Windows PowerShell activities.</span></span>

- [<span data-ttu-id="f72e0-114">Lägga till Windows PowerShell-aktiviteter i Visual Studio-verktygslådan</span><span class="sxs-lookup"><span data-stu-id="f72e0-114">Adding Windows PowerShell Activities to the Visual Studio Toolbox</span></span>](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md)

- [<span data-ttu-id="f72e0-115">Skapa ett arbets flöde med Windows PowerShell-aktiviteter</span><span class="sxs-lookup"><span data-stu-id="f72e0-115">Creating a Workflow with Windows PowerShell Activities</span></span>](./creating-a-workflow-with-windows-powershell-activities.md)

- [<span data-ttu-id="f72e0-116">Skapa ett arbets flöde med hjälp av ett Windows PowerShell-skript</span><span class="sxs-lookup"><span data-stu-id="f72e0-116">Creating a Workflow by Using a Windows PowerShell Script</span></span>](./creating-a-workflow-by-using-a-windows-powershell-script.md)

- [<span data-ttu-id="f72e0-117">Importera och anropa ett Windows PowerShell-arbetsflöde</span><span class="sxs-lookup"><span data-stu-id="f72e0-117">Importing and Invoking a Windows PowerShell Workflow</span></span>](./importing-and-invoking-a-windows-powershell-workflow.md)

- [<span data-ttu-id="f72e0-118">Skapa en arbets flödes aktivitet från en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="f72e0-118">Creating a Workflow Activity from a Windows PowerShell Cmdlet</span></span>](./creating-a-workflow-activity-from-a-windows-powershell-cmdlet.md)