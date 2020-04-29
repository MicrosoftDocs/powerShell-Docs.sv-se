---
ms.date: 08/23/2017
keywords: PowerShell, cmdlet
title: Avinstallera Windows PowerShell-Webbåtkomst
ms.openlocfilehash: 3c2c83525f5a240976eef215b5eac939796c91e8
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "78279018"
---
# <a name="uninstall-windows-powershell-web-access"></a><span data-ttu-id="4dd35-103">Avinstallera Windows PowerShell-Webbåtkomst</span><span class="sxs-lookup"><span data-stu-id="4dd35-103">Uninstall Windows PowerShell Web Access</span></span>

<span data-ttu-id="4dd35-104">Uppdaterad: 24 juni 2013</span><span class="sxs-lookup"><span data-stu-id="4dd35-104">Updated: June 24, 2013</span></span>

<span data-ttu-id="4dd35-105">Gäller för: Windows Server 2012 R2, Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="4dd35-105">Applies To: Windows Server 2012 R2, Windows Server 2012</span></span>

<span data-ttu-id="4dd35-106">Stegen i det här avsnittet tar bort webbplatsen för Windows PowerShell-webbåtkomsten och motsvarande program från Gateway-servern där den är installerad.</span><span class="sxs-lookup"><span data-stu-id="4dd35-106">The steps in this topic remove the Windows PowerShell Web Access website and corresponding application from the gateway server where it is installed.</span></span>

## <a name="notify-users"></a><span data-ttu-id="4dd35-107">Meddela användarna</span><span class="sxs-lookup"><span data-stu-id="4dd35-107">Notify users</span></span>

<span data-ttu-id="4dd35-108">Innan du börjar ska du meddela användarna om den webbaserade konsolen som du tar bort webbplatsen.</span><span class="sxs-lookup"><span data-stu-id="4dd35-108">Before you begin, notify users of the web-based console that you are removing the website.</span></span>

<span data-ttu-id="4dd35-109">Om du avinstallerar Windows PowerShell-webbåtkomsten avinstalleras inte IIS eller andra funktioner som installerades automatiskt eftersom Windows PowerShell-webbåtkomsten kräver att de körs.</span><span class="sxs-lookup"><span data-stu-id="4dd35-109">Uninstalling Windows PowerShell Web Access does not uninstall IIS or any other features that were installed automatically because Windows PowerShell Web Access requires them to run.</span></span> <span data-ttu-id="4dd35-110">Avinstallations processen lämnar funktioner som är installerade när Windows PowerShell-webbåtkomsten var beroende. Du kan avinstallera dessa funktioner separat om det behövs.</span><span class="sxs-lookup"><span data-stu-id="4dd35-110">The uninstallation process leaves features installed upon which Windows PowerShell Web Access was dependent; you can uninstall those features separately if needed.</span></span>

## <a name="recommended-quick-uninstallation"></a><span data-ttu-id="4dd35-111">Rekommenderad (snabb) avinstallation</span><span class="sxs-lookup"><span data-stu-id="4dd35-111">Recommended (quick) uninstallation</span></span>

<span data-ttu-id="4dd35-112">Procedurerna i det här avsnittet hjälper dig att avinstallera båda:</span><span class="sxs-lookup"><span data-stu-id="4dd35-112">Procedures in this section help you uninstall both:</span></span>

- <span data-ttu-id="4dd35-113">webb programmet för Windows PowerShell-webbåtkomst och</span><span class="sxs-lookup"><span data-stu-id="4dd35-113">the Windows PowerShell Web Access web application, and</span></span>
- <span data-ttu-id="4dd35-114">Windows PowerShell-funktionen för webb åtkomst</span><span class="sxs-lookup"><span data-stu-id="4dd35-114">the Windows PowerShell Web Access feature</span></span>

<span data-ttu-id="4dd35-115">med hjälp av Windows PowerShell-cmdletar.</span><span class="sxs-lookup"><span data-stu-id="4dd35-115">by using Windows PowerShell cmdlets.</span></span>

