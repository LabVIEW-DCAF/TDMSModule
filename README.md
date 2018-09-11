# Overview

This module contains a collection libraries and class implementations which provide a plugin for TDMS datalogging in the Distributed Control and Automation Framework (DCAF).

# Description

The TDMS Logging module may be used to write DCAF tag data to a TDMS file on local disk. Logging provides a useful mechanism to track critical system tags that may be used in monitoring of established applications, commissioning and certification of new deployments, system recovery, and troubleshooting.

For evaluation of saved tag values, descriptive information such as the tag name and datatype are also saved. The [TDMS file format](http://www.ni.com/white-paper/3727/en/) provides a format that supports storage of data properties and streaming of data from multiple tags. The TDMS Logging module consolidates writes to disk and uses the [LabVIEW Advanced TDMS VIs and Functions](http://zone.ni.com/reference/en-XX/help/371361P-01/glang/tdms_advanced_functions/) for optimal efficiency when writing TDMS log files.

![image001.png](https://ni.i.lithium.com/t5/image/serverpage/image-id/207413iED37EFD50CE9E83F/image-size/large?v=1.0&px=999 "image001.png")

The TDMS Logging module implements a file management strategy using three user configurable rules:

1. Generate a new log file when the current log is greater than or equal to **Maximum file size (kB)**

2. Archive log files up to **Maximum number of archived files to keep** in a configurable directory.

3. Delete log files with a *last modified* date older than **Maximum age of files (days)**

Note: Archived logs are rotated such that the newest log has the lowest index (for example, “MyLog.1.tdms” is newer (more recent) than “MyLog.2.tdms”).

Note: TDMS Logging module does not automatically archive existing log files. If a log file in the logging directory has the same name as the configured log **file name**, the existing file will be overwritten without warning.

# Configuration of the TDMS Logging Module

Using the DCAF Configuration Editor, you can add the TDMS Logging module to an engine by right-clicking the engine and selecting Add>>Utilities>>TDMS datalogger. The module automatically detects available tags:

![image003.png](https://ni.i.lithium.com/t5/image/serverpage/image-id/207414i449C8F9A6DC941A6/image-size/large?v=1.0&px=999 "image003.png")

Select the tags you want to log:

![image005.png](https://ni.i.lithium.com/t5/image/serverpage/image-id/207415iAA91F9DEF85ADB82/image-size/large?v=1.0&px=999 "image005.png")

Then, set datalogger configuration parameters:

 ![image007.png](https://ni.i.lithium.com/t5/image/serverpage/image-id/207416i236BF2560B91DD94/image-size/large?v=1.0&px=999 "image007.png")

By changing the scans per write and queue size you can balance the write-to-disk and memory performance of the TDMS Logging module.

Configure your data archival strategy in the ‘Log Rotation’ tab.

![image009.png](https://ni.i.lithium.com/t5/image/serverpage/image-id/207417iE01756F9A0CAF62F/image-size/large?v=1.0&px=999 "image009.png")

Dynamic mappings can also be configured to log tags with names that match patterns specified in the ‘Dynamic Configuration’ tab. Use the syntax of the LabVIEW Match Pattern function to find matching tags when the module initializes at runtime.

![image011.png](https://ni.i.lithium.com/t5/image/serverpage/image-id/207418iBF0CE32B586E5CA3/image-size/large?v=1.0&px=999 "image011.png")

Remember to save your configuration.

# Using the TDMS Logging Module

The TDMS Logging Module does not read the TDMS log files, so it is likely that this module will be used with other code or utilities to evaluate and post process saved tag data. Archived logs and the active log can be viewed at any time, but National Instruments does not recommend moving, editing, or deleting these files while your application is running; instead, copy files to an independent storage location before making edits.

For LabVIEW users, the TDMS File Viewer (found in the palettes at Functions>>Programming>>File I/O>>TDM Streaming>>TDMS File Viewer) can be used to quickly load and view the contents of any TDMS file. You can also write custom VIs to monitor the active log or manage archived logs, and NI LabVIEW DataFinder Toolkit users can create custom data management applications.

DIAdem also provides comprehensive data management and measurement analysis, and built-in DataFinder features may be used to find relevant data.

Use the [TDM Excel Add-In for Microsoft Excel](http://www.ni.com/example/27944/en/) to view TDMS files in Microsoft Excel.

Additionally, numerous other utilities for viewing and processing TDMS files are available on the [LabVIEW Tools Network](http://www.ni.com/labview-tools-network/).

# Software Requirements

+ LabVIEW 2014 or later
