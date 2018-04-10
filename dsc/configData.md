---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: Med konfigurationsdata
ms.openlocfilehash: 19544494a547a06d87701b38585844cb11d03e33
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="using-configuration-data-in-dsc"></a><span data-ttu-id="512d6-103">Med hjälp av konfigurationsdata i DSC</span><span class="sxs-lookup"><span data-stu-id="512d6-103">Using configuration data in DSC</span></span>

><span data-ttu-id="512d6-104">Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="512d6-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="512d6-105">Med hjälp av inbyggda DSC **ConfigurationData** parameter, kan du definiera data som kan användas i en konfiguration.</span><span class="sxs-lookup"><span data-stu-id="512d6-105">By using the built-in DSC **ConfigurationData** parameter, you can define data that can be used within a configuration.</span></span>
<span data-ttu-id="512d6-106">På så sätt kan du skapa en enkel konfiguration som kan användas för flera noder eller för olika miljöer.</span><span class="sxs-lookup"><span data-stu-id="512d6-106">This allows you to create a single configuration that can be used for multiple nodes or for different environments.</span></span>
<span data-ttu-id="512d6-107">Till exempel om du utvecklar ett program, kan du använda en konfiguration för både utveckling och produktionsmiljöer och Använd konfigurationsdata för att ange data för varje miljö.</span><span class="sxs-lookup"><span data-stu-id="512d6-107">For example, if you are developing an application, you can use one configuration for both development and production environments, and use configuration data to specify data for each environment.</span></span>

<span data-ttu-id="512d6-108">Det här avsnittet beskriver strukturen för de **ConfigurationData** hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="512d6-108">This topic describes the structure of the **ConfigurationData** hashtable.</span></span>
<span data-ttu-id="512d6-109">Exempel på hur du använder konfigurationsdata finns [avgränsa konfiguration och miljö data](separatingEnvData.md).</span><span class="sxs-lookup"><span data-stu-id="512d6-109">For examples of how to use configuration data, see [Separating configuration and environment data](separatingEnvData.md).</span></span>

## <a name="the-configurationdata-common-parameter"></a><span data-ttu-id="512d6-110">Parametern ConfigurationData vanliga</span><span class="sxs-lookup"><span data-stu-id="512d6-110">The ConfigurationData common parameter</span></span>

<span data-ttu-id="512d6-111">DSC-konfigurationen tar en parameter för vanliga **ConfigurationData**, som du anger när du sammanställer konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="512d6-111">A DSC configuration takes a common parameter, **ConfigurationData**, that you specify when you compile the configuration.</span></span>
<span data-ttu-id="512d6-112">Information om kompilering konfigurationer finns [DSC-konfigurationer](configurations.md).</span><span class="sxs-lookup"><span data-stu-id="512d6-112">For information about compiling configurations, see [DSC configurations](configurations.md).</span></span>

<span data-ttu-id="512d6-113">Den **ConfigurationData** parametern är en hasthtable som måste ha minst en nyckel som heter **AllNodes**.</span><span class="sxs-lookup"><span data-stu-id="512d6-113">The **ConfigurationData** parameter is a hasthtable that must have at least one key named **AllNodes**.</span></span>
<span data-ttu-id="512d6-114">Det kan också ha en eller flera nycklar.</span><span class="sxs-lookup"><span data-stu-id="512d6-114">It can also have one or more other keys.</span></span>

><span data-ttu-id="512d6-115">**Obs:** exemplen i det här avsnittet använder en enda ytterligare nyckel (än den namngivna **AllNodes** nyckel) med namnet `NonNodeData`, men du kan innehålla valfritt antal ytterligare nycklar och ge dem vad du vill.</span><span class="sxs-lookup"><span data-stu-id="512d6-115">**Note:** The examples in this topic use a single additional key (other than the named **AllNodes** key) named `NonNodeData`, but you can include any number of additional keys, and name them whatever you want.</span></span>

```powershell
$MyData =
@{
    AllNodes = @()
    NonNodeData = ""
}
```

