<script>
  let recipe = {
    title: '',
    description: '',
    prepTime: '',
    cookTime: '',
    servings: '',
    ingredients: [{ item: '', quantity: '' }],
    steps: ['']
  };

  function addIngredient() {
    recipe.ingredients = [...recipe.ingredients, { item: '', quantity: '' }];
  }

  function removeIngredient(index) {
    recipe.ingredients = recipe.ingredients.filter((_, i) => i !== index);
  }

  function addStep() {
    recipe.steps = [...recipe.steps, ''];
  }

  function removeStep(index) {
    recipe.steps = recipe.steps.filter((_, i) => i !== index);
  }

  function handleSubmit() {
    // TODO: Implement recipe submission
    console.log('Recipe submitted:', recipe);
  }
</script>

<div class="max-w-2xl mx-auto">
  <h1 class="text-3xl font-bold text-gray-900 mb-8">Create New Recipe</h1>

  <form on:submit|preventDefault={handleSubmit} class="space-y-6">
    <!-- Basic Information -->
    <div class="space-y-4">
      <div>
        <label for="title" class="block text-sm font-medium text-gray-700">Recipe Title</label>
        <input
          type="text"
          id="title"
          bind:value={recipe.title}
          class="mt-1 block w-full rounded-md border-gray-300 shadow-sm focus:border-blue-500 focus:ring-blue-500"
          required
        />
      </div>

      <div>
        <label for="description" class="block text-sm font-medium text-gray-700">Description</label>
        <textarea
          id="description"
          bind:value={recipe.description}
          rows="3"
          class="mt-1 block w-full rounded-md border-gray-300 shadow-sm focus:border-blue-500 focus:ring-blue-500"
          required
        ></textarea>
      </div>

      <div class="grid grid-cols-3 gap-4">
        <div>
          <label for="prepTime" class="block text-sm font-medium text-gray-700">Prep Time</label>
          <input
            type="text"
            id="prepTime"
            bind:value={recipe.prepTime}
            class="mt-1 block w-full rounded-md border-gray-300 shadow-sm focus:border-blue-500 focus:ring-blue-500"
            required
          />
        </div>
        <div>
          <label for="cookTime" class="block text-sm font-medium text-gray-700">Cook Time</label>
          <input
            type="text"
            id="cookTime"
            bind:value={recipe.cookTime}
            class="mt-1 block w-full rounded-md border-gray-300 shadow-sm focus:border-blue-500 focus:ring-blue-500"
            required
          />
        </div>
        <div>
          <label for="servings" class="block text-sm font-medium text-gray-700">Servings</label>
          <input
            type="text"
            id="servings"
            bind:value={recipe.servings}
            class="mt-1 block w-full rounded-md border-gray-300 shadow-sm focus:border-blue-500 focus:ring-blue-500"
            required
          />
        </div>
      </div>
    </div>

    <!-- Ingredients -->
    <div class="space-y-4">
      <div class="flex justify-between items-center">
        <h2 class="text-xl font-semibold text-gray-900">Ingredients</h2>
        <button
          type="button"
          on:click={addIngredient}
          class="inline-flex items-center px-3 py-1 border border-transparent text-sm font-medium rounded-md text-blue-700 bg-blue-100 hover:bg-blue-200"
        >
          Add Ingredient
        </button>
      </div>

      {#each recipe.ingredients as ingredient, i}
        <div class="flex gap-4 items-start">
          <div class="flex-1">
            <input
              type="text"
              bind:value={ingredient.quantity}
              placeholder="Quantity"
              class="block w-full rounded-md border-gray-300 shadow-sm focus:border-blue-500 focus:ring-blue-500"
            />
          </div>
          <div class="flex-[2]">
            <input
              type="text"
              bind:value={ingredient.item}
              placeholder="Ingredient"
              class="block w-full rounded-md border-gray-300 shadow-sm focus:border-blue-500 focus:ring-blue-500"
            />
          </div>
          {#if recipe.ingredients.length > 1}
            <button
              type="button"
              on:click={() => removeIngredient(i)}
              class="text-red-600 hover:text-red-800"
            >
              Remove
            </button>
          {/if}
        </div>
      {/each}
    </div>

    <!-- Steps -->
    <div class="space-y-4">
      <div class="flex justify-between items-center">
        <h2 class="text-xl font-semibold text-gray-900">Instructions</h2>
        <button
          type="button"
          on:click={addStep}
          class="inline-flex items-center px-3 py-1 border border-transparent text-sm font-medium rounded-md text-blue-700 bg-blue-100 hover:bg-blue-200"
        >
          Add Step
        </button>
      </div>

      {#each recipe.steps as step, i}
        <div class="flex gap-4 items-start">
          <div class="flex-1">
            <textarea
              bind:value={step}
              placeholder="Step {i + 1}"
              rows="2"
              class="block w-full rounded-md border-gray-300 shadow-sm focus:border-blue-500 focus:ring-blue-500"
            ></textarea>
          </div>
          {#if recipe.steps.length > 1}
            <button
              type="button"
              on:click={() => removeStep(i)}
              class="text-red-600 hover:text-red-800"
            >
              Remove
            </button>
          {/if}
        </div>
      {/each}
    </div>

    <!-- Submit Button -->
    <div class="flex justify-end">
      <button
        type="submit"
        class="inline-flex items-center px-4 py-2 border border-transparent text-sm font-medium rounded-md shadow-sm text-white bg-blue-600 hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-blue-500"
      >
        Create Recipe
      </button>
    </div>
  </form>
</div> 