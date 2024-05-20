<KODAMA>
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
        .navbar-nav .nav-link {color: #ffffff;
        .navbar-nav .nav-link {
            font-family: "Source Sans Pro", Arial, sans-serif;
            font-size: 16px;
            color: #ffffff;
            background-color: ;
        }}
         
        /* Navbar Styles */
        .navbar {
            position: fixed;
            top: 0;
            left: 0cm;
            right: 0;
            z-index: 500;
            background-color: #333333;
            padding-top: 0;
            padding-bottom: 0;
            height: 50px;
            width: calc(100%);
        }

        .navbar-brand {
            margin-top: -5px;
        }

        .navbar-nav .nav-item {
            margin-bottom: 04px;
            display: flex;
            align-items: center;
            justify-content: space-between;
            box-shadow: 0 109px 109px rgba(0, 0, 0, 0);
        }

        .navbar-nav .nav-link {
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
        }

        .navbar-nav .nav-item:nth-child(1) {
            margin-top: 20px;
        }

        .navbar-nav .nav-item:nth-child(2) {
            margin-top: 20px;
        }

        .navbar-nav .nav-item:nth-child(3) {
            margin-top: 20px;
        }

        .navbar-nav .nav-item:nth-child(4) {
            margin-top: 20px;
            margin-right: 10cm;
            margin-left: auto;
        }

        .navbar-nav .source-code-link {
            margin-top: 40px;
        }

        .container {
            padding-left: 8.5cm;
        }

        .navbar-brand,
        .navbar-nav .nav-link {
            padding: 0.1px 1rem;
            text-decoration: none;
            display: inline-block;
        }

        .navbar-brand {
            font-size: 20px;
            margin-right: 5px;
            position: relative;
            display: block;
        }

        .navbar-brand:hover,
        .navbar-nav .nav-link:hover {
            text-decoration: none;
        }

        .navbar-nav {
            display: flex;
            align-items: center;
            margin-left: 05px;
        }

        /* Body padding to compensate for fixed navbar */
        body {
            padding-top: 0cm;
            background-color: #ffffff;
            color: #333;
            margin: 0;
        }

        /* Sidebar Styles */
        #sidebar {
            position: fixed;
            top: 2.9cm;
            bottom: 2cm;
            left: 9.5cm;
            width: 180%;
            max-width: 260px;
            max-height: 17%;
            overflow-y: auto;
            box-shadow: 0px 0px 5px rgba(0, 0, 0, 0.0);
            padding: 5px;
            line-height: 20px;
            border-radius: 6px;
            border: 1px solid #ccc;
        }

        #sidebar ul {
            list-style: none;
            padding: 0;
            margin: 0;
        }

        #sidebar ul li {
            padding: 5px;
            transition: background-color 0.3s;
            cursor: pointer;
        }

        #sidebar ul li:hover {
            background-color: #none;
        }

        #sidebar ul li a {
            color: #000000;
            text-decoration: none;
            font-size: 16px;
            font-family: "Source Sans Pro", Arial, sans-serif;
        }

        #sidebar ul li a i {
            font-size: 10px;
        }

        /* Main Content Styles */
        .container {
            margin-left: 0.2cm;
        }

        /* Sections Styles */
        .data-section {
            margin-bottom: 20px;
        }

        /* Adjusting margin for Introduction */
        .navbar-nav .nav-item:first-child {
            margin-top: 20px;
        }

        /* Active link styles */
        .active-link {
            background-color: #2780e3 !important;
        }

        .active-link a {
            color: white !important;
        }

        /* Code container styles */
        .code-container {
            position: relative;
            background-color: #f8f9fa;
            border: 1px solid #ccc;
            padding: 10px;
            margin-top: 10px;
            border-radius: 6px;
            overflow: hidden;
        }

        pre {
            margin: 0;
            padding: 0;
            overflow-x: auto;
        }

        button {
            position: absolute;
            top: 5px;
            right: 5px;
            background-color: transparent;
            border: none;
            color: #007bff;
            cursor: pointer;
        }

        button:hover {
            color: #0056b3;
        }

        button.copied {
            color: #28a745;
        }

        button.copied:hover {
            color: #218838;
        }
        .card {
    transition: transform 0.3s;
}

