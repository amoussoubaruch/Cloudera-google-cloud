# Cloudera-google-cloud

1. Node installation

> Passer en mode root

```sh
$ sudo -i
```

> Changer le mot de passe Root 

```sh 
$ passwd                       # Saisir le nouveau mot de passe 
```

> Installation Gcloud

```sh 
$ curl https://sdk.cloud.google.com | bash
$ exec -l $SHELL
$ gcloud components list # Afficher toutes les composantes de gcloud
```

> Mise à jour des packages 

```sh 
$ yum update
```

> Modification de la configuration SSH 

```sh
$ cp /etc/ssh/sshd_config /etc/ssh/sshd_config.bak  # Copie du fichier sshd_config vers sshd_config.bak 
$ vi /etc/ssh/sshd_config                           # edit the file with this setting (PermitRootLogin yes PasswordAuthentication yes)
$ /etc/init.d/sshd –t                               # Save the file, and run this command 
$ service sshd restart                              # Restart the sshd service
```

> Installation de java 

```sh
$ yum install java-1.8.0-openjdk        # Java 8
```

> Installation de postgresql 

```sh
$ yum install postgresql-server.x86_64
```

> Prerequis installation cloudera : http://www.cloudera.com/documentation/enterprise/5-6-x/topics/cm_ig_cm_requirements.html#cmig_topic_4_1


> Configuration du fichier  /etc/hosts sur chaque machine 

```sh
$ vi /etc/hosts    # Ouvrir le fichier et ajouter les ip et nom de machines  
```
![MetaStore remote database](https://github.com/amoussoubaruch/hortonworks---Google-Cloud/blob/master/Img/img1.png)

> Configuration SSH entre le master node et les namenodes

> On name node generate key 

```sh
$ ssh-keygen  # Mettre le paramètre çi dessous
```
![MetaStore remote database](https://github.com/amoussoubaruch/hortonworks---Google-Cloud/blob/master/Img/ssh.png)


> Copie de la clé sur tous les autres noeuds y compris le name node 

```sh
$ ssh-copy-id -i /root/.ssh/id_rsa.pub root@hdp1.c.mapr-1355.internal    # Name node
$ ssh-copy-id -i /root/.ssh/id_rsa.pub root@hdp2.c.mapr-1355.internal     # Copy key to node 1 
$ ssh-copy-id -i /root/.ssh/id_rsa.pub root@hdp3.c.mapr-1355.internal    # Copy key to node 2
$ ssh-copy-id -i /root/.ssh/id_rsa.pub root@hdp4.c.mapr-1355.internal     # Copy key to node 3
$ ssh-copy-id -i /root/.ssh/id_rsa.pub root@hdp5.c.mapr-1355.internal    # Copy key to node 4
```
