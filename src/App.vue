<template>
  <div class="bg-gray-100 min-h-screen p-8">
    <h1 class="text-4xl font-bold mb-6 text-center">Clothing Store</h1>
    <div class="mb-6 flex justify-center">
      <input 
        v-model="query" 
        @input="search" 
        type="text" 
        placeholder="Search for clothing..." 
        class="w-full p-4 pl-12 border border-gray-300 rounded-lg shadow-md bg-white text-gray-700 placeholder-gray-400 focus:outline-none focus:ring-2 focus:ring-blue-500 transition duration-300 ease-in-out"
           />
    </div>
    <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-4">
      <div 
        v-for="item in filteredItems" 
        :key="item.id" 
        class="bg-white p-4 rounded-lg shadow-md"
      >
        <img 
          :src="item.image" 
          alt="Item image" 
          class="w-full h-48 object-cover rounded-lg mb-2"
        />
        <h2 class="text-xl font-semibold">{{ item.name }}</h2>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      query: '',
      items: [
        { id: 1, name: 'T-Shirt', image: 'https://www.creativefabrica.com/wp-content/uploads/2021/10/02/Pixel-Art-TShirt-Graphics-18210223-1-1-580x387.jpg' },
        { id: 2, name: 'Jeans', image: 'https://www.creativefabrica.com/wp-content/uploads/2021/10/02/Pixel-Art-TShirt-Graphics-18210223-1-1-580x387.jpg' },
        { id: 3, name: 'Jacket', image: 'https://www.creativefabrica.com/wp-content/uploads/2021/10/02/Pixel-Art-TShirt-Graphics-18210223-1-1-580x387.jpg' }
        // Add more items as needed
      ],
      filteredItems: []
    };
  },
  methods: {
    search() {
      if (this.query.length > 3) {
        this.filteredItems = this.items.filter(item => 
          item.name.toLowerCase().includes(this.query.toLowerCase())
        );
      } else {
        this.filteredItems = [];
      }
    }
  },
  mounted() {
    this.filteredItems = this.items;
  }
};
</script>

<style>
/* Optional: Add custom styles here */
</style>
