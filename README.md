# 🌐 Projeto: Página Web – Homenagem à Rika-chan  

Este projeto faz parte do meu **laboratório de TI (homelab)**, onde aplico conceitos de redes, virtualização, automação e publicação de serviços na web.  
O objetivo aqui é consolidar conhecimentos em:  

- Estruturação de servidores e serviços em rede.  
- Exposição segura de aplicações via **Cloudflare Tunnel**.  
- Configuração de **Nginx** para servir páginas estáticas.  
- Controle de versão com **Git e GitHub**.  
- Criação de páginas estáticas com **HTML + CSS**.  

---

## 📌 Descrição
O site principal está publicado em:  
https://nz.services.net.br


Dentro dele, foi criada uma seção especial:  
https://nz.services.net.br/rika-chan


Essa página é uma homenagem à minha irmãzinha, com uma galeria de fotos de tulipas 🌷 (as flores favoritas dela).  
O layout foi inspirado em redes sociais como Pinterest/Instagram, mas simplificado, apenas para exibição de imagens em estilo “masonry grid”.

---

## 🛠️ Tecnologias utilizadas
- **Proxmox VE** – Hypervisor para execução das VMs e containers.  
- **Linux (Ubuntu Server)** – Sistema operacional do container web.  
- **Nginx** – Servidor web para servir páginas estáticas.  
- **Cloudflare Tunnel** – Exposição segura do serviço web sem necessidade de IP público.  
- **Git & GitHub** – Versionamento e controle do código-fonte.  
- **HTML + CSS puro** – Criação do site estático responsivo.  

---

## 📂 Estrutura do Projeto
```bash
meu-site/
│
├── index.html          # Página principal
├── rika-chan/          # Subpágina de homenagem
│   ├── index.html
│   └── img/            # Fotos utilizadas
│       ├── flor1.jpg
│       ├── flor2.jpg
│       └── ...
└── README.md
```
Como rodar no Nginx

Clonar o repositório no servidor:
```bash
git clone https://github.com/seu-usuario/meu-site.git /var/www/meu-site
```

Criar o arquivo de configuração do site:
```
sudo nano /etc/nginx/sites-available/meu-site
```

Exemplo de configuração:
```
server {
    listen 80;
    server_name nz.services.net.br;

    root /var/www/meu-site;
    index index.html;

    location / {
        try_files $uri $uri/ =404;
    }
}
```

Ativar e reiniciar o Nginx:
```
sudo ln -s /etc/nginx/sites-available/meu-site /etc/nginx/sites-enabled/
sudo systemctl restart nginx
```

O Cloudflare Tunnel já cuida da exposição do domínio.

🔒 Segurança

O site está atrás do Cloudflare Tunnel, evitando a exposição direta do servidor à internet.

Apenas os serviços necessários são publicados.
