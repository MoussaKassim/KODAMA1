<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>KODAMA</title>
    <style>
        /* Dropdown Menu Styles */
        .dropdown {
            position: relative;
            display: inline-block;
        }

        .dropdown-content {
            display: none;
            position: absolute;
            background-color: #f9f9f9;
            min-width: 160px;
            box-shadow: 0px 8px 16px 0px rgba(0,0,0,0.2);
            z-index: 1;
        }

        .dropdown:hover .dropdown-content {
            display: block;
        }

        .dropdown-content a {
            color: black;
            padding: 12px 16px;
            text-decoration: none;
            display: block;
        }

        .dropdown-content a:hover {
            background-color: #f1f1f1;
        }

        /* Section Styles */
        section {
            margin-bottom: 20px;
            padding: 10px;
            border: 1px solid #ccc;
        }
    </style>
</head>
<body>

<!-- Dropdown Menu -->
<div class="dropdown">
    <span>Menu</span>
    <div class="dropdown-content">
        <a href="#introduction">Introduction</a>
        <a href="#software-tutorial">Software Tutorial</a>
        <a href="#simulation">Simulation</a>
        <a href="#data-analyses">Data Analyses</a>
        <a href="#code-source-github">Code Source GitHub</a>
    </div>
</div>

<!-- Introduction Section -->
<section id="introduction">
    <h1>Introduction</h1>
    <!-- Include provided script here -->
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>KODAMA</title>
    </head>
    <body>

    <!-- Tab 1: Home Page -->
    <div id="home">
        <h1>KODAMA</h1>

        <h2>News</h2>
        <p>
            KODAMA facilitates identification of patterns representing underlying groups on all samples in a data set. This is an improved version of KODAMA algorithm for spatially-aware dimensionality reduction. A landmarks procedure has been implemented to adapt the algorithm to the analysis of data set with more than 10,000 entries. The KODAMA package has been integrated with t-SNE and UMAP to convert the KODAMA's dissimilarity matrix in a low dimensional space.
        </p>

        <ul>
            <li><a href="https://www.ncbi.nlm.nih.gov/pmc/articles/PMC9887019/">KODAMA exploratory analysis in metabolic phenotyping</a></li>
            <li><a href="https://academic.oup.com/bioinformatics/article/33/4/621/2667156?login=false">KODAMA: an R package for knowledge discovery and data mining</a></li>
            <li><a href="https://www.pnas.org/doi/abs/10.1073/pnas.1220873111">Knowledge discovery by accuracy maximization</a></li>
        </ul>

        <h2>Installation</h2>
        <p>
            The KODAMA package is available on <a href="https://CRAN.R-project.org/package=KODAMA">CRAN</a>.
        </p>
        <pre><code>library(devtools)
    install_github("tkcaccia/KODAMA")
        </code></pre>

        <h2>Applications</h2>
        <ol>
            <li><a href="#metabolomic-data">Metabolomic data</a></li>
            <li><a href="https://github.com/tkcaccia/KODAMA/blob/main/docs/Single_cell_RNA_seq.md">Single cell RNA seq data</a></li>
            <li><a href="https://github.com/tkcaccia/KODAMA/blob/main/docs/Spatial%20_transcriptomic.md">Spatial Transcriptomic data</a></li>
        </ol>
    </div>

    <!-- Tab 2: Metabolomic Data -->
    <div id="metabolomic-data">
        <h1>Metabolomic Data</h1>

        <h2>Tutorial</h2>
        <p>
            The data belong to a cohort of 22 healthy donors (11 male and 11 female) where each provided about 40 urine samples over the time course of approximately 2 months, for a total of 873 samples. Each sample was analysed by Nuclear Magnetic Resonance Spectroscopy. Each spectrum was divided into 450 spectral bins.
        </p>

        <h3>Code</h3>
        <pre><code>data(MetRef)
    u <- MetRef$data
    u <- u[, -which(colSums(u) == 0)]

    u <- normalization(u)$newXtrain
    u <- scaling(u)$newXtrain

    class <- as.numeric(as.factor(MetRef$gender))
    class2 <- as.numeric(as.factor(MetRef$donor))

    res_MDS <- cmdscale(dist(u))
    res_tSNE <- Rtsne(u)$Y
    res_UMAP <- umap(u)$layout

    kk <- KODAMA.matrix(u, f.par = 50)
    res_KODAMA_MDS <- KODAMA.visualization(kk, method = "MDS")
    res_KODAMA_tSNE <- KODAMA.visualization(kk, method = "t-SNE")
    res_KODAMA_UMAP <- KODAMA.visualization(kk, method = "UMAP")
        </code></pre>

        <h3>Visualizations</h3>
        <!-- Include your visualizations here -->
    </div>

    <!-- Tab 3: Another Application 1 -->
    <!-- Add more applications here if needed -->

    </body>
    </html>
</section>

<!-- Software Tutorial Section -->
<section id="software-tutorial">
    <h1>Software Tutorial</h1>
    <p>
        # Tutorial Content
    </p>
    <!-- Add more content as needed -->
</section>

<!-- Simulation Section -->
<section id="simulation">
    <h1>Simulation</h1>
    <p>
        # Simulation Content
    </p>
    <!-- Add more content as needed -->
</section>

<!-- Data Analyses Section -->
<section id="data-analyses">
    <h1>Data Analyses</h1>
    <p>
        # Data Analyses Content
    </p>
    <!-- Add more content as needed -->
</section>

<!-- Code Source GitHub Section -->
<section id="code-source-github">
    <h1>Code Source GitHub</h1>
    <p>
        # GitHub Code Content
    </p>
    <!-- Add more content as needed -->
</section>

</body>
</html>
