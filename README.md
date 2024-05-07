<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>KODAMA</title>
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.4/css/all.min.css">
    <style>
        /* Styles CSS */

        /* Navbar Styles */
        .navbar {
            /* Styles Navbar */
        }

        /* Body padding to compensate for fixed navbar */
        body {
            /* Styles Body */
        }

        /* Sidebar Styles */
        #sidebar {
            /* Styles Sidebar */
        }

        /* Toolbox */
        .toolbox {
            /* Styles Toolbox */
        }

        /* Custom Styles for Data Sections */
        .data-section {
            /* Styles Data Sections */
        }

        /* Card Styles */
        .card {
            /* Styles Card */
        }

        /* Tooltip Styles */
        /* Styles Tooltip */
    </style>
</head>

<body>

    <!-- Navbar -->
    <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
        <div class="container">
            <a class="navbar-brand" href="#">
                KODAMA
            </a>
            <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent"
                aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
                <span class="navbar-toggler-icon"></span>
            </button>

            <div class="collapse navbar-collapse" id="navbarSupportedContent">
                <ul class="navbar-nav mr-auto">
                    <li class="nav-item" data-toggle="tooltip" data-placement="bottom" title="Introduction">
                        <a class="nav-link" href="#introduction">Introduction</a>
                    </li>
                    <li class="nav-item" data-toggle="tooltip" data-placement="bottom" title="Software Tutorial">
                        <a class="nav-link" href="#software-tutorial">Software Tutorial</a>
                    </li>
                    <li class="nav-item" data-toggle="tooltip" data-placement="bottom" title="Simulation">
                        <a class="nav-link" href="#simulation">Simulation</a>
                    </li>
                    <li class="nav-item dropdown" data-toggle="tooltip" data-placement="bottom"
                        title="Data Analyses">
                        <a class="nav-link dropdown-toggle" href="#" id="navbarDropdown" role="button"
                            data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
                            Data Analyses
                        </a>
                        <div class="dropdown-menu" aria-labelledby="navbarDropdown">
                            <a class="dropdown-item"
                                href="https://github.com/tkcaccia/KODAMA/blob/main/docs/Metabolomics_data.md">Metabolomic
                                data</a>
                            <a class="dropdown-item"
                                href="https://github.com/tkcaccia/KODAMA/blob/main/docs/Single_cell_RNA_seq.md">Single
                                cell RNA seq data</a>
                            <a class="dropdown-item"
                                href="https://github.com/tkcaccia/KODAMA/blob/main/docs/Spatial%20_transcriptomic.md">Spatial
                                Transcriptomic data</a>
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

    <!-- Sidebar -->
    <div id="sidebar">
        <ul>
            <li id="introLink" data-toggle="tooltip" data-placement="right" title="Introduction">
                <a href="#introduction">
                    <i class="fas fa-book-open"></i>
                    <span>Introduction</span>
                </a>
            </li>
            <li id="newsLink" data-toggle="tooltip" data-placement="right" title="News">
                <a href="#news">
                    <i class="fas fa-newspaper"></i>
                    <span>News</span>
                </a>
            </li>
            <li id="installationLink" data-toggle="tooltip" data-placement="right" title="Installation">
                <a href="#installation">
                    <i class="fas fa-tools"></i>
                    <span>Installation</span>
                </a>
            </li>
            <li id="applicationsLink" data-toggle="tooltip" data-placement="right" title="Applications">
                <a href="#applications">
                    <i class="fas fa-tasks"></i>
                    <span>Applications</span>
                </a>
            </li>
        </ul>
    </div>

    <!-- Toolbox -->
    <div class="toolbox">
        <div class="toolbox-item" data-toggle="tooltip" data-placement="left" title="Zoom" onclick="toggleZoom()">
            <i class="fas fa-search"></i>
        </div>
        <div class="toolbox-item" data-toggle="tooltip" data-placement="left" title="Highlight" onclick="toggleHighlight()">
            <i class="fas fa-highlighter"></i>
        </div>
        <div class="toolbox-item" data-toggle="tooltip" data-placement="left" title="Draw" onclick="toggleDrawing()">
            <i class="fas fa-pen"></i>
        </div>
    </div>

    <!-- Introduction Section -->
    <section id="introduction" class="data-section">
        <div class="container">
            <h2>Introduction</h2>
            <p>
                # KODAMA An unsupervised and semi-supervised learning algorithm to perform feature extraction from
                noisy and high-dimensional data
            </p>
        </div>
    </section>

    <!-- News Section -->
    <section id="news" class="data-section">
        <div class="container">
            <h2>News</h2>
            <p>
                KODAMA facilitates identification of patterns representing underlying groups on all samples in a data
                set. This is an improved version of KODAMA algorithm for spatially-aware dimensionality reduction. A
                landmarks procedure has been implemented to adapt the algorithm to the analysis of data set with more
                than 10,000 entries.
            </p>
            <p>
                The KODAMA package has been integrated with t-SNE and UMAP to convert the KODAMA's dissimilarity
                matrix in a low dimensional space.
            </p>
            <ul>
                <li><a href="https://www.ncbi.nlm.nih.gov/pmc/articles/PMC9887019/"
                        style="color: blue;">Zinga, M. M.,
                        Abdel-Shafy, E., Melak, T., Vignoli, A., Piazza, S., Zerbini, L. F., ... & Cacciatore, S.
                        (2022). KODAMA exploratory analysis in metabolic phenotyping. Frontiers in Molecular Biosciences,
                        9.</a></li>
                <li><a href="https://academic.oup.com/bioinformatics/article/33/4/621/2667156?login=false"
                        style="color: blue;">Cacciatore, S., Tenori, L., Luchinat, C., Bennett, P. R., & MacIntyre, D.
                        A. (2017). KODAMA: an R package for knowledge discovery and data mining. Bioinformatics,
                        33(4), 621-623.</a></li>
                <li><a href="https://www.pnas.org/doi/abs/10.1073/pnas.1220873111" style="color: blue;">Cacciatore,
                        S., Luchinat, C., & Tenori, L. (2014). Knowledge discovery by accuracy maximization. Proceedings
                        of the National Academy of Sciences, 111(14), 5117-5122.</a></li>
            </ul>
        </div>
    </section>

    <!-- Installation Section -->
    <section id="installation" class="data-section">
        <div class="container">
            <h2>Installation</h2>
            <p>
                The KODAMA is available on <a href="https://CRAN.R-project.org/package=KODAMA" style="color: blue;">CRAN</a>.
            </p>
            <pre><code style="color: blue;">