.card:hover {
    transform: scale(1.05);
}
.card {
    transition: transform 0.3s;
    border: none;
    border-radius: 10px;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    background-color: #fff;
    color: #333;
    margin-bottom: 20px;
}

.card:hover {
    transform: scale(1.05);
    box-shadow: 0 8px 12px rgba(0, 0, 0, 0.2);
}
.code-container {
    background-color: #f4f4f4; /* gris clair */
    border: 1px solid #ccc;
    border-radius: 5px;
    padding: 10px;
    margin-bottom: 20px;
}

/* Styles for specific screen sizes */

/* Small devices (landscape phones, 576px and up) */
@media (min-width: 576px) {
    /* Ajouter des styles spécifiques pour les petits appareils ici */
    body {
        padding-top: 50px; /* Compensation pour la barre de navigation fixe */
    }

    .container {
        padding-left: 15px;
        padding-right: 15px;
    }

    #sidebar {
        display: none; /* Masquer la barre latérale sur les petits appareils */
    }

    .navbar-nav {
        margin-left: auto;
    }

    .navbar-nav .nav-item {
        margin-bottom: 0;
    }

    .navbar-nav .nav-item:nth-child(4) {
        margin-right: 0;
        margin-left: auto;
        /* Ajouter d'autres modifications selon vos besoins */
    }
}




/* Medium devices (tablets, 768px and up) */
@media (min-width: 768px) {
    /* Medium devices (tablets, 768px and up) */
@media (min-width: 768px) {
    /* Ajoutez ici les styles spécifiques aux appareils de taille moyenne */

    /* Réduire la taille de la police du titre principal */
    h1 {
        font-size: 28px;
    }

    /* Ajuster la largeur de la barre latérale pour les tablettes */
    #sidebar {
        width: 250px;
    }

    /* Augmenter l'espacement entre les éléments du menu */
    .navbar-nav .nav-item {
        margin-bottom: 10px;
    }

    /* Réduire la taille de la police des liens du menu */
    .navbar-nav .nav-link {
        font-size: 14px;
    }

    /* Ajuster l'espacement du contenu principal */
    .container {
        padding-left: 20px;
        padding-right: 20px;
    }

    /* Ajouter d'autres modifications selon vos besoins */
}


/* Large devices (desktops, 992px and up) */
@media (min-width: 992px) {
    /* Ajoutez ici les styles spécifiques aux grands appareils */

    /* Augmenter la taille de la police du titre principal */
    h1 {
        font-size: 36px;
    }

    /* Augmenter la largeur de la barre latérale pour les grands écrans */
    #sidebar {
        width: 300px;
    }

    /* Réduire l'espacement entre les éléments du menu */
    .navbar-nav .nav-item {
        margin-bottom: 5px;
    }

    /* Augmenter la taille de la police des liens du menu */
    .navbar-nav .nav-link {
        font-size: 16px;
    }

    /* Ajuster l'espacement du contenu principal */
    .container {
        padding-left: 30px;
        padding-right: 30px;
    }

    /* Ajouter d'autres modifications selon vos besoins */
}


/* Extra large devices (large desktops, 1200px and up) */
@media (min-width: 1200px) {
    /* Ajoutez ici les styles spécifiques aux appareils extra larges */

    /* Augmenter encore la taille de la police du titre principal */
    h1 {
        font-size: 42px;
    }

    /* Augmenter encore la largeur de la barre latérale pour les grands écrans */
    #sidebar {
        width: 350px;
    }

    /* Réduire davantage l'espacement entre les éléments du menu */
    .navbar-nav .nav-item {
        margin-bottom: 3px;
    }

    /* Augmenter davantage la taille de la police des liens du menu */
    .navbar-nav .nav-link {
        font-size: 18px;
    }

    /* Ajuster davantage l'espacement du contenu principal */
    .container {
        padding-left: 40px;
        padding-right: 40px;
    }

    /* Ajouter d'autres modifications selon vos besoins */
}

    </style>
</head>

