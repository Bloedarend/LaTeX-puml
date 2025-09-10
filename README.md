# LaTeX-puml
A LaTeX package that allows for including PlantUML files as images into TEX files.

## Prerequisites
The following software must be installed:
- Java (https://www.java.com/)
- PlantUML (https://plantuml.com/)
- Graphviz (https://graphviz.org/download/)

Verify installation by running these commands:
```bash
java -version # Ensure Java is installed.
plantuml -V # Ensure PlantUML is installed.
dot -V # Ensure Graphviz is installed.
plantuml -testdot # Ensure PlantUML can generate images with Graphviz.
```

This package is tested with TeX Live 2025.
In theory, any LaTeX distribution from [here](https://www.latex-project.org/get/) should work, but if you do not have one installed yet, we recommend installing TeX Live.

## Installation

### Manual Installation
1. Locate your personal TeX tree. If you are using TeX Live, you can find the path by running:
    ```bash
    kpsewhich -var-value=TEXMFHOME
    ```

    If you are using another TeX distribution, you may need to use their respective methods to locate the TeX tree.
2. Move the `puml` directory from this repository to your local TeX tree.
3. Refresh the TeX database by running:
    ```bash
    texhash
    ```

    If you are using another TeX distribution, you may need to use their respective methods to refresh the TeX database.
4. Verify installation by running:
    ```bash
    kpsewhich puml.sty
    ```

    If the path to `puml.sty` is printed, the installation was successful.
    For other distributions, you will have to use their respective methods to verify the installation.

### Installation with LTXE.
1. Clone the LaTeX Environment repository from [here](https://github.com/Bloedarend/LaTeX-Environment).
2. Add the `puml` directory from this repository to the `pkg` directory of the LaTeX Environment repository.
3. Run the following command inside the LaTeX Environment repository to update the packages.
    ```bash
    ./ltxe.sh u
    ```

## Usage
Use the package in your LaTeX document by adding the following line to your preamble:
```latex
\usepackage{puml}
```

Then to include a PlantUML diagram into your figure, use the `\includepuml` command. For example:
```latex
\begin{figure}[H]
    \includepuml[width=0.8\textwidth]{diagram}
    \caption{PlantUML Diagram}
    \label{fig:plantuml}
\end{figure}
```

The `\includepuml` command accepts all optional arguments supported by the `\includegraphics` command.
The required argument is the path to the PlantUML file.
The file extension must be either `.puml` or `.plantuml`.
If no extension is provided, it will look for a file with those extensions in that order.

> **NOTE:** Make sure to enable shell escape (`-shell-escape`) when compiling your LaTeX document. This is necessary for the package to generate the PlantUML diagrams.
