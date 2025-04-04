<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Minicurso: Navegação Segura na Internet</title>
    <meta name="description" content="Minicurso online ensinando sobre golpes virtuais, fake news e privacidade digital">
    <meta name="theme-color" content="#2b5797">
    <link rel="canonical" href="https://seusite.com/navegacao-segura" />
    
    <!-- Open Graph / Social Media -->
    <meta property="og:title" content="Minicurso: Como Navegar na Internet com Segurança" />
    <meta property="og:description" content="Série de vídeos ensinando sobre golpes virtuais, fake news e privacidade digital" />
    <meta property="og:image" content="https://seusite.com/images/navegacao-segura-social.png" />
    <meta property="og:url" content="https://seusite.com/navegacao-segura" />
    <meta property="og:type" content="website" />
    <meta name="twitter:card" content="summary_large_image" />
    
    <!-- Favicons -->
    <link rel="icon" href="/favicon.ico" sizes="any">
    <link rel="icon" href="/icon.svg" type="image/svg+xml">
    <link rel="apple-touch-icon" href="/apple-touch-icon.png">
    <link rel="manifest" href="/site.webmanifest">
    
    <!-- Preload de recursos importantes -->
    <link rel="preload" href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600&display=swap" as="style">
    <link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600&display=swap">
    
    <!-- CSS dividido em seções lógicas -->
    <style>
        /* ===== RESET E VARIÁVEIS ===== */
        :root {
            --primary-color: #00a023;
            --primary-dark: #008b2a;
            --secondary-color: #11e88e;
            --background-dark: #121212;
            --background-light: #1e1e1e;
            --background-lighter: #2d2d2d;
            --text-color: #f0f0f0;
            --text-contrast: #fff;
            --border-color: #444;
            --shadow-color: rgba(255, 255, 255, 0.205);
            --transition-fast: 0.2s;
            --transition-medium: 0.3s;
            --border-radius-sm: 4px;
            --border-radius-md: 8px;
            --border-radius-lg: 10px;
            --focus-outline: 3px solid var(--primary-color);
            --focus-offset: 2px;
            --youtube-red: #ff0000;
            --youtube-dark: #282828;
            --youtube-light: #f9f9f9;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        /* ===== BASE E TIPOGRAFIA ===== */
        html {
            font-size: 16px;
            scroll-behavior: smooth;
        }

        @media (min-width: 768px) {
            html {
                font-size: 18px;
            }
        }

        body {
            font-family: 'Poppins', sans-serif;
            background-color: var(--background-dark);
            color: var(--text-color);
            line-height: 1.6;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
        }

        h1, h2, h3 {
            line-height: 1.2;
            font-weight: 600;
        }

        h1 {
            font-size: 2.5rem;
        }

        h2 {
            font-size: 1.8rem;
        }

        h3 {
            font-size: 1.4rem;
        }

        p, li {
            margin-bottom: 1em;
        }

        a {
            color: var(--primary-color);
            text-decoration: underline;
            text-underline-offset: var(--focus-offset);
            transition: color var(--transition-fast);
        }

        a:hover, a:focus {
            color: var(--primary-dark);
            text-decoration: none;
        }

        :focus {
            outline: var(--focus-outline);
            outline-offset: var(--focus-offset);
        }

        /* ===== ACESSIBILIDADE ===== */
        .skip-link {
            position: absolute;
            top: -40px;
            left: 0;
            background: var(--primary-color);
            color: var(--text-contrast);
            padding: 8px;
            z-index: 100;
            transition: top var(--transition-medium);
        }

        .skip-link:focus {
            top: 0;
        }

        .sr-only {
            position: absolute;
            width: 1px;
            height: 1px;
            padding: 0;
            margin: -1px;
            overflow: hidden;
            clip: rect(0, 0, 0, 0);
            white-space: nowrap;
            border-width: 0;
        }

        @media (prefers-contrast: more) {
            body {
                background-color: var(--background-dark);
                color: var(--text-contrast);
            }
            
            a, button {
                border: 2px solid currentColor;
            }
        }

        @media (prefers-reduced-motion: reduce) {
            * {
                animation-duration: 0.01ms !important;
                animation-iteration-count: 1 !important;
                transition-duration: 0.01ms !important;
                scroll-behavior: auto !important;
            }
        }

        /* ===== LAYOUT ===== */
        .container {
            width: 100%;
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }

        header {
            background-color: var(--background-lighter);
            padding: 20px 0;
            text-align: center;
        }

        header h1 {
            color: var(--primary-color);
            margin-bottom: 10px;
            letter-spacing: 1px;
        }

        main {
            flex: 1;
            padding: 20px;
            max-width: 800px;
            margin: 0 auto;
        }

        footer {
            background-color: var(--background-lighter);
            padding: 20px;
            text-align: center;
            margin-top: 30px;
        }

        /* ===== COMPONENTES ===== */
        /* Botões */
        .button {
            display: inline-block;
            background-color: var(--primary-color);
            color: var(--text-contrast);
            border: none;
            padding: 10px 20px;
            border-radius: var(--border-radius-sm);
            cursor: pointer;
            font-size: 1rem;
            margin: 5px;
            transition: background-color var(--transition-medium);
            text-align: center;
            position: relative;
            overflow: hidden;
        }

        .button:hover {
            background-color: var(--primary-dark);
        }

        .button:focus:not(:active)::after {
            content: '';
            position: absolute;
            top: 50%;
            left: 50%;
            width: 5px;
            height: 5px;
            background: rgba(255, 255, 255, 0.5);
            opacity: 0;
            border-radius: 100%;
            transform: scale(1, 1) translate(-50%);
            transform-origin: 50% 50%;
            animation: ripple 0.6s ease-out;
        }

        .button[aria-expanded="true"] {
            background-color: var(--primary-dark);
            font-weight: bold;
        }

        .button:disabled {
            opacity: 0.6;
            cursor: not-allowed;
        }

        .button-large {
            padding: 15px 30px;
            font-size: 1.1rem;
            border-radius: var(--border-radius-md);
            transition: transform var(--transition-fast);
        }

        .button-large:hover {
            transform: scale(1.05);
        }

        .button-large:active {
            transform: scale(0.95);
        }

        .button-secondary {
            background-color: var(--secondary-color);
        }

        .button-secondary:hover {
            background-color: #c50f1f;
        }

        /* Estilo do YouTube para botões */
        .youtube-button {
            background-color: var(--youtube-red);
            color: white;
            border-radius: 2px;
            padding: 10px 16px;
            font-weight: 500;
            text-transform: uppercase;
            letter-spacing: 0.5px;
            border: none;
            transition: background-color 0.2s;
        }

        .youtube-button:hover {
            background-color: #cc0000;
        }

        @keyframes ripple {
            0% {
                transform: scale(0, 0);
                opacity: 0.5;
            }
            100% {
                transform: scale(20, 20);
                opacity: 0;
            }
        }

        /* Abas */
        .tab {
            display: none;
        }

        .tab.active {
            display: block;
        }

        /* Seções de conteúdo */
        section {
            margin-bottom: 30px;
            background-color: var(--background-light);
            padding: 20px;
            border-radius: var(--border-radius-md);
            box-shadow: 0 2px 4px var(--shadow-color);
        }

        section h2 {
            color: var(--primary-color);
            margin-bottom: 15px;
        }

        section ul, section ol {
            margin-left: 20px;
            margin-bottom: 1em;
        }

        section li {
            margin-bottom: 10px;
        }

        /* Imagens */
        .section-image {
            width: 100%;
            max-width: 400px;
            height: auto;
            margin: 20px auto;
            display: block;
            border-radius: var(--border-radius-md);
        }

        /* Vídeos - Estilo do YouTube */
        .video-container {
            position: relative;
            padding-bottom: 56.25%; /* 16:9 */
            height: 0;
            overflow: hidden;
            margin: 20px 0;
            background-color: #000;
            border-radius: var(--border-radius-md);
        }

        .video-container iframe {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            border: none;
        }

        /* Barra de informações do vídeo (estilo YouTube) */
        .video-info {
            padding: 12px 0;
        }

        .video-title {
            font-size: 1.2rem;
            font-weight: 600;
            margin-bottom: 8px;
            color: var(--text-contrast);
        }

        .video-meta {
            display: flex;
            justify-content: space-between;
            color: #aaa;
            font-size: 0.9rem;
            margin-bottom: 8px;
        }

        .video-actions {
            display: flex;
            gap: 8px;
            margin-top: 12px;
        }

        .video-action {
            display: flex;
            align-items: center;
            gap: 6px;
            background: transparent;
            border: none;
            color: var(--text-color);
            cursor: pointer;
            font-size: 0.9rem;
            padding: 6px 12px;
            border-radius: 18px;
            transition: background-color 0.2s;
        }

        .video-action:hover {
            background-color: rgba(255, 255, 255, 0.1);
        }

        .video-action.active {
            color: var(--youtube-red);
        }

        .video-action svg {
            width: 18px;
            height: 18px;
            fill: currentColor;
        }

        /* Descrição do vídeo (estilo YouTube) */
        .video-description {
            background-color: var(--background-lighter);
            padding: 12px;
            border-radius: var(--border-radius-sm);
            margin-top: 12px;
            font-size: 0.9rem;
            line-height: 1.5;
        }

        .video-description-toggle {
            color: var(--text-color);
            background: none;
            border: none;
            cursor: pointer;
            font-weight: 600;
            margin-top: 8px;
            display: flex;
            align-items: center;
            gap: 4px;
        }

        .video-description-toggle svg {
            width: 16px;
            height: 16px;
            fill: currentColor;
            transition: transform 0.2s;
        }

        .video-description-toggle.collapsed svg {
            transform: rotate(-90deg);
        }

        /* Cartões de módulo */
        .module-card {
            background-color: var(--background-lighter);
            border-radius: var(--border-radius-md);
            padding: 20px;
            margin-bottom: 20px;
            transition: transform var(--transition-fast);
        }

        .module-card:hover {
            transform: translateY(-5px);
        }

        .module-card h3 {
            color: var(--primary-color);
            margin-bottom: 10px;
        }

        .module-card .meta {
            font-size: 0.9rem;
            color: #aaa;
            margin-bottom: 15px;
        }

        /* Chatbot */
        .chatbot {
            position: fixed;
            bottom: 20px;
            right: 20px;
            width: 350px;
            max-height: 80vh;
            background-color: var(--background-light);
            border-radius: var(--border-radius-lg);
            box-shadow: 0 2px 10px var(--shadow-color);
            display: none;
            flex-direction: column;
            overflow: hidden;
            z-index: 1000;
        }

        @media (max-width: 600px) {
            .chatbot {
                width: calc(100% - 40px);
                max-width: 100%;
                bottom: 10px;
                right: 10px;
            }
        }

        .chatbot.open {
            display: flex;
        }

        .chatbot header {
            background-color: var(--background-lighter);
            color: var(--text-contrast);
            padding: 10px;
            text-align: center;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .chatbot .messages {
            flex: 1;
            padding: 10px;
            overflow-y: auto;
            background-color: var(--background-light);
            border-bottom: 1px solid var(--border-color);
            max-height: 300px;
        }

        .chatbot .message {
            margin-bottom: 10px;
            padding: 8px 12px;
            border-radius: var(--border-radius-md);
            max-width: 80%;
            word-wrap: break-word;
        }

        .chatbot .message.user {
            background-color: var(--primary-color);
            color: var(--text-contrast);
            margin-left: auto;
        }

        .chatbot .message.bot {
            background-color: var(--background-lighter);
            color: var(--text-contrast);
            margin-right: auto;
        }

        .chatbot .message.bot strong {
            color: var(--primary-color);
        }

        .chatbot .message.bot[data-is-tip] {
            background-color: var(--background-lighter);
            border-left: 4px solid var(--primary-color);
            font-size: 0.9rem;
            margin-top: -5px;
        }

        .chatbot input {
            width: 100%;
            padding: 10px;
            border: none;
            border-top: 1px solid var(--border-color);
            outline: none;
            font-size: 1rem;
            background-color: var(--background-lighter);
            color: var(--text-contrast);
        }

        .chatbot-toggle {
            position: fixed;
            bottom: 20px;
            right: 20px;
            z-index: 999;
        }

        @media (max-width: 600px) {
            .chatbot-toggle {
                bottom: 10px;
                right: 10px;
            }
        }

        /* Quick questions */
        .quick-questions {
            padding: 10px;
            background-color: var(--background-lighter);
            border-radius: var(--border-radius-md);
            margin-top: 10px;
        }

        .quick-questions p {
            margin-bottom: 8px;
            font-size: 0.9rem;
        }

        .quick-questions ul {
            list-style: none;
            padding: 0;
            margin: 0;
        }

        .quick-questions li {
            margin-bottom: 5px;
        }

        .quick-question {
            background: none;
            border: none;
            color: var(--primary-color);
            text-decoration: underline;
            cursor: pointer;
            padding: 0;
            font-size: 0.9rem;
        }

        .quick-question:hover {
            text-decoration: none;
        }

        /* Modal */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.7);
            justify-content: center;
            align-items: center;
            z-index: 2000;
        }

        .modal.open {
            display: flex;
        }

        .modal-content {
            background-color: var(--background-light);
            padding: 20px;
            border-radius: var(--border-radius-md);
            width: 90%;
            max-width: 400px;
            box-shadow: 0 2px 10px var(--shadow-color);
        }

        @media (prefers-reduced-motion: no-preference) {
            .modal-content {
                animation: fadeIn 0.3s ease-out;
            }
            
            @keyframes fadeIn {
                from { opacity: 0; transform: translateY(20px); }
                to { opacity: 1; transform: translateY(0); }
            }
        }

        .modal-content h2 {
            color: var(--primary-color);
            margin-bottom: 15px;
        }

        .modal-content label {
            display: block;
            margin-bottom: 5px;
            font-size: 0.9rem;
        }

        .modal-content input {
            width: 100%;
            padding: 10px;
            margin-bottom: 15px;
            border: 1px solid var(--border-color);
            border-radius: var(--border-radius-sm);
            background-color: var(--background-lighter);
            color: var(--text-contrast);
        }

        .modal-content button {
            width: 100%;
        }

        /* Loading */
        .loading {
            padding: 10px;
            text-align: center;
            color: var(--primary-color);
            font-weight: bold;
        }

        /* Alertas */
        .alert {
            padding: 15px;
            border-radius: var(--border-radius-sm);
            margin-bottom: 20px;
        }

        .alert-warning {
            background-color: rgba(232, 17, 35, 0.2);
            border-left: 4px solid var(--secondary-color);
        }

        .alert-info {
            background-color: rgba(43, 87, 151, 0.2);
            border-left: 4px solid var(--primary-color);
        }

        /* Progresso */
        .progress-container {
            width: 100%;
            background-color: var(--background-lighter);
            border-radius: var(--border-radius-md);
            margin: 20px 0;
        }

        .progress-bar {
            height: 20px;
            background-color: var(--primary-color);
            border-radius: var(--border-radius-md);
            width: 0%;
            transition: width 0.5s ease;
        }

        /* Ícones */
        .icon {
            display: inline-block;
            width: 24px;
            height: 24px;
            vertical-align: middle;
            margin-right: 8px;
        }
    </style>
