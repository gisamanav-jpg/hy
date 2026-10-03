next-gen-trader/
├── app/
│   ├── layout.tsx
│   ├── page.tsx          ← HOME PAGE
│   ├── globals.css
│   └── courses/
│       └── page.tsx      ← (later)
├── components/
│   ├── Navbar.tsx
│   ├── Hero.tsx
│   ├── HowItWorks.tsx
│   ├── CoursePreview.tsx
│   └── Footer.tsx
└── public/
import type { Metadata } from "next";
import "./globals.css";
import Navbar from "@/components/Navbar";
import Footer from "@/components/Footer";

export const metadata: Metadata = {
  title: "Next Gen Trader — Learn Trading the Right Way",
  description:
    "An educational platform for students and beginners to learn financial markets and trading concepts.",
};

export default function RootLayout({
  children,
}: {
  children: React.ReactNode;
}) {
  return (
    <html lang="en">
      <body className="min-h-screen flex flex-col bg-slate-950 text-slate-100">
        <Navbar />
        <main className="flex-1">{children}</main>
        <Footer />
      </body>
    </html>
  );
}
import Link from "next/link";

export default function Navbar() {
  return (
    <header className="border-b border-slate-800 bg-slate-950/80 backdrop-blur sticky top-0 z-50">
      <nav className="max-w-6xl mx-auto flex items-center justify-between px-6 py-4">
        <Link href="/" className="text-xl font-bold text-emerald-400">
          Next Gen Trader
        </Link>
        <div className="flex items-center gap-6 text-sm">
          <Link href="/courses" className="hover:text-emerald-400">
            Courses
          </Link>
          <Link href="/about" className="hover:text-emerald-400">
            About
          </Link>
          <Link
            href="/login"
            className="px-4 py-2 rounded-lg bg-emerald-500 text-slate-950 font-semibold hover:bg-emerald-400"
          >
            Login
          </Link>
        </div>
      </nav>
    </header>
  );
}
import Link from "next/link";

export default function Hero() {
  return (
    <section className="max-w-6xl mx-auto px-6 py-20 text-center">
      <span className="inline-block px-3 py-1 rounded-full bg-emerald-500/10 text-emerald-400 text-xs font-medium mb-6">
        Education • Not Financial Advice
      </span>

      <h1 className="text-4xl md:text-6xl font-bold leading-tight">
        Learn Trading.
        <br />
        <span className="text-emerald-400">Build Real Skill.</span>
      </h1>

      <p className="mt-6 max-w-2xl mx-auto text-slate-400 text-lg">
        Next Gen Trader teaches students and beginners the fundamentals of
        financial markets — through structured courses, lessons, and quizzes.
        No signals. No shortcuts. Just education.
      </p>

      <div className="mt-10 flex justify-center gap-4">
        <Link
          href="/courses"
          className="px-6 py-3 rounded-lg bg-emerald-500 text-slate-950 font-semibold hover:bg-emerald-400"
        >
          Browse Courses
        </Link>
        <Link
          href="/about"
          className="px-6 py-3 rounded-lg border border-slate-700 hover:border-emerald-400 hover:text-emerald-400"
        >
          How It Works
        </Link>
      </div>
    </section>
  );
}
const steps = [
  { n: "01", title: "Browse Courses", desc: "Explore our catalog and read course details." },
  { n: "02", title: "Apply", desc: "Submit a short application for the course you want." },
  { n: "03", title: "Get Approved", desc: "Our team reviews your application." },
  { n: "04", title: "Pay & Enroll", desc: "Once approved, complete payment to unlock the course." },
  { n: "05", title: "Learn & Practice", desc: "Study lessons and take quizzes at your pace." },
  { n: "06", title: "Earn Certificate", desc: "Meet the requirements and get certified." },
];

export default function HowItWorks() {
  return (
    <section className="max-w-6xl mx-auto px-6 py-20">
      <h2 className="text-3xl font-bold text-center mb-4">How It Works</h2>
      <p className="text-center text-slate-400 mb-12 max-w-xl mx-auto">
        A simple, guided path from curious beginner to certified learner.
      </p>

      <div className="grid grid-cols-1 md:grid-cols-3 gap-6">
        {steps.map((s) => (
          <div
            key={s.n}
            className="p-6 rounded-xl border border-slate-800 bg-slate-900/50 hover:border-emerald-500/50 transition"
          >
            <div className="text-emerald-400 font-mono text-sm mb-2">{s.n}</div>
            <h3 className="font-semibold text-lg mb-2">{s.title}</h3>
            <p className="text-slate-400 text-sm">{s.desc}</p>
          </div>
        ))}
      </div>
    </section>
  );
}
export default function Footer() {
  return (
    <footer className="border-t border-slate-800 mt-20">
      <div className="max-w-6xl mx-auto px-6 py-10 text-sm text-slate-500">
        <p className="mb-4">
          <strong className="text-slate-300">Disclaimer:</strong> Next Gen
          Trader is an educational platform. We do not provide buy/sell
          signals, investment advice, or guarantee any profits. Trading
          involves risk. Always do your own research.
        </p>
        <p>© {new Date().getFullYear()} Next Gen Trader. All rights reserved.</p>
      </div>
    </footer>
  );
}
import Hero from "@/components/Hero";
import HowItWorks from "@/components/HowItWorks";

export default function HomePage() {
  return (
    <>
      <Hero />
      <HowItWorks />
    </>
  );
}
