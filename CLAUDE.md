# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Quarto book project titled "Using ggplot2 to produce meaningful plots" by Dan MacLean. The book teaches data visualization using R's ggplot2 package, with a focus on showing data variability rather than hiding it with summary statistics.

The project has migrated from Bookdown to Quarto, though some legacy Bookdown configuration remains (_bookdown.yml).

## Project Structure

- **Content files**: `.qmd` (Quarto Markdown) files containing chapters
- **Configuration**: `_quarto.yml` - main Quarto configuration defining book structure, chapters, and output formats
- **Output**: `docs/` directory - rendered HTML and PDF outputs
- **Assets**:
  - `fig/` - figures and images used in chapters
  - `data/` - data files for examples
  - `files/` - additional supporting files
- **R environment**: Uses `renv` for package management (R 4.4.1)

## Book Structure

The book is organized into three parts:
1. **ggplot2 fundamentals** (03-ggplot2-tour.qmd)
2. **Making a data appropriate plot** (04-geoms.qmd, 05-factors_facets.qmd, 07-themes.qmd)
3. **Working reproducibly** (06-rmarkdown.qmd, 08-data-loading.qmd)

With appendices: prerequisites.qmd, r-fundamentals.qmd, acknowledgements.qmd

## Development Commands

### Render the book
```bash
quarto render
```

### Preview the book (live reload during development)
```bash
quarto preview
```

### Render specific format
```bash
quarto render --to html
quarto render --to pdf
```

### Clean build artifacts
```bash
quarto clean
```

### R package management
The project uses `renv` for reproducible R package management:
```r
# In R console
renv::restore()  # Install packages from renv.lock
renv::snapshot() # Save current package state
```

## Key Technical Details

### R Environment
- R version: 4.4.1
- Key packages: ggplot2, bookdown (0.41), rmarkdown (2.29), knitr (1.49)
- Package management: renv (0.13.2)
- The `.Rprofile` automatically activates renv on project load

### Output Configuration
- HTML output uses the "cosmo" theme
- PDF output uses "scrreprt" document class
- Both formats are generated to `docs/` directory
- HTML includes Hypothesis commenting integration
- External link to "Data Exploration and Visualisation Chatbot" in navigation

### Code Chunks
All `.qmd` files contain R code chunks with the syntax:
```
{r}
# R code here
```

Some chunks use `{r, echo=FALSE}` to hide code in output.

## Content Philosophy

The book emphasizes:
- Showing data variability rather than hiding it with bar plots
- Understanding the limitations of p-values
- Using multiple visualization types to understand data distribution
- The "grammar of graphics" approach to building plots layer by layer

## Git Workflow
- Main branch: `master`
- Untracked: `.idea/` directory (IDE configuration)