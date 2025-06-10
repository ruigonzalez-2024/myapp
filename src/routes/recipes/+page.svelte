<script>
  // Mock data for recipes
  const recipes = [
    {
      id: 1,
      title: 'Classic Margherita Pizza',
      description: 'A simple yet delicious pizza with fresh tomatoes and mozzarella',
      prepTime: '30 mins',
      cookTime: '15 mins',
      rating: 4.5
    },
    {
      id: 2,
      title: 'Chocolate Chip Cookies',
      description: 'Soft and chewy cookies with chocolate chips',
      prepTime: '20 mins',
      cookTime: '12 mins',
      rating: 4.8
    },
    {
      id: 3,
      title: 'Chicken Stir Fry',
      description: 'Quick and healthy chicken stir fry with vegetables',
      prepTime: '15 mins',
      cookTime: '10 mins',
      rating: 4.2
    },
    {
      id: 4,
      title: 'Beef Tacos',
      description: 'Flavorful beef tacos with fresh toppings',
      prepTime: '25 mins',
      cookTime: '15 mins',
      rating: 4.6
    },
    {
      id: 5,
      title: 'Vegetable Pasta',
      description: 'Light and healthy pasta with seasonal vegetables',
      prepTime: '20 mins',
      cookTime: '15 mins',
      rating: 4.3
    },
    {
      id: 6,
      title: 'Apple Pie',
      description: 'Classic apple pie with a flaky crust',
      prepTime: '45 mins',
      cookTime: '60 mins',
      rating: 4.9
    }
  ];

  let searchQuery = '';
  let filteredRecipes = recipes;

  $: {
    filteredRecipes = recipes.filter(recipe =>
      recipe.title.toLowerCase().includes(searchQuery.toLowerCase()) ||
      recipe.description.toLowerCase().includes(searchQuery.toLowerCase())
    );
  }
</script>

<div class="space-y-6">
  <!-- Search and Filter Section -->
  <div class="flex justify-between items-center">
    <div class="flex-1 max-w-lg">
      <div class="relative">
        <input
          type="text"
          bind:value={searchQuery}
          placeholder="Search recipes..."
          class="block w-full rounded-md border-gray-300 shadow-sm focus:border-blue-500 focus:ring-blue-500 pl-10"
        />
        <div class="absolute inset-y-0 left-0 pl-3 flex items-center pointer-events-none">
          <svg class="h-5 w-5 text-gray-400" viewBox="0 0 20 20" fill="currentColor">
            <path fill-rule="evenodd" d="M8 4a4 4 0 100 8 4 4 0 000-8zM2 8a6 6 0 1110.89 3.476l4.817 4.817a1 1 0 01-1.414 1.414l-4.816-4.816A6 6 0 012 8z" clip-rule="evenodd" />
          </svg>
        </div>
      </div>
    </div>
    <a
      href="/create"
      class="inline-flex items-center px-4 py-2 border border-transparent text-sm font-medium rounded-md shadow-sm text-white bg-blue-600 hover:bg-blue-700"
    >
      Create Recipe
    </a>
  </div>

  <!-- Recipe Grid -->
  <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
    {#each filteredRecipes as recipe}
      <div class="bg-white rounded-lg shadow hover:shadow-lg transition">
        <div class="p-6">
          <div class="flex justify-between items-start">
            <h3 class="text-xl font-semibold text-gray-900 mb-2">{recipe.title}</h3>
            <div class="flex items-center">
              <svg class="h-5 w-5 text-yellow-400" viewBox="0 0 20 20" fill="currentColor">
                <path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z" />
              </svg>
              <span class="ml-1 text-sm text-gray-600">{recipe.rating}</span>
            </div>
          </div>
          <p class="text-gray-600 mb-4">{recipe.description}</p>
          <div class="flex justify-between text-sm text-gray-500">
            <span>Prep: {recipe.prepTime}</span>
            <span>Cook: {recipe.cookTime}</span>
          </div>
        </div>
        <div class="px-6 py-4 bg-gray-50 rounded-b-lg">
          <a
            href="/recipes/{recipe.id}"
            class="text-blue-600 hover:text-blue-800 font-medium"
          >
            View Recipe →
          </a>
        </div>
      </div>
    {/each}
  </div>

  <!-- Empty State -->
  {#if filteredRecipes.length === 0}
    <div class="text-center py-12">
      <svg class="mx-auto h-12 w-12 text-gray-400" fill="none" viewBox="0 0 24 24" stroke="currentColor">
        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9.172 16.172a4 4 0 015.656 0M9 10h.01M15 10h.01M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
      </svg>
      <h3 class="mt-2 text-sm font-medium text-gray-900">No recipes found</h3>
      <p class="mt-1 text-sm text-gray-500">Try adjusting your search or create a new recipe.</p>
    </div>
  {/if}
</div> 