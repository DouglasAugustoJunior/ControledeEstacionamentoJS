#[Douglas Augusto](http://github.com/DouglasAugustoJunior)- Outros projetos. # 
 
 
![VERSÃO DO SW](https://img.shields.io/badge/Version-1.0-blue.svg)
 
![LINGUAGEM FINALIDADE](https://img.shields.io/badge/javascript-system-orange.svg)
 
O **Controle de estacionamento** é um projeto simples que utilizei para praticar meus conhecimentos em JS. **[Projeto Online](https://douglasaugustojunior.github.io/ControledeEstacionamentoJS/)**

![Imagem](https://github.com/DouglasAugustoJunior/ControledeEstacionamentoJS/blob/master/images/Tela.PNG?raw=true)


 
Desenvolvido em HTML5,CSS3,Bootstrap e JS, ele traz diversas situações interessantes para utilizar diversos recursos.
 
## Cadastro de veículos
 

    function cadastra(){
    var modelo = document.getElementById('modelo').value; // pega o modelo digitado
    var placa = document.getElementById('placa').value; // pega a placa digitada
    var time = new Date(); //horário
    carro ={
        modelo:modelo,
        placa:placa,
        hora:time.getHours(),
        min:time.getMinutes()
        }
    
    if (!modelo || !placa){ // se algum dos campos está vazio
        alert('Preencha todos os campos para adicionar!');
        return false; // impede o processo continue
    }
    
    if (localStorage.getItem('patio') == null){ // se o patio estiver vazio
        var carros = [];
        carros.push(carro); // adiciona carro ao array
        localStorage.setItem('patio',JSON.stringify(carros)); // converte array de carros em um string para armazenar
    }else{
        carros = JSON.parse(localStorage.getItem('patio')); // json.parse converte o string em json
        carros.push(carro); // adiciona carro ao array
        localStorage.setItem('patio',JSON.stringify(carros)); // converte array de carros em um string para armazenar
    }
    document.getElementById('formulario').reset(); // limpa formulário após cadastrar
    }

 

 
##Apagar veículos
 

    function apagar(placa){
    var carros = JSON.parse(localStorage.getItem('patio')); // pega carros registrados
    for (var i=0;i<carros.length;i++){
        if (carros[i].placa == placa){ // verifica se o a placa bate com a placa fornecida no parametro
            carros.splice(i,1); // apaga um registro a partir da posição i
            localStorage.setItem('patio',JSON.stringify(carros));//insere itens devolta no localstorage
            mostraregistro();// atualiza lista
        }
    }


 
## Mostrar registros
 
    function mostraregistro(){
    var carros = JSON.parse(localStorage.getItem('patio'));
    var carrosresultados = document.getElementById('resultados');
    carrosresultados.innerHTML = ''; // insere um texto no html
    
    for (var i=0; i<carros.length;i++){ // percorre todos os registros
        var modelo = carros[i].modelo;
        var placa = carros[i].placa;
        var hora = carros[i].hora;
        var min = carros[i].min;
        carrosresultados.innerHTML += '<tr><td>'+modelo
            +'</td><td>'+placa
            +'</td><td>'+hora
            +':'+min
            +'</td><td><button class="btn btn-danger" onclick="apagar(\''+placa
            +'\')">Excluir</button></td></tr>'; //cria linha na tabela 
    }

Para mais informações acesse [meus repositórios](http://github.com/DouglasAugustoJunior).