<span data-ttu-id="512d6-116">Värdet för den **AllNodes** nyckeln är en matris.</span><span class="sxs-lookup"><span data-stu-id="512d6-116">The value of the **AllNodes** key is an array.</span></span> <span data-ttu-id="512d6-117">Varje element i denna matris är också en hash-tabell som måste ha minst en nyckel som heter **nodnamn**:</span><span class="sxs-lookup"><span data-stu-id="512d6-117">Each element of this array is also a hash table that must have at least one key named **NodeName**:</span></span>

```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName = "VM-1"
        },


        @{
            NodeName = "VM-2"
        },


        @{
            NodeName = "VM-3"
        }
    );

    NonNodeData = ""
}
```

<span data-ttu-id="512d6-118">Du kan lägga till andra nycklar varje hash-tabellen:</span><span class="sxs-lookup"><span data-stu-id="512d6-118">You can add other keys to each hash table as well:</span></span>

```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName = "VM-1"
            Role     = "WebServer"
        },


        @{
            NodeName = "VM-2"
            Role     = "SQLServer"
        },


        @{
            NodeName = "VM-3"
            Role     = "WebServer"
        }
    );

    NonNodeData = ""
}
```

<span data-ttu-id="512d6-119">Om du vill använda en egenskap för alla noder, du kan skapa en medlem i den **AllNodes** matris som har en **NodeName** av `*`.</span><span class="sxs-lookup"><span data-stu-id="512d6-119">To apply a property to all nodes, you can create a member of the **AllNodes** array that has a **NodeName** of `*`.</span></span>
<span data-ttu-id="512d6-120">Till exempel för att ge varje nod en `LogPath` egenskap, kan du göra detta:</span><span class="sxs-lookup"><span data-stu-id="512d6-120">For example, to give every node a `LogPath` property, you could do this:</span></span>

```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName     = "*"
            LogPath      = "C:\Logs"
        },


        @{
            NodeName     = "VM-1"
            Role         = "WebServer"
            SiteContents = "C:\Site1"
            SiteName     = "Website1"
        },


        @{
            NodeName     = "VM-2"
            Role         = "SQLServer"
        },


        @{
            NodeName     = "VM-3"
            Role         = "WebServer"
            SiteContents = "C:\Site2"
            SiteName     = "Website3"
        }
    );
}
```

<span data-ttu-id="512d6-121">Detta är detsamma som att lägga till en egenskap med namnet `LogPath` med värdet `"C:\Logs"` till var och en av de andra blocken (`VM-1`, `VM-2`, och `VM-3`).</span><span class="sxs-lookup"><span data-stu-id="512d6-121">This is the equivalent of adding a property with a name of `LogPath` with a value of `"C:\Logs"` to each of the other blocks (`VM-1`, `VM-2`, and `VM-3`).</span></span>

## <a name="defining-the-configurationdata-hashtable"></a><span data-ttu-id="512d6-122">Definiera ConfigurationData hash-tabell</span><span class="sxs-lookup"><span data-stu-id="512d6-122">Defining the ConfigurationData hashtable</span></span>

<span data-ttu-id="512d6-123">Du kan definiera **ConfigurationData** antingen som en variabel inom samma skriptfilen som en konfiguration (som i våra föregående exempel) eller i en separat `.psd1` fil.</span><span class="sxs-lookup"><span data-stu-id="512d6-123">You can define **ConfigurationData** either as a variable within the same script file as a configuration (as in our previous examples) or in a separate `.psd1` file.</span></span>
<span data-ttu-id="512d6-124">Definiera **ConfigurationData** i en `.psd1` fil, skapa en fil som innehåller den hash som representerar konfigurationsdata.</span><span class="sxs-lookup"><span data-stu-id="512d6-124">To define **ConfigurationData** in a `.psd1` file, create a file that contains only the hashtable that represents the configuration data.</span></span>

