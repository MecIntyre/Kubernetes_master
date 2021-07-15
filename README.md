# Kubernetes

```bash
Ein Kubernetes-Multinode-Cluster mit Ansible und Vagrant erstellt.
Es beinhaltet ceph-cluster-Dashboard, das Kubernetes-Dashboard, Chatbot-Ki, 
Wordpressumgebung mit MySQL Datenbank und nginx-Testumgebung.
```

#### Benutzung:

```bash
sudo apt update && sudo apt -y install ansible ansible-lint make vagrant git
git clone https://github.com/JoergEF/Kubernetes
cd Kubernetes
make
```

### Nachdem 'make' erfolgreich beendet ist, Master-Node-Verbindung festlegen

```bash
scp -P 2222 vagrant@127.0.0.1:/home/vagrant/.kube/config ~/.kube/config
```

<<<<<<< HEAD
##### Das Passwort lautet 'vagrant'
=======
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
>>>>>>> 0a3512eb1f6a5b70911fb0fd111423d41f54775e

### Testen der Pods und Services

```bash
1. kubectl get services
2. kubectl get pods 'name'
3. kubectl get pvc
```
