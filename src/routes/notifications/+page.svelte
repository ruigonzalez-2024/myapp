<script>
  // Mock notification settings
  let settings = {
    emailNotifications: {
      newRecipes: true,
      recipeComments: true,
      recipeRatings: true,
      weeklyDigest: false
    },
    pushNotifications: {
      newRecipes: true,
      recipeComments: true,
      recipeRatings: false
    }
  };

  let success = false;

  function handleSubmit() {
    // TODO: Implement notification settings update logic
    console.log('Notification settings update:', settings);
    success = true;
    setTimeout(() => {
      success = false;
    }, 3000);
  }
</script>

<div class="max-w-4xl mx-auto">
  <div class="bg-white rounded-lg shadow-lg overflow-hidden">
    <div class="p-8">
      <div class="flex justify-between items-start">
        <div>
          <h1 class="text-3xl font-bold text-gray-900 mb-2">Notification Settings</h1>
          <p class="text-gray-600">Manage how you receive notifications</p>
        </div>
      </div>
    </div>
  </div>

  <div class="mt-8">
    <form on:submit|preventDefault={handleSubmit}>
      <!-- Email Notifications -->
      <div class="bg-white rounded-lg shadow p-6 mb-8">
        <h2 class="text-xl font-semibold text-gray-900 mb-4">Email Notifications</h2>
        <div class="space-y-4">
          <div class="flex items-center justify-between">
            <div>
              <label for="new-recipes-email" class="text-sm font-medium text-gray-900">New Recipes</label>
              <p class="text-sm text-gray-500">Get notified when new recipes are added</p>
            </div>
            <div class="flex items-center">
              <input
                id="new-recipes-email"
                type="checkbox"
                bind:checked={settings.emailNotifications.newRecipes}
                class="h-4 w-4 text-blue-600 focus:ring-blue-500 border-gray-300 rounded"
              />
            </div>
          </div>

          <div class="flex items-center justify-between">
            <div>
              <label for="comments-email" class="text-sm font-medium text-gray-900">Recipe Comments</label>
              <p class="text-sm text-gray-500">Get notified when someone comments on your recipes</p>
            </div>
            <div class="flex items-center">
              <input
                id="comments-email"
                type="checkbox"
                bind:checked={settings.emailNotifications.recipeComments}
                class="h-4 w-4 text-blue-600 focus:ring-blue-500 border-gray-300 rounded"
              />
            </div>
          </div>

          <div class="flex items-center justify-between">
            <div>
              <label for="ratings-email" class="text-sm font-medium text-gray-900">Recipe Ratings</label>
              <p class="text-sm text-gray-500">Get notified when someone rates your recipes</p>
            </div>
            <div class="flex items-center">
              <input
                id="ratings-email"
                type="checkbox"
                bind:checked={settings.emailNotifications.recipeRatings}
                class="h-4 w-4 text-blue-600 focus:ring-blue-500 border-gray-300 rounded"
              />
            </div>
          </div>

          <div class="flex items-center justify-between">
            <div>
              <label for="weekly-digest" class="text-sm font-medium text-gray-900">Weekly Digest</label>
              <p class="text-sm text-gray-500">Receive a weekly summary of activity</p>
            </div>
            <div class="flex items-center">
              <input
                id="weekly-digest"
                type="checkbox"
                bind:checked={settings.emailNotifications.weeklyDigest}
                class="h-4 w-4 text-blue-600 focus:ring-blue-500 border-gray-300 rounded"
              />
            </div>
          </div>
        </div>
      </div>

      <!-- Push Notifications -->
      <div class="bg-white rounded-lg shadow p-6 mb-8">
        <h2 class="text-xl font-semibold text-gray-900 mb-4">Push Notifications</h2>
        <div class="space-y-4">
          <div class="flex items-center justify-between">
            <div>
              <label for="new-recipes-push" class="text-sm font-medium text-gray-900">New Recipes</label>
              <p class="text-sm text-gray-500">Get notified when new recipes are added</p>
            </div>
            <div class="flex items-center">
              <input
                id="new-recipes-push"
                type="checkbox"
                bind:checked={settings.pushNotifications.newRecipes}
                class="h-4 w-4 text-blue-600 focus:ring-blue-500 border-gray-300 rounded"
              />
            </div>
          </div>

          <div class="flex items-center justify-between">
            <div>
              <label for="comments-push" class="text-sm font-medium text-gray-900">Recipe Comments</label>
              <p class="text-sm text-gray-500">Get notified when someone comments on your recipes</p>
            </div>
            <div class="flex items-center">
              <input
                id="comments-push"
                type="checkbox"
                bind:checked={settings.pushNotifications.recipeComments}
                class="h-4 w-4 text-blue-600 focus:ring-blue-500 border-gray-300 rounded"
              />
            </div>
          </div>

          <div class="flex items-center justify-between">
            <div>
              <label for="ratings-push" class="text-sm font-medium text-gray-900">Recipe Ratings</label>
              <p class="text-sm text-gray-500">Get notified when someone rates your recipes</p>
            </div>
            <div class="flex items-center">
              <input
                id="ratings-push"
                type="checkbox"
                bind:checked={settings.pushNotifications.recipeRatings}
                class="h-4 w-4 text-blue-600 focus:ring-blue-500 border-gray-300 rounded"
              />
            </div>
          </div>
        </div>
      </div>

      <!-- Success Message -->
      {#if success}
        <div class="rounded-md bg-green-50 p-4 mb-8">
          <div class="flex">
            <div class="flex-shrink-0">
              <svg class="h-5 w-5 text-green-400" viewBox="0 0 20 20" fill="currentColor">
                <path fill-rule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zm3.707-9.293a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z" clip-rule="evenodd" />
              </svg>
            </div>
            <div class="ml-3">
              <p class="text-sm text-green-700">
                Notification settings updated successfully.
              </p>
            </div>
          </div>
        </div>
      {/if}

      <!-- Actions -->
      <div class="flex justify-end space-x-4">
        <a
          href="/profile"
          class="inline-flex items-center px-4 py-2 border border-gray-300 shadow-sm text-sm font-medium rounded-md text-gray-700 bg-white hover:bg-gray-50"
        >
          Cancel
        </a>
        <button
          type="submit"
          class="inline-flex items-center px-4 py-2 border border-transparent text-sm font-medium rounded-md shadow-sm text-white bg-blue-600 hover:bg-blue-700"
        >
          Save Changes
        </button>
      </div>
    </form>
  </div>
</div> 