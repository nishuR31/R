# R Installation and Execution Guide

## Table of Contents
1. [Install R](#1-install-r)
2. [Install RStudio (Optional IDE)](#2-install-rstudio-optional-ide)
3. [Install Packages](#3-install-packages)
4. [Running R Files](#4-running-r-files)
5. [Troubleshooting](#5-troubleshooting)
6. [Next Steps](#6-next-steps)

---

## 1. Install R

### Windows
1. Download installer from [CRAN](https://cran.r-project.org/bin/windows/base/)
2. Run `.exe` file (use default settings)
3. Add to PATH during installation

### macOS
1. Download `.pkg` from [CRAN](https://cran.r-project.org/bin/macosx/)
2. Follow installation wizard
3. Verify in Terminal:
```bash
R --version
```

### Linux (Debian/Ubuntu)
```bash
sudo apt-get update
sudo apt-get install r-base r-base-dev
```

### Verify Installation
Open terminal/command prompt:
```bash
R --version
# Should show something like: "R version 4.3.1 (2023-06-16)"
```

---

## 2. Install RStudio (Optional IDE)
1. Download from [posit.co/download](https://posit.co/download/rstudio-desktop/)
2. Install using default settings
3. Launch RStudio (auto-detects R installation)

### Alternative: VS Code Setup
1. Install [VS Code](https://code.visualstudio.com/)
2. Add these extensions:
   - **R** (by Yuki Ueda)
   - **R Debugger**
3. Configure R path in settings (Ctrl+,):
   ```json
   "r.rpath.windows": "C:\\Program Files\\R\\R-4.3.1\\bin\\R.exe",
   "r.rpath.mac": "/usr/local/bin/R",
   "r.rpath.linux": "/usr/bin/R"
   ```

---

## 3. Install Packages
### Basic Package Installation
```r
# Install from CRAN
install.packages("dplyr")

# Install multiple packages
install.packages(c("ggplot2", "tidyr"))

# Install from GitHub
install.packages("devtools")
devtools::install_github("tidyverse/dplyr")
```

### Verify Packages
```r
library(dplyr)
packageVersion("dplyr")  # Should return version number
```

---

## 4. Running R Files

### Method 1: RStudio
1. Open `.R` file in RStudio
2. Run entire script: **Ctrl+Shift+S**
3. Run line-by-line: **Ctrl+Enter**

### Method 2: Command Line
```bash
# Execute script
Rscript path/to/your_file.R

# Run with arguments
Rscript script.R arg1 arg2

# Interactive mode
R
> source("your_file.R")
```

### Method 3: VS Code
1. Open `.R` file
2. Use these shortcuts:
   - Run line/selection: **Ctrl+Enter**
   - Run entire file: **Ctrl+Shift+S**
   - Debugging: **F5**

### Method 4: Terminal (Mac/Linux)
```bash
# Make script executable
chmod +x script.R

# Add shebang line (first line in script)
#!/usr/bin/env Rscript

# Execute directly
./script.R
```

---

## 5. Troubleshooting

| Issue                          | Solution                               |
|--------------------------------|----------------------------------------|
| `R command not found`          | Add R to system PATH                   |
| Package installation errors    | Run R as admin/use `sudo R` (Linux)    |
| Script permissions denied      | `chmod +x file.R` (Linux/Mac)          |
| Encoding issues                | Add `# encoding: UTF-8` at file top    |
| Missing dependencies           | Install required system libraries      |

---

## 6. Next Steps
1. Explore built-in datasets: `data()`
2. Learn basic syntax: `?Syntax`
3. Practice with R Markdown: `install.packages("rmarkdown")`
4. Explore Tidyverse packages: [tidyverse.org](https://www.tidyverse.org/)

To use this guide:
1. Save as `README.md`
2. Add project-specific examples to Section 4
3. Customize troubleshooting for your environment
