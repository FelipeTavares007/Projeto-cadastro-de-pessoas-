## 📋 Projeto: Cadastro de Pessoas

Aplicação desktop desenvolvida em Python utilizando a biblioteca Tkinter para criar uma interface gráfica de cadastro e consulta de clientes. O projeto permite registrar informações pessoais, validar os dados inseridos, listar clientes cadastrados e realizar buscas pelo nome.

## 🚀 Funcionalidades
Cadastrar clientes: registra nome, telefone e e-mail.
Validar campos: verifica se todos os campos foram preenchidos corretamente.
Validar nome: exige pelo menos dois caracteres.
Validar telefone: aceita números com 10 ou 11 dígitos, incluindo o DDD.
Validar e-mail: verifica se o endereço informado segue um formato válido.
Evitar duplicidade: impede o cadastro de clientes com nomes já registrados, desconsiderando diferenças entre letras maiúsculas e minúsculas.
Listar clientes: exibe os clientes cadastrados em uma janela com barra de rolagem.
Buscar clientes: permite localizar clientes pelo nome, inclusive utilizando parte do nome.
Exibir mensagens: informa o sucesso do cadastro e apresenta alertas em caso de dados inválidos.
## 🛠️ Tecnologias utilizadas
Python 3 — linguagem de programação.
Tkinter — criação da interface gráfica.
Regular Expressions (re) — validação de e-mails e telefones.
Messagebox — exibição de mensagens e alertas para o usuário.
## 📂 Estrutura do projeto
Projeto-cadastro-de-pessoas/
├── cadastro.py
└── README.md

O arquivo cadastro.py é um exemplo de nome para o arquivo principal. Substitua-o pelo nome real do seu arquivo Python, caso seja diferente.
## ⚙️ Como executar o projeto
1. Pré-requisitos

Tenha o Python 3 instalado no computador.

Você pode baixá-lo no site oficial:

https://www.python.org/downloads/

O Tkinter geralmente já acompanha a instalação do Python. Em algumas distribuições Linux, pode ser necessário instalá-lo separadamente.

2. Clone o repositório

Abra o terminal e execute:

git clone https://github.com/SEU-USUARIO/Projeto-cadastro-de-pessoas-.git


Substitua SEU-USUARIO pelo seu nome de usuário do GitHub e ajuste o endereço caso o nome do repositório seja diferente.

3. Acesse a pasta do projeto
cd Projeto-cadastro-de-pessoas-

4. Execute a aplicação
python cadastro.py


Se necessário, utilize python3 cadastro.py no lugar do comando anterior.

## 🖥️ Como utilizar
Abra a aplicação.
Preencha os campos de nome, telefone e e-mail.
Clique em Adicionar Cliente para cadastrar uma pessoa.
Clique em Lista de Clientes para visualizar os cadastros realizados.
Clique em Procurar Clientes para pesquisar pessoas pelo nome.
Confira as mensagens exibidas pela aplicação para saber se a operação foi concluída ou se algum dado precisa ser corrigido.
## 📌 Observações
Os dados dos clientes são armazenados temporariamente em uma lista na memória.
Os cadastros são perdidos quando a aplicação é encerrada.
O projeto não utiliza banco de dados.
A validação de e-mail verifica o formato informado, mas não confirma se o endereço realmente existe.
## 🎯 Objetivo do projeto

Este projeto foi desenvolvido com o objetivo de praticar conceitos fundamentais de programação em Python, incluindo:

Criação de interfaces gráficas com Tkinter.
Manipulação de listas e dicionários.
Criação e utilização de funções.
Validação de dados.
Estruturas condicionais e de repetição.
Manipulação de eventos e interação com o usuário.
## 🔮 Melhorias futuras
Implementar armazenamento permanente utilizando SQLite.
Adicionar funcionalidades para editar e excluir clientes.
Permitir a busca por telefone e e-mail.
Melhorar o layout e a experiência visual da interface.
Exportar os dados cadastrados para arquivos CSV ou Excel.


⭐ Se este projeto foi útil para você, considere deixar uma estrela no repositório!
