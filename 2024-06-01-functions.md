<h1>Functions</H1>
* A function allows shortcuts to be created to condense tedious set of commands into a callable object
 
<h2>Examples</h2>
* There are numerous things that functions can be used for i'll be going over a few examples

  ```bash
  # Create a function which automatically prepends all files with the current date and appends with .md

  function file_create () {
    vi $(date '+%Y-%m-%d')-${1}.md
  }
  
  # Function which passes messages to Git Commit

  function gc () {  
    git commit -m "${1}"
  }

  ```

<h2>Persisting Functions</h2>
* Issues when creating `functions` is they are not persistent once the terminal is closed, they require you to recreate them
* A solution to this is to save these `functions` in a `shell rc` file
  - Each shell has what is known as an `rc` file which contains saved commands that will be run every time the terminal boots up
  - In this case since we are using `bash` you will be creating a `~/.bashrc` file
    * The `rc` file always exists in your home directory and will always be a hidden file prepended with `.` 
* Example:
  
  ```bash
  touch ~/.bashrc # Creating a bashrc file sicne this is being run in a bash terminal
  vi ~/.bashrc # vi into file
   
  # .bashrc
  # add functions 
  function file_create () {
    vi $(date '+%Y-%m-%d')-${1}.md
  }

  # Function which passes messages to Git Commit

  function gc () {
    git commit -m "${1}"
  }
  # save file

  source ~/.bashrc # sourcing file to pick up any new changes, only need to run once per change
