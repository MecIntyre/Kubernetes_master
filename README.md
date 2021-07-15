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

##### Das Passwort lautet 'vagrant'

### Testen der Pods und Services

```bash
1. kubectl get services
2. kubectl get pods 'name'
3. kubectl get pvc
```
