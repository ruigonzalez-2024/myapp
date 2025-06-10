<script>
  import '../app.css';
</script>

<div class="min-h-screen bg-gray-50">
  <header class="bg-white shadow">
    <nav class="container mx-auto px-4 py-4">
      <div class="flex justify-between items-center">
        <a href="/" class="text-2xl font-bold text-gray-800">KRMA</a>
        <div class="space-x-4">
          <a href="/recipes" class="text-gray-600 hover:text-gray-900">Recipes</a>
          <a href="/create" class="text-gray-600 hover:text-gray-900">Create Recipe</a>
          <a href="/login" class="text-gray-600 hover:text-gray-900">Login</a>
        </div>
      </div>
    </nav>
  </header>

  <main class="container mx-auto px-4 py-8">
    <slot />
  </main>

  <footer class="bg-white shadow mt-8">
    <div class="container mx-auto px-4 py-6">
      <p class="text-center text-gray-600">© 2024 Kitchen Recipe Management Application</p>
    </div>
  </footer>
</div> 