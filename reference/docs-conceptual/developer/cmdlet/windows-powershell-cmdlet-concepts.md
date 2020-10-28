---
ms.date: 09/13/2016
ms.topic: reference
title: Begrepp relaterade till Windows PowerShell-cmdlets
description: Begrepp relaterade till Windows PowerShell-cmdlets
ms.openlocfilehash: da34d3d229f6d57ee22d84fc024b31eb2ee27ba3
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92652525"
---
# <a name="windows-powershell-cmdlet-concepts"></a><span data-ttu-id="930f6-103">Begrepp relaterade till Windows PowerShell-cmdlets</span><span class="sxs-lookup"><span data-stu-id="930f6-103">Windows PowerShell Cmdlet Concepts</span></span>

<span data-ttu-id="930f6-104">I det här avsnittet beskrivs hur cmdlets fungerar.</span><span class="sxs-lookup"><span data-stu-id="930f6-104">This section describes how cmdlets work.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="930f6-105">I det här avsnittet</span><span class="sxs-lookup"><span data-stu-id="930f6-105">In This Section</span></span>

<span data-ttu-id="930f6-106">Det här avsnittet innehåller följande ämnen.</span><span class="sxs-lookup"><span data-stu-id="930f6-106">This section includes the following topics.</span></span>

<span data-ttu-id="930f6-107">[Rikt linjer för cmdlet-utveckling](./cmdlet-development-guidelines.md) Det här avsnittet innehåller rikt linjer för utveckling som kan användas för att skapa välformulerade cmdlets.</span><span class="sxs-lookup"><span data-stu-id="930f6-107">[Cmdlet Development Guidelines](./cmdlet-development-guidelines.md) This topic provides development guidelines that can be used to produce well-formed cmdlets.</span></span>

<span data-ttu-id="930f6-108">[Klass deklaration för cmdlet](./cmdlet-class-declaration.md) I det här avsnittet beskrivs cmdlet-klassens deklaration.</span><span class="sxs-lookup"><span data-stu-id="930f6-108">[Cmdlet Class Declaration](./cmdlet-class-declaration.md) This topic describes cmdlet class declaration.</span></span>

<span data-ttu-id="930f6-109">[Godkända verb för Windows PowerShell-kommandon](./approved-verbs-for-windows-powershell-commands.md) I det här avsnittet visas de fördefinierade cmdlet-verb som du kan använda när du deklarerar en cmdlet-klass.</span><span class="sxs-lookup"><span data-stu-id="930f6-109">[Approved Verbs for Windows PowerShell Commands](./approved-verbs-for-windows-powershell-commands.md) This topic lists the predefined cmdlet verbs that you can use when you declare a cmdlet class.</span></span>

<span data-ttu-id="930f6-110">[Cmdlet-indata bearbetnings metoder](./cmdlet-input-processing-methods.md) I det här avsnittet beskrivs de metoder som gör att en cmdlet kan utföra för bearbetnings åtgärder, åtgärder för indata och bearbetning av bearbetnings åtgärder.</span><span class="sxs-lookup"><span data-stu-id="930f6-110">[Cmdlet Input Processing Methods](./cmdlet-input-processing-methods.md) This topic describes the methods that allow a cmdlet to perform preprocessing operations, input processing operations, and post processing operations.</span></span>

<span data-ttu-id="930f6-111">[Cmdlet-parametrar](./cmdlet-parameters.md) I det här avsnittet beskrivs de olika typerna av parametrar som du kan lägga till i-cmdletar.</span><span class="sxs-lookup"><span data-stu-id="930f6-111">[Cmdlet Parameters](./cmdlet-parameters.md) This section describes the different types of parameters that you can add to cmdlets.</span></span>

<span data-ttu-id="930f6-112">[Cmdlet-attribut](./cmdlet-attributes.md) I det här avsnittet beskrivs de attribut som används för att deklarera .NET Framework klasser som cmdlets, för att deklarera fält som cmdlet-parametrar och för att deklarera ingångs verifierings regler för parametrar.</span><span class="sxs-lookup"><span data-stu-id="930f6-112">[Cmdlet Attributes](./cmdlet-attributes.md) This section describes the attributes that are used to declare .NET Framework classes as cmdlets, to declare fields as cmdlet parameters, and to declare input validation rules for parameters.</span></span>

