<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>KODAMA</title>
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.4/css/all.min.css">
    <style>
        /* Navbar Styles */
        .navbar {
            background-color: #333;
            border-radius: 0;
        }
        .navbar-nav .nav-link {
            color: white;
            transition: color 0.3s;
        }
        .navbar-nav .nav-link:hover {
            color: #007bff;
        }
        .navbar-brand {
            color: white;
            font-size: 24px;
        }
        /* Section Styles */
        section {
            padding: 20px;
            border-radius: 0;
            background-color: #f9f9f9;
            box-shadow: 0px 0px 20px rgba(0, 0, 0, 0.1);
        }
        section h1 {
            color: #007bff;
            margin-bottom: 20px;
        }
        /* Card Styles */
        .card {
            border: none;
            border-radius: 0;
            box-shadow: 0 4px 8px rgba(0,0,0,0.1);
            transition: transform 0.3s;
            cursor: pointer;
        }
        .card:hover {
            transform: translateY(-5px);
        }
        .card-body {
            text-align: center;
        }
    </style>
</head>
<body>

<!-- Navbar -->
<nav class="navbar navbar-expand-lg navbar-dark bg-dark">
    <div class="container-fluid">
        <a class="navbar-brand" href="#">KODAMA</a>
        <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
            <span class="navbar-toggler-icon"></span>
        </button>

        <div class="collapse navbar-collapse" id="navbarSupportedContent">
            <ul class="navbar-nav ml-auto">
                <li class="nav-item">
                    <a class="nav-link" href="#introduction">Introduction</a>
                </li>
                <li class="nav-item">
                    <a class="nav-link" href="#software-tutorial">Software Tutorial</a>
                </li>
                <li class="nav-item">
                    <a class="nav-link" href="#simulation">Simulation</a>
                </li>
                <li class="nav-item dropdown">
                    <a class="nav-link dropdown-toggle" href="#" id="navbarDropdown" role="button" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
                        Data Analyses
                    </a>
                    <div class="dropdown-menu" aria-labelledby="navbarDropdown">
                        <a class="dropdown-item" href="https://github.com/tkcaccia/KODAMA/blob/main/docs/Metabolomics_data.md">Metabolomic data</a>
                        <a class="dropdown-item" href="https://github.com/tkcaccia/KODAMA/blob/main/docs/Single_cell_RNA_seq.md">Single cell RNA seq data</a>
                        <a class="dropdown-item" href="https://github.com/tkcaccia/KODAMA/blob/main/docs/Spatial%20_transcriptomic.md">Spatial Transcriptomic data</a>
                    </div>
                </li>
            </ul>
            <ul class="navbar-nav">
                <li class="nav-item">
                    <a class="nav-link" href="https://github.com/tkcaccia/KODAMA">
                        <span class="fab fa-github"></span>
                        Source code
                    </a>
                </li>
            </ul>
        </div>
    </div>
</nav>

<!-- Introduction Section -->
<section id="introduction">
    <div class="container">
        <h1>Introduction</h1>
        <p>
            # KODAMA An unsupervised and semi-supervised learning algorithm to perform feature extraction from noisy and high-dimensional data
        </p>
    </div>
</section>

<!-- News Section -->
<section>
    <div class="container">
        <h2>News</h2>
        <p>
            KODAMA facilitates identification of patterns representing underlying groups on all samples in a data set. This is an improved version of KODAMA algorithm for spatially-aware dimensionality reduction. A landmarks procedure has been implemented to adapt the algorithm to the analysis of data set with more than 10,000 entries. The KODAMA package has been integrated with t-SNE and UMAP to convert the KODAMA's dissimilarity matrix in a low dimensional space.
        </p>
    </div>
</section>

<!-- Installation Section -->
<section>
    <div class="container">
        <h2>Installation</h2>
        <p>
            The KODAMA is available on <a href="https://CRAN.R-project.org/package=KODAMA">CRAN</a>.
        </p>
        <pre><code>library(devtools)
install_github("tkcaccia/KODAMA")
        </code></pre>
    </div>
</section>

<!-- Applications Section -->
<section>
    <div class="container">
        <h2>Applications</h2>
        <div class="card-deck">
            <div class="card">
                <div class="card-body">
                    <h5 class="card-title">Metabolomic data</h5>
                    <p class="card-text">Explore Metabolomic data</p>
                </div>
            </div>
            <div class="card">
                <div class="card-body">
                    <h5 class="card-title">Single cell RNA seq data</h5>
                    <p class="card-text">Explore Single cell RNA seq data</p>
                </div>
            </div>
            <div class="card">
                <div class="card-body">
                    <h5 class="card-title">Spatial Transcriptomic data</h5>
                    <p class="card-text">Explore Spatial Transcriptomic data</p>
                </div>
            </div>
        </div>
    </div>
</section>

<!-- Bootstrap Scripts -->
<script src="https://code.jquery.com/jquery-3.5.1.slim.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.5.3/dist/umd/popper.min.js"></script>
<script src="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/js/bootstrap.min.js"></script>

</body>
</html>
