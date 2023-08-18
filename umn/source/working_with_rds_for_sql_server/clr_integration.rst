:original_name: rds_11_0003.html

.. _rds_11_0003:

CLR Integration
===============

Scenarios
---------

The common language runtime (CLR) is the core of Microsoft .NET Framework and provides the execution environment for all .NET Framework code. Code that runs within the CLR is referred to as managed code. The CLR provides various functions and services required for program execution, including just-in-time (JIT) compilation, allocating and managing memory, enforcing type safety, exception handling, thread management, and security.

SQL CLR is a new function of SQL Server 2005. It injects the CLR service of .NET Framework into SQL Server, so that some database objects of SQL Server can be developed using the .NET Framework programming language (currently, only VB.NET and C# are supported). These database objects include stored procedures, triggers, user-defined functions, user-defined types, and user-defined aggregates. To execute the CLR code, you need to enable CLR integration first.

For more information about CLR integration, see `Common Language Runtime (CLR) Integration Programming Concepts <https://docs.microsoft.com/en-us/sql/relational-databases/clr-integration/common-language-runtime-clr-integration-programming-concepts?view=sql-server-2014>`__.

For more information about CLR integration security, see `CLR Integration Security <https://docs.microsoft.com/en-us/sql/relational-databases/clr-integration/security/clr-integration-security?view=sql-server-2014>`__.

Prerequisites
-------------

RDS for SQL Server can deploy SAFE assemblies only.

Enabling CLR
------------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a region and a project.

#. Click **Service List**. Under **Database**, click **Relational Database Service**. The RDS console is displayed.

#. On the **Instances** page, click the target DB instance.

#. In the navigation pane on the left, choose **Parameters**. On the displayed page, enter **clr enabled** and **clr strict security** in the search box in the upper right corner.

   .. note::

      -  **clr enabled** determines whether the CLR integration is enabled.
      -  **clr strict security** is a specific parameter to SQL Server 2017. This option controls the interpretation of the SAFE, EXTERNAL ACCESS, and UNSAFE permissions in SQL Server. The value **1** causes the DB engine to ignore the PERMISSION_SET information on the assemblies, and always interprets them as UNSAFE. For more information, see `CLR strict security <https://docs.microsoft.com/en-us/sql/database-engine/configure-windows/clr-strict-security?view=sql-server-2017>`__ at the Microsoft site.

#. Set the **clr enabled** value.

   Set **clr enabled** to **1** and click **Save**. In the displayed dialog box, click **Yes** to enable the CLR function.

   .. note::

      -  **clr enabled**: The value **1** indicates that the CLR function is enabled. The value **0** indicates that the CLR function is disabled.
      -  **clr strict security**: The default value is **1** and no configuration is required. For SQL Server 2017 DB instances, only **clr enabled** needs to be set to enable the CLR function.

#. On the **Change History** tab, check that the value of **clr enabled** has been changed to **1**.

Creating a SAFE CLR Assembly
----------------------------

The following factors should be considered when you design assemblies:

-  Packaging assemblies
-  Management assembly security
-  Restrictions on assemblies

For more information, see `Designing Assemblies <https://docs.microsoft.com/en-us/sql/relational-databases/clr-integration/assemblies-designing?view=sql-server-2014>`__.

Example: Creating a C# CLR Assembly
-----------------------------------

Microsoft SQL Server provides assemblies to make database operations simple and convenient.

.. note::

   When you restore data to a new or an existing DB instance, the **clr enabled** parameter is disabled by default. To use the CLR integration function, you need to enable **clr enabled** first.

Procedure
---------

#. Create a C# function to compile an SQL Server DLL.


   .. figure:: /_static/images/en-us_image_0000001166636984.png
      :alt: **Figure 1** C# function code

      **Figure 1** C# function code

   .. important::

      For more information about user-defined functions, see `CLR User-Defined Functions <https://docs.microsoft.com/en-us/sql/relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions?view=sql-server-2014>`__.

#. Use SQL Server Management Studio to connect to the database.


   .. figure:: /_static/images/en-us_image_0000001166795540.png
      :alt: **Figure 2** Connecting to the server

      **Figure 2** Connecting to the server

#. Select the target database and create the corresponding assembly.

   .. note::

      -  Only the SAFE assembly (**Permission** set is **Safe**) can be created.
      -  The DLL file is saved in the hexadecimal format, as shown in :ref:`Figure 4 <rds_11_0003__fig92191121274>`.


   .. figure:: /_static/images/en-us_image_0000001166955488.png
      :alt: **Figure 3** Creating an assembly

      **Figure 3** Creating an assembly

   .. _rds_11_0003__fig92191121274:

   .. figure:: /_static/images/en-us_image_0000001166795538.png
      :alt: **Figure 4** DLL file

      **Figure 4** DLL file

#. Execute the program. If the execution result is shown as :ref:`Figure 5 <rds_11_0003__fig1780316197333>`, the execution is successful. The TESTS assembly is added, as shown in :ref:`Figure 6 <rds_11_0003__fig17182124911387>`.

   .. _rds_11_0003__fig1780316197333:

   .. figure:: /_static/images/en-us_image_0000001212196859.png
      :alt: **Figure 5** Execution result

      **Figure 5** Execution result

   .. _rds_11_0003__fig17182124911387:

   .. figure:: /_static/images/en-us_image_0000001212196861.png
      :alt: **Figure 6** TESTS assembly

      **Figure 6** TESTS assembly

.. |image1| image:: /_static/images/en-us_image_0000001166476958.png
