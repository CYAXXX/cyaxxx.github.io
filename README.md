import React, { useState, useEffect } from 'react';
import {
  Moon,
  Sun,
  Mail,
  Github,
  Menu,
  X,
  BookOpen,
  Search,
  Plus,
  ArrowRight
} from 'lucide-react';

// --- Data ---

const workData = [
  { name: "DuckDuckGo", slug: "duckduckgo", color: "#DE5833", tag: "PRIVACY", desc: "Core privacy-search localization.", link: "https://duckduckgo.com" },
  { name: "Vivaldi", slug: "vivaldi", color: "#EF3939", tag: "BROWSER", desc: "Power-user browser UI modules.", link: "https://vivaldi.com" },
  { name: "OBS Studio", slug: "obsstudio", color: "#FFFFFF", tag: "MEDIA", desc: "Broadcasting engine Kurdish pack.", link: "https://obsproject.com/" },
  { name: "Arch Linux", slug: "archlinux", color: "#1793D1", tag: "SYSTEM", desc: "Archinstall & CLI localization.", link: "https://archlinux.org" },
  { name: "Telegram", slug: "telegram", color: "#26A5E4", tag: "SOCIAL", desc: "Secure messaging language sync.", link: "https://telegram.org" },
  { name: "Mastodon", slug: "mastodon", color: "#6364FF", tag: "SOCIAL", desc: "Decentralized UI localization.", link: "https://joinmastodon.org/ku" },
  { name: "Roundcube", slug: "roundcube", color: "#37BEFF", tag: "EMAIL", desc: "Webmail interface localization.", link: "https://roundcube.net/" },
  { name: "OpenMap", slug: "openstreetmap", color: "#7EBC6F", tag: "MAPS", desc: "Map viewing application.", link: "https://www.openstreetmap.org" },
  { name: "Nuclear", slug: "applemusic", color: "#FA243C", tag: "MEDIA", desc: "Music streaming program.", link: "https://nuclearplayer.com/" },
  { name: "Harmonoid", slug: "flutter", color: "#02569B", tag: "MEDIA", desc: "Material Design music player.", link: "https://harmonoid.com/" },
  { name: "Whoogle", slug: "google", color: "#4285F4", tag: "PRIVACY", desc: "Self-hosted privacy search.", link: "https://pypi.org/project/whoogle-search/" },
  { name: "Kiwi Browser", slug: "googlechrome", color: "#4285F4", tag: "BROWSER", desc: "Android browser extension support.", link: "https://github.com/kiwibrowser/src.next" }
];

const movieData = [
  {
      name: "EL CUERPO",
      year: "2012",
      genre: "MYSTERY",
      score: "7.6",
      desc: "Piştî mirina wê, bedena jina Alex, ji morgê winda dibe.",
      link: "https://tirsik.net/film/749?tab=agahi",
      img: "https://images.unsplash.com/photo-1596706915606-25f0cb18cb3e?q=80&w=1974&auto=format&fit=crop"
  },
  {
      name: "BENEATH US",
      year: "2019",
      genre: "HORROR",
      score: "5.2",
      desc: "Xewna amerîkî, ji bo komeke xebatkarên penaber vediguhere xewnereşkê.",
      link: "https://tirsik.net/film/769",
      img: "https://images.unsplash.com/photo-1595878715977-2e8f8df18ea8?q=80&w=1974&auto=format&fit=crop"
  },
  {
      name: "DON'T BREATHE",
      year: "2016",
      genre: "THRILLER",
      score: "7.1",
      desc: "Sê xort, ji bo dizehî bikin dikevin mala zilamek kor ku leşkerek kevin e.",
      link: "https://tirsik.net/film/680",
      img: "https://images.unsplash.com/photo-1505548689957-bf530eb7b049?q=80&w=2062&auto=format&fit=crop"
  }
];

