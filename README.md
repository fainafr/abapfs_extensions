# ABAPFS extensions
Allow updates on systems older than 7.51 with [visual studio code ABAP remote filesystem extension](https://github.com/marcellourbani/vscode_abap_remote_fs) and 
[NPM ADT API](https://github.com/marcellourbani/abap-adt-api)
## Installation

Import in your dev system with [ABAPGIT](https://github.com/larshp/abapGit)

## Technical details
The ABAP developement tools require ABAP objects to be locked before they can be updated. This requires stateful sessions
Eclipse works over RFC, which is stateful by default

Visual studio code works over HTTP, and needs to manage the stateful session flag.
This is handled fine in my 7.51 developer edition, but not in older systems. This enhancement implements the same mechanism in older systems

There is no need to install this in systems which handle the sessions already, but it won't cause issue if imported. It will simply (re)set the flag twice

In my 7.51 system this is done by SAP in method CONFIGURE_SESSION_STATE of class CL_ADT_WB_RES_APP, in my other systems (including a 7.50 PL5 one) it doesn't exist.