### <a name="step-1-delete-the-web-application-using-cmdlets"></a><span data-ttu-id="4dd35-116">Steg 1: ta bort webb programmet med cmdletar</span><span class="sxs-lookup"><span data-stu-id="4dd35-116">Step 1: Delete the web application using cmdlets</span></span>

1. <span data-ttu-id="4dd35-117">Gör något av följande för att öppna en Windows PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="4dd35-117">Do one of the following to open a Windows PowerShell session.</span></span>

   - <span data-ttu-id="4dd35-118">På Windows-skrivbordet högerklickar du på **Windows PowerShell** i aktivitets fältet.</span><span class="sxs-lookup"><span data-stu-id="4dd35-118">On the Windows desktop, right-click **Windows PowerShell** on the taskbar.</span></span>
   - <span data-ttu-id="4dd35-119">På Windows **Start** -skärmen klickar du på **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="4dd35-119">On the Windows **Start** screen, click **Windows PowerShell**.</span></span>

2. <span data-ttu-id="4dd35-120">Skriv `Uninstall-PswaWebApplication`och tryck sedan på **RETUR**.</span><span class="sxs-lookup"><span data-stu-id="4dd35-120">Type `Uninstall-PswaWebApplication`, and then press **Enter**.</span></span>

   1. <span data-ttu-id="4dd35-121">Om du har angett ett eget namn på en anpassad webbplats lägger `-WebsiteName` du till parametern till ditt kommando och anger namnet på webbplatsen.</span><span class="sxs-lookup"><span data-stu-id="4dd35-121">If you have specified your own, custom website name, add the `-WebsiteName` parameter to your command, and specify the website name.</span></span>

      `Uninstall-PswaWebApplication -WebsiteName <web-site-name>`

   1. <span data-ttu-id="4dd35-122">Om du har använt ett anpassat webb program (inte standard programmet, **pswa**, lägger du till `-WebApplicationName` parametern till ditt kommando och anger namnet på webb programmet.</span><span class="sxs-lookup"><span data-stu-id="4dd35-122">If you have used a custom web application (not the default application, **pswa**, add the `-WebApplicationName` parameter to your command, and specify the name of the web application.</span></span>

      `Uninstall-PswaWebApplication -WebApplicationName <web-application-name>`

   1. <span data-ttu-id="4dd35-123">Om du använder ett test certifikat lägger du till `DeleteTestCertificate` parametern i cmdleten, som du ser i följande exempel.</span><span class="sxs-lookup"><span data-stu-id="4dd35-123">If you are using a test certificate, add the `DeleteTestCertificate` parameter to the cmdlet, as shown in the following example.</span></span>

      `Uninstall-PswaWebApplication -DeleteTestCertificate`

### <a name="step-2-uninstall-windows-powershell-web-access-using-cmdlets"></a><span data-ttu-id="4dd35-124">Steg 2: Avinstallera Windows PowerShell-webbåtkomst med hjälp av cmdletar</span><span class="sxs-lookup"><span data-stu-id="4dd35-124">Step 2: Uninstall Windows PowerShell Web Access using cmdlets</span></span>

1. <span data-ttu-id="4dd35-125">Gör något av följande för att öppna en Windows PowerShell-session med utökade användarrättigheter.</span><span class="sxs-lookup"><span data-stu-id="4dd35-125">Do one of the following to open a Windows PowerShell session with elevated user rights.</span></span> <span data-ttu-id="4dd35-126">Om en session redan är öppen går du vidare till nästa steg.</span><span class="sxs-lookup"><span data-stu-id="4dd35-126">If a session is already open, go on to the next step.</span></span>

    - <span data-ttu-id="4dd35-127">På Windows-skrivbordet högerklickar du på **Windows PowerShell** i aktivitetsfältet och klickar sedan på **Kör som administratör**.</span><span class="sxs-lookup"><span data-stu-id="4dd35-127">On the Windows desktop, right-click **Windows PowerShell** on the taskbar, and then click **Run as Administrator**.</span></span>
    - <span data-ttu-id="4dd35-128">På **Start** skärmen i Windows högerklickar du på **Windows PowerShell**och klickar sedan på **Kör som administratör**.</span><span class="sxs-lookup"><span data-stu-id="4dd35-128">On the Windows **Start** screen, right-click **Windows PowerShell**, and then click **Run as Administrator**.</span></span>

1. <span data-ttu-id="4dd35-129">Skriv följande och tryck sedan på **RETUR**, där *computer_name* representerar en fjärrserver från vilken du vill ta bort Windows PowerShell-webbåtkomst.</span><span class="sxs-lookup"><span data-stu-id="4dd35-129">Type the following, and then press **Enter**, where *computer_name* represents a remote server from which you want to remove Windows PowerShell Web Access.</span></span> <span data-ttu-id="4dd35-130">`-Restart` Parametern startar automatiskt om mål servrarna om det krävs för borttagningen.</span><span class="sxs-lookup"><span data-stu-id="4dd35-130">The `-Restart` parameter automatically restarts destination servers if required by the removal.</span></span>

    `Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -Restart`

    <span data-ttu-id="4dd35-131">Om du vill ta bort roller och funktioner från en offline-VHD måste du `-ComputerName` lägga till både `-VHD` parametern och parametern.</span><span class="sxs-lookup"><span data-stu-id="4dd35-131">To remove roles and features from an offline VHD, you must add both the `-ComputerName` parameter and the `-VHD` parameter.</span></span> <span data-ttu-id="4dd35-132">Parametern `-ComputerName`, innehåller namnet på servern på vilken du vill montera VHD:n, och parametern `-VHD` innehåller sökvägen till VHD-filen på den angivna servern.</span><span class="sxs-lookup"><span data-stu-id="4dd35-132">The `-ComputerName` parameter contains the name of the server on which to mount the VHD, and the `-VHD` parameter contains the path to the VHD file on the specified server.</span></span>

    `Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -Restart`

1. <span data-ttu-id="4dd35-133">När borttagningen är klar kontrollerar du att du har tagit bort Windows PowerShell-webbåtkomsten genom att öppna sidan **alla servrar** i Serverhanteraren, välja en server som du tog bort funktionen från och sedan Visa panelen **roller och funktioner** på sidan för den valda servern.</span><span class="sxs-lookup"><span data-stu-id="4dd35-133">When removal is finished, verify that you removed Windows PowerShell Web Access by opening the **All Servers** page in Server Manager, selecting a server from which you removed the feature, and viewing the **Roles and Features** tile on the page for the selected server.</span></span>

    <span data-ttu-id="4dd35-134">`Get-WindowsFeature` Du kan också köra cmdleten som är riktad mot den valda servern (get- &lt;WindowsFeature-ComputerName *computer_name*&gt;) om du vill visa en lista över roller och funktioner som är installerade på servern.</span><span class="sxs-lookup"><span data-stu-id="4dd35-134">You can also run the `Get-WindowsFeature` cmdlet targeted at the selected server  (Get-WindowsFeature -ComputerName &lt;*computer_name*&gt;) to view a list of roles and features  that are installed on the server.</span></span>

## <a name="custom-uninstallation"></a><span data-ttu-id="4dd35-135">Anpassad avinstallation</span><span class="sxs-lookup"><span data-stu-id="4dd35-135">Custom uninstallation</span></span>

<span data-ttu-id="4dd35-136">Procedurerna i det här avsnittet hjälper dig att avinstallera både webb programmet Windows PowerShell-webbåtkomst och Windows PowerShell-webbåtkomst med hjälp av guiden ta bort roller och funktioner i Serverhanteraren och konsolen IIS-hanteraren.</span><span class="sxs-lookup"><span data-stu-id="4dd35-136">Procedures in this section help you uninstall both the Windows PowerShell Web Access web application and the Windows PowerShell Web Access feature by using the Remove Roles and Features Wizard in Server Manager, and the IIS Manager console.</span></span>

### <a name="step-1-delete-the-web-application-using-iis-manager"></a><span data-ttu-id="4dd35-137">Steg 1: ta bort webb programmet med IIS-hanteraren</span><span class="sxs-lookup"><span data-stu-id="4dd35-137">Step 1: Delete the web application using IIS Manager</span></span>

1. <span data-ttu-id="4dd35-138">Öppna konsolen IIS-hanteraren genom att göra något av följande.</span><span class="sxs-lookup"><span data-stu-id="4dd35-138">Open the IIS Manager console by doing one of the following.</span></span> <span data-ttu-id="4dd35-139">Om det redan är öppet går du vidare till nästa steg.</span><span class="sxs-lookup"><span data-stu-id="4dd35-139">If it is already open, go on to the next step.</span></span>

   - <span data-ttu-id="4dd35-140">Starta Serverhanteraren genom att klicka på Windows-skrivbordet **Serverhanteraren** i Aktivitetsfältet.</span><span class="sxs-lookup"><span data-stu-id="4dd35-140">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span> <span data-ttu-id="4dd35-141">I **verktyg** -menyn i Serverhanteraren klickar du på **Internet Information Services (IIS) Manager**.</span><span class="sxs-lookup"><span data-stu-id="4dd35-141">On the **Tools** menu in Server Manager, click **Internet Information Services (IIS) Manager**.</span></span>

   - <span data-ttu-id="4dd35-142">På **Start** skärmen i Windows skriver du valfri del av namnet **Internet Information Services (IIS) Manager**.</span><span class="sxs-lookup"><span data-stu-id="4dd35-142">On the Windows **Start** screen, type any part of the name **Internet Information Services (IIS) Manager**.</span></span> <span data-ttu-id="4dd35-143">Klicka på genvägen när den visas i **appens** resultat.</span><span class="sxs-lookup"><span data-stu-id="4dd35-143">Click the shortcut when it is displayed in the **Apps** results.</span></span>

1. <span data-ttu-id="4dd35-144">I träd fönstret i IIS-hanteraren väljer du den webbplats som kör webb programmet för Windows PowerShell-webbåtkomst.</span><span class="sxs-lookup"><span data-stu-id="4dd35-144">In the IIS Manager tree pane, select the website that is running the Windows PowerShell Web Access web application.</span></span>

1. <span data-ttu-id="4dd35-145">I rutan **åtgärder** under **Hantera webbplats**klickar du på **stoppa**.</span><span class="sxs-lookup"><span data-stu-id="4dd35-145">In the **Actions** pane, under **Manage Website**, click **Stop**.</span></span>

1. <span data-ttu-id="4dd35-146">I trädvyn högerklickar du på webb programmet på webbplatsen som kör webb programmet för Windows PowerShell-webbåtkomst och klickar sedan på **ta bort**.</span><span class="sxs-lookup"><span data-stu-id="4dd35-146">In the tree pane, right-click the web application in the website that is running the Windows PowerShell Web Access web application, and then click **Remove**.</span></span>

1. <span data-ttu-id="4dd35-147">I trädvyn väljer du **programpooler**, väljer mappen programpool för Windows PowerShell-programpool, klickar på **stoppa** i rutan **åtgärder** och klickar sedan på **ta bort** i innehålls rutan.</span><span class="sxs-lookup"><span data-stu-id="4dd35-147">In the tree pane, select **Application Pools**, select the Windows PowerShell Web Access application pool folder, click **Stop** in the **Actions** pane, and then click **Remove** in the content pane.</span></span>

1. <span data-ttu-id="4dd35-148">Stäng IIS-hanteraren.</span><span class="sxs-lookup"><span data-stu-id="4dd35-148">Close IIS Manager.</span></span>

   > [!WARNING]
   > <span data-ttu-id="4dd35-149">Certifikatet tas inte bort under avinstallationen.</span><span class="sxs-lookup"><span data-stu-id="4dd35-149">The certificate is not deleted during uninstallation.</span></span> <span data-ttu-id="4dd35-150">Om du har skapat ett självsignerat certifikat eller använt ett test certifikat och vill ta bort det, tar du bort certifikatet i IIS-hanteraren.</span><span class="sxs-lookup"><span data-stu-id="4dd35-150">If you created a self-signed certificate or used a test certificate and want to remove it, delete the certificate in IIS Manager.</span></span>

### <a name="step-2-uninstall-windows-powershell-web-access-using-the-remove-roles-and-features-wizard"></a><span data-ttu-id="4dd35-151">Steg 2: Avinstallera Windows PowerShell-webbåtkomst med hjälp av guiden ta bort roller och funktioner</span><span class="sxs-lookup"><span data-stu-id="4dd35-151">Step 2: Uninstall Windows PowerShell Web Access using the Remove Roles and Features Wizard</span></span>

1. <span data-ttu-id="4dd35-152">Gå vidare till nästa steg om Server Manager redan är öppen.</span><span class="sxs-lookup"><span data-stu-id="4dd35-152">If Server Manager is already open, go on to the next step.</span></span> <span data-ttu-id="4dd35-153">Öppna genom att göra något av följande om Server Manager inte är redan öppen.</span><span class="sxs-lookup"><span data-stu-id="4dd35-153">If Server Manager is not already open, open it by doing one of the following.</span></span>

    - <span data-ttu-id="4dd35-154">Starta Serverhanteraren genom att klicka på Windows-skrivbordet **Serverhanteraren** i Aktivitetsfältet.</span><span class="sxs-lookup"><span data-stu-id="4dd35-154">On the Windows desktop, start Server Manager by clicking **Server Manager** in the Windows taskbar.</span></span>
    - <span data-ttu-id="4dd35-155">På Windows **Start** -skärmen klickar du på **Serverhanteraren**.</span><span class="sxs-lookup"><span data-stu-id="4dd35-155">On the Windows **Start** screen, click **Server Manager**.</span></span>

1. <span data-ttu-id="4dd35-156">Klicka på **ta bort roller och funktioner**på **Hantera** -menyn.</span><span class="sxs-lookup"><span data-stu-id="4dd35-156">On the **Manage** menu, click **Remove Roles and Features**.</span></span>

1. <span data-ttu-id="4dd35-157">På sidan **Välj mål server** väljer du den server eller offline-VHD som du vill ta bort funktionen från.</span><span class="sxs-lookup"><span data-stu-id="4dd35-157">On the **Select destination server** page, select the server or offline VHD from which you want to remove the feature.</span></span> <span data-ttu-id="4dd35-158">Du kan välja en offline-VHD genom att först välja på vilken server VHD:n ska monteras och sedan välja VHD-filen.</span><span class="sxs-lookup"><span data-stu-id="4dd35-158">To select an offline VHD, first select the server on which to mount the VHD, and then select the VHD file.</span></span> <span data-ttu-id="4dd35-159">När du har valt mål servern klickar du på **Nästa**.</span><span class="sxs-lookup"><span data-stu-id="4dd35-159">After you have selected the destination server, click **Next**.</span></span>

1. <span data-ttu-id="4dd35-160">Klicka på **Nästa** igen för att hoppa till sidan **ta bort funktioner** .</span><span class="sxs-lookup"><span data-stu-id="4dd35-160">Click **Next** again to skip to the **Remove features** page.</span></span>

1. <span data-ttu-id="4dd35-161">Avmarkera kryss rutan för **Windows PowerShell-webbåtkomst**och klicka sedan på **Nästa**.</span><span class="sxs-lookup"><span data-stu-id="4dd35-161">Clear the check box for **Windows PowerShell Web Access**, and then click **Next**.</span></span>

1. <span data-ttu-id="4dd35-162">På sidan **Bekräfta borttagningsinställningarna** klickar du på **Ta bort**.</span><span class="sxs-lookup"><span data-stu-id="4dd35-162">On the **Confirm removal selections** page, click **Remove**.</span></span>

## <a name="see-also"></a><span data-ttu-id="4dd35-163">Se även</span><span class="sxs-lookup"><span data-stu-id="4dd35-163">See Also</span></span>

- [<span data-ttu-id="4dd35-164">Installera och använda Windows PowerShell-Webbåtkomst</span><span class="sxs-lookup"><span data-stu-id="4dd35-164">Install and Use Windows PowerShell Web Access</span></span>](install-and-use-windows-powershell-web-access.md)
- [<span data-ttu-id="4dd35-165">Hjälp om IIS-hanteraren 7,0</span><span class="sxs-lookup"><span data-stu-id="4dd35-165">IIS Manager 7.0 Help</span></span>](https://technet.microsoft.com/library/cc732664.aspx)