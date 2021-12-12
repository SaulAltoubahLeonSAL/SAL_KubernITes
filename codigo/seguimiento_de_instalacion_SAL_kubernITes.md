# Comandos de ejecución y archivos de configuración - proyecto ASIR "Infraestructura IT integrada en Kubernetes"

## En este archivo .md se mostrarán las capturas y los archivos de depliegue (_deployments_) y creación de los pods de **_Kubernetes_**

<br />

## - Instalaciones previas:

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

sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"

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
"añadir en la última línea del archivo" -> alias kubectl="minikube kubectl -- "
source ~/.bashrc

```

![alias_kubectl](/capturas/18_alias_kubectl.JPG)

<br />

### - Instalación de _kubectl_ y muestra de todos los **_namespaces_** de Minikube

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

### - Habilitar addons: métricas Kubernetes Dashboard

```bash

minikube addons enable metrics-server # Para utilizar Kubernetes Dashboard

```

![enable_minikube_addons](/capturas/21_activar_addons_minikube.JPG)

<br />

## - Monitorización - Kubernetes Dashboard, Lens IDE (_Prometheus+Grafana_ necesarios) y Netdata

<br />

### - Acceder al Dashboard de Kubernetes

```bash

minikube dashboard

```

![kubernetes_dashboard](/capturas/22_kubernetes_dashboard.JPG)

<br />

### - Dashboard de Kubernetes GUI

![kubernetes_dashboard_gui](/capturas/23_kubernetes_dashboard_gui.JPG)

<br />

### - Descarga de Lens IDE
![lens_ide](/capturas/24_descarga_Lens_IDE.JPG)

<br />

### - Interfaz gráfica Lens IDE
![lens_ide_gui](/capturas/25_Lens_IDE_gui.JPG)

<br />

### - Instalación clave GPG y paquetes de Helm

```bash

curl https://baltocdn.com/helm/signing.asc | sudo apt-key add -

echo "deb https://baltocdn.com/helm/stable/debian/ all main" sudo tee /etc/apt/sources.list.d/helm-stable-debian.list

```

![GPGkey_packages_helm](/capturas/26_instalacion_GPGkey_paquetes_helm.JPG)

<br />

### - Instalación Helm

```bash

sudo apt install helm -y

```

![installation_helm](/capturas/27_instalacion_helm.JPG)

<br />

### - Comprobación de versión de Helm

```bash

helm version

```

![helm_version](/capturas/28_comprobacion_helm_version.JPG)

<br />

### - Instalación de Netdata usando _Helm Charts_

```bash

helm repo add netdata https://netdata.github.io/helmchart
helm install netdata netdata/netdata

```

![netdata_helm_chart](/capturas/29_instalacion_netdata_helm_chart.JPG)

<br />

### - Instalación de Netdata en el servidor SAL_kubernITes

```bash

