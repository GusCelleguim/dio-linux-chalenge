### Resolução do Desafio

**Descrição do Projeto:**

Neste projeto, iremos desenvolver um script em bash para automação de tarefas relacionadas à criação de usuários, grupos de usuários, diretórios e configuração de permissões em um ambiente Linux. O script será versionado e armazenado em um repositório no GitHub para facilitar sua reutilização em futuras implantações de máquinas virtuais.

**Passo a Passo:**

1. **Configuração do Ambiente:**
   - Certifique-se de ter um sistema Linux operacional.
   - Instale o Git no seu sistema, se ainda não estiver instalado.

2. **Criação do Repositório no GitHub:**
   - Acesse o GitHub e crie um novo repositório chamado `infraestrutura-linux-automacao`.
   - Clone o repositório para sua máquina local usando o comando:
     ```sh
     git clone https://github.com/seu-usuario/infraestrutura-linux-automacao.git
     ```

3. **Desenvolvimento do Script:**
   - Dentro do diretório clonado, crie um arquivo chamado `setup_infraestrutura.sh`.
   - Adicione o conteúdo do script conforme abaixo:

```sh
#!/bin/bash

# Criando grupos
groupadd GRP_ADM
groupadd GRP_VEN
groupadd GRP_SEC

# Criando usuários e adicionando aos grupos
useradd carlos -m -s /bin/bash -p $(openssl passwd -crypt Senha123) -G GRP_ADM
useradd maria -m -s /bin/bash -p $(openssl passwd -crypt Senha123) -G GRP_ADM
useradd joao -m -s /bin/bash -p $(openssl passwd -crypt Senha123) -G GRP_ADM

useradd debora -m -s /bin/bash -p $(openssl passwd -crypt Senha123) -G GRP_VEN
useradd sebastiana -m -s /bin/bash -p $(openssl passwd -crypt Senha123) -G GRP_VEN
useradd roberto -m -s /bin/bash -p $(openssl passwd -crypt Senha123) -G GRP_VEN

useradd josefina -m -s /bin/bash -p $(openssl passwd -crypt Senha123) -G GRP_SEC
useradd amanda -m -s /bin/bash -p $(openssl passwd -crypt Senha123) -G GRP_SEC
useradd rogerio -m -s /bin/bash -p $(openssl passwd -crypt Senha123) -G GRP_SEC

# Criando diretórios
mkdir /publico
mkdir /adm
mkdir /ven
mkdir /sec

# Definindo permissões dos diretórios
chown root:GRP_ADM /adm
chown root:GRP_VEN /ven
chown root:GRP_SEC /sec

chmod 770 /adm
chmod 770 /ven
chmod 770 /sec
chmod 777 /publico

echo "Configuração da infraestrutura concluída!"
```

4. **Tornando o Script Executável:**
   - No terminal, navegue até o diretório do script e torne-o executável com o comando:
     ```sh
     chmod +x setup_infraestrutura.sh
     ```

5. **Executando o Script:**
   - Execute o script para testar sua funcionalidade:
     ```sh
     sudo ./setup_infraestrutura.sh
     ```

6. **Versionando o Script:**
   - Adicione e commite o script ao repositório Git:
     ```sh
     git add setup_infraestrutura.sh
     git commit -m "Adicionando script de configuração de infraestrutura"
     ```

7. **Subindo para o GitHub:**
   - Faça o push das alterações para o repositório remoto:
     ```sh
     git push origin main
     ```

### Considerações Finais

Ao seguir esses passos, você terá um script funcional que automatiza a configuração de infraestrutura em sistemas Linux. Este script pode ser reutilizado para configurar novas máquinas virtuais rapidamente, garantindo consistência e economia de tempo em implantações futuras.

O repositório GitHub pode ser acessado [aqui](https://github.com/seu-usuario/infraestrutura-linux-automacao) (substitua "seu-usuario" pelo seu nome de usuário no GitHub).