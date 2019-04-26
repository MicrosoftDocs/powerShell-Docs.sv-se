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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080330"
---
# <a name="writing-a-windows-powershell-workflow"></a><span data-ttu-id="1ca59-102">Skriva ett Windows PowerShell-arbetsflöde</span><span class="sxs-lookup"><span data-stu-id="1ca59-102">Writing a Windows PowerShell Workflow</span></span>

<span data-ttu-id="1ca59-103">Du kan skapa ett arbetsflöde i XAML genom att lägga till aktiviteter som visas av Windows PowerShell-sammansättningar till Arbetsflödesdesignern i Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1ca59-103">You can create a XAML workflow by adding activities exposed by Windows PowerShell assemblies to the Workflow designer in Visual Studio.</span></span> <span data-ttu-id="1ca59-104">Följande Windows PowerShell-sammansättningar visar arbetsflödet-aktiverade aktiviteter.</span><span class="sxs-lookup"><span data-stu-id="1ca59-104">The following Windows PowerShell assemblies expose workflow-enabled activities.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1ca59-105">Ett arbetsflöde i XAML måste vara paketerad som en modul om du vill visa hjälp för arbetsflödet.</span><span class="sxs-lookup"><span data-stu-id="1ca59-105">A XAML workflow must be packaged as a module if you want to provide help for the workflow.</span></span> <span data-ttu-id="1ca59-106">Läs om hur moduler [skriva en Windows PowerShell-modul](../module/writing-a-windows-powershell-module.md).</span><span class="sxs-lookup"><span data-stu-id="1ca59-106">For information about modules, see [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).</span></span>

- [<span data-ttu-id="1ca59-107">Microsoft.Powershell.Activities</span><span class="sxs-lookup"><span data-stu-id="1ca59-107">Microsoft.Powershell.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Activities)

- [<span data-ttu-id="1ca59-108">Microsoft.Powershell.Core.Activities</span><span class="sxs-lookup"><span data-stu-id="1ca59-108">Microsoft.Powershell.Core.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Core.Activities)

- [<span data-ttu-id="1ca59-109">Microsoft.Powershell.Diagnostics.Activities</span><span class="sxs-lookup"><span data-stu-id="1ca59-109">Microsoft.Powershell.Diagnostics.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Diagnostics.Activities)

- [<span data-ttu-id="1ca59-110">Microsoft.Powershell.Management.Activities</span><span class="sxs-lookup"><span data-stu-id="1ca59-110">Microsoft.Powershell.Management.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Management.Activities)

- [<span data-ttu-id="1ca59-111">Microsoft.Powershell.Security.Activities</span><span class="sxs-lookup"><span data-stu-id="1ca59-111">Microsoft.Powershell.Security.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Security.Activities)

- [<span data-ttu-id="1ca59-112">Microsoft.Powershell.Utility.Activities</span><span class="sxs-lookup"><span data-stu-id="1ca59-112">Microsoft.Powershell.Utility.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Utility.Activities)

  <span data-ttu-id="1ca59-113">I följande avsnitt beskrivs hur du skapar ett arbetsflöde med hjälp av Windows PowerShell-aktiviteter.</span><span class="sxs-lookup"><span data-stu-id="1ca59-113">The following topics describe how to create a Workflow by using Windows PowerShell activities.</span></span>

- [<span data-ttu-id="1ca59-114">Att lägga till Windows PowerShell-aktiviteter i verktygslådan Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1ca59-114">Adding Windows PowerShell Activities to the Visual Studio Toolbox</span></span>](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md)

- [<span data-ttu-id="1ca59-115">Skapa ett arbetsflöde med Windows PowerShell-aktiviteter</span><span class="sxs-lookup"><span data-stu-id="1ca59-115">Creating a Workflow with Windows PowerShell Activities</span></span>](./creating-a-workflow-with-windows-powershell-activities.md)

- [<span data-ttu-id="1ca59-116">Skapa ett arbetsflöde med hjälp av ett Windows PowerShell-skript</span><span class="sxs-lookup"><span data-stu-id="1ca59-116">Creating a Workflow by Using a Windows PowerShell Script</span></span>](./creating-a-workflow-by-using-a-windows-powershell-script.md)

- [<span data-ttu-id="1ca59-117">Importera och anropar ett Windows PowerShell-arbetsflöde</span><span class="sxs-lookup"><span data-stu-id="1ca59-117">Importing and Invoking a Windows PowerShell Workflow</span></span>](./importing-and-invoking-a-windows-powershell-workflow.md)

- [<span data-ttu-id="1ca59-118">Skapa en arbetsflödesaktivitet från en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="1ca59-118">Creating a Workflow Activity from a Windows PowerShell Cmdlet</span></span>](./creating-a-workflow-activity-from-a-windows-powershell-cmdlet.md)