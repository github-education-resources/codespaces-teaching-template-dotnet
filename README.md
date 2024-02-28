[![Open in GitHub Codespaces](https://github.com/codespaces/badge.svg)](https://github.com/codespaces/new?hide_repo_select=true&ref=main&repo=TO_BE_UPDATED)

# .NET Codespaces Template

_Extend and use for your Web Development lessons in minutes._

This .NET Codespaces template provides you a normalized environment for you to build your class on. No setup time needed from you or your students, allowing you to focus on the content and lessons.

- **Who is this for?** _Educators of all levels_.
- **How much experience do students need?** _Zero_. This template is built with basic elements complete with comments so it can be used in beginner to advanced lessons.
- **Can I use this template for other .NET applications?** _Absolutely_. This template uses ASP.NET web app and API app as examples.
- **Prerequisites:** _None_. This template will provide a working and deployable web app and API app you can immediately extend for your needs.

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

   ![Creating codespace](./images/codespaces-initializing.png)

## 🛠️ Customization

Customize your project for GitHub Codespaces by committing configuration files to your repository (often known as Configuration-as-Code), which creates a repeatable Codespaces configuration for all users of your project.

You can configure things like:

- Extensions, you can specify what extensions should be preinstalled.
- Dotfiles and settings.
- Operating system libraries and dependencies

> 💡 Learn more about [customization and configuration in the official documentation](https://docs.github.com/codespaces/customizing-your-codespace/personalizing-github-codespaces-for-your-account)

### Customization on `devcontainer.json`

#### Base Image

By default, this devcontainer settings uses the base image of **.NET 7.0 on Debian 11** by default. You can change the base image to [one in the list](https://hub.docker.com/_/microsoft-dotnet-sdk/).

```jsonc
"build": {
  "dockerfile": "./Dockerfile",
  "context": ".",
  "args": {
    "VARIANT": "7.0"
  }
}
```

#### Features

1. **Azure CLI**: Uncomment the section under the `features` attribute.

    ```jsonc
    "features": {
      ...
      "ghcr.io/devcontainers/features/azure-cli:1": {
        "version": "latest"
      }
      ...
    },
    ```

1. **GitHub CLI**: Uncomment the section under the `features` attribute.

    ```jsonc
    "features": {
      ...
      "ghcr.io/devcontainers/features/github-cli:1": {
        "version": "latest"
      }
      ...
    },
    ```

1. **node.js**: Uncomment the section under the `features` attribute. The latest LTS version of node.js is chosen by default.

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

1. There are optional extensions pre-installed under the `customizations.vscode.extensions` attribute.

    ```jsonc
    "customizations": {
      "vscode": {
        "extensions": [
          "GitHub.copilot",
          "GitHub.copilot-chat",
          "ms-dotnettools.csdevkit",
          "ms-vscode.PowerShell",
          "ms-vscode.vscode-node-azure-pack",
          "VisualStudioExptTeam.vscodeintellicode"
        ],
        ...
      }
    }
    ```

> 🔍 Alternatively, you can add as many extra extensions as you like, from [Visual Studio Code Marketplace](https://marketplace.visualstudio.com/VSCode).

### Customization on `on-create.sh` ##

You can pre-install any tool through `on-create.sh`, which the devcontainer features don't natively support yet. eg) PowerShell.

1. If you want to install oh-my-posh for PowerShell, uncomment the section below

    ```bash
    ## OH-MY-POSH ##
    # Uncomment the below to install oh-my-posh
    sudo wget https://github.com/JanDeDobbeleer/oh-my-posh/releases/latest/download/posh-linux-amd64 -O /usr/local/bin/oh-my-posh
    sudo chmod +x /usr/local/bin/oh-my-posh
    ```

> 🔍 There are more customization scenarios in [`on-create.sh`](./.devcontainer/on-create.sh), if you like to follow.

## 📚 Resources

- [GitHub Codespaces docs overview](https://docs.github.com/codespaces/overview)
- [GitHub Codespaces docs quickstart](https://docs.github.com/codespaces/getting-started/quickstart)
- [Using GitHub Codespaces with GitHub Classroom](https://docs.github.com/education/manage-coursework-with-github-classroom/integrate-github-classroom-with-an-ide/using-github-codespaces-with-github-classroom)

## 🔎 Found an issue or have an idea for improvement?

Help us make this template repository better by [letting us know and opening an issue!](/../../issues/new).