library(<span style="color: black;">devtools</span>)
install_github("<span style="color: green;">tkcaccia/KODAMA</span>")
            </code></pre>
        </div>
    </section>

    <!-- Applications Section -->
    <section id="applications" class="data-section">
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

    <!-- Font Awesome Script -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.4/js/all.min.js"></script>

    <!-- Custom Script -->
    <script>
        // Variables pour suivre l'état des outils
        let zoomEnabled = false;
        let highlightEnabled = false;
        let drawingEnabled = false;

        // Fonction pour activer ou désactiver le zoom
        function toggleZoom() {
            zoomEnabled = !zoomEnabled;
            if (zoomEnabled) {
                document.body.style.cursor = "zoom-in";
                document.addEventListener("mousemove", handleZoom);
            } else {
                document.body.style.cursor = "default";
                document.removeEventListener("mousemove", handleZoom);
            }
        }

        // Fonction pour gérer le zoom avec le curseur de la souris
        function handleZoom(event) {
            console.log("Zooming...");
        }

        // Fonction pour activer ou désactiver le surlignage
        function toggleHighlight() {
            highlightEnabled = !highlightEnabled;
            if (highlightEnabled) {
                document.body.style.cursor = "url('path/to/highlighter-cursor.png'), auto";
                document.addEventListener("mousedown", startHighlighting);
                document.addEventListener("mouseup", stopHighlighting);
            } else {
                document.body.style.cursor = "default";
                document.removeEventListener("mousedown", startHighlighting);
                document.removeEventListener("mouseup", stopHighlighting);
            }
        }

        // Fonction pour commencer le surlignage
        function startHighlighting(event) {
            console.log("Start highlighting...");
        }

        // Fonction pour arrêter le surlignage
        function stopHighlighting(event) {
            console.log("Stop highlighting...");
        }

        // Fonction pour activer ou désactiver le dessin
        function toggleDrawing() {
            drawingEnabled = !drawingEnabled;
            if (drawingEnabled) {
                document.body.style.cursor = "url('path/to/pencil-cursor.png'), auto";
                document.addEventListener("mousedown", startDrawing);
                document.addEventListener("mouseup", stopDrawing);
            } else {
                document.body.style.cursor = "default";
                document.removeEventListener("mousedown", startDrawing);
                document.removeEventListener("mouseup", stopDrawing);
            }
        }

        // Fonction pour commencer le dessin
        function startDrawing(event) {
            console.log("Start drawing...");
        }

        // Fonction pour arrêter le dessin
        function stopDrawing(event) {
            console.log("Stop drawing...");
        }

        // Navbar animations
        // Sidebar animations
    </script>

</body>

</html>
