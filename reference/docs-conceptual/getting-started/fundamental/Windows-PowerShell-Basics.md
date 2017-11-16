---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Grunderna i Windows PowerShell
ms.assetid: 6b3cbbc8-060c-4877-b00b-7300dbbe4e28
ms.openlocfilehash: 7b5cdfce876aa7d5559fe772379829011b275a02
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/08/2017
---
# <a name="windows-powershell-basics"></a><span data-ttu-id="52a66-103">Grunderna i Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="52a66-103">Windows PowerShell Basics</span></span>
<span data-ttu-id="52a66-104">Grafiska användargränssnitt använda några grundläggande begrepp som är kända för de flesta användare.</span><span class="sxs-lookup"><span data-stu-id="52a66-104">Graphical user interfaces use some basic concepts that are well known to most computer users.</span></span> <span data-ttu-id="52a66-105">Användare är beroende av välbekanta av dessa gränssnitt för att utföra aktiviteter.</span><span class="sxs-lookup"><span data-stu-id="52a66-105">Users rely on the familiarity of those interfaces to accomplish tasks.</span></span> <span data-ttu-id="52a66-106">Operativsystem ge användarna en grafisk representation av objekt som kan visas, vanligtvis med nedrullningsbara menyer för specifika funktioner och kontext menyer för att komma åt sammanhangsberoende funktioner.</span><span class="sxs-lookup"><span data-stu-id="52a66-106">Operating systems present users with a graphical representation of items that can be browsed, usually with drop-down menus for accessing specific functionality and context menus for accessing context-specific functionality.</span></span>

<span data-ttu-id="52a66-107">Kommandoradsgränssnittet (CLI), till exempel Windows PowerShell måste använda en annan metod för att avslöja information, eftersom den inte har menyer eller grafiska system kan hjälpa användaren.</span><span class="sxs-lookup"><span data-stu-id="52a66-107">A command-line interface (CLI), such as Windows PowerShell, must use a different approach to expose information, because it does not have menus or graphical systems to help the user.</span></span> <span data-ttu-id="52a66-108">Du bör känna till kommandonamn innan du kan använda dem.</span><span class="sxs-lookup"><span data-stu-id="52a66-108">You need to know command names before you can use them.</span></span> <span data-ttu-id="52a66-109">Men du kan skriva komplexa kommandon som motsvarar funktionerna i en GUI-miljö, måste du bekanta dig med vanliga kommandon och parametrar.</span><span class="sxs-lookup"><span data-stu-id="52a66-109">Although you can type complex commands that are equivalent to the features in a GUI environment, you must become familiar with commonly-used commands and command parameters.</span></span>

<span data-ttu-id="52a66-110">De flesta CLIs har inte mönster som kan hjälpa användaren att lära dig gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="52a66-110">Most CLIs do not have patterns that can help the user to learn the interface.</span></span> <span data-ttu-id="52a66-111">Eftersom CLIs var de första gränssnitt för operativsystemet, har många kommandonamn och parameternamn valts godtyckligt.</span><span class="sxs-lookup"><span data-stu-id="52a66-111">Because CLIs were the first operating system shells, many command names and parameter names were selected arbitrarily.</span></span> <span data-ttu-id="52a66-112">Terse kommandonamn har vanligtvis valt över avmarkera de.</span><span class="sxs-lookup"><span data-stu-id="52a66-112">Terse command names were generally chosen over clear ones.</span></span> <span data-ttu-id="52a66-113">Även om hjälpsystemet och kommandot designstandarder är integrerade i de flesta CLIs, de är vanligtvis avsedda för kompatibilitet med kommandona tidigaste så kommandot är fortfarande formats av beslut som gjorts sedan åren.</span><span class="sxs-lookup"><span data-stu-id="52a66-113">Although help systems and command design standards are integrated into most CLIs, they have been generally designed for compatibility with the earliest commands, so the command set is still shaped by decisions made decades ago.</span></span>

<span data-ttu-id="52a66-114">Windows PowerShell har utformats för att dra nytta av en användares historiska kunskap om CLIs.</span><span class="sxs-lookup"><span data-stu-id="52a66-114">Windows PowerShell was designed to take advantage of a user's historic knowledge of CLIs.</span></span> <span data-ttu-id="52a66-115">I det här kapitlet kommer vi om vissa grundläggande verktyg och koncept som du kan använda för att snabbt lära sig Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="52a66-115">In this chapter, we will talk about some basic tools and concepts that you can use to learn Windows PowerShell quickly.</span></span> <span data-ttu-id="52a66-116">Dessa är:</span><span class="sxs-lookup"><span data-stu-id="52a66-116">They include:</span></span>

- <span data-ttu-id="52a66-117">Kommandot Get</span><span class="sxs-lookup"><span data-stu-id="52a66-117">Using Get-Command</span></span>

- <span data-ttu-id="52a66-118">Kommandona Cmd.exe och UNIX</span><span class="sxs-lookup"><span data-stu-id="52a66-118">Using Cmd.exe and UNIX commands</span></span>

- <span data-ttu-id="52a66-119">Med hjälp av externa kommandon</span><span class="sxs-lookup"><span data-stu-id="52a66-119">Using External Commands</span></span>

- <span data-ttu-id="52a66-120">Med fliken slutförande</span><span class="sxs-lookup"><span data-stu-id="52a66-120">Using Tab-Completion</span></span>

- <span data-ttu-id="52a66-121">Med hjälp av Get-Help</span><span class="sxs-lookup"><span data-stu-id="52a66-121">Using Get-Help</span></span>

