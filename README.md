<kodama>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>KODAMA</title>
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.4/css/all.min.css">
    <style>
        /* Font Family and Size */
        body,
        .navbar-nav .nav-link {
            font-family: "Source Sans Pro", Arial, sans-serif;
            font-size: 18px; /* Taille de police par défaut */
            color: #ffffff; /* Couleur du texte */
        }

        /* Navbar Styles */
        .navbar {
            position: fixed;
            top: 0;
            left: 0cm; /* Ajustement pour couvrir toute la largeur de la page */
            right: 0; /* Ajustement pour couvrir toute la largeur de la page */
            z-index: 500;
            background-color: #121212; /* Couleur foncée pour la navbar */
            padding: 0 px 0; /* Réduit la hauteur de la barre noire et ajoute un peu de padding */
        }
.container {
            padding-left: 7.5cm; /* Ajouter une marge à gauche pour compenser le déplacement de la navbar */
        }
        .navbar-brand,
        .navbar-nav .nav-link {
            padding: 0.1rem 1rem; /* Ajuste les espacements */
            text-decoration: none; /* Supprime le soulignement */
        }

        .navbar-brand {
            font-size: 20px; /* Augmente la taille du texte de la marque */
            margin-right: 5px; /* Ajoute un espace entre la marque et les éléments du menu */
        }

        .navbar-brand:hover {
            text-decoration: none; /* Supprime le soulignement au survol */
        }

        .navbar-nav {
            display: flex; /* Affiche les éléments du menu en ligne */
            align-items: center; /* Centre les éléments du menu verticalement */
            margin-left: 05px; /* Ajuste la marge gauche pour correspondre à la marque */
        }

        .navbar-nav .nav-link {
            margin-right: 20px; /* Ajoute un espacement entre les éléments du menu */
            transition: color 0.3s; /* Animation de transition de la couleur au survol */
        }

        .navbar-nav .nav-link:hover {
            color: #000000; /* Changement de couleur au survol */
            text-decoration: none; /* Supprime le soulignement au survol */
        }

        /* Body padding to compensate for fixed navbar */
        body {
            padding-top: 50px; /* Augmente la marge supérieure pour compenser la hauteur de la navbar */
            background-color: #f8f9fa;
            color: #333;
            margin: 0;
        }

        /* Sidebar Styles */
        #sidebar {
            position: fixed;
            top: 2.5cm; /* Ajustez la valeur pour positionner le carré à 2 cm du haut de la page */
            bottom: 2cm; /* Ajustez la valeur pour positionner le carré à 2 cm du bas de la page */
            left: 4.5cm; /* Place le carré à 2 cm du bord gauche */
            width: 6cm; /* Largeur du carré */
            height: 5.5cm; /* Hauteur automatique pour s'adapter au contenu */
            overflow-y: auto; /* Activation du défilement vertical si nécessaire */
            box-shadow: 0px 0px 5px rgba(0, 0, 0, 0.1); /* Ombre plus subtile */
            padding: 5px; /* Ajoute de l'espacement à l'intérieur du carré */
            border-radius: 5px; /* Coins plus arrondis */
            border: 1px solid #dddddd; /* Bordure plus épaisse */
        }

        #sidebar ul {
            list-style: none; /* Supprime les puces des listes */
            padding: 0;
            margin: 0;
        }

        #sidebar ul li {
            padding: 10px; /* Espacement entre les éléments de la liste */
            transition: background-color 0.3s; /* Animation de transition de la couleur au survol */
            cursor: pointer; /* Change le curseur au survol */
        }

        #sidebar ul li:hover {
            background-color: #2780e3; /* Changement de couleur au survol */
        }

        #sidebar ul li a {
            color: #000000; /* Couleur du texte */
            text-decoration: none; /* Supprime le soulignement */
            font-size: 20px; /* Taille du texte ajustée */
        }

        #sidebar ul li a i {
            font-size: 10px; /* Taille des icônes ajustée */
        }

        /* Main Content Styles */
        .container {
            margin-left: 1.5cm; /* Ajoute un espacement à gauche pour éviter le chevauchement avec le menu latéral */
        }

        /* Sections Styles */
        .data-section {
            margin-bottom: 30px; /* Ajoute un espacement entre les sections */
        }

        /* Adjusting margin for Introduction */
        .navbar-nav .nav-item:first-child {
            margin-top: -1px;
        }
    </style>
</head>

<body>
    <!-- Navbar -->
    <nav class="navbar navbar-expand-lg navbar-dark bg-dark"> <!-- Retiré la classe custom-navbar -->
        <div class="container">
            <a class="navbar-brand" href="#">KODAMA</a>
            <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent"
                aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
                <span class="navbar-toggler-icon"></span>
            </button>

            <div class="collapse navbar-collapse" id="navbarSupportedContent">
                <ul class="navbar-nav mr-auto">
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
                        <a class="nav-link dropdown-toggle" href="#" id="navbarDropdown" role="button"
                            data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
                            Data Analyses
                        </a>
                        <div class="dropdown-menu" aria-labelledby="navbarDropdown">
                            <a class="dropdown-item" href="https://github.com/tkcaccia/KODAMA/blob/main/docs/Metabolomics_data.md">Metabolomic
                                data</a>
                            <a class="dropdown-item" href="https://github.com/tkcaccia/KODAMA/blob/main/docs/Single_cell_RNA_seq.md">Single
                                cell RNA seq data</a>
                            <a class="dropdown-item" href="https://github.com/tkcaccia/KODAMA/blob/main/docs/Spatial%20_transcriptomic.md">Spatial
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

    <!-- Main Content -->
    <div>
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
    </div>

    <!-- Bootstrap Scripts -->
    <script src="https://code.jquery.com/jquery-3.5.1.slim.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.5.3/dist/umd/popper.min.js"></script>
    <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/js/bootstrap.min.js"></script>

    <!-- Font Awesome Script -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.4/js/all.min.js"></script>
</body>

</html>
