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
            background-color: #333;
            border-radius: 0; /* Rounded rectangle */
        }
        .navbar-nav .nav-link {
            color: white;
            transition: color 0.3s, background-color 0.3s; /* Transition for glowing effect */
        }
        .navbar-nav .nav-link:hover {
            color: #FFA500; /* Modern orangish color */
            background-color: rgba(255, 165, 0, 0.1); /* Orange background */
        }
        .navbar-brand {
            color: white;
            font-size: 24px;
        }
        /* Body padding to compensate for fixed navbar */
        body {
            padding-top: 56px; /* Height of the navbar */
            margin-left: 200px; /* Adjusted to accommodate the sidebar */
            background-color: #f9f9f9; /* Light gray background */
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; /* Modern font */
        }
        /* Sidebar Styles */
        #sidebar {
            position: fixed;
            top: 0;
            left: -200px; /* Initially hidden */
            bottom: 0;
            z-index: 1000;
            background-color: #333;
            width: 200px;
            padding-top: 56px; /* Height of the navbar */
            overflow-y: auto;
            transition: left 0.3s; /* Smooth transition for opening and closing */
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
        #content {
            margin-left: 0; /* Adjusted to accommodate the sidebar */
            padding: 20px;
            transition: margin-left 0.3s; /* Smooth transition for adjusting content when sidebar opens and closes */
        }
        /* Section Styles */
        section {
            margin-top: 20px;
            padding: 20px;
            border-radius: 10px;
            background-color: #fff; /* White background for sections */
            box-shadow: 0px 0px 20px rgba(0, 0, 0, 0.1);
        }
        section h1 {
            color: #007bff; /* Modern blue color */
            margin-bottom: 20px;
        }
        /* Code Styles */
        pre code {
            display: block;
            padding: 1rem;
            background-color: #282c34; /* Dark gray background */
            color: #61dafb; /* Light blue text */
            border-radius: 10px;
            overflow-x: auto;
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
        <pre><code>library(devtools)
install_github("tkcaccia/KODAMA")</code></pre>
    </div>
</section>

<!-- News Section -->
<section id="news">
    <div class="container">
        <h1>News</h1>
        <pre><code>library(devtools)
install_github("tkcaccia/KODAMA")</code></pre>
    </div>
</section>

<!-- Installation Section -->
<section id="installation">
    <div class="container">
        <h1>Installation</h1>
        <pre><code>library(devtools)
install_github("tkcaccia/KODAMA")</code></pre>
    </div>
</section>

<!-- Applications Section -->
<section id="applications">
    <div class="container">
        <h1>Applications</h1>
        <pre><code>library(devtools)
install_github("tkcaccia/KODAMA")</code></pre>
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

    // JavaScript to toggle sidebar
    document.addEventListener('DOMContentLoaded', function() {
        var sidebar = document.getElementById('sidebar');
        var content = document.getElementById('content');

        document.getElementById('sidebarToggle').addEventListener('click', function() {
            sidebar.classList.toggle('active');
            content.classList.toggle('active');
        });
    });
</script>

</body>
</html>
