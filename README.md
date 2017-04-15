# tutorial-dockerapache

atualize o banco de dados de pacotes com 
####
> sudo apt-get update


instalando o Docker .É necessario adicionar ao sistema a chave GPG oficial do repositório do Docker:

>  sudo apt-key adv --keyserver hkp://p80.pool.sks-keyservers.net:80 --recv-keys 58118E89F3A912897C070ADBF76221572C52609D 

Adicione o repositório do Docker às fontes do APt

> sudo apt-add-repository 'deb https://apt.dockerproject.org/rep untu-xenial main'

Atualize o banco de dados de pacotes com os pacotes do Docker a partir do novo repositório adicionado

> sudo apt-get update

Certifique-se de que você está instalando a partir do repositório do Docker em vez do repositório padrão do Ubuntu 16.04:

> apt-cache policy docker-engine

Você deverá ver uma saída semelhante à seguinte:

> Output of apt-cache policy docker-engine
docker-engine:
  Installed: (none)
  Candidate: 1.11.1-0~xenial
  Version table:
     1.11.1-0~xenial 500
        500 https://apt.dockerproject.org/repo ubuntu-xenial/main amd64 Packages
     1.11.0-0~xenial 500
        500 https://apt.dockerproject.org/repo ubuntu-xenial/main amd64 Packages

Observe que o docker-engine não está instalado, mas o candidato para instalação é do repositório Docker do Ubuntu 16.04. O número da versão do docker-engine pode ser diferente.

Finalmente, instale o Docker:

> sudo apt-get install -y docker-engine

O Docker agora será instalado, o daemon iniciado, e o processo habilitado para iniciar no boot. Verifique que ele está executando:

> sudo systemctl status docker

##
utilize a imagem docker disponibilizada pelo usuario chicocx

> docker run -dit --name apache-app --publish=9081:80 chicocx/docker-apache

Para configurar externamente à imagem docker o local onde o apache salvará o site, utilize:


> docker run -dit --name apache-app --publish=9081:80 -v "$PWD":/usr/local/apache2/htdocs/ chicocx/docker-apache



