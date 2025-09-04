# Configuração do ERP Sankhya (Windows)

Após a instalação, realize as configurações iniciais para deixar o sistema pronto para uso.

## 1. Configurar variáveis de ambiente

- JAVA_HOME: já configurado durante a instalação do JDK.
- SANKHYA_HOME: crie e aponte para o diretório onde o Sankhya foi instalado, por exemplo `C:\Sankhya`.

Exemplo (PowerShell como Administrador):

setx /M SANKHYA_HOME "C:\\Sankhya"

## 2. Ajustar arquivos de configuração

Localize a pasta de configuração (ex.: `%SANKHYA_HOME%\\conf` ou `%SANKHYA_HOME%\\config`) e edite os arquivos principais:

- `application.properties` ou `sankhya.conf`: ajuste a URL do banco, usuário e senha.
- `server.xml` / `tomcat/conf/server.xml` (se o Sankhya rodar sobre Tomcat): ajuste a porta e conector HTTPS se necessário.

Dica: mantenha uma cópia de backup dos arquivos originais antes de editar.

## 3. Criar/atualizar o schema do banco

1. Execute os scripts SQL fornecidos pela Sankhya para criar tabelas e objetos necessários.
2. Se o fornecedor disponibilizar um script de patch, aplique-o conforme a ordem indicada.

Observação: recomenda-se executar esses scripts em ambiente de homologação primeiro.

## 4. Ajustes de rede e firewall

- Abra as portas usadas pelo application server (ex.: 8080/8443) no firewall do Windows.

Exemplo (PowerShell como Administrador):

New-NetFirewallRule -DisplayName "Sankhya HTTP" -Direction Inbound -LocalPort 8080 -Protocol TCP -Action Allow

## 5. Registrar e iniciar o serviço

Se o Sankhya incluir um instalador de serviço, use-o. Caso contrário, você pode criar um serviço Windows que execute o start script do servidor.

## 6. Testes e validação

- Acesse a URL do sistema no navegador.
- Efetue login com o usuário administrador fornecido.
- Verifique logs (`%SANKHYA_HOME%\\logs`) por erros.

## 7. Backups e manutenção

- Configure rotina de backup do banco de dados.
- Rotina de rotação de logs e monitoramento de disco.

## Próximos passos

- Após validar a instalação e configuração, proceda com a personalização do sistema e importação de dados (se aplicável).

