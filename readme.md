# brat

Bash-based R-adjacent tools.

A collection of bash scripts that streamline common R programming workflows.

## Quick Reference

| Command | Description |
|---------|-------------|
| `brat project <name>` | Create R project structure |
| `brat project <name> -o` | Create and open in RStudio |
| `brat rstudio [path]` | Open RStudio (alias: `rs`) |
| `brat install <pkg>` | Install from CRAN |
| `brat install -s <term>` | Search CRAN interactively |
| `brat install user/repo` | Install from GitHub |
| `brat update` | Check/install package updates |
| `brat clean` | Remove R artifacts |
| `brat tt` | Browse TidyTuesday datasets |
| `brat blog <title>` | Create Quarto blog post |

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

- `curl`, `jq`, `fzf` - required for search functionality
- `R` - required for `install`, `update`, and `tt`

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
brat project myanalysis -o    # Create and open in RStudio
```

**Options:**
- `-o, --open` - Open the project in RStudio after creation

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

### `brat rstudio [path]`

Open RStudio, optionally with a project or directory. Alias: `brat rs`

```bash
brat rstudio              # Open RStudio
brat rstudio .            # Open current directory
brat rs ~/R/myproject     # Open a specific project
```

Auto-detects `.Rproj` files in directories.

### `brat install <package>`

Install R packages from CRAN or GitHub.

```bash
brat install dplyr              # Direct CRAN install
brat install -s tidy            # Search CRAN interactively (fzf)
brat install tidyverse/ggplot2  # Install from GitHub
```

**Options:**
- `-s, --search` - Search CRAN interactively with fuzzy finder

If a package isn't found on CRAN, you'll be prompted to search for similar packages.

GitHub repositories are auto-detected by the `user/repo` format.

### `brat update`

Check for and install R package updates.

```bash
brat update           # Check and prompt to update
brat update -c        # Check only, no install prompt
```

**Options:**
- `-c, --check` - Only check for updates, don't prompt to install

Shows a table of outdated packages with version info, then prompts:
- `a` - Update all packages
- `c` - Update CRAN packages only
- `n` - Update none
- Or enter package numbers (e.g., `1 3 5` or `1,3,5`)

### `brat clean [path]`

Remove common R artifacts from a directory.

```bash
brat clean            # Clean current directory
brat clean -n         # Dry-run (show what would be deleted)
brat clean -r ~/R     # Recursive (clean all subdirectories)
brat clean -rn ~/R    # Dry-run recursive
```

**Options:**
- `-n, --dry-run` - Show what would be deleted without deleting
- `-r, --recursive` - Clean subdirectories too

**Removes:**
- `.Rhistory` - R command history
- `.RData` - Saved workspace (prompts for confirmation)
- `.Rapp.history` - R.app history (macOS)
- `.Rproj.user/` - RStudio user files
- `*_cache/` - Knitr/Quarto cache directories
- `*_files/` - Knitr/Quarto output files

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

### `brat logo`

Display the brat ASCII art logo.

```bash
brat logo
```

## Platform Support

- **macOS** - fully supported
- **Linux** - fully supported
- **WSL** - should work
- **Windows** - requires WSL or Git Bash
