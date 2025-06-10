<script>
  // Mock data for featured recipes
  const featuredRecipes = [
    {
      id: 1,
      title: 'Classic Margherita Pizza',
      description: 'A simple yet delicious pizza with fresh tomatoes and mozzarella',
      prepTime: '30 mins',
      cookTime: '15 mins'
    },
    {
      id: 2,
      title: 'Chocolate Chip Cookies',
      description: 'Soft and chewy cookies with chocolate chips',
      prepTime: '20 mins',
      cookTime: '12 mins'
    },
    {
      id: 3,
      title: 'Chicken Stir Fry',
      description: 'Quick and healthy chicken stir fry with vegetables',
      prepTime: '15 mins',
      cookTime: '10 mins'
    }
  ];
</script>

<div class="space-y-12">
  <!-- Hero Section -->
  <section class="text-center py-16 bg-white rounded-lg shadow">
    <h1 class="text-4xl font-bold text-gray-900 mb-4">
      Welcome to KRMA
    </h1>
    <p class="text-xl text-gray-600 mb-8">
      Your one-stop solution for managing and sharing kitchen recipes
    </p>
    <div class="space-x-4">
      <a
        href="/recipes"
        class="inline-block bg-blue-600 text-white px-6 py-3 rounded-lg hover:bg-blue-700 transition"
      >
        Browse Recipes
      </a>
      <a
        href="/create"
        class="inline-block bg-gray-200 text-gray-800 px-6 py-3 rounded-lg hover:bg-gray-300 transition"
      >
        Create Recipe
      </a>
    </div>
  </section>

  <!-- Featured Recipes Section -->
  <section>
    <h2 class="text-2xl font-bold text-gray-900 mb-6">Featured Recipes</h2>
    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
      {#each featuredRecipes as recipe}
        <div class="bg-white rounded-lg shadow p-6 hover:shadow-lg transition">
          <h3 class="text-xl font-semibold text-gray-900 mb-2">{recipe.title}</h3>
          <p class="text-gray-600 mb-4">{recipe.description}</p>
          <div class="flex justify-between text-sm text-gray-500">
            <span>Prep: {recipe.prepTime}</span>
            <span>Cook: {recipe.cookTime}</span>
          </div>
        </div>
      {/each}
    </div>
  </section>
</div>
