# Pre-configured workspace for LaTeX projects
This repository contains customized blank project for development pdf documentation in LaTeX format.
The project is configured for the [devcontainer](https://code.visualstudio.com/docs/devcontainers/containers) environment, so there is no need to install any local dependencies.

## Features
- No need to install locally LaTeX and other dependencies
- Automatically conversion **plantUML diagrams** from the text description to the resulting pdf document (command `\RenderPlantUML`)
- Importing and inserting vector images from **drawio** format (command `\RenderDrawio`)
- The ability to add a **watermark** to the entire document
- **Examples** of frequently used constructs in documentation (tables, item lists and so on)
- Configured **CI/CD** (Github Actions) for pdf document assembly

## Project structure
Main LaTeX source file located in the root folder: `main.tex`.

Title page description: `title.tex`.

External *plantUML* and *.drawio* files are located in a folder: `/diagrams`.

Folder *Chapters* contains the chapters of the document in the LaTeX language.

## Requirements
- [Docker](https://www.docker.com/get-started/) no older than v.23
- Microsoft VS Code (recommended)

## First launch
- Clone the repository
- In VS Code, open the downloaded folder and select the option 'Reopen in container' in a pop-up window

## Compiling the documentation

### VS Code pre-assigned tasks
Some pre-assigned tasks are configured to build resulting pdf document using MS VS Code. To use it press ```Ctrl + Shift + B``` then select apropriate target.

The following tasks are available to run:
1. ```Build pdf``` - This will start resulting pdf document build. 
2. ```Full clean build pdf``` - This will remove all intermidiate created files during builds before and start document build (executed twice, so the table of contents will be generated correctly).
3. ```Clear LaTeX cache and temporary files``` - This will clean temporary LaTeX files.

### Manual building
In any other case, there is a possibility to build resulting pdf document manually.
You can run local builder to compile LaTex source to .pdf file. To do so just open project in dev-container and when you want to build, run in container terminal:

```bash
xvfb-run lualatex --shell-escape main.tex
```

To cleanup temp files use:
```bash
latexmk -c
```

*Note:* in order for the table of contents to be generated correctly, you must run build command twice. 