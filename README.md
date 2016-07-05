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





