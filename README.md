<a href="https://github.com/AdaoG0n" style="pointer-events: none;"> <img src="https://github.com/AdaoG0n/AdaoG0n/blob/main/assests/Followbutton.png" width="130" align="right"/></a>

# <img src="https://img.shields.io/github/last-commit/AdaoG0n/Servidor_VNC?style=flat-square&color=%2312bab9" /> </a>


# Configuração de Servidor VNC no Ubuntu

Configurar um servidor VNC num sistema Ubuntu permite que se acesse a uma interface gráfica remota noutro computador. </br>
Isso pode ser útil se estiver trabalhando num servidor sem ambiente gráfico ou num ambiente sem acesso direto a uma GUI (Interface Gráfica do Usuário), </br>
mas quiser acessar a interface gráfica remotamente. </br>

</br>
Este guia detalha como configurar um servidor VNC no Ubuntu para acessar a interface gráfica remotamente. </br>
Ideal para servidores ou sistemas sem acesso direto a uma GUI.

---

## Sumário

1. [Passo 1: Instalar o Servidor VNC](#passo-1-instalar-o-servidor-vnc)  
2. [Passo 2: Configurar o Servidor VNC](#passo-2-configurar-o-servidor-vnc)  
3. [Passo 3: Configurar o Ambiente Gráfico](#passo-3-configurar-o-ambiente-gráfico)  
4. [Passo 4: Iniciar o Servidor VNC com o Ambiente Gráfico](#passo-4-iniciar-o-servidor-vnc-com-o-ambiente-gráfico)  
5. [Passo 5: Acessar o Servidor VNC Remotamente](#passo-5-acessar-o-servidor-vnc-remotamente)  
6. [Passo 6: Parar o Servidor VNC](#passo-6-parar-o-servidor-vnc)  
7. [Resumo dos Comandos Principais](#resumo-dos-comandos-principais)  

---

## Passo 1: Instalar o Servidor VNC

- **Instale o TigerVNC**  
  Atualize os pacotes e instale o servidor VNC:  
  ```
  sudo apt update  
  sudo apt install tigervnc-standalone-server tigervnc-common
  ```

- **Instale um Ambiente Gráfico** (caso não tenha)  
  Para instalar o XFCE (leve e recomendado):  
   ```
   sudo apt install xfce4 xfce4-goodies 
   ```
  Para instalar o GNOME (mais completo):  
    ```
    sudo apt install ubuntu-desktop  
    ```
---

## Passo 2: Configurar o Servidor VNC

1. **Defina uma senha para o VNC**  
   Execute:  
    ```
     vncpasswd
    ```  
   Escolha uma senha e, opcionalmente, configure uma senha de "somente leitura".  

3. **Inicie o Servidor VNC pela primeira vez**  
    ```
     vncserver
    ```  
   Após iniciar, você verá algo como:  
   New 'X' desktop is your-server:1  
   O número após o `:` indica a tela configurada.  

---

## Passo 3: Configurar o Ambiente Gráfico

1. **Crie ou edite o arquivo ~/.vnc/xstartup**  
    ```
     nano ~/.vnc/xstartup  
    ```

3. **Adicione o seguinte conteúdo**  
   Para XFCE:  
    ```bash
   #!/bin/sh  
   xrdb $HOME/.Xresources  
   startxfce4 &  
    ```

   Para GNOME:  
    ```bash
   #!/bin/sh  
   xrdb $HOME/.Xresources  
   gnome-session &  
    ```

4. **Torne o arquivo executável**  
    ```
    chmod +x ~/.vnc/xstartup  
    ```

---

## Passo 4: Iniciar o Servidor VNC com o Ambiente Gráfico

1. **Reinicie o Servidor VNC para aplicar as configurações**  
    ```
    vncserver -kill :1  
    vncserver :1  
    ```
---

## Passo 5: Acessar o Servidor VNC Remotamente

1. **Instale um cliente VNC no computador local**  
   Para Linux:  
    ```
     sudo apt install remmina  
    ```

   Para Windows: Baixe o `TightVNC` ou `RealVNC`.  

   Para macOS: Baixe o `TigerVNC` ou `RealVNC`.  

3. **Conecte-se ao Servidor VNC**  
   Abra o cliente VNC e insira o IP do servidor seguido pelo número da tela.  
   **Exemplo:** 192.168.1.100:1  

4. **Digite a senha configurada** e acesse o ambiente gráfico remoto.  

---

## Passo 6: Parar o Servidor VNC

Para parar o servidor, execute:  
    ```
     vncserver -kill :1  
    ```

---

## Resumo dos Comandos Principais

1. Instalar o servidor VNC:  
    ```
     sudo apt install tigervnc-standalone-server tigervnc-common  
    ```

2. Instalar o ambiente gráfico XFCE:  
    ```
     sudo apt install xfce4 xfce4-goodies  
    ```

3. Iniciar o servidor VNC:  
    ```
     vncserver  
    ```

4. Editar o arquivo xstartup:  
    ```
      nano ~/.vnc/xstartup  
    ```

5. Reiniciar o servidor VNC:  
    ```
     vncserver -kill :1  
     vncserver :1
    ```

![](https://github.com/AdaoG0n/AdaoG0n/blob/main/assests/bar.png)

![](https://github.com/AdaoG0n/AdaoG0n/blob/main/assests/animated%20gifs/madeby.gif)
