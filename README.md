<!DOCTYPE html>
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
        .navbar-nav .nav-link,
        .sidebar-item-content,
        .data-section,
        .card-title,
        .card-text {
            font-family: "Source Sans Pro", Calibri, Candara, Arial, sans-serif;
            font-size: 18px; /* Réduire la taille de la police */
            line-height: 1.5;
            color: #333333;
        }

        /* Navbar Styles */
        .navbar {
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            z-index: 1000;
            border-color: #121212;
            border-radius: 0;
            background-color: #121212;
            padding: 0.01rem 1rem; /* Réduire la taille de la barre noire */
        }

        .navbar-nav .nav-link {
            color: white;
            transition: color 0.3s, background-color 0.3s;
            padding: 0.5rem 1.5rem; /* Ajuster les espacements */
            font-weight: normal; /* Rendre le texte un peu en gras */
        }

        .navbar-nav .nav-link:hover {
            color: #fff;
            background-color: rgba(0, 0, 0, 0.2); /* Couleur de fond plus sombre au survol */
        }

        /* Body padding to compensate for fixed navbar */
        body {
            padding-top: 20px; /* Ajuster la marge supérieure pour compenser la hauteur de la barre de navigation */
            background-color: #f8f9fa;
        }

        /* Sidebar Styles */
        #sidebar {
            position: fixed;
            top: 0%;
            left: 0;
            transform: translateY(-50%);
            z-index: 1000;
            background-color: #343a40;
            width: 20px; /* Réduire la taille de la barre noire */
            height: auto;
            overflow: hidden;
            transition: width 0.3s;
            box-shadow: 0px 0px 20px rgba(0, 0, 0, 0.2);
        }

        #sidebar:hover {
            width: 80px; /* Ajuster la largeur de la barre noire au survol */
        }

        /* Styles for menu items */
        .nav-item {
            margin-bottom: 0;
        }

        /* Adjusting margin for Introduction */
        .navbar-nav .nav-item:first-child {
            margin-top: -1.5px; /* Réduire légèrement la marge supérieure */
        }

        /* Rest of your existing CSS */

    </style>
</head>

<body>

    <!-- Navbar -->
    <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
        <div class="container">
            <a class="navbar-brand" href="#" style="font-size: 15px;"> <!-- Taille de police pour "KODAMA" -->
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

    <!-- jQuery -->
    <script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
    <!-- Bootstrap JavaScript -->
    <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/js/bootstrap.bundle.min.js"></script>
</body>

</html>
