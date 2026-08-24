---
title: Learner Profiles
---

## Who Should Take This Workshop?

Workshop 7 — *Programming with R* — is designed for researchers and students at Pomona College who already have *some* exposure to data analysis (Excel, GraphPad, SPSS, or a single college statistics course) and now need to write reproducible analysis scripts in R. The three personas below capture the most common motivations for enrolling. If you see yourself in one of them, this workshop is a good fit.

All three personas use Pomona's Sagehen HPC cluster either directly (via the OnDemand portal at [https://ondemand.hpc.pomona.edu](https://ondemand.hpc.pomona.edu)) or indirectly (their PI does, and they need to be able to run their analyses there). Wherever the lesson refers to "your laptop," you can substitute "your home directory on Sagehen" without changing anything else.

---

## Profile 1: Maya — Biology PhD Candidate Working on Genomics

### Background
Maya is a fourth-year PhD candidate in the Pomona–Claremont Graduate University biology programme. Her dissertation focuses on the gut microbiome of *Peromyscus californicus* deer mice trapped at the Bernard Field Station, and her PI has just returned from a sabbatical promising "we'll do all the analysis in R from now on." Maya has six months of metabarcoding sequencing data on Sagehen at `/bigdata/lab/biolab/microbiome/` and a deadline that involves both her qualifying exam and a manuscript for *Molecular Ecology*. Her co-advisor uses Bioconductor heavily and expects her to follow along.

### What She Knows
- Strong wet-lab skills: extractions, library prep, quality control with a Bioanalyzer
- Comfortable with the Linux command line and SLURM (she completed Workshops 0–2 last semester)
- Has run someone else's R script for QIIME2 output but never written one from scratch
- Can compute means, medians, standard deviations, and t-tests by hand or in Excel
- Understands the *concept* of a vector and a matrix from her linear-algebra prerequisite

### What She Doesn't Know Yet
- How to import a CSV, TSV, or `.biom` file into R without using `clipr` and pasting
- What the `<-` assignment arrow does, or why R people prefer it over `=`
- How `data.frame`s differ from matrices and which one to use when
- How to write a function with default arguments
- How `apply`/`lapply`/`vapply` differ — and when one of them is the right tool for the job

### Why She Needs This
- **Her PI requires R.** Bioconductor (`phyloseq`, `DESeq2`, `vegan`) is the lingua franca of community-ecology genomics, and her PI's previous students all left scripts behind in R.
- **Her data is too big for Excel.** A single `.biom` table is 4 GB; a single Excel sheet caps out at ~1.5 million rows.
- **Reproducibility matters.** *Molecular Ecology* now requires a `Code Availability` statement; she can't just hand-paste figures any more.
- **She wants to graduate.** Six months of analysis on a deadline.

### How She Will Use Sagehen
Maya runs R 4.5.3 on Sagehen via the OnDemand RStudio Server app, with an interactive SLURM session on the **amd** partition (`--cpus-per-task=16 --mem=128G --time=8:00:00`). Her project lives at `/bigdata/lab/biolab/maya/microbiome/` so it persists between sessions.

### Success Indicator
By the end of the workshop, Maya can:

- Load CSV and TSV files from `/bigdata` into R with `read.csv` or `readr::read_tsv`
- Subset rows and columns of a `data.frame` using both base R and the `[` operator
- Write a function (with comments) that takes a sample name and returns a normalised count vector
- Use `for` loops and `apply` to process all 96 samples in the cohort without copy-pasting
- Read and understand error messages well enough to ask focused questions on Stack Overflow
- Open her work in a fresh RStudio session (or three months later) and rerun it without breakage

### How to Pace for Maya
Anchor every example to a "before/after" framing — what would she have done in Excel? what does R let her automate? — and pause on every error message so she practices reading them.

---

## Profile 2: Ben — Economics Major in Quantitative Methods

### Background
Ben is a senior at Pomona majoring in economics with a maths concentration, applying to PhD programmes for next fall. His senior thesis uses panel data from the U.S. Bureau of Labor Statistics and the IPUMS-CPS extracts to study the labour-market effects of community-college tuition policy. His thesis advisor strongly prefers R for econometrics ("Stata is for the second draft; R is for everything else"), and the PhD programmes he is targeting list R as a desired skill. He has used R in one course already but always treated it as "type until the answer appears" rather than learning it as a programming language.

### What He Knows
- Solid statistics: OLS, fixed effects, instrumental variables, standard errors
- A few R functions by muscle memory (`lm`, `summary`, `plot`)
- Comfortable with LaTeX and version control
- Has produced regression tables with `stargazer` once
- Can write a Stata `.do` file but has never written an R function

### What He Doesn't Know Yet
- The difference between a vector and a list (he has been treating both as "Stata variables")
- That `data.frame` columns are vectors and so vectorised operations apply
- How to scope variables inside functions — he has been writing one giant top-level script
- How package management works (`install.packages` vs `library` vs `renv`)
- Why his thesis advisor keeps saying "tidyverse" — and whether it matters for him

