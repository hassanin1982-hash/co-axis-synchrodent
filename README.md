import React, { useState, useEffect } from 'react';
import { 
  Activity, 
  Target, 
  Workflow, 
  ShieldCheck, 
  Users, 
  Microscope, 
  ChevronRight, 
  Instagram, 
  Linkedin,
  Mail,
  Menu,
  X,
  Layers,
  CheckCircle2,
  ExternalLink
} from 'lucide-react';

const App = () => {
  const [activeTab, setActiveTab] = useState('home');
  const [isMenuOpen, setIsMenuOpen] = useState(false);
  const [scrollPos, setScrollPos] = useState(0);

  useEffect(() => {
    const handleScroll = () => setScrollPos(window.scrollY);
    window.addEventListener('scroll', handleScroll);
    return () => window.removeEventListener('scroll', handleScroll);
  }, []);

  const sections = {
    home: "Welcome",
    philosophy: "The Concept",
    workflow: "Workflow",
    portfolio: "Case Portfolio",
    founder: "Founder"
  };

  const Navigation = () => (
    <nav className={`fixed top-0 w-full z-50 transition-all duration-300 ${scrollPos > 50 ? 'bg-white shadow-md py-2' : 'bg-transparent py-4'}`}>
      <div className="max-w-7xl mx-auto px-4 flex justify-between items-center">
        <div className="flex items-center gap-2 cursor-pointer" onClick={() => setActiveTab('home')}>
          <div className="w-10 h-10 bg-[#1A365D] rounded-lg flex items-center justify-center text-white">
            <Target size={24} strokeWidth={2.5} />
          </div>
          <div className="flex flex-col">
            <span className="text-[#1A365D] font-bold text-xl leading-none tracking-tight">Co-Axis</span>
            <span className="text-[#63B3ED] font-semibold text-sm">SynchroDent</span>
          </div>
        </div>

        {/* Desktop Nav */}
        <div className="hidden md:flex gap-8 items-center">
          {Object.entries(sections).map(([key, label]) => (
            <button
              key={key}
              onClick={() => setActiveTab(key)}
              className={`text-sm font-bold uppercase tracking-wider transition-colors ${activeTab === key ? 'text-[#1A365D] border-b-2 border-[#63B3ED]' : 'text-slate-500 hover:text-[#1A365D]'}`}
            >
              {label}
            </button>
          ))}
          <button className="bg-[#1A365D] text-white px-5 py-2 rounded-lg text-sm font-bold hover:bg-slate-800 transition-all shadow-md">
            Join Waitlist
          </button>
        </div>

        {/* Mobile Menu Button */}
        <button className="md:hidden text-[#1A365D]" onClick={() => setIsMenuOpen(!isMenuOpen)}>
          {isMenuOpen ? <X /> : <Menu />}
        </button>
      </div>

      {/* Mobile Drawer */}
      {isMenuOpen && (
        <div className="absolute top-full left-0 w-full bg-white border-t border-slate-100 flex flex-col p-6 gap-6 md:hidden shadow-2xl animate-in fade-in slide-in-from-top-4">
          {Object.entries(sections).map(([key, label]) => (
            <button
              key={key}
              onClick={() => { setActiveTab(key); setIsMenuOpen(false); }}
              className={`text-left text-lg font-bold ${activeTab === key ? 'text-[#1A365D]' : 'text-slate-500'}`}
            >
              {label}
            </button>
          ))}
          <button className="bg-[#1A365D] text-white py-4 rounded-xl font-bold shadow-lg">Join Waitlist</button>
        </div>
      )}
    </nav>
  );

  const PortfolioItem = ({ title, category, outcome, steps }) => (
    <div className="bg-white rounded-3xl overflow-hidden border border-slate-100 shadow-sm hover:shadow-xl transition-all duration-500 group">
      <div className="aspect-video bg-slate-100 relative overflow-hidden flex items-center justify-center">
        <div className="absolute inset-0 bg-gradient-to-br from-[#1A365D]/5 to-transparent"></div>
        <Target size={80} className="text-[#1A365D] opacity-10 group-hover:scale-110 transition-transform duration-700" />
        <div className="absolute top-4 left-4">
          <span className="bg-[#1A365D] text-white px-3 py-1 rounded-full text-[10px] font-bold uppercase tracking-widest">
            {category}
          </span>
        </div>
      </div>
      <div className="p-8">
        <h4 className="text-xl font-extrabold text-[#1A365D] mb-2">{title}</h4>
        <p className="text-slate-500 text-sm mb-6 leading-relaxed">{outcome}</p>
        
        <div className="space-y-3 mb-8">
          {steps.map((step, idx) => (
            <div key={idx} className="flex items-center gap-3 text-sm text-slate-700 font-medium">
              <CheckCircle2 size={16} className="text-[#63B3ED]" />
              {step}
            </div>
          ))}
        </div>
        
        <button className="w-full py-3 rounded-xl border-2 border-slate-100 text-[#1A365D] font-bold text-sm flex items-center justify-center gap-2 hover:bg-[#1A365D] hover:text-white hover:border-[#1A365D] transition-all">
          View Workflow <ExternalLink size={14} />
        </button>
      </div>
    </div>
  );

  const Hero = () => (
    <section className="relative min-h-[90vh] flex flex-col items-center justify-center px-4 pt-24 overflow-hidden bg-white">
      <div className="absolute inset-0 z-0 opacity-5 pointer-events-none">
        <div className="absolute top-0 left-0 w-full h-full bg-[radial-gradient(#1A365D_1px,transparent_1px)] [background-size:40px_40px]"></div>
      </div>
      
      <div className="z-10 text-center max-w-4xl animate-in fade-in slide-in-from-bottom-8 duration-1000">
        <div className="inline-flex items-center gap-2 bg-blue-50 text-[#1A365D] px-4 py-2 rounded-full text-xs font-black mb-8 border border-blue-100 tracking-[0.2em] uppercase">
          <Activity size={14} />
          Precision Defined
        </div>
        
        <h1 className="text-6xl md:text-8xl font-black tracking-tight mb-8 leading-[0.9]">
          <span className="text-[#1A365D]">CO-AXIS</span><br/>
          <span className="text-[#63B3ED]">SYNCHRODENT</span>
        </h1>
        
        <p className="text-xl md:text-2xl text-slate-500 mb-12 leading-relaxed font-medium max-w-2xl mx-auto">
          Aligning Surgery & Artistry through <span className="text-black font-bold">Absolute Digital Accuracy.</span>
        </p>
        
        <div className="flex flex-col sm:flex-row gap-4 justify-center">
          <button onClick={() => setActiveTab('workflow')} className="bg-[#1A365D] text-white px-10 py-5 rounded-2xl text-lg font-bold shadow-2xl shadow-blue-900/40 hover:translate-y-[-4px] active:translate-y-0 transition-all flex items-center justify-center gap-3">
            The Workflow <ChevronRight size={20} />
          </button>
          <button onClick={() => setActiveTab('portfolio')} className="bg-white border-2 border-slate-100 text-[#1A365D] px-10 py-5 rounded-2xl text-lg font-bold hover:border-[#63B3ED] transition-all">
            Case Portfolio
          </button>
        </div>
      </div>
    </section>
  );

  const Philosophy = () => (
    <section className="py-24 bg-slate-50 px-4 border-y border-slate-100">
      <div className="max-w-7xl mx-auto">
        <div className="grid md:grid-cols-2 gap-12 items-center">
          <div>
            <span className="text-[#63B3ED] font-black tracking-[0.3em] text-xs uppercase mb-4 block">The Foundation</span>
            <h2 className="text-4xl md:text-5xl font-black text-[#1A365D] mb-8 leading-tight">A Protocol of <br/>Collaborative Harmony.</h2>
            <p className="text-slate-600 text-lg leading-relaxed mb-8 font-medium">
              We bridge the gap between clinical surgery and laboratory engineering. By focusing on the "Axis," we define the trajectory; by focusing on "Synchro," we define the rhythm.
            </p>
            <div className="flex flex-wrap gap-4">
              <div className="bg-white px-6 py-4 rounded-2xl border border-slate-200 shadow-sm flex items-center gap-3">
                <Target className="text-[#1A365D]" />
                <span className="font-bold text-[#1A365D]">Zero Margin Error</span>
              </div>
              <div className="bg-white px-6 py-4 rounded-2xl border border-slate-200 shadow-sm flex items-center gap-3">
                <Workflow className="text-[#63B3ED]" />
                <span className="font-bold text-[#1A365D]">Unified Data</span>
              </div>
            </div>
          </div>
          <div className="grid grid-cols-1 gap-6">
            <div className="bg-[#1A365D] p-8 rounded-[2.5rem] text-white">
              <Layers className="text-[#63B3ED] mb-4" size={32} />
              <h3 className="text-xl font-bold mb-3">Axis Precision</h3>
              <p className="text-slate-400 text-sm leading-relaxed">
                Defining insertion paths with sub-millimeter mathematical accuracy using high-fidelity digital planning.
              </p>
            </div>
            <div className="bg-white p-8 rounded-[2.5rem] border border-slate-200 shadow-xl">
              <Users className="text-[#1A365D] mb-4" size={32} />
              <h3 className="text-xl font-bold mb-3 text-[#1A365D]">Synchro Lab</h3>
              <p className="text-slate-500 text-sm leading-relaxed">
                Real-time synchronization between the restorative technician and the surgeon for absolute prosthetic fit.
              </p>
            </div>
          </div>
        </div>
      </div>
    </section>
  );

  const PortfolioSection = () => (
    <section className="py-24 px-4 bg-white min-h-screen">
      <div className="max-w-7xl mx-auto">
        <div className="flex flex-col md:flex-row justify-between items-end gap-8 mb-16">
          <div className="max-w-2xl">
            <span className="text-[#63B3ED] font-black tracking-[0.3em] text-xs uppercase mb-4 block">Our Work</span>
            <h2 className="text-5xl font-black text-[#1A365D] leading-tight">Case Portfolio</h2>
            <p className="text-slate-500 text-lg mt-4 font-medium italic">
              "Visual evidence of surgery meets artistry."
            </p>
          </div>
          <div className="flex gap-2">
            <button className="bg-[#1A365D] text-white px-6 py-3 rounded-xl font-bold text-sm">All Cases</button>
            <button className="bg-slate-50 text-[#1A365D] px-6 py-3 rounded-xl font-bold text-sm border border-slate-200">Full Arch</button>
          </div>
        </div>

        <div className="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
          <PortfolioItem 
            title="Symmetry Alignment"
            category="Anterior Esthetics"
            outcome="Achieved a perfectly balanced gingival zenith through digitally guided tissue contouring and Co-Axis planning."
            steps={["3D Facial Mapping", "Guided Implant Placement", "Synchro Restorative Design"]}
          />
          <PortfolioItem 
            title="Digital Foundation"
            category="Full Arch"
            outcome="Reconstruction of a complex mandible using the Synchro workflow to ensure immediate load stability."
            steps={["Bone Reduction Guide", "Multi-Unit Axis Alignment", "PMMA Temp Sync"]}
          />
          <PortfolioItem 
            title="Molar Stability"
            category="Single Unit"
            outcome="Precise molar placement avoiding sinus intervention through aggressive Axis angling and custom abutment."
            steps={["Sinus Map Planning", "Co-Axis Angled Implant", "Digital Impression Sync"]}
          />
        </div>
      </div>
    </section>
  );

  const WorkflowSection = () => (
    <section className="py-24 px-4 bg-slate-900 text-white overflow-hidden relative">
      <div className="absolute top-0 right-0 w-1/2 h-full bg-[#1A365D] skew-x-12 translate-x-32 opacity-20"></div>
      <div className="max-w-7xl mx-auto relative z-10">
        <div className="text-center mb-20">
          <h2 className="text-5xl font-black mb-6 italic tracking-tight">The Synchro Workflow</h2>
          <div className="w-24 h-1 bg-[#63B3ED] mx-auto"></div>
        </div>
        
        <div className="grid md:grid-cols-4 gap-12">
          {[
            { n: "01", t: "Imaging", d: "High-resolution CBCT and intra-oral scans." },
            { n: "02", t: "Axis Plan", d: "Mathematical trajectory calculation." },
            { n: "03", t: "Synchro", d: "Laboratory restorative validation." },
            { n: "04", t: "Execution", d: "Guided surgery with absolute fit." }
          ].map((step, i) => (
            <div key={i} className="group cursor-default">
              <span className="text-6xl font-black text-white/10 group-hover:text-[#63B3ED]/40 transition-colors duration-500">{step.n}</span>
              <h4 className="text-2xl font-bold mt-[-10px] mb-4 text-white group-hover:translate-x-2 transition-transform">{step.t}</h4>
              <p className="text-slate-400 text-sm leading-relaxed">{step.d}</p>
            </div>
          ))}
        </div>
      </div>
    </section>
  );

  const Footer = () => (
    <footer className="bg-[#1A202C] text-white py-20 px-4 border-t border-white/5">
      <div className="max-w-7xl mx-auto flex flex-col md:flex-row justify-between items-start gap-12">
        <div className="max-w-sm">
          <div className="flex items-center gap-3 mb-8">
            <Target className="text-[#63B3ED]" size={40} />
            <h3 className="text-3xl font-black tracking-tighter uppercase italic">Co-Axis <br/><span className="text-[#63B3ED] not-italic">SynchroDent</span></h3>
          </div>
          <p className="text-slate-400 leading-relaxed mb-8 font-medium">
            Bridging the gap between the surgical clinic and the digital laboratory through geometric truth and collaborative harmony.
          </p>
        </div>
        
        <div className="bg-white/5 p-8 rounded-[2rem] border border-white/10 w-full md:w-auto">
          <h4 className="text-xl font-bold mb-6 flex items-center gap-2">
            <Users size={20} className="text-[#63B3ED]" /> Contact Dr. Albadry
          </h4>
          <div className="space-y-4">
             <div className="flex items-center gap-4 text-slate-300">
                <Mail size={18} />
                <span>office@coaxisdent.com</span>
             </div>
             <div className="flex items-center gap-4 text-slate-300">
                <Instagram size={18} />
                <span>@coaxis_synchrodent</span>
             </div>
          </div>
        </div>
      </div>
      
      <div className="max-w-7xl mx-auto mt-20 pt-10 border-t border-white/10 flex flex-col md:flex-row justify-between items-center gap-6 text-sm text-slate-500 font-bold uppercase tracking-widest">
        <p>© 2024 Co-Axis SynchroDent</p>
        <p className="text-white">by Dr. Hasanain Albadry</p>
      </div>
    </footer>
  );

  return (
    <div className="min-h-screen bg-white font-sans text-[#1A202C] selection:bg-blue-100 antialiased">
      <Navigation />
      
      <main className="animate-in fade-in duration-700">
        {activeTab === 'home' && (
          <>
            <Hero />
            <Philosophy />
            <WorkflowSection />
          </>
        )}
        
        {activeTab === 'philosophy' && <Philosophy />}
        {activeTab === 'workflow' && <WorkflowSection />}
        {activeTab === 'portfolio' && <PortfolioSection />}

        {activeTab === 'founder' && (
          <div className="pt-40 pb-24 min-h-screen flex items-center justify-center px-4 bg-slate-50">
            <div className="max-w-4xl bg-white p-16 rounded-[4rem] shadow-2xl border border-slate-100 text-center relative overflow-hidden">
              <div className="absolute top-0 right-0 w-32 h-32 bg-blue-50 rounded-bl-[100%]"></div>
              <div className="w-40 h-40 bg-slate-100 rounded-full mx-auto mb-10 flex items-center justify-center text-[#1A365D] border-8 border-white shadow-xl">
                <Users size={80} />
              </div>
              <h2 className="text-5xl font-black text-[#1A365D] mb-4">Dr. Hasanain Albadry</h2>
              <p className="text-[#63B3ED] font-black text-xl mb-10 tracking-[0.4em] uppercase">Foundation Lead</p>
              <div className="max-w-2xl mx-auto">
                <p className="text-2xl text-slate-600 leading-relaxed font-light mb-12 italic">
                  "Digital dentistry is the pursuit of absolute alignment—between data and biology, and between surgery and restoration."
                </p>
              </div>
              <button className="bg-[#1A365D] text-white px-12 py-5 rounded-2xl font-black text-lg hover:bg-slate-800 transition-all shadow-xl tracking-wider">
                Partner with the Foundation
              </button>
            </div>
          </div>
        )}
      </main>

      <Footer />
    </div>
  );
};

export default App;
