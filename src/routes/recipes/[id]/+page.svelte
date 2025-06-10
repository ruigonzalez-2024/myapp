<script>
  import { page } from '$app/stores';

  // Mock data for a single recipe
  const recipe = {
    id: 1,
    title: 'Classic Margherita Pizza',
    description: 'A simple yet delicious pizza with fresh tomatoes and mozzarella',
    prepTime: '30 mins',
    cookTime: '15 mins',
    servings: '4',
    rating: 4.5,
    ingredients: [
      { quantity: '2 cups', item: 'all-purpose flour' },
      { quantity: '1 tsp', item: 'active dry yeast' },
      { quantity: '1 cup', item: 'warm water' },
      { quantity: '2 tbsp', item: 'olive oil' },
      { quantity: '4', item: 'fresh tomatoes' },
      { quantity: '8 oz', item: 'fresh mozzarella' },
      { quantity: '1/4 cup', item: 'fresh basil leaves' },
      { quantity: 'to taste', item: 'salt and pepper' }
    ],
    steps: [
      'Mix flour, yeast, and warm water to form a dough. Let it rise for 1 hour.',
      'Roll out the dough and place it on a baking sheet.',
      'Slice tomatoes and mozzarella.',
      'Layer tomatoes and mozzarella on the dough.',
      'Bake at 450°F for 15 minutes.',
      'Top with fresh basil and season with salt and pepper.'
    ]
  };
</script>

<div class="max-w-4xl mx-auto">
  <!-- Recipe Header -->
  <div class="bg-white rounded-lg shadow-lg overflow-hidden">
    <div class="p-8">
      <div class="flex justify-between items-start">
        <div>
          <h1 class="text-3xl font-bold text-gray-900 mb-2">{recipe.title}</h1>
          <p class="text-gray-600 text-lg mb-4">{recipe.description}</p>
        </div>
        <div class="flex items-center">
          <svg class="h-6 w-6 text-yellow-400" viewBox="0 0 20 20" fill="currentColor">
            <path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z" />
          </svg>
          <span class="ml-1 text-lg text-gray-600">{recipe.rating}</span>
        </div>
      </div>

      <!-- Recipe Meta -->
      <div class="grid grid-cols-4 gap-4 mt-6">
        <div class="text-center">
          <div class="text-sm text-gray-500">Prep Time</div>
          <div class="text-lg font-medium text-gray-900">{recipe.prepTime}</div>
        </div>
        <div class="text-center">
          <div class="text-sm text-gray-500">Cook Time</div>
          <div class="text-lg font-medium text-gray-900">{recipe.cookTime}</div>
        </div>
        <div class="text-center">
          <div class="text-sm text-gray-500">Servings</div>
          <div class="text-lg font-medium text-gray-900">{recipe.servings}</div>
        </div>
        <div class="text-center">
          <div class="text-sm text-gray-500">Difficulty</div>
          <div class="text-lg font-medium text-gray-900">Easy</div>
        </div>
      </div>
    </div>
  </div>

  <!-- Recipe Content -->
  <div class="mt-8 grid grid-cols-1 md:grid-cols-2 gap-8">
    <!-- Ingredients -->
    <div class="bg-white rounded-lg shadow p-6">
      <h2 class="text-2xl font-bold text-gray-900 mb-4">Ingredients</h2>
      <ul class="space-y-2">
        {#each recipe.ingredients as ingredient}
          <li class="flex items-start">
            <span class="text-gray-600 font-medium w-24">{ingredient.quantity}</span>
            <span class="text-gray-900">{ingredient.item}</span>
          </li>
        {/each}
      </ul>
    </div>

    <!-- Instructions -->
    <div class="bg-white rounded-lg shadow p-6">
      <h2 class="text-2xl font-bold text-gray-900 mb-4">Instructions</h2>
      <ol class="space-y-4">
        {#each recipe.steps as step, i}
          <li class="flex">
            <span class="flex-shrink-0 flex items-center justify-center w-8 h-8 rounded-full bg-blue-100 text-blue-600 font-medium">
              {i + 1}
            </span>
            <span class="ml-4 text-gray-700">{step}</span>
          </li>
        {/each}
      </ol>
    </div>
  </div>

  <!-- Actions -->
  <div class="mt-8 flex justify-end space-x-4">
    <button
      class="inline-flex items-center px-4 py-2 border border-gray-300 shadow-sm text-sm font-medium rounded-md text-gray-700 bg-white hover:bg-gray-50"
    >
      <svg class="h-5 w-5 mr-2" viewBox="0 0 20 20" fill="currentColor">
        <path d="M15 8a3 3 0 10-2.977-2.63l-4.94 2.47a3 3 0 100 4.319l4.94 2.47a3 3 0 10.895-1.789l-4.94-2.47a3.027 3.027 0 000-.74l4.94-2.47C13.456 7.68 14.19 8 15 8z" />
      </svg>
      Share
    </button>
    <button
      class="inline-flex items-center px-4 py-2 border border-transparent text-sm font-medium rounded-md shadow-sm text-white bg-blue-600 hover:bg-blue-700"
    >
      <svg class="h-5 w-5 mr-2" viewBox="0 0 20 20" fill="currentColor">
        <path d="M13.586 3.586a2 2 0 112.828 2.828l-.793.793-2.828-2.828.793-.793zM11.379 5.793L3 14.172V17h2.828l8.38-8.379-2.83-2.828z" />
      </svg>
      Edit Recipe
    </button>
  </div>
</div> 