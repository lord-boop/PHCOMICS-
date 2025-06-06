# PHCOMICS-<!DOCTYPE html>
<html lang="pt-BR" class="scroll-smooth">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>PHcomics - Índice dos Capítulos</title>
  <script src="https://cdn.tailwindcss.com"></script>
</head>
<body class="bg-gradient-to-r from-purple-900 via-pink-800 to-red-700 text-gray-100 min-h-screen flex flex-col">

  <header class="p-6 text-center bg-black bg-opacity-60 shadow-lg">
    <h1 class="text-4xl font-extrabold tracking-wide drop-shadow-lg">PHcomics</h1>
    <p class="mt-2 text-pink-400 font-semibold">Índice dos Capítulos</p>
  </header>

  <main class="flex-grow container mx-auto p-4 grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-6">
    <div id="listaCapitulos" class="w-full"></div>
  </main>

  <footer class="p-4 text-center text-sm text-pink-300 bg-black bg-opacity-60">
    &copy; PHcomics 2025 | Desenvolvido com ❤️ por você
  </footer>

  <script>
    const listaEl = document.getElementById('listaCapitulos');
    let capitulos = JSON.parse(localStorage.getItem('phcomics-capitulos') || '[]');

    if (capitulos.length === 0) {
      listaEl.innerHTML = '<p class="col-span-full text-center text-red-400 font-semibold">Nenhum capítulo disponível. Faça login no painel e crie um!</p>';
    } else {
      listaEl.innerHTML = '';
      capitulos.forEach(c => {
        const card = document.createElement('div');
        card.className = "bg-black bg-opacity-40 rounded-lg shadow-lg cursor-pointer hover:scale-105 transition-transform duration-300";
        card.innerHTML = `
          <img src="${c.capa}" alt="Capa do ${c.titulo}" class="w-full h-56 object-cover rounded-t-lg" />
          <h2 class="text-center p-3 font-semibold text-pink-300">${c.titulo}</h2>
        `;
        card.onclick = () => window.location.href = c.arquivo;
        listaEl.appendChild(card);
      });
    }
  </script>
</body>
</html>
