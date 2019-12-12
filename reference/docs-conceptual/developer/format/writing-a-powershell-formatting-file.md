---
title: Skriver en fil med PowerShell-format | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 39acce45-5144-43ba-894d-a4ce782fa67d
caps.latest.revision: 13
ms.openlocfilehash: f89f0009972d5237d71cb8f0d1c53cd0ae614b67
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72353412"
---
# <a name="writing-a-powershell-formatting-file"></a><span data-ttu-id="055a0-102">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="055a0-102">Writing a PowerShell Formatting File</span></span>

<span data-ttu-id="055a0-103">"Att skriva en PowerShell-fil" är till exempel på kommando utvecklare som skriver cmdletar eller funktioner som skickar objekt till kommando raden.</span><span class="sxs-lookup"><span data-stu-id="055a0-103">"Writing a PowerShell Formatting File" is for command developers who are writing cmdlets or functions that output objects to the command line.</span></span> <span data-ttu-id="055a0-104">Formatering av filer definierar hur PowerShell visar dessa objekt på kommando raden.</span><span class="sxs-lookup"><span data-stu-id="055a0-104">Formatting files define how PowerShell displays those objects at the command line.</span></span> <span data-ttu-id="055a0-105">Den här dokumentationen innehåller en översikt över hur du formaterar filer, en förklaring av de begrepp som du bör känna till när du skriver de här filerna, exempel på XML som används i dessa filer och ett referens avsnitt för XML-elementen.</span><span class="sxs-lookup"><span data-stu-id="055a0-105">This documentation provides an overview of formatting files, an explanation of the concepts that you should understand when writing these files, examples of XML used in these files, and a reference section for the XML elements.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="055a0-106">I detta avsnitt</span><span class="sxs-lookup"><span data-stu-id="055a0-106">In This Section</span></span>

<span data-ttu-id="055a0-107">[Formaterar fil översikt](./formatting-file-overview.md) Beskriver vad en format fil är och de allmänna komponenterna i en formateringsinformation, inklusive vanliga funktioner som kan definieras i filen, de olika typer av format vyer som kan definieras för .NET-objekt och ett förenklat exempel på XML som används för att definiera en tabellvy.</span><span class="sxs-lookup"><span data-stu-id="055a0-107">[Formatting File Overview](./formatting-file-overview.md) Describes what a format file is and the general components of a formatting file, including common features that can be defined in the file, the different types of format views that can be defined for .NET objects, and a simplified example of the XML used to define a table view.</span></span>

<span data-ttu-id="055a0-108">[Formatera fil koncept](./formatting-file-concepts.md) Innehåller information som du kan behöva känna till när du skapar egna formateringsattribut, till exempel de olika typer av vyer som du kan definiera och särskilda komponenter i dessa vyer.</span><span class="sxs-lookup"><span data-stu-id="055a0-108">[Formatting File Concepts](./formatting-file-concepts.md) Includes information that you might need to know when creating your own formatting files, such as the different types of views that you can define and special components of those views.</span></span>

<span data-ttu-id="055a0-109">[Exempel på filer som ska formateras](./examples-of-formatting-files.md) Innehåller XML-exempel på flera formateringsattribut, inklusive exempel på en tabellvy, en listvy och en bred vy, samt exempel som visar hur du definierar funktioner som urvals uppsättningar, urvals villkor och vanliga kontroller.</span><span class="sxs-lookup"><span data-stu-id="055a0-109">[Examples of Formatting Files](./examples-of-formatting-files.md) Provides XML examples of several formatting files, including examples of a table view, a list view, and a wide view, as well as examples that show how to define features such as selection sets, selection conditions, and common controls.</span></span>

<span data-ttu-id="055a0-110">[Formatera XML-referens](./format-schema-xml-reference.md) Innehåller referens ämnen för de XML-element som används i en format fil.</span><span class="sxs-lookup"><span data-stu-id="055a0-110">[Format XML Reference](./format-schema-xml-reference.md) Includes reference topics for the XML elements used in a formatting file.</span></span>
