
Tu vas améliorer le fichier HTML ci-dessous pour qu’il serve de maquette de présentation client (Vanillextra), sans backend.

Contraintes STRICTES :

- Conserver le style premium café-vanille (palette, typos, cards, sections).
- Remplacer les informations inventées (ex: taux vanilline) par “Sur demande (B2B)”.
- Mettre des images placeholders via <img> avec URL neutre (placehold.co) et commentaires “À remplacer par photos cliente”.
- Garder une navigation anchor (#accueil, #produits, etc.).
- Ne pas ajouter de framework supplémentaire (garder Tailwind CDN ok).
- Le code final doit être propre, lisible, et prêt à ouvrir en double-cliquant (fichier unique).

Améliorations attendues :
1) Harmoniser les CTA : “Demander un devis” (B2B) / “Acheter” (B2C).
2) Ajouter une mini-section “Pourquoi le sous-vide ?” (3 bullets) dans la page.
3) Ajouter une mini-section “Process & Traçabilité” (3 étapes) dans Origine.
4) Ajouter un bandeau “Extrait/Essence sur commande” bien visible.

Voici le fichier à modifier : 
<!DOCTYPE html>
<html lang="fr" class="h-full">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Vanillextra — Vanille Premium de Madagascar</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,400;0,500;0,600;0,700;1,400&family=Montserrat:wght@300;400;500;600&display=swap" rel="stylesheet">
  <script src="/_sdk/element_sdk.js"></script>
  <style>
    body {
      box-sizing: border-box;
    }
    
    :root {
      --vanilla-deep: #3D2914;
      --vanilla-gold: #C4A35A;
      --cream-warm: #F5F0E8;
      --black-matte: #1A1A1A;
      --text-dark: #2C2418;
    }
    
    .font-serif {
      font-family: 'Cormorant Garamond', serif;
    }
    
    .font-sans {
      font-family: 'Montserrat', sans-serif;
    }
    
    .bg-vanilla-deep { background-color: var(--vanilla-deep); }
    .bg-vanilla-gold { background-color: var(--vanilla-gold); }
    .bg-cream-warm { background-color: var(--cream-warm); }
    .bg-black-matte { background-color: var(--black-matte); }
    
    .text-vanilla-deep { color: var(--vanilla-deep); }
    .text-vanilla-gold { color: var(--vanilla-gold); }
    .text-cream-warm { color: var(--cream-warm); }
    .text-dark { color: var(--text-dark); }
    
    .border-vanilla-gold { border-color: var(--vanilla-gold); }
    
    .hero-gradient {
      background: linear-gradient(135deg, rgba(61, 41, 20, 0.95) 0%, rgba(26, 26, 26, 0.9) 100%);
    }
    
    .gold-gradient {
      background: linear-gradient(90deg, #C4A35A 0%, #D4B86A 50%, #C4A35A 100%);
    }
    
    .card-hover {
      transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
    }
    
    .card-hover:hover {
      transform: translateY(-8px);
      box-shadow: 0 20px 40px rgba(61, 41, 20, 0.15);
    }
    
    .btn-primary {
      background: var(--vanilla-deep);
      color: var(--cream-warm);
      transition: all 0.3s ease;
    }
    
    .btn-primary:hover {
      background: var(--black-matte);
    }
    
    .btn-outline {
      border: 1px solid var(--vanilla-gold);
      color: var(--vanilla-gold);
      transition: all 0.3s ease;
    }
    
    .btn-outline:hover {
      background: var(--vanilla-gold);
      color: var(--vanilla-deep);
    }
    
    .nav-link {
      position: relative;
    }
    
    .nav-link::after {
      content: '';
      position: absolute;
      bottom: -4px;
      left: 0;
      width: 0;
      height: 1px;
      background: var(--vanilla-gold);
      transition: width 0.3s ease;
    }
    
    .nav-link:hover::after {
      width: 100%;
    }
    
    .section-divider {
      width: 60px;
      height: 2px;
      background: linear-gradient(90deg, transparent, var(--vanilla-gold), transparent);
    }
    
    .image-placeholder {
      background: linear-gradient(145deg, #2C2418 0%, #1A1A1A 100%);
      position: relative;
      overflow: hidden;
    }
    
    .image-placeholder::before {
      content: '';
      position: absolute;
      top: 0;
      left: -100%;
      width: 100%;
      height: 100%;
      background: linear-gradient(90deg, transparent, rgba(196, 163, 90, 0.1), transparent);
      animation: shimmer 3s infinite;
    }
    
    @keyframes shimmer {
      0% { left: -100%; }
      100% { left: 100%; }
    }
    
    .fade-in {
      animation: fadeIn 0.8s ease-out forwards;
    }
    
    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(20px); }
      to { opacity: 1; transform: translateY(0); }
    }
    
    .scroll-section {
      scroll-margin-top: 80px;
    }
    
    /* Dropdown Styles */
    .dropdown {
      position: relative;
    }
    
    .dropdown-menu {
      position: absolute;
      top: 100%;
      left: 0;
      min-width: 220px;
      background: var(--cream-warm);
      border: 1px solid rgba(196, 163, 90, 0.3);
      box-shadow: 0 10px 30px rgba(0,0,0,0.1);
      opacity: 0;
      visibility: hidden;
      transform: translateY(10px);
      transition: all 0.3s ease;
      z-index: 100;
    }
    
    .dropdown:hover .dropdown-menu {
      opacity: 1;
      visibility: visible;
      transform: translateY(0);
    }
    
    .dropdown-item {
      display: block;
      padding: 12px 20px;
      color: var(--text-dark);
      font-size: 0.875rem;
      transition: all 0.2s ease;
    }
    
    .dropdown-item:hover {
      background: rgba(196, 163, 90, 0.1);
      color: var(--vanilla-deep);
      padding-left: 24px;
    }
  </style>