<body>
    <!-- Navbar -->
    <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
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
                            <a class="dropdown-item"
                                href="https://moussakassim.github.io/Metabolomic-data/">Metabolomic
                                data</a>
                            <a class="dropdown-item"
                                href="https://moussakassim.github.io/Single-cell-Data/">Single
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
     <script>
        // Fonction pour changer le style de l'élément actif
        function setActiveLink(linkId) {
            // Supprimer la classe active-link de tous les éléments
            var links = document.querySelectorAll('#sidebar ul li');
            links.forEach(function (item) {
                item.classList.remove('active-link');
            });

            // Ajouter la classe active-link à l'élément sélectionné
            var selectedLink = document.getElementById(linkId);
            selectedLink.classList.add('active-link');
        }

        // Ajouter un écouteur d'événement pour chaque élément de la barre latérale
        var sidebarLinks = document.querySelectorAll('#sidebar ul li');
        sidebarLinks.forEach(function (link) {
            link.addEventListener('click', function (event) {
                // Empêcher le comportement par défaut du lien
                event.preventDefault();
                
                // Récupérer l'ID de l'élément cliqué
                var linkId = event.currentTarget.id;
                
                // Appeler la fonction pour définir l'élément actif
                setActiveLink(linkId);
            });
        });
    </script>

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
                    The KODAMA is available on <a href="https://CRAN.R-project.org/package=KODAMA"
                        style="color: blue;">CRAN</a>.
                </p>
                <div class="code-container">
                    <pre><code id="rCode" style="color: blue;">
library(<span style="color: black;">devtools</span>)
install_github("<span style="color: green;">tkcaccia/KODAMA</span>")
                    </code></pre>
                    <button id="copyButton"><i class="far fa-copy"></i> </button>
                </div>
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

    <!-- JavaScript for interactive functionality -->
    <script>
    // Fonction pour déplacer la page vers l'élément correspondant
function scrollToSection(sectionId) {
    var section = document.getElementById(sectionId);
    section.scrollIntoView({ behavior: 'smooth', block: 'start' });
}

// Ajouter un écouteur d'événement pour chaque élément de la barre latérale
var sidebarLinks = document.querySelectorAll('#sidebar ul li');
sidebarLinks.forEach(function (link) {
    link.addEventListener('click', function (event) {
        // Empêcher le comportement par défaut du lien
        event.preventDefault();

        // Récupérer l'ID de la section correspondante
        var sectionId = link.querySelector('a').getAttribute('href').replace('#', '');

        // Défiler jusqu'à la section correspondante
        scrollToSection(sectionId);
    });
});

        // Fonction pour ajouter la classe de couleur de fond au survol
        function addBackgroundOnHover(element) {
            element.addEventListener('mouseenter', function () {
                element.classList.add('bg-color');
            });
            element.addEventListener('mouseleave', function () {
                element.classList.remove('bg-color');
            });
        }

        // Fonction pour gérer le clic sur un élément de la liste
        function handleItemClick(element) {
            element.addEventListener('click', function () {
                // Supprimer la classe de couleur de fond de tous les éléments
                var listItems = document.querySelectorAll('.nav-item');
                listItems.forEach(function (item) {
                    item.classList.remove('bg-color');
                });

                // Ajouter la classe de couleur de fond à l'élément cliqué
                element.classList.add('bg-color');
            });
        }

        // Sélectionnez tous les éléments de la liste du menu
        var menuItems = document.querySelectorAll('.nav-item');

        // Ajouter la logique d'interaction pour chaque élément de la liste du menu
        menuItems.forEach(function (item) {
            handleItemClick(item);
            addBackgroundOnHover(item);
        });
        // JavaScript for copying code and adding hover effect
        function copyCode() {
            var rCode = document.getElementById('rCode');
            var codeText = rCode.innerText;
            navigator.clipboard.writeText(codeText);
        }

        var copyButton = document.getElementById('copyButton');
        copyButton.addEventListener('click', function () {
            copyCode();
            copyButton.classList.add('copied');
            setTimeout(function () {
                copyButton.classList.remove('copied');
            }, 1000);
        });
        
        // Fonction pour afficher/masquer la barre latérale sur les petits appareils
function toggleSidebar() {
    var sidebar = document.getElementById('sidebar');
    sidebar.style.display = (sidebar.style.display === 'none' || sidebar.style.display === '') ? 'block' : 'none';
}

// Ajouter un écouteur d'événement au bouton de la barre de navigation pour afficher/masquer la barre latérale
var toggleButton = document.querySelector('.navbar-toggler');
toggleButton.addEventListener('click', function() {
    toggleSidebar();
});

    </script>
</body>

</html>
