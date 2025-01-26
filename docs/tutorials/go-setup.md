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
mkdir goproject
cd goproject # (1)
```

1.   This creates a new directory for us to work in! 

Next, paste this code in. 

``` yaml
git init # (1)
```

1.   This initializes Git in this directory

Create a Readme File 

``` yaml
echo "# Go Project ReadMe" > README.md
git add README.md
git commit -m "Initial commit with README" # (1)
```

1. Now our project has a readme file!! 


### Step 2: Setting up a Remote Repository on GitHub

* Go to GitHub, sign in, and go to *create a new repository* 

* Fill in these details:

    Repository Name: go-project-wahoo

    Description: "Setting up my first Go repository."

    Visibility: Public

* Do not initialize the repository with a README, .gitignore, or license. 

* Click create repository 


### Step 3: Add the repo as a remote 

* Copy in this code, substituting in your Github username into the code: 

``` yaml
echo "# Go Project ReadMe" > README.md
git add README.md
git commit -m "Initial commit with README" # (1)
```

1. Now we have added our Github repo as a remote


Check your default branch name with the subcommand git branch. If it's not main, rename it to main with the following command: git branch -M main. 

Push your local commits to the GitHub repository with the following code:

``` yaml
git push --set-upstream origin main # (1)
```

1. Now we have 


#### Step 4: Setting up a Dev Container
1. In VS Code, open the go-project-wahoo directory. You can do this via: File > Open Folder.

1. Install the Dev Containers extension for VS Code.
    
1. Create a .devcontainer directory in the root of your project with the following file inside of this "hidden" configuration directory:

**.devcontainer/devcontainer.json**

Add the following code to your devcontainer.json file:

``` yaml
{
  "name": "Go Development Environment",                      // this is possibly wrong...?
  "image": "mcr.microsoft.com/devcontainers/go:1.19", 
  "settings": {
    "go.gopath": "/workspace/go",
    "go.useLanguageServer": true
  },
  "extensions": [
    "golang.go" 
  ],
  "postCreateCommand": "go mod init example.com/go-project-wahoo || true",
  "remoteUser": "vscode",
  "workspaceFolder": "/workspace"
}
```


#### Step 3: Reopen the Dev Container

Reopen the project in the container by pressing Ctrl+Shift+P (or Cmd+Shift+P on Mac), typing "Dev Containers: Reopen in Container," and selecting the option. 


#### Step 4: Try it Out - Add a Hello World Example

Enter pwd into your terminal within the dev container. If your current working directory is not go-project-wahoo, copy this code into your terminal to get inside the project.

``` yaml
cd /workspaces/go-project-wahoo
```

Enter the following code in order to initialize a go.mod file which is needed for all Go projects. 

``` yaml
go mod init example.com/go-project-wahoo
```

Enter the following code to create an empty file called main where we will create our Hello World project. We use nano here so we can immediately edit the file upon creation.

``` yaml
nano main.go
```

Paste in the following code to create our Hello World project 

``` yaml
package main

import "fmt"

func main() {
    fmt.Println("Hello COMP423!")}
```

Save the file by pressing Ctrl+S!


#### Step 5: Compile and Run Your Project 

Run the following code to compile and run your project!

``` yaml
go run main.go
```

You should see "Hello COMP423!" printed!

#### Congrats! You have set up a project in the Go programming language! 




Trying things out...
run this code 

``` py 
import tensorflow as tf
```

``` yaml
theme:
  features:
    - content.code.annotate # (1)
```

1.   I'm a code annotation! I can contain `code`, __formatted
    text__, images, ... basically anything that can be written in Markdown.


``` py linenums="1"
def bubble_sort(items):
    for i in range(len(items)):
        for j in range(len(items) - 1 - i):
            if items[j] > items[j + 1]:
                items[j], items[j + 1] = items[j + 1], items[j]
```

``` py hl_lines="2 3"
def bubble_sort(items):
    for i in range(len(items)):
        for j in range(len(items) - 1 - i):
            if items[j] > items[j + 1]:
                items[j], items[j + 1] = items[j + 1], items[j]
```

