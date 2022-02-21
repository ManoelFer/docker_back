<h2>Utilizando o Docker - API</h2>

Install Docker for Windows 10:
https://docs.docker.com/docker-for-windows/install/

Install Docker for Linux:
https://docs.docker.com/engine/install/

Install Docker for MacOS:
https://docs.docker.com/docker-for-mac/install/

Passo 1. Copie a pasta <b>DOCKER</b> para raiz do projeto

Passo 2. Faça uma cópia do arquivo <b>example.docker-compose.yml</b> e altere o nome para <b>docker-compose.yml</b>

Passo 3. Copie o arquivo <b>docker-compose.yml e .dockerignore </b> para a raiz do seu projeto

Passo 4. Adicione o <b>docker-compose.yml</b> no .gitignore

Passo 1. Trocar o <b>HOST </b> no .env para <b>0.0.0.0</b>

Passo 5. Criar uma network executando o comando <b> docker network create luby_projects </b>

Passo 6. Buildar a imagem (raiz):
<b>docker-compose up -d –-build  </b> (se com o --build falhar, execute sem ele)

Passo 7. Rodar migration e as seeds (Se necessário)
Essa imagem do docker está gerando um MYSQL, portanto, devemos conectar no host  criado para poder manipular o banco de dados.

<b>
DB_CONNECTION=mysql <br/>
DB_HOST=mysql <br/>
DB_PORT=3306 <br/>
DB_USER=root <br/>
DB_PASSWORD=root <br/>
DB_DATABASE=default <br/>
</b><br/>

<b>docker-compose exec api bash <br/> 
adonis migration:run <br/>
adonis seed <br/>
exit <br/></b>

Obs: Se retornar erro <b>"migration:run is not..."</b> rode os comandos: <br/>
<b>docker-compose exec api bash <br/>
npm install <br/>
exit <br/>
docker-compose exec api adonis migration:run <br/> </b>

Obs: Caso aconteça o erro abaixo descrito para instalação do Docker no windows 10, execute as seguintes etapas: <br/>
ERRO: System.InvalidOperationException: <br/>
Failed to set version to docker-desktop: exit code: -1 <br/>
 stdout: Não há suporte para a operação tentada para o tipo de objeto a que é feita referência. <br/>

stderr: em Docker.ApiServices.WSL2.WslShortLivedCommandResult.LogAndThrowIfUnexpectedExitCode...

1º Instale: www.proxifier.com/tmp/Test20200228/NoLsp.exe
2º Adicione o arquivo do download da etapa 1 na pasta system 32
3º Execute o PowerShell como Administrador.
4º Execute o comando: .\NoLsp.exe c:\windows\system32\wsl.exe

Observações: 

    • Toda vez que pegar um novo commit, execute
	docker-compose up -d –-build (se com o --build falhar, execute sem ele)

    • Essa imagem do docker está gerando um MYSQL, portanto, devemos conectar no host  criado para poder manipular o banco de dados.
      
      DB_CONNECTION=mysql
      DB_HOST=mysql 
      DB_PORT=3306
      DB_USER=root
      DB_PASSWORD=root
      DB_DATABASE=default
      
    • O arquivo docker-compose.yml não pode ir para o ambiente de homologação, por isso é necessário incluir ele no .gitignore
      
    • Instale a extensão do Docker no VS Studio para ter uma interface
    • Para listar os containers em execução: docker ps 
    • Para parar uma container: docker stop [id_container]
    • Para exibir o log do container: docker logs [id_container]
