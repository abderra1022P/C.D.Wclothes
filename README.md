[index.html](https://github.com/user-attachments/files/29683530/index.html)
<!DOCTYPE html>
<html lang="en" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CHOSEN WEAR | Premium Minimalist Apparel</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Google Fonts: Syne for headers, Inter for body -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600&family=Syne:wght@500;700;800&display=swap" rel="stylesheet">
    <!-- FontAwesome for Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <!-- Alpine.js for interactive elements -->
    <script defer src="https://cdn.jsdelivr.net/npm/alpinejs@3.x.x/dist/cdn.min.js"></script>

    <script>
        tailwind.config = {
            theme: {
                extend: {
                    fontFamily: {
                        sans: ['Inter', 'sans-serif'],
                        display: ['Syne', 'sans-serif'],
                    },
                    colors: {
                        luxury: {
                            50: '#f9f9f9',
                            100: '#f3f3f3',
                            200: '#e5e5e5',
                            800: '#1a1a1a',
                            900: '#0d0d0d',
                        }
                    },
                    letterSpacing: {
                        widest: '.25em',
                        ultra: '.4em',
                    }
                }
            }
        }
    </script>

    <style>
        /* Custom scrollbar */
        ::-webkit-scrollbar {
            width: 6px;
            height: 6px;
        }
        ::-webkit-scrollbar-track {
            background: #0d0d0d;
        }
        ::-webkit-scrollbar-thumb {
            background: #333;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: #555;
        }
        /* Selection color */
        ::selection {
            background-color: #ffffff;
            color: #000000;
        }
    </style>
</head>
<body class="bg-black text-white font-sans overflow-x-hidden" x-data="{ cartOpen: false, mobileMenu: false, cartCount: 0 }">

    <!-- Top Announcement Bar -->
    <div class="bg-white text-black text-[10px] tracking-ultra py-2 px-4 text-center font-medium uppercase border-b border-neutral-900">
        Complimentary Express Worldwide Shipping on Orders Over $250
    </div>

    <!-- Navigation Header -->
    <header class="sticky top-0 z-50 bg-black/90 backdrop-blur-md border-b border-neutral-900 transition-all duration-300">
        <div class="max-w-7xl mx-auto px-6 h-20 flex items-center justify-between">
            
            <!-- Mobile Menu Toggle -->
            <button @click="mobileMenu = true" class="lg:hidden text-white focus:outline-none" aria-label="Open menu">
                <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M4 8h16M4 16h16"></path></svg>
            </button>

            <!-- Navigation Links (Left) -->
            <nav class="hidden lg:flex items-center space-x-8 text-xs uppercase tracking-widest font-medium">
                <a href="#collections" class="hover:text-neutral-400 transition-colors duration-300">Collections</a>
                <a href="#categories" class="hover:text-neutral-400 transition-colors duration-300">Shop</a>
                <a href="#editorial" class="hover:text-neutral-400 transition-colors duration-300">Editorial</a>
                <a href="#about" class="hover:text-neutral-400 transition-colors duration-300">Our Story</a>
            </nav>

            <!-- Brand Logo -->
            <div class="absolute left-1/2 -translate-x-1/2 text-center">
                <a href="#" class="font-display font-extrabold text-xl md:text-2xl tracking-ultra text-white hover:opacity-80 transition-opacity">
                    CHOSEN<span class="font-light text-neutral-400">WEAR</span>
                </a>
            </div>

            <!-- Icons (Right) -->
            <div class="flex items-center space-x-6">
                <!-- Search Icon (Decorative) -->
                <button class="hidden md:block text-white hover:text-neutral-400 transition-colors" aria-label="Search">
                    <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z"></path></svg>
                </button>
                <!-- Wishlist (Decorative) -->
                <button class="hidden md:block text-white hover:text-neutral-400 transition-colors" aria-label="Wishlist">
                    <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M4.318 6.318a4.5 4.5 0 000 6.364L12 20.364l7.682-7.682a4.5 4.5 0 00-6.364-6.364L12 7.636l-1.318-1.318a4.5 4.5 0 00-6.364 0z"></path></svg>
                </button>
                <!-- Cart Icon -->
                <button @click="cartOpen = true" class="relative text-white hover:text-neutral-400 transition-colors flex items-center space-x-1" aria-label="Shopping Cart">
                    <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M16 11V7a4 4 0 00-8 0v4M5 9h14l1 12H4L5 9z"></path></svg>
                    <span class="absolute -top-2 -right-2 bg-white text-black text-[9px] font-bold w-4 h-4 rounded-full flex items-center justify-center" x-text="cartCount">0</span>
                </button>
            </div>
        </div>
    </header>

    <!-- Mobile Drawer Menu -->
    <div x-show="mobileMenu" class="fixed inset-0 z-50 overflow-hidden lg:hidden" style="display: none;" role="dialog" aria-modal="true">
        <div class="absolute inset-0 bg-black/60 backdrop-blur-sm" @click="mobileMenu = false"></div>
        <div class="absolute inset-y-0 left-0 max-w-full flex">
            <div class="w-screen max-w-xs bg-luxury-900 text-white p-8 flex flex-col justify-between border-r border-neutral-800">
                <div>
                    <div class="flex items-center justify-between mb-12">
                        <span class="font-display font-extrabold text-lg tracking-widest">CHOSEN</span>
                        <button @click="mobileMenu = false" class="text-white hover:text-neutral-400">
                            <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M6 18L18 6M6 6l12 12"></path></svg>
                        </button>
                    </div>
                    <nav class="flex flex-col space-y-6 text-sm uppercase tracking-widest font-medium">
                        <a href="#collections" @click="mobileMenu = false" class="hover:text-neutral-400">Collections</a>
                        <a href="#categories" @click="mobileMenu = false" class="hover:text-neutral-400">Shop All</a>
                        <a href="#editorial" @click="mobileMenu = false" class="hover:text-neutral-400">Editorial</a>
                        <a href="#about" @click="mobileMenu = false" class="hover:text-neutral-400">Our Story</a>
                    </nav>
                </div>
                <div class="border-t border-neutral-800 pt-8 text-neutral-400 text-xs space-y-2">
                    <p>© CHOSEN WEAR Studio</p>
                    <p>Designed for the Modern Minimalist</p>
                </div>
            </div>
        </div>
    </div>

    <!-- Hero Section -->
    <section class="relative h-[90vh] bg-neutral-950 flex items-center overflow-hidden">
        <!-- Background Overlay / Image Placeholder -->
        <div class="absolute inset-0 z-0">
            <!-- Modern dark abstract background with CSS gradient mesh -->
            <div class="absolute inset-0 bg-[radial-gradient(ellipse_at_top_right,_var(--tw-gradient-stops))] from-neutral-800 via-neutral-950 to-black opacity-90"></div>
            <!-- Large subtle logo outline in background -->
            <div class="absolute inset-0 flex items-center justify-center select-none pointer-events-none opacity-5">
                <span class="font-display font-black text-[30vw] tracking-tighter">CHOSEN</span>
            </div>
        </div>

        <div class="relative z-10 max-w-7xl mx-auto px-6 w-full grid grid-cols-1 lg:grid-cols-12 gap-12 items-center">
            <!-- Left Hero Content -->
            <div class="lg:col-span-7 space-y-8">
                <span class="inline-block text-xs uppercase tracking-ultra text-neutral-400 font-semibold border-l-2 border-white pl-4">
                    New Era of Luxury
                </span>
                <h1 class="font-display text-5xl md:text-7xl lg:text-8xl font-extrabold tracking-tight leading-none text-white">
                    CURATED<br>
                    <span class="text-transparent bg-clip-text bg-gradient-to-r from-neutral-100 via-neutral-400 to-neutral-600">MINIMALISM</span>
                </h1>
                <p class="text-neutral-400 text-sm md:text-base max-w-md leading-relaxed font-light">
                    Every piece is carefully tailored to represent the absolute pinnacle of contemporary craftsmanship, engineered for those who celebrate the art of subtlety.
                </p>
                <div class="flex flex-col sm:flex-row items-stretch sm:items-center gap-4 pt-4">
                    <a href="#collections" class="group relative inline-flex items-center justify-center bg-white text-black text-xs font-semibold uppercase tracking-widest py-4 px-8 overflow-hidden transition-all duration-300 hover:bg-neutral-200">
                        Explore Collection
                    </a>
                    <a href="#categories" class="group inline-flex items-center justify-center border border-neutral-700 hover:border-white text-white text-xs font-semibold uppercase tracking-widest py-4 px-8 transition-colors duration-300">
                        Shop Categories
                    </a>
                </div>
            </div>

            <!-- Right Hero Interactive Card (3D-like perspective card) -->
            <div class="lg:col-span-5 hidden lg:block">
                <div class="relative group mx-auto w-[360px] h-[480px] bg-neutral-900 border border-neutral-800 rounded-lg overflow-hidden shadow-2xl transition-all duration-500 hover:scale-[1.02] hover:border-neutral-700">
                    <!-- Product Image Container -->
                    <div class="absolute inset-0 bg-neutral-950 flex items-center justify-center p-8">
                        <div class="absolute inset-0 bg-[radial-gradient(circle_at_center,_var(--tw-gradient-stops))] from-neutral-800/30 to-transparent"></div>
                        <!-- Stylized Minimalist Garment Illustration in lieu of live assets -->
                        <div class="relative w-48 h-64 border border-neutral-800 bg-neutral-900 flex flex-col justify-between p-6 rounded-md">
                            <span class="text-[9px] uppercase tracking-widest text-neutral-500">Selected Silhouette</span>
                            <div class="space-y-2">
                                <div class="w-12 h-[2px] bg-white"></div>
                                <div class="w-24 h-[2px] bg-neutral-700"></div>
                            </div>
                            <div class="text-right">
                                <span class="font-display text-2xl font-bold italic text-neutral-400">C.01</span>
                            </div>
                        </div>
                    </div>
                    <!-- Label Overlay -->
                    <div class="absolute bottom-0 inset-x-0 p-6 bg-gradient-to-t from-black via-black/80 to-transparent flex items-end justify-between">
                        <div>
                            <p class="text-[10px] uppercase tracking-widest text-neutral-400">Featured Capsule</p>
                            <h3 class="text-sm font-semibold tracking-wide mt-1">THE MONOCHROME COAT</h3>
                        </div>
                        <span class="text-xs font-medium">$495</span>
                    </div>
                </div>
            </div>
        </div>

        <!-- Scroll Indicator -->
        <div class="absolute bottom-8 left-1/2 -translate-x-1/2 flex flex-col items-center space-y-2 opacity-50 hover:opacity-100 transition-opacity">
            <span class="text-[9px] uppercase tracking-widest">Scroll to Explore</span>
            <div class="w-[1px] h-8 bg-neutral-500 relative overflow-hidden">
                <div class="absolute top-0 left-0 w-full h-full bg-white animate-bounce"></div>
            </div>
        </div>
    </section>

    <!-- Brand Philosophy / Stats Section -->
    <section class="py-20 border-y border-neutral-900 bg-black">
        <div class="max-w-7xl mx-auto px-6 grid grid-cols-1 md:grid-cols-3 gap-12 text-center md:text-left">
            <div class="space-y-3">
                <h4 class="font-display text-lg font-bold uppercase tracking-wider">01 / UNCOMPROMISING QUALITY</h4>
                <p class="text-neutral-400 text-xs leading-relaxed">
                    We source the finest Italian cottons, Japanese denim, and cashmere, working with ethical, family-owned ateliers.
                </p>
            </div>
            <div class="space-y-3">
                <h4 class="font-display text-lg font-bold uppercase tracking-wider">02 / CIRCULAR VISION</h4>
                <p class="text-neutral-400 text-xs leading-relaxed">
                    Designed for permanence. Our garments bypass seasonal trends, built both physically and aesthetically to last.
                </p>
            </div>
            <div class="space-y-3">
                <h4 class="font-display text-lg font-bold uppercase tracking-wider">03 / RADICAL SIMPLICITY</h4>
                <p class="text-neutral-400 text-xs leading-relaxed">
                    Stripping away the excess. A meticulous focus on form, precise tailoring, and architectural structure.
                </p>
            </div>
        </div>
    </section>

    <!-- Categories Section -->
    <section id="categories" class="py-24 bg-neutral-950">
        <div class="max-w-7xl mx-auto px-6">
            <div class="flex flex-col md:flex-row justify-between items-baseline mb-16 gap-4">
                <div>
                    <span class="text-xs uppercase tracking-ultra text-neutral-500">Curated Categories</span>
                    <h2 class="font-display text-3xl md:text-5xl font-extrabold tracking-tight mt-2">SHOP BY CLASSIFICATION</h2>
                </div>
                <a href="#collections" class="text-xs uppercase tracking-widest border-b border-white pb-1 hover:text-neutral-400 hover:border-neutral-400 transition-colors">
                    View All Collections
                </a>
            </div>

            <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
                <!-- Category Card 1 -->
                <div class="group relative h-[480px] bg-neutral-900 overflow-hidden cursor-pointer">
                    <div class="absolute inset-0 bg-[radial-gradient(circle_at_center,_var(--tw-gradient-stops))] from-neutral-800 to-black group-hover:scale-105 transition-transform duration-700"></div>
                    <!-- Minimalist Representation of Category -->
                    <div class="absolute inset-0 flex items-center justify-center">
                        <div class="w-32 h-48 border border-neutral-700/50 flex flex-col justify-center items-center p-4">
                            <span class="text-[10px] tracking-widest uppercase text-neutral-400">Structured</span>
                            <div class="w-12 h-[1px] bg-neutral-600 my-4"></div>
                            <span class="text-2xl font-bold tracking-tight">COATS</span>
                        </div>
                    </div>
                    <div class="absolute bottom-0 inset-x-0 p-8 flex justify-between items-center bg-gradient-to-t from-black to-transparent">
                        <div>
                            <h3 class="text-lg font-semibold tracking-wider">OUTERWEAR</h3>
                            <p class="text-xs text-neutral-400 mt-1">Sculpted silhouettes for any season</p>
                        </div>
                        <div class="w-10 h-10 rounded-full border border-neutral-800 flex items-center justify-center group-hover:bg-white group-hover:text-black transition-all duration-300">
                            <i class="fa-solid fa-arrow-right text-xs"></i>
                        </div>
                    </div>
                </div>

                <!-- Category Card 2 -->
                <div class="group relative h-[480px] bg-neutral-900 overflow-hidden cursor-pointer">
                    <div class="absolute inset-0 bg-[radial-gradient(circle_at_center,_var(--tw-gradient-stops))] from-neutral-700/50 to-neutral-950 group-hover:scale-105 transition-transform duration-700"></div>
                    <div class="absolute inset-0 flex items-center justify-center">
                        <div class="w-32 h-48 border border-neutral-700/50 flex flex-col justify-center items-center p-4">
                            <span class="text-[10px] tracking-widest uppercase text-neutral-400">Effortless</span>
                            <div class="w-12 h-[1px] bg-neutral-600 my-4"></div>
                            <span class="text-2xl font-bold tracking-tight">BASICS</span>
                        </div>
                    </div>
                    <div class="absolute bottom-0 inset-x-0 p-8 flex justify-between items-center bg-gradient-to-t from-black to-transparent">
                        <div>
                            <h3 class="text-lg font-semibold tracking-wider">ESSENTIALS</h3>
                            <p class="text-xs text-neutral-400 mt-1">Premium everyday fundamental layers</p>
                        </div>
                        <div class="w-10 h-10 rounded-full border border-neutral-800 flex items-center justify-center group-hover:bg-white group-hover:text-black transition-all duration-300">
                            <i class="fa-solid fa-arrow-right text-xs"></i>
                        </div>
                    </div>
                </div>

                <!-- Category Card 3 -->
                <div class="group relative h-[480px] bg-neutral-900 overflow-hidden cursor-pointer">
                    <div class="absolute inset-0 bg-[radial-gradient(circle_at_center,_var(--tw-gradient-stops))] from-neutral-800 to-black group-hover:scale-105 transition-transform duration-700"></div>
                    <div class="absolute inset-0 flex items-center justify-center">
                        <div class="w-32 h-48 border border-neutral-700/50 flex flex-col justify-center items-center p-4">
                            <span class="text-[10px] tracking-widest uppercase text-neutral-400">Refined</span>
                            <div class="w-12 h-[1px] bg-neutral-600 my-4"></div>
                            <span class="text-2xl font-bold tracking-tight">KITS</span>
                        </div>
                    </div>
                    <div class="absolute bottom-0 inset-x-0 p-8 flex justify-between items-center bg-gradient-to-t from-black to-transparent">
                        <div>
                            <h3 class="text-lg font-semibold tracking-wider">ACCESSORIES</h3>
                            <p class="text-xs text-neutral-400 mt-1">Minimalist leather goods & details</p>
                        </div>
                        <div class="w-10 h-10 rounded-full border border-neutral-800 flex items-center justify-center group-hover:bg-white group-hover:text-black transition-all duration-300">
                            <i class="fa-solid fa-arrow-right text-xs"></i>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Featured Products Section -->
    <section id="collections" class="py-24 bg-black">
        <div class="max-w-7xl mx-auto px-6">
            <div class="flex flex-col md:flex-row justify-between items-baseline mb-16">
                <div>
                    <span class="text-xs uppercase tracking-ultra text-neutral-500">Selected Pieces</span>
                    <h2 class="font-display text-3xl md:text-5xl font-extrabold tracking-tight mt-2">FEATURED APPAREL</h2>
                </div>
                <div class="flex space-x-2 mt-4 md:mt-0">
                    <span class="text-xs uppercase tracking-widest text-neutral-500">Capsule 01: Core</span>
                </div>
            </div>

            <!-- Product Grid -->
            <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-x-8 gap-y-16">
                
                <!-- Product Card 1 -->
                <div class="group" x-data="{ hovered: false }" @mouseenter="hovered = true" @mouseleave="hovered = false">
                    <div class="relative bg-neutral-900 border border-neutral-800 aspect-[3/4] flex items-center justify-center overflow-hidden mb-6">
                        <!-- Simulated Product Silhouette -->
                        <div class="w-32 h-44 bg-neutral-950 border border-neutral-800 group-hover:scale-105 transition-transform duration-500 flex flex-col justify-between p-4">
                            <div class="w-4 h-4 rounded-full bg-white"></div>
                            <span class="text-[8px] tracking-widest uppercase text-neutral-600">Pure Cotton</span>
                        </div>
                        
                        <!-- Quick Add Overlay -->
                        <div class="absolute inset-0 bg-black/60 opacity-0 group-hover:opacity-100 transition-opacity duration-300 flex items-end justify-center p-6">
                            <button @click="cartCount++" class="w-full bg-white text-black py-3 text-xs font-semibold uppercase tracking-widest hover:bg-neutral-200 transition-colors">
                                Add To Cart
                            </button>
                        </div>
                        <span class="absolute top-4 left-4 bg-white text-black text-[9px] uppercase tracking-widest font-bold py-1 px-2">Limited</span>
                    </div>
                    <div class="flex justify-between items-start">
                        <div>
                            <h3 class="text-sm font-medium tracking-wide group-hover:text-neutral-400 transition-colors">Premium Raw Hem Tee</h3>
                            <p class="text-xs text-neutral-500 mt-1">Jet Black / Heavyweight</p>
                        </div>
                        <span class="text-sm font-semibold">$95</span>
                    </div>
                </div>

                <!-- Product Card 2 -->
                <div class="group" x-data="{ hovered: false }" @mouseenter="hovered = true" @mouseleave="hovered = false">
                    <div class="relative bg-neutral-900 border border-neutral-800 aspect-[3/4] flex items-center justify-center overflow-hidden mb-6">
                        <div class="w-32 h-44 bg-neutral-950 border border-neutral-800 group-hover:scale-105 transition-transform duration-500 flex flex-col justify-between p-4">
                            <div class="w-4 h-4 rounded-full bg-neutral-400"></div>
                            <span class="text-[8px] tracking-widest uppercase text-neutral-600">Tailored Fit</span>
                        </div>
                        
                        <div class="absolute inset-0 bg-black/60 opacity-0 group-hover:opacity-100 transition-opacity duration-300 flex items-end justify-center p-6">
                            <button @click="cartCount++" class="w-full bg-white text-black py-3 text-xs font-semibold uppercase tracking-widest hover:bg-neutral-200 transition-colors">
                                Add To Cart
                            </button>
                        </div>
                    </div>
                    <div class="flex justify-between items-start">
                        <div>
                            <h3 class="text-sm font-medium tracking-wide group-hover:text-neutral-400 transition-colors">Oversized Trench Coat</h3>
                            <p class="text-xs text-neutral-500 mt-1">Asphalt Grey / Wool</p>
                        </div>
                        <span class="text-sm font-semibold">$390</span>
                    </div>
                </div>

                <!-- Product Card 3 -->
                <div class="group" x-data="{ hovered: false }" @mouseenter="hovered = true" @mouseleave="hovered = false">
                    <div class="relative bg-neutral-900 border border-neutral-800 aspect-[3/4] flex items-center justify-center overflow-hidden mb-6">
                        <div class="w-32 h-44 bg-neutral-950 border border-neutral-800 group-hover:scale-105 transition-transform duration-500 flex flex-col justify-between p-4">
                            <div class="w-4 h-4 rounded-full bg-neutral-700"></div>
                            <span class="text-[8px] tracking-widest uppercase text-neutral-600">Selvedge</span>
                        </div>
                        
                        <div class="absolute inset-0 bg-black/60 opacity-0 group-hover:opacity-100 transition-opacity duration-300 flex items-end justify-center p-6">
                            <button @click="cartCount++" class="w-full bg-white text-black py-3 text-xs font-semibold uppercase tracking-widest hover:bg-neutral-200 transition-colors">
                                Add To Cart
                            </button>
                        </div>
                    </div>
                    <div class="flex justify-between items-start">
                        <div>
                            <h3 class="text-sm font-medium tracking-wide group-hover:text-neutral-400 transition-colors">Relaxed Tailored Trouser</h3>
                            <p class="text-xs text-neutral-500 mt-1">Obsidian / Wool Crepe</p>
                        </div>
                        <span class="text-sm font-semibold">$210</span>
                    </div>
                </div>

                <!-- Product Card 4 -->
                <div class="group" x-data="{ hovered: false }" @mouseenter="hovered = true" @mouseleave="hovered = false">
                    <div class="relative bg-neutral-900 border border-neutral-800 aspect-[3/4] flex items-center justify-center overflow-hidden mb-6">
                        <div class="w-32 h-44 bg-neutral-950 border border-neutral-800 group-hover:scale-105 transition-transform duration-500 flex flex-col justify-between p-4">
                            <div class="w-4 h-4 rounded-full bg-neutral-800"></div>
                            <span class="text-[8px] tracking-widest uppercase text-neutral-600">Merino Blend</span>
                        </div>
                        
                        <div class="absolute inset-0 bg-black/60 opacity-0 group-hover:opacity-100 transition-opacity duration-300 flex items-end justify-center p-6">
                            <button @click="cartCount++" class="w-full bg-white text-black py-3 text-xs font-semibold uppercase tracking-widest hover:bg-neutral-200 transition-colors">
                                Add To Cart
                            </button>
                        </div>
                        <span class="absolute top-4 left-4 bg-white text-black text-[9px] uppercase tracking-widest font-bold py-1 px-2">Sold Out</span>
                    </div>
                    <div class="flex justify-between items-start">
                        <div>
                            <h3 class="text-sm font-medium tracking-wide group-hover:text-neutral-400 transition-colors">Structured Box Hoodie</h3>
                            <p class="text-xs text-neutral-500 mt-1">Matte Off-White / Cotton fleece</p>
                        </div>
                        <span class="text-sm font-semibold">$180</span>
                    </div>
                </div>

            </div>
        </div>
    </section>

    <!-- Editorial Feature Section -->
    <section id="editorial" class="py-24 bg-neutral-950 border-t border-neutral-900">
        <div class="max-w-7xl mx-auto px-6 grid grid-cols-1 lg:grid-cols-12 gap-12 items-center">
            <div class="lg:col-span-5 space-y-6">
                <span class="text-xs uppercase tracking-ultra text-neutral-500">The Journal</span>
                <h2 class="font-display text-4xl md:text-5xl font-extrabold tracking-tight leading-tight">THE GEOMETRY OF SILENCE</h2>
                <p class="text-neutral-400 text-sm leading-relaxed font-light">
                    An examination of form and functional aestheticism. Our Editorial 04 collection represents a dialogue between structured tailoring and organic movement, photographed on site in architectural landmarks across Copenhagen.
                </p>
                <div class="pt-4">
                    <a href="#" class="inline-flex items-center space-x-3 group text-xs uppercase tracking-widest font-semibold">
                        <span>Read the Editorial</span>
                        <span class="w-8 h-[1px] bg-white group-hover:w-12 transition-all"></span>
                    </a>
                </div>
            </div>
            <div class="lg:col-span-7">
                <div class="grid grid-cols-2 gap-4">
                    <div class="bg-neutral-900 border border-neutral-800 aspect-[4/5] flex items-center justify-center p-8">
                        <div class="text-center">
                            <span class="font-display text-6xl font-extrabold text-neutral-800 block">01</span>
                            <span class="text-[10px] tracking-widest text-neutral-500 uppercase">Structure & Form</span>
                        </div>
                    </div>
                    <div class="bg-neutral-900 border border-neutral-800 aspect-[4/5] flex items-center justify-center p-8 mt-8">
                        <div class="text-center">
                            <span class="font-display text-6xl font-extrabold text-neutral-800 block">02</span>
                            <span class="text-[10px] tracking-widest text-neutral-500 uppercase">Fluid Movement</span>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Testimonials / Philosophy Quote -->
    <section class="py-24 bg-black border-t border-neutral-900 text-center relative overflow-hidden">
        <div class="absolute inset-0 bg-[radial-gradient(circle_at_center,_var(--tw-gradient-stops))] from-neutral-900/40 via-black to-black"></div>
        <div class="relative z-10 max-w-4xl mx-auto px-6 space-y-8">
            <div class="flex justify-center text-neutral-600">
                <svg class="w-12 h-12" fill="currentColor" viewBox="0 0 24 24"><path d="M14.017 21v-7.391c0-5.704 3.731-9.57 8.983-10.609l.995 2.151c-2.432.917-3.995 3.638-3.995 5.849h4v10h-9.983zm-14.017 0v-7.391c0-5.704 3.748-9.57 9-10.609l.996 2.151c-2.433.917-3.996 3.638-3.996 5.849h3.983v10h-9.983z"/></svg>
            </div>
            <p class="font-display text-2xl md:text-4xl font-semibold leading-relaxed tracking-tight text-neutral-100">
                "Chosen Wear represents a rejection of the hyper-consumerist trend cycle. Its simplicity is highly intentional, speaking volumes through whispers rather than shouts."
            </p>
            <div class="space-y-1">
                <p class="text-xs uppercase tracking-widest font-bold">MONOCLE MAGAZINE</p>
                <p class="text-[10px] text-neutral-500 uppercase tracking-widest">Design & Lifestyle Annual</p>
            </div>
        </div>
    </section>

    <!-- About Section -->
    <section id="about" class="py-24 bg-neutral-950 border-t border-neutral-900">
        <div class="max-w-7xl mx-auto px-6">
            <div class="grid grid-cols-1 lg:grid-cols-2 gap-16 items-center">
                <div class="space-y-6">
                    <span class="text-xs uppercase tracking-ultra text-neutral-500">Our Identity</span>
                    <h2 class="font-display text-4xl md:text-5xl font-extrabold tracking-tight">CRAFTED FOR THE FEW</h2>
                    <p class="text-neutral-400 text-sm leading-relaxed font-light">
                        We exist to build curated essential wear for the global citizen. Operating with a relentless dedication to high-grade textile sourcing, structural tailoring, and neutral colorways, Chosen Wear delivers pieces that integrate effortlessly into modern life.
                    </p>
                    <p class="text-neutral-400 text-sm leading-relaxed font-light">
                        No logos, no branding clutter, no compromise. Merely structural garments engineered for everyday life.
                    </p>
                </div>
                <div class="border border-neutral-800 p-8 bg-neutral-900 flex flex-col justify-between h-[350px]">
                    <div class="space-y-4">
                        <h3 class="text-xl font-bold tracking-tight">TRANSPARENT VALUE</h3>
                        <p class="text-xs text-neutral-400 leading-relaxed">
                            Every garment comes with an integrated NFC tag disclosing our exact supply chain, from the organic cotton farms in Turkey to the finishing studio in northern Italy.
                        </p>
                    </div>
                    <div class="flex justify-between items-center text-neutral-500 text-xs">
                        <span>ESTABLISHED 2024</span>
                        <span>0% SYNTHETIC BLENDS</span>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Newsletter Subscription -->
    <section class="py-24 bg-black border-t border-neutral-900">
        <div class="max-w-3xl mx-auto px-6 text-center space-y-8">
            <div class="space-y-3">
                <span class="text-[10px] uppercase tracking-ultra text-neutral-500">EXCLUSIVITY INBOX</span>
                <h2 class="font-display text-3xl md:text-4xl font-extrabold tracking-tight">JOIN THE SYNDICATE</h2>
                <p class="text-neutral-400 text-xs max-w-md mx-auto leading-relaxed">
                    Subscribe to receive priority access to limited seasonal capsule drops, private showroom events, and editorial journals.
                </p>
            </div>
            <form class="flex flex-col sm:flex-row items-stretch gap-2 max-w-md mx-auto" @submit.prevent="alert('Thank you for subscribing to CHOSEN WEAR.')">
                <input type="email" placeholder="Your Email Address" required class="flex-grow bg-neutral-900 border border-neutral-800 text-white text-xs px-4 py-3 outline-none focus:border-white transition-colors">
                <button type="submit" class="bg-white text-black text-xs uppercase tracking-widest font-semibold px-6 py-3 hover:bg-neutral-200 transition-colors">
                    Subscribe
                </button>
            </form>
        </div>
    </section>

    <!-- Footer -->
    <footer class="bg-black text-neutral-400 text-xs py-16 border-t border-neutral-900">
        <div class="max-w-7xl mx-auto px-6 grid grid-cols-1 md:grid-cols-4 gap-12 mb-16">
            <!-- Brand Column -->
            <div class="space-y-4">
                <span class="font-display font-extrabold text-lg text-white tracking-widest">CHOSEN</span>
                <p class="text-[11px] leading-relaxed text-neutral-500">
                    Sovereign minimalist luxury designed with intent.
                </p>
                <div class="flex space-x-4 pt-2">
                    <a href="#" class="hover:text-white transition-colors" aria-label="Instagram"><i class="fa-brands fa-instagram text-base"></i></a>
                    <a href="#" class="hover:text-white transition-colors" aria-label="Pinterest"><i class="fa-brands fa-pinterest text-base"></i></a>
                    <a href="#" class="hover:text-white transition-colors" aria-label="Twitter"><i class="fa-brands fa-twitter text-base"></i></a>
                </div>
            </div>
            
            <!-- Links Column 1 -->
            <div class="space-y-3">
                <h4 class="text-white font-bold uppercase tracking-widest text-[10px]">Shop</h4>
                <ul class="space-y-2 text-[11px]">
                    <li><a href="#collections" class="hover:text-white transition-colors">All Collections</a></li>
                    <li><a href="#categories" class="hover:text-white transition-colors">New Arrivals</a></li>
                    <li><a href="#" class="hover:text-white transition-colors">Best Sellers</a></li>
                    <li><a href="#" class="hover:text-white transition-colors">Online Exclusives</a></li>
                </ul>
            </div>

            <!-- Links Column 2 -->
            <div class="space-y-3">
                <h4 class="text-white font-bold uppercase tracking-widest text-[10px]">Client Services</h4>
                <ul class="space-y-2 text-[11px]">
                    <li><a href="#" class="hover:text-white transition-colors">Contact Support</a></li>
                    <li><a href="#" class="hover:text-white transition-colors">Shipping & Returns</a></li>
                    <li><a href="#" class="hover:text-white transition-colors">Size Guide</a></li>
                    <li><a href="#" class="hover:text-white transition-colors">Garment Care</a></li>
                </ul>
            </div>

            <!-- Links Column 3 -->
            <div class="space-y-3">
                <h4 class="text-white font-bold uppercase tracking-widest text-[10px]">Corporate</h4>
                <ul class="space-y-2 text-[11px]">
                    <li><a href="#" class="hover:text-white transition-colors">Sustainability Commitments</a></li>
                    <li><a href="#" class="hover:text-white transition-colors">Careers</a></li>
                    <li><a href="#" class="hover:text-white transition-colors">Press & Media</a></li>
                </ul>
            </div>
        </div>

        <div class="max-w-7xl mx-auto px-6 pt-8 border-t border-neutral-900 flex flex-col sm:flex-row justify-between items-center gap-4 text-neutral-600 text-[10px]">
            <p>© 2024 CHOSEN WEAR. All rights reserved.</p>
            <div class="flex space-x-6">
                <a href="#" class="hover:text-neutral-400 transition-colors">Privacy Policy</a>
                <a href="#" class="hover:text-neutral-400 transition-colors">Terms of Service</a>
            </div>
        </div>
    </footer>

    <!-- Shopping Cart Drawer (Slide-over) -->
    <div x-show="cartOpen" class="fixed inset-0 z-50 overflow-hidden" style="display: none;" role="dialog" aria-modal="true">
        <div class="absolute inset-0 bg-black/60 backdrop-blur-sm transition-opacity" @click="cartOpen = false"></div>
        <div class="absolute inset-y-0 right-0 max-w-full flex">
            <div class="w-screen max-w-md bg-luxury-900 text-white p-8 flex flex-col justify-between border-l border-neutral-800">
                <div>
                    <div class="flex items-center justify-between pb-6 border-b border-neutral-800">
                        <h2 class="text-lg font-bold tracking-widest uppercase">Shopping Bag</h2>
                        <button @click="cartOpen = false" class="text-white hover:text-neutral-400">
                            <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M6 18L18 6M6 6l12 12"></path></svg>
                        </button>
                    </div>

                    <!-- Cart Items container -->
                    <div class="py-8 space-y-6">
                        <template x-if="cartCount === 0">
                            <div class="text-center py-12 text-neutral-500">
                                <p class="text-sm">Your bag is currently empty.</p>
                                <button @click="cartOpen = false" class="text-xs uppercase border-b border-white pb-1 mt-4 text-white">Continue Browsing</button>
                            </div>
                        </template>
                        <template x-if="cartCount > 0">
                            <div class="flex space-x-4 items-center">
                                <div class="w-16 h-20 bg-neutral-800 flex items-center justify-center">
                                    <span class="text-[9px] text-neutral-400">ITEM</span>
                                </div>
                                <div class="flex-grow">
                                    <h4 class="text-xs font-semibold uppercase">Premium Heavyweight Piece</h4>
                                    <p class="text-[11px] text-neutral-400 mt-1">One Size / Dark Obsidian</p>
                                    <p class="text-xs mt-2 font-medium" x-text="'$120 x ' + cartCount"></p>
                                </div>
                                <button @click="cartCount = 0" class="text-xs text-neutral-500 hover:text-white">Remove</button>
                            </div>
                        </template>
                    </div>
                </div>

                <!-- Footer Checkout of Cart -->
                <div class="border-t border-neutral-800 pt-6 space-y-4">
                    <div class="flex justify-between text-sm">
                        <span class="text-neutral-400">Subtotal</span>
                        <span class="font-bold" x-text="'$' + (cartCount * 120)">$0</span>
                    </div>
                    <p class="text-[10px] text-neutral-500">Shipping and taxes calculated at checkout.</p>
                    <button @click="alert('Proceeding to checkout sequence.')" class="w-full bg-white text-black py-4 text-xs font-semibold uppercase tracking-widest hover:bg-neutral-200 transition-colors">
                        Proceed to Checkout
                    </button>
                </div>
            </div>
        </div>
    </div>

</body>
</html>
