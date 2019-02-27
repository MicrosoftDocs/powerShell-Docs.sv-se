---
title: Windows PowerShell-cmdleten begrepp | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b3ef3f4-c626-4679-884f-406a37412b3e
caps.latest.revision: 16
ms.openlocfilehash: 2f84c57da7429462c69b2a020d9f8ac04f8d0f35
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846664"
---
# <a name="windows-powershell-cmdlet-concepts"></a><span data-ttu-id="d975a-102">Begrepp relaterade till Windows PowerShell-cmdlets</span><span class="sxs-lookup"><span data-stu-id="d975a-102">Windows PowerShell Cmdlet Concepts</span></span>

<span data-ttu-id="d975a-103">Det här avsnittet beskrivs hur cmdlets fungerar.</span><span class="sxs-lookup"><span data-stu-id="d975a-103">This section describes how cmdlets work.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="d975a-104">I detta avsnitt</span><span class="sxs-lookup"><span data-stu-id="d975a-104">In This Section</span></span>

<span data-ttu-id="d975a-105">Det här avsnittet innehåller följande ämnen.</span><span class="sxs-lookup"><span data-stu-id="d975a-105">This section includes the following topics.</span></span>

<span data-ttu-id="d975a-106">[Riktlinjer för utveckling av cmdlet](./cmdlet-development-guidelines.md) det här avsnittet innehåller riktlinjer för utveckling som kan användas för att skapa rätt cmdlets.</span><span class="sxs-lookup"><span data-stu-id="d975a-106">[Cmdlet Development Guidelines](./cmdlet-development-guidelines.md) This topic provides development guidelines that can be used to produce well-formed cmdlets.</span></span>

<span data-ttu-id="d975a-107">[Cmdlet klassdeklarationen](./cmdlet-class-declaration.md) det här avsnittet beskriver cmdlet klassdeklarationen.</span><span class="sxs-lookup"><span data-stu-id="d975a-107">[Cmdlet Class Declaration](./cmdlet-class-declaration.md) This topic describes cmdlet class declaration.</span></span>

<span data-ttu-id="d975a-108">[Godkända verb för Windows PowerShell-kommandon](./approved-verbs-for-windows-powershell-commands.md) det här avsnittet listar de fördefinierade cmdlet verb som du kan använda när du deklarerar en cmdlet-klass.</span><span class="sxs-lookup"><span data-stu-id="d975a-108">[Approved Verbs for Windows PowerShell Commands](./approved-verbs-for-windows-powershell-commands.md) This topic lists the predefined cmdlet verbs that you can use when you declare a cmdlet class.</span></span>

<span data-ttu-id="d975a-109">[Cmdlet bearbetar inmatningsmetoder](./cmdlet-input-processing-methods.md) det här avsnittet beskrivs de metoder som gör att en cmdlet för att utföra förbearbetning åtgärder, ange bearbetningsåtgärder och publicera bearbetningsåtgärder.</span><span class="sxs-lookup"><span data-stu-id="d975a-109">[Cmdlet Input Processing Methods](./cmdlet-input-processing-methods.md) This topic describes the methods that allow a cmdlet to perform preprocessing operations, input processing operations, and post processing operations.</span></span>

<span data-ttu-id="d975a-110">[Cmdlet-parametrarna](./cmdlet-parameters.md) det här avsnittet beskrivs de olika typerna av parametrar som du kan lägga till cmdlet: ar.</span><span class="sxs-lookup"><span data-stu-id="d975a-110">[Cmdlet Parameters](./cmdlet-parameters.md) This section describes the different types of parameters that you can add to cmdlets.</span></span>

<span data-ttu-id="d975a-111">[Cmdlet-attribut](./cmdlet-attributes.md) i det här avsnittet beskrivs attribut som används för att deklarera .NET Framework-klasser som cmdlet: ar, att deklarera fält som cmdlet-parametrarna och för att deklarera verifiering av indata-regler för parametrar.</span><span class="sxs-lookup"><span data-stu-id="d975a-111">[Cmdlet Attributes](./cmdlet-attributes.md) This section describes the attributes that are used to declare .NET Framework classes as cmdlets, to declare fields as cmdlet parameters, and to declare input validation rules for parameters.</span></span>

