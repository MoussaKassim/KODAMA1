<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>KODAMA</title>
    <style>
        /* Dropdown Menu Styles */
        .dropdown {
            position: relative;
            display: inline-block;
            background-color: #f9f9f9;
            border-radius: 8px;
            padding: 10px;
            cursor: pointer;
            font-size: 18px;
            font-weight: bold;
        }

        .dropdown:hover .dropdown-content {
            display: block;
        }

        .dropdown-content {
            display: none;
            position: absolute;
            background-color: #f9f9f9;
            min-width: 160px;
            box-shadow: 0px 8px 16px 0px rgba(0,0,0,0.2);
            border-radius: 8px;
            z-index: 1;
        }

        .dropdown-content a {
            color: black;
            padding: 12px 16px;
            text-decoration: none;
            display: block;
        }

        .dropdown-content a:hover {
            background-color: #f1f1f1;
            color: #007bff;
        }

        /* Section Styles */
        section {
            margin-bottom: 20px;
            padding: 20px;
            border: 1px solid #ccc;
            border-radius: 8px;
            background-color: #f9f9f9;
        }

        section h1 {
            font-size: 24px;
            color: #007bff;
            margin-bottom: 10px;
        }

        section p {
            font-size: 18px;
            line-height: 1.6;
            color: #333;
        }

        section pre {
            font-size: 16px;
            color: #555;
            background-color: #fff;
            padding: 10px;
            border-radius: 8px;
            overflow-x: auto;
        }

        section pre code {
            font-family: 'Courier New', Courier, monospace;
            font-size: 16px;
        }
    </style>
</head>
<body>

<!-- Dropdown Menu -->
<div class="dropdown">
    <span>Menu</span>
    <div class="dropdown-content">
        <a href="#introduction">Introduction</a>
        <a href="#software-tutorial">Software Tutorial</a>
        <a href="#simulation">Simulation</a>
        <a href="#data-analyses">Data Analyses</a>
        <a href="#code-source-github">Code Source GitHub</a>
    </div>
</div>

<!-- Introduction Section -->
<section id="introduction">
    <h1>Introduction</h1>
    <!-- Include provided script here -->
    <!-- Script content goes here -->
</section>

<!-- Software Tutorial Section -->
<section id="software-tutorial">
    <h1>Software Tutorial</h1>
    <p>
        # Tutorial Content
    </p>
    <!-- Add more content as needed -->
</section>

<!-- Simulation Section -->
<section id="simulation">
    <h1>Simulation</h1>
    <p>
        # Simulation Content
    </p>
    <!-- Add more content as needed -->
</section>

<!-- Data Analyses Section -->
<section id="data-analyses">
    <h1>Data Analyses</h1>
    <p>
        # Data Analyses Content
    </p>
    <!-- Add more content as needed -->
</section>

<!-- Code Source GitHub Section -->
<section id="code-source-github">
    <h1>Code Source GitHub</h1>
    <p>
        # GitHub Code Content
    </p>
    <!-- Add more content as needed -->
</section>

</body>
</html>
