# Albuquerque

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Pagina Inicial</title>
    <link href="https://fonts.googleapis.com/css2?family=Lato&display=swap" rel="stylesheet">
    <link rel="icon" href="bb.png">

    <style>

        *{
            font-family: 'Lato', sans-serif;
            margin:0;
            padding:0;
            box-sizing: border-box;
            background-color: black;
            
        }

        #produtos{
            max-width: 900px;
            margin:0 auto;
            padding:0 2%;
            display: flex;
            flex-wrap: wrap;
        }

        #carrinho{
            max-width: 900px;
            margin:0 auto;
            padding:0 2%;
            display: block;
            color: white;
        }

        .produto-single{
            width:32%;
            margin-right: 1%;
            border:1px solid white;
            margin-top:20px;
            margin-bottom:20px;
        }

        .produto-single img{
            max-width: 100%;
        }

        .produto-single p{
            text-align: center;
            font-size:16px;
            padding:10px;
            color: white;
        }

        .produto-single a{
            text-decoration: none;
            color: white;
            background-color: darkgreen;
            text-align: center;
            display: block;
            padding: 4px;
            font-size: 18px;
        }

        h1 {
            color: blanchedalmond;
        }

        h2 {
            background-color: green;
            padding:10px 0;
            text-align: center;
            color: white;
        }

        .info-single-checkout{
            border-bottom: 2px dotted;
            padding: 10px 0;
        }

        @media screen and (max-width: 768px){
            .produto-single{
                width: 100%;
                margin-right: 0;
            }
        }

    </style>
</head>
<body>
    <h1>Albuquerque</h1><br>
    <h2>Vitrine:</h2>
    <div id="produtos">
        
    </div>

    <h2>Carrinho:</h2>
    <div id="carrinho">
        
    </div>

    <script>
        const items = [
            {
                id: 0,
                nome: 'produto1',
                img: 'tde.jpg',
                quantidade: 0
            },
            {
                id: 1,
                nome: 'produto2',
                img: 'tde.jpg',
                quantidade: 0
            },
            {
                id: 2,
                nome: 'produto3',
                img: 'tde.jpg',
                quantidade: 0
            },

        ]

            inicializarLoja = () => {
                var  containerProdutos = document.getElementById('produtos');
                items.map((val)=>{
                    containerProdutos.innerHTML+= `

                    <div class="produto-single">
                        <img src="`+val.img+`" />
                        <p>`+val.nome+`</p>
                        <a key="`+val.id+`" href="#">Adicionar ao carrinho<a/>
                    </div>




                    `;
                })
            }

            inicializarLoja();

            atualizarCarrinho = () => {
                var  containerCarrinho = document.getElementById('carrinho');
                containerCarrinho.innerHTML = "";
                items.map((val)=>{
                     if(val.quantidade > 0){
                    containerCarrinho.innerHTML+= `
                    <div class="info-single-checkout">
                    <p style="float:left;">Produto: `+val.nome+`</p>
                    <p style="float:right;">Quantidade: `+val.quantidade+`</p>
                    <div style="clear:both"></div>
                    
                    </div>

                     
                    `;
                     }
                })
            }

            var links = document.getElementsByTagName('a');

            for(var i = 0; i < links.length; i++) {
                links[i].addEventListener("click",function(){
                    let key = this.getAttribute('key');
                    items[key].quantidade++;
                    atualizarCarrinho();
                    return false;
                })
            }



    </script>

</body>
</html>
