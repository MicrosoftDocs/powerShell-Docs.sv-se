---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: Starta 32-bitars Version av Windows PowerShell
ms.assetid: 12b31890-2609-4a76-8c24-0ebe78084f50
ms.openlocfilehash: d682ce45ebc92cda3a9008ab608bacf9ef8eba57
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/08/2017
---
# <a name="starting-the-32-bit-version-of-windows-powershell"></a><span data-ttu-id="00805-103">Starta 32-bitarsversionen av Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="00805-103">Starting the 32-Bit Version of Windows PowerShell</span></span>
<span data-ttu-id="00805-104">När du installerar Windows PowerShell på en 64-bitarsdator **Windows PowerShell (x86)**, en 32-bitarsversion av Windows PowerShell installeras förutom 64-bitarsversionen.</span><span class="sxs-lookup"><span data-stu-id="00805-104">When you install Windows PowerShell on a 64-bit computer, **Windows PowerShell (x86)**, a 32-bit version of Windows PowerShell is installed in addition to the 64-bit version.</span></span> <span data-ttu-id="00805-105">64-bitarsversionen körs som standard när du kör Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="00805-105">When you run Windows PowerShell, the 64-bit version runs by default.</span></span>

<span data-ttu-id="00805-106">Men du kan ibland behöva köra **Windows PowerShell (x86)**, t.ex. när du använder en modul som kräver 32-bitarsversionen eller när du ansluter via en fjärranslutning till en 32-bitars dator.</span><span class="sxs-lookup"><span data-stu-id="00805-106">However, you might occasionally need to run **Windows PowerShell (x86)**, such as when you are using a module that requires the 32-bit version or when you are connecting remotely to a 32-bit computer.</span></span>

<span data-ttu-id="00805-107">Använd någon av följande procedurer för att starta en 32-bitarsversion av Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="00805-107">To start a 32-bit version of Windows PowerShell, use any of the following procedures.</span></span>

#### <a name="in-windows-server-2012-r2"></a><span data-ttu-id="00805-108">I Windows Server® 2012 R2</span><span class="sxs-lookup"><span data-stu-id="00805-108">In Windows Server® 2012 R2</span></span>

- <span data-ttu-id="00805-109">På den **starta** skriver **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="00805-109">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="00805-110">Klicka på den **Windows PowerShell x86** panelen.</span><span class="sxs-lookup"><span data-stu-id="00805-110">Click the **Windows PowerShell x86** tile.</span></span>

- <span data-ttu-id="00805-111">I **Serverhanteraren**, från den **verktyg** väljer du **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="00805-111">In **Server Manager**, from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="00805-112">Flytta markören till det övre högra hörnet och klicka på skrivbordet, **Sök**, typen **PowerShell x86** och klicka sedan på **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="00805-112">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="00805-113">Ange via kommandoraden:`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="00805-113">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-server-2012"></a><span data-ttu-id="00805-114">I Windows Server® 2012</span><span class="sxs-lookup"><span data-stu-id="00805-114">In Windows Server® 2012</span></span>

- <span data-ttu-id="00805-115">På den **starta** skriver **PowerShell** och klicka sedan på **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="00805-115">On the **Start** screen, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="00805-116">I **Serverhanteraren**, från den **verktyg** väljer du **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="00805-116">In **Server Manager**, from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="00805-117">Flytta markören till det övre högra hörnet och klicka på skrivbordet, **Sök**, typen **PowerShell** och klicka sedan på **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="00805-117">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="00805-118">Ange via kommandoraden:`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="00805-118">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-81"></a><span data-ttu-id="00805-119">I Windows® 8.1</span><span class="sxs-lookup"><span data-stu-id="00805-119">In Windows® 8.1</span></span>

- <span data-ttu-id="00805-120">På den **starta** skriver **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="00805-120">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="00805-121">Klicka på den **Windows PowerShell x86** panelen.</span><span class="sxs-lookup"><span data-stu-id="00805-121">Click the **Windows PowerShell x86** tile.</span></span>

- <span data-ttu-id="00805-122">Om du kör [Remote Server Administration Tools](http://go.microsoft.com/fwlink/?LinkID=304145) för Windows 8.1 kan du också öppna Windows PowerShell x86 från den **Server ManagerTools** menyn.</span><span class="sxs-lookup"><span data-stu-id="00805-122">If you are running [Remote Server Administration Tools](http://go.microsoft.com/fwlink/?LinkID=304145) for Windows 8.1, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span> <span data-ttu-id="00805-123">Välj **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="00805-123">Select **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="00805-124">Flytta markören till det övre högra hörnet och klicka på skrivbordet, **Sök**, typen **PowerShell x86** och klicka sedan på **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="00805-124">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>
   
- <span data-ttu-id="00805-125">Ange via kommandoraden:`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="00805-125">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-8"></a><span data-ttu-id="00805-126">I Windows® 8</span><span class="sxs-lookup"><span data-stu-id="00805-126">In Windows® 8</span></span>

- <span data-ttu-id="00805-127">På den **starta** skärmen, flyttar markören till det övre högra hörnet, klickar du på **inställningar**, klickar du på **paneler**, och sedan flytta den **visa Administrationsverktyg** skjutreglaget till Ja.</span><span class="sxs-lookup"><span data-stu-id="00805-127">On the **Start** screen, move the cursor to the upper right corner, click **Settings**, click **Tiles**, and then move the **Show Administrative Tools** slider to Yes.</span></span> <span data-ttu-id="00805-128">Skriv **PowerShell** och på **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="00805-128">Then, type **PowerShell** and click **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="00805-129">Om du kör [Remote Server Administration Tools](http://www.microsoft.com/download/details.aspx?id=28972) för Windows 8 kan du också öppna Windows PowerShell x86 från den **Server ManagerTools** menyn.</span><span class="sxs-lookup"><span data-stu-id="00805-129">If you are running [Remote Server Administration Tools](http://www.microsoft.com/download/details.aspx?id=28972) for Windows 8, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span> <span data-ttu-id="00805-130">Välj **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="00805-130">Select **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="00805-131">På den **starta** skärmen eller skrivbordet, Skriv **PowerShell (x86)** och klicka sedan på **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="00805-131">On the **Start** screen or the desktop, type **PowerShell (x86)** and then click **Windows PowerShell (x86)**.</span></span>

- <span data-ttu-id="00805-132">Ange via kommandoraden:`%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="00805-132">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

