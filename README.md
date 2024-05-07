<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>KODAMA</title>
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.4/css/all.min.css">
    <style>
        /* Styles pour la boîte à outils */
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
            padding: 8px;
            cursor: pointer;
            transition: background-color 0.3s;
        }

        .toolbox-item:hover {
            background-color: #4CAF50;
        }
    </style>
</head>

<body>

    <!-- Boîte à outils -->
    <div class="toolbox">
        <div class="toolbox-dropdown">
            <button class="toolbox-dropdown-btn" onclick="toggleToolboxDropdown()">
                <i class="fas fa-cog"></i>
            </button>
            <div class="toolbox-dropdown-content">
                <div class="toolbox-item" data-tooltip="Zoom" onclick="toggleZoom()">
                    <i class="fas fa-search"></i>
                </div>
                <div class="toolbox-item" data-tooltip="Surligner" onclick="toggleHighlight()">
                    <i class="fas fa-highlighter"></i>
                </div>
                <div class="toolbox-item" data-tooltip="Dessiner" onclick="toggleDrawing()">
                    <i class="fas fa-pen"></i>
                </div>
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
        // Toggle Toolbox Dropdown
        function toggleToolboxDropdown() {
            const dropdownContent = document.querySelector('.toolbox-dropdown-content');
            dropdownContent.classList.toggle('toolbox-dropdown-content-show');
        }

        // Toggle Zoom Function
        function toggleZoom() {
            const body = document.querySelector('body');
            const zoomMarker = document.createElement('div');
            zoomMarker.style.position = 'absolute';
            zoomMarker.style.width = '100px';
            zoomMarker.style.height = '100px';
            zoomMarker.style.border = '2px solid #000';
            zoomMarker.style.pointerEvents = 'none';
            zoomMarker.style.background = 'rgba(255, 255, 255, 0.5)';
            zoomMarker.style.zIndex = '9999';
            zoomMarker.style.cursor = 'zoom-in';
            body.appendChild(zoomMarker);

            let isDragging = false;
            let startX, startY;

            zoomMarker.addEventListener('mousedown', function (e) {
                isDragging = true;
                startX = e.clientX - parseInt(zoomMarker.style.left);
                startY = e.clientY - parseInt(zoomMarker.style.top);
            });

            body.addEventListener('mousemove', function (e) {
                if (isDragging) {
                    const left = e.clientX - startX;
                    const top = e.clientY - startY;
                    zoomMarker.style.left = left + 'px';
                    zoomMarker.style.top = top + 'px';
                }
            });

            body.addEventListener('mouseup', function () {
                isDragging = false;
            });

            body.addEventListener('mouseleave', function () {
                isDragging = false;
            });
        }

        // Toggle Highlight Function
        function toggleHighlight() {
            const body = document.querySelector('body');
            const highlightMarker = document.createElement('div');
            highlightMarker.style.position = 'absolute';
            highlightMarker.style.backgroundColor = 'rgba(255, 255, 0, 0.5)';
            highlightMarker.style.pointerEvents = 'none';
            highlightMarker.style.zIndex = '9999';
            body.appendChild(highlightMarker);

            let isHighlighting = false;
            let startX, startY;

            body.addEventListener('mousedown', function (e) {
                if (e.button === 0) {
                    isHighlighting = true;
                    startX = e.clientX;
                    startY = e.clientY;
                    highlightMarker.style.left = startX + 'px';
                    highlightMarker.style.top = startY + 'px';
                }
            });

            body.addEventListener('mousemove', function (e) {
                if (isHighlighting) {
                    const width = e.clientX - startX;
                    const height = e.clientY - startY;
                    highlightMarker.style.width = width + 'px';
                    highlightMarker.style.height = height + 'px';
                }
            });

            body.addEventListener('mouseup', function () {
                isHighlighting = false;
                highlightMarker.style.width = '';
                highlightMarker.style.height = '';
            });
        }

        // Toggle Drawing Function
        function toggleDrawing() {
            const body = document.querySelector('body');
            const drawingCanvas = document.createElement('canvas');
            drawingCanvas.style.position = 'absolute';
            drawingCanvas.style.pointerEvents = 'none';
            drawingCanvas.style.zIndex = '9999';
            body.appendChild(drawingCanvas);

            const ctx = drawingCanvas.getContext('2d');
            let isDrawing = false;
            let startX, startY;

            body.addEventListener('mousedown', function (e) {
                if (e.button === 0) {
                    isDrawing = true;
                    startX = e.clientX;
                    startY = e.clientY;
                }
            });

            body.addEventListener('mousemove', function (e) {
                if (isDrawing) {
                    ctx.beginPath();
                    ctx.moveTo(startX, startY);
                    ctx.lineTo(e.clientX, e.clientY);
                    ctx.strokeStyle = '#000';
                    ctx.lineWidth = 2;
                    ctx.stroke();
                    startX = e.clientX;
                    startY = e.clientY;
                }
            });

            body.addEventListener('mouseup', function () {
                isDrawing = false;
            });

            body.addEventListener('mouseleave', function () {
                isDrawing = false;
            });
        }
    </script>
</body>

</html>
