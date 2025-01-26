# Setting up a dev container for Go
<!-- Its README.md should link back to your course notes site's tutorial. -->


* Primary author: [Cassidy Lowe](https://github.com/calowe2) 

## Today we will be learning how to set up a dev container for Go 😊

### What does this tutorial contain?

We are going to go through prerequisites needed, the steps to install, how to set up a dev container for a Go project, and finally create a Hello World project. 

### Notes: 

You will not need to install anything directly to your host machine since we are using a Dev Container. Since we are running Linux in our Dev Container, you should not expect to see a .exe file.

### What is Go? 

Go defines itself as "An open-source programming language supported by Google" and is used due to its concurrency support, simplicity, and performance. It is often used for cloud applications, web developement, and networking applications.  


#### Prerequisites for today's tutorial: 

* VSCode installed
* Docker installed **and** running
* Git installed  


### Step 1: Setting up a Git Repository

Go in your terminal and paste the following code 

``` yaml
mkdir go-project
cd go-project # (1)
```

1.   This creates a new directory for us to work in! 

Next, paste this code in. 

``` yaml
git init # (1)
```

1.   This initializes Git in this directory

Create a Readme file with the following code 

``` yaml
echo "# Go Project ReadMe" > README.md
git add README.md
git commit -m "Initial commit with README" # (1)
```

1. Now our project has a readme file!!  


### Step 2: Setting up a Remote Repository on GitHub

* Go to GitHub, sign in, and go to *create a new repository* 

* Fill in these details:

    **Repository Name:** go-project

    **Description:** "Setting up my first Go repository."

    **Visibility:** Public

* Do not initialize the repository with a README, .gitignore, or license. 

* Click create repository  


### Step 3: Add the Repo as a Remote  

* Enter this code substituting in your Github username: 

``` yaml
git remote add origin https://github.com/<your-username>/go-project.git # (1)
```

1. Now we have added our Github repo as a remote


Check your default branch name with the subcommand git branch. If it's not main, rename it to main with the following command: 

``` yaml
git branch -M main.
``` 

Push your local commits to the GitHub repository with the following code:

``` yaml
git push --set-upstream origin main # (1)
```

1. Now we have pushed out local commits to our GitHub repo  



### Step 4: Setting up a Dev Container  
1. In VS Code, open the go-project directory. You can do this via: File > Open Folder.

1. Install the Dev Containers extension for VS Code.
    
1. Create a .devcontainer directory in the root of your project with the following file inside of this "hidden" configuration directory:

**.devcontainer/devcontainer.json**

Add the following code to your devcontainer.json file:

``` yaml
{
	"name": "Go Project",
	"image": "mcr.microsoft.com/devcontainers/go:latest",
	"customizations": {
        "vscode": {
        "settings": {
        "go.useLanguageServer": true
    },
    "extensions": [
      "golang.go"
    ]
  }
}
}
```  


### Step 5: Reopen the Dev Container

Reopen the project in the container by pressing Ctrl+Shift+P (or Cmd+Shift+P on Mac), typing "Dev Containers: Reopen in Container," and selecting the option.  


### Step 6: Try it Out by Adding a Hello World Example

Enter the following code in the terminal in order to initialize a go.mod file which is needed for all Go projects. 

``` yaml
go mod init example.com/go-project
```

Enter the following code in the terminal to create an empty file called main where we will create our Hello World project. We use nano here so we can immediately edit the file upon creation.

``` yaml
touch main.go
```

Paste in the following code in your new main.go file to create our Hello World project 

``` yaml
package main

import "fmt"

func main() {
    fmt.Println("Hello COMP423!")}
```

Save the file by pressing Ctrl+S!  


### Step 7: Compile and Run Your Project 

Run the following code to compile and run your project!

``` yaml
go run main.go
```

You should see "Hello COMP423!" printed!  

### Step 8: Let's Save Our Work!

Enter the following code in your terminal to commit

``` yaml
git add .
git commit -m "Hello Comp423!"
```

**Note**: If you get the following error

fatal: detected dubious ownership in repository at '/workspaces/go-project'
To add an exception for this directory, call:

        git config --global --add safe.directory /workspaces/go-project

Run the code as it says 

``` yaml
git config --global --add safe.directory /workspaces/go-project
```

Then add and commit as stated above ^

Finally, run

``` yaml
git push origin main # (1)
```

1. Now our Github has all of our work!


#### Congrats! You have set up a project in the Go programming language! 