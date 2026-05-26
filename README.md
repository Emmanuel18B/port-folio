# port-folio
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0"> <meta name="keywords" content="portfolio, CV, génie informatique, développeur web">
    <title>Accueil - Belone Eyamba</title>
    <style>
        /* =========================================
           1. RESET ET VARIABLES GLOBALES
           ========================================= */
        :root {
            --bg-color: rgba(20, 1, 36, 0.95);
            --primary-color: #00ffff;
            --text-color: aliceblue;
            --card-bg: rgba(255, 255, 255, 0.05);
            --transition-speed: 0.3s;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        html {
            scroll-behavior: smooth;
        }

        body {
            background-color: var(--bg-color);
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            color: var(--text-color);
            line-height: 1.6;
            overflow-x: hidden; /* Empêche le scroll horizontal sur mobile */
        }

        /* Typographie fluide : s'adapte automatiquement à la taille de l'écran */
        h1 { font-size: clamp(2rem, 5vw, 4rem); text-align: center; margin-bottom: 20px; }
        h2, h3, h4 { font-size: clamp(1.5rem, 3vw, 2.5rem); text-align: center; margin-bottom: 15px; }
        p { font-size: clamp(1rem, 2vw, 1.25rem); text-align: justify; margin-bottom: 15px; }
        
        a { color: var(--primary-color); text-decoration: none; transition: color var(--transition-speed); }
        a:hover { color: #fff; text-shadow: 0 0 8px var(--primary-color); }

        /* =========================================
           2. NAVIGATION (Responsive & Touch-friendly)
           ========================================= */
        nav {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            z-index: 999;
            background-color: rgba(0, 0, 0, 0.9);
            backdrop-filter: blur(10px); /* Effet verre moderne */
        }

        #menu {
            display: flex;
            flex-wrap: wrap; /* Permet aux éléments de passer à la ligne sur très petits écrans */
            justify-content: center;
            gap: 15px;
            padding: 15px;
        }

        #menu div a {
            display: block;
            padding: 10px 20px;
            font-weight: bold;
            border-radius: 5px;
            transition: background var(--transition-speed);
        }

        #menu div a:hover {
            background-color: rgba(0, 255, 255, 0.1);
        }

        /* =========================================
           3. SECTIONS PRINCIPALES (Layout)
           ========================================= */
        /* Marges pour compenser la nav fixe */
        section, #conteneur, #a, #futur, .contact, .formulaire {
            padding: 100px 5% 50px 5%; /* 5% de padding latéral pour respirer sur mobile */
            max-width: 1200px; /* Limite la largeur sur les très grands écrans */
            margin: 0 auto;
        }

        /* --- Section Accueil (Flexbox) --- */
        #conteneur {
            display: flex;
            flex-direction: column-reverse; /* Sur mobile : image en haut, texte en bas */
            align-items: center;
            gap: 40px;
            min-height: 100vh;
            justify-content: center;
        }

        .s1, .s2 {
            width: 100%; /* Occupe toute la largeur sur mobile */
        }

        .s1 span {
            color: var(--primary-color);
            font-weight: bold;
        }

        .s2 img {
            width: 100%;
            max-width: 400px;
            height: auto;
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.5);
            display: block;
            margin: 0 auto;
        }

        /* --- Section Compétences --- */
        #lang strong {
            display: block;
            text-align: center;
            font-size: 1.2rem;
            color: var(--primary-color);
            letter-spacing: 2px;
            text-transform: uppercase;
        }

        .nom {
            margin: 30px 0;
            width: 100%;
        }

        .nom span {
            display: block;
            margin-bottom: 10px;
            font-weight: bold;
        }

        .forme {
            width: 100%;
            height: 25px;
            background-color: var(--card-bg);
            border-radius: 15px;
            overflow: hidden;
            border: 1px solid rgba(255, 255, 255, 0.1);
        }

        /* Le JS va animer la width de ces éléments */
        #html, #css, #python, #java, #sql {
            height: 100%;
            width: 0% !important; /* Force à 0 pour l'animation JS */
            transition: width 1.5s cubic-bezier(0.1, 1, 0.1, 1);
            display: flex;
            align-items: center;
            justify-content: flex-end;
            padding-right: 10px;
            font-weight: bold;
            color: #000;
        }

        #html { background-color: chartreuse; }
        #css { background-color: aqua; }
        #python { background-color: #4B8BBE; color: white; }
        #java { background-color: #f89820; }
        #sql { background-color: crimson; color: white; }

        /* --- Section Outils & Spécialités (CSS Grid) --- */
        #a {
            display: grid;
            grid-template-columns: 1fr; /* 1 colonne sur mobile */
            gap: 30px;
        }

        .outils, .special {
            background-color: var(--card-bg);
            padding: 30px;
            border-radius: 20px;
            border: 1px solid rgba(255,255,255,0.1);
            transition: transform var(--transition-speed);
        }

        .outils:hover, .special:hover {
            transform: translateY(-5px);
            border-color: var(--primary-color);
        }

        ul { list-style-type: none; }
        ul li {
            padding: 15px;
            margin-bottom: 10px;
            background: rgba(0,0,0,0.3);
            border-radius: 10px;
            text-align: center;
        }

        /* --- Section Projets & Contact --- */
        #futur, .contact { text-align: center; }
        .projet a {
            display: inline-block;
            margin-top: 20px;
            padding: 15px 30px;
            background: var(--card-bg);
            border: 1px solid var(--primary-color);
            border-radius: 30px;
        }

        /* =========================================
           4. FORMULAIRE (Responsive & Ergonomique)
           ========================================= */
        .formulaire table {
            width: 100%;
            max-width: 600px;
            margin: 0 auto;
            border-collapse: collapse;
        }

        /* Remplacement du comportement tableau par blocs sur mobile */
        .formulaire td {
            display: block;
            width: 100%;
            padding: 10px 0;
            text-align: left;
        }

        input, textarea {
            width: 100%;
            padding: 15px;
            border: 1px solid #ccc;
            border-radius: 8px;
            background-color: rgba(255, 255, 255, 0.05);
            color: white;
            font-size: 1rem;
            transition: all var(--transition-speed);
            font-family: inherit;
        }

        textarea { resize: vertical; min-height: 120px; }

        input:focus, textarea:focus {
            outline: none;
            border-color: var(--primary-color);
            box-shadow: 0 0 8px rgba(0, 255, 255, 0.3);
            background-color: rgba(255, 255, 255, 0.1);
        }

        button {
            width: 100%;
            background-color: var(--primary-color);
            color: #140124;
            font-weight: bold;
            font-size: 1.1rem;
            border: none;
            padding: 15px 20px;
            border-radius: 8px;
            cursor: pointer;
            transition: all var(--transition-speed);
            margin-top: 10px;
        }

        button:hover {
            transform: scale(1.02);
            box-shadow: 0 0 15px rgba(0, 255, 255, 0.5);
        }

        footer {
            text-align: center;
            padding: 30px;
            background: black;
            margin-top: 50px;
        }

        /* =========================================
           5. ANIMATIONS JS (Conservées)
           ========================================= */
        .fade-in-element {
            opacity: 0;
            transform: translateY(30px);
            transition: opacity 0.8s ease-out, transform 0.8s ease-out;
        }

        .fade-in-element.visible {
            opacity: 1;
            transform: translateY(0);
        }

        /* =========================================
           6. MEDIA QUERIES (Tablettes & Écrans Larges)
           ========================================= */
        @media (min-width: 768px) {
            /* À partir des tablettes, on passe l'accueil en 2 colonnes */
            #conteneur {
                flex-direction: row;
                text-align: left;
            }
            .s1, .s2 {
                width: 50%;
            }
            
            /* Les outils et spécialités passent côte à côte */
            #a {
                grid-template-columns: 1fr 1fr;
            }
            
            /* Le formulaire redevient un tableau classique, plus lisible sur grand écran */
            .formulaire td {
                display: table-cell;
                padding: 15px;
                vertical-align: middle;
            }
            .formulaire td:first-child {
                width: 30%;
                text-align: right;
                padding-right: 20px;
            }
            button {
                width: auto;
                min-width: 200px;
            }
        }
    </style>
