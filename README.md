# Bash project manager
It will be similar to [prm project](https://github.com/eivind88/prm)

### What it does?

- helps you manage your projects and switch between them
- runs specific tasks releted to the project in isolated enviornment

### How does it work?

- stores information:

File structure and extension is yet to be defined.
Options to evaluate (yml, json, sh)

in `~/.<project_manager>/projects/<project_name>/`

    - start
    - stop
    - tasks

in `~/.<project_manager>/templates/`

    - contains templates for new projects
    - when `<project_manager> start --tempaltes=osx,python,django` is run it will lookup folder for mapped templates and load them

### usage

    $ <project_manager>
    if within pwd there is .project_manager.cfg then 
        it start it
    else 
        asks to create new project in that directory
        
    $ <project_manager> <commend>

<commend> corelates to | reaction
--- | ---
nothing | asks what to add under this **name** (project, task, cancel)
`create <name> --templates=osx,python` | creates project under **name** using templates
project [name] | turns on project
project [name] [task] | turns on project and executes **task**
list | list all projects
list --task|templates | list all tasks|templates within projects 
edit taskname | helps you edit task
remove | removes project / task
rename \<old> \<new> | renames command
stop | executes stop.sh and comes back to directory before activating project
config | shows config
config -e | edits config

### Examples

we are **adding** first project

    $ <project_manager> my_project
    do you want to create [p]roject or [c]ancel
    p
    
    opens start in editor
    > we are adding

        cd ~/my_project/
        source ./env/bin/activate

    save
    
    opens stop in editor
    > we are adding

        deactivate

    save
    
    Second execution will know that this is project folder and will ask 
    [my_project] $ <project_manager> new-task
    do you want to create [t]ask or [c]ancel
    t

we are **turning on** our project
> commands from /project_name/start are executed

    $ <project_manager> my_project -v
    cd ~/my_project/
    source ./env/bin/activate
    [my_project](env)$ 

we are working on project...

and finally our work is done

we are **turning off** our project
> commands from /project_name/stop are executed and we are coming back to directory before turning on project

    [my_project](env)$ <project_manager> stop -v
    deactivate
    $

we are **executing** task within project
    
    [my_project](env)$ <project_manager> task-name -v # it will pass all params towards task