<span data-ttu-id="512d6-125">Du kan till exempel skapa en fil med namnet `MyData.psd1` med följande innehåll:</span><span class="sxs-lookup"><span data-stu-id="512d6-125">For example, you could create a file named `MyData.psd1` with the following contents:</span></span>

```powershell
@{
    AllNodes =
    @(
        @{
            NodeName    = 'VM-1'
            FeatureName = 'Web-Server'
        },

        @{
            NodeName    = 'VM-2'
            FeatureName = 'Hyper-V'
        }
    )
}
```

## <a name="compiling-a-configuration-with-configuration-data"></a><span data-ttu-id="512d6-126">Kompilera en konfiguration med konfigurationsdata</span><span class="sxs-lookup"><span data-stu-id="512d6-126">Compiling a configuration with configuration data</span></span>

<span data-ttu-id="512d6-127">För att kompilera en konfiguration som du har definierat konfigurationsdata skicka konfigurationsdata som värde för den **ConfigurationData** parameter.</span><span class="sxs-lookup"><span data-stu-id="512d6-127">To compile a configuration for which you have defined configuration data, you pass the configuration data as the value of the **ConfigurationData** parameter.</span></span>

<span data-ttu-id="512d6-128">Detta skapar en MOF-fil för varje post i den **AllNodes** matris.</span><span class="sxs-lookup"><span data-stu-id="512d6-128">This will create a MOF file for each entry in the **AllNodes** array.</span></span>
<span data-ttu-id="512d6-129">Varje MOF-filen kommer att namnges med den `NodeName` egenskapen för motsvarande post i matrisen.</span><span class="sxs-lookup"><span data-stu-id="512d6-129">Each MOF file will be named with the `NodeName` property of the corresponding array entry.</span></span>

<span data-ttu-id="512d6-130">Till exempel om du definierar konfigurationsdata som i den `MyData.psd1` filen ovan, kompilera en konfiguration skulle skapa båda `VM-1.mof` och `VM-2.mof` filer.</span><span class="sxs-lookup"><span data-stu-id="512d6-130">For example, if you define configuration data as in the `MyData.psd1` file above, compiling a configuration would create both `VM-1.mof` and `VM-2.mof` files.</span></span>

### <a name="compiling-a-configuration-with-configuration-data-using-a-variable"></a><span data-ttu-id="512d6-131">Kompilera en konfiguration med konfigurationsdata med en variabel</span><span class="sxs-lookup"><span data-stu-id="512d6-131">Compiling a configuration with configuration data using a variable</span></span>

<span data-ttu-id="512d6-132">Att använda konfigurationsdata som har definierats som en variabel i samma `.ps1` filen som konfigurationen du skickar variabelnamnet som värde för den **ConfigurationData** parametern vid kompilering av konfigurationen:</span><span class="sxs-lookup"><span data-stu-id="512d6-132">To use configuration data that is defined as a variable in the same `.ps1` file as the configuration, you pass the variable name as the value of the **ConfigurationData** parameter when compiling the configuration:</span></span>

```powershell
MyDscConfiguration -ConfigurationData $MyData
```

### <a name="compiling-a-configuration-with-configuration-data-using-a-data-file"></a><span data-ttu-id="512d6-133">Kompilera en konfiguration med konfigurationsdata med hjälp av en datafil</span><span class="sxs-lookup"><span data-stu-id="512d6-133">Compiling a configuration with configuration data using a data file</span></span>

<span data-ttu-id="512d6-134">Om du vill använda konfigurationsdata som har definierats i en .psd1-fil du skickar sökvägen och namnet på filen som värde för den **ConfigurationData** parametern vid kompilering av konfigurationen:</span><span class="sxs-lookup"><span data-stu-id="512d6-134">To use configuration data that is defined in a .psd1 file, you pass the path and name of that file as the value of the **ConfigurationData** parameter when compiling the configuration:</span></span>

```powershell
MyDscConfiguration -ConfigurationData .\MyData.psd1
```