</head>

<body>
    <header> 
        <nav>
            <div id="menu">     
                <div class="m1"><a href="#conteneur">Accueil</a></div>
                <div class="m2"><a href="#lang">Compétences</a></div>
                <div class="m3"><a href="#futur">Projets</a></div>
            </div>
        </nav>
    </header>

    <div id="conteneur">
        <div class="s1">
            <h1>ÉTUDIANT EN GÉNIE INFORMATIQUE</h1> 
            <p>
                Je suis BELONE EYAMBA, étudiant en génie informatique basé au Cameroun. <br><br>
                Je suis disponible pour tous vos besoins de création de sites web vitrines mais aussi pour vos besoins d'automatisation des processus de gestion de vos entreprises. <br><br>
                Mon approche : <span>simplicité, efficacité, originalité.</span> Chaque projet est une opportunité de créer quelque chose d'impactant.
            </p>
        </div> 
        <div class="s2">
            <img src="maphoto.jpg" alt="Portrait de Belone Eyamba">
        </div> 
    </div>

    <section id="lang">
        <strong>COMPÉTENCES</strong>
        <h2>Technologies que je maîtrise</h2>
        <div class="nom"><span>HTML5</span>
            <div class="forme">
                <div id="html"><span>70%</span></div>
            </div>                    
        </div>    
        <div class="nom"><span>CSS</span>
            <div class="forme">
                <div id="css"><span>50%</span></div>
            </div>
        </div>       
        <div class="nom"><span>SQL</span>
            <div class="forme">
                <div id="sql"><span>40%</span></div>
            </div> 
        </div>
        <div class="nom"><span>PYTHON</span>
            <div class="forme">
                <div id="python"><span>40%</span></div>
            </div> 
        </div> 
        <div class="nom"><span>JAVASCRIPT</span>
            <div class="forme">
                <div id="java"><span>30%</span></div>
            </div>
        </div> 
    </section>

    <section id="a">
        <div class="outils">
            <h2>Outils & Environnement</h2>
            <ul>
                <li>VS CODE</li>
                <li>Analyse SI</li>
                <li>LOOPING</li>
            </ul>
        </div>
        <div class="special">
            <h3>Spécialités</h3>
            <ul>
                <li>Sites vitrines</li>
                <li>Modélisation des systèmes d'informations</li>
            </ul>
        </div>
    </section>

    <section id="futur">
        <h4 class="taille">Projets à venir</h4>
        <p class="projet">Chaque projet est une opportunité d'apprendre et de créer quelque chose d'unique.</p>
        <div class="projet"><a href="page.html" target="_blank">Réservation de billets de bus</a></div>
    </section>

    <section class="contact">
        <strong>CONTACTEZ-MOI</strong>
        <h2>Travaillons ensemble</h2>
        <p>Passionné par le développement web et la modélisation des systèmes d'informations, je suis disponible et ouvert à toute sollicitation professionnelle.<br>Mon sérieux et mes compétences techniques sont une garantie de travail bien fait.</p>
    </section>

    <section class="formulaire">
        <form action="">
            <table>
                <tr>
                    <td><label for="nom">Nom</label></td>
                    <td><input type="text" id="nom" placeholder="Votre nom"></td>
                </tr>
                <tr>
                    <td><label for="email" class="email">Adresse email</label></td>
                    <td><input type="email" id="email" placeholder="exemple@gmail.com"></td>
                </tr>
                <tr>
                    <td><label for="message">Commentaires</label></td>
                    <td><textarea name="commentaires" id="message" placeholder="Tapez ici vos commentaires"></textarea></td>
                </tr>   
                <tr>
                    <td colspan="2" style="text-align: center;">
                        <button type="submit">Envoyer</button>
                    </td> 
                </tr>
            </table>    
        </form>
    </section>

    <footer>
        © 2026 Belone Eyamba - Portfolio Étudiant
    </footer>

    <script>
    document.addEventListener("DOMContentLoaded", () => {
        // ==========================================
        // 1. ANIMATION DES BARRES DE COMPÉTENCES
        // ==========================================
        const skillsPercentages = {
            'html': '70%',
            'css': '50%',
            'sql': '40%',
            'python': '40%',
            'java': '30%'
        };

        const skillsSection = document.querySelector('#lang');

        const skillsObserver = new IntersectionObserver((entries, observer) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    Object.keys(skillsPercentages).forEach(id => {
                        const progressBar = document.getElementById(id);
                        if (progressBar) {
                            progressBar.style.setProperty('width', skillsPercentages[id], 'important');
                        }
                    });
                    observer.unobserve(entry.target);
                }
            });
        }, { threshold: 0.2 });

        if (skillsSection) {
            skillsObserver.observe(skillsSection);
        }

        // ==========================================
        // 2. EFFET DE FADE-IN AU DÉFILEMENT
        // ==========================================
        const sectionsToAnimate = document.querySelectorAll('#conteneur, #a, #futur, .contact, .formulaire');
        sectionsToAnimate.forEach(section => section.classList.add('fade-in-element'));

        const fadeObserver = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.classList.add('visible');
                }
            });
        }, { threshold: 0.1 });

        sectionsToAnimate.forEach(section => fadeObserver.observe(section));

        // ==========================================
        // 3. VALIDATION INTERACTIVE DU FORMULAIRE
        // ==========================================
        const form = document.querySelector('form');
        const emailInput = document.getElementById('email');
        const nomInput = document.getElementById('nom');

        if (form) {
            form.addEventListener('submit', (e) => {
                e.preventDefault();

                emailInput.style.borderColor = '';
                nomInput.style.borderColor = '';

                let isValid = true;

                if (nomInput.value.trim() === '') {
                    nomInput.style.borderColor = 'crimson';
                    isValid = false;
                }

                const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
                if (!emailRegex.test(emailInput.value)) {
                    emailInput.style.borderColor = 'crimson';
                    isValid = false;
                }

                if (isValid) {
                    const submitBtn = form.querySelector('button');
                    const originalText = submitBtn.innerText;
                    
                    submitBtn.style.backgroundColor = 'chartreuse';
                    submitBtn.style.color = 'black';
                    submitBtn.innerText = '✓ Message envoyé !';
                    form.reset();

                    setTimeout(() => {
                        submitBtn.style.backgroundColor = '';
                        submitBtn.style.color = '';
                        submitBtn.innerText = originalText;
                    }, 3000);
                }
            });
        }
    });
    </script>
</body> 
</html>
