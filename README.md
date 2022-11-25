[![Open in GitHub Codespaces](https://github.com/codespaces/badge.svg)](https://github.com/codespaces/new?hide_repo_select=true&ref=main&repo=TO_BE_UPDATED)

# .NET Codespaces Template

_Extend and use for your Web Development lessons in minutes._

This .NET Codespaces template provides you a normalized environment for you to build your class on. No setup time needed from you or your students, allowing you to focus on the content and lessons.

* **Who is this for?** _Educators of all levels_. 
* **How much experience do students need?** _Zero_. This template is built with basic elements complete with comments so it can be used in beginner to advanced lessons.
* **Can I use this template for other .NET applications?** _Absolutely_. This template uses ASP.NET web app and API app as examples.
* **Prerequisites:** _None_. This template will provide a working and deployable web app and API app you can immediately extend for your needs.

🤔 Curious? Watch the following video where we explain all the details:

[![Teaching .NET with Codespaces](https://img.youtube.com/vi/TO_BE_UPDATED/0.jpg)](https://youtu.be/TO_BE_UPDATED "Teaching .NET with Codespaces")

<details>
   <summary><b>🎥 Watch the video tutorial to learn more about Codespaces</b></summary>
   
   [![Codespaces Tutorial](https://img.youtube.com/vi/ozuDPmcC1io/0.jpg)](https://aka.ms/CodespacesVideoTutorial "Codespaces Tutorial")
</details>

🚀 Codespaces features:

- Repeatable cloud environment offering a push-button experience.
- Can be configured and customized.
- Integrates with your repositories on GitHub and [Visual Studio Code](https://visualstudio.microsoft.com/?WT.mc_id=dotnet-82023-juyooo).

As a teacher that means that you can create an environment, in the cloud, for your class that all students can use with zero or next to zero configuration regardless of what operating system they are using.

## 🧑‍🏫 What is GitHub Codespaces and how can I use it in my teaching?

A Codespace is a development environment that's hosted in the cloud that you can configure. The Codespaces Education benefit gives Global Campus teachers a free monthly allowance of GitHub Codespaces hours to use in [GitHub Classroom](https://classroom.github.com). Learn more [here](https://docs.github.com/education/manage-coursework-with-github-classroom/integrate-github-classroom-with-an-ide/using-github-codespaces-with-github-classroom) about Using GitHub Codespaces with GitHub Classroom.

If you are not already a Global Campus teacher, apply [here](https://education.github.com/discount_requests/pack_application) or for more information, see [Apply to GitHub Global Campus as a teacher](https://docs.github.com/education/explore-the-benefits-of-teaching-and-learning-with-github-education/github-global-campus-for-teachers/apply-to-github-global-campus-as-a-teacher).

## 🔍 What is in this template?

This template repository contains:

- `.devcontainer` settings:
  - [`Dockerfile`](.devcontainer/Dockerfile): defines the devcontainer image for GitHub Codespaces that determines the operating system and .NET version.
  - [`devcontainer.json`](.devcontainer/devcontainer.json): declares the devcontainer configuration for GitHub Codespaces including extensions and tools to be pre-installed, and workspace settings.
  - [`post-create.sh`](.devcontainer/post-create.sh): describes additional tools to be pre-installed.
- [ASP.NET web app](src/MyWebApp): A sample web app
- [ASP.NET API app](src/MyApiApp): A sample API app
- [`README`](README.md): _this file_ &ndash; describes this repository and what's in it.

## 🚀 Getting Started

1. Create a repository from this template. Use this [create repo link](../../generate). You can make the repository private or public, up to you.
1. Navigate to the main page of the newly created repository.
1. Under the repository name, use the Code drop-down menu, and in the Codespaces tab, select "Create codespace on main".

   ![Create codespace](https://docs.github.com/assets/cb-138303/images/help/codespaces/new-codespace-button.png)

1. Wait as Github initializes the codespace:

   ![Creating codespace](./images/Codespace_build.png)

## 🛠️ Customization

Customize your project for GitHub Codespaces by committing configuration files to your repository (often known as Configuration-as-Code), which creates a repeatable Codespaces configuration for all users of your project.

You can configure things like:

- Extensions, you can specify what extensions should be preinstalled.
- Dotfiles and settings.
- Operating system libraries and dependencies

> 💡 Learn more about [customization and configuration in the official documentation](https://docs.github.com/codespaces/customizing-your-codespace/personalizing-github-codespaces-for-your-account)


### Customization on `devcontainer.json`

#### Base Image

By default, this devcontainer settings uses the base image of .NET 7.0 on Ubuntu 22.04 LTS (jammy). You can change the base image to one of the followings:

- `7.0` (Debian 11)
- `7.0-bullseye-slim` (Debian 11)
- `7.0-jammy` (Ubuntu 22.04 LTS)
- `6.0` (Debian 11)
- `6.0-bullseye-slim` (Debian 11)
- `6.0-jammy` (Ubuntu 22.04 LTS)
- `6.0-focal` (Ubuntu 20.04 LTS)

```jsonc
"build": {
  "dockerfile": "./Dockerfile",
  "context": ".",
  "args": {
    "VARIANT": "7.0-jammy"
  }
}
```

#### Features

1. AWS CLI: Uncomment the section under the `features` attribute.

    ```jsonc
    "features": {
      ...
      "ghcr.io/devcontainers/features/aws-cli:1": {
        "version": "latest"
      }
      ...
    },
    ```

1. Azure CLI: Uncomment the section under the `features` attribute.

    ```jsonc
    "features": {
      ...
      "ghcr.io/devcontainers/features/azure-cli:1": {
        "version": "latest"
      }
      ...
    },
    ```

1. GitHub CLI: Uncomment the section under the `features` attribute.

    ```jsonc
    "features": {
      ...
      "ghcr.io/devcontainers/features/github-cli:1": {
        "version": "latest"
      }
      ...
    },
    ```

1. node.js: Uncomment the section under the `features` attribute. You can choose the node.js version of:

    - `latest`
    - `lts`
    - `18`
    - `16`
    - `14`

    ```jsonc
    "features": {
      ...
      "ghcr.io/devcontainers/features/node:1": {
        "version": "lts",
        "nodeGypDependencies": true,
        "nvmInstallPath": "/usr/local/share/nvm"
      }
      ...
    },
    ```

> 🔍 If you want to add more features, find [this repository: devcontainer features](https://github.com/devcontainers/features).


#### Extensions

1. There are optional extensions that you can selectively install, under the `customizations.vscode.extensions` attribute. You can simply uncomment each line to enable or comment out one to disable.

    ```jsonc
    "customizations": {
      "vscode": {
        "extensions": [
          // Recommended extensions - GitHub
          "cschleiden.vscode-github-actions",
          "GitHub.vscode-pull-request-github",
  
          // Recommended extensions - Azure
          "Azurite.azurite",
          "ms-azuretools.vscode-bicep",
          "ms-vscode.vscode-node-azure-pack",
  
          // Recommended extensions - Collaboration
          "eamodio.gitlens",
          "EditorConfig.EditorConfig",
          "MS-vsliveshare.vsliveshare-pack",
          "streetsidesoftware.code-spell-checker",
  
          // Recommended extensions - .NET
          "Fudge.auto-using",
          "jongrant.csharpsortusings",
          "kreativ-software.csharpextensions",
  
          // Recommended extensions - Markdown
          "bierner.github-markdown-preview",
          "DavidAnson.vscode-markdownlint",
          "docsmsft.docs-linting",
          "johnpapa.read-time",
          "yzhang.markdown-all-in-one",

          ...
        ],
        ...
      }
    }
    ```

> 🔍 Alternatively, you can add as many extra extensions as you like, from [Visual Studio Code Marketplace](https://marketplace.visualstudio.com/VSCode).


#### Settings

1. In `devcontainer.json`, there are customisation options for your Codespaces settings, under the `customizations.vscode.settings` attribute. You can simply uncomment each item to enable or comment out one to disable.

    ```jsonc
    "customizations": {
      "vscode": {
        "settings": {
          // Uncomment if you want to use zsh as the default shell
          "terminal.integrated.defaultProfile.linux": "zsh",
          "terminal.integrated.profiles.linux": {
            "zsh": {
              "path": "/usr/bin/zsh"
            }
          },

          // Uncomment if you want to use CaskaydiaCove Nerd Font as the default terminal font
          "terminal.integrated.fontFamily": "CaskaydiaCove Nerd Font",

          // Uncomment if you want to disable the minimap view
          "editor.minimap.enabled": false,

          // Uncomment if you want to disable the welcome page of GitLens
          "gitlens.showWelcomeOnInstall": false,
          "gitlens.showWhatsNewAfterUpgrades": false,
  
          // Uncomment if you prefer the light colour theme
          "workbench.colorTheme": "Default Light+",

          // Recommended settings for the explorer pane
          "explorer.sortOrder": "type",
          "explorer.fileNesting.enabled": true,
          "explorer.fileNesting.patterns": {
            "*.js": "${capture}.js.map",
            "*.razor": "${capture}.razor.cs,${capture}.razor.css"
          }
        }
      }
    }
    ```

> 🔍 If you want to do more granular configurations, refer to this page, [User and Workspace Settings](https://code.visualstudio.com/docs/getstarted/settings).


#### Lifecycle

1. In `devcontainer.json`, if you want to use `bash` as your main shell and want to run the shell script after the container is created:

    ```jsonc
    // Uncomment if you want to use bash in 'postCreateCommand' after the container is created
    "postCreateCommand": "/bin/bash ./.devcontainer/post-create.sh > ~/post-create.log",
    ```

1. If you want to use `zsh` as your main shell and want to run the shell script after the container is created:

    ```jsonc
    // Uncomment if you want to use zsh in 'postCreateCommand' after the container is created
    "postCreateCommand": "/usr/bin/zsh ./.devcontainer/post-create.sh > ~/post-create.log",
    ```


### Customization on `post-create.sh` ##

1. If you want to install CaskaydiaCove Nerd Font, uncomment the section below.

    ```bash
    ## CaskaydiaCove Nerd Font
    # Uncomment the below to install the CaskaydiaCove Nerd Font
    mkdir $HOME/.local
    mkdir $HOME/.local/share
    mkdir $HOME/.local/share/fonts
    wget https://github.com/ryanoasis/nerd-fonts/releases/latest/download/CascadiaCode.zip
    unzip CascadiaCode.zip -d $HOME/.local/share/fonts
    rm CascadiaCode.zip
    ```

    > Use this option if you want to use either oh-my-zsh for zsh or oh-my-posh for PowerShell.

1. If you want to install Azure CLI extensions, uncomment the section below.

    ```bash
    ## AZURE CLI EXTENSIONS ##
    # Uncomment the below to install Azure CLI extensions
    extensions=(account alias deploy-to-azure functionapp subscription webapp)
    for extension in $extensions;
    do
        az extension add --name $extension
    done
    ```

1. If you want to install Azure Bicep CLI, uncomment the section below.

    ```bash
    ## AZURE BICEP CLI ##
    # Uncomment the below to install Azure Bicep CLI
    az bicep install
    ```

1. If you want to install Azure Functions Core Tools, uncomment the section below.

    ```bash
    ## AZURE FUNCTIONS CORE TOOLS ##
    # Uncomment the below to install Azure Functions Core Tools
    npm i -g azure-functions-core-tools@4 --unsafe-perm true
    ```

1. If you want to install Azurite, uncomment the section below.

    ```bash
    ## AZURITE ##
    # Uncomment the below to install Azurite. Make sure you have installed node.js
    npm install -g azurite
    ```

1. If you want to install Azure Static Web Apps CLI, uncomment the section below.

    ```bash
    ## AZURE STATIC WEB APPS CLI ##
    # Uncomment the below to install Azure Static Web Apps CLI
    npm install -g @azure/static-web-apps-cli
    ```

1. If you want to install Azure Dev CLI, uncomment the section below.

    ```bash
    ## AZURE DEV CLI ##
    # Uncomment the below to install Azure Dev CLI
    curl -fsSL https://aka.ms/install-azd.sh | bash
    ```

    > **DEPENDENCIES**: Make sure that you must get both Azure CLI and GitHub CLI installed beforehand.

1. If you want to install plugins and themes for oh-my-zsh without using your dotfiles, uncomment the section below.

    ```bash
    ## OH-MY-ZSH PLUGINS & THEMES (POWERLEVEL10K) ##
    # Uncomment the below to install oh-my-zsh plugins and themes (powerlevel10k) without dotfiles integration
    git clone https://github.com/zsh-users/zsh-completions.git $HOME/.oh-my-zsh/custom/plugins/zsh-completions
    git clone https://github.com/zsh-users/zsh-syntax-highlighting.git $HOME/.oh-my-zsh/custom/plugins/zsh-syntax-highlighting
    git clone https://github.com/zsh-users/zsh-autosuggestions.git $HOME/.oh-my-zsh/custom/plugins/zsh-autosuggestions

    git clone https://github.com/romkatv/powerlevel10k.git $HOME/.oh-my-zsh/custom/themes/powerlevel10k --depth=1
    ln -s $HOME/.oh-my-zsh/custom/themes/powerlevel10k/powerlevel10k.zsh-theme $HOME/.oh-my-zsh/custom/themes/powerlevel10k.zsh-theme
    ```

    > **DEPENDENCIES**: Make sure that you have already installed oh-my-zsh through the settings on `devcontainer.json`.

1. If you want to install oh-my-posh for PowerShell, uncomment the section below

    ```bash
    ## OH-MY-POSH ##
    # Uncomment the below to install oh-my-posh
    sudo wget https://github.com/JanDeDobbeleer/oh-my-posh/releases/latest/download/posh-linux-amd64 -O /usr/local/bin/oh-my-posh
    sudo chmod +x /usr/local/bin/oh-my-posh
    ```

## 📚 Resources

- [GitHub Codespaces docs overview](https://docs.github.com/codespaces/overview)
- [GitHub Codespaces docs quickstart](https://docs.github.com/codespaces/getting-started/quickstart)
- [Using GitHub Codespaces with GitHub Classroom](https://docs.github.com/education/manage-coursework-with-github-classroom/integrate-github-classroom-with-an-ide/using-github-codespaces-with-github-classroom)

## 🔎 Found an issue or have an idea for improvement?

Help us make this template repository better by [letting us know and opening an issue!](/../../issues/new).
