<script>
    import { page } from '$app/stores';
  
    $: title = $page.data.title ?? 'App de Tarefas';
  </script>
  
  <nav class="navbar bg-primary text-white px-4">
    <h1>{title}</h1>
  </nav>
  
  <slot />
  