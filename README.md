# Kubernetes

```bash
Ein Kubernetes-Multinode-Cluster mit Ansible und Vagrant erstellt.
Es beinhaltet das Kubernetes-Dashboard, Chatbot-Ki, Wordpressumgebung mit MySQL Datenbank.
```

#### Benutzung:

```bash
sudo apt update && sudo apt -y install ansible ansible-lint make vagrant git
git clone https://github.com/JoergEF/Kubernetes
cd Kubernetes
make
```

### config erstellen

```bash
scp -P 2222 vagrant@127.0.0.1:/home/vagrant/.kube/config ~/.kube/config
```

### Dashboard herunterladen und aktivieren

```bash
kubectl apply -f https://raw.githubusercontent.com/kubernetes/
dashboard/v2.2.0/aio/deploy/recommended.yaml
```
```bash
kubectl apply -f kubernetes-dashboard-service-np.yaml
```
```bash
Adresse: (https://192.168.100.11:30002)
```

### Token erstellen
```bash
kubectl -n kubernetes-dashboard describe secret $(kubectl -n \
kubernetes-dashboard get secret | grep admin-user | awk '{print $1}')
```

### Wordpress aktivieren
```bash
kubectl apply -k wordpress/.
```
```bash
Adresse: (http://192.168.100.11:32274)
```

### Chatbot aktivieren 
```bash
kubectl apply -f chatbot/.
```
```bash
Adresse: (http://192.168.100.11:30080)
```

### Services und Pods checken
```bash
kubectl get services
kubectl get pod "name"
```
