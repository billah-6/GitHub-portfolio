// Portfolio React avec menu à gauche - Dark Mode

import { useState } from "react";
import { motion } from "framer-motion";
import {
  Home,
  GraduationCap,
  Briefcase,
  Award,
  Languages,
  Mail
} from "lucide-react";

const sections = [
  { id: "presentation", label: "Présentation", icon: <Home /> },
  { id: "formation", label: "Formation", icon: <GraduationCap /> },
  { id: "experience", label: "Expérience", icon: <Briefcase /> },
  { id: "certificats", label: "Certificats", icon: <Award /> },
  { id: "langues", label: "Langues", icon: <Languages /> },
  { id: "contact", label: "Contact", icon: <Mail /> }
];

export default function Portfolio() {
  const [activeSection, setActiveSection] = useState("presentation");

  return (
    <div className="flex min-h-screen bg-zinc-900 text-white">
      <aside className="w-64 bg-zinc-800 p-4 space-y-4">
        <h1 className="text-2xl font-bold text-yellow-400">Abdelilah</h1>
        <nav className="space-y-2">
          {sections.map((section) => (
            <button
              key={section.id}
              onClick={() => setActiveSection(section.id)}
              className={`flex items-center gap-2 w-full p-2 rounded hover:bg-zinc-700 ${
                activeSection === section.id ? "bg-zinc-700" : ""
              }`}
            >
              {section.icon} {section.label}
            </button>
          ))}
        </nav>
      </aside>

      <main className="flex-1 p-8">
        <motion.div
          key={activeSection}
          initial={{ opacity: 0, x: 50 }}
          animate={{ opacity: 1, x: 0 }}
          transition={{ duration: 0.4 }}
        >
          {activeSection === "presentation" && (
            <section>
              <h2 className="text-3xl font-semibold mb-4">Présentation</h2>
              <p>Je suis Abdelilah Ait Ouabbou, auditeur financier passionné par l'analyse de données et les outils modernes comme Python, Power BI et Excel avancé.</p>
            </section>
          )}

          {activeSection === "formation" && (
            <section>
              <h2 className="text-3xl font-semibold mb-4">Formation</h2>
              <ul className="list-disc ml-6">
                <li>Master en Audit et Contrôle de Gestion - Maroc</li>
                <li>Modules : Audit, Contrôle interne, Power BI, Python</li>
              </ul>
            </section>
          )}

          {activeSection === "experience" && (
            <section>
              <h2 className="text-3xl font-semibold mb-4">Expérience</h2>
              <ul className="list-disc ml-6">
                <li>Auditeur Financier Junior chez TCG (2023 - Aujourd’hui)</li>
                <li>Stage en Contrôle de Gestion - [Entreprise]</li>
              </ul>
            </section>
          )}

          {activeSection === "certificats" && (
            <section>
              <h2 className="text-3xl font-semibold mb-4">Certificats</h2>
              <ul className="list-disc ml-6">
                <li>Power BI Analyst – Microsoft</li>
                <li>Google Data Analytics – Coursera</li>
                <li>Python pour la Finance – OpenClassrooms</li>
              </ul>
            </section>
          )}

          {activeSection === "langues" && (
            <section>
              <h2 className="text-3xl font-semibold mb-4">Langues</h2>
              <ul className="list-disc ml-6">
                <li>Français – Courant</li>
                <li>Anglais – Professionnel</li>
                <li>Arabe – Langue maternelle</li>
              </ul>
            </section>
          )}

          {activeSection === "contact" && (
            <section>
              <h2 className="text-3xl font-semibold mb-4">Contact</h2>
              <p>Email : ton.email@exemple.com</p>
              <p>LinkedIn : <a href="https://linkedin.com/in/ton-profil" className="text-blue-400 hover:underline">ton-profil</a></p>
            </section>
          )}
        </motion.div>
      </main>
    </div>
  );
}


