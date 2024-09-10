+++
title = 'Script Boilerplate para Desenvolvimento Web'
date = 2024-09-10T14:58:36+02:00
draft = false
description = "Este script facilita a criação de todas as pastas e arquivos para iniciar um projeto de desenvolvimento web usando HTML, CSS, JavaScript."
image = "/images/terminal-bash.png"
imageBig = "/images/terminal-bash.png"
categories = ["Programação"]
authors = ["Higor Zica"]
avatar = "/images/avatar.webp"
+++


Você pode criar um script em shell para gerar o boiler plate de um projeto com HTML, CSS e JavaScript. Esse script pode criar as pastas e os arquivos básicos para o projeto. Aqui está um exemplo de script:


- Crie um arquivo chamado create_project.sh
- Insira o conteúdo abaixo para gerar um diretório contendo a estrutura padrão de pastas do seu projeto.


```bash
#!/bin/bash

# Verifica se o nome do projeto foi fornecido
if [ -z "$1" ]; then
  echo "Erro: Nenhum nome de projeto fornecido."
  echo "Uso: ./create_project.sh <nome-do-projeto>"
  exit 1
fi

# Nome do projeto
PROJECT_NAME=$1

# Cria o diretório do projeto
mkdir $PROJECT_NAME
cd $PROJECT_NAME

# Cria as pastas para o projeto
mkdir css js images

# Cria o arquivo index.html
cat <<EOL > index.html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>${PROJECT_NAME}</title>
    <link rel="stylesheet" href="css/style.css">
</head>
<body>
    <h1>Boilerplate de ${PROJECT_NAME}</h1>
    <script src="js/script.js"></script>
</body>
</html>
EOL

# Cria o arquivo style.css
cat <<EOL > css/style.css
/* CSS Boilerplate para ${PROJECT_NAME} */
body {
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
h1 {
    color: #333;
    text-align: center;
    margin-top: 50px;
}
EOL

# Cria o arquivo script.js
cat <<EOL > js/script.js
// JavaScript Boilerplate para ${PROJECT_NAME}
console.log("Projeto ${PROJECT_NAME} iniciado com sucesso!");
EOL

# Exibe mensagem de sucesso
echo "Projeto ${PROJECT_NAME} criado com sucesso!"

```


- Antes de utilizar seu script é necessário atribuir a permissão de execução do script para sistema:


```bash
chmod +x create_project.sh
```


- Por ultimo, e contudo o mais importante para gerar o script você deve escrever o seguinte comando no terminal Linux. Obs. : o ultimo parâmetro deve ser o nome do seu diretório onde será a pasta raiz do projeto.


```bash
./create_project.sh nome-projeto
```


## Caso você não utilize Linux ou Wsl e ainda esteja totalmente amarrado no Windows. Também existe uma solução usando o powershell mas com algumas diferenças.


- Crie um arquivo chamado create_project.ps1
- Insira o script abaixo para gerar um diretório contendo a estrutura padrão de pastas do seu projeto.
- Observe que existem algumas diferenças devido ao diferente sistema operacional.


```bash
# Verifica se o nome do projeto foi fornecido
if (-not $args[0]) {
    Write-Host "Erro: Nenhum nome de projeto fornecido."
    Write-Host "Uso: .\create_project.ps1 <nome-do-projeto>"
    exit
}

# Nome do projeto
$projectName = $args[0]

# Cria o diretório do projeto
New-Item -Path $projectName -ItemType Directory
Set-Location -Path $projectName

# Cria as pastas para o projeto
New-Item -Path "css" -ItemType Directory
New-Item -Path "js" -ItemType Directory
New-Item -Path "images" -ItemType Directory

# Cria o arquivo index.html
@"
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>$projectName</title>
    <link rel="stylesheet" href="css/style.css">
</head>
<body>
    <h1>Boilerplate de $projectName</h1>
    <script src="js/script.js"></script>
</body>
</html>
"@ > "index.html"

# Cria o arquivo style.css
@"
/* CSS Boilerplate para $projectName */
body {
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
h1 {
    color: #333;
    text-align: center;
    margin-top: 50px;
}
"@ > "css/style.css"

# Cria o arquivo script.js
@"
// JavaScript Boilerplate para $projectName
console.log('Projeto $projectName iniciado com sucesso!');
"@ > "js/script.js"

# Exibe mensagem de sucesso
Write-Host "Projeto $projectName criado com sucesso!"

```


- Em scripts do powershell não é necessário rodar o comando de permissão como no Linux.
- Você pode iniciar diretamente o comando como abaixo:


```bash
.\create_project.ps1 nome-projeto
```
