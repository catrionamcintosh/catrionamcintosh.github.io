# catrionamcintosh.github.io

A small Quarto personal blog with two posts analyzing the Gapminder dataset, one in R and one in Python.

### What to install

| Tool   | Version in this Repos  | Get it from |
|--------|----------------|-------------|
| Quarto | `1.10.18`      | <https://quarto.org/docs/get-started/> |
| uv     | `0.12.5`      | <https://docs.astral.sh/uv/getting-started/installation/> |
| R      | `4.6.1`      | <https://cran.r-project.org/> |
| Git    | any recent     | <https://git-scm.com/> |

You don't need to install Python yourself. uv downloads the version this
project pins (Python `3.14`) the first time you run `uv sync`.
 
You don't need to install renv or any R packages yourself either. renv
installs itself the first time R starts in this folder, then installs the
package versions recorded in `renv.lock`.

### How to build

Run these commands in order

Inside a bash **shell**:

Clone the repository and move into it:

```bash
git clone git@github.com:catrionamcintosh/catrionamcintosh.github.io.git
cd catrionamcintosh.github.io
```

Install the Python packages from `uv.lock` into `.venv/`.

```bash
uv sync
```

**R:**  Start R from the top level of
the repository (the folder with `renv.lock` in it), so that `.Rprofile` turns
renv on: 

```bash
R
```

Then, in the R console:
 
```r
renv::restore()
q()
```

Answer `y` if renv asks whether to proceed. Answer `n` when `q()` asks whether
to save the workspace.

Back inside the **Shell** from the top level of the repository, render the whole site:

```bash
uv run quarto render
```

### Open the site

The rendered site is written to `docs/`. Open the homepage in the browser:

From the **Shell**:

```bash
open docs/index.html        # macOS
start docs/index.html       # Windows
```

Or serve it with:

```bash
uv run quarto preview
```

## Data Used

Both blog posts the Gapminder dataset rom [Gapminder](https://www.gapminder.org/data/),
free to use under the CC-BY 4.0 licence.
 
No data files are committed, and **rendering does not need the network**. The
data ships inside those packages. You only need a network connection for
`uv sync` and `renv::restore()`, which download the packages. Once they have
run, `uv run quarto render` works offline.

