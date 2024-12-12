<script>
    let nombre = "";
    let apellido = "";
    let email = "";
    let telefono = "";
    let puesto = "";
  
    // Función para agregar un nuevo registro al JSON Server
    const agregarUsuario = async () => {
      if (nombre && apellido && email && telefono && puesto) {
        const usuario = { nombre, apellido, email, telefono, puesto };
  
        // Enviar datos al servidor
        await fetch("http://localhost:3000/usuarios", {
          method: "POST",
          headers: {
            "Content-Type": "application/json"
          },
          body: JSON.stringify(usuario)
        });
  
        // Limpiar los campos del formulario
        nombre = "";
        apellido = "";
        email = "";
        telefono = "";
        puesto = "";
      }
    };
  </script>
  
  <div class="form-container">
    <form on:submit|preventDefault={agregarUsuario}>
      <label>
        Nombre:
        <input type="text" bind:value={nombre} required />
      </label>
  
      <label>
        Apellido:
        <input type="text" bind:value={apellido} required />
      </label>
  
      <label>
        Email:
        <input type="email" bind:value={email} required />
      </label>
  
      <label>
        Teléfono:
        <input type="text" bind:value={telefono} required />
      </label>
  
      <label>
        Puesto:
        <input type="text" bind:value={puesto} required />
      </label>
  
      <button type="submit">Agregar</button>
    </form>
  </div>
  
  <style>
    .form-container {
      width: 100%;
      max-width: 400px;
      background-color: var(--bg-color);
      padding: 1em;
      border: 1px solid var(--border-color);
      border-radius: 8px;
      box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    }
  
    form {
      display: flex;
      flex-direction: column;
      gap: 1em;
    }
  
    label {
      display: flex;
      flex-direction: column;
      font-size: 1em;
      color: var(--text-color);
    }
  
    input {
      padding: 0.5em;
      border: 1px solid var(--border-color);
      border-radius: 4px;
      background-color: var(--input-bg-color);
      color: var(--text-color);
    }
  
    input:focus {
      outline: none;
      border-color: var(--button-bg-color);
    }
  
    button {
      padding: 0.75em;
      font-size: 1em;
      font-weight: bold;
      background-color: var(--button-bg-color);
      color: var(--button-text-color);
      border: none;
      border-radius: 4px;
      cursor: pointer;
    }
  
    button:hover {
      background-color: var(--button-hover-bg-color);
    }
  </style>