### Why He Needs This
- **PhD programmes expect R fluency.** Top economics programmes increasingly assign R for problem sets.
- **His thesis is large.** Five years of monthly CPS extracts is roughly 40 GB of CSVs; he cannot fit it in memory on his laptop.
- **He wants to publish.** Having a clean, function-based R workflow makes his thesis chapter much easier to convert into a working paper after graduation.

### How He Will Use Sagehen
Ben runs his thesis on Sagehen because the IPUMS extracts won't fit on a laptop. He requests an interactive `--mem=64G` session on the amd partition, mounts the IPUMS data from `/bigdata/lab/economics/ipums/`, and uses `data.table` (taught in Workshop 8) for the heavy lifting.

### Success Indicator
By the end of the workshop, Ben can:

- Distinguish vectors, lists, matrices, and `data.frame`s and choose the right one for a task
- Write a function `sample_summary(df, group_var)` that returns mean and SD by group
- Use control flow (`if`, `else if`, `else`) inside a function instead of in a top-level script
- Read his own R code three months later and not flinch
- Translate a small Stata `.do` file into an R script that produces identical regression output

### How to Pace for Ben
Lean into "R as a programming language, not a calculator." Whenever he asks "but can't I just …," answer with the *programming concept* (scope, vectorisation, functions) rather than the shortcut.

---

## Profile 3: Priya — Humanities Researcher Doing Text Analysis

### Background
Priya is a postdoc in the Pomona College English department, joint-appointed with the Claremont Colleges Library digital humanities centre. She is building a corpus of 19th-century American newspaper articles digitised by the Pomona archives, and she has been told by her co-PI that "you should learn some R" so she can run topic models on the corpus. She has never programmed before, but she is a careful editor of LaTeX, and she has read enough about reproducibility in the humanities to know that hand-counting is not an option for a 14,000-document corpus. She is enthusiastic but slightly nervous: she has never used a Linux command line before this workshop.

### What She Knows
- Deep close-reading and qualitative-coding skills
- Comfortable with LaTeX and bibliographic tooling (Zotero, BibTeX)
- Has used Excel for grant budgets but never for analysis
- Understands the *idea* of statistical significance from a graduate research-methods seminar
- Can navigate macOS Finder and Microsoft Word well enough to advise a junior colleague

### What She Doesn't Know Yet
- Anything about programming control flow (`for`, `if`, `while`)
- The difference between a script (`.R`) and an R Markdown document (`.Rmd`)
- How to read an error message without anxiety
- How character vectors, factors, and strings differ in R
- How to call a function vs. how to write one

### Why She Needs This
- **The corpus is too large.** A close-reading approach to 14,000 articles is not feasible on a postdoc timeline.
- **The library wants a reproducible pipeline.** The DH centre is committed to open methods so future researchers can rerun and extend her work.
- **Publication venues are changing.** Journals such as *Cultural Analytics* and *Journal of Cultural Analytics* now require code and data deposits.
- **She wants to ask questions her qualitative methods cannot answer alone.** "Did the framing of *immigrant* shift between 1850 and 1910?" is a question text-mining can address at scale.

### How She Will Use Sagehen
Priya does *not* want to install R on her laptop. She uses the OnDemand RStudio Server app on Sagehen exclusively, with her corpus stored at `/bigdata/lab/dhlab/newspapers/`. Her co-PI helped her open her HPC account through `its-hpc@pomona.edu`. The whole workflow lives behind one URL ([https://ondemand.hpc.pomona.edu](https://ondemand.hpc.pomona.edu)) and one DUO push.

### Success Indicator
By the end of the workshop, Priya can:

- Open RStudio Server on Sagehen, navigate to her project, and create a new R Markdown document
- Read a CSV of document metadata into a `data.frame` and inspect its first few rows
- Use `for` loops to apply a simple transformation across the documents in her corpus
- Knit an R Markdown file to HTML and share the result with her co-PI
- Recognise an error message as information rather than a personal failing

### How to Pace for Priya
She needs encouragement more than additional content. Use her humanities domain in examples ("imagine each row is a newspaper article instead of a patient"), pause on every error, and make sure she leaves with a working notebook she can show her co-PI tomorrow.

---

## Common Threads

Despite very different domains, all three personas share three things:

1. **They have real data on Sagehen.** None of them is here because they want to learn programming for its own sake. They are here because their data has outgrown the tools they know.
2. **They have a deadline.** A qualifying exam, a thesis defence, a co-PI meeting. Pacing matters.
3. **They are not computer scientists.** Use the language of their domain wherever possible. "Each patient is a row" works for Maya; "each article is a row" works for Priya; "each worker–year observation is a row" works for Ben.

If you teach to one of them at the expense of the other two, you will lose the room. The strength of the workshop is teaching the *programming concepts* (vectors, functions, control flow, error messages) using examples from each of their worlds in rotation.

## Where They Go Next

After Workshop 7, all three are well prepared for **Workshop 8 — R for Reproducible Scientific Analysis**, which deepens the same skills in a project-oriented, dplyr/ggplot2-first way. Maya will also benefit from the SLURM Job Scheduling workshop (Workshop 9), and Priya should take the OnDemand Portal Orientation (Workshop 11) to build fluency with the cluster. Ben, who is graduating, will use Workshop 7's foundations as the basis for his graduate-school R coursework.
