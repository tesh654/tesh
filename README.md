import { useState } from "react";
import { Card, CardContent } from "@/components/ui/card";
import { Button } from "@/components/ui/button";
import { Input } from "@/components/ui/input";
import { motion } from "framer-motion";

export default function AffiliateSite() {
  const [search, setSearch] = useState("");
  const products = [
    { name: "Auriculares Inalámbricos", price: "$49.99", link: "#", img: "/headphones.jpg" },
    { name: "Smartwatch Deportivo", price: "$99.99", link: "#", img: "/smartwatch.jpg" },
    { name: "Teclado Mecánico RGB", price: "$79.99", link: "#", img: "/keyboard.jpg" }
  ];

  return (
    <div className="min-h-screen bg-white text-gray-900 p-4">
      <header className="text-center py-6">
        <h1 className="text-4xl font-bold">🔥 Mejores Ofertas de Amazon 🔥</h1>
        <p className="text-lg mt-2">Descubre los productos más vendidos y ahorra en tus compras</p>
      </header>
      <div className="flex justify-center mb-6">
        <Input
          className="w-full max-w-md text-gray-900 border-gray-300 border rounded-lg p-2"
          placeholder="Buscar productos..."
          value={search}
          onChange={(e) => setSearch(e.target.value)}
        />
      </div>
      <div className="grid grid-cols-1 md:grid-cols-3 gap-6">
        {products
          .filter((p) => p.name.toLowerCase().includes(search.toLowerCase()))
          .map((product, index) => (
            <motion.div key={index} whileHover={{ scale: 1.05 }}>
              <Card className="bg-gray-100 shadow-lg rounded-2xl">
                <img src={product.img} alt={product.name} className="w-full h-48 object-cover rounded-t-2xl" />
                <CardContent className="p-4 text-center">
                  <h2 className="text-xl font-semibold">{product.name}</h2>
                  <p className="text-lg text-green-600 font-bold">{product.price}</p>
                  <Button className="mt-3 w-full bg-blue-600 hover:bg-blue-700 text-white font-semibold py-2 rounded-lg">
                    <a href={product.link} target="_blank">Comprar en Amazon</a>
                  </Button>
                </CardContent>
              </Card>
            </motion.div>
          ))}
      </div>
    </div>
  );
}
