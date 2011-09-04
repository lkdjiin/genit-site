NAME
---------------
create - Create a project

SYNOPSIS
---------------
**genit create** [options] _project_

DESCRIPTION
---------------
**create** create the project root folder, named _project_, adding any needed files
and subfolders, and perfoms basic initialization.

OPTIONS
---------------
**-d, --doctype** _DOCTYPE_  
By default, the doctype of a Genit project is HTML5. You can specify another doctype.
_DOCTYPE_ could be one of:

* `xhtml_1.0_strict`
* `xhtml_1.0_transitional`
* `html_5`

**-e, --empty**  
By default, Genit create a smoke test with each new project. This option create a project
without the smoke test.

BUGS
---------------
None.

SEE ALSO
---------------
None.
