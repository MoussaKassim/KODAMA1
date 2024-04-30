<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Metabolomic Data Analysis</title>
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css">
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f8f9fa;
            color: #343a40;
            margin: 0;
            padding: 0;
        }
        .container {
            max-width: 800px;
            margin: 20px auto;
            padding: 20px;
            background-color: #fff;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
        h1 {
            color: #007bff;
            margin-top: 0;
        }
        h2 {
            color: #007bff;
            margin-top: 30px;
        }
        p {
            line-height: 1.6;
        }
        pre {
            background-color: #f8f9fa;
            border: 1px solid #dee2e6;
            border-radius: 5px;
            padding: 10px;
            overflow-x: auto;
        }
        img {
            max-width: 100%;
            height: auto;
            margin-top: 20px;
        }
    </style>
</head>
<body>

<div class="container">
    <h1>Metabolomic Data Analysis</h1>

    <div>
        <h2>Data Description</h2>
        <p>
            The data belong to a cohort of 22 healthy donors (11 male and 11 female) where each provided about 40 urine samples over the time course of approximately 2 months, for a total of 873 samples. Each sample was analysed by Nuclear Magnetic Resonance Spectroscopy. Each spectrum was divided into 450 spectral bins.
        </p>
    </div>

    <div>
        <h2>Tutorial</h2>
        <pre><code>
data(MetRef)
u=MetRef$data
u=u[,-which(colSums(u)==0)]
        </code></pre>
        <p>
            We apply the Probabilistic Quotient Normalization
            <code>
u=normalization(u)$newXtrain
            </code>
        </p>
        <!-- Add other tutorial steps as needed -->
    </div>

    <div>
        <h2>Analysis</h2>
        <!-- Add analysis steps and code snippets here -->
    </div>

    <div>
        <h2>Visualizations</h2>
        <h3>Cluster Analysis by Gender</h3>
        <img src="https://github.com/tkcaccia/KODAMA/blob/main/figures/metabolites.gender.png" alt="Cluster Analysis by Gender">
        <h3>Cluster Analysis by Donor</h3>
        <img src="https://github.com/tkcaccia/KODAMA/blob/main/figures/metabolites.donor.png" alt="Cluster Analysis by Donor">
    </div>
</div>

</body>
</html>