<span data-ttu-id="d975a-112">[Alias för cmdleten](./cmdlet-aliases.md) det här avsnittet beskriver cmdlet alias.</span><span class="sxs-lookup"><span data-stu-id="d975a-112">[Cmdlet Aliases](./cmdlet-aliases.md) This topic describes cmdlet aliases.</span></span>

<span data-ttu-id="d975a-113">[Cmdlet-utdata](./cmdlet-output.md) det här avsnittet beskrivs vilken typ av utdata som cmdlet: ar kan returnera och hur du definierar och visa objekten som returneras av cmdlet: ar.</span><span class="sxs-lookup"><span data-stu-id="d975a-113">[Cmdlet Output](./cmdlet-output.md) This section describes the type of output that cmdlets can return and how to define and display the objects that are returned by cmdlets.</span></span>

<span data-ttu-id="d975a-114">[Registrera cmdletar](./modules-and-snap-ins.md) i det här avsnittet beskriver hur du registrerar cmdletar med hjälp av moduler och snapin-moduler.</span><span class="sxs-lookup"><span data-stu-id="d975a-114">[Registering Cmdlets](./modules-and-snap-ins.md) This section describes how to register cmdlets by using modules and snap-ins.</span></span>

<span data-ttu-id="d975a-115">[Uppmanar dig att bekräfta](./requesting-confirmation-from-cmdlets.md) det här avsnittet beskrivs hur cmdletar begär bekräftelse från en användare innan de gör en ändring i systemet.</span><span class="sxs-lookup"><span data-stu-id="d975a-115">[Requesting Confirmation](./requesting-confirmation-from-cmdlets.md) This section describes how cmdlets request confirmation from a user before they make a change to the system.</span></span>

<span data-ttu-id="d975a-116">[Windows PowerShell-felrapportering](./error-reporting-concepts.md) det här avsnittet beskrivs hur cmdletar rapportera avslutande fel och icke-avslutande fel och beskriver hur du tolkar felposter.</span><span class="sxs-lookup"><span data-stu-id="d975a-116">[Windows PowerShell Error Reporting](./error-reporting-concepts.md) This section describes how cmdlets report terminating errors and non-terminating errors, and it describes how to interpret error records.</span></span>

<span data-ttu-id="d975a-117">[Bakgrundsjobb](./background-jobs.md) det här avsnittet beskrivs hur cmdlets kan utföra sitt arbete inom bakgrundsjobb som inte stör de kommandon som körs i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="d975a-117">[Background Jobs](./background-jobs.md) This topic describes how cmdlets can perform their work within background jobs that do not interfere with the commands that are executing in the current session.</span></span>

<span data-ttu-id="d975a-118">[Anropar Cmdlets och skript i en Cmdlet](./invoking-cmdlets-and-scripts-within-a-cmdlet.md) det här avsnittet beskrivs hur cmdlets kan anropa andra cmdlet: ar och skript inifrån sin syn metoderna.</span><span class="sxs-lookup"><span data-stu-id="d975a-118">[Invoking Cmdlets and Scripts Within a Cmdlet](./invoking-cmdlets-and-scripts-within-a-cmdlet.md) This topic describes how cmdlets can invoke other cmdlets and scripts from within their input processing methods.</span></span>

<span data-ttu-id="d975a-119">[Cmdlet: en anger](./cmdlet-sets.md) det här avsnittet beskrivs hur du använder basklasser för att skapa uppsättningar av cmdlets.</span><span class="sxs-lookup"><span data-stu-id="d975a-119">[Cmdlet Sets](./cmdlet-sets.md) This topic describes using base classes to create sets of cmdlets.</span></span>

<span data-ttu-id="d975a-120">[Windows PowerShell-sessionstillstånd](./windows-powershell-session-state.md) det här avsnittet beskriver Windows PowerShell-sessionstillstånd.</span><span class="sxs-lookup"><span data-stu-id="d975a-120">[Windows PowerShell Session State](./windows-powershell-session-state.md) This topic describes Windows PowerShell session state.</span></span>
