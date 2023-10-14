<!-- Menu.svelte -->
<script>
  let menuSections = [
    {
      title: "Desayunos",
      items: [
        {
          name: "Desayuno Continental",
          description: "Variedad de panes y bollería con café o té.",
          price: "$9.99",
          image: "/images/desayuno-continental.png"
        },
        {
          name: "Huevos Revueltos",
          description: "Huevos revueltos con jamón, queso y tostadas.",
          price: "$12.99",
          image: "/images/huevos.png"
          
        },
        {
          name: "Hot-Cakes",
          description: "Hot-Cakes con lechera y mantequilla.",
          price: "$18.99",
          image: "/images/hot-cakes.png"
          
        }
      ]
    },
    {
      title: "Comidas",
      items: [
        {
          name: "Pasta Carbonara",
          description: "Fettuccine con salsa de huevo, queso, panceta y pimienta.",
          price: "$14.99",
          image: "/images/pasta-carbonara.png"
        },
        {
          name: "Pollo a la Parrilla",
          description: "Pechuga de pollo a la parrilla con verduras y patatas.",
          price: "$16.99",
          image: "/images/pollo-parrilla.png"
        },
        {
          name: "Salmón a la Sartén",
          description: "Filete de salmón fresco cocido a la sartén con una deliciosa salsa de limón.",
          price: "$18.99",
          image: "/images/salmon-sarten.png"
        }
      ]
    },
    {
      title: "Postres",
      items: [
        {
          name: "Tiramisú",
          description: "Un clásico postre italiano con capas de café, crema y bizcochos de soletilla.",
          price: "$8.99",
          image: "/images/tiramisu.png"
        },
        {
          name: "Helado de Chocolate",
          description: "Tres bolas de helado de chocolate con nueces y salsa de chocolate.",
          price: "$6.99",
          image: "/images/helado-chocolate.png"
        },
        {
          name: "Cheesecake de Fresa",
          description: "Cheesecake casero con salsa de fresa y una base de galleta crujiente.",
          price: "$10.99",
          image: "/images/cheesecake-fresa.png"
        }
      ]
    },
    {
      title: "Bebidas",
      items: [
        {
          name: "Café Espresso",
          description: "Café espresso recién preparado.",
          price: "$2.99",
          image: "/images/cafe-espresso.png"
        },
        {
          name: "Té de Hierbabuena",
          description: "Infusión de hierbabuena refrescante.",
          price: "$2.49",
          image: "/images/te-hierbabuena.png"
        },
        {
          name: "Limonada Fresca",
          description: "Limonada casera con rodajas de limón y hielo.",
          price: "$3.49",
          image: "/images/limonada-fresca.png"
        }
      ]
    }
  ];

  let currentPage = 0;

  function changePage(direction) {
    currentPage += direction;
    if (currentPage < 0) {
      currentPage = menuSections.length - 1;
    } else if (currentPage >= menuSections.length) {
      currentPage = 0;
    }
  }
</script>

<main style="max-width: 800px; margin: 0 auto; height: 100%;">
  {#if currentPage < menuSections.length}
    <h1 style="background-color: orange; padding: 10px;">{menuSections[currentPage].title}</h1>
    <table style="width: 100%; height: 100%;">
      <thead>
        <tr style="background-color: orange; color: white; text-align: center;">
          <th style="width: 25%;">Imagen</th>
          <th style="width: 25%;">Platillo</th>
          <th style="width: 25%;">Descripción</th>
          <th style="width: 25%;">Precio</th>
        </tr>
      </thead>
      <tbody>
        {#each menuSections[currentPage].items as item (item.name)}
          <tr>
            <td><img src={item.image} alt={item.name} style="max-width: 100px; max-height: 100px;" /></td>
            <td>{item.name}</td>
            <td>{item.description}</td>
            <td>{item.price}</td>
          </tr>
        {/each}
      </tbody>
    </table>
  {:else}
    <h1 style="background-color: orange; padding: 10px;">¡Fin del menú!</h1>
  {/if}

  <div class="navigation" style="text-align: center;">
    <button on:click={() => changePage(-1)}>Página Anterior</button>
    <button on:click={() => changePage(1)}>Página Siguiente</button>
  </div>
</main>

<style>
  table {
    border-collapse: collapse;
    height: 100%;
  }

  th, td {
    border: 1px solid #ddd;
    padding: 8px;
    text-align: left;
    height: 25%;
  }
</style>
