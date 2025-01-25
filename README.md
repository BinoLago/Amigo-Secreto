<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <title>Amigo Secreto</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 20px;
    }
    input, button {
      margin: 5px 0;
      padding: 10px;
    }
    ul {
      list-style-type: none;
      padding: 0;
    }
    li {
      margin: 5px 0;
    }
  </style>
</head>
<body>
  <h1>Amigo Secreto</h1>
  
  <input type="text" id="nomeAmigo" placeholder="Nome do amigo">
  <button onclick="adicionarAmigo()">Adicionar</button>
  
  <h2>Lista de Amigos</h2>
  <ul id="listaAmigos"></ul>
  
  <button onclick="sortearAmigo()">Sortear Amigo</button>
  
  <h2 id="resultadoSorteio"></h2>
  
  <script>
    let amigos = [];
    
    function adicionarAmigo() {
      const input = document.querySelector('#nomeAmigo');
      const nome = input.value.trim();
      
      if (nome === '') {
        alert('Por favor, insira um nome.');
        return;
      }
      
      amigos.push(nome);
      input.value = ''; // Limpa o campo de entrada
      atualizarLista();
    }
    
    function atualizarLista() {
      const lista = document.querySelector('#listaAmigos');
      lista.innerHTML = ''; // Limpa a lista existente
      
      amigos.forEach(amigo => {
        const li = document.createElement('li');
        li.textContent = amigo;
        lista.appendChild(li);
      });
    }
    
    function sortearAmigo() {
      if (amigos.length === 0) {
        alert('A lista de amigos está vazia!');
        return;
      }
      
      const indiceAleatorio = Math.floor(Math.random() * amigos.length);
      const amigoSorteado = amigos[indiceAleatorio];
      document.querySelector('#resultadoSorteio').textContent = `Amigo secreto: ${amigoSorteado}`;
    }
  </script>
</body>
</html>


