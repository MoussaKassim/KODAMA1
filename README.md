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
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            z-index: 1000;
            background-color: #1e1e1e;
            border-bottom: 2px solid #FFA500; /* Orange border bottom */
            border-radius: 0;
            box-shadow: 0 2px 4px rgba(0,0,0,0.1); /* Subtle shadow */
        }
        .navbar-brand {
            color: #FFA500; /* Orange color for the brand */
            font-size: 24px;
            font-weight: bold;
        }
        .navbar-toggler {
            border-color: #FFA500; /* Orange color for the toggler */
        }
        .navbar-toggler-icon {
            color: #FFA500; /* Orange color for the toggler icon */
        }
        .navbar-nav .nav-link {
            color: white;
            transition: color 0.3s, background-color 0.3s; /* Smooth transition */
        }
        .navbar-nav .nav-link:hover {
            color: #FFA500; /* Orange color on hover */
            background-color: transparent; /* Transparent background on hover */
        }
        .navbar-nav .active > .nav-link {
            color: #FFA500; /* Orange color for the active link */
        }
        /* Sidebar Styles */
        #sidebar {
            position: fixed;
            top: 0;
            left: 0;
            bottom: 0;
            z-index: 1000;
            background-color: #333;
            width: 200px;
            padding-top: 56px; /* Height of the navbar */
            overflow-y: auto;
            transition: all 0.3s;
        }
        #sidebar ul {
            list-style-type: none;
            padding: 0;
        }
        #sidebar ul li {
            padding: 10px;
            color: white;
            cursor: pointer;
            transition: background-color 0.3s;
        }
        #sidebar ul li:hover {
            background-color: rgba(255, 255, 255, 0.1);
        }
        /* Introduction Section */
        #introduction {
            height: 100vh;
            background-color: #f9f9f9;
        }
        /* News Section */
        #news {
            height: 100vh;
            background-color: #e9ecef;
        }
        /* Installation Section */
        #installation {
            height: 100vh;
            background-color: #f8f9fa;
        }
        /* Applications Section */
        #applications {
            height: 100vh;
            background-color: #f8f9fa;
        }
    </style>
</head>
<body>

<!-- Navbar -->
<nav class="navbar navbar-expand-lg navbar-dark">
    <div class="container">
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
                    <a class="nav-link" href="#news">News</a>
                </li>
                <li class="nav-item">
                    <a class="nav-link" href="#installation">Installation</a>
                </li>
                <li class="nav-item">
                    <a class="nav-link" href="#applications">Applications</a>
                </li>
            </ul>
        </div>
    </div>
</nav>

<!-- Sidebar -->
<div id="sidebar">
    <ul>
        <li id="introLink">Introduction</li>
        <li id="newsLink">News</li>
        <li id="installationLink">Installation</li>
        <li id="applicationsLink">Applications</li>
    </ul>
</div>

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
<section id="news">
    <div class="container">
        <h2>News</h2>
        <p>
            <span style="color: black;">KODAMA facilitates identification of patterns representing underlying groups on all samples in a data set. 
This is an improved version of KODAMA algorithm for spatially-aware dimensionality reduction. A landmarks procedure has been implemented to adapt the algorithm to the analysis of data set with more than 10,000 entries.</span>
        </p>
        <p>
            <span style="color: black;">The KODAMA package has been integrated with t-SNE and UMAP to convert the KODAMA's dissimilarity matrix in a low dimensional space.</span>
        </p>
        <p>
            <ul>
                <li><a href="https://www.ncbi.nlm.nih.gov/pmc/articles/PMC9887019/" style="color: blue; text-decoration: underline;">Zinga, M. M., Abdel-Shafy, E., Melak, T., Vignoli, A., Piazza, S., Zerbini, L. F., ... & Cacciatore, S. (2022). KODAMA exploratory analysis in metabolic phenotyping. Frontiers in Molecular Biosciences, 9.</a></li>
                <li><a href="https://academic.oup.com/bioinformatics/article/33/4/621/2667156?login=false" style="color: blue; text-decoration: underline;">Cacciatore, S., Tenori, L., Luchinat, C., Bennett, P. R., & MacIntyre, D. A. (2017). KODAMA: an R package for knowledge discovery and data mining. Bioinformatics, 33(4), 621-623.</a></li>
                <li><a href="https://www.pnas.org/doi/abs/10.1073/pnas.1220873111" style="color: blue; text-decoration: underline;">Cacciatore, S., Luchinat, C., & Tenori, L. (2014). Knowledge discovery by accuracy maximization. Proceedings of the National Academy of Sciences, 111(14), 5117-5122.</a></li>
            </ul>
        </p>
    </div>
</section>

<!-- Installation Section -->
<section id="installation">
    <div class="container">
        <h2>Installation</h2>
        <p>
            The KODAMA is available on <a href="https://CRAN.R-project.org/package=KODAMA">CRAN</a>.
        </p>
        <pre><code style="color: blue;">
library(<span style="color: black;">devtools</span>)
install_github("<span style="color: green;">tkcaccia/KODAMA</span>")
        </code></pre>
    </div>
</section>

<!-- Applications Section -->
<section id="applications">
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

<!-- JavaScript for Smooth Scrolling and Active Navigation -->
<script>
    // Smooth scrolling for sidebar links
    document.getElementById('introLink').addEventListener('click', function() {
        document.getElementById('introduction').scrollIntoView({ behavior: 'smooth' });
    });
    document.getElementById('newsLink').addEventListener('click', function() {
        document.getElementById('news').scrollIntoView({ behavior: 'smooth' });
    });
    document.getElementById('installationLink').addEventListener('click', function() {
        document.getElementById('installation').scrollIntoView({ behavior: 'smooth' });
    });
    document.getElementById('applicationsLink').addEventListener('click', function() {
        document.getElementById('applications').scrollIntoView({ behavior: 'smooth' });
    });
</script>

</body>
</html>
