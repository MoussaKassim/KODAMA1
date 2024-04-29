<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>KODAMA</title>
    <style>
        /* Navbar Styles */
        .navbar {
            background-color: #000;
            overflow: hidden;
            border-radius: 10px;
        }
        .navbar a {
            float: left;
            display: block;
            color: white;
            text-align: center;
            padding: 14px 16px;
            text-decoration: none;
            font-size: 18px;
            transition: background-color 0.3s;
        }

        .navbar a:hover {
            background-color: #555;
        }

        /* Section Styles */
        section {
            margin-top: 20px;
            padding: 20px;
            border: 1px solid #ccc;
            border-radius: 10px;
            background-color: #f9f9f9;
        }

        section h1 {
            color: #007bff;
        }
    </style>
</head>
<body>

<!-- Navbar -->
<div class="navbar">
    <a href="#introduction">Introduction</a>
    <a href="#software-tutorial">Software Tutorial</a>
    <a href="#simulation">Simulation</a>
    <a href="#data-analyses">Data Analyses</a>
    <a href="#code-source-github">Code Source GitHub</a>
</div>

<!-- KODAMA Section -->
<section>
    <h1>KODAMA</h1>
    <p>
        An unsupervised and semi-supervised learning algorithm to perform feature extraction from noisy and high-dimensional data
    </p>
</section>

<!-- News Section -->
<section>
    <h2>News</h2>
    <p>
        KODAMA facilitates identification of patterns representing underlying groups on all samples in a data set. 
        This is an improved version of KODAMA algorithm for spatially-aware dimensionality reduction. 
        A landmarks procedure has been implemented to adapt the algorithm to the analysis of data set with more than 10,000 entries. 
        The KODAMA package has been integrated with t-SNE and UMAP to convert the KODAMA's dissimilarity matrix in a low dimensional space.
    </p>
    <!-- Links to articles -->
</section>

<!-- Installation Section -->
<section>
    <h2>Installation</h2>
    <p>
        The KODAMA is available on <a href="https://CRAN.R-project.org/package=KODAMA">CRAN</a>.
    </p>
    <pre><code>library(devtools)
install_github("tkcaccia/KODAMA")
    </code></pre>
</section>

<!-- Applications Section -->
<section>
    <h2>Applications</h2>
    <ol>
        <li><a href="https://github.com/tkcaccia/KODAMA/blob/main/docs/Metabolomics_data.md">Metabolomic data</a></li>
        <li><a href="https://github.com/tkcaccia/KODAMA/blob/main/docs/Single_cell_RNA_seq.md">Single cell RNA seq data</a></li>
        <li><a href="https://github.com/tkcaccia/KODAMA/blob/main/docs/Spatial%20_transcriptomic.md">Spatial Transcriptomic data</a></li>
    </ol>
</section>

</body>
</html>