export default function App() {
  const [isDark, setIsDark] = useState(true);
  const [isMobileMenuOpen, setIsMobileMenuOpen] = useState(false);

  // Initialize theme based on preference or local storage logic
  useEffect(() => {
    // Inject fonts
    const link = document.createElement('link');
    link.href = "https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800;900&family=JetBrains+Mono:wght@400;500&display=swap";
    link.rel = "stylesheet";
    document.head.appendChild(link);
    return () => document.head.removeChild(link);
  }, []);

  const toggleTheme = () => setIsDark(!isDark);

  return (
    <div className={`min-h-screen transition-colors duration-300 ${isDark ? 'dark' : ''}`}>
      <style>{`
        :root {
            --bg-primary: #ffffff;
            --bg-surface: #f3f4f6;
            --bg-surface-highlight: #e5e7eb;
            --text-primary: #111827;
            --text-secondary: #4b5563;
            --border-color: rgba(0, 0, 0, 0.1);
            --nav-bg: rgba(255, 255, 255, 0.8);
            --primary-col: #3b82f6;
            --secondary-col: #8b5cf6;
        }

        .dark {
            --bg-primary: #050505;
            --bg-surface: #121212;
            --bg-surface-highlight: #1E1E1E;
            --text-primary: #ffffff;
            --text-secondary: #9ca3af;
            --border-color: rgba(255, 255, 255, 0.1);
            --nav-bg: rgba(5, 5, 5, 0.8);
        }

        body {
            font-family: 'Inter', sans-serif;
            background-color: var(--bg-primary);
            color: var(--text-primary);
        }

        .font-mono { font-family: 'JetBrains Mono', monospace; }

        .glass-nav {
            background: var(--nav-bg);
            backdrop-filter: blur(12px);
            -webkit-backdrop-filter: blur(12px);
            border-bottom: 1px solid var(--border-color);
        }

        .text-gradient {
            background: linear-gradient(to right, #60a5fa, #c084fc);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .mesh-bg {
             background-image:
                radial-gradient(at 0% 0%, rgba(59, 130, 246, 0.15) 0px, transparent 50%),
                radial-gradient(at 100% 100%, rgba(139, 92, 246, 0.15) 0px, transparent 50%);
        }

        /* Custom Scrollbar */
        ::-webkit-scrollbar { width: 8px; }
        ::-webkit-scrollbar-track { background: var(--bg-primary); }
        ::-webkit-scrollbar-thumb { background: #555; border-radius: 4px; }
        ::-webkit-scrollbar-thumb:hover { background: #777; }
      `}</style>

      {/* Main Wrapper to apply CSS Variables */}
      <div style={{ backgroundColor: 'var(--bg-primary)', color: 'var(--text-primary)' }} className="min-h-screen transition-colors duration-300">

        {/* Navigation */}
        <nav className="fixed top-0 w-full z-50 glass-nav transition-all duration-300">
          <div className="max-w-7xl mx-auto px-6 h-20 flex items-center justify-between">
            <a href="#" className="text-2xl font-bold tracking-tighter flex items-center gap-2 text-[var(--text-primary)]">
              <div className="w-8 h-8 bg-gradient-to-br from-blue-500 to-violet-500 rounded-lg flex items-center justify-center text-white shadow-lg">
                <span className="font-mono font-bold text-xs">CY</span>
              </div>
              <span>CYAXXX</span>
            </a>

            <div className="flex items-center gap-6">
              <div className="hidden md:flex items-center gap-8 text-sm font-medium text-[var(--text-secondary)]">
                <a href="#work" className="hover:text-[var(--text-primary)] transition-colors">Projects</a>
                <a href="#movies" className="hover:text-[var(--text-primary)] transition-colors">Subtitles</a>
                <a href="#dictionary" className="hover:text-[var(--text-primary)] transition-colors">Dictionary</a>
              </div>

              {/* Theme Toggle */}
              <button
                onClick={toggleTheme}
                className="p-2 rounded-full hover:bg-[var(--bg-surface-highlight)] transition-colors text-[var(--text-primary)] border border-transparent hover:border-[var(--border-color)]"
              >
                {isDark ? <Moon className="w-5 h-5" /> : <Sun className="w-5 h-5" />}
              </button>

              {/* Desktop Icons */}
              <div className="hidden md:flex gap-2">
                <a href="mailto:cyaxxx@vivaldi.net" className="flex items-center justify-center p-2 bg-[var(--bg-surface)] hover:bg-[var(--bg-surface-highlight)] rounded-full text-[var(--text-primary)] transition-all border border-[var(--border-color)] shadow-sm group">
                  <Mail className="w-5 h-5 group-hover:scale-110 transition-transform" />
                </a>
                <a href="https://github.com/CYAXXX" target="_blank" rel="noreferrer" className="flex items-center justify-center p-2 bg-[var(--bg-surface)] hover:bg-[var(--bg-surface-highlight)] rounded-full text-[var(--text-primary)] transition-all border border-[var(--border-color)] shadow-sm group">
                  <Github className="w-5 h-5 group-hover:scale-110 transition-transform" />
                </a>
              </div>

              {/* Mobile Menu Button */}
              <button
                className="md:hidden text-[var(--text-primary)]"
                onClick={() => setIsMobileMenuOpen(!isMobileMenuOpen)}
              >
                {isMobileMenuOpen ? <X className="w-6 h-6" /> : <Menu className="w-6 h-6" />}
              </button>
            </div>
          </div>

          {/* Mobile Menu */}
          {isMobileMenuOpen && (
            <div className="md:hidden absolute top-20 left-0 w-full bg-[var(--bg-primary)] border-b border-[var(--border-color)] p-6 flex flex-col gap-4 shadow-xl">
              <a href="#work" className="text-[var(--text-secondary)] hover:text-[var(--text-primary)]" onClick={() => setIsMobileMenuOpen(false)}>Projects</a>
              <a href="#movies" className="text-[var(--text-secondary)] hover:text-[var(--text-primary)]" onClick={() => setIsMobileMenuOpen(false)}>Subtitles</a>
              <a href="#dictionary" className="text-[var(--text-secondary)] hover:text-[var(--text-primary)]" onClick={() => setIsMobileMenuOpen(false)}>Dictionary</a>
            </div>
          )}
        </nav>

        {/* Hero Section */}
        <section className="relative pt-40 pb-32 overflow-hidden mesh-bg">
          <div className="max-w-4xl mx-auto px-6 relative z-10 text-center">

            <div className="inline-flex items-center gap-2 px-4 py-1.5 rounded-full bg-[var(--bg-surface)] border border-[var(--border-color)] text-xs font-mono text-blue-500 mb-8 shadow-sm">
              <span className="relative flex h-2 w-2">
                <span className="animate-ping absolute inline-flex h-full w-full rounded-full bg-blue-500 opacity-75"></span>
                <span className="relative inline-flex rounded-full h-2 w-2 bg-blue-500"></span>
              </span>
              Available for Localization Projects
            </div>

            <h1 className="text-5xl md:text-8xl font-extrabold tracking-tight leading-[1.1] mb-8 text-[var(--text-primary)]">
              Software that speaks <br />
              <span className="text-gradient">Kurdish.</span>
            </h1>

            <p className="text-lg md:text-xl text-[var(--text-secondary)] max-w-2xl mx-auto leading-relaxed mb-10">
              I bridge the gap between global technology and the Kurdish (Kurmanji) community through precise, open-source engineering and localization.
            </p>

            <div className="flex flex-col sm:flex-row items-center gap-4 justify-center">
              <a href="#work" className="w-full sm:w-auto px-8 py-4 bg-blue-500 hover:bg-blue-600 text-white font-bold rounded-lg transition-all transform hover:scale-105 shadow-lg shadow-blue-500/25 flex items-center justify-center gap-2">
                View Selected Works
              </a>
              <a href="#dictionary" className="w-full sm:w-auto px-8 py-4 bg-[var(--bg-surface)] hover:bg-[var(--bg-surface-highlight)] text-[var(--text-primary)] font-medium rounded-lg transition-colors border border-[var(--border-color)] flex items-center justify-center gap-2 shadow-sm">
                Open Dictionary
              </a>
            </div>
          </div>
        </section>

        {/* Trusted By / Marquee */}
        <div className="border-y border-[var(--border-color)] bg-[var(--bg-surface)] bg-opacity-50">
            <div className="max-w-7xl mx-auto px-6 py-10">
                <p className="text-center text-xs font-mono text-[var(--text-secondary)] uppercase tracking-widest mb-8">Contributing Localization To</p>
                <div className="flex flex-wrap justify-center gap-10 md:gap-16 items-center">
                    <img src="https://cdn.simpleicons.org/duckduckgo" className="h-10 w-auto hover:scale-110 transition-transform duration-300" alt="DuckDuckGo" />
                    <img src="https://cdn.simpleicons.org/vivaldi" className="h-10 w-auto hover:scale-110 transition-transform duration-300" alt="Vivaldi" />
                    <img src="https://cdn.simpleicons.org/obsstudio" className={`h-10 w-auto hover:scale-110 transition-transform duration-300 ${isDark ? 'invert' : ''}`} alt="OBS" />
                    <img src="https://cdn.simpleicons.org/archlinux" className={`h-10 w-auto hover:scale-110 transition-transform duration-300 ${isDark ? 'invert' : ''}`} alt="Arch Linux" />
                    <img src="https://cdn.simpleicons.org/telegram" className="h-10 w-auto hover:scale-110 transition-transform duration-300" alt="Telegram" />
                    <img src="https://cdn.simpleicons.org/mastodon" className="h-10 w-auto hover:scale-110 transition-transform duration-300" alt="Mastodon" />
                </div>
            </div>
        </div>

        {/* Projects Grid */}
        <section id="work" className="py-24 bg-[var(--bg-primary)]">
            <div className="max-w-7xl mx-auto px-6">
                <div className="text-center max-w-2xl mx-auto mb-16">
                    <h2 className="text-3xl md:text-5xl font-bold mb-4 text-[var(--text-primary)]">Selected Works</h2>
                    <p className="text-[var(--text-secondary)]">A collection of software that I have helped translate and localize for the Kurdish community.</p>
                </div>

                <div className="grid md:grid-cols-2 lg:grid-cols-3 gap-6">
                    {workData.map((item) => (
                        <a
                            key={item.slug}
                            href={item.link}
                            target="_blank"
                            rel="noreferrer"
                            className="p-6 rounded-xl flex flex-col h-full group relative overflow-hidden transition-all duration-300 hover:-translate-y-1 hover:shadow-2xl border border-[var(--border-color)] bg-[var(--bg-surface)] hover:border-blue-500/50"
                        >
                            <div className="flex items-start justify-between mb-4 relative z-10">
                                <div className="w-12 h-12 rounded-lg bg-[var(--bg-surface-highlight)] border border-[var(--border-color)] flex items-center justify-center group-hover:bg-[var(--bg-surface)] transition-colors">
                                     <img src={`https://cdn.simpleicons.org/${item.slug}/${item.color.replace('#','')}`} className="w-6 h-6" alt={item.name} />
                                </div>
                                <span className="text-[10px] font-mono uppercase tracking-wider text-[var(--text-secondary)] bg-[var(--bg-surface-highlight)] px-2 py-1 rounded border border-[var(--border-color)]">{item.tag}</span>
                            </div>
                            <h3 className="text-xl font-bold text-[var(--text-primary)] mb-2 group-hover:text-blue-500 transition-colors relative z-10">{item.name}</h3>
                            <p className="text-sm text-[var(--text-secondary)] leading-relaxed relative z-10">{item.desc}</p>

                            {/* Hover Glow Effect */}
                            <div
                                className="absolute -bottom-10 -right-10 w-32 h-32 opacity-0 group-hover:opacity-10 blur-[50px] transition-opacity duration-500 pointer-events-none rounded-full"
                                style={{ backgroundColor: item.color }}
                            ></div>
                        </a>
                    ))}
                </div>
            </div>
        </section>

        {/* Subtitles Section */}
        <section id="movies" className="py-24 relative border-t border-[var(--border-color)] bg-[var(--bg-surface)] bg-opacity-30">
            <div className="max-w-7xl mx-auto px-6 relative z-10">
                <div className="flex flex-col md:flex-row justify-between items-end mb-12 gap-6">
                    <div>
                        <h2 className="text-3xl md:text-5xl font-bold mb-2 text-[var(--text-primary)]">Subtitle Translations</h2>
                        <p className="text-[var(--text-secondary)]">Bringing global cinema to local screens.</p>
                    </div>
                    <div className="flex gap-2">
                        <span className="px-3 py-1 bg-red-500/10 text-red-500 border border-red-500/20 rounded text-xs font-mono font-bold">SRT</span>
                        <span className="px-3 py-1 bg-blue-500/10 text-blue-500 border border-blue-500/20 rounded text-xs font-mono font-bold">ASS</span>
                    </div>
                </div>

                <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
                    {movieData.map((movie) => (
                        <a
                            key={movie.name}
                            href={movie.link}
                            target="_blank"
                            rel="noreferrer"
                            className="group relative aspect-[3/4] rounded-xl overflow-hidden bg-[var(--bg-surface)] border border-[var(--border-color)]"
                        >
                            <img src={movie.img} className="absolute inset-0 w-full h-full object-cover transition-transform duration-700 group-hover:scale-110 opacity-60" alt={movie.name} />
                            <div className="absolute inset-0 bg-gradient-to-t from-black via-black/50 to-transparent"></div>

                            <div className="absolute inset-0 p-6 flex flex-col justify-end">
                                <div className="transform translate-y-4 group-hover:translate-y-0 transition-transform duration-300">
                                    <div className="flex items-center gap-2 mb-2">
                                         <span className="text-xs font-bold text-red-500 bg-red-500/10 px-2 py-0.5 rounded border border-red-500/20">{movie.score}</span>
                                         <span className="text-[10px] text-gray-300 font-mono uppercase shadow-sm">{movie.genre}</span>
                                    </div>
                                    <h3 className="text-2xl font-black uppercase italic mb-2 leading-none text-white">{movie.name}</h3>
                                    <p className="text-sm text-gray-300 line-clamp-2 opacity-0 group-hover:opacity-100 transition-opacity duration-300">{movie.desc}</p>
                                </div>
                            </div>
                        </a>
                    ))}
                </div>
            </div>
        </section>

        {/* Dictionary CTA Section */}
        <section id="dictionary" className="py-32 relative overflow-hidden bg-[var(--bg-primary)]">
            {/* Background Pattern */}
            <div className="absolute inset-0 opacity-[0.03] pointer-events-none" style={{ backgroundImage: 'radial-gradient(#888 1px, transparent 1px)', backgroundSize: '24px 24px' }}></div>

            <div className="max-w-5xl mx-auto px-6 relative z-10 text-center">
                <div className="inline-block p-4 rounded-full bg-[var(--bg-surface)] border border-[var(--border-color)] mb-8 shadow-lg">
                    <BookOpen className="w-8 h-8 text-blue-500" />
                </div>

                <h2 className="text-4xl md:text-6xl font-bold tracking-tight mb-6 text-[var(--text-primary)]">
                    Ferhenga <span className="text-gradient">Dijîtal</span>
                </h2>

                <p className="text-xl text-[var(--text-secondary)] mb-10 max-w-2xl mx-auto">
