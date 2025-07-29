<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Day/Night Mode Toggle</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            --bg-color: #ffffff;
            --text-color: #333333;
            --toggle-bg: #f0f0f0;
            --toggle-border: #cccccc;
            --sun-color: #f39c12;
            --moon-color: #3498db;
            --theme-transition: all 0.3s ease;
        }

        .dark-mode {
            --bg-color: #1a1a1a;
            --text-color: #f0f0f0;
            --toggle-bg: #333333;
            --toggle-border: #555555;
        }

        body {
            background-color: var(--bg-color);
            color: var(--text-color);
            font-family: 'Arial', sans-serif;
            transition: var(--theme-transition);
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            padding: 20px;
        }

        .container {
            text-align: center;
            max-width: 800px;
        }

        h1 {
            margin-bottom: 30px;
        }

        .theme-toggle {
            position: relative;
            display: inline-block;
            width: 70px;
            height: 34px;
        }

        .theme-toggle input {
            opacity: 0;
            width: 0;
            height: 0;
        }

        .toggle-slider {
            position: absolute;
            cursor: pointer;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background-color: var(--toggle-bg);
            border: 1px solid var(--toggle-border);
            border-radius: 34px;
            transition: var(--theme-transition);
        }

        .toggle-slider:before {
            position: absolute;
            content: "";
            height: 26px;
            width: 26px;
            left: 4px;
            bottom: 3px;
            background-color: white;
            border-radius: 50%;
            transition: var(--theme-transition);
        }

        input:checked + .toggle-slider {
            background-color: var(--toggle-bg);
        }

        input:checked + .toggle-slider:before {
            transform: translateX(36px);
        }

        .toggle-icons {
            position: absolute;
            width: 100%;
            height: 100%;
            pointer-events: none;
        }

        .toggle-icons i {
            position: absolute;
            font-size: 16px;
            transition: var(--theme-transition);
            top: 50%;
            transform: translateY(-50%);
        }

        .sun-icon {
            left: 8px;
            color: var(--sun-color);
        }

        .moon-icon {
            right: 8px;
            color: var(--moon-color);
            display: none;
        }

        input:checked + .toggle-slider .sun-icon {
            display: none;
        }

        input:checked + .toggle-slider .moon-icon {
            display: block;
        }

        .content {
            margin-top: 30px;
            line-height: 1.6;
        }
    </style>
</head>
<body>
    <div class="container">
        
        <label class="theme-toggle">
            <input type="checkbox" id="theme-switch">
            <span class="toggle-slider">
                <div class="toggle-icons">
                    <i class="fas fa-sun sun-icon"></i>
                    <i class="fas fa-moon moon-icon"></i>
                </div>
            </span>
        </label>
        </div>
    </div>

    <script>
        const themeSwitch = document.getElementById('theme-switch');
        const body = document.body;

        // Check for saved theme preference or use preferred color scheme
        const savedTheme = localStorage.getItem('theme');
        const prefersDark = window.matchMedia('(prefers-color-scheme: dark)').matches;

        if ((savedTheme === 'dark') || (!savedTheme && prefersDark)) {
            body.classList.add('dark-mode');
            themeSwitch.checked = true;
        }

        // Toggle theme when switch is clicked
        themeSwitch.addEventListener('change', function() {
            if (this.checked) {
                body.classList.add('dark-mode');
                localStorage.setItem('theme', 'dark');
            } else {
                body.classList.remove('dark-mode');
                localStorage.setItem('theme', 'light');
            }
        });

        // Watch for system theme changes
        window.matchMedia('(prefers-color-scheme: dark)').addEventListener('change', e => {
            const newPrefersDark = e.matches;
            if (newPrefersDark) {
                body.classList.add('dark-mode');
                themeSwitch.checked = true;
            } else {
                body.classList.remove('dark-mode');
                themeSwitch.checked = false;
            }
        });
    </script>
</br>
    
<div>
<main>
  <h1>everything - everyone i loved once</h1>
  <!-- TODO: Add link to bunny photos -->
  <p>hey</p>
    <a href="https://t3.ftcdn.net/jpg/02/36/99/22/360_F_236992283_sNOxCVQeFLd5pdqaKGh8DRGMZy7P4XKm.jpg"></a>
  <img src="https://t3.ftcdn.net/jpg/02/36/99/22/360_F_236992283_sNOxCVQeFLd5pdqaKGh8DRGMZy7P4XKm.jpg" alt="bunny">
</main></div>

</body>
</html>
