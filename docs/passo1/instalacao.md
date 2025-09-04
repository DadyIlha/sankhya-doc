# Instalação do ERP Sankhya (Windows)

Este guia descreve os passos mínimos para preparar e instalar o ERP Sankhya em uma máquina com Windows (10/11). Dependendo da versão do produto e da política da sua empresa, passos adicionais podem ser necessários.

## Requisitos mínimos

- Sistema operacional: Windows 10/11 (64-bit)
- CPU: 4 vCPUs
- Memória: 8 GB RAM (16 GB recomendado)
- Disco: 50 GB livres
- Java: JDK 11 ou JDK 17 (verificar compatibilidade da versão Sankhya)
- Banco de dados: Oracle ou PostgreSQL (conforme licenciamento)

Obs: ajuste os requisitos conforme a escala do ambiente (produção vs homologação/desenvolvimento).

## Pré-requisitos (passo a passo)

1. Instalar o Java JDK

    - Baixe o instalador do JDK (11 ou 17) do fornecedor escolhido (Adoptium, Oracle, etc.).
    - Execute o instalador e siga os passos.
    - Configure a variável de ambiente `JAVA_HOME` apontando para o diretório de instalação.
    - Adicione `%JAVA_HOME%\bin` ao `Path` do sistema.

    Exemplo (PowerShell como Administrador):

    setx /M JAVA_HOME "C:\\Program Files\\Eclipse Adoptium\\jdk-11.0.18.10-hotspot"
    $env:Path = [System.Environment]::GetEnvironmentVariable('Path', 'Machine') + ";%JAVA_HOME%\\bin"

2. Instalar o banco de dados

    - Instale e configure o banco conforme a escolha (Oracle ou PostgreSQL).
    - Crie o usuário e o schema necessários para a instância Sankhya. Consulte o DBA para parâmetros de performance.

3. Preparar rede e permissões

    - Verifique portas necessárias (HTTP/HTTPS, porta do banco, etc.).
    - Garanta permissões de leitura/escrita para o usuário que executará o serviço Sankhya.

## Instalação do aplicativo Sankhya

1. Obtenha os arquivos de instalação do fornecedor (pacote ZIP/instalador).
2. Descompacte ou execute o instalador em uma pasta apropriada (ex.: `C:\Sankhya`).
3. Edite os arquivos de configuração base (geralmente em `conf` ou `config`) para apontar para o banco de dados e ajustar caminhos.
4. Registre o serviço (se aplicável) ou crie um atalho para inicializar o servidor.

## Pós-instalação

- Verifique os logs iniciais na pasta `logs` do Sankhya.
- Acesse a aplicação via navegador apontando para o host/porta configurada.
- Valide a conexão com o banco de dados e o login inicial.

## Recursos e referências

- Consulte a documentação oficial fornecida pela Sankhya para scripts de criação de schema e pacotes específicos.

Agora vá para o [Configuração](./configuracao.md).
