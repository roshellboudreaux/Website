import React, { useState } from "react";

export default function Site() {
  const [open, setOpen] = useState(false);

  const navItems = [
    { id: "home", label: "Home" },
    { id: "services", label: "Services" },
    { id: "about", label: "About" },
    { id: "resources", label: "Resources" },
    { id: "contact", label: "Contact" },
  ];

  const scrollTo = (id) => {
    const el = document.getElementById(id);
    if (el) el.scrollIntoView({ behavior: "smooth", block: "start" });
    setOpen(false);
  };

  return (
    <div className="min-h-screen bg-white text-slate-800">
      <header className="sticky top-0 z-50 backdrop-blur bg-white/80 border-b border-slate-200">
        <div className="max-w-6xl mx-auto px-4 sm:px-6">
          <div className="flex items-center justify-between h-16">
            <div className="flex items-center gap-3">
              <div className="w-9 h-9 rounded-2xl bg-violet-600 flex items-center justify-center text-white font-semibold shadow-sm">RB</div>
              <div>
                <p className="font-semibold leading-tight">Roshell Boudreaux</p>
                <p className="text-xs text-slate-500 -mt-0.5">Christian Counseling & Coaching</p>
              </div>
            </div>
            <nav className="hidden md:flex items-center gap-6">
              {navItems.map((n) => (
                <button
                  key={n.id}
                  onClick={() => scrollTo(n.id)}
                  className="text-sm text-slate-700 hover:text-violet-700 transition-colors"
                >
                  {n.label}
                </button>
              ))}
              <a
                href="#booking"
                className="inline-flex items-center gap-2 rounded-2xl bg-violet-600 px-4 py-2 text-white text-sm shadow-sm hover:bg-violet-700 transition-colors"
                onClick={(e) => {
                  e.preventDefault();
                  scrollTo("booking");
                }}
              >
                Book Session
              </a>
            </nav>
            <button
              className="md:hidden inline-flex items-center justify-center w-10 h-10 rounded-xl border border-slate-200 hover:bg-slate-50"
              onClick={() => setOpen((v) => !v)}
              aria-label="Open menu"
            >
              <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" strokeWidth="2" strokeLinecap="round" strokeLinejoin="round" className="text-slate-700">
                <line x1="3" y1="12" x2="21" y2="12" />
                <line x1="3" y1="6" x2="21" y2="6" />
                <line x1="3" y1="18" x2="21" y2="18" />
              </svg>
            </button>
          </div>
        </div>
        {open && (
          <div className="md:hidden border-t border-slate-200 bg-white">
            <div className="max-w-6xl mx-auto px-4 py-4 grid gap-3">
              {navItems.map((n) => (
                <button
                  key={n.id}
                  onClick={() => scrollTo(n.id)}
                  className="text-left text-sm px-3 py-2 rounded-xl hover:bg-slate-50"
                >
                  {n.label}
                </button>
              ))}
              <button
                onClick={() => scrollTo("booking")}
                className="text-left text-sm px-3 py-2 rounded-xl bg-violet-600 text-white hover:bg-violet-700"
              >
                Book Session
              </button>
            </div>
          </div>
        )}
      </header>

      <section id="home" className="relative overflow-hidden">
        <div className="absolute inset-x-0 -top-40 -z-10 blur-3xl opacity-30" aria-hidden="true">
          <div className="mx-auto max-w-2xl rotate-6 bg-gradient-to-tr from-violet-300 via-fuchsia-200 to-rose-200 p-24 rounded-full" />
        </div>
        <div className="max-w-6xl mx-auto px-4 sm:px-6 py-20 sm:py-28">
          <div className="grid md:grid-cols-2 gap-10 items-center">
            <div>
              <h1 className="text-4xl sm:text-5xl font-semibold tracking-tight text-slate-900">
                Faith-forward counseling for real life.
              </h1>
              <p className="mt-5 text-slate-600 leading-relaxed">
                Compassionate, scripture-aligned guidance for women and families. Together, we’ll build rhythms of healing, clarity, and hope.
              </p>
              <div className="mt-8 flex flex-wrap gap-3">
                <a
                  href="#booking"
                  onClick={(e) => { e.preventDefault(); scrollTo("booking"); }}
                  className="rounded-2xl bg-violet-600 px-5 py-3 text-white text-sm font-medium shadow-sm hover:bg-violet-700"
                >
                  Book a Session
                </a>
                <a
                  href="#services"
                  onClick={(e) => { e.preventDefault(); scrollTo("services"); }}
                  className="rounded-2xl border border-slate-300 px-5 py-3 text-slate-700 text-sm hover:bg-slate-50"
                >
                  Explore Services
                </a>
              </div>
            </div>
          </div>
        </div>
      </section>

      <section id="services" className="py-20 bg-slate-50">
        <div className="max-w-6xl mx-auto px-4 sm:px-6">
          <h2 className="text-3xl font-semibold mb-6">Services</h2>
          <div className="grid sm:grid-cols-2 lg:grid-cols-3 gap-6">
            {["Individual Counseling","Marriage & Family Support","Women’s Coaching","Workshops & Retreats","Virtual Sessions","Prayer & Care"].map((title, i) => (
              <div key={i} className="rounded-3xl bg-white p-6 shadow-sm border border-slate-200">
                <h3 className="font-semibold text-lg">{title}</h3>
                <p className="mt-2 text-sm text-slate-600">Faith-centered support to help you grow, heal, and walk confidently in your purpose.</p>
              </div>
            ))}
          </div>
        </div>
      </section>

      <section id="about" className="py-20">
        <div className="max-w-6xl mx-auto px-4 sm:px-6 text-center">
          <h2 className="text-3xl font-semibold mb-4">About Roshell</h2>
          <p className="text-slate-600 max-w-3xl mx-auto leading-relaxed">
            I’m Roshell Boudreaux—creative, devoted to serving others, and passionate about spiritual wellness. As a counselor and coach, I blend biblical wisdom with practical tools to help you grow in grace, integrity, and purpose.
          </p>
        </div>
      </section>

      <section id="booking" className="py-20 bg-slate-50 text-center">
        <h2 className="text-3xl font-semibold mb-4">Ready to begin?</h2>
        <p className="text-slate-600 mb-8 max-w-2xl mx-auto">
          Book a discovery call to see if we’re a fit. Sessions available online and in person.
        </p>
        <a
          href="https://calendly.com/"
          target="_blank"
          rel="noreferrer"
          className="inline-block rounded-2xl bg-violet-600 px-6 py-3 text-white text-sm font-medium shadow-sm hover:bg-violet-700"
        >
          Schedule on Calendly
        </a>
      </section>

      <footer className="border-t border-slate-200 py-10 text-center text-sm text-slate-500">
        <p>© {new Date().getFullYear()} Roshell Boudreaux. All rights reserved.</p>
      </footer>
    </div>
  );
}
