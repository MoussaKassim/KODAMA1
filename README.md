<kodama >
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
            background-color: #333;
            border-radius: 0;
            transition: transform 0.3s, box-shadow 0.3s;
        }

        .navbar:hover {
            transform: scale(1.05);
            box-shadow: 0px 0px 20px rgba(0, 0, 0, 0.5);
        }

        .navbar-brand {
            transition: transform 0.3s, box-shadow 0.3s;
        }

        .navbar-brand:hover {
            transform: scale(1.1);
            box-shadow: 0px 0px 20px rgba(255, 255, 255, 0.5);
        }

        .navbar-nav .nav-link {
            color: white;
            transition: color 0.3s, background-color 0.3s;
        }

        .navbar-nav .nav-link:hover {
            color: #FFA500;
            background-color: rgba(255, 165, 0, 0.1);
        }

        /* Body padding to compensate for fixed navbar */
        body {
            padding-top: 56px;
            margin: 0;
            background-color: #f8f9fa;
            font-family: Arial, sans-serif;
        }

        /* Sidebar Styles */
        #sidebar {
            position: fixed;
            top: 50%;
            left: 0;
            transform: translateY(-50%);
            z-index: 1000;
            background-color: #343a40;
            width: 70px;
            height: auto;
            overflow: hidden;
            transition: width 0.3s, box-shadow 0.3s;
            box-shadow: 0px 0px 20px rgba(0, 0, 0, 0.2);
        }

        #sidebar:hover {
            width: 200px;
        }

        #sidebar ul {
            list-style-type: none;
            padding: 0;
            margin: 0;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100%;
        }

        #sidebar ul li {
            width: 200px;
            padding: 15px;
            color: white;
            cursor: pointer;
            transition: background-color 0.3s, transform 0.3s;
            display: flex;
            align-items: center;
            justify-content: flex-start;
        }

        #sidebar ul li:hover {
            background-color: #adb5bd;
            transform: translateX(10px);
        }

        #sidebar ul li a {
            text-decoration: none;
            color: inherit;
        }

        #sidebar ul li i {
            margin-right: 10px;
        }

        .sidebar-item-content {
            #sidebar ul li:hover .sidebar-item-content {
        display: block;
    }

    @keyframes fadeIn {
        from {
            opacity: 0;
        }

        to {
            opacity: 1;
        }
    }

    .sidebar-item-title {
        font-weight: bold;
        margin-bottom: 5px;
    }

    /* Custom Styles for Data Sections */
    .data-section {
        margin-top: 20px;
        padding: 20px;
        border-radius: 10px;
        background-color: #fff;
        box-shadow: 0px 0px 20px rgba(0, 0, 0, 0.1);
        animation: fadeInUp 1s ease;
    }

    @keyframes fadeInUp {
        from {
            opacity: 0;
            transform: translateY(50px);
        }

        to {
            opacity: 1;
            transform: translateY(0);
        }
    }

    .data-section h2 {
        color: #007bff;
        margin-bottom: 20px;
    }

    .data-section p {
        color: #343a40;
        margin-bottom: 20px;
    }

    /* Card Styles */
    .card {
        border: none;
        border-radius: 10px;
        box-shadow: 0px 0px 20px rgba(0, 0, 0, 0.1);
        transition: transform 0.3s, box-shadow 0.3s;
    }

    .card:hover {
        transform: scale(1.05);
        box-shadow: 0px 0px 30px rgba(0, 0, 0, 0.2);
    }

    .card-title {
        color: #007bff;
        font-weight: bold;
    }

    .card-text {
        color: #343a40;
    }
</style>
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
                    <a class="nav-link" href="#tutorial">Software Tutorial</a>
                </li>
                <li class="nav-item" data-toggle="tooltip" data-placement="bottom" title="
                <!-- Sidebar -->
<div id="sidebar">
    <ul>
        <li id="TutorialLink" data-toggle="tooltip" data-placement="right" title="Tutorial">
            <a href="#tutorial">
                <i class="fas fa-book-open"></i>
                <span>Tutorial</span>
            </a>
        </li>
        <li id="MDS, tSNE and UMAPLink" data-toggle="tooltip" data-placement="right" title="MDS, tSNE and UMAP">
            <a href="#dimensionality-reduction">
                <i class="fas fa-newspaper"></i>
                <span>MDS, tSNE and UMAP</span>
            </a>
        </li>
        <li id="KODAMALink" data-toggle="tooltip" data-placement="right" title="KODAMA">
            <a href="#kodama">
                <i class="fas fa-tools"></i>
                <span>KODAMA</span>
            </a>
        </li>
        <li id="VisualizeAlgorithmsLink" data-toggle="tooltip" data-placement="right"
            title="Visualize the different clustering algorithms">
            <a href="#visualizations">
                <i class="fas fa-tasks"></i>
                <span>Visualize the different clustering algorithms</span>
            </a>
        </li>
    </ul>
</div>

<!-- Content -->
<div class="container">
    <!-- Metabolomic data -->
    <div class="data-section" id="metabolomic-data">
        <h2>Metabolomic data</h2>
        <p>The data belong to a cohort of 22 healthy donors (11 male and 11 female) where each provided about 40 urine
            samples over the time course of approximately 2 months, for a total of 873 samples. Each sample was
            analysed by Nuclear Magnetic Resonance Spectroscopy. Each spectrum was divided into 450 spectral bins.
        </p>
    </div>

    <!-- Tutorial -->
    <div class="data-section" id="tutorial">
        <h2>Tutorial</h2>
        <p>Here, we load the
        import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

# Load the data
data = pd.read_csv("metabolomic_data.csv", index_col=0)

# Check the first rows of the data
print(data.head())

# Check the shape of the data
print(data.shape)

# Check the data types of the data
print(data.dtypes)

# Check the correlation matrix
corr_matrix = data.corr()
plt.figure(figsize=(10, 10))
sns.heatmap(corr_matrix, annot=True, cmap="coolwarm")
plt.show()

# Check the distribution of the data
data.hist(bins=50, figsize=(20, 15))
plt.show()

# Check the missing values
print(data.isnull().sum())

# Replace the missing values with the mean of the column
data_cleaned = data.fillna(data.mean())

# Check the missing values after cleaning
print(data_cleaned.isnull().sum())
from sklearn.manifold import MDS, TSNE, UMAP

# MDS
mds = MDS(n_components=2, dissimilarity="precomputed")
X_mds = mds.fit_transform(corr_matrix)

# tSNE
tsne = TSNE(n_components=2, perplexity=30, learning_rate="auto")
X_tsne = tsne.fit_transform(corr_matrix)

# UMAP
umap = UMAP(n_neighbors=10, min_dist=0.1, metric="correlation")
X_umap = umap.fit_transform(corr_matrix)

# Plot the results
plt.figure(figsize=(10, 10))
plt.scatter(X_mds[:, 0], X_mds[:, 1], label="MDS")
plt.scatter(X_tsne[:, 0], X_tsne[:, 1], label="tSNE")
plt.scatter(X_umap[:, 0], X_umap[:, 1], label="UMAP")
plt.legend()
plt.show()
# Load the data
data = pd.read_csv("single_cell_rna_seq_data.csv", index_col=0)

# Run KODAMA
!kodama run -i data.csv -o kodama_output

# Open the KODAMA web interface
!kodama open kodama_output
# Open the KODAMA web interface
!kodama open kodama_output
