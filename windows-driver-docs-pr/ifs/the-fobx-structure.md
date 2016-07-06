---
title: The FOBX Structure
author: windows-driver-content
description: The FOBX Structure
ms.assetid: 95177b38-4ca5-49ed-9f9d-bafedd156044
keywords: ["reference counts WDK RDBSS", "FOBX structure", "FILE_OBJECT structure", "counting references WDK RDBSS", "backpointers WDK RDBSS", "data structures WDK file systems", "RDBSS WDK file systems , connection and file structures", "Redirected Drive Buffering Subsystem WDK file systems , connection and file structures", "connection structures WDK RDBSS", "file structures WDK RDBSS", "structures WDK RDBSS", "connection information WDK RDBSS"]
---

# The FOBX Structure


## <span id="ddk_the_fobx_structure_if"></span><span id="DDK_THE_FOBX_STRUCTURE_IF"></span>


A file object extension (FOBX) structure is an RDBSS extension to the [**FILE\_OBJECT**](https://msdn.microsoft.com/library/windows/hardware/ff545834) structure. The FOBX structure is pointed to by the **FileObjectExtension** field in the file object. An FOBX structure contains the following:

-   A signature and reference count

-   A backpointer to the associated FCB structure

-   A backpointer to the associated SRV\_OPEN structure

-   Context information about this open structure

-   Additional storage requested by the network mini-redirector or the creator of the FOBX structure

The FOBX structure contains all of the information that is needed, per file object, which is not normally stored by the I/O system. Information about file objects is stored by the I/O system in fixed-size file system objects. The FOBX structure handles the other information needed on file objects by network mini-redirectors.

The FOBX structure for any file object is referenced by the **FsContext2** field in the file object. Even though the FOBX structure is ordinarily a terminus in the RDBSS structure, the FOBX structure is currently reference counted anyway.

The FOBX flags are split into two groups:

-   Flags visible to network mini-redirectors

-   Flags used internally by RDBSS and invisible to network mini-redirectors

The flags visible to network mini-redirectors consist of the lower 16 bits of the possible FOBX flags. The upper 16 bits are reserved for use internally by RDBSS.

 

 


--------------------
[Send comments about this topic to Microsoft](mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20[ifsk\ifsk]:%20The%20FOBX%20Structure%20%20RELEASE:%20%285/9/2016%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "Send comments about this topic to Microsoft")