<span data-ttu-id="930f6-113">[Cmdlet-alias](./cmdlet-aliases.md) I det här avsnittet beskrivs cmdlet-alias.</span><span class="sxs-lookup"><span data-stu-id="930f6-113">[Cmdlet Aliases](./cmdlet-aliases.md) This topic describes cmdlet aliases.</span></span>

<span data-ttu-id="930f6-114">[Cmdlet-utdata](./cmdlet-output.md) I det här avsnittet beskrivs vilken typ av utdata som cmdletar kan returnera och hur du definierar och visar de objekt som returneras av cmdletar.</span><span class="sxs-lookup"><span data-stu-id="930f6-114">[Cmdlet Output](./cmdlet-output.md) This section describes the type of output that cmdlets can return and how to define and display the objects that are returned by cmdlets.</span></span>

<span data-ttu-id="930f6-115">[Registrerar cmdletar](./modules-and-snap-ins.md) I det här avsnittet beskrivs hur du registrerar cmdlets med hjälp av moduler och snapin-moduler.</span><span class="sxs-lookup"><span data-stu-id="930f6-115">[Registering Cmdlets](./modules-and-snap-ins.md) This section describes how to register cmdlets by using modules and snap-ins.</span></span>

<span data-ttu-id="930f6-116">[Begär bekräftelse](./requesting-confirmation-from-cmdlets.md) I det här avsnittet beskrivs hur cmdletar begär bekräftelse från en användare innan de gör en ändring i systemet.</span><span class="sxs-lookup"><span data-stu-id="930f6-116">[Requesting Confirmation](./requesting-confirmation-from-cmdlets.md) This section describes how cmdlets request confirmation from a user before they make a change to the system.</span></span>

<span data-ttu-id="930f6-117">[Windows PowerShell fel rapportering](./error-reporting-concepts.md) I det här avsnittet beskrivs hur cmdlets rapporterar fel och icke-avslutande fel och beskriver hur du tolkar fel poster.</span><span class="sxs-lookup"><span data-stu-id="930f6-117">[Windows PowerShell Error Reporting](./error-reporting-concepts.md) This section describes how cmdlets report terminating errors and non-terminating errors, and it describes how to interpret error records.</span></span>

<span data-ttu-id="930f6-118">[Bakgrunds jobb](./background-jobs.md) I det här avsnittet beskrivs hur cmdlets kan utföra sitt arbete i bakgrunds jobb som inte stör de kommandon som körs i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="930f6-118">[Background Jobs](./background-jobs.md) This topic describes how cmdlets can perform their work within background jobs that do not interfere with the commands that are executing in the current session.</span></span>

<span data-ttu-id="930f6-119">[Anropa cmdlets och skript inom en cmdlet](./invoking-cmdlets-and-scripts-within-a-cmdlet.md) I det här avsnittet beskrivs hur cmdlets kan anropa andra cmdlets och skript inifrån deras metoder för bearbetning av indata.</span><span class="sxs-lookup"><span data-stu-id="930f6-119">[Invoking Cmdlets and Scripts Within a Cmdlet](./invoking-cmdlets-and-scripts-within-a-cmdlet.md) This topic describes how cmdlets can invoke other cmdlets and scripts from within their input processing methods.</span></span>

<span data-ttu-id="930f6-120">[Cmdlet-uppsättningar](./cmdlet-sets.md) I det här avsnittet beskrivs hur du använder bas klasser för att skapa uppsättningar cmdlets.</span><span class="sxs-lookup"><span data-stu-id="930f6-120">[Cmdlet Sets](./cmdlet-sets.md) This topic describes using base classes to create sets of cmdlets.</span></span>

<span data-ttu-id="930f6-121">Sessionstillstånd för [Windows PowerShell](./windows-powershell-session-state.md) I det här avsnittet beskrivs sessionstillstånd för Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="930f6-121">[Windows PowerShell Session State](./windows-powershell-session-state.md) This topic describes Windows PowerShell session state.</span></span>
