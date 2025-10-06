# LaTeX Document Template for Technical Reports and Theses

This project provides a flexible and modern LaTeX template designed for creating professional technical documents and project deliverables. It is built upon the `abntex2` class and customized into a new `freelance-doc` class, offering a clean structure, modern aesthetics, and ease of use.

## Key Features

* **Modular Structure**: The document is organized into separate files for pre-textual elements, chapters, and post-textual content, making it easy to manage large projects.
* **Custom Class (`freelance-doc.cls`)**: Centralizes all styling and custom commands, separating the document's appearance from its content.
* **Professional Cover and Title Pages**: Includes commands (`\imprimircapalogo`, `\imprimirfolhaderosto`) for generating stylized cover and title pages with support for logos and client information.
* **Styled Executive Summary**: The summary (`Resumo`) is automatically formatted into a modern-looking box using `tcolorbox`.
* **Advanced Code Listings**: Comes pre-configured with the `minted` package for syntax-highlighted code blocks, which requires Python's Pygments library.
* **Makefile for Easy Cleanup**: A `Makefile` is included with a `clean` command to remove all temporary LaTeX auxiliary files from the project directory and subdirectories[cite: 48, 51, 52, 53, 54].
* **Customizable Table of Contents**: The TOC is styled with a distinct color for chapter entries and consistent indentation for sections and subsections.
* **Bibliography Management**: Supports bibliography management with `abntex2cite`, allowing for both numeric and author-date citation styles.

---

## File Structure

The project is organized into logical directories to keep the content manageable:

.
├── Makefile
├── freelance-doc.cls
├── main.tex
├── references.bib
├── pretextual_elements.tex
├── imgs/
│   ├── cover-top.png
│   ├── cover-bottom.png
│   └── closing-image.png
├── chapters/
│   ├── 01_introduction.tex
│   ├── 02_related_work.tex
│   ├── 03_methodology.tex
│   ├── 04_development.tex
│   └── ...
└── posttextual/
├── appendix_a.tex
└── attachment_a.tex


* **`main.tex`**: The root file that assembles the entire document. Project metadata (title, author, client) is configured here.
* **`freelance-doc.cls`**: The custom class file that defines the document's layout and style.
* **`chapters/`**: Contains the individual `.tex` files for each chapter of the document.
* **`pretextual_elements.tex`**: Includes the executive summary and other pre-textual sections.
* **`posttextual/`**: Holds appendices and attachments.
* **`references.bib`**: The BibTeX file for managing all bibliographic references.
* **`Makefile`**: A utility script to help clean the project directory.

---

## Prerequisites

1.  **LaTeX Distribution**: A full LaTeX installation such as TeX Live, MiKTeX, or MacTeX.
2.  **Python and Pygments**: The `minted` package requires Python and the Pygments library for syntax highlighting. You can install Pygments using pip:
    ```sh
    pip install Pygments
    ```

## How to Use

1.  **Configure Your Document**: Open `main.tex` and fill in your project's information under the `DOCUMENT INFORMATION` section:
    ```latex
    \titulo{Your Project Title}
    \autor{Your Full Name}
    \cliente{Client Name}
    \local{City, State}
    \data{\the\year}
    ```
2.  **Add Your Content**:
    * Write your chapters in the respective files inside the `chapters/` directory (e.g., `01_introduction.tex`, `02_related_work.tex`).
    * Edit `pretextual_elements.tex` to write your executive summary
    * Add your bibliographic entries to the `references.bib` file.
3.  **Compile the Document**: Because `minted` is used for code highlighting, you must compile with the `-shell-escape` flag enabled. The recommended tool is `latexmk`, which automates the multiple compilation passes needed for the table of contents, citations, and references.
    ```sh
    latexmk -pdf -shell-escape main.tex
    ```
4.  **Clean Up Auxiliary Files**: After compilation, you can remove all temporary files by running:
    ```sh
    make clean
    ```
    This command is defined as a phony rule in the Makefile.

---

## Customization

### Citation Style

The template defaults to a numeric citation style (`abnt-num`). To switch to an author-date style, change the `abntex2cite` package import in `main.tex`:

```latex
% From:
\usepackage[num]{abntex2cite}
% To:
\usepackage[alf]{abntex2cite}
```

### Colors and Fonts

The hyperlink color and summary box colors are defined in freelance-doc.cls. You can modify the \definecolor commands to match your desired branding.

### Document Sections

You can easily add or remove chapters, appendices, or attachments by adding or commenting out the 

\include{} commands in main.tex