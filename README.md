# teeba-obaid.github.io

## About This Website

This is my personal Quarto website.

I use it to share blog posts and data analysis projects using Python and R.

My computational posts include:

- Exploring Beach Width Changes Over Time, using Python.
- Exploring Penguin Measurements in R, using R.

Both posts include executable code, generated results, visualizations, and explanations.

## Website Structure

- `index.qmd` is the home page.
- `about.qmd` is the About page.
- `blog.qmd` is the blog page.
- `posts/` contains my blog posts.
- `_quarto.yml` contains the website settings.
- `docs/` contains the rendered website files.
- `README.md` contains instructions for working on the website.

### Software I Used

I used:

- Git for version control.
- Quarto to build the website.
- Positron to edit files and run code.
- Python and R for data analysis.
- `uv` to manage the Python environment.
- `renv` to manage the R environment.

## Setting Up My Python Environment

I opened a Terminal in my website's main directory.

I initialized the Python project:

```bash
uv init --bare
```

I pinned Python 3.14:

```bash
uv python pin 3.14
```

I added Jupyter and the Python kernel:

```bash
uv add jupyter ipykernel
```

I installed pandas for data manipulation:

```bash
uv add pandas
```

I installed Altair for visualization:

```bash
uv add altair
```

The Python dependencies are recorded in `pyproject.toml` and `uv.lock`.

## Creating My Python Post

I created a folder for the beach analysis:

```bash
mkdir posts/beach-width-analysis
```

In Positron, I created:

```text
posts/beach-width-analysis/index.qmd
```

I added the title, author, date, and categories at the top of the file.

I then wrote the introduction, data source, Python code chunks, explanations, and conclusion.

### Data Source

I used beach survey data from Narrabeen Beach in Australia.

The dataset was provided in DSCI 511 Worksheet 7.

Original data source:

http://narrabeen.wrl.unsw.edu.au

The post reads the local file:

```text
posts/beach-width-analysis/beach_data.csv
```

### Python Analysis

I used pandas to:

1. Read the beach data.
2. Resample the measurements to monthly intervals.
3. Calculate the average measurement at each beach location.
4. Subtract each location's average from its monthly measurements.
5. Reshape the results for visualization.

I used Altair to create a heatmap.

The heatmap shows how the monthly measurements compare with the average at each of the five beach locations.

## Setting Up My R Environment

I used `renv` to manage the R packages for this website.

In the R Console for my website project, I initialized the environment:

```r
renv::init()
```

I installed the penguins dataset package:

```r
renv::install("palmerpenguins")
```

I checked that the package and dataset worked:

```r
library(palmerpenguins)

head(penguins)
```

After completing the R post, I recorded the installed packages:

```r
renv::snapshot()
```

This updated `renv.lock`.

## Managing Files with Git

I updated `.gitignore` to exclude temporary files and locally installed packages.

```gitignore
/.quarto/
**/*.quarto_ipynb
.venv/
renv/library/
renv/staging/
```

This keeps the repository smaller and avoids uploading my local Python and R package installations.

## Creating My R Post

I created a folder for the penguin analysis:

```bash
mkdir posts/penguins-factor-analysis
```

In Positron, I created:

```text
posts/penguins-factor-analysis/index.qmd
```

I added the title, author, date, and categories at the top of the file.

I then wrote the introduction, data source, R code chunks, explanations, and conclusion.

### Data Source

I used the `penguins` dataset from the `palmerpenguins` R package.

I previously worked with this dataset in DSCI 523 R Programming.

Package and dataset information:

https://allisonhorst.github.io/palmerpenguins/

### R Analysis

I loaded the packages and displayed the first six rows:

```r
library(palmerpenguins)
library(ggplot2)
library(dplyr)

head(penguins)
```

I grouped the penguins by species and calculated their average bill length and body mass.

I created a scatter plot comparing bill length and body mass across the three species.

I then used `forcats::fct_relevel()` to change the order of the species in the plot legend.

This let me compare the original plot with the reordered plot.

## Reproducing My Website

These instructions explain how to rebuild the website from a fresh clone.

### Step 1: Clone the Repository

Open a Terminal and run:

```bash
git clone https://github.com/Teeba-Obaid/teeba-obaid.github.io.git
```

Move into the website directory:

```bash
cd teeba-obaid.github.io
```

### Step 2: Restore the Python Environment

Run:

```bash
uv sync
```

This installs the Python dependencies recorded in the project files.

There is no need to initialize a new Python project.

### Step 3: Restore the R Environment

Open R in the website's main directory.

Run:

```r
renv::restore()
```

This installs the R packages recorded in `renv.lock`.

There is no need to initialize a new R environment.

### Step 4: Render the Website

From the website's main directory, run:

```bash
uv run quarto render
```

This renders the website, including the Python and R posts.

The rendered files are saved in `docs/`.

## Previewing My Website

To check changes locally, I run:

```bash
quarto preview
```

This opens a local preview of the website.

## Publishing Updates

After editing the website, I save my files and check that the website renders successfully.

I check the repository status:

```bash
git status
```

I stage the intended changes:

```bash
git add .
```

I commit the changes:

```bash
git commit -m "Add Python and R analysis posts"
```

I push the changes to GitHub:

```bash
git push origin main
```

I then check the public website to confirm that the updates appear correctly.

## Public Website

https://teeba-obaid.github.io/