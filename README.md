import { Button } from "@/components/ui/button";
import { motion } from "framer-motion";
import { useState, useEffect } from "react";

export default function HeroSection() {
  const [mouseX, setMouseX] = useState(0);
  const [mouseY, setMouseY] = useState(0);

  useEffect(() => {
    const handleMouseMove = (event) => {
      setMouseX(event.clientX);
      setMouseY(event.clientY);
    };
    window.addEventListener("mousemove", handleMouseMove);
    return () => window.removeEventListener("mousemove", handleMouseMove);
  }, []);

  return (
    <div className="bg-black text-white min-h-screen flex flex-col items-center relative overflow-hidden">
      {/* Navbar */}
      <nav className="absolute top-0 left-0 w-full flex justify-between px-8 py-4 text-lg items-center backdrop-blur-lg bg-opacity-30 bg-black">
        <h1 className="text-2xl font-semibold text-[#4F7942] tracking-wide">VIANRAA</h1>
        <div className="space-x-6 hidden md:flex">
          <a href="#" className="text-gray-300 hover:text-[#4F7942] transition">Home</a>
          <a href="#" className="text-gray-300 hover:text-[#4F7942] transition">Projects</a>
          <a href="#" className="text-gray-300 hover:text-[#4F7942] transition">Services</a>
          <a href="#" className="text-gray-300 hover:text-[#4F7942] transition">Contact</a>
        </div>
        <Button className="bg-[#4F7942] text-black px-5 py-2 rounded-lg shadow-md hover:bg-opacity-80 transition">Get Started</Button>
      </nav>

      {/* Hero Content */}
      <div className="flex flex-grow items-center justify-between w-full px-12 max-w-7xl relative">
        <div className="w-1/2">
          <h1 className="text-6xl font-extrabold text-[#4F7942] leading-tight">Transforming IT Solutions</h1>
          <p className="text-gray-400 mt-4 text-lg max-w-md">AI-Powered Innovation for Everyone, Everywhere</p>
          <Button className="mt-6 bg-[#4F7942] text-black px-6 py-3 rounded-lg shadow-lg hover:bg-opacity-80 transition">Get Started</Button>
        </div>

        {/* Hover Panels */}
        <div className="absolute right-20 top-1/3 w-96 h-64 flex flex-wrap justify-center items-center opacity-40">
          {["bg-red-500", "bg-blue-500", "bg-yellow-500", "bg-green-500"].map((color, index) => (
            <motion.div
              key={index}
              className={`w-28 h-20 ${color} bg-opacity-30 rounded-lg m-2 transition-all duration-300`}
              whileHover={{ scale: 1.2, opacity: 0.7 }}
            />
          ))}
        </div>
      </div>

      {/* Scroll Instruction */}
      <div className="absolute bottom-10 text-gray-500 text-sm tracking-wide animate-bounce">Scroll ↓</div>

      {/* Why Choose Us Section */}
      <section className="w-full bg-black text-white py-16 flex flex-col items-center">
        <h2 className="text-4xl font-bold text-[#4F7942]">WHY CHOOSE US?</h2>
        <div className="w-16 border-b-4 border-[#4F7942] mt-2 mb-8"></div>
        <div className="grid grid-cols-1 md:grid-cols-3 gap-8 max-w-6xl">
          {[
            { icon: "⚡", title: "AI-Driven IT Solutions", desc: "We offer intelligent solutions tailored to meet unique needs, utilizing advanced AI to drive innovation and efficiency." },
            { icon: "📦", title: "Scalable Infrastructure", desc: "Our services are designed to grow with your business, offering flexibility and scalability to adapt to evolving goals." },
            { icon: "⏳", title: "24/7 Support", desc: "Round-the-clock support from our dedicated team ensures your business stays online and operational at all times." }
          ].map((item, index) => (
            <motion.div 
              key={index} 
              className="bg-gray-900 p-6 rounded-xl shadow-lg text-center transition duration-300 hover:scale-105 hover:bg-gray-800"
              whileHover={{ scale: 1.1, backgroundColor: "#2d2d2d" }}
            >
              <div className="text-4xl text-[#4F7942] mb-4">{item.icon}</div>
              <h3 className="text-2xl font-semibold mb-2">{item.title}</h3>
              <p className="text-gray-400">{item.desc}</p>
            </motion.div>
          ))}
        </div>
      </section>
    </div>
  );
}

