# Devcontainer for Python Control System Development

This repository contains the configuration for a development container tailored for Python control system development. The container is based on Ubuntu 22.04 LTS and includes essential tools and libraries for control system analysis and design.

## Table of Contents

- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
- [Libraries](#libraries)
- [VS Code IDE](#vs-code-ide)
- [License](#license)

## Features

- **Base Image**: Ubuntu 22.04 LTS with Python 3.12.
- **Python Libraries**: `slycot`, `control`, `harold`, and `jupyterlab`.
- **Development Tools**: `git`, `cmake`, `ninja-build`, `zsh`, `oh-my-zsh`, and `powerline fonts`.
- **User Setup**: A `vscode` user with sudo privileges and zsh as the default shell.
- **JupyterLab**: Ready to use JupyterLab environment with port 8888 exposed.

## Installation

To build and use this development container, you need Docker and Visual Studio Code with the Remote - Containers extension installed.

1. **Clone the repository**:

    ```bash
    git clone https://github.com/jamestjat/Py_Control.git
    cd Py_Control
    ```

2. **Build and run the container**:

    Open the repository in Visual Studio Code. When prompted to open the repository in a container, click "Reopen in Container". Alternatively, you can use the command palette (`Ctrl+Shift+P`) and select `Remote-Containers: Reopen in Container`.

## Usage

Once the container is running, you can start developing your Python control system projects. The container is preconfigured with the necessary tools and libraries. You can access the terminal with zsh and start JupyterLab by running:

```bash
jupyter lab --ip=0.0.0.0 --no-browser --allow-root
```

You can access JupyterLab in your browser at `http://localhost:8888`.

## Libraries

This devcontainer includes the following Python libraries:

- **[control](https://github.com/python-control/python-control)**: A Python library for system and control theory.
- **[harold](https://github.com/ilayn/harold)**: A library for control system analysis and design.
- **[slycot](https://github.com/python-control/Slycot)**: A Python wrapper for the SLICOT control and systems library.

## VS Code IDE

The development container is configured to enhance your development experience with Visual Studio Code. Here are some features and settings:

- **Extensions**: The container automatically installs the Python and Jupyter extensions.
- **Terminal**: The default terminal is set to zsh with Oh My Zsh and Powerline fonts for an improved user experience.
- **Settings**: Custom settings for the integrated terminal to use zsh.

### Using Visual Studio Code

1. **Open Terminal**: You can open the integrated terminal in VS Code by pressing `` ` ``, or from the menu: `Terminal > New Terminal`.
2. **Python Development**: The Python extension provides features such as IntelliSense, code navigation, linting, and debugging.
3. **Jupyter Notebooks**: You can open and edit Jupyter notebooks directly within VS Code. Use the Jupyter extension to run and manage your notebooks.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.
