<script>
  import Form from "./Form.svelte";
  import Table from "./Table.svelte";
  import "./themes.css";

  let pantalla = "form"; 
  let darkMode = false; 

  const toggleTheme = () => {
    darkMode = !darkMode;

    document.documentElement.classList.toggle("dark-theme", darkMode);
  };
</script>

<div class="contenedor">
  <nav>
    <button on:click={() => pantalla = "form"}>Formulario</button>
    <button on:click={() => pantalla = "table"}>Tabla</button>
    <button on:click={toggleTheme}>
      {darkMode ? "Modo Claro" : "Modo Oscuro"}
    </button>
  </nav>

  <main>
    {#if pantalla === "form"}
      <Form />
    {:else if pantalla === "table"}
      <Table />
    {/if}
  </main>
</div>

<style>
  /* Contenedor principal */
  .contenedor {
    display: flex;
    flex-direction: column;
    height: 100vh;
    background-color: var(--bg-color);
    color: var(--text-color);
  }

  /* Navegación fija en la parte superior */
  nav {
    display: flex;
    justify-content: center;
    gap: 1em;
    padding: 1em;
    background-color: var(--header-bg-color);
    border-bottom: 1px solid var(--border-color);
    box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.1);
  }

  button {
    padding: 0.5em 1em;
    font-size: 1em;
    background-color: var(--button-bg-color);
    color: var(--button-text-color);
    border: none;
    border-radius: 4px;
    cursor: pointer;
  }

  button:hover {
    background-color: var(--button-hover-bg-color);
  }

  /* Área de contenido */
  main {
    flex: 1;
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 2em;
    transition: opacity 0.3s ease-in-out;
  }
</style>