## <a name="using-configurationdata-variables-in-a-configuration"></a><span data-ttu-id="512d6-135">Använda ConfigurationData variabler i en konfiguration</span><span class="sxs-lookup"><span data-stu-id="512d6-135">Using ConfigurationData variables in a configuration</span></span>

<span data-ttu-id="512d6-136">DSC innehåller tre särskilda variabler som kan användas i ett konfigurationsskript: **$AllNodes**, **$Node**, och **$ConfigurationData**.</span><span class="sxs-lookup"><span data-stu-id="512d6-136">DSC provides three special variables that can be used in a configuration script: **$AllNodes**, **$Node**, and **$ConfigurationData**.</span></span>

- <span data-ttu-id="512d6-137">**$AllNodes** refererar till hela uppsättningen av noder som definierats i **ConfigurationData**.</span><span class="sxs-lookup"><span data-stu-id="512d6-137">**$AllNodes** refers to the entire collection of nodes defined in **ConfigurationData**.</span></span> <span data-ttu-id="512d6-138">Du kan filtrera den **AllNodes** med hjälp av **. WHERE ()** och **. ForEach()**.</span><span class="sxs-lookup"><span data-stu-id="512d6-138">You can filter the **AllNodes** collection by using **.Where()** and **.ForEach()**.</span></span>
- <span data-ttu-id="512d6-139">**Noden** refererar till en särskild post i den **AllNodes** samlingen när den har filtrerats med hjälp av **. WHERE ()** eller **. ForEach()**.</span><span class="sxs-lookup"><span data-stu-id="512d6-139">**Node** refers to a particular entry in the **AllNodes** collection after it is filtered by using **.Where()** or **.ForEach()**.</span></span>
- <span data-ttu-id="512d6-140">**ConfigurationData** refererar till hela hash-tabell som skickades som parametern vid kompilering av en konfiguration.</span><span class="sxs-lookup"><span data-stu-id="512d6-140">**ConfigurationData** refers to the entire hash table that is passed as the parameter when compiling a configuration.</span></span>

## <a name="using-non-node-data"></a><span data-ttu-id="512d6-141">Med hjälp av data-nod</span><span class="sxs-lookup"><span data-stu-id="512d6-141">Using non-node data</span></span>

<span data-ttu-id="512d6-142">Som vi har sett i föregående exempel kan den **ConfigurationData** hash-tabellen kan ha en eller flera nycklar utöver de nödvändiga **AllNodes** nyckel.</span><span class="sxs-lookup"><span data-stu-id="512d6-142">As we've seen in previous examples, the **ConfigurationData** hashtable can have one or more keys in addition to the required **AllNodes** key.</span></span>
<span data-ttu-id="512d6-143">I exemplen i det här avsnittet har vi används endast en extra nod och heter den `NonNodeData`.</span><span class="sxs-lookup"><span data-stu-id="512d6-143">In the examples in this topic, we have used only a single additional node, and named it `NonNodeData`.</span></span>
<span data-ttu-id="512d6-144">Du kan dock definiera valfritt antal ytterligare nycklar och namn som helst.</span><span class="sxs-lookup"><span data-stu-id="512d6-144">However, you can define any number of additional keys, and name them anything you want.</span></span>

<span data-ttu-id="512d6-145">Ett exempel på hur nod-data finns [avgränsa konfiguration och miljö data](separatingEnvData.md).</span><span class="sxs-lookup"><span data-stu-id="512d6-145">For an example of using non-node data, see [Separating configuration and environment data](separatingEnvData.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="512d6-146">Se även</span><span class="sxs-lookup"><span data-stu-id="512d6-146">See Also</span></span>
- [<span data-ttu-id="512d6-147">Alternativ för autentiseringsuppgifter i konfigurationsdata</span><span class="sxs-lookup"><span data-stu-id="512d6-147">Credentials Options in Configuration Data</span></span>](configDataCredentials.md)
- [<span data-ttu-id="512d6-148">DSC-konfigurationer</span><span class="sxs-lookup"><span data-stu-id="512d6-148">DSC Configurations</span></span>](configurations.md)