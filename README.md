# Configuração do n8n com Evolution API

Este repositório contém a configuração do n8n com suporte para o nó da Evolution API.

## Recursos

- n8n atualizado para a versão mais recente
- Integração com Evolution API
- Configuração automática da rede Docker para comunicação entre serviços
- Instalação automática do nó Evolution API

## Requisitos

- Docker
- Docker Compose

## Instalação

1. Clone este repositório:
```bash
git clone https://github.com/marques823/n8n-setup.git
cd n8n-setup
```

2. Copie o arquivo `.env.example` para `.env` e configure as variáveis conforme necessário:
```bash
cp .env.example .env
```

3. Crie a rede Docker para comunicação com a Evolution API:
```bash
docker network create evolution-network
```

4. Execute o Docker Compose para iniciar os serviços:
```bash
docker-compose up -d
```

5. Conecte o contêiner da Evolution API à rede do n8n (se ainda não estiver conectado):
```bash
docker network connect evolution-network evolution_api
```

## Utilização do nó da Evolution API

Após a instalação, o nó da Evolution API estará disponível no n8n para utilização em seus workflows.

Para acessar o n8n, acesse `http://localhost:5678` ou o domínio configurado no arquivo `.env`.

## Solução de problemas

Se o nó da Evolution API não aparecer na interface do n8n:

1. Verifique se os contêineres estão em execução:
```bash
docker ps | grep n8n
```

2. Verifique os logs do n8n:
```bash
docker logs n8n-setup_n8n_1
```

3. Reinicie os contêineres:
```bash
docker-compose restart
```

4. Certifique-se de que o contêiner da Evolution API está na mesma rede:
```bash
docker network inspect evolution-network
```
