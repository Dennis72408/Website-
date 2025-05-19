
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CSS Animations with Local Storage</title>
    <style>
        .animated-btn {
            padding: 10px 20px;
            background-color: #3498db;
            color: white;
            border: none;
            border-radius: 8px;
            transition: background-color 0.3s ease;
            cursor: pointer;
        }

        .animated-btn:hover {
            background-color: #2980b9;
        }

        .animate {
            animation: bounce 0.5s ease;
        }

        @keyframes bounce {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-10px); }
        }
    </style>
</head>
<body>
    <button id="actionBtn" class="animated-btn">Click Me</button>

    <script>
        const actionBtn = document.getElementById("actionBtn");

        // Load animation state from localStorage
        const isAnimated = localStorage.getItem("isAnimated");
        if (isAnimated === "true") {
            actionBtn.classList.add("animate");
        }

        actionBtn.addEventListener("click", () => {
            actionBtn.classList.add("animate");
            localStorage.setItem("isAnimated", "true");
            setTimeout(() => {
                actionBtn.classList.remove("animate");
                localStorage.setItem("isAnimated", "false");
            }, 500);
        });
    </script>
</body>
</html>