<script>
    import { onMount } from "svelte";
  
    let usuarios = [];
  
    // Cargar datos desde el servidor al montar el componente
    onMount(async () => {
      const respuesta = await fetch("http://localhost:3000/usuarios");
      usuarios = await respuesta.json();
    });
  </script>
  
  <div class="table-container">
    <table>
      <thead>
        <tr>
          <th>Nombre</th>
          <th>Apellido</th>
          <th>Email</th>
          <th>Teléfono</th>
          <th>Puesto</th>
        </tr>
      </thead>
      <tbody>
        {#each usuarios as usuario}
          <tr>
            <td>{usuario.nombre}</td>
            <td>{usuario.apellido}</td>
            <td>{usuario.email}</td>
            <td>{usuario.telefono}</td>
            <td>{usuario.puesto}</td>
          </tr>
        {/each}
      </tbody>
    </table>
  </div>
  
  <style>
    .table-container {
      width: 100%;
      max-width: 800px;
      margin: auto;
      background-color: var(--bg-color);
      padding: 1em;
      border: 1px solid var(--border-color);
      border-radius: 8px;
      box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
      overflow-x: auto;
    }
  
    table {
      width: 100%;
      border-collapse: collapse;
      font-family: Arial, sans-serif;
      color: var(--text-color);
    }
  
    th, td {
      padding: 0.75em;
      border: 1px solid var(--border-color);
      text-align: left;
    }
  
    th {
      background-color: var(--header-bg-color);
      font-weight: bold;
    }
  
    tr:hover {
      background-color: var(--row-hover-bg-color);
    }
  </style>