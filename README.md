# bash project manager
> extending prm (in examples prm is placeholder for program's final name)

### what it does

- prepers your terminal for work on specific project
- accomplishes tasks from specific projects in correct environment

### how it does it

- stores information about projects in ~/.prm/projects/project_name/
    - start
    - stop
    - tasks
    - aliases
- provides templates for creating projects based on template(s) that are stored in ~/.prm/templates/
- shows information about current project in prompt

### usage

    $ prm
    
activates manager (adding /.../prm to .bashrc might be a good idea)

    $ prm input

input corelates to | reaction
--- | ---
nothing | asks what to add under this **name** (project, task, alias, cancel)
create \<name> [\*args] | creates project under **name** as instance of template(s) **[args]**
project [name] [\*args] | turns on project or executes **project task name [\*args]**
list [type] [-from] | lists all possible commands based on **type** (project (shows a/m time), task, alias), **-from** adds where command was added (project, template)
help | shows this table
edit [\*args] [-r] | helps you edit command, if found **-r** edits in source of command (eg. if comes from template)
remove | removes command
rename \<old> \<new> | renames command
stop | executes cleaning tasks, stops active project and comes back to directory before turning on project
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

we are working on project...

and finally our work is done

we are **turning off** our project
> commands from /project_name/stop are executed and we are coming back to directory before turning on project

    [my_project](env)$ prm stop
    deactivate
    $

let's say we created **task** for deploying changes under name of deploy and can take as parameter -n for dry-run
we turn it like that:

    $ prm project_name deploy -n

it executes project_name/start
then **task** with parameter -n
then executes project_name/stop

