# brat

Bash-based R-adjacent tools.

A collection of bash scripts that streamline common R programming workflows.

## Installation

```bash
git clone https://github.com/yourusername/brat.git
cd brat
./setup
```

The setup script will:
- Check for required dependencies
- Make scripts executable
- Add brat to your PATH

### Dependencies

- `curl`, `jq`, `fzf` - required for all commands
- `R` - required for `install` and `tt`

Install on macOS:
```bash
brew install curl jq fzf
```

Install on Linux/WSL:
```bash
sudo apt install curl jq fzf r-base
```

## Commands

### `brat project <name>`

Create a new R project with standard directory structure.

```bash
brat project myanalysis
```

Creates:
```
myanalysis/
├── data-raw/
├── data/
├── ref/
├── output/
├── script.R
└── myanalysis.Rproj
```

### `brat install <package>`

Search CRAN for packages and install interactively with `fzf`.

```bash
brat install dplyr
```

Shows package details (version, author, dependencies) in the preview pane.

### `brat tt`

Browse TidyTuesday datasets by year and generate starter scripts.

```bash
brat tt
```

Navigate with `p`/`n` to change years, select a dataset to create a pre-populated R script.

### `brat blog <title>`

Create a Quarto blog post template with frontmatter.

```bash
brat blog "My First Post"
```

Creates a subdirectory with `index.qmd` ready for writing.

## Platform Support

- **macOS** - fully supported
- **Linux** - fully supported
- **WSL** - should work
- **Windows** - requires WSL or Git Bash
