<script>
  // Mock user data
  const user = {
    name: 'John Doe',
    email: 'john@example.com',
    joinDate: 'January 2024',
    recipes: [
      {
        id: 1,
        title: 'Classic Margherita Pizza',
        createdAt: '2024-01-15',
        rating: 4.5
      },
      {
        id: 2,
        title: 'Chocolate Chip Cookies',
        createdAt: '2024-01-20',
        rating: 4.8
      }
    ]
  };

  let isEditing = false;
  let editedName = user.name;
  let editedEmail = user.email;

  function handleSave() {
    // TODO: Implement profile update logic
    console.log('Profile update:', { name: editedName, email: editedEmail });
    isEditing = false;
  }
</script>

<div class="max-w-4xl mx-auto">
  <!-- Profile Header -->
  <div class="bg-white rounded-lg shadow-lg overflow-hidden">
    <div class="p-8">
      <div class="flex justify-between items-start">
        <div>
          <h1 class="text-3xl font-bold text-gray-900 mb-2">Profile</h1>
          <p class="text-gray-600">Member since {user.joinDate}</p>
        </div>
        <button
          on:click={() => isEditing = !isEditing}
          class="inline-flex items-center px-4 py-2 border border-gray-300 shadow-sm text-sm font-medium rounded-md text-gray-700 bg-white hover:bg-gray-50"
        >
          {isEditing ? 'Cancel' : 'Edit Profile'}
        </button>
      </div>
    </div>
  </div>

  <!-- Profile Content -->
  <div class="mt-8 grid grid-cols-1 md:grid-cols-3 gap-8">
    <!-- User Information -->
    <div class="md:col-span-2">
      <div class="bg-white rounded-lg shadow p-6">
        <h2 class="text-xl font-semibold text-gray-900 mb-4">Personal Information</h2>
        
        {#if isEditing}
          <form on:submit|preventDefault={handleSave} class="space-y-4">
            <div>
              <label for="name" class="block text-sm font-medium text-gray-700">Name</label>
              <input
                type="text"
                id="name"
                bind:value={editedName}
                class="mt-1 block w-full rounded-md border-gray-300 shadow-sm focus:border-blue-500 focus:ring-blue-500"
              />
            </div>
            <div>
              <label for="email" class="block text-sm font-medium text-gray-700">Email</label>
              <input
                type="email"
                id="email"
                bind:value={editedEmail}
                class="mt-1 block w-full rounded-md border-gray-300 shadow-sm focus:border-blue-500 focus:ring-blue-500"
              />
            </div>
            <div class="flex justify-end">
              <button
                type="submit"
                class="inline-flex items-center px-4 py-2 border border-transparent text-sm font-medium rounded-md shadow-sm text-white bg-blue-600 hover:bg-blue-700"
              >
                Save Changes
              </button>
            </div>
          </form>
        {:else}
          <dl class="space-y-4">
            <div>
              <dt class="text-sm font-medium text-gray-500">Name</dt>
              <dd class="mt-1 text-sm text-gray-900">{user.name}</dd>
            </div>
            <div>
              <dt class="text-sm font-medium text-gray-500">Email</dt>
              <dd class="mt-1 text-sm text-gray-900">{user.email}</dd>
            </div>
          </dl>
        {/if}
      </div>

      <!-- User's Recipes -->
      <div class="mt-8 bg-white rounded-lg shadow p-6">
        <h2 class="text-xl font-semibold text-gray-900 mb-4">My Recipes</h2>
        <div class="space-y-4">
          {#each user.recipes as recipe}
            <div class="flex justify-between items-center p-4 bg-gray-50 rounded-lg">
              <div>
                <h3 class="text-lg font-medium text-gray-900">{recipe.title}</h3>
                <p class="text-sm text-gray-500">Created on {recipe.createdAt}</p>
              </div>
              <div class="flex items-center">
                <svg class="h-5 w-5 text-yellow-400" viewBox="0 0 20 20" fill="currentColor">
                  <path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z" />
                </svg>
                <span class="ml-1 text-sm text-gray-600">{recipe.rating}</span>
              </div>
            </div>
          {/each}
        </div>
      </div>
    </div>

    <!-- Settings Sidebar -->
    <div class="space-y-8">
      <!-- Account Settings -->
      <div class="bg-white rounded-lg shadow p-6">
        <h2 class="text-xl font-semibold text-gray-900 mb-4">Account Settings</h2>
        <div class="space-y-4">
          <a
            href="/change-password"
            class="block text-blue-600 hover:text-blue-800"
          >
            Change Password
          </a>
          <a
            href="/notifications"
            class="block text-blue-600 hover:text-blue-800"
          >
            Notification Settings
          </a>
          <button
            class="block text-red-600 hover:text-red-800"
          >
            Delete Account
          </button>
        </div>
      </div>

      <!-- Statistics -->
      <div class="bg-white rounded-lg shadow p-6">
        <h2 class="text-xl font-semibold text-gray-900 mb-4">Statistics</h2>
        <dl class="space-y-4">
          <div>
            <dt class="text-sm font-medium text-gray-500">Total Recipes</dt>
            <dd class="mt-1 text-2xl font-semibold text-gray-900">{user.recipes.length}</dd>
          </div>
          <div>
            <dt class="text-sm font-medium text-gray-500">Average Rating</dt>
            <dd class="mt-1 text-2xl font-semibold text-gray-900">
              {(user.recipes.reduce((acc, recipe) => acc + recipe.rating, 0) / user.recipes.length).toFixed(1)}
            </dd>
          </div>
        </dl>
      </div>
    </div>
  </div>
</div> 