// Jagost Website - React + Tailwind
import { useState } from "react";
import { Button } from "@/components/ui/button";
import { Card, CardContent } from "@/components/ui/card";

const mockAdmin = {
  username: "admin",
  password: "jagostonfire",
};

export default function JagostWebsite() {
  const [loggedIn, setLoggedIn] = useState(false);
  const [products, setProducts] = useState([
    {
      id: 1,
      name: "Jagost Corn Original",
      price: "10.000",
      image: "https://via.placeholder.com/150",
    },
  ]);
  const [form, setForm] = useState({ name: "", price: "", image: "" });
  const [loginForm, setLoginForm] = useState({ username: "", password: "" });
  const [orders, setOrders] = useState([]);

  const handleLogin = () => {
    if (
      loginForm.username === mockAdmin.username &&
      loginForm.password === mockAdmin.password
    ) {
      setLoggedIn(true);
    } else {
      alert("Login gagal");
    }
  };

  const handleAddProduct = () => {
    if (!form.name || !form.price || !form.image) return;
    const newProduct = {
      ...form,
      id: Date.now(),
    };
    setProducts([...products, newProduct]);
    setForm({ name: "", price: "", image: "" });
  };

  const handleDelete = (id) => {
    setProducts(products.filter((p) => p.id !== id));
  };

  const handleOrder = (product) => {
    const name = prompt("Masukkan nama Anda:");
    const contact = prompt("Masukkan nomor HP Anda:");
    const level = prompt("Pilih level pedas (1. Pedas 2. Extra Pedas 3. Ghost!!):");

    let levelText = "";
    if (level === "1") levelText = "Pedas";
    else if (level === "2") levelText = "Extra Pedas";
    else if (level === "3") levelText = "Ghost!!";
    else levelText = "Pedas";

    if (name && contact) {
      setOrders([...orders, { ...product, customer: name, contact, level: levelText }]);

      const message = Halo saya ${name} mau pesan ${product.name} seharga Rp ${product.price} dengan level ${levelText};
      const whatsappURL = https://wa.me/6281227858684?text=${encodeURIComponent(message)};
      window.open(whatsappURL, "_blank");
    }
  };

  return (
    <div className="p-4 space-y-4">
      <h1 className="text-3xl font-bold text-red-600">JAGOST - Jangn cuma once, harus on fire!</h1>

      {!loggedIn && (
        <div className="space-y-2 max-w-sm">
          <input
            placeholder="Username"
            className="border w-full p-2"
            value={loginForm.username}
            onChange={(e) => setLoginForm({ ...loginForm, username: e.target.value })}
          />
          <input
            placeholder="Password"
            type="password"
            className="border w-full p-2"
            value={loginForm.password}
            onChange={(e) => setLoginForm({ ...loginForm, password: e.target.value })}
          />
          <Button onClick={handleLogin}>Login Admin</Button>
        </div>
      )}

      {loggedIn && (
        <div className="space-y-4">
          <div className="space-y-2 max-w-md">
            <input
              placeholder="Nama Produk"
              className="border w-full p-2"
              value={form.name}
              onChange={(e) => setForm({ ...form, name: e.target.value })}
            />
            <input
              placeholder="Harga"
              className="border w-full p-2"
              value={form.price}
              onChange={(e) => setForm({ ...form, price: e.target.value })}
            />
            <input
              placeholder="Link Gambar"
              className="border w-full p-2"
              value={form.image}
              onChange={(e) => setForm({ ...form, image: e.target.value })}
            />
            <Button onClick={handleAddProduct}>Tambah Produk</Button>
          </div>

          <div>
            <h2 className="text-xl font-semibold mt-4">Pesanan Masuk</h2>
            <ul className="list-disc ml-6">
              {orders.map((order, index) => (
                <li key={index}>
                  {order.customer} pesan {order.name} (Rp {order.price}) - {order.contact} - Level: {order.level}
                </li>
              ))}
            </ul>
          </div>
        </div>
      )}

      <div className="grid grid-cols-2 md:grid-cols-3 gap-4">
        {products.map((product) => (
          <Card key={product.id} className="relative">
            <img src={product.image} alt={product.name} className="w-full h-32 object-cover rounded-t" />
            <CardContent>
              <h2 className="font-semibold text-lg">{product.name}</h2>
              <p className="text-sm text-gray-600">Rp {product.price}</p>
              {loggedIn ? (
                <Button variant="destructive" onClick={() => handleDelete(product.id)}>
                  Hapus
                </Button>
              ) : (
                <Button onClick={() => handleOrder(product)}>Pesan Sekarang</Button>
              )}
            </CardContent>
          </Card>
        ))}
      </div>
    </div>
  );
}
