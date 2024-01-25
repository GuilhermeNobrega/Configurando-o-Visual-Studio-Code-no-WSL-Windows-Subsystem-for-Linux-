# Configurando o Visual Studio Code no WSL (Windows Subsystem for Linux) 💻

Este tutorial demonstra como configurar o Visual Studio Code (VS Code) para ser executado no Windows Subsystem for Linux (WSL) e criar um link simbólico para facilitar o acesso ao VS Code a partir do terminal.

## Pré-requisitos 🛠️

- Ter o WSL instalado no seu sistema Windows.
- Ter o Visual Studio Code instalado no WSL.
- Instalar a extensão no VS Code: "WSL".

## Passo 1: Criar um Link Simbólico 🚀

1. Abra o terminal do WSL.

2. Crie um link simbólico para o executável do VS Code no diretório `/usr/local/bin/`. Substitua `seu_nome_de_usuário` pelo seu nome de usuário real.

    ```bash
    sudo ln -s /mnt/c/Users/seu_nome_de_usuário/AppData/Local/Programs/Microsoft\ VS\ Code/bin/code /usr/local/bin/code
    ```

3. **Remover outros links simbólicos existentes:**
   Execute o seguinte comando para remover links simbólicos existentes relacionados ao VS Code. Substitua `/mnt/c/Users/nome_user_path/AppData/Local/Programs/cursor/resources/app/bin/code` pelo caminho real no seu sistema.

    ```bash
    sudo rm /mnt/c/Users/nome_user_path/AppData/Local/Programs/cursor/resources/app/bin/code
    ```

## Passo 2: Verificar o Link Simbólico ✔️

1. Verifique se o link simbólico foi criado corretamente.

    ```bash
    ls -l /usr/local/bin/code
    ```

    Deverá exibir algo como:

    ```bash
    lrwxrwxrwx 1 root root 68 Jan 25 12:11 /usr/local/bin/code -> '/mnt/c/Users/seu_nome_de_usuário/AppData/Local/Programs/Microsoft VS Code/bin/code'
    ```

    Se não houver esse caminho, substitua pelo fornecido no passo 1.

2. **Verifique outros links simbólicos relacionados ao `code`:**
   Execute o seguinte comando para listar todos os links simbólicos existentes.

    ```bash
    which -a code
    ```

    Certifique-se de que o caminho correto foi definido.

## Passo 3: Testar o VS Code ▶️

1. Execute o comando `code` para iniciar o Visual Studio Code.

    ```bash
    code
    ```

    ou

    ```bash
    code .
    ```

2. Certifique-se de que o Visual Studio Code é iniciado corretamente.

## Passo 4: Uso Prático 🚀

1. Agora você pode usar o comando `code .` para abrir o VS Code no diretório atual.

    ```bash
    code .
    ```

## Resolvendo o Erro "No such file or directory" ou "unable to determine app path from symlink vscode" ❌

O erro "No such file or directory" indica que o sistema não consegue encontrar o arquivo ou diretório especificado. Caso isso aconteça, siga os passos abaixo:

### Remover o Link Simbólico Existente:

```bash
sudo rm /usr/local/bin/code

```
### Atualizar o Cache do Bash

```bash
hash -r

