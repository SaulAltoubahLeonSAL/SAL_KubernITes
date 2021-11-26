# Comandos de ejecución y archivos de configuración - proyecto "Infraestructura integrada en Kubernetes"

## En este archivo README.md se mostrarán las capturas y los archivos de depliegue (_deployments_) y creación de los pods de **_Kubernetes_**

<br />

### - SAL_kubernITes instalado

![server_sal_kubernITes](/capturas/01_sal_kubernITes_instalado.JPG)

<br />

### - Instalación del asistente **_tasksel_** para instalar el escritorio de Ubuntu

```bash

sudo apt install tasksel -y

```

![tasksel](/capturas/02_instalacion_tasksel.JPG)

<br />

### - Selección de parámetros Tasksel

```bash

sudo tasksel

```

![parametros_tasksel](/capturas/03_seleccion_parametros_tasksel.JPG)

### - Escritorio gráfico Ubuntu instalado

![ubuntu_gui](/capturas/04_escritorio_grafico_ubuntu_instalado.JPG)

<br />

### - Instalación del entorno de escritorio "Cinnamon"

```bash

sudo apt install cinnamon-desktop-environment -y

```

![cinnamon_instalacion](/capturas/05_instalacion_escritorio_cinnamon.JPG)

<br />

### - Escritorio "Cinnamon" instalado

![cinnamon_gui](/capturas/06_escritorio_cinnamon_instalado.JPG)

<br />

### - Instalación de paquetes de requisitos previos para poder descargar mediante HTTPS

```bash

sudo apt install apt-transport-https ca-certificates curl software-properties-common -y

```

![packages_https](/capturas/07_instalacion_paquetes_requisitos_previos_https.JPG)

<br />

### - Adición clave GPG del repositorio oficial de Docker

```bash

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

```

![gpg_key](/capturas/08_adicion_clave_gpg_docker.JPG)

<br />

### - Adición repositorio oficial de Docker a las fuentes APT

```bash

sudo add-apt-repository "deb[arch=amd64] https://download.docker.com/linux/ubuntu focal stable"

```

![apt_docker](/capturas/09_adicion_repositorio_docker_apt.JPG)

<br />

### - Asegurar última versión de Docker

```bash

apt-cache policy docker-ce

```

![policy_docker](/capturas/10_asegurar_ultima_version_docker.JPG)

<br />

### - Instalación de Docker

```bash

sudo apt install docker-ce -y

```

![docker_install](/capturas/11_instalacion_docker.JPG)

<br />

### - Comprobación del **_daemon_** de Docker

```bash

sudo service docker status

```

![daemon_docker](/capturas/12_comprobacion_daemon_docker.JPG)

<br />

### - Agregación usuario al grupo de Docker

```bash

sudo usermod -aG docker ${USER}
su - ${USER}
id -nG

```

![user_docker_group](/capturas/13_agregacion_usuario_grupo_docker.JPG)

<br />

### - Comprobacioón funcionmiento comando Docker

```bash

docker

```

![docker](/capturas/14_comando_docker.JPG)

<br />

### - Descarga de los paquetes de Minikube

```bash

curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64

```

![packages_minikube](/capturas/15_descarga_paquetes_minikube.JPG)

<br />

### - Instalacion Minikube

```bash

sudo install minikube-linux-amd64 /usr/local/bin/minikube

```

![minikube_instalacion](/capturas/16_instalacion_minikube.JPG)

<br />

### - Inicio Minikube

```bash

minikube start

```

![minikube_start](/capturas/17_inicio_minikube.JPG)

<br />

### - Creación alias para kubectl

```bash

vim ~/.bashrc
"añadir en la última línea del archivo" -> alias kubectl="minikube kubectl --"
source ~/.bashrc

```

![alias_kubectl](/capturas/18_alias_kubectl.JPG)

<br />

### - Mostrar todos los **_namespaces_** de Minikube

```bash

kubectl get all -Ao wide

```

![kubectl_ns](/capturas/19_kubectl_get_ns.JPG)

<br />

### - Lista de addons de Minikube

```bash

minikube addons list

```

![minikube_addons_list](/capturas/20_lista_addons_minikube.JPG)

<br />

### - Habilitar addons: métricas Kubernetes Dashboard, Helm Tiller, Ingress

```bash

minikube addons enable metrics-server
minikube addons enable helm-tiller
minikube addons enable ingress-dns

```

![enable_minikube_addons](/capturas/21_activar_addons_minikube.JPG)

<br />

### - Acceder al Dashboard de Kubernetes

```bash

minikube dashboard

```

![kubernetes_dashboard](/capturas/22_kubernetes_dashboard.JPG)

<br />

### - Dashboard de Kubernetes GUI

![kubernetes_dashboard_gui](/capturas/23_kubernetes_dashboard_gui.JPG)
