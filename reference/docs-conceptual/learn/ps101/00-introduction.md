---
title: Introduktion
ms.date: 06/02/2020
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
description: Detta är introduktionen till boken PowerShell 101 av Mike F. Robbins.
ms.openlocfilehash: bb6ab1a95404b5d6d5595d62df136a937a1faee4
ms.sourcegitcommit: df5e6f032ee2d4b556d50406832732d2f7dc2502
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/14/2021
ms.locfileid: "98216174"
---
# <a name="introduction"></a><span data-ttu-id="0dddd-103">Introduktion</span><span class="sxs-lookup"><span data-stu-id="0dddd-103">Introduction</span></span>

<table>
  <tr><td>
  <a href="https://leanpub.com/powershell101">
  <img src="media/powershell101-150x194.png" alt="PowerShell 101 (the book)" />
  </a>
  </td>
  <td colspan=2>
<span data-ttu-id="0dddd-104">Innehållet fanns ursprungligen i boken <em>PowerShell 101</em> av Mike F Robbins.</span><span class="sxs-lookup"><span data-stu-id="0dddd-104">This content originally appeared in the book <em>PowerShell 101</em> by Mike F Robbins.</span></span> <span data-ttu-id="0dddd-105">Vi tackar Mike för att ge oss behörighet att återanvända sitt innehåll här.</span><span class="sxs-lookup"><span data-stu-id="0dddd-105">We thank Mike for granting us permission to reuse his content here.</span></span> <span data-ttu-id="0dddd-106">Innehållet har redigerats från den ursprungliga publikationen.</span><span class="sxs-lookup"><span data-stu-id="0dddd-106">The content has been edited from the original publication.</span></span> <span data-ttu-id="0dddd-107">Du kan fortfarande hämta den ursprungliga boken från Leanpub på <a href="https://leanpub.com/powershell101">PowerShell 101</a>.</span><span class="sxs-lookup"><span data-stu-id="0dddd-107">You can still get the original book from Leanpub at <a href="https://leanpub.com/powershell101">PowerShell 101</a>.</span></span>
  </td></tr>
</table>

## <a name="who-is-this-book-for"></a><span data-ttu-id="0dddd-108">Vem är den här boken för?</span><span class="sxs-lookup"><span data-stu-id="0dddd-108">Who is this book for?</span></span>

<span data-ttu-id="0dddd-109">Det här är en bok på ingångs nivå för alla som vill lära sig PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0dddd-109">This is an entry-level book for anyone wanting to learn PowerShell.</span></span>

<span data-ttu-id="0dddd-110">Den här boken fokuserar på PowerShell version 5,1 som körs på Windows 10 och Windows Server 2016 i en Microsoft Active Directory domän miljö.</span><span class="sxs-lookup"><span data-stu-id="0dddd-110">This book focuses on PowerShell version 5.1 running on Windows 10 and Windows Server 2016 in a Microsoft Active Directory domain environment.</span></span> <span data-ttu-id="0dddd-111">De grundläggande begreppen gäller dock för alla versioner av PowerShell som körs på alla plattformar som stöds.</span><span class="sxs-lookup"><span data-stu-id="0dddd-111">However, the basic concepts apply to all versions of PowerShell running on any supported platform.</span></span>

## <a name="about-this-book"></a><span data-ttu-id="0dddd-112">Om den här boken</span><span class="sxs-lookup"><span data-stu-id="0dddd-112">About this book</span></span>

<span data-ttu-id="0dddd-113">Den här boken är en samling av vad jag vill att någon skulle ha sagt mig när jag startade Learning PowerShell, tillsammans med de tips, knep och bästa praxis som jag har lärt oss när jag använde PowerShell under de senaste 10 åren.</span><span class="sxs-lookup"><span data-stu-id="0dddd-113">This book is a collection of what I wish someone would have told me when I started learning PowerShell, along with the tips, tricks, and best practices that I've learned while using PowerShell during the past 10 years.</span></span>

<span data-ttu-id="0dddd-114">I stället för att tillhandahålla enorma mängder information försöker den här boken tillhandahålla en balans med tillräckligt med information för att lyckas för någon som precis har börjat med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0dddd-114">Instead of providing an enormous amount of information, this book attempts to provide a balance of enough information to be successful for someone who is just getting started with PowerShell.</span></span> <span data-ttu-id="0dddd-115">Varje kapitel innehåller länkar till specifika hjälp avsnitt för de som vill ha mer information om de ämnen som beskrivs i det kapitlet.</span><span class="sxs-lookup"><span data-stu-id="0dddd-115">Each chapter contains links to specific help topics for those who want more information about the topics covered in that chapter.</span></span>

## <a name="about-the-author"></a><span data-ttu-id="0dddd-116">Om författaren</span><span class="sxs-lookup"><span data-stu-id="0dddd-116">About the author</span></span>

<span data-ttu-id="0dddd-117">Mike F Robbins är en tidigare Microsoft MVP, en gemensam författare till _Windows POWERSHELL TFM 4-utgåvan_ och en bidrags författare i _PowerShell djup dykningar_ -boken.</span><span class="sxs-lookup"><span data-stu-id="0dddd-117">Mike F Robbins is a former Microsoft MVP, co-author of _Windows PowerShell TFM 4th Edition_, and a contributing author in the _PowerShell Deep Dives_ book.</span></span> <span data-ttu-id="0dddd-118">Mike har varit en stark supportare för PowerShell-gruppen och är nu den ledande skribenten för [Azure PowerShell][] på Microsoft.</span><span class="sxs-lookup"><span data-stu-id="0dddd-118">Mike has been a strong supporter of the PowerShell community and is now the lead writer for [Azure PowerShell][] at Microsoft.</span></span> <span data-ttu-id="0dddd-119">He bloggar på [mikefrobbins.com][] och finns på Twitter [@mikefrobbins][] .</span><span class="sxs-lookup"><span data-stu-id="0dddd-119">He blogs at [mikefrobbins.com][] and can be found on twitter [@mikefrobbins][].</span></span>

## <a name="lab-environment"></a><span data-ttu-id="0dddd-120">Labb miljö</span><span class="sxs-lookup"><span data-stu-id="0dddd-120">Lab environment</span></span>

<span data-ttu-id="0dddd-121">Exemplen i den här boken har utformats och testats på Windows 10 jubileums version (build 1607) och Windows Server 2016 med PowerShell version 5,1.</span><span class="sxs-lookup"><span data-stu-id="0dddd-121">The examples in this book were designed and tested on Windows 10 Anniversary Edition (build 1607) and Windows Server 2016 using PowerShell version 5.1.</span></span> <span data-ttu-id="0dddd-122">Om du använder en annan version av PowerShell eller operativ system kan resultatet skilja sig från de som visas här.</span><span class="sxs-lookup"><span data-stu-id="0dddd-122">If you're using a different version of PowerShell or operating system, your results may differ from those shown here.</span></span>

<!-- link references -->
[@mikefrobbins]: https://twitter.com/mikefrobbins
[mikefrobbins.com]: http://mikefrobbins.com/
[PowerShell 101]: https://leanpub.com/powershell101
[Azure PowerShell]: /powershell/azure
