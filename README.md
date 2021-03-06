 # ASP NET CORE APPLICATION COM MÉTRICAS E PIPELINE COM JENKINS
Este repositório foi criado para demonstrar os estudos desenvolvidos utilizando as seguintes tecnologias:
- docker
- docker-compose
- prometheus
- grafana
- nginx
- jenkins
- .net 5.0

# Objetivo

O objetivo é ter o contato prático com todas as tecnologias citadas acima através do estudo de documentações originais, artigos da comunidade e vídeos no youtube.

# Como começar
Passo a passo para implantar este repositório em uma máquina Linux

1. Criar uma máquina virtual linux em um ambiente 
    * no meu caso criei na oracle cloud, usando o ambiente gratuito (always free)
2. Acessar a máquina linux com uma chave SSH
3. Clonar o repositório: ` git clone https://github.com/Vinaum8/aspnetcore-metrics-app.git `
4. acessar a pasta ` cd aspnetcore-metrics-app/container/ `
5. Criar as pastas para hospedar os volumes:
    * ` mkdir grafana `
    * ` mkdir jenkins `
    * ` mkdir jenkins/jenkins_home/ `
6. Dar permissões de acesso e escrita nas pastas criadas:
    * ` sudo chown -R :root prometheus/ nginx/ jenkins/ jenkins/jenkins_home/ grafana/ `
    * ` sudo chmod 777 -R jenkins/jenkins_home/ `
7. Instalar o Docker;
    * ` curl -fsSL https://get.docker.com -o get-docker.sh `
    * ` sudo sh get-docker.sh `
    * ` sudo usermod -aG docker your-user `
8. Baixar e instalar o docker-compose:     
    * ` sudo curl -L "https://github.com/docker/compose/releases/download/1.27.4/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose `
9. Dar permissão de execução ao binário baixado: 
    * ` sudo chmod +x /usr/local/bin/docker-compose `
10. Dar permissão de acesso ao socket daemon do Docker
    * ` sudo chmod 770 -R /var/run/ `
10. Iniciar a execução de todos os containers 
    * ` docker-compose up `

Obs: Para acessar os containers criados, precisamos acessar o NGINX (nosso ingress) na porta 80 e vamos necessitar definir os registros DNS em nossa máquina local para testes.

No meu caso, o IP Público aparece na interface da Oracle Cloud, então abri o arquivo /etc/hosts/ e adicionei alguns registros DNS para referenciar os **server_name** localizados no arquivo /container/nginx/nginx.conf deste repositório.

Adicionei as seguintes linhas no arquivo /etc/hosts:
* "IP" net-test.com
* "IP" grafana-test.com
* "IP" prometheus-test.com
* "IP" jenkins-test.com

Onde "IP", era o IP do HOST sem aspas