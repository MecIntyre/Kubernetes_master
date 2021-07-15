# Wordpress im k8s-Cluster mit 3 Instanzen
## mit lokalem Storage

1. Notwendige Verzeichnisse anlegen:
    ```bash
    vagrant ssh k8s-n-1
    sudo mkdir -p /mnt/{wp, my}
    exit
    vagrant ssh k8s-n-2
    sudo mkdir -p /mnt/{wp, my}
    exit
    vagrant ssh k8s-n-3
    sudo mkdir -p /mnt/{wp, my}
    exit
    ```

2. wordpress/kustomization.yaml anpassen:

```bash
    in Zeile 6 <ENTER> und dann zusätzlich einfügen:
    - persistentvolume.yaml

    speichern nicht vergessen!
```

3. worpress/mysql-deployment anpassen:
    
    in Zeile 22 einfügen:

 ```yaml
    StorageClassName = manual
    capacity:
        storage: 10Gi
    hostPath:
    path: "/mnt/data/my"
 ```

 4. worpress/wordpress-deployment anpassen:
    
    in Zeile 22 einfügen:

 ```yaml
    StorageClassName = manual
    capacity:
        storage: 10Gi
    hostPath:
    path: "/mnt/data/wp"
 ```

5. anwenden:

```bash
kubectl apply -k wordpress/.
```
---
## mit Cluster - Storage (ceph)

1. ceph-Cluster installieren
2. wordpress/kustomization.yaml anpassen:

```bash
    in Zeile 6 löschen

    speichern nicht vergessen!
```

3. worpress/mysql-deployment anpassen:
    
    in Zeile 22 ändern:

 ```yaml
    StorageClassName = rook-ceph-block

ab Zeile 23 folgendes löschen:

    capacity:
        storage: 10Gi
    hostPath:
    path: "/mnt/data/my"
```

 4. worpress/wordpress-deployment anpassen:
    
    in Zeile 22 ändern:

 ```yaml
    StorageClassName = rook-ceph-block

ab Zeile 23 folgendes löschen:

    capacity:
        storage: 10Gi
    hostPath:
    path: "/mnt/data/wp"
```
