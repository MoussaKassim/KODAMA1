<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>KODAMA</title>
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.4/css/all.min.css">
    <style>
        /* Styles for Toolbox */
        .toolbox {
            position: fixed;
            top: 50%;
            right: 20px;
            transform: translateY(-50%);
            z-index: 1000;
            background-color: rgba(0, 0, 0, 0.8);
            width: 50px;
            height: auto;
            border-radius: 10px;
            padding: 10px;
            box-shadow: 0px 0px 20px rgba(0, 0, 0, 0.5);
            transition: width 0.3s;
        }

        .toolbox:hover {
            width: 200px;
        }

        .toolbox-item {
            color: white;
            margin-bottom: 10px;
            cursor: pointer;
            transition: transform 0.3s;
        }

        .toolbox-item:hover {
            transform: translateX(5px);
        }
    </style>
</head>

<body>

    <!-- Toolbox -->
    <div class="toolbox">
        <div class="toolbox-item zoom" data-toggle="tooltip" data-placement="left" title="Zoom">
            <i class="fas fa-search"></i>
        </div>
        <div class="toolbox-item highlight" data-toggle="tooltip" data-placement="left" title="Highlight">
            <i class="fas fa-highlighter"></i>
        </div>
        <div class="toolbox-item draw" data-toggle="tooltip" data-placement="left" title="Draw">
            <i class="fas fa-pen"></i>
        </div>
    </div>

    <!-- JavaScript for Tool Actions -->
    <script>
        document.addEventListener('DOMContentLoaded', function () {
            const toolboxItems = document.querySelectorAll('.toolbox-item');

            // Function to change cursor style on toolbox item click
            function changeCursor(cursorStyle) {
                document.body.style.cursor = cursorStyle;
            }

            // Zoom functionality
            const zoomTool = document.querySelector('.toolbox-item.zoom');
            zoomTool.addEventListener('click', function () {
                changeCursor('url("https://www.google.com/intl/en_ALL/mapfiles/openhand.cur"), move');
                // Implement zoom functionality here
            });

            // Highlight functionality
            const highlightTool = document.querySelector('.toolbox-item.highlight');
            highlightTool.addEventListener('click', function () {
                changeCursor('url("https://www.google.com/intl/en_ALL/mapfiles/dd-via-searchbox-dragging.png"), auto');
                // Implement highlight functionality here
            });

            // Draw functionality
            const drawTool = document.querySelector('.toolbox-item.draw');
            drawTool.addEventListener('click', function () {
                changeCursor('url("https://www.google.com/intl/en_ALL/mapfiles/ms/tent.8.png"), auto');
                // Implement draw functionality here
            });
        });
    </script>

</body>

</html>
