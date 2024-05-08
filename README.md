<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>KODAMA</title>
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.4/css/all.min.css">
    <style>
        /* Styles CSS ici */
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
                    <!-- Vos liens de navigation ici -->
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
            <li id="TutorialLink" data-toggle="tooltip" data-placement="right" title="Tutorial">
                <a href="#Tutorial">
                    <i class="fas fa-book-open"></i>
                    <span>Tutorial</span>
                </a>
            </li>
            <li id="MDS, tSNE and UMALink" data-toggle="tooltip" data-placement="right" title="MDS, tSNE and UMAP">
                <a href="#MDS, tSNE and UMA">
                    <i class="fas fa-newspaper"></i>
                    <span>MDS, tSNE and UMA</span>
                </a>
            </li>
            <li id="KODAMALink" data-toggle="tooltip" data-placement="right" title="KODAMA">
                <a href="#KODAMA">
                    <i class="fas fa-tools"></i>
                    <span>KODAMA</span>
                </a>
            </li>
            <li id="Visualize the different clustering algorithmss:Link" data-toggle="tooltip" data-placement="right" title="Visualize the different clustering algorithmss:">
                <a href="#Visualize the different clustering algorithmss:">
                    <i class="fas fa-tasks"></i>
                    <span>Visualize the different clustering algorithmss:</span>
                </a>
            </li>
        </ul>
    </div>

    <!-- Contenu principal -->
    <div class="container">
        <div class="row">
            <div class="col-md-12">
                # Metabolomic data

The data belong to a cohort of 22 healthy donors (11 male and 11 female) where each provided about 40 urine samples over the time course of approximately 2 months, for a total of 873 samples. Each sample was analysed by Nuclear Magnetic Resonance Spectroscopy. Each spectrum was divided in 450 spectral bins.

## Tutorial

Here, we load the MetRef dataset. Columns with only zero values are removed. 

```
data(MetRef)
u=MetRef$data
u=u[,-which(colSums(u)==0)]
```
We apply the Probabilistic Quotient Normalization
```
u=normalization(u)$newXtrain
```
We mean-center and univariate scaling the data set.
```
u=scaling(u)$newXtrain
```
Two classification vectors are created
```
class=as.numeric(as.factor(MetRef$gender))
class2=as.numeric(as.factor(MetRef$donor))
```
# MDS, tSNE and UMAP
Different algorithms for dimensionality reduction are applied
```
res_MDS=cmdscale(dist(u))
res_tSNE=Rtsne(u)$Y
res_UMAP = umap(u)$layout
```
# KODAMA
We apply KODAMA with Partial Least Square Discriminant Analysis (PLS-DA) as classifier with 50 components to drive the accuracy maximixation. The KODAMA dissimilarity matrix's is converted in a low dimensionality space using three different methods (i.e., MDS, t-SNE, and UMAP).

```
kk=KODAMA.matrix(u,f.par = 50)
res_KODAMA_MDS=KODAMA.visualization(kk,method = "MDS")
res_KODAMA_tSNE=KODAMA.visualization(kk,method = "t-SNE")
res_KODAMA_UMAP=KODAMA.visualization(kk,method = "UMAP")
```

# Visualize the different clustering algorithmss:

  a) labelled by the gender

```
par(mfrow = c(2,3))
plot(res_MDS,pch=21,bg=rainbow(2)[class],main="MDS")
plot(res_tSNE,pch=21,bg=rainbow(2)[class],main="tSNE")
plot(res_UMAP,pch=21,bg=rainbow(2)[class],main="UMAP")
plot(res_KODAMA_MDS,pch=21,bg=rainbow(2)[class],main="KODAMA_MDS",)
plot(res_KODAMA_tSNE,pch=21,bg=rainbow(2)[class],main="KODAMA_tSNE")
plot(res_KODAMA_UMAP,pch=21,bg=rainbow(2)[class],main="KODAMA_UMAP")
```
<p>
  <p align="center">
    <img src="https://github.com/tkcaccia/KODAMA/blob/main/figures/metabolites.gender.png" alt="hello-light"  />
  </p>
</p>

  b) labelled by the donor

```
plot(res_MDS,pch=21,bg=rainbow(22)[class2],main="MDS")
plot(res_tSNE,pch=21,bg=rainbow(22)[class2],main="tSNE")
plot(res_UMAP,pch=21,bg=rainbow(22)[class2],main="UMAP")
plot(res_KODAMA_MDS,pch=21,bg=rainbow(22)[class2],main="KODAMA_MDS",)
plot(res_KODAMA_tSNE,pch=21,bg=rainbow(22)[class2],main="KODAMA_tSNE")
plot(res_KODAMA_UMAP,pch=21,bg=rainbow(22)[class2],main="KODAMA_UMAP")
```
<p>
  <p align="center">
    <img src="https://github.com/tkcaccia/KODAMA/blob/main/figures/metabolites.donor.png" alt="hello-light" />
  </p>
</p>


            </div>
        </div>
    </div>

    <!-- Bootstrap Scripts -->
    <script src="https://code.jquery.com/jquery-3.5.1.slim.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.5.3/dist/umd/popper.min.js"></script>
    <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/js/bootstrap.min.js"></script>

    <!-- Font Awesome Script -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.4/js/all.min.js"></script>

    <!-- Custom Script -->
    <script>
        // Navbar animations
        document.querySelector('.navbar-brand').addEventListener('mouseover', function () {
            this.style.transform = 'scale(1.1)';
            this.style.boxShadow = '0px 0px 20px rgba(255, 255, 255, 0.5)';
        });

        document.querySelector('.navbar-brand').addEventListener('mouseout', function () {
            this.style.transform = 'scale(1)';
            this.style.boxShadow = 'none';
        });

        // Sidebar animations
        const sidebarItems = document.querySelectorAll('#sidebar ul li');
        sidebarItems.forEach(item => {
            item.addEventListener('mouseover', function () {
                this.style.backgroundColor = 'rgba(173, 181, 189, 0.5)';
                this.style.transform = 'translateX(10px)';
            });
            item.addEventListener('mouseout', function () {
                this.style.backgroundColor = '';
                this.style.transform = 'translateX(0)';
            });
        });
    </script>

</body>

</html>