bash <(curl -Ss https://my-netdata.io/kickstart.sh) --claim-token 9j7nx0c7y9Bo_kN3bD3FJcm36loPL9qbRSN0jvhCp7zRYvgAQAZenpEwBYnFWk1kycuftbuq3LDtC1RMt9Q5LA0SxpnaiN0wOmOGKfA1YKFrEXpq_12v1_sCVlgzA8aRum-T8vQ --claim-rooms 4edae1ee-695e-4e87-ba46-ba99bb467f12 --claim-url https://app.netdata.cloud

```

![netdata_host_sal_kubernITes](/capturas/30_sal_kubernITes_host_netdata.JPG)

<br />

### - Actualización de nodos en Netdata Cloud

![netdata_helm_chart](/capturas/31_pods_netdata.JPG)

<br />

### - Interfaz web Netdata Cloud

![netdata_cloud](/capturas/32_interfaz_web_netdata_cloud.JPG)

<br />

## - Seguridad - LinuxAudit, OpenVPN (Intento _fallido_ de pod, plan B en contendor Docker)

<br />

### - Instalación LinuxAudit

![linuxaudit](/capturas/33_descarga_LinuxAudit.JPG)

<br />

### - Ejecución LinuxAudit
(SE RECOMIENDA MIRAR EL ARCHIVO [_/codigo/logs/LinuxAudit.log_](/codigo/logs/LinuxAudit.log))

![linuxaudit](/capturas/34_ejecucion_linuxaudit.JPG)

<br />

### - Comprobación/Cambio permisos archivo _docker.service_

```bash
sudo systemctl status docker

ls -lisha /lib/systemd/system/docker.service

```

![docker_service](/capturas/35_comprobacion-cambio_permisos_archivo_docker-service.JPG)

<br />

### - Comprobación/Cambio permisos archivo _docker.socket_

```bash
sudo find /*/*/*/*/docker.socket

ls -lisha /usr/lib/systemd/system/docker.socket

```

![docker_socket](/capturas/36_comprobacion-cambio_permisos_archivo_docker-socket.JPG)

<br />

### - Comprobación/Cambio permisos archivo _/etc/default/docker_

```bash
ls -lisha /etc/default/docker

```

![etc-default-docker](/capturas/37_comprobacion-cambio_permisos_archivo_etc-default-docker.JPG)

<br />

### - Comprobación/Cambio permisos archivo _/etc/docker_

```bash
ls -lisha /etc/docker

```

![etc-docker](/capturas/38_comprobacion-cambio_permisos_archivo_etc-docker.JPG)

<br />

### - **_OPCIÓN A_**: POD OpenVPN Server
###   · Creación y conversión docker-compose.yaml a "_deployments_" en .yaml para servidor OpenVPN en Minikube

```yaml
version: "2"
services:
  openvpn:
    cap_add:
      - NET_ADMIN
    image: kylemanna/openvpn
    container_name: openvpn
    ports:
      - "1194:1194/udp"
    restart: always
    volumes:
      - ./openvpn-data/conf:/etc/openvpn

```

```bash
kompose convert -f docker-compose.yaml

```

![docker-compose-deployment-yaml-openvpn-server](/capturas/39_creacion_conversion_docker-compose-deployment-openvpn_server.JPG)

<br />

### - Aplicación de archivos _.yaml_ en Minikube

```bash
kubectl apply -f openvpn-claim0-persistenvolumeclaim.yaml

kubectl apply -f openvpn-deployment.yaml

kubectl apply -f openvpn-service.yaml

```

![aplicacion_yaml_minikube](/capturas/40_aplicacion_archivos_yaml_openvpn_minikube.JPG)

**(DESGRACIADAMENTE ESTA PARTE NO HA PODIDO FUNCIONAR. PASAMOS AL _PLAN B_: OpenVPN Server docker-compose)**

<br />

### - OPCIÓN B: _Docker Container OpenVPN Server_
###   · Preparación _docker-compose_ OpenVPN Server (I)

```bash
ifconfig ens32
cat /etc/hosts | grep "vpn"

```

![docker-compose_openvpn_server_I](/capturas/41_preparacion_docker-compose_openvpn_server_I.JPG)

<br />

### - Preparación _docker-compose_ OpenVPN Server (II - Configuración)

```bash
docker-compose run --rm openvpn ovpn_genconfig -u udp://VPN.SAL-KUBERNITES.LOCAL #localhost:1194

```

![docker-compose_openvpn_server_II](/capturas/42_preparacion_docker-compose_openvpn_server_II.JPG)

<br />

### - Preparación _docker-compose_ OpenVPN Server (III - _initpki_(1))

```bash
docker-compose run --rm openvpn ovpn_initpki

```

![docker-compose_openvpn_server_III](/capturas/43_preparacion_docker-compose_openvpn_server_III.JPG)

<br />

### - Preparación _docker-compose_ OpenVPN Server (IV - _initpki_(2))

![docker-compose_openvpn_server_IV](/capturas/44_preparacion_docker-compose_openvpn_server_IV.JPG)

<br />

### - Preparación _docker-compose_ OpenVPN Server (V - Compobación propiedad carpetas _openvpn-data_)

```bash
sudo chown $(whoami): ./openvpn-data
ls -l ./openvpn-data
sudo whoami

```

![docker-compose_openvpn_server_V](/capturas/45_preparacion_docker-compose_openvpn_server_V.JPG)

<br />

### - Ejecución y comporbación OpenVPN Server _docker-compose_)

```bash
docker-compose up -d openvpn
docker-compose logs -f
```

![docker-compose_openvpn_server_running](/capturas/46_docker-compose_openvpn_server_corriendo.JPG)

<br />

### - _docker-compose_ OpenVPN Server (Certificado cliente)

```bash
export CLIENTNAME="SAL_kITs"
docker-compose run --rm openvpn easyrsa build-client-full $CLIENTNAME

```

![docker-compose_openvpn_server_V](/capturas/47_docker-compose_openvpn_server_cert_cliente.JPG)

<br />

### - _docker-compose_ OpenVPN Server (_SAL_kITs.ovpn_)

```bash
docker-compose run --rm openvpn ovpn_getclient $CLIENTNAME > $CLIENTNAME.ovpn
# modificar el archivo y sustituir "localhost" por la IP del servidor

```

![docker-compose_openvpn_server_clientfile](/capturas/48_docker-compose_openvpn_server_clientfile.JPG)

<br />

### - RBAC (Role Based Access Control)
### - Creación clave privada de usuario

```bash
sudo mkdir cert && cd cert

sudo openssl genrsa --out sal.key 2048
```

![rbac_user_private_cert](/capturas/49_rbac_I.JPG)

<br />

### - Creación _request_ para certificado

```bash
sudo openssl req --new \
  --key sal.key \
  --out sal.csr \
  --subj "/CN=sal/O=salkubernites"
```

![rbac_user_req_cert](/capturas/50_rbac_II.JPG)

<br />

### - Creación certificado x.509 de usuario

```bash
# Revisamos que existen los certificado y la clave privada de Minikube (ca.crt, ca.key)
ls -lisha ~/.minikube/ca.*

sudo openssl x509 --req \
  --in sal.csr \
  --CA ~/.minikube/ca.crt \
  --CAkey ~/.minikube/ca.key \
  --CAcreateserial \
  --out sal.crt \
  --days 500
# Este certificado "sal.crt" será para el administrador del cluster de Kubernetes
```

![rbac_user_req_cert](/capturas/51_rbac_III.JPG)

<br />

### - Enlazado de certificado y clave privada y creación de contexto de usuario

```bash
kubectl config set-credentials sal \
  --client-certificate=sal.crt \
  --client-key=sal.key

kubectl config set-context sal-context \
  --cluster=minikube \
  --namespace=default \
  --user=sal
```

![rbac_user_req_cert](/capturas/52_rbac_IV.JPG)

<br />

### - Cambio de contexto de cluster

```bash
kubectl config use-context sal-context

kubectl config current-context
```

![rbac_user_req_cert](/capturas/53_rbac_V.JPG)

<br />

### - Comporbación de permisos en el cluster

```bash
kubectl create ns sal-ns # Prohibido

kubectl get pods # También prohibido
```
(Si hay problemas de permisos, ejecutar _```bash sudo chown ${USER}:${USER} sal.*```_)

![rbac_user_req_cert](/capturas/54_rbac_VI.JPG)

<br />

### - Despliegue de _Role & RoleBinding_ (Asignación de permisos)
```bash
kubectl config use-context minikube
```

```yaml
# role.yaml
kind: Role
apiVersion: rbac.authorization.k8s.io/v1
metadata:
  namespace: default
  name: pod-lector
rules:
- apiGroups: [""]
  resources: ["pods"]
  verbs: ["get", "watch", "list"]
# Este .yaml creará las acciones para permitir la lectura de pods disponibles en el cluster

---

# rolebinding.yaml
kind: RoleBinding
apiVersion: rbac.authorization.k8s.io/v1
metadata:
  name: read-pods
  namespace: default
subjects:
- kind: User
  name: sal
  apiGroup: rbac.authorization.k8s.io
roleRef:
  kind: Role
  name: pod-reader # *lector
  apiGroup: rbac.authorization.k8s.io
  # Este archivo .yaml enlazará el "role" de "pod-lector" junto con el usuario "sal"
```

```bash
kubectl apply -f role.yaml

kubectl apply -f rolebinding.yaml

kubectl get roles,rolebindings

# Para comprobar
kubectl use-context sal-context

kubectl get pods 
```

![rbac_user_req_cert](/capturas/55_rbac_VII.JPG)

<br />

### - Comprobación final de permisos de usuario

```bash
kubectl config use-context sal-context

kubectl get pods
```

![rbac_context_final_check](/capturas/56_rbac_VIII.JPG)

<br />

## - Almacenamiento de datos: StatefulSet Helm Chart PostgreSQL

<br />

### - Preparación del terreno de campo, instalación y actualización de chart Helm de Bitnami

```bash
helm repo add bitnami https://charts.bitnami.com/bitnami

helm repo update
```

![helm_postgresql_repo_add_install](/capturas/57_helm_postgresql_I.JPG)

<br />

### - Creación de _namespace_ "sal-postgresql" e instalación de repositorio PostgreSQL

```bash
kubectl create namespace sal-postgresql

kubectl get ns # Comprobación

helm install postgresql bitnami/postgresql -n sal-postgresql
```

![helm_postgresql_repo_install](/capturas/58_helm_postgresql_II.JPG)

<br />

### - Comprobación de objetos K8s PostgreSQL

```bash
kubectl -n sal-postgresql get pos,svc,pv,pvc -o wide # Pods, servicios, "persistent-volume", "persistent-volume-claim"
```

![helm_postgresql_check](/capturas/59_helm_postgresql_III.JPG)

<br />

### - Obtención contraseña PostgreSQL K8s

```bash
export POSTGRES_PASSWORD=$(kubectl get secret --namespace sal-postgresql postgresql -o jsonpath="{.data.postgresql-password}" | base64 --decode)

echo $POSTGRES_PASSWORD
```

![helm_postgresql_check](/capturas/60_helm_postgresql_IV.JPG)

<br />

### - Conexión a la base de datos de PostgreSQL CLI

```bash
kubectl run postgresql-client --rm --tty -i --restart='Never' --namespace sal-postgresql --image docker.io/bitnami/postgresql:11.14.0-debian-10-r17 --env="PGPASSWORD=$POSTGRES_PASSWORD" --command -- psql --host postgresql -U postgres -d postgres -p 5432
```

![helm_postgresql_check](/capturas/61_helm_postgresql_V.JPG)


<br />

### - Conexión a la base de datos de PostgreSQL _"remota"_ desde DBeaver

```bash
kubectl port-forward --namespace sal-postgresql svc/postgresql 5432:5432 & PGPASSWORD="$POSTGRES_PASSWORD" psql --host 127.0.0.1 -U postgres -d postgres -p 5432
# Una vez ejecutado pulsar CTRL+C y aparecerá el prompt de PostgreSQL
```

![helm_postgresql_check](/capturas/62_helm_postgresql_VI.JPG)

<br />

## - Redes - Servidor Web Nginx + _Ingress Cert-ManagerTLS Let's Encrypt_

<br />

### - Implantación de _Cert-Manager_

```bash
curl -LO https://github.com/jetstack/cert-manager/releases/download/v1.6.1/cert-manager.yaml

ls -la cert-* # Para comprobar su existencia

mv cert-manager.yaml cert-manager-v1.6.1.yaml # Renombramos el archivo

kubectl create ns cert-manager

kubectl apply --validate=false -f cert-manager-v1.6.1.yaml
```

![nginx_cert-manager](63_nginx_I.JPG)

<br />

### - Comprobación de _Cert-Manager_

```bash
kubectl -n cert-manager get all
```

![nginx_cert-manager](64_nginx_II.JPG)

<br />

### - Creación de archivos "_sal-issuer.yaml_" y "_sal-certificate.yaml_"

```yaml
# sal-issuer.yaml
apiVersion: cert-manager.io/v1
kind: Issuer
metadata:
  name: sal-selfsigned
  namespace: cert-manager
spec:
  selfSigned: {}
```
```yaml
# sal-certificate.yaml
apiVersion: cert-manager.io/v1
kind: Certificate
metadata:
  name: selfsigned-cert
  namespace: cert-manager
spec:
  dnsNames:
    - sal-kubernites.com
  secretName: selfsigned-cert-tls
  issuerRef:
    name: sal-selfsigned
```

```bash
kubectl apply -f sal-issuer.yaml

kubectl apply -f sal-certificate.yaml
```

![nginx_cert-manager_issuer_certificate](65_nginx_III.JPG)

<br />

### - Comprobación del funcionamiento del _issuer_

```bash
kubectl -n cert-manager get all
```

![nginx_cert-manager_issuer_check](66_nginx_IV.JPG)

<br />

### - Habilitación y comprobación de _Minikube Addon **Ingress**_

```bash
minikube addons enable ingress

kubectl -n ingress-nginx get all

NODEIP=$(minikube ip)

echo $NODEIP

curl http://$NODEIP:#nodo
```

![nginx_ingress](67_nginx_V.JPG)

![nginx_ingress](68_nginx_VI.JPG)

<br />

### - Comprobación de Clusterissuer _Let's Encrypt_
```yaml
# sal-cert-issuer-nginx-ingress.yaml
apiVersion: cert-manager.io/v1
kind: ClusterIssuer
metadata:
  name: sal-letsencrypt-cluster-issuer
spec:
  acme:
    server: https://acme-v02.api.letsencrypt.org/directory
    email: sal-kubernites@kubernites.com
    privateKeySecretRef:
      name: letsencrypt-cluster-issuer-key
    solvers:
      - http01:
          ingress:
            class: nginx
```

```bash
kubectl apply -f sal-cert-issuer-nginx-ingress.yaml

kubectl describe clusterissuer sal-letsencrypt-cluster-issuer
```

![nginx_clusterissuer-letsencrypt](69_nginx_VII.JPG)

<br />

### - Despliegue de pods y servicios _sal-kubernites_

```bash
kubectl apply -f sal-kubernites-deploy.yaml

kubectl apply -f sal-kubernites-svc.yaml

kubectl get pods,svc
```

![nginx_sal-kubernites_deploy-svc](70_nginx_VIII.JPG)