</head>
<body class="h-full font-sans bg-cream-warm text-dark">
  <div id="app-wrapper" class="w-full h-full overflow-auto">
    
    <!-- Header -->
    <header id="header" class="fixed top-0 left-0 right-0 z-50 transition-all duration-300" style="background: rgba(245, 240, 232, 0.98); backdrop-filter: blur(10px);">
      <div class="max-w-7xl mx-auto px-6 lg:px-8">
        <div class="flex items-center justify-between h-20">
          <!-- Logo -->
          <a href="#" class="flex items-center gap-3">
            <div class="w-10 h-10 flex items-center justify-center">
              <svg viewBox="0 0 40 40" class="w-full h-full">
                <ellipse cx="20" cy="20" rx="18" ry="6" fill="none" stroke="#C4A35A" stroke-width="1.5" transform="rotate(-30 20 20)"/>
                <ellipse cx="20" cy="20" rx="14" ry="4" fill="none" stroke="#3D2914" stroke-width="1" transform="rotate(-30 20 20)"/>
                <circle cx="20" cy="20" r="2" fill="#C4A35A"/>
              </svg>
            </div>
            <span class="font-serif text-2xl font-semibold text-vanilla-deep tracking-wide">Vanillextra</span>
          </a>
          
          <!-- Navigation Desktop -->
          <nav class="hidden lg:flex items-center gap-8">
            <a href="#accueil" class="nav-link text-sm font-medium text-dark tracking-wide">Accueil</a>
            
            <!-- Dropdown La Boutique -->
            <div class="dropdown">
              <a href="#produits" class="nav-link text-sm font-medium text-dark tracking-wide flex items-center gap-1">
                La Boutique
                <svg class="w-3 h-3 opacity-50" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7"/>
                </svg>
              </a>
              <div class="dropdown-menu">
                <a href="#gousses" class="dropdown-item">Gousses de vanille</a>
                <a href="#poudre" class="dropdown-item">Graines & Poudre</a>
                <a href="#extrait" class="dropdown-item">Extrait / Essence</a>
              </div>
            </div>
            
            <a href="#professionnels" class="nav-link text-sm font-medium text-dark tracking-wide">Espace Professionnels</a>
            <a href="#origine" class="nav-link text-sm font-medium text-dark tracking-wide">L'Origine</a>
            <a href="#recettes" class="nav-link text-sm font-medium text-dark tracking-wide">Recettes & Conseils</a>
          </nav>
          
          <!-- CTA Button -->
          <div class="hidden lg:flex items-center gap-4">
            <a href="#contact" class="btn-outline px-5 py-2.5 text-sm font-medium tracking-wide">
              Demander un devis
            </a>
          </div>
          
          <!-- Mobile Menu Button -->
          <button id="mobile-menu-btn" class="lg:hidden p-2">
            <svg class="w-6 h-6 text-vanilla-deep" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M4 6h16M4 12h16M4 18h16"/>
            </svg>
          </button>
        </div>
      </div>
      
      <!-- Mobile Menu -->
      <div id="mobile-menu" class="lg:hidden hidden bg-cream-warm border-t border-vanilla-gold/20">
        <div class="px-6 py-4 space-y-3">
          <a href="#accueil" class="block py-2 text-sm font-medium text-dark">Accueil</a>
          <a href="#produits" class="block py-2 text-sm font-medium text-dark">La Boutique</a>
          <a href="#professionnels" class="block py-2 text-sm font-medium text-dark">Espace Professionnels</a>
          <a href="#origine" class="block py-2 text-sm font-medium text-dark">L'Origine</a>
          <a href="#recettes" class="block py-2 text-sm font-medium text-dark">Recettes & Conseils</a>
        </div>
      </div>
    </header>
    
    <!-- Hero Section -->
    <section id="accueil" class="scroll-section relative min-h-screen flex items-center pt-20">
      <!-- Background Image Placeholder -->
      <div class="absolute inset-0 image-placeholder">
        <div class="absolute inset-0 hero-gradient"></div>
        <!-- Decorative vanilla illustration -->
        <svg class="absolute right-0 top-1/2 -translate-y-1/2 w-1/2 h-auto opacity-10" viewBox="0 0 400 600">
          <path d="M200 50 Q220 150 200 300 Q180 450 200 550" stroke="#C4A35A" stroke-width="3" fill="none"/>
          <path d="M180 100 Q200 200 180 350 Q160 450 180 520" stroke="#C4A35A" stroke-width="2" fill="none" opacity="0.5"/>
          <path d="M220 80 Q240 180 220 330 Q200 480 220 540" stroke="#C4A35A" stroke-width="2" fill="none" opacity="0.5"/>
          <ellipse cx="200" cy="200" rx="40" ry="15" stroke="#C4A35A" stroke-width="1" fill="none" opacity="0.3"/>
          <ellipse cx="200" cy="350" rx="35" ry="12" stroke="#C4A35A" stroke-width="1" fill="none" opacity="0.3"/>
        </svg>
      </div>
      
      <!-- Image Suggestion Label -->
      <div class="absolute top-24 right-6 bg-vanilla-gold/90 text-vanilla-deep px-4 py-2 text-xs font-medium z-10">
        📷 Suggestion : Plantation de vanille à Madagascar ou macro gousses brillantes
      </div>
      
      <div class="relative z-10 max-w-7xl mx-auto px-6 lg:px-8 py-20">
        <div class="max-w-2xl">
          <div class="flex items-center gap-3 mb-6">
            <div class="section-divider"></div>
            <span class="text-vanilla-gold text-sm font-medium tracking-widest uppercase">Madagascar — Région SAVA</span>
          </div>
          
          <h1 id="hero-title" class="font-serif text-5xl md:text-7xl font-semibold text-cream-warm leading-tight mb-6">
            Vanillextra
          </h1>
          
          <p id="hero-subtitle" class="font-serif text-2xl md:text-3xl text-vanilla-gold italic mb-8">
            L'excellence de la vanille à la source
          </p>
          
          <p class="text-cream-warm/80 text-lg leading-relaxed mb-10 max-w-xl">
            Fournisseur premium de vanille Bourbon de Madagascar. Gousses, graines, poudre et extraits pour les professionnels exigeants.
          </p>
          
          <div class="flex flex-wrap gap-4">
            <a href="#produits" class="inline-flex items-center gap-2 bg-vanilla-gold text-vanilla-deep px-8 py-4 font-medium tracking-wide hover:bg-cream-warm transition-all duration-300">
              Découvrir nos produits
              <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 8l4 4m0 0l-4 4m4-4H3"/>
              </svg>
            </a>
            <a href="#professionnels" class="inline-flex items-center gap-2 border border-cream-warm/30 text-cream-warm px-8 py-4 font-medium tracking-wide hover:bg-cream-warm/10 transition-all duration-300">
              Espace professionnels
            </a>
          </div>
        </div>
      </div>
      
      <!-- Scroll Indicator -->
      <div class="absolute bottom-8 left-1/2 -translate-x-1/2 flex flex-col items-center gap-2 text-cream-warm/50">
        <span class="text-xs tracking-widest uppercase">Défiler</span>
        <svg class="w-5 h-5 animate-bounce" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M19 14l-7 7m0 0l-7-7m7 7V3"/>
        </svg>
      </div>
    </section>
    
    <!-- Products Section -->
    <section id="produits" class="scroll-section py-24 bg-cream-warm">
      <div class="max-w-7xl mx-auto px-6 lg:px-8">
        <div class="text-center mb-16">
          <span class="text-vanilla-gold text-sm font-medium tracking-widest uppercase mb-4 block">Notre Collection</span>
          <h2 id="products-title" class="font-serif text-4xl md:text-5xl font-semibold text-vanilla-deep mb-6">
            Nos Produits d'Exception
          </h2>
          <div class="section-divider mx-auto mb-6"></div>
          <p class="text-dark/70 max-w-2xl mx-auto">
            Sélection rigoureuse de vanille Bourbon, récoltée et préparée selon les traditions malgaches pour préserver tous ses arômes.
          </p>
        </div>
        
        <div class="grid md:grid-cols-3 gap-8">
          
          <!-- Product 1: Gousses -->
          <article id="gousses" class="scroll-section card-hover bg-white">
            <div class="image-placeholder aspect-[4/3] relative">
              <div class="absolute inset-0 flex items-center justify-center">
                <svg class="w-24 h-24 text-vanilla-gold/30" viewBox="0 0 100 100">
                  <path d="M30 20 Q35 50 30 80" stroke="currentColor" stroke-width="4" fill="none"/>
                  <path d="M50 15 Q55 50 50 85" stroke="currentColor" stroke-width="5" fill="none"/>
                  <path d="M70 20 Q75 50 70 80" stroke="currentColor" stroke-width="4" fill="none"/>
                </svg>
              </div>
              <div class="absolute top-4 left-4 bg-vanilla-gold/90 text-vanilla-deep px-3 py-1.5 text-xs font-medium">
                📷 Gousses brillantes sur fond sombre
              </div>
              <div class="absolute bottom-4 right-4 bg-vanilla-deep/90 text-cream-warm px-3 py-1 text-xs">
                Sous-vide
              </div>
            </div>
            <div class="p-6">
              <span class="text-vanilla-gold text-xs font-medium tracking-widest uppercase">Produit phare</span>
              <h3 class="font-serif text-2xl font-semibold text-vanilla-deep mt-2 mb-3">Gousses de Vanille</h3>
              <p class="text-dark/70 text-sm leading-relaxed mb-4">
                Gousses entières, souples et brillantes. Conditionnées sous-vide pour une conservation optimale des arômes.
              </p>
              
              <!-- Fiche technique -->
              <div class="border-t border-vanilla-gold/20 pt-4 mb-6">
                <table class="w-full text-xs">
                  <tbody>
                    <tr class="border-b border-vanilla-gold/10">
                      <td class="py-2 text-dark/50">Origine</td>
                      <td class="py-2 text-right font-medium">Madagascar — SAVA</td>
                    </tr>
                    <tr class="border-b border-vanilla-gold/10">
                      <td class="py-2 text-dark/50">Variété</td>
                      <td class="py-2 text-right font-medium">Planifolia Bourbon</td>
                    </tr>
                    <tr class="border-b border-vanilla-gold/10">
                      <td class="py-2 text-dark/50">Conditionnement</td>
                      <td class="py-2 text-right font-medium">Sous-vide</td>
                    </tr>
                    <tr>
                      <td class="py-2 text-dark/50">Formats</td>
                      <td class="py-2 text-right font-medium">Sur demande</td>
                    </tr>
                  </tbody>
                </table>
              </div>
              
              <div class="flex gap-3">
                <button class="flex-1 btn-primary px-4 py-3 text-sm font-medium">
                  Ajouter au panier
                </button>
                <button class="btn-outline px-4 py-3 text-sm font-medium">
                  Devis B2B
                </button>
              </div>
            </div>
          </article>
          
          <!-- Product 2: Poudre -->
          <article id="poudre" class="scroll-section card-hover bg-white">
            <div class="image-placeholder aspect-[4/3] relative">
              <div class="absolute inset-0 flex items-center justify-center">
                <svg class="w-24 h-24 text-vanilla-gold/30" viewBox="0 0 100 100">
                  <circle cx="50" cy="50" r="30" stroke="currentColor" stroke-width="3" fill="none"/>
                  <circle cx="50" cy="50" r="20" stroke="currentColor" stroke-width="2" fill="none" opacity="0.5"/>
                  <path d="M35 70 L30 90" stroke="currentColor" stroke-width="3" fill="none"/>
                </svg>
              </div>
              <div class="absolute top-4 left-4 bg-vanilla-gold/90 text-vanilla-deep px-3 py-1.5 text-xs font-medium">
                📷 Poudre dans bol céramique
              </div>
            </div>
            <div class="p-6">
              <span class="text-vanilla-gold text-xs font-medium tracking-widest uppercase">Polyvalent</span>
              <h3 class="font-serif text-2xl font-semibold text-vanilla-deep mt-2 mb-3">Graines & Poudre</h3>
              <p class="text-dark/70 text-sm leading-relaxed mb-4">
                Graines pures et poudre de vanille naturelle. Idéal pour l'incorporation directe dans vos préparations.
              </p>
              
              <!-- Fiche technique -->
              <div class="border-t border-vanilla-gold/20 pt-4 mb-6">
                <table class="w-full text-xs">
                  <tbody>
                    <tr class="border-b border-vanilla-gold/10">
                      <td class="py-2 text-dark/50">Origine</td>
                      <td class="py-2 text-right font-medium">Madagascar — SAVA</td>
                    </tr>
                    <tr class="border-b border-vanilla-gold/10">
                      <td class="py-2 text-dark/50">Variété</td>
                      <td class="py-2 text-right font-medium">Planifolia Bourbon</td>
                    </tr>
                    <tr class="border-b border-vanilla-gold/10">
                      <td class="py-2 text-dark/50">Conditionnement</td>
                      <td class="py-2 text-right font-medium">Pot hermétique</td>
                    </tr>
                    <tr>
                      <td class="py-2 text-dark/50">Formats</td>
                      <td class="py-2 text-right font-medium">Sur demande</td>
                    </tr>
                  </tbody>
                </table>
              </div>
              
              <div class="flex gap-3">
                <button class="flex-1 btn-primary px-4 py-3 text-sm font-medium">
                  Ajouter au panier
                </button>
                <button class="btn-outline px-4 py-3 text-sm font-medium">
                  Devis B2B
                </button>
              </div>
            </div>
          </article>
          
          <!-- Product 3: Extrait -->
          <article id="extrait" class="scroll-section card-hover bg-white">
            <div class="image-placeholder aspect-[4/3] relative">
              <div class="absolute inset-0 flex items-center justify-center">
                <svg class="w-24 h-24 text-vanilla-gold/30" viewBox="0 0 100 100">
                  <rect x="35" y="20" width="30" height="60" rx="3" stroke="currentColor" stroke-width="3" fill="none"/>
                  <rect x="40" y="10" width="20" height="15" rx="2" stroke="currentColor" stroke-width="2" fill="none"/>
                  <line x1="40" y1="40" x2="60" y2="40" stroke="currentColor" stroke-width="1" opacity="0.5"/>
                  <line x1="40" y1="50" x2="60" y2="50" stroke="currentColor" stroke-width="1" opacity="0.5"/>
                </svg>
              </div>
              <div class="absolute top-4 left-4 bg-vanilla-gold/90 text-vanilla-deep px-3 py-1.5 text-xs font-medium">
                📷 Flacon sombre style épicerie fine
              </div>
              <div class="absolute bottom-4 right-4 bg-black-matte text-vanilla-gold px-3 py-1 text-xs">
                Sur commande
              </div>
            </div>
            <div class="p-6">
              <span class="text-vanilla-gold text-xs font-medium tracking-widest uppercase">Sur mesure</span>
              <h3 class="font-serif text-2xl font-semibold text-vanilla-deep mt-2 mb-3">Extrait / Essence</h3>
              <p class="text-dark/70 text-sm leading-relaxed mb-4">
                Extrait et essence de vanille préparés sur commande. Concentration et volume selon vos besoins spécifiques.
              </p>
              
              <!-- Fiche technique -->
              <div class="border-t border-vanilla-gold/20 pt-4 mb-6">
                <table class="w-full text-xs">
                  <tbody>
                    <tr class="border-b border-vanilla-gold/10">
                      <td class="py-2 text-dark/50">Origine</td>
                      <td class="py-2 text-right font-medium">Madagascar — SAVA</td>
                    </tr>
                    <tr class="border-b border-vanilla-gold/10">
                      <td class="py-2 text-dark/50">Variété</td>
                      <td class="py-2 text-right font-medium">Planifolia Bourbon</td>
                    </tr>
                    <tr class="border-b border-vanilla-gold/10">
                      <td class="py-2 text-dark/50">Conditionnement</td>
                      <td class="py-2 text-right font-medium">Flacon verre</td>
                    </tr>
                    <tr>
                      <td class="py-2 text-dark/50">Formats</td>
                      <td class="py-2 text-right font-medium">Sur mesure</td>
                    </tr>
                  </tbody>
                </table>
              </div>
              
              <div class="flex gap-3">
                <button class="flex-1 btn-outline px-4 py-3 text-sm font-medium">
                  Demander un devis
                </button>
              </div>
            </div>
          </article>
        </div>
      </div>
    </section>
    
    <!-- Espace Professionnels Section -->
    <section id="professionnels" class="scroll-section py-24 bg-vanilla-deep relative overflow-hidden">
      <!-- Decorative background -->
      <div class="absolute inset-0 opacity-5">
        <svg class="w-full h-full" viewBox="0 0 100 100" preserveAspectRatio="none">
          <pattern id="grid" width="10" height="10" patternUnits="userSpaceOnUse">
            <path d="M 10 0 L 0 0 0 10" fill="none" stroke="#C4A35A" stroke-width="0.5"/>
          </pattern>
          <rect width="100" height="100" fill="url(#grid)"/>
        </svg>
      </div>
      
      <div class="relative z-10 max-w-7xl mx-auto px-6 lg:px-8">
        <div class="grid lg:grid-cols-2 gap-16 items-center">
          
          <!-- Content -->
          <div>
            <span class="text-vanilla-gold text-sm font-medium tracking-widest uppercase mb-4 block">Partenariat B2B</span>
            <h2 id="pro-title" class="font-serif text-4xl md:text-5xl font-semibold text-cream-warm mb-6">
              Espace Professionnels
            </h2>
            <div class="section-divider mb-8"></div>
            
            <p class="text-cream-warm/80 text-lg leading-relaxed mb-8">
              Vanillextra accompagne les professionnels de la gastronomie avec des solutions adaptées à leurs besoins : qualité constante, volumes sur mesure et service dédié.
            </p>
            
            <div class="grid sm:grid-cols-2 gap-6 mb-10">
              <div class="flex items-start gap-4">
                <div class="w-12 h-12 flex items-center justify-center border border-vanilla-gold/30 flex-shrink-0">
                  <svg class="w-6 h-6 text-vanilla-gold" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z"/>
                  </svg>
                </div>
                <div>
                  <h4 class="text-cream-warm font-medium mb-1">Qualité constante</h4>
                  <p class="text-cream-warm/60 text-sm">Lots homogènes, traçabilité complète</p>
                </div>
              </div>
              
              <div class="flex items-start gap-4">
                <div class="w-12 h-12 flex items-center justify-center border border-vanilla-gold/30 flex-shrink-0">
                  <svg class="w-6 h-6 text-vanilla-gold" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M9 5H7a2 2 0 00-2 2v12a2 2 0 002 2h10a2 2 0 002-2V7a2 2 0 00-2-2h-2M9 5a2 2 0 002 2h2a2 2 0 002-2M9 5a2 2 0 012-2h2a2 2 0 012 2"/>
                  </svg>
                </div>
                <div>
                  <h4 class="text-cream-warm font-medium mb-1">Traçabilité</h4>
                  <p class="text-cream-warm/60 text-sm">Circuit court, origine certifiée</p>
                </div>
              </div>
              
              <div class="flex items-start gap-4">
                <div class="w-12 h-12 flex items-center justify-center border border-vanilla-gold/30 flex-shrink-0">
                  <svg class="w-6 h-6 text-vanilla-gold" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M12 6V4m0 2a2 2 0 100 4m0-4a2 2 0 110 4m-6 8a2 2 0 100-4m0 4a2 2 0 110-4m0 4v2m0-6V4m6 6v10m6-2a2 2 0 100-4m0 4a2 2 0 110-4m0 4v2m0-6V4"/>
                  </svg>
                </div>
                <div>
                  <h4 class="text-cream-warm font-medium mb-1">Sur mesure</h4>
                  <p class="text-cream-warm/60 text-sm">Formats et conditionnements adaptés</p>
                </div>
              </div>
              
              <div class="flex items-start gap-4">
                <div class="w-12 h-12 flex items-center justify-center border border-vanilla-gold/30 flex-shrink-0">
                  <svg class="w-6 h-6 text-vanilla-gold" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M12 8c-1.657 0-3 .895-3 2s1.343 2 3 2 3 .895 3 2-1.343 2-3 2m0-8c1.11 0 2.08.402 2.599 1M12 8V7m0 1v8m0 0v1m0-1c-1.11 0-2.08-.402-2.599-1M21 12a9 9 0 11-18 0 9 9 0 0118 0z"/>
                  </svg>
                </div>
                <div>
                  <h4 class="text-cream-warm font-medium mb-1">Tarifs dégressifs</h4>
                  <p class="text-cream-warm/60 text-sm">Remises selon volumes commandés</p>
                </div>
              </div>
            </div>
            
            <a href="#contact" class="inline-flex items-center gap-3 bg-vanilla-gold text-vanilla-deep px-8 py-4 font-medium tracking-wide hover:bg-cream-warm transition-all duration-300">
              Devenir partenaire
              <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 8l4 4m0 0l-4 4m4-4H3"/>
              </svg>
            </a>
          </div>
          
          <!-- Image placeholder -->
          <div class="relative">
            <div class="image-placeholder aspect-[4/5] relative">
              <div class="absolute inset-0 flex items-center justify-center">
                <svg class="w-32 h-32 text-vanilla-gold/20" viewBox="0 0 100 100">
                  <circle cx="50" cy="30" r="15" stroke="currentColor" stroke-width="2" fill="none"/>
                  <path d="M50 45 L50 70 M35 55 L50 55 L65 55 M35 70 L35 90 M65 70 L65 90" stroke="currentColor" stroke-width="2" fill="none"/>
                </svg>
              </div>
              <div class="absolute top-4 left-4 bg-vanilla-gold/90 text-vanilla-deep px-3 py-1.5 text-xs font-medium">
                📷 Chef travaillant un dessert premium
              </div>
            </div>
            
            <!-- Floating card -->
            <div class="absolute -bottom-6 -left-6 bg-cream-warm p-6 shadow-xl max-w-xs">
              <div class="flex items-center gap-3 mb-3">
                <div class="w-10 h-10 bg-vanilla-gold/20 flex items-center justify-center">
                  <svg class="w-5 h-5 text-vanilla-gold" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M5 13l4 4L19 7"/>
                  </svg>
                </div>
                <span class="font-serif text-lg text-vanilla-deep">Chefs, Pâtissiers</span>
              </div>
              <p class="text-dark/70 text-sm">Épiciers fins, Revendeurs, Distributeurs</p>
            </div>
          </div>
        </div>
      </div>
    </section>
    
    <!-- Origine Section -->
    <section id="origine" class="scroll-section py-24 bg-cream-warm">
      <div class="max-w-7xl mx-auto px-6 lg:px-8">
        <div class="grid lg:grid-cols-2 gap-16 items-center">
          
          <!-- Image / Map -->
          <div class="order-2 lg:order-1">
            <div class="relative">
              <!-- Map placeholder -->
              <div class="image-placeholder aspect-square relative">
                <div class="absolute inset-0 flex items-center justify-center p-8">
                  <svg class="w-full h-full text-vanilla-gold/30" viewBox="0 0 200 200">
                    <!-- Simplified Madagascar shape -->
                    <path d="M100 30 Q130 50 140 80 Q150 120 140 160 Q120 190 90 180 Q60 160 70 120 Q65 80 80 50 Q90 35 100 30" 
                          stroke="currentColor" stroke-width="2" fill="none"/>
                    <!-- SAVA region marker -->
                    <circle cx="120" cy="55" r="15" stroke="#C4A35A" stroke-width="2" fill="rgba(196, 163, 90, 0.2)"/>
                    <text x="120" y="58" text-anchor="middle" fill="#C4A35A" font-size="8" font-weight="bold">SAVA</text>
                    <!-- Pin -->
                    <circle cx="120" cy="55" r="4" fill="#C4A35A"/>
                  </svg>
                </div>
                <div class="absolute top-4 left-4 bg-vanilla-gold/90 text-vanilla-deep px-3 py-1.5 text-xs font-medium">
                  📷 Carte stylisée région SAVA ou paysage agricole
                </div>
              </div>
              
              <!-- Small images -->
              <div class="grid grid-cols-2 gap-4 mt-4">
                <div class="image-placeholder aspect-video relative">
                  <div class="absolute top-2 left-2 bg-vanilla-gold/90 text-vanilla-deep px-2 py-1 text-[10px] font-medium">
                    📷 Producteurs au travail
                  </div>
                </div>
                <div class="image-placeholder aspect-video relative">
                  <div class="absolute top-2 left-2 bg-vanilla-gold/90 text-vanilla-deep px-2 py-1 text-[10px] font-medium">
                    📷 Séchage des gousses
                  </div>
                </div>
              </div>
            </div>
          </div>
          
          <!-- Content -->
          <div class="order-1 lg:order-2">
            <span class="text-vanilla-gold text-sm font-medium tracking-widest uppercase mb-4 block">Notre Engagement</span>
            <h2 id="origin-title" class="font-serif text-4xl md:text-5xl font-semibold text-vanilla-deep mb-6">
              L'Origine de l'Excellence
            </h2>
            <div class="section-divider mb-8"></div>
            
            <p class="text-dark/80 text-lg leading-relaxed mb-8">
              Notre vanille provient exclusivement de la région SAVA au nord-est de Madagascar, berceau historique de la vanille Bourbon. Un terroir unique qui confère à nos gousses leurs arômes incomparables.
            </p>
            
            <div class="space-y-6 mb-10">
              <div class="flex items-start gap-4 p-4 bg-white border-l-2 border-vanilla-gold">
                <div class="w-10 h-10 flex items-center justify-center bg-vanilla-gold/10 flex-shrink-0">
                  <svg class="w-5 h-5 text-vanilla-gold" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M13 10V3L4 14h7v7l9-11h-7z"/>
                  </svg>
                </div>
                <div>
                  <h4 class="font-medium text-vanilla-deep mb-1">Circuit court</h4>
                  <p class="text-dark/60 text-sm">De la plantation à votre atelier, sans intermédiaire superflu.</p>
                </div>
              </div>
              
              <div class="flex items-start gap-4 p-4 bg-white border-l-2 border-vanilla-gold">
                <div class="w-10 h-10 flex items-center justify-center bg-vanilla-gold/10 flex-shrink-0">
                  <svg class="w-5 h-5 text-vanilla-gold" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M4.318 6.318a4.5 4.5 0 000 6.364L12 20.364l7.682-7.682a4.5 4.5 0 00-6.364-6.364L12 7.636l-1.318-1.318a4.5 4.5 0 00-6.364 0z"/>
                  </svg>
                </div>
                <div>
                  <h4 class="font-medium text-vanilla-deep mb-1">Respect du produit</h4>
                  <p class="text-dark/60 text-sm">Affinage traditionnel, séchage naturel, manipulation soignée.</p>
                </div>
              </div>
              
              <div class="flex items-start gap-4 p-4 bg-white border-l-2 border-vanilla-gold">
                <div class="w-10 h-10 flex items-center justify-center bg-vanilla-gold/10 flex-shrink-0">
                  <svg class="w-5 h-5 text-vanilla-gold" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M20 7l-8-4-8 4m16 0l-8 4m8-4v10l-8 4m0-10L4 7m8 4v10M4 7v10l8 4"/>
                  </svg>
                </div>
                <div>
                  <h4 class="font-medium text-vanilla-deep mb-1">Conservation sous-vide</h4>
                  <p class="text-dark/60 text-sm">Préservation optimale des arômes jusqu'à utilisation.</p>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
    
    <!-- Recettes Section (Preview) -->
    <section id="recettes" class="scroll-section py-24 bg-black-matte">
      <div class="max-w-7xl mx-auto px-6 lg:px-8">
        <div class="text-center mb-16">
          <span class="text-vanilla-gold text-sm font-medium tracking-widest uppercase mb-4 block">Inspiration</span>
          <h2 class="font-serif text-4xl md:text-5xl font-semibold text-cream-warm mb-6">
            Recettes & Conseils
          </h2>
          <div class="section-divider mx-auto mb-6"></div>
          <p class="text-cream-warm/70 max-w-2xl mx-auto">
            Découvrez comment sublimer vos créations avec notre vanille d'exception.
          </p>
        </div>
        
        <div class="grid md:grid-cols-3 gap-6">
          <article class="group cursor-pointer">
            <div class="image-placeholder aspect-[4/3] relative overflow-hidden">
              <div class="absolute inset-0 bg-vanilla-gold/10 group-hover:bg-vanilla-gold/20 transition-colors duration-300"></div>
              <div class="absolute top-4 left-4 bg-vanilla-gold/90 text-vanilla-deep px-3 py-1.5 text-xs font-medium">
                📷 Crème brûlée vanillée
              </div>
            </div>
            <div class="mt-4">
              <span class="text-vanilla-gold text-xs tracking-widest uppercase">Dessert</span>
              <h3 class="font-serif text-xl text-cream-warm mt-2 group-hover:text-vanilla-gold transition-colors">Crème brûlée traditionnelle</h3>
            </div>
          </article>
          
          <article class="group cursor-pointer">
            <div class="image-placeholder aspect-[4/3] relative overflow-hidden">
              <div class="absolute inset-0 bg-vanilla-gold/10 group-hover:bg-vanilla-gold/20 transition-colors duration-300"></div>
              <div class="absolute top-4 left-4 bg-vanilla-gold/90 text-vanilla-deep px-3 py-1.5 text-xs font-medium">
                📷 Macarons à la vanille
              </div>
            </div>
            <div class="mt-4">
              <span class="text-vanilla-gold text-xs tracking-widest uppercase">Pâtisserie</span>
              <h3 class="font-serif text-xl text-cream-warm mt-2 group-hover:text-vanilla-gold transition-colors">Macarons vanille intense</h3>
            </div>
          </article>
          
          <article class="group cursor-pointer">
            <div class="image-placeholder aspect-[4/3] relative overflow-hidden">
              <div class="absolute inset-0 bg-vanilla-gold/10 group-hover:bg-vanilla-gold/20 transition-colors duration-300"></div>
              <div class="absolute top-4 left-4 bg-vanilla-gold/90 text-vanilla-deep px-3 py-1.5 text-xs font-medium">
                📷 Gousses fendues
              </div>
            </div>
            <div class="mt-4">
              <span class="text-vanilla-gold text-xs tracking-widest uppercase">Conseil</span>
              <h3 class="font-serif text-xl text-cream-warm mt-2 group-hover:text-vanilla-gold transition-colors">Bien utiliser ses gousses</h3>
            </div>
          </article>
        </div>
        
        <div class="text-center mt-12">
          <a href="#" class="inline-flex items-center gap-2 text-vanilla-gold font-medium hover:text-cream-warm transition-colors">
            Voir toutes les recettes
            <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 8l4 4m0 0l-4 4m4-4H3"/>
            </svg>
          </a>
        </div>
      </div>
    </section>
    
    <!-- Contact / CTA Section -->
    <section id="contact" class="scroll-section py-24 bg-cream-warm">
      <div class="max-w-4xl mx-auto px-6 lg:px-8 text-center">
        <span class="text-vanilla-gold text-sm font-medium tracking-widest uppercase mb-4 block">Contactez-nous</span>
        <h2 class="font-serif text-4xl md:text-5xl font-semibold text-vanilla-deep mb-6">
          Parlons de votre projet
        </h2>
        <div class="section-divider mx-auto mb-8"></div>
        <p class="text-dark/70 text-lg mb-10 max-w-2xl mx-auto">
          Une question, une demande de devis ou un projet particulier ? Notre équipe est à votre écoute pour vous accompagner.
        </p>
        
        <div class="flex flex-wrap justify-center gap-4 mb-16">
          <a href="mailto:contact@vanillextra.com" class="inline-flex items-center gap-3 btn-primary px-8 py-4 font-medium tracking-wide">
            <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"/>
            </svg>
            contact@vanillextra.com
          </a>
          <a href="tel:+261000000000" class="inline-flex items-center gap-3 btn-outline px-8 py-4 font-medium tracking-wide">
            <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M3 5a2 2 0 012-2h3.28a1 1 0 01.948.684l1.498 4.493a1 1 0 01-.502 1.21l-2.257 1.13a11.042 11.042 0 005.516 5.516l1.13-2.257a1 1 0 011.21-.502l4.493 1.498a1 1 0 01.684.949V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z"/>
            </svg>
            +261 00 00 000 00
          </a>
        </div>
        
        <!-- Trust badges -->
        <div class="flex flex-wrap justify-center items-center gap-8 pt-8 border-t border-vanilla-gold/20">
          <div class="flex items-center gap-2 text-dark/50 text-sm">
            <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M9 12l2 2 4-4m5.618-4.016A11.955 11.955 0 0112 2.944a11.955 11.955 0 01-8.618 3.04A12.02 12.02 0 003 9c0 5.591 3.824 10.29 9 11.622 5.176-1.332 9-6.03 9-11.622 0-1.042-.133-2.052-.382-3.016z"/>
            </svg>
            Paiement sécurisé
          </div>
          <div class="flex items-center gap-2 text-dark/50 text-sm">
            <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M20 7l-8-4-8 4m16 0l-8 4m8-4v10l-8 4m0-10L4 7m8 4v10M4 7v10l8 4"/>
            </svg>
            Livraison mondiale
          </div>
          <div class="flex items-center gap-2 text-dark/50 text-sm">
            <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-widt