<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>IntelliTrek - Simple Travel Planner</title>
    <link rel="stylesheet" href="style.css">
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;700&display=swap" rel="stylesheet">
</head>
<body>
    <nav class="navbar">
        <div class="nav-brand"><a href="index.html">IntelliTrek</a></div>
        <ul class="nav-links">
            <li><a href="index.html">Home</a></li>
            <li id="nav-login"><a href="login.html">Login</a></li>
            <li id="nav-signup"><a href="signup.html">Signup</a></li>
            <li id="nav-logout" class="hidden"><a href="#" id="logout-btn">Logout</a></li>
        </ul>
    </nav>

    <header>
        <h1>IntelliTrek</h1>
        <p>Your intelligent, simple travel companion</p>
    </header>

    <main class="container">
        <!-- Auth state warnings and welcomes -->
        <div id="welcome-message" class="hidden text-center" style="margin-bottom: 2rem;">
            <h2 style="color: var(--primary-color);">Welcome, <span id="user-name-display"></span>!</h2>
            <p style="color: var(--text-secondary);">Ready to plan your next adventure?</p>
        </div>
        
        <div id="auth-warning" class="hidden error-msg text-center">
            <strong>Access Limited:</strong> Please <a href="login.html" style="color: var(--primary-color); text-decoration: underline;">Login</a> or <a href="signup.html" style="color: var(--primary-color); text-decoration: underline;">Signup</a> to generate a custom itinerary.
        </div>

        <!-- Input Form Section -->
        <section class="form-section">
             <h2>Plan Your Trip</h2>
             <form id="travel-form">
                 <div class="form-group">
                     <label for="destination">Destination</label>
                     <input type="text" id="destination" placeholder="e.g. Paris, Dubai, Ooty, India" required>
                 </div>
                 <div class="form-group">
                     <label for="budget">Budget Level</label>
                     <select id="budget" required>
                         <option value="budget">Budget-Friendly</option>
                         <option value="moderate">Moderate</option>
                         <option value="luxury">Luxury</option>
                     </select>
                 </div>
                 <div class="form-group">
                     <label for="days">Number of Days</label>
                     <input type="number" id="days" min="1" max="14" value="3" required>
                 </div>
                 <button type="submit" class="submit-btn" id="generate-btn">Generate Itinerary</button>
             </form>
        </section>

        <!-- Results Section -->
        <section id="results-section" class="results-section hidden">
             <h2>Your Travel Plan to <span id="display-destination"></span></h2>
             <p class="summary">Budget: <span id="display-budget"></span> | Duration: <span id="display-days"></span> Days</p>
             <div id="itinerary-container">
                 <!-- Itinerary days will be injected here -->
             </div>
        </section>
    </main>

    <script src="script.js"></script>
</body>
</html>
