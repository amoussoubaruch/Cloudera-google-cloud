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

> Configurer seLinux

```sh
$ getenforce                            # Voir quelle est la config actuelle
$ vim /etc/selinux/config               # change to permissive permissive
$ setenforce 0                          # run the following command to disable SELinux immediately
$ reboot                                # Si la modification ne prend pas immédiatement effet
```

> https://www.cloudera.com/documentation/enterprise/5-5-x/topics/install_cdh_disable_selinux.html

> Configuration du fichier  /etc/hosts sur chaque machine 

```sh
$ vi /etc/hosts    # Ouvrir le fichier et ajouter les ip et nom de machines  
```
![MetaStore remote database](https://github.com/amoussoubaruch/hortonworks---Google-Cloud/blob/master/Img/img1.png)

> Ajouter l'ulisisateur hadoop avec les droits root

```sh
$ useradd hadoop     # Ajout de l'utilisateur haddop
$ passwd hadoop      # Changer son mot de passe
$ visudo             # Donner les droits root à l'utilisateur hadoop (Voir grapphe ci dessous)
```

![MetaStore remote database](https://github.com/amoussoubaruch/hortonworks---Google-Cloud/blob/master/Img/img2.png)

> Configuration SSH entre le master node et les namenodes

> Génération de la clé privé SSH  

```sh
$ ssh-keygen  # Mettre le paramètre çi dessous
```
![MetaStore remote database](https://github.com/amoussoubaruch/hortonworks---Google-Cloud/blob/master/Img/ssh.png)


> Copie de la clé sur tous les autres noeuds y compris le name node 

```sh
$ ssh-copy-id -i /root/.ssh/id_rsa.pub root@cloudera1.c.cloudera-1363.internal    # Name node
$ ssh-copy-id -i /root/.ssh/id_rsa.pub root@cloudera2.c.cloudera-1363.internal     # Copy key to node 1 
$ ssh-copy-id -i /root/.ssh/id_rsa.pub root@cloudera3.c.cloudera-1363.internal    # Copy key to node 2
$ ssh-copy-id -i /root/.ssh/id_rsa.pub root@cloudera4.c.cloudera-1363.internal     # Copy key to node 3
```
> Configurer le fichier  /etc/sysconfig/network et rajouter le nom de la machine

```sh
$ vi /etc/sysconfig/network
```

> Télécharger et lancer cloudera manager server sur le master node

1. Téléchargement 

```sh
$ wget https://archive.cloudera.com/cm5/installer/5.7.0/cloudera-manager-installer.bin
```

2. Donner les droits d'exécution sur au fichier 

```sh
$ chmod u+x cloudera-manager-installer.bin
```

3. Lancer cloudera manager installer

```sh
$ ./cloudera-manager-installer.bin
```

> On a les images suivantes (Cliquer sur next --> next ...)

![MetaStore remote database](https://github.com/amoussoubaruch/hortonworks---Google-Cloud/blob/master/Img/img3.png)

![MetaStore remote database](https://github.com/amoussoubaruch/hortonworks---Google-Cloud/blob/master/Img/img4.png)

> Lorsque tous les packages sont bien installés 

![MetaStore remote database](https://github.com/amoussoubaruch/hortonworks---Google-Cloud/blob/master/Img/img5.png)

> Fichier log de démarage : tail -f /var/log/cloudera-scm-server/cloudera-scm-server.log


