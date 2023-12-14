# SFTP com Gerenciamento Web usando Webmin

Este Dockerfile cria um contêiner Docker baseado no Ubuntu que fornece um servidor SFTP com gerenciamento web usando Webmin. Ele é configurado para permitir o acesso SFTP e inclui o Webmin para facilitar a administração do sistema.

## Como usar

### Pré-requisitos
- [Docker](https://www.docker.com/) instalado na sua máquina.

### Construir a imagem Docker

```bash
docker build -t nome-da-imagem:tag .
```

### Executar o contêiner

```bash
docker run -p 2222:22 -p 10000:10000 -v /caminho/para/seu/diretorio:/home nome-da-imagem:tag
```

Substitua `/caminho/para/seu/diretorio` pelo caminho no seu sistema de arquivos onde deseja armazenar os dados do contêiner.

### Acesso ao Webmin

Após executar o contêiner, você pode acessar o Webmin através do navegador:

```
https://seu_endereco_ip:10000/
```

- Nome de usuário: `root`
- Senha: `password`

Certifique-se de substituir `seu_endereco_ip` pelo endereço IP da máquina onde o contêiner está sendo executado.

### Acesso SFTP

Use um cliente SFTP para conectar-se ao servidor SFTP no endereço:

```
sftp://seu_endereco_ip:2222/
```

- Nome de usuário: `root`
- Senha: `password`

Certifique-se de substituir `seu_endereco_ip` pelo endereço IP da máquina onde o contêiner está sendo executado.

## Configurações Adicionais

- O Webmin está configurado para usar HTTP padrão. Considere a configuração adicional para HTTPS em um ambiente de produção.
- A senha para o usuário root e outras configurações podem ser personalizadas no Dockerfile.

## Observações

- Este ambiente é configurado para fins de teste. Em um ambiente de produção, certifique-se de tomar medidas de segurança adicionais, como configurar SSL para o Webmin e configurar usuários e senhas robustas.
