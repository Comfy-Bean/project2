<script lang="ts">
  import { onMount } from "svelte";
  import ProductCard from "$lib/ProductCard.svelte";

  // Sample products data
  let products = [
    {
      id: "product1",
      name: "Hazelnut Coffee",
      price: 150,
      image: "images/hazelnut.jpg",
      description: "A rich and nutty coffee experience.",
      brand: "Coffee House",
      size: "250ml",
      material: "Glass",
      category: "Black-based Coffee",
    },
    {id: "product1",
      name: "Hazelnut Coffee",
      price: 150,
      image: "images/hazelnut.jpg",
      description: "A rich and nutty coffee experience.",
      brand: "Coffee House",
      size: "250ml",
      material: "Glass",
      category: "Black-based Coffee",
    },
    {
      id: "product2",
      name: "Cortado Coffee",
      price: 150,
      image: "images/cortado.jpg",
      description: "A perfect balance of espresso and milk.",
      brand: "Coffee House",
      size: "250ml",
      material: "Glass",
      category: "Black-based Coffee",
    },
    {
      id: "product3",
      name: "Machiatto Coffee",
      price: 150,
      image: "images/caramel macchiato.jpg",
      description: "A delightful caramel macchiato.",
      brand: "Coffee House",
      size: "250ml",
      material: "Glass",
      category: "Black-based Coffee",
    },
    {
      id: "product4",
      name: "Flat White Coffee",
      price: 150,
      image: "images/flat white.jpg",
      description: "Smooth and velvety flat white.",
      brand: "Coffee House",
      size: "250ml",
      material: "Glass",
      category: "Black-based Coffee",
    },
    {
      id: "product5",
      name: "Affogato Coffee",
      price: 150,
      image: "images/affogato.jpg",
      description: "Espresso poured over ice cream.",
      brand: "Coffee House",
      size: "250ml",
      material: "Glass",
      category: "Black-based Coffee",
    },
    // Add more products as needed
  ];
</script>

<div
  data-scroll-container 
  class="flex flex-col pt-20 px-24 max-sm:px-5 h-screen relative"
>
  <!-- DIV FOR HEADER TEXTS -->
  <div class="w-[50%] max-sm:w-[100%] max-sm:text-center text-white border-black border--accent">
    <h1 class="text-8xl font-bold mb-4 border-black">
      Comfy Bean 
    </h1>

    <p class="text-2xl font-bold mb-4 border-black">
      Where stories are shared and friendships bloom. Comfy Bean isn't just a coffee shop it's your home away from home.
    </p>
  </div>

  <!-- DIV FOR CALL TO ACTION BUTTONS -->
  <div   
    class="ml-20 mt-20 max-sm:ml-0 max-sm:mt-10 flex gap-5 max-sm:justify-center "
  >
    <a href="/project2/shop" class="text-white p-5 text-2xl max-sm:text-lg font-bold rounded-xl bg-red-500 shadow-md">
      <h1>Shop Now!</h1>
    </a>

    <a href="/project2/contact" class="text-black p-5 text-2xl max-sm:text-lg font-bold rounded-xl bg-white shadow-md">
      <h1>Contact Us!</h1>
    </a>
  </div>

  <!-- DIV FOR MASCOT -->
  <div class="max-sm:hidden absolute -right-20 -top-8 w-[55%]">
    <img src="assets/lol.png" alt="" />
  </div>

  <!-- DIV FOR BACKGROUND SQUARE -->
  <div   class="element">
    <img  src="assets/real.jpg" alt="" />
  </div>

  <!-- Popular Products Section -->
  <div class="heading">
    <h2>Popular Products</h2>
  </div>
  <div class="products-container">
    {#each products as product}
      <div class="box">
        <img src={product.image} alt={product.name} />
        <h3>{product.brand}</h3>
        <p class="content">{product.name}</p>
        <p class="price">₱{product.price}</p>
      </div>
    {/each}
  </div>
  </div>

<style>
  .element{
    position: absolute;
    z-index: -1;
    top: 0px;
}

.heading {
  text-align: center;
  margin-top: 2rem;
}

.heading h2 {
  font-size: 1.8rem;
    text-transform: uppercase;
    top: 19vh;
    position: relative;
}

.products-container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 1.5rem;
  margin-top: 2rem;
}

.products-container .box {
  position: relative;
    top: 13rem;
    padding: 21px;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: space-between;
    height: 350px;
    background-color: #f9f9f9;
    border: 1px solid #e0e0e0;
    border-radius: 0.5rem;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    transition: transform 0.3s ease;
    width: 90%;
    padding-bottom: 36px;
}

.products-container .box:hover {
  transform: translateY(-5px); /* Lift on hover */
}

.products-container img {
  width: 100%;
  height: 150px;
  object-fit: cover;
  border-radius: 0.5rem;
  margin-bottom: 10px;
}

.products-container .box h3 {
  font-size: 1rem;
  font-weight: bold;
  margin-bottom: 5px;
}

.products-container .box .content {
  font-size: 0.9rem;
  color: #555;
  text-align: center;
}

.products-container .box .price {
  font-size: 1.2rem;
  font-weight: 700;
  color: #333;
  margin-top: 10px;
}

.flex {
  padding-bottom: 10rem; /* Adjust the value as needed */
}
</style>
