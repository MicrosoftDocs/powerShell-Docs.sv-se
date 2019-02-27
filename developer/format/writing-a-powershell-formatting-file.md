---
title: Skriva ett PowerShell formatering fil | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 39acce45-5144-43ba-894d-a4ce782fa67d
caps.latest.revision: 13
ms.openlocfilehash: f89f0009972d5237d71cb8f0d1c53cd0ae614b67
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847546"
---
# <a name="writing-a-powershell-formatting-file"></a><span data-ttu-id="a99fb-102">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="a99fb-102">Writing a PowerShell Formatting File</span></span>

<span data-ttu-id="a99fb-103">”Skriver en PowerShell-formatering fil” är för kommando-utvecklare som skriver cmdletar eller funktioner som mata ut objekt till kommandoraden.</span><span class="sxs-lookup"><span data-stu-id="a99fb-103">"Writing a PowerShell Formatting File" is for command developers who are writing cmdlets or functions that output objects to the command line.</span></span> <span data-ttu-id="a99fb-104">Formateras definierar hur PowerShell visar objekten på kommandoraden.</span><span class="sxs-lookup"><span data-stu-id="a99fb-104">Formatting files define how PowerShell displays those objects at the command line.</span></span> <span data-ttu-id="a99fb-105">Den här dokumentationen innehåller en översikt över formatering filer, en förklaring av de begrepp som du bör känna till när du skriver dessa filer bör du exempel på XML som används i dessa filer och ett referensavsnitt för XML-elementen.</span><span class="sxs-lookup"><span data-stu-id="a99fb-105">This documentation provides an overview of formatting files, an explanation of the concepts that you should understand when writing these files, examples of XML used in these files, and a reference section for the XML elements.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="a99fb-106">I detta avsnitt</span><span class="sxs-lookup"><span data-stu-id="a99fb-106">In This Section</span></span>

<span data-ttu-id="a99fb-107">[Formatering: översikt](./formatting-file-overview.md) beskriver vilka en formatfil är och allmänna delar av en formatering filen, inklusive vanliga funktioner som kan definieras i filen, olika typer av format som kan definieras för .NET-objekt och en förenklat exempel på XML-filen som används för att definiera en tabellvy.</span><span class="sxs-lookup"><span data-stu-id="a99fb-107">[Formatting File Overview](./formatting-file-overview.md) Describes what a format file is and the general components of a formatting file, including common features that can be defined in the file, the different types of format views that can be defined for .NET objects, and a simplified example of the XML used to define a table view.</span></span>

<span data-ttu-id="a99fb-108">[Formatering filen begrepp](./formatting-file-concepts.md) innehåller information som du kan behöva veta vid skapa dina egna formatering av filer, till exempel de olika typerna av vyer som du kan definiera och särskild komponent i dessa vyer.</span><span class="sxs-lookup"><span data-stu-id="a99fb-108">[Formatting File Concepts](./formatting-file-concepts.md) Includes information that you might need to know when creating your own formatting files, such as the different types of views that you can define and special components of those views.</span></span>

<span data-ttu-id="a99fb-109">[Exempel på formatering filer](./examples-of-formatting-files.md) innehåller XML-exempel på flera formatering filer, inklusive exempel på en tabellvy, en listvy och en bred vy och exempel som visar hur du definierar funktioner, till exempel val av uppsättningar, val av villkor, och vanliga kontroller.</span><span class="sxs-lookup"><span data-stu-id="a99fb-109">[Examples of Formatting Files](./examples-of-formatting-files.md) Provides XML examples of several formatting files, including examples of a table view, a list view, and a wide view, as well as examples that show how to define features such as selection sets, selection conditions, and common controls.</span></span>

<span data-ttu-id="a99fb-110">[Formatera XML-referens](./format-schema-xml-reference.md) omfattar referensämnen för XML-elementen som används i en fil med formatering.</span><span class="sxs-lookup"><span data-stu-id="a99fb-110">[Format XML Reference](./format-schema-xml-reference.md) Includes reference topics for the XML elements used in a formatting file.</span></span>
