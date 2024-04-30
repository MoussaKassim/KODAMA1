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
            border-radius: 10px;
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
            margin-top: 20px;
            padding: 20px;
            border-radius: 10px;
            background-color: #f9f9f9;
            box-shadow: 0px 0px 20px rgba(0, 0, 0, 0.1);
            display: none; /* Hide sections by default */
        }
        section.active {
            display: block; /* Show active section */
        }
        section h1 {
            color: #007bff;
            margin-bottom: 20px;
        }
        /* Card Styles */
        .card {
            border: none;
            border-radius: 10px;
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
        /* Code Styles */
        pre {
            background-color: #f8f9fa;
            border: 1px solid #dee2e6;
            border-radius: 5px;
            padding: 10px;
            overflow-x: auto;
            position: relative;
            cursor: pointer;
        }
        pre:hover::after {
            content: "";
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 255, 0.1); /* Blue color when hovered */
            border-radius: 5px;
            z-index: 1;
        }
        pre:hover::before {
            content: "\f0ea"; /* FontAwesome copy icon */
            font-family: "Font Awesome 5 Free";
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            font-size: 20px;
            color: #007bff;
            z-index: 2;
        }
        .copy-box {
            border: 1px solid #dee2e6;
            border-radius: 5px;
            padding: 10px;
            background-color: #f8f9fa;
            margin-top: 20px;
            cursor: pointer;
            display: inline-block;
            position: relative;
        }
        .copy-box:hover {
            background-color: #e9ecef;
        }
        .copy-box::before {
            content: "\f0c5"; /* FontAwesome copy icon */
            font-family: "Font Awesome 5 Free";
            position: absolute;
            top: 50%;
            left: 5px;
            transform: translateY(-50%);
            font-size: 18px;
            color: #007bff;
        }
    </style>
</head>
<body>

<!-- Navbar -->
<nav class="navbar navbar-expand-lg navbar-dark bg-dark">
    <div class="container">
        <a class="navbar-brand" href="#">KODAMA</a>
        <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
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
                    <a class="nav-link dropdown-toggle" href="#" id="navbarDropdown" role="button" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
                        Data Analyses
                    </a>
                    <div class="dropdown-menu" aria-labelledby="navbarDropdown">
                        <a class="dropdown-item" href="#metabolomic-data">Metabolomic data</a>
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
<section id="introduction" class="active">
    <div class="container">
        <h1>Introduction</h1>
        <p>
            # KODAMA An unsupervised and semi-supervised learning algorithm to perform feature extraction from noisy and high-dimensional data
        </p>
    </div>
</section>

<!-- Metabolomic Data Section -->
<section id="metabolomic-data">
    <div class="container">
        <h1>Metabolomic data</h1>
        <p>
            The data belong to a cohort of 22 healthy donors (11 male and 11 female) where each provided about 40 urine samples over the time course of approximately 2 months, for a total of 873 samples. Each sample was analysed by Nuclear Magnetic Resonance Spectroscopy. Each spectrum was divided in 450 spectral bins.
        </p>
        <h2>Tutorial</h2>
        <pre><code>data(MetRef)
u=MetRef$data
u=u[,-which(colSums(u)==0)]
u=normalization(u)$newXtrain
u=scaling(u)$newXtrain
class=as.numeric(as.factor(MetRef$gender))
class2=as.numeric(as.factor(MetRef$donor))
res_MDS=cmdscale(dist(u))
res_tSNE=Rtsne(u)$Y
res_UMAP = umap(u)$layout
kk=KODAMA.matrix(u,f.par = 50)
res_KODAMA_MDS=KODAMA.visualization(kk,method = "MDS")
res_KODAMA_tSNE=KODAMA.visualization(kk,method = "t-SNE")
res_KODAMA_UMAP=KODAMA.visualization(kk,method = "UMAP")
par(mfrow = c(2,3))
plot(res_MDS,pch=21,bg=rainbow(2)[class],main="MDS")
plot(res_tSNE,pch=21,bg=rainbow(2)[class],main="tSNE")
plot(res_UMAP,pch=21,bg=rainbow(2)[class],main="UMAP")
plot(res_KODAMA_MDS,pch=21,bg=rainbow(2)[class],main="KODAMA_MDS",)
plot(res_KODAMA_tSNE,pch=21,bg=rainbow(2)[class],main="KODAMA_tSNE")
plot(res_KODAMA_UMAP,pch=21,bg=rainbow(2)[class],main="KODAMA_UMAP")
</code></pre>
        <p>
            <p align="center">
                <img src="https://github.com/tkcaccia/KODAMA/blob/main/figures/metabolites.gender.png" alt="hello-light"  />
            </p>
        </p>
        <p>
            <p align="center">
                <img src="https://github.com/tkcaccia/KODAMA/blob/main/figures/metabolites.donor.png" alt="hello-light" />
            </p>
        </p>
    </div>
</section>

<!-- Bootstrap Scripts -->
<script src="https://code.jquery.com/jquery-3.5.1.slim.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.5.3/dist/umd/popper.min.js"></script>
<script src="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/js/bootstrap.min.js"></script>

<!-- Script to toggle active class on section click -->
<script>
    document.querySelectorAll('.navbar-nav .nav-link').forEach(link => {
        link.addEventListener('click', function(e) {
            e.preventDefault(); // Prevent default link behavior
            const targetId = this.getAttribute('href'); // Get target section ID
            document.querySelectorAll('section').forEach(section => {
                section.classList.remove('active'); // Remove active class from all sections
            });
            document.querySelector(targetId).classList.add('active'); // Add active class to target section
        });
    });
</script>

</body>
</html>
