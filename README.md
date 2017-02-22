# bash project manager
> extending prm (in examples prm is placeholder for program final name)

### what it does

- prepers your terminal for work on specific project
- accomplishes tasks from specific projects in correct environment

### how it does it

- turns on prm/start.(sh/ py)
- stores information about projects in prm/project_name/
    - start
    - stop
    - tasks
    - aliases
- provides templates for creating projects based on template(s)
- shows information about current project in prompt

### usage

    $ prm
    
activates manager (adding /.../prm to .bashrc might be a good idea)

    $ prm input

found corelation with | reaction
--- | ---
nothing | asks what to add under this **name** (project, task, alias, cancel)
create \<name> [\*args] | creates project under **name** as instance of template(s) **[args]**
projekt name [\*args] | turns on project or executes **project task (args[0]) [\*args[1:]]**
list [type] [-from] | lists all possible commands based on **type** (project (shows a/m time), task, alias), **-from** adds where command was added (project, template)
help | shows this table
edit [\*args] [-r] | helps you edit command, if found **-r** edits in source of command (if comes from template)
remove | removes command
rename \<old> \<new> | renames command
stop | executes cleaning tasks and stops active project
config | edits config
aliases | edits names found in left side of this table (adding, changing or removing alias)

we are **adding** first project

    $ prm my_project
    do you want to create [P]roject, [T]ask, [A]lias or [C]ancel
    P

opens start in editor
> we are adding

    cd ~/my_project/
    source ./env/bin/activate

save

opens stop in editor
> we are adding

    deactivate

save

we are **turning on** our project
> commands from /project_name/start are executed

    $ prm my_project
    cd ~/my_project/
    source ./env/bin/activate
    [my_project](env)$ 

