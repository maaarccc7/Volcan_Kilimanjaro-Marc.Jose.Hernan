<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Misión Kilimanjaro | Ciencias 4º ESO</title>
    
    <!-- Fuentes y Iconos -->
    <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@500;700;900&family=Inter:wght@400;600&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">

    <style>
        /* --- VARIABLES DE COLOR --- */
        :root {
            --dark-rock: #111827; 
            --slate: #1f2937; 
            --magma: #ea580c; 
            --magma-glow: #f97316;
            --ash: #f3f4f6;
            --white: #ffffff;
            --success: #10b981;
            --danger: #ef4444;
        }

        /* --- RESET GLOBALES --- */
        * { margin: 0; padding: 0; box-sizing: border-box; }
        body { font-family: 'Inter', sans-serif; background-color: var(--ash); color: #374151; line-height: 1.6; overflow-x: hidden; }
        h1, h2, h3, h4 { font-family: 'Montserrat', sans-serif; color: var(--dark-rock); }
        
        /* --- NAVEGACIÓN Y MENÚ --- */
        nav { background-color: var(--dark-rock); position: sticky; top: 0; z-index: 1000; box-shadow: 0 4px 20px rgba(0,0,0,0.5); }
        .mobile-header { display: none; justify-content: space-between; align-items: center; padding: 15px 20px; }
        .mobile-header .logo { font-family: 'Montserrat'; font-weight: 900; font-size: 1.3rem; color: var(--magma); letter-spacing: 1px;}
        .menu-toggle { font-size: 1.8rem; cursor: pointer; color: var(--white); transition: 0.3s; }
        
        .nav-container { max-width: 1200px; margin: 0 auto; display: flex; justify-content: center; flex-wrap: wrap; transition: max-height 0.4s ease-out; }
        .nav-link { color: #d1d5db; text-decoration: none; font-family: 'Montserrat'; font-weight: 700; font-size: 0.85rem; padding: 1.2rem 1.5rem; cursor: pointer; transition: 0.3s; text-transform: uppercase; border-bottom: 3px solid transparent;}
        .nav-link:hover, .nav-link.active { color: var(--white); border-bottom: 3px solid var(--magma); background-color: rgba(255,255,255,0.05); }

        /* --- HERO (SOLO VISIBLE EN INICIO) --- */
        #main-hero { background: linear-gradient(to bottom, rgba(17,24,39,0.7), rgba(17,24,39,0.95)), url('https://images.unsplash.com/photo-1589553416260-f586c8f1514f?q=80&w=2000&auto=format&fit=crop') center/cover; padding: 100px 20px; text-align: center; border-bottom: 5px solid var(--magma); color: var(--white); display: block; animation: fadeIn 1s ease-out;}
        #main-hero h1 { font-size: 3.5rem; margin-bottom: 15px; color: var(--white); text-transform: uppercase; letter-spacing: 1px;}
        #main-hero p { font-size: 1.2rem; max-width: 800px; margin: 0 auto; color: #d1d5db; }
        .badge { background: var(--magma); color: white; padding: 5px 15px; border-radius: 20px; font-weight: bold; font-size: 0.9rem; display: inline-block; margin-bottom: 15px; box-shadow: 0 0 15px rgba(234, 88, 12, 0.5);}

        /* --- CONTENEDORES --- */
        .container { max-width: 1200px; margin: 40px auto; padding: 0 20px; min-height: 60vh; }
        .page-section { display: none; }
        .page-section.active { display: block; }
        
        .section-title { text-align: center; font-size: 2.5rem; margin-bottom: 40px; position: relative; padding-bottom: 15px;}
        .section-title::after { content: ''; position: absolute; bottom: 0; left: 50%; transform: translateX(-50%); width: 80px; height: 5px; background-color: var(--magma); border-radius: 3px;}

        /* --- EFECTOS DE ENTRADA EN CASCADA --- */
        .page-section.active .cascade-1 { animation: slideUpFade 0.5s ease-out 0.1s forwards; opacity: 0; }
        .page-section.active .cascade-2 { animation: slideUpFade 0.5s ease-out 0.2s forwards; opacity: 0; }
        .page-section.active .cascade-3 { animation: slideUpFade 0.5s ease-out 0.3s forwards; opacity: 0; }

        /* --- GRIDS Y TARJETAS INTERACTIVAS --- */
        .grid-2 { display: grid; grid-template-columns: 1fr 1fr; gap: 30px; margin-bottom: 30px;}
        .grid-3 { display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 30px; margin-bottom: 30px;}
        
        .card { background: var(--white); border-radius: 12px; padding: 35px; box-shadow: 0 8px 20px rgba(0,0,0,0.06); border: 1px solid #e5e7eb; transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275); position: relative; overflow: hidden;}
        .card:hover { transform: translateY(-10px) scale(1.02); box-shadow: 0 20px 40px rgba(234, 88, 12, 0.15); border-color: rgba(234, 88, 12, 0.3);}
        .card-icon { font-size: 2.5rem; color: var(--magma); margin-bottom: 20px; transition: 0.3s;}
        .card:hover .card-icon { transform: scale(1.2) rotate(5deg); }

        .map-box { border-radius: 12px; overflow: hidden; height: 100%; min-height: 350px; box-shadow: inset 0 0 10px rgba(0,0,0,0.1); }
        .map-box iframe { width: 100%; height: 100%; border: none; }

        /* --- LISTAS Y TOOLTIPS ANIMADOS --- */
        ul.bullet-list { margin-left: 20px; margin-top: 15px; }
        ul.bullet-list li { margin-bottom: 10px; }
        .highlight { color: var(--magma); font-weight: 700; }

        .tooltip-text { border-bottom: 2px dashed var(--magma); color: var(--slate); font-weight: 700; cursor: help; position: relative; transition: 0.2s;}
        .tooltip-text:hover { color: var(--magma); }
        .tooltip-text .tooltip-box { visibility: hidden; opacity: 0; position: absolute; bottom: 100%; left: 50%; transform: translateX(-50%) translateY(10px); background: var(--dark-rock); color: var(--white); padding: 15px; border-radius: 8px; width: 260px; font-size: 0.85rem; font-weight: normal; z-index: 100; transition: all 0.3s cubic-bezier(0.68, -0.55, 0.265, 1.55); text-align: center; box-shadow: 0 10px 20px rgba(0,0,0,0.3); pointer-events: none;}
        .tooltip-text .tooltip-box::after { content: ''; position: absolute; top: 100%; left: 50%; margin-left: -8px; border-width: 8px; border-style: solid; border-color: var(--dark-rock) transparent transparent transparent; }
        .tooltip-text:hover .tooltip-box { visibility: visible; opacity: 1; transform: translateX(-50%) translateY(-10px); }

        /* --- TABS INTERNAS (Pestañas) --- */
        .tabs-header { display: flex; justify-content: center; gap: 15px; margin-bottom: 30px; flex-wrap: wrap; }
        .tab-btn { background: var(--white); border: 2px solid #e5e7eb; padding: 12px 25px; font-family: 'Montserrat'; font-weight: 700; color: var(--text-main); border-radius: 8px; cursor: pointer; transition: 0.3s; position: relative; overflow: hidden;}
        .tab-btn:hover { border-color: var(--magma); color: var(--magma); transform: translateY(-2px);}
        .tab-btn.active { background: var(--dark-rock); color: var(--white); border-color: var(--dark-rock); box-shadow: 0 10px 20px rgba(17, 24, 39, 0.2); }
        
        .tab-content { display: none; }
        .tab-content.active { display: block; animation: slideInRight 0.5s cubic-bezier(0.23, 1, 0.32, 1) forwards; }

        /* --- TARJETAS GIRATORIAS (FLIP CARDS) --- */
        .flip-card { background-color: transparent; width: 100%; height: 260px; perspective: 1000px; }
        .flip-card-inner { position: relative; width: 100%; height: 100%; text-align: center; transition: transform 0.8s cubic-bezier(0.175, 0.885, 0.32, 1.275); transform-style: preserve-3d; }
        .flip-card:hover .flip-card-inner { transform: rotateY(180deg); }
        .flip-card-front, .flip-card-back { position: absolute; width: 100%; height: 100%; backface-visibility: hidden; border-radius: 12px; display: flex; flex-direction: column; justify-content: center; align-items: center; padding: 25px; box-shadow: 0 5px 15px rgba(0,0,0,0.08);}
        .flip-card-front { background-color: var(--white); border: 2px solid var(--border); }
        .flip-card-back { background-color: var(--dark-rock); color: var(--white); transform: rotateY(180deg); border: 2px solid var(--magma);}
        .flip-card-back h3 { color: var(--magma); margin-bottom: 10px;}

        /* --- INTERACTIVOS: SIMULADOR --- */
        .simulator-box { background: var(--dark-rock); border-radius: 16px; padding: 40px; color: var(--white); text-align: center; box-shadow: 0 15px 35px rgba(0,0,0,0.2);}
        .volcano-container { height: 220px; display: flex; align-items: flex-end; justify-content: center; margin: 30px 0; border-bottom: 4px solid #374151; position: relative;}
        .volcano { width: 0; height: 0; border-left: 120px solid transparent; border-right: 120px solid transparent; border-bottom: 160px solid #4b5563; position: relative; z-index: 2;}
        .crater { position: absolute; top: 160px; left: 50%; transform: translateX(-50%); width: 40px; height: 10px; background: #1f2937; border-radius: 50%; z-index: 3;}
        .lava { position: absolute; bottom: 0; left: -20px; width: 40px; height: 0; background: var(--magma); transition: height 0.5s; z-index: 1; box-shadow: 0 0 20px var(--magma-glow);}
        .ash-cloud { position: absolute; bottom: 160px; left: 50%; transform: translateX(-50%); width: 60px; height: 60px; background: #9ca3af; border-radius: 50%; opacity: 0; transition: all 0.5s; z-index: 0; filter: blur(8px);}
        input[type=range] { width: 100%; max-width: 500px; margin: 20px 0; accent-color: var(--magma); cursor: pointer; height: 8px;}
        .mag-display { font-family: 'Montserrat'; font-size: 4.5rem; font-weight: 900; color: var(--magma); line-height: 1; text-shadow: 0 0 15px rgba(234,88,12,0.4);}

        /* --- INTERACTIVOS: TEST CON SHAKE --- */
        .quiz-btn { width: 100%; padding: 18px; margin-bottom: 12px; background: #f8fafc; border: 2px solid #e5e7eb; border-radius: 8px; text-align: left; font-family: 'Inter'; font-size: 1rem; font-weight: 600; cursor: pointer; transition: 0.2s;}
        .quiz-btn:hover { border-color: var(--slate); transform: translateX(5px); }
        .quiz-btn.correct { background: #d1fae5; border-color: var(--success); color: #065f46; animation: bounceIn 0.5s;}
        .quiz-btn.wrong { background: #fee2e2; border-color: var(--danger); color: #991b1b; animation: shake 0.4s;}
        .quiz-feedback { margin-top: 15px; padding: 20px; border-radius: 8px; font-size: 0.95rem; display: none; font-weight: 600; animation: fadeIn 0.4s;}

        /* --- DONACIONES ($5 MILLONES) --- */
        .donation-container { max-width: 850px; margin: 0 auto; background: var(--white); border-radius: 16px; box-shadow: 0 20px 40px rgba(0,0,0,0.1); overflow: hidden; }
        .donation-header { background: var(--dark-rock); color: var(--white); padding: 40px; text-align: center; border-bottom: 5px solid var(--magma);}
        .progress-section { padding: 40px; background: #f8fafc; border-bottom: 1px solid #e5e7eb;}
        .progress-stats { display: flex; justify-content: space-between; margin-bottom: 15px; font-family: 'Montserrat'; font-size: 1.2rem; font-weight: 800;}
        .progress-bar-bg { background: #e2e8f0; height: 18px; border-radius: 20px; overflow: hidden; box-shadow: inset 0 2px 4px rgba(0,0,0,0.1); }
        .progress-bar-fill { height: 100%; background: linear-gradient(90deg, #ea580c, #ef4444); width: 77%; transition: width 1.5s cubic-bezier(0.4, 0, 0.2, 1); position: relative;}
        /* Animación de brillo en la barra */
        .progress-bar-fill::after { content: ''; position: absolute; top: 0; left: 0; right: 0; bottom: 0; background: linear-gradient(45deg, rgba(255,255,255,0.2) 25%, transparent 25%, transparent 50%, rgba(255,255,255,0.2) 50%, rgba(255,255,255,0.2) 75%, transparent 75%, transparent); background-size: 20px 20px; animation: moveStripes 1s linear infinite; }
        
        .donation-form-wrapper { padding: 40px; }
        .amount-buttons { display: flex; gap: 15px; margin-bottom: 25px; flex-wrap: wrap;}
        .btn-amount { flex: 1; padding: 15px; background: var(--white); border: 2px solid #e5e7eb; border-radius: 8px; font-family: 'Montserrat'; font-size: 1.2rem; font-weight: 800; cursor: pointer; transition: 0.2s; min-width: 100px;}
        .btn-amount:hover { border-color: var(--magma); transform: translateY(-3px);}
        .btn-amount.selected { border-color: var(--magma); background: #fff7ed; color: var(--magma); box-shadow: 0 5px 15px rgba(234,88,12,0.2);}
        .input-group { margin-bottom: 20px; }
        .input-group label { display: block; margin-bottom: 8px; font-weight: 600; font-size: 0.95rem; }
        .input-group input { width: 100%; padding: 15px; border: 2px solid #e5e7eb; border-radius: 8px; font-family: 'Inter'; font-size: 1rem; transition: 0.3s;}
        .input-group input:focus { outline: none; border-color: var(--magma); }
        .btn-submit { width: 100%; padding: 20px; background: var(--magma); color: var(--white); border: none; border-radius: 8px; font-family: 'Montserrat'; font-size: 1.2rem; font-weight: 800; cursor: pointer; transition: 0.3s; text-transform: uppercase;}
        .btn-submit:hover { background: var(--magma-glow); box-shadow: 0 10px 20px rgba(234,88,12,0.4); transform: translateY(-2px);}

        /* --- EQUIPO --- */
        .team-card { text-align: center; padding: 40px 20px; background: var(--white); border-radius: 12px; border: 1px solid #e5e7eb; position: relative; overflow: hidden; transition: 0.3s;}
        .team-card:hover { transform: translateY(-10px); box-shadow: 0 15px 30px rgba(0,0,0,0.1); }
        .team-card::before { content: ''; position: absolute; top: 0; left: 0; width: 100%; height: 6px; background: var(--magma); border-radius: 12px 12px 0 0;}
        .team-avatar { width: 120px; height: 120px; background: var(--dark-rock); color: var(--magma); border-radius: 50%; display: flex; align-items: center; justify-content: center; font-size: 3rem; margin: 0 auto 20px; font-family: 'Montserrat'; font-weight: 900; border: 5px solid #f3f4f6; box-shadow: 0 10px 15px rgba(0,0,0,0.1); transition: 0.5s;}
        .team-card:hover .team-avatar { transform: rotateY(180deg); background: var(--magma); color: var(--white); }

        /* --- MODAL (POP-UP) --- */
        .modal-overlay { display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(17, 24, 39, 0.85); z-index: 2000; align-items: center; justify-content: center; backdrop-filter: blur(5px);}
        .modal-content { background: var(--white); padding: 50px; border-radius: 20px; text-align: center; max-width: 90%; width: 450px; border-bottom: 8px solid var(--success); animation: zoomIn 0.3s cubic-bezier(0.175, 0.885, 0.32, 1.275);}

        /* --- KEYFRAMES (ANIMACIONES) --- */
        @keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }
        @keyframes slideUpFade { from { opacity: 0; transform: translateY(30px); } to { opacity: 1; transform: translateY(0); } }
        @keyframes slideInRight { from { opacity: 0; transform: translateX(30px); } to { opacity: 1; transform: translateX(0); } }
        @keyframes zoomIn { from { opacity: 0; transform: scale(0.8); } to { opacity: 1; transform: scale(1); } }
        @keyframes moveStripes { 0% { background-position: 0 0; } 100% { background-position: 40px 0; } }
        @keyframes erupt { 0% { height: 0; opacity: 0;} 100% { height: 250px; width: 250px; opacity: 0.9; transform: translateX(-50%) scale(1.5);} }
        @keyframes rumble { 0% { transform: translate(0,0);} 25% { transform: translate(-2px,2px);} 50% { transform: translate(2px,-2px);} 75% { transform: translate(-2px,-2px);} 100% { transform: translate(0,0);} }
        @keyframes shake { 0%, 100% {transform: translateX(0);} 20%, 60% {transform: translateX(-10px);} 40%, 80% {transform: translateX(10px);} }
        @keyframes bounceIn { 0% {transform: scale(0.9);} 50% {transform: scale(1.05);} 100% {transform: scale(1);} }

        /* --- RESPONSIVE MÓVIL --- */
        @media (max-width: 768px) {
            .mobile-header { display: flex; }
            .nav-container { flex-direction: column; overflow: hidden; max-height: 0; background: var(--dark-rock); }
            .nav-container.active { max-height: 500px; }
            .nav-link { padding: 1.2rem; border-bottom: 1px solid rgba(255,255,255,0.05); text-align: center; width: 100%;}
            .grid-2 { grid-template-columns: 1fr; }
            #main-hero { padding: 80px 20px; }
            #main-hero h1 { font-size: 2.2rem; }
            .section-title { font-size: 1.8rem; }
        }
    </style>
</head>
<body>

    <!-- NAVEGACIÓN PRINCIPAL -->
    <nav>
        <div class="mobile-header">
            <div class="logo"><i class="fa-solid fa-fire"></i> KILIMANJARO</div>
            <div class="menu-toggle" onclick="toggleMenu()"><i class="fa-solid fa-bars" id="menu-icon"></i></div>
        </div>
        <div class="nav-container" id="nav-menu">
            <a onclick="showSection('inicio')" class="nav-link active" id="link-inicio">Inicio</a>
            <a onclick="showSection('volcan-fondo')" class="nav-link" id="link-volcan-fondo">El Volcán a Fondo</a>
            <a onclick="showSection('impacto')" class="nav-link" id="link-impacto">Riesgos y Daños</a>
            <a onclick="showSection('prevencion')" class="nav-link" id="link-prevencion">Prevención</a>
            <a onclick="showSection('interactivos')" class="nav-link" id="link-interactivos"><i class="fa-solid fa-gamepad"></i> Interactivos</a>
            <a onclick="showSection('donaciones')" class="nav-link" id="link-donaciones" style="color: var(--magma);"><i class="fa-solid fa-hand-holding-heart"></i> Donar</a>
            <a onclick="showSection('equipo')" class="nav-link" id="link-equipo">Ingenieros</a>
        </div>
    </nav>

    <!-- CABECERA (SOLO SE VE EN INICIO) -->
    <header id="main-hero">
        <span class="badge">Ciencias de la Tierra - 4º ESO</span>
        <h1>Volcán Kilimanjaro</h1>
        <p>Aprende de forma visual y directa la tectónica de placas, la sismología y los riesgos ambientales del "Techo de África".</p>
    </header>

    <main class="container">
        
        <!-- 1. INICIO -->
        <section id="inicio" class="page-section active">
            <h2 class="section-title cascade-1">Expediente Geológico</h2>
            <div class="card cascade-2" style="text-align: center;">
                <i class="fa-solid fa-mountain card-icon" style="font-size: 4rem;"></i>
                <h3 style="font-size: 1.8rem; margin-bottom: 15px;">¿Sabías que la montaña más alta de África es un volcán?</h3>
                <p style="font-size: 1.1rem; max-width: 800px; margin: 0 auto;">El monte Kilimanjaro (Tanzania) es un <strong>estratovolcán</strong> gigante de 5,895 metros. Navega por las secciones del menú superior para descubrir cómo el movimiento del interior de la Tierra lo creó, por qué los volcanes también generan terremotos, y la terrible amenaza climática que sufre hoy en día.</p>
            </div>
        </section>

        <!-- 2. EL VOLCÁN A FONDO (SUBPÁGINAS / PESTAÑAS) -->
        <section id="volcan-fondo" class="page-section">
            <h2 class="section-title cascade-1">El Kilimanjaro a Fondo</h2>
            <p class="cascade-1" style="text-align:center; margin-bottom: 30px;">Toda la geología del volcán explicada paso a paso. <strong>Selecciona una pestaña:</strong></p>
            
            <div class="tabs-header cascade-2">
                <button class="tab-btn active" onclick="openTab('tab-placas', 'fondo-tabs', this)"><i class="fa-solid fa-map-location-dot"></i> Ubicación y Placas</button>
                <button class="tab-btn" onclick="openTab('tab-dinamica', 'fondo-tabs', this)"><i class="fa-solid fa-fire"></i> Dinámica Interna</button>
                <button class="tab-btn" onclick="openTab('tab-sismos', 'fondo-tabs', this)"><i class="fa-solid fa-wave-square"></i> Sismos Volcánicos</button>
            </div>

            <!-- Pestaña 1: Placas -->
            <div class="card fondo-tabs active cascade-3" id="tab-placas">
                <div class="grid-2" style="margin-bottom: 0;">
                    <div>
                        <h3 style="margin-bottom: 15px; color: var(--magma); font-size: 1.5rem;">¿Dónde está y qué placas lo forman?</h3>
                        <p>Se localiza en el <strong>Gran Valle del Rift (Tanzania, África)</strong>. Literalmente, la corteza terrestre de África se está partiendo en dos.</p>
                        <ul class="bullet-list">
                            <li><strong>Placas Implicadas:</strong> La <span class="highlight">Placa Nubia</span> y la <span class="highlight">Placa Somalí</span>.</li>
                            <li><strong>Tipo de Borde:</strong> Es un <span class="tooltip-text">Borde Divergente<span class="tooltip-box">Límite donde dos placas tectónicas se SEPARAN. Esto crea fallas (grietas) por donde puede subir el magma.</span></span>.</li>
                        </ul>
                    </div>
                    <div class="map-box">
                        <iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d508930.22277457785!2d37.014498305374495!3d-3.076045059632837!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x1839db43e74880bb%3A0xb1575fc176cdb2c9!2sMonte%20Kilimanjaro!5e0!3m2!1ses!2ses!4v1700000000000!5m2!1ses!2ses" allowfullscreen="" loading="lazy"></iframe>
                    </div>
                </div>
            </div>

            <!-- Pestaña 2: Dinámica -->
            <div class="card fondo-tabs cascade-3" id="tab-dinamica">
                <h3 style="margin-bottom: 15px; color: var(--magma); font-size: 1.5rem;">¿Qué movimiento se produce y por qué?</h3>
                <p>El movimiento es <strong>de separación</strong>. La corteza se estira, se hace delgada y se fractura.</p>
                <ul class="bullet-list">
                    <li><strong>Relación con la Dinámica Interna:</strong> El motor de todo esto son las <span class="tooltip-text">Corrientes de Convección<span class="tooltip-box">Movimientos circulares en el manto de la Tierra: el material caliente (menos denso) sube, y al enfriarse baja. Como agua hirviendo.</span></span> del manto terrestre.</li>
                    <li><strong>La creación del volcán:</strong> Estas corrientes empujan las placas hacia lados opuestos. Por la grieta generada (falla), asciende una <em>pluma de magma</em> hirviendo que, al salir a la superficie y enfriarse capa tras capa, formó el Kilimanjaro.</li>
                </ul>
            </div>

            <!-- Pestaña 3: Sismos y Ondas -->
            <div class="card fondo-tabs cascade-3" id="tab-sismos">
                <h3 style="margin-bottom: 15px; color: var(--magma); font-size: 1.5rem;">Sismología: ¿Los volcanes dan temblores?</h3>
                <p>¡Sí! Cuando el magma intenta subir a la superficie, rompe la roca sólida de la corteza, generando <strong>terremotos volcánicos</strong> (Enjambres sísmicos).</p>
                <ul class="bullet-list" style="margin-bottom: 30px;">
                    <li><strong>Magnitud:</strong> En lugar de la escala de Richter, las erupciones volcánicas se miden con el <span class="highlight">VEI (Índice de Explosividad)</span>, del 0 al 8. Mide cuánta ceniza y lava expulsa.</li>
                    <li><strong>Intensidad:</strong> Se usa la escala de Mercalli para medir los daños visuales en los poblados cercanos.</li>
                </ul>
                
                <h4 style="text-align: center; margin-bottom: 20px;">Ondas Sísmicas que genera (Pasa el ratón)</h4>
                <div class="grid-3" style="margin-bottom: 0;">
                    <div class="flip-card">
                        <div class="flip-card-inner">
                            <div class="flip-card-front">
                                <i class="fa-solid fa-bolt card-icon"></i>
                                <h3>Ondas P (Primarias)</h3>
                            </div>
                            <div class="flip-card-back">
                                <h3>Ondas P</h3>
                                <p>Las más rápidas. Comprimen y estiran la roca como un acordeón en la dirección que viajan.</p>
                            </div>
                        </div>
                    </div>
                    <div class="flip-card">
                        <div class="flip-card-inner">
                            <div class="flip-card-front">
                                <i class="fa-solid fa-water card-icon"></i>
                                <h3>Ondas S (Secundarias)</h3>
                            </div>
                            <div class="flip-card-back">
                                <h3>Ondas S</h3>
                                <p>Llegan después. Mueven el suelo de arriba a abajo o de lado a lado. Solo viajan por sólidos.</p>
                            </div>
                        </div>
                    </div>
                    <div class="flip-card">
                        <div class="flip-card-inner">
                            <div class="flip-card-front">
                                <i class="fa-solid fa-house-crack card-icon"></i>
                                <h3>Ondas Superficiales</h3>
                            </div>
                            <div class="flip-card-back">
                                <h3>Love y Rayleigh</h3>
                                <p>Viajan por la superficie terrestre. Son las más lentas pero las más <strong>destructivas</strong> para las casas.</p>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- 3. IMPACTO Y RIESGOS -->
        <section id="impacto" class="page-section">
            <h2 class="section-title cascade-1">Impacto y Daños</h3>
            <div class="grid-2 cascade-2">
                <div class="card">
                    <i class="fa-solid fa-house-chimney-crack card-icon"></i>
                    <h3 style="color: var(--magma); margin-bottom: 15px;">Daños Humanos y Materiales</h3>
                    <p>El Kilimanjaro está <em>dormido</em>, pero si despertara hoy, los daños serían catastróficos.</p>
                    <ul class="bullet-list">
                        <li><strong>Por qué sería tan destructivo:</strong> No por la lava, sino por las inmensas nubes de gas tóxico y cenizas que arruinarían los cultivos de Tanzania y Kenia.</li>
                        <li>El hielo de la cima se derretiría de golpe, creando <span class="tooltip-text">Lahares<span class="tooltip-box">Avalanchas gigantes de barro, rocas y agua hirviendo que bajan por la ladera arrasando ciudades enteras.</span></span> mortales para la tribu Chagga.</li>
                    </ul>
                </div>
                <div class="card">
                    <i class="fa-solid fa-snowflake card-icon" style="color: #3b82f6;"></i>
                    <h3 style="color: #3b82f6; margin-bottom: 15px;">Impacto Ambiental (El riesgo real)</h3>
                    <p>El verdadero peligro del Kilimanjaro hoy no es el magma, es el <strong>Cambio Climático</strong>.</p>
                    <ul class="bullet-list">
                        <li>Sus famosos glaciares (las nieves del Kilimanjaro) han desaparecido un <strong>80% desde el año 1912</strong>.</li>
                        <li><strong>Impacto:</strong> Si el hielo desaparece, los ríos que bajan de la montaña se secarán, destruyendo la flora, la fauna (elefantes, cebras) y dejando sin agua potable a la población local.</li>
                    </ul>
                </div>
            </div>
        </section>

        <!-- 4. PREVENCIÓN -->
        <section id="prevencion" class="page-section">
            <h2 class="section-title cascade-1">Prevención: ¿Se puede evitar?</h2>
            <div class="card cascade-2" style="text-align: center; border-top: 6px solid var(--success);">
                <i class="fa-solid fa-shield-heart" style="font-size: 3.5rem; color: var(--success); margin-bottom: 15px;"></i>
                <h3 style="margin-bottom: 15px; font-size: 1.8rem;">La erupción NO, las muertes SÍ</h3>
                <p style="max-width: 800px; margin: 0 auto 20px;">A diferencia de los terremotos de las fallas tectónicas, los volcanes <strong>sí avisan antes de estallar</strong>. El magma tarda semanas o meses en subir, lo que nos da tiempo para evacuar a la población. Así es como lo prevenimos hoy:</p>
                
                <div class="grid-3" style="text-align: left; margin-top: 30px; margin-bottom: 0;">
                    <div style="background: var(--ash); padding: 20px; border-radius: 8px; border-left: 4px solid var(--magma);">
                        <h4 style="color: var(--dark-rock); margin-bottom: 5px;"><i class="fa-solid fa-wave-square" style="color: var(--magma);"></i> Sismógrafos</h4>
                        <p style="font-size: 0.9rem;">Instalados en la roca para detectar los temblores armónicos (el ruido del magma moviéndose por la chimenea).</p>
                    </div>
                    <div style="background: var(--ash); padding: 20px; border-radius: 8px; border-left: 4px solid var(--magma);">
                        <h4 style="color: var(--dark-rock); margin-bottom: 5px;"><i class="fa-solid fa-satellite" style="color: var(--magma);"></i> Satélites</h4>
                        <p style="font-size: 0.9rem;">Vigilan desde el espacio si la montaña se "hincha" o se deforma por la enorme presión del gas acumulado en el interior.</p>
                    </div>
                    <div style="background: var(--ash); padding: 20px; border-radius: 8px; border-left: 4px solid var(--magma);">
                        <h4 style="color: var(--dark-rock); margin-bottom: 5px;"><i class="fa-solid fa-smog" style="color: var(--magma);"></i> Sensores de Gas</h4>
                        <p style="font-size: 0.9rem;">Analizan el humo del cráter. Si sube el nivel de Dióxido de Azufre (SO2), significa que el magma está muy cerca de la salida.</p>
                    </div>
                </div>
            </div>
        </section>

        <!-- 5. INTERACTIVOS -->
        <section id="interactivos" class="page-section">
            <h2 class="section-title cascade-1">Centro Interactivo</h2>
            
            <div class="grid-2 cascade-2">
                <!-- Simulador VEI -->
                <div class="simulator-box">
                    <h3 style="margin-bottom: 10px;">Simulador VEI (Fuerza Eruptiva)</h3>
                    <p style="font-size: 0.9rem; margin-bottom: 20px;">Desliza la barra para ver la escala eruptiva (0 a 8).</p>
                    
                    <div class="mag-display" id="mag-value">0</div>
                    <input type="range" id="mag-slider" min="0" max="8" step="1" value="0" oninput="updateSimulator(this.value)">
                    <p id="mag-desc" style="min-height: 45px; margin-top: 10px; font-weight: bold; color: var(--magma);">Nivel 0: Erupción Hawaiana. Lava fluida, sin explosión.</p>
                    
                    <div class="volcano-container" id="volcano-sim">
                        <div class="ash-cloud" id="ash-cloud"></div>
                        <div class="volcano">
                            <div class="crater"></div>
                            <div class="lava" id="lava"></div>
                        </div>
                    </div>
                </div>

                <!-- Test de Supervivencia (Con Shake effect) -->
                <div class="card">
                    <h3 style="color: var(--dark-rock); margin-bottom: 15px;"><i class="fa-solid fa-person-hiking" style="color: var(--magma);"></i> Test de Supervivencia</h3>
                    <p style="margin-bottom: 20px; font-weight: 600;">Estás de excursión escolar cerca del cráter del volcán. De repente, sientes un temblor fuerte bajo tus pies y sale una nube de gas con olor a huevo podrido (azufre). ¿Qué haces?</p>
                    
                    <div id="quiz-container">
                        <button class="quiz-btn" onclick="answerQuiz(this, false)">A) Me escondo dentro de una cueva honda para protegerme.</button>
                        <button class="quiz-btn" onclick="answerQuiz(this, false)">B) Me acerco rápido al borde para grabar la lava con el móvil.</button>
                        <button class="quiz-btn" onclick="answerQuiz(this, true)">C) Me cubro la nariz con un paño húmedo y bajo de la montaña ya.</button>
                    </div>
                    <div id="quiz-feedback" class="quiz-feedback"></div>
                </div>
            </div>
        </section>

        <!-- 6. DONACIONES -->
        <section id="donaciones" class="page-section">
            <h2 class="section-title cascade-1">Fondo de Investigación Escolar</h2>
            <div class="donation-container cascade-2">
                <div class="donation-header">
                    <h2 style="font-size:2.2rem; margin-bottom: 10px; color: var(--white);">Proyecto Salvemos el Glaciar</h2>
                    <p style="opacity: 0.9; font-size: 1.1rem;">Fondo de $5 Millones para instalar tecnología de monitoreo en África.</p>
                </div>
                
                <div class="progress-section">
                    <div class="progress-stats">
                        <span>Recaudado: <span id="amount-raised" style="color: var(--magma);">$3,850,500</span></span>
                        <span>Meta: $5,000,000 USD</span>
                    </div>
                    <div class="progress-bar-bg">
                        <div class="progress-bar-fill" id="progress-bar"></div>
                    </div>
                </div>

                <div class="donation-form-wrapper">
                    <form onsubmit="processDonation(event)">
                        <label style="font-weight: 800; margin-bottom: 15px; display: block; color: var(--dark-rock);">Selecciona la aportación ficticia de tu clase:</label>
                        <div class="amount-buttons">
                            <button type="button" class="btn-amount selected" onclick="selectAmount(this, 100)">$100</button>
                            <button type="button" class="btn-amount" onclick="selectAmount(this, 500)">$500</button>
                            <button type="button" class="btn-amount" onclick="selectAmount(this, 1000)">$1,000</button>
                        </div>
                        <input type="hidden" id="donation-amount" value="100">

                        <div class="grid-2" style="margin-bottom: 0;">
                            <div class="input-group">
                                <label>Nombre del Alumno o Instituto</label>
                                <input type="text" required placeholder="Ej. IES Ciencias - 4º ESO">
                            </div>
                            <div class="input-group">
                                <label>Código de Beca Ficticia</label>
                                <input type="text" required placeholder="XX-4ESO-XX">
                            </div>
                        </div>

                        <button type="submit" class="btn-submit"><i class="fa-solid fa-paper-plane"></i> Enviar Donación Simbólica</button>
                    </form>
                </div>
            </div>
        </section>

        <!-- 7. EQUIPO -->
        <section id="equipo" class="page-section">
            <h2 class="section-title cascade-1">Equipo de Ingenieros (IGV)</h2>
            <div class="grid-3 cascade-2">
                <div class="team-card">
                    <div class="team-avatar">MA</div>
                    <h3 style="margin-bottom: 5px;">Marc Alemany</h3>
                    <p style="color: var(--magma); font-weight: 800; font-size: 0.95rem; margin-bottom: 15px; text-transform: uppercase;">Ingeniero Vulcanólogo</p>
                    <p style="font-size: 0.9rem;">Experto en magmatismo y placas tectónicas. Estudia las fallas del Gran Valle del Rift y la composición química de las rocas del volcán.</p>
                </div>
                
                <div class="team-card">
                    <div class="team-avatar">HM</div>
                    <h3 style="margin-bottom: 5px;">Hernán Martínez</h3>
                    <p style="color: var(--magma); font-weight: 800; font-size: 0.95rem; margin-bottom: 15px; text-transform: uppercase;">Ingeniero Sismólogo</p>
                    <p style="font-size: 0.9rem;">Especialista en ondas sísmicas P y S. Se encarga de instalar los sismógrafos en la montaña para detectar si el volcán se está despertando.</p>
                </div>
                
                <div class="team-card">
                    <div class="team-avatar">JM</div>
                    <h3 style="margin-bottom: 5px;">Jose Muñoz</h3>
                    <p style="color: var(--magma); font-weight: 800; font-size: 0.95rem; margin-bottom: 15px; text-transform: uppercase;">Ingeniero Ambiental</p>
                    <p style="font-size: 0.9rem;">Experto en prevención de riesgos climáticos. Mide el ritmo del deshielo glaciar y crea mapas de evacuación en caso de avalanchas de lodo (lahares).</p>
                </div>
            </div>
        </section>

    </main>

    <!-- MODAL (POP-UP DONACIÓN) -->
    <div class="modal-overlay" id="success-modal">
        <div class="modal-content">
            <i class="fa-solid fa-check-circle" style="font-size: 4rem; color: var(--success); margin-bottom: 20px;"></i>
            <h3 style="font-size: 1.8rem; margin-bottom: 15px;">¡Aportación Registrada!</h3>
            <p style="margin: 15px 0; font-size: 1.1rem;">Tu clase ha donado <strong>$<span id="modal-amount"></span> USD</strong> al proyecto de ciencias.</p>
            <p style="font-size: 0.85rem; color: var(--text-light); background: var(--ash); padding: 10px; border-radius: 5px; margin-bottom: 25px;">(Aviso: Plataforma educativa, no se realizan cargos reales).</p>
            <button class="btn-submit" onclick="document.getElementById('success-modal').style.display='none'">Cerrar Panel</button>
        </div>
    </div>

    <!-- SCRIPTS INTERACTIVOS -->
    <script>
        // --- 1. MENÚ MÓVIL Y NAVEGACIÓN ---
        function toggleMenu() {
            const nav = document.getElementById('nav-menu');
            const icon = document.getElementById('menu-icon');
            nav.classList.toggle('active');
            icon.className = nav.classList.contains('active') ? "fa-solid fa-xmark" : "fa-solid fa-bars";
        }

        function showSection(sectionId) {
            // Ocultar todas las secciones y quitar activo de links
            document.querySelectorAll('.page-section').forEach(sec => sec.classList.remove('active'));
            document.querySelectorAll('.nav-link').forEach(link => link.classList.remove('active'));
            
            // Mostrar la seleccionada
            document.getElementById(sectionId).classList.add('active');
            document.getElementById('link-' + sectionId).classList.add('active');
            
            // Lógica para mostrar/ocultar el HERO (La imagen gigante)
            const hero = document.getElementById('main-hero');
            if(sectionId === 'inicio') {
                hero.style.display = 'block';
            } else {
                hero.style.display = 'none'; // Se oculta para que el usuario vea el contenido directamente
            }

            // Cerrar menú en móvil
            const nav = document.getElementById('nav-menu');
            if(nav.classList.contains('active')) toggleMenu();

            // Desplazar suavemente hasta el inicio del contenedor
            window.scrollTo({ top: 0, behavior: 'smooth' });
        }

        // --- 2. PESTAÑAS INTERNAS (TABS) ---
        function openTab(tabId, groupClass, btn) {
            document.querySelectorAll('.' + groupClass).forEach(el => el.classList.remove('active'));
            btn.parentElement.querySelectorAll('.tab-btn').forEach(b => b.classList.remove('active'));
            document.getElementById(tabId).classList.add('active');
            btn.classList.add('active');
        }

        // --- 3. SIMULADOR VEI ---
        function updateSimulator(val) {
            document.getElementById('mag-value').innerText = val;
            const volcanoContainer = document.getElementById('volcano-sim');
            const lava = document.getElementById('lava');
            const ash = document.getElementById('ash-cloud');
            const desc = document.getElementById('mag-desc');
            
            // Reiniciar animaciones CSS
            volcanoContainer.style.animation = 'none';
            lava.style.height = '0';
            ash.style.animation = 'none';
            ash.style.opacity = '0';
            void volcanoContainer.offsetWidth; // Magia para reiniciar CSS

            if (val == 0) {
                desc.innerText = "Nivel 0: Erupción Hawaiana. La lava fluye suave y despacio.";
            } else if (val >= 1 && val <= 3) {
                desc.innerText = "Nivel " + val + ": Erupción Estromboliana. Explosiones moderadas y temblores.";
                volcanoContainer.style.animation = 'rumble 0.3s infinite';
                lava.style.height = '30px';
                ash.style.animation = 'erupt 2s forwards';
                ash.style.background = '#9ca3af';
            } else if (val >= 4 && val <= 6) {
                desc.innerText = "Nivel " + val + ": Erupción Pliniana. Muy destructiva. Columna de ceniza gigante.";
                volcanoContainer.style.animation = 'rumble 0.1s infinite';
                lava.style.height = '60px';
                ash.style.animation = 'erupt 1s forwards';
                ash.style.background = '#4b5563';
            } else {
                desc.innerText = "Nivel " + val + ": Súper Volcán. Capaz de cambiar el clima global por bloquear el sol.";
                volcanoContainer.style.animation = 'rumble 0.05s infinite';
                lava.style.height = '120px';
                ash.style.animation = 'erupt 0.5s forwards';
                ash.style.background = '#111827';
            }
        }

        // --- 4. TEST CON ANIMACIONES ---
        function answerQuiz(btn, isCorrect) {
            const container = document.getElementById('quiz-container');
            const feedback = document.getElementById('quiz-feedback');
            
            // Bloquear clics extra
            container.querySelectorAll('button').forEach(b => b.style.pointerEvents = 'none');
            
            // Quitar clases previas de animación
            btn.classList.remove('correct', 'wrong');
            void btn.offsetWidth; // reset anim

            if(isCorrect) {
                btn.classList.add('correct');
                feedback.innerHTML = "<i class='fa-solid fa-check'></i> <strong>¡Correcto!</strong> Los gases volcánicos (como el azufre) son letales. Debes proteger tus pulmones y descender rápidamente.";
                feedback.style.background = "#d1fae5"; feedback.style.color = "#065f46";
            } else {
                btn.classList.add('wrong');
                feedback.innerHTML = "<i class='fa-solid fa-xmark'></i> <strong>¡Error Crítico!</strong> Las cuevas son trampas mortales. Los gases tóxicos pesan más que el aire y se acumulan en el suelo asfixiándote. Debes bajar de la montaña rápido.";
                feedback.style.background = "#fee2e2"; feedback.style.color = "#991b1b";
            }
            feedback.style.display = 'block';
        }

        // --- 5. DONACIONES (BARRA DE PROGRESO) ---
        let currentRaised = 3850500;
        const goal = 5000000;

        function formatNumber(num) { return num.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ","); }

        function selectAmount(el, amount) {
            document.querySelectorAll('.btn-amount').forEach(b => b.classList.remove('selected'));
            el.classList.add('selected');
            document.getElementById('donation-amount').value = amount;
        }

        function processDonation(e) {
            e.preventDefault();
            const amount = parseInt(document.getElementById('donation-amount').value);
            currentRaised += amount;
            if(currentRaised > goal) currentRaised = goal; 
            
            // Actualizar textos y barra
            document.getElementById('amount-raised').innerText = "$" + formatNumber(currentRaised);
            document.getElementById('progress-bar').style.width = (currentRaised / goal * 100) + '%';
            
            // Mostrar Modal emergente
            document.getElementById('modal-amount').innerText = formatNumber(amount);
            document.getElementById('success-modal').style.display = 'flex';
        }
    </script>
</body>
</html>
