<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>LEDEX \| Loja Oficial</title>
  <style>
    body { margin:0; font-family: 'Arial Black', Arial, sans-serif; background:#f5f5f5; }
    header { background:#111; color:#fff; padding:15px; text-align:center; }
    nav a { color:#fff; margin:0 10px; text-decoration:none; }
    .container { padding:20px; }
    .products { display:grid; grid-template-columns:repeat(auto-fit,minmax(220px,1fr)); gap:20px; }
    .card { background:#fff; padding:15px; border-radius:0; box-shadow:none; border:1px solid #e5e5e5; }
    .card img { width:100%; border-radius:8px; }
    .card h3 { margin:10px 0 5px; }
    .card button { background:#000; color:#fff; border:none; padding:12px; width:100%; font-weight:bold; letter-spacing:1px; cursor:pointer; }
    .card button:hover { background:#055fc2; }
    footer { background:#111; color:#fff; text-align:center; padding:15px; margin-top:30px; }
    .cart { position:fixed; right:20px; bottom:20px; background:#0a7cff; color:#fff; padding:15px; border-radius:50%; cursor:pointer; }
  </style>
</head>
<body>

<header style="background:#000; padding:20px;">
  <h1 style="font-size:48px; letter-spacing:2px; font-weight:900;">LEDEX</h1>
  <p style="font-size:14px; opacity:.8; margin-top:-10px;">JUST MOVE FORWARD</p>
  <nav style="margin-top:10px;">
    <a href="#" style="text-transform:uppercase; font-size:14px;">Início</a>
    <a href="#produtos" style="text-transform:uppercase; font-size:14px;">Produtos</a>
    <a href="#contato" style="text-transform:uppercase; font-size:14px;">Contato</a>
  </nav>
</header>

<div class="container" id="produtos">
  <h2 style="text-transform:uppercase; letter-spacing:2px;">Produtos LEDEX</h2>
  <div class="products">
    <div class="card" onclick="openProduct('Tênis LEDEX Run', 399.9)">
      <img src="https://via.placeholder.com/400" />
      <h3>Tênis LEDEX Run</h3>
      <p>R$ 399,90</p>
      <button>Ver produto</button>
    </div>
    <div class="card" onclick="openProduct('Camiseta LEDEX Pro', 129.9)">
      <img src="https://via.placeholder.com/400" />
      <h3>Camiseta LEDEX Pro</h3>
      <p>R$ 129,90</p>
      <button>Ver produto</button>
    </div>
  </div>
</div>

<!-- Página do Produto -->
<div class="container" id="produto-detalhe" style="display:none;">
  <button onclick="closeProduct()" style="margin-bottom:20px;">← Voltar</button>
  <div style="display:grid; grid-template-columns:1fr 1fr; gap:30px;">
    <img id="produto-img" src="https://via.placeholder.com/500" style="width:100%;" />
    <div>
      <h2 id="produto-nome"></h2>
      <p id="produto-preco" style="font-size:24px; font-weight:bold;"></p>
      <p>Produto premium LEDEX, desenvolvido para performance máxima.</p>
      <label>Tamanho</label><br>
      <select style="padding:10px; margin:10px 0;">
        <option>38</option><option>39</option><option>40</option><option>41</option><option>42</option>
      </select><br>
      <button onclick="addToCart(produtoAtual, precoAtual)" style="padding:15px; background:#000; color:#fff; width:100%;">Adicionar ao carrinho</button>
    </div>
  </div>
</div>
    <div class="card">
      <img src="https://via.placeholder.com/300" />
      <h3>Produto 2</h3>
      <p>R$ 149,90</p>
      <button onclick="addToCart('Produto 2', 149.9)">Adicionar ao carrinho</button>
    </div>
  </div>
</div>

<footer id="contato">
  <p>Contato: contato@sualoja.com</p>
</footer>

<div class="cart" onclick="checkout()">🛒</div>

<script>
  let cart = [];

  function addToCart(name, price) {
    cart.push({ name, price });
    alert(name + ' adicionado ao carrinho');
  }

  let produtoAtual = '';
  let precoAtual = 0;

  function openProduct(nome, preco) {
    produtoAtual = nome;
    precoAtual = preco;
    document.getElementById('produto-nome').innerText = nome;
    document.getElementById('produto-preco').innerText = 'R$ ' + preco.toFixed(2);
    document.getElementById('produtos').style.display = 'none';
    document.getElementById('produto-detalhe').style.display = 'block';
  }

  function closeProduct() {
    document.getElementById('produto-detalhe').style.display = 'none';
    document.getElementById('produtos').style.display = 'block';
  }

  function checkout() {
    if(cart.length === 0) {
      alert('Carrinho vazio');
      return;
    }

    let total = cart.reduce((s,p)=>s+p.price,0).toFixed(2);

    document.body.innerHTML += `
    <div id="checkout" style="position:fixed;top:0;left:0;width:100%;height:100%;background:#fff;z-index:9999;padding:30px;overflow:auto;">
      <h1>Checkout LEDEX</h1>

      <p>Total a pagar: <strong>R$ ${total}</strong></p>

      <h3>Pagamento via PIX</h3>

      <p>Chave PIX:</p>
      <div style="background:#f5f5f5;padding:15px;font-weight:bold;">
        luizfreitas098h@gmail.com
      </div>

      <p style="margin-top:10px;">Copie a chave acima e pague no app do seu banco.</p>

      <button onclick="alert('Após pagar o PIX, envie o comprovante para confirmação do pedido.')"
        style="margin-top:20px;padding:15px;width:100%;background:#000;color:#fff;">
        Já paguei
      </button>

      <p style="margin-top:20px;font-size:12px;opacity:.7;">
        Pagamento via PIX manual. Confirmação feita pelo vendedor.
      </p>
    </div>`;
  }

    let total = cart.reduce((s,p)=>s+p.price,0).toFixed(2);
    alert('Total: R$ ' + total + '\n\nIntegração com pagamento (Mercado Pago / Pix / Cartão) deve ser feita no backend.');
  }
</script>

</body>
</html>

