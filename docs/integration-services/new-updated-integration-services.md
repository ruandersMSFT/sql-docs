---
title: Updated - Integration Services for SQL Server docs | Microsoft Docs
description: Display snippets of updated content for recently changed in documentation, for Integration Services for Microsoft SQL Server.
services: na
documentationcenter: ''
author: MightyPen
manager: jhubbard
editor: ''
ms.service: na
ms.topic: updart-autogen
ms.technology: database-engine
ms.custom: UpdArt.exe
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: updart-autogen
ms.date: 12/02/2017
ms.author: genemi
ms.workload: integration-services
---
# New and Recently Updated: Integration Services for SQL Server



Nearly every day Microsoft updates some of its existing articles on its [Docs.Microsoft.com](http://docs.microsoft.com/) documentation website. This article displays excerpts from recently updated articles. Links to new articles might also be listed.

This article is generated by a program that is rerun periodically. Occasionally an excerpt can appear with imperfect formatting, or as markdown from the source article. Images are never displayed here.

Recent updates are reported for the following date range and subject:



- *Date range of updates:* &nbsp; **2017-09-28** &nbsp; -to- &nbsp; **2017-12-02**
- *Subject area:* &nbsp; **Integration Services for SQL Server**.




&nbsp;

## New Articles Created Recently

The following links jump to new articles that have been added recently.


1. [Store and retrieve files on file shares on premises and in Azure with SSIS](lift-shift/ssis-azure-files-file-shares.md)
2. [Validate SSIS packages deployed to Azure](lift-shift/ssis-azure-validate-packages.md)



&nbsp;

## Updated Articles with Excerpts

This section displays the excerpts of updates gathered from articles that have recently experienced a large update.

The excerpts displayed here appear separated from their proper semantic context. Also, sometimes an excerpt is separated from important markdown syntax that surrounds it in the actual article. Therefore these excerpts are for general guidance only. The excerpts only enable you to know whether your interests warrant taking the time to click and visit the actual article.

For these and other reasons, do not copy code from these excerpts, and do not take as exact truth any text excerpt. Instead, visit the actual article.





&nbsp;

<a name="compactupdatedlist"/>

### Compact List of Articles Updated Recently

This compact list provides links to all the updated articles that are listed in the Excerpts section.

1. [Hadoop Connection Manager](#TitleNum_1)
2. [Connect to on-premises data sources and Azure file shares with Windows Authentication](#TitleNum_2)




&nbsp;

&nbsp;

<a name="TitleNum_1"/>

### 1. &nbsp; [Hadoop Connection Manager](connection-manager/hadoop-connection-manager.md)

*Updated: 2017-11-28* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Next](#TitleNum_2))

<!-- Source markdown line 65.  ms.author= "douglasl".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 2d68f4e884304f1a28045b42b680c15cc6a41ec5 fb2429466ea4d545682975d8dbea47451ce98ec7  (PR=4113  ,  Filename=hadoop-connection-manager.md  ,  Dirpath=docs\integration-services\connection-manager\  ,  MergeCommitSha40=28cccac53767db70763e5e705b8cc59a83c77317) -->



**Connect with Kerberos authentication**

There are two options to set up the on-premises environment so you can use Kerberos Authentication with the Hadoop Connection Manager. You can choose the option that better fits your circumstances.
-   Option 1: [Join the SSIS computer to the Kerberos realm--#kerberos-join-realm)
-   Option 2: [Enable mutual trust between the Windows domain and the Kerberos realm--#kerberos-mutual-trust)

**<a name="kerberos-join-realm"></a>Option 1: Join the SSIS computer to the Kerberos realm**


**Requirements:**


-   The gateway computer needs to join the Kerberos realm and can't join any Windows domain.

**How to configure:**


**On the SSIS computer:**

1.	Run the **Ksetup** utility to configure the Kerberos KDC server and realm.

    The computer must be configured as a member of a workgroup since a Kerberos realm is different from a Windows domain. Set the Kerberos realm and add a KDC server as shown in the following example. Replace *REALM.COM* with your own respective realm as needed.

```
    C:> Ksetup /setdomain REALM.COM`
    C:> Ksetup /addkdc REALM.COM <your_kdc_server_address>
```

	Restart the computer after executing these two commands.

2.	Verify the configuration with **Ksetup** command. The output should look like the following sample:

```
    C:> Ksetup
    default realm = REALM.COM (external)
    REALM.com:
        kdc = <your_kdc_server_address>
```

**<a name="kerberos-mutual-trust"></a>Option 2: Enable mutual trust between the Windows domain and the Kerberos realm**


**Requirements:**

-   The gateway computer must join a Windows domain.
-   You need permission to update the domain controller's settings.

**How to configure:**


> [!NOTE]
> Replace REALM.COM and AD.COM in the following tutorial with your own respective realm and domain controller as needed.



&nbsp;

&nbsp;

---

<a name="TitleNum_2"/>

### 2. &nbsp; [Connect to on-premises data sources and Azure file shares with Windows Authentication](lift-shift/ssis-azure-connect-with-windows-auth.md)

*Updated: 2017-11-27* &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  ([Previous](#TitleNum_1))

<!-- Source markdown line 66.  ms.author= "douglasl".  -->

&nbsp;


<!-- git diff --ignore-all-space --unified=0 673386fca53cb60b983e0cb3cd4b9e2ee1dee0de 65458b4dceb92d01184c5e9c6f68ec0e8f16ba08  (PR=4104  ,  Filename=ssis-azure-connect-with-windows-auth.md  ,  Dirpath=docs\integration-services\lift-shift\  ,  MergeCommitSha40=19e1c4067142d33e8485cb903a7a9beb7d894015) -->



**Connect to an on-premises SQL Server**

To check whether you can connect to an on-premises SQL Server, do the following things:

1.  To run this test, find a non-domain-joined computer.

2.  On the non-domain-joined computer, run the following command to start SQL Server Management Studio (SSMS) with the domain credentials that you want to use:

```
    runas.exe /netonly /user:<domain>\<username> SSMS.exe
```

3.  From SSMS, check whether you can connect to the on-premises SQL Server that you want to use.

**Connect to an on-premises file share**

To check whether you can connect to an on-premises file share, do the following things:

1.  To run this test, find a non-domain-joined computer.

2.  On the non-domain-joined computer, run the following command. This command opens a command prompt window with the domain credentials that you want to use, and then tests connectivity to the file share by getting a directory listing.

```
    runas.exe /netonly /user:<domain>\<username> cmd.exe
    dir \\fileshare
```

3.  Check whether the directory listing is returned for the on-premises file share that you want to use.

**Connect to a file share on an Azure VM**

To connect to a file share on an Azure virtual machine, do the following things:

1.  With SQL Server Management Studio (SSMS) or another tool, connect to the SQL Database that hosts the SSIS Catalog database (SSISDB).

2.  With SSISDB as the current database, open a query window.

3.  Run the `catalog.set_execution_credential` stored procedure as described in the following options:

```
    catalog.set_execution_credential @domain = N'.', @user = N'username of local account on Azure virtual machine', @password = N'password'
```

**Connect to a file share in Azure Files**

For more info about Azure Files, see [Azure Files](https://azure.microsoft.com/services/storage/files/).







## Similar Articles

<!--  HOW TO:
    Refresh this file's line items with the latest 'Count-in-Similars*' content.
    Then run Run-533-*.BAT
    2017-12-02  23:00pm
-->

This section lists very similar articles for recently updated articles in other subject areas, within our public GitHub.com repository: [MicrosoftDocs/sql-docs](https://github.com/MicrosoftDocs/sql-docs/).

#### Subject areas which do have new or recently updated articles

- [New + Updated (3+14): **Advanced Analytics for SQL** docs](../advanced-analytics/new-updated-advanced-analytics.md)
- [New + Updated (1+0):  **Analysis Services for SQL** docs](../analysis-services/new-updated-analysis-services.md)
- [New + Updated (87+0): **Analytics Platform System for SQL** docs](../analytics-platform-system/new-updated-analytics-platform-system.md)
- [New + Updated (5+4):  **Connect to SQL** docs](../connect/new-updated-connect.md)
- [New + Updated (0+1):  **Database Engine for SQL** docs](../database-engine/new-updated-database-engine.md)
- [New + Updated (2+2):  **Integration Services for SQL** docs](../integration-services/new-updated-integration-services.md)
- [New + Updated (10+9): **Linux for SQL** docs](../linux/new-updated-linux.md)
- [New + Updated (2+4):  **Relational Databases for SQL** docs](../relational-databases/new-updated-relational-databases.md)
- [New + Updated (4+2):  **Reporting Services for SQL** docs](../reporting-services/new-updated-reporting-services.md)
- [New + Updated (0+1):  **Samples for SQL** docs](../sample/new-updated-sample.md)
- [New + Updated (21+0): **SQL Operations Studio** docs](../sql-operations-studio/new-updated-sql-operations-studio.md)
- [New + Updated (5+1):  **Microsoft SQL Server** docs](../sql-server/new-updated-sql-server.md)
- [New + Updated (0+1):  **SQL Server Data Tools (SSDT)** docs](../ssdt/new-updated-ssdt.md)
- [New + Updated (1+0):  **SQL Server Migration Assistant (SSMA)** docs](../ssma/new-updated-ssma.md)
- [New + Updated (0+1):  **SQL Server Management Studio (SSMS)** docs](../ssms/new-updated-ssms.md)
- [New + Updated (0+2):  **Transact-SQL** docs](../t-sql/new-updated-t-sql.md)

#### Subject areas which have no new or recently updated articles

- [New + Updated (0+0): **Data Migration Assistant (DMA) for SQL** docs](../dma/new-updated-dma.md)
- [New + Updated (0+0): **ActiveX Data Objects (ADO) for SQL** docs](../ado/new-updated-ado.md)
- [New + Updated (0+0): **Data Quality Services for SQL** docs](../data-quality-services/new-updated-data-quality-services.md)
- [New + Updated (0+0): **Data Mining Extensions (DMX) for SQL** docs](../dmx/new-updated-dmx.md)
- [New + Updated (0+0): **Master Data Services (MDS) for SQL** docs](../master-data-services/new-updated-master-data-services.md)
- [New + Updated (0+0): **Multidimensional Expressions (MDX) for SQL** docs](../mdx/new-updated-mdx.md)
- [New + Updated (0+0): **ODBC (Open Database Connectivity) for SQL** docs](../odbc/new-updated-odbc.md)
- [New + Updated (0+0): **PowerShell for SQL** docs](../powershell/new-updated-powershell.md)
- [New + Updated (0+0): **Tools for SQL** docs](../tools/new-updated-tools.md)
- [New + Updated (0+0): **XQuery for SQL** docs](../xquery/new-updated-xquery.md)


