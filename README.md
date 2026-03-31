# 📊 R Learning Roadmap

> **Who this is for:** Someone who knows programming (JavaScript) and wants to learn R for data analysis, statistics, and visualization. R is not a general-purpose language — it's a statistician's language, and that's exactly what makes it powerful.

---

## What Makes R Different

R was built by statisticians, for statisticians. Unlike Python, which does statistics *among other things*, R's entire design is oriented around data. This means:

- Vectors are the basic unit (not single values)
- Data frames are built-in (not imported)
- Plotting is a first-class feature
- Statistical functions exist that simply don't have direct equivalents elsewhere

If Python is a Swiss Army knife, R is a surgeon's scalpel for data.

---

## Phase 1 — Get Set Up and Learn the Fundamentals (Week 1–2)

**Goal:** Install R and RStudio, understand R's data model, and write basic programs.

### Setup
1. Install [R](https://cran.r-project.org/) first
2. Then install [RStudio](https://posit.co/download/rstudio-desktop/) — this is the IDE everyone uses

### 📖 Official / Core Docs
- [R Documentation](https://www.rdocumentation.org/) — searchable reference for every function
- [R for Data Science (free book)](https://r4ds.hadley.nz/) — the single best R learning resource that exists. Written by Hadley Wickham, who created most of the packages you'll use. Bookmark this and return to it throughout.

### 🎥 YouTube
- **R Programming 101** — [R Programming for Beginners (playlist)](https://www.youtube.com/@RProgramming101) — Best starting channel. Each video covers one concept, practical and clear.
- **MarinStatsLectures** — [R Tutorials for Beginners (playlist)](https://www.youtube.com/@marinstatlectures) — More academic, excellent if you want to understand *why* as well as *how*.

### Topics to Cover
- Vectors, lists, matrices, data frames
- Variable assignment with `<-` (R's version of `=`)
- Basic math and operations (R treats everything as a vector — `5 + c(1,2,3)` works!)
- Functions: defining and calling
- Control flow: `if/else`, `for`, `while`
- Importing data: `read.csv()`, `read.table()`
- The RStudio interface: console, environment, plots pane

---

## Phase 2 — The Tidyverse (Week 3–4)

**Goal:** Learn the Tidyverse — R's dominant ecosystem for data wrangling and visualization. This is the modern, readable way to work with data in R.

The Tidyverse is a collection of packages (installable libraries) that share a consistent philosophy. The two you'll use most: `dplyr` for data manipulation and `ggplot2` for visualization.

```r
install.packages("tidyverse") # installs everything at once
library(tidyverse)
```

### 📖 Official / Core Docs
- [dplyr documentation](https://dplyr.tidyverse.org/) — your go-to for data wrangling
- [ggplot2 documentation](https://ggplot2.tidyverse.org/) — for visualization
- [tidyr documentation](https://tidyr.tidyverse.org/) — for reshaping data
- [R for Data Science — Data Transformation chapter](https://r4ds.hadley.nz/data-transform)

### 🎥 YouTube
- **StatQuest with Josh Starmer** — [Statistics and R playlist](https://www.youtube.com/@statquest) — Josh makes statistics genuinely fun with animations and humor. Essential viewing.
- **R Programming 101** — [ggplot2 tutorials](https://www.youtube.com/@RProgramming101) — Practical, visual, no fluff.

### Core dplyr verbs to learn
```r
filter()    # filter rows (like SQL WHERE)
select()    # pick columns
mutate()    # add/transform columns
group_by()  # group data
summarize() # aggregate (like SQL GROUP BY + aggregate)
arrange()   # sort
```

### The pipe operator `|>` (or `%>%`)
This is R's superpower for readable data pipelines:
```r
data |>
  filter(age > 18) |>
  group_by(country) |>
  summarize(avg_income = mean(income))
```

### ggplot2 basics
```r
ggplot(data, aes(x = height, y = weight, color = sex)) +
  geom_point() +
  geom_smooth(method = "lm") +
  labs(title = "Height vs Weight")
```

---

## Phase 3 — Statistics in R (Week 5–6)

**Goal:** Use R for actual statistical analysis — the core reason R exists.

### 📖 Official / Core Docs
- [R for Data Science — Modeling section](https://r4ds.hadley.nz/)
- [Introduction to Statistical Learning (free PDF)](https://www.statlearning.com/) — the textbook that teaches ML through R (used at universities worldwide)

### 🎥 YouTube
- **StatQuest with Josh Starmer** — [Linear Regression in R](https://www.youtube.com/@statquest) — Start with linear regression, then explore from there
- **MarinStatsLectures** — [Statistical Methods in R](https://www.youtube.com/@marinstatlectures)

### Topics to Cover
- Descriptive statistics: `mean()`, `median()`, `sd()`, `summary()`
- Correlation: `cor()`
- Linear regression: `lm()`
- Visualizing model results with ggplot2
- Working with distributions: `dnorm()`, `pnorm()`, `rnorm()`
- Hypothesis testing: `t.test()`, `chisq.test()`

---

## Phase 4 — R Markdown and Reporting (Week 7)

**Goal:** Learn to produce clean, shareable reports that combine code, output, and narrative. This is what makes R so valued in academic and research contexts.

### 📖 Official Docs
- [R Markdown](https://rmarkdown.rstudio.com/) — the classic
- [Quarto](https://quarto.org/) — the modern successor to R Markdown, also works with Python and Julia

### 🎥 YouTube
- **R Programming 101** — [R Markdown Tutorial](https://www.youtube.com/@RProgramming101)

An R Markdown file looks like this:
```markdown
## My Analysis

Here's what I found:

```{r}
summary(my_data)
``​`

The average age was `r mean(data$age)`.
```

When you "knit" the file, it runs all the code and produces a clean HTML or PDF report.

---

## 🏗️ Capstone Project: Global Health EDA Report

**What you'll build:** A full exploratory data analysis (EDA) report on a real public health dataset, rendered as an HTML document.

**Dataset:** [Our World in Data — public health datasets](https://ourworldindata.org/data) or the [WHO Global Health Observatory](https://www.who.int/data/gho). Download any CSV that interests you — life expectancy, disease rates, vaccination coverage, etc.

**Your report should include:**

1. **Data Overview** — how many rows/columns, what variables, any missing data
2. **Distribution Plots** — histograms or density plots of key variables (ggplot2)
3. **Relationships** — scatter plots or correlation matrices comparing two variables
4. **Country/Region Comparisons** — bar charts grouped by continent or income group
5. **A Simple Model** — fit a linear regression and interpret the output (e.g. "does GDP predict life expectancy?")
6. **Written Narrative** — explain what you found in plain English throughout the document

**Tools:** `tidyverse`, `ggplot2`, `dplyr`, R Markdown or Quarto

**Repo structure suggestion:**
```
r-health-analysis/
├── README.md
├── report.Rmd         # your R Markdown report
├── report.html        # the rendered output (commit this too)
├── data/
│   └── health_data.csv
└── scripts/
    └── clean_data.R   # data cleaning script
```

---

## Ongoing References

| Resource | Use It For |
|---|---|
| [R for Data Science](https://r4ds.hadley.nz/) | Your primary textbook — free online |
| [R Documentation](https://www.rdocumentation.org/) | Looking up any function |
| [TidyTuesday](https://github.com/rfordatascience/tidytuesday) | Weekly dataset challenges with community code to learn from |
| [StatQuest](https://www.youtube.com/@statquest) | Understanding statistics visually |
| [ggplot2 cheat sheet](https://rstudio.github.io/cheatsheets/data-visualization.pdf) | Always keep this open |

---

*Next step after this roadmap: Pick a statistics topic that genuinely interests you — survival analysis, logistic regression, time series — and go deep using R.*
