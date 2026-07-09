<!DOCTYPE html>
<html lang="en" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>NEXORA GAMES | Enter Worlds Beyond Reality</title>
    <meta name="description" content="NEXORA GAMES - A premier gaming studio creating high-quality animated action, adventure, racing, and fantasy games.">
    
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    
    <!-- Google Fonts -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;500;700;900&family=Rajdhani:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    
    <!-- FontAwesome for Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">

    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        dark: '#05050A',
                        darker: '#020205',
                        neonBlue: '#00F3FF',
                        neonPurple: '#BC13FE',
                        surface: 'rgba(255, 255, 255, 0.03)',
                        surfaceHover: 'rgba(255, 255, 255, 0.08)'
                    },
                    fontFamily: {
                        heading: ['Orbitron', 'sans-serif'],
                        body: ['Rajdhani', 'sans-serif'],
                    },
                    backgroundImage: {
                        'gradient-radial': 'radial-gradient(var(--tw-gradient-stops))',
                        'hero-pattern': "url('https://images.unsplash.com/photo-1605806616949-1e87b487cb2a?q=80&w=2070&auto=format&fit=crop')",
                    }
                }
            }
        }
    </script>

    <style>
        /* Custom Futuristic Styles */
        :root {
            --neon-blue: #00F3FF;
            --neon-purple: #BC13FE;
        }

        body {
            background-color: theme('colors.darker');
            color: #E2E8F0;
            overflow-x: hidden;
        }

        /* Scrollbar */
        ::-webkit-scrollbar { width: 8px; }
        ::-webkit-scrollbar-track { background: #020205; }
        ::-webkit-scrollbar-thumb { background: #333; border-radius: 4px; }
        ::-webkit-scrollbar-thumb:hover { background: var(--neon-blue); }

        /* Typography Glows */
        .glow-text-blue { text-shadow: 0 0 10px rgba(0, 243, 255, 0.7), 0 0 20px rgba(0, 243, 255, 0.5); }
        .glow-text-purple { text-shadow: 0 0 10px rgba(188, 19, 254, 0.7), 0 0 20px rgba(188, 19, 254, 0.5); }

        /* Glassmorphism */
        .glass-nav {
            background: rgba(5, 5, 10, 0.7);
            backdrop-filter: blur(12px);
            -webkit-backdrop-filter: blur(12px);
            border-bottom: 1px solid rgba(255, 255, 255, 0.05);
        }
        
        .glass-card {
            background: rgba(255, 255, 255, 0.03);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.05);
            transition: all 0.3s ease;
        }

        /* Neon Buttons */
        .btn-neon {
            position: relative;
            display: inline-flex;
            justify-content: center;
            align-items: center;
            padding: 0.75rem 2rem;
            font-family: 'Orbitron', sans-serif;
            font-weight: 600;
            letter-spacing: 2px;
            color: var(--neon-blue);
            background: transparent;
            border: 1px solid var(--neon-blue);
            text-transform: uppercase;
            overflow: hidden;
            transition: 0.3s ease-in-out;
            z-index: 1;
            clip-path: polygon(10px 0, 100% 0, 100% calc(100% - 10px), calc(100% - 10px) 100%, 0 100%, 0 10px);
        }

        .btn-neon::before {
            content: '';
            position: absolute;
            top: 0; left: 0; right: 0; bottom: 0;
            background: var(--neon-blue);
            z-index: -1;
            transform: scaleX(0);
            transform-origin: left;
            transition: transform 0.3s ease-in-out;
        }

        .btn-neon:hover {
            color: #000;
            box-shadow: 0 0 20px rgba(0, 243, 255, 0.6);
        }

        .btn-neon:hover::before { transform: scaleX(1); }

        .btn-neon-purple {
            color: var(--neon-purple);
            border-color: var(--neon-purple);
        }
        .btn-neon-purple::before { background: var(--neon-purple); }
        .btn-neon-purple:hover { box-shadow: 0 0 20px rgba(188, 19, 254, 0.6); color: #fff;}

        /* Card Hover Effects */
        .game-card-wrapper { position: relative; }
        .game-card-wrapper::after {
            content: '';
            position: absolute;
            top: -2px; left: -2px; right: -2px; bottom: -2px;
            background: linear-gradient(45deg, var(--neon-blue), transparent, var(--neon-purple));
            z-index: -1;
            opacity: 0;
            transition: opacity 0.3s ease;
            border-radius: 0.5rem;
        }
        .game-card-wrapper:hover::after { opacity: 1; }
        .game-card-wrapper:hover .glass-card { transform: translateY(-5px); background: rgba(255,255,255,0.05); }

        /* Character Card Reveal */
        .char-details {
            transform: translateY(100%);
            transition: transform 0.4s cubic-bezier(0.4, 0, 0.2, 1);
        }
        .char-card:hover .char-details { transform: translateY(0); }
        .char-card:hover .char-img { transform: scale(1.1); }
        .char-img { transition: transform 0.6s ease; }

        /* Scroll Reveal Animation */
        .reveal { opacity: 0; transform: translateY(30px); transition: all 0.8s ease-out; }
        .reveal.active { opacity: 1; transform: translateY(0); }

        /* Loader */
        #loader {
            position: fixed; inset: 0; background: theme('colors.darker'); z-index: 9999;
            display: flex; justify-content: center; align-items: center; transition: opacity 0.5s ease;
        }
        .spinner {
            width: 60px; height: 60px;
            border: 3px solid rgba(0, 243, 255, 0.1);
            border-top-color: var(--neon-blue);
            border-radius: 50%;
            animation: spin 1s linear infinite;
            box-shadow: 0 0 20px rgba(0, 243, 255, 0.5);
        }
        @keyframes spin { to { transform: rotate(360deg); } }

        /* Canvas Background */
        #hero-canvas { position: absolute; top: 0; left: 0; width: 100%; height: 100%; z-index: 0; pointer-events: none; }
        .hero-content { position: relative; z-index: 10; }

        /* Cinematic Gradients */
        .cinematic-overlay {
            background: linear-gradient(to bottom, rgba(2,2,5,0.3) 0%, rgba(2,2,5,0.9) 100%);
        }
        .vignette {
            box-shadow: inset 0 0 150px rgba(0,0,0,0.9);
        }
    </style>
</head>
<body class="font-body antialiased selection:bg-neonBlue selection:text-black">

    <!-- Loading Screen -->
    <div id="loader">
        <div class="flex flex-col items-center gap-4">
            <div class="spinner"></div>
            <div class="font-heading text-neonBlue tracking-[0.3em] uppercase text-sm glow-text-blue">Initializing Core</div>
        </div>
    </div>

    <!-- Sticky Navigation -->
    <nav class="fixed w-full top-0 z-50 glass-nav transition-all duration-300" id="navbar">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex items-center justify-between h-20">
                <!-- Logo -->
                <div class="flex-shrink-0">
                    <a href="#" class="font-heading text-2xl font-black tracking-widest text-white flex items-center gap-2 group">
                        <i class="fa-solid fa-gamepad text-neonBlue group-hover:animate-pulse"></i>
                        <span>NEXORA<span class="text-neonBlue">.</span></span>
                    </a>
                </div>
                
                <!-- Desktop Menu -->
                <div class="hidden md:block">
                    <div class="ml-10 flex items-baseline space-x-8">
                        <a href="#home" class="hover:text-neonBlue px-3 py-2 rounded-md text-sm font-medium uppercase tracking-wider transition-colors duration-300">Home</a>
                        <a href="#games" class="hover:text-neonBlue px-3 py-2 rounded-md text-sm font-medium uppercase tracking-wider transition-colors duration-300">Games</a>
                        <a href="#trailers" class="hover:text-neonBlue px-3 py-2 rounded-md text-sm font-medium uppercase tracking-wider transition-colors duration-300">Trailers</a>
                        <a href="#characters" class="hover:text-neonBlue px-3 py-2 rounded-md text-sm font-medium uppercase tracking-wider transition-colors duration-300">Characters</a>
                        <a href="#news" class="hover:text-neonBlue px-3 py-2 rounded-md text-sm font-medium uppercase tracking-wider transition-colors duration-300">News</a>
                        <a href="#community" class="hover:text-neonBlue px-3 py-2 rounded-md text-sm font-medium uppercase tracking-wider transition-colors duration-300">Community</a>
                    </div>
                </div>
                
                <!-- Play Now Button -->
                <div class="hidden md:block">
                    <a href="#games" class="btn-neon text-sm">Play Now</a>
                </div>

                <!-- Mobile menu button -->
                <div class="-mr-2 flex md:hidden">
                    <button type="button" id="mobile-menu-btn" class="inline-flex items-center justify-center p-2 rounded-md text-gray-400 hover:text-white hover:bg-surface focus:outline-none">
                        <i class="fa-solid fa-bars text-2xl"></i>
                    </button>
                </div>
            </div>
        </div>

        <!-- Mobile Menu -->
        <div class="md:hidden hidden bg-darker/95 backdrop-blur-xl border-b border-white/5 absolute w-full" id="mobile-menu">
            <div class="px-2 pt-2 pb-6 space-y-1 sm:px-3">
                <a href="#home" class="block px-3 py-4 rounded-md text-base font-medium hover:bg-surface hover:text-neonBlue border-b border-white/5 uppercase">Home</a>
                <a href="#games" class="block px-3 py-4 rounded-md text-base font-medium hover:bg-surface hover:text-neonBlue border-b border-white/5 uppercase">Games</a>
                <a href="#trailers" class="block px-3 py-4 rounded-md text-base font-medium hover:bg-surface hover:text-neonBlue border-b border-white/5 uppercase">Trailers</a>
                <a href="#characters" class="block px-3 py-4 rounded-md text-base font-medium hover:bg-surface hover:text-neonBlue border-b border-white/5 uppercase">Characters</a>
                <a href="#news" class="block px-3 py-4 rounded-md text-base font-medium hover:bg-surface hover:text-neonBlue border-b border-white/5 uppercase">News</a>
                <a href="#support" class="block px-3 py-4 rounded-md text-base font-medium hover:bg-surface hover:text-neonBlue uppercase">Support</a>
                <div class="pt-4 px-3">
                    <a href="#games" class="btn-neon w-full text-center">Play Now</a>
                </div>
            </div>
        </div>
    </nav>

    <!-- Hero Section -->
    <section id="home" class="relative h-screen flex items-center justify-center overflow-hidden bg-dark">
        <!-- Parallax Background Image -->
        <div class="absolute inset-0 bg-hero-pattern bg-cover bg-center bg-no-repeat opacity-40 scale-105" id="hero-bg" style="transform: translateZ(0);"></div>
        
        <!-- Overlays -->
        <div class="absolute inset-0 cinematic-overlay vignette"></div>
        
        <!-- Canvas for Particles -->
        <canvas id="hero-canvas"></canvas>

        <!-- Content -->
        <div class="relative z-10 text-center px-4 max-w-5xl mx-auto hero-content">
            <h2 class="text-neonBlue font-heading tracking-[0.5em] uppercase text-sm md:text-base mb-4 animate-pulse">Welcome to the Next Generation</h2>
            <h1 class="font-heading text-5xl md:text-7xl lg:text-8xl font-black text-white mb-6 leading-tight drop-shadow-2xl">
                Enter Worlds <br />
                <span class="text-transparent bg-clip-text bg-gradient-to-r from-neonBlue to-neonPurple glow-text-blue">Beyond Reality</span>
            </h1>
            <p class="mt-4 text-lg md:text-xl text-gray-300 max-w-2xl mx-auto mb-10 font-light leading-relaxed">
                Experience cinematic stories, intense battles, and unforgettable adventures created for the most demanding gamers across the multiverse.
            </p>
            <div class="flex flex-col sm:flex-row gap-6 justify-center items-center">
                <a href="#games" class="btn-neon text-lg w-full sm:w-auto">Explore Games</a>
                <a href="#trailers" class="flex items-center gap-3 text-white hover:text-neonPurple transition-colors duration-300 font-heading uppercase tracking-widest text-sm group">
                    <div class="w-12 h-12 rounded-full border border-white/30 flex items-center justify-center group-hover:border-neonPurple group-hover:bg-neonPurple/20 transition-all">
                        <i class="fa-solid fa-play ml-1"></i>
                    </div>
                    Watch Trailer
                </a>
            </div>
        </div>

        <!-- Scroll Indicator -->
        <div class="absolute bottom-10 left-1/2 transform -translate-x-1/2 flex flex-col items-center gap-2 opacity-50 animate-bounce cursor-pointer">
            <span class="text-xs uppercase tracking-widest font-heading">Scroll</span>
            <i class="fa-solid fa-chevron-down"></i>
        </div>
    </section>

    <!-- Featured Games Section -->
    <section id="games" class="py-24 bg-dark relative border-t border-white/5">
        <div class="absolute top-0 left-1/2 transform -translate-x-1/2 w-3/4 h-1 bg-gradient-to-r from-transparent via-neonBlue to-transparent opacity-20"></div>
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="text-center mb-16 reveal">
                <h2 class="font-heading text-4xl md:text-5xl font-bold uppercase tracking-wider mb-4"><span class="text-neonBlue">Featured</span> Titles</h2>
                <div class="w-24 h-1 bg-neonPurple mx-auto rounded-full mb-4 box-shadow-glow"></div>
                <p class="text-gray-400 max-w-2xl mx-auto">Immerse yourself in our award-winning library of groundbreaking experiences.</p>
            </div>

            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8">
                <!-- Game 1 -->
                <div class="game-card-wrapper rounded-xl reveal" style="transition-delay: 100ms;">
                    <div class="glass-card rounded-xl overflow-hidden h-full flex flex-col relative group">
                        <div class="h-64 overflow-hidden relative">
                            <div class="absolute inset-0 bg-black/40 group-hover:bg-transparent transition-colors z-10"></div>
                            <img src="https://images.unsplash.com/photo-1552820728-8b83bb6b773f?q=80&w=2070&auto=format&fit=crop" alt="Shadow Protocol" class="w-full h-full object-cover transition-transform duration-700 group-hover:scale-110">
                            <span class="absolute top-4 right-4 z-20 bg-black/80 backdrop-blur text-xs font-bold px-3 py-1 rounded border border-white/10 uppercase text-neonBlue">Cyberpunk RPG</span>
                        </div>
                        <div class="p-6 flex-grow flex flex-col">
                            <h3 class="font-heading text-2xl font-bold mb-2 text-white group-hover:text-neonBlue transition-colors">Shadow Protocol</h3>
                            <div class="flex gap-3 text-gray-500 mb-4 text-lg">
                                <i class="fa-brands fa-windows hover:text-white transition-colors cursor-help" title="PC"></i>
                                <i class="fa-brands fa-playstation hover:text-white transition-colors cursor-help" title="PlayStation"></i>
                                <i class="fa-brands fa-xbox hover:text-white transition-colors cursor-help" title="Xbox"></i>
                            </div>
                            <p class="text-gray-400 text-sm mb-6 flex-grow">Infiltrate the megacorps in a dystopian future where your augmentations define your survival.</p>
                            <div class="flex gap-2">
                                <a href="#" class="bg-white/10 hover:bg-neonBlue hover:text-black text-white text-xs font-bold uppercase tracking-wider py-2 px-4 rounded transition-all flex-grow text-center">View</a>
                                <button class="bg-white/10 hover:bg-white/20 text-white py-2 px-3 rounded transition-all"><i class="fa-solid fa-video"></i></button>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Game 2 -->
                <div class="game-card-wrapper rounded-xl reveal" style="transition-delay: 200ms;">
                    <div class="glass-card rounded-xl overflow-hidden h-full flex flex-col relative group">
                        <div class="h-64 overflow-hidden relative">
                            <div class="absolute inset-0 bg-black/40 group-hover:bg-transparent transition-colors z-10"></div>
                            <img src="https://images.unsplash.com/photo-1547394765-185e1e68f34e?q=80&w=2070&auto=format&fit=crop" alt="Velocity X" class="w-full h-full object-cover transition-transform duration-700 group-hover:scale-110">
                            <span class="absolute top-4 right-4 z-20 bg-black/80 backdrop-blur text-xs font-bold px-3 py-1 rounded border border-white/10 uppercase text-neonPurple">Anti-Grav Racing</span>
                        </div>
                        <div class="p-6 flex-grow flex flex-col">
                            <h3 class="font-heading text-2xl font-bold mb-2 text-white group-hover:text-neonPurple transition-colors">Velocity X</h3>
                            <div class="flex gap-3 text-gray-500 mb-4 text-lg">
                                <i class="fa-brands fa-windows hover:text-white transition-colors cursor-help"></i>
                                <i class="fa-brands fa-playstation hover:text-white transition-colors cursor-help"></i>
                            </div>
                            <p class="text-gray-400 text-sm mb-6 flex-grow">Defy gravity at Mach 3. Master neon-lit tracks in the ultimate futuristic racing league.</p>
                            <div class="flex gap-2">
                                <a href="#" class="bg-white/10 hover:bg-neonPurple hover:text-white text-white text-xs font-bold uppercase tracking-wider py-2 px-4 rounded transition-all flex-grow text-center">View</a>
                                <button class="bg-white/10 hover:bg-white/20 text-white py-2 px-3 rounded transition-all"><i class="fa-solid fa-video"></i></button>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Game 3 -->
                <div class="game-card-wrapper rounded-xl reveal" style="transition-delay: 300ms;">
                    <div class="glass-card rounded-xl overflow-hidden h-full flex flex-col relative group">
                        <div class="h-64 overflow-hidden relative">
                            <div class="absolute inset-0 bg-black/40 group-hover:bg-transparent transition-colors z-10"></div>
                            <img src="https://images.unsplash.com/photo-1518709268805-4e9042af9f23?q=80&w=2069&auto=format&fit=crop" alt="Realm of Titan