</head>
<body>
    <a href="#main-content" class="skip-link">Pular para conteúdo principal</a>

    <header role="banner">
        <div class="container">
            <h1 id="site-title">Navegação Segura na Internet</h1>
            <p>Minicurso online sobre golpes virtuais, fake news e privacidade digital</p>
            <nav aria-label="Navegação principal">
                <div class="header-buttons">
                    <button class="button" onclick="showTab('modules')" aria-controls="modules" aria-expanded="true">Módulos</button>
                    <button class="button" onclick="showTab('resources')" aria-controls="resources" aria-expanded="false">Recursos</button>
                    <button class="button" onclick="showTab('about')" aria-controls="about" aria-expanded="false">Sobre</button>
                </div>
            </nav>
        </div>
    </header>

    <main id="main-content" role="main">
        <!-- Aba: Módulos -->
        <div id="modules" class="tab active" role="tabpanel" aria-labelledby="modules-tab">
            <section>
                <h2>Módulos do Minicurso</h2>
                <p>Aprenda a navegar na internet com segurança através dos nossos módulos educativos. Cada módulo contém vídeos curtos e materiais complementares.</p>
                
                <div class="progress-container">
                    <div class="progress-bar" id="course-progress"></div>
                </div>
                
                <div class="module-card">
                    <h3>Módulo 1: Golpes Virtuais</h3>
                    <div class="meta">3 vídeos • 15 minutos • <span id="module1-status">Não iniciado</span></div>
                    <p>Aprenda a identificar e evitar os principais golpes na internet como phishing, falsos prêmios e fraudes bancárias.</p>
                    
                    <!-- Player de vídeo com estilo YouTube -->
                    <div class="video-container">
                        <iframe src="./videoplayback.mp4" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
                    </div>
                    
                    <!-- Informações do vídeo estilo YouTube -->
                    <div class="video-info">
                        <h3 class="video-title">Como identificar golpes de phishing na internet</h3>
                        <div class="video-meta">
                            <span>1.234 visualizações</span>
                            <span>Publicado em 15/05/2023</span>
                        </div>
                        
                        <div class="video-actions">
                            <button class="video-action" onclick="toggleLike(this)">
                                <svg viewBox="0 0 24 24">
                                    <path d="M1 21h4V9H1v12zm22-11c0-1.1-.9-2-2-2h-6.31l.95-4.57.03-.32c0-.41-.17-.79-.44-1.06L14.17 1 7.59 7.59C7.22 7.95 7 8.45 7 9v10c0 1.1.9 2 2 2h9c.83 0 1.54-.5 1.84-1.22l3.02-7.05c.09-.23.14-.47.14-.73v-1.91l-.01-.01L23 10z"></path>
                                </svg>
                                <span>Gostei</span>
                            </button>
                            
                            <button class="video-action" onclick="toggleDislike(this)">
                                <svg viewBox="0 0 24 24">
                                    <path d="M15 3H6c-.83 0-1.54.5-1.84 1.22l-3.02 7.05c-.09.23-.14.47-.14.73v1.91l.01.01L1 14c0 1.1.9 2 2 2h6.31l-.95 4.57-.03.32c0 .41.17.79.44 1.06L9.83 23l6.59-6.59c.36-.36.58-.86.58-1.41V5c0-1.1-.9-2-2-2zm4 0v12h4V3h-4z"></path>
                                </svg>
                                <span>Não gostei</span>
                            </button>
                            
                            <button class="video-action" onclick="shareVideo()">
                                <svg viewBox="0 0 24 24">
                                    <path d="M18 16.08c-.76 0-1.44.3-1.96.77L8.91 12.7c.05-.23.09-.46.09-.7s-.04-.47-.09-.7l7.05-4.11c.54.5 1.25.81 2.04.81 1.66 0 3-1.34 3-3s-1.34-3-3-3-3 1.34-3 3c0 .24.04.47.09.7L8.04 9.81C7.5 9.31 6.79 9 6 9c-1.66 0-3 1.34-3 3s1.34 3 3 3c.79 0 1.5-.31 2.04-.81l7.12 4.16c-.05.21-.08.43-.08.65 0 1.61 1.31 2.92 2.92 2.92 1.61 0 2.92-1.31 2.92-2.92s-1.31-2.92-2.92-2.92z"></path>
                                </svg>
                                <span>Compartilhar</span>
                            </button>
                        </div>
                        
                        <div class="video-description">
                            <p>Neste vídeo, você aprenderá a identificar os principais golpes virtuais que circulam na internet, incluindo phishing, falsos prêmios e fraudes bancárias. Vamos mostrar exemplos reais e ensinar como se proteger.</p>
                            <button class="video-description-toggle collapsed" onclick="toggleDescription(this)">
                                <svg viewBox="0 0 24 24">
                                    <path d="M16.59 8.59L12 13.17 7.41 8.59 6 10l6 6 6-6z"></path>
                                </svg>
                                <span>Mostrar mais</span>
                            </button>
                        </div>
                    </div>
                    
                    <button class="button button-secondary" onclick="markModuleComplete(1)">Marcar como concluído</button>
                </div>
                
                <div class="module-card">
                    <h3>Módulo 2: Fake News</h3>
                    <div class="meta">4 vídeos • 20 minutos • <span id="module2-status">Não iniciado</span></div>
                    <p>Descubra como identificar notícias falsas, verificar fontes e não compartilhar desinformação.</p>
                    
                    <div class="video-container">
                        <iframe src="./videoplayback (1).mp4" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
                    </div>
                    
                    <div class="video-info">
                        <h3 class="video-title">Como identificar e combater fake news</h3>
                        <div class="video-meta">
                            <span>2.567 visualizações</span>
                            <span>Publicado em 22/05/2023</span>
                        </div>
                        
                        <div class="video-actions">
                            <button class="video-action" onclick="toggleLike(this)">
                                <svg viewBox="0 0 24 24">
                                    <path d="M1 21h4V9H1v12zm22-11c0-1.1-.9-2-2-2h-6.31l.95-4.57.03-.32c0-.41-.17-.79-.44-1.06L14.17 1 7.59 7.59C7.22 7.95 7 8.45 7 9v10c0 1.1.9 2 2 2h9c.83 0 1.54-.5 1.84-1.22l3.02-7.05c.09-.23.14-.47.14-.73v-1.91l-.01-.01L23 10z"></path>
                                </svg>
                                <span>Gostei</span>
                            </button>
                            
                            <button class="video-action" onclick="toggleDislike(this)">
                                <svg viewBox="0 0 24 24">
                                    <path d="M15 3H6c-.83 0-1.54.5-1.84 1.22l-3.02 7.05c-.09.23-.14.47-.14.73v1.91l.01.01L1 14c0 1.1.9 2 2 2h6.31l-.95 4.57-.03.32c0 .41.17.79.44 1.06L9.83 23l6.59-6.59c.36-.36.58-.86.58-1.41V5c0-1.1-.9-2-2-2zm4 0v12h4V3h-4z"></path>
                                </svg>
                                <span>Não gostei</span>
                            </button>
                            
                            <button class="video-action" onclick="shareVideo()">
                                <svg viewBox="0 0 24 24">
                                    <path d="M18 16.08c-.76 0-1.44.3-1.96.77L8.91 12.7c.05-.23.09-.46.09-.7s-.04-.47-.09-.7l7.05-4.11c.54.5 1.25.81 2.04.81 1.66 0 3-1.34 3-3s-1.34-3-3-3-3 1.34-3 3c0 .24.04.47.09.7L8.04 9.81C7.5 9.31 6.79 9 6 9c-1.66 0-3 1.34-3 3s1.34 3 3 3c.79 0 1.5-.31 2.04-.81l7.12 4.16c-.05.21-.08.43-.08.65 0 1.61 1.31 2.92 2.92 2.92 1.61 0 2.92-1.31 2.92-2.92s-1.31-2.92-2.92-2.92z"></path>
                                </svg>
                                <span>Compartilhar</span>
                            </button>
                        </div>
                        
                        <div class="video-description">
                            <p>Neste vídeo, mostramos técnicas para identificar notícias falsas e como verificar a veracidade de informações antes de compartilhar. Aprenda a usar ferramentas de fact-checking e a reconhecer os sinais de desinformação.</p>
                            <button class="video-description-toggle collapsed" onclick="toggleDescription(this)">
                                <svg viewBox="0 0 24 24">
                                    <path d="M16.59 8.59L12 13.17 7.41 8.59 6 10l6 6 6-6z"></path>
                                </svg>
                                <span>Mostrar mais</span>
                            </button>
                        </div>
                    </div>
                    
                    <button class="button button-secondary" onclick="markModuleComplete(2)">Marcar como concluído</button>
                </div>
                
                <div class="module-card">
                    <h3>Módulo 3: Privacidade Digital</h3>
                    <div class="meta">3 vídeos • 18 minutos • <span id="module3-status">Não iniciado</span></div>
                    <p>Proteja seus dados pessoais, configure privacidade em redes sociais e evite vazamentos de informações.</p>
                    
                    <div class="video-container">
                        <iframe src="./videoplayback (2).mp4" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
                    </div>
                    
                    <div class="video-info">
                        <h3 class="video-title">Configurando a privacidade nas redes sociais</h3>
                        <div class="video-meta">
                            <span>1.890 visualizações</span>
                            <span>Publicado em 29/05/2023</span>
                        </div>
                        
                        <div class="video-actions">
                            <button class="video-action" onclick="toggleLike(this)">
                                <svg viewBox="0 0 24 24">
                                    <path d="M1 21h4V9H1v12zm22-11c0-1.1-.9-2-2-2h-6.31l.95-4.57.03-.32c0-.41-.17-.79-.44-1.06L14.17 1 7.59 7.59C7.22 7.95 7 8.45 7 9v10c0 1.1.9 2 2 2h9c.83 0 1.54-.5 1.84-1.22l3.02-7.05c.09-.23.14-.47.14-.73v-1.91l-.01-.01L23 10z"></path>
                                </svg>
                                <span>Gostei</span>
                            </button>
                            
                            <button class="video-action" onclick="toggleDislike(this)">
                                <svg viewBox="0 0 24 24">
                                    <path d="M15 3H6c-.83 0-1.54.5-1.84 1.22l-3.02 7.05c-.09.23-.14.47-.14.73v1.91l.01.01L1 14c0 1.1.9 2 2 2h6.31l-.95 4.57-.03.32c0 .41.17.79.44 1.06L9.83 23l6.59-6.59c.36-.36.58-.86.58-1.41V5c0-1.1-.9-2-2-2zm4 0v12h4V3h-4z"></path>
                                </svg>
                                <span>Não gostei</span>
                            </button>
                            
                            <button class="video-action" onclick="shareVideo()">
                                <svg viewBox="0 0 24 24">
                                    <path d="M18 16.08c-.76 0-1.44.3-1.96.77L8.91 12.7c.05-.23.09-.46.09-.7s-.04-.47-.09-.7l7.05-4.11c.54.5 1.25.81 2.04.81 1.66 0 3-1.34 3-3s-1.34-3-3-3-3 1.34-3 3c0 .24.04.47.09.7L8.04 9.81C7.5 9.31 6.79 9 6 9c-1.66 0-3 1.34-3 3s1.34 3 3 3c.79 0 1.5-.31 2.04-.81l7.12 4.16c-.05.21-.08.43-.08.65 0 1.61 1.31 2.92 2.92 2.92 1.61 0 2.92-1.31 2.92-2.92s-1.31-2.92-2.92-2.92z"></path>
                                </svg>
                                <span>Compartilhar</span>
                            </button>
                        </div>
                        
                        <div class="video-description">
                            <p>Neste vídeo, mostramos passo a passo como configurar as opções de privacidade nas principais redes sociais (Facebook, Instagram, Twitter) para proteger seus dados pessoais e limitar quem pode ver suas informações.</p>
                            <button class="video-description-toggle collapsed" onclick="toggleDescription(this)">
                                <svg viewBox="0 0 24 24">
                                    <path d="M16.59 8.59L12 13.17 7.41 8.59 6 10l6 6 6-6z"></path>
                                </svg>
                                <span>Mostrar mais</span>
                            </button>
                        </div>
                    </div>
                    
                    <button class="button button-secondary" onclick="markModuleComplete(3)">Marcar como concluído</button>
                </div>
                
                <div class="module-card">
                    <h3>Módulo 4: Segurança em Redes Sociais</h3>
                    <div class="meta">2 vídeos • 12 minutos • <span id="module4-status">Não iniciado</span></div>
                    <p>Configurações de segurança, reconhecimento de perfis falsos e proteção contra cyberbullying.</p>
                    
                    <div class="video-container">
                        <iframe src="./videoplayback (3).mp4" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
                    </div>
                    
                    <div class="video-info">
                        <h3 class="video-title">Protegendo suas contas em redes sociais</h3>
                        <div class="video-meta">
                            <span>1.432 visualizações</span>
                            <span>Publicado em 05/06/2023</span>
                        </div>
                        
                        <div class="video-actions">
                            <button class="video-action" onclick="toggleLike(this)">
                                <svg viewBox="0 0 24 24">
                                    <path d="M1 21h4V9H1v12zm22-11c0-1.1-.9-2-2-2h-6.31l.95-4.57.03-.32c0-.41-.17-.79-.44-1.06L14.17 1 7.59 7.59C7.22 7.95 7 8.45 7 9v10c0 1.1.9 2 2 2h9c.83 0 1.54-.5 1.84-1.22l3.02-7.05c.09-.23.14-.47.14-.73v-1.91l-.01-.01L23 10z"></path>
                                </svg>
                                <span>Gostei</span>
                            </button>
                            
                            <button class="video-action" onclick="toggleDislike(this)">
                                <svg viewBox="0 0 24 24">
                                    <path d="M15 3H6c-.83 0-1.54.5-1.84 1.22l-3.02 7.05c-.09.23-.14.47-.14.73v1.91l.01.01L1 14c0 1.1.9 2 2 2h6.31l-.95 4.57-.03.32c0 .41.17.79.44 1.06L9.83 23l6.59-6.59c.36-.36.58-.86.58-1.41V5c0-1.1-.9-2-2-2zm4 0v12h4V3h-4z"></path>
                                </svg>
                                <span>Não gostei</span>
                            </button>
                            
                            <button class="video-action" onclick="shareVideo()">
                                <svg viewBox="0 0 24 24">
                                    <path d="M18 16.08c-.76 0-1.44.3-1.96.77L8.91 12.7c.05-.23.09-.46.09-.7s-.04-.47-.09-.7l7.05-4.11c.54.5 1.25.81 2.04.81 1.66 0 3-1.34 3-3s-1.34-3-3-3-3 1.34-3 3c0 .24.04.47.09.7L8.04 9.81C7.5 9.31 6.79 9 6 9c-1.66 0-3 1.34-3 3s1.34 3 3 3c.79 0 1.5-.31 2.04-.81l7.12 4.16c-.05.21-.08.43-.08.65 0 1.61 1.31 2.92 2.92 2.92 1.61 0 2.92-1.31 2.92-2.92s-1.31-2.92-2.92-2.92z"></path>
                                </svg>
                                <span>Compartilhar</span>
                            </button>
                        </div>
                        
                        <div class="video-description">
                            <p>Neste vídeo, ensinamos como proteger suas contas em redes sociais contra hackers, como reconhecer perfis falsos e o que fazer em casos de cyberbullying ou assédio online.</p>
                            <button class="video-description-toggle collapsed" onclick="toggleDescription(this)">
                                <svg viewBox="0 0 24 24">
                                    <path d="M16.59 8.59L12 13.17 7.41 8.59 6 10l6 6 6-6z"></path>
                                </svg>
                                <span>Mostrar mais</span>
                            </button>
                        </div>
                    </div>
                    
                    <button class="button button-secondary" onclick="markModuleComplete(4)">Marcar como concluído</button>
                </div>
            </section>
        </div>

        <!-- Aba: Recursos -->
        <div id="resources" class="tab" role="tabpanel" aria-labelledby="resources-tab">
            <section>
                <h2>Recursos Adicionais</h2>
                <p>Materiais complementares para aprofundar seu conhecimento sobre navegação segura:</p>
                
                <div class="alert alert-info">
                    <h3>Guia Rápido de Segurança Online</h3>
                    <p>Baixe nosso PDF com dicas essenciais para proteger seus dados e dispositivos.</p>
                    <button class="button" onclick="downloadResource('guia-seguranca.pdf')">Baixar Guia</button>
                </div>
                
                <div class="alert alert-warning">
                    <h3>Verificador de Links</h3>
                    <p>Cole um link suspeito abaixo para verificar se é seguro antes de clicar:</p>
                    <input type="text" id="link-checker" placeholder="https://exemplo.com" style="width: 100%; padding: 8px; margin-bottom: 10px;">
                    <button class="button" onclick="checkLink()">Verificar Link</button>
                </div>
                
                <h3>Ferramentas Recomendadas</h3>
                <ul>
                    <li><a href="https://haveibeenpwned.com/" target="_blank">Have I Been Pwned</a> - Verifique se seu email ou senha foram vazados</li>
                    <li><a href="https://www.virustotal.com/" target="_blank">VirusTotal</a> - Analise arquivos e links suspeitos</li>
                    <li><a href="https://web.whatsapp.com/check" target="_blank">Verificador Oficial do WhatsApp</a> - Confirme se mensagens são verdadeiras</li>
                </ul>
                
                <h3>Teste Seu Conhecimento</h3>
                <p>Responda ao quiz e descubra se você está preparado para os perigos da internet:</p>
                <button class="button button-large" onclick="startQuiz()">Iniciar Quiz</button>
            </section>
        </div>

        <!-- Aba: Sobre -->
        <div id="about" class="tab" role="tabpanel" aria-labelledby="about-tab">
            <section>
                <h2>Sobre o Minicurso</h2>
                <p>Este minicurso foi desenvolvido para conscientizar usuários sobre os riscos da internet e ensinar práticas seguras de navegação.</p>
                
                <img src="https://img.freepik.com/fotos-gratis/conceito-de-seguranca-de-dados-com-cadeado-de-internet_53876-124626.jpg" 
                     alt="Cadeado simbolizando segurança digital" 
                     class="section-image" 
                     loading="lazy">
                
                <h3>Objetivos</h3>
                <ul>
                    <li>Reduzir o número de vítimas de golpes online</li>
                    <li>Combater a disseminação de fake news</li>
                    <li>Promover a proteção de dados pessoais</li>
                    <li>Empoderar usuários com conhecimento sobre segurança digital</li>
                </ul>
                
                <h3>Como foi feito</h3>
                <p>Os vídeos foram criados usando Canva e PowerPoint narrado, com linguagem simples e exemplos práticos do dia a dia.</p>
                
                <h3>Impacto Esperado</h3>
                <p>Esperamos que após completar este minicurso, os participantes:</p>
                <ul>
                    <li>Identifiquem tentativas de golpes com 80% mais precisão</li>
                    <li>Verifiquem a veracidade de notícias antes de compartilhar</li>
                    <li>Configurem corretamente as opções de privacidade em seus perfis</li>
                    <li>Adotem senhas fortes e autenticação em dois fatores</li>
                </ul>
                
                <button class="button button-large" onclick="showFeedbackModal()">Enviar Feedback</button>
            </section>
        </div>
    </main>

    <footer role="contentinfo">
        <div class="container">
            <h3>Navegação Segura na Internet</h3>
            <p>&copy; <span id="current-year"></span> Todos os direitos reservados.</p>
            <p>Desenvolvido para conscientização sobre segurança digital</p>
        </div>
    </footer>

    <!-- Chatbot -->
    <div id="chatbot" class="chatbot" role="dialog" aria-labelledby="chatbot-title" aria-modal="true">
        <header>
            <h3 id="chatbot-title">Assistente de Segurança</h3>
            <button class="button close-btn" onclick="toggleChatbot()" aria-label="Fechar chatbot">×</button>
        </header>
        <div class="messages" id="chatbotMessages" role="log" aria-live="polite">
            <div class="message bot">Olá! Sou o assistente de segurança digital. Posso te ajudar com:<br>
                - Dúvidas sobre golpes online<br>
                - Como identificar fake news<br>
                - Configurações de privacidade<br>
                Digite sua pergunta abaixo!
            </div>
        </div>
        <label for="chatbotInput" class="sr-only">Digite sua mensagem</label>
        <input type="text" id="chatbotInput" placeholder="Digite sua mensagem..." onkeypress="handleChatbotInput(event)">
    </div>

    <button id="chatbot-toggle" class="button chatbot-toggle" onclick="toggleChatbot()">Precisa de ajuda?</button>

    <!-- Modal de Feedback -->
    <div id="feedbackModal" class="modal" role="dialog" aria-labelledby="feedback-modal-title" aria-modal="true">
        <div class="modal-content">
            <h2 id="feedback-modal-title">Enviar Feedback</h2>
            <form id="feedbackForm">
                <label for="feedbackName">Seu Nome (opcional):</label>
                <input type="text" id="feedbackName" placeholder="Nome">
                
                <label for="feedbackEmail">Seu Email (opcional):</label>
                <input type="email" id="feedbackEmail" placeholder="Email">
                
                <label for="feedbackMessage">Seu Feedback:</label>
                <textarea id="feedbackMessage" rows="4" required></textarea>
                
                <button type="submit" class="button">Enviar</button>
            </form>
        </div>
    </div>

    <!-- Modal de Quiz -->
    <div id="quizModal" class="modal" role="dialog" aria-labelledby="quiz-modal-title" aria-modal="true">
        <div class="modal-content">
            <h2 id="quiz-modal-title">Quiz de Segurança Digital</h2>
            <div id="quiz-container">
                <!-- O conteúdo do quiz será inserido aqui pelo JavaScript -->
            </div>
        </div>
    </div>

    <script>
        // ===== VARIÁVEIS GLOBAIS =====
        const qaPairs = [
            {
                question: "o que é phishing",
                answer: "Phishing é um golpe onde criminosos se passam por empresas ou pessoas confiáveis para roubar seus dados. Eles enviam emails ou mensagens falsas com links para sites que imitam bancos, redes sociais ou serviços conhecidos, pedindo para você digitar senhas ou informações pessoais."
            },
            {
                question: "como identificar fake news",
                answer: "Para identificar fake news:<br>1) Verifique a fonte - sites confiáveis?<br>2) Pesquise o assunto em outros sites<br>3) Cheque a data da publicação<br>4) Desconfie de títulos sensacionalistas<br>5) Use ferramentas de verificação de fatos como Lupa, Aos Fatos ou Comprova"
            },
            {
                question: "o que é autenticação em dois fatores",
                answer: "Autenticação em dois fatores (2FA) é uma camada extra de segurança além da senha. Quando ativada, além de digitar sua senha, você precisa confirmar sua identidade com:<br>- Um código enviado por SMS<br>- Um aplicativo autenticador (Google Authenticator, Authy)<br>- Biometria (digital, reconhecimento facial)<br>Isso impede que hackers acessem suas contas mesmo que descubram sua senha."
            },
            {
                question: "como criar senhas seguras",
                answer: "Para criar senhas seguras:<br>1) Use pelo menos 12 caracteres<br>2) Combine letras maiúsculas, minúsculas, números e símbolos<br>3) Não use informações pessoais (nomes, datas)<br>4) Use frases que só você conhece (ex: 'Cachorro@GostaDePassear2023!')<br>5) Use um gerenciador de senhas como Bitwarden ou LastPass"
            },
            {
                question: "o que fazer se cair em um golpe",
                answer: "Se cair em um golpe:<br>1) Mude todas as suas senhas imediatamente<br>2) Contate seu banco se compartilhou dados financeiros<br>3) Ative a autenticação em dois fatores<br>4) Denuncie no <a href='https://www.gov.br/mj/pt-br/assuntos/seus-direitos/seguranca-internet' target='_blank'>site do Ministério da Justiça</a><br>5) Avise amigos e familiares para não caírem no mesmo golpe<br>6) Monitore seus extratos bancários por atividades suspeitas"
            },
            {
                question: "como configurar privacidade no facebook",
                answer: "Para configurar a privacidade no Facebook:<br>1) Clique na seta no canto superior direito > Configurações & Privacidade<br>2) Vá em 'Configurações' > 'Privacidade'<br>3) Ajuste 'Quem pode ver suas publicações?' para 'Amigos'<br>4) Em 'Como as pessoas podem te encontrar?', restrinja quem pode ver seu email/telefone<br>5) Em 'Linha do tempo e marcações', revise o que outras pessoas podem postar no seu perfil<br>6) Desative o 'Reconhecimento facial' em 'Configurações de Reconhecimento Facial'"
            },
            {
                question: "o que é vpn e por que usar",
                answer: "VPN (Rede Privada Virtual) é um serviço que criptografa sua conexão e esconde seu endereço IP, aumentando sua privacidade online. Benefícios:<br>- Navegação mais segura em redes públicas de Wi-Fi<br>- Acesso a conteúdo bloqueado por região<br>- Proteção contra rastreamento por provedores de internet<br>- Maior privacidade contra anunciantes<br>Serviços populares: NordVPN, ExpressVPN, ProtonVPN (este tem versão gratuita)."
            },
            {
                question: "como proteger o whatsapp",
                answer: "Para proteger seu WhatsApp:<br>1) Ative a verificação em duas etapas (Configurações > Conta > Verificação em duas etapas)<br>2) Não compartilhe seu código de verificação com ninguém<br>3) Ative notificações de segurança (alertas se seu número for registrado em outro dispositivo)<br>4) Configure privacidade (quem pode ver sua foto, status, última vez online)<br>5) Desative backups na nuvem ou criptografe-os (eles não são protegidos pela criptografia do WhatsApp)<br>6) Cuidado com links suspeitos, mesmo que venham de contatos conhecidos"
            },
            {
                question: "o que é malware",
                answer: "Malware é qualquer software malicioso projetado para danificar ou invadir dispositivos. Tipos comuns:<br>- <strong>Vírus:</strong> se espalha infectando arquivos<br>- <strong>Spyware:</strong> espiona suas atividades<br>- <strong>Ransomware:</strong> bloqueia seu dispositivo e pede resgate<br>- <strong>Adware:</strong> exibe anúncios indesejados<br>- <strong>Trojans:</strong> disfarçados de programas legítimos<br>Proteja-se usando antivírus, não abrindo anexos suspeitos e mantendo seu sistema atualizado."
            },
            {
                question: "como saber se um email é falso",
                answer: "Sinais de email falso:<br>1) Remetente com domínio estranho (ex: suport@bancoo.com.br)<br>2) Saudações genéricas ('Prezado cliente' em vez de seu nome)<br>3) Erros de gramática e ortografia<br>4) Urgência exagerada ('sua conta será bloqueada em 24h')<br>5) Links que não correspondem ao texto mostrado (passe o mouse para ver o destino real)<br>6) Anexos inesperados (como .exe ou .zip)<br>Sempre acesse sites digitando o endereço manualmente, não clicando em links de emails."
            },
            {
                question: "o que é engenharia social",
                answer: "Engenharia social é a manipulação psicológica para que pessoas divulguem informações confidenciais ou realizem ações que comprometam a segurança. Técnicas comuns:<br>- <strong>Pretexting:</strong> criar um cenário falso para obter informações<br>- <strong>Baiting:</strong> oferecer algo tentador (como um prêmio)<br>- <strong>Tailgating:</strong> seguir alguém para acessar áreas restritas<br>- <strong>Phishing:</strong> mensagens falsas se passando por instituições<br>A melhor defesa é desconfiar de solicitações inesperadas, mesmo que pareçam vir de fontes confiáveis."
            },
            {
                question: "como proteger crianças online",
                answer: "Para proteger crianças na internet:<br>1) Use controles parentais nos dispositivos<br>2) Ensine a nunca compartilhar informações pessoais<br>3) Monitore atividades sem invadir privacidade<br>4) Configure filtros de conteúdo inapropriado<br>5) Estabeleça limites de tempo de uso<br>6) Mantenha computadores em áreas comuns da casa<br>7) Ensine sobre cyberbullying e como denunciar<br>8) Use modos restritos no YouTube e outros sites<br>9) Converse abertamente sobre os perigos da internet"
            },
            {
                question: "o que é deepfake",
                answer: "Deepfake é uma técnica que usa inteligência artificial para criar vídeos, fotos ou áudios falsos extremamente realistas. Pode ser usado para:<br>- Espalhar desinformação<br>- Criar pornografia não consensual<br>- Enganar pessoas em golpes<br>Como identificar:<br>1) Movimentos faciais estranhos ou não naturais<br>2) Voz que não combina com a pessoa<br>3) Falta de sincronia entre áudio e vídeo<br>4) Pesquisar a origem do material"
            },
            {
                question: "como apagar dados da internet",
                answer: "Para remover seus dados da internet:<br>1) Entre em contato com sites para solicitar remoção<br>2) Use o <a href='https://www.google.com/webmasters/tools/removals' target='_blank'>solicitante de remoção do Google</a><br>3) Exclua contas antigas que não usa mais<br>4) Peça para amigos removerem fotos suas<br>5) Use serviços como DeleteMe (pago) para limpar dados de pessoas<br>6) Configure privacidade máxima em redes sociais<br>Lembre-se: uma vez online, é difícil remover completamente."
            },
            {
                question: "o que é dark web",
                answer: "A Dark Web é uma parte da internet não indexada por motores de busca, acessível apenas com navegadores especiais como Tor. Características:<br>- Anonimato maior (mas não absoluto)<br>- Usada tanto para atividades legítimas (jornalismo em regimes opressivos) quanto ilegais<br>- Muitos sites mudam de endereço frequentemente<br>- Não é recomendada para usuários comuns, pois contém conteúdos perigosos e alto risco de golpes<br>Se precisar acessar por motivos legítimos, tome extremo cuidado e use máquina virtual."
            },
            {
                question: "como denunciar crimes virtuais",
                answer: "No Brasil, você pode denunciar crimes virtuais:<br>1) <strong>Ministério Público Federal:</strong> <a href='https://www.mpf.mp.br' target='_blank'>www.mpf.mp.br</a><br>2) <strong>SaferNet:</strong> <a href='https://www.safernet.org.br' target='_blank'>www.safernet.org.br</a><br>3) <strong>Delegacias especializadas:</strong> procure a mais próxima<br>4) <strong>Bancos:</strong> contate seu banco imediatamente em caso de fraude<br>Guarde todas as evidências (prints, emails, URLs) antes de denunciar."
            },
            {
                question: "o que é criptografia",
                answer: "Criptografia é o processo de codificar informações para que apenas pessoas autorizadas possam acessá-las. Na internet:<br>- <strong>Criptografia de dados:</strong> protege informações armazenadas<br>- <strong>Criptografia em trânsito:</strong> protege dados sendo transmitidos (como o cadeado nos navegadores)<br>- <strong>Criptografia de ponta a ponta:</strong> usada em apps como WhatsApp, onde só remetente e destinatário podem ler as mensagens<br>A criptografia forte é essencial para privacidade e segurança online."
            },
            {
                question: "como fazer backup seguro",
                answer: "Para backups seguros:<br>1) Use a regra 3-2-1: 3 cópias, em 2 mídias diferentes, 1 fora do local<br>2) Criptografe backups sensíveis<br>3) Para fotos/vídeos: Google Fotos, iCloud ou Amazon Photos<br>4) Para documentos: Google Drive, OneDrive ou Dropbox (com 2FA ativado)<br>5) Para todo o sistema: Time Machine (Mac) ou File History (Windows)<br>6) Teste regularmente a recuperação dos backups<br>7) Mantenha pelo menos um backup offline para proteção contra ransomware"
            },
            {
                question: "o que é token",
                answer: "Token é um dispositivo ou aplicativo que gera códigos numéricos temporários usados para autenticação em dois fatores. Tipos:<br>- <strong>Tokens físicos:</strong> pequenos dispositivos como os usados por bancos<br>- <strong>Apps autenticadores:</strong> Google Authenticator, Microsoft Authenticator, Authy<br>- <strong>SMS/Email:</strong> códigos enviados para seu celular ou email<br>- <strong>Push notifications:</strong> confirmação em apps como do Google ou Facebook<br>Tokens são mais seguros que apenas senhas porque o código muda frequentemente e é único para cada login."
            },
            {
                question: "como limpar historico",
                answer: "Para limpar histórico em navegadores:<br><br><strong>Chrome/Edge/Firefox (computador):</strong><br>1) Ctrl+Shift+Delete (Windows) ou Command+Shift+Delete (Mac)<br>2) Selecione o período ('Todo o tempo')<br>3) Escolha o que apagar (histórico, cookies, cache)<br>4) Clique em 'Limpar dados'<br><br><strong>Celular (Android/iOS):</strong><br>1) Abra o navegador<br>2) Toque no menu (três pontos)<br>3) Vá em 'Histórico' > 'Limpar dados de navegação'<br><br>Obs: Limpar o histórico não remove seus dados de sites ou serviços onde você fez login."
            },
            {
                question: "o que é nuvem",
                answer: "Nuvem (cloud computing) é o armazenamento e processamento de dados em servidores remotos acessados pela internet, em vez do seu computador local. Serviços populares:<br>- Armazenamento: Google Drive, Dropbox, iCloud<br>- Email: Gmail, Outlook.com<br>- Streaming: Netflix, Spotify<br>Vantagens: acesso de qualquer lugar, compartilhamento fácil, backups automáticos. Riscos: privacidade (seus dados estão com terceiros), dependência de internet."
            },
            {
                question: "como bloquear anúncios",
                answer: "Para bloquear anúncios:<br>1) <strong>Navegadores de computador:</strong> instale extensões como uBlock Origin ou AdBlock Plus<br>2) <strong>Celular Android:</strong> use navegadores com bloqueador nativo como Firefox com extensões ou Brave<br>3) <strong>iPhone:</strong> Safari tem bloqueador de conteúdo (ative em Ajustes > Safari)<br>4) <strong>Para todo o dispositivo:</strong> use VPNs com bloqueio de ads como AdGuard VPN<br>5) <strong>Redes sociais:</strong> pague pelas versões sem ads quando disponível<br>Cuidado: alguns sites não funcionam bem com bloqueadores ativos."
            },
            {
                question: "o que é bitcoin",
                answer: "Bitcoin é uma criptomoeda (moeda digital) descentralizada que usa blockchain como tecnologia base. Características:<br>- Transações pseudônimas (não totalmente anônimas)<br>- Sem controle de bancos ou governos<br>- Volátil (valor pode mudar rapidamente)<br>- Usada tanto para investimentos quanto para pagamentos (em alguns lugares)<br>Riscos:<br>- Alvo comum de golpes e fraudes<br>- Perda irreversível se enviar para endereço errado<br>- Carteiras podem ser hackeadas se não protegidas<br>Se for usar, pesquise muito e comece com pequenos valores."
            },
            {
                question: "como funciona o reconhecimento facial",
                answer: "Reconhecimento facial usa algoritmos para mapear características únicas do rosto e identificar pessoas. Usos comuns:<br>- Desbloqueio de celulares (Face ID, Android Face Unlock)<br>- Segurança em aeroportos e fronteiras<br>- Identificação em redes sociais (tagging automático)<br>Preocupações:<br>- Coleta de dados biométricos sensíveis<br>- Uso por governos para vigilância em massa<br>- Vieses raciais e de gênero em alguns sistemas<br>Você pode desativar em configurações de privacidade na maioria dos serviços."
            },
            {
                question: "o que é cookie",
                answer: "Cookies são pequenos arquivos que sites salvam no seu navegador para lembrar informações como:<br>- Preferências de idioma<br>- Itens no carrinho de compras<br>- Dados de login (em cookies persistentes)<br>- Hábitos de navegação (para anunciantes)<br>Tipos:<br>- <strong>Cookies essenciais:</strong> necessários para o site funcionar<br>- <strong>Cookies de desempenho:</strong> melhoram experiência<br>- <strong>Cookies de marketing:</strong> rastreiam para mostrar anúncios<br>Você pode gerenciar cookies nas configurações do navegador."
            },
            {
                question: "como funciona o rastreamento online",
                answer: "Você é rastreado online principalmente por:<br>1) <strong>Cookies:</strong> pequenos arquivos que registram sua navegação<br>2) <strong>Pixel tags:</strong> imagens invisíveis em emails/sites que registram acessos<br>3) <strong>Fingerprinting:</strong> identificação única baseada em configurações do seu navegador<br>4) <strong>Logins:</strong> serviços como Google e Facebook rastreiam mesmo em outros sites<br>Para reduzir:<br>- Use modo anônimo/navegadores como Brave<br>- Instale extensões como Privacy Badger<br>- Desative cookies de terceiros<br>- Use VPN"
            },
            {
                question: "o que é spam",
                answer: "Spam são mensagens não solicitadas enviadas em massa, geralmente por email, mas também por SMS, redes sociais etc. Tipos:<br>- <strong>Publicitário:</strong> propaganda não autorizada<br>- <strong>Golpes:</strong> phishing, falsos prêmios<br>- <strong>Malicioso:</strong> com links ou anexos perigosos<br>Como reduzir:<br>- Não divulgue seu email publicamente<br>- Use filtros de spam<br>- Marque mensagens como spam em seu serviço de email<br>- Nunca responda ou clique em links de spam<br>- Considere ter um email secundário para cadastros"
            },
            {
                question: "como funciona o modo anônimo",
                answer: "O modo anônimo/privado (Chrome, Firefox, Safari etc) oferece privacidade limitada:<br><strong>O que faz:</strong><br>- Não salva histórico, cookies ou dados de formulários<br>- Sessões são isoladas (não mantém logins)<br><strong>O que NÃO faz:</strong><br>- Não esconde sua navegação do provedor de internet ou empregador<br>- Não impede rastreamento por sites (eles ainda sabem quem você é se fizer login)<br>- Não bloqueia malware ou phishing<br>É útil para usar em computadores compartilhados, mas não fornece anonimato completo."
            },
            {
                question: "o que é um hacker",
                answer: "Hacker é um termo amplo para pessoas com habilidades avançadas em computação. Tipos:<br>- <strong>White hat:</strong> hackers éticos que ajudam a encontrar falhas de segurança<br>- <strong>Black hat:</strong> criminosos que invadem sistemas para roubar ou causar danos<br>- <strong>Grey hat:</strong> ficam no meio termo, às vezes agindo ilegalmente mas com boas intenções<br>- <strong>Script kiddies:</strong> inexperientes que usam ferramentas prontas<br>Nem todo hacker é criminoso - muitos trabalham em segurança digital protegendo sistemas."
            },
            {
                question: "como funciona o antivírus",
                answer: "Antivírus são programas que detectam e removem malware. Funcionam através de:<br>1) <strong>Assinaturas:</strong> comparam arquivos com banco de dados de vírus conhecidos<br>2) <strong>Heurística:</strong> analisam comportamento suspeito mesmo sem assinatura conhecida<br>3) <strong>Proteção em tempo real:</strong> monitoram atividades suspeitas<br>4) <strong>Quarentena:</strong> isolam arquivos infectados sem deletar imediatamente<br>Dicas:<br>- Mantenha seu antivírus atualizado<br>- Escolha soluções reconhecidas (Bitdefender, Kaspersky, Windows Defender)<br>- Não instale mais de um antivírus simultaneamente"
            }
        ];

        const quizQuestions = [
            {
                question: "Qual destes NÃO é um sinal de email de phishing?",
                options: [
                    "Remetente com domínio estranho (ex: suport@bancoo.com.br)",
                    "Saudações personalizadas com seu nome completo",
                    "Links que não correspondem ao texto mostrado",
                    "Urgência exagerada ('sua conta será bloqueada em 24h')"
                ],
                answer: 1,
                explanation: "Emails de phishing geralmente usam saudações genéricas como 'Prezado cliente' em vez do seu nome. Eles raramente personalizam com informações que não conseguiram obter em vazamentos públicos."
            },
            {
                question: "Qual é a maneira mais segura de criar e gerenciar senhas?",
                options: [
                    "Usar a mesma senha forte em todos os sites",
                    "Anotar todas as senhas em um caderno guardado em casa",
                    "Usar um gerenciador de senhas com autenticação em dois fatores",
                    "Criar senhas baseadas em informações pessoais fáceis de lembrar"
                ],
                answer: 2,
                explanation: "Gerenciadores de senhas como Bitwarden ou LastPass (com 2FA ativado) permitem criar senhas únicas e complexas para cada site sem precisar memorizá-las. Eles criptografam seus dados e são mais seguros que anotar em papel ou reutilizar senhas."
            },
            {
                question: "O que você deve fazer se receber uma mensagem no WhatsApp dizendo ser de um familiar pedindo dinheiro urgentemente?",
                options: [
                    "Transferir imediatamente pois deve ser realmente urgente",
                    "Ligar para a pessoa em um número conhecido para confirmar",
                    "Perguntar na mensagem por detalhes que só ela saberia",
                    "Encaminhar a mensagem para outros familiares avisando sobre o possível golpe"
                ],
                answer: 1,
                explanation: "Golpes de 'falso sequestro' ou emergência falsa são comuns. Sempre confirme por outro meio de comunicação (ligação, contato pessoal) antes de agir. Criminosos podem ter acesso a contas ou criar perfis falsos idênticos."
            },
            {
                question: "Qual destas configurações NÃO ajuda a proteger sua privacidade no Facebook?",
                options: [
                    "Limitar quem pode ver suas publicações antigas",
                    "Desativar o reconhecimento facial",
                    "Permitir que motores de pesquisa liguem ao seu perfil",
                    "Revisar tags antes que apareçam na sua linha do tempo"
                ],
                answer: 2,
                explanation: "Permitir que motores de pesquisa liguem ao seu perfil torna seu perfil mais público e acessível fora do Facebook. As outras opções são medidas importantes de privacidade."
            },
            {
                question: "Você recebe um SMS dizendo que ganhou um prêmio e para clicar no link e preencher seus dados. O que fazer?",
                options: [
                    "Clicar no link para ver se é verdadeiro",
                    "Responder a mensagem perguntando mais detalhes",
                    "Ignorar e deletar a mensagem",
                    "Compartilhar com amigos para ver se eles também receberam"
                ],
                answer: 2,
                explanation: "Mensagens não solicitadas sobre prêmios são quase sempre golpes. Nunca clique em links ou responda. Se realmente tiver ganhado algo, você será contactado por meios oficiais e não precisará fornecer dados sensíveis por SMS."
            }
        ];

        // ===== FUNÇÕES DE INTERAÇÃO =====
        function showTab(tabId) {
            // Esconder todas as abas
            document.querySelectorAll('.tab').forEach(tab => {
                tab.classList.remove('active');
                tab.setAttribute('aria-hidden', 'true');
            });
            
            // Mostrar a aba selecionada
            const activeTab = document.getElementById(tabId);
            activeTab.classList.add('active');
            activeTab.setAttribute('aria-hidden', 'false');
            
            // Atualizar atributos ARIA dos botões
            document.querySelector('[aria-controls="modules"]').setAttribute('aria-expanded', tabId === 'modules');
            document.querySelector('[aria-controls="resources"]').setAttribute('aria-expanded', tabId === 'resources');
            document.querySelector('[aria-controls="about"]').setAttribute('aria-expanded', tabId === 'about');
        }

        function toggleChatbot() {
            const chatbot = document.getElementById('chatbot');
            const toggleButton = document.getElementById('chatbot-toggle');
            const isOpen = chatbot.classList.toggle('open');
            
            // Atualizar atributos ARIA
            chatbot.setAttribute('aria-hidden', !isOpen);
            toggleButton.setAttribute('aria-expanded', isOpen);
            
            // Esconder o botão de toggle quando o chatbot está aberto
            toggleButton.style.display = isOpen ? 'none' : 'block';
            
            // Focar no input quando o chatbot abrir
            if (isOpen) {
                setTimeout(() => {
                    document.getElementById('chatbotInput').focus();
                    
                    // Mostrar sugestões apenas se não houver mensagens
                    const messages = document.getElementById('chatbotMessages');
                    if (messages.children.length <= 1) { // Apenas a mensagem inicial
                        showQuickQuestions();
                    }
                }, 100);
            }
        }

        function showQuickQuestions() {
            const quickQuestions = document.createElement('div');
            quickQuestions.className = 'quick-questions';
            
            // Pegar 3 perguntas aleatórias
            const randomQuestions = [...qaPairs]
                .sort(() => 0.5 - Math.random())
                .slice(0, 3)
                .map(pair => pair.question);
            
            quickQuestions.innerHTML = `
                <p>Você pode perguntar coisas como:</p>
                <ul>
                    ${randomQuestions.map(q => `<li><button class="quick-question" onclick="askQuickQuestion('${q}')">${q}</button></li>`).join('')}
                </ul>
            `;
            
            const messages = document.getElementById('chatbotMessages');
            messages.appendChild(quickQuestions);
        }

        function askQuickQuestion(question) {
            const input = document.getElementById('chatbotInput');
            input.value = question;
            
            // Disparar o evento de Enter
            const event = new KeyboardEvent('keypress', {key: 'Enter'});
            input.dispatchEvent(event);
            
            // Remover as sugestões
            document.querySelector('.quick-questions')?.remove();
        }

        function showFeedbackModal() {
            const modal = document.getElementById('feedbackModal');
            modal.classList.add('open');
            modal.setAttribute('aria-hidden', 'false');
            document.getElementById('feedbackName').focus();
        }

        function closeFeedbackModal() {
            const modal = document.getElementById('feedbackModal');
            modal.classList.remove('open');
            modal.setAttribute('aria-hidden', 'true');
        }

        function startQuiz() {
            const quizContainer = document.getElementById('quiz-container');
            let quizHTML = '';
            let questionNumber = 1;
            
            quizQuestions.forEach((q, index) => {
                quizHTML += `
                    <div class="quiz-question" id="question-${index}">
                        <h3>Pergunta ${questionNumber++}: ${q.question}</h3>
                        <div class="quiz-options">
                            ${q.options.map((opt, i) => `
                                <button class="quiz-option" onclick="checkAnswer(${index}, ${i})">${opt}</button>
                            `).join('')}
                        </div>
                        <div class="quiz-explanation" id="explanation-${index}" style="display: none;">
                            <p><strong>Resposta correta:</strong> ${q.options[q.answer]}</p>
                            <p>${q.explanation}</p>
                        </div>
                    </div>
                `;
            });
            
            quizHTML += `<button class="button" onclick="closeQuizModal()" style="margin-top: 20px;">Fechar Quiz</button>`;
            quizContainer.innerHTML = quizHTML;
            
            const modal = document.getElementById('quizModal');
            modal.classList.add('open');
            modal.setAttribute('aria-hidden', 'false');
        }

        function checkAnswer(questionIndex, selectedOption) {
            const question = quizQuestions[questionIndex];
            const options = document.querySelectorAll(`#question-${questionIndex} .quiz-option`);
            const explanation = document.getElementById(`explanation-${questionIndex}`);
            
            // Resetar todas as opções
            options.forEach(opt => {
                opt.style.backgroundColor = '';
                opt.style.color = '';
            });
            
            // Marcar a selecionada
            const selected = options[selectedOption];
            selected.style.backgroundColor = selectedOption === question.answer ? '#2b5797' : '#e81123';
            selected.style.color = 'white';
            
            // Marcar a correta se diferente
            if (selectedOption !== question.answer) {
                const correct = options[question.answer];
                correct.style.backgroundColor = '#2b5797';
                correct.style.color = 'white';
            }
            
            // Mostrar explicação
            explanation.style.display = 'block';
        }

        function closeQuizModal() {
            const modal = document.getElementById('quizModal');
            modal.classList.remove('open');
            modal.setAttribute('aria-hidden', 'true');
        }

        function downloadResource(filename) {
            alert(`Simulação: O arquivo ${filename} seria baixado. Em um site real, isso iniciaria o download.`);
        }

        function checkLink() {
            const link = document.getElementById('link-checker').value;
            if (!link) {
                alert('Por favor, insira um link para verificar.');
                return;
            }
            
            // Simulação de verificação
            const isSafe = Math.random() > 0.3; // 70% de chance de ser seguro
            if (isSafe) {
                alert('✅ Este link parece seguro com base em nossa verificação. Mas sempre mantenha cautela com links desconhecidos.');
            } else {
                alert('⚠️ Atenção! Este link pode ser perigoso. Nossa análise indica características suspeitas. Recomendamos não acessar.');
            }
        }

        // ===== FUNÇÕES DO YOUTUBE =====
        function toggleLike(button) {
            button.classList.toggle('active');
            const dislikeButton = button.parentElement.querySelector('.video-action:nth-child(2)');
            
            if (button.classList.contains('active')) {
                dislikeButton.classList.remove('active');
            }
            
            // Simular envio para o servidor
            console.log('Like toggled');
        }

        function toggleDislike(button) {
            button.classList.toggle('active');
            const likeButton = button.parentElement.querySelector('.video-action:nth-child(1)');
            
            if (button.classList.contains('active')) {
                likeButton.classList.remove('active');
            }
            
            // Simular envio para o servidor
            console.log('Dislike toggled');
        }

        function shareVideo() {
            alert('Simulação: Abriria o menu de compartilhamento como no YouTube. Em um site real, isso permitiria compartilhar o vídeo em redes sociais ou copiar o link.');
        }

        function toggleDescription(button) {
            const description = button.parentElement;
            const fullText = description.querySelector('p:first-child');
            
            button.classList.toggle('collapsed');
            
            if (button.classList.contains('collapsed')) {
                fullText.style.display = '-webkit-box';
                fullText.style.webkitLineClamp = '2';
                fullText.style.webkitBoxOrient = 'vertical';
                fullText.style.overflow = 'hidden';
                button.innerHTML = `
                    <svg viewBox="0 0 24 24">
                        <path d="M16.59 8.59L12 13.17 7.41 8.59 6 10l6 6 6-6z"></path>
                    </svg>
                    <span>Mostrar mais</span>
                `;
            } else {
                fullText.style.display = 'block';
                button.innerHTML = `
                    <svg viewBox="0 0 24 24">
                        <path d="M12 8l-6 6 1.41 1.41L12 10.83l4.59 4.58L18 14z"></path>
                    </svg>
                    <span>Mostrar menos</span>
                `;
            }
        }

        // ===== PROGRESSO DO CURSO =====
        function markModuleComplete(moduleNumber) {
            const statusElement = document.getElementById(`module${moduleNumber}-status`);
            statusElement.textContent = 'Concluído';
            statusElement.style.color = '#4CAF50';
            statusElement.style.fontWeight = 'bold';
            
            updateProgress();
        }

        function updateProgress() {
            const totalModules = 4;
            let completed = 0;
            
            for (let i = 1; i <= totalModules; i++) {
                if (document.getElementById(`module${i}-status`).textContent === 'Concluído') {
                    completed++;
                }
            }
            
            const progress = (completed / totalModules) * 100;
            document.getElementById('course-progress').style.width = `${progress}%`;
            
            if (progress === 100) {
                alert('Parabéns! Você completou todos os módulos do minicurso. Esperamos que tenha aprendido muito sobre segurança digital!');
            }
        }

        // ===== FUNÇÕES DO CHATBOT =====
        function respondToMessage(message) {
            const lowerMessage = message.toLowerCase().trim();
            let response = "Desculpe, não entendi. Aqui estão algumas perguntas que posso responder:<br>";
            
            const commonQuestions = [
                "O que é phishing?",
                "Como identificar fake news?",
                "O que é autenticação em dois fatores?",
                "Como criar senhas seguras?"
            ];
            
            response += commonQuestions.map((q, i) => `${i+1}) ${q}`).join("<br>");
            
            // Busca por sinônimos e variações
            const synonymGroups = {
                'phishing': ['phising', 'fishing', 'golpe email', 'fraude online'],
                'fake news': ['noticia falsa', 'desinformação', 'mentira internet', 'boato'],
                'senha': ['password', 'credencial', 'acesso', 'login'],
                'privacidade': ['dados pessoais', 'proteção', 'confidencialidade', 'segurança informação']
            };
            
            // Verifica cada par de Q&A
            for (const pair of qaPairs) {
                const questionWords = pair.question.toLowerCase().split(' ');
                
                // Verifica correspondência direta
                if (lowerMessage.includes(pair.question.toLowerCase())) {
                    response = pair.answer;
                    break;
                }
                
                // Verifica sinônimos
                let synonymMatch = false;
                for (const [key, synonyms] of Object.entries(synonymGroups)) {
                    if (lowerMessage.includes(key)) {
                        for (const synonym of synonyms) {
                            if (lowerMessage.includes(synonym)) {
                                synonymMatch = true;
                                break;
                            }
                        }
                    }
                    if (synonymMatch) break;
                }
                
                if (synonymMatch) {
                    response = pair.answer;
                    break;
                }
                
                // Verifica pelo menos 60% das palavras-chave
                const matches = questionWords.filter(word => 
                    lowerMessage.includes(word) && word.length > 3
                );
                
                if (matches.length / questionWords.length >= 0.6) {
                    response = pair.answer;
                    break;
                }
            }
            
            // Adicionar sugestões de acompanhamento
            if (!response.startsWith("Desculpe")) {
                const relatedQuestions = qaPairs
                    .filter(pair => pair.question !== message.toLowerCase())
                    .sort(() => 0.5 - Math.random())
                    .slice(0, 3)
                    .map(pair => `"${pair.question}"`);
                
                if (relatedQuestions.length > 0) {
                    response += `<br><br>Posso te ajudar com algo mais? Talvez sobre:<br>- ${relatedQuestions.join("<br>- ")}`;
                }
            }
            
            return response;
        }

        function addMessage(text, sender) {
            const messages = document.getElementById('chatbotMessages');
            const messageElement = document.createElement('div');
            messageElement.classList.add('message', sender);
            messageElement.innerHTML = text;
            messages.appendChild(messageElement);
            
            // Adicionar dicas contextuais para certas respostas
            if (sender === 'bot') {
                const lowerText = text.toLowerCase();
                
                if (lowerText.includes('senha') && !lowerText.includes('dica')) {
                    const tip = document.createElement('div');
                    tip.className = 'message bot';
                    tip.innerHTML = '<strong>Dica:</strong> Use um gerenciador de senhas como o Google Password Manager ou LastPass para guardar suas senhas com segurança!';
                    messages.appendChild(tip);
                }
                
                if (lowerText.includes('email') && !lowerText.includes('dica')) {
                    const tip = document.createElement('div');
                    tip.className = 'message bot';
                    tip.innerHTML = '<strong>Dica:</strong> Você pode criar aliases de email (endereços alternativos) no Gmail adicionando um "+" antes do @, como seunome+redesocial@gmail.com para identificar vazamentos.';
                    messages.appendChild(tip);
                }
            }
            
            messages.scrollTop = messages.scrollHeight;
        }

        function handleChatbotInput(event) {
            const input = document.getElementById('chatbotInput');
            
            if (event.key === 'Enter') {
                const message = input.value.trim();
                if (message) {
                    addMessage(message, 'user');
                    input.value = '';
                    
                    // Mostrar que o bot está digitando
                    const typingIndicator = document.createElement('div');
                    typingIndicator.id = 'typing-indicator';
                    typingIndicator.className = 'message bot';
                    typingIndicator.textContent = 'Digitando...';
                    document.getElementById('chatbotMessages')
                        .appendChild(typingIndicator);
                    
                    // Simular tempo de resposta
                    setTimeout(() => {
                        document.getElementById('typing-indicator')?.remove();
                        const botResponse = respondToMessage(message);
                        addMessage(botResponse, 'bot');
                    }, 1000 + Math.random() * 2000);
                }
            }
        }

        // ===== MANIPULAÇÃO DE FORMULÁRIOS =====
        function handleFeedbackForm(event) {
            event.preventDefault();
            
            const name = document.getElementById('feedbackName').value.trim();
            const email = document.getElementById('feedbackEmail').value.trim();
            const message = document.getElementById('feedbackMessage').value.trim();
            
            // Validação
            if (!message) {
                alert('Por favor, insira sua mensagem de feedback.');
                return;
            }
            
            if (email && !email.includes('@') || !email.includes('.')) {
                alert('Por favor, insira um email válido ou deixe o campo em branco.');
                return;
            }
            
            // Simular envio
            const form = event.target;
            const loading = document.createElement('div');
            loading.className = 'loading';
            loading.textContent = 'Enviando feedback...';
            form.appendChild(loading);
            
            setTimeout(() => {
                loading.remove();
                alert('Obrigado pelo seu feedback! Sua opinião nos ajuda a melhorar o minicurso.');
                closeFeedbackModal();
                form.reset();
            }, 1500);
        }

        // ===== INICIALIZAÇÃO =====
        document.addEventListener('DOMContentLoaded', function() {
            // Configurar eventos
            document.getElementById('feedbackForm').addEventListener('submit', handleFeedbackForm);
            
            // Fechar modais ao clicar fora
            window.addEventListener('click', (event) => {
                if (event.target === document.getElementById('feedbackModal')) {
                    closeFeedbackModal();
                }
                if (event.target === document.getElementById('quizModal')) {
                    closeQuizModal();
                }
            });
            
            // Navegação por teclado nos modais
            const modals = document.querySelectorAll('.modal');
            modals.forEach(modal => {
                modal.addEventListener('keydown', function(e) {
                    if (e.key === 'Escape') {
                        if (modal.id === 'feedbackModal') closeFeedbackModal();
                        if (modal.id === 'quizModal') closeQuizModal();
                    }
                    
                    if (e.key === 'Tab') {
                        const focusableElements = 'button, [href], input, select, textarea, [tabindex]:not([tabindex="-1"])';
                        const focusableModalElements = modal.querySelectorAll(focusableElements);
                        const firstElement = focusableModalElements[0];
                        const lastElement = focusableModalElements[focusableModalElements.length - 1];
                        
                        if (e.shiftKey && document.activeElement === firstElement) {
                            lastElement.focus();
                            e.preventDefault();
                        } else if (!e.shiftKey && document.activeElement === lastElement) {
                            firstElement.focus();
                            e.preventDefault();
                        }
                    }
                });
            });
            
            // Atualizar ano no rodapé
            document.getElementById('current-year').textContent = new Date().getFullYear();
            
            // Configurar atributos ARIA iniciais
            document.getElementById('modules').setAttribute('aria-hidden', 'false');
            document.getElementById('resources').setAttribute('aria-hidden', 'true');
            document.getElementById('about').setAttribute('aria-hidden', 'true');
            document.getElementById('chatbot').setAttribute('aria-hidden', 'true');
            
            // Inicializar descrições de vídeo recolhidas
            document.querySelectorAll('.video-description p:first-child').forEach(p => {
                p.style.display = '-webkit-box';
                p.style.webkitLineClamp = '2';
                p.style.webkitBoxOrient = 'vertical';
                p.style.overflow = 'hidden';
            });
        });
    </script>
</body>
</html> 
