<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>IntelliTrek - Simple Travel Planner</title>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;700&display=swap" rel="stylesheet">
    <style>
        /* ==================== CSS STYLES ==================== */
        :root {
            --bg-color: #121212;
            --surface-color: #1e1e1e;
            --primary-color: #6366f1;
            --primary-hover: #4f46e5;
            --text-primary: #f3f4f6;
            --text-secondary: #9ca3af;
            --border-color: #374151;
            --accent-color: #10b981;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Inter', sans-serif;
            background-color: var(--bg-color);
            color: var(--text-primary);
            line-height: 1.6;
        }

        /* Navbar styles */
        .navbar {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 1rem 2rem;
            background-color: var(--surface-color);
            border-bottom: 1px solid var(--border-color);
        }
        .nav-brand a {
            font-size: 1.5rem;
            font-weight: 700;
            color: var(--primary-color);
            text-decoration: none;
            letter-spacing: -0.05em;
            cursor: pointer;
        }
        .nav-links {
            list-style: none;
            display: flex;
            gap: 1.5rem;
        }
        .nav-links button {
            background: none;
            border: none;
            color: var(--text-primary);
            text-decoration: none;
            font-weight: 600;
            font-size: 1rem;
            font-family: inherit;
            cursor: pointer;
            transition: color 0.2s;
        }
        .nav-links button:hover {
            color: var(--primary-hover);
        }

        header {
            text-align: center;
            padding: 3rem 1rem 2rem;
            background: linear-gradient(135deg, rgba(99,102,241,0.1) 0%, rgba(18,18,18,0) 100%);
            border-bottom: 1px solid var(--border-color);
        }

        header h1 {
            font-size: 2.5rem;
            font-weight: 700;
            color: var(--primary-color);
            margin-bottom: 0.5rem;
            letter-spacing: -0.05em;
        }

        header p {
            color: var(--text-secondary);
            font-size: 1.1rem;
        }

        .container {
            max-width: 800px;
            margin: 0 auto;
            padding: 2rem 1rem;
        }

        /* Auth & Utils */
        .error-msg {
            color: #fca5a5;
            background-color: rgba(239, 68, 68, 0.1);
            padding: 1rem;
            border-radius: 8px;
            margin-bottom: 1.5rem;
            border: 1px solid #ef4444;
        }
        .text-center {
            text-align: center;
        }

        .form-section, .results-section {
            background-color: var(--surface-color);
            border-radius: 12px;
            padding: 2rem;
            margin-bottom: 2rem;
            border: 1px solid var(--border-color);
            box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.5);
            transition: transform 0.3s ease;
        }

        h2 {
            font-size: 1.5rem;
            margin-bottom: 1.5rem;
            font-weight: 600;
            color: var(--text-primary);
        }

        .form-group {
            margin-bottom: 1.5rem;
        }

        .form-group label {
            display: block;
            margin-bottom: 0.5rem;
            font-size: 0.9rem;
            color: var(--text-secondary);
            font-weight: 600;
        }

        input, select {
            width: 100%;
            padding: 0.75rem 1rem;
            background-color: var(--bg-color);
            border: 1px solid var(--border-color);
            border-radius: 8px;
            color: var(--text-primary);
            font-size: 1rem;
            font-family: inherit;
            transition: border-color 0.2s, box-shadow 0.2s;
        }

        input:focus, select:focus {
            outline: none;
            border-color: var(--primary-color);
            box-shadow: 0 0 0 3px rgba(99, 102, 241, 0.2);
        }

        .submit-btn {
            width: 100%;
            padding: 1rem;
            background-color: var(--primary-color);
            color: white;
            border: none;
            border-radius: 8px;
            font-size: 1rem;
            font-weight: 600;
            cursor: pointer;
            transition: background-color 0.2s, transform 0.1s;
        }

        .submit-btn:hover {
            background-color: var(--primary-hover);
        }

        .submit-btn:active {
            transform: translateY(2px);
        }

        .hidden {
            display: none !important;
        }

        .summary {
            color: var(--text-secondary);
            margin-bottom: 2rem;
            padding-bottom: 1rem;
            border-bottom: 1px solid var(--border-color);
        }

        .day-card {
            background-color: var(--bg-color);
            border-radius: 8px;
            padding: 1.5rem;
            margin-bottom: 1.5rem;
            border-left: 4px solid var(--primary-color);
            animation: fadeIn 0.5s ease forwards;
            opacity: 0;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .day-title {
            font-size: 1.25rem;
            font-weight: 600;
            margin-bottom: 1rem;
            display: flex;
            align-items: center;
        }

        .day-title::before {
            content: '';
            display: inline-block;
            width: 8px;
            height: 8px;
            background-color: var(--accent-color);
            border-radius: 50%;
            margin-right: 10px;
        }

        .activity-list {
            list-style: none;
        }

        .activity-item {
            padding: 0.75rem 0;
            border-bottom: 1px solid var(--border-color);
            display: flex;
            flex-direction: column;
        }

        .activity-item:last-child {
            border-bottom: none;
            padding-bottom: 0;
        }

        .activity-time {
            font-size: 0.85rem;
            color: var(--text-secondary);
            margin-bottom: 0.25rem;
        }

        .activity-desc {
            font-size: 0.95rem;
        }
        
        .inline-btn {
            background: none;
            border: none;
            color: var(--primary-color);
            text-decoration: underline;
            font-size: inherit;
            font-family: inherit;
            cursor: pointer;
            padding: 0;
        }
    </style>
</head>
<body>
    <nav class="navbar">
        <div class="nav-brand"><a onclick="app.showView('home')">IntelliTrek</a></div>
        <ul class="nav-links">
            <li><button onclick="app.showView('home')">Home</button></li>
            <li id="nav-login"><button onclick="app.showView('login')">Login</button></li>
            <li id="nav-signup"><button onclick="app.showView('signup')">Signup</button></li>
            <li id="nav-logout" class="hidden"><button id="logout-btn">Logout</button></li>
        </ul>
    </nav>

    <header>
        <h1>IntelliTrek</h1>
        <p>Your intelligent, simple travel companion</p>
    </header>

    <main class="container">
        
        <!-- ==================== HOME VIEW ==================== -->
        <div id="view-home">
            <!-- Auth state warnings and welcomes -->
            <div id="welcome-message" class="hidden text-center" style="margin-bottom: 2rem;">
                <h2 style="color: var(--primary-color);">Welcome, <span id="user-name-display"></span>!</h2>
                <p style="color: var(--text-secondary);">Ready to plan your next adventure?</p>
            </div>
            
            <div id="auth-warning" class="hidden error-msg text-center">
                <strong>Access Limited:</strong> Please <button class="inline-btn" onclick="app.showView('login')">Login</button> or <button class="inline-btn" onclick="app.showView('signup')">Signup</button> to generate a custom itinerary.
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
        </div>

        <!-- ==================== LOGIN VIEW ==================== -->
        <div id="view-login" class="hidden">
            <section class="form-section">
                <h2>Login to IntelliTrek</h2>
                <form id="login-form">
                    <div class="error-msg hidden" id="login-error"></div>
                    <div class="form-group">
                        <label for="username">Username</label>
                        <input type="text" id="username" placeholder="Enter your username" required>
                    </div>
                    <div class="form-group">
                        <label for="password">Password</label>
                        <input type="password" id="password" placeholder="Enter your password" required>
                    </div>
                    <button type="submit" class="submit-btn">Login</button>
                </form>
                <p style="margin-top: 1.5rem; text-align: center; color: var(--text-secondary);">
                    Don't have an account? <button class="inline-btn" type="button" onclick="app.showView('signup')">Signup</button>
                </p>
            </section>
        </div>

        <!-- ==================== SIGNUP VIEW ==================== -->
        <div id="view-signup" class="hidden">
            <section class="form-section">
                <h2>Signup for IntelliTrek</h2>
                <form id="signup-form">
                    <div class="error-msg hidden" id="signup-error"></div>
                    <div class="form-group">
                        <label for="new-username">Username</label>
                        <input type="text" id="new-username" placeholder="Choose a username" required>
                    </div>
                    <div class="form-group">
                        <label for="new-password">Password</label>
                        <input type="password" id="new-password" placeholder="Create a password" required>
                    </div>
                    <button type="submit" class="submit-btn">Signup</button>
                </form>
                <p style="margin-top: 1.5rem; text-align: center; color: var(--text-secondary);">
                    Already have an account? <button class="inline-btn" type="button" onclick="app.showView('login')">Login</button>
                </p>
            </section>
        </div>

    </main>

    <script>
        /* ==================== JAVASCRIPT LOGIC ==================== */
        const app = {
            currentUser: null,

            init() {
                // Check localStorage for logged-in user
                this.currentUser = localStorage.getItem('intelliTrek_user');

                // DOM Elements bound to views
                this.views = {
                    home: document.getElementById('view-home'),
                    login: document.getElementById('view-login'),
                    signup: document.getElementById('view-signup')
                };

                this.nav = {
                    login: document.getElementById('nav-login'),
                    signup: document.getElementById('nav-signup'),
                    logout: document.getElementById('nav-logout')
                };

                this.homeEls = {
                    welcomeMessage: document.getElementById('welcome-message'),
                    userNameDisplay: document.getElementById('user-name-display'),
                    authWarning: document.getElementById('auth-warning'),
                    resultsSection: document.getElementById('results-section'),
                    itineraryContainer: document.getElementById('itinerary-container'),
                    displayDestination: document.getElementById('display-destination'),
                    displayBudget: document.getElementById('display-budget'),
                    displayDays: document.getElementById('display-days')
                };

                // Listeners
                document.getElementById('logout-btn').addEventListener('click', () => this.handleLogout());
                document.getElementById('travel-form').addEventListener('submit', (e) => this.handleGeneratePlan(e));
                document.getElementById('login-form').addEventListener('submit', (e) => this.handleLogin(e));
                document.getElementById('signup-form').addEventListener('submit', (e) => this.handleSignup(e));

                this.updateAuthUI();
                this.showView('home'); // Show home view by default
            },

            showView(viewName) {
                // Hide all views simultaneously
                Object.values(this.views).forEach(v => v.classList.add('hidden'));
                
                // Show requested view
                if (this.views[viewName]) {
                    this.views[viewName].classList.remove('hidden');
                }

                // If navigating to home, refresh the authentication states visually
                if (viewName === 'home') this.updateAuthUI();
            },

            updateAuthUI() {
                // Update Navbar Buttons dynamically
                if (this.currentUser) {
                    this.nav.login.classList.add('hidden');
                    this.nav.signup.classList.add('hidden');
                    this.nav.logout.classList.remove('hidden');

                    this.homeEls.welcomeMessage.classList.remove('hidden');
                    this.homeEls.userNameDisplay.textContent = this.currentUser;
                    this.homeEls.authWarning.classList.add('hidden');
                } else {
                    this.nav.login.classList.remove('hidden');
                    this.nav.signup.classList.remove('hidden');
                    this.nav.logout.classList.add('hidden');

                    this.homeEls.welcomeMessage.classList.add('hidden');
                }
            },

            handleLogout() {
                localStorage.removeItem('intelliTrek_user');
                this.currentUser = null;
                this.homeEls.resultsSection.classList.add('hidden'); // collapse current itinerary
                this.updateAuthUI();
                this.showView('home'); // Navigate safely home
            },

            handleLogin(e) {
                e.preventDefault();
                const user = document.getElementById('username').value.trim();
                const pass = document.getElementById('password').value;
                const errorMsg = document.getElementById('login-error');

                const storedPass = localStorage.getItem(`intelliTrek_pass_${user}`);
                
                if (storedPass && storedPass === pass) {
                    localStorage.setItem('intelliTrek_user', user);
                    this.currentUser = user;
                    
                    // Clear secure inputs & alerts
                    document.getElementById('login-form').reset();
                    errorMsg.classList.add('hidden');

                    this.showView('home'); // Switch view
                } else {
                    errorMsg.textContent = 'Invalid username or password.';
                    errorMsg.classList.remove('hidden');
                }
            },

            handleSignup(e) {
                e.preventDefault();
                const newuser = document.getElementById('new-username').value.trim();
                const newpass = document.getElementById('new-password').value;
                const errorMsg = document.getElementById('signup-error');

                // Check collisions 
                if (localStorage.getItem(`intelliTrek_pass_${newuser}`)) {
                    errorMsg.textContent = 'Username already exists.';
                    errorMsg.classList.remove('hidden');
                } else {
                    localStorage.setItem(`intelliTrek_pass_${newuser}`, newpass);
                    localStorage.setItem('intelliTrek_user', newuser);
                    this.currentUser = newuser;

                    // Clear inputs & alerts
                    document.getElementById('signup-form').reset();
                    errorMsg.classList.add('hidden');

                    this.showView('home'); // Switch view
                }
            },

            handleGeneratePlan(e) {
                e.preventDefault();

                if (!this.currentUser) {
                    this.homeEls.authWarning.classList.remove('hidden');
                    return;
                }

                this.homeEls.authWarning.classList.add('hidden');

                const destination = document.getElementById('destination').value.trim();
                const budget = document.getElementById('budget').value;
                const days = parseInt(document.getElementById('days').value);

                this.homeEls.displayDestination.textContent = destination.charAt(0).toUpperCase() + destination.slice(1);
                this.homeEls.displayBudget.textContent = budget.charAt(0).toUpperCase() + budget.slice(1);
                this.homeEls.displayDays.textContent = days;

                this.homeEls.itineraryContainer.innerHTML = '';

                // Mock logic generating customized activities loop
                for (let i = 1; i <= days; i++) {
                    const dayCard = document.createElement('div');
                    dayCard.className = 'day-card';
                    dayCard.style.animationDelay = `${i * 0.1}s`;

                    const morningActivity = this.getRandomActivity(destination, 'morning');
                    const afternoonActivity = this.getRandomActivity(destination, 'afternoon');
                    const eveningActivity = this.getRandomActivity(destination, 'evening');

                    dayCard.innerHTML = `
                        <div class="day-title">Day ${i}</div>
                        <ul class="activity-list">
                            <li class="activity-item">
                                <span class="activity-time">Morning</span>
                                <span class="activity-desc">${morningActivity}</span>
                            </li>
                            <li class="activity-item">
                                <span class="activity-time">Afternoon</span>
                                <span class="activity-desc">${afternoonActivity}</span>
                            </li>
                            <li class="activity-item">
                                <span class="activity-time">Evening</span>
                                <span class="activity-desc">${eveningActivity}</span>
                            </li>
                        </ul>
                    `;
                    this.homeEls.itineraryContainer.appendChild(dayCard);
                }

                this.homeEls.resultsSection.classList.remove('hidden');
                this.homeEls.resultsSection.scrollIntoView({ behavior: 'smooth', block: 'start' });
            },

            getRandomActivity(destination, timeOfDay) {
                const destinationData = {
                    "ooty": {
                        morning: ["Visit Doddabetta Peak", "Stroll through Botanical Gardens", "Breakfast near Ooty Lake"],
                        afternoon: ["Boating at Ooty Lake", "Visit the Tea Factory and Museum", "Lunch at a hill-view restaurant"],
                        evening: ["Ride the Nilgiri Mountain Railway", "Shop for homemade chocolates", "Enjoy sunset at Tiger Hill"]
                    },
                    "paris": {
                        morning: ["Visit the Eiffel Tower", "Breakfast at a classic French café", "Explore the Louvre Museum"],
                        afternoon: ["Walk along the Seine River", "Visit Notre-Dame Cathedral", "Shopping at Champs-Élysées"],
                        evening: ["Dinner cruise on the Seine", "Watch a cabaret show", "See the Eiffel Tower sparkling"]
                    },
                    "dubai": {
                        morning: ["Visit the view at the Palm", "Breakfast with a view of Burj Al Arab", "Ski Dubai experience"],
                        afternoon: ["Desert Safari adventure", "Visit Dubai Mall", "Go to the top of Burj Khalifa"],
                        evening: ["Watch the Dubai Fountain show", "Dinner at a Dhow Cruise", "Explore Dubai Marina"]
                    },
                    "india": {
                        morning: ["Visit a historic temple or monument", "Have traditional street food breakfast", "Explore local heritage markets"],
                        afternoon: ["Lunch featuring regional thali", "Visit a famous palace or fort", "Take an auto-rickshaw ride through the city"],
                        evening: ["Enjoy a classical dance or music show", "Dinner at a fine-dining Indian restaurant", "Walk around a bustling night bazaar"]
                    },
                    "default": {
                        morning: ["Visit the historic city center", "Take a guided walking tour", "Breakfast at a famous local cafe"],
                        afternoon: ["Lunch at a traditional street market", "Relax at the central park", "Visit an interactive art gallery"],
                        evening: ["Dinner at a top-rated local restaurant", "Experience the local nightlife", "Take a sunset photography walk"]
                    }
                };

                const lowerDest = destination.toLowerCase();
                let poolSource = destinationData.default;
                
                for (const key in destinationData) {
                    if (lowerDest.includes(key)) {
                        poolSource = destinationData[key];
                        break;
                    }
                }
                
                const pool = poolSource[timeOfDay];
                return pool[Math.floor(Math.random() * pool.length)]; // Output completely random selections securely handled without backend
            }
        };

        // Initialize App once document layout registers fully
        document.addEventListener('DOMContentLoaded', () => app.init());
    </script>
</body>
</html>

