import React, { useEffect, useState, useRef } from "react";

export default function JawmaxerWebshop() {
  const preOrderRef = useRef(null);

  const [timeLeft, setTimeLeft] = useState({
    days: 18,
    hours: 20,
    minutes: 15,
    seconds: 42,
  });

  useEffect(() => {
    const timer = setInterval(() => {
      setTimeLeft((prev) => {
        let { days, hours, minutes, seconds } = prev;

        if (seconds > 0) {
          seconds--;
        } else {
          if (minutes > 0) {
            minutes--;
            seconds = 59;
          } else {
            if (hours > 0) {
              hours--;
              minutes = 59;
              seconds = 59;
            } else {
              if (days > 0) {
                days--;
                hours = 23;
                minutes = 59;
                seconds = 59;
              }
            }
          }
        }

        return { days, hours, minutes, seconds };
      });
    }, 1000);

    return () => clearInterval(timer);
  }, []);

  const scrollToPreOrder = () => {
    preOrderRef.current?.scrollIntoView({ behavior: "smooth" });
  };

  return (
    <div className="bg-[#1a1a1a] text-white min-h-screen font-sans">
      {/* HERO */}
      <section className="text-center py-20 px-6 border-b border-gray-700">
        <h1 className="text-6xl font-bold tracking-widest">JawMaxer</h1>
        <p className="mt-4 text-gray-400 uppercase tracking-wider">
          Skarp din kæbelinje
        </p>

        <h2 className="mt-12 text-3xl md:text-4xl font-semibold">
          FORUDBESTIL NU OG FÅ EN SKARPERE JAWLINE!
        </h2>

        {/* COUNTDOWN */}
        <div className="mt-10 grid grid-cols-4 gap-6 max-w-3xl mx-auto">
          {Object.entries(timeLeft).map(([label, value]) => (
            <div
              key={label}
              className="bg-[#2a2a2a] py-6 rounded-lg border border-gray-700"
            >
              <div className="text-4xl font-bold">
                {value.toString().padStart(2, "0")}
              </div>
              <div className="text-gray-400 uppercase text-sm mt-2">
                {label}
              </div>
            </div>
          ))}
        </div>
      </section>

      {/* PRODUCT */}
      <section className="py-20 px-6 text-center border-b border-gray-700">
        <h2 className="text-4xl font-bold mb-12">VORES PRODUKT</h2>

        <div className="grid md:grid-cols-3 gap-8 max-w-6xl mx-auto">
          <img
            src="/jawmaxer-product-1.png"
            alt="JawMaxer produkt"
            className="rounded-lg shadow-xl"
          />
          <img
            src="/jawmaxer-product-2.png"
            alt="JawMaxer produkt"
            className="rounded-lg shadow-xl"
          />
          <img
            src="/jawmaxer-product-3.png"
            alt="JawMaxer produkt"
            className="rounded-lg shadow-xl"
          />
        </div>

        <p className="mt-10 text-gray-300 max-w-2xl mx-auto">
          Få en skarpere kæbelinje med JawMaxer tyggegummi. Styrk din kæbe – ét
          tyg ad gangen.
        </p>

        <p className="mt-6 text-3xl font-bold">Pris: 249,-</p>

        <button
          onClick={scrollToPreOrder}
          className="mt-6 px-10 py-4 bg-white text-black font-bold rounded hover:bg-gray-300 transition"
        >
          FORUDBESTIL NU
        </button>
      </section>

      {/* BEFORE AFTER */}
      <section className="py-20 px-6 text-center border-b border-gray-700">
        <h2 className="text-4xl font-bold mb-12">FØR & EFTER</h2>

        <div className="grid md:grid-cols-2 gap-10 max-w-5xl mx-auto">
          <img
            src="/jawmaxer-before.png"
            alt="Før brug"
            className="rounded-lg shadow-xl"
          />
          <img
            src="/jawmaxer-after.png"
            alt="Efter brug"
            className="rounded-lg shadow-xl"
          />
        </div>

        <p className="text-gray-400 mt-6 text-sm">
          * Resultater kan variere fra person til person.
        </p>
      </section>

      {/* ABOUT + WHY */}
      <section className="py-20 px-6 border-b border-gray-700">
        <div className="grid md:grid-cols-2 gap-12 max-w-6xl mx-auto">
          <div>
            <h3 className="text-3xl font-bold mb-6">OM OS</h3>
            <p className="text-gray-400 leading-relaxed">
              JawMaxer er dedikeret til at hjælpe dig med at opnå en skarpere
              kæbelinje og en stærkere kæbe gennem innovativ træning.
            </p>
          </div>

          <div>
            <h3 className="text-3xl font-bold mb-6">HVORFOR VÆLGE OS?</h3>
            <ul className="space-y-4 text-gray-400">
              <li>✔ Styrker kæbemusklerne</li>
              <li>✔ Høj kvalitet tyggegummi</li>
              <li>✔ Hurtige resultater</li>
            </ul>
          </div>
        </div>
      </section>

      {/* PREORDER FORM */}
      <section ref={preOrderRef} className="py-20 px-6 text-center">
        <h2 className="text-4xl font-bold mb-12">FORUDBESTIL NU</h2>

        <form className="max-w-xl mx-auto space-y-6">
          <input
            type="text"
            placeholder="Navn"
            className="w-full p-4 bg-[#2a2a2a] border border-gray-700 rounded text-white"
          />
          <input
            type="email"
            placeholder="E-mail"
            className="w-full p-4 bg-[#2a2a2a] border border-gray-700 rounded text-white"
          />
          <input
            type="tel"
            placeholder="Telefonnummer"
            className="w-full p-4 bg-[#2a2a2a] border border-gray-700 rounded text-white"
          />

          <button
            type="submit"
            className="w-full py-4 bg-white text-black font-bold rounded hover:bg-gray-300 transition"
          >
            GENNEMFØR FORUDBESTILLING
          </button>
        </form>
      </section>

      <footer className="py-8 text-center text-gray-500 border-t border-gray-700">
        © 2026 JawMaxer. Alle rettigheder forbeholdes.
      </footer>
    </div>
  );
}
